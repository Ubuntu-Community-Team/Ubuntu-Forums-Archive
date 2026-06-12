---
title: "Ubuntu cannot find my hard disk"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by Drowz0r on 2011-10-23
Good day Ubuntu-ites.

I've installed Ubuntu on a tablet PC of mine and really liked the results. It seems to support everything I use and it runs everything exactly how I wanted so I figured, why not change everything over?

I've changed a family member's machine over and that worked fine but now I'm swapping **my** machine over.

I'm on the "Installation type" screen of "Install Ubuntu 11.10" (64 bit) and cannot see any drives. Clicking any of the buttons except quit or back do nothing. Clicking "Install Now" gives an error: "No root file system defined". On clicking "Install Now" again as I am impatient and lacked immediately fixing options... it just crashed completely and is now chilling out on my other monitor screen while I type this.

My machine uses a SATA HDD while the other machine uses an IDE HDD. Could this be the issue? Everything else seems to be working just dandy, even my dual screen displays aren't causing the slightest bit of fuss and worked right off the bat.

Can anyone help here or know what information I need to provide before I can get help? :(

My motherboard is:

P5N32-E SLI from ASUS. Also has "AI Lifestyle" and E2929 on the manual if that helps. I've still got my driver disks for both my motherboard and GFX card but they seem quite Window's orientated.

Help me obi-wan ken obi, you're my only hope :O

---

### Post by Swagman on 2011-10-23
Do you have multiple sata drives ?

If so you might be experiencing the DMRAID bug. I thought they had cured that though.

Boot into a live session and issue the command

```
sudo apt-get remove dmraid
```

Then try the install

---

### Post by Drowz0r on 2011-10-23
Hello there

Thanks for the quick reply. I'm not running multiple SATA disks, just one 320MB disk but I was previously running multiple disks. Perhaps there is something left over from that.

I'll give it a shot and let you know if it works...

---

### Post by Drowz0r on 2011-10-23
Back.

Well I did the command exactly how you wrote it and it worked fine. Said it could not remove the thingy but disabled it (as it was running off a read-only DVD). It then found the disk without any issue and I installed ubuntu. Ta da!

BUT

Once completely finished, it wanted to reboot and for me to remove the disk. I did it exactly how instructed and how I've done it on (now 3) other machines (just made a laptop ubuntu while trying to get it on my computer) but on loading back up it gave an error in the BIOS:

HARD DISK NOT FOUND INSERT SYSTEM DISK or something like that. Maybe HARD DISK FAILURE INSERT SYSTEM DISK.

The disk itself is actually fine so I have no fears of a hardware fault issue.

I did notice my BIOS boot up as normal and my RAID array was still showing before it got to where the ubuntu loader would kick in.

Is there something else that is needed? With Windows XP I had to load my RAID drivers on via a floppy disk after a prompt in the Windows XP installer asking if I was going to load any 3rd party RAID drivers. This was actually built into the Windows XP installer though so I'm not sure how I would do something like this for ubuntu. I'm guessing the RAID drivers are set for a 32-bit Windows XP and not a 64 bit ubuntu?

Any ideas?

---

### Post by cryptotheslow on 2011-10-23
I'm confused. Why would you want or need RAID enabled with only one hard disk installed in the machine?

Is there an option in the BIOS to disable RAID on the motherboard?

---

### Post by Drowz0r on 2011-10-23
Hello

As stated, I **previously** had two hard disks in this machine which required a RAID array. ("I'm not running multiple SATA disks, just one 320MB disk but I was  previously running multiple disks. Perhaps there is something left over  from that.") It used to be 320MB x2 but now it's x1 after one disk failed a while ago. This remaining disk is fine.

I never really found a way to disable the RAID array and Windows wouldn't detect it without a RAID array either, even if there was only one disk.

I chose the mirror array at the time as I had a lot of important information on the PC. After one disk failed, I did intend to replace the disk but my uni course and such finished so there was no need to be as paranoid with my data so I now only actually require 1 HDD.

I can't see any method of removing the array at the moment. I'll take a look through the BIOS again but the array seems to trigger post-bios. I'm reading options on turning RAID off and it gets detected like an IDE drive but I'd rather not lose the speed there.

---

### Post by cozumel on 2011-10-23
I agree with cryptotheslow.  You should not have RAID enabled in the BIOS.  You should disable that and maybe also the configuration settings of the SATA controller within the BIOS.

That might be the reason the original installation failed.

While you are in the BIOS (and this just a personal preference), I recommend disabling all components that are not in use.  You can always edit at a later.

And since we are talking about the BIOS, have you checked for updates that fix any known issues related to HDDs or enable new HDD features?  (again that is personal preference)

---

### Post by Drowz0r on 2011-10-23
Well I disabled the feature in the advance settings of the BIOS to detect SATA but my RAID Array thing still pops up after the bios boot. It seems some how independent from the BIOS. I went into the RAID thing and deleted my array but there were very limited options and I couldn't get rid of this Raid Array detector thing.

---

### Post by cryptotheslow on 2011-10-23
Found the manual for that board.....  phew your BIOS has a lot of option!
[http://dlcdnet.asus.com/pub/ASUS/mb/socket775/P5N32-E%20SLI/e2929_P5N32-E_SLI.pdf](http://dlcdnet.asus.com/pub/ASUS/mb/socket775/P5N32-E%20SLI/e2929_P5N32-E_SLI.pdf)

Anyway.....

On Page 28 of the PDF
 - Serial-ATA Configuration
RAID Enabled  [Disabled]


That I believe is the setting you need.

---

### Post by Drowz0r on 2011-10-23
I did check for BIOS updates a little while ago but none of the safe BIOS updaters I found seemed to work. I've always been heavily warned against updating it. A kind of, "only do it if you absolutely have to" but given the right information I'd give it a shot, considering upgrading to Windows 7 is like £80. That being said, this RAID Array detector doesn't seem to be a part of the BIOS itself per-say. The BIOS fires off quite happily and then a "Detecting RAID array..." thing pops up and nothing I do to the BIOS makes a difference to it, the Raid array detector has it's own boot menu too.

---

### Post by cozumel on 2011-10-23
> **Drowz0r said:**
> I can't see any method of removing the array at the moment. I'll take a look through the BIOS again but the array seems to trigger post-bios. I'm reading options on turning RAID off and it gets detected like an IDE drive but I'd rather not lose the speed there.I don't use your motherboard but just did a quick check.

Your SATA RAID is controlled by the NVidia Mediashield RAID controller.  To vhange the settings you need to enter BIOS and go to:
Advanced Menu > Onboard Device Configuration > Serial-ATA Configuration
RAID Enabled - Change to disabled
Make sure that SATA 1/2/3/4/5/6 have all become greyed out and/or changed to disabled.

---

### Post by cozumel on 2011-10-23
Also, just checked and BIOS version 1601 includes > Patch it might be unable to install certain Linux OS on this motherboard Which BIOS are you running?

---

### Post by cozumel on 2011-10-23
> **Drowz0r said:**
> That being said, this RAID Array detector doesn't seem to be a part of the BIOS itself per-say. The BIOS fires off quite happily and then a "Detecting RAID array..." thing pops up and nothing I do to the BIOS makes a difference to it, the Raid array detector has it's own boot menu too.That is because the controller is not a part of of LGA775 Intel spec.  It is an add-on that Asus decided to install as an extra (Asus specialize in this and do it brilliantly in the most part).  The NVidia controller setup is however incorporated within the BIOS which was developed in partnership with Award to be used with these particular series of Asus motherboard.

Hope that makes sense.

Edit: @cryptotheslow - I didn't mean to hijack any advice you were giving.  Just to give extra information.  I hope I have not insulted you or caused any offence.  Not my intention at all.

---

### Post by Drowz0r on 2011-10-23
> **cryptotheslow said:**
> Found the manual for that board.....  phew your BIOS has a lot of option!
[http://dlcdnet.asus.com/pub/ASUS/mb/socket775/P5N32-E%20SLI/e2929_P5N32-E_SLI.pdf]("http://dlcdnet.asus.com/pub/ASUS/mb/socket775/P5N32-E%20SLI/e2929_P5N32-E_SLI.pdf")

Anyway.....

On Page 28 of the PDF
 - Serial-ATA Configuration
RAID Enabled  [Disabled]


That I believe is the setting you need.

Ah-ha. Yes, I have turned this off already but it made no difference, it still went through a RAID array detector thing.

So, I completely turned off my Serial-ATA Configuration detection thing and it stopped comming up... unfortunately it didn't find my hard disk at all in ubuntu then (duh!).

SO I've turned it back on but that seems to have cleared the RAID array detector prompt thing. (Did I just turn my SATA off and on again? ;) )

I'll give the ubuntu install another shot and I'll remember that sudo...apt...get.. terminal command you gave me and I'll get back to ya~

I'll find my BIOS version too...

---

### Post by cozumel on 2011-10-23
Just read this on NVidia forums:
> Disable Raid in BIOS then boot up.

Open Nvidia Control Panel, Dynamic Bios Access. Select "periferials" under the Avialabe BIOS Pages (you'll see RAID is enabled)and disable the RAID on the SATA Device control...Reboot.And cross-referenced it in Toms Hardware forum and it seemed to work.

---

### Post by cryptotheslow on 2011-10-23
> **cozumel said:**
> 
Edit: @cryptotheslow - I didn't mean to hijack any advice you were giving.  Just to give extra information.  I hope I have not insulted you or caused any offence.  Not my intention at all.

No offence taken :D Whole point of a discussion forum is for people to dive in and help - and you're giving far more detailed response than I would have :D

---

### Post by Drowz0r on 2011-10-23
Well disabling the whole SATA controller and turning it back on seemed to work. Must have flushed out any previous settings. I did try and disable the RAID stuff only in the BIOS but it didn't seem to make any difference. Perhaps updating the BIOS and then disabling the RAID stuff would have fixed it though. I guess it's a bug or sommat.

Help is much appreciated. Who said Linux was too complicated? :P

That makes four machines having a successful install, one to go. Now to convince my friends to convert! :p

Thanks again :D

---

