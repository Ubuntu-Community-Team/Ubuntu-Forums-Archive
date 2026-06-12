---
title: "IBM T22 Laptop- keeps locking up on install"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by andy128 on 2008-04-23
Greetings-
First post and first time ubuntu user.  I have installed it on my 800 mhz desktop and did so with out a hitch and it is going well.

But when I try to do the same on my IBM Thinkpad T22 800 mhz with 256mb ram- it frequently locks up.  This is a fresh install(have wiped drive with Dariks Boot and Nuke).

Does this particular machine have problems or had problems in the past been experienced with this machine model?

Thanks in advance -

Andy

---

### Post by nicedude on 2008-04-23
Good to see your desktop went well and your right on with the boot-n-nuke thats my favorite. But it might be the 256mb of RAM thats causing it or if not its probably graphics related. Can you tell us what version Ubuntu disk you have & also whether it was the LIVE or ALTERNATE type.

---

### Post by spiderbatdad on 2008-04-23
You are a little shy in RAM. Maybe xubuntu is a better choice. Either way try booting  with parameters lapic pci=routeirq

---

### Post by andy128 on 2008-04-23
Thanks for the quick reply.  I have ubuntu 7.10.  It is true that the desk top had more ram and is working fine.  

As to the suggestion:
Either way try booting with parameters lapic pci=routeirq 

I am afraid at this point in my ubuntu infancy, I will need more instruction to accomplish this.  

Additional note- the live cd did install but froze too at one point prompting a manual shut down/re-boot.

Andy

---

### Post by spiderbatdad on 2008-04-23
From the installation options screen on the live cd, press F6. You will see a line begining with the word kernel at the bottom of the screen, At the end of that line "ro --quiet splash." Delete the words "--quiet splash." Replace with "lapic pci=routeirq" After installation you will need to edit a file called /boot/grub/menu.lst to the same effect. Assuming those parameters works for you. They are what I use on my T-30. If those parameters don't work, try "noapic nolapic" (no quotes)

---

### Post by andy128 on 2008-04-23
Thanks- I will give it a go.

One correction though.........I thought I had more ram on the desktop but I only have 256.  Seems to hum along just fine.

I will post tomorrow if it was a success or not.

Cheers-
Andy

---

### Post by andy128 on 2008-04-24
I used - noapic nolapic - as instructed and no love.  Froze on install at 56%.

Also tried - lapic pci=routeirq - with no luck either.

I believe that it is in fact Ubuntu 6.06 because when I go to System and then click "About Ubuntu" it comes up with a screen that says "Thank you for your interest in Ubuntu 6.06......"

So I shall nuke the disc again and try XUbuntu............

Andy

---

### Post by andy128 on 2008-04-24
...............still no luck with this.  Doing an integrity check before installing on laptop showed (1) checksum mismatch

This was not the case for the desktop using the same disc.

Any suggestions?

Andy

---

### Post by spiderbatdad on 2008-04-24
A checksum error isn't a good disk. I even had a disk once that verified, but I could not get it to install. In frustration I downloaded another iso and burned a new disk...and finally got the system on an old HP laptop. 
There are many posts on Launchpad regarding the T-22, so it is installable. You might also try the parameter all_generic_ide.
Do a google of launchpad T-22 and see if you can find what boot parameters or installation methods have worked for others. I would try slowly burning another iso of xubuntu, as well.

---

### Post by andy128 on 2008-04-24
Thanks- will look into it.

Andy

---

### Post by andy128 on 2008-04-24
How would I implement your suggestion of the...

You might also try the parameter all_generic_ide.


Andy

---

