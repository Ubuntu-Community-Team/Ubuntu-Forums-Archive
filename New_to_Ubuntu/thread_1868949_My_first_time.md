---
title: "My first time"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by biohzrd87 on 2011-10-25
So this is my first time posting here so I thought my title would be fitting. I just got an old gateway desktop from a friend and since windows xp was running very slow I decided to try something new and just put xubuntu on to it. So far all I have done is install and get the updates. I was wondering, I did look around but I more then likely missed it, where is a good place to start learning about this new system? I am pretty new to this os since is my first time ever installing a linux system. Any advise or a point to right direction would be awesome. 
Also I was wondering how do I figure out what I have in this desktop without opening it open and looking? I tried to find a model number but didn't find anything. I found the task manager and I know this beast has a 256mb ram and 20g harddrive. This thing I old so I wanna start playing around with it and see what I can do to make this worth having. I wanna learn more about computers so I am open to the idea of complete rebuilding this, just unsure how to start.
Thanks in advance for any advise.

---

### Post by papibe on 2011-10-25
Hi biohzrd87. Welcome to the forums!

The best way to learn is to ask questions. There's a few tricks to make the most out of the forums. Start taking a look at this [post]("http://ubuntuforums.org/showthread.php?t=1422475").

Since you are wondering what's inside your machine, here's a few tips:
To get all you hardware details:
```
sudo lshw
```
To get details about your graphics you can use this two commands:
```
sudo lshw -C display

lspci | grep -i vga
```
To see how much memory you have, and how much is being used:
```
free -m
```
To learn how much space your partitions have:
```
df -h
```
To see details about your connected USB devices:
```
lsusb
```
I hope that helps, and keep asking questions.
Kind Regards.

---

### Post by ShodanjoDM on 2011-10-25
Welcome to the forum. You have come to the right place to ask and learn about Ubuntu and Linux in general.

Aside from this forum, there are websites dedicated to Ubuntu and/or Linux/Open Source Softwares that you might find interesting. Sites such as: [webupd8]("http://www.webupd8.org/") and [omgubuntu]("http://www.omgubuntu.co.uk/") or [tuxmachines]("http://www.tuxmachines.org/") are very informative. And do check [Official Ubuntu Documentation]("https://help.ubuntu.com/") site also.

Regarding your system, you can perform some commands in terminal to find out about your hardware specifications. Here are some examples:

```
sudo lspci
```

and

```
sudo lshw
```

Hope that helps, and may others fill in with more info as well.

Edit: papibe got it first and with more complete answers as well :)

---

### Post by mike555 on 2011-10-25
If you plan on working on it,I would recommend more RAM........ sites that sell RAN often let you how much your computer will work with and what type to buy.

---

### Post by scania_gti on 2011-10-25
> **biohzrd87 said:**
> ... has a 256mb ram and 20g harddrive. ...
Today i check RAM usage in Xubuntu (with opened Firefox) and Bodhi (with opened Firefox)
Xubuntu use 150 MB, and Bodhi - 115 MB. It's less tham windows 2000 eating RAM :D
Your's old machine still can run modern linux ;)
But anyway Ubuntu, IMHO, little too big.

---

### Post by cortman on 2011-10-25
Welcome to the forum!
I'm pretty new here myself, so I won't play the knowledgeable old-timer, but-
If you want to really understand the system and be at least somewhat smart about it, I'd strongly recommend learning how to use the command line interface, or CLI. For me, Linux became way easier to understand and was far less intimidating once I got comfortable with using the command line. And I will say too that being able to use the CLI opens up a whole new world of computing power to you. For me, it's really exciting!
I learned a lot using this free book, and I can highly recommend it even if it is a bit dated- [http://www.math.hcmuns.edu.vn/~ngson/courses/Unix/Books/teach_yourself_unix_in_24_hours.pdf](http://www.math.hcmuns.edu.vn/~ngson/courses/Unix/Books/teach_yourself_unix_in_24_hours.pdf).

Happy trails!

---

### Post by biohzrd87 on 2011-10-25
Awesome thank you all for the feedback. I'm at work right now reading this so when I get home I'm gonna try out these and of course aske more questions.
 
I really do wanna work on this computer so the RAM is my first concern. Since I really know nothing about this computer what should I look to figure out what kinda of RAM to get? 
 
Thats all have now but I may have some more tech questions once I get home.
Again thanks for the help so far this is awesome.

---

### Post by JKyleOKC on 2011-10-25
Tou're going to find the report from "sudo lshw" a bit overwhelming at first; it will tell you much more than you want to know at this stage of your learning curve!

For the details of your RAM, look for something similar to this: ```
     *-memory:0
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR2 800 MHz (1.2 ns)
             product: HYMP112U64CP8-S6
             vendor: AD00000000000000
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 800 MHz (1.2 ns)
             product: M3 78T5663QZ3-CF7
             vendor: CE00000000000000
             physical id: 1
             serial: None
             slot: A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)

```It will be near the start of the report, and the details will differ a lot, because this report is from my machine here with 3 GB of RAM. However, you should have at least one "bank" line, and it should contain a "description" line at the minimum. The key thing in this description is the "DDR2 800 MHz" part, which says that my two memory sticks are the 800-MHz DDR2 variety. With only 256 MB in your system, yours are likely to be either PC-100, PC-133, or DDR. The various types are NOT interchangeable, so this is essential info before you go shopping for additional RAM.

Also I didn't see anyone warn you that when you type your password as requested by "sudo" you won't see any indication at all that it's being accepted, unlike most other places where the system asks for your password. That's a common complaint for newcomers; we all expect some sort of feedback that the keys are being recognized! Worry not, just type it in carefully and things will work.

And welcome to this great world of promise and freedom. Don't worry much about breaking the system while you're learning; we've all done it, most of us multiple times!

---

