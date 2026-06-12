---
title: "Killed by Ugrade"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by UbuLambert on 2008-05-26
So I installed the Heron for the ISO image on my old Dell C619. It was just fine, nice and nippy. Great thought I. Shame the FF 3.0 is incompatible with Google Browser Synch but...  That was yesterday. Today I noteced the updates icon on the menu bar thingie. 

After dl and installing the 89 updates, now after a very long wait I get this error message from GNOME, error starting GNOME Setting Daemon, and everythig runs so slooooow.

Help!

---

### Post by drs305 on 2008-05-26
Have you tried rebooting. Normally when I get that message a reboot clears it.

---

### Post by Joeb454 on 2008-05-26
Rebooting normally clears this for me if it ever comes up :)

I'd say it comes up once every few months :)

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-05-26
I had those same 89 updates installed on my Comp. (8.04 Hardy Heron too) and same thing happened. Rebooted and everything went smooth again...very smooth! One thing that I don't get is why you got a GNOME error. Unusual things can happen when unusual things are done!

---

### Post by Joeb454 on 2008-05-26
What's unusual about updating ;)

---

### Post by UbuLambert on 2008-05-26
> **drs305 said:**
> Have you tried rebooting. Normally when I get that message a reboot clears it.

Well yes I did. In fact I've rebooted three or four times now, and I still get the same problem.

This is the error message...(which I had to photograph off the screen as my flash drive is not seen by the file system and I cannot browse my windows network (but I could before the update).
[IMG]http://www.pillowworks.com/test/ErrorMessage.jpg[/IMG]

How to tell which of those 89 updates caused the problem? :confused:

---

### Post by UbuLambert on 2008-05-26
> **Joeb454 said:**
> What's unusual about updating ;)

Quite so. I was hoping that death by update was going to be a think of my Windows past, but maybe not.:rolleyes:

---

### Post by philinux on 2008-05-26
Probably the new kernel. Press esc as soon as grub stage 1.5 appears and select the previous kernel.

---

### Post by UbuLambert on 2008-05-26
No good for me. See the error message here 

[http://ubuntuforums.org/showthread.php?p=5047437#post5047437](http://ubuntuforums.org/showthread.php?p=5047437#post5047437)

---

### Post by UbuLambert on 2008-05-26
Thanks for that pointer philinux, I get three entries on the kernels menu 

Ubuntu 8.4 kernel 2.6.24-16 generic
Ubuntu 8.4 kernel 2.6.24-16 generic (recovery mode)
Ubuntu 8.4 memtest86+

I'll try the memtest86+ one first.

---

### Post by philinux on 2008-05-26
> **UbuLambert said:**
> Thanks for that pointer philinux, I get three entries on the kernels menu 

Ubuntu 8.4 kernel 2.6.24-16 generic
Ubuntu 8.4 kernel 2.6.24-16 generic (recovery mode)
Ubuntu 8.4 memtest86+

I'll try the memtest86+ one first.

After my update today I have 2 lots

2.6.24-17 and 2.6.24-16

Some people have been having problems with version 17.

I would do this.

sudo apt-get update && sudo apt-get upgrade

You might have got only half of todays updates.

---

### Post by UbuLambert on 2008-05-26
SO nothing wrong with the memory. 

The recovery mode kernel offers choices of which I have no knowledge. Other than the obvios choice of "resume normal boot", which I don't expect to get far, but let's give it a whirl.

---

### Post by UbuLambert on 2008-05-26
BTW I'm chatting here in a windows machine, no hope for Heron right now.

---

### Post by UbuLambert on 2008-05-26
After I log in there is a long delay of 30-40 seconds with just a bland desktop. Then a gray rectangle appears top left, eventually after another 30 seconds or so the error is displayed. Meanwhile the task bar thingie is displayed partly on top of the screen and partly below.

Eventually it settles down, but then launching almost anything takes an age.

Also, I'm so new at this game I don't know how to open a console window, which I assume is where I have to issue the command 

sudo apt-get update && sudo apt-get upgrade :(

---

### Post by theDaveTheRave on 2008-05-26
Hi all.

I have a similar issue to this on a semi regular basis, it normally blows out my wifi connection though!

I assume that the system logs all the updates etc, but I don't know where this file would be, it obviously isn't in /var/lg/syslog.  as I've checked there and it seems to only store the details from the "current" session.

This information would be really usefull as I could then remove all the updates and I assume that synaptic will recognise this and find them again a new updates, where I can search through and see which one it may have been that caused my problem!

Cheers in advance for your assistance.

Dave

---

### Post by UbuLambert on 2008-05-26
OK. Found terminal and the sudo commands are executing. Let's see how it goes.

currently, after all the downloading I see

ldconfig deferred processing now taking place

and then my $ prompt. Only the occasional disk access happening, so I guess I have to let it sit, but until when??

---

### Post by philinux on 2008-05-26
> **UbuLambert said:**
> OK. Found terminal and the sudo commands are executing. Let's see how it goes.

currently, after all the downloading I see

ldconfig deferred processing now taking place

and then my $ prompt. Only the occasional disk access happening, so I guess I have to let it sit, but until when??

If you're back at the $ prompt you're done.

Try a restart now.

---

### Post by UbuLambert on 2008-05-26
Progress!
So after following Phil' suggetion and rebooting yet again things are now quite sprightly once again.

But now another oddity. The system tells me there are nin more updates, one of which is version 17 of the kernel. So I said, go ahead and install them. All the buttons on the update manager gray out and the spinning dohicky tells me to wait. But nothing much seems to be happening. Just very occasinal hard drive accesses, and nothing much else. At least I can get online now via a wired ethernet port. Next I'll try the wireless one.

---

### Post by philinux on 2008-05-26
> **UbuLambert said:**
> Progress!
So after following Phil' suggetion and rebooting yet again things are now quite sprightly once again.

But now another oddity. The system tells me there are nin more updates, one of which is version 17 of the kernel. So I said, go ahead and install them. All the buttons on the update manager gray out and the spinning dohicky tells me to wait. But nothing much seems to be happening. Just very occasinal hard drive accesses, and nothing much else. At least I can get online now via a wired ethernet port. Next I'll try the wireless one.

You can try waiting. My guess is the servers are bogged down. These forums are slow today too.

You can do the command below anytime, Just make sure that synaptic, update manager or add/remove are active at the same time.

sudo apt-get update && sudo apt-get upgrade

---

### Post by UbuLambert on 2008-05-26
Thanks again Phil.

Both wires and wireless connections are functioning, but no sign of update manager making progress. I guess I'll just leave it trying for now.

Lambert

---

### Post by UbuLambert on 2008-05-26
> **UbuLambert said:**
> Thanks again Phil.

Both wires and wireless connections are functioning, but no sign of update manager making progress. I guess I'll just leave it trying for now.

Lambert

> **philinux said:**
> You can try waiting. My guess is the servers are bogged down. These forums are slow today too.

You can do the command below anytime, Just make sure that synaptic, update manager or add/remove are active at the same time.

sudo apt-get update && sudo apt-get upgrade

Hmm. Moved from one room to another. Hibernated. And then on restoring from hybernation we are once again back to the Gnome error message.

---

