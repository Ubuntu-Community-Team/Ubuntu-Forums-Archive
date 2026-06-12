---
title: "Cannot Convert Outlook to Evolution"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by JerryC on 2011-10-17
I have tried many things, but I give up.

I am using the current version of Evolution which is 3.2.0.  It doe not offer the option of directly importing an outlook.pst file.  Someone suggested installing Evolution on Windows, importing, then moving the files over to linux.  Evolution is very unstable on Windows 7. I even uninstalled Ev and re-installed.  Doesn't work. I also tried installing Thunderbird and converting the outlook file. That is a joke.  It presents a list of fields which have to be moved around to math up.  All of the Outlook fields aren't on the list. One of the outlook fields not on the list is the email address.  Duh!  Out of 15 or 20 fields on the list, only about 10 of them can be matched up.  Next I started searching the web for a couple hours.  Anything turned up was anywhere from 6 to 8 years old.  One place offered to sell a conversion software package for $49.  For a one time use?  I don't think so.  Another place had something that needed to be compiled which I couldn't find to download.  No matter.  That's way over my head. 

I spent a solid 6 hours on this yesterday so I have come to the conclusion it is not possible for a new user to Ubuntu to convert email from Outlook to Evolution.  If anyone can show me a detailed step by step method to get this done, I would really appreciate it.

On the upside, last week I got the name and address file converted by exporting to a CSV file and then importing.  I only had to spend about 3 hours cleaning up the discrepancies.

JC

---

### Post by elhijodelpeje on 2011-10-20
As an evolution fan that I am, I quit digging on a solution after one hour without results. I am planning to install thunderbird, import my .pst file, then go back to evolution and try to import from thunderbird. Hope this might work. regards...RR.

---

### Post by haqking on 2011-10-20
> **JerryC said:**
> I have tried many things, but I give up.

I am using the current version of Evolution which is 3.2.0.  It doe not offer the option of directly importing an outlook.pst file.  Someone suggested installing Evolution on Windows, importing, then moving the files over to linux.  Evolution is very unstable on Windows 7. I even uninstalled Ev and re-installed.  Doesn't work. I also tried installing Thunderbird and converting the outlook file. That is a joke.  It presents a list of fields which have to be moved around to math up.  All of the Outlook fields aren't on the list. One of the outlook fields not on the list is the email address.  Duh!  Out of 15 or 20 fields on the list, only about 10 of them can be matched up.  Next I started searching the web for a couple hours.  Anything turned up was anywhere from 6 to 8 years old.  One place offered to sell a conversion software package for $49.  For a one time use?  I don't think so.  Another place had something that needed to be compiled which I couldn't find to download.  No matter.  That's way over my head. 

I spent a solid 6 hours on this yesterday so I have come to the conclusion it is not possible for a new user to Ubuntu to convert email from Outlook to Evolution.  If anyone can show me a detailed step by step method to get this done, I would really appreciate it.

On the upside, last week I got the name and address file converted by exporting to a CSV file and then importing.  I only had to spend about 3 hours cleaning up the discrepancies.

JC

you can convert the .pst to mbox format.

There was a tool called libPST a while ago i think, give it a google or there will be a similar tool

---

### Post by JerryC on 2011-10-20
> **elhijodelpeje said:**
> As an evolution fan that I am, I quit digging on a solution after one hour without results. I am planning to install thunderbird, import my .pst file, then go back to evolution and try to import from thunderbird. Hope this might work. regards...RR.

If you can get that to work, more power to ya.  It doesn't look feasible to me.  Read my post again.

JC

---

### Post by JerryC on 2011-10-20
> **haqking said:**
> you can convert the .pst to mbox format.

There was a tool called libPST a while ago i think, give it a google or there will be a similar tool

I found that once and couldn't see where to download it.  I found it this time.  Thanks.

JC

---

### Post by haqking on 2011-10-20
> **JerryC said:**
> I found that once and couldn't see where to download it.  I found it this time.  Thanks.

JC

no worries, hope it helps

---

### Post by tech4him on 2011-11-03
I'm not an evolution user but Thunderbird, however if evolution can import .eml files, perhaps the process I went through from Outlook .pst files to .eml file might help. Just a thought.

