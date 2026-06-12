---
title: "Cannot configure Canon MX410 scanner"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by EthanD on 2012-10-10
Hello,

I am a Ubuntu and Linux rookie. I am currently running Ubuntu 12.04LTS and having a heck of a time to get a scanner on the OS. It is a Canon MX410 multifunction. I got the printer side to work no problem. The scanner on the other hand is being a royal pain. I have all the drivers for the printer and scanner but I just need some guidance on this whole issue. I mean completely start from scratch. I would also like to take advantage of the wifi that the Canon has. I appricate any and all advice and/or help. Thank you in advance

Ethan

---

### Post by David D. on 2012-10-10
You don't say whether or not you have installed any scanning software.  I use Simple Scan for most short jobs with my printer/scanner.  Simple Scan is available in the repositories.  Open Ubuntu Software Center, do a search on "scan" and then choose Simple Scan for install (or one of the other scanning software packages of your choice).

Once installed, you can open the Dash, do a search on "scan" and your scanning software should show up.  Open the program and scan a document.

If you already have scanning software installed, please describe any problems you are encountering.

---

### Post by twipley on 2012-10-10
Indeed, [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html) reports the printer being untested, which means the are needing help for the scanner to be compatible out-of-the-box through Simple Scan.

Oftentimes what is needed is USB sniffing through Windows-use, although to know you would have to contact project heads.

[http://www.sane-project.org/contrib.html](http://www.sane-project.org/contrib.html)

You can thank Canon for providing adequate Linux support. Up to date, I have had better luck using HP machines.

Good luck, champion! ;)

---

### Post by jim_deadlock on 2012-10-10
I remember the headaches I had originally trying to set up my all-in-one for wireless scanning. The key to it is to go through the settings on the device itself and connect it to the wireless network - note this is nothing to do with your computer or Ubuntu, I'm talking about the controls on your printer/scanner.

Once your device is connected to the network, install xsane via the Software Centre, then run Gimp and go to File... Create... Xsane... Device Dialog. Cross your fingers and it should find your scanner. If it doesn't work, first make sure your firewall isn't blocking it (if you've installed the firewall that is). If still no joy we'll have to think of something else.

---

### Post by EthanD on 2012-10-10
Thank you for the replies!!

I do have simple scan and xsane. Both will not even recognize the device.  I did also see that it was "un-tested" but wasn't too sure how often it gets updated. I wasn't too sure if a person would have to do it through Root or if there was something I was missing. If I have to go through Root the all-in-one will go back to the store, as I am not experienced enough to even dive in that side of the house.  So at this time am I S.O.L? I figured that if I got all the drivers for it (that i found on the forums) that I would be able to use my scanner. The printer side was a breeze. Ubuntu even picked up the FAX side of the device also but not the scanner. I am very thankful everyone is giving some input.. :)

Ethan

---

### Post by jim_deadlock on 2012-10-10
I'm confused as to whether you're trying to get the scanner working with a USB cable or wirelessly. Can you scan with a cable and/or print wirelessly now?

---

### Post by sandyd on 2012-10-10
**Moved to ABS**

---

### Post by EthanD on 2012-10-11
jim_deadlock,

I cannot get it to scan with usb or wireless.

---

### Post by pdc on 2012-10-12
Ethan:

you need to install [COLOR="Red"]**ScanGearMP**[/COLOR] that [COLOR="Red"]**Canon**[/COLOR] provide: it works well

go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100330601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100330601.html)

and download [COLOR="Red"]MX410 series ScanGear MP Ver. 1.70 for Linux (debian Packagearchive)[/COLOR]

......it comes down as a compressed debian package..

> [COLOR="SeaGreen"]scangearmp-mx410series-1.70-1-deb.tar.gz[/COLOR]

........select "*[COLOR="Blue"]save file[/COLOR]*" as your system downloads it..it should save it to your Downloads directory??.......

I can suggest the terminal commands to now install [COLOR="Red"]scangearmp
[/COLOR]

> cd Downloads

> tar -zxvf scangearmp-mx410series-1.70-1-deb.tar.gz

> cd scangearmp-mx410series-1.70-1-deb

> ./install.sh

............once installed issue the command

> scangearmp

and the programme opens......

______________________________________________

good eh?

______________________________________________--

