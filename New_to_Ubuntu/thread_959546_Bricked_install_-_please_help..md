---
title: "Bricked install - please help."
date: 2008-10-26
forum: New to Ubuntu
---

### Post by GCL on 2008-10-26
I just installed Ubuntu Hardy on my machine this weekend (first time I've used a *nix OS in close to 10 years).

All was going well - I had a clean install to a fresh drive, boot manager was working nicely, so my XP Pro install is still available to me, and I successfully installed the drivers for my RadeonHD 4870x2 which allowed me to exceed the 1600x1200 limit which is imposed by the default video drivers.

So, while I'm new to Ubuntu, I want you to understand that I'm capable of following directions and I do possess a basic understanding of how UNIX-based OS's work.

Having said that, [**THIS GUIDE**]("https://help.ubuntu.com/community/OpenSound"), which I followed to the letter (TWICE), has resulted in a completely ruined install (and already required one re-install).  Now, when I select my Ubuntu build from the bootloader I get to enjoy a nice long stare at a black screen until I finally get tired of it and reset the machine.  No Ubuntu splash screen... no error message... not so much as a command line.  Something has pooched my install and the recovery options (what few there are) seem impotent to help me.

If anyone can offer some insight as to what happened and how I can fix it, I can sure use the help.

Thanks & regards,

GCL

---

### Post by phidia on 2008-10-26
I think there needs to be clarification.
The link you provided is for setting up open sound (OSS) so are you saying you have a working install until you try to get sound working-or was the link made incorrectly?

If you are trying to get sound working on a new install there are some sound troubleshooting guides you can use. For that take a look at the guide [here]("http://ubuntuforums.org/showthread.php?t=205449").

---

### Post by GCL on 2008-10-26
> **phidia said:**
> I think there needs to be clarification.
The link you provided is for setting up open sound (OSS) so are you saying you have a working install until you try to get sound working-or was the link made incorrectly?

If you are trying to get sound working on a new install there are some sound troubleshooting guides you can use. For that take a look at the guide [here]("http://ubuntuforums.org/showthread.php?t=205449").

I had a working install, just no sound (X-Fi Xtreme Gamer) so I tried to install the OSS drivers because they have a beta driver for my card.  Now the OS won't load at all (other than recovery console).

Whether or not the guide I linked was made incorrectly is not something I have the experience to comment on, other than to say that I followed it to the letter and it has cost me 2 botched installs (the first I fixed by re-installing and starting over).

I'm hoping to avoid having to do a 3rd install if there's some way to undo what I've done.

---

### Post by dracayr on 2008-10-26
If you press alt+f2 while trying to boot, does it say anything?

dracayr

---

### Post by phidia on 2008-10-26
> **GCL said:**
> I had a working install, just no sound (X-Fi Xtreme Gamer) so I tried to install the OSS drivers because they have a beta driver for my card.  Now the OS won't load at all (other than recovery console).

Whether or not the guide I linked was made incorrectly is not something I have the experience to comment on, other than to say that I followed it to the letter and it has cost me 2 botched installs (the first I fixed by re-installing and starting over).

I'm hoping to avoid having to do a 3rd install if there's some way to undo what I've done.

I'm not saying the guide is incorrect. It wasn't clear what the problem was because you only provided a link for the OSS guide and didn't say specifically what problem you were having. I provided the sound troubleshooting link because it seemed like the problem could be trying to enable sound.

If you can't get a gui desktop you can use apt or dpkg to remove the packages you installed, and restart or enter "startx". For that matter what does that command output?

---

### Post by handydan918 on 2008-10-26
> **GCL said:**
> I just installed Ubuntu Hardy on my machine this weekend (first time I've used a *nix OS in close to 10 years).

GCL


If this is really the first time you used linux in 10 yrs, try some more stable branches of debian. 
Debian comes to mind...
Mepis is another good one. 
Ubu is inherently "unstable" in the sense that it is "bleeding edge". You will always have software that has not gone thru the debian wringer of unstable>testing>stable before deployment. 


IMHO....

---

