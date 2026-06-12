---
title: "Script to Install Vector NTI 10 with Wine"
date: 2007-01-26
forum: Outdated Tutorials &amp; Tips
---

### Post by misha680 on 2007-01-26
**These instructions have been updated for wine 0.9.37 and higher. The old scripts are still available for [0.9.33]("http://misha680.googlepages.com/InstallVectorNTI10.33.sh") and [0.9.29]("http://misha680.googlepages.com/InstallVectorNTI10.sh") and later but are not recommended.**

Vector NTI 10 is the gold standard product available free of charge to researchers in the molecular biology community for designing and manipulating DNA and protein sequences. For more information, please see the [Vector NTI Community]("https://catalog.invitrogen.com/index.cfm?fuseaction=userGroup.home"). 

The following instructions are designed to get the *optimal* installation experience (with all menus, etc.). If they are too complicated, you can just do step 1 & then download and double-click the Vector NTI installer from Invitrogen, but a few things will be missing.

**1. Install wine**

Please follow the instructions [here]("http://www.winehq.org/site/download-deb") to install the latest version of Wine. This is necessary as the builtin version of wine in Feisty is 0.9.33, which is not new enough to accomodate these instructions. *DO NOT* follow instructions from other HOWTOs that specify using winetools.

**2. Create .wine directory if necessary using wineprefixcreate command.**

This is necessary (for step 3) if you just installed wine or if you have not used it before. If you are already using other programs with wine, you do not need to do this (but you might run into programs if you have made any tweaks to get those other programs to run).

**3. Place mfc42.dll (just search google) into .wine/drive_c/windows/system32.**

This is not strictly necessary, but without it install will not create a few things like Web ordering in the tools menu.

**4. Run the Vector NTI installer (wine "Vector NTI Advance 10.exe") and follow all instructions provided until told install is complete.**

You can also just double click on the installer Executable.

**5. *(NOT REQUIRED ON 0.9.40)* Run wineboot to simulate a Windows reboot and create all the Invitrogen items in the "wine" menu.**

You may have to log out and back in to actually see these changes in your menu.

**6. *(NOT REQUIRED ON 0.9.40)* Run winecfg, and select "Windows 98" mode.**

This takes care of some glitches (esp. visualizing circular molecules) that occur when running in Win2000 mode.
   
**7. ADVANCED: If you want to associate, e.g., ".gb" files with Vector NTI...**

[INDENT]a. You need to make a simple shell script. Applications->Accessories->Text Editor, type this is in and save it somewhere (I have a bin subdirectory in my home directory and call this file winestart because it lets you start files with wine):

```

#!/bin/sh
wine start `winepath -w $*` 

```        

Save the file and exit.

b. Now right click on the file, Properties..., Permissions tab, and check "Allow executing file as program." Click OK. Or you can type in:

```

chmod +x ~/bin/winestart

```

c. Now, find a file you'd like to "associate" with a program that runs in wine (like Vector NTI) that is also associated with that program in Windows. Right click on the file, properties..., Open With tab, Add button, Custom, type in the path to the file you created like ~/bin/winestart, Ok, and make sure the little radiobutton next to winestart is clicked. Now press Ok.

Now, every time you double click on such a file (e.g., .gb), it will launch  in Vector NTI.
[/INDENT]

Known problems:
[INDENT]1. winhelp functionality is not fully implemented in Wine. Therefore the Help menus are not currently usable at the moment.
[/INDENT]

Let me know if you have any other problems, and I will try to address them here/submit patches to wine to fix them.

Misha

---

### Post by biotux on 2007-02-20
Dear Misha,
Thank you so much for this great script. I can finally completely dump the windows installation on my laptop.
I just found one little bug in the script. When it creates the desktop link to VectorNTI it is directed to /home/misha/bin... which I then had to change to my own home directory.
Anyway I owe you a beer for this :) 

Best wishes,
BioTux

P.S. My system: Ubuntu 6.10 with wine 0.9.31

---

### Post by misha680 on 2007-02-21
No prob, glad it worked for you and helped you dump windows. I fixed the error... guess people who don't have my username should be able to run it too :) Beer's good too.

Oh yeah, and running with 0.9.31 is definitely good, as there are some bug fixes in that version that affect Vector NTI.

Misha

> **biotux said:**
> Dear Misha,
Thank you so much for this great script. I can finally completely dump the windows installation on my laptop.
I just found one little bug in the script. When it creates the desktop link to VectorNTI it is directed to /home/misha/bin... which I then had to change to my own home directory.
Anyway I owe you a beer for this :) 

Best wishes,
BioTux

P.S. My system: Ubuntu 6.10 with wine 0.9.31

---

### Post by kabu on 2007-02-22
Hi all,

I tried to follow all the instructions..installed the latest wine 0.9.31 on ubuntu 6.10 and installed cabextract and unzip...I set the permission to allow the script to be executed as a program and when I click on RUN IN TERMINAL, I see a black window poping up for half a second before disappearing and that's it ..no error message no nothing.
I have to admit I am not a big user of ubuntu but i followed all the intructions..any idea what could be my problem ??? I 'd really like to have this working..thanks

---

### Post by misha680 on 2007-02-22
Hi, what I would do is to try to run the script from Terminal, because the problem is if there is some kind of error message in a script Terminal will just close right away, which isn't very helpful to actually seeing the error message.

So what I'd do is start Terminal from Applications->Accessories->Terminal. Then you need to change the current directory into wherever you saved the script. Probably easiest thing would be just to make sure it is in the home directory with the execute permissions and then type:

```

cd ~

```

Then to run the script type:

```

./InstallVectorNTI10.sh

```

now I think based on the behavior you described it will give you some kind of error. Post the error here and then I will have to instruct you further.

Misha

> **kabu said:**
> Hi all,

I tried to follow all the instructions..installed the latest wine 0.9.31 on ubuntu 6.10 and installed cabextract and unzip...I set the permission to allow the script to be executed as a program and when I click on RUN IN TERMINAL, I see a black window poping up for half a second before disappearing and that's it ..no error message no nothing.
I have to admit I am not a big user of ubuntu but i followed all the intructions..any idea what could be my problem ??? I 'd really like to have this working..thanks

---

### Post by kabu on 2007-02-22
Hi and thanks for your quick answer!

I ran the script from the terminal and I got a message saying that CABEXTRACT needs to be installed. 
When I tried to install it using: sudo aptitude install cabextract i get a serie of tasks "done", the last one is "building tag database" done and then I get  "couldnt find any package whose name or description matched "cabextract"
what should i do now??? thanks for ur help..

---

### Post by misha680 on 2007-02-22
> **kabu said:**
> Hi and thanks for your quick answer!

I ran the script from the terminal and I got a message saying that CABEXTRACT needs to be installed. 
When I tried to install it using: sudo aptitude install cabextract i get a serie of tasks "done", the last one is "building tag database" done and then I get  "couldnt find any package whose name or description matched "cabextract"
what should i do now??? thanks for ur help..

