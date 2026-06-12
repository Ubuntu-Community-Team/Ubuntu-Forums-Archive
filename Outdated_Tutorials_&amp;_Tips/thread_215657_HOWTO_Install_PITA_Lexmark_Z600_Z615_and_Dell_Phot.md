---
title: "HOWTO: Install PITA Lexmark Z600 Z615 and Dell Photo Printer 720"
date: 2006-07-14
forum: Outdated Tutorials &amp; Tips
---

### Post by numb401 on 2006-07-14
Ok heres my first guide in ubuntu. I'd never thought i'd become this proficient in linux but after enough hacking around I've learned you can get almost anything to work, like the Z600 series of lexmark printers (Also rebranded dell photo 720). So heres my first how-to in anything linux.

First you'll need the drivers from lexmark, you can find those at
[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:433:0:0&searchLang=en&os_group=Redhat&target=](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:433:0:0&searchLang=en&os_group=Redhat&target=)
Or search on lexmark for the redhat drivers.
In a terminal, untar the files you just downloaded using 
```
tar -xvzf CJLZ600LE_CUPS_1_0_1.TAR.gz
```
Since its packaged for redhat, its gonna be a not so straightforeward install to get it to run on your ubuntu system. Next your picking apart the shell script and untarring the install file within
```
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
tar -xvzf install.tar.gz
```

Since rpms are ALMOST worthless to us in ubuntu, you need to install a program called alien to convert them to our favorite .deb packages.
```
sudo aptitude install alien
```
once alien is installed we being the converting, ignore any messages about scripts not being converted, we dont need those.
```
sudo alien -k z600llpddk-2.0-1.i386.rpm
sudo alien -k z600cups-1.0-1.i386.rpm
```
Once you have ran them through alien, you will find nice little .deb packages in the folder you downloaded everything in. First install the pddk (Printer development kit) then install the CUPS driver.
Afterwords if your in gnome, go into System>Administration>Printing and add your printer.
You will find the driver under lexmark as the z600-1.01 or something similar to that.
Congrats now you got that pesky printer running under linux!:D

---

### Post by linuxgeekery on 2006-07-16
Thanks a lot for this. A year ago, Dell was giving these away free with their computers. I didn't have a printer, so I got one. Now it works in linux :KS

---

### Post by twede on 2006-07-21
great forum, lots of help available!  thanks for this posting, my printer works perfectly too  :D

---

### Post by tgow on 2006-07-21
I have a dell photo 944.  Does anyone know if this is perhaps also based on lexmark? If not, does anyone know where I may find some potential ideas or help for getting my Dell Photo 944 to work w/ Ubuntu or linux in general?

Thanks,
tgow

---

### Post by s13_mills on 2006-07-24
Hey - I used the above method to install my lexmark Z615 - the method seemed to go fine, no error messages etc, and the driver installed from the list... but my printer still won't work! Works perfectly with XP.
Any help would be greatly appreciated!

---

### Post by Redindian on 2006-07-26
i was struggling with my printer, it works like a charm now.....thanks.

---

### Post by KBenk on 2006-07-29
Hello,

First of all, I would like to thank you for posting this walk-through. When I first started I really had no idea how to get my printer going.

After saying that, I want to offer a little more help to anyone trying to do this. When I first downloaded the driver from Lexmark it came with a slightly different name than is used in this tutorial. So, when trying to run the command:

```
tar -xvzf CJLZ600LE_CUPS_1_0_1.TAR.gz
```

I kept getting an error message telling me that this was an unknown file. This is because the name of the file that I downloaded was "CJLZ600LE-CUPS-1.0-1.TAR.gz". Therefore the command that I needed to run was:

```
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
```

It is amazing the frustration that these slight variations can cause, but I figured it out and after changing this one command the rest of the process went just as the tutorial stated. So, if you are having trouble go ahead and try the new command. I hope this will be of some help to those of you that are having trouble. 

~KBenk

---

### Post by PhilJ on 2006-08-05
H all,
    I used that howto to install my z600 under breezy no problem
but under dapper I cant get the %^^&&%&!!!!! thing to work with F-photo or gnome photo printer.

it starts printing halfway down the page  (postcard) or wont shrink the photo to fit the page or sometimes just spits the paper out and sits there saying printer busy.

If I use Gimp it works OK

edit  gthumb wont do it either

any ideas ?

Philj
:confused:

---

### Post by lefty.crupps on 2006-08-07
Worked very well, thank you for the great instructions!

---

### Post by hbchrist on 2006-08-13
Worked like a charm in 6.06. Brilliantly done!

---

### Post by JohnJSal on 2006-08-14
Glad I found this thread, because I have a Dell 720. But I'm having a problem with the first line. The file I downloaded was a slightly different name, but when I press <tab> to complete the file name, it doesn't work, it just beeps. So something seems to be wrong, I can't get past the first step!

Edit: Well, just in case anyone else has this problem, I just manually typed the full filename instead of using autocomplete, and the rest worked just fine!

Thanks.

---

### Post by theStorminMormon on 2006-08-15
I appreciate the great tutorial, until I got to this part:

First install the pddk (Printer development kit) then install the CUPS driver.

I'm an absolute noob.  The very first thing I did was figure out how to get Firefox 1.5.0.6 instaled, the 2nd thing I'm trying to do is get my printer working, so I don't know how to intall pddk (or where to get it) or how to install the CUPS driver.  I'm sure the answer is so simple I'll feel stupid when I figure it out, but in the meantime this incredibly easy-to-follow tutorial just ditched me right before the end.  

I feel abandoned!

---

### Post by JohnJSal on 2006-08-15
I had to do some searching for this part too. Just type this at the terminal for both .deb files:

dpkg -i <packagename>

---

### Post by Narpas on 2006-08-17
Or, better yet, just navigate to thier location in Nautilus - the file manager, and double click!

---

### Post by tmpete on 2006-10-11
:KS For a Dell 720, I followed these steps exactly and it worked like a charm.  Thanks so much for this post!

---

### Post by qiemem on 2006-10-22
First off, thanks for posting this!

However, I followed the instructions, and successfully installed the debs in the correct order and everything (pddk then cups), but the driver isn't showing up in the list of Lexmark printers (though there are many Lexmark options). Any thoughts?

