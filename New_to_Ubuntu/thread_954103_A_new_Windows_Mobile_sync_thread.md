---
title: "A new Windows Mobile sync thread"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by HittingSmoke on 2008-10-20
I had pretty much given up on syncing my HTC Apache with Ubuntu. All the threads I've read on the subject have really discouraged me.

I'm a total Linux noob but in learning Ubuntu I've heard talk of "porting" programs being tossed around. I know what this means but dont know the technical aspects of it in an OS case, only gaming.

I got [this]("http://www.pocketpcmag.com/cms/blog/5752/mac-loves-winmo") post on one of my news feeds and was wondering if it's possible to port a program like [this]("http://www.sync-mac.com/") from Mac to Ubuntu?

---

### Post by AdamWill on 2008-11-04
There is a Linux synchronization framework for Windows Mobile devices, and it does work well once you have it set up and working. I package the relevant stuff for Mandriva; I use a Windows Mobile phone as my main cellphone, and I sync it daily, it's simple and works reliably.

It's not as straightforward to set up on Ubuntu as it is on Mandriva as no official Ubuntu packager has yet taken an interest and integrated it properly into the Ubuntu repositories, but it should be possible. [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) is the place to start. The basic workflow is to get SynCE working to establish the basic communication with the phone; then create a partnership with the phone (there are various tools to do this, and you only have to do it once); then, once those two steps are done, use an opensync frontend - multisync-gui, kitchensync, or msynctool - to create a synchronization group containing the synce plugin and the plugin(s) for whatever you want to synchronize the phone with. Once that's done, each time you want to synchronize, all you have to do is connect the phone, run the opensync frontend, and tell it to synchronize that group.

