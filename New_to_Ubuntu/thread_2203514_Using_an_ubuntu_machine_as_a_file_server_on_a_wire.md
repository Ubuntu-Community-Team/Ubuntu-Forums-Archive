---
title: "Using an ubuntu machine as a file server on a wireless network"
date: 2014-02-03
forum: New to Ubuntu
---

### Post by keith3 on 2014-02-03
Okay, this is the absolute beginner section, right? So I am a complete and total beginner and noob and all that. I'm that guy that makes you say "we all had to start somewhere".

OBJECTIVE: Use an old crappy netbook as a file server.

REASON: I have a Macbook, my wife has a Windows Laptop and we can't swap hard drives for a common source of files. I have an old netbook lying around and decided to use it to both reach my (above) objective, but also to learn a little about ubuntu. I didn't want to spend any money to reach this objective if possible.

STATS: My Macbook runs OSX 10.9.1. My wife's laptop runs Windows XP. The net book now runs Ubuntu 13.04. I have a wireless router that spreads interwebs all over my house and I have my mac, my wife's lappy, the netbook and a couple of phones and internet enabled devices connected to it.

PROGRESS: I have bumbled my way through installing ubuntu. Took ages and a couple of goes, but it seems to be working. I have haven't really done anything with it though as I still don't know what I'm doing. 

That mostly covers where I'm up to.

From here, I need some help because it's just not coming together for me. I also hope that this thread will help others in my position. I would love it if everyone treated me as some thawed out caveman that needs to be stepped through every single step.

So.... I'm not sure what the next step is. I want to be able to log onto the mac and see the hard drive hanging off the unbuntu machine so I can save stuff to it. I want the same to happen for the windows PC. 

Where do I go from here? 

Keith

---

### Post by devine.steve on 2014-02-03
Truth is Keith - there is a lot of learning, trial and error to get to where you want to go.The software you need to learn is Samba. It's a package on Ubuntu.

---

### Post by TheFu on 2014-02-03
Did you install desktop ubuntu or server ubuntu?
Which release?

Desktop would imply point-n-click and the instructions will be pages and pages with images.
Server means lots of copy/paste and if any issues come up, reading the errors and taking appropriate corrective action.

Here's some reading material while you figure those questions out:
* [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
* [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)
Samba is probably what you need due to Windows clients, though there are better file sharing methods for OSX and Linux.

You;ll need to know about networking enough to make each machine find the other machines on the network. That usually means a **static IP** for the server and modifying /etc/hosts files on each of the clients ... windows puts that file deep under WINDOWS somewhere.  Editing this file requires administrative rights on every OS these days.

Good luck!

---

### Post by keith3 on 2014-02-03
Okay, thanks, Steve.

I've gone to the search icon, typed in Samba, found the file, downloaded it and it's installing now. Hopefully.

I appreciate the help - I'll see how far I get and post my progress.

---

### Post by keith3 on 2014-02-03
Thanks, TheFu.

I tried to install server ubuntu and found it too confusing, so I went with the desktop ubuntu. The release I have says 13.04, but I have done all the instructions to update to 13.10, so it might be on that.

Where I'm really missing out is the big picture stuff. I don't really know what's missing.

For example, if you gave me instructions to make a cup of tea, you might say "boil the kettle, add tea bag to cup, fill with boiling water, drink". Then I might have a question such as "where is the button to turn on the kettle".

I hope you understand what I mean.

Anyway, I'm looking into Samba and see if I can work out how to use that.

Thanks!

---

### Post by devine.steve on 2014-02-03
Try this.
[URL="http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/"]http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/
or
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html)

[U]Just so you know when I first installed Samba it took me a VERY long time to get it to work. Linux is a wonderful thing, but it has a steep learning curve.
[/U][/URL]

---

### Post by TheFu on 2014-02-03
> **keith3 said:**
> Okay, thanks, Steve.

I've gone to the search icon, typed in Samba, found the file, downloaded it and it's installing now. Hopefully.

I appreciate the help - I'll see how far I get and post my progress.