Sure. I think you don't have the "universe" repository enabled. To do this go to System->Administration->Software Sources. Type your password, then make sure that "Community maintained Open Source Software (universe)" is enabled and click "Close." This should reload your sources files, and then you should be able to do:

```
sudo aptitude install cabextract
```

Let me know how it goes.

Misha

---

### Post by kabu on 2007-02-22
Hi Misha,

You were right! I enabled the universe software settings and i was able to install cabextract.
I ran the script..the download went fine..the installation was going on for 20 minutes..i left my computer on,hopefully the installation will be done by tomorrow morning :)
I will let u know, thanks again!

---

### Post by misha680 on 2007-02-22
> **kabu said:**
> Hi Misha,

You were right! I enabled the universe software settings and i was able to install cabextract.
I ran the script..the download went fine..the installation was going on for 20 minutes..i left my computer on,hopefully the installation will be done by tomorrow morning :)
I will let u know, thanks again!

Great, let me know how it goes.

Misha

---

### Post by kabu on 2007-02-23
Hey Misha,

After failing the installation a few times with the error "stack overflow", it finally worked.
I was able to launch VNTI and also the database, but i cannot open any molecule (i'm very familiar with the software) and I am getting the attached errors in the terminal. any clue??
thanks!

---

### Post by misha680 on 2007-02-23
Ok, so I am not sure what the "stack overflow" error is as I have never seen anything like that when installing Vector NTI, so that concerns me a bit. As for the the errors you are getting in Terminal, the wine program actually prints out a lot of errors that aren't really significant, and I checked your list and it is the same thing I get if I run Vector NTI but it works fine and loads molecules fine too. So perhaps you could tell me more about what exactly is going on when you are trying to load molecules. First, are you loading a molecule from a file, the database, the network? (I would try to load a plasmid from the database for the first test.) When you say it is not loading, what exactly is happening when you try to load it?

Misha

p.s. Maybe the thing you are referring to is also that the Load Molecule dialog box looks empty when you start it up because there are some redrawing problems right now (although in the next version of Wine that has not come out yet there is a fix for this), but if you just move the load molecules window off the screen and back on again, it will force a redraw and you will be able to see everything that's there. Also you can just blindly click in the right places and it will work as everything on the window is there it just does not draw correctly when it starts up. Maybe that is the problem...

> **kabu said:**
> Hey Misha,

After failing the installation a few times with the error "stack overflow", it finally worked.
I was able to launch VNTI and also the database, but i cannot open any molecule (i'm very familiar with the software) and I am getting the attached errors in the terminal. any clue??
thanks!

---

### Post by kabu on 2007-02-23
hello,

It's not a redrawing problem. When I try to open any molecule from the database (either by double clicking or right click>>open) just nothing happens at all, as I haven't clicked.

HOWEVER, when I open a molecule from File>>Open ..it works beautifully!!!
Thank u for this genius work!!!!!!!!!

---

### Post by misha680 on 2007-02-24
> **kabu said:**
> hello,

It's not a redrawing problem. When I try to open any molecule from the database (either by double clicking or right click>>open) just nothing happens at all, as I haven't clicked.

HOWEVER, when I open a molecule from File>>Open ..it works beautifully!!!
Thank u for this genius work!!!!!!!!!

No prob, its not genius. What is pretty cool though is I've been getting some patches into wine recently and if my latest patches go through all that will be required to install Vector NTI on wine in the next version will be:

1. Copy mfc42.dll to the .wine/drive_c/windows/system32 directory (you can get this file on google search).
2. Run the Vector NTI installer executable.

Down from like 20 steps before.

Misha

---

### Post by misha680 on 2007-02-26
Ok, I fixed a bug in the installer. It had an ampersand where it shouldn't have which could have caused a lot of chaos. The new version should work better for ppl who have had problems (I think it depends on your computer speed, if it is fast the action will finish in time for the next one, if not there will be problems).

Misha

---

### Post by benebeck on 2007-03-09
Hi Misha,

thanks a lot for this script. I have now Vector NTI running on Debian Etch (testing) and now I can kick windows from my labtop soon :-)

Did someone already manage to register to enable more functions? This demo-version is somewhat limited (especially direct importing of GenBank-Files, pasting and saving of sequences is not allowed).

benebeck

-------------------
Debian Etch
wine 0.9.32

---

### Post by benebeck on 2007-03-12
Ok, I did it myself :) 

If you are in non-profit research, you can simply register and get a one-year free trial version that allows to use more of the features.
Due to problems in installation it didn´t work in the beginning but now everything is fine.

Thanks again,

Benebeck

---

### Post by frogotronic on 2007-03-19
Hey Misha,

  Thanks for the script - It's amazing!

I just installed and tried out VectorNTI 10 Advance on Feisty Fawn Herd 5 pre-release.  I'm running WINE 0.9.32-0ubuntu1 and looks good.

Cheers,
- CH


   :guitar:

---

### Post by misha680 on 2007-03-19
Glad it worked on feisty. I actually have written all the patches for wine that take care of the very last thing (MSI scripting) that is necessary so that the script is not required (mfc42 would be though), and they are sitting in the wine patch queue, but apparently the way I made one of the definition files (IDT) is not the proper way for wine (it has to be done in a specific way so as not to possibly infringe Microsoft copyright), so it will probably have to be redone (no intellectual work involved, basically involves looking at one file and making another one like it but different in a few ways like parameter names and order of some attributes)...

Anyway, writing a grant until April 5th so maybe will try to redo the def file then... then there will be no more script required :)

Misha 

> **cement_head said:**
> Hey Misha,

  Thanks for the script - It's amazing!

I just installed and tried out VectorNTI 10 Advance on Feisty Fawn Herd 5 pre-release.  I'm running WINE 0.9.32-0ubuntu1 and looks good.

Cheers,
- CH


   :guitar:

---

### Post by misha680 on 2007-03-29
Sorry to bump my thread but I have made a new (much simpler) script that works with 0.9.33 (and prob 0.9.32) to account for patches myself & other ppl have gotten into wine for those releases. It is linked back in the first post. I think this might help some ppl solve their install problems.

Misha

---

### Post by carromeu on 2007-05-02
Hi Misha

Primarily, thanks for your efforts to install Vector in Ubuntu. However, I tried, tried and tried, but haven't success installing the program (I used the two scripts that you wrote and, finally, only the wine 0.9.36). I found different errors, but the most common was attached as desktop screen picture (corrupted archive - note: the archive is OK for installation). When I don't have the error (using the scripts), the installation was not completed (sometimes by the same error, sometimes with no errors, but without the exe archive installed). Do you have any idea?

Thanks in advance.

Carromeu.  

> **misha680 said:**
> **5-1-07: As of 0.9.36 with Feisty, no script is necessary. Just download the Vector NTI 10 installer and install :)**

**3-29-07: New [script]("http://misha680.googlepages.com/InstallVectorNTI10.33.sh") for wine version 0.9.33 and later that is simpler and I think should work for more ppl (but make sure to wait for everything to fully install before running Vector NTI, the script will finish but Vector NTI will keep installing).  **



---

