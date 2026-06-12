---
title: "Formatting Without LiveCD?"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by missrachel on 2013-05-29
Help! My computer was running Ubuntu Hardy and it recently crashed. It gives me this error and won't boot up: "kernel panic - not syncing vfs unable to mount root fs on unknown-block(0 0)"    


As this computer was given to me, I've never had the LiveCD but I want to format it and instead put Windows XP on it. Please help me figure something out.. thanks!

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]missrachel; Hi ;

The install medium that you choose may/will have the function to format the drive(s). Any of the 'buntu desktop installations (free, just down load and burn) or a purchased edition of Windows will serve.
edit: from 'buntu liveDVD one can mount the hardy install and save the data on that old install.
[/COLOR][INDENT][COLOR=#000000]

[/COLOR][/INDENT]
[INDENT=3]ain't nothing but a thing

[/INDENT]

---

### Post by Cheesemill on 2013-05-30
You can use the Windows XP disk to delete the Ubuntu partitions and create an NTFS partition for XP.

---

### Post by zeroseven0183 on 2013-05-30
A word of caution, though, when choosing Windows XP. It's a few months now from its [end of support]("http://www.microsoft.com/en-us/windows/endofsupport.aspx"), meaning

> After April 8, 2014, there will be no new security updates,  non-security hotfixes, free or paid assisted support options or online  technical content updates.

Running Windows XP SP3 and Office  2003 in your environment after their end of support date may expose your  company to potential risks, such as:[I]
* Security & Compliance Risks: [/I]Unsupported  and unpatched environments are vulnerable to security risks. This may  result in an officially recognized control failure by an internal or  external audit body, leading to suspension of certifications, and/or  public notification of the organization’s inability to maintain its  systems and customer information.[I]
* Lack of Independent Software Vendor (ISV) & Hardware Manufacturers support: [/I]  A recent industry report from Gartner Research suggests "many  independent software vendors (ISVs) are unlikely to support new versions  of applications on Windows XP in 2011; in 2012, it will become common."  And it may stifle access to hardware innovation: Gartner Research  further notes that in 2012, most PC hardware manufacturers will stop  supporting Windows XP on the majority of their new PC models. 

[LIST] 
[/LIST]


It's up to you until when are you keeping it but if I were to fix a computer, I'd rather have Linux on it the next time.

[1] Support ends in 2013 for Windows XP and Office 2003 [http://www.microsoft.com/en-us/windows/endofsupport.aspx](http://www.microsoft.com/en-us/windows/endofsupport.aspx)

---

### Post by ShadowVegan on 2013-05-30
I would strongly suggest reinstalling Ubuntu. If you do that, just put the Ubuntu CD in the disk drive, restart the computer, press F2 to enter BIOS, go to boot settings/boot device priority and set priority #1 to CD. Then press F10 (save and exit) then during the installation it gives you the option to overwrite the entire drive. This should fix it.

I think a Windows installation disk would have a similar option.

If you specifically want tools for wiping and/or reformatting your hard drive, you can use [DBAN](http://www.dban.org/) to completely wipe your hard drive and [GParted](http://gparted.sourceforge.net/) to re-partition your drive. However, these aren't necessary, you can just put in the Ubuntu or Windows installation CD and follow the steps.

---

### Post by Mark Phelps on 2013-05-30
I strongly advise AGAINST reinstalling Hardy -- that was Ubuntu version 8.04, reached end-of-life long ago.  

LOTS of things have changes since Hardy -- and with a PC that old, it's likely that the newer Ubuntu versions will not work as well.  I would suggest nothing newer than 12.04 at this point.  

If you want to try it, download the ISO file, burn a DVD from it, and boot from that -- selecting Try Ubuntu.  That will show you how well a recent Ubuntu versions recognizes your hardware and installs working drivers.

---

