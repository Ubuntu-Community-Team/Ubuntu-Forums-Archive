---
title: "Unable to activate SCIM in 11.10"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by swarup on 2011-10-20
Just installed 11.10, and have installed SCIM and SCIM-m17n, for typing in Hindi. But all the usual tricks I use for activating SCIM on a newly installed distribution, are not working. Went into SCIM setup, set the keyboard type etc and the trigger, and set the icon to show "always", and logged out and back in. Even shut down and booted back up. When I open gedit and do ctrl-space, SCIM does not activate. No sign of life. Any ideas, how I can get SCIM to activate?

---

### Post by swarup on 2011-10-20
Sorry to "bump"-- has anyone used SCIM yet in 11.10? Does it work?

---

### Post by osg on 2011-11-06
I had the same problem for several weeks now. After hours of trial and error, and reading old documentation, I added the following command to my startup applications menu:

ibus-daemon -dr

To add the ibus daemon to your startup applications in Ubuntu 11.10:

1. In the upper right-hand corner of your screen, click the little "Settings wheel" that is to the right of your username.
2. Select Startup Applications.
3. Click Add and fill in the command field with the following path:
   /usr/bin/ibus-daemon -dr
   If this path is incorrect, you can find the correct path by using the command $ type ibus-daemon.
4. Click Save and log out and log back in.
5. Start scim.

(I also added scim to my list of startup applications.)

To change your input method for Google Chrome, right-click to select Input Methods --> IBus (Intelligent Input Bus).

This right-click method might work for other applications too, but I have not tried.

I hope that helps!

---

### Post by swarup on 2011-11-08
Thank you very much-- I will try this and report back.

---

### Post by swarup on 2011-11-08
Fantastic! Worked great! You're a life-saver. :)

The default set through ibus just working right. The Hindi letters were getting splayed all over the page, irregularly, instead of grouped together in words as they are supposed to be. Now with SCIM installed, it works perfectly.

---

### Post by kevindewalt on 2011-11-28
> **swarup said:**
> Fantastic! Worked great! You're a life-saver. :)

The default set through ibus just working right. The Hindi letters were getting splayed all over the page, irregularly, instead of grouped together in words as they are supposed to be. Now with SCIM installed, it works perfectly.

Hey guys, appreciate this great writeup but unfortunately it didn't work for me.  Still getting no response, trying to get chinese character input. 

screenshot attached.

---

### Post by grahammechanical on 2011-11-28
@kevindewalt

The other day I was trying to help someone on Askubuntu to set up a Korean layout. It turns out that the usual method does not work. Now I know that you want Chinese not Korean but stay with me.

The answer was to install ibus-hangul support (hangul = Korean script) and then install through the Ubuntu Software Centre Keyboard Input Methods.

This Keyboard Input Methods utility puts another keyboard icon in the top panel the menu of which has a preferences option which lets you choose the input method. There are two Korean and Chinese. You need ibus to be activated. This might work for you.

I have also found this link for you. Note the link near the top of the page Ubuntu 11 Chinese Setup.

[http://www.pinyinjoe.com/linux/ubuntu-10-chinese-input-pinyin-chewing.htm]("http://www.pinyinjoe.com/linux/ubuntu-10-chinese-input-pinyin-chewing.htm")

Regards.

---

### Post by kevindewalt on 2011-11-28
@grahammechanical

Thanks for your reply, funny I was working through the same article when I received your response.  Unfortunately I cannot get past the No input window problem.  I'll try installing korean, but I don't really see why that would help. 

See screenshots attached...

---

### Post by kevindewalt on 2011-11-28
ok...getting somewhere...after reading [through this articl]("http://www.pinyinjoe.com/linux/ubuntu-11-chinese-setup.htm")e I realized I cannot select a keyboard input method system.

The drop-down menu is greyed out, I cannot select ibus or anything.  

See screenshot.

Suggestions?

---

### Post by kevindewalt on 2011-11-28
ok seems to be working after re-installing parts of ibus and restarting.  &#23545;&#19981;&#36215;&#35874;&#35874;thanks and sorry for the many posts.

---

### Post by EthioJOB on 2012-03-29
Have you tried going into 

for Ubuntu 11.10, Unity Dash > installed softwares > Input method switcher

for ubuntu 10.10, System > Preferences > Input method switcher



and then mark "Use SCIM via xim (scim)"

log out and then log in again, and try pressing Ctrl+Space to switch between languages.

---

