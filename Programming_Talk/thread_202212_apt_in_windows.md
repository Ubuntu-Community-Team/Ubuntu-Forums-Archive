---
title: "apt in windows"
date: 2006-06-23
forum: Programming Talk
---

### Post by grexk on 2006-06-23
I have been using Debian and Ubuntu and my problem is that I can't apt-get. Because I don't have internet connection at home, so I had to install ubuntu in usb-harddisk and apt-get packages. Do you think this is possible in using python-apt? What are the requirements of apt(eg. dir, etc)? Right now I'm studying the python-apt.

---

### Post by oldmanstan on 2006-06-23
one thing that you could do which might be a little easier than running ubuntu off a usb disk is just downloading the packages wherever you have an internet connection and then installing them when you get home.

just a thought.

if you want to do this check out the debian web site for the packages (it lets you search and it will inform you of all dependencies) and also read up on the dpkg command (basically you just do dpkg -i <packagename> where <packagename> is a *.deb file you have downloaded

also, synaptic has a setting to just download the packages without installing, this might allow you to do the same thing but you wouldn't have to worry about dependencies yourself, however you would need to have access to another computer running some sort of ubuntu or debian based linux with an internet connection

---

### Post by grexk on 2006-06-23
> dpkg -i <packagename> where <packagename> is a *.deb file you have downloaded
...from packages.ubuntu.com is tiresome.

---

### Post by oldmanstan on 2006-06-23
well yes, it is sort of a pain, but once you install all the software you want you won't have to do it very often

also, i am pretty sure that you could use synaptic to download packages onto the harddrive with your internet-connected system and then once they are there use synaptic to install them by adding the location you downloaded them to as a "source"

also, you could write a shell script (i don't know how comfortable you are with such things) that would install the packages for you

---

### Post by grexk on 2006-06-24
Yes, but I want to have a simple python app with gui that is portable to other platform. I know basic shell scripting but I'm more comfortable with python.

---

### Post by oldmanstan on 2006-06-26
so wait, you want it to be platform independent why? there is no reason to hook up to the repositories using anything other than linux because the software is for linux... as far as using another system to install software on your portable harddrive, why not just use a liveCD or your portable harddrive to boot your internet-connected machine into linux... you are making it too complicated for yourself i think, unless i'm misunderstanding what you actually want

---

### Post by grexk on 2006-06-29
Thanks for your opinion. I just need to do my homework with apt and python-apt.

---

### Post by minasmorath on 2008-05-08
i'm more than willing to write a windows application that downloads deb files and their dependencies into a directory so that you can move them to your ubuntu machine... is that what you're looking for? I've been working on this problem for awhile, but i'm still missing the basics, like how to find the dependencies without using an algorithm that scans for sections of the web page that indicate the start of the list and the end of the list... i think the key is in the .tar.gz file within the .deb but i'm still shaky on the programming needed to read it...

---

### Post by evymetal on 2008-05-09
inside the .deb there is a file control.tar.gz

Inside that there is a file called "control" (in the folder ".") - that's the file that tells you everything about the .deb

---

