---
title: "given up"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by buzbyx on 2012-11-27
I was never able to transfer my data and programs from 11.10 to 12.04, so I was just working in 11.10...until today's update, which made my machine unable to boot back into 11.10.        does anyone know a simple, clear, and straightforward way to access my 11.10 desktop from 12.04?     I can't find the other desktop folder in the file system at all

thanks for your help


OH and I don't just need to LOOK at the old desktop, I need to move a file to the new desktop...

---

### Post by audiomick on 2012-11-27
Tell us a little more about the machine, please.

The way I read your post, you have both 11.10 and 12.04 installed on one machine, the 11.10 install is now broken but you can still boot into the 12.04. From 12.04, you can't see the partition where the data from 11.10 is. Is this correct? If not, please fill us in on the details.

Also, tell us a little more about "can't boot into 11.10". It is possible that this might be able to be repaired too.

---

### Post by buzbyx on 2012-11-27
first off, thanks for your kindness.    the 11.10 partition is visible and all the accoutrements of 11.10 seem to be there except the actual desktop file...it isn't in the home folder on the old system

I tried to do ctrl-h but all it brought up was .cache and .gnome with nothing I needed in either directory

---

### Post by audiomick on 2012-11-27
> **buzbyx said:**
> ... the actual desktop file...it isn't in the home folder on the old system

I gather you mean the folder called "desktop". Don't mean to be picky about terminology; I just want to be sure we are talking about the same thing.

Where that folder should be is /home/username/desktop.

You shouldn't need to use ctrl+h to see it, as it is &#324;ot a hidden folder/file. I gather you can get in to the /home/user folder on the 11.10 install, not just into /home ?

---

### Post by buzbyx on 2012-11-27
I'm in the /home/(11.10 user) folder right now and it's got nothing in it except .cache and .gnome2

---

### Post by buzbyx on 2012-11-27
is it possible that I cleverly chose some sort of idiotic encryption option offered me when I installed 11.10, thereby slicing off my own balls a year ago and not even knowing it?

---

### Post by crocodile-mick on 2012-11-27
Have you tried updating your grub2 from within the 12.04? Open a terminal and type sudo update-grub. Enter your password if requested. Grub should scan your computer and pick up the 11.10 version. Once the grub2 is updated reboot your computer and you should see a selection there for the 11.10 version. Hope this helps.

---

### Post by buzbyx on 2012-11-27
first thing I tried, brother.  thanks though

---

### Post by audiomick on 2012-11-27
> **buzbyx said:**
> is it possible that I cleverly chose some sort of idiotic encryption option offered me when I installed 11.10, thereby slicing off my own balls a year ago and not even knowing it?

That is not impossible, but I think not likely.

It is possible you have a permissions problem, although I am guessing. The whole thing sounds a little odd. What I would try next is an instance of Nautilus, the file manager, with root privileges. To get that
```
gksudo nautilus
```
in a terminal. 

Navigate to the /home/11.10username folder with that and see what you can see. 

As far as the suggestion to use "update-grub" to try and repair the boot, I am not sure that this works if you are not executing it from in the install that put the grub there, but I could be wrong. Anyway, if you want to try and repair the boot, I would suggest looking at this

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

It may be able to repair the boot, and if not, it will generate a listing of the state of affairs regarding the boot process and a lot of other useful stuff about the state of the computer.

One thing at a time, though.

---

### Post by buzbyx on 2012-11-27
thanks michael.  nautilus shows me only the two aforementioned folders, along with a broken link to a file called .ecryptfs, which kind of confirms my self-mutilation hypothesis.

I will try your link to the boot repair.  maybe I'll get lucky

---

### Post by buzbyx on 2012-11-27
michael, your link to boot-repair was just the ticket.   not only am I booted in, but I'm finding wherever I might've put my encryption password and emailing it to myself.  I will also strive to be a better man from now henceforth.

I will build a metaphorical shrine to your kindness, and if I ever attain super powers, you will be safe.


thank you.

---

### Post by audiomick on 2012-11-27
> **buzbyx said:**
>  I will also strive to be a better man from now henceforth.

Good lad. Glad I could help. I, for my part, will use your experience as motivation to finally get around to instigating a useful regular backup procedure.:-\"

---

### Post by YannBuntu on 2012-11-27
If your problem is solved, please could you use the Thread Tools in order to mark it [SOLVED]

---

