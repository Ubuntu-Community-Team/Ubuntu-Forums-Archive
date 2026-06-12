---
title: "problem using 8.10 LiveCD"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by echo314 on 2008-11-01
I try to use the LiveCD, but something goes wrong. After the Loading, Please Wait message, I eventually come to something that reads like failed to initilize cooling device [on] and it just repeats every 6 seconds forever.

I tried booting without acpi, both the apci=off and noapci option, but it does not work. the last message that I get is just something like --[end trace (bunch of letters/numbers ]--

Please help, I would like to get this working as its for a friend who is currently not happy with Windows. It works fine on my comp, but not on theirs. They have like 700mb of ram so thats enough...

---

### Post by bscbrit on 2008-11-02
We will need more information if you want us to provide a solution.  What are the hardware specs for the machine that is misbehaving?  Check that you are using the correct LiveDisk for the target machine.  Do other LiveDisks exhibit the same behaviour?

---

### Post by ashmew2 on 2008-11-02
If using the Live CD isnt an absolute necessity , try  giving the Alternate CD a try.Alternate CD is text based and you can only install the system with it. You cant try stuff like with the Live CD.

---

### Post by echo314 on 2008-11-02
Well its a friends computer, so I don't have all the specs. When I go back over I will find out. I think it had an Athlon 3200+ processor though.

I am trying to back up their files, so the Live CD is a must. Unless they have some free space, and I can just install it in that...

---

### Post by bscbrit on 2008-11-02
The easiest way to collect all the data from your friend's computer is at the command line.  Type 

sudo lshw 

which will show you all the hardware that Ubuntu has found.  Better yet, do

sudo lshw | lshw.txt

where the '|' is the pipe symbol.  On my keyboard it is immediately left of the 'z' on the same key as the '\' symbol.  That will save all the data to a file called lshw.txt which you can either print or copy to a usb memory stick (thumb drive or whatever you want to call it).

On a cautionary note, if the graphics card in your friends computer is a Nvidia card, then the error message about not being able to initialize the cooling fan might indicate that there is no cooling on the graphics card.  Someone else on the forum thread discovered this fact this morning but only after it trashed his graphics card. (see [http://ubuntuforums.org/showthread.php?t=967373](http://ubuntuforums.org/showthread.php?t=967373))

---

### Post by echo314 on 2008-11-02
if I had access to a command line, then I would be set. I could just use cp to copy the various folders to the thumb drive. The problem is I cant get to the command line lol. 

I appreciate your help bscbrit!

---

### Post by bscbrit on 2008-11-02
Sorry - that wasn't particularly helpful, was it!?

My only other (slightly more relevant) suggestion is to download the Live Disc from another distro, or an earlier Ubuntu LiveDisc (e.g. 7.10 or 8.04) simply to get the computer into a position where you can start to install edubuntu.  There are quite a few display 'teething' problems with 8.10 which are not evident on earlier releases.

---