### Post by misha680 on 2007-05-02
Hmm... the corruption error does seem quite odd. What I would try is the following. The Vector NTI installer executable that you download from Invitrogen is actually a CAB archive, and you can extract it with the following command:

```
cabextract Vector\ NTI\ Advance\ 10.exe
```

Now if it is really corrupt, this should fail. Otherwise, if you are using wine 0.9.36, you
should just be able to install by typing:

```
wine setup.exe
```

Let me know if this works.

Misha

> **carromeu said:**
> Hi Misha

Primarily, thanks for your efforts to install Vector in Ubuntu. However, I tried, tried and tried, but haven't success installing the program (I used the two scripts that you wrote and, finally, only the wine 0.9.36). I found different errors, but the most common was attached as desktop screen picture (corrupted archive - note: the archive is OK for installation). When I don't have the error (using the scripts), the installation was not completed (sometimes by the same error, sometimes with no errors, but without the exe archive installed). Do you have any idea?

Thanks in advance.

Carromeu.

---

### Post by carromeu on 2007-05-02
Hi Misha

Thanks for your reply. Just now I solved the problem: uninstall completely the wine and Vector and re-install all (using only wine 0.9.36). Now every thing is OK and working.  The only problem is with plasmid visualization (linear is OK, but the circular is broken - figures) and with restriction fragment analysis (the program do with all active enzymes, not only the enzymes that I have selected). Do you have the same problem?

Thanks again,
Carromeu.

---

### Post by azelter on 2007-05-02
I'm using wine version 0.9.33 kernel 2.6.20-15-generic feisty and VNTI works quite well for me. I don't have the problems you describe. Thanks Misha!

---

### Post by misha680 on 2007-05-02
> **carromeu said:**
> Hi Misha

Thanks for your reply. Just now I solved the problem: uninstall completely the wine and Vector and re-install all (using only wine 0.9.36). Now every thing is OK and working.  The only problem is with plasmid visualization (linear is OK, but the circular is broken - figures) and with restriction fragment analysis (the program do with all active enzymes, not only the enzymes that I have selected). Do you have the same problem?

Thanks again,
Carromeu.

The visual thing looks like a regression in the newer wine version... will have to look into it.

Misha

---

### Post by misha680 on 2007-05-03
> **carromeu said:**
> Hi Misha

Thanks for your reply. Just now I solved the problem: uninstall completely the wine and Vector and re-install all (using only wine 0.9.36). Now every thing is OK and working.  The only problem is with plasmid visualization (linear is OK, but the circular is broken - figures) and with restriction fragment analysis (the program do with all active enzymes, not only the enzymes that I have selected). Do you have the same problem?

Thanks again,
Carromeu.

Ok easy fix for this one (at least for the visual thing... let me know if it works for the restriction fragment analysis). Run winecfg and switch to Windows 98 mode after installing (when you sue the scripts this is automatically done for another reason, but installing in 0.9.36 and above just by running the installer this will have to be done manually).

Misha

---

### Post by frogotronic on 2007-05-03
Cool!

I just thought I had to live with the visual bug - I'll try this next time I use VectorNTI.

- CH


:guitar:

---

### Post by carromeu on 2007-05-03
Hi Misha

Great! You are right! Now the visual look and the restriction analysis are OK! Thanks a lot!

Carromeu :) .

> **misha680 said:**
> Ok easy fix for this one (at least for the visual thing... let me know if it works for the restriction fragment analysis). Run winecfg and switch to Windows 98 mode after installing (when you sue the scripts this is automatically done for another reason, but installing in 0.9.36 and above just by running the installer this will have to be done manually).

Misha

---

### Post by misha680 on 2007-05-26
I submitted some new wine patches last night that should fix problems with opening molecules from VectorNTIExplorer and also allow you to associate .gb and other files in GNOME with wine so you can open them in Vector NTI by double-clicking on them.

For the latter, you will need to make a shellscript, say call it /home/yourusername/bin/winestart that is as follows:

```

#!/bin/sh
wine start Z:$*

```

Make it executable (right click on it, Properties, Permissions, allow executing program as executable), and now right click on a file type you want to associate with a wine application, and then again Properties, Open With, add, custom, browse for the script you made, and finally make sure the radio label to the left of winestart is selected so it is default.

That's it. Will be in 0.9.38.

Misha

---

### Post by entobuntu on 2007-06-01
Thanks to Misha's advice, I've got Vector NTI 10 working well on a Core Duo notebook running 6.06. 

1. install wine 0.9.37 (or later;) 
2. run wine to generate its directories
3. run winecfg and select W2K
4. run wine "Vector NTI Advance 10.exe" and be patient
5. you can run winecfg again afterwards to select win98 -avoids some graphics issues.

it seems wine and CXO happily co-exist; but the latter won't install VNTI...

Again many thanks to Misha!

:D

---

### Post by misha680 on 2007-06-01
> **entobuntu said:**
> Thanks to Misha's advice, I've got Vector NTI 10 working well on a Core Duo notebook running 6.06. 

1. install wine 0.9.37 (or later;) 
2. run wine to generate its directories
3. run winecfg and select W2K
4. run wine "Vector NTI Advance 10.exe" and be patient
5. you can run winecfg again afterwards to select win98 -avoids some graphics issues.

it seems wine and CXO happily co-exist; but the latter won't install VNTI...

Again many thanks to Misha!

:D

Just to cut it down to the bare necessities, steps 2 & 3 shouldn't be necessary (the default is win2k already and running wine 'Vector NTI Advance 10.exe" should generate
the .wine directory and subdirectories just like running wine by itself will).

Glad to be of help. Going to have to start my round the world free beer trip soon :)

Misha

---

### Post by misha680 on 2007-06-03
Btw, it looks like to get all the Invitrogen stuff to show up in your "wine" menu just run ```
wineboot
``` after you install it (this should in theory work months later too).

You will then have to log out and back in.

Misha

---

### Post by DSAKA on 2007-06-06
this is probably a stupid question, but I'm new to Linux...so now that I've successfully installed Vector NTI how do I run the program!
Thanks! :grin:

---

### Post by misha680 on 2007-06-06
> **DSAKA said:**
> this is probably a stupid question, but I'm new to Linux...so now that I've successfully installed Vector NTI how do I run the program!
Thanks! :grin:

No problem, first try the insturcitons in the very comment above, run wineboot and then log out and
log back in. If it worked, you should see it in your Applications->Wine->Invitrogen menu. If not, please let me know. 

Otherwise, you will have to navigate through the wine directories. You can do this graphically by going to your home directory (places/home folder), View->Show HIdden files to show hidden files, then navigate through .wine, drive_c, Program Files, Invitrogen, Vector NTI, and run Vector NTI 10.exe (double -click, I think you can right click and "Make shortcut" and drag that to the desktop too). But really the above with wineboot should work.

Misha

---

### Post by DSAKA on 2007-06-06
> **misha680 said:**
> No problem, first try the insturcitons in the very comment above, run wineboot and then log out and
log back in. If it worked, you should see it in your Applications->Wine->Invitrogen menu. If not, please let me know. 

