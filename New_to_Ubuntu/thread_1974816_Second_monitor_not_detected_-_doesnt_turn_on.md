---
title: "Second monitor not detected - doesnt turn on"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by schejk on 2012-05-06
hello,

i have a problem with detecting second monitor.
radeon x1950pro and two monitors samsung (main) and lg (secondary)

did a first time install of ubuntu 12.04 and the lg L1710m is not detected - doesnt turn on, tried to switch to dvi still nothing. samsung is always detected.

if i have connected only lg when computer starts is detected then turns of when ubuntu starts to load.

have a dual boot win 7. no problems there.

also tried xubuntu, problem stays. please some help. dual monitors are really important.

---

### Post by gordintoronto on 2012-05-06
Did you run "additional drivers"?

---

### Post by schejk on 2012-05-08
yes did run it. sais there are no additional drivers or somtehing like that.

now tried mint and runs on both lcds with no problems, but would really like to try ubuntu

---

### Post by schejk on 2012-05-09
so i confirmed that the second monitor doesn work on
ubuntu, xubuntu, kubunto
works on mint, opensuse, fedora.

can someone please tell me what do they have that ubuntu doesnt?
still want to run on ubunto (xubuntu)!

---

### Post by gordintoronto on 2012-05-09
What kernel versions?

To find out, open Terminal, which is sometimes Accesories/Terminal, and type the command:
uname -a

The output will look like this:
Linux m12-64 3.0.0-19-generic #33-Ubuntu SMP Thu Apr 19 19:05:14 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

And 3.0.0-19 is my kernel version.

---

### Post by schejk on 2012-05-10
this is it:

Linux  3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 athlon i386 GNU/Linux

found out in the system that the card is unknown but i think that both monitors should work no mather that.

---

### Post by gordintoronto on 2012-05-11
Sorry, I was asking for a comparison of kernel versions that work versus ones which don't work.

---

### Post by schejk on 2012-05-13
so i kind of made a pictures of when the second monitor turns off.

am impresed that there is no support from the community for any kind of help. 

again dual screen works in win xp, vista, 7, mint, opensuse, fedora, **puppy**, but not in ubuntu, xubuntu nor kubuntu nor lubuntu. 

specs
cpu AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ × 2 
mobo asus asus m4a79 deluxe
ram 4gb ddr2
gpu x1950 pro 512mb ( in ubuntu says Gallium 0.4 on ATI RV570 )
ubuntu 32bit

---

### Post by steeldriver on 2012-05-13
what does ```
xrandr -q
``` say ? have you looked in /var/log/Xorg.0.log to see if there are any obvious problems (you can grep "(EE)")?

---

### Post by schejk on 2012-05-13
xrandr


Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
[COLOR="Red"]**DVI-0**[/COLOR] disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
DVI-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0 +   75.0* 
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  

i am total begginer in linux so please dont know what ee means

card has vga, dvi and s-video. could this be a problem

---

### Post by steeldriver on 2012-05-13
```
$ cat /var/log/Xorg.0.log | grep "(EE)"
```picks out all the lines in Xorg.0.log that are flagged as errors (EE)

---

### Post by schejk on 2012-05-13
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.045] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    20.047] (EE) Failed to load module "fglrx" (module does not exist, 0)

---

### Post by schejk on 2012-05-15
so changed gpu, did a fresh install problem stays. so not the problem with gpu.

solved the problem --> ubuntu delete and mint install :popcorn:

**dual screen works from the beggining without any kind of settings**

---

