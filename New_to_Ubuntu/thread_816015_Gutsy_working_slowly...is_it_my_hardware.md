---
title: "Gutsy working slowly...is it my hardware?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by clintonsears on 2008-06-02
Hi, everyone!  Let me just say in advance I really love the Ubuntu community for all the support and effort people put into it.  I got 7.10 about 2 months ago and just upgraded to 8.04 yesterday...so far, so good!

There's one problem:  When I run Amarok together with Firefox and Pidgin (or any combo of programs) I frequently have long pauses where the screen turns gray and there's a processing delay.  I have a dual boot with XP and I rarely experience dramatic slowdowns there.  Often Amarok will stop playing continuous music and just let out long scratchy static.  :(

I have only TWO 256MB RAM memory chips installed on my HP laptop. (I got it in Decemeber 2005...it's been AROUND).  I've been wondering if upgrading to two 1GB RAM chips would help increase the speed?  But maybe my Celeron processor is just too old?  I really don't understand the differences in processors well, so if anyone has a thread/website about it, I'd love to read it.

Also, if it's of use, during particularly trying times for my system, the System Monitor shows memory at about 80% use and CPU at nearly 100%.

In the terminal I used the lshw command and got the following (sorry, I'm still not sure how to use the code, HTML and PHP tags):
cds                       
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 503MiB
     *-cpu
          product: Intel(R) Celeron(R) M processor         1.50GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.8
          size: 1500MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts

Anyway, I'm grateful for any input you might have!

Cheers,

Clinton

---

### Post by abraxas334 on 2008-06-02
heya, 
am not an expert either, but i got a similar processor to yours but got 1512 MB ram and i have none of the problems u describe after the upgrade...

---

### Post by derred on 2008-06-02
More RAM is good. 
You might also want to consider turning off the desktop effects (in the system/preferences/appearance/visual effects tab click on None) You won't get the eye candy graphic effects (zooming/fading windows) but you should notice an increase in speed
Also I recommend you try a less resource hungry player (amarok is a bit of a hog, in my experience any way). I use xmms2, beep media player(a bit like winamp) or Rhythmbox.
Hope this helps

Edit
Oh and don't worry about your 2005 Celeron, I've run ubuntu on systems from 1998 so I think you're safe

---

### Post by clintonsears on 2008-06-02
Right, thanks Derred & Abraxas!

I'll check out getting more RAM.  Amarok, a resource hog thought it may be, allows me to transfer music to and from my iPod.  If Apple made an iTunes for linux, I'd almost never use XP anymore...sigh.

Anyone else had problems (or had them alleviated) with a RAM increase?

---

