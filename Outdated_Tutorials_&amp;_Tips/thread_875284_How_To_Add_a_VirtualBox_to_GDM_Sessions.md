---
title: "How To: Add a VirtualBox to GDM Sessions"
date: 2008-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by rossjman1 on 2008-07-30
This is a quick tutorial on how to add a VirtualBox session to GDMs Session menu. This can be useful for someone with a decently powered computer, looking for all the benefits of having a dual boot system without actually having to restart the computer to go into Windows/DOS/*nix. For the purposes of this tutorial I'm assuming you have already got a VirtualBox set up.

Open a terminal and navigate to /usr/share/xsessions. Now you need to create a new file here. My virtualbox is Windows XP, so I named it windows.desktop. To do this:
```
 sudo gedit windows.desktop
```
Paste this into the file:
```
[Desktop Entry]
Encoding=UTF-8
Name=**Windows XP Pro**
Comment=This session will run your VirtualBox
Exec=VirtualBox -startvm "**Windows XP Pro**"
Icon=
Type=Application
```
The stuff that is bold is what you need to change. Name is what the session is going to be called (GNOME, Failsafe GNOME, etc are all ready taken!). The most important part is the Exec command. This is the command that will be executed by GDM, you need to change the bold part to the Name of the VirtualBox you have installed (See pic).
[http://jeffantosh.googlepages.com/Screenshot-VirtualBoxOSE.png](http://jeffantosh.googlepages.com/Screenshot-VirtualBoxOSE.png)
Reboot gdm (ctrl-alt-backspace) and log into VirtualBox via GDM. To make VirtualBox fullscreen press the right control button and f at the same time.

---

### Post by zugol on 2008-08-27
Hi, 
It doesn't work for me, I have a bad agument number error message...

Any idee ?

Thanks

---

### Post by rossjman1 on 2008-08-27
It should still work, just click ok.

---

### Post by Crafty Kisses on 2008-08-28
It worked for me, thanks for that.

---

### Post by zugol on 2008-08-28
Unfortunatly no, he return to my default session "gnome"...

But I try your tips with the XBMC and it works perfectly !....

---

### Post by rossjman1 on 2008-08-28
If anyone knows how to get rid of those meaningless error messages, please share!

---

### Post by bornagainpenguin on 2008-08-30
> **zugol said:**
> But I try your tips with the XBMC and it works perfectly !....

Okay, I'll bite...what exactly did you do to accomplish that?

Also, does anyone know if it would be possible to do something like this with the Netbook Remix?  I have an ASUS EeePC 901 and would like to be able to switch between interfaces, if that's possible!

Another thought that just hit me--would it be possible to do this with other emulators?  For example Basilisk II the MacOS Classic emulator?

--bornagainpenguin

---

### Post by zugol on 2008-08-30
1-add this repo : deb [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main
2-install xbmc
3-go to /usr/share/xsessions
4-copy launcher gnome.destop as xbmc.desktop (as root)
5-edit it (as root) :
```

[Desktop Entry]
Encoding=UTF-8
Name=XBMC
Comment=Media Center XBMC
Exec=xbmc
Icon=
Type=Application

```

Now you can log on XBMC session.

(I created a new user called XBMC with this launcher as default session.)

But, doing this you cannot run anything except xbmc built-in apps (no firefox, no xmame...) Becaus it's not multitask... I dont't know if bender mameOx can be run like this.

I hope this can help you.

For more information go to [HTML]http://xbmc.org/forum/forumdisplay.php?f=52[/HTML]

---

### Post by zugol on 2008-08-30
1-add this repo : deb [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main
2-install xbmc
3-go to /usr/share/xsessions
4-copy launcher gnome.destop as xbmc.desktop (as root)
5-edit it (as root) :
```

[Desktop Entry]
Encoding=UTF-8
Name=XBMC
Comment=Media Center XBMC
Exec=xbmc
Icon=
Type=Application

```

Now you can log on XBMC session.

(I created a new user called XBMC with this launcher as default session.)

But, doing this you cannot run anything except xbmc built-in apps (no firefox, no xmame...) Becaus it's not multitask... I dont't know if bender mameOx can be run like this.

I hope this can help you.

For more information go to [http://xbmc.org/forum/forumdisplay.php?f=52]("http://xbmc.org/forum/forumdisplay.php?f=52")

---

### Post by Jose Catre-Vandis on 2008-08-31
Tried the OP's instructions under Xubuntu 8.04.1. Get the following error message:
```
X session: unsupported number of arguments
(3); falling back to default session
``` and am then returned to a normal session. 

FWIW, the command ```
 VirtualBox -startvm Windows
``` runs fine from a terminal window

EDIT

tried this under gnome-hardy too with same result

---

### Post by washeddang on 2008-08-31
I managed to get it working by replacing the command in Exec= with a script that launches my VM. By using VBoxSDL instead of VirtualBox or VBoxManage to launch the VM, GDM doesn't complain about the session lasting less than 10 seconds.

---

### Post by Jose Catre-Vandis on 2008-08-31
> **washeddang said:**
> I managed to get it working by replacing the command in Exec= with a script that launches my VM. By using VBoxSDL instead of VirtualBox or VBoxManage to launch the VM, GDM doesn't complain about the session lasting less than 10 seconds.

Any chance you could share the script?  ;)

EDIT

It's OK, a very simple script sorts this out.

Lets call it winxp.sh

```
#!/bin/bash
VBoxSDL -fullscreen -vm "Windows XP"
done
```

Then make it executable

then edit your "windows.desktop" file and replace the Vbox command on the Exec line with the path to the script
in my case
```
Exec=/home/jose/winxp.sh
```

Log Out and try again :)

EDIT

Anyone know how to get host interface networking to work when running Vbox from GDM? Can get NAT OK, but would prefer HIN...

---

### Post by calito on 2008-09-06
thanks jose. your script got my gdm virtualbox session working but how do you log out of this session safely

---

### Post by washeddang on 2008-09-06
When you shutdown the VM, it logs you out.

---

### Post by calito on 2008-09-06
oo ok. thanks washe

---

### Post by calito on 2008-09-06
oh  and if anyone doesnt know how to shutdown a virtualbox session the key combo is host+Q. Which is usually right control+Q

---

### Post by Jose Catre-Vandis on 2008-09-06
I just closed the OS in the virtual machine, this also logged me out

---

### Post by rossjman1 on 2008-09-08
For those of you who are still interested, my original tutorial does not work anymore. You need to create a bash script like so:
```
#!/bin/bash
su [your username here]
VirtualBox -startvm "Windows XP Pro"

```
An update apparently broke it, and you are no longer able to launch a VM owned by you as root.

---

### Post by calito on 2008-10-11
are you supposed to use this script with joses script. Ex:

Exec=/home/calito/your bash script

---

### Post by Jose Catre-Vandis on 2008-10-17
Yes, edit your desktop file to point to the script

And having just tested on an uptodate xubuntu hardy, find that my script still works without going "su" in the script:

```
#!/bin/bash
VBoxSDL -fullscreen -vm "Windows XP"
done
```

---

### Post by harpazo on 2008-10-20
Is there a way to make this work with VMWare Server?  I'm not using VirtualBox but I really want to login to my WMware Virtual Machine from GDM login.  If so, could you post exactly how to make this work?

Thanks so much.

Harpazo

---

### Post by Jose Catre-Vandis on 2008-10-23
Here is an example of the command line syntax to run a vmware virtual machine (i.e. put this into a terminal to open up a VM
```
vmrun start "/full/path/to/your/VirtualMachine/WindowsXPPro.vmx"
```

I guess you can try setting up a desktop file with this in it instead of the VBox command, or put it in a script and point the desktop file to it as above? Test you command line first to check that it works first.

Not tried it but don't see why it shouldn't work ;)

---

### Post by gogo242 on 2008-11-04
I've got this all working up to this point.  When I log into windows it show's up on my laptop screen and my attached monitor is blank.  I'd like to make it appear on my attached monitor...is there a way to make this happen?

---

### Post by pinklerose on 2008-11-09
It works for me but I want to do this as different user (using switch user). I create new user and got error that machine don't exist.
Next I create symbolic link
```
ln -s ~/.VirtualBox /home/newuser
```
and got another error. I think still another files need to be link to new user.
Any idea what files I need to link?

---

### Post by calito on 2008-11-10
make sure your .Virtualbox has the proper permissions to be used by another user. In the user that contains the virtualbox folder, do:

sudo chmod -R 777 .Virtualbox

this should work. correct me if the command needs revision

---

### Post by JohnFH on 2008-11-10
> **pinklerose said:**
> It works for me but I want to do this as different user (using switch user). I create new user and got error that machine don't exist.
Next I create symbolic link
```
ln -s ~/.VirtualBox /home/newuser
```
and got another error. I think still another files need to be link to new user.
Any idea what files I need to link?

Why do you want to run VirtualBox as a different user?  It is because the switch user command is convenient?  There are probably easier and better ways of making the switch convenient.

Please don't listen to anyone who tells you to 'sudo chmod -R 777' anything.  Please.

---

### Post by ale@forums on 2009-12-28
Hi everybody!

I am using an ubuntu 9.10 and i tried to follow the tutorial.
As result it just log me in like a normal gnome session:(....
Then i tried the hint of addin a script like told by [rossjman1]("http://ubuntuforums.org/member.php?u=44187") But the behaviour doesn't change....:confused:
To be precise i put th script in /home/myname/NameOfTheScript.sh
and then called it in the exec part adding the path /home/myname/NameOfTheScript.sh

Is it right?
What am i supposed to do ? Is there something to make it work on the 9.10?


Thank you guys....

---

### Post by calito on 2009-12-29
What exactly was the script you made?

---

