---
title: "Help with 3rd party software installation."
date: 2008-06-16
forum: New to Ubuntu
---

### Post by comus on 2008-06-16
Hi all,

I've searched as well as I can to avoid posting unnecessarily, but couldn't find an answer to what I'm sure is the newbiest of newbie questions.

I've recently swapped over to Ubuntu 8.4 from Vista and am slowly working through the numerous training files.

My wife has bought a CD rom of kids games which she wants to install. She's double clicked on the image that appears on my desktop but all we get is a message stating that we don't have permissions to open the disk. 

I've ensured that I have SUDO rights etc.

My question is: How do I install 3rd party software from a cd/dvd onto my new system.

Really appreciate any help as my wife is already muttering about 'How easy it was with Vista!!'

Regards,

Comus

---

### Post by pedro_orange on 2008-06-16
What format are the files?

If you want to be SU when in the CD/DVD folders just open a terminal and type the following:

```
sudo nautilus
```

This will open a file browser with SU permissions. You should be able to do what you need that way.

---

### Post by bumanie on 2008-06-16
You really need to give more details re what you are trying to install ie the package name and the file type etc. It is not that ubuntu is necessarily harder, it's just that it is different - one has to learn a different way of doing things. All OSes have their good points and their not so good points. Linux does not suit everyone, but if you can give more information, someone may be able to help. By the way, if they are .exe type games made for windows they will not work on ubuntu unless you install wine. Linux has some native games - [here]("http://ubuntuforums.org/showthread.php?t=427205")

---

### Post by comus on 2008-06-16
Hi and thanks for the speedy responses.

The CD is a disk of .jpeg images from a comic. I can open them in my apple MacBook.

Thanks,

Comus

---

### Post by bumanie on 2008-06-16
Not sure about this, other than saying that ubuntu does support .jpeg  I would try to install vlc player and see if it will open in there. > sudo apt-get install vlc in terminal. The in vlc (found under Applications --> Sound and video --> vlc media player, choose file and then open disc - that may work - not sure. You may be able to view it via the gimp - again not sure, but either are worth a try.

---

