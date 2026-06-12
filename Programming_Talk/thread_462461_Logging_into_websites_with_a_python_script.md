---
title: "Logging into websites with a python script"
date: 2007-06-02
forum: Programming Talk
---

### Post by flummoxed on 2007-06-02
I recently had the idea of creating a python program that would log into my local library's online renewal service, which tells you the titles, due dates, renewals, etc. of your currently checked out books, take that information, display it, and alert you when books are about to be overdue. That's the general idea for some of the features for when I have a finished program. 

The first problem I'm trying to solve while writing this is that I need to find a way to connect to the library website with username/password. It's more difficult when you have to actually log into something than just grab a URL. I don't have much in the way of python or http expertise (but i know a fair amount of python... enough to understand the basics and learn as I go). I googled this subject in hopes of finding an answer, and I think I sort of did. However, it's unclear to me what is the right choice.

urllib2, which  is a built-in Python library, seems like it would be the easiest, but it's unclear as to whether or not it supports what I'm looking for. I believe the technical term is Authentication? I also came across urlgrabber, which is an independently developped library that was meant to extend urllib2, I believe. Does anyone know which library would be easier to use?

Maybe somebody could point me in the right direction with some links describing what I'm trying to understand.

Thanks

---

### Post by pmasiar on 2007-06-02
It depends what kind of authentication your library uses.

Ours uses java applet which handles authentication and display, so  any outside app could have hard time connect. And it makes sense, library does not want to be responsible if a patron's book record was leaked out.

How connecting to your library record looks like? Is it HTML form, or something fancier?

Maybe you can try to do something simpler first, like checking temperature in your home city from yahoo weather or somehing.

Wiki in my sig has many trainig tasks for Python learners, feel free to check it out.

---

### Post by ghostdog74 on 2007-06-02
urllib2 does support some basic authentication. you may want to check it out.

---

### Post by flummoxed on 2007-06-02
It's using JavaScript. I thought that might make it harder to connect.

That's too bad, maybe when I'm more advanced in python I'll be able to work around it, but for now I'll check out your list of training tasks.

---

### Post by cwaldbieser on 2007-06-04
> **flummoxed said:**
> I recently had the idea of creating a python program that would log into my local library's online renewal service, which tells you the titles, due dates, renewals, etc. of your currently checked out books, take that information, display it, and alert you when books are about to be overdue. That's the general idea for some of the features for when I have a finished program. 

The first problem I'm trying to solve while writing this is that I need to find a way to connect to the library website with username/password. It's more difficult when you have to actually log into something than just grab a URL. I don't have much in the way of python or http expertise (but i know a fair amount of python... enough to understand the basics and learn as I go). I googled this subject in hopes of finding an answer, and I think I sort of did. However, it's unclear to me what is the right choice.

urllib2, which  is a built-in Python library, seems like it would be the easiest, but it's unclear as to whether or not it supports what I'm looking for. I believe the technical term is Authentication? I also came across urlgrabber, which is an independently developped library that was meant to extend urllib2, I believe. Does anyone know which library would be easier to use?

Maybe somebody could point me in the right direction with some links describing what I'm trying to understand.

Thanks

Here is a link to another forum site where I helped someone with a similar problem:
[http://www.linuxquestions.org/questions/showthread.php?t=352040]("http://www.linuxquestions.org/questions/showthread.php?t=352040")

---

### Post by Max_Might on 2007-06-04
Can`t you just connect to the MySQL database or whatever you are using?

---

