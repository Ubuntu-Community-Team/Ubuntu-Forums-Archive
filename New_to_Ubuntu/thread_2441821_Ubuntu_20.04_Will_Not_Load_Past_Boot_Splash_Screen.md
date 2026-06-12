---
title: "Ubuntu 20.04 Will Not Load Past Boot Splash Screen"
date: 2020-04-27
forum: New to Ubuntu
---

### Post by dacky2 on 2020-04-27
Hi All,

A bit newish to Ubuntu, I've dabbled with it a few times in the past and been using 18.04 for the past 6 months with great success,

However I upgraded (fresh install) to 20.04 and everything was fine during install and reboot. But after I rebooted again I cannot get past the boot splash screen unless I disable the splash screen, use nomodeset in grub or boot into safe mode.

I'm using and old Lenovo ThinkPad T460s with Intel® Core™ i7-6600U CPU @ 2.60GHz 12gb RAM with inbuilt graphics card using Mesa Intel® HD Graphics 520 (SKL GT2) drivers.

Any help would be much appreciated, I am a sucker for nice looking splash screens and don't really want to disable it permanently.

---

### Post by TheFu on 2020-04-27
Does the release notes have any clues?  Always check those. Google found it:
[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)

Some flavors have "Safe Graphics" boot modes.  Ubuntu-Mate does.  i don't remember seeing that option with the default Ubuntu Desktop.  it is a little frustrating to see nvidia stuff downloaded for systems that don't have any nvidia at all.

---

### Post by dacky2 on 2020-04-27
Nope I'm afraid not, it was the first place I looked.

---

### Post by oldfred on 2020-04-27
have you updated UEFI?
UEFI or BIOS install?
Does it boot to grub menu? Or do you not know as with one system, it will just auto boot and may fail somewhere else.
If UEFI boot you press escape between UEFI Lenovo logo & grub menu.
If BIOS you press & hold shift key until grub menu appears.