......instead of typing the above into a terminal each time, you can automate the process by creating a launcher.....that launches scangear

from this thread

[http://ubuntuforums.org/showthread.p...ighlight=canon](http://ubuntuforums.org/showthread.p...ighlight=canon)

see post # 85

and this thread

[http://linuxhelp.host.org/index.php?...create-desktop](http://linuxhelp.host.org/index.php?...create-desktop)

---

### Post by EthanD on 2012-10-12
pdc

this is what I got when i got to ./install.sh. What does this mean?

"An error occurred. The package management system cannot be identified."

---

### Post by pdc on 2012-10-12
I am guessing you have 64bit Ubuntu, even though you kept that to yourself..................if so....................

you need to edit the install.sh script

......to do that, I would 

> cd Downloads/scangearmp-mx410series-1.70-1-deb

> sudo gedit install.sh

look for the section

> ## rpm and deb are error, or rpm and deb are no error, is error ##
        if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
               printf "$L_INST_COM_01_02"
               return $C_ERR_CODE
        else
               if test $c_system_rpm -eq 0; then
                       C_system="rpm"
               else

                        C_system="deb"
               fi
        fi

***[COLOR="Blue"]you just add the two lines[/COLOR]***

> [COLOR="Red"]C_arch32="i386"
       C_arch64="x86_64"[/COLOR]


.......as indicated............


> ## rpm and deb are error, or rpm and deb are no error, is error ##
        if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
               printf "$L_INST_COM_01_02"
               return $C_ERR_CODE
        else
               if test $c_system_rpm -eq 0; then
                       C_system="rpm"
                        [COLOR="Red"]C_arch32="i386"
			C_arch64="x86_64"[/COLOR]
               else

                        C_system="deb"
                        [COLOR="Red"]C_arch32="i386"
			C_arch64="x86_64"[/COLOR]

               fi
        fi

......as you have changed the file [COLOR="Red"]install.sh[/COLOR] then you just save it and close it and run the commands again from the terminal that I gave you in the first post.....we hope it all goes well this time......

I have put the additions in red, just so they stand out .......

.......what I quote is in the more recent version of scangear; 1.8 which I installed with a newer Canon printer (by chance)

---

### Post by EthanD on 2012-10-12
pdc,


This is the only one I had to change. 
C_arch64= "amd64"

Made the changes like you recommended but after the change I got this error:
An error occurred. The package management system cannot be identified.
./install.sh: line 337: [: =: unary operator expected

Don't know what that means, I don't know if it is me or what.....

---

### Post by pdc on 2012-10-12
...........so did you do what I suggested?

---

### Post by pdc on 2012-10-12
I downloaded the mx410.tar.gz file you have;

using a terminal, I used the text editor nano, as it can count the line that you are on

when I do that, and count the **[COLOR="Red"]UNEDITED[/COLOR]** file, I find line 337 is highlighted in red ..[COLOR="Blue"]*I only do that to give us an approximate estimate where your system is reading an error*[/COLOR];

> ######################################################
#### _ _ E x e c u t e _ I n s t a l l . s h  _ _ ####
######################################################
if [ ${0##*/} = $C_install_script_fname ]; then

        #################################################################
        #### _ _ B o t h _ P a c k a g e _ C o m m o n _ F l o w _ _ ####
        #################################################################

        C_argment=$1

        ########################
        ## Show the copyright ##
        ########################
        C_FUNC_get_system
        [COLOR="Red"]if [ $C_system = "rpm" ]; then[/COLOR]


so if you 

> cd Downloads/scangearmp-mx410series-1.70-1-deb 

and 

> nano install.sh

......the command (*without the sudo*) [COLOR="SeaGreen"]allows you to look; before changing anything[/COLOR]

 your system should open nano in the terminal, and using the Control C keys, tell you which line you are on; 

........you can copy and paste that line back here if you wish ..

....*I think my hunch is* you would be best to paste exactly what I said to do; as that is what Canon have done in their 1.8 version; and it seems to work...............

---

### Post by EthanD on 2012-10-12
pdc,

yes, i did as you suggested, last time as well as this time lol. 

Here is what line 337 and the following 3 lines are saying:
  
if [ $C_system = "rpm" ]; then
                ##  Check permission by root ##
                if test `id -un` != "root"; then
                        su -c "$0 $C_argment"

---

### Post by pdc on 2012-10-12
sometimes the bleeding obvious doesn't occur to me ..

........each Canon package......needs 

1) a common package 

..and ...

2) a specific package for the device

so looking inside the packages directory; in the scangearmx410 directory:

are what we need:

so the commands should be ......

> cd Downloads/scangearmp-mx410series-1.70-1-deb/packages

......that should get you in the correct directory;

if you type 

> ls     .....*that should list the contents of that director*y.....if all is good......

> [COLOR="Red"]sudo dpkg -i scangearmp-common_1.70-1_amd64.de[/COLOR]b

and > [COLOR="Red"]sudo dpkg -i scangearmp-mx410series_1.70-1_amd64.deb[/COLOR]

...that should install it......


and again in a terminal

> [COLOR="Red"]scangearmp[/COLOR]

should open the programme

....to save using terminal each time........

linuxhelp.host.org/index.php?page=news&type=view&id=linux-help_2%2Fhow-to-create-desktop

this post should help you create a launcher......

......I do hope now we can get you working!

best wishes

---

### Post by EthanD on 2012-10-12
pdc,

I followed your suggestions and I got, i copied and pasted directly from my terminal and this is how it came up. any thoughts?

scangearmp-common_1.70-1_amd64.deb  scangearmp-mx410series_1.70-1_amd64.deb
scangearmp-common_1.70-1_i386.deb   scangearmp-mx410series_1.70-1_i386.deb

---

### Post by pdc on 2012-10-12
so that is the list of the packages in the packages directory:

you should then install them.......using the commands I suggested;

......or use the GUI method; identify the packages in the directory; and double-click on the common amd one first and then the specific amd one ..

with the terminal, use the commands I suggested

> sudo dpkg -i scangearmp-common_1.70-1_amd64.deb 

and then 

> sudo dpkg -i scangearmp-mx410series_1.70-1_amd64.deb

....then proceed as in the previous post..

---

### Post by EthanD on 2012-10-13
pdc,

This is what i got, 
i am about to pull my friggin hair out!! LOL

/Downloads/scangearmp-mx410series-1.70-1-deb/packages$ sudo dpkg -i scangearmp-common_1.70-1_amd64.deb 
dpkg: error processing scangearmp-common_1.70-1_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Errors were encountered while processing:
 scangearmp-common_1.70-1_amd64.deb

---

### Post by pdc on 2012-10-13
please copy and paste into a terminal

.......and copy and paste back the results

> uname -m

and > quote -a

....... your last message suggests you have a 32bit system installed?

____________________________________________________________________________

if it is 32bit you need

> sudo dpkg -i scangearmp-common_1.70-1_i386.deb .....for the common package.......

....and then ...........

> sudo dpkg -i scangearmp-mx410series_1.70-1_i386.deb

......and if that installs, 

> scangearmp .....to open the programme......

.....how are we doing?

---

### Post by EthanD on 2012-10-13
pdc,

uname -m 
i686

---

### Post by EthanD on 2012-10-13
pdc,

Ok I got it installed. I ran scangear and it came back saying that no scanners could be found. The device is plugged in and is on.  maybe i need to try it wirelessly. i will let ya know. thank you for all your help.

---

### Post by EthanD on 2012-10-13
got it to work wirelessly. thank you again!! :)

---

### Post by pdc on 2012-10-13
great! 

wasn't that easy.........

........so you have a 32bit system installed.....

.......but is it completely standard? .. the installer should just work with a 32bit system the first time around..

..... you can just type scangearmp into a terminal each time you want to scan, and I gave you the link to set up a launcher that should just need a click when set up.....

......in a week or two or three; if you ever had five minutes, go over some of the territory we went through; it all sort of adds up eventually..

---

### Post by abumaia on 2012-12-11
> **pdc said:**
> ......instead of typing the above into a terminal each time, you can automate the process by creating a launcher.....that launches scangear

from this thread

[http://ubuntuforums.org/showthread.p...ighlight=canon](http://ubuntuforums.org/showthread.p...ighlight=canon)

see post # 85

and this thread

[http://linuxhelp.host.org/index.php?...create-desktop](http://linuxhelp.host.org/index.php?...create-desktop)

Neither of those links work, you've got the ellipses in there instead of the whole link.

---

