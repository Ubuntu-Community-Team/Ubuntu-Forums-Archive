---
title: "Generic recovery mode"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by malsha on 2012-03-16
I am trying to start up my laptop in recovery mode but I don't know what I should type after ~$. I don't know what it means. When I start my laptop there is a list of different versions of ubuntu with linux such as Ubuntu with Linux 2.6.32-39 generic (recovery mode) and the regular start up thread without (recovery mode). What commands do I type in after ~$ to finish booting up the computer? I am stuck in this section of the start up and to get out I'll have to do a hard shut down and start over. Linux is too hard for me to understand will probably change back to windows. Any help would be greately appreciated. Thanks.

---

### Post by winh8r on 2012-03-16
Hi, Welcome to the forum.

In order for people to be better able to help you can you give us the following information please:

Which version of Ubuntu you are running

The make and model of your laptop

Is it running Ubuntu only or Ubuntu and Windows?

Has it booted successfully before now?



******EDIT***** there is a reply to your earlier post about the wireless issue here: [http://ubuntuforums.org/showthread.php?t=1941857]("http://ubuntuforums.org/showthread.php?t=1941857")

---

### Post by jerome1232 on 2012-03-16
What's wrong exactly that your trying to boot into recovery mode?

edit: Also When booting into recovery mode you should get a screen like the screenshot I show, do you ever get that?

btw whenever you are at that prompt you mentioned, you can type 'sudo reboot' to restart.

---

### Post by dmouck on 2012-03-16
Before everyone can provide some help, could you answer a few questions to help in troubleshooting:

what version of Ubuntu did you install?
Why are you in recovery mode? What happened to the system that you needed to enter it instead of regular mode?

Don't lose heart and go back to Windows just yet! It's a different operating system than Windows, so it can be intimidating. But if you stick with it (and with the help from the community), you will enjoy using Ubuntu :D

---

### Post by malsha on 2012-03-16
GNU GRUB Version 1.98-1 Ubuntu 13
Ubuntu 10.4  I think not sure if there were other numbers after the 10.4
I messed up something when I went into Administrator  and selected Login Screen from the list of programs I changed the settings to failsafe GNOME as default screen and now it won't unlock so can reset it to what it was before and it has also affected my ability to access my wireless.
Lenovo ThinPad R61i   802.11abg wireless, modem 1 Gb 160 Gb 5400rpm HD 1280x800, Intel x 3100 (no windows anymore HD crashed and would only read and load Ubuntu operating system)

---

### Post by malsha on 2012-03-16
I was trying recovery mode to see if I can get back the settings or get my system back to the original working condition before I went changing the login settings (I mainly went in there to try to change my login pass word) I gotta leave not I'm at work but will check in when I get home thank goodness I have a Tablet so I can access the internet from there. Thanks for replying.
@ jerome1232, thanks I tried that so now I know how to avoid doing a hard shut dwn.

---

### Post by jerome1232 on 2012-03-16
At the login screen (regular boot), there should be something you can click, or you might have to hit F10 (maybe F2?) to get a menu to select your default session. Choose the one you want (not failsafe gnome), your preference should automatically save.

(it's been awhile since I've used 10.04)

---

### Post by malsha on 2012-03-17
Thanks Jerome for replying. Having some difficulty moving around inthis forum using my android tablet. I will  try what you   suggested.   My main issue is not being able to get my computer to access the internet because the wireless signal is not automatically being pickedup by my computer anymore. Itis hard to type onthis tablet.

---

### Post by bigmonmulgrew on 2012-03-17
> **malsha said:**
> Thanks Jerome for replying. Having some difficulty moving around inthis forum using my android tablet. I will  try what you   suggested.   My main issue is not being able to get my computer to access the internet because the wireless signal is not automatically being pickedup by my computer anymore. Itis hard to type onthis tablet.

I've heard many android tablets have mouse support. You'll need a mini usb adapter of course or a bluetooth mouse

Might make things easier for you.

---

### Post by malsha on 2012-03-19
Hi bigmonmulgrew, I've been looking at the holders for my size tablet and I did see one with a keyboard. Planning to get one. I have a Pandora SuperNova 8" first time using one. Still trying to figure out how to get my laptop fixed though. Wondering if I reloaded ubuntu and started from fresh if my internet will be restored?

---

### Post by malsha on 2012-03-19
Never mind all, I got my problem solved!! I got some info from another forum thread that lead me to go search googlebuntu I typed in 'how to unlock failsafe GNOME'. From the list I chose '[[SOLVED] disable **Failsafe Gnome** and/or **unlock** login preference **...**]("http://www.google.com/url?q=http://ubuntuforums.org/showthread.php%3Ft%3D1527773&sa=U&ei=GGVnT8eWMfHisQL_p-G2Dw&ved=0CAQQFjAA&client=internal-uds-cse&usg=AFQjCNH46byffCjdq8a5MCW1XScu2-5udw") I followed thread #10 and Problem solved! Now how do I mark this discussion as solved?

---

### Post by cryptotheslow on 2012-03-19
Look above your post at the "Thread Tools" options and select mark as solved.

---

