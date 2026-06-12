---
title: "[SOLVED] uninstall problem with Google Earth - help please"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by bwallum on 2008-11-28
Hi

I have downloaded Google Earth, the 4.3 beta version. I can change the download file giving it permission for myself. I used> cd Desktopbecause that is where it downloaded to and then> sudo chmod +x GoogleEarthLinux.binI then ran it with (DO NOT FOLLOW THIS COMMAND)sudo ./GoogleEarthLinux.bin

Yes the sudo was my undoing. I don't know why I did it but now I have Google Earth installed in root! The correct command should have been> ./GoogleEarthLinux.bin. the rest is then plain sailing.

However I would like to take out the root installed version. The main programme is in /opt/google-earth/ and the symbolic link is in /usr/local/bin/.

I have tried to chmod the google-earth folder and it won't let me.

Can you help me unistall the root installed Google Earth please?

---

### Post by silkstone on 2008-11-28
If all you want to do is delete the folders/files...

Open a terminal or Alt-F2

gksudo nautilus

You are then in the file manager as root and can delete what you want. ;)

---

### Post by vikramaditya on 2008-11-28
> **silkstone said:**
> If all you want to do is delete the folders/files...
yeah, but do dis be da same as uninstalling? :)

---

### Post by oldos2er on 2008-11-28
You've got it backwards. You should've made it executable with "chmod a+x GoogleEarthLinux.bin" then run it as "sudo ./GoogleEarthLinux.bin". Another crucial step is, immediately after installing when the installer program asks if you want to start GoogleEarth, you have to choose 'quit' or it will require you to run it as root forever after.

---

### Post by bwallum on 2008-11-28
Thanks, the gksudo nautilus sounds the way to go...

---

### Post by bwallum on 2008-11-28
I wish it was only backwards! It might make some sense then. Totally mashed is probably a better description! Sorry to confuse. The really annoying thing is I have it running on a similar machine perfectly. AMD64 with nvidia.

Can you tell me your interpretation of the steps please? I know it's do-able.

How about the default paths offered? /opt/google-earth/ for the install path and /usr/local/bin for the Binary path. Do you just accept them?

Regards
Bob

---

### Post by silkstone on 2008-11-29
If you enable the Medibuntu repository, Google Earth is in it and you can install from Synaptic - much easier!

---