Oh, I've got the rebranded Dell Photo 720 and am using Edgy. Does this not work for Edgy?

---

### Post by xwipeoutx on 2006-10-23
I got this working no problem under 6.06, but I recently upgraded to Dapper... I accidentally removed the drivers (was going through synaptic and deleting obselete stuff)... and now I'm having the same symptoms as qiemem (above me) is.

Any help? I've also got rebranded Dell 720 thingy

EDIT: or rather, UPDATE: I went to /usr/share/cups/model, and had a look at the tar.gz file in there, and found a file in the same format as a PPD, so i extracted it to my home folder and gave it a ppd extension and manually went about installing the driver.  It found it as a z600, and added it.

I had to restart the wizard before it showed in the list, but I added it and it works for gedit... doesn't seem to work for evince though (The button stays greyed).  Prepare for another edit... ^_^

---

### Post by xwipeoutx on 2006-10-23
Ok, after a restart things seem to print ok.  Although evince gave me an error saying "Print Error: Successful OK".  Weird.  But at least it printed

---

### Post by qiemem on 2006-10-26
thanks xipeoutx! This worked for me too. Though, for others, you dont actually have to decompress the ppd.gz file since the wizard accepts this as a valid driver install file. haven't tried printing yet, but it should work given that worked for you.

fyi, this is how to install this printer on edgy.

---

### Post by twstokes on 2006-11-10
xwipeoutx, thanks for your tip! That's all it needed to work!

---

### Post by insub2 on 2006-11-20
i have the dell 720 and am running dapper (right now...upgrading to edgy when i get around to it).

i followed the howto and it didn't work.

i'll try a restart and get back to you in a sec.

***

ok, restarted and it seems like it may have worked.
but i think it is out of ink. (i got the printer from my mom and i don't know how much ink she left in it.  looks like none.)

---

### Post by Darrious on 2006-11-21
Does anyone know of a good printer program for ubuntu. 

I mean something that is able to check the amount of ink in the printer and show statistics. 

I really just want it to check ink though.

---

### Post by MsTiggy on 2007-01-08
> **xwipeoutx said:**
> EDIT: or rather, UPDATE: I went to /usr/share/cups/model, and had a look at the tar.gz file in there, and found a file in the same format as a PPD, so i extracted it to my home folder and gave it a ppd extension and manually went about installing the driver.  It found it as a z600, and added it.

I'm having the same problem.  I feel really stupid, though, as I'm a bit of a noob.  Could you explain what you're saying here in more noob-friendly terms?  I'd appreciate it!:KS

EDIT: Nevermind!  I got it working!  I don't really know how I got it working... but it works now, and that's all that matters, hopefully!

---

### Post by Zzwazz on 2007-01-15
I had some trouble installing Alien but I was able to find the .deb files elsewhere.

[http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb)

[http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb)

I got the files off this website:
[http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge](http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge)

After installing the files I went to System>Administration>Printing
then added the printer and installed the driver found in location

/usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz

Hope this helps.

---

### Post by jio on 2007-01-19
Hi, I'm having a little trouble getting your instructions to work.  I have the driver tar file from lexmark, downloaded I can see it on my desktop but when I run the the detarring command as you typed it, an error comes up telling me that file doesn't exist.  Any Ideas?

---

### Post by kochen on 2007-01-21
Hi,
How can I make Dell 720 work on my Ubuntu 6.10 Server?

---

### Post by ssavelan on 2007-01-22
I had to find that the .ppd file was located in:

/usr/share/cups/model/lex*.ppd.gz

to tell the print manager.....

otherwise these are the best instructions out of three.

Thanks

---

### Post by kochen on 2007-01-22
I managed to install the printer & print from command line or from the web manager.
I've installed Samba for Windows printer sharing, but I get access denied on XP machines (although file sharing is working fine) - Vista don't have drivers, so I can't test it...

any ideas?

---

### Post by mac71 on 2007-01-23
As a total idiot and newbie, i found this post invaluable and now have my Dell 720 up and running:) Just a quick note for those equally dim witted - the first command can be ommited as, by default Archive Manager does this automatically for you when you download. I was so daunted and concerned with entering the command line, it took me a looong time to realize the machine had already done it and thats why the initial file could not be found ](*,) Never mind, good learning curve and alls well that ends well:D

---

### Post by olddog58 on 2007-01-31
Beautiful - your post worked great for me.  I'm new to ubuntu, thanks.

---

### Post by blackhole82 on 2007-02-07
I couldn't get this to work with my lexmark x2470 shared printer.  I'm still trying to find a way to get that to work as a network printer on my windows box.  It will show that data is being sent to the printer but nothing will actually print.

---

### Post by krimson on 2007-02-07
i went through this howto, and all seemed to work well, but before i tried using this howto, when i added the printer through the kde printer menu, i could pick the 720, and then it gave me a big list of manu's and models of printers.
now, when i go through those same steps, i have NONE.
i am unsure of where i went wrong, i followed everything, and then just dpkg -i **.deb the two files and thats it!

---

### Post by blakegrover on 2007-02-16
I couldn't see the driver after installing it in the driver selection screen but as someone else posted if you click the button to install the driver from a file and point it to the location:

/usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz

it works great!

Thanks

---

### Post by KIAaze on 2007-02-16
For me everything went fine until the end:
The z600 driver isn't in the list when I try to add the new printer through the gnome control panel. :(

edit:
Nevermind, I just didn't go to the last page of this thread...

I just printed my first page with the Dell 720 under Ubuntu Feisty Fawn perfectly. :D (only tested on B&W text so far)
Thanks a lot for this walkthrough!
And thanks to the poster above me for the tip on how to find the driver. :)

---

### Post by MonkeyPuncher on 2007-03-01
Excellent HOWTO!  I was able to get my Dell 720 up and running on 6.06 in no time.

Has anyone been able to print from XP to a Dell 720 shared via cups?  

I followed these [[COLOR="Blue"]instructions[/COLOR]]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP") and successfully added the printer to my XP box.  When I attempt to print from XP I hear the printer kick in like it is engaging the cartridge carriage but the sheet feeder never loads paper and the job dies.  I do not receive an error in XP and I do not see anything in the cups logs that explains what happened.  On XP I am using the true Dell 720 driver.

