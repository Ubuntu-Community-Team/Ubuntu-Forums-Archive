---
title: "HOWTO: Install Windows Vista Beta 2 (With Vmware without burning ISO file) On Dapper"
date: 2006-06-08
forum: Outdated Tutorials &amp; Tips
---

### Post by aktiwers on 2006-06-08
[COLOR=Indigo][B][COLOR=Red]Edit : THIS GUIDE IS PRETTY OUTDATED AND THE DOWNLOADS ARE NOT AVAILABLE ANYMORE.
HOWEVER, YOU COULD USE THE GUIDE IF YOU ALREADY HAVE THE ISO, OR AN ISO FROM ANOTHER OS.

Good Luck!
[/COLOR][/B][/COLOR][COLOR=Indigo]
Hi All !

This is my first HOWTO, so I hope it will be useful to some.

This Howto will explain how you Download [/COLOR]  [COLOR=Red](3GB+ Download!)[/COLOR][COLOR=Indigo], install and get free licensens to Windows Vista Beta 2 (that expires June 2007).

[B]THIS IS NOT FOR DUAL BOOTING! YOU WILL BE RUNNING WINDOWS VISTA TRHOUGH VMWARE (a window) ON TOP OF UBUNTU.

[/B]I have only tested this on my PC with Dapper 6.06.
I will be using some stuff from this guide made by Peturrr.
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)
Okey, lets get started :D[/COLOR]   

[COLOR=Red]1)[/COLOR][COLOR=Indigo] First we need to use some stuff from Peturrr's HOWTO:


>  First we need to install a few dependencies:

In a terminal type[/COLOR]> 
```
[LEFT][COLOR=Indigo]sudo apt-get install linux-headers-`uname -r` build-essential xinetd[/COLOR][/LEFT]
                     
```[COLOR=Indigo]
 This will install all needed dependencies (atleast I hope so :wink: )[/COLOR][COLOR=Indigo] 
This somehow didnt work for me, but I got it installed successfully anyway. So if this makes some kind of error, you could try to go on[/COLOR].

[COLOR=Red]2)[/COLOR]
[COLOR=Indigo] Again, Follow this from Peturrr's guide:

>  We are now ready to download VMWare Server.[/COLOR]> [LIST]
[*][COLOR=Indigo]Go to [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)[/COLOR]
[*][COLOR=Indigo]On the menu on the right click: Download VMWare Server[/COLOR]
[*][COLOR=Indigo]Click on the appropriate Download Now button.[/COLOR]
[*][COLOR=Indigo]Register as new user, do give a valid email adres, since you will be receiving the registration key by email.[/COLOR]
[*][COLOR=Indigo]Select the VMWare Server beta (for Linux)[/COLOR]
[*][COLOR=Indigo]Accept the EULA[/COLOR]
[*][COLOR=Indigo]Download VMware Server for Linux. (first mentioned, binary (.tar.gz) )[/COLOR][/LIST][COLOR=Indigo]The Installation[/COLOR][LIST]
[*][COLOR=Indigo]Open the downloaded file with the archive manager.[/COLOR]
[*][COLOR=Indigo]Extract it to somewhere, I will use /tmp here.[/COLOR]
[*][COLOR=Indigo] Startup the terminal and go to the extracted files 

   [/COLOR]```
[LEFT][COLOR=Indigo]cd /tmp  replace with your download directory
cd vmware-server-distrib[/COLOR][/LEFT]



















[COLOR=Indigo]
[/COLOR]
```
[*][COLOR=Indigo]Execute the installation script 

[/COLOR]          [LEFT][COLOR=Indigo]```
sudo ./vmware-install.pl
```[/COLOR][/LEFT]
[*][COLOR=Indigo]You can accept all defaults, only thing you might want to alter is the directory where the Virtual Machines are stored. I have mine set to /home/username/vmware . But offcourse, just accept the settings you want to.[/COLOR]
[*][COLOR=Indigo]You will be prompted for your key during the installation. You will find the key in your email inbox[/COLOR]
[*][COLOR=Indigo]If everything went allright, the installation will finish without any problems[/COLOR][/LIST][COLOR=Indigo]We can now test if it worked by starting the VMWare server console[/COLOR][LIST]
[*][COLOR=Indigo]Via the menu Applications => System Tools => Vmware Server Console[/COLOR]
[*][COLOR=Indigo] If everything is allright, the server console program will show up.[/COLOR]
[*][COLOR=Indigo]If it didn't, start the terminal and execute   
[/COLOR]      [LEFT][COLOR=Indigo]```
vmware
```[/COLOR][/LEFT]
[/LIST] [COLOR=Red]3)[/COLOR]  [COLOR=Indigo]Okey if thats working, lets move on to getting Vista downloaded. This is a big file([COLOR=Red]3gb +[/COLOR] )

First go here and download either 32bit or 64bit version. ( I only Tested it with 32bit).

[B]
Download Page[/B]
[http://download.windowsvista.com/preview/beta2/en/x86/download.htm?]("http://download.windowsvista.com/preview/beta2/en/x86/download.htm?www.dailytech.com")

As a lot of people want to try this "new" OS, I found that its almost impossible to get access to the downloads. So while I was there, I graped the direct links.

(the board for some reason shortens the link. If you use wget, it should be the full link address) ([COLOR=Red]Using wget will work even though microsoft says "[/COLOR][/COLOR][COLOR=Red]*We are currently experiencing a high level of demand bla bla bla*"[/COLOR])
[COLOR=Indigo] ** 32Bit Version**
[URL="http://download.windowsvista.com/dl/preview/beta2/en/x86/iso/vista_5384.4.060518-1455_winmain_beta2_x86fre_client-LB2CFRE_EN_DVD.iso"]http://download.windowsvista.com/dl/preview/beta2/en/x86/iso/vista_5384.4.060518-1455_winmain_beta2_x86fre_client-LB2CFRE_EN_DVD.iso
[/URL][/COLOR]```
[COLOR=Indigo]wget [/COLOR][COLOR=Indigo][http://download.windowsvista.com/dl/preview/beta2/en/x86/iso/vista_5384.4.060518-1455_winmain_beta2_x86fre_client-LB2CFRE_EN_DVD.iso](http://download.windowsvista.com/dl/preview/beta2/en/x86/iso/vista_5384.4.060518-1455_winmain_beta2_x86fre_client-LB2CFRE_EN_DVD.iso) [/COLOR]
``` [COLOR=Indigo] 

[B]64Bit Version
[/B][URL="http://download.windowsvista.com/dl/preview/beta2/en/x64/iso/vista_5384.4.060518-1455_winmain_beta2_x64fre_client-LB2CxFRE_EN_DVD.iso"]http://download.windowsvista.com/dl/preview/beta2/en/x64/iso/vista_5384.4.060518-1455_winmain_beta2_x64fre_client-LB2CxFRE_EN_DVD.iso
[/URL][/COLOR]```
wget [COLOR=Indigo][http://download.windowsvista.com/dl/preview/beta2/en/x64/iso/vista_5384.4.060518-1455_winmain_beta2_x64fre_client-LB2CxFRE_EN_DVD.iso](http://download.windowsvista.com/dl/preview/beta2/en/x64/iso/vista_5384.4.060518-1455_winmain_beta2_x64fre_client-LB2CxFRE_EN_DVD.iso) [/COLOR]
```[COLOR=Red]4) 
[COLOR=Black][COLOR=Indigo]Okey, this might take some time for must users.  While waiting go signup for your product Key. [B]Its Free and lasts until June 2007!
[/B][http://www.microsoft.com/windowsvista/getready/preview.mspx](http://www.microsoft.com/windowsvista/getready/preview.mspx)

Now when you got your CD-Key, save the image on your PC for later use.[/COLOR] 

[COLOR=Red]5)