Please, please, please use the package manager or PPA (extends the package manager) and **do not **directly download files to be installed manually. [http://blog.jdpfu.com/2009/10/06/easy-software-updates-and-patches](http://blog.jdpfu.com/2009/10/06/easy-software-updates-and-patches) explains, though some of the program names to be used have changed, the ideas are still accurate.

apt-get --> aptitude

---

### Post by keith3 on 2014-02-04
Guys, thanks so much for the responses. I have worked through a tutorial and changed config files and so on.

The problem I have now is that I don't know how to start it. If that's even what I need to do.....

How do I start Samba? I believe there's supposed to be a graphic UI, but I can't even find the file to run.

---

### Post by mastablasta on 2014-02-04
install server version as it will use a lot less resources than desktop version. and everythign will work a lot faster especially on netbook. have a look here for a nice how to with pics.: [http://askubuntu.com/questions/340965/how-do-i-install-ubuntu-server-13-04-step-by-step](http://askubuntu.com/questions/340965/how-do-i-install-ubuntu-server-13-04-step-by-step)

once you have server up and running install webmin to it so you can access it via web interface (another option is to install zentyal). i would suggest to keep server connected by wire instead of wireless if possible.

ok once you have web interface you need FTP server, then you can access server using various FTP programmes. i think it should work wiht windows explorer, but there are better ones such as Filezilla, WinSCP. i dont' know whqat is used in Mac, but probably its fileexplorer shoudl work as well.

another option is to install Zentyal initially. Zentyal is a GUI platform based on Ubuntu 12.04 LTS ment for home servers and small offices. it's easy to use and they have a free community version. Webmin is a GUI for server. post back when you reach this stage.

here is zentyal review so you can see how it looks and learn a bit about it: [http://distrowatch.com/weekly.php?issue=20140113#zentyal](http://distrowatch.com/weekly.php?issue=20140113#zentyal)
here are some webmin screenshots as well as demo of this interface: [http://www.webmin.com/demo.html](http://www.webmin.com/demo.html)

other easy web GUI server platforms include:
Openmediavault (based on Debian stable)
ClearOS (based on CentOS which is based on Redhat -> one of the most succesfull enteprise systems)

if you don't use a GUI then you will control the server via command line from another maschine using SSH (or in your case you can do it from laptop as well since oyu have the screen there). to use SSH in windows it's best to use ***putty*** terminal (free and opensource). Mac might allready have this funciton built in. maybe windows does as well...

---

### Post by keith3 on 2014-02-04
Mastablasta.

Thanks for the tips.

I didn't want to just do the server version of ubuntu because I wanted to find out a bit about the OS and learn something new. It won't get that much use, so should be fine running from desktop.

I downloaded Zentyal, but that overrides the OS doesn't it? Just turns the net book into a server?

I've put a lot of work into trying to get Samba to work so I'd at least like to try it.

Any ideas why I can't run it? Or if I should?

---

### Post by mastablasta on 2014-02-04
> **keith3 said:**
> I didn't want to just do the server version of ubuntu because I wanted to find out a bit about the OS and learn something new. It won't get that much use, so should be fine running from desktop.


you would learn more abotu the OS form server version, but desktop version will teach you more about interface. 
> 
I downloaded Zentyal, but that overrides the OS doesn't it? Just turns the net book into a server?

yup. a server with a GUI interface. 

linux is modular. think of it as Lego bricks. you have the base kernel upon which various modules and services run. you can add and remove as much as you want. you can create a version that will work well only on your specific mashcine (which was what apple was doing before and largely still is). so you can have the basic cli server and just add the web interface. or you can add or change a desktop environment (Unity, Gnome, KDE, XFCE, LXDE...) or add just a very light windows manager (like for example Icewm, openbox...). don't like the server packages you can remove them.

or you can choose a minimal install iso (net install -- [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)) and install base only and then add only modules you want or think you need. here is how that install looks like - how to with pics: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

> 

I've put a lot of work into trying to get Samba to work so I'd at least like to try it.

Any ideas why I can't run it? Or if I should?

Samba - it can work perfectly or not at all. i will guess here that windows 7 is the one giving you issues? make sure you are in same work group. you can use samba tree (command smbtree: [http://www.samba.org/samba/docs/man/manpages/smbtree.1.html](http://www.samba.org/samba/docs/man/manpages/smbtree.1.html)) to see what linux sees on network.

i have 2 Kubuntu's, 1 Openelec (debian based on Pi). wile i can access kubuntu and openelec from windows 7 i can access only kubuntu from windows xp. i've tried many things but can't get it to work (apparently windows xp additionally complicates some netowkr address stuff).

for windows 7 make sure you gave access to folder/disk to other users (you can arrange that with chmod command or in desktop right clicking and then properties) - you may need to open file manager with root access to do that. ```
**gksudo nautilus**
``` should do it.
- make sure folder is shared.
- make sure propper permissions are set for folder
- make sure make sure both maschines are in same "workgroup"

it should work then.

samba on desktop should work.

zentyal and similar will help you set sharing via GUI as well. i avoid manualy configuring via config files if at all possible.

edit: just saw you have win xp is that the one giving you issue in samba?

FTP or sFTP (secure ftp) is in my opinion better option for server. you can secure it and then access it from anywhere in the world.

---

### Post by TheFu on 2014-02-04
Respect to mastablasta, but much of that last response seems to be based on his difficulty with Linux and love of GUIs, not the facts around samba. He is trying to be helpful, that is certain. I worry that telling you to install a different OS release or install webmin will become a install a, b, c, d, e, .... Z, 1, 2, 3 .... exercise.

Samba works fine for Win8, Win7, WinXP, OSX, and other OSes.  It just needs to be properly configured, **like all Linux services**, by editing configuration files with a normal editor.  GUIs get in the way and never support all the settings you may want/need.  After modifying settings, most services need to be restarted.  
To restart (or start) the samba service, run **sudo restart smbd**.  Anytime a setting is modified in the /etc/samba/ directory, restarting samba is needed. "smbd" is the name of the service.  **sudo status smbd** will return the current status.  **sudo stop smbd** will do what you expect too.  This is NOT just for samba, but for any service on the machine. There are 20-4000 daemons on any Linux system, so having them all behave in a similar way is smart.  Also, these commands work for "desktop" or server Linux installs, so there isn't any need to learn the GUI way.

webmin ... ah ... webmin.  It is a web-app to control critical services. It dumbs down the settings and makes it possible for a web browser to modify. Scary. IMHO - if you can't figure out how to make a needed setting using the CLI, then it is unlikely you can properly secure the webmin application. Once setup, yes, it is easier for point-n-click admins. The danger happens when the admin doesn't understand what it is doing under the covers. Webmin gets hacked every day around the world because new-admins don't secure it. A few times there were bugs in webmin that allowed crackers in too, but that hardly ever happens. It is a well-regarded tool.

If something isn't working with any daemon, **check the log files**. It is possible to enable more logging output too, which will help determine the root cause for issues. Linux uses a centralized log system and puts those files in /var/log/ ... often admin-level authority is needed to view the logs - they contain sensitive data.

sftp completely rocks and I use it from all over the world (literally), but almost nobody should be using plain FTP anymore. It is not safe.  sftp is include with ssh which is a remote terminal that is secure. If you want most information about that, create a new thread, please.  This thread is about samba.

---

### Post by verymadpip on 2014-02-04
Hi there keith3.
I'm trying to get samba to work myself, so I'll be watching this thread.
Something I discovered: in one of the guides linked you're going to be asked to install smbfs, which won't happen - a replacement will be suggested (cifs I think).
It may be worth looking at this article:

[http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/](http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/)

Which also tells us how to install the funky GUI config tool.  (Although I'm trying to do this using the CLI & config files personally).
I've been at this for about a week, with 3 reinstalls,  & still can't get into the folders I want.  I can see the blighters from Ubuntu & Win 8.1, but I can't get into 'em. (That's my probem though, I don't want  to hijack your thread).  It's a good job this is a bit of a project for me & not mission critical :)

Good luck sir.

---

### Post by Morbius1 on 2014-02-04
Are you using 13.04 Ubuntu with Unity?

Open Nautilus > Right click your Public folder ( as an example ) > Select Sharing Options > check all the boxes:
[ATTACH=CONFIG]250089[/ATTACH]

You just created a samba share.

[COLOR=#0000cd]* Note: It's too late now but if you didn't have samba installed already this process would have installed the right version for you automatically.*[/COLOR]

You can create more complicated shares by installing the following package:
```
sudo apt-get install system-config-samba
```
But for simple shares creating them in Nautilus may be the only thing you need.

---

### Post by keith3 on 2014-02-04
TheFu - I'm with you 100%.

I have done this:

> sudo restart smbd
smbd start/running, process 2782
sudo status smbd
smbd start/running, process 2782

Not sure what to do next. Do I have to run Samba? Does it just happen? I've done all the config files... I don't know what's next.

I can't see the machine on the windows laptop, but I can see my machine on the Mac - but I can't connect to it.Where to from here?

Edit - Also, Morbius (sp?), I have made that samba share - but what do I do with it? How do I find it and connect? Why isn't it on the network?

---

### Post by Morbius1 on 2014-02-04
> I've done all the config files.
Now you're going to have to show us what you did. Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by keith3 on 2014-02-04
[COLOR=#000000][FONT=Arial]Testparm -s[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR]> [COLOR=#000000][FONT=Arial]Load smb config files from /etc/samba/smb.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Processing section "[homes]"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Processing section "[printers]"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Processing section "[print$]"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Loaded services file OK.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Server role: ROLE_STANDALONE[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][global][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	server string = %h server (Samba, Ubuntu)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	map to guest = Bad User[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	obey pam restrictions = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	pam password change = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	passwd program = /usr/bin/passwd %u[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	username map = /etc/samba/smbusers[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	unix password sync = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	syslog = 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	log file = /var/log/samba/log.%m[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	max log size = 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	dns proxy = No[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	usershare allow guests = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	panic action = /usr/share/samba/panic-action %d[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	idmap config * : backend = tdb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial][homes][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	comment = Home Directories[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	valid users = %S[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial][printers][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	comment = All Printers[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	path = /var/spool/samba[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	create mask = 0700[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	printable = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	print ok = Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	browseable = No[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial][print$][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	comment = Printer Drivers[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]	path = /var/lib/samba/printers[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]net usershare info --long[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]> [COLOR=#000000][FONT=Arial][Documents][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]path=/home/keith/Desktop/Documents[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]comment=[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]usershare_acl=Everyone:F,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]guest_ok=y[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR]

---

### Post by TheFu on 2014-02-04
Sorry - 
**sudo restart nmbd**
if it hasn't shown up yet.
nmbd is the "browsing" service.  It announces the share on the LAN.

Then using any network-ready file manager (MS-Explorer too), the shared directories will be visible.

I don't use non-LTS releases and don't usually have nautilus installed, so Morbius1's instructions aren't always an option.  OTOH, if you are on that version or later, DEFINITELY follow those instructions.

The shared folder needs to exist and be accessible to the users.  File permissions can put a damper on that, especially if the folders shared are in a HOME.

---

### Post by Morbius1 on 2014-02-04
Run the following command please and post the output:
```
smbtree
```
Does it show your own Ubuntu host and the documents share?

---

### Post by keith3 on 2014-02-04
@TheFu - "nmbd start/running, process 2586"

Although, that hasn't helped. I still can't connect to it.

:(

---

### Post by keith3 on 2014-02-04
smbtree:

> [COLOR=#58B442][FONT=Arial]WORKGROUP[/FONT][/COLOR]
[COLOR=#58B442][FONT=Arial]	\\KBFILESERVER   		KBFileServer server (Samba, Ubuntu)[/FONT][/COLOR]
[COLOR=#58B442][FONT=Arial]		\\KBFILESERVER\Documents      	[/FONT][/COLOR]
[COLOR=#58B442][FONT=Arial]		\\KBFILESERVER\keith          	Home Directories[/FONT][/COLOR]
[COLOR=#58B442][FONT=Arial]		\\KBFILESERVER\IPC$           	IPC Service (KBFileServer server (Samba, Ubuntu))[/FONT][/COLOR]
[COLOR=#58B442][FONT=Arial]		\\KBFILESERVER\print$         	Printer Drivers[/FONT][/COLOR]
[COLOR=#58B442][FONT=Arial]		\\KBFILESERVER\homes          	Home Directories[/FONT][/COLOR]

(Let me know if this is too much info or if I shouldn't be posting it)

---

### Post by Morbius1 on 2014-02-04
Let's focus on the Mac since Apple does networking correctly:
> but I can see my machine on the Mac - but I can't connect to it.
If you are talking about the [homes] share you won't be able to connect to it unless you access it a certain way:
Create a samba password for keith:
```
sudo smbpasswd -a keith
```
From the mac Connect to Server it should be like this:
Finder > Go > Connect to Server >Server Address:
```
smb://kbfileserver.local/keith
```
You may have to pass the username twice:
```
smb://keith@kbfileserver.local/keith
```

If you are talking about the documents share then that's something else. It's a guest accessible share and the mac should just be able to access it - unless you've encrypted your home directory of course.

---

### Post by TheFu on 2014-02-04
> **keith3 said:**
> @TheFu - "nmbd start/running, process 2586"

Although, that hasn't helped. I still can't connect to it.

:(

The testparm output isn't showing where you've added any shared directories beside the [homes] one.  Here is the stanza that I use here:

```
[homes]
  hosts allow = 127.0.0.1 192.168.1.0/24 192.168.1.27
  hosts deny = 0.0.0.0/0
  comment = Home Directories
  browseable = yes
  writable = yes
  create mask = 0644
  directory mask = 0755 
  valid users = %S
# ######## Special use options, not generally wanted.
#  follow symlinks = yes
#  wide links = yes
```
Don't forget to use **smbpasswd** to tell samba about any user accounts on the box - so the "valid users" works.
Without   *browseable = yes* in the section - it will not be announced. You'll have to _know_ where the share is located.
Things in [homes] are not usually shared with other users. 

I think you are close. Add the "browseable" setting and restart both smbd and nmbd. If that doesn't work, ... rerun testparms and smbtree and post the output again here.

I've never heard of the **net usershare info --long** command before. Don't understand how that interacts with samba.  The **smbtree** output is useful.  Also ay attention to what Morbius says.

---

### Post by Morbius1 on 2014-02-04
> The testparm output isn't showing where you've added any shared  directories beside the [homes] one.  Here is the stanza that I use here:
He has a documents share right here - created from Nautilus using the samba usershare process:
> [COLOR=#000000][FONT=Arial][Documents][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]path=/home/keith/Desktop/Documents[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]comment=[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]usershare_acl=Everyone:F,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]guest_ok=y[/FONT][/COLOR]
Share definition is in /var/lib/samba/usershares not /etc/samba/smb.conf

EDIT: A screenshot of the dialog box on OSX where you would put keith and the samba password you created for him on the Ubuntu server:
[ATTACH=CONFIG]250094[/ATTACH]

---

### Post by TheFu on 2014-02-04
> **Morbius1 said:**
> He has a documents share right here - created from Nautilus using the samba usershare process:

Share definition is in /var/lib/samba/usershares not /etc/samba/smb.conf

EDIT: A screenshot of the dialog box on OSX where you would put keith and the samba password you created for him on the Ubuntu server:
[ATTACH=CONFIG]250094[/ATTACH]

I take it that usershares are new?  Never heard of them before today. Guess I'm old school.  That command returns NOTHING on any samba servers here ... is this the Nautilus sharing stuff addon?

If I were doing it, I'd create a "[Documents]" stanza like this:
```
[Documents]
   path = /home/keith/Desktop/Documents
   hosts allow = 127.0.0.1 192.168.1.20/28  192.168.1.28
   hosts deny = 0.0.0.0/0
   comment =  Documents-Readonly
   browseable = yes
   guest ok = yes
   read only = yes
   directory mask = 0555
   file mask = 0444
```
Then **restart** both **nmbd** and **smbd**. Clearly the local network would need to be "allow" would need to be set - probably 192.168.0.0/24 is the most common, but we don't have enough data for that.

If that works, then I'd consider changing the    **read only = yes** setting and figure out exactly how to allow other users.  Honestly, for shares under /home/keith, I'd use the [homes] for read-write access. THAT works well and only the "keith" user would have write access. 

Still, I'd read carefully what Morbius writes.

---

### Post by Morbius1 on 2014-02-04
Usershare was added to Samba in Version 3.0.23 which places it around July 10, 2006 - I don't know if you consider 7+ years ago "new" ;)

It was a while after that that gnome created nautilus-share that allowed you to create it from the file manager.

[COLOR=#0000cd]**BTW**[/COLOR], the one thing you do not want to do is have 2 share definitions for the same path so if you create a share definition in smb.conf delete the one you created in Nautilus. You can do it graphically or by command:
```
net usershare delete documents
```
[COLOR=#0000cd]*Note: a nice thing about usershare is that you can create and delete a samba share via a one line statement in a terminal so it will work regardless of what DE you happen to be using - or no DE at all.*[/COLOR]

---

### Post by TheFu on 2014-02-04
> **Morbius1 said:**
> Usershare was added to Samba in Version 3.0.23 which places it around July 10, 2006 - I don't know if you consider 7+ years ago "new" ;)

When you get to my age, 7 yrs **is** new. ;) 

If I were staring over with samba today ... I'd definitely look into usershare. Actually, read the man page.

Is "usershare allow guests" enabled in the smb.conf [global] section?  According to the man page section for "net usershare" that is required for guest access. The default ACL is 'Everyone:R'.  Very interesting. Seems like it should work easy.

Can't see the [global] secton from here.

---

### Post by keith3 on 2014-02-04
> **Morbius1 said:**
> 
From the mac Connect to Server it should be like this:
Finder > Go > Connect to Server >Server Address:
```
smb://kbfileserver.local/keith
```
You may have to pass the username twice:
```
smb://keith@kbfileserver.local/keith
```

> **Morbius1 said:**
> 
[COLOR=#0000cd]**BTW**[/COLOR], the one thing you do not want to do is have 2 share definitions for the same path so if you create a share definition in smb.conf delete the one you created in Nautilus. You can do it graphically or by command:
```
net usershare delete documents
```

Okay, guys, I've done both of these and nothing seems to be different - I still can't connect.

Any further suggestions? :)

---

### Post by Morbius1 on 2014-02-04
On the Linux system does your name show up when you run this command:
```
sudo pdbedit -L | grep keith
```
EDIT: I should have shut down 2 hours ago so let me leave you with this.

If you name didn't show up with that command then you didn't add yourself to the samba password database:
```
sudo smbpasswd -a keith
```
I can't reproduce your symptoms with any of the Macs here but I'll try again tomorrow.

---

### Post by keith3 on 2014-02-04
Thanks for all your help, Morbius1 - I really appreciate it.

I ran the command and it resulted with "keith:1000:<My Full Name>"

Not sure what that means apart from my name is in the database.

---

### Post by devine.steve on 2014-02-04
well you should have a start up script in /etc/init.d/
I would look for a file labled smbd or samba 
SO:```
    /etc/init.d/smbd start      
```

Ha - I didn't see all the posts done since last night so this is kinda unneeded.

---

### Post by ally2 on 2014-02-04
If you want to get Samba up and running 

[http://www.howtoforge.com/ubuntu-12.04-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-12.04-samba-standalone-server-with-tdbsam-backend)

Good tutorial served me well forget the GUI stuff :) get hardcore 
You learn a hell of alot more 

I had Samba up and running first time using that

---

### Post by TheFu on 2014-02-05
> **keith3 said:**
> Thanks for all your help, Morbius1 - I really appreciate it.

I ran the command and it resulted with "keith:1000:<My Full Name>"

Not sure what that means apart from my name is in the database.

Can you **ping kbfileserver.local** from the other machines? Does it work?

---

### Post by Morbius1 on 2014-02-05
If you follow every HowTo that's been recommended here you will end up in a hole so deep you will never get out. There's a lot of voices here pulling you into different directions and I am very well adding to the confusion but here is what I propose:

[1] Post your entire smb.conf since I really don't know where you are any more. You can do that by issuing this command and posting it's output to the forum:
```
cat /etc/samba/smb.conf
```

[2] What I'm going to suggest is removing the [homes] share entirely. It's introducing a level of complexity that's just getting in the way at the moment.

[3] Then I want to add a line in the [global] section - right under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```
This is mainly for the Windows machine but it will help with the mac as well. [COLOR=#0000cd]*You can make Linux act just like an OSX samba server and force it's detection by the mac but that's another thread.*[/COLOR]

[4] Then I want to create a "Samba" directory away from your home directory.
```
sudo mkdir -p /Samba/Public
```
Then change permissions so that anyone can access it:
```
sudo chmod 777 /Samba/Public
```

[5] Since there's an anti-gui theme in this thread I want to create the simplest possible share at the bottom of smb.conf as the only share on this box:
```
[public]
path = /Samba/Public
guest ok = yes
read only = no
force user = keith
```

[6] The restart some services:
```
sudo service smbd restart
sudo service nmbd restart
```

[6] Then we'll see[COLOR=#0000cd] if the Linux box itself can access it's own samba share[/COLOR] with the following command in the terminal:
```
nautilus smb://kbfileserver.local/public
```

[7] If that works we can see if you can do the same thing from the mac using "guests" not "keith" as the "Connect As" user.

You can move on to more advanced settings once we get past this simple setup.

---

### Post by keith3 on 2014-02-06
[1] Entire smb.conf file:

```
[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# Sample configuration file for the Samba suite for Debian GNU/Linux.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# This is the main Samba configuration file. You should read the[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# smb.conf(5) manual page in order to understand the options listed[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# here. Samba has a huge number of configurable options most of which[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# are not shown in this example[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# Some options that are often worth tuning have been included as[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# commented-out examples in this file.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#  - When such options are commented with ";", the proposed setting[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#    differs from the default Samba behaviour[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#  - When commented with "#", the proposed setting is the default[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#    behaviour of Samba but the option is considered important[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#    enough to be mentioned here[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# NOTE: Whenever you modify this file you should run the command[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# "testparm" to check that you have not made any basic syntactic[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# errors.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# A well-established practice is to name the original file[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# "smb.conf.master" and create the "real" config file with[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# testparm -s smb.conf.master >smb.conf[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# This minimizes the size of the really used smb.conf file[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# which, according to the Samba Team, impacts performance[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# However, use this with caution if your smb.conf file contains nested[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# "include" statements. See Debian bug #483187 for a case[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# where using a master file is not a good idea.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]#======================= Global Settings =======================[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial][global][/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]## Browsing/Identification ###[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Change this to the workgroup/NT-domain name your Samba server will part of[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   workgroup = WORKGROUP[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# server string is the equivalent of the NT Description field[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   server string = %h server (Samba, Ubuntu)[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Windows Internet Name Serving Support Section:[/FONT][/COLOR]










[COLOR=#000000][FONT=Arial]# WINS Support - Tells the NMBD component of Samba to enable its WINS Server[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#   wins support = no[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# WINS Server - Tells the NMBD components of Samba to be a WINS Client[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   wins server = w.x.y.z[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# This will prevent nmbd to search for NetBIOS names through DNS.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   dns proxy = no[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# What naming service and in what order should we use to resolve host names[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# to IP addresses[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   name resolve order = lmhosts host wins bcast[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]#### Networking ####[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# The specific set of interfaces / networks to bind to[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# This can be either the interface name or an IP address/netmask;[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# interface names are normally preferred[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   interfaces = 127.0.0.0/8 eth0[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Only bind to the named interfaces and/or networks; you must use the[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# 'interfaces' option above to use this.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# It is recommended that you enable this feature if your Samba machine is[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# not protected by a firewall or is a firewall itself.  However, this[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# option cannot handle dynamic or non-broadcast interfaces correctly.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   bind interfaces only = yes[/FONT][/COLOR]











[COLOR=#000000][FONT=Arial]#### Debugging/Accounting ####[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# This tells Samba to use a separate log file for each machine[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# that connects[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   log file = /var/log/samba/log.%m[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Cap the size of the individual log files (in KiB).[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   max log size = 1000[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# If you want Samba to only log through syslog then set the following[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# parameter to 'yes'.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#   syslog only = no[/FONT][/COLOR]













[COLOR=#000000][FONT=Arial]# We want Samba to log a minimum amount of information to syslog. Everything[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# through syslog you should set the following parameter to something higher.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   syslog = 0[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Do something sensible when Samba crashes: mail the admin a backtrace[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   panic action = /usr/share/samba/panic-action %d[/FONT][/COLOR]








[COLOR=#000000][FONT=Arial]####### Authentication #######[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# "security = user" is always a good idea. This will require a Unix account[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# in this server for every user accessing the server. See[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# in the samba-doc package for details.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]security = user[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]username map = /etc/samba/smbusers[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# You may wish to use password encryption.  See the section on[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# 'encrypt passwords' in the smb.conf(5) manpage before enabling.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   encrypt passwords = true[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# If you are using encrypted passwords, Samba will need to know what[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# password database type you are using.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   passdb backend = tdbsam[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]   obey pam restrictions = yes[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# This boolean parameter controls whether Samba attempts to sync the Unix[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# password with the SMB password when the encrypted SMB password in the[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# passdb is changed.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   unix password sync = yes[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# For Unix password sync to work on a Debian GNU/Linux system, the following[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# sending the correct chat script for the passwd program in Debian Sarge).[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   passwd program = /usr/bin/passwd %u[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]*password\supdated\ssuccessfully* .[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# This boolean controls whether PAM will be used for password changes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# when requested by an SMB client instead of the program listed in[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# 'passwd program'. The default is 'no'.[/FONT][/COLOR]










[COLOR=#000000][FONT=Arial]   pam password change = yes[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# This option controls how unsuccessful authentication attempts are mapped[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# to anonymous connections[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   map to guest = bad user[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]########## Domains ###########[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Is this machine able to authenticate users. Both PDC and BDC[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# must have this setting enabled. If you are the BDC you must[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# change the 'domain master' setting to no[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   domain logons = yes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# The following setting only takes effect if 'domain logons' is set[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# It specifies the location of the user's profile directory[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# from the client point of view)[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# The following required a [profiles] share to be setup on the[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# samba server (see below)[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   logon path = \\%N\profiles\%U[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# Another common choice is storing the profile in the user's home directory[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# (this is Samba's default)[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#   logon path = \\%N\%U\profile[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# The following setting only takes effect if 'domain logons' is set[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# It specifies the location of a user's home directory (from the client[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# point of view)[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   logon drive = H:[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#   logon home = \\%N\%U[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# The following setting only takes effect if 'domain logons' is set[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# It specifies the script to run during logon. The script must be stored[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# in the [netlogon] share[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# NOTE: Must be store in 'DOS' file format convention[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   logon script = logon.cmd[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# This allows Unix users to be created on the domain controller via the SAMR[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# RPC pipe.  The example command creates a user account with a disabled Unix[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# password; please adapt to your needs[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# This allows machine accounts to be created on the domain controller via the[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# SAMR RPC pipe.[/FONT][/COLOR]










[COLOR=#000000][FONT=Arial]# The following assumes a "machines" group exists on the system[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]/var/lib/samba -s /bin/false %u[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# This allows Unix groups to be created on the domain controller via the SAMR[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# RPC pipe.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]; add group script = /usr/sbin/addgroup --force-badname %g[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]########## Printing ##########[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# If you want to automatically load your printer list rather[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# than setting them up individually then you'll need this[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#   load printers = yes[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# lpr(ng) printing. You may wish to override the location of the[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# printcap file[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   printing = bsd[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   printcap name = /etc/printcap[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# CUPS printing.  See also the cupsaddsmb(8) manpage in the[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# cupsys-client package.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   printing = cups[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   printcap name = cups[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]############ Misc ############[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Using the following line enables you to customise your configuration[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# on a per machine basis. The %m gets replaced with the netbios name[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# of the machine that is connecting[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   include = /home/samba/etc/smb.conf.%m[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Most people will find that this option gives better performance.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# for details[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# You may want to add the following on a Linux system:[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#         SO_RCVBUF=8192 SO_SNDBUF=8192[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#   socket options = TCP_NODELAY[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# The following parameter is useful only if you have the linpopup package[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# installed. The samba maintainer and the linpopup maintainer are[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# working to ease installation and configuration of linpopup and samba.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &[/FONT][/COLOR]













[COLOR=#000000][FONT=Arial]# Domain Master specifies Samba to be the Domain Master Browser. If this[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# machine will be configured as a BDC (a secondary logon server), you[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# must set this to 'no'; otherwise, the default behavior is recommended.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#   domain master = auto[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Some defaults for winbind (make sure you're not using the ranges[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# for something else.)[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   idmap uid = 10000-20000[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   idmap gid = 10000-20000[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   template shell = /bin/bash[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# The following was the default behaviour in sarge,[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# but samba upstream reverted the default because it might induce[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# performance issues in large organizations.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# See Debian bug #368251 for some of the consequences of *not*[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# having this setting and smb.conf(5) for details.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   winbind enum groups = yes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   winbind enum users = yes[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Setup usershare options to enable non-root users to share folders[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# with the net usershare command.[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Maximum number of usershare. 0 (default) means that usershare is disabled.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   usershare max shares = 100[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Allow users who've been granted usershare privileges to create[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# public shares, not just authenticated ones[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   usershare allow guests = yes[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]#======================= Share Definitions =======================[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Un-comment the following (and tweak the other settings below to suit)[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# to enable the default home directory shares. This will share each[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# user's home director as \\server\username[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial][homes][/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]comment = Home Directories[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]browseable = yes[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# By default, the home directories are exported read-only. Change the[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# next parameter to 'no' if you want to be able to write to them.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]read only = yes[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# File creation mask is set to 0700 for security reasons. If you want to[/FONT][/COLOR]










[COLOR=#000000][FONT=Arial]# create files with group=rw permissions, set next parameter to 0775.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   create mask = 0700[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Directory creation mask is set to 0700 for security reasons. If you want to[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# create dirs. with group=rw permissions, set next parameter to 0775.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   directory mask = 0700[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# By default, \\server\username shares can be connected to by anyone[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# with access to the samba server. Un-comment the following parameter[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# to make sure that only "username" can connect to \\server\username[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# The following parameter makes sure that only "username" can connect[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# This might need tweaking when using external authentication schemes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]valid users = %S[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Un-comment the following and create the netlogon directory for Domain Logons[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# (you need to configure Samba to act as a domain controller too.)[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];[netlogon][/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   comment = Network Logon Service[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   path = /home/samba/netlogon[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   guest ok = yes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   read only = yes[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Un-comment the following and create the profiles directory to store[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# users profiles (see the "logon path" option above)[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# (you need to configure Samba to act as a domain controller too.)[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# The path below should be writable by all users so that their[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# profile directory may be created the first time they log on[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];[profiles][/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   comment = Users profiles[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   path = /home/samba/profiles[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   guest ok = no[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   browseable = no[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   create mask = 0600[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   directory mask = 0700[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial][printers][/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   comment = All Printers[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   browseable = no[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   path = /var/spool/samba[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   printable = yes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   guest ok = no[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   read only = yes[/FONT][/COLOR]










[COLOR=#000000][FONT=Arial]   create mask = 0700[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# Windows clients look for this share name as a source of downloadable[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# printer drivers[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial][print$][/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   comment = Printer Drivers[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   path = /var/lib/samba/printers[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   browseable = yes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   read only = yes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]   guest ok = no[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# Uncomment to allow remote administration of Windows print drivers.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# You may need to replace 'lpadmin' with the name of the group your[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# admin users are members of.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# Please note that you also need to set appropriate Unix permissions[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# to the drivers directory for these users to have write rights in it[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   write list = root, @lpadmin[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# A sample share for sharing your CD-ROM with others.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];[cdrom][/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   comment = Samba server's CD-ROM[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   read only = yes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   locking = no[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   path = /cdrom[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial];   guest ok = yes[/FONT][/COLOR]





[COLOR=#000000][FONT=Arial]# The next two parameters show how to auto-mount a CD-ROM when the[/FONT][/COLOR]



[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR][COLOR=#000000][FONT=Arial]cdrom share is accesed. For this to work /etc/fstab must contain[/FONT][/COLOR]



[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR][COLOR=#000000][FONT=Arial]an entry like this:[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]# The CD-ROM gets unmounted automatically after the connection to the[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]#[/FONT][/COLOR]


[COLOR=#000000][FONT=arial][/FONT][/COLOR][COLOR=#000000][FONT=arial][/FONT][/COLOR]






```

---

### Post by Morbius1 on 2014-02-06
I'm going to warn you - this is most likely the last post of the day for me.

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
Then add this line in blue:
> #======================= Global Settings =======================
[global]
## Browsing/Identification ###
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
**  [COLOR=#0000cd] name resolve order = bcast host lmhosts wins[/COLOR]**

Further down the file comment out ( place a # in front of a line ) all the [homes] share definition:
> # to enable the default home directory shares. This will share each
# user's home director as \\server\username
[COLOR=#0000cd]**#**[homes]
**#**comment = Home Directories[/COLOR]
browseable = yes
# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
[COLOR=#0000cd]**#**read only = yes[/COLOR]
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700
# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700
# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
[COLOR=#0000cd]**#**valid users = %S[/COLOR]
Then at the very bottom past all the other lines add the following share definition:
```
[public]
path = /Samba/Public
guest ok = yes
read only = no
force user = keith
```
Save smb.conf and in a terminal restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```

Now create the folder and change it's permissions by running these commands in sequence:
```
sudo mkdir -p /Samba/Public
sudo chmod 777 /Samba/Public
```
While still in the terminal see if you can access your own share:
```
nautilus smb://kbfileserver.local/public
```

If that was sucessfull then move to the mac and run connect to server using the same type of format: smb://kbfileserver.local/public. If you have an issue with that then do what TheFu suggested and ping the Linux box from the mac to make sure you you are in the same network:
```
ping kbfileserver.local
```

---

### Post by keith3 on 2014-02-06
Morbius1, thanks so much for your time. I can see our time zones are a bit of a problem but I appreciate your help, so I'll just post here as I have replies for you.

Long story short, I have done everything that you have asked of me and it all went well up until the Mac bit.

The ubuntu files page now has a connection to kbfileserver.local and that seems great. 

The Mac, however, just won't connect to it. It won't allow the connection to the folder, and the ping had the following result:

> *ping: cannot resolve kbfileserver.local: Unknown host*
Not quite sure where to go from here.....

*** STOP THE PRESS ***

Okay, it's actually worked. I went back tracked and double checked I had done everything - and I noticed that I had commented out the "browsable" bit. I changed it, saved the config file and restarted the services.

Then I tried to connect and couldn't. But then I noticed I had turned off the wireless on the ubuntu machine. 

I turned it back on, pinged - and it worked!!! Then I tried to make the connection and I now have the folder "public" sitting in my Finder window!!

:) - I'm a happy man.

I just need to have a look at the windows computer now to see if that will work.

---

### Post by keith3 on 2014-02-17
Okay, just got time to get back to this.

So far I'm able to see the ubuntu machine from my Mac and I've been able to put a folder up that I can see.

The next thing I need to be able to do is to make a harddrive that is plugged into the ubuntu machine visible on the Mac.

As above, we were able to build a new folder and give access to it, but I'm a little foggy on how I can plug in a hard drive and make that folder able to be connected to on the Mac.

Any help is appreciated.

---

### Post by Morbius1 on 2014-02-18
That kind of post is just going to produce another wave of potentially conflicting recommendations since you haven't told us:

[1] What does "harddrive that is plugged in" mean - a new internal drive? USB?
[2] Where is it being mounted?
[3] How is it being mounted?
[4] How is it formatted?
[5] How did you share it?
[6] What are the conditions of that share?

Without any of that it's just a guess so here's mine - just like you did the [public] share except change the path to wherever this "harddrive" is mounted and change it's share name.

---

### Post by PDA1 on 2014-02-22
I might be wrong about the following and the applicability to your situation but here's what I did;

- I needed to be able to access files from any computer in my house while I was in my house. Remote access wasn't an interest. Security issues? What? Me worry? 

I wasted 24 hours trying to get Samba to do something (anything!) and a whole mess of other programs (NFS, FreeNAS) written for people who know how to really use computers but can't explain it to regular people. There is so much garbage on the web about "how easy it is to set up a home server!" *Remember- Ubuntu is Linux for humans*.

My opinion is that if I can't solve a computer problem in 20 minutes then I shouldn't be trying to solve it. There's an easier way.

Finally, I deleted Samba and all the junk I had installed.

I then installed open-ssh

Now, I just access all of my other computers in Nautilus (or web browser) using "sftp://192.184.25.25/"  (those numbers are from ifconfig found on each of the machines and aren't any real numbers of my machines).

As to the security matters- alright, security is extremely important. So show me how to do it in simple to understand terms- not computer ease. Such as- now, "type this...."

Maybe that'll help you?

---

