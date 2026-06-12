---
title: "Root access given when fstab not mounted properly"
date: 2010-08-20
forum: Recurring Discussions
---

### Post by sinurge on 2010-08-20
Need understanding on this issue!
 
I made a mistake while editing the fstab on maverick alpha3. When i rebooted it told me about the issue but gave me M - go to command line and fix the issue (Ctrl + D) to continue post that and 'S' to go to recovery mode.
 
If you choose 'M' it immediately sets to root access.!!!!
 
Is this a correct approach. I think it should go exit and go to command line access but not to root. Root access can be used to change anything.

---

### Post by movieman on 2010-08-20
> **sinurge said:**
> Root access can be used to change anything.

That's rather the point: what if you screw up the system so badly that you can't sudo in order to fix it?

I'm pretty sure Redhat has an option to require the root password before letting you access the machine at that point, I don't know about Ubuntu since it doesn't have a root password.

Remember, if a bad guy is sitting at the keyboard, they can insert a Live CD or USB stick and boot off of that, so it's not really a security hole. The only way to protect against local attacks of this kind is to encrypt the disk.

---

### Post by FuturePilot on 2010-08-20
I think you should be more worried about that fact that a malicious person has physical access in the first place. And even if it didn't drop you to a root prompt in that situation it wouldn't matter anyway. Physical access == game over.

---

### Post by bodhi.zazen on 2010-08-20
Moved to recurring discussions.

Physical access is root access and the only potential solution is to perform an encrypted install.

See also :

[https://wiki.ubuntu.com/SecurityTeam/Policies#Reasonable%20Physical%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Reasonable%20Physical%20Access)

---

### Post by del_diablo on 2010-08-20
> **sinurge said:**
> Need understanding on this issue!
 
I made a mistake while editing the fstab on maverick alpha3. When i rebooted it told me about the issue but gave me M - go to command line and fix the issue (Ctrl + D) to continue post that and 'S' to go to recovery mode.
 
If you choose 'M' it immediately sets to root access.!!!!
 
Is this a correct approach. I think it should go exit and go to command line access but not to root. Root access can be used to change anything.

You made a mistake on fstab?
How about opening nano or vim, and fixing it?

---

### Post by saulgoode on 2010-08-20
> **sinurge said:**
> I made a mistake while editing the fstab on maverick alpha3. When i rebooted it told me about the issue but gave me M - go to command line and fix the issue (Ctrl + D) to continue post that and 'S' to go to recovery mode.
 
If you choose 'M' it immediately sets to root access.!!!

If you've [password protected]("http://www.makeuseof.com/tag/how-to-password-protect-grub-entries-linux/") the recovery mode in GRUB, is the GRUB password required?

---

### Post by sinurge on 2010-08-21
> **del_diablo said:**
> How about opening nano or vim, and fixing it?

I was headed that way but point is drop me to a login prompt. i will login use sudo and get it down. my only concern was about dropping me to root access thats all

---