Otherwise, you will have to navigate through the wine directories. You can do this graphically by going to your home directory (places/home folder), View->Show HIdden files to show hidden files, then navigate through .wine, drive_c, Program Files, Invitrogen, Vector NTI, and run Vector NTI 10.exe (double -click, I think you can right click and "Make shortcut" and drag that to the desktop too). But really the above with wineboot should work.

Misha

the above didn't work...(wineboot and killall...) Then I got confused (this was before I read your post about navigating to the program) and tried "wine Vector NTI Advance 10.exe" got an error message that it couldn't be found. Then I went to applications and suddenly I had a Wine folder with the program in it...so not sure how it worked, but everything's OK now! Thanks!

---

### Post by misha680 on 2007-06-06
> **DSAKA said:**
> the above didn't work...(wineboot and killall...) Then I got confused (this was before I read your post about navigating to the program) and tried "wine Vector NTI Advance 10.exe" got an error message that it couldn't be found. Then I went to applications and suddenly I had a Wine folder with the program in it...so not sure how it worked, but everything's OK now! Thanks!

No prob. Btw, I have updated the very first post with clear (step-by-step)  instructions on installing Vector NTI.

Misha

---

### Post by xavierman on 2007-06-17
Hey guys,

I'm quite new to Ubuntu but thanks to detailed Misha's instructions I managed to install Vector NTI on my Feisty! It's working just fine so far except that from time to time it justs crushes :( But still, it works fine enough to completely forget about WIndows. Vector NTI was the only application that made me reluctant of removing Windows but now I have no more excuses!
Thanks Misha!!!

Xavier

---

### Post by misha680 on 2007-06-17
> **xavierman said:**
> Hey guys,

I'm quite new to Ubuntu but thanks to detailed Misha's instructions I managed to install Vector NTI on my Feisty! It's working just fine so far except that from time to time it justs crushes :( But still, it works fine enough to completely forget about WIndows. Vector NTI was the only application that made me reluctant of removing Windows but now I have no more excuses!
Thanks Misha!!!

Xavier

Glad to help out. The crashes are a known (rather new) bug in Wine

