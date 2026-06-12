---
title: "help"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by eilyn on 2008-09-23
I am going mad, it seems that i can't do anything with this programs/system, i just dont know what i am doing wrong!!!!! i need help somebody please could provide me with acurate info, i cant install u torrent (i did it through wine and is not working) I can't use/set wireless connection, in terminal thing i can change anything or enable programs, so as a result i dont know what else to do and i am frankly really tired, i do believe in the conception of free software beside i dont have Microsoft, i keep looking in the forums and i try to set a key thing which seems to not be working neither so i dont know what else to do, i just want to be able to use my computer normally, without the whole hassle but it seems that is impossible even to get starting with this. So if you could please help me i will be really grateful since i dont know what else i can possible do.

---

### Post by eilyn on 2008-09-23
I am going mad, it seems that i can't do anything with this programs/system, i just dont know what i am doing wrong!!!!! i need help somebody please could provide me with acurate info, i cant install u torrent (i did it through wine and is not working) I can't use/set wireless connection, in terminal thing i can change anything or enable programs, so as a result i dont know what else to do and i am frankly really tired, i do believe in the conception of free software beside i dont have Microsoft, i keep looking in the forums and i try to set a key thing which seems to not be working neither so i dont know what else to do, i just want to be able to use my computer normally, without the whole hassle but it seems that is impossible even to get starting with this. So if you could please help me i will be really grateful since i dont know what else i can possible do.

---

### Post by Tatty on 2008-09-23
Hi eilyn,

Your post is rather confusing, lets try to separate it out.  It may help for you to rename this thread to something more relevant to your issues.

It also helps to try to stick to "one problem per thread", as it can get confusing in threads where different people are trying to troubleshoot different issues.

So as i understand it, your problems are:

1. Utorrent is not working in wine
2. Wireless connection is not working
3. General installation issues.

First lets sort out your installation issues:

Do you have an internet connection in your ubuntu install currently?

What happens when you try to install software?  
Do any error messages appear, and what are they?
Have you read this guide to installing software in Ubuntu?
[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

### Post by Kain000 on 2008-09-23
Alright so your trouble is installing U-torrent?

U-torrent is a windows app and will only "work" in wine.. if work is what you call it. lolhttp://ubuntuforums.org/images/smilies/smiley-faces-75.gif

Why put yourself threw all those hoops trying to configure that under wine when there are PLENTY of linux torrent apps that you can choose from.  Personally I like azureus because you can tell it to encrypt it's transfers with RC4.    If your looking for a lightweight and efficent torrent and not so much worried about encryption just use the default app that comes with ubuntu, transmission is very handy and it needs very little configuration.  Just do a google search for linux torrent apps and look arround.  see what you like.
You may be interested in this thread
[http://ubuntuforums.org/showthread.php?t=232673](http://ubuntuforums.org/showthread.php?t=232673)
they discuss different torrent apps.

Also if your heart is set on U-torrent check this out and it should get you up and running.
[http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml](http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml)

---

### Post by phidia on 2008-09-23
Computer problems can be frustrating. So if you choose to maybe take some deep breaths and get a cup of tea or something else soothing.

What version of Ubuntu do you have installed? What kind (make, model and hardware) is Ubuntu installed on? Did your install of Ubuntu ever work correctly or has it always been a big pain? 

You should be able to use a linux native torrent application like transmission-just open System > Administration Synaptic Package Manager and search for "torrent".
Programs installed in wine can sometimes be hard to configure/get working.

You can use the [Ubuntu wiki]("https://help.ubuntu.com/community/") and it's search feature to look up other things you are having problems with. 

Just a suggestion but it's probably best to open a thread for each problem you have rather than lump them all together.

---

### Post by cariboo on 2008-09-23
In stead of using programs that aren't designed for the system why not use native programs. Deluge is a good replacement for &#371;Torrent. It is available in the repositories, you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

We have to know what type of wireless card you have to be able to solve your problem. In a terminal type:

```
lspci
```

And paste the results in your next post.

If you browse Add/Remove Programs with All Available Programs selected you will find more programs then by searching the various download sites you usually browse.

Remember Linux is not Windows, so most of the windows programs you are use to using will not work. There are plenty of Linux programs that have the same functionality as their windows equivalents. If you can't find something you can always ask here in the forums.

Jim

---

### Post by twitch2197 on 2008-09-23
in the future, you'll probably get better (and faster) replies if you give a descriptive title.
also, it helps to either break the questions up, with some white space... or ask in seperate threads.

for your answer... i use transmission bittorrent client. it works natively in linux and is provided in the synaptic package manager.

i suggest you ask about the wireless in the wireless/networking forum. you'll get answers from some 'specialists' there, who can walk you through it.

---

### Post by issih on 2008-09-23
Ok, Linux isn't windows, and the best bet is always going to be to find a linux native app that will do what you want...Try opening up add/remove from the main menu and searching for torrent...there are loads of them available.

Wireless is a known issue, unfortunately the hardware manufacturers do not provide support for linux in the same way they do for windows, so quite often getting wireless working is a chore, but it is usually possible, either by installing new drivers or using ndiswrapper, either way we'd need to know the make and model of your wireless hardware to help there.

As for the rest of it, I'm afraid there is a learning curve, things do not work exactly the same as in windows...Ubuntu is not a direct drop in replacement, and never claimed to be...It is an entity in its own right, and you have to learn its ways, but don't worry, it is actually pretty easy to get the hang of, and in many cases is actually more logical than windows...you just have to get used to it, and unlearn your bad habits.

---

### Post by alzie on 2008-09-23
It sounds like you have information overload.

When I use windows I use uTorrent but it isn't available on Ubuntu (yet).  You do have a Torrent program already (if you have Hardy Heron) called Transmission.  

Try under Applications>Internet

I found that it works best (for me) to select the torrent I want,  save to desktop then double click to start the torrent.

I'm afraid I can't help you with the wireless issue but if you post in the [Absolute Beginners Forum]("http://ubuntuforums.org/forumdisplay.php?f=326") someone should be able to help you.  It will help if you can include information about your computer,  the make and model, type of wireless card and so on.

It looks like you've already found the terminal,  you may be offered commands to copy and paste into the terminal to get information that will help them to help you.

I hope this helps some.

edit:  I've found psychocats tutorials to be very helpful if I run into any problems, You'll find that here: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Nano Geek on 2008-09-23
It would also be best for you to ask each question is a separate thread. Also try to give us as much information as you can such as what hardware you have, error messages, that kind of thing. 

Good luck with your problems.

---

### Post by cariboo on 2008-09-23
The OP double posted this. The other post is in Absolute Beginners here:

[http://ubuntuforums.org/showthread.php?t=928054](http://ubuntuforums.org/showthread.php?t=928054)

Jim

---

### Post by Rocket2DMn on 2008-09-23
Threads merged, please do not create duplicate threads, it's not fair to those helping you.  Thanks.

---

