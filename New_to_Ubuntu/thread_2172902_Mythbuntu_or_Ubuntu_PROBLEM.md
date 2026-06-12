---
title: "Mythbuntu or Ubuntu PROBLEM"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by jim_collins2 on 2013-09-07
OK, I have fresh Mythbuntu installed (just a few weeks ago)  FINALLY got everything up and running correctly.  Had only one very minor issue with the update manager popping up daily so I set it to weekly.  Well it popped up and I wanted to install the latest updates.  There seemed to be no issues with the install.  Got the message that I had to reboot for these changes to take effect.  Rebooted and got this crazy message:
GNU GRUB version 1.99-21ununtu3.10
Then in a box covering almost all of the screen is:
Ubuntu, with Linux 3.5.0-40-generic
Ubuntu, with Linux 3.5.0-40-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Ubuntu 12.04.1 LTS, kernel 3.2.0-30-generic (on /dev/sdb1)
Ubuntu 12.04.1 LTS, kernel 3.2.0-30-generic (recovery mode) (on /dev/sdb1)
Ubuntu 12.04.1 LTS, kernel 2.6.32-42-generic (on /dev/sdb1)
   "         "         "       "          "                     (recovery mode)  "
Ubuntu 12.04.1 LTS, kernel 2.6.31-22-generic (on /dev/sdb1)
   "         "         "       "          "                     (recovery mode)  "
Ubuntu 12.04.1 LTS, kernel 2.6.28-16-generic (on /dev/sdb1)
   "         "         "       "          "                     (recovery mode)  "
Ubuntu 12.04.1 LTS, memtest86+ (on /dev/sdb1)

Then outside the box there are instructions on how to make my selection.  I tried them all and got the error:

no such device.....you need to load the kernel first.

When I selected Previous Linux versions i was able to pick:
Ubuntu, with Linux 3.5.0-39-generic

My system started.  The background looked a little different but everything seemed to be there.  After I got up and running I tried update manager again and it said no updates available.  Same thing happens every time I restart.  Now I do not know a lot, but in my recent installation I learned that sdb1 would be HDD 2 and sda1 would be HDD 1.  So why is it saying that my HDD is not the initial HDD?  And most importantly HOW CAN I GET BACK TO NORMAL WITHOUT GOING THROUGH THIS ON EVERY STARTUP?????????  PLEASE HELP ME!!!!!

---

### Post by squakie on 2013-09-07
I don't know if this would help or not, as I've never been in that situation.  It does appear that some how grub is setting up pointing to the wrong device, in which case you could try:

sudo update-grub

This will regenerate the grub config files and I *think* it also scans the drives first to see where things are at.

Since I have been very wrong on some of my posts lately, I hope I'm not leading you astray.  I don't see how running update-grub could possible hurt.  If you'd prefer, you can wait for someone else to post to see their suggestion.

---

### Post by r_avital on 2013-09-07
Jim,

A couple of questions:

1 When the GRUB screen shows up, is the first line inside the box highlighted?  That would be the line that reads "Ubuntu, with Linux 3.5.0-40-generic"

2. Using the arrow up/down keys, can you move the highlight up and down on those options?

3. If you simply highlight the first line, after intentionally moving down and back up, then hit Enter, do you still get the error "No such device?"

4. Is there a counter near the bottom of the screen, outside the box, counting backwards?  What happens if you just wait it out and let it boot up to the default option (which should be the latest kernel installed), do you boot up correctly?

5. regarding this:
> **jim_collins2 said:**
> ...in my recent installation I learned that sdb1 would be HDD 2 and sda1 would be HDD 1.  So why is it saying that my HDD is not the initial HDD? 

I remember you mentioned you had puppy-linux on the same system for maintenance purposes.  When you see your drives identified as sda and sdb, do you see that from puppy-linux or from Mythbuntu?  Because each installation of Ubuntu is likely to identify the **drive/partition on which it is installed **as the first one, which can be confusing.

6. Finally, if you want to eliminate that screen altogether when you  boot up, I'm not familiar with what is and is not available in  Mythbuntu, but if you run Synaptic, can you find grub-customizer and  install it?

Sorry for the silly questions, just want to make sure I have all the details, anything relating to GRUB can be delicate.

