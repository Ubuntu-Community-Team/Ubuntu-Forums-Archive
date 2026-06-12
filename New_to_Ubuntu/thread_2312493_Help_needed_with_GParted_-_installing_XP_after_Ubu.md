---
title: "Help needed with GParted - installing XP after Ubuntu"
date: 2016-02-04
forum: New to Ubuntu
---

### Post by sean109 on 2016-02-04
I've currently just got Ubuntu 14.04.3 installed on my laptop.

I want to mulitboot with Ubuntu and Windows XP. I've downloaded and burned XP to a CD.

The XP installer needs me to create a partition for it to install, but GParted won't let me resize my /dev/sda2 partition.

I saw something online that said you can't resize the partition you're currently using.

How do I resize my main partition and create a new one for XP?

---

### Post by grahammechanical on 2016-02-04
We use GParted from a Ubuntu live session. It will already be installed. A piece of advice? XP might need to be put in a partition at the start of the disk. I cannot say that is for sure but maybe.

---

### Post by steveo314 on 2016-02-04
Use the partition tool in the XP install. But you are going to want to install XP followed by Ubuntu unless you know how to update grub from a liveDVD.

---

### Post by monkeybrain20122 on 2016-02-04
XP is long dead and should be buried. How long are people still going to run this antique? If you must put it in a VB and cut off internet connection.

---

### Post by steveo314 on 2016-02-04
XP isn't dead. Just because the don't support it anymore doesn't mean anything. I'd rather use XP than Vista or 8. I'd rather use 2000 than Vista or 8. 

As long as the laptop isn't a couple years old or newer XP will run just fine.

---

### Post by monkeybrain20122 on 2016-02-04
> **steveo314 said:**
> XP isn't dead. Just because the don't support it anymore doesn't mean anything. I'd rather use XP than Vista or 8. I'd rather use 2000 than Vista or 8. 

As long as the laptop isn't a couple years old or newer XP will run just fine.

Here we don't support eol OSes, even Ubuntu ones. OP is asking the equivalence of how to install Ubuntu 8.04 and it shouldn't be supported. Running an insecure OS with contact to the internet poses a risk not just to yourself, but others as well as your machine can be hijacked.  XP is dead, get used to it.

---

### Post by steveo314 on 2016-02-04
I'd say Vista is dead before XP. And you can't compare Ubuntu to Windows. You can compare Debian to Windows. Ubuntu has too many releases to compare it to Windows. EOL is just a flag. EOL = use at own risk.

[http://www.w3schools.com/browsers/browsers_os.asp]("http://www.w3schools.com/browsers/browsers_os.asp")

---

### Post by monkeybrain20122 on 2016-02-04
No one tells you to use Vista. I don't think EOL Debain should be supported here either, and I doubt that it would be supported on Debian's forum.

---

### Post by Vladlenin5000 on 2016-02-04
> **monkeybrain20122 said:**
> Here we don't support eol OSes, even Ubuntu ones. OP is asking the equivalence of how to install Ubuntu 8.04 and it shouldn't be supported. Running an insecure OS with contact to the internet poses a risk not just to yourself, but others as well as your machine can be hijacked.  XP is dead, get used to it.

+1

Exactly. It's the same problem regarding 'herd immunity' that a certain group of otherwise intelligent people in the US doesn't seem to get.

Regarding XP we're not discussing its relative merits. We're simply pointing out that XP now is huge security HOLE and that has the potential to affect many other people not just the stubborn users that won't let go. Hadn't Microsoft pulled the plug on XP and we wouldn't be having this conversation but because they did nobody should be running such a relic in this day and age. Period.

---

### Post by v3.xx on 2016-02-04
> **Vladlenin5000 said:**
> +1

Exactly. It's the same problem regarding 'herd immunity' that a certain group of otherwise intelligent people in the US doesn't seem to get.

Its the US is it.  A very intelligent reply.  Smells like flame bait, lets find out :)

---

### Post by sean109 on 2016-02-04
Thanks for the replies.

I put my Ubuntu disc in and managed to split my main partition into 2 using GParted which is what I wanted.

However, now when I start the XP installer it says "No valid system partitions were found. Setup is unable to continue."

I made my new partition an NTFS file system as recommended on the Windows website.

Any ideas?

---

### Post by oldos2er on 2016-02-04
Microsoft no longer supports Windows XP, and it is beyond the scope of ubuntuforums.org to do what Microsoft doesn't. 

Thread closed.

---

