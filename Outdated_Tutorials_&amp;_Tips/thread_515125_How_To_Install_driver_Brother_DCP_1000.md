---
title: "How To: Install driver Brother DCP 1000"
date: 2007-08-01
forum: Outdated Tutorials &amp; Tips
---

### Post by bwtranch on 2007-08-01
So you want it to PRINT, huh? Well scanning is easy and I would refer you to other fine articles for that. After much searching and frustration, I found nothing that worked until now. The instructions they give you don't work. You know that or you wouldn't be here, right? This is actually easy if you know how.

Download both the lpr and cupswrapper packages. Install the lpr FIRST, this is very important. This will not fully install and you will get an error. We can ignore it for now. We will come back and fix it later. We will have to because it messed up dpkg. 

Now install the cupwrapper package. This should go off without a hitch. Use the deb installer or shell command 
sh /usr/local/Brother/cupswrapper/cupswrapperDCP1000-1.0.2 -i and you possibly could get another error, but ignore that, too.

Then, Copy the file "/usr/share/cups/model/brsdp1000_cups.ppd"
to the directory "/usr/share/ppd".

If you are using USB interface,
connect the device to the PC and turn the power on.

Access to the page "http://localhost:631"
and click on "Add Printer",
then install the driver following the instructions.

Print a test page. Every thing OK? Think we are done? No, like I said installing the lpr package messed up dpkg and we have to fix it. --force does not work. Run "sudo gedit /var/lib/dpkg/status". Find the log for Brother lpr and it should say that it halfway installed. Delete the entry and save.

You can now go to Synaptic or whatever you like and delete the partially installed package.

Test printer again and I wish you good luck!:)

---

### Post by bwtranch on 2007-08-05
Sorry about the typo

Should read "Now install the cupswrapper package..."

Everything else should be Ok. Email if you have a problem. I have this one down.:)

---

### Post by bwtranch on 2007-08-05
I am getting reports that this procedure works with other Brother drivers as well. Apparently the MFC family (at least the laser printers) use this driver and I am getting positive reports.

I don't really know where the problem lies, Brother, Ubuntu or both. The lpr driver should not hang and for that matter if it does hang, then dpkg should be able to get over it. But, you cannot install anything else frontend or terminal unless you clear that log entry. I am going to report this to launchpad and to tell you the truth, I think they already know about it. But nobody has done anything about it yet. I know it was in Feisty and now that I am using Gutsy, it's still the same.

But, just because you can't install one package, should not disable the whole package install system.:(

---

### Post by neoroses on 2007-12-15
you my friend are a genius!!!!!! worked on the dcp 135c no problem what so ever much better than thoes other non working guides!!!!!:lolflag:

---

### Post by MasterSushi on 2008-07-11
I can't seem to be able to get the 'brsdp1000_cups.ppd' file to extract from the cupswrapper. Can anyone upload the .ppd file for the DCP-1000 printer?

---

