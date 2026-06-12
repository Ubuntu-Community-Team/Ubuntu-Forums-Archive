---
title: "Don't have permission to play a CD"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by lile001 on 2012-05-14
I am having a strange problem on Ubuntu 11.10.  I can play a CD, sometimes.  Later, I put in another CD into the player, and start up Movie Player (It seems to play nicer with CDs than Banshee) and Movie player puts up a message "Could not open location, you might not have permission to open the file".  

Banshee seems to want to play the file without complaining.  (I don't like Banshee, because sometimes it will do goofy things like continue to play after you have shut it down, or start to play random MP3 tracks in the middle of a CD.) 

Same thing happens with a movie occasionally - no permission to access the DVD drive.  What is going on that would make Movie Player think it doesn't have access to the CD/DVD drive, when everybody else can access it just fine?

---

### Post by Lisiano on 2012-05-14
Not sure, but could you clarify what kind of CD? Is it a Audio CD, Mixed (Both Audio and Data) or Data only? If it's an Audio CD then it is mounted using GVFS and it might fail (If you know what Fuse is, it's something like that), if it's a Mixed one, then it also might get mounted via GVFS, if it's a Data CD then it should get mounted as any other removable drive.
It might be a permission problem as in you not being in a group, open a terminal (Ctrl+Alt+T) and type in ```
groups
``` then paste what it spits at you here.

---

### Post by lile001 on 2012-05-14
> **Lisiano said:**
> Not sure, but could you clarify what kind of CD? Is it a Audio CD, Mixed (Both Audio and Data) or Data only? If it's an Audio CD then it is mounted using GVFS and it might fail (If you know what Fuse is, it's something like that), if it's a Mixed one, then it also might get mounted via GVFS, if it's a Data CD then it should get mounted as any other removable drive.
It might be a permission problem as in you not being in a group, open a terminal (Ctrl+Alt+T) and type in ```
groups
``` then paste what it spits at you here.

Here is what I get

[INDENT]larry adm dialout cdrom plugdev users lpadmin admin sambashare[/INDENT]

The CD is a standard audio CD from the library.  I get the same error in Movie Player from a standard commercial audio CD, and a similar error when I insert a standard commercial DVD  
[INDENT]Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed.[/INDENT]

---

### Post by lile001 on 2012-05-14
Found this howto - is it relevant?

[INDENT]How-To: Play DVD under Ubuntu
DVD are usually encrypted and therefore, due to legal reasons, Ubuntu Linux does not ship the package which decrypt DVD.
However, Ubuntu offers an easy way to get this package install. This tutorial will show which packages have to be installed in order to get most multimedia applications to run under Ubuntu.
The default movie player on Ubuntu is Totem, a Gnome movie player based on GStreamer or xine. As GStreamer is the default library used with Totem, this tutorial will be focused on GStreamer backend.
To get started with the codecs, we are going to install all the GStreamer library packages available on the repository:
$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse

From now on, you should be able to play any divx, non encrypted DVD and music.
In order to be able to play encrypted DVDs, we need to install libdvdcss2 package. As I said earlier, this package is not provided by Ubuntu for legal reasons. However, a script is supplied in order to easily install this package. This script is provided by libdvdread3 package.
Let's go back to the command line and, for people using Ubuntu Feisty 7.04 or Ubuntu Edgy 6.10, type:
$ sudo /usr/share/doc/libdvdread3/install-css.sh

People using releases prior to Edgy Eft, such as Ubuntu Dapper 6.04 will type:
$ sudo /usr/share/doc/libdvdread3/examples/install-css.sh

