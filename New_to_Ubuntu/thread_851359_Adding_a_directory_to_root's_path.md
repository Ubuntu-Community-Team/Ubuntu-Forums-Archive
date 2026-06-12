---
title: "Adding a directory to root's path"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by tapetibett on 2008-07-06
I'm trying to add the directory /opt/lampp/bin to $PATH so I don't have to reference the programs there directly every time I want to run them. I successfully did this for regular users by adding the lines:
PATH=$PATH:/opt/lampp/bin
export PATH
to the end of etc/profile, however this doesn't do it for root. I looked it up and saw that I should edit the file .bash_profile in the /root directory but this file doesn't exist, in fact the /root directory is completely empty. I opened gedit, added those 2 lines to an empty file and saved it as /root/.bash_profile but this didn't change root's PATH and it still looks like the /root directory is empty. I feel like I'm missing something obvious.. what did I do wrong?

---

### Post by kbuel on 2008-07-06
are you doing this because something doesn't work when you use sudo to run the program?

---

### Post by kbuel on 2008-07-06
I normally add directories to my path in my .bashrc file located in my home directory.

gedit ~/.bashrc

then just go to the bottom and add 
PATH=$PATH:/opt/lampp/bin

You don't need to export it.

this path will work when using sudo also.

---

### Post by tapetibett on 2008-07-06
OK I tried that but it still won't work with sudo unless I reference the program directly.

---

### Post by lamego on 2008-07-06
The system wide base path is set from /etc/environment .

---