[COLOR=Indigo]Now open Vmware by typing into the terminal:


[/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Indigo]```
vmware
``` [/COLOR]
[COLOR=Red]6)
[/COLOR][COLOR=Indigo] Select 'Create a new virtual machine'[/COLOR][LIST]
[*][COLOR=Indigo] => Next => Next => Select Windows Vista (Experimental)[/COLOR]
[*][COLOR=Indigo]=> Next => Enter a name and select a location for the Virtual Machine File (It contains the virtual harddisk, so it needs to be atleast 16GB)[/COLOR]
[*][COLOR=Indigo] => Next => Select Network type. I use " Brigde: Connected Directly to the physical Network". Pick what suits you best.[/COLOR]
[*][COLOR=Indigo]=> Next => Choose the size for the Virtual Disk and set other preferences[/COLOR]
[*][COLOR=Indigo] => Next => Finish[/COLOR][/LIST][COLOR=Red][COLOR=Black][COLOR=Red]7)
[COLOR=Indigo]
[/COLOR] [COLOR=Indigo]Now when its done, Clik on the tap of your [/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Indigo]virtual machine, and Pick:
"Edit Virtual Machine settings."

Click on the CD-Rom Drive and pick Use ISO.
Below that, type in the path to your ISO file from Microsoft, remember at this time it has to be done downloading.

/path/to/your/windows/download/windowsvista.iso

and hit OK.[/COLOR]   
[COLOR=Red]
[COLOR=Black][COLOR=Indigo]Hit "Power on This Vitual Machine" and follow the installation!

Remember to have your CD-Key Image ready.

And done! [/COLOR]  

[COLOR=Red]8 )[/COLOR]

[COLOR=Indigo]Now when you are logged in and see your desktop, click CTRL+ALT
 (this will take your mouse out of Vista, and back on Ubuntu)


Click on VM and pick "Intall Vmware Tools...[COLOR=Indigo]" Now inside Windows Vista, the installation will start. Install it, and it  will reboot.

This should give a good bust to the performance!

[/COLOR]Thats it, done![/COLOR]

[COLOR=Red][B][COLOR=Blue]Im afraid Im a Noob myself, so sadly I wont be at much help if anyone has any errors. But post them below anyways, maybe others knows how to fix it.

Oh yeah, sorry for any typo's!

Also Please read Paturrr's guide, its real good, and you will get the basic idea. 
Im sure I forgot something, let me know.

[COLOR=Indigo]EDIT:
Added number 8!
Some Screenshots attatched below.
[/COLOR] [/COLOR] [/B][/COLOR][/COLOR][/COLOR][COLOR=Red]
[/COLOR]

---

### Post by lucia_engel on 2006-06-09
Thanks for the guide, I'll try it out when the link works again. I want to try other distros too, now that I know you can just use iso.

Some general VMware questions:
- I have a / and /home partitions. When I allocate space for Vista in VMWare, which partition does it use? 
- How much space should I allocate for a very basic Vista install?
- Can files be shared between the virtual machine and Ubuntu?
- I'm guessing I can install softwares to Windows from CDs right? (ie. photoshop)

---

### Post by aktiwers on 2006-06-09
[quote=lucia_engel]Thanks for the guide, I'll try it out when the link works again. I want to try other distros too, now that I know you can just use iso.

Some general VMware questions:
- I have a / and /home partitions. When I allocate space for Vista in VMWare, which partition does it use? 
- How much space should I allocate for a very basic Vista install?
- Can files be shared between the virtual machine and Ubuntu?
- I'm guessing I can install softwares to Windows from CDs right? (ie. photoshop)[/quote] 
[COLOR=Indigo]Yes this should work with other distro's as well
About your VMware questions:

1) While creating the Virtual Machine, it asks you where to store it. You can pick where you like. I place mine on another Hard disc. (in my case its /media/sda1/vmware/)

2) As I say in the guide (proberbly wasnt clear enough, sorry), they reqiure 16gb as minimum.

3) Yes! I havent got this working my self, but like in my point 7 in the guide, in the [/COLOR][COLOR=Indigo] "Edit Virtual Machine settings." you can add a lot of things. Just click on the "Add" button. You can add hard discs, cdrom drives, floppys  and  more. 
I also forgot to say, if you want sound working, simply go ad it there. 
 
4) Yes, simply add the cd-rom drive as I just mentioned :)[/COLOR]

---

### Post by raffytaffy on 2006-06-09
Can using vmware cause any problems in general? Bcse i have a windows xp pro sp2 cd id like to try out..but im worried id mess something up....and if i do use it..does windows actually get instaled in a directory used by vmware?

---

### Post by lucia_engel on 2006-06-09
Thanks for the reply. 

Sorry, I have one more question. :p
Do you need a virtual harddisk for each virtual machine? (ie 16GB for vista, 8GB for XP, 8GB for random distro).

I appreciate your help.

---

### Post by FredB on 2006-06-09
[QUOTE=lucia_engel]Thanks for the reply. 

Sorry, I have one more question. :p
Do you need a virtual harddisk for each virtual machine? (ie 16GB for vista, 8GB for XP, 8GB for random distro).

I appreciate your help.[/QUOTE]

Every virtual machine is like a real machine. Each one needs an hard disk

Also, no need to launch vmware using sudo vmware. A simple vmware and all will work. Using sudo is like running it as root == bad thing.

