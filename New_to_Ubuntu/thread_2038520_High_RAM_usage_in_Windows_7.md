---
title: "High RAM usage in Windows 7"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by kingkratos on 2012-08-06
Hello,

I have installed Ubuntu on my Dell laptop as a dual boot next to Windows 7 Home Premium. I have never run Linux next to windows as a dual boot and have only ever had Linux (specifically Ubuntu) as a stand alone system on a dedicated machine.

Having said that, I am not completely sure how the two systems are "supposed" to react when "sharing" resources, such as RAM. I used the Wubi installer and was able to install Ubuntu just fine. I can boot into each system without issue as well.

My issue is that my Windows 7 setup was reporting a regular, steady RAM usage of 10-20% at almost any given time. Ever since I installed Ubuntu (about 2-3 hours ago), Windows reports that it is using 35-55% of my RAM at any given time.

Is there any explanation as to why my RAM usage while using Windows 7 would be so drastically high after installing Ubuntu as compared to before installing Ubuntu? Is there anything that can be done to decrease my overall RAM usage in Windows?

Also, does it even matter that my RAM usage seems so high? I have 6GB physical installed and know that I want to be using it to it's fullest, but such a large jump in my "normal" usage seems odd.

Kratos

---

### Post by z3nhakr on 2012-08-06
dual booting ubuntu and win7 won't affect your ram usage because although they are both on your hard drive, they do not run at the same time, hence the need to reboot when switching between the two. the increased ram usage would have been caused by something else such as installing another program or the number of startup programs. Google "[msconfig]("https://www.google.com/#hl=en&gs_nf=1&tok=4nH87IpakiJvHBY0PkD1bg&cp=6&gs_id=8c&xhr=t&q=msconfig&pf=p&safe=off&output=search&sclient=psy-ab&oq=msconf&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.&fp=1b95b2584f9377ea&biw=1301&bih=680")" you can use it to experiment and cut down on ram usage.

---

### Post by Jerry N on 2012-08-06
> **z3nhakr said:**
> dual booting ubuntu and win7 won't affect your ram usage because although they are both on your hard drive, they do not run at the same time, hence the need to reboot when switching between the two. the increased ram usage would have been caused by something else such as installing another program or the number of startup programs. 

OP said he was using WUBI.  I have never used WUBI but I think the idea is that Ubuntu is a program running within Win 7.  I would expect to see increased memory usage.

Jerry

---

### Post by z3nhakr on 2012-08-06
wubi installs a master boot record and a rootfs file onto your windows drive. it is registered like a program so it can be easily installed and removed but it doesn't run inside windows. this is not possible unless you use a virtual machine.

---

### Post by kingkratos on 2012-08-06
Based on what I know about OS's, rebooting/shutting down clears out the RAM. Is there anything with Wubi that runs in the background?

I can't seem to find anything, and haven't installed anything but Ubuntu for ~3 months.

Not a big deal as I do have a ton of RAM to spare, but just wondering...

Kratos

---

### Post by z3nhakr on 2012-08-06
you are correct in thinking that the ram is cleared on reboot. ram is flash memory and flash memory needs power to store data. also the only time wubi runs or uses ram is when you are installing or uninstalling ubuntu. try a ctrl+shift+esc in windows and in the processes tab check to see what process is using the most ram.

---

### Post by naresh pathipati on 2012-08-06
As you said ur RAM usage is more now.As soon as u start ur pc ,ur BIOS(pre programmed chip)looks for OS in various devices(mostly hard drive).As soon  as bios detects OS it displays list of OS'es( using boot loader).Then as per ur Selection of Os,the OS gets loaded in the RAM and then ur actual interaction with OS starts.
So this high RAM  usage is not because of dual booting.
Wait...........
If u installed UBUNTU inside windows i.e there are two options while installing 1.Install inside windows nd 2.In other way.
Then probably RAM usage might be high as compared to previous one.

---

### Post by Wim Sturkenboom on 2012-08-06
> **z3nhakr said:**
> ... ram is flash memory and flash memory needs power to store data.That's not correct. Flash does not need power to retain information; think of memory sticks, the don't need it ;)

---

### Post by z3nhakr on 2012-08-06
> **Wim Sturkenboom said:**
> That's not correct. Flash does not need power to retain information; think of memory sticks, the don't need it ;)
 memory sticks contain capacitors which store energy to keep the data intact. the amount of power needed is minimal so you never have to worry about a memory stick running out of juice but if you let it sit for many many years it would eventually lose its data.

---

### Post by Wim Sturkenboom on 2012-08-07
> **z3nhakr said:**
> memory sticks contain capacitors which store energy to keep the data intact. the amount of power needed is minimal so you never have to worry about a memory stick running out of juice but if you let it sit for many many years it would eventually lose its data.
Nonsense. Capacitors might be there for stabilization of the power and for any other purpose that capacitors usually have, but not to keep the flash memory powered.

From wikipedia ( [http://en.wikipedia.org/wiki/Flash_memory](http://en.wikipedia.org/wiki/Flash_memory) ) :
> 
Flash memory is a **non-volatile** computer storage chip that can be electrically erased and reprogrammed
The keyword is 'non-volatile' and it's an inherent part of the design of flash memory.

And from another wikipedia article ( [http://en.wikipedia.org/wiki/Non-volatile_memory#Flash_memory](http://en.wikipedia.org/wiki/Non-volatile_memory#Flash_memory) ) :
> 
The flash memory chip is a close relative to the EEPROM; it differs in that it can only be erased one block or "page" at a time. It is a solid-state chip **that maintains stored data without any external power source**.


---

### Post by Cheesemill on 2012-08-07
Dual booting, whether by the traditional method or by using Wubi will not increase the memory usage of either OS.
 
Only one OS is ever running and loaded into memory at a time.

---

### Post by kingkratos on 2012-08-19
Thought I would come back to this post and give a quick update. I have since ditched the WUBI install and installed Ubuntu via CD to a 200 GB partition instead. 

When I boot into Windows 7, I am now showing that I am only using ~15% RAM at any given time, which is what I was using before the WUBI install. I cannot explain why this is, but am thinking that it may have something to do with the WUBI install.

Not sure if the WUBI install has anything to do with the 30-35% RAM usage, but can say that since I have gone with a traditional dual boot set up, the RAM usage is "back to normal".

Thanks for all the good information here!

Kratos

---

