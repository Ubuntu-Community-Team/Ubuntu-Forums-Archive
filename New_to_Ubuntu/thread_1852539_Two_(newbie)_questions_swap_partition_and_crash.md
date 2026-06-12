---
title: "Two (newbie) questions: swap partition and crash"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by primvirlaux on 2011-09-30
Hey.

I'm more or less a total newcomer to Linux. I installed Lubuntu yesterday, on my Asus X101 netbook. Two questions:

1) When I installed Lubuntu, I selected 'advanced' setup (or whatever the exact name is) to decide on my own how to partition my HD. However, I wasn't sure how to actually make a swap partition. In the installation settings, I was able to select under 'mount point' "/" and "/home", but it said nothing like "swap". Under the selection 'file system' I found something that mentioned 'swap', so I used that. My system seems to be running okay, but my question: How can I find out if the swap partition is used correctly?

2) I don't know if it's a bug or my mistake, but when I open, under preferences, 'keyboard and mouse' settings, a small window opens, but as soon as I change a setting in it, the window seems to crash. The first time it happened some report came up, asking me if I want to report the problem, but since then, the crash persists but that question doesn't show up anymore. Anyone has any idea what could cause the problem?

3) EDIT: another question: assuming I get the 'keyboard and mouse' settings window to work, is there a way to configure in more detail the mouse/touchpad. The default settings window allows me change the sensitivity and speed, but that's about it. Is there a way to configure the touchpad in more detail, like enabling/disabling gestures or set parametes for tap-for-left-click, stuff like that? Like I said, I'm new to Linux, so I don't know where to look for something like that...

---

### Post by Elfy on 2011-09-30
Open a terminal - then run 

```
free -m
```

If the swap row is not at 0 then you have some. 

You can see if it's set to mount by looking at fstab - this file tells the system what to mount on boot.

In a terminal again - 

```
cat /etc/fstab |grep swap
```

Running xubuntu so I've no idea what the keyboard/mouse tool's called, if you can find the name you can run

ubuntu-bug *nameofapplication*

Not using touchpad either - but this is a search on an ubuntu search engine for touchpad and the wiki page for it- have a look

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

[http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=touchpad](http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=touchpad)

---