### Post by gandaran on 2008-11-29
I believe there's a un-install script somewhere in the google earth installed files, look for it and run the script, if you can't find it then the only way out is deleting all google earth files
use synaptic to install google earth (add the medibuntu repo [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to get google earth) this way you can easyly remove it with synaptic too.
google earth is always installed in root file system

---

### Post by oldos2er on 2008-11-29
> **bwallum said:**
> 
Can you tell me your interpretation of the steps please? I know it's do-able.

How about the default paths offered? /opt/google-earth/ for the install path and /usr/local/bin for the Binary path. Do you just accept them?

Regards
Bob

 My Interpretation of the steps:

 Download GoogleEarthLinux.bin. If you use Firefox and you haven't changed its default settings, this will put GoogleEarthLinux.bin on your desktop.

 Open a terminal, run "cd Desktop".

 Run "chmod a+x GoogleEarthLinux.bin"

 Run "sudo ./GoogleEarthLinux.bin". I accept the default directories it creates, but there's no need to.

 Exit the installer when, at the end of the process, it asks you to either quit or start GoogleEarth.

 That's it. I've used these same steps on each version of Ubuntu since 7.04, and have not had problems.

---

### Post by oldos2er on 2008-11-29
> **gandaran said:**
> I believe there's a un-install script somewhere in the google earth installed files, look for it and run the script, if you can't find it then the only way out is deleting all google earth files

 Yes, if you used GoogleEarth's installer, you can run /opt/google-earth/uninstall as root. The command would look like "sudo /opt/google-earth/uninstall".

---

### Post by paultag on 2008-11-29
My issue with Google Earth was that it failed to uninstall on my system ( x86 64 ) because the uninstaller did not see that as an arch...

I would purge files by hand

Cheers,
Tag

---

### Post by bwallum on 2008-11-29
Thanks for that Ann. Is this good for AMD64bit?

Progress made so far is:
I can Install GoogleEarthLinux.bin but it ends up as root. It does fully run however if I log on as root.
I can install from Medibuntu repos the googleearth-4.2 and it works as user.
I can't install from Medibuntu repos the googleearth-4.3 version (much better than 4.2 btw). It fails at the point a 'tip of the day' screen is normally shown.

It has to be a permissions issue. the software definately runs. I just need it to run as me, not root.

I have followed your steps precisely. Is there a file that I have not purged that contains eula agreement info? I might need to get rid of it along with some configuration information possibly.

---

### Post by oldos2er on 2008-11-29
I don't know about the EULA, but GoogleEarth keeps its settings in ~/.googleearth . Open Nautilus, hit Ctrl-h, and you should see it.

---

### Post by bwallum on 2008-11-30
I have deleted and try to reinstall GE a number of times now. I probably have all the right files because I can run GE with the command 'sudo googleearth'. They are probably in the wrong place though, or at least have the wrong permissions.

It is purely a permissions thing so this thread has probably now served its use. I have opened another one called 'How do I change Google Earth user permissions?' at [http://ubuntuforums.org/showthread.php?t=998345]("http://ubuntuforums.org/showthread.php?t=998345")

---

### Post by Nux Muncher on 2008-12-11
I'm noob... shouldve installed from medibuntu repos ...shouldve never strayed from synaptic.  Anywaze, google earth only gives me a steady image of space withOUT earth.  I'd be willing to repair, if possible, or remove and go from repos with synaptic.  installed in usr/local but icons have a lock on them so can't delete...if that's an option.  please help

---

### Post by oldos2er on 2008-12-11
To uninstall GoogleEarth if it wasn't installed from the repositories, run "sudo /opt/google-earth/uninstall"

---

### Post by Nux Muncher on 2008-12-12
Hi Ann,

Tried your advice but got error: "Could not find a usable uninstall program. Aborting."

...and tried other stuff...as I said before... i'm noob...

[B]stav@stav-UBUdesktop:~$ cd usr
bash: cd: usr: No such file or directory
stav@stav-UBUdesktop:~$ cd..
bash: cd..: command not found
stav@stav-UBUdesktop:~$ dir
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos
stav@stav-UBUdesktop:~$ root
The program 'root' is currently not installed.  You can install it by typing:
sudo apt-get install root-system-bin
bash: root: command not found
stav@stav-UBUdesktop:~$ cd /usr
stav@stav-UBUdesktop:/usr$ cd opt
bash: cd: opt: No such file or directory
stav@stav-UBUdesktop:/usr$ cd /opt
stav@stav-UBUdesktop:/opt$ google-earth
bash: google-earth: command not found
stav@stav-UBUdesktop:/opt$ sudo /google-earth/uninstall
sudo: /google-earth/uninstall: command not found
stav@stav-UBUdesktop:/opt$ 
[/B]

..can u point me in right direction please?

Thanks in advance =)

---

### Post by bwallum on 2008-12-12
You need to be root to take out any google earth files that you may have littered around. you can do a lot ( but be careful) by opening nautilus as root. In a terminal enter```
gksudo nautilus
```What you may find is that when you do Places>Search for Files you can see hidden folders ('ctrl h' toggles them on and off) but nautilus (File Browser) can't see them. If you experience this take a note of the full path and then refer to [http://ubuntuforums.org/showthread.php?t=997873](http://ubuntuforums.org/showthread.php?t=997873)

EDIT only try this if you still have stuff left following the use of Uninstall as oldos2er suggests.

---

### Post by Nux Muncher on 2008-12-12
Hi,

Did what you recommended and browsed to /usr/local folder.  now what?  I'm sure I installed GE in an /opt directory somewhere.  I have real difficulty with file structure in ubuntu.  I don't get the logic.

I followed the thread you referred... so should I "find / | grep googleearth"?

When I entered "gksudo nautilus"  I get error message: 

[B]** (nautilus:11538): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


[/B]

... and an instance of nautilus opens up... so I should browse to problem?

---

### Post by oldos2er on 2008-12-12
Copy and paste the command I gave you in msg #16.

---

### Post by Nux Muncher on 2008-12-12
hi Ann,

I did copy/paste and responded in message 17.  Tried again and same problem.

Thanks

---

### Post by oldos2er on 2008-12-12
Can you post the output from this command:

 cd /opt && ls

---

### Post by bwallum on 2008-12-13
Sorry about the delay in replying...

What you need to do is first establish if you have any files there that will be a problem. these are all called googleearth something or other so you need to find out if you have any of these.

Do not use nautilus, it cannot find hidden (dot) files.

Use Places>Search for Files

'Look in Folder' should be set to File System
Then open 'Select more options', use the drop down to find Show hidden and backup files. Highlight the option and click Add. You should now see the option in black text above the drop down menu. Add is a very important step and got me going for a while.

In 'Name contains' type in googleearth. If you have any files with googleearth in then you will have to delete them.

Use the terminal and 'sudo rm' with full path and file name. Be careful and precise and do not use wild cards, simply remove all the googleearth files found.

That is you cleaned up sufficiently to then restart and reload googleearth from the repositories.

Let me know how you get on.

Good luck
Bob

---

### Post by oldos2er on 2008-12-14
"Do not use nautilus, it cannot find hidden (dot) files."

 Ctrl-H or 'View, Show Hidden Files' works in Nautilus.

---

### Post by bwallum on 2008-12-14
Agreed but I was pointing out that the search in File Browser (nautilus) can't find them. Try searching for any hidden (dot) file in both Search for Files and File Browser search.

In Places>Search for Files - make sure you have 'Select more options' on (triangle arriow pointing down and drop down options menu showing) and that you have Add-ed 'Show hidden and backup files'

In File Browser, (you can get there with Places>Documents) - Edit>Preferences>Views tab make sure 'Show hidden and backup files' is checked.

Set both to search 'File System'. Note results of your search.

The tricky thing is the novice thinks it is all the same programme just different windows or views. They are different and File Browser does not do what you might expect, hence my advice to use 'Search for Files'. I'm now bald working through this first time around!

---

### Post by oldos2er on 2008-12-15
I never noticed that about Nautilus search--I've always used catfish instead.

---

### Post by bwallum on 2008-12-15
Yeah, I think a lot is lost in translation from cli to gui. The old hands seem to know the programme names and then acknowledge that there is a gui that displays the programme. The new hands and Windows converts (me) are used to an integrated gui os where the programme names are never known and 'search' is 'search' whenever the os presents it.

I am just using all the default stuff so was quite surprised to find that 'search' varied from window to window and that the nautilus search in File Browser, probably the most used facilty in the operating system, simply does not do what it says.

I think I am at the point of getting deeper into Linux (by necessity) and will take a look at other options, catfish being the first as you were kind enough to suggest it.

---

### Post by darkhole on 2009-02-18
I don't know if this answers works for Google Eart v4, this realy works for uninstall Google Earth 5 installed using the .bin file like sudo in Ubuntu Linux:
[http://ubuntuforums.org/showpost.php?p=6753733&postcount=10](http://ubuntuforums.org/showpost.php?p=6753733&postcount=10)

---

