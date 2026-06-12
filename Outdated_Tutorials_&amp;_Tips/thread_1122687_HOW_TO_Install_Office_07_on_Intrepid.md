---
title: "HOW TO: Install Office 07 on Intrepid"
date: 2009-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by linnuxnub on 2009-04-11
I ran into many problems trying to install Microsoft Office 2007 on Ubuntu 8.10, and quite frankly Open Office doesn't cut it for me.

It used to be that installing Office 07 on Ubuntu with wine was a large inconvenience, since you had to configure windows dll's and such.

This is how I installed Office, it is really simple to do. Make sure wine is not installed, and that the wine repository is disabled in your software sources.

**Step 1:**
Install Wine 1.1.16 from the old .deb archive ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html))

**Step 2:**
Type ```
winecfg
``` in a terminal and make sure the Windows version is set to XP (I believe it is the default but just to make sure)

**Step 3:**
Run your Office setup in wine.
Using the command line, cd to the directory where your Office setup files are and run:
```
wine setup.exe
```
Using the GUI: Navigate to your Office setup files, right click on the setup.exe file and choose open with "wine windows program loader."

**Step 4:**
Click customize in the setup window and disable any features you do not want, and change any settings (name, organization, etc.), then click install.

**Step 5:**
Once the installation is complete close the window, and navigate to /home/username/.wine/drive_c/Program\ Files/Microsoft\ Office/Office12 and run any office programs to test (WINWORD.EXE, EXCEL.EXE, POWERPNT.EXE, MSPUB.EXE, etc.).

**Step 6:**
Re-enable the wine repository (steps to install repository here: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)), and update wine to the latest version. 

