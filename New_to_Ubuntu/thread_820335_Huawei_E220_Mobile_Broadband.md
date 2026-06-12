---
title: "Huawei E220 Mobile Broadband"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by flyingmachete on 2008-06-06
Hi!

Started using Ubuntu 8.04 Desktop as a dual boot with Windows XP Pro this week and so far have been very impressed! Dabbled with various Linux distros over the years (Knoppix and the rest) and found this to be the most user friendly and easiest to install. After using Windows for so long, feels great, you still have to work out how to do things, but feel like you are learning and have more control.

Two issues: -

One is my internet connection is mobile broadband, with 3 and the Huawei E220. I have used scanmodem to find it and write the wvdial config file, then I use wvdial and then press enter at the prompt. This seems to work, but is there any programs or better ways of doing this?

Second is I have installed the latest Linux i386 driver from Nvidia, works ok, but now when using the Synaptic package manager to install programs, it keeps displaying message of "can't do sub process, removal of nvidia-glx", does anyone have any idea? 

Would be grateful for any help.

---

### Post by alexandremrj on 2008-06-16
Hello,

about the first issue you can use gnome-ppp, it's a GUI for wvdial and after you setup the connection you can create a shortcut for gnome-ppp and to connect you just go click shortcut and click connect

This thread (2ºpost) has info on installing gnome-ppp (although with a different modem)
[http://ubuntuforums.org/showthread.php?t=763122](http://ubuntuforums.org/showthread.php?t=763122)

About the second issue I'm sorry but can't help you.

---

### Post by Fingers &amp; Thumbs on 2008-06-22
Hi flyingmachete,

 Regarding your modem, I've just writen a beginners HOWTO to get it up and running you can find it at [http://ubuntuforums.org/showthread.php?t=836918]("http://ubuntuforums.org/showthread.php?t=836918")

Now I'm wondering, what graphics card are you using, it's possible you want nvidia-glx-new, instead of nvidia-glx, but I wouldn't worry too much that it's saying "can't remove" as without one you would have graphical issues.

I would always recommend installing software via apt, or synaptic over dowlnoading. You seem to suggest that you d/loaded from nvidia's site. I'm not an expert, but as I understand it, if you install from repositories, then apt/synaptic will take care of adding/removing for you, anything installed by other means and your on your own as far as apt is concerned.

Hope this helps

---

