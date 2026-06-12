---
title: "Need a program that works with webpage"
date: 2008-05-15
forum: Programming Talk
---

### Post by chjustc on 2008-05-15
Hi there,

I am new to Ubuntu and programming. I want to develop a good method for collecting data from websites for my research.

I want to know how to write a program that can automatically push button on webpage to open new webpages, fill out right information on right fields if there is a form on the webpage and submit the form, and download stuff from the webpage opened if needed.

I know that someone did this (the program for automatic webpage manipulation) by using Visual Basic (on Windows).  Yet, someone else mentioned that Perl can do it too (on RedHat Enterprise).  I just want to ask you about the best way to do it on ubuntu, the best program language, and possible references that I should look for.

Thanks,

---

### Post by Majorix on 2008-05-15
I don't understand how you mean it. If you are planning to develop a program that can open up a random page, click to open a page then fill the username&pass and so on, you are in deep trouble. No seriously, the computers aren't any smart, they can't think as of yet.

But if you know the layout and url-map of the page, then you can use your favorite language (doesn't matter really, pick one you like) and its url-reading libraries.

Good luck.

---

### Post by pmasiar on 2008-05-15
You cannot run your program on someone else's webpage or server. But you can easily put together python script to get a page by it's URL (see urllib module), parse it (BeautifulSoup and many other parsers), and post the data back - including handling cokies. 

It will be plain commandline - or you can add pretty GUI frontend.

---

### Post by chjustc on 2008-05-15
> **Majorix said:**
> I don't understand how you mean it. If you are planning to develop a program that can open up a random page, click to open a page then fill the username&pass and so on, you are in deep trouble. No seriously, the computers aren't any smart, they can't think as of yet.

But if you know the layout and url-map of the page, then you can use your favorite language (doesn't matter really, pick one you like) and its url-reading libraries.

Good luck.

Thanks.

My case is the latter.  I know the layout and url-map of the page.  The page belongs to a vendor of public records.  I need to get the similar info for many different units, which means repeating the same procedure many times.  Hence, having a program to do is much better than doing it mannually.

I have a little bit experience with C/C++.  What would be the best way to learn about using the url-reading libraries?  Google?

---

### Post by chjustc on 2008-05-15
> **pmasiar said:**
> You cannot run your program on someone else's webpage or server. But you can easily put together python script to get a page by it's URL (see urllib module), parse it (BeautifulSoup and many other parsers), and post the data back - including handling cokies. 

It will be plain commandline - or you can add pretty GUI frontend.

Thanks. I just googled python.  It seems to be promising.

What do you mean by "commandline would be pain?"  I need the program to collect data for my own research purpose. If there is pain, I would have it all before I develop the GUI frontend.  Am I right?

---

### Post by NormR2 on 2008-05-15
An approach I used for a similiar program was a proxy server. The site was http, not https.  The program is written in Java.
The browser sent the initial request and cookies etc, then the program scanned the HTML as it came in and filled in the text fields in the <FORM before passing it on to display in the browser. All I had to do was click on the submit button. A smarter/better program could do the whole browser thing and send the complete <FORM data back to the sender.

---

### Post by chjustc on 2008-05-15
> **NormR2 said:**
> An approach I used for a similiar program was a proxy server. The site was http, not https.  The program is written in Java.
The browser sent the initial request and cookies etc, then the program scanned the HTML as it came in and filled in the text fields in the <FORM before passing it on to display in the browser. All I had to do was click on the submit button. A smarter/better program could do the whole browser thing and send the complete <FORM data back to the sender.

Thanks.  Good to know another example.

---

### Post by nanotube on 2008-05-16
> **chjustc said:**
> Thanks. I just googled python.  It seems to be promising.

What do you mean by "commandline would be pain?"  I need the program to collect data for my own research purpose. If there is pain, I would have it all before I develop the GUI frontend.  Am I right?

read carefully, he didn't say "pain" he said "plain". and "plain" is good in my book. :)

I would suggest you look at the "mechanize" library for python, that will make the coding pretty much a cinch (once you figure out the basics of using mechanize):
[http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/)

I've used it myself for data retrieval for research, it works very nicely. :)

give it a shot, play around with it, and if you run into trouble, feel free to post back here with your code and questions.

---

### Post by chjustc on 2008-05-16
> **nanotube said:**
> read carefully, he didn't say "pain" he said "plain". and "plain" is good in my book. :)

I would suggest you look at the "mechanize" library for python, that will make the coding pretty much a cinch (once you figure out the basics of using mechanize):
[http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/)

I've used it myself for data retrieval for research, it works very nicely. :)

give it a shot, play around with it, and if you run into trouble, feel free to post back here with your code and questions.

Thanks! My bad on the "plain" v.s. "pain".  I agree that plain means good.

I will definitely give it shot and possibly get back to you.  It may take some time. :p

---

