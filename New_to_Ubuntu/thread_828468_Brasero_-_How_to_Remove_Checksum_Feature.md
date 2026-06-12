---
title: "Brasero - How to Remove Checksum Feature?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by felicity on 2008-06-13
The Hardy version of Brasero seems to have a feature I don't recall being there before of making a checksum for the data to be burnt. While it ejects the disc afterwards and hence allows me to cancel checking the burnt data integrity, it appears to take much longer to start burning the disc due to making the checksum.

I've gone to the Edit, Plugins menu but when I uncheck the boxes next to the plugins and close the dialog box, then reopen it, Brasero has automatically rechecked them. 

Does anyone have any ideas for fixing this problem? Is it just my imagination that it's much slower now? 

Thanks! :KS

---

### Post by SunnyRabbiera on 2008-06-13
well it checking the checksum is a very important step, but if you need an alternative to brasero try k3b, it works better anyway.

---

### Post by Sef on 2008-06-13
> Is it just my imagination that it's much slower now?


I don't find it slower on my system; however, on your system it may run slower.

---

### Post by felicity on 2008-06-13
Thanks. It just seems like when I used to burn a disc with Brasero, it would start burning right away. Now the dialog box comes up that it's making a checksum and five or ten minutes pass before it starts to burn the disc. 

k3b is nice, I've used it before, but I prefer to stick to a gtk burning application, preferably Brasero if I can figure out why it's taking longer than it used to.

---

### Post by alienexplorers on 2008-06-13
You could try gnomebaker which I use to burn CD's & DVD's.

---

### Post by isaacj87 on 2008-06-13
> **felicity said:**
> Thanks. It just seems like when I used to burn a disc with Brasero, it would start burning right away. Now the dialog box comes up that it's making a checksum and five or ten minutes pass before it starts to burn the disc. 

k3b is nice, I've used it before, but I prefer to stick to a gtk burning application, preferably Brasero if I can figure out why it's taking longer than it used to.

Hey,

I can understand your reasoning for sticking with Brasero. I actually like the app. I was poking around in the menus...Perhaps disabling the checksum plugin in the plugins menu could solve the your issue?

It's in Edit->Plugins

---

### Post by Vivaldi Gloria on 2008-06-13
> **felicity said:**
> I've gone to the Edit, Plugins menu but when I uncheck the boxes next to the plugins and close the dialog box, then reopen it, Brasero has automatically rechecked them. 

This worked for me, don't know why it doesn't work for you. Alternative method:

1. Start gconf-editor

2. Goto > apps > brasero > config and double click on plugins.

3. Remove md5 related plugins.

This should do it.

By the way, I think md5 plugins are better disabled by default.

---

### Post by felicity on 2008-06-14
isaacj87: Thanks but I already tried unchecking the plugins.

Vivaldi Gloria: Hmm, that is strange that it works for you and not me. I tried your good idea for gconf-editor, but unfortunately even when I delete entries from the plugin list, when Brasero is started the plugins are still there, checked, and when I go back to gconf-editor the entries for the plugins have been re-added. :confused:

alienexplorers: I might have to resort to gnomebaker if I can't get this figured out. It's not a huge deal, but if Brasero is the default burning program in Hardy I'd like to figure out what this bug, if it is one, is, and how to fix it. :-k

---

### Post by prshah on 2008-06-14
> **felicity said:**
> The Hardy version of Brasero seems to have a feature I don't recall being there before of making a checksum for the data to be burnt. 
Does anyone have any ideas for fixing this problem? 


Just a note: From your previous posts, I assume that you've been using hardy since it's beta days; is it fully updated and current?

---

### Post by felicity on 2008-06-14
prshah: No I never used the beta, I downloaded and installed a fresh copy of the final release (not an upgrade) and it's fully updated with all the current updates - Thanks for your help though!

---

### Post by isaacj87 on 2008-06-14
> **felicity said:**
> isaacj87: Thanks but I already tried unchecking the plugins.

Vivaldi Gloria: Hmm, that is strange that it works for you and not me. I tried your good idea for gconf-editor, but unfortunately even when I delete entries from the plugin list, when Brasero is started the plugins are still there, checked, and when I go back to gconf-editor the entries for the plugins have been re-added. :confused:

alienexplorers: I might have to resort to gnomebaker if I can't get this figured out. It's not a huge deal, but if Brasero is the default burning program in Hardy I'd like to figure out what this bug, if it is one, is, and how to fix it. :-k

Doh! Sorry, that'll teach me to pay attention better. I'm going to try something else and I'll get back to you. :)

---

### Post by felicity on 2008-06-17
isaacj87: It's OK no problem.

I installed GnomeBaker, it's actually nicer than I remembered it being. One immediate thing I liked better in GnomeBaker than Brasero is how it fully integrates the color scheme I use in Gnome; Brasero has that bright white screen when you go to add files to it and I can't stand bright white on my computer screen.. my poor eyes! So I think I'll stick with GnomeBaker for now. 

:popcorn:

---

### Post by Farmer_Fred on 2008-08-19
the checksum business takes around 5mins on my pc on hardy, the latest edition, that is. Gets there in the end

---

### Post by IGITIHI on 2008-09-05
I also face the same problem; even though I try to deactivate the md5-related plugins by unchecking the appropriate boxes in the plugin menu, brasero still performs the integrity check and the boxes become checked again.

---

### Post by aoakley on 2011-01-01
Thanks for the tip on turning of checksums in Brasero.

Someone asked why you would want to do this - my answer: Because the files I'm burning are on a relatively slow remote NFS share, maximum throughput 8 megabytes/sec. Since this is slower than the maximum DVD burn speed, this means that having checksum turned on makes it take twice as long to burn a DVD!

---

### Post by kwikshot on 2011-05-04
The checksum for me takes longer than the actual burning most of the time

---

### Post by bad killer on 2011-05-04
I have problem with edubuntu it refuse to play music....

---

