---
title: "[SOLVED] Brother MFC-240c not printing"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-05-19
My Brother MFC-240C printer won't print. Sane works!

mark@Lexington-19:~$ sudo lsusb
 
Bus 003 Device 002: ID 04f9:01ab Brother Industries, Ltd 

I'm not getting any error messages. The printer icon does NOT appear in the panel.

Synaptic PM shows the MFC-240C as installed. HELLlppp!

---

### Post by HotShotDJ on 2008-05-19
You may need to set it up in System --> Administration --> Printing.  Take a look there first and if you run into trouble, check back with us. :)

OH.. found this after I posted the above: [https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging)

---

### Post by avtolle on 2008-05-19
> **Mark_in_Hollywood said:**
> My Brother MFC-240C printer won't print. Sane works!

mark@Lexington-19:~$ sudo lsusb
 
Bus 003 Device 002: ID 04f9:01ab Brother Industries, Ltd 

I'm not getting any error messages. The printer icon does NOT appear in the panel.

Synaptic PM shows the MFC-240C as installed. HELLlppp!
[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793) is something to which you might want to refer, if you haven't already. Used it to install MC-240C under 8.04. There might be something in there that would help you. BTW, see my post to the thread several weeks ago about setting up a directory (sorry, my notes aren't here, and memory isn't good) that the installer will look for, but which isn't set up under 8.04; a note to this effect is on the Brother website as well. HTH.

Edit: At the terminal ```
mkdir /usr/share/cups/MFC240C
``` is what is needed to be created, IIRC.

---

### Post by Mark_in_Hollywood on 2008-05-19
> **HotShotDJ said:**
> You may need to set it up in System --> Administration --> Printing.  Take a look there first and if you run into trouble, check back with us. :)

OH.. found this after I posted the above: [https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging)

Please see the attached screenshots.

---

### Post by avtolle on 2008-05-19
> **Mark_in_Hollywood said:**
> Please see the attached screenshots.
From what you posted, you have the "generic" driver installed. You will need to install the appropriate driver from the Brother website, the details of which are contained in the link I posted a bit ago.

---

### Post by Mark_in_Hollywood on 2008-05-19
> **avtolle said:**
> [http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793) is something to which you might want to refer, if you haven't already. Used it to install MC-240C under 8.04. There might be something in there that would help you. BTW, see my post to the thread several weeks ago about setting up a directory (sorry, my notes aren't here, and memory isn't good) that the installer will look for, but which isn't set up under 8.04; a note to this effect is on the Brother website as well. HTH.

Edit: At the terminal ```
mkdir /usr/share/cups/MFC240C
``` is what is needed to be created, IIRC.

Your Edit has me a little confused. I can do the cut & paste in the terminal, but what is IIRC?

---

### Post by HotShotDJ on 2008-05-19
> **avtolle said:**
> You will need to install the appropriate driver from the Brother websiteNo.  This is no longer necessary.  The drivers are in the regular ubuntu software repository. See [https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging)

---

### Post by avtolle on 2008-05-19
IIRC=If I recall correctly. Do not cut and paste that. :-)

---

### Post by avtolle on 2008-05-19
> **HotShotDJ said:**
> No.  This is no longer necessary.  The drivers are in the regular ubuntu software repository. See [https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging)
Good to know.

---

### Post by Mark_in_Hollywood on 2008-05-19
I tried to do the instructions given above via links to other threads.

I d/l-d the brother lpr driver. Right click brought up GDebi. See attached screenshots.

---

### Post by HotShotDJ on 2008-05-19
> **Mark_in_Hollywood said:**
> I tried to do the instructions given above via links to other threads.Mark... please use the packages found in the standard software repository (System --> Administration --> Synaptic Package Manager).  Look at the web site I linked to.  Find your printer model, and then use Synaptic to install the proper package.

---

### Post by Mark_in_Hollywood on 2008-05-19
> **HotShotDJ said:**
> Mark... please use the packages found in the standard software repository (System --> Administration --> Synaptic Package Manager).  Look at the web site I linked to.  Find your printer model, and then use Synaptic to install the proper package.

That is what I did. Using Syn PM, I found the Brother packages and installed them. Still no printer. 

Please see my previous post for screenshots of trying to reinstall the lpr.

---

### Post by avtolle on 2008-05-19
> **Mark_in_Hollywood said:**
> I tried to do the instructions given above via links to other threads.

I d/l-d the brother lpr driver. Right click brought up GDebi. See attached screenshots.
You need both the lpr driver and the cups wrapper for that printer, or at least I did. BTW, are you using AMD-64 8.04?

---

