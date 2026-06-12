---
title: "Howto: Add a Wubi boot entry in Vista"
date: 2009-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by pasteta on 2009-06-27
This tutorial is meant to help all those who installed Wubi in Vista but did not get "Ubuntu" option in boot menu.

First you need to download and install EasyBCD: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

1.) Open it and select "Add/Remove entries" button.

[IMG]http://img44.imageshack.us/img44/8003/72438956.jpg[/IMG]

Then select "Linux" under "Add an entry". Click "type" and select "Wubi" You can also rename it from *NeoSmart* Linux to *Ubunto*. (Note: what ever you write here will display in the boot menu). Click "Add Entry", then "Save". 

[IMG]http://img3.imageshack.us/img3/5338/62996658.jpg[/IMG]

(Note: if you want to remove the just added entry from the list, select it and click "delete". You will get an error saying *You must uninstall NeoGrub from its own section below*. To do that select "NeoGrub" option left from "Linux" and click "Remove Neogrub". Now you can remove the newly created entry.)

2.)Close EasyBCD, and run CommandPrompt in Administrator mode. 
(Start>All Programs>Accessories>right click on the "Command Prompt" icon and select "Run as administrator")

3.)Type *bcdedit*
You will get a list of all boot entries. 

[IMG]http://img7.imageshack.us/img7/6020/70447359.jpg[/IMG]

We will be editing the "Real-mode Boot sector" entry.
*device partiton=C:* tells us on which partition your Wubi installation is located, in case you did not install it on the same one as Windows.
*path \NTS\NeoGrub.mb* tells us the location of the files needed to boot Ubuntu (at least i think those files serve that purpose - correct me if im wrong).

4.)First were gonna change the partition from "C" to the one you have wubi installed on.
(Note: if the right partition of your wubi installation in already selected, skip this step - in my case that would be if i installed wubi on drive C:)

type:"bcdedit /set {*copy the number under "identifier" in here*} device partition=E:" 

(without "", insted of "E" type the letter of the drive you have wubi installed on)
If everything went right you will get "The operation completed successfully." Otherwise look for possible typos.

After that type "bcdedit" again. We now see that the *device* changed from *partition=C::* to partition=E )

[IMG]http://img190.imageshack.us/img190/6730/68971793.jpg[/IMG]

5.)Its time to change the path to our boot files.

type:"bcdedit /set {*copy the number under "identifier" in here*} path \ubuntu\winboot\wubildr.mbr"

(Note: "\ubuntu\winboot\wubildr.mbr" is the path on your drive, so check how you named the first folder (i named it *ubuntu, *dont forget to check the name of yours, and enter the right folder name.) The *\winboot\wubildr.mbr *should be the same for everyone.

Again if everything went fine you will get "The operation completed successfully.". 
Type "bcdedit" again and you will see that *path* changed.

[IMG]http://img520.imageshack.us/img520/1544/14595285.jpg[/IMG]

6.)You are now done! Close the Command prompt, restart your pc and boot into Ubuntu. :D

Enjoy!!!

---

### Post by izint on 2009-07-27
i just tried this but it gives me an error
when i try to boot it
Try (hd0,0): NTFS5: No wublidr
Try (hd0,1): NTFS5: No wublidr
Try (hd0,2): invalid or null
Try (hd032): invalid or null
Cannot find GRLDR
Press space bar to hold the screen,.....
Timeout: #

I'm trying to do this, where Wubi worked fine when I first installed, then I reformatted by windows partition and reinstall it

---

