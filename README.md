# 100-real-life-code-examples-across-Python-SQL-and-JavaScript-

Python Code Examples 

Reading and Writing Files:


with open('data.txt', 'r') as file:
    content = file.read()
#Sending Emails:

import smtplib
from email.mime.text import MIMEText

msg = MIMEText('Hello from Python!')
msg['Subject'] = 'Test Email'
server = smtplib.SMTP('smtp.gmail.com', 587)
server.starttls()
server.login('youremail@gmail.com', 'password')
server.sendmail('from@gmail.com', 'to@gmail.com', msg.as_string())
server.quit()

# Renaming Files in Bulk:
import os

for filename in os.listdir('my_folder'):
    new_name = filename.replace('old', 'new')
    os.rename(f'my_folder/{filename}', f'my_folder/{new_name}')

# Automating Browser Tasks:

from selenium import webdriver

browser = webdriver.Chrome()
browser.get('https://www.google.com')
search_box = browser.find_element_by_name('q')
search_box.send_keys('Python automation')
search_box.submit()

# Scheduling Tasks:

import schedule
import time

def job():
    print("Doing scheduled task...")

schedule.every().day.at("10:30").do(job)

while True:
    schedule.run_pending()
    time.sleep(1)

# Web Scraping with BeautifulSoup:

import requests
from bs4 import BeautifulSoup

response = requests.get('https://news.ycombinator.com/')
soup = BeautifulSoup(response.text, 'html.parser')
headlines = soup.find_all('a', class_='storylink')
for headline in headlines:
    print(headline.text)

# Calculating Age from Birthdate:


from datetime import datetime

def calculate_age(birthdate):
    today = datetime.today()
    age = today.year - birthdate.year - ((today.month, today.day) < (birthdate.month, birthdate.day))
    return age

print(calculate_age(datetime(1990, 5, 12)))
# Password Generator:

import random
import string

def generate_password(length=8):
    chars = string.ascii_letters + string.digits + string.punctuation
    return ''.join(random.choice(chars) for _ in range(length))

print(generate_password(12))
# CSV Data Analysis:

import csv

with open('data.csv', newline='') as csvfile:
    reader = csv.DictReader(csvfile)
    for row in reader:
        print(row['Name'], row['Age'])

# Unit Conversion (e.g., Celsius to Fahrenheit):

def celsius_to_fahrenheit(celsius):
    return (celsius * 9/5) + 32

print(celsius_to_fahrenheit(25))

# Random Number Guessing Game:

import random
number = random.randint(1, 100)
guess = None
while guess != number:
    guess = int(input('Guess a number between 1 and 100: '))
    if guess < number:
        print('Too low!')
    elif guess > number:
        print('Too high!')
    else:
        print('Correct!')

# Image Downloader:


import requests

url = 'https://example.com/image.jpg'
response = requests.get(url)
with open('image.jpg', 'wb') as file:
    file.write(response.content)

# Working with JSON:


import json
data = '{"name": "John", "age": 30}'
parsed = json.loads(data)
print(parsed['name'])

# Dictionary Word Lookup:


import json

dictionary = {'Python': 'A high-level programming language.'}
word = input('Enter a word: ')
if word in dictionary:
    print(f'{word}: {dictionary[word]}')
else:
    print('Word not found')

# Stock Price Fetching (Using APIs):


import requests

response = requests.get('https://api.example.com/stock/AAPL')
stock_data = response.json()
print(stock_data['price'])

# Currency Converter (API-based):

import requests

response = requests.get('https://api.exchangerate-api.com/v4/latest/USD')
data = response.json()
usd_to_inr = data['rates']['INR']
print(f"USD to INR: {usd_to_inr}")


# Instagram Photo Downloader:

from instaloader import Instaloader, Profile

loader = Instaloader()
profile = Profile.from_username(loader.context, "username")
for post in profile.get_posts():
    loader.download_post(post, target=profile.username)


# Temperature Logger:

import time

def read_temperature():
    return 22.5  # Simulated temperature

with open('temperature_log.txt', 'a') as file:
    while True:
        temperature = read_temperature()
        file.write(f'{time.ctime()}: {temperature}\n')
        time.sleep(60)

# PDF Merger:

from PyPDF2 import PdfMerger

merger = PdfMerger()
merger.append('file1.pdf')
merger.append('file2.pdf')
merger.write('merged.pdf')
merger.close()
Sorting a List of Strings:


names = ['John', 'Alice', 'Bob']
sorted_names = sorted(names)
print(sorted_names)


# Working with Datetime:

from datetime import datetime

now = datetime.now()
print(now.strftime('%Y-%m-%d %H:%M:%S'))
BMI Calculator:


def calculate_bmi(weight, height):
    return weight / (height ** 2)

print(calculate_bmi(70, 1.75))

# Finding Prime Numbers:

def is_prime(num):
    for i in range(2, num):
        if num % i == 0:
            return False
    return True

print([x for x in range(2, 100) if is_prime(x)])


# URL Shortener (Using TinyURL API):


import requests

url = 'https://tinyurl.com/api-create.php?url=http://example.com'
short_url = requests.get(url).text
print(short_url)

# Real-Time Weather Checker (API-based):

import requests

city = 'London'
api_key = 'your_api_key'
url = f'http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}'
weather_data = requests.get(url).json()
print(weather_data['main']['temp'])

# Phone Number Validator:

import phonenumbers

number = phonenumbers.parse("+14155552671")
print(phonenumbers.is_valid_number(number))


# Data Encryption (AES):


from Crypto.Cipher import AES

cipher = AES.new('This is a key123', AES.MODE_CBC, 'This is an IV456')
encrypted = cipher.encrypt('secret message'.rjust(32))
print(encrypted)

# Automating WhatsApp Messages:


import pywhatkit

pywhatkit.sendwhatmsg('+123456789', 'Hello!', 18, 0)

# Scraping Amazon Product Prices:


import requests
from bs4 import BeautifulSoup

url = 'https://www.amazon.com/dp/B08J5F3G18'
headers = {"User-Agent": "Mozilla/5.0"}
page = requests.get(url, headers=headers)
soup = BeautifulSoup(page.content, 'html.parser')
price = soup.find('span', {'id': 'priceblock_ourprice'}).text
print(f'Price: {price}')


# Face Detection with OpenCV:


import cv2

face_cascade = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')
img = cv2.imread('photo.jpg')
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
faces = face_cascade.detectMultiScale(gray, 1.3, 5)
for (x, y, w, h) in faces:
    cv2.rectangle(img, (x, y), (x+w, y+h), (255, 0, 0), 2)
cv2.imshow('Image', img)
cv2.waitKey(0)

# Simple Chatbot:


responses = {
    "hi": "Hello!",
    "how are you": "I'm doing well, thank you!",
    "bye": "Goodbye!"
}

while True:
    user_input = input("You: ").lower()
    if user_input in responses:
        print(f'Bot: {responses[user_input]}')
    else:
        print("Bot: I don't understand.")

# Downloading YouTube Videos:

from pytube import YouTube

url = 'https://www.youtube.com/watch?v=dQw4w9WgXcQ'
yt = YouTube(url)
yt.streams.first().download()

# Analyzing Text Frequency:

from collections import Counter

text = "Python is great. Python is fun."
words = text.split()
word_count = Counter(words)
print(word_count)

# Speech Recognition:

import speech_recognition as sr

recognizer = sr.Recognizer()
with sr.Microphone() as source:
    audio = recognizer.listen(source)
text = recognizer.recognize_google(audio)
print(text)
