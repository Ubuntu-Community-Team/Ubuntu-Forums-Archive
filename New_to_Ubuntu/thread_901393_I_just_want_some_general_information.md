---
title: "I just want some general information"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by pastelinux on 2008-08-26
Hi, I'm pretty new to this linux stuff and I realize that there's a lot of things one should know. I have no idea how to install flash plugin. When I went to the forums, people had a lot of weird code stuff. Could anybody get me familiar with this complicated stuff, because being a regular windows user, I don't know too much. Any information is greatly appreciated.:mad:

---

### Post by Thelasko on 2008-08-26
Usually, when you go to a website that requires flash, you should be prompted to install it.  It should walk you through it pretty easily.

If it doesn't install automatically you can go to the terminal (applications>accessories>terminal) and enter:
```
sudo apt-get install ubuntu-restricted-extras
```
That should install all sorts of software, mp3, and video codecs, and of course, Flash.  You can just copy and paste that right into the command line.  You have to use right click to paste.

PS [here's what the prompted method looks like.]("http://www.psychocats.net/ubuntu/flash")
PPS As you are new, you should probably get familiar with the [methods Ubuntu uses to install software.]("http://www.psychocats.net/ubuntu/installingsoftware")  It's much different than Windows.  If you try to install software the way you used to in Windows you could end up in trouble.  It's very simple, just different.

---

### Post by cariboo on 2008-08-26
THere is nothing complicated invovled if you want the flash plugin. Got to System-->Administration-->Synaptic Package Manager and click the search button, enter:

```
ubuntu-restricted-extras
```

Then click the search button. Once Synaptic has found the restsricted extras package mark it for installation by right clicking on the click apply.

The resticted extras will also install java and codecs that you need for playing most audio and video files.

Most of the solutions that you see that use "complicated stuff" can also be done using the default programs that are already installed. Synaptic Package Manager and Add/Remove Programs will install any thing that is available in the repositories.

Jim

---

### Post by barbedsaber on 2008-08-26
The repository's, (or repos for short) are just library's of software that you can install for ubuntu. Synaptic is like the librarian, it finds what you are looking for, and gets it all "set up for you." the best part is, you don't need a library card to use it.

---

### Post by nicedude on 2008-08-26
Quote
because being a regular windows user, I don't know too much

Man that is a really awesome quote you have there I would trademark it :-)

Sorry to be smarty pants but that one struck me really funny, To install Flash player & codecs you will need to watch various video type etc you need to add the medibuntu repositories so that you can install software from there. To do so go to the following and do what it says to do in the section "adding repositories".

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

When people give you crazy codes those are just commands to install things etc and you can just copy and paste them into a terminal window ( to open a terminal go to Applications -> Accessories -> Terminal ) and then press enter to run them. Note however when you do that you are trusting the person supplying you with the commands with your system and there are people who might suggest bad things. That said in general no-one here will do that to you and if they do the won't be here anymore but since there are allot of sources for such information be careful of commands you do not understand.

To find stuff to install after using the Medibuntu repositories adding advice from above link, just open a terminal and type "sudo synaptic" without quotes to open the synaptic package manager which is like the super add/remove programs in Ubuntu. Synaptic is searcheable by name of software or name & description with these two types of searches you can find anything you want that is there. 

Hope this info helps and welcome to Ubuntu ( sorry for joking on your statement )

---

### Post by Nythain on 2008-08-26
quick spot of advice on copy/pasting terminal commands...
google "<command> man page". You get lots of info on the command, wether or not it will be harmfull how someone is telling you to use it, and its a great way to actually learn what is doing what on the cli. :)

---

