---
title: "Ubuntu 9.1 - How to change password"
date: 2018-05-30
forum: New to Ubuntu
---

### Post by bighatnohorse on 2018-05-30
A bit of history;  
I've never used Ubuntu
I installed an old 9.1 version of Ubuntu over a Windows XP pro operating system (I had the old Ubuntu 9.1 CD laying around) - because I am getting rid of that machine and didn't want any left over XP stuff.
Yes, I let Ubuntu "wipe out" Windows during the install.

I set a password during the install.
Now, I want to remove the password before I give the machine away.
Yes, I know what the password is.

How do I access and remove the password so that anyone can use the machine?

---

### Post by QIII on 2018-05-30
Hello!

9.10 is many years past End of Life (EOL).  As such, it has long since ceased to receive updates -- including security updates -- and effectively creates a paperweight of the machine.  Further, the high-level formatting of an installation does not actually remove most of the physical and detectable signature of the stored files.  If you give it away as it is, a moderately skilled Linux user could easily recover and use much of the information still on the disk.

You would be better off, and safer, if you "zeroed out" the drive by deliberately overwriting the entire disk.  The recipient would thus also not be unwittingly given a very unsafe operating system.

You may use the installation media you have to boot the machine in a Live session, open a terminal emulator and issue the command

```
dd if=/dev/zero of=/dev/sda
```

to do that.

Be aware that:

1.  "sda" may need to be substituted with a name appropriate to the system.
2.  This method is suitable for this purpose, but carries the risk that a sufficiently capable agent with sufficiently sophisticated tools may be able to recover some data based on the faint residual charge on the physical particles of iron oxide that make HDDs work.  Unless you think organized crime or a State actor will take an interest in your machine, there is little worry there.

If you have any questions, please feel free to ask.  But please do not give the machine away in its current state.  It isn't safe for you and it isn't safe for the recipient.

Someone else can install the OS of their choice.

---

### Post by coffeecat on 2018-05-30
**Note:** I spent so much time typing this below, that I was ninja'd by QIII making similar points but in a more eloquent way. Since these are fundamentally important points, I'll emphasise them by posting my post anyway.

> **bighatnohorse said:**
> 
I installed an old 9.1 version of Ubuntu over a Windows XP pro operating system (I had the old Ubuntu 9.1 CD laying around) - because I am getting rid of that machine and didn't want any left over XP stuff.
Yes, I let Ubuntu "wipe out" Windows during the install.


If you didn't zero out or randomise the hard disk before installing Ubuntu, there is likely to be plenty of "left over stuff" from Windows that will be recoverable using data recovery software. Some of your old Windows files will have been overwritten - much will not have been. If you had personally sensitive information saved by Windows XP, then you really need to erase the hard disk properly.

Second point - Ubuntu 9.10 is so old that palaeontologists find interesting fossils in it. It is utterly out of date and a security risk if connected to the internet. I understand that you are not going to use it yourself, but giving the machine away with such an obsolete operating system for others to use is irresponsible. I would hope that no one here will help you with such an enterprise. 

If you really want to to be altruistic by giving away an old but usable computer, and you also want to protect any information that may still be lurking on the hard drive at present, I suggest you:

[list=1][*]Use something like dban to securely erase the hard drive.
[*]Install an up-to-date version of Ubuntu, or one of the lighter flavours, to the machine.[/list]

Forum members here will be able to advise you with each of these steps if you need.

---

