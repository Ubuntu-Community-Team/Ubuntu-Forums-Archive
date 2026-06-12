---
title: "Grub Prompt - How Do I Respond?"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by csutherland on 2013-04-20
I'm trying to install 32-bit 12.10 Ubuntu from a live CD on an x86 laptop with Vista.  As soon as my machine begins to read the grub file, installation stops.  I am left staring at a black screen with a grub prompt (grub>).  How do I respond to the grub prompt to complete installation?

---

### Post by oldfred on 2013-04-21
Was laptop drive ever RAID or did you create more than 4 partitions so it converted to dynamic? That can cause issues with grub not installing correctly.

Post this from liveCD.
       sudo parted /dev/sda unit s print

---

### Post by csutherland on 2013-04-21
> **oldfred said:**
> Was laptop drive ever RAID or did you create more than 4 partitions so it converted to dynamic? That can cause issues with grub not installing correctly.

Post this from liveCD.
       sudo parted /dev/sda unit s print[HR][/HR]Solved, I guess (I don't see what I need in Advanced to mark it solved).  This was my solution: I found a document called "Getting Started with Ubuntu 12.10.pdf."  In this document, on page 11, "Downloading Ubuntu," is a link to [[COLOR=#dd4814]http://www.ubuntu.com/download/[/COLOR]]("http://www.ubuntu.com/download/").  I went there and drilled down to /desktop/windows-installer, where I found a button (Get the Installer) that downloads the installation tarball Ubuntu-12.10-wubi-amd64.tar.xz.  I clicked on this link and Ubuntu 12.10 was immediately and automatically installed onto my Dell Inspiron (32-bit) laptop next to Vista and both are behaving and getting along well, so far.  I still have the original problem (which I reworded and resubmitted as "how do I reply to the grub> prompt?" when I try to install).  No takers on either thread.  But I at least now have a working installation of Ubuntu 12.10 exactly as I wanted and expected to install.  Perhaps a reference to this document (117 pages of great stuff, well-written) is what many people need in the beginner's section.

---

### Post by oldfred on 2013-04-21
Glad you got it working. 

It sound like you have wubi which is the version that is installed inside Windows NTFS partition and uses the Windows boot loader. Good for trying out Ubuntu but not the best for long term use.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

      
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

