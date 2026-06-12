---
title: "Guitar processor POD Line6"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by malform11 on 2012-07-25
TuxGuitar and Playitslow has opened up new possibilities for me. Thank you UBUNTU!

My life would be complete if I could hook up my guitar processor to my desktop 64-bit UBUNTU.

I found a driver, I think. I can't install it, I don't understand.
I get "bad directory or file name" when I try to change directory.

The downloaded folder:
line6-usb-0.8.0+svn551
it is in:
 /home/michael/downloads
but /home/home/downloads is what shows at the bar menu

Should I move it to another location? Then what?

Here are the INSTRUCTIONS included with the driver:

tar xjf line6usb-0.8.1.tar.bz2
    cd line6usb-0.8.1
    make install

This will compile the driver and install it in the module directory, so the
driver should be loaded automatically as soon as the Line6 device is connected.
If it doesn't, you can load it manually with

    modprobe line6usb

You need root privileges to install and manually load the driver.

[END INSTRUCTIONS]
BTW is GNOME the proper prefix?

---

### Post by malform11 on 2012-07-28
perhaps my question should be, what computer courses do I need to take to control my Ubuntu computer. i want to be able to install hardware and write multimedia programs.

I had to give up and buy a windows computer because I can't get any help with Linux.

---

### Post by Breadified on 2012-08-02
As I am also a new user, this is just a guess - at the start of the instructions in Terminal have you tried typing "sudo"? I believe that'll give you root privileges and let you run the install.

Could very well be wrong, but will hopefully help.

Cheers.

---

### Post by malform11 on 2012-08-03
After some stress I got a cheap windows unit and had to reset password, but I eventually installed a driver. 

My line6 as is does nothing, it was a waste of time. It doesn't output midi unless you have a variax guitar.

Using windows was strange. I had to wait after each command for something to happen! i got spoiled to the instantaneous response that I get with linux.

Back to Ubuntu:

I ran a perl program, finally. It didn't work, but it ran from the terminal. I  am reading more and u-tubing, will likely learn "sudo"  and terminal at some point...

---

### Post by Breadified on 2012-08-04
Alright, I'm glad you're back on track with things. Let me know if you have any more questions; I might be able to help with some basic problems. If not, you know yourself the forums will help if you give it time!

All the best,
Breadified.

---