**Step 7:**
Type ```
winecfg
``` in a terminal, then go to the libraries tab. In the "Add new override for library" box type "riched20" (no ") and click add, then click edit and make sure it is set to "native then built in".



That's it, I told you it was easy. Now just create links to these executables for easy access. Type this in the command box when making links to wine programs ```
wine "/pathtoexecutable/"
``` (replace "pathtoexecutable" with a valid file path).

---

### Post by kamitsukai on 2009-04-11
Thank you that was most helpful =] Unfortunately I still an error when installing office 2007 on 64 bit Ubuntu 8.10...

***EDIT***
Sorted now after I'd removed my old wine install I hadn't removed the ".Wine" folder in my home directory before downgrading, but it all works fine now on Ubuntu 8.10 Intrepid 64-bit

---

### Post by msfz751 on 2009-04-11
Thank you, thank you very much for the tip.
Now I can run Office 2007 without the need to open a XP virtual machine.
Flawless installation on 64-bit AMD-3800 Ubuntu Intrepid.
Office runs much, much faster than in virtualized mode.
The WINE guys have made an awesome job.

---

### Post by kamitsukai on 2009-04-11
> **msfz751 said:**
> Thank you, thank you very much for the tip.
Now I can run Office 2007 without the need to open a XP virtual machine.
Flawless installation on 64-bit AMD-3800 Ubuntu Intrepid.
Office runs much, much faster than in virtualized mode.
The WINE guys have made an awesome job.

Agreed they've done a great job although you still can't copy and paste images from Firefox! my one and only moan;)

---

### Post by se2131 on 2009-04-12
Very nice! Unfortunately OneNote 2007 still doesn't work with this (which everyone in my class uses extensively), but great tutorial nonetheless!

---

### Post by john770g on 2009-04-24
Many thanks linnuxnub for the How-To.  Much easier than the DLL gaggle I've had to use previously.
 
Installed Word, Excel, and Powerpoint 2k7 on Ubuntu Jaunty (9.04) following post 1 verbatim.  Word and Excel were working right off the bat, however PowerPoint was hanging on launch.

The fix:

1. Launch Wine Configuration (Applications/Wine/Configure Wine)
2. Libraries tab:  Select 'riched20' from the 'New Override for Library' drop-down menu.  Click add.
3. Highlight 'riched20 (native,builtin) from the existing overrides list.  Click edit.
4. Select the radio button entitled 'Native (Windows)'.  Hit OK.
5. Hit 'OK' to exit 'Wine Configuration'.

Powerpoint should now work - worked for me.

8)

---

### Post by lastrite on 2009-04-25
Worked perfectly, thank you!

---

### Post by StormRoBoT2 on 2009-04-26
> **john770g said:**
> Many thanks linnuxnub for the How-To.  Much easier than the DLL gaggle I've had to use previously.
 
Installed Word, Excel, and Powerpoint 2k7 on Ubuntu Jaunty (9.04) following post 1 verbatim.  Word and Excel were working right off the bat, however PowerPoint was hanging on launch.

The fix:

1. Launch Wine Configuration (Applications/Wine/Configure Wine)
2. Libraries tab:  Select 'riched20' from the 'New Override for Library' drop-down menu.  Click add.
3. Highlight 'riched20 (native,builtin) from the existing overrides list.  Click edit.
4. Select the radio button entitled 'Native (Windows)'.  Hit OK.
5. Hit 'OK' to exit 'Wine Configuration'.

Powerpoint should now work - worked for me.

8)


what version of wine are you using?

---

### Post by StormRoBoT2 on 2009-04-26
This tutorial is great!!!!! Everything work fine for me!!!

I feel free to guild any one who need help with this.. :)

thanks!!! Sooo much!!!

---

### Post by StormRoBoT2 on 2009-04-26
1 last question, will it still work if i update to newer wine?

---

### Post by kamitsukai on 2009-04-26
> **StormRoBoT2 said:**
> 1 last question, will it still work if i update to newer wine?

Yes it wont effect currently installed applications

---

### Post by therascalking on 2009-04-26
This may seem like a silly question ..

But how well do Word and Excel work in Wine? I mean really?

Can you say it's flawless? Same as running on Windows?

I ask because I have FINALLY convinced my dad to move to Ubuntu. I was able to convince him to run Ubuntu only because I promised to install Windows under VirtualBox so he could run Office.

His beef was the documents he brings home to work HAVE to look exactly the same as when he's in the office (where they run Windows XP). I convinced him to give Open Office a whirl but I am fairly certain he won't like it. Old dog .. new tricks. :)

If I could get Office running under Wine it would probably be the final nail in the coffin of Windows. ;)

---

### Post by SunnyRabbiera on 2009-04-26
> **therascalking said:**
> This may seem like a silly question ..

But how well do Word and Excel work in Wine? I mean really?

Can you say it's flawless? Same as running on Windows?

I ask because I have FINALLY convinced my dad to move to Ubuntu. I was able to convince him to run Ubuntu only because I promised to install Windows under VirtualBox so he could run Office.

His beef was the documents he brings home to work HAVE to look exactly the same as when he's in the office (where they run Windows XP). I convinced him to give Open Office a whirl but I am fairly certain he won't like it. Old dog .. new tricks. :)

If I could get Office running under Wine it would probably be the final nail in the coffin of Windows. ;)


Well actually in personal experience Office 2007 installed without me needing to do a thing, but personal experience will vary.

---

### Post by john770g on 2009-04-27
> **therascalking said:**
> This may seem like a silly question ..

But how well do Word and Excel work in Wine? I mean really?

Can you say it's flawless? Same as running on Windows?

I ask because I have FINALLY convinced my dad to move to Ubuntu. I was able to convince him to run Ubuntu only because I promised to install Windows under VirtualBox so he could run Office.

His beef was the documents he brings home to work HAVE to look exactly the same as when he's in the office (where they run Windows XP). I convinced him to give Open Office a whirl but I am fairly certain he won't like it. Old dog .. new tricks. :)

If I could get Office running under Wine it would probably be the final nail in the coffin of Windows. ;)

Work requirements also force me to use Office 2k7, specifically Word, Excel, and PowerPoint.  Other than having used MS Office for upwards of ten years now (as you said - old dog, new tricks), there were a few elements that didn't translate to well into OpenOffice - for example using PowerPoint embedded in Excel.

I've been using Office 2k7 in Wine 1.1.16 under Jaunty 9.04 for about a week and haven't noticed anything aesthetically or functionally that differs from running under winXP.

-John

---

### Post by fougas on 2009-04-28
I followed all steps and it seems to work nicely. Thank you ! Your guide rocks :guitar:

---

### Post by Jesus_Valdez on 2009-04-28
Thank you very much. Another step away from Vista.

---

### Post by Legace on 2009-05-02
Is it **Wine 1.1.16** or **Wine 1.1.6**?

EDIT: I tried 1.1.16 and it works perfectly. Thanks :)

---

### Post by linnuxnub on 2009-05-05
In my experience the only difference between running office 07 on wine and running it on windows is a "slight" lag and the fact that addons do not work, but since very few people use these it is not much of an issue. Also, I don't know if it's just me but I notice a difference in the appearence of fonts on wine as opposed to windows, on wine it appears a little distorted.

---

### Post by bmullan on 2009-06-01
I've tried to install Microsoft Office 07 on a couple machines and everything seems to install OK... so I thought it worked.  I could run Word, Excel, Powerpoint etc... or at least I thought as they all start up ok etc.

Later while trying to SAVE (or SAVE-AS) a file in PPT, XLS or WORD always resulted in a crashed Office 07 App and a box asking if I'd like to report a bug to Microsoft.

I did _not_ use your method to install but I am curious if you can actually SAVE or SAVE AS a file in Powerpoint, Excel or Word.

But I wanted to confirm whether you can actually save or save-as a file created in any of the Office 07 applications.

---

### Post by john770g on 2009-06-02
> **bmullan said:**
> I've tried to install Microsoft Office 07 on a couple machines and everything seems to install OK... so I thought it worked.  I could run Word, Excel, Powerpoint etc... or at least I thought as they all start up ok etc.

Later while trying to SAVE (or SAVE-AS) a file in PPT, XLS or WORD always resulted in a crashed Office 07 App and a box asking if I'd like to report a bug to Microsoft.

I did _not_ use your method to install but I am curious if you can actually SAVE or SAVE AS a file in Powerpoint, Excel or Word.

But I wanted to confirm whether you can actually save or save-as a file created in any of the Office 07 applications.
I've had issues saving to SMB network locations, but no problems saving in any format to the machine I'm running O2k7 on.

---

### Post by ieBrazil on 2009-07-16
Do you consider all these stuff easy? Think of me, a new user? Command ... I am not familiar with them... it sucks me. And repository, and everything!

Anyway. Tnx.


> **linnuxnub said:**
> I ran into many problems trying to install Microsoft Office 2007 on Ubuntu 8.10, and quite frankly Open Office doesn't cut it for me.

It used to be that installing Office 07 on Ubuntu with wine was a large inconvenience, since you had to configure windows dll's and such.

This is how I installed Office, it is really simple to do. Make sure wine is not installed, and that the wine repository is disabled in your software sources.

**Step 1:**
Install Wine 1.1.16 from the old .deb archive ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html))

**Step 2:**
Type ```
winecfg
``` in a terminal and make sure the Windows version is set to XP (I believe it is the default but just to make sure)

**Step 3:**
Run your Office setup in wine.
Using the command line, cd to the directory where your Office setup files are and run:
```
wine setup.exe
```
Using the GUI: Navigate to your Office setup files, right click on the setup.exe file and choose open with "wine windows program loader."

**Step 4:**
Click customize in the setup window and disable any features you do not want, and change any settings (name, organization, etc.), then click install.

**Step 5:**
Once the installation is complete close the window, and navigate to /home/username/.wine/drive_c/Program\ Files/Microsoft\ Office/Office12 and run any office programs to test (WINWORD.EXE, EXCEL.EXE, POWERPNT.EXE, MSPUB.EXE, etc.).

**Step 6:**
Re-enable the wine repository (steps to install repository here: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)), and update wine to the latest version. 

**Step 7:**
Type ```
winecfg
``` in a terminal, then go to the libraries tab. In the "Add new override for library" box type "riched20" (no ") and click add, then click edit and make sure it is set to "native then built in".



That's it, I told you it was easy. Now just create links to these executables for easy access. Type this in the command box when making links to wine programs ```
wine "/pathtoexecutable/"
``` (replace "pathtoexecutable" with a valid file path).

---

