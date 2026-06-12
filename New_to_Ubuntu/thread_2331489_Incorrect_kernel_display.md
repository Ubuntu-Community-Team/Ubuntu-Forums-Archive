---
title: "Incorrect kernel display"
date: 2016-07-22
forum: New to Ubuntu
---

### Post by anonb on 2016-07-22
I just purchased a chromebook and have installed Ubuntu 14.0.4 (trusty) on it.  I'm trying to install vmbox or vmplayer and it keeps saying linux-headers-3.18.0 cannot be found.  I tried updating the kernel, upgrading,rebuilding it, and cloning it but nothing will work.  I even tried installing synaptic to remove the kernel header that is displaying but the header and image files are no where to be found on that system.  Is there someway I can fix this issue?

---

### Post by Andreyshel on 2016-07-22
Have you dkms package installed?

---

### Post by anonb on 2016-07-22
No what command should i try?

---

### Post by jeremy31 on 2016-07-22
What does ```
uname -a; ls /usr/src/ | grep header
``` show as 3.18 is not a supported Ubuntu kernel

---

### Post by anonb on 2016-07-22
Linux localhost 3.18.0-11125-g013294a #1 SMP PREEMPT Wed Jul 6 15:28:37 PDT 2016 x86_64 x86_64 x86_64 GNU/Linux
linux-headers-3.13.0-24
linux-headers-3.13.0-24-generic
linux-headers-3.13.0-92
linux-headers-3.13.0-92-generic
linux-headers-4.4.0-24
linux-headers-4.4.0-24-generic
linux-headers-4.4.0-31
linux-headers-4.4.0-31-generic

---

### Post by jeremy31 on 2016-07-22
See if it will install after booting into the 3.13.0-92 kernel

---

### Post by anonb on 2016-07-22
How do I boot into that kernel?

---

### Post by jeremy31 on 2016-07-22
Hold the shift key during boot until the Grub menu appears, then scroll to Previous Linux Versions or Advanced Options, then you should be able to select that kernel to boot to

---

### Post by anonb on 2016-07-22
aww i've been trying to figure that out... ok im doing it now. brb

ok so i dont think it will do that since it is chromeos and ubuntu OS runs beside it.  any other ideas?

---

### Post by jeremy31 on 2016-07-22
You may want to find where you got the 3.18 kernel and see if there are any header files you can download

---

### Post by anonb on 2016-07-22
i just tried to change the grub file to boot with another kernel but that didnt work either...

i looked on the repository and they wasnt there.  im not sure where i can get them.  this is crazy...

---

### Post by jeremy31 on 2016-07-22
You shouldn't change the grub file unless you know what you are doing.  It shouldn't matter to ChromeOS what kernel Ubuntu is booting into and Ubuntu 14.04 may only be able to compile the VM program in a supported kernel depending on the hardware enablement stack(HWE) which I guess yours is still at the original 3.13 kernel series as I haven't seen any instructions on the wiki to upgrade Ubuntu 14.04 to the Xenial 4.4 kernel

---

### Post by deadflowr on 2016-07-22
Crouton?
Then it's the ChromeOS Kernel running, and not the Ubuntu Kernel.

As far as I know, you will only ever be running the Chrome kernel when using Crouton.

