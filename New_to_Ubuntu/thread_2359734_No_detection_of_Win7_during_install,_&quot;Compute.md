---
title: "No detection of Win7 during install, &quot;Computer&quot; from menu shifts to Rythmbox, etc"
date: 2017-04-27
forum: New to Ubuntu
---

### Post by smith73 on 2017-04-27
I was installing Ubuntu Mate 16.04.2 LTS on Asus Intel 2 core 4Gb RAM machine with Windows 7 Embedded (preactivated in a roundabout route) and in the installation window there was no notification that Windows is preinstalled there, like the first option was to just install Ubuntu and the last option was "Something else" as if it doesn't detect Windows at all (although in a dozen of tutorials I have watched there had always been this notification to install Ubuntu alongside with Windows if Windows was installed first). Although I wanted to perform "Something else" option for separate home and boot partitions, but I also wanted to encrypt the hard drive during install, so I just installed Ubuntu with encrypted hard drive and LVM, and during this installation there also wasn't any option for choosing the disk size, so it installed itself automatically in the whole hdd space. So if I were to dual boot Win7 and Ubuntu, I probably wouldn't? Well, maybe I do not need Windows that much, but then other issues had appeared.

I configured network details (IP, DNS, etc) in the "Edit Network Connections" window (from top menu bar), but after clicking on the "Software Update" and "Drivers" buttons in the Ubuntu Mate Welcome screen a green notification above these buttons appeared informing that for software download I need to be connected to the Internet. I figured out that the Internet was actually working, made the updates, then somehow downloaded the drivers and other Ubuntu software. 

Another issue appeared when from a detachable hdd I downloaded several folders to the desktop, one of which contained audio files, and enqueued this folder in the Rythmbox. It played the files, but later any time when I wanted to get to the file system GUI from the top menu bar Places-> Computer, etc the Rythmbox with enqueued files had been opened. So basically the only way to get to the file system GUI from the desktop was via "Username Home" folder that appeared on the desktop by default. 

I would be pretty happy with that installation for basic user interface and the facilities provided in the command line help (I found 1 typo in desktop help documentation ("the the") while searching for keyboard shortcuts for shifting multiple installed keyboard languages, like shift+alt in Windows 7). The main issue is that I work via remote desktop access to a server and am using the .rdp program provided by my employer to connect to their Windows 8 server desktop (run on Windows Server 2012 probably). So he provided me a Linux version of remote desktop access program, I installed Remmina from the Software boutique and it doesn't connect to their server. Then my employer connected to my desktop to configure Remmina, he installed xfreerdp (although he told me to install krdc, but it doesn't connect to their server either), tried to remove known_hosts, anyway it doesn't connect due to their certificate issues. So when I connect to their server in Windows via .rdp program and enter my login the window appears informing that "The remote computer could not be authenticated due to problems with its security certificate. The certificate is not from a trusted certifying authority", so I basically proceed and connect to their server from Windows normally, but in Ubuntu 16.04 it doesn't work. I would readily switch to Ubuntu if this issue(-s) would be solved. Maybe you would provide some information on what to do, thanks in advance. (There have been multiple issues so that's the brief description)
[TABLE]
[TR]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2017-04-27
Post this from live installer's terminal:
sudo parted -l

Often the issue is that you have used all 4 primary partitions. You need one available to convert to an extended, so you can then add as many logical partitions as you want.
Newer Windows have fast start up/hibernation. Make sure you did not turn on hibernation, but you do not have fast start up.
Also if Windows needs chkdsk, the Linux NTFS driver will not see the NTFS partition. And if resized, you need to reboot so it can run chkdsk as that is always required after a resize.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by Dennis N on 2017-04-27
> Another issue appeared when from a detachable hdd I downloaded several folders to the desktop, one of which contained audio files, and enqueued this folder in the Rythmbox. It played the files, but later any time when I wanted to get to the file system GUI from the top menu bar Places-> Computer, etc the Rythmbox with enqueued files had been opened. So basically the only way to get to the file system GUI from the desktop was via "Username Home" folder that appeared on the desktop by default. 

This problem with "Places" should be fixed by the method described in my post #6 in this thread:

[https://ubuntuforums.org/showthread.php?t=2343283](https://ubuntuforums.org/showthread.php?t=2343283)

---

