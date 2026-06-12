---
title: "Does anyone know about where to get USB drivers for  ZTE 831 All modem?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by bhadotia on 2008-07-01
I can still connect it through the ethernet port . But I am just curious , about how to connect a modem through the USB port.
All help is appreciated. It's OK even if there is no reply.
Many thanks in advance.

---

### Post by pytheas22 on 2008-07-01
What is the output of the command:
```

lsusb
```

after you plug the modem in via the USB cable?

Also, try unplugging the ethernet cable and pluggin in using USB, and then reboot the router.  Sometimes it's necessary to do this to make it work.

---

### Post by bhadotia on 2008-07-01
Here ya go:
```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0915:0005 GlobeSpan, Inc. 
Bus 001 Device 001: ID 0000:0000
```
And thanks for the reply ( I was not expecting one:)).

---

### Post by pytheas22 on 2008-07-01
From this [thread]("http://www.geekzone.co.nz/forums.asp?ForumId=46&TopicId=15459") I found instructions that may work.  It says you should download the driver for your modem from [http://eciadsl.flashtux.org/download.php](http://eciadsl.flashtux.org/download.php) and follow these [instructions]("http://eciadsl.flashtux.org/tutorial.php") to install it.  The instructions are for Redhat, but it shouldn't be hard to substitute the appropriate procedures for Ubuntu.  Judging by the screenshots in the installation guide, it's really old, but hopefully this will still work for you.  Let me know how it goes.

---

### Post by bhadotia on 2008-07-01
Thanks for the reply . I will go through  those links now and let you know when I'm through.

---

### Post by bhadotia on 2008-07-01
Do I need the Synch.bin files also.

---

### Post by pytheas22 on 2008-07-01
> Do I need the Synch.bin files also.

I guess so, if the instructions say it.  I guess you are supposed to download eciadsl-synch_bin.tar.bz2, unpack it and follow the instructions inside.  But I've never done anything like this myself, so I'm not certain about anything.

---

### Post by bhadotia on 2008-07-01
What do I need to enter in VID1, VID2, PID1, PID2 ; and which chipset do I choose (how do I know my chipset?)?
Also which ppp mode do I select?

---

### Post by pytheas22 on 2008-07-01
I have no idea what any of that stuff is so I can't give you a good answer.  But based on the last two posts in this [thread]("http://www.geekzone.co.nz/forums.asp?ForumId=46&TopicId=15459"), I guess that that data comes from your ISP and maybe is specific to your geographical region?  But really I don't know.  I don't even know what VID or PID means.  Maybe a Google search would help, or make a thread asking about it.  I've never had to configure a USB modem personally so I'm sort of lost as to what those values should be.

As for the chipset, I also don't know, but there are only two options so I guess you will just have to try both and see which one works.

Also make sure to check the box for dhcp (if you use that on your network).

---

### Post by bhadotia on 2008-07-01
VID and PID respectively mean Product ID and Vendor ID. I searching the net for these for my modem.

---

### Post by bhadotia on 2008-07-05
I think I am almost there:
I found about the PID etc from a tool that was included with the driver .
I think I will be able to find the version of my modem chipset with 
```
lsusb -vv
```I haven't tried this command yet coz I'm in the middle of a download and wold have to connect my modem through USB.

Now all I need to Know about is what should I  fill in ALTsynch and the other ALTec.. and what PPP mode I am using and which .bin file should I select (see the snap shot above).

Can someone with internet technical knowledge guide me through these .

Many thanks.

---

### Post by pytheas22 on 2008-07-06
For the .bin file, the directions I think say that you have to just try each one until you find the one that works.

For Alt synch and Alt tech, I would try 0 or 1, or possibly -1.  But I have absolutely no idea.  The only reason I suggest those numbers is because the box is small and it looks like 0 or 1 would make the most sense there.

For ppp0 mode, again, you might have to try all the options until you find the right one.

I'm sorry I can't provide more help for this; unfortunately, it's really way beyond anything that I have experience with.  Hopefully someone more knowledgeable about this stuff will find this thread and help you out; if not, you may want to start a new thread to get more attention.

---

### Post by bhadotia on 2008-07-06
Ok.. Thank you very much again for the reply.
I think I will have to try the hit and trial method: but I will try it in some days - not now- coz its getting frustrating - and any way it will take a long time .
Still thank you very much.

---

### Post by wep940 on 2011-07-10
When you do the lsusb, the information that shows in this syntax xxxx, a colon, xxxx is the manufacturer(vendor) id and the product id respectively.

---

