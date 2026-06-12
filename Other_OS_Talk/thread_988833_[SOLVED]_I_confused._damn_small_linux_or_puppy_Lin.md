---
title: "[SOLVED] I confused. damn small linux or puppy Linux, having troble installing both"
date: 2008-11-20
forum: Other OS Talk
---

### Post by Hyper Tails on 2008-11-20
Hi I have an old computer in the basement running windows 2000
and I want to install dsl or puppy linux

but I having troble installing both
I'm not sure which one would go good

old pc info:
128mb ram
4g hardrive
intel processor (I don't know which one)
It's original os was windows 95

help will be thanked

---

### Post by cardinals_fan on 2008-11-20
Neither.  Use SliTaz loram (download the tiny SliTaz iso and enter slitaz-loram at the boot prompt).

---

### Post by zmjjmz on 2008-11-20
I totally prefer DSL, but SliTaz might be a better option for you.

---

### Post by loell on 2008-11-20
DSL is my first love, great little distro, backed with a friendly community and it has the option to use APT.  :)

---

### Post by kerry_s on 2008-11-21
dsl, with 128mb ram you can run it in ram for maximum speed.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/dsl-4.4.10.iso](http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/dsl-4.4.10.iso)

---

### Post by snowpine on 2008-11-21
Hi there, tell us more about your installation troubles. We can try to help you troubleshoot. DSL, Puppy, and SliTaz are all good distros, the choice really depends on your needs. I am a big SliTaz fan myself.

---

### Post by Hyper Tails on 2008-11-21
my installation problems is that I created a partition for it by 2000 and linux
and I tried dsl and It continues and it closes and I thought it was done and instead it brong me stragit to windows 2000

on puppy It was doing the installation smoothly and but it stops at a point

---

### Post by Bungo Pony on 2008-11-22
Personally, I would choose TinyMe to install on that computer, but that's just me.

If you want to install DSL, try doing it in the CLI only. Here's how to do it...

Boot off the CD. Eventually, you will get to a screen with the big DSL logo and a prompt that says 'boot:". Type 'install' at the prompt and let it go through its motions.

You should get to a text menu asking for install options. Select #2 (install to hard drive). Make sure you install it on the correct partition. If you partitioned your drive and plan on keeping windows, it's likely that the partition you want to install to is hda2. But if I were you, I'd double check and make sure that this is the partition you want.

Watch the screen as it installs. If you get an error, you should get some kind of an idea how, where, or why the install is failing.

---

### Post by K.Mandla on 2008-11-22
> **cardinals_fan said:**
> neither.  Use slitaz loram (download the tiny slitaz iso and enter slitaz-loram at the boot prompt).
+1.

---

### Post by zmjjmz on 2008-11-22
Chances are you need to install GRUB to the MBR.
It should take care of this during the DSL install. Are you doing a Frugal install? Because that could be the problem.

---

### Post by Hyper Tails on 2008-11-22
never mind i got xp on it now
it works great on it

---

### Post by zmjjmz on 2008-11-22
XP on 128MB RAM is a joke.
You cannot be serious. I run XP on 128MB RAM and it's nigh unusable.

---

### Post by Hyper Tails on 2008-11-23
> **zmjjmz said:**
> XP on 128MB RAM is a joke.
You cannot be serious. I run XP on 128MB RAM and it's nigh unusable.

I'm telling the truth
It works with xp sp1
it's 5% slow on some spots but It's working good
 don't believe me I'l take a picture of it to prove it

---

### Post by maybeway36 on 2008-11-23
Windows XP is quite a bit faster than most Linux distributions, likely because of its low memory usage. Just don't add too many startup apps and you'll be good.

---

### Post by zmjjmz on 2008-11-23
> **Hyper Tails said:**
> I'm telling the truth
It works with xp sp1
it's 5% slow on some spots but It's working good
 don't believe me I'l take a picture of it to prove it

Picture won't help ;)
But I see you're running SP1, which presumably makes it faster (because it's older).
My 128MB RAM machine uses SP3, so that's probably why it's slow.

---