---

### Post by kochen on 2007-03-13
Similar problem here.
Installation went fine, but printing doesn't do anything.
(I tried on both XP & Vista with proper drivers)

---

### Post by strabes on 2007-05-12
@monkeypuncher: Sounds like you have the wrong driver installed.

@kochen: In /etc/cups/printers.conf, change "Shared No" to "Shared Yes"

Save the file and restart cups with ```
sudo /etc/init.d/cupsys restart
```

---

### Post by kochen on 2007-05-12
> **strabes said:**
> 
@kochen: In /etc/cups/printers.conf, change "Shared No" to "Shared Yes"

Save the file and restart cups with ```
sudo /etc/init.d/cupsys restart
```

It was always a YES...

---

### Post by wulfhound on 2007-05-19
The drivers aren't there. Can anyone share the driver? Even if you save as the link, it downloads a .tar.gz file that states "this file could not be found on the server".

Hence when I started to unpack it it gave me a status 1 error.

---

### Post by brooksbp on 2007-05-30
Okay. I have had many problems with this tutorial and set out to set this straight.  This method is sure to work for just about any printer with the appropriate PPD file.

1) [http://localhost:631/admin](http://localhost:631/admin)
2) Add a printer / Add detected printer
3) Choose from the PPD's found on your machine / recommended already OR browse for a PPD to use.
4) Install

** In the case of the Dell 720 **

To obtain the PPD: I had to manually extract the PPD from the gz in /usr/share/cups/model/ after running the tutorial on the first post of this thread.  Or you can simply go online and browse for the Lexmark z000 series linux drivers and extract the PPD from those.

HOPE THAT HELPED!!!!!!!!!

---

### Post by seoras on 2007-06-28
Hi,
thanks for the tutorial, well written. However, I followed all the instructions, no errors everything seems OK but the Lexmark Z600 driver doesn't show up in the list.

Any thoughts?

Found the solution (actually in this thread DOH!)
go to /usr/share/cups/model where you'll see a file called Lexmark-Z600-lxz600cj-cups.ppd.gz Extract this archive to Desktop or home folder it will extract a file called X~=@l9q5 so just give it a .PPD extension (X~=@l9q5.ppd) Go to Admin>Printing install new printer and select install driver and just point to the file you just extracted. It should then show up in the list of Lexmark printers as Z600 v1.0-1

---

### Post by FuturePilot on 2007-08-17
I tried all the suggestions in this thread. I've got the printer recognized but nothing will print. I click on the little printer icon in the notification area and it says job:stopped. Any help here?

---

### Post by mackrackit on 2007-08-21
Thank you.

I am able to print to the 720 hoked up to a XP machine.

---

### Post by neoroses on 2007-08-22
man u guys are awsome.....added the ppd file manualy and it worked!!!! brilliant love u alllllllll god save ubuntu

---

### Post by TheSoko on 2007-08-26
I'm running Kubuntu Feisty right now...

I don't get any feedback or errors about my printer! If it's not on the Printers - System Settings page says it's Idle - Accepting Jobs. My printer also sucks at grabbing the next sheet of paper, so if it fails at that it just stops the whole job altogether without telling me anything.

Should I be expecting more information than this?

---

### Post by ironblade on 2007-10-28
Please note you need to install libstdc++5 for the driver to actually DO stuff:
```
sudo aptitude install libstdc++5
```

Cheers!

---

### Post by garyedavidson on 2007-10-29
Thanks for the Great Instructions, This worked Great on My Lexmark X1185

---

### Post by bydlo23 on 2007-10-30
> **ironblade said:**
> Please note you need to install libstdc++5 for the driver to actually DO stuff:
```
sudo aptitude install libstdc++5
```

Cheers!

This is what I was missing. Thank you!

---

### Post by jkblacker on 2007-11-11
Worked for me on Feisty and working now in Gutsy too. Most helpful how-to I've seen :)

---

### Post by EmilyRose on 2007-12-13
Thanks so much! I've now succesfully installed this printer on two different computers! (first w/ edgy and now with gutsy!)

---

### Post by JustinAlf on 2008-04-18
> **bydlo23 said:**
> This is what I was missing. Thank you!

sudo aptitude install libstdc++5

Thank God someone finally has fixed my printing problems!

---

### Post by JHutch737 on 2008-04-27
It looks like I'm a couple years later to the party than everyone else in this thread, but figured it was worth mentioning this guide still works great.

I just installed my Dell Photo Printer 720 in 8.04 using this tutorial in about 5 minutes.  This ended a couple weeks of frustration.

Thanks!

---

### Post by UbuNewGuy on 2008-05-06
Hi everyone,
I am keen to get this printer going however i seem to be stuck at the second step where you use the tail command and get the following error:

UbuNewGuy@comp:/home/download$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
bash: install.tar.gz: Permission denied

Does anyone know whats going wrong? I am using Ubuntu 8.0.4

---

### Post by JoePits on 2008-06-19
> **ironblade said:**
> Please note you need to install libstdc++5 for the driver to actually DO stuff:
```
sudo aptitude install libstdc++5
```

Cheers!

THANKS
this is what made it work for me (first page tutorial + this)

---

### Post by haplo_dk on 2008-07-15
> **UbuNewGuy said:**
> Hi everyone,
I am keen to get this printer going however i seem to be stuck at the second step where you use the tail command and get the following error:

UbuNewGuy@comp:/home/download$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
bash: install.tar.gz: Permission denied

Does anyone know whats going wrong? I am using Ubuntu 8.0.4

I have the excact same problem, and after hours of searching for a solution, you are the first one I find to have the same problem - did you find a solution ? (hoping).

Thanks in advance for any help from anyone :)

---

### Post by xwipeoutx on 2008-07-15
> **haplo_dk said:**
> I have the excact same problem, and after hours of searching for a solution, you are the first one I find to have the same problem - did you find a solution ? (hoping).

Thanks in advance for any help from anyone :)

Just make sure you're the owner and have write access to the directory you're currently in. You may have to sudo these commands if you're not the current owner

```

[sudo] chown username:username <directoryname>
[sudo] chmod 775 <directoryname>

```

you can try doing a touch before running the tail command, to see if you have write access to the directory
```

touch install.tar.gz

```

---

