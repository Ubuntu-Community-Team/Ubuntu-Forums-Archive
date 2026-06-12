---
title: "lubuntu booted once, crashed, won't boot again"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by lcooper145 on 2012-12-10
Hello,
I just installed ubuntu from wubi and got it to boot the first time. However, it couldn't find my wireless network and immediately crashed when I clicked "system tools" (or was it "system preferences"?) I restarted with ubuntu and I got a black screen, which flashed twice as if it was about to load, but never did.

I restarted again with windows 7 and uninstalled ubuntu, and installed lubuntu with wubi again (thinking I was just using too much memory with ubuntu or something...my computer is sort of considered a "netbook.") Well, lubuntu booted up fine the first time it came up after installing it. But then, although it did recognize my wireless network, it said I needed to type in a password, even though my network doesn't require a password. Then, I went to "system tools" again in the start menu, and lubuntu crashed there too.

What's going on? How can I fix it?

I'm trying to dual boot with Windows 7 on an acer aspire one 722.

Thanks for your help, in advance.

EDIT: I fixed the wireless problem. It was my own fault.

New problem: I fixed the blank screen by using nomodeset in the boot up screen. Now I'm trying to "install a graphics driver," which apparently was the problem? I don't know how to do this, though. I went to this forum:

[http://askubuntu.com/questions/74171/is-my-ati-graphics-card-supported-in-ubuntu](http://askubuntu.com/questions/74171/is-my-ati-graphics-card-supported-in-ubuntu)

and followed the directions, but whenever I try to type in "sudo apt-get" anything, I get an error message.

---

### Post by Wim Sturkenboom on 2012-12-11
> **lcooper145 said:**
> 
EDIT: I fixed the wireless problem. It was my own fault.
what did you do wrong? Others might have the same problem and can learn from it.

> **lcooper145 said:**
> 
... but whenever I try to type in "sudo apt-get" anything, I get an error message.It does not help to state that you get an error message; there are possibly a few hundred of them. Please provide full command and full error message (you can copy and paste from terminal).

---

### Post by lcooper145 on 2012-12-11
Sorry, here's the error message:

```
sudo: parse error in /etc/sudoers near line 31
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
```

I think that happened after I changed the /etc/sudoers file to include

```
username (ALL)=ALL NOPASSWD (ALL)=ALL
```

Sorry, it's late, that might not be the exact code that I did. I wanted to make it so I didn't have to type my password into terminal because it was telling me my password was wrong for some reason. 

I first noticed the error when I typed this:

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
```

while trying to install a graphics driver (I told you I have no idea what I'm doing, I've just been trying to make lubuntu usable for the past eleven hours),

although I got the same message when I typed

```
sudo apt-get install gpointing-device-settings
```

while trying to somehow get auto-click to stop (I can't find Universal Access or any relevant mouse settings)

---

### Post by lcooper145 on 2012-12-11
Re: the wireless thing, I realized that "password" was just asking for my own ubuntu password. heh.

---