And Vista is not the only OS you can emulate this way. You can also emulate another ubuntu, or worse like Fedora Core 5 ;)

---

### Post by FredB on 2006-06-09
[QUOTE=raffytaffy]Can using vmware cause any problems in general? Bcse i have a windows xp pro sp2 cd id like to try out..but im worried id mess something up....and if i do use it..does windows actually get instaled in a directory used by vmware?[/QUOTE]

Windows will run in a close space, using a lot of file for its hard disk drive. No problems if you run VMWare using only your user rights.

And VMWare installs a shortcut in applications / System tools Menu (for Ubuntu), I don't know if you use Kubuntu where is the shortcut.

---

### Post by bluevoodoo1 on 2006-06-09
Good guide. I guess I'll have to suck it up and use 16 gigs to install it (trying it with 8 gigs wasn't enough it seems. bah!)


[QUOTE=FredB]Also, no need to launch vmware using sudo vmware. A simple vmware and all will work. Using sudo is like running it as root == bad thing.

And Vista is not the only OS you can emulate this way. You can also emulate another ubuntu, or worse like Fedora Core 5 ;)[/QUOTE]

1. Agreed.

2. Agreed... I've had breezy, dapper, Suse 10, FreeBSD all working with VMware... (though fedora core 5 or Solaris 10 doesn't seem to want to cooperate).

---

### Post by aktiwers on 2006-06-09
Removed the "sudo" ;)
Didnt know, added it because I had some permition problems. But its working fine now.

---

### Post by bluevoodoo1 on 2006-06-09
Anyone's internet working with Vista? All other OSes that I've got working with vmware have had internet working, but not Vista. Probably a blessing in disguise...

---

### Post by aktiwers on 2006-06-09
[quote=bluevoodoo1]Anyone's internet working with Vista? All other OSes that I've got working with vmware have had internet working, but not Vista. Probably a blessing in disguise...[/quote] 
It didnt work for me first.. but go to Control Panel and setup a connection, as usual on Windows. On XP it worked on my first boot, but in Vista I had to do this.

But yes it works if you do that. Maybe I should add this to the howto? Well its here now, I will do it when I get some more time.

---

### Post by raffytaffy on 2006-06-09
[http://rbancer.2.ag/Screenshot.png](http://rbancer.2.ag/Screenshot.png)
im on my way to making my virtual windows

---

### Post by bluevoodoo1 on 2006-06-09
[QUOTE=aktiwers]It didnt work for me first.. but go to Control Panel and setup a connection, as usual on Windows. On XP it worked on my first boot, but in Vista I had to do this.

But yes it works if you do that. Maybe I should add this to the howto? Well its here now, I will do it when I get some more time.[/QUOTE]


Strange, it won't find my network hardware. It's a simple ethernet connection.. eh... oh well!

---

### Post by aktiwers on 2006-06-09
[quote=bluevoodoo1]Strange, it won't find my network hardware. It's a simple ethernet connection.. eh... oh well![/quote]
 
Yeah I got a simply connection too. Normally it would work on first boot.. did both with ubuntu, gentoo, knoppix and windows xp. But in Vista I had to manually set it up. 
 
While I was setting up the internet connection on Vista, it stopped and told me I already had a running and working connection. After that, it worked!
 
Before that it didnt. I had rebooted into it like 5 times, before doing this, and with no internet access.
 
Did you remember to install the Vmware tools?
 
My experiance is, that Network Brigde works best. 
What kind of connection did you setup for the virtual machine in Vmware?

EDIT:
Okey im running Vista now, full screen, and made a screenshot of the Internet connection place. Try mess with some stuff there, and Im sure you will make it work.

(A little offtopic)
The New explorer.exe is really a lot like Gnome! Also when I wanted to save my screenshot (using mspaint :(  ) it actually suggested .Png format as default!

---

### Post by bluevoodoo1 on 2006-06-09
[QUOTE=aktiwers]Did you remember to install the Vmware tools?[/QUOTE]

Ah ha! Yes, installing vmware tools fixed it! Thanks!

Sidenote: What do you know about the "14 days left to activate" from the 
Control Panel > Maintenance > System area??

Does it actually countdown until someone activates it? (perhaps tomorrow I will find this out for myself!)

---

### Post by cooldudejz on 2006-06-09
i just got everything to work, but i dont have a dvd burner/player everything worked fine until i put in my product key and then the installer said it couldnt find the cd. is there a waya round this, since the iso is on my harddrive can i trick it into thinking i have a cd in while it is just loading off my harddrive.

---

### Post by jnev on 2006-06-09
vmware doesn't work as a command in the terminal.. it says 'command not found'

```
jnev@jnev:~$ vmware
bash: vmware: command not found

```

I already had vmware installed running windows xp, and I just installed it again from the repos to try and rectify the problem. no love though. any help?

---

### Post by raffytaffy on 2006-06-10
ok say i allocated 10 gigs to a vmware OS...but i decided to ditch it...how do i get that 10 gigs back?
ok i went into /var/lib/vmware/virtual_machines  and erased the dir:)

---

### Post by FredB on 2006-06-10
Under good old vmware (workstation one), you can easily destroy a Virtual Machine. Also, you have to option to have a dynamically growing virtual hard drive instead of making it for good at the first time you run your virtual machine.

---

### Post by Kza on 2006-06-10
Well I just tried it, and no luck with the vista installation. Text in windows was missing, a dll reported missing.. I have attached screenshots. I guess my ISO must have been corrupted or something...

Can someone generate me a quick md5sum (or better yet some par2s) for the english 32bit version?
I get a md5sum of:
0e733ab1a8e8ff9a8684fd3639332773 *vista_5384.4.060518-1455_winmain_beta2_x86fre_client-LB2CFRE_EN_DVD.iso

---

### Post by miggl on 2006-06-10
When trying to install vmware from the commandline, it returns this error:
```
mike@ubuntu:~/Desktop/vmware$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

mike@ubuntu:~/Desktop/vmware$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

```

I currently don't have vm-ware installed. However, when I look in synamptiv for vmware packages, one is installed (apparently by default) called "xserver-xorg-driver-vmware". If I try to uninstall that, it will uninstall "xserver-xorg-driver-all" as well, which I obviously don't want.

UPDATE: I noticed I have a vmware folder in my home directory from a previous installation. I removed that and it fixed the error above. However, now when I try to install, I get:
```
mike@ubuntu:~/Desktop/vmware$ sudo sh ./vmware-install.pl
./vmware-install.pl: line 8: use: command not found
./vmware-install.pl: line 11: use: command not found
./vmware-install.pl: line 14: my: command not found
./vmware-install.pl: line 15: my: command not found
./vmware-install.pl: line 16: my: command not found
./vmware-install.pl: line 17: my: command not found
./vmware-install.pl: line 18: my: command not found
./vmware-install.pl: line 19: my: command not found
./vmware-install.pl: line 20: my: command not found
./vmware-install.pl: line 21: my: command not found
./vmware-install.pl: line 22: my: command not found
./vmware-install.pl: line 23: my: command not found
./vmware-install.pl: line 24: my: command not found
./vmware-install.pl: line 25: my: command not found
./vmware-install.pl: line 28: my: command not found
./vmware-install.pl: line 31: my: command not found
./vmware-install.pl: line 35: my: command not found
./vmware-install.pl: line 36: my: command not found
./vmware-install.pl: line 37: my: command not found
./vmware-install.pl: line 38: my: command not found
./vmware-install.pl: line 39: my: command not found
./vmware-install.pl: line 40: my: command not found
./vmware-install.pl: line 41: my: command not found
./vmware-install.pl: line 43: my: command not found
./vmware-install.pl: line 44: my: command not found
./vmware-install.pl: line 45: my: command not found
./vmware-install.pl: line 46: my: command not found
./vmware-install.pl: line 47: my: command not found
./vmware-install.pl: line 50: sub: command not found
./vmware-install.pl: line 51: undef: command not found
./vmware-install.pl: line 52: undef: command not found
./vmware-install.pl: line 53: undef: command not found
./vmware-install.pl: line 54: undef: command not found
./vmware-install.pl: line 55: undef: command not found
./vmware-install.pl: line 57: syntax error near unexpected token `INSTALLDB,'
./vmware-install.pl: line 57: `  open(INSTALLDB, '<' . $gInstallerMainDB)'
```
Not sure what I'm doing wrong, is some prerequisite missing?

---

### Post by aktiwers on 2006-06-10
First off, The links are back online, and you can now download the .Iso again!

[quote=cooldudejz]i just got everything to work, but i dont have a dvd burner/player everything worked fine until i put in my product key and then the installer said it couldnt find the cd. is there a waya round this, since the iso is on my harddrive can i trick it into thinking i have a cd in while it is just loading off my harddrive.[/quote] 
Its in the guide! Read nr. [COLOR=Red]7)[/COLOR] again. Check if you have other Virtual cd's, that you picked the right one to install on.