Then can you boot recovery mode?

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by mrdc76 on 2020-04-27
These should be reported as bugs. This has already been, but the more people do, the faster this will be fixed. [https://bugs.launchpad.net/ubuntu/+bug/1871641]("https://bugs.launchpad.net/ubuntu/+bug/1871641")

---

### Post by CelticWarrior on 2020-04-27
> **mrdc76 said:**
> These should be reported as bugs. This has already been, but the more people do, the faster this will be fixed. [https://bugs.launchpad.net/ubuntu/+bug/1871641](https://bugs.launchpad.net/ubuntu/+bug/1871641)

And how are you sure it is a bug?
It may be as simple as the firmware settings having the show logo disabled. Many UEFI and BIOS has that option.

---

### Post by mrdc76 on 2020-04-27
> **CelticWarrior said:**
> And how are you sure it is a bug?
It may be as simple as the firmware settings having the show logo disabled. Many UEFI and BIOS has that option.

The OP said: "I cannot get past the boot splash screen unless I disable the splash screen [...]" This suggests that his/her computer gets stuck at the splash screen so that it never reaches the login screen.

---

### Post by dacky2 on 2020-04-28
Hi oldfred,

I will have a look into the BIOS update, although the latest updated was November 2019. Please see below for current answers to your questions.

UEFI or BIOS install? **UEFI**
Does it boot to grub menu? Or do you not know as with one system, it will just auto boot and may fail somewhere else. **Boots into grub as I dual boot with windows for the odd windows only task**

Then can you boot recovery mode **I can boot into recovery mode no problem, everything else works fine apart from JAVA, MS TEAMS, and the boot splash. I was thinking it was something to do with the graphics drivers, if I disable them on boot UBUNTU loads fine fine. **

---

### Post by CelticWarrior on 2020-04-28
> **I was thinking it was something to do with the graphics drivers, if I disable them on boot UBUNTU loads fine fine. **

Perhaps what you need is to disable Secure Boot and not the graphics drivers.

---

### Post by oldfred on 2020-04-28
I thought Intel video just worked.

I have this in older notes, but newer chips & newer kernel do this automatically. You could try it.
 i915.fastboot=1 kernel parameter. Fastboot helps provide a clean, flicker-free Linux boot experience.
New 5.1 kernel will include it by default on Skylake and newer

I change this just to speed boot. It eliminates the splash quiet and you see all the lines as it boots. With my SSD, they go by very fast. Years ago I used to be able to read them. 
I replace quiet splash with noplymouth.

[https://askubuntu.com/questions/1119167/slow-boot-issue-due-to-plymouth-quit-wait-service-ubuntu-18-04](https://askubuntu.com/questions/1119167/slow-boot-issue-due-to-plymouth-quit-wait-service-ubuntu-18-04)
Plymouth is the application which provides the graphical "splash" screen when booting and shutting down an Ubuntu system.

---

### Post by dacky2 on 2020-04-28
> **CelticWarrior said:**
> Perhaps what you need is to disable Secure Boot and not the graphics drivers.

Secure boot is disabled as I had issues with that before.

---

### Post by CelticWarrior on 2020-04-28
> **dacky2 said:**
> Secure boot is disabled as I had issues with that before.

Just making sure. It shouldn't interfere with Intel Graphics drivers though, as correctly mentioned by oldfred but it's better, or more convenient, to have it disabled from the start.

A firmware update should correct the issue in question. If not available now it should be, sooner than later.

---

### Post by dacky2 on 2020-04-29
> **CelticWarrior said:**
> Just making sure. It shouldn't interfere with Intel Graphics drivers though, as correctly mentioned by oldfred but it's better, or more convenient, to have it disabled from the start.

A firmware update should correct the issue in question. If not available now it should be, sooner than later.

Hopefully sooner rather than later.

I checked my BIOS firmware and I am on the latest version, so I'm a little stumped.

In the meantime I've had to go back to 18.04 as I'm working from home and couldn't afford to lose anymore time messing around.

Hopefully it won't be too long till this is fixed as I liked what I saw with 20.04.

---

### Post by CelticWarrior on 2020-04-29
Wise decision.

The first time I've read about this new feature at OMGUbuntu I had two thoughts: "Cool" and "this is going to screw up the boot in some odd computer creating a problem that wasn't there before".

---

### Post by sotires on 2020-04-29
Just what is this "cool new feature"? 
What is the advantage that some of us are missing out on?

---

### Post by CelticWarrior on 2020-04-29
> **sotires said:**
> Just what is this "cool new feature"? 
What is the advantage that some of us are missing out on?

The "cool new feature" is showing the vendor's logo in the same initial Ubuntu splash screen. The Ubuntu logo and the moving circle that replaced the dots have been conveniently move from the center screen to the bottom. It's just a more "Windowsesc" feature, there's nothing useful about it, just aesthetics.
[https://www.omgubuntu.co.uk/2020/03/ubuntu-20-04-oem-boot-splash](https://www.omgubuntu.co.uk/2020/03/ubuntu-20-04-oem-boot-splash)

It works in one HP laptop I have but all my other computers are unbranded generic from top tier providers where pretty much everything is "to be filled by OEM" so nothing shows up in those.

---

### Post by oldfred on 2020-04-29
To speed boot slightly I replace quiet splash with noplymouth.
I then do not get any splash screens, but do get scrolling list of boot process (that is then in log file).

With my new NVMe drive it scrolls by so quick I cannot read it. With my old slow HDDs I used to be able to follow along the boot process. 
Or is it oldfred cannot read as fast as he used to? :)

---

### Post by sotires on 2020-04-29
I can even turn this into a "feature". It's effectively a log on screen where you have to go through a procedure rather than simply enter a password!

Still, it's a pain. 
I don't get the procedure for getting rid of it altogether. What is it that should be edited?

---

### Post by oldfred on 2020-04-29
I change this line in grub and run update grub.

sudoedit /etc/default/grub
> GRUB_CMDLINE_LINUX_DEFAULT="noplymouth i915.fastboot=1"
sudo update-grub

---

### Post by him610 on 2020-05-01
Experienced similar issue during Xubuntu development phase a two or three weeks ago on one system. Reported it as a bug along with log of how far system got during boot process - it wasn't very far. I had been running developmental Xubuntu for three or four months. The occurrence of problem was sporadic.
My workaround whenever it happened - unplugged every cable that was not absolutely necessary, cold boot, after system booted, plugged in cables one-by-one. Don't know if that corrected it or not, probably not - just grasping at straws; however, an update/upgrade came down shortly afterwards and the issue never reoccurred. I assumed it had been corrected, but then again, maybe not.

---

