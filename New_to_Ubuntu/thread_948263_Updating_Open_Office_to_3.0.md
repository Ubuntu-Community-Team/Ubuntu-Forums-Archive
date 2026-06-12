---
title: "Updating Open Office to 3.0"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Sailorcancer on 2008-10-15
I noticed that OpenOffice has been updated to 3.0.  I downloaded the DEB for Open Office, but I have no clue how to update it.

I saved it to my desktop.  Any help would be great!  Thanks!

---

### Post by hyper_ch on 2008-10-15
you don't... normally you don't get any software versioning update (at least not major ones) during a release. So 8.04 was released half a year ago and you won't get OOo v3 in there. However someone might do a backport but you'd have to activate those.

I think you'll get OOo v3 in 8.10 which will be released as stable soon.

---

### Post by Sailorcancer on 2008-10-15
I'm still new to Linux so I'm a little confused.

Why do I need to wait for a newer version of Ubuntu to update to 3.0?

---

### Post by Mr. Swiveller on 2008-10-15
> **Sailorcancer said:**
> I'm still new to Linux so I'm a little confused.

Why do I need to wait for a newer version of Ubuntu to update to 3.0?

SUN/Openoffice.org offer a package for download from their own web page. If you downloaded the (Ubuntu) deb version, it should work (note that you should get the 64-bit version if you are using Ubuntu 64-bit). If it's a deb package, right click on it - there should be an install function somewhere in the menu. If it's a .gz package, open it with your file browser or archiving application, copy the debs to a new directory, and install from there.

However, SUN's package is unlikely to receive any official support from Ubuntu. Wait until you can download Openoffice.org from the official Ubuntu repositories if you want a version which has been tested (and possibly adapted for (K)Ubuntu) by the Ubuntu team. It is indeed more likely that such a version will be made available for 8.10 than for 8.04, which will slowly be fased out. 

* Swiveller *

---

### Post by hyper_ch on 2008-10-15
What features does OOo 3 offer that you can't live without?

---

### Post by randcoop on 2008-10-15
To be clear: Ubuntu won't put OpenOffice 3.0 into 8.04 for a while.  It's also quite possible that it won't make it into the 8.10 version coming out in a couple of weeks, because they probably won't have enough time to test it.

If you want to upgrade to OpenOffice 3.0, you can do so.  

This will NOT remove your 2.4 version.  So you'll actually have two versions of OpenOffice on your computer.  If you don't want that to happen, you should remove OpenOffice 2.4 BEFORE you install OpenOffice 3.0 (it will be too confusing to do it afterwards).

The DEB file you downloaded from the OpenOffice site came in as a tar.gz file.  Put that file in a folder of its own and then unzip it with the command:
```
tar -xvzf [FILENAME]
```

You'll now have a folder in the folder you saved the tar.gz file to.  You'll be able to find the folder in there that contains all the deb files (probably called DEBS).

Go into that folder and run the command:

```
sudo dpkg -i *.deb
```

And OpenOffice 3.0 will install.

With regard to "things you can't live without," you should know that OpenOffice 3.0 is a major version upgrade.  Among the many things that may be quite important to users are that Calc now will accept a far larger spreadsheet size and that PDF files can now be imported and edited in OpenOffice.

Visit the OpenOffice site for the release notes that explain the many changes to the program.

---

### Post by hyper_ch on 2008-10-15
Additional features isn't the same as features you can't live without... and also a major version upgrade implies nothing that it's a must-have ;)

Hence I asked what he can't live without ;)

---

### Post by randcoop on 2008-10-15
In my experience, asking what you can't live without is code for you don't really need to upgrade.  If that's not what you meant to imply, I apologize for the misunderstanding.

The additional features I mentioned may, indeed, be features that users can't live without.  For example, the PDF import and edit feature is significant for me.

There's no software in the world, of course, that I can't live without.  I can live without a computer.  So I take that expression to really mean what is it that I really would like to have that isn't available in the current Ubuntu-sanctioned version of OpenOffice.  That would be PDF capability, among other things, for me.

---

### Post by The Cog on 2008-10-15
I have installed OOo 3.0 the way randcoop said. Works a treat.

I also created an executable file /usr/local/bin/ooo with the following contents:
```
#!/bin/bash
/opt/openoffice.org3/program/soffice "$*"
```
then I can configure nautilus to open .odt files etc. with ooo and can just re-point this script to the new directory when another upgrade arrives.

---

