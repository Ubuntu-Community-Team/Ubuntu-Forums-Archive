---
title: "Xubuntu blew up, need guidance. Permissions issue?"
date: 2019-05-26
forum: New to Ubuntu
---

### Post by joe_schell on 2019-05-26
I've been running Xubuntu for a few years  (but I don't know as much as I should about it) on an Acer NX78 laptop .
I always leave it on. Last week, It locked up and I had to do a hard restart.

Now, I'm unable to use a lot of the "System" apps when launching them through the GUI. I can run some of them from Terminal, i.e. Synaptic. Even though Synaptic will launch, most of the packages I try to remove or repair give me permission error messages.

 I've also lost my wireless and sound capabilities.

I get all kinds of errors when attempting to chop my way through to a fix. That's right, I'm a butcher.

Here's an example of an error when attempting to edit libvirt-bin.postinst

"Error accessing system permissions: Error initializing authority: Could not connect: No such file or directory."

I tried to access that file because:

sudo dpkg --configure -a
Setting up libvirt-bin (1.2.2-0ubuntu13.1.28) ...
/var/lib/dpkg/info/libvirt-bin.postinst: 138: /var/lib/dpkg/info/libvirt-bin.postinst: chown: Permission denied
dpkg: error processing package libvirt-bin (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 libvirt-bin

So I'd like some guidance in order to stop barking up the wrong tree. I've spent many hours so far trying to either break or fix this and I'm just tired enough to ask for help.

---

### Post by Autodave on 2019-05-26
I would start by running some tests on the hard drive.  Your problem (at least to me) sounds more like a hardware issue than a software issue.

Do you still have your installation medium to try and boot to that?  If you can run from that, then I would be looking hard at the hard drive.

---

### Post by dino99 on 2019-05-26
you can erase .Xauthority then reboot to get a clean file.
if libvirt-bin (which i have not on my gnome system) configuration is broken, does that means you are also using third party(ies) sources which can disturb the system ?

---

### Post by yetimon_64 on 2019-05-26
> **joe_schell said:**
> ...Setting up libvirt-bin (**1.2.2**-0ubuntu13.1.28) ...

That version of libvirt-bin was from Trusty 14.04.

Trusty is now "End of Life", you should really consider either an upgrade to, or fresh install of, a supported version of Ubuntu or Xubuntu.

I was going to suggest you try run fsck to check the filesystem ([[COLOR=#0000ff]--here--[/COLOR]]("https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/") is a linked guide for fsck from "TecMint"), and as          Autodave suggested then test the hard drive for errors if fsck showed clean results. However if you are still using Trusty fixing such an install would be a bit like "flogging a dead horse" at this time. 

Regards, yeti.

---

### Post by joe_schell on 2019-05-26
I have run fsck, it found and repaired a few things. I ran it until  it  gave no errors.

System boots fine (except I have to run startxfce4 from the prompt).

Lots of things are broken though. 
  

I have attempted to upgrade to a higher version, but I get permission errors.



Here's just one example----

I can run Synaptic from Terminal, even though I get this:


(synaptic:14925): IBUS-WARNING **: The owner of /home/joe/.config/ibus/bus is not root!


Did not want to upgrade prior as the hardware is old and I liked what I had just fine.

If I could use DOS to do what I need to do, I would.

---

### Post by Geoffrey_Arndt on 2019-05-27
Maybe high time to save important data/files, then get latest LTS 18.04, create a bootable usb flash-stick and do a clean install.    That would be the simpler and faster route (typically).

---

### Post by yetimon_64 on 2019-05-27
> **joe_schell said:**
> ...I have attempted to upgrade to a higher version, but I get permission errors....
Then your best bet is as Geoffrey_Arndt posted ...
> ...create a bootable usb flash-stick and do a clean install...

> **joe_schell said:**
> ...Did not want to upgrade prior as the hardware is old and I liked what I had just fine....
Xubuntu 18.04, or if the hardware is very old Lubuntu 18.04, should work fine on older hardware. Posting your hardware specs here may be a good idea for helpers to make suggestions for alternatives to Trusty.

I understand how you feel about Trusty; I was disappointed to have to tarball my old install of it recently and clean out the partitions for it. Trusty was, for four years here, my best ever install to use but the time to move on to a supported release has come now. 

Using trusty past this point is dangerous in the sense it is NOT getting  any more updates including for security purposes. The repositories are  now moved to old-releases.ubuntu.com, that is they have been "archived". You have options with Xubuntu or Lubuntu on older hardware that are officially supported. Also note that getting support here on the forums requires you to be using an officially supported version, often threads here are closed when members ask for help with non-supported versions.

Regards, yeti.

---

### Post by RobGoss on 2019-05-27
**+1** yetimon_64

---

### Post by joe_schell on 2019-05-28
Well that's too bad, I always like a challenge but sounds like I'd be beating a dead horse by continuing to attempt to fix it. 

It's a shame the community doesn't seem to want to be bold and take risks. 

I believe I'll copy my precious data over to a stable Win 7 install and forge ahead trying to fix my Xubuntu.

---

### Post by oldfred on 2019-05-28
Soon same issue with Windows 7 EOL.
[https://www.microsoft.com/en-us/windowsforbusiness/end-of-windows-7-support](https://www.microsoft.com/en-us/windowsforbusiness/end-of-windows-7-support)
The end of the Windows 7 lifecycle is set for January 2020. "End of life" means Microsoft will discontinue all support, including paid support; and all updates, including security updates.

18.04  LTS support increased to 10 years 
[https://ubuntuforums.org/showthread.php?t=2406087](https://ubuntuforums.org/showthread.php?t=2406087)

---

### Post by yetimon_64 on 2019-05-29
> **joe_schell said:**
> Well that's too bad, I always like a challenge but sounds like I'd be beating a dead horse by continuing to attempt to fix it.  I am sorry have to say it, but yes, that is pretty much the case.

> **joe_schell said:**
> It's a shame the community doesn't seem to want to be bold and take risks.  
What is bold for one person is foolhardy to others, and somewhat unnecessary risk taking considering how botnets and malware can thive on the web when people use such insecure installations. Only a, probably short, matter of time before old Trusty installs are compromised and become UN-trust-worthy. The sort of damage malware and botnets can do render using an out of date install as extremely irresponsible net usage, if you keep it isolated from the internet and use it only for specific home purposes it would not be such a potential problem.

> **joe_schell said:**
> I believe I'll copy my precious data over to a stable Win 7 install and forge ahead trying to fix my Xubuntu.Ok, good luck to you on both counts, cheers, yeti.

> **oldfred said:**
> ... 18.04  LTS support increased to 10 years 
[https://ubuntuforums.org/showthread.php?t=2406087](https://ubuntuforums.org/showthread.php?t=2406087)I didn't think that applies to desktop installs, I was under the impression that is more for servers and IoT installations. I sure would love to see the desktop get support of that length, even if only once every 10 years an extra-long-term-support release was available.

---

### Post by oldrocker99 on 2019-05-29
If you are reinstalling, which is highly recommended, it's a very good idea to create a separate /home partition, to make reinstallations a lot easier and quicker.

Here are trustworthy instructions. It's not as hard as you might think. Download the 18.04 .iso, which is supported for 5 years.

[https://www.psychocats.net/ubuntu/installseparatehome](https://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by joe_schell on 2019-06-02
> **oldrocker99 said:**
> If you are reinstalling, which is highly recommended, it's a very good idea to create a separate /home partition, to make reinstallations a lot easier and quicker.

Here are trustworthy instructions. It's not as hard as you might think. Download the 18.04 .iso, which is supported for 5 years.

[https://www.psychocats.net/ubuntu/installseparatehome](https://www.psychocats.net/ubuntu/installseparatehome)

Thank you very much. 

It's refreshing to actually receive some useful guidance.

---