I don't want to lead you astray either, but there are ways to avoid the GRUB screen successfully, while steel being able to recall it if you need it (I've done it recently, don't currently remember all the steps, and this is delicate).  I'll look deeper into that and get back to you if no one else comes back with a procedure for that in the meantime.

---

### Post by jim_collins2 on 2013-09-07
Ok, yes, there is a countdown when this starts and if I let it completely countdown then it tries to start the first item on the list.  This results in the previously mentioned error message.  Yes, I can move up and down throughout the items, all seem to give me the same error except the memory tests.  I only used Puppy Linux with the boot CD, I did not install it so this is through Mythbuntu.  I will try the update grub next time I reboot.  It doesn't seem to be making problems after i get into the frontend so I am hesitant to make changes.  I actually unhooked the old harddrive (unplugged the red SATA cable).  It STILL had the same error and still called the only HDD sdb1.  Strange.

---

### Post by r_avital on 2013-09-10
Sorry for the delay, Jim,

Let's try to fix the booting problem first. If you don't have this already, try this boot repair CD from this location:[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

Once you've burned the CD and booted with it, follow the directions on that site, and let's see if you can boot up correctly, with all your HDDs connected.

Once we get to that point, we can talk about configuring the GRUB timeouts so you don't get the grub screen when you boot up.

---

### Post by grahammechanical on 2013-09-10
May I mention what I think about this?

1) The box you are seeing is the standard Grub menu.
2) You have 12.04 on one disk and that uses Grub 1.99 (yes, it is called Grub 2 but it is actually Grub 1.99)
3) You have 12.10 or later on the other hard disk and that uses Grub 2.0.

Grub 2.0 has sub menus. So the recovery mode and previous Linux versions would go in a sub menu called Advance Options for Ubuntu. But Grub 1.99 does not understand the sub menu structure of Grub 2.0 and presents a very messy Grub boot menu.

You can try booting into Linux kernel 3.5.0.39-generic and at the desktop open a terminal and run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

It is clear the 12.04.1 is on sdb with its Grub 1.99 and what you have done is updated 12.04.1 and it most probably brought in a kernal update that had to also update Grub and that put Grub 1.99 back into the MBR of whatever hard disk has boot priority. But you need Grub 2.0 back into the MBR to get rid of this mess of a Grub menu.

By the way, if you select Recovery Mode you can update Grub from the Recovery Menu and Ubuntu 12.04 is now at version 12.04.3 and from 12.04.2 it will have the Grub 2.0 and this mess disappears.

I know. I experienced all this when testing the development branch of 12.10 and Grub 2.0 was first used. Choose one version of Ubuntu to be in charge of the Grub in the MBR and whenever an update switches things around simply boot into your favourite Ubuntu and run those two commands again. To switch things back.

Regards.

---

### Post by jim_collins2 on 2013-09-10
Does anyone see ANY possible issues if I open a new terminal and type [COLOR=#000000][FONT=Ubuntu Mono]sudo update-grub???  I am willing to take that chance, but as I stated earlier, after I get through the booting up and get into the frontend/backend there seem to be no issues.  And thank you again for all help.  I think I will do this at the next reboot.  I'll wipe my old hard drive completely clean and then copy all my recordings before I do so the wife will still love me.[/FONT][/COLOR]

---

### Post by squakie on 2013-09-10
Be sure you boot the correct kernel version (see grahamechanical's post) and have booted off of that, then you *need* to run update-grub.

So, boot the proper kernel image, then YES, open a terminal and do sudo update grub.

---

### Post by jim_collins2 on 2013-09-10
I did that and still got the same error message.  I thought maybe since for some reason it was looking at my new HDD as sdb i would try that, but it said couldn't find or couldn't launch (sorry i am writing this from memory).  I have the installation disk for 12.04.2. can i do the recovery from that disk or do i need something else?

---

### Post by squakie on 2013-09-13
What is your current hardware configuration?  How many drives?  How many internal, how many external?  How were they configured when you installed Ubuntu?  Were there any previous operating systems - especially some other linux flavor - installed previously and if so, how were the drives configured then?  When you installed ubuntu, did you watch were it was installing grub to?  Any other installed OS's on the system?

---

