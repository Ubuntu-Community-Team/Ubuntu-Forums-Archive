---
title: "Non-executable memory"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by mlnease on 2012-04-10
Hello,

I've been looking at Non-Executable Memory at  [https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures).  From that page:  "...you  can start using it if you install the [FONT=Courier New]-server[/FONT]     or [FONT=Courier New]-generic-pae[/FONT] flavor of the 32bit     kernel..." 

So I've installed the -generic-pae kernel; still, in my /proc/cpuinfo file, the first flags line *does* include 'pae' but does *not* include 'nx',     which I take to mean that the CPU is nx-capable but that nx is disabled.
     
     Can anyone advise me as to how to 'un-disable' it?  I've searched this page and several others to no avail.

Thanks in advance.

---

### Post by roelforg on 2012-04-10
The -server and -pae have (primarily) to do with the amount of ram you can access.
You know how 32bit windows caps at 3gb?
The 32bit -pae caps at 64gb and is default.

---

### Post by ridetheteapot on 2012-04-10
well, im gonna guess that you already tried to use the ubuntu helper app they refer to on that page. (its ubuntu specific as far as i know):
```
/usr/bin/check-bios-nx --verbose
```

useful info would be make and model of your computer --- is it a laptop?
And have you checked through your bios settings?

Just for curiosity - Why haven't you switched to 64bit?

---

### Post by mlnease on 2012-04-10
Interesting, thanks--no, I know little about it (RAM, capping at 3GB etc.)--as for 32bit -pae being default, I don't think I've seen it before, in many Lucid installations.  Could be wrong of course...

---

### Post by mlnease on 2012-04-10
> **ridetheteapot said:**
> well, im gonna guess that you already tried to use the ubuntu helper app they refer to on that page. (its ubuntu specific as far as i know):
```
/usr/bin/check-bios-nx --verbose
```I did, yes--ouput: ```
This CPU is family 6, model 15, and has NX capabilities but is unable to
use these protective features because the BIOS is configured to disable
the capability.  Please enable this in your BIOS.  For more details, see:
https://wiki.ubuntu.com/Security/CPUFeatures
```(The above is where I found the site location).> useful info would be make and model of your computerIt's a Dell Optiplex GX745--
[QUOTE]And have you checked through your bios settings?I have and found no way to enable nx.  Though--now you mention it--I haven't checked since installing the -pae kernel.  I'll restart and have a look.
> Just for curiosity - Why haven't you switched to 64bit?I've never really understood the difference or known how or why--hence the Absolute Beginner Talk.  I'm wide open to suggestions, though--thanks in advance.

I have to run out for a bit but I look forward to any more advice you may have to offer.

I *did *find the setting in BIOS settings under Security/Execute Disable--and nx does now appear in my /proc/cpuinfo.   Thanks!  If you have any advice about switching to 64bit I'd still be  glad to hear it.

---

### Post by ridetheteapot on 2012-04-10
nice.

pae is just kind of a hack (but preformance of non pae vs pae kernels is negligible with the amount of ram consumers normally use).
64bit systems run faster (though it depends what software really) and utilize your ram fully - (but by nature the same app will use more ram in 64bit then 32).

64bit is also the way forward - on the other hand you can find (very few) binaries that will not run in 64bit systems. (most 32 bit stuff you can run in a 64bit system - its just a matter of having the 32bit compatibility libraries).

As far as switching goes - i'm a proponent of the 'whatever works' philosophy, so w/e. if your gonna do a fresh install at some time I would recommend just going 64bit.

---

### Post by mlnease on 2012-04-10
> **ridetheteapot said:**
> nice.

pae is just kind of a hack (but preformance of non pae vs pae kernels is negligible with the amount of ram consumers normally use).
64bit systems run faster (though it depends what software really) and utilize your ram fully - (but by nature the same app will use more ram in 64bit then 32).

64bit is also the way forward - on the other hand you can find (very few) binaries that will not run in 64bit systems. (most 32 bit stuff you can run in a 64bit system - its just a matter of having the 32bit compatibility libraries).

As far as switching goes - i'm a proponent of the 'whatever works' philosophy, so w/e. if your gonna do a fresh install at some time I would recommend just going 64bit.
Thanks again!  I am in the process of completing my upgrade to AMD64 (I didn't even know this was synonymous with 64bit)--it's all going swimmingly.  Thanks again for the advice.

---