[quote=jnev]vmware doesn't work as a command in the terminal.. it says 'command not found'

```
jnev@jnev:~$ vmware
bash: vmware: command not found

``` 
I already had vmware installed running windows xp, and I just installed it again from the repos to try and rectify the problem. no love though. any help?[/quote] 
Sorry, I dont know. Try reinstalling vmware. First remove it, then install it again. But I dont know, as I said im a noob myself. Maybe someone else knows?

[quote=Kza]Well I just tried it, and no luck with the vista installation. Text in windows was missing, a dll reported missing.. I have attached screenshots. I guess my ISO must have been corrupted or something...

Can someone generate me a quick md5sum (or better yet some par2s) for the english 32bit version?
I get a md5sum of:
0e733ab1a8e8ff9a8684fd3639332773 *vista_5384.4.060518-1455_winmain_beta2_x86fre_client-LB2CFRE_EN_DVD.iso[/quote] 
Try this to check it:
Open k3b and go to Tools -> Burn DVD Image.  (we are not burning anything) We use k3b to test out the integrity of your Vista file. Navigate to where vista.iso is and click on it . Then, k3b will test out the integrity of your vista.iso. If it comes back with a green check mark, then it is good.

If you dont have k3b, simply ```

sudo apt-get install k3b
``` 
[B]Miggl:

[/B]Sorry, I really dont know. But I would suggest to remove the program completely. Then you could begin all over from the start of the guide. Else hopefully someone else can help you.

---

### Post by aktiwers on 2006-06-10
[quote=bluevoodoo1]Ah ha! Yes, installing vmware tools fixed it! Thanks!

Sidenote: What do you know about the "14 days left to activate" from the 
Control Panel > Maintenance > System area??

Does it actually countdown until someone activates it? (perhaps tomorrow I will find this out for myself!)[/quote]

I dont know. I did it right after I got online. 8)
Did it? :)

---

### Post by bluevoodoo1 on 2006-06-10
[QUOTE=jnev]vmware doesn't work as a command in the terminal.. it says 'command not found'

```
jnev@jnev:~$ vmware
bash: vmware: command not found

```[/QUOTE]

To start the vmware from the Repos it might be vmplayer or vmware-player

From a terminal type "vm" then hit the Tab button on your keyboard, and it *should* autocomplete it or something...

The vmware from the repo never worked for me, might be better off with the guide here....

EDIT:
[QUOTE=aktiwers]I dont know. I did it right after I got online. 8)
Did it? :)[/QUOTE]

Yes it did go down! I "activated" it.

---

### Post by jnev on 2006-06-10
[QUOTE=bluevoodoo1]To start the vmware from the Repos it might be vmplayer or vmware-player

From a terminal type "vm" then hit the Tab button on your keyboard, and it *should* autocomplete it or something...

The vmware from the repo never worked for me, might be better off with the guide here....[/QUOTE]

well if I type vmplayer it opens up vmware.. but that's not what I want. I can open my existing windows xp image.. but there's no option to make a new one..

---

### Post by nickm on 2006-06-10
Thanks, its not a hard thing to set up, but i would never have thought to try vmware server, i'v tried Xen and Qemu and was about to give up.

Its worked for me and i can safely say no one is missing anything by staying with linux :-D 
Except maybe the voice controling it has ;) but im sure we have that too

---

### Post by malte on 2006-06-10
It works good...
But randomly connection disappears :( 
Have you found the same problem? ](*,)

---

### Post by medw1974 on 2006-06-10
[QUOTE=Kza]Well I just tried it, and no luck with the vista installation. Text in windows was missing, a dll reported missing.. I have attached screenshots. I guess my ISO must have been corrupted or something...

Can someone generate me a quick md5sum (or better yet some par2s) for the english 32bit version?
I get a md5sum of:
0e733ab1a8e8ff9a8684fd3639332773 *vista_5384.4.060518-1455_winmain_beta2_x86fre_client-LB2CFRE_EN_DVD.iso[/QUOTE]

I've got the same thing happening here, I suspect it may be something to do with available memory for the virtual machine, but am not entirely sure about this.

---

### Post by miggl on 2006-06-10
I was able to fix my problems:
```
sudo rm -d -r ~/vmware
sudo rm -d -r /etc/vmware
```

After that the install went off without a hitch.

