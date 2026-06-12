---
title: "Distros using 2.6.28.x kernel"
date: 2009-01-29
forum: Other OS Talk
---

### Post by oldos2er on 2009-01-29
Subject says it all. Does anyone know of any distros using the latest kernel 2.6.28.x? Something other than alpha software....

---

### Post by cardinals_fan on 2009-01-29
Arch does.  I think Fedora *can* with relatively little difficulty.

---

### Post by kk0sse54 on 2009-01-29
Gentoo

---

### Post by SunnyRabbiera on 2009-01-29
sometimes later kernels can break compatibility so thats why most distros like ubuntu use older kernels unless there is a good reason to use a more modern kernel such as a security issue.

---

### Post by Sorivenul on 2009-01-30
> **cardinals_fan said:**
> Arch does.  I think Fedora *can* with relatively little difficulty.
Fedora is currently on 2.6.27.12 and 2.6.28 is being tested for release in Fedora 10. Fedora Rawhide currently is currently using RC3 of 2.6.29.

---

### Post by kagashe on 2009-01-30
KNOPPIX 6.0

kagashe

---

### Post by s3kt0r on 2009-01-30
I am running ubuntu intrepid with 2.6.28, no problems.

---

### Post by YeOK on 2009-01-30
> **Sorivenul said:**
> Fedora is currently on 2.6.27.12 and 2.6.28 is being tested for release in Fedora 10. Fedora Rawhide currently is currently using RC3 of 2.6.29.

They also have 2.6.29 builds for fedora 10 in testing. You can download them from koji, the fedora build system.

I'm using the 2.6.29 now, I have been using 2.6.28 and its been fine.

[Kernel packages@koji]("http://koji.fedoraproject.org/koji/packageinfo?packageID=8")

---

### Post by zmjjmz on 2009-01-30
Supposedly GEM is integrated into 2.6.28rc2, so that means better intel graphics performance :D

---

### Post by L815 on 2009-01-30
> **zmjjmz said:**
> Supposedly GEM is integrated into 2.6.28rc2, so that means better intel graphics performance :D

I've been waiting for better intel gfx performance for so long. If it's true, I can finally do a full switch ^_^

---

### Post by smartboyathome on 2009-01-30
> **L815 said:**
> I've been waiting for better intel gfx performance for so long. If it's true, I can finally do a full switch ^_^

Intel drivers haven't been upgraded for 2.6.28's new GEM unfortunately. :(

---

### Post by pgatrick on 2009-01-30
sidux does too. :)

---

### Post by K.Mandla on 2009-01-30
CRUX. :lolflag:

---

### Post by igknighted on 2009-01-30
> **smartboyathome said:**
> Intel drivers haven't been upgraded for 2.6.28's new GEM unfortunately. :(

You can get 2.6.1 from the intel graphics testing PPA.  However, there are still a lot of bugs with GEM, so depending on your hardware, your mileage may vary.

---

### Post by oldos2er on 2009-01-30
Thanks for the answers, everyone.

---

### Post by oldos2er on 2009-01-30
> **s3kt0r said:**
> I am running ubuntu intrepid with 2.6.28, no problems.

 Did you compile it yourself, or get it from the Jaunty repos?

---

### Post by smartboyathome on 2009-01-30
> **igknighted said:**
> You can get 2.6.1 from the intel graphics testing PPA.  However, there are still a lot of bugs with GEM, so depending on your hardware, your mileage may vary.

I was on Arch Linux with the 2.6.28, but am on Puppy right now (Arch doesn't work, I am not wanting to hassle with it right now). I will see about that later when I get back on Arch.

---

### Post by igknighted on 2009-01-31
> **oldos2er said:**
> Did you compile it yourself, or get it from the Jaunty repos?

kernelcheck ftw... it's as easy as installing from synaptic, but it compiles it for you.

---