The Mandriva documentation - [http://wiki.mandriva.com/en/2009.0_Synchronization](http://wiki.mandriva.com/en/2009.0_Synchronization) - may also prove useful to you in some way, so I link it here. Of course, you can't just follow it on Ubuntu. The page I linked earlier ([http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) ) should be your primary guide.

If you get stuck, you can ask for help in #synce on Freenode IRC. There's usually people around during European daytime hours.

---

### Post by HittingSmoke on 2008-11-09
> **AdamWill said:**
> There is a Linux synchronization framework for Windows Mobile devices, and it does work well once you have it set up and working. I package the relevant stuff for Mandriva; I use a Windows Mobile phone as my main cellphone, and I sync it daily, it's simple and works reliably.

It's not as straightforward to set up on Ubuntu as it is on Mandriva as no official Ubuntu packager has yet taken an interest and integrated it properly into the Ubuntu repositories, but it should be possible. [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) is the place to start. The basic workflow is to get SynCE working to establish the basic communication with the phone; then create a partnership with the phone (there are various tools to do this, and you only have to do it once); then, once those two steps are done, use an opensync frontend - multisync-gui, kitchensync, or msynctool - to create a synchronization group containing the synce plugin and the plugin(s) for whatever you want to synchronize the phone with. Once that's done, each time you want to synchronize, all you have to do is connect the phone, run the opensync frontend, and tell it to synchronize that group.

The Mandriva documentation - [http://wiki.mandriva.com/en/2009.0_Synchronization](http://wiki.mandriva.com/en/2009.0_Synchronization) - may also prove useful to you in some way, so I link it here. Of course, you can't just follow it on Ubuntu. The page I linked earlier ([http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) ) should be your primary guide.

If you get stuck, you can ask for help in #synce on Freenode IRC. There's usually people around during European daytime hours.

Thanks for the reply, but the idea I had was more towards the idea of full support, including installing programs. I thought maybe if this program could get working on Ubuntu it would be like a full featured interface for accessing your Pocket PC. I don't know how that works with Mac programs though.

---

### Post by smooth3006 on 2008-11-15
> **AdamWill said:**
> There is a Linux synchronization framework for Windows Mobile devices, and it does work well once you have it set up and working. I package the relevant stuff for Mandriva; I use a Windows Mobile phone as my main cellphone, and I sync it daily, it's simple and works reliably.

It's not as straightforward to set up on Ubuntu as it is on Mandriva as no official Ubuntu packager has yet taken an interest and integrated it properly into the Ubuntu repositories, but it should be possible. [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) is the place to start. The basic workflow is to get SynCE working to establish the basic communication with the phone; then create a partnership with the phone (there are various tools to do this, and you only have to do it once); then, once those two steps are done, use an opensync frontend - multisync-gui, kitchensync, or msynctool - to create a synchronization group containing the synce plugin and the plugin(s) for whatever you want to synchronize the phone with. Once that's done, each time you want to synchronize, all you have to do is connect the phone, run the opensync frontend, and tell it to synchronize that group.

The Mandriva documentation - [http://wiki.mandriva.com/en/2009.0_Synchronization](http://wiki.mandriva.com/en/2009.0_Synchronization) - may also prove useful to you in some way, so I link it here. Of course, you can't just follow it on Ubuntu. The page I linked earlier ([http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) ) should be your primary guide.

If you get stuck, you can ask for help in #synce on Freenode IRC. There's usually people around during European daytime hours.

why not just port the apps over from mandriva to ubuntu in the form of a deb install for us ? if i could get my wm pocket pc to sync fully id totally swith to linux.

---

### Post by lswb on 2008-11-15
> **smooth3006 said:**
> why not just port the apps over from mandriva to ubuntu in the form of a deb install for us ? if i could get my wm pocket pc to sync fully id totally swith to linux.

Wouldn't it really be the _ubuntu_ developers who should be doing this? :)

---

### Post by TomtheWombat on 2008-11-26
It is not that hard, but the documentation is outdated and misleading.  Here is my best job at a tutorial:

First you need to add better repositories.  You can get it to work with the standard packages in Ibex, but it doesn't work as smoothly.

> sudo nano /etc/apt/sources.list

And add this to the bottom of the file:

> deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) intrepid main

The necessary modules are already included in the Intrepid kernel.  Install the core libraries:

> sudo apt-get update
sudo apt-get install synce-hal librra0-tools librapi2-tools

Now connect your device to the computer and run:

> synce-pls

You should see a list of files on your device.  If you device is password protected, then you will get this error:

>  . WARNING **: synce_info_from_odccm: Failed to get a connection for <device_name>: Not authenticated, you need to call !ProvidePassword with the correct password. pls: Could not find configuration at path '(Default)'

You will need to install synce-trayicon or synce-kpm.

If you have the Gnome Network Manager running on Ubuntu, it will setup your device as the new default network connection. Check what ethernet device was given to your device with by running the following command in a terminal after you have connected your device:

> /sbin/ifconfig -a | grep 80:00:60:0f:e8:00  | cut -d " " -f 1

then add the next line to /etc/network/interfaces: 

> iface <interface of your device> inet dhcp

This will make Gnome Network Manager ignore the interface. Then restart the networking with the command: 

> sudo /etc/init.d/networking restart

You are going to need to disable any firewalls or configure them.  I don't know how to do this, but I have seen lists of the necessary ports.


Now you can install the synce-engine, opensync libraries, and multisync front-end.

> sudo apt-get install multisync-tools opensync-plugin-evolution opensync-plugin-synce

KDE users can use opensync-plugin-kdepim instead of the evolution2 plugin. There is no Thunderbird support in any stable opensync release.

Now we are going to need to setup synce and opensync.  The synce-sync-engine starts up automatically if you use the ppa repository.  The synce-engine should work without a config file, but you may want to download  the config file and edit it (it is no longer called config.xml):

> mkdir ~/.synce
wget -O ~/.synce/syncengine.conf.xml [http://synce.svn.sf.net/svnroot/synce/releases/0.11.1/sync-engine/config/config.xml](http://synce.svn.sf.net/svnroot/synce/releases/0.11.1/sync-engine/config/config.xml)
gedit ~/.synce/syncengine.conf.xml

You may to disconnect and reconnect your device before the changes are loaded.  Now you need to setup a sync profile on the device.  Windows Mobile can only handle up to two profiles, so you may need to delete a profile first using synce-delete-partnership.  To create a partnership use the following command.  (You can tell it to sync "Contacts,Calendar,Tasks,Files".  Delete the ones you don't want.)

> synce-create-partnership "Linux desktop" "Contacts,Calendar,Tasks,Files"

Now we need to setup a opensync.  You can use the `multisync0.90' program to setup, or you can create the group and add components via commandline:

> msynctool --addgroup synce-sync
msynctool --addmember synce-sync synce-opensync-plugin
msynctool --addmember synce-sync evo2-sync

You can edit the settings with multisync0.90.  To sync, press the button in multisync0.90 or do:

> msynctool --sync synce-sync

You can also press the sync button within activesync on the device.  By using the custom config, you can change it to popup a terminal on your computer when activesync asks for a sync instead of doing it in the background.

Good luck.  Sorry if the writing is hard to understand.  However, I think that the commands are straight forward.




A special thanks to [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) (that is outdated)

---

### Post by vbulash on 2008-12-23
> **TomtheWombat said:**
> 
...
Now we are going to need to setup synce and opensync.  The **synce-sync-engine starts up automatically if you use the ppa repository**.  The synce-engine should work without a config file, but you may want to download  the config file and edit it (it is no longer called config.xml):
...


Unfortunately, synce-sync-engine DOESN'T start up automatically :-(
The visible result of it is in the next console output:

```
vbulash@pc-vbulash:~$ synce-create-partnership "Ubuntu.WiTu" "Contacts,Calendar,Tasks" 

error: unable to connect to running sync-engine

Please ensure sync-engine is running before executing this command

```

Ok, I'll try to start synce-engine by hands and got the following:

```
vbulash@pc-vbulash:~$ synce-sync-engine
SynCE sync-engine starting up
2008-12-23 16:52:57,037 DEBUG syncengine : running main loop
2008-12-23 16:52:57,037 DEBUG syncengine : creating SyncEngine object
2008-12-23 16:52:57,063 DEBUG syncengine : installing signal handlers

```

That's all - infinite waiting for signal handlers...

Trying to use synce-engine in another shell:

```
vbulash@pc-vbulash:~$ synce-create-partnership "Ubuntu.WiTu" "Contacts,Calendar,Tasks" 
Creating partnership...

error: failed to create partnership
error: org.synce.SyncEngine.Error.Disconnected
```

Evidently, synce-engine doesn't working in any case :-(
What's up?

P.S. When started first time, synce-pls show me the folders of my WM6 device without any errors. When started second time and next (after all steps I wrote here), synce-pls show me the following:

```
vbulash@pc-vbulash:~$ synce-pls

** (process:7735): CRITICAL **: synce_info_from_hal: Failed to obtain property pda.pocketpc.name for device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.name on device with id /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00

** (process:7735): WARNING **: No devices connected to odccm
synce-pls: Could not find configuration at path '(Default)'

```

---

### Post by vbulash on 2008-12-23
+Little bit more...
After PC reboot I've got the following behavior of synce-pls:

```
vbulash@pc-vbulash:~$ synce-pls

** (process:6553): CRITICAL **: synce_info_from_hal: Failed to obtain property pda.pocketpc.name for device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.name on device with id /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00
Directory               2008-12-09 17:34:04  &#1051;&#1080;&#1095;&#1085;&#1099;&#1077;/
Directory               2008-12-10 08:35:56  DCIM/
Directory               2008-01-01 12:00:20  &#1064;&#1072;&#1073;&#1083;&#1086;&#1085;&#1099;/
Directory               2008-12-09 17:34:04  &#1052;&#1086;&#1080; &#1084;&#1077;&#1083;&#1086;&#1076;&#1080;&#1080; &#1079;&#1074;&#1086;&#1085;&#1082;&#1072;/
Directory               2008-12-09 17:34:04  &#1052;&#1086;&#1080; &#1092;&#1086;&#1090;&#1086;&#1075;&#1088;&#1072;&#1092;&#1080;&#1080;/
Directory               2008-12-09 17:34:10  &#1052;&#1086;&#1103; &#1084;&#1091;&#1079;&#1099;&#1082;&#1072;/
Directory               2008-12-08 15:50:12  DOIM/
Directory               2008-12-08 22:32:32  RSS Reader/
Directory               2008-12-09 17:34:24  &#1057;&#1083;&#1091;&#1078;&#1077;&#1073;&#1085;&#1099;&#1077;/
Archive           4673  2008-12-15 19:01:46  &#1056;&#1072;&#1089;&#1093;&#1086;&#1076;&#1099;.xlsx
Archive             43  2008-12-09 18:28:24  Mobipocket.lnk
Directory               2008-12-10 08:35:56  &#1052;&#1086;&#1080; &#1074;&#1080;&#1076;&#1077;&#1086;&#1079;&#1072;&#1087;&#1080;&#1089;&#1080;/

```

Yet another error, unfortunately...

---

### Post by TomtheWombat on 2008-12-23
Synce-engine needs to be running in order for synce-pls to work.  Apparently it doesn't start as soon as you plug in your phone, but any synce command should start up the engine automatically.

Your synce-pls is obviously working at least once.  That means that the engine started up.  Try adding a synce relationship right after a successful synce-pls.

Also make sure that you add the ppa repositories that I listed above.  It would not work for me with the intrepid packages!

Also you can only have maximum of 2 sync relationships on your mobile phone.  It will refuse to add another one.

---

### Post by TomtheWombat on 2008-12-23
Also may want to try downloading and editing the config file.

---

### Post by abu123 on 2009-01-03
hi i'm a newb ubuntu user.

trying to install Synce

unable to install get following msg

```
Package librra0-tools is a virtual package provided by:
  librra-tools 0.12-0ubuntu0~ppa1+intrepid
You should explicitly select one to install.
E: Package librra0-tools has no installation candidate
```

any help would be greatly appreciated
thanks

---

### Post by scorp123 on 2009-01-03
> **abu123 said:**
> unable to install get following msg

```
Package librra0-tools is a virtual package provided by:
  librra-tools 0.12-0ubuntu0~ppa1+intrepid
**[COLOR="Red"]You should explicitly select one to install.[/COLOR]**
E: Package librra0-tools has no installation candidate
```

any help would be greatly appreciated Do what the message says. :D

---

### Post by abu123 on 2009-01-03
I'm new to linux please give details i'm using intrepid.
> 
sudo ap-get.......(what)

---

### Post by scorp123 on 2009-01-03
> **abu123 said:**
> I'm new to linux please give details i'm using intrepid. The message above tells you precisely which package you need to install instead of the one you wanted. This has nothing to do with being "new to Linux". All you need to do is to read the message you posted yourself and act accordingly.

Your message said:
```
Package librra0-tools is a virtual package provided by:
  **[COLOR="Purple"]librra-tools[/COLOR]** 0.12-0ubuntu0~ppa1+intrepid
**[COLOR="Red"]You should explicitly select one to install.[/COLOR]**
E: Package librra0-tools has no installation candidate
``` Bingo. The package you wanted does not exist (anymore?). So you pick one of the alternate packages that were suggested to you, e.g. "librra-tools". I just checked and I know that the package is there in the repos.

As I said: do as the message suggests. It's all there. You only need to read it. ;)

---

### Post by abu123 on 2009-01-03
So installed in followoing order

sudo apt-get install synce-hal librapi2-tools
sudo apt-get install librra-tools

on **synce-pls** got error as below.

installed synce-kpm then tried above still same error.

so then installed **synce-trayicon** and again same error.

```

~$ synce-pls

** (process:7586): CRITICAL **: synce_info_from_hal: Failed to obtain property pda.pocketpc.name for device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.name on device with id /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00

** (process:7586): WARNING **: synce_info_from_odccm: Failed to get devices: The name org.synce.odccm was not provided by any .service files
synce-pls: Could not find configuration at path '(Default)'

```

Any pointers would be great. thanks

---

### Post by Ruyuk on 2009-01-03
Hmm... Have you tried Toast Titanium?

---

### Post by lswb on 2009-01-03
> **abu123 said:**
> hi i'm a newb ubuntu user.

trying to install Synce

unable to install get following msg

```
Package librra0-tools is a virtual package provided by:
  librra-tools 0.12-0ubuntu0~ppa1+intrepid
You should explicitly select one to install.
E: Package librra0-tools has no installation candidate
```

any help would be greatly appreciated
thanks

Unfortunately the synce tools for linux are not coherently organized. Different tools are needed depending on the version of CE, PPC, or WM running on your device. You may get better help by starting a new thread and including this information. I have an older ipaq running PPC 2002 that I have working successfully. If your device runs ppc 2002 or 2003 I may be able to help. For the more recent WM versions maybe someone else can share what they have learned.

---

### Post by clarkkentjt on 2009-01-05
I'm very close, but can't get any PIM info to sync over to my Samsung SCH-i910 with WM6.1. I'm only trying to get my contacts onto my cell phone, which I have 270 contacts in evolution. I'm running Ubuntu 8.10 Intrepid AMD. Here's where I'm at:

1. I've followed TomtheWombat's guide from [http://ubuntuforums.org/showthread.php?t=954103](http://ubuntuforums.org/showthread.php?t=954103) (thanks Tom)
2. I'm using the svm repos, which forces the uninstall of odccm btw.
3. I can see my windows mobile directories via terminal synce-pls and with GUI utility gpe-filemanager (found that suggestion on another forum entry). I can transfer files using gpe-filemanager.
4. Gnome Nautilus never displayed synce:/// (even with synce-gnomevfs plugin and after a reboot).
5. synce-trayicon only appears if I launch as sudo for the terminal.
6. I can create/delete partnerships using synce in the terminal, or via the synce-trayicon GUI. I can successfully delete software addons (ie. google search or google maps) Deleting a partnership has now removed all of my SCH-i910 initial default Verizon contacts. No big deal.
7. My mobile phone displays the correct partnership in activesync. I can initiate a sync and it says successful, but no contacts.
8. I've tried msynctool and multisync0.90, which will attempt to send the data (I see the debug of all the data), but it sits there waiting for opensync to connect to my mobile phone, but never does.
9. synce-kpm GUI shows correctly, but nothing happens when I click the sync Icon. It also can delete software addons.
10. Also FWIW: on my mobile phone, in the settings, connections, usb connection mode, I have 2 options: ActiveSync or Mass Storage/MyStorage. Interesting when I select 'mass storage' my mobile phone's memory card auto-mounts in Ubuntu as a storage device, but synce doesn't see the mobile phone. synce only sees my mobile phone device when set to 'activesync'.

Suggestions? Maybe it's a synce config.xml setting?
Any help is appreciated.
-Clark

---

### Post by TomtheWombat on 2009-01-10
abu123:

you HAVE to add the following sources to /etc/apt/sources.list because the synce packages in intrepid are a fustercluck.  Either that or don't use synce-hal only odccm.  You can't ahve **synce-hal AND odccm** at the same time.  That causes the can't find phone name (and other) errors.

```
deb http://ppa.launchpad.net/synce/ubuntu intrepid main
deb-src http://ppa.launchpad.net/synce/ubuntu intrepid main
``` 

Now apt-get update, upgrade, make sure that odccm is forced removed, and that you have the proper things installed:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove odccm
sudo apt-get install synce-hal librra0-tools librapi2-tools multisync-tools opensync-plugin-evolution opensync-plugin-synce
```

Now your syncing should work.  synce-sync-engine should start automatically for you.

You may have to delete partnership and then add it back, but I doubt it.

The packages included in Intrepid are broken for the new synce howtos. You have to PPAs.

---

### Post by Ehol on 2009-01-12
For those who wants to use the transport synce:/// in Gnome Nautilus, simply add

```
sudo apt-get install synce-trayicon synce-gvfs
```

Synce-gnomevfs doesn't work anymore. You need to use synce-gvfs to connect through synce transport.

Regards
Ehol

---

### Post by kwokyinc on 2009-01-14
> **TomtheWombat said:**
> It is not that hard, but the documentation is outdated and misleading.  

Dude, it works for me. I am using Dopod 818 pro running WM5. You and the synce team rock !!

---

### Post by kwokyinc on 2009-01-17
> **kwokyinc said:**
> Dude, it works for me. I am using Dopod 818 pro running WM5. You and the synce team rock !!

Hey, after installing synce for around 5 days. I found it quite unstable. It sometimes can connect to my Dopod (now HTC) device without any problem. But very often it cannot detect my device at all, and display the following error message when I input "synce-pls" in the terminal.

** Message: Device /org/freedesktop/Hal/devices/usb_device_bb4_bce_noserial_if1_serial_usb_6 not fully set in Hal, skipping
** Message: Device /org/freedesktop/Hal/devices/usb_device_bb4_bce_noserial_if0_serial_usb_5 not fully set in Hal, skipping
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'


Any idea what went wrong?

---

### Post by n2wz on 2009-01-18
> **TomtheWombat said:**
> abu123:

you HAVE to add the following sources to /etc/apt/sources.list because the synce packages in intrepid are a fustercluck.  Either that or don't use synce-hal only odccm.  You can't ahve **synce-hal AND odccm** at the same time.  That causes the can't find phone name (and other) errors.

```
deb http://ppa.launchpad.net/synce/ubuntu intrepid main
deb-src http://ppa.launchpad.net/synce/ubuntu intrepid main
``` 

Now apt-get update, upgrade, make sure that odccm is forced removed, and that you have the proper things installed:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove odccm
sudo apt-get install synce-hal librra0-tools librapi2-tools multisync-tools opensync-plugin-evolution opensync-plugin-synce
```

Now your syncing should work.  synce-sync-engine should start automatically for you.

You may have to delete partnership and then add it back, but I doubt it.

The packages included in Intrepid are broken for the new synce howtos. You have to PPAs.

I faced just the same issues like Abul123 did, nothing of the above helps.

This is what i get:
```
n2wz@n2wz-laptop:~$ synce-pls
** Message: Hal reports no devices connected
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'
```

---

### Post by gishaust on 2009-01-18
I get the exact same error  as TomtheWombat but i am using hardy

---

### Post by liquidarts on 2009-01-20
> **kwokyinc said:**
> Hey, after installing synce for around 5 days. I found it quite unstable. It sometimes can connect to my Dopod (now HTC) device without any problem. But very often it cannot detect my device at all, and display the following error message when I input "synce-pls" in the terminal.

** Message: Device /org/freedesktop/Hal/devices/usb_device_bb4_bce_noserial_if1_serial_usb_6 not fully set in Hal, skipping
** Message: Device /org/freedesktop/Hal/devices/usb_device_bb4_bce_noserial_if0_serial_usb_5 not fully set in Hal, skipping
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'


Any idea what went wrong?

I'm getting a similar response as kwokyinc when I run synce-pls;

** Message: Device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00 not fully set in Hal, skipping

My device is an iPaq 4700 running WM6.  I have not yet seen a file listing from the device.  Relating to others mentioning blacklisting and ipaq module or something, if it's any help, my output from lsmod has nothing referring to ipaq.

I'd be pleased to hear if anyone has had any positive experience with this problem.

---

### Post by kwokyinc on 2009-01-21
**[QUOTE=liquidarts;6583289] I'm getting a similar response as kwokyinc when I run synce-pls; [QUOTE]**


Hey, now I found that when I have such problem, then I simply disconnect the phone, reboot it, and then reconnect the phone. 

The Activesync in WM5 will try to search for connection and then after a while it will connect.

I haven't seen such problems in the last few days.

Liquidarts, hope this helps you.

---

### Post by kwokyinc on 2009-01-21
> **kwokyinc said:**
> **[QUOTE=liquidarts;6583289] I'm getting a similar response as kwokyinc when I run synce-pls; [QUOTE]**


Hey, now I found that when I have such problem, then I simply disconnect the phone, reboot it, and then reconnect the phone. 

The Activesync in WM5 will try to search for connection and then after a while it will connect.

I haven't seen such problems in the last few days.

Liquidarts, hope this helps you.


Bad bad, now my device won't sync again....not even after rebooting the device or the computer.....

Guess I have to declare the synce solution unstable for my device...

---

### Post by HittingSmoke on 2009-01-21
I've once again given up on this natively.

Right now I'm trying to put together a way to run an extremely stripped down XP install from a USB stick or through VM to sync. That way programs can be installed as well.

I've heard some shotty results from VM syncing, and I don't know how syncing from a USB drive install would work, or even if it's possible. I could get an XP install to under one or two GB I think but the only way I know of to install on a USB drive is using a PE and those don't generally have great hardware access.

If anyone wants to elaborate on this that would be great.

---

### Post by Trab on 2009-01-28
I wrote a guide a while ago on using SynCE with Ubuntu. it is very outdated, but I have heard reports that the methods still work (in a rudimentary way?)

I have a suggestion to those of you who are still struggling with this. I know its not a catch all solution, but it's what I have started doing, and I find it to be even MORE effective than trying to sync my device.

Firstly, I never bothered to sync PIM data. I keep all of that sort of data online, so I can access it via wireless (this won't work for everyone, I'm just fortunate to have wireless everywhere I use my PocketPC).

Secondly, SynCE's transport method for files is PAINFULLY slow. I've instead just started using a card reader and a SD (or CF) card to copy music, books, videos, and even .CABs to install my programs. 

There was a nifty program (I believe it was part of SynCE) called "Orange" or something similar, that allowed you to take the exe's you would run on Windows to install programs through active sync, and it would extract the CAB files needed to manually install. I found this to be much more effective.

Hopefully this helps. 

TomTheWombat, I have updated my guide based on yours. (credit is given =]) just thought you should know.


Cheers,
Trab

---

### Post by HittingSmoke on 2009-01-29
> **Trab said:**
> I wrote a guide a while ago on using SynCE with Ubuntu. it is very outdated, but I have heard reports that the methods still work (in a rudimentary way?)

I have a suggestion to those of you who are still struggling with this. I know its not a catch all solution, but it's what I have started doing, and I find it to be even MORE effective than trying to sync my device.

Firstly, I never bothered to sync PIM data. I keep all of that sort of data online, so I can access it via wireless (this won't work for everyone, I'm just fortunate to have wireless everywhere I use my PocketPC).

Secondly, SynCE's transport method for files is PAINFULLY slow. I've instead just started using a card reader and a SD (or CF) card to copy music, books, videos, and even .CABs to install my programs. 

There was a nifty program (I believe it was part of SynCE) called "Orange" or something similar, that allowed you to take the exe's you would run on Windows to install programs through active sync, and it would extract the CAB files needed to manually install. I found this to be much more effective.

Hopefully this helps. 

TomTheWombat, I have updated my guide based on yours. (credit is given =]) just thought you should know.


Cheers,
Trab

I should be getting (hopefully) my Touch Pro today and will have wireless anywhere. What program do you use to sync your contacts online and will it work with calendar and other data as well?

I'm very interested by this "Orange" thing but for now am focusing on getting Vbox to sync. Ill check out some of your suggestions later but instead of focusing on one or two features, me new aim is to have full functionality connecting my phone without having to reboot into a new OS install.

I'm fairly certain it CAN work with a Windows VM, it's just a matter of finding people who want to work on it who know what they're doing.

---

### Post by beansdad on 2009-02-09
Many thanks too those who have posted ways of getting synce to work. I had it working with Intrepid then lost it. Remove and install repeatedly still gave me an error with the evo2 plugin. Then ran "sudo synce-sync-engine" in a terminal, opened another terminal when this stopped at something like "installing signal handlers" and used that terminal to create the partnership, group and members, closed both terminals and re-ran the "sudo synce-sync-engine" with MDA Vario (HTC Wizard) funning WM5 attached and started Activsync. Opened Multisync Gui 0.9 (I think that's it's name) and sync worked.

Hope this helps - and desperately hope it will sync again!!

---

### Post by Trab on 2009-02-09
HittingSmoke: I use google for all of my data storage (e-mail, contacts, calendar) therefore, I can just access it all via a browser when I'm online. I am toying with the idea of using a program called OggSync to get contacts and Calendar to sync (you can already sync gmail via IMAP very simply). As for tasks, I use a website called RememberTheMilk. They have a syncing program, it costs 20$ I believe (this gets you a year of premium membership, which also means you can use the sync program), or you can use it through a web browser (what I do).

let me know if you find anything interesting. 

Cheers!


Edit: Just saw this on lifehacker. [http://www.google.com/mobile/default/sync.html](http://www.google.com/mobile/default/sync.html)

Google released a (beta) program that acts as an exchange server between pocketpc and google!

---

### Post by HittingSmoke on 2009-02-10
> **Trab said:**
> HittingSmoke: I use google for all of my data storage (e-mail, contacts, calendar) therefore, I can just access it all via a browser when I'm online. I am toying with the idea of using a program called OggSync to get contacts and Calendar to sync (you can already sync gmail via IMAP very simply). As for tasks, I use a website called RememberTheMilk. They have a syncing program, it costs 20$ I believe (this gets you a year of premium membership, which also means you can use the sync program), or you can use it through a web browser (what I do).

let me know if you find anything interesting. 

Cheers!


Edit: Just saw this on lifehacker. [http://www.google.com/mobile/default/sync.html](http://www.google.com/mobile/default/sync.html)

Google released a (beta) program that acts as an exchange server between pocketpc and google!

I saw that the other day and am going to toy around with it as soon as I get ActiveSync working on Vbox. Syncing isnt the only issue, I need the ability to install software and flash my device.

I've gotten to the point of getting my device listed under the Device Manager in my XP Guest but ActiveSync still won't recognise it. I've tried it with Enhanced Networking disabled on the device as well as USB2.0 disabled in Vbox and still no luck.

---

### Post by beansdad on 2009-02-11
Having got it to sync (see above) I can get a resync only by successfully getting synce-sync-engine to run as far as "installing signal handlers" (where it always hangs!) and then using Multisync 0.90. Thought about using Google but often don't have a signal for phone or internet connection when out & about.

Would still like something better but can't find it so far.

---

### Post by ha5dzs on 2009-02-26
Hi all!

I've been using Ubuntu for three years, and syncing w/ windows mobile was/is a big issue.


I'm using evolution, and i'm syncing my palm every day and i'm happy with it. Of course this is a windows mobile thread, so the main task is to sync Evolution with my windows mobile phone.

Of course you will need your device to connect the internet somehow...

Here is my flavor of the solution. You will need to use a completely different (SyncML based, instead of the exchange based) syncing framework for your device. You will need to have a SyncML based server at your hands, or if you don't have one, there are on the Net. The idea is funambol based.

Step by step:

1., log on to [www.scheduleworld.com]("http://www.scheduleworld.com"), and create an account.

2., Download Funambol sync client and install it on the PDA [ You can download the .cab file]("http://funambol.com/opensource/download.php?file_id=funambol-pocketpc-plugin-7.0.8.cab&_=d"), and set it up by using the tutorial [here.]("http://wiki.scheduleworld.com/wiki/Funambol_Clients_Interoperability")

Now you should be able to sync your device with the ScheduleWorld server. Please note that it requires internet connection, so if you use mobile broadband on your device, additional fees may apply from the provider (data draffic)

3., Download SyncEvolution from [here]("http://www.estamos.de/download/syncevolution/"), and set it up from the tutorial [found here.]("http://www.estamos.de/projects/SyncML/GettingStarted.html")


You will be able to sync evolution's PIM database (NOT emails) by typing the "syncevolution scheduleworld" command in a terminal (this will use internet connection too). When it's done, all the data will be synced to the ScheduleWorld server, so if you sync the windows mobile device, your stuff will be there.


i'm using this method for a month now, and I love it.

If you have other device (like iphone, blackberry, etc...) there might be a Funambol plugin to sync your PIMs.

You can have your own funambol server, but it's hard to get it working (at least it was for me).

If anybody has questions, please not be afraid to ask, and if you like the way it works, put it to Ubuntu docs.

bye!


[RIGHT]dzs[/RIGHT]

---

### Post by HittingSmoke on 2009-02-27
Ok everyone. I've got a solution working that does everything but run MSI installers from the PC (which can be extracted as CABs and installed) and installing custom ROMs.

This is **the most** full featured and complete sync suite I've found yet so here's the link to the guide.

[http://ubuntuforums.org/showthread.php?p=6808083#post6808083](http://ubuntuforums.org/showthread.php?p=6808083#post6808083)

---

### Post by ushills on 2009-02-27
Just out of interest google has added the ability to sync calendar and contacts via exchange activesync on WM devices as if using an exchange server.

[http://www.google.com/mobile/winmo/sync.html](http://www.google.com/mobile/winmo/sync.html)

This has solved all my sync problems as I use gmail hosted apps for my calendar.  All I need to do next is set this up in evolution as well.

---

### Post by rwslippey on 2009-02-28
I just wanted to reply here, your howto here works on ubuntu 8.10  however I have one problem that I can't get figured out....

I may have missed it somewhere however I need to upload files... such as word documents and pdf documents..... however I can't figure out how to do this. I have it set to upload files as described in the how to... just not sure where to put the files I need uploaded....

Thanks for the help....

Rob

---

### Post by Packrat73 on 2009-03-05
I just had one question (everything works, but the only thing I cannot find is the GPG key address so I dont get an error in Synaptic complaining about a public gpg.) Thanks for any help.

---

### Post by rwslippey on 2009-03-05
Hello again all.... Well heres the deal...


I have figured out how to upload files using a blue tooth dongle I purchased. 

The dongle was already set for this ability (required no action on dump user----- Mainly = ME!) witch was nice.

At the panel youll see a blue tooth icon, LEft click behold "browse files on device" send files to device...

Works on my treo 800 W and ubuntu 8.10   with the exception of the browseing for files....  go figure... but thats no big deal


AS far as syncing I found a way I like better....

I built a microsoft exchange server at home put my calendar on that and it upgrades great with Activesync.... Okay wait no ... that was too much 

Google mail uses Exchange servers for their calendar and email... setup you gmail account with calendar and then set up activsynce as desribed on their site..  

Mine will update the calendar and contact   as well as email

However be sure to note that the email and calendar are done serperatly...

Setup activesync to sycn and then setup your email  and that should get everything you bargain for.

Good luck  everyone let me know of new ideas and what it working...

Rob

---

### Post by gavrogirl on 2009-03-08
> **Packrat73 said:**
> I just had one question (everything works, but the only thing I cannot find is the GPG key address so I dont get an error in Synaptic complaining about a public gpg.) Thanks for any help.

Hello all, this is my first post and I'm, yes, a hopeless n00b in all things Ubuntu. Well, here goes.

In trying to synch my LG KS20 WM6.1 on Intrepid, I'm stuck at the outdated gpg key, both command line and Synaptic. After trying to find a newer key, I'm still stuck, and can't go any further. Sure, I've come into other problems with Synce, but if I can get around the gpg key I'll try to continue the tutorials to the letter. Any ideas on a newer key?

Thanks in advance for your help.

---

### Post by RichardCain on 2009-03-11
[I]And add this to the bottom of the file:

Quote:
deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) intrepid main
The necessary modules are already included in the Intrepid kernel. Install the core libraries:

Quote:
sudo apt-get update[/I]

I got this far, only to be told:

E: Type &#8216;bash:&#8217; is not known on line 10 in source list /etc/apt/sources.list

Que??

---

### Post by RichardCain on 2009-03-11
Don't bother replying to that last post, I've fixed it myself.  Haha - the things you learn!

---

### Post by RichardCain on 2009-03-11
Thank you so much, TomtheWombat!!  What a relief to finally get it up and running  :)

---

### Post by RichardCain on 2009-03-20
Arrrghh!!

Now it's all gone to rats again.  :(

Multisync tells me "plugin missing"  -  Which plugin??  How do I install the right one?

---

### Post by HittingSmoke on 2009-03-20
> **RichardCain said:**
> Arrrghh!!

Now it's all gone to rats again.  :(

Multisync tells me "plugin missing"  -  Which plugin??  How do I install the right one?

Try this

```
sudo apt-get install opensync-plugin-synce
```

This is the Sync CE plugin for Multisync

If that doesn't work try this guide [http://ubuntuforums.org/showthread.php?t=1081897](http://ubuntuforums.org/showthread.php?t=1081897)

---

### Post by gdiepen on 2009-03-30
Hi,

I have updated the Ubuntu instructions on our wiki ( [http://www.synce.org/moin/SynceInstallation/Ubuntu](http://www.synce.org/moin/SynceInstallation/Ubuntu) ) the other day.

It should contain the right instructions now. I am trying to prevent a wildspread of different guides that will not be updated in future anymore. We have a lot of people asking questions why SynCE is not working, while after some investigating it turns out to be that they were following out-of-date tutorials (i.e. wm2003 tutorials, while they have a wm6 device for example). Therefore, I would like to ask whether you can please report all problems that you find in the instructions, such that the SynCE wiki can be updated to reflect the correct way of installing it.

Kind regards,

Guido Diepen

---

### Post by radirk on 2009-05-12
I set it all up today and my 2 cents are thus:
1. Follow Guido's latest guide above (see point 5 thoug).
2. Install multisync0.90 from the repositories to have a gui.
3. Adding users and groups via
```
msynctool --addgroup synce-sync
msynctool --addmember synce-sync synce-opensync-plugin
```**multiple times** will lead to **multiple records** in evolution. You can use the multisync0.90 GUI to check for multiple groups and members with the same name. Then remove them all and add again as needed via the command line.
4. It might be a good idea to restart your machine after running 
```
sudo apt-get install synce-trayicon synce-gvfs
```especially if you get 
```
Nautilus cannot handle "synce" locations
```After the restart things should fall into place.
5. The sync command suggested by Guido
```
msynctool --sync synce-sync
```should be handled with care, it might be safer to use the multisync0.90 GUI as it will ask you for each duplicate record which one to keep, for example.

Cheers,

Dirk

---

### Post by green hot peppa on 2009-06-16
> **gdiepen said:**
> Hi,

I have updated the Ubuntu instructions on our wiki ( [http://www.synce.org/moin/SynceInstallation/Ubuntu](http://www.synce.org/moin/SynceInstallation/Ubuntu) ) the other day.

It should contain the right instructions now. I am trying to prevent a wildspread of different guides that will not be updated in future anymore. We have a lot of people asking questions why SynCE is not working, while after some investigating it turns out to be that they were following out-of-date tutorials (i.e. wm2003 tutorials, while they have a wm6 device for example). Therefore, I would like to ask whether you can please report all problems that you find in the instructions, such that the SynCE wiki can be updated to reflect the correct way of installing it.

Kind regards,

Guido Diepen

Hey Guido, I followed your guide and I still get the invalid GPG error.  When I look in the authentication Tab of Software Sources, it seems to point to the AWN team..... is that correct? here is the terminal output from your command:

hunter@Kids-Playroom:~$ sudo apt-key adv --recv-keys --keyserver subkeys.pgp.net 7D2C7A23BF810CD5
[sudo] password for hunter: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver subkeys.pgp.net 7D2C7A23BF810CD5
gpg: requesting key BF810CD5 from hkp server subkeys.pgp.net
gpg: key BF810CD5: "Launchpad PPA for Awn Testing Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

When I reload the package manager, I get this error:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D

Thanks for any help!

---

### Post by w2vy on 2009-06-21
I have gotten synce-pls to work but I get

```
synce-create-partnership "Ubuntu" "Contacts,Calendar,Tasks,Files" 
Creating partnership...

error: failed to create partnership
error: org.synce.SyncEngine.Error.Disconnected

```

synce-engine is running

```
tom@tom:~$ ps -ale |grep synce
1 S  1000 16564     1  0  80   0 -  5674 poll   ?        00:00:00 synce-sync-engi
tom@tom:~$ 

```

It gets the same thing when the phone is unplugged

ideas?
------------

This post helped me solve this problem [Install right packages]("http://ubuntuforums.org/showpost.php?p=6629627&postcount=14")

I have a T-Mobile Shadow (HTC) running WM6.1

> **Runamok said:**
> 
In Summary, you need to go System>Administration>Synaptic Package Manager and make sure all of the following programs are installed.

multisync-tools multisync0.90 opensync-module-python opensync-plugin-evolution opensync-plugin-google-calendar opensync-plugin-synce python-opensync synce-gnomevfs synce-gvfs synce-hal synce-sync-engine synce-trayicon


---

### Post by w2vy on 2009-07-05
Now this is strange...

What could be causing this?

When I enter calender items they show up both on my phone and my laptop fine.

But when I enter Birthdays and my anniversary they are 1 day off!

The phone is a day early!

I am running Windows Mobile 6.1 on a T-Mobile Shadow.

Anyone see this type of problem before?

tom

---

### Post by descent89 on 2009-09-19
> **green hot peppa said:**
> Hey Guido, I followed your guide and I still get the invalid GPG error.  When I look in the authentication Tab of Software Sources, it seems to point to the AWN team..... is that correct? here is the terminal output from your command:

hunter@Kids-Playroom:~$ sudo apt-key adv --recv-keys --keyserver subkeys.pgp.net 7D2C7A23BF810CD5
[sudo] password for hunter: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver subkeys.pgp.net 7D2C7A23BF810CD5
gpg: requesting key BF810CD5 from hkp server subkeys.pgp.net
gpg: key BF810CD5: "Launchpad PPA for Awn Testing Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

When I reload the package manager, I get this error:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D

Thanks for any help!

The VERY SAME problem. Anybody, an idea?

Thanks in advance.

---

### Post by gregb49 on 2009-10-03
> **descent89 said:**
> The VERY SAME problem. Anybody, an idea?

Thanks in advance.Following guido's post, I typed in ```
sudo apt-key adv --recv-keys --keyserver subkeys.pgp.net  B152F042D246C25D
```and got the result >  key D246C25D: public key "Launchpad PPA for SynCE" imported

---

### Post by fivercomp on 2009-10-28
After some research and testing to make it work in Karmic, here my findings:

To start synce-sync-engine automatically in conjunction with SynCE-Trayicon you need to do two things:

1. Copy the config.xml file from [http://synce.svn.sf.net/svnroot/synce/releases/0.11.1/sync-engine/config/config.xml](http://synce.svn.sf.net/svnroot/synce/releases/0.11.1/sync-engine/config/config.xml)  to your home/.synce/ folder. then change value of <AppendDefaultTimezone>0</AppendDefaultTimezone> to 1 in the XML file.

2. Change the configuration file for launching the engine via DBUS as soon as needed. The file "org.synce.SyncEngine.service" resides in the following directoy: /usr/share/dbus-1/services. You need to change the executable reference /usr/bin/synce-engine to the one used in ubuntu, synce-sync-engine.
Change the last line to: Exec=/usr/bin/synce-sync-engine --detached --logfile=~/.synce/sync-engine.log --once

Now you can use SynCe-Trayicon an click on "view device status" to create/ adapt a partnership. First remove the autocreated one and then create new one.

Follow all other steps on the installation guide of synce, [http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice](http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice) 

Good luck.
Fiver

---

