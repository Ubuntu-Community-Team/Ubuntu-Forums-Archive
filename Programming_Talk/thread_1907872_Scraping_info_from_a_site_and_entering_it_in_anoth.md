---
title: "Scraping info from a site and entering it in another"
date: 2012-01-12
forum: Programming Talk
---

### Post by shortridge11 on 2012-01-12
In my city there is a large company that uses a site to raise awareness about itself. They announce several code words over the course of each day and you can enter them in on a site.There is a fan-based site that shows the code-names at the end of each day, and I usually go there around 7pm and enter them all in. I've decided as a side-project to become familiar with scraping info from sites I'm going to attempt to learn how to automate this process. 

So what I want to know how to do: Scrape codewords from one site, and enter them into another site.

I have no idea where to start, I have a home-server that I can use.  All I can think of is having a cron-tab script pull the html file down, process it using some overly complicated C and pull out the words, storing them in another file. I'd then use some service that acts as a user browsing the site and input the information using the newly generated text file containing the codewords as input.

Does this sound correct? Any pointers appreciated.


Edit: I don't intend on putting this out in the wild, I'd just like to have something concrete to show someone if they ask for experiencing in data-mining and parsing content.

---

### Post by CoffeeRain on 2012-01-12
I don't know how you would enter it into a site, but I know that looking at the content of the website would be easier than downloading it and then digging it out and storing it in a file. I have my experience in Python, and I know it is fairly simple to do it in Python, but do you have experience in Python?

---

### Post by shortridge11 on 2012-01-12
I do not, but I am more than willing to learn if that would be a good way to process it.

---

### Post by CharlesA on 2012-01-12
Why do I have a feeling that this sort of thing would be against the rules...

---

### Post by CoffeeRain on 2012-01-12
Would it be against the rules? Could you explain? And for Python, it is a good language to learn and pretty easy to learn too. I used the Google Python Class to learn. Just Google it. After that, looking at the Python docs and using the help() command just got me along. If you have any questions about it, post them here or Google them. Most likely you will find a Python doc for what you want, or someone on Stack Overflow with the same question. :)

---

### Post by shortridge11 on 2012-01-12
It probably would be if I used it, good thing I don't :P

---

### Post by shortridge11 on 2012-01-12
I will check out the python class and let you know the results. Thanks!

---

### Post by CharlesA on 2012-01-12
> **shortridge11 said:**
> It probably would be if I used it, good thing I don't :P
Ok, thanks for clarifying.

---

### Post by CoffeeRain on 2012-01-12
:) Python is not just for scraping info from websites. It is a great language, and you may be able to have more fun if you learn it.  I would recommend it, but if you don't have time, or if you don't need or want to you don't have to.

---

### Post by Boludinux on 2012-01-12
If you use gambas you could probably:

a) Download the webpage calling wget or creating an httpclient object checking from time to time changes with a timer object.
b) Look for the information with regular expressions (pcre module) from the downloaded file / buffer.
c) Use the post method of the httpclient object to insert values in such webpage.

Hope it helps.

---

