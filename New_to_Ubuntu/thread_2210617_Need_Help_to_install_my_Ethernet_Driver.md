---
title: "Need Help to install my Ethernet Driver"
date: 2014-03-11
forum: New to Ubuntu
---

### Post by michael120 on 2014-03-11
Hello, I got Ubuntu installed and its the latest version. The problem is when I connect the Ethernet cable to my system it just won't connected to the internet. Then I ran a command(sudo ifconfig -a)that will let me see if my driver(ethx should be shown but it was not) is installed but it's not. So I got my phone and teathered to my system (only option to connect to the internet). I go online and find the name of my network adapter and go to their website and download the latest driver version. After I downloaded it I extracted to the desktop. Now I have no clue what to do. Just need to install or apply. Just have zero clue. 
Thanks for everyone who helps me.

I have Realtek ethernet card

RTL 8111/8168/8411 PCI Express Gigabit Ethernet Controller

---

### Post by varunendra on 2014-03-11
Welcome to Ubuntu Forums Michael !

Please give us link to the driver you downloaded, also the full name of the file.

Apart from these, please also show us the following outputs, so we know if it is correct driver and you indeed need it. Open a terminal (Ctrl-Alt-T) and run the following commands -
```
uname -mr
lsb_release -d
sudo lshw -numeric -C network -sanitize
nm-tool
```
Copy the outputs using your mouse cursor, and paste them in your next post here.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

