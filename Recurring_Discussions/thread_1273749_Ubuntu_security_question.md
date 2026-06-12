---
title: "Ubuntu security question"
date: 2009-09-23
forum: Recurring Discussions
---

### Post by punkybouy on 2009-09-23
Tonight I tried the 9.04 64 bit live CD which worked well but much to my surprise it was able to access my current hard drive running 32 bit 8.04 LTS and read any file I wanted.  What good does it do to have a "secure" operating system when anyone with a live cd can come along and boot with it and read files off the hard disk?
Am I missing something or would the only way to secure the hard disk be to encrypt the drive with the alternate CD?
Thanks for the help.

---

### Post by marshmallow1304 on 2009-09-23
BIOS password.

---

### Post by QIII on 2009-09-23
Encrypt, BIOS password, HDD password, file privileges.  Take your pick.

Physical access is the mother of all security risks.  You had physical access.

---

### Post by wojox on 2009-09-23
> **QIII said:**
> Encrypt, BIOS password, HDD password, file privileges.  Take your pick.

Physical access is the mother of all security risks.  You had physical access.

+1 You will never be able to completely stop anyone with physical access to your box from breaking into it.

---

### Post by Compintuit on 2009-09-23
> **wojox said:**
> +1 You will never be able to completely stop anyone with physical access to your box from breaking into it.

Not quite true, but a good assumption. The problem is, even if you encrypt, all someone has to do is put a keylogger on the keyboard. Then they get your key, and you're encryption is useless.

So unless you're confident no one is looking over your shoulder, and your keyboard doesn't have a keylogger on in, physical access = no security.

---

### Post by scrooge_74 on 2009-09-23
If I steel your box, forget about security.

I'll just wipe the HD clean and start a new :p

Or if I want your data take it out of it and hook it up to another PC.

What you really want is security over the networks and the internet which you get the moment you start using linux

---

### Post by overdrank on 2009-09-23
Moved to  Recurring Discussions

---

### Post by hoppipolla on 2009-09-23
> **punkybouy said:**
> Tonight I tried the 9.04 64 bit live CD which worked well but much to my surprise it was able to access my current hard drive running 32 bit 8.04 LTS and read any file I wanted.  What good does it do to have a "secure" operating system when anyone with a live cd can come along and boot with it and read files off the hard disk?
Am I missing something or would the only way to secure the hard disk be to encrypt the drive with the alternate CD?
Thanks for the help.

I know to be honest I LOVE this! I was really quite proud of myself when I finally sussed it ._.  lol

Because I was like "Yes I can hack into almost any machine now as long as I'm sitting at it!" lol xD

Encrypted filesystem is your best bet if you want to stop it though. BIOS passwords work until someone opens the case and resets the CMOS, but of course that's a fairly big ordeal! :)

---

### Post by punkybouy on 2009-09-24
All good input!  Thanks for the replies.

---

### Post by punkybouy on 2009-09-24
Jaunty's alternate cd has the option of just encrypting your personal/home folder which seems like a reasonable option.  I tried encrypting the whole drive but the kernel would not install. That could have been a faulty CD so I downloaded another.  Using the PC to write this.  64 bit is nice and stuff I thought would be difficult to install like Skype and Flash were a breeze.

---

### Post by NCLI on 2009-09-24
This should be merged with that other thread...

---