### Post by wouterd on 2008-08-04
EDIT: It seems this was already suggested earlier in this thread, but hey.. it works! :D

If your Dell Photo Printer 720 won't print after you installed the driver, try installing this library: libstdc++5.

```
$ sudo apt-get install libstdc++5
```

Then reopen the printer administration tool (System > Administration > Printers) and reselect the driver.

I don't think this will let you print the Test Page from the tool, but printing from other apps works from now on. Enjoy!

---

### Post by dahamsta on 2008-10-08
Just a hat tip to the OP, got this printer installed on Fedora with their advice, and a little help from [these guys]("http://fedoraforum.org/forum/showthread.php?t=197334"). ;)

adam

---

### Post by azbobc on 2008-10-10
The only part out of this I've been able to do is go to the site to download the driver. When I attempt to unTAR it here's what I get....

At terminal prompt I type: 
**tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz**
then press enter

Here's what follows:
[B]tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors[/B]

It would be different if there wasn't a step by step how to in front of me but this is frustrating when others have done the work and are showing me how to do it....

---

### Post by dahamsta on 2008-10-10
tar can't find the file you're trying to unpack. Is it in the directory you're currentlly in? Use **ls** to find out.

---

### Post by azbobc on 2008-10-10
*lol* tar can't find or perform the function because the code is a tad off.
Should be -zxvf, not -xvzf.

---

### Post by dahamsta on 2008-10-10
The order of the flags is not a factor. Try it yourself.

---

### Post by azbobc on 2008-10-10
> **dahamsta said:**
> The order of the flags is not a factor. Try it yourself.
I did, as posted earlier, and it would not unzip. I tried several times without success. Someone suggested I do this:
 
[I]To unzip the zipped file, this is done differently depending on the file extension. For files ending in .tar.gz, use: **tar -zxvf <filename>**
(replacing <filename> with the name of the file).[/I]

