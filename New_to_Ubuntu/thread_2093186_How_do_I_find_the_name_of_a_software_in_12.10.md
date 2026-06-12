---
title: "How do I find the name of a software in 12.10?"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by CFJensen on 2012-12-10
Hi,  So I've installed 12.10, and it is my very first time using Ubuntu.  So far so good, but I was prompted to install "reddit" when I visited the website, and was curious.      Now "reddit" with the logo appears when clicking the top-right mail icon. Also reddit appears as a program when I search using the ubuntu button, and basically just opens the website in Firefox.     I really want to remove it, but I can't for the life of me figure out how to do it?   I tried sudo apt-get remove reddit, but nothing was found.   I've tried to make a list of all the software I have installed as a txt, but I can't find the name there either.   So my questions are:    What have I installed?    How do I remove it?      Thank you very much!  edit: Wow, formatting is completely screwed up?

---

### Post by debodas on 2012-12-10
Have you opened the software center and checked to see if redit is listed in the install list there? If it is just click on the remove button.

---

### Post by 3rdalbum on 2012-12-10
[http://askubuntu.com/questions/166655/how-do-i-remove-a-website-from-ubuntus-web-applications]("http://askubuntu.com/questions/166655/how-do-i-remove-a-website-from-ubuntus-web-applications")

---

### Post by vasa1 on 2012-12-10
```
dpkg --get-selections
``` should give you a list of installed software.
Alternatively, you could look around in /usr/share/applications.

---

### Post by CFJensen on 2012-12-10
> **3rdalbum said:**
> [http://askubuntu.com/questions/166655/how-do-i-remove-a-website-from-ubuntus-web-applications](http://askubuntu.com/questions/166655/how-do-i-remove-a-website-from-ubuntus-web-applications)

I tried this without luck. I have uninstalled the web-app for Reddit as well as the Service for Web-apps altogether, and it appears as Deinstall if I use the --get-selections command.

Reddit still appears in my mail-indicator and under Programs in the Panel start page.

Any other ideas? :)

---

### Post by debodas on 2012-12-10
Have you tried ```
sudo apt-get purge reddit
```

---

