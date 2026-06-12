---
title: "Disk encryption in ubiquity for Oneiric"
date: 2011-05-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by twopointfour on 2011-05-07
Hi! I'm an avid Ubuntu user and a web developer at the Electronic Frontier Foundation. I recently wrote a blog post encouraging people to vote for a feature on Ubuntu Brainstorm: [https://www.eff.org/deeplinks/2011/05/help-bring-disk-encryption-ubuntu-live-cd](https://www.eff.org/deeplinks/2011/05/help-bring-disk-encryption-ubuntu-live-cd)

Here's the Ubuntu Brainstorm idea: [http://brainstorm.ubuntu.com/idea/24712/](http://brainstorm.ubuntu.com/idea/24712/)

In the last couple days it has gained hundreds of votes. Lots of Ubuntu users really want this feature because it will greatly improve their security.

I noticed that the Oneiric Feature Definition Freeze is May 26. Any chance that this could get added in the Oneiric feature list? What's the proper protocol for this?

---

### Post by madjr on 2011-05-08
this looks interesting.

maybe you should send it in to the [omgubuntu]("http://www.omgubuntu.co.uk/") guys. They might be interested.

also checking the status of this bug in launchpad would help.

---

### Post by teachop on 2011-05-08
This makes sense to me.  I started an idea a few weeks ago on Brainstorm for a secure wipe prior to install, as a checkbox option.  I worry about old data laying about that is not completely wiped from the prior OS.

That idea was a dud however... Guess you have to advocate for them somehow to build up interest, as it seems important for security.  

Still think that would be good: [http://brainstorm.ubuntu.com/idea/27685/](http://brainstorm.ubuntu.com/idea/27685/)

---

### Post by gnomeuser on 2011-05-08
What exactly is the technical issue with the home directory encryptfs powered encryption.

It seems to be a much nicer solution. You do not require a single password to merely turn the machine on which solves situations such as family machines with several people using the machine while retaining security. You do no experience a slowdown due to encrypting system binaries.

More importantly, this is available on the LiveCD as it is.

---

### Post by juancarlospaco on 2011-05-08
/home encryption is already offered

And...  ALL encryption Slow Down your system and Eats CPU

---

### Post by teachop on 2011-05-08
> **juancarlospaco said:**
> ALL encryption Slow Down your system and Eats CPU
I wouldn't want my computer that way, but options for people are good.  Consider if somebody were to lose a laptop with personal info (say your insurance agent or something), although in that case /home encryption would probably do (or can data be pulled from virtual memory buffers on disk?)...

---

### Post by twopointfour on 2011-05-09
madjr, thanks for the suggestions. I will definitely contact omgubuntu, and I will look into this bug in launchpad.

Home folder encryption with encfs is much less efficient than full disk encryption. The metadata for each file is separately encrypted and requires a separate disk read and crypto operation per-file for stat or readdir. So if you end up with very large directories with lots of files, you can notice a performance hit. Full disk encryption with luks/dm-crypt is blazingly fast and doesn't have to worry about meta data (which also protects your privacy). I have been using Ubuntu with full disk encryption since about 2005, and I have never noticed any performance problems at all.

But more importantly, just encrypting /home is not enough. Sensitive data ends up in your swap partition all the time. Lots of people use things like MySQL databases, the data of which gets stored in /var/lib/mysql. Try this:

```
zcat /var/log/auth*.gz |grep COMMAND
```There's a history of everything you ran with sudo. Other sensitive logs end up in /var/log. Not to mention your user password hashes in /etc/shadow.

In addition to all of this, anyone with 5 minutes of physical access to your computer can add rootkits and keyloggers that run on startup, or trojan any of your binaries. This sort of attack still exists against full disk encryption, but it is a lot harder to do, takes lots of preparation, depends on the system it's done on, and if you're paranoid there are ways to make it not work at all at the cost of convenience.

Using full disk encryption when installing Ubuntu will of course not happen by default. It should just be added as an option in the Live CD installer in people want to use it. Windows 7 has BitLocker full disk encryption included. The new version of Mac OS X (Lion) that's coming out soon also will include full disk encryption out of the box, replacing their less secure home folder encryption in current versions. Ubuntu is at risk of lagging behind the two major proprietary OSes in this important security feature.

---

### Post by twopointfour on 2011-05-09
Also, I just posted a comment on the ubiquity bug ticket: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/245399](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/245399)

---

### Post by needhelpplease on 2011-08-03
> **juancarlospaco said:**
> And...  ALL encryption Slow Down your system and Eats CPU

Nonsense.  Can you back that up with anything?  The filesystem already does checksums on blocks that it writes.  Encryption operations are just slightly more complex than checksums.  Modern CPUs are optimized specifically for encryption.  In fact modern CPUs have AES cipher rounds built in to the hardware, so encrypting a block is probably nearly the same speed as copying without encrypting.

Your statement was probably true five or ten years ago but is absolute nonsense today.  I can't imagine why people are still willing to accept ridiculous claims like that with no supporting evidence.

Here's an [analysis of contemporary CPUs]("http://www.tomshardware.com/reviews/clarkdale-aes-ni-encryption,2538-9.html") using AES instructions.  Conclusion: AES instructions are so fast that any slow-down caused by doing encryption is irrelevant.  I'm sure the [AES instructions]("http://en.wikipedia.org/wiki/AES_instruction_set") will soon be standard on all CPUs.  And even without the AES instructions, AES itself is very fast.

---