---

### Post by miggl on 2006-06-10
One thing that is important to note: if you are running Linux 64-bit, you should install the 64-bit version of Vista as well, as otherwise the 3d graphics will not be accelerated and you wont get all the goodies!

---

### Post by uno on 2006-06-11
[QUOTE=miggl]UPDATE: I noticed I have a vmware folder in my home directory from a previous installation. I removed that and it fixed the error above. However, now when I try to install, I get:
```
mike@ubuntu:~/Desktop/vmware$ sudo sh ./vmware-install.pl
./vmware-install.pl: line 8: use: command not found
./vmware-install.pl: line 11: use: command not found
./vmware-install.pl: line 14: my: command not found

```
Not sure what I'm doing wrong, is some prerequisite missing?[/QUOTE]

You mistyped the command. There is no "sh" in there. It should be:
```
sudo ./vmware-install.pl
```

---

### Post by drfalkor on 2006-06-11
Thnx for the guide! 6 stars for you ! :KS :KS :KS :KS :KS :KS

---

### Post by hajk on 2006-06-11
Some games, like Train Simulator, want to do *hardware* graphics acceleration, so will NOT run in a virtual Vista or XP installed in VMware...:(

---

### Post by uno on 2006-06-11
The install worked great. Thanks for the great howto. I'm typing this in under vista.

The only thing I had to do differently was my network connection. I used "Network Bridge" as suggested and made sure vmware tools were installed. THen I tried a few times to configure the network connection. It could see a network adapter, but couldn't connect to the internet. Then I powered down vista and changed the vmware setting from "Network Bridge" to "NAT", and that fixed it.

---

### Post by Who on 2006-06-11
[QUOTE=Kza]Well I just tried it, and no luck with the vista installation. Text in windows was missing, a dll reported missing.. I have attached screenshots. I guess my ISO must have been corrupted or something...

Can someone generate me a quick md5sum (or better yet some par2s) for the english 32bit version?
I get a md5sum of:
0e733ab1a8e8ff9a8684fd3639332773 *vista_5384.4.060518-1455_winmain_beta2_x86fre_client-LB2CFRE_EN_DVD.iso[/QUOTE]

I have the same problem _and_ the same md5sum. Can someone who has it working post their md5sum?

---

### Post by Kza on 2006-06-11
[QUOTE=Who]I have the same problem _and_ the same md5sum. Can someone who has it working post their md5sum?[/QUOTE]

Heh I have to admit, I feel a lot better now that someone else has the same problem. Apparently that md5sum is correct, so the image cant be the problem it must be something else.

I found the md5sums at [http://board.iexbeta.com/index.php?s=&showtopic=23258&view=findpost&p=269272]("http://board.iexbeta.com/index.php?s=&showtopic=23258&view=findpost&p=269272")

---

### Post by Who on 2006-06-11
[QUOTE=Kza]Heh I have to admit, I feel a lot better now that someone else has the same problem. Apparently that md5sum is correct, so the image cant be the problem it must be something else.

I found the md5sums at [http://board.iexbeta.com/index.php?s=&showtopic=23258&view=findpost&p=269272]("http://board.iexbeta.com/index.php?s=&showtopic=23258&view=findpost&p=269272")[/QUOTE]

Right then: 
I have an Athglon XP 512mb RAM (using 256 for vmware) and an Nforce4 MX400 64mbc ard - any similarities?

Has anyone else had to do any special things with the bios

Oh, I have a 16gb disk, split into 2gb files on the disk...

If I run vmware form the terminal I get:
```

terminate called after throwing an instance of 'std::length_error'
  what():  basic_string::_S_create
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

```

but it still starts...

Any ideas anyone - do others get these errors?

Thanks for any help. 
Who

---

### Post by Kza on 2006-06-11
[QUOTE=Who]Right then: 
I have an Athglon XP 512mb RAM (using 256 for vmware) and an Nforce4 MX400 64mbc ard - any similarities?

Has anyone else had to do any special things with the bios

Oh, I have a 16gb disk, split into 2gb files on the disk...

If I run vmware form the terminal I get:
```

terminate called after throwing an instance of 'std::length_error'
  what():  basic_string::_S_create
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

```

but it still starts...

Any ideas anyone - do others get these errors?

Thanks for any help. 
Who[/QUOTE]

Yes my system is also athlon xp and is the same regarding the ram and virtual hard drive configuration. Didnt do anything to the bios, but I did add an autodetected sound card. I also get the same error starting vmware.

---

### Post by uno on 2006-06-11
When I start from a terminal I also get:

```

/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

```

But it works just fine. I don't think that is your problem.

---

### Post by uno on 2006-06-11
I hava 1 GB of RAM with 512 MB for vista. I think the minimum requirements for vista is 512 MB. That might be your problem.

[http://www.microsoft.com/windowsvista/getready/systemrequirements.msp](http://www.microsoft.com/windowsvista/getready/systemrequirements.msp)

---

### Post by Viivac on 2006-06-14
I have some trouble getting this to work. I get the following: 

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

I have no idea how to get past this point. I've tried to apt-get some header files but it said that the files included no linux.h and that I should probably reconfigure my kernel. I didn't want to do this manually as the kernel I use is working just fine (686-smp on a laptop) but I won't get past this point. 

Anyone got this problem?

---

### Post by Kza on 2006-06-14
You must have forgotten this step: ```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
```

[QUOTE=Viivac]I have some trouble getting this to work. I get the following: 

...

I have no idea how to get past this point. I've tried to apt-get some header files but it said that the files included no linux.h and that I should probably reconfigure my kernel. I didn't want to do this manually as the kernel I use is working just fine (686-smp on a laptop) but I won't get past this point. 

Anyone got this problem?[/QUOTE]

---

### Post by Viivac on 2006-06-14
[QUOTE=Kza]You must have forgotten this step: ```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
```[/QUOTE]

I did. Silly me. :(  Thanks!

---

### Post by someusernoob on 2006-06-15
It was working fine untill i got this kernel update today.

It wouldnt start blabla, so i updated the build-eesential, did a uninstall of VMware, and re-installed it. No errors or such.

It will start up now, i can make virtual machins, but i can not power them on?

I get this funny error:
Unable to change virtual machine power state: The process exited with an error:
End of error message.

What to do?

Edit: I used the same default settings during the installation, and put the Virtual Machines in the same folder as before (/home/user/VMware)...

---

### Post by someusernoob on 2006-06-15
Did a large search through the computer for vmware files/folders, and found some config files of vmware server. Deleted them and it seems it works fine now (it's installing xubuntu without any problems). Strange that the uninstaller didn't delete them for me.

---

### Post by hizaguchi on 2006-06-17
Heh, doesn't work with 128 megs of ram.  If I give the virtual machine any less than 272 megs Windows complains that it can't make the ramdisk.  And by that time I'm swapping so much (on a laptop harddrive, too) that it took a half hour to get the boot up progress bar half way.  What's your system like if this is working for you?

---

### Post by domino on 2006-06-17
Does anyone know the default install size for Vista? I can only accommodate 8gig on this drive.

---

### Post by BlackWoxs on 2006-06-18
[QUOTE=domino]Does anyone know the default install size for Vista? I can only accommodate 8gig on this drive.[/QUOTE]

"Be sure the virtual machine has at least 512MB of RAM. The host computer must have more than 512MB of RAM to support this setting. If you are installing the 32-bit version of Windows Vista beta, be sure the virtual machine&#8217;s hard drive is 16GB or larger. If you are installing the 64-bit version of Windows Vista beta, be sure the virtual machine&#8217;s hard drive is 24GB or larger."
[http://www.vmware.com/support/guestnotes/doc/guestos_winvista.html](http://www.vmware.com/support/guestnotes/doc/guestos_winvista.html)

I could not get VISTA to install using a 8 - 10 GB HDD, once I changed to 16GB all is fine. The base install used 8.6GB

---

### Post by domino on 2006-06-18
Yea, 16gig would let me install. That leaves me with about 9gig of free space which I think is way too much for a non-production OS. I was thinking of cloning the install on a 10gig virtual disk which gives me back some usefull disk space for the host.

I have another question, Is it a problem to activate Vista while in vmware and later reactivate it on a native install?

---

### Post by Huggy on 2006-06-18
Can anyone help me? I'm running Drapper 6.06 64bit, and I can't seem to find vmware tools. I have all the repositories enabled. Also I tried downloading and installing it per guide specs, and there is no .pl in any of my file downloads. I need help, because I would really like to try and play with windows vista, but I all I seem to be able to get is just the vmware plaer itself. Which works great for SUSE because I can download the vmx file itself already made. So can anyone help me? PLEASE???

---

### Post by aktiwers on 2006-06-18
[quote=Huggy]Can anyone help me? I'm running Drapper 6.06 64bit, and I can't seem to find vmware tools. I have all the repositories enabled. Also I tried downloading and installing it per guide specs, and there is no .pl in any of my file downloads. I need help, because I would really like to try and play with windows vista, but I all I seem to be able to get is just the vmware plaer itself. Which works great for SUSE because I can download the vmx file itself already made. So can anyone help me? PLEASE???[/quote]

Im not sure what you mean? 

I attached a screenshot. Download the first one -  Extract the Tar.gz - cd to the folder - and run the .pl file. Just like the guide says.

Hope this helps. :)

---

### Post by Huggy on 2006-06-18
ok I downloaded the second time and I found it. Appearently I got a bad download, but now I'm running into it detecting another vmware I installed through ubuntu? 

huggy@huggy-desktop:~/MyDownloads/vmware-mui-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

huggy@huggy-desktop:~/MyDownloads/vmware-mui-distrib$

So What am I to do. Uninstall it?

---

### Post by BlackWoxs on 2006-06-19
[QUOTE=Huggy]ok I downloaded the second time and I found it. Appearently I got a bad download, but now I'm running into it detecting another vmware I installed through ubuntu? 

huggy@huggy-desktop:~/MyDownloads/vmware-mui-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

huggy@huggy-desktop:~/MyDownloads/vmware-mui-distrib$

So What am I to do. Uninstall it?[/QUOTE]


Did you try running the vmware uninstall script: vmware-uninstall.pl

---

### Post by DaveH on 2006-06-20
I had an error about GCC_3.4...

```

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

```

I'm using the cairo libs from Beerorkid - just running 
```

sudo apt-get install --reinstall libcairo2 

```
seemed to fix it

---

### Post by souteneur3190 on 2006-06-21
so wait i just cant make a folder called "Vista" in home, i need another physical harddrive in my computer?

---

### Post by souteneur3190 on 2006-06-22
i just got done reinstalling ubuntu because of that problem, the old one really messed up my respitorys.

---

### Post by cooldudejz on 2006-06-22
when i try to create a virtual sever for vista, everything is ok until after the disk space is allocated. after the allocating i get this error message. 

"Error opening virtual machine "/var/lib/vmware/Virtual Machines/Windows Vista (experimental)/Windows Vista (experimental).vmx": Virtual machine "/var/lib/vmware/Virtual Machines/Windows Vista (experimental)/Windows Vista (experimental).vmx" is not in the inventory."

can anyone help me

---

### Post by PingunZ on 2006-06-22
Is this much slower then normal windows cause I want to run my games in it :)
looks like a nice HOWTO ;)

Grtz PingunZ

---

### Post by th3gh05t on 2006-06-22
[QUOTE=aktiwers]
Try this to check it:
Open k3b and go to Tools -> Burn DVD Image.  (we are not burning anything) We use k3b to test out the integrity of your Vista file. Navigate to where vista.iso is and click on it . Then, k3b will test out the integrity of your vista.iso. If it comes back with a green check mark, then it is good.[/QUOTE]

Hi, 

I am getting the same error message as 'Kza'. What if we check the file, and it comes out as green? Should we download another file? Anyone had luck with installing after receiving this error?

Thanks, th3gh05t

---

### Post by naked on 2006-06-25
So, This is great, but I'm confused at why the server is free, and why it will remain after it is out of beta?

L

---

### Post by aktiwers on 2006-06-25
[quote=th3gh05t]Hi, 

I am getting the same error message as 'Kza'. What if we check the file, and it comes out as green? Should we download another file? Anyone had luck with installing after receiving this error?

Thanks, th3gh05t[/quote]

If it shows up as Green, the .iso should be ok! Then just follow the guide.
What error are you receiving? Post it here, maybe someone can help.

> So, This is great, but I'm confused at why the server is free, and why it will remain after it is out of beta?

I really dont know the answer to that, but I believe a small search here on the forum or on google, will tell you the answer. 

>  	Is this much slower then normal windows cause I want to run my games in it :smile:
looks like a nice HOWTO :wink:

Grtz PingunZ

On my PC, Vista runs a little slower, but my XP install runs great, and I cant really feel any differents. But about running games in it, I think Vmware Tools installs some drivers for you, and so fare I had problems with 3D games. 

But I never really tried to get around this, as I am not a gamer, so it is proberbly possible. Maybe someone else can help out with this.



Well im on a vacation now, so I should get out in the good weather, hope you guys can help each others out :)

---

### Post by mdh on 2006-06-26
Is the audio device shared by vmware by default. I am inside vista now but it says no audio devices found. Is this a case of missing drivers or does vmware does not allow the audio device to be shared ??, I am a noob with vmware sorry if this question is silly ;)

---

### Post by aktiwers on 2006-06-26
[quote=mdh]Is the audio device shared by vmware by default. I am inside vista now but it says no audio devices found. Is this a case of missing drivers or does vmware does not allow the audio device to be shared ??, I am a noob with vmware sorry if this question is silly ;)[/quote]

You Will Need to Go add the sound Manually!

You do that in the "Edit Virtual Machine settings" where you can ad cdrom drive, harddrives (had no luck with that yet) and other stuff. Simply add the sound device and the sound will work.

---

### Post by gommle on 2006-06-26
I needed to use a proxy to access the VMWare site. I used this one: 24.18.37.170:8080 if anybody else needs.

---

### Post by jinx099 on 2006-06-27
anyone know how to use a pci card with vmware?

---

### Post by PhogHawk on 2006-06-27
I have these errors when running "vmware" from the terminal:

```
phoghawk@ben:~/Desktop/vmware-server-distrib$ vmware
/usr/lib/bin/vmware: /usr/lib/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/bin/vmware: /usr/lib/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/bin/vmware: /usr/lib/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/bin/vmware: /usr/lib/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/bin/vmware: /usr/lib/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/bin/vmware: /usr/lib/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

```

I tried "apt-get install --reinstall libcairo2" but that didn't work. This is really lame. The VMware server console doesn't even start up.

---

### Post by Sam on 2006-06-30
Nice howto, it worked well. Thank you !

---

### Post by anothernoob123 on 2006-06-30
Hi, Sorry but I am trying to follow these steps.. what "terminal" am i supposed to type these codes in?

---

### Post by Mr.X on 2006-07-02
Lol, why would i emulate windows in linux, wouldn't it be wiser to emulate linux in windows :P?

---

### Post by -deadcats on 2006-07-02
[QUOTE=PhogHawk]I have these errors when running "vmware" from the terminal:

```
phoghawk@ben:~/Desktop/vmware-server-distrib$ vmware
/usr/lib/bin/vmware: /usr/lib/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/bin/vmware: /usr/lib/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/bin/vmware: /usr/lib/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/bin/vmware: /usr/lib/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/bin/vmware: /usr/lib/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/bin/vmware: /usr/lib/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

```

I tried "apt-get install --reinstall libcairo2" but that didn't work. This is really lame. The VMware server console doesn't even start up.[/QUOTE]


Fire-up Synaptic and install GCC 3.4.

regards,
-dc

---

### Post by s_h_a_d_o_w_s on 2006-07-02
I can't get a CD-KEY. The site says that the public preview program has ended, and they are no longer taking in requests for cd-keys. can some1 paste theirs here plz? I really want to try it!

---

### Post by RRS on 2006-07-02
[QUOTE=s_h_a_d_o_w_s]I can't get a CD-KEY. The site says that the public preview program has ended, and they are no longer taking in requests for cd-keys. can some1 paste theirs here plz? I really want to try it![/QUOTE]

Same problem here. 
While downloading Friday night I switched over to the site listed and it said no more orders were being accepted and had no links or other options to get a key.

Odd that they'd quit providing keys while still providing the download, which was successfull btw.

Will a "borrowed" key work or is it "one key/one machine" like xp?

---

### Post by aktiwers on 2006-07-03
The CD Key will work on 10 Machines!

Here is mine:

> W2P3M-HG7WV-2QG8B-CGFJX-BJCVP 
I used it on 1 machine, wich means the next 9 people will be able to use it.

EDIT:

Maybe post below if you used it, so we know how many used it. To avoid number 10 to start the installation without a working cd-key. 

(Also I dont hope this breaks any rules on the forum, as I am allowed to install it on 10 computers. But if so, please remove the key and many times sorry).

---

### Post by RRS on 2006-07-03
[QUOTE=aktiwers]The CD Key will work on 10 Machines!

Here is mine:

 
I used it on 1 machine, wich means the next 9 people will be able to use it.

EDIT:

Maybe post below if you used it, so we know how many used it. To avoid number 10 to start the installation without a working cd-key. 

(Also I dont hope this breaks any rules on the forum, as I am allowed to install it on 10 computers. But if so, please remove the key and many times sorry).[/QUOTE]

Kewl :) Thanks.
That still leaves 8 I believe.