[http://blog.tech4him.com/2011/09/moving-outlook-pst-emails-to-thunderbird-on-ubuntu-linux/](http://blog.tech4him.com/2011/09/moving-outlook-pst-emails-to-thunderbird-on-ubuntu-linux/)

To summarize:

1. sudo apt-get install readpst
2. mkdir pst-export
3. readpst -D -M -b -o pst-export archive.pst
4. find . -type f ! -iname '*.eml' -exec rename 's/([0-9]+)$/$1.eml/' {} \;
5. Import .eml

Cheers!

---

### Post by Ross Gayler on 2011-11-23
FWIW the import PST plugin was present in the version of evolution available on Ubuntu 11.04 (Natty) and worked fine for me.  It looks like the PST import filter has disappeared on past Ubuntu version upgrades ([https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/670747](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/670747)).

I have logged this as a bug [(https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/893420]("http://ubuntuforums.org/%28https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/893420")), but there has been no activity so far.

I have about 10Gb of PST files I need to import.  I contemplated installing 11.04 on a virtual machine and importing the PSTs there but that sounds a bit tedious.  If the PST import plugin doesn't reappear soon I will probably try using readpst to convert the PSTs to mbox format then import that to evolution.

UPDATE 26 November 2011

I tried readpst -r.  This created a directory tree mirroring the PST folder hierarchy with an mbox file in each directory.  I have not tried to import these to evolution because I have thousands of folders which would have to be created manually in evolution and each of the thousands of mbox files manually imported.

I created a virtualbox virtual machine, installed an older version of Ubuntu and evolution and used the import PST plugin.  That worked, but I needed to merge the imported folders with my current evolution setup that contains emails i don't want to lose.  I can't find any way in evolution to export a folder tree.  It can only export all the emails in one folder, which implies having to export each of the folders individually.  I don't want to do that.

I looked at using evolution backup/restore, but restore completely replaces the contents of evolution,so you can't use it to add folders to an existing evolution.

I thought I could backup my current evolution, restore it on an older ubuntu on a virtual machine, import the PSTs, back it up, and restore it to the current machine.  That won't work because the 11.04 Ubuntu runs evolution 2.32 which can't properly read the backup produced by evolution 3.2 on Ubuntu 11.10

I'm getting really tired of this game and the bug report is still unassigned.

---

### Post by Ross Gayler on 2011-11-29
OK - I did it!  I imported my PST files to Evolution 3.2.1 on Ubuntu 11.10, but it was a reasonably tedious, brute force process.  (However, I am fairly clueless about most of this, so there may have been a more elegant way to do it.)

The problem: I have about 10Gb of PST files with thousands of folders to import to evolution.  Evolution 2.32.2 on Ubuntu 11.04 had an Import PST plugin which has inexplicably disappeared from Evolution 3.2.1 on Ubuntu 11.10.  I also have about 20 folders of local mail in Evolution 3.2.1 that I want to keep when I add in the PSTs.

My solution:

[LIST]
[*]Create a virtual machine with VirtualBox
[*]Install Ubuntu 11.04 on the VM (Evolution 2.32.2 is the default email client on Ubuntu 11.04)
[*]Import the PSTs into Evolution 2.32.2 on Ubuntu 11.04 on the VM
[*]For each local mail folder on Evolution 3.2.1 on Ubuntu 11.10 export all the emails to an mbox file
[*]For each exported mbox file import it into Evolution 2.32.2 on Ubuntu 11.04 on the VM
[*]Upgrade the OS on the VM from Ubuntu 11.04 to Ubuntu 11.10
[*]For some reason the installed Evolution 2.32.2 is not upgraded properly, so install Evolution on Ubuntu 11.10 on the VM.  This installs Evolution 3.2.1
[*]When Evolution 3.2.1 is run for the first time on Ubuntu 11.10 on the VM it finds the old mail files from the Evolution 2.32.2 installation and migrates them (because the Evolution mail format was changed between 2.32.2 and 3.2.1)
[*]You now have an Evolution 3.2.1 on the VM with local folders containing the imported PSTs and the local folders exported from the original Evolution 3.2.1on the physical machine.
[*]Backup the Evolution 3.2.1 on the VM
[*]Restore the backup to the Evolution 3.2.1 on the physical machine
[/LIST]
While I was doing all that I was taking lots of VM snapshots and Evolution backups and experimenting to see what worked and trying to be safe - so it took about 2 days to get it done.

Oh, and the bug [(https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/893420]("http://ubuntuforums.org/%28https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/893420")) is still unassigned.

*UPDATE* The bug has been assigned, 7 December 2011

---

