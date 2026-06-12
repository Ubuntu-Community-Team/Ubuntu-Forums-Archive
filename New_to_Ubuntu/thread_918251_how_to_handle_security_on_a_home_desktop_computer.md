---
title: "how to handle security on a home desktop computer"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by grashdur on 2008-09-12
Please excuse me for asking what may be a lightning-rod question — I want to better understand this issue, but books and websites have not really satisfied my curiosity. :confused: So I’m inviting input from anyone who would like to chime in on this: 

I’ve heard that if an experienced hacker *wants* to break into a computer, it’s pretty hard to stop him/r regardless of what operating system you use. I’ve also heard that Linux is inherently easier to defend than Windows, as it’s less susceptible to malware when used properly. But for a home computer used by two people: 

1.** How much safer are one’s personal files in Ubuntu/Linux than in Windows XP from hackers, viruses and other malware that install keyloggers, etc.?**  (I keep seeing more viruses nowadays on my Windows virus scans, and I know that enterprising individuals are using them as a money-making opportunity, including more people overseas now, in places such as Russia and China.)
2. **Is a dual-boot computer (Ubuntu/Windows) more vulnerable than Linux-only** (even if Ubuntu is running most of the time)?
3. **How much safer are one’s personal files in the /home partition as opposed to the /My Documents folder on the Windows side** while running Ubuntu?
4. **How useful are encrypted volumes on a desktop computer** (that nobody else has physical access to)?  (Strong encryption can be circumvented by a keylogger, but how easily can one be installed from outside onto Ubuntu?)
5. ** If you use encrypted volumes (such as with Truecrypt), is there any easy way to use them over a home computer network?**  (Truecrypt does not allow you to open volumes located on another computer, so you end up copying a volume back and forth over the network in order to use it on different computers — this creates the possibility of data loss if you make a mistake in copying the volume file, and I would think the constant re-copying could eventually corrupt the file.)
6. **How necessary/useful is a firewall?** ](*,) (Some people say you don’t need one on Ubuntu unless setting up a local server; others say you do need one.)
7. **Which firewall to use?**  (Firestarter seems to be the most popular, but Andrew & Paul Hudson in *Ubuntu Unleashed* only recommend lokkit and gnome-lokkit). (The book is rather technical for me but interesting.)

---

### Post by t0p on 2008-09-12
1.  I'd say your files are infinitely safer on a Linux box.

2.  The Windoze half of the dual-boot is vulnerable.  As far as I know, dual-booting doesn't endanger the Linux side.

3.  Again, the files on the Linux box are infinitely safer.  If a Linux virus *did* attack your computer, the /home directory would be the part of the filesystem most at risk, because the virus would not need root access to trash it.  But that's theoretical, as there aren't any Linux viruses "in the wild".

4.  Encrypted files are great, but I see their value in their security against intruders who *do* have physical access to the machine.  The intruder could bypass the computer's login/password security by booting a Live CD or by physically removing the hard drive - but would then be faced with encrypted files that he'd need a super-computer to crack.  But then again, maybe the intruder will plant that keylogger you're worried about...

5.  I don't know.

6.  I don't think a firewall is at all necessary.

7.  UFW is currently the recommended firewall gui for ubuntu.

---

### Post by handydan918 on 2008-09-12
Wow! Lot's of good questions...

> **grashdur said:**
> 

1.** How much safer are one’s personal files in Ubuntu/Linux than in Windows XP from hackers, viruses and other malware that install keyloggers, etc.?**  (I keep seeing more viruses nowadays on my Windows virus scans, and I know that enterprising individuals are using them as a money-making opportunity, including more people overseas now, in places such as Russia and China.)
While there really is more to security than just the O/S, if you are comparing a default XP install to a default Ubu install, there is really no comparison. Ubu is safer by far.

2. **Is a dual-boot computer (Ubuntu/Windows) more vulnerable than Linux-only** (even if Ubuntu is running most of the time)?

No, the presence of a windows partition does not present a vulnerability in and of itself.

3. **How much safer are one’s personal files in the /home partition as opposed to the /My Documents folder on the Windows side** while running Ubuntu?

well, it is certainly easier to back them up properly, and if you do that they are certainly safer.

4. **How useful are encrypted volumes on a desktop computer** (that nobody else has physical access to)?  (Strong encryption can be circumvented by a keylogger, but how easily can one be installed from outside onto Ubuntu?)

If you are behind a NAT router and have no extraneous ports open, no one is likely to get into your machine. That said, I have had attempts made to brute-force port 22 (ssh) every time I have opened that up on a net-facing machine. Use good passwords! Disk encryption is probably not all that great if you really have perfect control over physical access.

5. ** If you use encrypted volumes (such as with Truecrypt), is there any easy way to use them over a home computer network?**  (Truecrypt does not allow you to open volumes located on another computer, so you end up copying a volume back and forth over the network in order to use it on different computers — this creates the possibility of data loss if you make a mistake in copying the volume file, and I would think the constant re-copying could eventually corrupt the file.)

Not certain about this one.

6. **How necessary/useful is a firewall?** ](*,) (Some people say you don’t need one on Ubuntu unless setting up a local server; others say you do need one.)

this is one of the great points of debate and miscommunication. There IS a firewall on Ubu, the question is "Do you want to be able to configure it?"
That leads into your next question, which could be rephrased as "Which configuration tool should I use?
7. **Which firewall to use?**  (Firestarter seems to be the most popular, but Andrew & Paul Hudson in *Ubuntu Unleashed* only recommend lokkit and gnome-lokkit). (The book is rather technical for me but interesting.)

The only answer to this question is "Which one do you like?" 

Hope this helps, and I'm sure many others will weigh in, too.

---

### Post by cariboo on 2008-09-12
The only way any malware of any sort is going to be installed on your computer is if you install it yourself as root. As a regular user you don't have any rights to install any software on the system except in your home directory.

On a bone stock Ubuntu setup there are no ports open to the outside world so there really isn;t any need for a firewall. The default firewall installed is ufw, by default it is disabled. To learn more about ufw in a Applications-->Accessories-->Terminal type:

```
man ufw
```

This will give you all the information you want to know about setting it up. I did see this morning that there will be a gui for ufw in the next release of Ubuntu due out at the end of October. Another option that will be available in version 8.10 is an encrypted Private folder in your home directory, as it is right now the only way to create it is from the command line, but there is a gui in the works to set it up also.

Jim

---

