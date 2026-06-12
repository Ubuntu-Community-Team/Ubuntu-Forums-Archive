---
title: "[SOLVED] what does core dumped mean?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by beanco on 2008-05-21
i been having problems with FF, evolutin and epiphany

getting segmentation and/or core dumped errors.

now I tried to run synaptic from menues, does not launch and from the command line and i got this

Segmentation fault (core dumped)

what up with this?

robi

---

### Post by stchman on 2008-05-21
> **beanco said:**
> i been having problems with FF, evolutin and epiphany

getting segmentation and/or core dumped errors.

now I tried to run synaptic from menues, does not launch and from the command line and i got this

Segmentation fault (core dumped)

what up with this?

robi

When that happens that usually means that an array in the program exceeded it's size and tried to write in protected memory.  The OS does not let the program do this and therefore the program dumps it's core.

---

### Post by EndPerform on 2008-05-21
> **beanco said:**
> i been having problems with FF, evolutin and epiphany

getting segmentation and/or core dumped errors.

now I tried to run synaptic from menues, does not launch and from the command line and i got this

Segmentation fault (core dumped)

what up with this?

robi

Something is wrong with the program you're attempting to run.  A core dump contains information useful for developers to debug exactly where a program aborted.  Have you done anything to your system lately?

---

### Post by Frak on 2008-05-21
Hmm... How much RAM do you have?

---

### Post by pdtpatrick on 2008-05-21
Like our colleague mentioned above - the core dump is information used by a developer to troubleshoot your computer problems. However, i would check your log files and see what you have installed recently that might be causing the problem. If you find the problem, I would uninstall the program and try using your computer again and see if the problem persists.

---

### Post by beanco on 2008-05-21
ok thanks for all the ifo.

I am a bit of a noob so not sure how to read the system logs. I have not installed anything I can remmeber but I will look...

nope, i  looked but do not understand a darn thing it says.

oh, and I am on feisty BTW


Robi

---

### Post by Cypher on 2008-05-21
How recently have these issues start to come up? Having released applications like FF, evolution and others seg fault means that something very basic is broken in the system.

In the GRUB Menu during boot you have an optiong for "Ubuntu, MemTest86+". You might want to run that test to see if there are any issues with your installed memory.

---

### Post by beanco on 2008-05-21
> **Cypher said:**
> How recently have these issues start to come up? Having released applications like FF, evolution and others seg fault means that something very basic is broken in the system.

In the GRUB Menu during boot you have an optiong for "Ubuntu, MemTest86+". You might want to run that test to see if there are any issues with your installed memory.

started on the weekend.... there was the *your system has been booted 30 times...* or whatever it says... I tried to take care of it and things have gone down hill since... It was up and running for a few hours. then this...

I will reboot and look for the test you mention.... 

robi

---

### Post by beanco on 2008-05-21
ok.  i started the run the check but i do not have the time to wait for it now. I waited 15 minutes but it was not finished.

how long does it normaly take?

is it a matter of minutes or hours?

thanks

robi

---

### Post by Cypher on 2008-05-21
The "you've booted 30 times" deals primarily with the HDD to ensure that all the files are OK. That shouldn't necessairly cause any problems with the applications..

The MemTest86+ can take a while..depending on the amount of memory you have, an hour or more wouldn't surprise me. So I'd run it before you go to bed or something and check up on it in the morning..

---

### Post by bumanie on 2008-05-21
Hi Beanco,
A memtest takes a number of hours to do it properly.

---

### Post by beanco on 2008-05-21
> **bumanie said:**
> Hi Beanco,
A memtest takes a number of hours to do it properly.

hey bumaine,

do I need to be present? or can I start it and go to work in the morning and check it when I get home 12 hours later?


robi

---

### Post by Cypher on 2008-05-21
You don't have to watch it run..it will give you a report when it's done..so let it rip when you're not going to be using the machine for a few hours..

---

### Post by Frak on 2008-05-21
I'd still like to know how much RAM you have in your machine.

---

### Post by beanco on 2008-05-22
> **Frak said:**
> I'd still like to know how much RAM you have in your machine.


oops, forgot to check and I do not know it off the top of my head.

I will check when I get home tonight.

right now the memtest is running BTW.


robi

---

### Post by beanco on 2008-05-22
> **Frak said:**
> I'd still like to know how much RAM you have in your machine.

503.9 i think


and the memtest did not run because there was a serious power shortage/outage while I was away.

i will run it tomorrow.

robi

---

### Post by beanco on 2008-05-23
justhow long does the memtest take_

I left home afte rit had been running 6.5 hours and it was still going.

it seems to have found 2 errors. at least there is a red stripe at the bottom with some text in it .... I have no idea what the text means though.

when I get home in a few hours I will look at it ..

robi

---

### Post by Sunfist on 2008-05-23
First if you only have 512megs of ram like you think you do it should have been done in a lot less than 6 hours. Second if you have frequent power outages, brown outs where you live its very possible your data got corrupted on your HD if a program was writing to the HD when one of these events occurred, or the HD itself could have gotten damaged.

---

### Post by bumanie on 2008-05-23
Memtest 86+ will run basically indefinitely. It is inadvisable to allow it do  more than one pass however, as often errors will show up after extended use and won't be picked up in the first pass. It is not uncommon for memtest to be run overnight, so as to allow a number of passses and to provide 'real use' conditions, as most often computers will be used for a number of hours at a time. If you have done a number of passes, the first thing to do is to try a new ram module - borrow a known good module (if possible) to see if that cures your computer problems/core dump issues. If not it may that it is some other component causing the problem. Of course if it is the borrowed ram works, give back the borrowed module and buy yourself a new one. If the ram seems to be OK, it is really trial and error to track down the problem in other components.

---

### Post by Frak on 2008-05-23
And if your RAM does happen to be bad, this is the part of your system that isn't a worry to go out as RAM prices are falling through the floor. (2GB in my system for around $30)

---

### Post by beanco on 2008-06-01
> **Frak said:**
> And if your RAM does happen to be bad, this is the part of your system that isn't a worry to go out as RAM prices are falling through the floor. (2GB in my system for around $30)

I had two 256 RAMs and one died... that is what was causing the problems.

Got 2 512 RAMs, they tested them in the shop, both worked, put them in the computer and only one worked... but I am up and running, that is what counts... 

of course I will have to get that other 512 replaced.

When I have time/money I will get some serious RAM going...

---

### Post by bumanie on 2008-06-01
May be it's a bad dimm slot???, if both sticks tested OK in the shop.

---

### Post by beanco on 2008-06-01
> **bumanie said:**
> May be it's a bad dimm slot???, if both sticks tested OK in the shop.

maybe but now I have to look up dim slot... 

you know, when you help me here I actually learn alot because I have to keep loooking up the stuff you suggest/say... which is great!

robi

---

