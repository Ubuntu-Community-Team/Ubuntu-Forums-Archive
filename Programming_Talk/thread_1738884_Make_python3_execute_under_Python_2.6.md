---
title: "Make python3 execute under Python 2.6"
date: 2011-04-25
forum: Programming Talk
---

### Post by Code9 on 2011-04-25
I recently found a python script that runs under python 3. My problem is the server I am running it in only has python 2.6 in it.
It uses the urllib module in order to function and I know a lot of that was changed when they changed it to python 3. 

[Here ]("http://code.google.com/p/python-weather-api/")is a link to the weather script I plan on using.

---

### Post by ssam on 2011-04-25
there is a script called 3to2 that can convert some python3 into python2. but you may have to do some of the translation by hand.

---

### Post by oldfred on 2011-04-25
The example is python2?

With python3 you have to have print(). And the example does not have the parenthesizes.

---

### Post by Code9 on 2011-04-25
Thanks for your response.

I got a script to work, however I cannot get it to execute properly on my site. The cgiwrapd shows no errors but when I try to load the page, it doesn't load at all. An Internal Server Error

---

