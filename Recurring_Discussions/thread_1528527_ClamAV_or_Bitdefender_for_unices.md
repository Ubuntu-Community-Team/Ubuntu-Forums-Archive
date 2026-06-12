---
title: "ClamAV or Bitdefender for unices"
date: 2010-07-10
forum: Recurring Discussions
---

### Post by Winalways on 2010-07-10
Which antivirus is more suitable for ubuntu or any linux for that matter. Is clamav more powerful than bitdefender? I mean is clam capable of catching linux virus (if any exists) and bitdefender only windows types?

---

### Post by ex_isp on 2010-07-10
I see the question "do I really need an anti virus in Linux?" a lot!  IMO there are several issues here.  

1.  Though Linux is very hardened and immune to virii (as opposed to Windows), the state of the infection business is always changing.  New exploits are being written every day.  Better to be safe than sorry.  Yes, run an anti virus program.

2.  The BIG reason to use an AV in Linux is social responsibility.  I have been very surprised through the years that this reason is seldom mentioned:
Many file types (audio-visual comes immediately to mind) can be a wrapper, or container.  For example, mpg...if it's only  sound file, it's only  sound file.  When you incorporate a video portion into it, now the mpg is a container holding audio and video (and possibly and a malicious payload too!)  If you are in Linux, you are most likely immune to that infection.  It won't affect you and you may never know of it's harmful content.  Lets say it's  funny video and you forward it to your friends...are THEY on Windows?  If so, you may be responsible for infecting them through negligence.  Again, YES you should run an anti virus program!!!


There are several good ones out there that are free.  I run Clam on 2 machines here, and Avast on 2 others, all running Linux.  BitDefender does have  good rep, but I've found very few comparisons/reports on different AVs on Xnix platforms.  Clam is probably the easiest to use with Linux.  nd Clam has recently had some VERY positive reviews

Help protect your friends in cyberspace.  Be a good netizen, run an anti virus program!!!!!

Your original question but which to use stands, but is less important as most ll of todays AVs will detect things from the Linux side.  The real weakness of AVs is in Windows, where the "trust" model is so weak, and the "drive-by" infections are so fast.

This brings up another reason why Linix OSs have such an advantage.  In Windows, you update you Windows and feel safe.  Did you remember to update Acrobat reader? Flash? Shockwave? ETC.... A recent article (I forget where) indicted that as much of 15-20% of infections today re coming through .pdf files!     Linux has single source updates (or at least all through  single interface)

Winalways, I realize that this is perhaps a bit more of an editorial than an actual answer to your question, and that you probably  are already aware of the majority of my "speech", but I really felt it needed to be said.  :-)

Please, any gurus out there, feel free to comment/critique/slam or validate the above text!

Ex

---

### Post by CharlesA on 2010-07-11
Don't need either unless you are serving files to Windows machines.

---

### Post by ex_isp on 2010-07-11
Or emailing with windows buddies?

---

### Post by Rubi1200 on 2010-07-11
As CharlesA already pointed out:

> Don't need either unless you are serving files to Windows machines. 	

Here are some links that might help:

[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

[https://help.ubuntu.com/community/Antivirus?highlight=%28\bCategorySecurity\b%29](https://help.ubuntu.com/community/Antivirus?highlight=%28\bCategorySecurity\b%29)

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by ex_isp on 2010-07-11
Exactly my point

[https://help.ubuntu.com/community/ScanningEmail](https://help.ubuntu.com/community/ScanningEmail)

---

### Post by lisati on 2010-07-11
A big part of the answer is "personal choice". 

As others have said, it probably matters more if you're likely to be sharing files with Windows users, but that shouldn't stop you checking out your options. Being smart with what you allow on your system (and what you open) is a good idea regardless of your choice of OS.

I have Clam scanning emails on my main server, nothing on my backup machine or the Ubuntu partition on my laptop, and AVG free on the Vista partition on my laptop.

---

### Post by cariboo on 2010-07-11
THis is a recurring discussion. Moved.

---

### Post by McRat on 2010-07-11
IMO, your #1 concern doesn't come from the operating system, but from application software.

If you have any applications that are capable of storing macros/scripts in part of their data format, it does not matter what O/S you have.  You can get infected.

This bypasses the normal "no execute" status of files on Linux.  You open the file in your application, the macro/script launches, then it can do anything that application can, sometimes more.  

So if you receive files from others that are "active data" such as Excel, Word, Adobe, etc, you need to be careful.  In any case, you should always have macro/script execution off if it's an option.  If it's not, you should have A/V software.

---

