---
title: "wine &amp; printer drivers"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Bristol Rogue on 2008-04-27
Why can I not install my printer under wine and then use it from OO.o and other applications as a normal printer?

I'm asking this as, like many others attempting to convert to linux/GNU, I come with a large quantity of baggage, in this case including a Lexmark X9350 given to me as a Christmas present.

I'm sure that there is a very obvious answer to this, I just cannot see it at present!

Don't just confirm what I believe, but explain too please.  If there is already a good write up please point me at it, although it will need to be at a quite basic level.

Thanks in anticipation.

:confused:

---

### Post by Hospadar on 2008-04-27
You can't install drivers through wine for technical reasons regarding how the OS works.  I won't get too into it, because that's what college-level CS courses are for, but basically:

Wine is a program loader: A program is a set of binary instructions run in the processor.  Some of these instructions (in a windows program) link to windows libraries that do not exist in linux.  The wine project provides equivalent libraries for linux and alters the exe file so that the instructions point properly to these new libraries.

A driver is a module that gets loaded into the kernel (the lowest level of software) that allows software to interface with that hardware in a standardized way.  Windows drivers require a windows kernel to do anything.  So even though you can run the installer in wine, it just puts a file somewhere in wine's virtual file system that doesn't do anything (since there is no windows kernel for it to get loaded into).

So the bottom line is, unless you have a specialized driver wrapper like ndiswrapper (which only works for wireless drivers) you can't use windows drivers in linux.

You'll either have to: find linux drivers for your printer, or figure out what needs to be done to make it work (a lot of times it's a matter of changing some configuration or manually adding it somewhere, this would requre some googling on your part).  I think lexmark may provide some linux drivers, you may want to start there.

Also how are you connecting to the printer?  Are you using the wifi (which I believe this printer has from what little googling I did) or a usb cable?  If you are using only one, try the other and see if that works.

---

### Post by Bristol Rogue on 2008-04-28
Many thanks for your reply, my understanding is better, although still far from perfect.

From my Googling it seems that Lexmark used to provide a Linux driver builder for their printers but this is no longer available from their site, neither have I been able to find it and the instructions anywhere else.  I am aware that Lexmark have a lousy reputation within the GNU/Linux communities for their [lack of] printer support and lack of clear information about the communications with their printers.

My solution will be to print to pdf in ubuntu, then print the pdf when I boot up in windoze, a great pity, but there it is!

I have tried connecting the printer via both network and usb.  Using usb the standard print system recognises that the appropriate printer is attached but nothing comes out of the printer when I print to it.  The printer is not even recognised via the network, but then it didn't provide all the features over the network it should have in windoze either!

Now I know that the answer is not that simple it will go on 'the back burner' whilst I try and tackle other features.

Thanks again for answering the generic question, not just the specific one.

---

### Post by aigelonic on 2008-04-28
You might try this HOWTO. It's not for the X9000 series, but I've experienced with another printer that even though the driver model was not the same as my printer model, it worked.

[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

---

### Post by Bristol Rogue on 2008-04-29
Many thanks for the pointer, sadly the lexmark x9350 remains a lemon for me.  On the brighter side I picked up a few tips on the way through!

---

### Post by Cadmus on 2008-04-29
From what I understand Lexmark has little or no Linux support, though I have a vague recollection of something to do with HP printers being useful in getting at least basic functionality out of a Lexmark.

---

### Post by Bristol Rogue on 2008-05-05
Thanks for your thought, I've tried four different types of HP drivers now without success.

---

