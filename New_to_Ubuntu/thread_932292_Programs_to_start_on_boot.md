---
title: "Programs to start on boot?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by fgn89 on 2008-09-28
I just installed firebird2.0-common. and firebird2.0-super using the synaptic package manager, from system tools.

After rebooting, I checked using System Monitor, and I couldn't find it, it should have a process name akin to firebirdxyz right?

Assuming it's not.. how do I make it start automatically on booting?

How do I start it manually? Clicking on fbserver in the bin dir doesn't seem to work. =\

Thanks in advance!

---

### Post by drs305 on 2008-09-28
You can go back to Synaptic, highlight the app and then click on Properties, Installed Files. There is probably a /usr/bin file which would contain the app start command. 

Depending on when you wanted it to start, you can add it in the System, Preferences, Sessions, Startup Programs section. 

If you need it to start earlier, you would have to deal with one of the system folders in /etc .

---

### Post by fgn89 on 2008-09-28
I did manage to find the .bin file, which is fbmgr.bin

But when I open it, it gives me the option to run, or run in terminal.

When I try to run it, nothing happens.

But if I run it in terminal..

[I]FBMGR> help


Usage:		fbmgr -command [-option [parameter]]

or		fbmgr<RETURN>
		FBMGR> command [-option [parameter]]

		shut  [-now]		shutdown server
		show			show host and user
		user <user_name>	set user name
		password <password>	set DBA password
		pidfile <filename>	file to save fbserver's PID
		help			prints help text
		quit			quit prompt mode

Command switches 'user' and 'password' can also be used
as an option switches for commands like start or shut.
For example, to shutdown server you can: 

fbmgr -shut -password <password>

or

fbmgr<RETURN>
FBMGR> shut -password <password>

or

fbmgr<RETURN>
FBMGR> password <password>
FBMGR> shut


FBMGR> start
no permissions to perform operation
[/I]

How'd I start it?

I don't know if this will help.. But in Windows, when I installed firebird.

It shows in the processes as fbserver.exe and fbguard.exe

I'm not able to open those two applications, trying to start them in the Terminal gives these messages.

[I]
fgn89@fgn89-desktop:/usr/lib/firebird/2.0/bin$ sudo start fbserver
start: Unknown job: fbserver
fgn89@fgn89-desktop:/usr/lib/firebird/2.0/bin$ sudo start fbguard
start: Unknown job: fbguard
[/I]

I think if I can startup these two, it would solve my dilemma.

---

### Post by fgn89 on 2008-09-29
I've just checked.. and the fbserver is an executable.

Do executables work the same in Linux as they do in windows?

---

### Post by drs305 on 2008-09-29
You don't run executables in linux the way you did in windows. You can't just click on an .exe or .bin file.

I could reply to your first query in general but I am not familiar with the firebird. I tried installing it via synaptic but did not get it started. I then uninstalled it and installed it in terminal so I could watch the commands:
```
sudo apt-get install firebird2.0-super
```

It installed but did not run as several online tutorials said it would. Next I ran the following:
```
sudo dpkg-reconfigure firebird2.0-super
```
At that point I got to an installation setup. I did not proceed any further as I didn't really want to install the app. But that should get you going.

I found a couple of tutorials. Please note that wherever they refer to *firebird2-super* you need to replace it with *firebird2.0-super*

Both the guides are a bit old but may provide you with some useful information:
[http://www.ubuntugeek.com/firebird-database-setup-on-ubuntu-linux.html]("http://www.ubuntugeek.com/firebird-database-setup-on-ubuntu-linux.html")
[http://www.firebirdsql.org/manual/ubusetup.html]("http://www.firebirdsql.org/manual/ubusetup.html")

Perhaps someone familiar with firebird will help you from here.

---

### Post by fgn89 on 2008-09-29
Wow.. I'm constantly amazed by the detail of the help you guys provide here.

Thanks a lot! 

That's exactly what I went through.

The tutorial doesn't help with the new installation. =\

The problem is, the help forums there isn't quite as responsive..

Eh, well, still, thanks. 

I don't think I'm gonna regret migrating to Linux. ^^

---

### Post by fgn89 on 2008-10-01
I thought it'd be a little pointless starting a new thread about this so..

I just want to know, whats the use of executable files in Ubuntu?

Is there some way to run them?

---

### Post by KIAaze on 2008-10-01
> **fgn89 said:**
> I thought it'd be a little pointless starting a new thread about this so..

I just want to know, whats the use of executable files in Ubuntu?


As far as I know, executables in Ubuntu have the same use as in windows. They're just usually called "binary" instead of "executable".

> In computing, an executable (file) causes a computer "to perform indicated tasks according to encoded instructions,"[1] as opposed to a file that only contains data. Files that contain instructions for an interpreter or virtual machine may be considered executables, but are more specifically called scripts or bytecode. Executables are also called "binaries" in contrast to the program's source code.

[http://en.wikipedia.org/wiki/Executable](http://en.wikipedia.org/wiki/Executable)

> **fgn89 said:**
> Is there some way to run them?
By changing the file properties to executable (check "allow executing file as program"), you can run it by double-clicking it.
However most executables are meant to be run in a terminal. This is almost certainly the case for firebird, unless it comes with a GUI.

Now concerning your problem with firebird:
I can't help you completely, but I can give you a few leads.

_Info on what's in the firebird2.0-super package:_
```
/etc/init.d/firebird2.0-super -> This is an init script to start/stop the firebird daemon, cf below

Those are all executables (binaries), you can run from the command-line:
/usr/bin/fbstat
/usr/bin/gbak
/usr/bin/gdef
/usr/bin/gfix
/usr/bin/gpre
/usr/bin/gsec
/usr/bin/isql-fb
/usr/bin/nbackup
/usr/bin/qli

```

The firebird2.0-common package just seems to be a dependency containing the basic libraries and docs.

I'm not sure if the following info is what you need, but if you're installing a daemon (program running in the background), which firebird is, you will likely find it useful one day.

_Enabling/disabling daemons/services:_

If you're lucky and the firebird packages are well done, you should be able to enable/disable the firebird service by just going to:
> System > Administration > Services

If it's not in there, you may have to deal the **sysVinit** and/or **upstart** systems. Upstart is what is gradually replacing sysVinit in Ubuntu.

I don't have time  (and don't know enough about it yet) to go into further details, but here are a lot of links about service configuration:
[http://ubuntuforums.org/showpost.php?p=35858&postcount=8](http://ubuntuforums.org/showpost.php?p=35858&postcount=8)
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)
[http://www.linux.com/feature/125977](http://www.linux.com/feature/125977)
[http://docs.kde.org/stable/en/kdeadmin/ksysv/index.html](http://docs.kde.org/stable/en/kdeadmin/ksysv/index.html)
[http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html](http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html)
[http://www.cyberciti.biz/faq/linux-define-the-runlevel-and-determine-which-runlevel-my-system-is-currently-in/](http://www.cyberciti.biz/faq/linux-define-the-runlevel-and-determine-which-runlevel-my-system-is-currently-in/)

_Tools:_
> rcconf
update-rc.d
chkconfig
ksysv
sysv-rc-conf
sysvconfig


P.S: I'm trying to control what gets run at startup on my PC. So this info is for me too. ;)

---

