---
title: "[SOLVED] i686 or x86_64"
date: 2008-06-30
forum: Other OS Talk
---

### Post by nerd0795 on 2008-06-30
I'm planning on installing fedora to a usb 4GB stick and i don't know which to choose (I'm using Fedora LiveUSB creator)  and I'm getting the KDE version.  But it says i686 or x86_64.  I don't know which one to choose... I'm using a Intel Pentium D CPU 2.80GHz and Windows Vista 32 bit (don't know my version of ubuntu).  But I'm gonna be using it on a Windows XP 32 Bit.  I don't know the processor specs.  I know it's not that powerful, it's a dell machine (the one that came with the deal when you sign up with Telus Internet).  So which do I choose.

---

### Post by ironcitypete on 2008-06-30
Download the i686 version which is 32 bit. The x86_64 is the 64bit version.  The i686 version will work on 32 and 64 bit processors. 

Persistent overlay allows you to save changes you make to fedora. Such as adding new programs and saving files.

Here are the [requirements]("http://docs.fedoraproject.org/release-notes/f9/en_US/sn-ArchSpecific.html#sn-ArchSpecific-x86-hw") for fedora 9. They recommend 256MB of ram but 512 and up would be best.

---

### Post by nerd0795 on 2008-06-30
thank you but how much should be my persistant overlay be... I have a 4GB thumb drive.

---

### Post by ironcitypete on 2008-06-30
> **nerd0795 said:**
> thank you but how much should be my persistant overlay be... I have a 4GB thumb drive.

Well it all depends on how many programs you will be installing. I would make it at least 512MB but since you have a bigger drive you could make 1GB and you would still have 2.3GB free to save other files on the drive.

---

### Post by nerd0795 on 2008-06-30
can I put it all the way to the max (2024MB)?

That's all I'm gonna do with my thumb drive. Is use it to use Fedora

---

### Post by LaRoza on 2008-06-30
Your processor looks like a Pentium D 820, which is 64 bit.

But for a flash drive install, I recommend 32 bit.

---

### Post by nerd0795 on 2008-06-30
But does using 2 GB for persistance (or a bit less) a good idea on a 4gb thumb drive?  This is mainly for linux-on-the-go.

---

### Post by ironcitypete on 2008-06-30
> **nerd0795 said:**
> can I put it all the way to the max (2024MB)?

That's all I'm gonna do with my thumb drive. Is use it to use Fedora

The one thing to keep in mind is the files you save to the home folder in fedora will not be accessible on other systems.  Once you boot into the system it should automatically mount the flash drive i would save any files you may need to use on other systems on the free space on the drive.  If you won't be transferring files to and from other systems you can make the overlay as big as you want.

---

### Post by nerd0795 on 2008-06-30
Ok thank you :)

---

### Post by LaRoza on 2008-06-30
You might want to check out something that is designed to be run live (unless this is a live bootable Fedora)

Knoppix, Puppy, Slax, etc make good flash drive Linux's.

---

### Post by ironcitypete on 2008-06-30
> **nerd0795 said:**
> Ok thank you :)

No problem I hope it works out for you.

---

### Post by nerd0795 on 2008-06-30
I'm creating a live usb drive (of fedora) using the Fedora LiveUSb creator.  I was gonna try those others one's but Fedora's guide was the easiest.

---

### Post by LaRoza on 2008-06-30
> **nerd0795 said:**
> I'm creating a live usb drive (of fedora) using the Fedora LiveUSb creator.  I was gonna try those others one's but Fedora's guide was the easiest.

Many distros seem to have that ability built in nowadays. Slax has a script that does it for you :-)

---

