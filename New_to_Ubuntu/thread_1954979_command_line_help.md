---
title: "command line help"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by vegan1 on 2012-04-09
I do use Ubuntu. Is there a forum more specifically for people who want to move from the GUI to the command line?

How do you specify pathnames for moving or copying files? The book I'm using doesn't give real examples. Like if I wanted to copy a file from the desktop to my home directory, for example.

It seems like a lot of work to keep posting a forum thread for each question, since they will all be simple questions. There must be a better way.

I had trouble figuring out how to use VI, to create files to play around with.:popcorn:

---

### Post by Vaphell on 2012-04-09
sticky thread in this forum doesn't have useful information?
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

cp ~/Desktop/file.ext ~
~ being a shorthand for /home/current_user (or $HOME variable which has that path as its value)

tab is extremely useful as it shows possibilities and autocompletes names if first few chars provided unambiguously define the object of interest.
eg
cd ~/Des[COLOR="Blue"][tab][/COLOR]/file[COLOR="Blue"][tab][/COLOR] ~

---

### Post by jerome1232 on 2012-04-09
It's very usefull to know the general filesystem hierarchy, in otherwords where things go in the file system (expect system wide configurations to be in /etc, logs to be in /var, etc...)

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by mojorising on 2012-04-09
Vaphell's reply shows a great fast way's to do the copy job example you mentioned. mv is the command to move files so if you wanted to move those files, substitute mv for cp. 

You can always use man to learn lots about any command. For example:
```
man cp
```

Linux.com has some tutorials for beginners and there are lots more all over the web. Some decent looking ones to get you started:
[http://www.phas.ubc.ca/~mbelab/computer/linux-intro/html/](http://www.phas.ubc.ca/~mbelab/computer/linux-intro/html/)
[http://www.fortystones.com/40-basic-linux-command-line-tips-tricks/](http://www.fortystones.com/40-basic-linux-command-line-tips-tricks/)

I haven't tested those since it's been a long time since I learned Linux but I took a quick glance through them for you and they look good. I searched Google for "Linux CLI basics" to find them.

O'Reilly makes excellent Linux and open source print books. Linux Pocket guide, Unix in a Nutshell, and Running Linux are excellent, though I haven't read the last one myself. 

Use vim instead of vi. It's easier and much more comfortable (sudo apt-get update && sudo apt-get install vim), even for experienced users. It has lots of cool advanced features you can use when you get the hang of the basics too.


Good luck and don't get discouraged. It takes a bit of time to really learn an OS, especially at the command line but it can be a lot of fun and definitely well worth it if your job is in the technology field (even if it isn't). Once you get a good foundation down, you'll be able to learn more things quickly and you'll see how powerful and exciting Unix, bash, and all the tools that come with them really are. 


Mike

---

### Post by vegan1 on 2012-04-09
Thanks Mike, for the two links to tutorials. They look good.

Louis:guitar:

---

### Post by codemaniac on 2012-04-09
You can also find this sticky helpful in getting you started .Wish you a happy ride . :)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

---

### Post by daslinkard on 2012-04-10
The thing that has helped me the most with the Command Line Interface (CLI) has been *The Linux Command Line *by William Shotts, Jr.  

When I first came to Linux this [link]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") was provided to me to help with my learning curve.  It's free to download through sourceforge.

---

