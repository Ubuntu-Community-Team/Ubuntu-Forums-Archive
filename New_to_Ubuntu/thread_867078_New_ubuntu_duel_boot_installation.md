---
title: "New ubuntu duel boot installation"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by paulm2008 on 2008-07-22
Hi, Good evening

I have just installed ubuntu on my Striker II Formula, Q9450, Corsair 4Gb [2x2Gb] 1066MHz [CL5] Dominator RAM and 8800GTX XFX graphics card.

Being a total novice to Linux.  My fist attempt to undertake any activity [which incidently resulted in me having to re-install both vista and ubuntu] was to install a wireless driver for my Netgear WG111v3 USB wireless adaptor.  However when I followed the instructions as posted on the web [link below] to generate an executable named ndiswrapper

[http://ubuntuforums.org/showthread.php?t=732827](http://ubuntuforums.org/showthread.php?t=732827)

the make instruction failed as a result of the system being unable to find a vast number of libraries, following compilation.  I assume the PC has to be configured in someway to ensure my system system knows what the library paths are.

Is there a link to a thread highlighting how I actually set the system up [I'm sure there must be one - I find it hard at first navigating forum site - particularly if you do not know what question you really want to ask] - such that installation of this nature can be carried out.  I do not want to have to re-install every thing again !!

Kind Regards

Paul

---

### Post by Potatoj316 on 2008-07-22
you might not have had the package build-essential installed, to install type this in the terminal
```
sudo aptitude install build-essential
```this should add all those libraries that are not found

---

### Post by Het Irv on 2008-07-22
Do you have a way to temporarily hook up to the internet in Ubuntu, like a ethernet connnection?  If so you can search for and install the missing libs using Synaptic.

System -> Administration -> Synaptic Package Manager

If you cannot hook up, you can look for the packages @ packages.ubuntu.com and manually install them.

---

### Post by wtp00 on 2008-07-22
I had installed ubuntu a month ago and had the same problem getting it set up. I found a soultion that involves ndiswrapper as you mentioned,though I got it from add/remove programs as Windows Wireless Drivers. Then download the windows driver and unzip. Then open Windows Wireless Drivers (System>Administration>Windows Wireless Drivers), click install driver, and select the .inf file. If it works you should see "Hardware Present: yes"

Hope it helps...

---

### Post by wtp00 on 2008-07-22
Also where did you download the driver from?

---

### Post by aomlives on 2008-07-22
> **Het Irv said:**
> If you cannot hook up, you can look for the packages @ package.ubuntu.com and manually install them.

That's package**s**.ubuntu.com ;)

---

### Post by paulm2008 on 2008-07-22
Thank you all for the very quick reply's.  I will keep going with this as it seems linux is a very versatile operating system [compared with windows].  I think as soon as I get used to the basic principles it should become easier [famous last words !!]

Thanks Again for you help - I will keep you informed about my progress

Kind Regards

Paul

---

### Post by paulm2008 on 2008-07-22
Hello, Thank for the reply

I downloaded ndiswrapper from

[http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/](http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/)

and the wireless driver from

wget [http://www.avengergear.com/](http://www.avengergear.com/)

I just hope I did not introduce a virus into my system by doing so

Regards

Paul

---

### Post by Potatoj316 on 2008-07-22
i am almost 100% sure you didnt get any viruses, linux is known for not having many viruses.  This is partially due to the few users it has but also because it is more secure than windows.  also sourceforge is a reputable site, theres probably no viruses there

---

### Post by Het Irv on 2008-07-22
> **aomlives said:**
> That's package**s**.ubuntu.com ;)

Edited, Thanks.   
I don't go there much.

---

### Post by stmiller on 2008-07-23
> **paulm2008 said:**
> 

I just hope I did not introduce a virus into my system by doing so

Regards

Paul

No viruses in Linux. That is only a feature of the Windows world. :)

---