Since I probably won't have time to install for a day or 2 so let us know if this breaks any forum rules, etc.

Thanks again,  aktiwers

---

### Post by s_h_a_d_o_w_s on 2006-07-03
I will use it in .10 mins.,  7 more people!!!!

---

### Post by JsPr on 2006-07-03
I will use one. 6 to go.

---

### Post by featherking on 2006-07-03
ill use one too! 5 more peeps

---

### Post by corefile on 2006-07-04
I just used it too, 4 more

---

### Post by corefile on 2006-07-04
[QUOTE=aktiwers]


On my PC, Vista runs a little slower, but my XP install runs great, and I cant really feel any differents. But about running games in it, I think Vmware Tools installs some drivers for you, and so fare I had problems with 3D games. 

But I never really tried to get around this, as I am not a gamer, so it is proberbly possible. Maybe someone else can help out with this.



Well im on a vacation now, so I should get out in the good weather, hope you guys can help each others out :)[/QUOTE]

VMware does not support 3D in the guest system, so you can't use VMware to play any 3D games

---

### Post by vijirajan on 2006-07-04
I just used it too, 3 more

---

### Post by Jazzbunny on 2006-07-06
I used one, so 2 to go.

---

### Post by no neck joe on 2006-07-06
I used one, one to go.

---

