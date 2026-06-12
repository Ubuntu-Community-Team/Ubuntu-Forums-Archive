---
title: "How to install lubuntu with this partition configuration?"
date: 2016-08-08
forum: New to Ubuntu
---

### Post by DoPiDo on 2016-08-08
Sme time ago, I asked this question: [https://ubuntuforums.org/showthread.php?t=2066202](https://ubuntuforums.org/showthread.php?t=2066202)

I managed to install xubuntu, but now I want to install Lubuntu.
I don't need the Windowspartition anymore. In fact, I don't think I need any partition. How can I achieve this?

---

### Post by yancek on 2016-08-08
You need to clarify what you want to do.  Do you want to replace Xubuntu with Lubuntu?  If so, follow the same procedure explained in your other thread.

If you want to add it and install it over windows ( which will delete all the data on those partitions), you can delete the first four windows partitions and leave it unallocated and then select that space during the install.  Make sure you install Grub from the new Lubuntu to /dev/sda.

Are you using GPT or MBR?  What happened to sda4?  

Just realize that if you have data on the windows partitions which you delete/format, that data will be gone so make sure you have backups.

---

### Post by RobGoss on 2016-08-08
Hello and welcome to the forum, Do you to have just Lubuntu as the only operating system on your machine? if the answer is yes then when you run the live USB or DVD, just choose to use the entire disk space and following the instructions.

As you stated I'm assuming you want to remove the current version of Ubuntu you already have on your machine if this is correct then my comment should help you

---

### Post by DoPiDo on 2016-08-11
I want Lubuntu on my machine, and only Lubuntu. I don't want to keep Windows. I don't want to keep Xubuntu. I don't have data I want to keep.

> [COLOR=#000000]Hello and welcome to the forum, Do you to have just Lubuntu as the only operating system on your machine? if the answer is yes then when you run the live USB or DVD, just choose to use the entire disk space and following the instructions.
I'm going to give this a try.

I thank you both for your replies.[/COLOR]

---

### Post by DoPiDo on 2016-08-11
Ok, so I installed with the option **entire disk space**. Everything seemed ok during installation. The system asks to reboot.
And when I reboot I get this:

> /dev/sda1: clean 123098/15204352 files, 1749078/60790016 blocks

and nothing happens... All I get is that line.

So I guess something went wrong.

Any ideas?


EDIT: So I tried again, and this is what I get in the "Something else" option:
[http://imgur.com/a/it9HN](http://imgur.com/a/it9HN)

---

### Post by wildmanne39 on 2016-08-11
That is running a check of your files, I see that message too, if you let it finish you should get the log in screen unless something else is going on. Give it a little time especially if it is the first time to boot to the desktop.

---

### Post by DoPiDo on 2016-08-11
> **Wild Man said:**
> That is running a check of your files, I see that message too, if you let it finish you should get the log in screen unless something else is going on. Give it a little time especially if it is the first time to boot to the desktop.
nothing after 15 minutes. Is that normal?

---

### Post by wildmanne39 on 2016-08-11
> **DoPiDo said:**
> nothing after 15 minutes. Is that normal?

No you have another issue then most likely video card driver issue, what video card are you using and what driver for the card if you know.

---

### Post by mörgæs on 2016-08-11
Does the hard disk LED show any activity?

---

### Post by DoPiDo on 2016-08-11
> **Wild Man said:**
> No you have another issue then most likely video card driver issue, what video card are you using and what driver for the card if you know.
I have no idea what video card it is.
I installed xubuntu in the past on this machine, and that was no problem.
During installation of Lubuntu, I checked "download drivers" to true.

> [COLOR=#000000]Does the hard disk LED show any activity?
about every 10 seconds 1 short blink.[/COLOR]

---

### Post by mörgæs on 2016-08-11
Are you sure that you picked 16.04.1 and not 16.04.0?

---

### Post by DoPiDo on 2016-08-11
> **mörgæs said:**
> Are you sure that you picked 16.04.1 and not 16.04.0?
No, I am not.
I'll download again and start all over. I'll keep you posted.

Thanks for your input!

---

### Post by RobGoss on 2016-08-11
> **DoPiDo said:**
> Ok, so I installed with the option **entire disk space**. Everything seemed ok during installation. The system asks to reboot.
And when I reboot I get this:



and nothing happens... All I get is that line.

So I guess something went wrong.

Any ideas?


EDIT: So I tried again, and this is what I get in the "Something else" option:
[http://imgur.com/a/it9HN](http://imgur.com/a/it9HN)


As **Wild man **stated that message is normal I also see this on many of my machines why your system won't boot might me yet another problem

 What are the specs to your machine?

Have you try ed loading up another version of Ubuntu to see how that installation runs, unless you checked the integrity of that ISO you used there might have been something wrong with it

---

### Post by DoPiDo on 2016-08-11
> **RobGoss said:**
> As **Wild man **stated that message is normal I also see this on many of my machines why your system won't boot might me yet another problem

 What are the specs to your machine?

Have you try ed loading up another version of Ubuntu to see how that installation runs, unless you checked the integrity of that ISO you used there might have been something wrong with it

The specs of my machine: [http://www.cnet.com/products/acer-aspire-one/specs/](http://www.cnet.com/products/acer-aspire-one/specs/)

I'm making a new bootable usb, because I was not using the latest version of Lubuntu.

I'll keep you all posted.

---

### Post by DoPiDo on 2016-08-11
> **DoPiDo said:**
> The specs of my machine: [http://www.cnet.com/products/acer-aspire-one/specs/](http://www.cnet.com/products/acer-aspire-one/specs/)

I'm making a new bootable usb, because I was not using the latest version of Lubuntu.

I'll keep you all posted.

Works like a charm.

So, the solution was to use the latest version of Lubuntu.

I thank you all for your time!

---

### Post by RobGoss on 2016-08-11
If you've found a fix for your problem can you mark this thread as solved, You can use the **Thread tool **tab at the top of this post

---

