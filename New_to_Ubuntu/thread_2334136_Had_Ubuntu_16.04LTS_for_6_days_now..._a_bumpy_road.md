---
title: "Had Ubuntu 16.04LTS for 6 days now... a bumpy road from windows 10"
date: 2016-08-16
forum: New to Ubuntu
---

### Post by nexhuntr on 2016-08-16
I guess first place to start is my system specs. Those can be found here
[https://www.frontierpc.com/computers/laptops/notebooks/notebook/acer/aspire-v3-112p/aspire-v3-112p-c1aq-notebook-nx.mrqaa.002-1028422725.html](https://www.frontierpc.com/computers/laptops/notebooks/notebook/acer/aspire-v3-112p/aspire-v3-112p-c1aq-notebook-nx.mrqaa.002-1028422725.html)

Yeah. I've had Ubuntu for 6 days now, installed from a USB, I've been having some fun with errors and random freezing. Wondering if anyone can help me out. I've been googling half the stuff but it seems like for every fix I've made, I get six more issues that pop up.

Anyways, this is a few of the error messages I get when I go to var/log/systemlog.1

```
Aug 15 08:42:13george-Aspire-V3-112P org.gnome.ScreenSaver[2621]: ** Message: Lostthe name, shutting down.
Aug 15 08:42:39george-Aspire-V3-112P systemd[1]: Starting Stop ureadahead datacollection...
Aug 15 08:42:39george-Aspire-V3-112P systemd[1]: Stopped Read required files inadvance.
Aug 15 08:42:39george-Aspire-V3-112P systemd[1]: Started Stop ureadahead datacollection.
Aug 15 08:43:02george-Aspire-V3-112P org.gnome.zeitgeist.Engine[2621]: /bin/sh: 1:/usr/bin/zeitgeist-daemon: not found
Aug 15 08:43:02george-Aspire-V3-112P com.canonical.Unity.Scope.LocalFiles[2621]: **(process:3195): CRITICAL **: file log.c: line 981: unexpected error:Error calling StartServiceByName for org.gnome.zeitgeist.Engine:GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Processorg.gnome.zeitgeist.Engine exited with status 127(g-dbus-error-quark, 25)
Aug 15 08:43:02george-Aspire-V3-112P org.gnome.zeitgeist.Engine[2621]: /bin/sh: 1:/usr/bin/zeitgeist-daemon: not found
Aug 15 08:43:02george-Aspire-V3-112P com.canonical.Unity.Scope.LocalFiles[2621]: **(unity-files-daemon:3195): CRITICAL **: file index.c: line 315:unexpected error: Error calling StartServiceByName fororg.gnome.zeitgeist.Engine:GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Processorg.gnome.zeitgeist.Engine exited with status 127(g-dbus-error-quark, 25)
Aug 15 08:43:04george-Aspire-V3-112P org.gnome.zeitgeist.Engine[2621]: /bin/sh: 1:/usr/bin/zeitgeist-daemon: not found
Aug 15 08:43:04george-Aspire-V3-112P com.canonical.Unity.Scope.Applications[2621]:(unity-scope-loader:3193): LibZeitgeist-CRITICAL **: Failed to createproxy for Zeitgeist daemon: Error calling StartServiceByName fororg.gnome.zeitgeist.Engine:GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Processorg.gnome.zeitgeist.Engine exited with status 127
Aug 15 08:43:04george-Aspire-V3-112P com.canonical.Unity.Scope.Applications[2621]:(unity-scope-loader:3193): LibZeitgeist-CRITICAL **: Unable toconnect to Zeitgeist daemon: Error calling StartServiceByName fororg.gnome.zeitgeist.Engine:GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Processorg.gnome.zeitgeist.Engine exited with status 127
Aug 15 08:43:04george-Aspire-V3-112P com.canonical.Unity.Scope.Applications[2621]:(unity-scope-loader:3193): unity-applications-daemon-WARNING **:daemon.vala:679: Error calling StartServiceByName fororg.gnome.zeitgeist.Engine:GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Processorg.gnome.zeitgeist.Engine exited with status 127
Aug 15 08:43:04george-Aspire-V3-112P com.canonical.Unity.Scope.Applications[2621]:(unity-scope-loader:3193): unity-applications-daemon-WARNING **:daemon.vala:1111: Error performing search '': Error callingStartServiceByName for org.gnome.zeitgeist.Engine:GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Processorg.gnome.zeitgeist.Engine exited with status 127
Aug 15 08:43:16george-Aspire-V3-112P dbus[2250]: [system] Activating via systemd:service name='org.freedesktop.hostname1'unit='dbus-org.freedesktop.hostname1.service'
Aug 15 08:43:16george-Aspire-V3-112P systemd[1]: Starting Hostname Service...
Aug 15 08:43:16george-Aspire-V3-112P dbus[2250]: [system] Successfully activatedservice 'org.freedesktop.hostname1'
Aug 15 08:43:16george-Aspire-V3-112P systemd[1]: Started Hostname Service.
Aug 15 08:43:18george-Aspire-V3-112P gnome-session[2752]: Nautilus-Share-Message:Called "net usershare info" but it failed: Failed toexecute child process "net" (Not a directory)
Aug 15 08:43:18george-Aspire-V3-112P org.gtk.vfs.Daemon[2621]: ** (gvfsd:2666):WARNING **: dbus_mount_reply: Error fromorg.gtk.vfs.Mountable.mount(): Failed to retrieve share list fromserver: Connection refused
Aug 15 08:43:18george-Aspire-V3-112P org.gtk.vfs.Daemon[2621]: ** (gvfsd:2666):WARNING **: dbus_mount_reply: Error fromorg.gtk.vfs.Mountable.mount(): Failed to retrieve share list fromserver: Connection refused
Aug 15 08:43:18george-Aspire-V3-112P org.gtk.vfs.Daemon[2621]: ** (process:3272):WARNING **: Couldn't create directory monitor onsmb://x-gnome-default-workgroup/. Error: The specified location isnot mounted
Aug 15 08:43:18george-Aspire-V3-112P org.gtk.vfs.Daemon[2621]: ** (process:3280):WARNING **: Couldn't create directory monitor onsmb://x-gnome-default-workgroup/. Error: The specified location isnot mounted
```

also it seems that [COLOR=#000000]gksudo nautilus doesn't want to work very well when I try to delete a few files that may be bugging the system when I've tried to change my ect/apt/sources.list.d files wondering how to solve that.

But I've been trying to run minecraft, and it regularly freezes. I have java, and I've tried to install the OpenGL drivers but it fails to install every time. But my system even without running minecraft freezes completely randomly and alt + SysRq + REISUB won't work. It even froze twice while I've been trying to type this out. And then it will be fine for like 8 hours. No idea what's causing the problem at this point even though I get all this in my system log.[/COLOR]

---

### Post by grahammechanical on 2016-08-16
Why are you trying to delete files from /etc/apt/sources.list.d/ ?

Is Ubuntu your first experience of using a Linux distribution? The specification says "Graphics Memory Accessibility: Shared." I take that to mean that the graphics adapter is sharing the system memory (RAM). I do not play games so I am not sure if shared memory is good or not so good for the playing of games.

I have just done a web search for "minecraft requirements." And this is what I get back

> GPU (integrated): Intel HD Graphics or AMD (formerly ATI) Radeon HD with OpenGL 2.1
GPU (discrete): Nvidia GeForce 9600 GT or AMD Radeon HD 2400 with OpenGL 3.1

Does the video adapter in that machine meet those minimum requirements? Can you run this command?

```
/usr/lib/nux/unity_support_test -p
```

This is what I see with 16.04 and the open source video driver (Nouveau) on my Nvidia GT 220. 

> graham@Ub1604:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 11.2.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Regards

---

### Post by nexhuntr on 2016-08-16
```
george@george-Aspire-V3-112P:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Bay Trail 
OpenGL version string:  3.0 Mesa 11.2.0


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes
```

That's what I see, so I take it that's a yes my computer can take Minecraft and my question about OpenGL. But why does my computer randomly freeze?

Oh and deleting files within the folder I had mentioned... I was attempting to use sudo nano to change my medibuntu.list which solved one of my problems. But in my negligence I created three files named nano.save.1,2,3 which keep popping up that the terminal keeps ignoring.

---

### Post by ian-weisser on 2016-08-16
> **nexhuntr said:**
> I was attempting to use sudo nano to change my medibuntu.list which solved one of my problems.

Medibuntu was shut down in 2013, and the old software in it is certainly not recommended for Ubuntu 16.04. Don't do it.
Using old or incompatible repositories is a very good way to add  software that will merely freeze or crash your system.

WARNING: Sudo and gksudo are very powerful commands. They remove the razor-sharp sword from the scabbard. They give you the power to wreak terrible damage upon your system and your data. They assume that you fully understand what you are doing.

Seems like you dived into the deep end of the pool. Ubuntu is not a Windows clone. It's very different. Your Windows skills and habits may be leading you down the wrong path.

Why did you add medibuntu?
What else did you add? Why?
What were you trying to accomplish when you introduced the freezing?
Did Minecraft run well on the same hardware under Windows?

---

### Post by nexhuntr on 2016-08-16
Well... before I even went for the switch I wanted to make sure I had all the same sort of programs available to me as I would with my Windows programs. And yes Minecraft was one of them. And yes... it ran fine for days on end.
    I was making my list of programs that I use which was, Office, steam, a youtube Downloader, Video/Audio converter, Torrent downloader, Music Player, CD/DVD burner, Movie player, E-sword, zip file, Auto-CAD, Java, One Drive, Google Drive, Chrome, Skype, and of course Minecraft.
    Most of these were already installed along with Ubuntu. For the rest I had to Google as to the commands to install them or the Ubuntu Equivelent.
     
    Kind of already getting the "Ok, what did you break?" Line.
    I'm really tempted to fall back into old 98 Windows habits where if ever there's a problem, backup, format, and re-install fresh.
     
    I settled for a lot of in-browser based options. Like One Drive, Google Drive as well as A youTube Downloader, and E-sword. I was half way through Installing steam when it froze, so I picked up where I left off and it never finished. VLC player offers a lot on video and Audio. And I haven't gotten as far to the CD/DVD burner just yet. Java and Minecraft was one of the first things, and went fairly easy. Chrome was tough going, and wasn't fun. It kept failing time and time again. After I reboted it was there.
     
    So... how in my list did I get Medibuntu? and if this is my problem, which I thought I already solved, how do I get rid of it? Because it looks more like I've got a Unity or screensaver issue

---

### Post by QIII on 2016-08-16
> **nexhuntr said:**
> So... how in my list did I get Medibuntu? 

Hello!

Did you download Ubuntu from Canonical's website or from a third party?

---

### Post by nexhuntr on 2016-08-16
I got Ubuntu right from Canonical's website, followed their directions to install it upon a USB flash using rufus. And of course I did this with a Windows system. Then wiped my hard drive of all partitions, formatted and began anew with Legacy as a boot option for Ubuntu because UEFI and it's options to get it to happen was just not happening for me.

I might have just solved my problem. Chrome
I re-installed Ubuntu fresh. And yes I checked to see if medibuntu was there... it wasn't.
I updated and waited... no freezing or crashes.
I install chrome and boom... freezes every time... I did some google searching and it seems it's using GPU rendering when available. Un-checked that in my chrome settings... So far so good. Let everyone know in a few hours

Nope... Problem not solved with a fresh install I simply left my computer to run and it froze up. I could not find in the log when it froze up or what caused it. So... Started to do some email this morning and got it to freeze up again. Getting these error codes.

```
Aug 17 07:24:40 Aspire-V3-112P-C1AQ gnome-session[2867]: (gnome-software:3137): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug 17 07:24:40 Aspire-V3-112P-C1AQ gnome-session[2867]: (gnome-software:3137): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug 17 07:24:40 Aspire-V3-112P-C1AQ dbus[2289]: [system] Activating service name='org.freedesktop.fwupd' (using servicehelper)
Aug 17 07:24:43 Aspire-V3-112P-C1AQ org.gnome.ScreenSaver[2718]: ** Message: Lost the name, shutting down.
Aug 17 07:24:44 Aspire-V3-112P-C1AQ org.freedesktop.fwupd[2289]: (fwupd:3280): Fu-WARNING **: Failed to coldplug: UEFI firmware updating not supported
Aug 17 07:24:44 Aspire-V3-112P-C1AQ dbus[2289]: [system] Successfully activated service 'org.freedesktop.fwupd'
Aug 17 07:24:44 Aspire-V3-112P-C1AQ systemd-timesyncd[1750]: Synchronized to time server 91.189.89.199:123 (ntp.ubuntu.com).
Aug 17 07:24:56 Aspire-V3-112P-C1AQ com.canonical.Unity.Scope.Applications[2718]: Error loading package indexes: Couldn't stat '/var/cache/software-center/xapian'
Aug 17 07:24:56 Aspire-V3-112P-C1AQ com.canonical.Unity.Scope.Applications[2718]: (unity-scope-loader:3429): unity-applications-daemon-CRITICAL **: daemon.vala:144: Failed to load Software Center index. 'Apps Available for Download' will not be listed
Aug 17 07:24:56 Aspire-V3-112P-C1AQ org.gnome.zeitgeist.SimpleIndexer[2718]: ** Message: Empty index detected. Doing full rebuild
Aug 17 07:24:57 Aspire-V3-112P-C1AQ gnome-session[2867]: ** (zeitgeist-datahub:3481): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Aug 17 07:24:58 Aspire-V3-112P-C1AQ dbus[2289]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Aug 17 07:24:58 Aspire-V3-112P-C1AQ systemd[1]: Starting Hostname Service...
Aug 17 07:24:58 Aspire-V3-112P-C1AQ dbus[2289]: [system] Successfully activated service 'org.freedesktop.hostname1'
Aug 17 07:24:58 Aspire-V3-112P-C1AQ systemd[1]: Started Hostname Service.
Aug 17 07:24:59 Aspire-V3-112P-C1AQ gnome-session[2867]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
Aug 17 07:25:00 Aspire-V3-112P-C1AQ dnsmasq[2812]: nameserver 192.168.137.1 refused to do a recursive query
Aug 17 07:25:01 Aspire-V3-112P-C1AQ org.gtk.vfs.Daemon[2718]: ** (process:3503): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
Aug 17 07:25:01 Aspire-V3-112P-C1AQ org.gtk.vfs.Daemon[2718]: ** (process:3495): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
```

Isn't this a problem with smb? Either that I'm lost

---

### Post by mastablasta on 2016-08-17
you are installing things in a wrong way. you should use ubuntu software center. 

chrome is installed by donwloading and running .deb package as i know. the rest of neede apps are in software center and plenty of them available.

minecraft - you need to install oracle java, then it should work with no issues at all. my son plays it on a much weaker old pc. for oracle java there is a good PPA on webupd8 website. add ti to repositories and java will apear in software center.
> 
Like One Drive, Google Drive as well as A youTube Downloader, and E-sword. I was half way through Installing steam when it froze, so I picked up where I left off and it never finished. VLC player offers a lot on video and Audio. And I haven't gotten as far to the CD/DVD burner just yet. Java and Minecraft was one of the first things, and went fairly easy. Chrome was tough going, and wasn't fun. It kept failing time and time again. After I reboted it was there.


google drive - there is an app to add it to nautilus (share folder with drive) and to connect to it i believe. for example: [http://www.linuxtechi.com/access-google-drive-in-ubuntu-16-04/](http://www.linuxtechi.com/access-google-drive-in-ubuntu-16-04/)

youtube downloader - add on is available in firefox. maybe in Chrome as well.
e-sword - don't know about this one but there is probably an alternative in software center if they do not have a linux version
video player - VLC, smplayer, mpv,mplayer2, miro, ... the list just goes on and on.
CD/DVD burner you have k3b.
Video/Audio converter- handbrake, if you want to edit videos there is also blender for profesionals or kdenlive. there are a few others.
Torrent downloader - what kind you want CLI ?, simple (transmission), complex (deluge, ktorrent...)
 Music Player - xampp, clementine, amarok...
zip file - ? it's installed by default. there should also be 7zip.
[COLOR=#ff0000]**Auto-CAD - **[/COLOR]the only one where i don't think there is a good alternative available.

MS office - alternative is libre office. MS office 2010 and less can be run relatively well using wine/playonlinux or crossover

Aside from Chrome there is also Chromium available in the repos, which is Chrome without the google added stuff. Chrome is based on Chromium in fact. Opera, vivaldi and many other borwser are also available. No IE though.

---

### Post by nexhuntr on 2016-08-17
*Groan* @ 4 postings "But thank you mastablasta got it the first time"
Also thank you for your footnote, the ubuntu-manual has been my bathroom reading material.

There's a lot of applications from Windows that I've really hated. IE, is one of them. I've always gone to an alternative.
But I've already figured out most of my faults the first time around. I spent a bit of time last night cleaning up and re-installing Ubuntu from scratch.
Woke up this morning with a frozen computer, and found out that the Ubuntu Software Center was gone. Had to get it back with reinstalling it through the terminal;
sudo apt-get install software-centerI know... most of the programs are already there through this, and it makes it a lot easier for a spoon like me to find and install without having to add outdated repositories.

---

### Post by QIII on 2016-08-17
Given the information you provided, did you think the very first response you got should have cleared everything up for you?

---

### Post by deadflowr on 2016-08-17
> *Groan* @ 4 postings "But thank you mastablasta got it the first time"
forum at fault.
fixed

---

### Post by nexhuntr on 2016-08-17
Thank you QIII and deadflowr
New to this forum too you know. What should I do next time I catch something like that?

---

### Post by deadflowr on 2016-08-17
> **nexhuntr said:**
> Thank you QIII and deadflowr
New to this forum too you know. What should I do next time I catch something like that?

Simple.
click the report post button at the bottom of one of the duplicate posts and simply write dupes or whatever else is wrong with the post.
we'll do the rest.

---

### Post by jetman350 on 2016-08-17
@nexhuntr, considering all your problems, I would highly suggest doing this:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Make sure you are Installing Chrome from the Official Google site, and make sure you are using a 64bit Installation DVD.  Google Chrome is no longer available for 32bit.

You might also want to post some Linux based Specs just to be sure of what you are running.  I've seen many post their specs, then we find they are wrong.  If you like you can run these in the Terminal and post the output here, I don't think staff will mind.
```
sudo lshw -short
```

and 

```
sudo parted -l
```

---

### Post by nexhuntr on 2016-08-18
I did post my specs almost first thing by adding the website of my laptop. That was this website
[https://www.frontierpc.com/computers/laptops/notebooks/notebook/acer/aspire-v3-112p/aspire-v3-112p-c1aq-notebook-nx.mrqaa.002-1028422725.html](https://www.frontierpc.com/computers/laptops/notebooks/notebook/acer/aspire-v3-112p/aspire-v3-112p-c1aq-notebook-nx.mrqaa.002-1028422725.html)
Here are the results of those codes
```
george@Aspire-V3-112P-C1AQ:~$ sudo lshw -short
[sudo] password for george: 
H/W path               Device     Class          Description
============================================================
                                  system         Aspire V3-112P (Aspire V3-112P_
/0                                bus            R2
/0/0                              memory         64KiB BIOS
/0/4                              processor      Intel(R) Celeron(R) CPU  N2940 
/0/4/7                            memory         32KiB L1 cache
/0/4/8                            memory         1MiB L2 cache
/0/6                              memory         24KiB L1 cache
/0/e                              memory         4GiB System Memory
/0/e/0                            memory         4GiB SODIMM DDR3 Synchronous 13
/0/100                            bridge         Atom Processor Z36xxx/Z37xxx Se
/0/100/2                          display        Atom Processor Z36xxx/Z37xxx Se
/0/100/12                         generic        Atom Processor Z36xxx/Z37xxx Se
/0/100/13                         storage        Atom Processor E3800 Series SAT
/0/100/14                         bus            Atom Processor Z36xxx/Z37xxx, C
/0/100/14/0            usb3       bus            xHCI Host Controller
/0/100/14/0/1          scsi2      storage        BUP Slim BK
/0/100/14/0/1/0.0.0    /dev/sdb   disk           1TB BUP Slim BK
/0/100/14/0/1/0.0.0/1  /dev/sdb1  volume         931GiB Windows NTFS volume
/0/100/14/1            usb2       bus            xHCI Host Controller
/0/100/14/1/2                     bus            USB2.0 Hub
/0/100/14/1/2/1                   communication  Atheros AR3012 Bluetooth
/0/100/14/1/2/2                   bus            USB 2.0 Hub
/0/100/14/1/2/2/3                 input          Comfort Curve Keyboard 3000
/0/100/14/1/2/2/4                 input          USB Optical Mouse
/0/100/14/1/3                     input          Touchscreen
/0/100/14/1/4                     multimedia     HD WebCam
/0/100/17                         generic        Atom Processor E3800 Series eMM
/0/100/1a                         generic        Atom Processor Z36xxx/Z37xxx Se
/0/100/1b                         multimedia     Atom Processor Z36xxx/Z37xxx Se
/0/100/1c                         bridge         Atom Processor E3800 Series PCI
/0/100/1c.1                       bridge         Atom Processor E3800 Series PCI
/0/100/1c.1/0          wlp2s0     network        QCA9565 / AR9565 Wireless Netwo
/0/100/1c.2                       bridge         Atom Processor E3800 Series PCI
/0/100/1c.2/0          enp3s0     network        RTL8111/8168/8411 PCI Express G
/0/100/1d                         bus            Atom Processor Z36xxx/Z37xxx Se
/0/100/1d/1            usb1       bus            EHCI Host Controller
/0/100/1d/1/1                     bus            USB hub
/0/100/1f                         bridge         Atom Processor Z36xxx/Z37xxx Se
/0/100/1f.3                       bus            Atom Processor E3800 Series SMB
/0/1                   scsi0      storage        
/0/1/0.0.0             /dev/sda   disk           500GB TOSHIBA MQ01ABF0
/0/1/0.0.0/1           /dev/sda1  volume         461GiB EXT4 volume
/0/1/0.0.0/2           /dev/sda2  volume         3979MiB Extended partition
/0/1/0.0.0/2/5         /dev/sda5  volume         3979MiB Linux swap / Solaris pa
george@Aspire-V3-112P-C1AQ:~$
```
```
george@Aspire-V3-112P-C1AQ:~$ sudo parted -l
Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  4172MB  extended
 5      496GB   500GB  4172MB  logical   linux-swap(v1)




Model: Seagate BUP Slim BK (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs




george@Aspire-V3-112P-C1AQ:~$ 
```


Lot of Text for a post
I think one of my problems at the beginning was that I installed Chrome from an non-trusted site with an outdated repository. Yes, I cleared all that up with a fresh install. After a day of use I've been getting strange freezing, I can play a video for a while, then poof it freezes, not all the time but some times, especially from my external hard drive which is connected for the moment. I also see that minecraft freezes after about 5 minutes of play. Wondering if this is having to update my graphics driver... seems like everyone else has that problem. And yet it's not part of the System Settings -> Software & Updates -> Additional Drivers. The only thing I see there is Firmware for CPU's and I've been seeing if that makes any difference, and it hasn't on or off.

---

### Post by Geoffrey_Arndt on 2016-08-18
Your notebook doesn't run a proprietary graphics chipset, hence no "additional drivers" required/needed . . . (e.g., Intel Graphics).   (the drivers are already baked into the linux kernel).    This system is not exactly a powerhouse.   Might consider experimenting and trying a slightly lighter flavor of Ubuntu like Xubuntu with XFCE desktop.

---

### Post by nexhuntr on 2016-08-18
Yeah it isn't a powerhouse... but it's quiet, no fan. I've been wanting to dump my hard drive for a SSD so it's quieter. I've already had to mod my mouse twice to reduce the noise of the clicking...
However... I'm currently downloading a fresh ISO, since the integrity check turned up a page of errors. I'm going to give that a try first. Then move on to a lighter flavor.

---

### Post by mastablasta on 2016-08-18
Firstly - i didn't see even one post, not even on page reload. :O

anyway,
> **nexhuntr said:**
> Yeah it isn't a powerhouse... but it's quiet, no fan. I've been wanting to dump my hard drive for a SSD so it's quieter. I've already had to mod my mouse twice to reduce the noise of the clicking...
However... I'm currently downloading a fresh ISO, since the integrity check turned up a page of errors. I'm going to give that a try first. Then move on to a lighter flavor.
this is what i wanted to say that your image is bad.

however, this doesn't explain the freezing when GPU is stressed. install psensor: [https://wpitchoune.net/psensor/](https://wpitchoune.net/psensor/)

might be a bit complicated but in the end you end up with nice graph and temp monitor. the freeze under stress sounds like overheating or it can also be a power management issue (incorrect drivers selected by OS?!).

you can also check logs found in /var/logs to see if there is anything crashing or any error reports when the freeze happened. there should be a log viewver available on the system. you can post last few lines here if you think they contain some interesting errors and not just normal reports.

---

### Post by nexhuntr on 2016-08-18
I thought about this... The graphical interface doesn't help one bit. I was tinkering with the settings of Minecraft to bring the demand down, and instead of it freezing up it ran for 10 minutes longer. It froze up when I brought on the graphical interface. Another note with this, is that the settings I had Minecraft on ran just fine when I had Windows 10. Don't know if that helps.
Checking the var/logs I was intrigued with that it froze while looking at the logs, nothing else running. I've noted some things other than the huge error list.

Aug 18 10:56:50Aspire-V3-112P-C1AQ gpu-manager[2303]: update-alternatives: error: noalternatives for x86_64-linux-gnu_gfxcore_conf
Aug 18 10:56:50Aspire-V3-112P-C1AQ systemd[1]: Started Detect the available GPUs anddeal with any system changes.
Aug 18 10:56:50Aspire-V3-112P-C1AQ systemd[1]: Starting Light Display Manager...

So... is this the driver log for the GPU?




Aug 18 10:56:52Aspire-V3-112P-C1AQ ModemManager[2295]: <info>  Couldn't findsupport for device at'/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0': not supported byany plugin
Aug 18 10:56:52Aspire-V3-112P-C1AQ ModemManager[2295]: <info>  Couldn't findsupport for device at'/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0': not supported byany plugin
Aug 18 10:56:52Aspire-V3-112P-C1AQ wpa_supplicant[2532]: dbus:wpa_dbus_get_object_properties: failed to get object properties:(none) none
Aug 18 10:56:52Aspire-V3-112P-C1AQ wpa_supplicant[2532]: dbus: Failed to constructsignal
Aug 18 10:56:52Aspire-V3-112P-C1AQ NetworkManager[2336]: <info> [1471539412.4150] device (wlp2s0): supplicant interface state:starting -> ready
Aug 18 10:56:52Aspire-V3-112P-C1AQ NetworkManager[2336]: <info> [1471539412.4152] device (wlp2s0): state change: unavailable ->disconnected (reason 'supplicant-available') [20 30 42]
Aug 18 10:56:52Aspire-V3-112P-C1AQ kernel: [   30.203492] IPv6: ADDRCONF(NETDEV_UP):wlp2s0: link is not ready

I'm not sure if what's causing the issues is the WIFI manager. I've got an old router that seems to glitch in and out of service. I've got a better one coming soon.


Aug 18 10:56:57Aspire-V3-112P-C1AQ org.gnome.ScreenSaver[2686]: **(gnome-screensaver:2896): WARNING **: Couldn't get presence status:The name org.gnome.SessionManager was not provided by any .servicefiles

This is the first error in a long list of errors. dealing with gnome.And ends with the one below.



Aug 18 10:57:04Aspire-V3-112P-C1AQ gnome-session[2802]: (gnome-software:2989):Gs-WARNING **: Failed to create permissionorg.freedesktop.packagekit.trigger-offline-update


Aug 18 10:57:08Aspire-V3-112P-C1AQ org.freedesktop.fwupd[2255]: (fwupd:3147):Fu-WARNING **: Failed to coldplug: UEFI firmware updating notsupported

So I don't have UEFI enabled, I'm running off of Legacy, I don't know if that's causing the problems.

---

### Post by Geoffrey_Arndt on 2016-08-18
first check that you don't have usb flashstick enabled in your sources since your image may be bad.

---

### Post by jetman350 on 2016-08-18
> [COLOR=#000000]I've got an old router that seems to glitch in and out of service.[/COLOR]

This is a problem, do you know how to install and use DownThemAll Firefox Extension?  Go ahead and install it and get the SHAsum of the iso you choose.  This is a Firefox Extension, so just go into firefox and add it, let ff restart and you should be ready. 

Once installed, DTA Should open as soon as you click on your download, again, insert the Checksum and choose the type of checksum in the Dropdown, SHAwhatever, or even the md5sum will work. 

It will pause if the connection stops, and resume when it is up again, this should guarantee you get a good download!  If not, all is a waste of time, with damaged files from a bad download you will be chasing problems forever.  If you need, help just ask.  

[https://addons.mozilla.org/en-US/firefox/addon/downthemall/](https://addons.mozilla.org/en-US/firefox/addon/downthemall/)

---

### Post by mastablasta on 2016-08-19
actually the easiest way (appart from replacing faulty router) is to use bit torrent to download the image. torrent checks file integrity during download. so once it is downloaded it should be the same as on server.

---

### Post by howefield on 2016-08-19
> **mastablasta said:**
> actually the easiest way (appart from replacing faulty router) is to use bit torrent to download the image. torrent checks file integrity during download. so once it is downloaded it should be the same as on server.

+1

[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

---

### Post by nexhuntr on 2016-08-20
So, after so much time, checking and double checking. I'm back up and running with some satisfactory numbers. So, I downloaded a lot of ISO's two right off of the website, both did not pass the md5sum test, however one passed for checking disc integrity in the boot option... What a waste of time... but now I can see how much skipping a step could result in failure and I wouldn't know. It took three torrents to get one to pass the md5sum test twice, and another five to get md5sum test twice and disc integrity check. I went all hard core to get a decent operating system USB. So far so good, I haven't put on chrome or Minecraft yet... I'm just going to take this slower than a decrepit grandmother with bubble gum on her walker

---

### Post by mastablasta on 2016-08-21
> **nexhuntr said:**
> So, I downloaded a lot of ISO's two right off of the website, both did not pass the md5sum test, however one passed for checking disc integrity in the boot option... What a waste of time... but now I can see how much skipping a step could result in failure and I wouldn't know. It took three torrents to get one to pass the md5sum test twice, and another five to get md5sum test twice and disc integrity check.

that is not possible. not unless you have a bad disk.

torrent checks md5sum while it downloads. 

also do not use wi-fi for download. wi-fi can loose packets or create errors. still torrent would have fixed them or redownload them pieces of the file.

---

### Post by The Cog on 2016-08-21
> that is not possible. not unless you have a bad disk.
A bad disk could explain the freezing too. My PC tends to go through a period of intermittent freezes, anything up to a minute, accompanied by clonking noises from the disk. It's OK once it's warm, but I guess the disk won't last too much longer. Anyway, that shows that disk problems can cause short freezes.

---

### Post by jetman350 on 2016-08-21
Very unusual?  I wonder if your HDD is going bad?  I'm no IT Pro but something is not right in the scenario you are describing.  Sorry I've not been prompt, I have not figured out how to use this site yet.

---

### Post by nexhuntr on 2016-08-22
Xubuntu... for two days now. The freezing issues are still there. Every once in a while it freezes up and I've had no choice but to restart. Also shutting down it freezes. Minecraft it freezes. I've tried to update firmware. But Xubuntu seems to run a whole lot smother. I've disc checked my hard drive three times without failures. Unstable wifi seems to also send my computer into a freeze mode. I did some research into my hardware, to see if the Atom processors and Ubuntu had issues. Looks like I was onto something. But... Minecraft still doesn't work stable.

---

### Post by sgian on 2016-08-23
I suspect one of two things...
1. there is possibly some hardware component that has gone bad, and it fails under stress.  Since you already did a hard drive test, I would recommend testing the RAM at boot.  It will take a long time, just so you know.  
2. driver issues.  
--From your logs, it appears to me that your wireless adapter does not have a good driver.  Does the laptop work better when plugged in with a cable?  Have you replaced that adapter, and if you did then did you recompile any drivers or the kernel firmware?
--some other hardware might not be supported properly, possibly the graphics or gpu.

---

### Post by mastablasta on 2016-08-23
certain type of Atom GPU didn't have intel driver support as they were actually made by another company. at least the GPU part. so they didn't have propper acceleration.

Hard disk can show good and still be bad. it depends on the brand etc. for example read this article: [SIZE=2]http://www.computerworld.com/article/2846009/the-5-smart-stats-that-actually-predict-hard-drive-failure.html
[/SIZE]
once there are certain types of errors the OS along with drivers tries to compensate.

---

### Post by QLee on 2016-08-23
Several knowledgeable posters are already involved here and they are doing a good job analyzing symptoms and making corrections but it seems something has not yet been considered. That 2940 CPU is a "Bay Trail" and the freezing may be due to that and making it appear that something else might be related. Freezing that appears random and freezing while idle are a couple of the symptoms. There are several threads on the forums regarding "Bay Trail" CPUs which could be found using those keywords. Perhaps a small change in the BIOS or the addition to the command line in GRUB of intel_idle.max_cstate=1 would stop the freezing so the other fixes would be more effective. That CPU should have enough power for regular Ubuntu, I'm posting this from a 16.04 system with a similar chip.

---

### Post by nexhuntr on 2016-08-23
Thanks QLee
I've been starting to feel like either I'm completely inept or loosing touch with what's going on. These guys are working very hard to help solve my problem but I feel like I'm not getting anywhere.
To answer a few previous questions. I've not checked RAM because honestly I'm not sure how to do that. I've checked my hard drive and every test I know I've been able to either correct errors, or there aren't errors to correct. I've changed routers, gone other places to have stable internet, plugged in as well and the freezing still occurs.
It was the reasons why I went with Ubuntu in the first place, because I should be able to run it. I'll be looking for the forums about the "Bay Trail" CPU. I've been pondering if that was my problems all along.

---

### Post by QLee on 2016-08-23
> **nexhuntr said:**
> Thanks QLee
I've been starting to feel like either I'm completely inept or loosing touch with what's going on. 

Yes, well when there is an intermittent problem it can be extremely hard to pin down, you are getting symptoms that could be from a hardware problem so there may be more than one trouble. Maybe this can help eliminate the freezing.

It is pretty easy to test the command line option. When GRUB comes up for your OS choice, press the e key to edit (instructions at the bottom of the GRUB screen), go down to the line with "linux", on Ubuntu 16.04 it will look something like this (different depending on what you have installed at the present time). ```
linux	/boot/vmlinuz-4.4.0-34-generic root=UUID=50d978a9-da74-4abc-9654-6104e7ce2a74 ro  quiet splash $vt_handoffp
```, after the quiet splash insert the option, intel_idle.max_cstate=1, then follow the instructions at the bottom of the screen to boot with that line. After you have booted, test by opening a terminal and entering: ```
cat /sys/module/intel_idle/parameters/max_cstate
```, it will return a number (hopefully 1). If so, then use it like that for a while to see if the freezes stop.  That is a temporary test for that boot only.

It could be added to default GRUB if that solves the freezing problem. (You will find instructions for that in your search.) There may also be a BIOS option that could be used to disable the cstate change but that might depend on what the manufacturer of your mainboard has chosen and might be difficult to decipher.

---

### Post by nexhuntr on 2016-08-26
absolute SPOON moment, hence took 2 days to answer this...
cat /sys/module/intel_idle/parameters/max_cstate
9

I lost my mind after all that
I checked the grub file... I still saw max_cstate=1 and I didn't get anywhere... I had to find out what cstate 9 was... looks like a pretty deep low level power use.
Pulling out my hair, as also I couldn't get into the boot grub until today by hitting Esc key then continuing on... It was there that I saw something like this...

/boot/vmlinuz-4.4.0-34-generic root=UUID=50d978a9-da74-4abc-9654-6104e7ce2a74 ro  quiet splash intel_idel.max_cstate=1$vt_handoffp
I wished I had more hair, so I could pull it out.
I reached spoon level 9 now didn't I?
It took me two hours to figure out how to change what I did wrong... I'm nearly ready to move this into [SOLVED] I'm simply testing now to see if that truly solved my freezing issues. I'll get back to everyone in a short while.

---

### Post by QLee on 2016-08-26
I imagine almost all of us have had things like that happen to us along the way.

The important thing is you figured it out, best of luck in the future.

---