### Post by maver on 2006-07-06
seems I have got the last one :) 
many thanks

---

### Post by evil_elman on 2006-07-06
Hmmm... Managed to install VMWare Server without any issues. Also succeeded in creating a virtual machine and so on.

However, when booting my recovery Windows XP CD (which I got with my laptop) it complains that this is not an Acer computer...

Is there any way to get around this check or have the server emulate the Hardware characteristics and ID's of the host system?

---

### Post by erico on 2006-07-06
For internet with Vista Ultimate, I used the driver from the NIC chipset. I have a Linksys WMP54G v4, the chipset is Railink,so I used the Railink R2500 driver. All you need to do is Google for the chipset of your wireless or wired NIC and you should be in business. There are very few drivers for NICs that are native within Vista. Good luck!! If you have any more questions on more details with Vista there are numerous sites. I enjoyed playing around with Vista although there were a few things built in that I did not care for at all.
Eric :cool:

---

### Post by ALIENDUDE5300 on 2006-07-06
How do you download firefox for virtual windows?

---

### Post by ALIENDUDE5300 on 2006-07-06
Nevermind, I figured it out.

---

### Post by VetterZor on 2006-07-06
This thread is expired. Vista has closed the Beta 2 product key site down. Does anyone have a key I could use?? Legally of course!

