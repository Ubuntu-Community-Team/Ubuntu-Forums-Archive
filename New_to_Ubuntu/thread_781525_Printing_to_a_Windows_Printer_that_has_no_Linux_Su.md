---
title: "Printing to a Windows Printer that has no Linux Support"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by timorrill on 2008-05-04
Dear Ubuntu Experts,

I have a Lexmark X4850 printer, which is listed by the OpenPrinting database as a "paperweight" ([http://openprinting.org/show_printer.cgi?recnum=Lexmark-X4850](http://openprinting.org/show_printer.cgi?recnum=Lexmark-X4850)).

I know that I cannot install this printer directly on Ubuntu.

The printer is currently set up on a (separate) Windows machine, and is working well. Is there any way to "tell" the Windows machine on my network to print a document on my behalf? 

I am currently running Ubuntu 8.04 in a dual-boot configuration with Windows XP. The printer issue is the only thing that is keeping me from switching to Ubuntu full-time.

Thank you!

---

### Post by glennric on 2008-05-04
You will have to share to printer in windows and then use samba to connect to the printer over the network.  I am not sure what you will need to do to set up samba.  After sharing the printer go to System->Administration->Printing and you may already be able to connect.

---

### Post by drsox1899 on 2008-05-04
Try this easy HowTo for installing Samba. Works well.

[http://ubuntuforums.org/showthread.p...ht=samba+howto](http://ubuntuforums.org/showthread.p...ht=samba+howto)

Having a static IP address is not needed, but ensure that you tell the system that you don't.

See in the HowTo :

" .... -> wins support = yes

If your box doesn't have a static ip-address, or you cannot configure your router/server to provide you with a fixed dhcp-lease, change this configuration parameter to "no".

In this case you cannot use the benefits of WINS. .... "

Luck

---

### Post by timorrill on 2008-05-04
For some reason, I can't the Samba HowTo link to work.

---

### Post by drsox1899 on 2008-05-04
> **timorrill said:**
> For some reason, I can't the Samba HowTo link to work.

How far did you get ?  Do you have a connection with other Windows PCs from your Ubuntu PC ?

---

### Post by timorrill on 2008-05-04
I went to System | Administration | Printing and clicked "New Printer". I selected "Windows Printer Via Samba" and used the "Browse" button to navigate through the Workgroup to the Windows machine and selected the printer. Authentication is not required, so I just hit forward.

The next screen wanted me to select a driver, or provide a PPD file. I don't know if I have a PPD file with the Windows driver for the printer; I was unable to find it searching for "*.ppd". I selected "Lexmark" as the make, and the next screen provided a list of models. My model, the X4850, is not listed. There is an X73 listed, which I tried with no luck (the printer did show some activity, spitting out a page with nothing on it... I as attempting to print an OpenOffice document).

Should I have selected "Generic" as the make of the printer, instead of "Lexmark"?

Or should I go about this some other way?

---

### Post by MayOne.Net on 2008-05-04
Unfortunately, you will need to set up a virtual postscript printer on windows with ghostscript and then share the virtual printer via samba. 

I haven't done it myself because Canon finally released the drivers I needed, but here are several useful links I found when looking into how to do this:

My favorite: [http://www.mat3impex.com/wiki/index.php?title=How_to_use_a_Image_Class_Printer_as_a_Post_Script_Printer_in_Windows_%26_Share_from_MAT3UBengali_Linux](http://www.mat3impex.com/wiki/index.php?title=How_to_use_a_Image_Class_Printer_as_a_Post_Script_Printer_in_Windows_%26_Share_from_MAT3UBengali_Linux)

And Several other forums posts:

[http://ubuntuforums.org/showthread.php?t=589546](http://ubuntuforums.org/showthread.php?t=589546)
[http://ubuntuforums.org/showthread.php?t=347730](http://ubuntuforums.org/showthread.php?t=347730)

Finally a wiki for Gentoo:
[http://gentoo-wiki.com/HOWTO_Native_Windows_Printing_with_CUPS/Samba](http://gentoo-wiki.com/HOWTO_Native_Windows_Printing_with_CUPS/Samba)

Good luck.

---

### Post by timorrill on 2008-05-05
I followed the instructions on the first site listed, and everything seemed to work well.

However, one problem remains. When I do the "Print Test Page" step, I am getting a test page that has almost no top margin. When I try to print anything to the redirected printer, there is no top margin. I can now print from Linux though, also with no top margin.

Any suggestions?

I have tried to set up the redirected printer with several different drivers, with no luck.

Is there a setting that I have incorrect in Ghostscript or GSView?

---

### Post by MayOne.Net on 2008-05-05
Hmm, I'm not sure, what is going wrong. Are you printing the test page from the linux box or the windows box? 

If you haven't yet, you can print a test page directly from the GS printer on the windows box by selecting properties on the GS printer and hitting the "Print Test Page" on the General tab. This will at least tell which side to look at.

---

### Post by timorrill on 2008-05-05
It is happening from both the Windows machine and the Linux machine.

---

### Post by MayOne.Net on 2008-05-06
It sounds like the problem is with the GS settings on the Windows box, and unfortunately, I know next to nothing about GS. The one thing you might try is poking around the Printing Preferences & Advanced Settings. I think GS defaults to A4 rather then letter, but I don't think that would crop the top of the page.

---