People using Debian based distribution might have to use:
$ wget [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
$ sudo dpkg -i libdvdcss2_1.2.5-1_i386.deb

Now, libdvdcss2 is installed and that's it :), insert a DVD in your player, Totem should open up and the DVD start playing.[/INDENT]

---

### Post by lile001 on 2012-05-14
locate -i libdvdcss2 returns nothing, maybe the problem is I don't have this package?

---

### Post by Lisiano on 2012-05-14
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
For DVD, relevant, for CD, nope.
Try this command when you insert the disk, it should show information about it and where it get's mounted.
```
gvfs-mount -l
```

---

### Post by Frogs Hair on 2012-05-14
The package libdvdcss2 is included with medibuntu repository which had to be enabled before I could install it . [http://www.ubuntuupdates.org/ppa/medibuntu_free?dist=precise](http://www.ubuntuupdates.org/ppa/medibuntu_free?dist=precise)

---

### Post by matt_symes on 2012-05-14
Hi

@OP. To see if the package is installed you use


```
dpkg -l libdvdcss2
```


If it has "un" next to it, it is not installed.


I think it's part of ubuntu-restricted-extras package as well as in the medibuntu repos's


You need to enable multiverse repository.


```
sudo apt-get install ubuntu-restricted-extras
```


Kind regards

---

### Post by lile001 on 2012-05-15
Still an issue after installing Ubuntu 12.02 

This


```
sudo apt-get install ubuntu-restricted-extras
```

ended in a microsoft EULA agreement about some kinda truetype fonts in the terminal that I could not turn off.  It ends with [OK].  Hitting enter, clicking on it, escape, shift enter, right click, spacebar, Control-C, q, shift-q, control-q, and so forth would not work to agree to it, so there it is stuck.  How do you respond to something in terminal that wants an [OK] ? 

Here is the response I don't understand from the other suggestion above: 

```
gvfs-mount -1
Error mounting location: volume doesn't implement mount

```

hmm.  ????   

Giving up on those ideas, I will try one of the other suggestions here. P.S. - don't assume I have any idea what I am doing. 10,000 chimps would actually have a better chance of typing the correct code.

---

### Post by Lisiano on 2012-05-15
The window with the MS EULA is called a ... Forgot the name. Either way. You navigate it using keys, to select a button, use Tab, to press that button, press Space.

EDIT: It's called ncurses.

And the command I told you (gvfs-mount) contains a lowercase L, not a 1. If unsure how to type it or you just lazy to type it, then copy paste it.

---

### Post by lile001 on 2012-05-15
> **matt_symes said:**
> Hi


```
sudo apt-get install ubuntu-restricted-extras
```


Kind regards

which didn't work for me.  I'm not an expert, remember. This SHOULD have been easy, but it isn't if like me one does not know the basics. 

This page 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

has a way to install this package using Ubuntu Software Center that doesn't require a terminal.  Many experts here are terminally addicted (pun intended) and don't realize that, for knucklheads like me, there are many alternatives that don't require the mysteries involved in working with hammer and tongs in terminal.  Like, for example, most beginners won't know what to do with [OK] at the end of an EULA in terminal. I am trying the Ubuntu Software Center method now.

---

### Post by Lisiano on 2012-05-15
Exactly why I like to give links to software like this [Ubuntu Restricted Extras are here, click me and you will install them using Ubuntu Software Center](apt://ubuntu-restricted-extras) cept usually I make only the name the link. Anyway, the window you saw, the ncurses menu, is navigated with tab and space. Do note that most of the time, it's way easier to find or do something in the terminal under our guidance than to use the GUI.

---

### Post by matt_symes on 2012-05-15
Hi

> This page 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

has a way to install this package using Ubuntu Software Center that doesn't require a terminal. Many experts here are terminally addicted (pun intended) and don't realize that, for knucklheads like me, there are many alternatives that don't require the mysteries involved in working with hammer and tongs in terminal. Like, for example, most beginners won't know what to do with [OK] at the end of an EULA in terminal. I am trying the Ubuntu Software Center method now.

You assume i was using Unity/Gnome shell yesterday. You even assume i was using a debian derivative.

The terminal is desktop agnostic.

Anyway, after checking i have just found out that ubuntu-restricted-extras will not install libdvdcss2.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Kind regards

---

### Post by lile001 on 2012-05-15
This code

```
Installing libdvdcss
Legal Warning: Check with your local laws to make sure usage of libdvdcss2 would be legal in your area.

Ubuntu 10.04 (i386, amd64), 10.10, 11.04, 11.10 and 12.04 (i386, amd64)
Works for old releases that are no longer supported if you have repositories on Cd/Dvd or somewhere. So, anything from 9.04 onwards. The latest LTS, 10.04, and the radically different 11.04 also work this way. 

Install the libdvdread4 package (no need to add third party repositories) via Synaptic or command line:


sudo apt-get install libdvdread4
Then open a terminal window and execute:

sudo /usr/share/doc/libdvdread4/install-css.sh
Rebooting may be necessary.
```

was able to make movies playable, however this:


```
Easy Install
For Ubuntu 9.04 (Karmic Koala) and Newer (10.04LTS Lucid Lynx, 10.10 Maverick Meerkat, 11.04 Natty Narwhal)

(If it hasn't happened automatically, you may have to update the list of available packages from the apt sources. You can do it clicking on the "Reload" button of Synaptic or running in a terminal either sudo apt-get update or sudo aptitude update)

Click here to install the ubuntu-restricted-extras package
```

didn't make audio CDs playable, although it DID let me click through the problematic EULA with a mouse like a boss.

---

### Post by lile001 on 2012-05-15
> **matt_symes said:**
> Hi
You assume i was using Unity/Gnome shell yesterday. You even assume i was using a debian derivative.


Well, no I didn't assume any of those things, in fact I haven't the slightest idea what you are talking about.  That's the problem here, often, even on the absolute beginner forum, it is assumed that I know something. Check the avatar - Homer Simpson.  Pretend that's who you are communicating with.  I know just enough to be really, really dangerous. If there is a way to screw it up, I will probably find it.  I try to investigate the things that people suggest and if I find the same thing on a harmless looking Ubuntu Community page that I can halfway understand, then paste away! and hope that I am doing something that doesn't result in a fire or an explosion.  

So far we are about halfway there......

---

### Post by lile001 on 2012-05-15
> **Lisiano said:**
> The window with the MS EULA is called a ... Forgot the name. Either way. You navigate it using keys, to select a button, use Tab, to press that button, press Space.

EDIT: It's called ncurses.

And the command I told you (gvfs-mount) contains a lowercase L, not a 1. If unsure how to type it or you just lazy to type it, then copy paste it.

Curses!  I should have expected ncurses! :P

Here is what I get with gvfs-mount minus the typo

```

gvfs-mount -l
Drive(0): 250 GB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): OS
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): OS -> file:///media/OS
      Type: GProxyMount (GProxyVolumeMonitorGdu)
Drive(1): HP Officejet 7500 E
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(2): Generic- SM/xD Picture
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(3): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): Audio Disc
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): Audio Disc -> cdda://sr0/
      Type: GProxyShadowMount (GProxyVolumeMonitorGdu)
Drive(4): Generic- SD/MMC
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(5): 1.0 TB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): Bigdrive1
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): Bigdrive1 -> file:///media/Bigdrive1
      Type: GProxyMount (GProxyVolumeMonitorGdu)
  Volume(1): Bigdrive2
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): Bigdrive2 -> file:///media/Bigdrive2
      Type: GProxyMount (GProxyVolumeMonitorGdu)
Drive(6): Generic- MS/MS-Pro
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(7): Generic- Compact Flash
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Mount(0): Audio Disc -> cdda://sr0/
  Type: GDaemonMount
```

I hope that stuff makes some sense to someone else here!  

Thanks!

---

### Post by Lisiano on 2012-05-15
I assume a persons experience level depending on the amount of posts and the registration date, don't really care about the avatar, for example a while back I had that for an avatar (It's a transparent png, don't know why it has a black bg). Yet it didn't mean I don't even know how to hold food or which end to bite first (Chocolate first obviously).

Anyway, can you post the output of ```
gvfs-mount -l
``` and yes, that's a lowercase L, not a 1.

EDIT: Ninja'd by the OP, I'm getting slow. Anyway. Looks like the disk is properly connected, can you take a look inside this folder
```
~/.gvfs
```It's normally invisible in nautilus (The default file manager in Ubuntu) so press Ctrl+H to show it or press Ctrl+L to go directly to it.

---

### Post by lile001 on 2012-05-15
> Yet it didn't mean I don't even know how to hold food or which end to bite first (Chocolate first obviously). 

Yes, bite the chocolate first, that is a good rule.  Hold food [like this]("http://hergreenlife.files.wordpress.com/2011/12/img_7933.jpg")

The only thing in said directory is  "cdda mount on sr0" which contains a list of the wav files on the CD.  When I investigate further, Nautilus says "the permissions of "Track1.wav" could not be determined".  That sounds really suspicious.  There is a way to show permissions in terminal but I don't remember how.

---

### Post by Lisiano on 2012-05-15
That's actually your CD mounted, try playing the files from there.

---

### Post by lile001 on 2012-05-15
> **Lisiano said:**
> That's actually your CD mounted, try playing the files from there.

Seems to work.  Banshee will play them, then won't shut off if you kill the program, as I noted earlier.  Movie Player will play them as well, however will generate the same error if the CD is placed in the drive and we let the computer do it's thing.  So we are 2/3 the way there!

New signature BTW:

---

### Post by lile001 on 2012-05-15
Here is a Big hammer solution:

1.  dis-associate Movie Player with Audio files

2. Get rid of Banshee, or put up with its idiosyncracies and 

3.  Get a different audio player that dies when you kill it.  

Movie Player seems to play movies OK, so the only remaining problem is to avoid the error message when playing audio files.  It is possible that I can pull off some of the above tasks without killing any small children.

---

### Post by Lisiano on 2012-05-15
I'm assuming GUI?
[LIST=1]
[*]Top right corner -> System Settings -> Details -> Default Applications -> Music -> Pick whatever you want
[*][Banshee](apt://banshee) <- Click that, then press Remove
[*]Everything dies when it get's killed. Unless it becomes a zombie. (Reference to process managment) Anyway, you can create a shortcut on your destkop to this command 
```
killall -9 banshee
``` (Replace banshee with what you want to kill) and the second you run the shortcut, it dies instantly.
[/LIST]

Might I suggest SMPlayer? It's a GUI for MPlayer, dare I say one of the best players Linux has to offer? If you have an nVidia GPU, it will even use it to decrease the load on the CPU and is VERY lightweight (Beside MPlayer being run from a terminal ofc)

---

### Post by Acharn on 2012-05-16
I'm having the same problem, but with a VCD. I burned this CD on this same burner back when I was still running Windows. I know the CD-ROM reader works because I've been booting from last year's live CD every day for months, until I got my new hard drive today. I have searched all over with no joy, so I got to thinking about the part of the error message, "...you might not have permission to open the file." I took a look with 'ls -l':

roger@roger-Aspire-M1610:~$ ls -l /media
total 2
dr-x------ 1 roger roger 2048 1978-07-14 07:00 VIDEOCD
roger@roger-Aspire-M1610:~$ ls -l /media/VIDEOCD
total 8
dr-x------ 1 roger roger 2048 1978-07-14 07:00 ext
dr-x------ 1 roger roger 2048 1978-07-14 07:00 mpegav
dr-x------ 1 roger roger 2048 1978-07-14 07:00 segment
dr-x------ 1 roger roger 2048 1978-07-14 07:00 vcd

Aha! NOBODY has permission to do anything but execute. Nobody can read or write to these files. I'm the owner and I also own the group that owns the files and neither I nor root can read them.

So the question is, how to arrange things so CDs are opened with read permission set?

---

### Post by lile001 on 2012-05-16
> **Lisiano said:**
> I'm assuming GUI?
[LIST=1]
[*]Top right corner -> System Settings -> Details -> Default Applications -> Music -> Pick whatever you want
[*][Banshee]("apt://banshee") <- Click that, then press Remove
[*]Everything dies when it get's killed. Unless it becomes a zombie. (Reference to process managment) Anyway, you can create a shortcut on your destkop to this command 
```
killall -9 banshee
``` (Replace banshee with what you want to kill) and the second you run the shortcut, it dies instantly.
[/LIST]

Might I suggest SMPlayer? It's a GUI for MPlayer, dare I say one of the best players Linux has to offer? If you have an nVidia GPU, it will even use it to decrease the load on the CPU and is VERY lightweight (Beside MPlayer being run from a terminal ofc)

THANKS for demonstrating the GUI method for changing file permissions.  I have searched long and hard for this, and only found pages one that recommend editing some complex file, which I swiftly realize is way over my head.  I'm glad there is a REALLY SIMPLE way to accomplish the task at hand.    

Meanwhile, I have tried Amarok, which was recommended highly on one of the Ubuntu forums I was reading, and SMplayer. 

 SMplayer looks easy to use yet powerful to configure, however it has an annoying skip every few seconds, as if it can't read the disk fast enough.  Other players don't seem to have this problem, so I'll table that idea for a while since it becomes a game of whack-a-mole.   I'll give SMplayer another crack later.  


Amarok is a huge download, and it looks  like it has more options than a day-trader, seems kind of complex to use, maybe more program than I  need so I dumped it.

Rhythmbox seems to work properly, and behave well after making it the default program for audio disks.   

Movies seem to play properly now that I've convinced Movie Player to stay in it's cage when an audio CD is plugged in.  So it looks like the main problem was that the wrong program was set to open by default, and also there was some extra DVD stuff that isn't installed when one installs Ubuntu because of some legal mumbo-jumbo, but is really actually required to make a DVD movie play.  

Fantastic!

---

