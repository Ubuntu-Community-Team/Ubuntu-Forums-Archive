---
title: "Printer Stopped &quot;Filter Failed&quot;"
date: 2014-08-05
forum: New to Ubuntu
---

### Post by pablo23 on 2014-08-05
I'm really new to ubunty and I'm trying to install a thermal printer which I have the drivers for using CUPS, the system recognizes the printer and I can add it in CUPS, and can even see that it says idle, but when printing I always get Stopped "Filter Failed", so I looked into the CUPS error_log and I can see this error message:
PPD uses qualifier 'Gray..'
Calling FindDeviceById(cups-XP-58)
Found device /org/freedesktop/ColorManager/devices/cups_XP_58
Calling GetProfileForQualifiers(Gray.....)
Failed to send: org.freedesktop.ColorManager.Device.NothingMatched:nothing matched expression 'Gray..,Gray..*,Gray.*.,Gray.*.*,*'
Failed to get profile filename for cups-XP-58
no profiles specified in PPD


I have been looking in the forums and in google with no luck, can anyone help?

Thanks!

---

### Post by pablo23 on 2014-08-06
Ok, after a lot of research and not been able to find anything and guided by the "Failed to get profile filename for cups-XP-58" I tried copying the XP-58.ppd to a cups-XP-58.ppd and it got rid of that error, now the log says it found the profile, but the job is still ending in "Filter Failed" and no previous error is logged. I can not seem find the issue.

---

### Post by pablo23 on 2014-08-06
Ok, I digged into the error log again and I found this problem:
[Job 10] PID 8462 (/usr/lib/cups/filter/rastertoxp) stopped with status 102 (No such file or directory)
however the file is there, why is cups not accesing to it?

---

### Post by willie4 on 2014-09-03
[HTML][/HTML]Any luck with this error?

FYI: I have the same cups issue on my Fedora 19 cups 1.6.4 with the J-speed XP-58.

---

### Post by jess8 on 2014-10-15
I also have this same issue. My printer is a chinese model (xprinter XP-58) that comes with the instructions manual (in chinese), I was able to install the printer on windows 7, but I can't make it work on linux with cups. The error I get is the same: Filter Failed, rastertoxp failed. In my case the file rastertoxp file is extracted from a script that came with my printer to the corresponding folder.

---

### Post by ibod on 2014-11-06
I also had this error today. HP C5280. 
I had a look at several posts and found one that said removing and reinstalling the printer fixed the problem but did not work for me. Then I remembered I had just printed a double sided doc on a non duplex printer by setting the 'Filter' to odd then even pages only. 

I was now trying to print off the first page only, of a document. ( an odd page !! ) With the Filter still set to even pages only (forgot to set it back to all pages)

Needles to say it works fine now. 

I don't suppose this is the cause for all the people with this problem but I hope this will at least help some 

Check the printer filter settings you may have the wrong filter set

---

### Post by kurt18947 on 2014-11-06
> **jess8 said:**
> I also have this same issue. My printer is a chinese model (xprinter XP-58) that comes with the instructions manual (in chinese), I was able to install the printer on windows 7, but I can't make it work on linux with cups. The error I get is the same: Filter Failed, rastertoxp failed. In my case the file rastertoxp file is extracted from a script that came with my printer to the corresponding folder.

I had a somewhat similar problem installing a Samsung Multifunction laser on MX14, a Debian based distro from antix.  This thread has the solution to my problem:

[http://askubuntu.com/questions/390803/samsung-printer-ml-2545](http://askubuntu.com/questions/390803/samsung-printer-ml-2545).

I need to create a symlink. I don't know if this is similar to your problem or not.

---

### Post by dylan41 on 2015-04-15
Did anyone solve this problem because I'm having the same problem with the Xprinter XP-Q200 which uses the XP-80 driver. It just says filter failed and in the debug info the rastertoxp filter says status 127 (File to large)

Getting kind of desperate.

---

### Post by gempur on 2015-06-18
> **dylan41 said:**
> Did anyone solve this problem because I'm having the same problem with the Xprinter XP-Q200 which uses the XP-80 driver. It just says filter failed and in the debug info the rastertoxp filter says status 127 (File to large)

Getting kind of desperate.

I found an alternative drivers for my Xprinter XP360B. 
I use TSC Printer Drivers.
See [https://gempur.wordpress.com/2015/06/18/xprinter-xp360b-di-linux/](https://gempur.wordpress.com/2015/06/18/xprinter-xp360b-di-linux/)

---

### Post by Sergadiz on 2015-08-29
Hello. I hope you fixed your problem a while ago since this thread is more than a year old, but I hope my input helps if not the OP, someone else that might encounter this problem.
I had the exact same problem as you and after months of struggling i finally found the solution. I solved this by installing some 32 bit cups libraries. 
Just execute
```
sudo apt-get install libcupsimage2:i386
```
and 
```
sudo apt-get install libcups2:i386
```

Then just reboot cups or your system and your thermal printer should be working.
I hope this helps.

---

### Post by frisket on 2015-12-25
CUPS regularly ships updates which are plain broken, either in the HP PPD (driver) files, or in the filters. It has happened so often that I have given up even trying to report the errors. I don't know why they do this; the only solution is to download and install hplip. I have no idea what you would do if you are using a non-HP printer. There are two main errors:

 &#8226; In the CUPS-supplied PPD file[s] for HP A3 printers (eg K7100, K8600), there is a bug which crops the image to A4 size, 
   even when printing on A3 paper using the correct A3 settings;
 &#8226; In the CUPS-supplied ps* filters there is some bug which causes the "filter failed" error message. 
   This has been fixed a couple of times, but repeatedly gets unfixed somehow.

Both of these disappear when you install hplip, but if there is then another CUPS update, it breaks (same errors) so you have to install hplip all over again, even if it is the same version.

---

### Post by johanscm50 on 2016-03-30
Thank you very much this solved the problem for me

---

### Post by oldos2er on 2016-03-30
Old thread closed.

---

