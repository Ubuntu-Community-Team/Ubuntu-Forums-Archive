---
title: "Just wanted to check if my drives look okay"
date: 2015-11-04
forum: New to Ubuntu
---

### Post by madura2 on 2015-11-04
I installed Ubuntu via USB. 
Had some problems when it turned on, and did boot-repair as this suggestion:
[http://askubuntu.com/questions/153082/accidently-installed-grub-to-usb](http://askubuntu.com/questions/153082/accidently-installed-grub-to-usb)

Things seem to be really slow
Swap (not really sure what that is) is often near 100%

I'm not sure what to make of the drives though. 
I look in System Monitor and there are two devices

[TABLE="width: 500"]
[TR]
[TD]device[/TD]
[TD]directory[/TD]
[TD]type[/TD]
[TD]total[/TD]
[TD]available [/TD]
[TD]used[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/mapper/ubuntu--vg-root[/TD]
[TD]/[/TD]
[TD]ext4[/TD]
[TD]77.9GB[/TD]
[TD]69.5GB[/TD]
[TD]4.4G[/TD]
[TD]5%[/TD]
[/TR]
[TR]
[TD]/dev/sda1[/TD]
[TD]/boot[/TD]
[TD]ext2[/TD]
[TD]246.8MB[/TD]
[TD]140.7MB[/TD]
[TD]98.3MB[/TD]
[TD]39%[/TD]
[/TR]
[/TABLE]

Does that look alright?
On Windows, there was a C drive, which is the first one. And I think a partition D for recovery... 

Just want to use the internet with this computer and would prefer it to run a bit smoother and faster.
Thanks for any help.

---

### Post by Bashing-om on 2015-11-04
madura2; Hello, My Welcome to the forum .

Is this older hardware ?
> 
Things seem to be really slow
Swap (not really sure what that is) is often near 100%


Takes some horse power to run the top-of-the-line edition ubuntu. Do you have the assets to do so ?
Post back the outputs - Between code tags - of terminal command:
```

free -m

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
To see what memory is available and how it is managed.

Maybe we see that a lighter version - Lubuntu - may suit this hardware better ?

[INDENT][INDENT]pack'n 5 pounds of sugar
[INDENT][INDENT][INDENT]in a 5 pound sack
[INDENT][INDENT][INDENT]a real tight fit
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by madura2 on 2015-11-04
It's an old laptop that I wasn't using. Thought Ubuntu might work faster than Windows XP.

```
 
            total       used       free     shared    buffers     cached
Mem:           485        472         13        105          8        256
-/+ buffers/cache:        207        278
Swap:          503        189        314


```

---

### Post by Bashing-om on 2015-11-04
madura2; Yeah ...

You are real short on memory .. 
Add more ram ? OR
install lubuntu. Lubuntu is designed to run on older hardware with less memory constraints.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
My system, running ' minimal' :
```

sysop@1404mini:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3953        943       3010         28         38        537
-/+ buffers/cache:        367       3586
Swap:            7          0          7
sysop@1404mini:~$

``` with a very very small swap partition.

[INDENT][INDENT]won't hurt to try
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-11-04
Your **free** output shows you have not sufficient ram to run Ubuntu, and in all honesty, not really enough for Lubuntu to run at a usable speed.
```
            total       used       free     shared    buffers     cached
Mem:           485        472         13        105          8        256
-/+ buffers/cache:        207        278
Swap:          503        189        314
```
You can see that there is a total of 485MB ram available, presumably a 512 chip with some memory used by the graphics chip, leaving you 485.  Swap is the same thing as your XP's virtual memory, ie is on the hard disk, and is used by the system when the ram is overloaded, so is very slow in comparison with ram.

Try Lubuntu by all means rather than Ubuntu, to see if that is better, but if you can get some more ram it will probably be very worth while.  2GB would be my recommendation if the motherboard will take it.

---

### Post by madura2 on 2015-11-06
Thank you for replying. I was sure I'd checked the requirements a long time ago. 
I've decided to use Puppy Linux for the time being and upgrade to 2GB ram later.
I love the look of Ubuntu and want to use it if i can.

---