### Post by HotShotDJ on 2008-05-19
> **Mark_in_Hollywood said:**
> That is what I did. Using Syn PM, I found the Brother packages and installed them. Still no printer. 

Please see my previous post for screenshots of trying to reinstall the lpr.Right... when you did the gdebi thing, you got the conflict.  Which is fine.  You do not want to install the downloaded package.  Now go back to the printing dialog that we looked at earlier.  Select the Brother printer that isn't working.  Now, click on the "Change" button next to the printer make and model line.  Work through the dialogs... they should be self explanatory.  This will change your system to use the proper driver, now that it is installed.

---

### Post by HotShotDJ on 2008-05-19
> **avtolle said:**
> You need both the lpr driver and the cups wrapper for that printerWhen he installed the driver package for his printer, the cups wrapper SHOULD have been pulled in as a dependency.  However, it certainly would not hurt to check that if he has difficulty with setting up the printer in the Printing setup dialog.

---

### Post by avtolle on 2008-05-19
> **HotShotDJ said:**
> When he installed the driver package for his printer, the cups wrapper SHOULD have been pulled in as a dependency.  However, it certainly would not hurt to check that if he has difficulty with setting up the printer in the Printing setup dialog.
Right. Do you know whether installing the driver packages from Synaptic removes the need to create the file the Brother driver looks for, which is not automatically created in 8.04? Since I did my driver install before the drivers were in Synaptic, I'm not familiar with what installing the drivers from the repos does, thus the query.

---

### Post by Mark_in_Hollywood on 2008-05-19
> **avtolle said:**
> You need both the lpr driver and the cups wrapper for that printer, or at least I did. BTW, are you using AMD-64 8.04?

Not using 64bit or AMD.

---

### Post by Mark_in_Hollywood on 2008-05-19
> **HotShotDJ said:**
> Right... when you did the gdebi thing, you got the conflict.  Which is fine.  You do not want to install the downloaded package.  Now go back to the printing dialog that we looked at earlier.  Select the Brother printer that isn't working.  Now, click on the "Change" button next to the printer make and model line.  Work through the dialogs... they should be self explanatory.  This will change your system to use the proper driver, now that it is installed.

Opened the System/Admin/Printing. Saw the MFC-240C, highlighted it, clicked change, saw a small window: "searching for drivers". It closed and re-opened again with "searching for drivers" (or some like words). A moment later, the Printer panel or window, what you may call it, was done, but the Apply or Revert was greyed-out. I closed that and tried to print from Gedit, but nothing printed.

---

### Post by Mark_in_Hollywood on 2008-05-19
Changing the PPD over fixed it.

Thank you everyone.

---

### Post by HotShotDJ on 2008-05-19
> **avtolle said:**
> Do you know whether installing the driver packages from Synaptic removes the need to create the file the Brother driver looks for, which is not automatically created in 8.04?I am operating under the assumption that the packages from the official repository were created correctly for Hardy, and therefore create all the files necessary to use the package.  We will know more when Mark reports back from the last step that I posted above. (I'm a firm believer in crossing a bridge only if I come to it :) )

---

### Post by avtolle on 2008-05-19
> **HotShotDJ said:**
> I am operating under the assumption that the packages from the official repository were created correctly for Hardy, and therefore create all the files necessary to use the package.  We will know more when Mark reports back from the last step that I posted above. (I'm a firm believer in crossing a bridge only if I come to it :) )
Understand not "crossing a bridge" prematurely. Since Mark reports success, there's no need to pursue that one any further it appears.
@Mark, good to hear.

---

### Post by AgentZ86 on 2008-07-28
> **avtolle said:**
> Understand not "crossing a bridge" prematurely. Since Mark reports success, there's no need to pursue that one any further it appears.
@Mark, good to hear.

Thanks for the info, I had recently re-installed everything so my 7.04 printer installation and my notes did not work for 8.04, this was a big help to find that the MFC-240C is in the synaptic package manager, 

After making symbolic links and mkdir directories as the Brother site indicates etc., however I was not getting any messages as the brother site was suggesting to mkdir, so really that did not apply to me.

Anyhow after my searching and re-reading my notes, and wiki's etc etc. 

I found your instructions to use the synaptic to install and it worked soooo easily LOL

Just thought you should know, and to confirm Printing with MFC-240C after installing with synaptic, and YES it did automatically uninstall some of my other lpr and cupswrappers I was trying to get working. And worked flawlessly.


I think you mentioned mkdir ???/MFC240C is no longer needed ?
I just wanted to confirm this is correct that no mkdir is needed for 8.04 32bit install


Anyhow Thanks
:guitar:

---

