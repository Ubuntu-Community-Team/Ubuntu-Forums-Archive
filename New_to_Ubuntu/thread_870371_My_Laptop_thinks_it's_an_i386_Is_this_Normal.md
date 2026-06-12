---
title: "My Laptop thinks it's an i386 Is this Normal??"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by zamm on 2008-07-25
Hello all,
I am _*so much*_ absolute a beginner. Well, I have no idea what I am doing but here goes:
I have a Dell Inspiron 8200 that's about 3 years old. It ran Windows XP Pro/sp2 and I just installed Ubuntu on it. I did away with the XP and let Ubuntu have the whole drive.
My question is that I was trying to install a version of Wine, the windows emulator, and opted for burning it to a disk (the wine download) from another computer because I have no internet connection with the Ubuntu laptop. I chose Wine 1.0.0.i386 because Wine HQ site said that was stable one (from an archive). Then I opened the disk/file in Ubuntu and got the message that there was an error. OK, Put away disk, cannot install, no big deal, but I suppose the question is: Now My laptop with Ubuntu on it believes it is a i386 system, and under all the downloads of third party apps, etc..., all say ( even drivers for wi-fi) that they cannot run on my system because the hardware is that of a i386. Is there anyway of re-setting the system, or going into it to find out what it is? I know it is a Pentium, fairly fast, so I find it hard to believe that it cannot run drivers for windows USB wi-fi, etc...
It just feels like something happened to the system when I tried to load the wine version.
Or, am I making something out of nothing?
I am appreciative of all the members time and consideration.
My Best, Zamm

---

### Post by northern lights on 2008-07-25
It's not like your laptop "thinks" it's a decade old machine.

Ubuntu has no specific version catered to a single x86 architecture. The 32bit version of Ubuntu is compatible with i386 and above.

There are distros with specific 32bit/686 releases, I'm pretty certain Arch does, but it doesn't really matter.

Don't be afraid of not utilizing your comps potential, it's not downgraded in any way.

---

### Post by damis648 on 2008-07-25
This is completely normal.

---

### Post by tjwoosta on 2008-07-25
im a bit confused..


i386 or i686 would be most standard 32bit computers

x86-64 would be 64 bit computers (with 64bit ubuntu)

did you install 64bit ubuntu or 32bit ubuntu?

if you are unsure type this in the terminal to see what version you have installed

```
uname -a
```

---

### Post by steveneddy on 2008-07-26
It's been a while since I messed with 32 bit, but I think the -SMP kernel will give you i686 kernel.

I don't even know if the -SMP kernel even exists for 32 bit anymore, but that's my answer.

Hope it works.

---

### Post by Flyingjester on 2008-07-26
It's perfectly normal, and is mostly likely the architecture you are running.

---

### Post by jamesrfla on 2008-07-26
32 Bit, i386, x86 are all the same.

---

### Post by mikewhatever on 2008-07-26
The message you get from the package manager about i386 etc, is misleadings. It actually means that a repository is unaccessible, which makes sense since you have no internet connection. In short, get connected, and don't worry yourself about i386 stuff.

---

### Post by mcduck on 2008-07-26
> **steveneddy said:**
> It's been a while since I messed with 32 bit, but I think the -SMP kernel will give you i686 kernel.

I don't even know if the -SMP kernel even exists for 32 bit anymore, but that's my answer.

Hope it works.

There are no more specific 686, k7, 686-smp or k7-smp kernels. The generic kernel is used for all 32-bit CPUs and 64-bit kernel for 64-bit CPUs. Both kernels support SMP.

---

### Post by zamm on 2008-07-26
Excellent,
thank you all for the info! All very informative.
And thank you Mikewhatever for clearing up the message from the package manager.
OK, Things are beginning to fall into place slowly.
Next step is some sort of internet connection.
Again, Thanks to everyone.
Cheers, Zamm

---

### Post by steveneddy on 2008-07-26
> **zamm said:**
> Excellent,
thank you all for the info! All very informative.
And thank you Mikewhatever for clearing up the message from the package manager.
OK, Things are beginning to fall into place slowly.
Next step is some sort of internet connection.
Again, Thanks to everyone.
Cheers, Zamm

You're welcome. Keep in touch.

---

