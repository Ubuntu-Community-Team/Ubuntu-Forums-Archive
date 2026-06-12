---
title: "sooo frustrated"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by rickf18 on 2008-09-28
i have ubuntu 7.10 installed (dual boot with vista) and had been very happy with it until , after a year, i still can't do some things and other problems have cropped up.

i use an acer aspire 5100 notebook

i want to get beryl/compiz working (ati radeon xpress 1100)
virtual box stopped working (after a kernal lib upgrade)
firefox looses my bank card info (to log into webbanking) regularly

please help, linux feels more like home now, but is also very frustrating

i have MS and need vista to use dragon naturally speaking

---

### Post by brunolabs on 2008-09-28
Give the latest Ubuntu version (8.04.1) a try.

---

### Post by lian1238 on 2008-09-28
I have an Acer Aspire 5580 and my wireless doesn't work on 8.04. You might want to try the LiveCD first, before installing.

My wireless model is:
Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by panhandle on 2008-09-28
> i want to get beryl/compiz working (ati radeon xpress 1100)

see this thread for starters, though I recommend understanding your actions and commands as much as possible: 

[http://ubuntuforums.org/archive/index.php/t-557905.html](http://ubuntuforums.org/archive/index.php/t-557905.html)

> virtual box stopped working (after a kernal lib upgrade)

see this link: [http://ubuntuforums.org/showthread.php?t=472658](http://ubuntuforums.org/showthread.php?t=472658)
Virtual Box possibly needs to be reconfigured.

> firefox looses my bank card info (to log into webbanking) regularly

What version of FF are you using? If 3.0, go to Edit-->Preferences-->Security tab-->check "Remember passwords for sites"

Do you consistently clear all private data?

---

### Post by rickf18 on 2008-09-29
well,

updating to ubuntu 8.04 didn't help
still can't use compiz, when i try to activate visual effects, it mentions something about composite and doesn't respond
virtualbox is gone altogether
firefox (now 3) still loosing numbers

am going to try delving into the other suggestions, as i mentioned, i have ms and dont do anything quickly, please be patient

---

### Post by hyper_ch on 2008-09-29
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by starcannon on 2008-09-29
Just to check:

Have you run the "Hardware Drivers" utility? If you didn't know about it, you can find it in:
{System>Administration>Hardware Drivers} , am betting your ATi Drivers are available in there, be sure that the little check box is selected (it may say enabled even when its not, be sure the check box is selected) 

It will likely do some downloading and ask you for permission to install things, then ask you to reboot when its done. If all goes according to plan you should reboot into a desktop capable of compiz effects. 

You will likely need to reinstall VirtualBox, though your windows or other drives that you created previously should still be accessible once VB is reinstalled, you may find that you need to do this anytime you get a new kernel.

GL

---

### Post by starcannon on 2008-09-29
Okay, well, lets work on one project at a time. I get lost otherwise.

1st: Have you gotten compiz working? If I recall that was what we started out working on.

if so please mark this thread as solved, and open a new thread for a new problem, be sure to follow hypers advice and give you thread title a good name.

---

### Post by rickf18 on 2008-09-29
i agree, i think that i should begin over with one message thread and one problem. thank-you to all who replied.

---

### Post by LowSky on 2008-09-29
> **rickf18 said:**
> well,

updating to ubuntu 8.04 didn't help
still can't use compiz, when i try to activate visual effects, it mentions something about composite and doesn't respond
virtualbox is gone altogether
firefox (now 3) still loosing numbers

am going to try delving into the other suggestions, as i mentioned, i have ms and dont do anything quickly, please be patient

You need to install ATI Graphics drivers, try using Envy (from Repos)
VirtualBox needs to be reinstalled/reconfigured
FF3 might not be the culprit, many websites are now designed to delete your info so that hackers and other users of the computer have no access to you private data. I know for a fact that Amex's website doesn't save my data. If you think FF3 is an issue than look at the privacy settings, if you set them to delete cookies and personal data then that would cause the issue.

---

### Post by rickf18 on 2008-10-01
ok, i have and always had the/an ati driver installed. the one envy picked for me doesn't work either. wit it i couldn't shutdown (blank blue screen), had to do alt f2 and shutdown -r . i am presently using the latest one from ati's website. i have seen all kinds of things that say that the radeon xpress 1100 will not even work with compiz. now i'm confused.

---

### Post by Terl on 2008-10-01
My laptop has the same card and I am running compiz just fine.  I just used whatever the restricted drivers manager gave me.  I am using Ubuntu version 8.04

---

### Post by rickf18 on 2008-10-01
ok, have switched to restricted driver, now what. i must be missing something

---

### Post by rickf18 on 2008-10-03
restricted driver caused every video i play to crash linux.
when i try to enable desktop effects a dialogue box says they can't be enabled. man, this is hard!

---

### Post by Kartoffelbursche on 2008-10-03
Dont be so frustrated... i was trying 3 days straight to get my wifi working on my acer aspire one... finally i got it running and i am new to ubuntu!

I will try all the other stuff in linux also (network, ftp, email ...etc) once i am used to it, i can change my main system as well... the acer is my so called "Try to change Project" :-)

So, cross your fingers... maybe in a few weeks i can say goodbye to microsoft :-) no more registrations, validations and codes etc.... 

I will cross my fingers for you!

---

### Post by rickf18 on 2008-12-07
ok, i upgraded to 8.4 and no go but ... i upgraded from 8.4 to 8.10 and went to system/administration/hardware driver activated the appropriate ati
and voila i am cubing.

---