So I tried it and the file unzipped. 
Right now I'm stuck at the aptitude section because my son 'borrowed' my Ubuntu CD. As soon as he gets off work I'll have to ask him to bring it by so I can finish this up.... hopefully.[-o<
Thanks for the help thus far.

---

### Post by jal301 on 2009-07-18
+1

Thanks to all who had input on this - FINALLY I got something to work on my machine!

> **bydlo23 said:**
> This is what I was missing. Thank you!

---

### Post by JRoCc on 2009-08-27
will the Z600 work for the Dell AIO 920 as well or only the 720.

---

### Post by KIAaze on 2009-09-16
Any instructions for 64bit? :(
I'm getting this when running alien:
```
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1

```

edit: Found it: [http://ubuntuforums.org/showthread.php?t=616097](http://ubuntuforums.org/showthread.php?t=616097)
They really should stop rebranding printers. It makes things harder. :/
Lexmark Z600. I shall engrave that into my printer some day...

---

### Post by Neosano on 2009-11-07
Doesn't work in Karmic (9.10)
Or something went wrong. Btw I'm using KDE.

---

### Post by socngill on 2009-11-14
Same here. Installing on Kubuntu 9.10 and when I try to install the cups deb file I get an error message stating:

Error: Dependency is not satisfiable: libstdc++5 (>=1.3.3.4-1)

Any ideas how to fix this? I've tried installing the above dependency through the terminal but it isn't having it.

Edit - got it to work. It seemed to create two deb files for cups. Using the 1.0-1 worked.

---

### Post by sqrooup on 2009-11-25
> **seoras said:**
> 
go to ***_/usr/share/cups/model_*** where you'll see a file called Lexmark-Z600-lxz600cj-cups.ppd.gz Extract this archive to Desktop or home folder it will extract a file called X~=@l9q5 so just give it a .PPD extension (X~=@l9q5.ppd) 

I am using Karmic, and the highlighted folder above seems to be missing! where else can I get this file?

---

### Post by jbrid on 2009-12-19
I had this working in Jaunty and now I cannot get it to work in Karmic. Anyone else seen this...

```

$ sudo dpkg -i z600cups_1.0-2_i386.deb
Selecting previously deselected package z600cups.
(Reading database ... 79574 files and directories currently installed.)
Unpacking z600cups (from z600cups_1.0-2_i386.deb) ...
dpkg: dependency problems prevent configuration of z600cups:
 z600cups depends on libcupsys2 (>= 1.2.3); however:
  Package libcupsys2 is not installed.
dpkg: error processing z600cups (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 z600cups
$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  z600cups: Depends: libcupsys2 (>= 1.2.3)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
$ dpkg -l | grep z600
iU  z600cups                             1.0-2                                                  CUPS printer driver for Lexmark Z600 printer
ii  z600llpddk                           2.0-2                                                  A printer driver development kit for Lexmark

```
As you can see the driver (z600cups) needs libcupsys2 but it won't let me install libcupsys2 for some reason. 

I have CUPS version 1.4.1 and Ubuntu 9.10.

---

### Post by tbogue on 2010-01-17
I just got this working on 9.10.  I encountered two problems with the initial instructions.

The first (as socngill mentioned) is that libstdc++5 isn't installable, but it can be found at
[http://ftp.egr.msu.edu/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb]("http://ftp.egr.msu.edu/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb")

and installed via the command

*sudo dpkg -i /tmp/libstdc++5_3.3.6-18_i386.deb*

Executing ./z600 still produced no output, even after mounting the usbfs (I'm not sure that mounting the usbfs is nessesary, but I did it anyway)

I installed the new printer specifying the driver by choosing ``Provide a PPD file'' and selecting
/usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd

But the printer showed up with an exclamation mark over its icon and wouldn't print.  Looking at the error message and a bit of searching suggested the following commands to fix any permission problems.

[I]sudo chown -R root:root /usr/lib/cups
sudo chmod -R 755 /usr/lib/cups
[/I]
I cannot remember if I restarted cups at this point, but my printer now works (and doesn't have an exclamation mark on its icon).

---

### Post by DarkFienix on 2010-01-24
Hi,

Has anyone found a guide, or can write one, as to how to install the Lexmark Z615/Dell 720 drivers for Ubuntu 9.10 64-bit ?

The instructions I've found via google and these forums, relate to 32-bit.

Many thanks.

---

### Post by KIAaze on 2010-01-24
[edit]
.deb package for the Lexmark Z600 driver! (seems to be for all architectures):
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)
[/edit]
============
Here you go:
[Ubuntu 7.10 64 bit Lexmark Z645 Install](http://ubuntuforums.org/showthread.php?t=616097) (worked for me, so Z645 probably uses the same driver as Z600, Z615, Dell Photoprinter 720)

[COLOR="Red"]**_WARNING: SECURITY ISSUE_**[/COLOR]
The howto I gave you has a security issue!
Since I'm too lazy to rephrase things, here's what I wrote to jdong a while ago and his answer:

> **jdong]Well using Alien in general to convert packages can lead to some incredibly dangerous results. I've seen some cases where /usr or / was chmodded to zero along with everything underneath leading to some very broken systems.

I'll think about how to handle this, but in general I think the staff should be more wary about letting alien-using HOWTO's through.

Thanks for the heads-up!

[QUOTE=KIAaze]Hi,

I discovered today that my / was owned by me instead of by root.
After some research, it seems this was caused by following the howto: [http://ubuntuforums.org/showthread.php?t=616097](http://ubuntuforums.org/showthread.php?t=616097)

(Running "find / -user $USER -print 2>/dev/null | grep -v $USER " showed all files extracted by the driver archive.)

Following the howto blindly leads to ownership change of /.

Instead of:
```
Convert unusable rpm packages to tgz
alien -t z600cups-1.0-1.i386.rpm
alien -t z600llpddk-2.0-1.i386.rpm

Extract the tgz's to / putting the files in their right place
sudo tar xvzf z600llpddk-2.0.tgz -C /
sudo tar xvzf z600cups-1.0.tgz -C /

```

the howto should say:
```
Convert unusable rpm packages to tgz
sudo alien -t z600cups-1.0-1.i386.rpm
sudo alien -t z600llpddk-2.0-1.i386.rpm

Extract the tgz's to / putting the files in their right place
sudo tar xvzf z600llpddk-2.0.tgz -C /
sudo tar xvzf z600cups-1.0.tgz -C /

```

This seems to fix the issue of the ownership changes.
I think it would be important to update the howto just in case.

I wasn't sure who exactly to contact, but since you wrote the post about malicious commands and are a forum admin, I thought I'd first contact you.  said:**
> 

The howto has been archived, so it's not possible to post there unfortunately.

The safest and best way, would probably be to extract the files locally (alien and tar without sudo) and then move them to the correct location manually (you only need the .ppd file as far as I know).

---

### Post by KIAaze on 2010-02-02
I created a basic .deb package for the Lexmark Z600 / Dell Photoprinter 720 printers:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

Tested successfully on Ubuntu/Kubuntu 9.10 32-bit and 64-bit.

(The "other" packages were already there, but did not work for me. I did not try the C510 .deb package from "General Setup".)

---

### Post by P.Forest on 2010-02-03
This is of no help whatsoever! It did not answer my question. Does anyone know how to install a Lexmark Z615 in **UBUNTU 9.10 KARMIC KOALA**? Apparently 9.10 is the most recent edition.

Cheers!

---

### Post by KIAaze on 2010-02-03
Have you tried this?: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

---

### Post by P.Forest on 2010-02-03
That's what I've already tried, & all I get is incompletion error messages about 'broken pipes' without any indicators.

I've tried just about every other suggestion, & I don't have the time to waste spending half a day, when there should really be 'A' solution, especially for a supposedly stabilised & supported system.

I still have my XP restore disc, AND the Lexmark driver disc. There seem to be too many problems & incompatibilities between Karmic & other things.

My printer worked in Jaunty, but that's no longer supported, & I couldn't use most of my previous media files in it.

Hmmm...

---

### Post by KIAaze on 2010-02-04
> especially for a supposedly stabilised & supported system.
The Lexmark printers are not officially supported by Canonical as far as I know. At least not the Lexmark Z600 series.

It's Lexmark and Dell's fault for not providing an easy to install and working driver! :mad:
They made one (partially working), the famous "CJLZ600LE-CUPS-1.0-1.TAR.gz" and that's all.
Now it's incompatible with most modern distros and we have to figure out how to get it working.

What printer exactly do you have?
I have the Dell Photoprinter 720 (rebranded Lexmark Z6XX) and the instruction on the wiki worked for me.

Since the printer worked for you in Jaunty, there must be a way to get it working again, even if it might be complicated.
How did you get the printer working in Jaunty?

Also, could you please post the "broken pipes" message you spoke off?

As well as the contents of:
/var/log/cups/access_log
/var/log/cups/error_log

I found this about broken pipes in CUPS: [http://forums.linux-foundation.org/read.php?19,3825](http://forums.linux-foundation.org/read.php?19,3825)
For me the device URI in the printer properties window is "usb://Dell/Photo%20Printer%20720".
Maybe you should try to change that.

---

### Post by P.Forest on 2010-02-07
[FONT=Microsoft Sans Serif]My printer is a lexmark Z615.

I still have the CUPS tar.gz from when I used 9.04, & used the procedure that worked then, but didn't work in 9.10, which does seem rather odd. I also tried the other 5 or 6 suggestions I found on the grid.

Alas, I no longer have the 'broken pipe' report, so I can't send it to you. Tragically, I had to change back to XP to use my printer! Could I install it in WINE?

I'm not a programmer, but all of this has led me to start to learn UNIX/Linux. I've also downloaded an Ubuntu handbook, which should prove to be invaluable.

Nonetheless, I shall follow the Buddha's instruction that, 'All phenomena are temporary: work towards liberation with diligence' - or, paraphrased - ' All commercial software is short-lived: persevere towards liberation in freeware!'

I notice you use Kubuntu. Is it 'gooder'? Apparently, Linus Torvalds prefers it (?). I'll download it, on principle.

Many thanks KIAaze, may the penguins be with you!
[/FONT]

---

### Post by KIAaze on 2010-02-07
> **P.Forest said:**
> I still have the CUPS tar.gz from when I used 9.04, & used the procedure that worked then, but didn't work in 9.10,

And what procedure was it?
> 
Alas, I no longer have the 'broken pipe' report, so I can't send it to you. Tragically, I had to change back to XP to use my printer!

Why not install XP and Ubuntu side-by-side?
If you have enough disk space, that's the best thing to do as a beginner.
That way, if you have problems with Ubuntu and no time to solve them, you can use Windows temporarily.

Here's a dual-boot tutorial: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you need help with this, create a new thread. ;)

> 
Could I install it in WINE?

I thought about that too, but I didn't try it.
It would be strange if it worked, but who knows?
Let me know the results if you try it. :)

> 
I'm not a programmer, but all of this has led me to start to learn UNIX/Linux. I've also downloaded an Ubuntu handbook, which should prove to be invaluable.

Nonetheless, I shall follow the Buddha's instruction that, 'All phenomena are temporary: work towards liberation with diligence' - or, paraphrased - ' All commercial software is short-lived: persevere towards liberation in freeware!'

[No, it's not "freeware"! It's "Free Software", which is very different.]("http://www.fsf.org/licensing/essays/words-to-avoid.html#Freeware")
"freeware" just means "gratis software", while "Free Software" means "Software that gives you [freedom]("http://www.gnu.org/philosophy/free-sw.html")".
Alternative names are: Libre Software, Free Open-Source Software (FOSS), Free/Libre Open Source Software (FLOSS)

> 
I notice you use Kubuntu. Is it 'gooder'? Apparently, Linus Torvalds prefers it (?). I'll download it, on principle.

No, I wouldn't say it's better. It's different.
Actually, you might have more problems with Kubuntu than Ubuntu.
Not because KDE is worse than Gnome, but because it hasn't been implemented very well in Kubuntu. Other KDE distros like OpenSUSE seem to work better.
Just try it as a Live-CD or install it on a free partition.

You can even try it out under Ubuntu directly by installing "kubuntu-desktop" and selecting KDE as environment before logging in.
```
sudo apt-get install kubuntu-desktop
```

> 
Many thanks KIAaze, may the penguins be with you!

And with you too. :)

---

### Post by P.Forest on 2010-02-08
Apologies for my syntactic error: I did mean 'free software'/'FOSS'.

Before I go for the dual boot, I'll try 'nLite 1.4.9.1' to strip the 'especially unwanted' components from XP, then clean with 'CCleaner' from [http://www.piriform.com/](http://www.piriform.com/). I ran CCleaner before, & using its 'wipe free space' option liberated **6GB** from my laptop's 53 GB c-drive - I recommend it (& their other progs) to Windows users - & the nice folks at Piriform appreciate a small donation.

(I'll try to find the Z600 installation procedure & send a link.)

---

### Post by P.Forest on 2010-02-08
Hi KIAaze, here's the install procedure (I keep anything useful on an XHD, OR, I always intended to return to The FOSS):

           **'Setup Lexmark Z600 and X series printer on Ubuntu**

                                               If you have one of the Lexmark Z601, Z602,  Z604. Z605, Z615 or other Z600-series printers, this how-to will show  you how to install it on your Linux system.
 The Lexmark X1270 on Xandros 4 with the same Red Hat driver and  instructions works also. The X-Series of printers are All-In-One  printers, and these instructions work only for the printer, not the  copier and scanner. *(with thanks to JD McLeod)*
 For rpm-based distributions like Redhat, Suse and Mandrake, you can [download rpms from the Lexmark  site]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&os_group=Redhat&target=").
 If you run a debian-based distro, like Knoppix or Ubuntu, read on. 

[LIST=1]
[*]download [CJLZ600LE-CUPS-1.0-1.TAR.gz]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&os_group=Redhat&target=")  from Lexmark.com - it is the CUPS driver for RedHat 9.0
[*]Untar and unzip this file using
$ tar -zxvf CJLZ600LE-CUPS-1.0-1.TAR.gz
[*]You will end up with a file called
z600cups-1.0-1.gz.sh
[*]Extract the .rpm part of this file using
sh z600cups-1.0-1.gz.sh -target temp_lex
this will create a sub-directory called "temp_lex" under the current  directory, and put a whole lot of files in it.  Ignore any errors you  might get - if the two .rpm files are in temp_lex you are fine.
[*]In the newly created directory temp_lex you will find, amongst  others, the files:
z600cups-1.0-1.i386.rpm, and
z600llpddk-2.0-1.i386.rpm
[*]To install to a debian system (or Ubuntu or Knoppix) you need to  convert these two files to the .deb equivalent.  The program to use is  called "alien" and you run it as follows:
$ alien z600cups-1.0-1.i386.rpm $ alien z600llpddk-2.0-1.i386.rpm 
[*]You will now find the dpkg packages:
z600cups-1.0-1.i386.deb
z600llpddk-2.0-1.i386.deb
[*]Now install the driver with:
dpkg -i z600cups-1.0-1.i386.deb
dpkg  -i z600llpddk-2.0-1.i386.deb
[*]Now use CUPS or the Printer configuration tool in Ubuntu to add the  printer
[/LIST]
 


© 2005 Honey Badger IT Services'

---

### Post by P.Forest on 2010-02-13
I'm out, can't be bothered with this any more.

The driver DOES exist, but none of the methods seem to work.

Clear instruction would help though, like where the commands should be entered, because they sure don't work in terminal.

I'll give LinuxMint8 Helena a try. I WANT AN OS THAT WORKS; ONE THAT GIVES ME FREEDOM! Ubuntu only seems to create MORE work & bother than anything Windoze ever did!

At least LinuxMint8 has a user guide, rather than just a confusing mass of opinions & conflicting instructions.
It also looks better & the reviews are good.

But I don't expect anything great, given that it seems to be basically the same as Ubuntu.

Best wishes & farewell.

---

### Post by P.Forest on 2010-02-13
Final point: don't bother with Mint; it's even less user-friendly than Ubuntu ('Ubuntu' even comes up as a spelling error in this dialogue box!), & the 'Official User Guide' spends more time extolling its own dubious virtues.

I'd very much like to be FOSS-based, & I have strong ethical principles, but a system on which I can neither install my printer nor read my documents, nor install fonts (I have approximantely 1750 of them!) let alone navigate with the ease I can in XP is not much use to me.

Yes, I do like to be able to install hardware & manage it without having to open a terminal & spend hours entering instructions that aren't recognised.

Yes, I don't want to have to reinstall my mobile broadband connection every time I log on.

So XP may be a little slower, but it does what I want, & it is easy to manage & keep secure. Actually, both Ubuntu & Mint are not much faster, & both are still full of bugs. Even Open Office works better on XP.

I sincerely hope that someone will design a really good OS, but when there are 200-ish OSOSs out there, it's not going to happen. Why don't all the Linux-Debian-GNU-Gnomes get together & work towards a common goal? Then something good may happen. Using 'the enemy's' strategies has great value.

All I want is a straightforward OS that I can do my work on.

I'll keep looking; maybe BSD or Haiku will work, maybe not, but an OS that either alienates people or can only work in conjunction with the grid is not likely to become popular.

Personally, I think it's a great pity that UNIX didn't 'go for it' in the first place.

I wish you all well, but 'Linux' just doesn't work for me.

---

### Post by KIAaze on 2010-02-14
Again, please post the contents of "/var/log/cups/access_log" and "/var/log/cups/error_log" after trying to use the printer.

It's probably just a permission problem on some files.

Here is a list of the installed files and the permissions they should have:
```
-rw-r--r-- 1 root root    1508 2010-02-02 13:01 /usr/include/lexmark/alignmentdata.h
-rw-r--r-- 1 root root    4124 2010-02-02 13:01 /usr/include/lexmark/cartridgemanager.h
-rw-r--r-- 1 root root    1772 2010-02-02 13:01 /usr/include/lexmark/cartridgeuserinterface.h
-rw-r--r-- 1 root root    1336 2010-02-02 13:01 /usr/include/lexmark/cleaningdata.h
-rw-r--r-- 1 root root    3441 2010-02-02 13:01 /usr/include/lexmark/clock.h
-rw-r--r-- 1 root root    5594 2010-02-02 13:01 /usr/include/lexmark/errorcommunicator.h
-rw-r--r-- 1 root root    1944 2010-02-02 13:01 /usr/include/lexmark/linuxinkjetprinter.h
-rw-r--r-- 1 root root    3934 2010-02-02 13:01 /usr/include/lexmark/mediamanager.h
-rw-r--r-- 1 root root    6430 2010-02-02 13:01 /usr/include/lexmark/portmonitor.h
-rw-r--r-- 1 root root    3070 2010-02-02 13:01 /usr/include/lexmark/printerdevice.h
-rw-r--r-- 1 root root    3536 2010-02-02 13:01 /usr/include/lexmark/printjobmanager.h
-rwxr-xr-x 1 root root  119011 2010-02-02 13:01 /usr/lib/cups/backend/z600
-rwxr-xr-x 1 root root   97862 2010-02-02 13:01 /usr/lib/cups/filter/rastertoz600
-rw-r--r-- 1 root root  100064 2010-02-02 13:01 /usr/lib/liblexprinter.a
-rw-r--r-- 1 root root     741 2010-02-02 13:01 /usr/lib/liblexprinter.la
-rw-r--r-- 1 root root   76780 2010-02-02 13:01 /usr/lib/liblexprinter.so.0.0.0
-rw-r--r-- 1 root root   31578 2010-02-02 13:01 /usr/lib/liblexprintjob.a
-rw-r--r-- 1 root root     748 2010-02-02 13:01 /usr/lib/liblexprintjob.la
-rw-r--r-- 1 root root   25579 2010-02-02 13:01 /usr/lib/liblexprintjob.so.0.0.0
-rw-r--r-- 1 root root 2254574 2010-02-02 13:01 /usr/lib/liblexz600core.a
-rw-r--r-- 1 root root     748 2010-02-02 13:01 /usr/lib/liblexz600core.la
-rw-r--r-- 1 root root 1381164 2010-02-02 13:01 /usr/lib/liblexz600core.so.0.0.0
-rw-r--r-- 1 root root 1440768 2010-02-02 13:01 /usr/local/z600llpddk/utility/bnsi1.lut
-rw-r--r-- 1 root root 1440768 2010-02-02 13:01 /usr/local/z600llpddk/utility/bnsi2.lut
-rw-r--r-- 1 root root 1440768 2010-02-02 13:01 /usr/local/z600llpddk/utility/bnsi3.lut
-rw-r--r-- 1 root root 1080498 2010-02-02 13:01 /usr/local/z600llpddk/utility/lxbcalgn.out
-rw-r--r-- 1 root root  654780 2010-02-02 13:01 /usr/local/z600llpddk/utility/lxbccln.out
-rw-r--r-- 1 root root   13086 2010-02-02 13:01 /usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd
-rw-r--r-- 1 root root     172 2010-02-02 15:11 /usr/share/doc/liblexz600core0/changelog.Debian.gz
-rw-r--r-- 1 root root    5421 2010-02-02 14:51 /usr/share/doc/liblexz600core0/copyright

```

Here is some help on understanding and changing file permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

For a quick start, you can just run the following 2 commmands:
```

sudo chmod +x /usr/lib/cups/backend/z600
sudo chmod +x /usr/lib/cups/filter/rastertoz600

```
and see if it works afterwards.

Additionnally, I found this in French: [http://doc.ubuntu-fr.org/imprimante_lexmark_z600](http://doc.ubuntu-fr.org/imprimante_lexmark_z600)

It suggests that the z600cups package from June 2008 has a bug, which can be solved by creating a symbolic link named "/etc/init.d/cups" to "/etc/init.d/cupsys":
```
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
```

So try that too.

[B]But first of all post the contents of "/var/log/cups/access_log" and "/var/log/cups/error_log" after trying to use the printer.
[/B]

---

### Post by P.Forest on 2010-02-24
Cheers KIAaze, but too late: I've had enough of user unfriendly systems.

The fault is with the Linux/Ubuntu development teams who have neglected to come up with straightforward procedures that enable users to install hardware. It ***SHOULD*** be possible to install either with a driver disc, or with an appropriate CUPS.

Why dual-boot if Linux/Ubuntu is ***SO*** great? Why use WINE when Windows actually works? Either way, antivirus is still necessary. And I do not believe the claim that Linux is virus-proof: it ain't UNIX.

In spite of feeling quite alienated by the Linux/Ubuntu system, I will say one thing: the Ubuntu forums have been a source of ideas, even if they didn't work. I can't say the same about LinuxMint.

There's a huge difference between ideology and practicality, and it was the impracticality of Linux/Ubuntu that turned me back towards Windows, while I look for a system I can work with.

Best wishes.

P

---

### Post by KIAaze on 2010-02-24
> **P.Forest said:**
> Cheers KIAaze, but too late: I've had enough of user unfriendly systems.

The fault is with the Linux/Ubuntu development teams who have neglected to come up with straightforward procedures that enable users to install hardware. It ***SHOULD*** be possible to install either with a driver disc, or with an appropriate CUPS.
Then don't tell it to me. Tell it to the Ubuntu developers.
GNU/Linux is about freedom. And you are free not to use it.

I would like to be able to help you get the printer working, but I need more information to do so.

It would be easier if you can find a local person to help you.
Have you checked if there are any Ubuntu LoCo or LUGs near you?:
[https://wiki.ubuntu.com/LoCoTeams](https://wiki.ubuntu.com/LoCoTeams)
[http://www.linux.org/groups/](http://www.linux.org/groups/)

Otherwise, you could also try other distros like OpenSUSE.
I noticed that most Lexmark drivers come as .rpm packages instead of .deb.
So they might actually work better on RPM based distros like OpenSUSE, Fedora, Mandriva or CentOS:
[http://en.wikipedia.org/wiki/List_of_Linux_distributions#RPM-based](http://en.wikipedia.org/wiki/List_of_Linux_distributions#RPM-based)

> Why dual-boot if Linux/Ubuntu is ***SO*** great?
Because if you have problems with Ubuntu like now, you can use Windows instead.
I actually still dual-boot and print from Windows because my printer seems to have problems with printing more than one page when he can't pull in the next sheet of paper.

And it isn't "SO" great yet, but it is already pretty great and I already prefer it to Windows.
Not everything works for me too, but nothing bothers me enough to switch back to Windows.
I have access to lots of Free software, a good programming and working environment, multiple desktops, copy-paste history, useful desktop effects, internet and multimedia work, etc.

> Why use WINE when Windows actually works?
To avoid rebooting (or installing Windows) when Ubuntu is your main operating system.
Personally, I still boot into Windows to play some games even if some of them work under GNU/Linux via wine.

>  Either way, antivirus is still necessary. And I do not believe the claim that Linux is virus-proof: it ain't UNIX.
It is not virus-proof. But it certainly is more virus-proof than Windows so far.
Whatever the OS, the security ultimately depends on the user.
[Ubuntu security]("http://ubuntuforums.org/showthread.php?t=510812")

> 
In spite of feeling quite alienated by the Linux/Ubuntu system, I will say one thing: the Ubuntu forums have been a source of ideas, even if they didn't work. I can't say the same about LinuxMint.

There's a huge difference between ideology and practicality, and it was the impracticality of Linux/Ubuntu that turned me back towards Windows, while I look for a system I can work with.

Best wishes.

P

Come back whenever you want. :)

I had a Debian-Windows dual-boot system for quite a while, until the Beryl/Compiz 3D desktop and open-source philosophy hooked me into GNU/Linux completely.
Keeping a 5 GB partition to try out GNU/Linux isn't a big sacrifice IMO. (or you could install it on a USB stick, use Wubi, etc)

P.S.: This thread is to help get the Lexmark printers to work under Ubuntu. If you want to discuss the reasons to switch to Ubuntu or why you quit Ubuntu, you may post here:
[http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)

---

### Post by ectospasm on 2010-02-24
I did a quick skim of the first and last pages of this thread, and I don't see any instructions on getting this working in x86_64 OSes.  I had trouble last time I tried to install this Lexmark X1150, because the binaries included only seemed to support i386.  This won't be too big of an issue when I put together my new computer this weekend.  I'll install a 32bit OS.  Problems like this are still too frequent for my liking in Linux, even after all these years and countless hours trying to get this stuff working.

I'd consider myself a Linux geek, but I'm tired of futzing for the sake of futzing.  I disagree with P.Forest, I think these instructions work great (if you disregard my 64bit troubles above).  I've gotten them to work no problem in a previous 32bit install.  Linux is still far away from not needing the command line, so you're asking too much if you want to avoid it completely.  This is just my personal opinion, take it for what it's worth.

---

### Post by KIAaze on 2010-02-24
For 64-bit: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

Let me know how it works.

---

### Post by Questor_ix on 2010-05-17
> **tbogue said:**
> I just got this working on 9.10.  I encountered two problems with the initial instructions.

The first (as socngill mentioned) is that libstdc++5 isn't installable, but it can be found at
[http://ftp.egr.msu.edu/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb](http://ftp.egr.msu.edu/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb)

and installed via the command

*sudo dpkg -i /tmp/libstdc++5_3.3.6-18_i386.deb*

Executing ./z600 still produced no output, even after mounting the usbfs (I'm not sure that mounting the usbfs is nessesary, but I did it anyway)

I installed the new printer specifying the driver by choosing ``Provide a PPD file'' and selecting
/usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd

But the printer showed up with an exclamation mark over its icon and wouldn't print.  Looking at the error message and a bit of searching suggested the following commands to fix any permission problems.

[I]sudo chown -R root:root /usr/lib/cups
sudo chmod -R 755 /usr/lib/cups
[/I]
I cannot remember if I restarted cups at this point, but my printer now works (and doesn't have an exclamation mark on its icon).

Amazing, this thread setup my printer.  I was having problems with:

> Job stopped due to filter errors

But following the quoted steps above resolved my problems.  

Thanks, Ubuntu Forums!

---

### Post by justine777w on 2010-05-28
I have tried to follow these instructions several times and no results. I keep getting error messages and I am not sure if I downloaded the right redhat or not. I have a Dell 720 Photo Printer. I have Ubuntu 9.10. I am not sure what I am doing wrong. Can someone please help me? Also, would it be possible for someone to post, in detail, the steps needed to make this printer work? Thanks.

---

### Post by migel_wimtore on 2010-08-16
Perseverance. No one method posted here got it working completetly for me, but, it appears, a combination did.

Can now print perfectly with Dell 720, Ubuntu 10.4. 

Thanks so much everybody.

---

### Post by bunlacken on 2010-12-19
This site for ubuntu Z600 drivers, works like a charm. Debi installer.:D
https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.4.deb[/url]

---

