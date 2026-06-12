---
title: "Ubuntu - 14.04 - Desktop Icons Missing - Can't Access Terminal either"
date: 2014-09-20
forum: New to Ubuntu
---

### Post by tarun4 on 2014-09-20
[COLOR=#000000]Hi , [/COLOR]

[COLOR=#000000]An offtrack question . I'm new to Ubuntu .[/COLOR]
[COLOR=#000000]Have installed Ubuntu 14.0.4 .[/COLOR]
[COLOR=#000000]Since this morning, all desktop icons are gone .[/COLOR]
[COLOR=#000000]I can log in to Ubuntu but after that desktop is completely blank, the menu icons which used to come at the left hand side of the desktop are missing .[/COLOR]
[COLOR=#000000]Also , pressing Ctrl+ALT+T to access terminal is also not working .[/COLOR]

[COLOR=#000000]Can somebody please help .[/COLOR]

[COLOR=#000000]regards[/COLOR]
[COLOR=#000000]Tarun[/COLOR]

---

### Post by sandyd on 2014-09-20
Moved to *New to Ubuntu*

---

### Post by tarun4 on 2014-09-20
Hello ,

A correction in the subject line "  Can't Access the terminal as well"  ...the desktop is blank with no launcher and no icons .

Checked in the forums but could not find a solution . 
Interesting this is only happening in my login, the Guest login seems to work fine .
Can someone please suggest
1) What has gone wrong
2) how to rectify it

thanks in advance

---

### Post by Bashing-om on 2014-09-20
tarun4; Hi !

No idea as to the why, but to fix ;
Try; at the login screen key combo ctl+alt+F1 to get a terminal console; login => username and password  ( no response to the screen when password enterd) :
```

sudo apt-get install dconf-tools
DISPLAY=:0 dconf reset -f /org/compiz/
unity --reset-icons
setsid unity

```

Now reboot to see the effect;
```

sudo shutdown -r now

```

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]perhaps, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tarun4 on 2014-09-21
> **Bashing-om said:**
> tarun4; Hi !

No idea as to the why, but to fix ;
Try; at the login screen key combo ctl+alt+F1 to get a terminal console; login => username and password  ( no response to the screen when password enterd) :
```
g-
sudo apt-get install dconf-tools
DISPLAY=:0 dconf reset -f /org/compiz/
unity --reset-icons
setsid unity

```

Now reboot to see the effect;
```

sudo shutdown -r now

```[INDENT][INDENT][INDENT]maybe yes[INDENT][INDENT][INDENT]perhaps, not so yes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hi Bashing-om , thanks, i tried the mentioned code
firstly, Ctrl+ALT+F1  did not open anything, but Ctrl+ALT+F6 opened a terminal so i went there
on the second line
"DISPLAY=:0 dconf reset -f /org/compiz/"   the error thrown was  --- 

"error : Could not connect: Connection refused "

Please suggest a way to overcome this problem.

thanks

---

### Post by Bashing-om on 2014-09-21
tarun4; Odd;

Real odd:
OK, let's see what we can do:
reboot to the grub boot menu, press 'e' for edit mode, arrow down and across to the terms "quiet splash" and replace them with the term "text";
key combo crl+x to continue the boot process to a textual terminal (TTY1). login here - username and password.
Now what results with terminal commands:
```

export DISPLAY=:0.0
dconf reset -f /org/compiz/
unity --reset-icons
setsid unity

```

Reboot to see the effect:
```

sudo shutdown -r now

```

Else, well, we can consider (RE-)installing the desktop (??).

[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT]try try again ( sky diving excepted )
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by backup757 on 2014-10-29
Same thing has happened to my Ubuntu installation.   I just installed it yesterday, have rebooted several times without issue.  Last night Ubuntu updater asked to install an update, so I said yes, it installed, asked to reboot, and after reboot the desktop is no longer using the video driver (so its like a stretched out 400x600 picture) and there are no icons on the desktop.   I could not break out using CtRL+ ALT - F1, but using F6 instead worked.    I have tried this procedure and it does not restore the icons.  Why is this happening, can I ever trust Ubuntu updates again???

---

### Post by wamses2 on 2014-12-01
I have the same problem, after running for a few months on 14.04.1 I saw a solution suggested for getting a sound alert on Capslock, the solution was based on compiz. I installed compiz settings manager, attempted the definition, but it didn't seem to be applying the alert. After trying various I changed the display option on compiz, overridding Ubuntu displays (the messages associated with this procedure I didn't write down).
I attempted the above fix, but on entering the DISPLAY=:0 reset -f /org/compiz/ command I encountered the message 
Error spawning command line 'dbus-launch --autolaunch=blahblah --binary-syntax --close-stderr'
'dconf reset [-f] PATH'
Reset a key or dir. -f is required for dirs.

If I logon to Ubuntu as my home user, I see no icons, and Ctl/Alt/T doesn't work, I can log on as a guest, and the display is fine, but I don't seem to be able to get rid of the compiz effect.
Any suggestions most welcome, at worst - even if it just an easy way to get my data from the machine so I can start again and reinstall 14.04.1

---

### Post by Bashing-om on 2014-12-01
wamses2; Humm;

I can not tell what changes you made might be of effect. Let me do some checking and think'n and I will return.
We poke at the desktop and see what we can do ( make sure "you" have the authority to access "your" desktop).
I will verify the procedure I have in mind.

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT].

---

### Post by Bashing-om on 2014-12-01
wamses2; I am Baacckk;

OK, let's determine what is:
Boot the install to the grub boot menu ( soon as bios screen clears depress and hold the right -shift- key);
With a ubuntu kernel highlighted ( asterisk ) press the 'e' key for edit mode -> boot parameters screen;
You see the line similar:
> 
linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff

In this screen arrow down to the line, and across to the terms "quiet splash" and replace with the term "text' - without the quotes;
Key combo ctl+x to continue the boot process to  the TTY1 terminal;
Login here with "your" username and "your" password ( there is no response to the screen when password is entered, security reasons and is normal)

Now to get to the nitty gritty:
Do you have authority to access "your" /home ?
```

ls -al .Xauthority
ls -al .ICEauthority

```
You should get similar:
> 
sysop@1404mini:~$ ls -al .Xauthority
-rw------- 1 sysop sysop 209 Aug  1 10:10 .Xauthority

sysop@1404mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 15648 Dec  1 16:10 .ICEauthority

Where "sysop" is my username, do these file reflect "YOU" ?

Next if "you" have authority, who owns your /home ?
```

ls -al /home

```
Again where I am "sysop" :
> 
sysop@1404mini:~$ ls -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 Nov 25 13:36 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 28 sysop sysop  4096 Dec  1 16:10 sysop


Next, do you own all the files in "your" /home directory ?
```

ls -al /home/<username>

```
where <username> is your actual username.

So far so good ?
Then, what desktop do you have - unity (lightdm)?
tell me the results:
```

ls -al /var/lib/lightdm
ls -al /etc/lightdm/lightdm.conf

```

------------------------------
Now we have some idea of what we are dealing with and from this we can proceed to see what can be done .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by wamses2 on 2014-12-01
Hi Bashing-Om
Many thanks for your reply. It was all going like your script said, although I only got 3 entries listed for ls -al /home
Then in response to ls -al /home/username many lines were output.
But in response to ls -al /var/lib/lightdm  I got the message ls :cannot open directory /var/lib/lightdm: Permission denied
And for ls -al /etc/lightdm/lightdm.conf I got the message ls: cannot  access /etc/lightdm/lightdm.comf: No such file or directory.

Sorry this prob wasn't the response you were hoping for.

---

### Post by Bashing-om on 2014-12-01
wamses2; Welp;

It is not what I hope for that counts, It is what it takes to fix the issue.
OK, indications are that you are not running "unity" for your desktop.
What then is your desktop ?
What desktop do you want to use ?
In Reference to:
> 
Then in response to ls -al /home username many lines were output.

were all the listed files and directories owned and grouped to "YOU" ?

Let's see if this gives a response:
```

sudo ls -al /var/lib/lightdm

``` as I am not going to give up on the notion that you are running unity for the DE.

And:
> 
/etc/lightdm/lightdm.co[color=red]m[/color]f

Make sure there is no typo here ( as I see it ) the command is " ls -al /etc/lightdm/lightdm.conf " where it is an 'n' vice 'm' in "conf' .
So far, not all bad.
[INDENT][INDENT][INDENT]we be looking
[/INDENT][/INDENT][/INDENT]

---

### Post by wamses2 on 2014-12-01
Thanks again
Sorry about the delay, I just typed this in once, and in going back to recheck your reply,seemed to have lost the pesky response from my previous typing.
As far as ls -al/home entries were concerned, the entries I could see (only the last 25 or so) appeared to belong to me except one which read:
drwx------ 2  2 root root 4096 Oct 16  14:45 .gvfs

Which desktop would I like? To be honest I'll go with anything I can get working, but right now from where I sit compiz doesn't appear very attractive.

The responses to the commands are:
sudo ls -al /var/lib/lightdm  returned the following

total 32
drwxr-x---   7 lightdm  lightdm  4096 Oct 16 11:24  .
drwxr-xr-x  67 root      root      4096  Oct 17 05:55 ..
drwxrwxr-x   4 lightdm  lightdm 4096 Oct16  11:24 .cache
drwxrwxr-x   6 lightdm  lightdm 4096 Oct16  11:24 .config
drwx------     3 lightdm  lightdm 4096 Oct16   11:24 .dbus
drwx------    3  lightdm  lightdm 4096 Dec  1   23:02 .gconf
drwxrwxr-x  3   lightdm  lightdm 4096 Oct16 11:24  .local
-rw------      1   lightdm  lightdm 183  Dec  1  23:03 .Xauthority

Apologies for the alignment of the above, I'm having to transcribe from the poorly machine.

ls -al /etc/lightdm/lightdm.conf
Returns No such file or directory.

---

### Post by Bashing-om on 2014-12-01
wamses2; Well, well ;

Looking more promising.
But I am bothered by :
> 
ls -al /etc/lightdm/lightdm.conf
Returns [color=red]No such file or directory[/color].


What release are you running ? And I will verify that that file should exist !
And to verify what desktop we are working with; What returns:
```

apt-cache policy ubuntu-desktop

```

Then we are ready to do something.

[INDENT]right, wrong, or otherwise
[INDENT][INDENT][INDENT][INDENT]do something
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wamses2 on 2014-12-02
Bashing-Om

Well the response to apt-cache policy ubuntu-desktop reads as follows
ubuntu-desktop
   Installed: (none)
   Candidate: 1.325
   Version table:
        1.325 0
            500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages

Which I guess will mean a lot more to you than it does to me. Am running on 14.04.1 32 bit version.

---

### Post by Bashing-om on 2014-12-02
wamses2; Humm (??).

Not having " ubuntu-desktop " installed:
> 
ubuntu-desktop
Installed: (none)

Blows away my plan of attack. I am presently at a loss as to a certain method from that terminal - no desktop GUI running - to determine what in fact we are working with. As a new user I do not expect you to "know" .
Let's see if this will reveal your environment:
```

cat /etc/X11/default-display-manager

```
As I would fix what you have - and are accustomed to - rather than install a different Desktop Environment that you may not like/want. ( you can experiment to your heart's desire once the system is stable )

Once we are sure of what we are working with, then we can take appropriate measures to fix what is.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by wamses2 on 2014-12-02
Hail Bashing-om
Message from cmd cat /etc/X11/default-display-manager
Reads
/usr/sbin/lightdm

I'll be out for a few hours, so if you send a response, it may be a while before I can get to try it. Thanks for your thoughts so far.

---

### Post by wamses2 on 2014-12-02
Sorry Bashing-om, one more thought. It's very considerate of you to try and preserve a familiar Desktop environment, but I'm pretty flexible in that respect, it's more about getting to the applications, although having said that it was my desire to get an audible warning over Capslock that got me into this fine mess to start with. Maybe I'm just a mixed up old boy.

---

### Post by Bashing-om on 2014-12-02
wamses2; Well, well;

You are not at fault here, the failure is all on me. Let's "ASSUME" that you have unity - good indications that is is true - as the DE. To that end to restore, let's see what results:
From the terminal from the grub boot menu: 
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo shutdown -r now

```
Do you now boot to the GUI login, and able to login in to your desktop ?

[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by wamses2 on 2014-12-02
Dear Bashing-om
Thanks for the commands, but unfortunately I ran them, many lines of text were output, nothing seemed to fail, but at the end, I'm afraid the same result. Log in using my user credentials, but no icons on desktop, and no reaction from Ctl/Alt/T.
I can get terminal from ctl/alt/F5 once I get through the login.
For what it's worth, the wallpaper that gets displayed when ubuntu kicks in, is not the standard one, it is one I selected a few weeks back.  This may or may not be significant.
Is it time to back up my data and re-install Unbuntu? I appreciate the time you've spent on this, but sometimes it's best to just get things moving again.  Either way, it's getting late here and I'll have to sleep on it. If you have any other commands you'd like me to deploy that's fine, I'll give them a go in the morning.
Thanks again.

---

### Post by Bashing-om on 2014-12-02
wamses2; Hey hey !

Making progress; ( can always re-install at any time ) 
ctl+alt+F5 -> terminal commands:
```

rm ~/.dmrc
sudo service lightdm stop
sudo dpkg-reconfigure lightdm
sudo dkpg-reconfigure unity
sudo shutdown - r now

``` 

Set 'lightdm' as the (D)esktop (M)anager and 'unity' as the (D)esktop (E)nvironment .

Post back any errors.

[INDENT][INDENT]this now could be it
[/INDENT][/INDENT]

---

### Post by wamses2 on 2014-12-03
Greetings Bashing-om
I ran the commands, only output from terminal was msg 'lightdm stop/waiting' after sudo service lightdm stop - following the commands :
 
Logon to my user displayed same symptoms, ie no sign of launcher, no toolbar at top of screen and no response to Ctl/alt/t.

I guess (maybe wrongly) that .dmrc may be created by  the reconfigures?  If so, when I attempted to rerun the commands I got the message 'rm:cannot remove 'home/g/.dmrc': No such file or directory'. I've no idea if this is significant or not, but I feel it's tricky for you not having much to work with in terms of evidence.

Only question I have from your last msg is where you write 'set 'lightdm' as the DM and 'unity' DE etc' - I assume this was you commenting about what the commands were doing rather than me requiring me to set them? If it is the latter, where would I do it?

---

### Post by Bashing-om on 2014-12-03
wamses2; UmmPhhh ....

Disappointed, to say the least, I sure thought a re-install of the desktop would be a resolution.

I am about out of ideas.
As you surmise, the file .dmrc should have been re-created ( config file for the user desk top );
I had expected a wizard for the reconfigure commands for you to interact with and direct the system in it's actions.

As a last hope;
What returns now from:
```

dpkg -l ubuntu-desktop
apt-cache policy ubuntu-desktop

```
IF, the response is positive ( ubuntu-desktop is fully installed ) then let's try post #4 once more.
```

DISPLAY=:0 dconf reset -f /org/compiz/
unity --reset-icons
setsid unity

```

Else; we begin the tedious process of reading the log files, see what the system reports for problems.

[INDENT][INDENT]no quit in my nature
[/INDENT][/INDENT]

---

### Post by wamses2 on 2014-12-03
Howdy Bashing-om

The results of dpkg -l ubuntu-desktop and  apt-cache policy ubuntu-desktop suggest that I have ubuntu desktop  installed in that they output the following:
ubuntu-desktop
  Installed: 1.325
  Candidate: 1.325
  Version table
*** 1.325 0
         500 httpgb.archive..ubuntu.com/ubuntu/ trusty/main i386 Packages
         100 /var/lib/dpkg/status

So, encouraged by this positive looking state, I went to the next step:
DISPLAY=:0 dconf reset -f /org/compiz
unity --reset-icons  
The unity  --reset-icons returned the following:
WARNING: no DISPLAY variable set, setting it to :0
stop: Unknown job: unity-panel-service
compiz (core) - Info: Loading plugin: core
start Unknown job: unity-panel-service
compiz (core) - Info: Starting plugin: core

But then, oh no! the system seems to hang, with a flashing underscore in column1 of the next line on the terminal display. That was about 20 mins ago, in the meantime I have typed this in and it still seems to be in a hang state. I suspect I'll need to disconnect the power supply to force a reboot, but before that I'll await your sage advice if that's OK with you.

---

### Post by wamses2 on 2014-12-03
Howdy Bashing-om

The results of dpkg -l ubuntu-desktop and  apt-cache policy ubuntu-desktop suggest that I have ubuntu desktop  installed in that they output the following:
ubuntu-desktop
  Installed: 1.325
  Candidate: 1.325
  Version table
*** 1.325 0
         500 httpgb.archive..ubuntu.com/ubuntu/ trusty/main i386 Packages
         100 /var/lib/dpkg/status

So, encouraged by this positive looking state, I went to the next step:
DISPLAY=:0 dconf reset -f /org/compiz
unity --reset-icons  
The unity  --reset-icons returned the following:
WARNING: no DISPLAY variable set, setting it to :0
stop: Unknown job: unity-panel-service
compiz (core) - Info: Loading plugin: core
start Unknown job: unity-panel-service
compiz (core) - Info: Starting plugin: core

But  then, oh no! the system seems to hang, with a flashing underscore in  column1 of the next line on the terminal display. That was about 20 mins  ago, in the meantime I have typed this in and it still seems to be in a  hang state. I suspect I'll need to disconnect the power supply to force  a reboot, but before that I'll await your sage advice if that's OK with  you.

---

### Post by Bashing-om on 2014-12-03
wamses2; Humm;

I hate when I have to say " I do not know" !
We did set the display " DISPLAY=:0 dconf reset -f /org/compiz "
I can not imagine why the system responds:
> 
WARNING: no DISPLAY variable set, setting it to :0

Someone enlighten us, please .

As to " with a flashing underscore in column1 " :
Is there a hidden window behind the present display ? - seems maybe the system is awaiting a response from some where ? - 
 If there is nothing else going on, in order to get back to the terminal, try:
key combo ctl+c
Failing that to stop the Xserver try:
ctl+alt+delete
IF even that fails, gracefully shut the system down:
alt+SysRq+rseiub ; slowly
-----------------
In the meantime, I am doing the homework, see if I can learn what might be taking place.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-12-03
wamses2; Hey ;

A bug, maybe ?
see:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1166765](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1166765)
and try the recommended work-a-round :
```

gsettings reset org.compiz.core:/org/compiz/profiles/unity/plugins/core/ active-plugins

```

I still be look'n to learn the why .

---

### Post by wamses2 on 2014-12-03
Eureka Bashing-om, free drinks for all Arkansasians at my house tonight!

To my surprise Ctrl/C worked and gave me a prompt
I applied the gsettings cmd, and immediately got back:
(process:3523):dconf-WARNING **:failed to commit changes to dconf:cannot autolaunch D-Bus without X11 $DISPLAY
So I then rebooted and from the login, the desktop was restored. I obviously haven't had time to use it yet to see if everything else is hanging together, but it looks very promising.

I'm sorry to put you to all of this trouble over a bug, unfortunately, my understanding of Ubuntu is pretty puny at the moment, and I tend to think it's something I've done that's caused the trouble, which in a way it was I guess. Anyway I am enormously grateful for your perseverance and unstinting help. For what it's worth, I have learned quite a lot over the last few days, I just hope I remember most of it.

I guess as this wasn't my original post, I can hardly mark it as solved, or can I? Anyone care to let me know the protocol I'd appreciate it

Meanwhile for my guru in Ozark, cheers!

---

### Post by Bashing-om on 2014-12-03
wamses2; Great !

For what it is worth, your issue had me going for a while ! It did keep me entertained .

Pleased it has now been worked out. (Never say never). And yepper, only the (O)riginal (P)oster can mark the thread. You have done your due to say something works !

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by Elven Decker on 2015-04-11
Had a similar problem - Desktop icons disappeared but still had a launcher to work with.  Tried all the recommended fixes, and finally got my icons back by rebooting into recovery mode and doing an fsck.

---

### Post by caughran on 2015-07-16
This problem exists in several threads. After trying most of the suggestions, I still had the problem on my underpowered Compaq laptop. Finally, after trying to repair ubuntu 5.4, I reinstalled it. Many adventures doing so, but it got done.

Problem still there! Wait a minute! If it's not in the root partition, there must be a file somewhere else that tells it to do bad things. So, I rename .config from /home/jim, and replace it with an empty folder. No help. Restore .config, and rename .local. No help. (Ubuntu was not completely happy without .local or .config, but it ran and did not have application top-bars or HUD or the like.)

I am going somewhat crazy. I decided to scorch and destroy. I formatted the /home partition and re-re-reinstalled ubuntu. Now it works. 

This leaves me some work. I have to restore /home/jim from backups (selectively, cleaning it up), and reinstall a flock of application programs. That will keep me busy longer than I want to be busy.

So, which file in /home/jim was the culprit?

---

### Post by BarryD9545 on 2015-09-09
i am continually replacing the Terminal and Computer icons every restart by dragging from the desktop folder to the desktop.

Anyone having any luck getting them to stay?

---

### Post by Geoffrey_Arndt on 2015-09-09
Just a quick question for Barry and perhaps a few of the other unfortunate souls that are having difficulties with misappearing icons, launcher, etc.

When you all "first" installed Ubuntu on your PC's . . . did you need to install "additional drivers" for  nvidia or amd/ati graphics?   And, if so, did you install those drivers from the official Ubuntu sources (via the Ubuntu Software Center or Synaptic) OR, did you go to nvidia or ati or another external (not Ubuntu) website to download and install the drivers? 

What I'm wondering is - - if drivers are installed outside of the normal Ubuntu "proprietary drivers" fetch and install process, then, new kernel updates (which happen many times a year), can break the video system and result in loss of normal displays, etc.

Maybe this is not the issue at all, but is worth a question because new users are just not used to getting drivers and software from with-in the system or OS.

---

### Post by mills2 on 2016-06-13
remove any application which was previously installed but is not in use
Like I use to get same screen I just removed unwanted nvidia Drivers and here My Ubuntu starts....

sudo apt-get remove --nvidia 

and here you go....

---

