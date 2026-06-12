---
title: "I have a folder on my desktop filled with .html files.."
date: 2012-06-18
forum: New to Ubuntu
---

### Post by bostoncab on 2012-06-18
I have a folder on my desktop filled with .html files.. I want to merge them into a single .html file via command line in the terminal. Can you help with this?

---

### Post by MG&amp;TL on 2012-06-18
You'll have to give us a bit more info...if you just want them all in one file, that's easy enough.

```

cd ~/Desktop/folder
cat *.html > allinone.html
```But I guarantee that the complete file won't be strict html. You'll have multiple <html>, <head> and <body> tags, for a start.

---

### Post by vasa1 on 2012-06-18
> **MG&TL said:**
> You'll have to give us a bit more info...if you just want them all in one file, that's easy enough.

[CODE]... You'll have multiple <html>, <head> and <body> tags, for a start.

That's for sure! Also, many .html files may have a folder associated with them and that folder may contain images, css, etc.

Altogether not the way to go!

Assuming the number of files is manageable, I would use one browser to open as many files as convenient. Then open something like Seamonkey in "Composer" mode and then use control+A and control+C in the other browser for file #1, alt tab over to the Composer window of Seamonkey and paste. After pasting, ensure the cursor is at the end of the Composer window, hit a couple of returns, enter some sort of ++++++ or whatever to indicate the end of file #1, and repeat the whole thing for file #2, etc, saving the Composer window as often as possible.

---

### Post by bostoncab on 2012-06-19
We are talking about the top 1,000 results for a specific keyword. 

Are there other HTML tags you predict being troublesome besides for the header tag? 

> **vasa1 said:**
> That's for sure! Also, many .html files may have a folder associated with them and that folder may contain images, css, etc.

Altogether not the way to go!

Assuming the number of files is manageable, I would use one browser to open as many files as convenient. Then open something like Seamonkey in "Composer" mode and then use control+A and control+C in the other browser for file #1, alt tab over to the Composer window of Seamonkey and paste. After pasting, ensure the cursor is at the end of the Composer window, hit a couple of returns, enter some sort of ++++++ or whatever to indicate the end of file #1, and repeat the whole thing for file #2, etc, saving the Composer window as often as possible.

---

### Post by greenpeace on 2012-06-19
> **bostoncab said:**
> We are talking about the top 1,000 results for a specific keyword. 

Would be useful for you to say what exactly it is that you're trying to achieve... but I'm guessing it's some kind of text analysis, and therefore you're not interested in images or styles?

If so, you would be find it much faster to use a scripting language like Python to process your files.

have a look at the [BeautifulSoup]("http://www.crummy.com/software/BeautifulSoup/") module for processing html in Python.  
It gives you simple ways to strip out the elements of the page that you want (<p> tags for example), or just all the text (see **get_text()** method)

perl is also very common used for text processing tasks...but I am not familiar enough with it to advise you.

---

### Post by bostoncab on 2012-06-19
I responded via pm with my the details of what I am trying.. it is an experiment but something much less high brow then what you suggested. Thank you and everyone else so much for the help. 


> **greenpeace said:**
> Would be useful for you to say what exactly it is that you're trying to achieve... but I'm guessing it's some kind of text analysis, and therefore you're not interested in images or styles?

If so, you would be find it much faster to use a scripting language like Python to process your files.

have a look at the [BeautifulSoup]("http://www.crummy.com/software/BeautifulSoup/") module for processing html in Python.  
It gives you simple ways to strip out the elements of the page that you want (<p> tags for example), or just all the text (see **get_text()** method)

perl is also very common used for text processing tasks...but I am not familiar enough with it to advise you.

---

