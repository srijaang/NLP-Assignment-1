import urllib.request
from bs4 import BeautifulSoup
import nltk
nltk.download('stopwords')
from nltk.corpus import stopwords
import matplotlib.pyplot as plt

#urllib library used to read SpaceX wikipedia page

response = urllib.request.urlopen('https://en.wikipedia.org/wiki/SpaceX')
html =  response.read()

#Beautiful Soup used to parse raw html data
soup = BeautifulSoup(html, "html5lib")
text = soup.get_text(strip = True)
tokens = [t for t in text.split()]
clean_tokens = tokens[:]

#NLTKs Frequency Distribution to count the word frequency
frequency = nltk.FreqDist(tokens)
keys =[]
values = []

for key,val in frequency.items():
    #Printing Values where frequency is greater than 5
    if val>5:
        print(str(key) + ':' +str(val))
        keys.append(key)
        values.append(val)
    else:
        tokens.remove(key)

#Plotting of graph without removing stopwords
frequency.plot(20,cumulative= False)

#After removal of stop words
for token in tokens:
    #Removing Tokens which contain digits
    if str(token).isdigit():
        clean_tokens.remove(token)
    #Removing stopwords in English langauge
    if token in stopwords.words('english'):
        clean_tokens.remove(token)

# Frequency calculation after removing stopwords
final = nltk.FreqDist(clean_tokens)

#Plotting first 10 high distribution words
final.plot(10,cumulative= False)

#Plotting Bar graph as form of frequency visualization
plt.bar(keys[0:10], values[0:10], color='green')
plt.show()