---

### Post by JoshHendo on 2006-07-07
I don't have a key you can use, sorry :(. Used it just then.

I had Vista stitting in a ISO that I never installed. I managed to install it with VMWare, but it really slows down the computer, and I can't get my wireless card to work on it. I would really like to try Windows Live Messenger on it, but without my wireless card, it is pointless.

Had anyone had any success getting a TP-Link wireless card working?

---

### Post by s_h_a_d_o_w_s on 2006-07-09
Does anyone have another cd-key for me? I used the aforementioned cd-key and vista says it expires in 13 days 'cause it's in use.

---

### Post by s_h_a_d_o_w_s on 2006-07-09
I got it! You just have to enter the same cd-key where it says ''activate Windows''. It now says I have genuine windows!

---

### Post by th3gh05t on 2006-07-18
How do I remove everything that is associated with VMware?

---

### Post by beerorkid on 2006-07-25
> **th3gh05t said:**
> How do I remove everything that is associated with VMware?

you almost have to reinstall ;)

I wanted to put vmware server on my box after I had player on there.  COuld not figure it out, and it seemed noone else knew how to either.
Guess you could locate vmware and delete tons of stuff, but a reinstall sounds easier ;)

BTW server is sooooo fricking awesome.  i use it at work and home.  We use a bunch of vmware stuff at work, and the free stuff is just about as good.

---

### Post by billputer on 2006-07-26
Here's my key, it should work on 9 more machines.

BFVXP-PWWCR-RK6KV-XGCFT-BQDYV

---

### Post by junamuno on 2006-08-18
Can't get to launch vmplayer,neither from Apps>System tools>vmware player nor the terminal, the message I get from the terminal is:

junamuno@EUZKADI:~$ vmplayer
/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

(vmplayer:13270): Gdk-WARNING **: locale not supported by Xlib

(vmplayer:13270): Gdk-WARNING **: cannot set locale modifiers
/home/junamuno/.gtkrc-2.0:2: No se ha podido encontrar el archivo «include»: «.gtkrc-2.0-scrollbar_cog»

Any Suggestions????

THX

---

### Post by BLTicklemonster on 2006-09-28
> **Who said:**
> Right then: 
I have an Athglon XP 

but it still starts...



Who


Intgel > Athglon XP

:)

j/k I have athlon, wouldn't use intel.

So has anyone installed Edgy in vmware in Dapper, and if so, did you experience any problems with the sound not being recognized? I get an error message, and the system locks up. 

> **aktiwers said:**
> You Will Need to Go add the sound Manually!

You do that in the "Edit Virtual Machine settings" where you can ad cdrom drive, harddrives (had no luck with that yet) and other stuff. Simply add the sound device and the sound will work.

I can't edit because it's a live cd. No operating system installed yet.

*edit:

Ah yes, I do have xp installed in vmware, so I opened the vmx file, and use the sound setting from it in the ubuntu.vmx file, and now I can get to the desktop in live cd complete with sound. (upped the ram to 267, too)

*edit:

I'm in Edgy in VMWare server on Dapper right now posting this. Appears sluggish and "laggy" for lack of a better term. I need the vmware tools, of course, and there's an update pending. Looks pretty sharp.

Hope this helps if anyone has problems.

---

### Post by neogamerdrew on 2006-10-10
RC1 is out. Just click [http://www.microsoft.com/windowsvista/getready/preview.mspx]("http://www.microsoft.com/windowsvista/getready/preview.mspx")and you should be able to download and insatll RC1 just fine. That's what I did.

---

### Post by turkenator on 2006-11-01
hey aktiwers i know this post is abit old but if u happen to see this can u please post that background that we can c on the screen shot looks awsome thanks (if any1 else reads this and has vista installed can they plz post that background thanx heaps)

---

### Post by aktiwers on 2006-11-05
> **turkenator said:**
> hey aktiwers i know this post is abit old but if u happen to see this can u please post that background that we can c on the screen shot looks awsome thanks (if any1 else reads this and has vista installed can they plz post that background thanx heaps)

Its just the vista defualt background. Just google it. I found this in less than a minute:
[http://www.activewin.com/screenshots/vista/nov05ctp/Bliss.bmp](http://www.activewin.com/screenshots/vista/nov05ctp/Bliss.bmp)

---

### Post by turkenator on 2006-11-06
thanks alot

---

### Post by deepwave on 2006-11-07
Sigh... trying this Vista thing out on VMPlayer but it just stops on the progress bar finishes at the black Windows is loading files... screen.

Here is my .vmx file... any ideas what is wrong?

```

#!/usr/bin/vmware
displayName = "Windows"
guestOS = "winvista"

memsize = "512"
ide0:0.fileName = "vista-trial.vmdk"
ide1:0.fileName = "vista_dvd.iso"

# DEFAULT SETTINGS UNDER THIS LINE
config.version = "8"
virtualHW.version = "3"

MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

uuid.location = "56 4d bf 85 d7 56 a2 2d-dd cd 55 f6 57 2b 1c 74"
uuid.bios = "56 4d bf 85 d7 56 a2 2d-dd cd 55 f6 57 2b 1c 74"

uuid.action = "create"
checkpoint.vmState = ""

ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:2b:1c:74"
ethernet0.generatedAddressOffset = "0"

usb.present = "TRUE"
sound.present = "TRUE"

scsi0.present = "FALSE"
scsi0:0.present = "FALSE"
scsi0:1.present = "FALSE"

floppy0.present = "FALSE"

ide0:1.present = "FALSE"
ide1:1.present = "FALSE"

ide0:0.present = "TRUE"
ide0:0.deviceType = "disk"
ide0:0.startConnected = "TRUE"

ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "FALSE"
ide1:0.startConnected = "TRUE"

ide0:0.redo = ""

fileSearchPath = "/var/vmware;."

sound.virtualDev = "es1371"

```

---

### Post by ap9er on 2006-11-13
Has anyone successfully been able to install RTM? I can only seem to get as far as the splash screen on bootup, just want to see if I am not fighting a dying cause here by spending more time on it.

---

### Post by BLTicklemonster on 2006-11-14
So is there a download still to be had?

---