[http://bugs.winehq.org/show_bug.cgi?id=7959](http://bugs.winehq.org/show_bug.cgi?id=7959)

Hopefully it will get fixed soon, as it actually affects pretty much any Wine app.

Misha

---

### Post by misha680 on 2007-06-22
Btw, as of wine 0.9.40 (will be out in a week or week and half) Vector NTI's visual corruptions running under win2k have been fixed, and switching to windows 98 mode in winecfg will no longer be necessary.

Misha

---

### Post by pkuldg on 2007-07-16
Hi Misha,

Thank you for your instructions. however, I am having trouble to install Vector NTI on my Ubuntu 7.04. I've tried Wine version 0.9.33 and 0.9.41, but neither works. I can get the program right to the start of its installation and it said "Error" then quit. Here's the messages I got from the terminal. I'd appreciate your input. Thanks again!

```

ldg@ldg-biology:~/VectorNTI$ err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:msi:MSI_OpenDatabaseW open failed r = 80030050!
fixme:msi:MSI_OpenDatabaseW open failed r = 80030050!
err:msi:call_script Could not find CLSID for Windows Script
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"c:\\windowsC:\\windows\\system32\\msxml4.dll"
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1

```

---

### Post by misha680 on 2007-07-16
> **pkuldg said:**
> Hi Misha,

Thank you for your instructions. however, I am having trouble to install Vector NTI on my Ubuntu 7.04. I've tried Wine version 0.9.33 and 0.9.41, but neither works. I can get the program right to the start of its installation and it said "Error" then quit. Here's the messages I got from the terminal. I'd appreciate your input. Thanks again!

```

ldg@ldg-biology:~/VectorNTI$ err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:msi:MSI_OpenDatabaseW open failed r = 80030050!
fixme:msi:MSI_OpenDatabaseW open failed r = 80030050!
err:msi:call_script Could not find CLSID for Windows Script
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"c:\\windowsC:\\windows\\system32\\msxml4.dll"
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1

```

It looks like this is happening when you run the installer (correct?). If so try (**note this will erase anything else you may have installed in wine!!!**) with wine 0.9.41:

```

rm -rf ~/.wine
wine "Vector NTI Advance 10.exe"

```

Let me know if that helps.

Misha

---

### Post by pkuldg on 2007-07-16
I tried to run your shell script several times without success (got stuck at the "Creating WINE prefix"), then I tried to directly install by wine "vector nti..." and thus the error message.

However, using your method above it woked for me this time! I've played with it a little bit and so far everything seems fine. Thank you very much, Misha. One less reason to boot back into Windows. :)

---

### Post by misha680 on 2007-07-22
> **pkuldg said:**
> I tried to run your shell script several times without success (got stuck at the "Creating WINE prefix"), then I tried to directly install by wine "vector nti..." and thus the error message.

However, using your method above it woked for me this time! I've played with it a little bit and so far everything seems fine. Thank you very much, Misha. One less reason to boot back into Windows. :)

I am glad it worked for you. The shell script is only required for older versions of wine...

Misha

---

### Post by GuildNavigator on 2007-07-31
After fidgeting a bit with it (I think most of the problems were due to my previous non-scripted installation attempts), I got Vector NTI working on my laptop and imported all of my old molecules!

Thank you so much for the script!  You are a Linux GOD!  And I bet you have a marvelous singing voice, too.

---

### Post by azelter on 2007-08-09
I just followed the instructions and installed VNTI in Gutsy (wine version 0.9.42). Everything seems to work well - except that the screen refresh is terrible. For example minimising/maximising windows within VNTI when you have several vectors open causes the contents to be unreadable. Do you think this is a 0.9.42 issue as it seems to perform less well than when I had it installed using an earlier version of wine? Also, if I downgrade the wine version post-VNTI-install (i.e. now) am I likely to break VNTI. As it is at the moment - it is still preferable to running VNTI from inside vmware, which is my other option.

---

### Post by misha680 on 2007-08-09
> **azelter said:**
> I just followed the instructions and installed VNTI in Gutsy (wine version 0.9.42). Everything seems to work well - except that the screen refresh is terrible. For example minimising/maximising windows within VNTI when you have several vectors open causes the contents to be unreadable. Do you think this is a 0.9.42 issue as it seems to perform less well than when I had it installed using an earlier version of wine? Also, if I downgrade the wine version post-VNTI-install (i.e. now) am I likely to break VNTI. As it is at the moment - it is still preferable to running VNTI from inside vmware, which is my other option.

Hi, glad things are generally working well, but for whatever reason I can't reproduce your problems with refresh on 0.9.42 or on git. You should be able to change the wine version as much as you want without affecting (at least irreversibly) Vector NTI as it resides in your ~/.wine directory which is not touched by the wine package. You can try moving back a version and let me know how it goes.

Misha

P.S. Maybe you can let me know exactly what you are doing to run into this problem? Do you see it in any other wine apps? Non wine apps? Are you
using a 64-bit system (I am not, and my laptop is pretty old and slow so I don't think it is a timing issue).

P.P.S. Also since you are using 0.9.42 I am assuming you followed the non-script install instructions skipping the steps that are not required for
0.9.41 and up? If not, please try reinstalling that way. Also maybe there's a problem with Gutsy's wine packages, not sure tho as I am using Feisty
and will prob do so until I get a new laptop in the late fall (I believe that Ubuntu packages are done by a different person than winehq's and may
have additional patches, not really sure tho).

P.P.S. Btw, in 0.9.43 web ordering will now work properly (not that anyone prob cares except maybe Invitrogen :) )

---

### Post by azelter on 2007-08-10
Hi Misha,
I remover gutsy's version of wine and installed the wineHQ version for feisty and the problems are solved. I guess the gutsy version has it's own issues at the moment. I can't say if they are generic as I don't run any other MS programs (except office and that uses crossover's version of wine).
Thanks for your help and advice.
Alex

---

### Post by misha680 on 2007-08-10
> **azelter said:**
> Hi Misha,
I remover gutsy's version of wine and installed the wineHQ version for feisty and the problems are solved. I guess the gutsy version has it's own issues at the moment. I can't say if they are generic as I don't run any other MS programs (except office and that uses crossover's version of wine).
Thanks for your help and advice.
Alex

Glad it worked for you. Nowadays I usually wait a month before a new version of Ubuntu is released ot upgrade (then again I only have one computer and I like to keep it fairly stable).

Misha

---

### Post by kabu on 2007-09-22
Hi Misha,

Do you think this wine technology will ever work on OSX ? Vector NTI doesn't run on Tiger :(

---

### Post by frogotronic on 2007-09-22
> **kabu said:**
> Hi Misha,

Do you think this wine technology will ever work on OSX ? Vector NTI doesn't run on Tiger :(

It should run natively on OS X

[http://www.invitrogen.com/content.cfm?pageid=10130](http://www.invitrogen.com/content.cfm?pageid=10130) 

- CH    :lolflag:

---

### Post by misha680 on 2007-09-22
> **kabu said:**
> Hi Misha,

Do you think this wine technology will ever work on OSX ? Vector NTI doesn't run on Tiger :(

If you are talking about Intel-based Macs, it should definitely work at some point. I don't really have any
experience using wine on Macs so I don't know how well Vector NTI will or will not work on Mac with wine (but as the underlying Mac support gets better it should start working better), but you might want to check out:

[http://wiki.winehq.org/MacOSX](http://wiki.winehq.org/MacOSX)

for some tips. Let me know how it goes.

Misha

p.s. For PowerPC macs there would need to be an emulator, and this would be a much more significant undertaking, although I believe there is a group "working" on this as well (although I don't know at what pace).

---

### Post by kabu on 2007-09-22
Thanks for the link Misha, I'll go through it and hope it will install the latest wine on my intel based mac.
My question might sound stupid but...under earlier versions of Wine we had to first install your script but not anymore, is this because your script is now incorporated in the latest wine releases? And so this would mean if I manage to install the latest Wine on my intel-mac there is a good chance that it might work there as well ?? :o
Thanks!
Kabu

---

### Post by misha680 on 2007-09-23
> **kabu said:**
> Thanks for the link Misha, I'll go through it and hope it will install the latest wine on my intel based mac.
My question might sound stupid but...under earlier versions of Wine we had to first install your script but not anymore, is this because your script is now incorporated in the latest wine releases? And so this would mean if I manage to install the latest Wine on my intel-mac there is a good chance that it might work there as well ?? :o
Thanks!
Kabu

Good luck. No prob about het question, it is not stupid. My scripts were workarounds for bugs in wine versions of DLLs (DLLs are "libraries" of functions that programs like Vector NTI call to perform certain operations) by installing native versions e.g., from microsoft.com. Later, these underlying bugs in the wine versions of the DLLs were fixed and thus the scripts are no longer necessary. So from this perspective none of the bugs that were fixed will break when running on Mac etiher (and thus no script is necessary).

_However_, there are some more low-level wine functions, etc. that depend on the underlying operating system (e.g., things like writing to a file, the network, etc. differ between Linux and BSD/MacOS sometimes), and there may be bugs in these implementations, so there could be other bugs (however, since these bugs are more lower level they are likely to affect more programs that run with wine and thus more likely to get fixed without any input/help from me than the very Vector NTI-specific bugs that the scripts would workaround earlier).

Hope this explains things. Let me know how things go.

Misha

---

### Post by frogotronic on 2007-10-17
totally and complete crash with wine 0.9.47

---

### Post by misha680 on 2007-10-17
> **cement_head said:**
> totally and complete crash with wine 0.9.47

Umm... what caused the crash? Can you repeat it by doing whatever caused it? Is there any command line output? Not sure what to make of your message above as is...

Misha

---

### Post by frogotronic on 2007-10-17
the installer crashed as per before you made the scripts for versions 0.9.29 +.  I'm going to try trashing my wine install (only Vector NTI was attempted to have the install and then use the highest script 0.9.33?)

MDAC
JET PACKs

are missing and the installer kaks.

- CH

---

### Post by frogotronic on 2007-10-17
didn't work - script (*.33.sh) says there is a .vectornti dir, but I can't see it

---

### Post by misha680 on 2007-10-17
> **cement_head said:**
> didn't work - script (*.33.sh) says there is a .vectornti dir, but I can't see it

Ok, not sure what you are doing but here is what I just did and it worked fine for me (granted on git, which is a little bit more recent than 0.9.47 but not much):

(1) rm -rf ~/.wine 

will delete your wine prefix

(2) wine "Vector NTI Advance 10.exe"

will start the installer.

That is all you really need to do, there is no need to (nor should you) use any of the scripts on 0.9.47

Pls let me know if you are still having problems
Misha

---

### Post by frogotronic on 2007-10-17
okay.

whatever caused the first attempt problem was not repeated.  everything installed okay (I think).

Another question:  How do I get the wine menu to show up?  doesn't seem to be ANYWHERE

Thanks
CH

---

### Post by misha680 on 2007-10-17
> **cement_head said:**
> okay.

whatever caused the first attempt problem was not repeated.  everything installed okay (I think).

Another question:  How do I get the wine menu to show up?  doesn't seem to be ANYWHERE

Thanks
CH

Easiest way for the menu to show up, just log out and log in (at least for GNOME, should work for KDE too I imagine).

Misha

---

### Post by Carambakaracho on 2007-11-23
> **misha680 said:**
> 

(2) wine "Vector NTI Advance 10.exe"

will start the installer.

That is all you really need to do, there is no need to (nor should you) use any of the scripts on 0.9.47

Misha

Great, no need to do more than that. (on Gutsy and fresh installed wine 0.9.46 from the repositories).
It could not have been easier.

CarambaKaracho

---

### Post by misha680 on 2007-11-23
> **Carambakaracho said:**
> Great, no need to do more than that. (on Gutsy and fresh installed wine 0.9.46 from the repositories).
It could not have been easier.

CarambaKaracho

Yup, took about six months of patching wine to get it to that point though :)

Misha

p.s. I believe if you don't install mfc42.dll first you'll be missing some of the Web ordering stuff in the Tools menu, but really that's pretty much stuff I don't think most people use anyhow although I'm sure the Invitrogen people consider that stuff to be pretty important.

---

### Post by Leo the Lion on 2007-12-20
Misha, I'm very new to all this and have just switched to ubuntu 7.10. I've installed "wine", but I'm not sure how to create a .wine directory. Could you please guide me through this?
Thanks a bunch.

---

### Post by misha680 on 2007-12-20
> **Leo the Lion said:**
> Misha, I'm very new to all this and have just switched to ubuntu 7.10. I've installed "wine", but I'm not sure how to create a .wine directory. Could you please guide me through this?
Thanks a bunch.

No prob. If you have Gutsy Gibbon you can just create this .wine directory by going to Applications -> Wine -> Configure Wine and just running that (or any wine app) will create your .wine directory.

Once that's done you can to Browse C:\ Drive in the same menu and you will already be in .wine/drive_c . Then you can put mfc42.dll in the windows/system32 folder in there.

Of course if you really don't need the full Tools menu with some of the Invitrogen web ordering, you can just skip these steps and download the Vector NTI installer and just double click on it. Otherwise, you would do this at this point.

Oh and make sure you have the latest Wine version and not just the one from the repository. This info I believe is in my howto (well it's just a link to [www.winehq.org's](www.winehq.org's) page on how to set this up), but let me know if you
need any more help.

Let me know if this helps/doesn't

Misha

---

### Post by Leo the Lion on 2007-12-21
WOW, thanks for the quick reply. I'll try this out tonight. I've been trying to convert everybody in my lab to Ubuntu. So far, the only problem holding them back was getting VNTI to work. No excuses now :)

---

### Post by misha680 on 2007-12-21
> **Leo the Lion said:**
> WOW, thanks for the quick reply. I'll try this out tonight. I've been trying to convert everybody in my lab to Ubuntu. So far, the only problem holding them back was getting VNTI to work. No excuses now :)

No prob hope it works out for you. It really works very well with wine (help search/contents still don't work in wine though, but that's for all apps and winehelp supposedly is a milestone for wine 1.0 which is slated I think for next summer... we'll see).

Misha

---

### Post by Leo the Lion on 2007-12-23
Misha680,
I was able to get installation started but after a while an "error" window popped up and installation was terminated. Any idea of what this might be?
BTW, I'm running Gutsy 7.10.

---

### Post by misha680 on 2007-12-24
> **Leo the Lion said:**
> Misha680,
I was able to get installation started but after a while an "error" window popped up and installation was terminated. Any idea of what this might be?
BTW, I'm running Gutsy 7.10.

What error was it exactly? Did you make sure that you are using the WineHQ wine packges and not the default Gutsy ones following the instructions in the link on the very first post in this thread?

If not or if you did just try:

```

rm -rf ~/.wine
wine ~/Desktop//Vector\ NTI\ Advance\ 10.exe

```

this assumes you put the Vector NTI installer on the desktop. In any case when reporting an error the actual window that popped up (all the words in it if not a screen capture) would be quite useful.

Thanks
Misha

---

### Post by Leo the Lion on 2007-12-25
I followed your instructions to a T, and everything was installing just fine. The error message that popped up just said "Error". I'm starting to think that the VNTI file I downloaded might have gotten corrupted in the process.

---

### Post by misha680 on 2007-12-25
> **Leo the Lion said:**
> I followed your instructions to a T, and everything was installing just fine. The error message that popped up just said "Error". I'm starting to think that the VNTI file I downloaded might have gotten corrupted in the process.

Hmm that does sound odd I am not sure honestly. So you even tried doing the rm -rf ~/.wine and then calling wine on the installer directly? I will try later to see if I can reproduce, which version of wine are you using (I believe wine --version will give you the version number)?

Thanks
Misha

p.s. Just tried under wine 0.9.51. I had to do an extra wineboot at one point when it had to reboot during install, but other than that it installed fine and did not give me an error. Let me know if you are unable to fix this by redownloading the binary and making sure you have wine 0.9.51 by using wine --version

---

### Post by kabu on 2008-02-13
Hi Misha,

I have managed to install Darwin on my mac intel and install VNTI too. It works but it keeps flickering, its not as stable as in Wine. Do u know why ? Thanks

Kabu

---

### Post by misha680 on 2008-02-13
> **kabu said:**
> Hi Misha,

I have managed to install Darwin on my mac intel and install VNTI too. It works but it keeps flickering, its not as stable as in Wine. Do u know why ? Thanks

Kabu

Hi Kabu,

I was actually playing around with MacOS in VMWare (I don't have a Mac) and install Darwine and VNTI. Darwine is known not to be as mature as wine on linux platforms so maybe this is causing your flicker, but personally when I played on the VMware install I didn't get any. Maybe also try XFree86 instead of the stock Apple X server (I think you can install it through fink), don't know if this will help.

Did you use the Darwine installer from:
[http://www.thisismyinter.net/](http://www.thisismyinter.net/)

It's pretty handy.

Misha

---

### Post by kabu on 2008-02-16
Hi Misha,

It wasnt working at all after installing xfree86 :( so I had to reinstall x11. Are you saying that you had VNTI  running on OSX via VMWARE and it was as stable as on Linux/Wine ??
All you did is install Darwin from the tidbits website or did u do anything else ?
Thanks!

Kabu

---

### Post by misha680 on 2008-02-17
> **kabu said:**
> Hi Misha,

It wasnt working at all after installing xfree86 :( so I had to reinstall x11. Are you saying that you had VNTI  running on OSX via VMWARE and it was as stable as on Linux/Wine ??
All you did is install Darwin from the tidbits website or did u do anything else ?
Thanks!

Kabu

Hi Kabu,

Sorry about Xfree86. You might try asking about Mac specific issues on tidbits or somewhere else too.

So I don't think Wine/MacOS can work as well as it does on Linux/Wine, mainly b/c I don't think the MacOS platform really gets as much Wine attention as Linux (therefore there should be more underlying problems that will cause probs).

However, after I installed MacOS in VMWare (which is quite a pain in itself, this would be something very long to describe) and then wine from tidbits package and VNTI on top of that I did not experience any flicker.

The only other thing I did was install some of the ms core fonts. I used the winetricks package which can always be found at:
[http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

However, I did not do very thorough testing. All I can say is basic stuff seemed to work and there was no flicker.

Misha

p.s. btw just remembered something. I think the one time I would see flicker is when resizing a window... But certainly not at any other time.

---

### Post by Leo the Lion on 2008-02-27
Hi Misha,
I had Vector NTI running just fine on my Ubuntu 7.10, however, after one of those updates, it stopped working properly.

I'm able to open up Vector NTI and Vector NTI Explorer. However, when I try to open a molecule it just hangs. 
Here's a screenshot of what it looks like.

---

### Post by frogotronic on 2008-02-27
> **Leo the Lion said:**
> Hi Misha,
I had Vector NTI running just fine on my Ubuntu 7.10, however, after one of those updates, it stopped working properly.

I'm able to open up Vector NTI and Vector NTI Explorer. However, when I try to open a molecule it just hangs. 
Here's a screenshot of what it looks like.

Similiar problem here - VectorNTI has stopped working with 0.9.55 update on my Gutsy install.

- CH

---

### Post by misha680 on 2008-02-27
Crap I get it too. I guess for now downgrade wine (Synaptic -> wine package -> Force Version)

A regression test will have to be done (and a bug filed on winehq and/or I'll fix it):

[http://wiki.winehq.org/RegressionTesting?highlight=%28Regression%29](http://wiki.winehq.org/RegressionTesting?highlight=%28Regression%29)

I'll try to do one when I have time, but currently busy at work, so if I have to use VNTI for now I'll just downgrade prob.

Misha

---

### Post by Leo the Lion on 2008-02-28
> **misha680 said:**
> Crap I get it too. I guess for now downgrade wine (Synaptic -> wine package -> Force Version)

A regression test will have to be done (and a bug filed on winehq and/or I'll fix it):

[http://wiki.winehq.org/RegressionTesting?highlight=%28Regression%29](http://wiki.winehq.org/RegressionTesting?highlight=%28Regression%29)

I'll try to do one when I have time, but currently busy at work, so if I have to use VNTI for now I'll just downgrade prob.

Misha

How do I downgrade wine? I'm a noob, so go easy on me :0).

Thanks.

---

### Post by Leo the Lion on 2008-02-28
Nevermind, got it. With the downgrade, Vector NTI works fine again.

---

### Post by misha680 on 2008-02-28
> **Leo the Lion said:**
> Nevermind, got it. With the downgrade, Vector NTI works fine again.

Cool. For anyone else:

1. open synaptic
2. search for the wine package
3. Package menu
4. Force Version option
5. Select the one labeled gutsy (or whichever one is below .55)

Misha

---

### Post by frogotronic on 2008-02-28
> **Leo the Lion said:**
> How do I downgrade wine? I'm a noob, so go easy on me :0).

Thanks.

download and install 0.9.54 deb from winehq:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Then choose LOCK VERSION from Synaptic

- CH

---

### Post by misha680 on 2008-03-02
Btw I checked on the git version and it looks like this is already fixed so it should be fixed in 0.9.56.

Misha

---

### Post by brunovecchi on 2008-05-11
Thanks a lot Misha. This was the one thing that was preventing me from completely formatting my Windows partition. The install worked perfectly! Thank you!

---

### Post by misha680 on 2008-05-12
> **brunovecchi said:**
> Thanks a lot Misha. This was the one thing that was preventing me from completely formatting my Windows partition. The install worked perfectly! Thank you!

Glad to hear it worked so well.

Misha

---

### Post by cubicdau on 2008-06-05
Thank you for the little script. There are just two things I'd like to mention:

1. Vector NTI does install under last testing release (1.0-rc1-1) at least on a 64bit-Debian machine. 

2. You have to place the .exe at the drive_c directory in order to install, otherwise you'd get a bunch of errors.

---

### Post by misha680 on 2008-06-14
> **cubicdau said:**
> Thank you for the little script. There are just two things I'd like to mention:

1. Vector NTI does install under last testing release (1.0-rc1-1) at least on a 64bit-Debian machine. 

2. You have to place the .exe at the drive_c directory in order to install, otherwise you'd get a bunch of errors.

Btw I just tried with wine-1.0-rc4 on 64-bit Hardy Heron (amd64) installing from ~/wine with the commands:
```
mv ~/.wine ~/.wineold
wine ~/wine/Vector\ NTI\ Advance\ 10.exe

```
with no errors. Are you still having this problem? What kind of errors do you get?

Misha

---

### Post by kabu on 2008-06-29
Thanks for keeping the updates Micha!

Is it possible to run Vector NTI on Macs too at this stage ? I heard it works if you install Darwine (the Mac version of Wine) as described on this site: [http://vnti.subject-expert.com](http://vnti.subject-expert.com)
Do you know if it is as reliable as Wine for Linux ?
thanks!
Kabu

---

### Post by alperyilmaz on 2008-07-03
I'm using Hardy and I'm trying to install Vector NTI.
Wine has memory problem with new kernel versions and gives 
"preloader: Warning: failed to reserve range 00000000-60000000" error upon running. But how come everybody here is reporting it's working fine even with latest Ubuntu versions?
Besides that problem, Vector NTI does not install at all with Wine in my machine. This the error message I get:

```

alper@alper-laptop:~/.wine/drive_c$ wine Vector\ NTI\ Advance\ 10.exe 
preloader: Warning: failed to reserve range 00000000-60000000
Warning: could not find DOS drive for current working directory '/home/alper/.wine/drive_c', starting in the Windows directory.
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"c:\\windows\\system32\\Vector NTI Advance 10.exe": Module not found
alper@alper-laptop:~/.wine/drive_c$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))

```
I tried the newest Wine from Ubuntu repositories and in accordance with earlier posts in this thread, I tried older version of Wine (0.9.54) and I still get the same error. What is the trick that it installs, works fine in your machine?

---

### Post by misha680 on 2008-07-07
> **alperyilmaz said:**
> I'm using Hardy and I'm trying to install Vector NTI.
Wine has memory problem with new kernel versions and gives 
"preloader: Warning: failed to reserve range 00000000-60000000" error upon running. But how come everybody here is reporting it's working fine even with latest Ubuntu versions?
Besides that problem, Vector NTI does not install at all with Wine in my machine. This the error message I get:

```

alper@alper-laptop:~/.wine/drive_c$ wine Vector\ NTI\ Advance\ 10.exe 
preloader: Warning: failed to reserve range 00000000-60000000
Warning: could not find DOS drive for current working directory '/home/alper/.wine/drive_c', starting in the Windows directory.
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"c:\\windows\\system32\\Vector NTI Advance 10.exe": Module not found
alper@alper-laptop:~/.wine/drive_c$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))

```
I tried the newest Wine from Ubuntu repositories and in accordance with earlier posts in this thread, I tried older version of Wine (0.9.54) and I still get the same error. What is the trick that it installs, works fine in your machine?

I have hardy amd64, completely updated as of this morning. Here is my kernel info (uname -a):
```
Linux misha-d630 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux
```
My current wine version (wine --version):
```
wine-1.1.0
```
Try reinstalling Vector NTI in terminal as follows (upgrade to wine 1.0 first):
```
mv ~/.wine ~/.wineold
wine /path/to/vector/nti/installer/Vector\ NTI\ Advance\ 10.exe
```
wait for install and then to run either use the menu entry or:
```
wine ~/.wine/drive_c/Program\ Files/Invitrogen/Vector\ NTI\ Advance\ 10/Vector\ NTI\ 10.exe
```
Let me know if you still have problems.

Misha

---

### Post by misha680 on 2008-07-07
Oh yeah and get wine 1.0 from [www.winehq.org](www.winehq.org) (Downloads) if not available from repos.

---

### Post by misha680 on 2008-07-07
> **kabu said:**
> Thanks for keeping the updates Micha!

Is it possible to run Vector NTI on Macs too at this stage ? I heard it works if you install Darwine (the Mac version of Wine) as described on this site: [http://vnti.subject-expert.com](http://vnti.subject-expert.com)
Do you know if it is as reliable as Wine for Linux ?
thanks!
Kabu

[http://wiki.winehq.org/FAQ#head-5bba8bcc401e4ee1d3b733501f98768a47e661e6](http://wiki.winehq.org/FAQ#head-5bba8bcc401e4ee1d3b733501f98768a47e661e6)

has some info for running on the Macs. I've tried the unofficial builds linked from there with Vector NTI on an Intel mac and it seemed to work fine, but I didn't play with it sufficiently. You should try it and let us know.

Misha

---

### Post by alperyilmaz on 2008-07-07
Hi Misha,

I removed the old version of Wine (i did it manually by deleting all files and folders containing Wine related stuff) and installed the Wine from repositories (version 1.0).

This time Wine installed and RAN correctly. I didn't get any preloader errors. Then I did Vector NTI installation which went smooth and now Vector NTI works fine. 

thanks for your help..
alper

---

### Post by misha680 on 2008-07-07
> **alperyilmaz said:**
> Hi Misha,

I removed the old version of Wine (i did it manually by deleting all files and folders containing Wine related stuff) and installed the Wine from repositories (version 1.0).

This time Wine installed and RAN correctly. I didn't get any preloader errors. Then I did Vector NTI installation which went smooth and now Vector NTI works fine. 

thanks for your help..
alper

Hi Alper,

I'm glad everything worked out.

Misha

---

### Post by xtalhammy on 2008-07-21
Hi,

I managed to install vector NTI on Ubuntu hardy running wine-1.0.0. Most things are working fine, however the fonts in the results page of a protein BLAST are messed up and therefore unreadable. Any ideas here?

---

### Post by misha680 on 2008-07-21
> **xtalhammy said:**
> Hi,

I managed to install vector NTI on Ubuntu hardy running wine-1.0.0. Most things are working fine, however the fonts in the results page of a protein BLAST are messed up and therefore unreadable. Any ideas here?

Glad installation worked for you. Here is a screenshot of BLAST results on my computer (attached), what does yours looks like (Ubuntu Menu -> Applications -> Take Screenshot is quite useful)

Btw, do you have Microsoft Core Fonts installed? You can find it in Ubuntu Menu -> Applications -> Add/Remove Programs... just search for core (type it in the search box and press enter), it might help not sure.

Misha

---

### Post by xtalhammy on 2008-07-22
Thanks, apt-get install msttcorefonts did the trick.

best
Michael

---

### Post by misha680 on 2008-07-23
> **xtalhammy said:**
> Thanks, apt-get install msttcorefonts did the trick.

best
Michael

Glad it worked out.

Misha

---

### Post by davebridges on 2009-01-02
Has anyone checked this with the new version (11) of Vector NTI Advance?

---

### Post by azelter on 2009-01-05
> **davebridges said:**
> Has anyone checked this with the new version (11) of Vector NTI Advance?

I don't know if anyone noticed, but as of VNTI 11, this software will no longer be free. It seems they have also removed the Vector NTI usercommunity pages (at least the links don't work as of today). I don't know if this means VNTI 10 free licenses will soon be disabled or not, but I suppose it's time to back up my database into plain text and search for alternative software. What a shame as VNTI runs so nicely under linux now....
Alex

---

### Post by jocko on 2009-01-06
> **azelter said:**
> I don't know if anyone noticed, but as of VNTI 11, this software will no longer be free. It seems they have also removed the Vector NTI usercommunity pages (at least the links don't work as of today). I don't know if this means VNTI 10 free licenses will soon be disabled or not, but I suppose it's time to back up my database into plain text and search for alternative software. What a shame as VNTI runs so nicely under linux now....
Alex
Try [clc sequence viewer]("http://www.clcbio.com/index.php?id=28"). It's free, runs on windows, mac and linux and I think it can import a vnti database. It may lack some features available in vnti, so it's up to you to decide if it's what you need.
I use it at work (where we also have a licence for clc genomics workbench and dna workbench, so I don't miss anything from vnti...). A problem I've noticed with the linux version is that it does not run if compiz is running, so a "metacity --replace" may be needed to get it started.

---

### Post by azelter on 2009-01-06
Thanks very much for the pointer. I will give it a go.

---

### Post by Miche on 2009-08-25
Hello Mischa, sorry to bother you again with Vector NTI; thanks so much for all your efforts in order to make it run. 
I'm actually escaping from clone manager and Windows. Since I work in molecular biology I need something reliable and powerful. So far, pDRAW32 and APE did not match the expectations. But at least both run under Ubunutu Jaunty (I'm on a 64 bits PC). Regarding Vector NTI, lots of struggle but it does not work at all. I tried first 11, than I found your post and I tried 10.
Problems: even if I remove wine I still have a folder INVITROGEN under applications -> wine. 
I run .exe from the terminal and a part the redundant error messages I have this one:
err:rundll32:main Unable to load L"\00e2\0012\0081\\ime.dll"
which stucks everything. The funny thing is that the installer recognizes the previuos installation and asks me to modify, repair or remove. None of those work. I have been able to install V NTI 11 only the very first time I tried, but it stucked finalizing the installation. 
I'm testing right now trial softwares from clcbio. I want to have a suitable prgram for my job without depending on licensed softwares. Too optimistic?
Any clue will be really appreciate. Thanks for your great effort..
Miche

---

### Post by frogotronic on 2009-08-25
[http://www.clcbio.com/index.php?id=28](http://www.clcbio.com/index.php?id=28)

---

### Post by misha680 on 2009-08-25
> **cement_head said:**
> [http://www.clcbio.com/index.php?id=28](http://www.clcbio.com/index.php?id=28)

In all honesty I have stopped working on this project and am now in Computational Neuroscience. However I have in fact tried the CLC viewer and have found it adequate.

Misha

p.s. Vector NTI 10 should still work on older Wine versions maybe 1.0 or 1.1 (?) I would try those.

---

### Post by Miche on 2009-08-25
Hi guys, 

thank you all for your support. 
I was after CLC DNA workbench (or genomics), but the license expires in 29 days. Sequence viewer has a few limitations. 
Before I "adapt" to workbench (i.e.: convert files and so forth) I want to solve license issue. 
I wrote them asking for single users and "students'" access. Hopefully I'll be able to let you know more in the next few days. 
Good luck everybody in this jungle of cloning softwares!
M

---

### Post by meital101 on 2011-02-13
Hello, 
I have just bought vector NTI from invitrogen and I am trying to install it, however I am coming across an error message saying:
 
There was a problem starting the \ime.dll
The specified module could not be found
 
I know this may sound quite basic, but I am not even sure what the \ime.dll is, it sounds like a drive on the computer, however when installing I made sure that the installation path did not have this name in the address....
 
What should I do?
Thank you very much
Meital

---