But basically you're running into the same area of problems as these folks on github:
[https://github.com/dnschneid/crouton/issues/2642]("https://github.com/dnschneid/crouton/issues/2642")

---

### Post by MAFoElffen on 2016-07-23
@DeadFlower 
Sort of yes and no. He is running "Crouton" which means he really did not install a traditional installation of Ubuntu. Rather it installs an Ubuntu Image, with Crouton (by way of many scripts) chroot's into. At least, that is what Crouton's doc's say about itself.

Are you saying it really does not chroot into the image and tries to use it's own (ChromebookOS) kernel? It actually is supposed to be "both", but in two different places. (ChromeOS and a chrooted Ubuntu) They just lost track of where they were. 

It reported using kernel 3.18.0 instead of 4.4.0-31(?) in that link you posted for that reason. They were trying to edit an image while NOT chrooted into that image, so were still running on the ChromebookOS kernel, That is why the github thread, it showed via uname as 3.18.0. If they had been in the chrooted environment = the ubuntu image, then they would have been running on that Ubuntu kernel image, and the results would have different, IMHO: "uname" would be a good test there to see if they are actually on the chrooted environment or not... 

@OP:
Simple fix. Watch this YouTube video: [https://www.youtube.com/watch?v=OImoN7frSdg](https://www.youtube.com/watch?v=OImoN7frSdg)

That video was for ChromebookOS, installing Crouton > Ubuntu 12.04 > Virtualbox ... Step-by-Step. Mold it to what you need for 14.04. That video included detailed instructions on downloading and building your headers from within the chroot. There are times that you have to pop out to ChromeOS, but most of it is from within your chroot. That video will help you keep track of what you need to do when and where.

One of my past Instructors used to harp on: "Remember where you are, and where you want to go to." He was talking about scripting, commandline, piping and redirection... But in your case (chroot's and the host system), it is pertinent.

---

### Post by anonb on 2016-07-23
I have looked on  the internet and i have the 3.18 installed but its not 3.18.0.11125. For some reason that makes a difference...

@mafeellfin im watching that video now

so i watched this video and tried a few steps.  i ran this sudo sh ~/Downloads/change-kernel-flags and it worked fine.  Then i ran sudo sh setup-headers.sh but my kernel isnt supported by his scripts so it fails.  
Your kernel version 3.18.0-11125-g013294a with architecture amd64 is not supported

is there a manual process i can try????

---

### Post by MAFoElffen on 2016-07-23
That was with a current version of the script at GitHub right? If so, then...

Since the GitHub Crouton scripts are external to Canonical and Ubuntu Support and it is looking for a ChromeOS kernel to insert "something" into the target chroot image... before being able to deal with it from the chroot... That is someone else's script on an OpenSource Project. That is where I respect other people's boundaries and I look at the bigger picture. OpenSource is open code, but they should have the chance to know about it and be part of the loop. (That is formally or informally... beforehand or afterwards.)

The correct thing to do would be to report that to the GitHub Crouton Project as a bug. They do the support for their own project. Now if you could talk someone into looking at that script to include that kernel version, and they came up with a fix, then they could submit that as a proposed fix  ( a push to a proposed branch) to the GitHub project's code. In the meanwhile, you would be "fixed."

As a Project Lead of my own OpenSource project, that is what I would expect. i.e.: "Tell me there is a problem needed for a change..." But with that experience, I know that resources for OpenSource projects are limited and that proposed changes do not happen overnight.

EDIT-- I used to report bugs, with: "Here is a bug and here is the patch to correct it...", but I have less personal time for that now. (And I do not have a chromebook to test that.)

---

### Post by smelheim85 on 2016-07-23
You can try and manually change the boot order in the /etc/defaults and then run a update-grub command on the command prompt.  However it almost sounds like you can't enter grub which might be an issue why you can't boot into other images.  I don't know what type of boot manager that the chromebooks use but there might be a special case.  Normally from what I've experience Ubuntu usually brings of the grub menu at boot.  

Do it speed through the boot process or do you actually get the grub menu for your system boots into Ubuntu?

---

### Post by anonb on 2016-07-23
it speeds through the boot process... i cannot get to the other grub menus upon reboot...

---

### Post by MAFoElffen on 2016-07-24
Grub is not used in a chroot. In a chroot, the host system boots > the chroot is done directly into the guest system (inside the guest mage). You want to get a hint into how that works, look at the second half of post #3 of the sticky linked in my sigline.

That is similar to how we had WinMobile phones chrooted into custom Linux images ("Linux on HTC") ... and later had Android devices chroot into Linux images such as Ubuntu. ("Linux on Android')

Just for curiousity sake, I went over to the Github Crouton Project to see if there where users having similar issues.
[https://github.com/dnschneid/crouton/issues/2684](https://github.com/dnschneid/crouton/issues/2684) (That was 6 days ago)


That says, at the current date, that they are still only supporting up to Ubuntu Precise (12.04)... Proposed is that they update their code to support a newer version of Ubuntu. That would be a reason that newer kernel is not supported in their code. Trusty kernels are not supported yet. (by them)

---

### Post by anonb on 2016-07-25
Not sure where i can get the 3.18.0 kernel.  i cant find it at all....

---

