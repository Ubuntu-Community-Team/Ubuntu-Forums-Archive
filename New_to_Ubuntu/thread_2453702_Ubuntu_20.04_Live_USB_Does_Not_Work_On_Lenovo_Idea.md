---
title: "Ubuntu 20.04 Live USB Does Not Work On Lenovo Ideapad S145-15API Type 81UT"
date: 2020-11-15
forum: New to Ubuntu
---

### Post by lambquiet on 2020-11-15
Background

I purchased this laptop on sale back in MAR/APR and thought it would be an amazing upgrade against my 12 year old DELL.

I noted this particular model had an M.2 slot and space for a regular 2.5 inch drive. When I bought this thing, Windows 10 was pre-installed on the M.2, so I slapped a 500 GB SSD laying around and installed Ubuntu.

So fast forward through Social Distancing and eventually the 500 GBs runs out. I get this idea to upgrade to a 1 TB SSD that I picked up on sale and didn't get around to installing.

ENTER THE TERROR

I'll point out that the actual installation of the SSD wasn't the issue. I cloned the original Ubuntu SSD without a hitch. I was going through this task like a boss.

So now I wanted to shrink/move some partitions so Ubuntu could open up that 1 TB to the fullest. I used a 20.04 Live USB that I've used in the past on this very model...I released the DEMON.

When I inserted the USB and rebooted, the Lenovo turned on to a black screen. I didn't proceed to GRUB as I expected.  Weird.

I hit Fn and F2 and the Lenovo permit me to get into the bios. Couldn't figure out where this Live USB was on the boot sequence...strange.

I Google this problem and learn that the USB has to be set up a certain way, so I install RUFUS on the Windows. I have my done up Ubuntu Live USB to try again. I plug the USB in, I got into the BIOS, I can see the drive, I change the sequence to boot the USB first, I reboot this thing.

Big blue screen comes up with some small, tiny text about some kind of security issue.

Reboot

Same blue screen.

Reboot

Same blue screen.

I unplug the Live USB hoping to try something else with RUFUS...now the Lenovo turns on into a black, blank screen. I don't get to GRUB right away.

More Google. I open the Lenovo, detach the battery and the CMOS, re-attach: black screen.

I plug in an HDMI cable laying around to a monitor, plug in some hub laying around to another open USB slot, I hit the power button...GRUB.

I boot into Ubuntu, no problem. I'm scratching my head here and decide to reboot to see what happens. I have to detach the battery and the CMOS...plug in the HDMI...you get the picture.

I'm not sure what's happening or what I've done.

I've babied a 12 year old DELL laptop like I mentioned before. I've got other laptops from different companies lying around and I've never seen this.

I just want to boot into my Live USB and change some partitions!

HELP

---

### Post by GhX6GZMB on 2020-11-15
I'm sorry, but you're messing around with so many things at once with no plan.
CMOS battery, USB sticks etc., there's no way of knowing.

FIRST, get an OFFICIAL .iso from ubuntu.com, there are links there to all flavours: Kubuntu, Lubuntu, Ubuntu, Xubuntu, you name it.
SECOND: _burn_ an image of the .iso on DVD or USB. This should result in bootable media that needs to be first in your BIOS boot sequence.
THIRD: live boot from the media of your choice. Expect a couple of blank screens, but don't worry. Select language and keyboard layout. Select "Try Unbuntu" or "Start Lubuntu" from the text menu (first item in the list).

Fetch a cup of coffee, the live boot will take anything from 2...10 minutes. At the end you'll get a desktop with a few icons, one of which is "Install Ubuntu". This is the one you need.

NOW, when this runs, you'll be asked about language, keyboard, locale etc. again, and after that, you'll be in the partitioning and installation mode. Not before.

Report back about which step fails for you.

I've done this so many times on different, old machines and it works every time. Be patient.

Cheers.

---

### Post by lambquiet on 2020-11-16
Hi Ml, thanks for the reply.

You're right, I was never the patient type.

I obtained a fresh and official .ISO from UBUNTU for UBUNTU.

I created the Live USB, and it is first in the BIOS boot sequence.

I am now stuck on the third step where I am presented with a large blue screen entitled "ERROR". I see "Verification failed:  (0x1A) Security Violation"

With this screen, a notice offers to reboot the system in roughly 10 seconds.

When the system does reboot, I note that the screen does not return to GRUB. Instead, the screen goes black and blank indefinitely. I then must perform a "hard reset" of the Lenovo by disconnecting the power brick, the battery, and the CMOS. I then reconnect the battery and the CMOS, and power the Lenovo back on. Once this is done, GRUB loads, and I select the OS. I reconnect the power brick.

---

### Post by GhX6GZMB on 2020-11-16
Sounds like your USB is not bootable. I suspect you just copied the .iso, that won't work. Check its contents, if correct, they should look like this:

---

### Post by lambquiet on 2020-11-28
Happy news. After coming back to this issue I am happy to report that the USB was indeed the stumbling block for my situation.

I downloaded the latest version of Ubuntu, went over to a laptop with Ubuntu already running, fired up the Start Up Disk Creator, and used that to complete my project. I guess the lesson for me is not to use old Live USBs even if they've worked in the past.

About my issues with GRUB, an update in the last week or so fixed that. I am now back to enjoying Ubuntu the way I know. 

Shout out to @ml9104 for the helpful points.

---

