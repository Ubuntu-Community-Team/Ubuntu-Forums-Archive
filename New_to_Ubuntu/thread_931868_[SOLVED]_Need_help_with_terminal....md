---
title: "[SOLVED] Need help with terminal..."
date: 2008-09-27
forum: New to Ubuntu
---

### Post by TheFly on 2008-09-27
hi.. I'm following a setup-guide for my eee pc so that I can get wifi on thisd laptop. But i am having problems with the codes that are to be used in the terminal.
Here is the guide:[http://wiki.eeeuser.com/ubuntu#wireless_internet_using_native_madwifi_drivers]("http://wiki.eeeuser.com/ubuntu#wireless_internet_using_native_madwifi_drivers")

I have downloaded the madwifi-hal-0.10.5.6 and placed it on the desktop. Then I am to insert this command in the terminal: "tar zxvf madwifi-hal-0.10.5.6-r<revision>-<generation date>.tar.gz"

Here is the message I got when I tried:
```
anders@anders-laptop:~$  tar zxvf madwifi-hal-0.10.5.6-r3861-20080903.tar.gz
tar: madwifi-hal-0.10.5.6-r3861-20080903.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

Does anyone know what I have done wrong?

---

### Post by jrothwell97 on 2008-09-27
You need to change directory (*cd*) into the Desktop folder first.

The command for this is:

```
cd Desktop
```

Make sure you type this in the correct case.

A little tip: once you've done that, you can save typing out the command again by pressing the Up arrow key twice. It shows you commands you've run in the past (sort of like the History menu in Firefox). Then just press Enter again to run it.

Good luck!

---

### Post by nothingspecial on 2008-09-27
You are in your home folder

anders@anders-laptop:~

You need to go to your desktop. We use the cd command for this. So -

```
cd Desktop
```

Then try again.

---

### Post by dhughes on 2008-09-27
You may also want to press the Tab key after typing a few letters of the file name, it will fill in the rest in case you didn't know that. It's good to prevent spelling mistakes when typing out long and obscure filenames.

---

### Post by TheFly on 2008-09-27
Thanks. I learn a lot of you guys :).

New problem: anders@anders-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

---

### Post by starcannon on 2008-09-27
I have a 2g, two 4g's, and an 8g, all of them working perfectly, I followed the guide and "hacks" from [http://array.org/ubuntu/setup901.html](http://array.org/ubuntu/setup901.html), it has the custom kernel that has wifi working outta the box, as well as suspend resume from usb working perfectly.

GL hope that helps.

P.S. after you get through that first link, be sure to run the hacks you want from this link [http://array.org/ubuntu/features.html?device=701&dist=hardy](http://array.org/ubuntu/features.html?device=701&dist=hardy)

---

### Post by nothingspecial on 2008-09-27
Have you got an internet connection?

---

### Post by fooman on 2008-09-27
> New problem: anders@anders-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essential


you may need to enable the universe/multiverse repos.  open synaptic ...system > administration > synaptic package manager

in the toolbar go to > settings > repositories

under ubuntu software,  make sure the first 4 choices are checked (main-universe-restricted-multiverse). click close and you will see a message that the repos have changed.  close that box and then click "reload" in synaptic.  close synaptic and try to install build-essential again:

```
sudo apt-get update
```

```
sudo apt-get install build-essential
```

---

### Post by TheFly on 2008-09-27
I followed starcannon's tips... worked great! Now I'm on wifi!

---

### Post by nothingspecial on 2008-09-27
Nice one.

:guitar:

Do us a favour and mark this thread solved.  It just so that if someone`s looking for an answer to the same question, they can find a thread that`s been resolved without reading all 3 pages.

There`s a dojit near the top of the page called thread tools.

Click it, and near the bottom is an option to mark the thread solved.
\\:D/

---

