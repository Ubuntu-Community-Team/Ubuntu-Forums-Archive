---
title: "[SOLVED] How to install another distro with same desktop enviro and kepping the same"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by bhadotia on 2008-06-25
I want to install open suse 11 dual boot with my ubuntu keeping the same /home partition for both. I want to install both kde and gnome in open suse. But in the past when I did that I always had problems because of the /home being the same . I always mixed up ubuntu gnome settings with the gnome settings of the other distro.

This time I want to avoid it.


Any suggestions on how to do this?

Heres how my partitions look like:


```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000837a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2611    20972826   83  Linux
/dev/sda2            2612        7496    39238762+  83  Linux
/dev/sda3            7497        7627     1052257+  82  Linux swap / Solaris
/dev/sda4   *        7628        9729    16884315   83  Linux
``` 

The /home is sda2. ubuntu / is sda1. I plan to install suse on sda4.

---

### Post by cdtech on 2008-06-25
You can't share the same "home" partition without conflicts from either OS.

Your "home" folder uses "." dot configuration files for your current settings for GNOME or whatever Desktop you choose. By changing those files through another distro, you change your existing setup.

The only way is to install each apt individually and assign it's own config file naming scheme.

I say "No Way". But as always, I could be wrong.

---

### Post by bhadotia on 2008-06-25
Ok .... Then I will not keep a common /home. But I just need a  little confirmation , If import my account from ubuntu to suse will I be able to access my data on the existing / /home without any ownership problems?

---

### Post by Dr Small on 2008-06-25
It could probably be done, but it might be messy. But I have never tried it.

---

### Post by volkswagner on 2008-06-25
I have seen conflicting arguments on this topic.  No guide on how to do it.  What if you were to share /home but use another user name for the second distro?  You could still import settings.

---

### Post by Gripp on 2008-06-25
i saw a post here maybe a month or two ago asking basically the same question.  but i *think* that it was for dual boot Ubuntu and Kubutu.  i'm not sure that mixing entirely diff. systems would work though...

but search around, i'm sure you can find that thread

---

### Post by Dr Small on 2008-06-25
Here is one thread about the subject that is recent:
[http://ubuntuforums.org/showthread.php?t=830345](http://ubuntuforums.org/showthread.php?t=830345)

---

### Post by bhadotia on 2008-06-25
Can I import settings of my account in ubuntu to another account in suse with another username?

Interesting !  Never tried it before.


But would not that again cause the problem. Because all the ubuntu settings will be imported to the suse gnome?

It's the data I want, not the settings.

---

### Post by Dr Small on 2008-06-25
If Ubuntu was running Gnome and SuSE running KDE (for instances), I don't think there would be any conflicts. But if they are both running the same DE, then there might be conflicts. Why not use the /home partition, but choose a different username, which would give you a different Home Folder ?

Dr Small

---

### Post by bhadotia on 2008-06-25
Affirmative! there are no problems when you have different DEs I've tried that before many times.

So there is no real foolproof solution to this issue afterall?

---

### Post by unutbu on 2008-06-25
Here is one strategy that works:

Use a common /data partition, not a common /home partition. Under this method, Ubuntu on sda1 has a /home directory, and SUSE on sda4 has a (separate but equal) /home directory too. These /home directories can be very small -- they only need space to hold the dot files and a few supporting directories. sda2 could be mounted at /data. When you boot Ubuntu, running
```

cd 
ln -s  /data data
```
would create a symlink from /home/bhadotia/data to /data. So you could pretend that your common data is in your home directory.

You could run the same command in SUSE.

If you have more than one user, then make sure you create the users in the same order in SUSE as they exist in Ubuntu. Ubuntu users start with UID 1000 (you can see the UIDs in /etc/passwd). Make sure SUSE UIDs also start at 1000. If not, you'll have to change your UID to 1000. The key point here is that your ext3 filesystem really does not care about your username for ownership purposes. It cares about the UID. As long as the UID is the same, both Ubuntu and SUSE will believe the file belongs to the same user.

(PS. I picked up the idea I described above here [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817), at bodhi.zazen's tutorial on creating multi-boot systems.)

---

### Post by Dr Small on 2008-06-25
> **bhadotia said:**
> Affirmative! there are no problems when you have different DEs I've tried that before many times.

So there is no real foolproof solution to this issue afterall?
Nothing ever got done without trying.
/me pats bhadotia on the back.

Good luck, mac :)

---

### Post by bhadotia on 2008-06-26
@unutbu :
But what about the fact that /home is already mounted on sda2.
Are you you not implying a reinstall of the system(ubuntu) with a /data mounted on sda2.
I mean you say keep a common /data partition mounted on sda2 where the /home of ubuntu is already mounted there.

Can you be a little clear . 

I am at present going through the post on the link you gave me to clarify.

---

### Post by bhadotia on 2008-06-26
Ok....... I've installed  suse11 with the home partition of ubuntu mounted on /data . 

All is well uptill now . I am having no problems accessing my data on /data from suse.

Thanks guys.

---

### Post by unutbu on 2008-06-26
Here are instructions for separating your current Ubuntu home directory on sda2 into a small Ubuntu home directory on sda1 and all your data on sda2.

I am assuming you are the only user, and your username is bhadotia. 


Boot from a LiveCD. Open a terminal.
```

export user=bhadotia
sudo mkdir /Ubuntu
sudo mount /dev/sda1 /Ubuntu
sudo mkdir /Ubuntu/home
sudo mkdir /Ubuntu/home/$user

sudo mkdir /oldhome
sudo mount /dev/sda2 /oldhome

cd /oldhome/$user

find . -print | grep  "^\./\."     # This will show you what you are about to copy over

find . -print0 | grep -zZ "^\./\." | sudo cpio --null --sparse -pvd /Ubuntu/home/$user
```

This will copy all the dot (config) files (like .bashrc, .profile) from your old home to your new home. 

```
gksudo gedit /Ubuntu/etc/fstab
```

Change the line with "/home" in it to "/data".
For example, change the line that looks something like this:

```
UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed /home ext3 defaults,errors=remount-ro 0 2
```

to:

```
UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed /data ext3 defaults,errors=remount-ro 0 2
```


Save and exit. Reboot into Ubuntu. You should now have a small home directory with nothing but dot config files, and your old home (still with all the dot config files) in sda2 which should now be mounted at /data.

Now for some cleanup:
```

cd
ln -s /data data
```

If you have a special directory for scripts and executables in your home directory, let's say it's called ~/bin, then you probably set your PATH variable include this special directory. You probably set your PATH in ~/.profile. You'll have to update that now that your bin directory is in /data/bin.

If you make use of the ~/Desktop directory, you can either copy it over to your new home using Nautilus or the command line.

Although the commands
```

cd /data
find . -print | grep  "^\./\."     # This will show you what you are about to erase
find . -print0 | grep -zZ "^\./\." | xargs -0 rm -rf

```
should remove all the dot config files from /data, I suggest you *DO NOT USE THOSE COMMANDS* and rather do this by hand to make sure you don't lose something you want. 

All the commands above are safe except for the last command with the "xargs -0 rm -rf" in it. They are safe in the sense that nothing is permanently erased, and I can help you back out of these commands and restore you to your present state if something were to go wrong due to these commands. The "xargs -0 rm -rf" command is inherently dangerous; I cannot help you back out of that one if I somehow screwed up the command. That's why I suggest you do the removing manually.

---

### Post by bodhi.zazen on 2008-06-26
In general you can share /home across distros, just use a unique user name on each distro :twisted:

Actually you can share a home and common username as long as you understand the potential conflicts and are willing to trouble shoot.

In terms of using $HOME (ie a /home with a common user name) you will get possible conflicts with both . files and uid. For example the first user on Fedora has a uid of 500. On Ubuntu it is 1000. (users are known in most ways to the system by uid and not name).

You can not save your settings if your settings refer to things outside of home such as specific themes, icons, or background images.

Last piece of advice, be careful of "rude" distros. *Some* distros will reformat /home without asking permission (bad distro, bad, bad distro). I usually edit fstab and mount the data partition post-install.

Best to use a data partition with links.

ls -s /data/music ~/music

---

### Post by bhadotia on 2008-06-27
> **unutbu said:**
> If you have a special directory for scripts and executables in your home directory, let's say it's called ~/bin,then you probably set your PATH variable include this special directory. You probably set your PATH in ~/.profile. You'll have to update that now that your bin directory is in /data/bin.

If you make use of the ~/Desktop directory, you can either copy it over to your new home using Nautilus or the command line.


I did not get these points . I have a directory called 'bin' in my home folder and it contains links to the IE4Linux script  . The link target is :"/home/abhishek/.ies4linux/bin/ie6".
> then you probably set your PATH variable include this special directory. You probably set your PATH in ~/.profile. You'll have to update that now that your bin directory is in /data/bin.
What do you mean by this?
> If you make use of the ~/Desktop directory, you can either copy it over to your new home using Nautilus or the command line.

How do we make use of the ~/Desktop directory? I thought that it contained all the data that was placed on our desktops. In my case it is empty because I like clean desktop.

Also I don't have my 8.04 live CD (gave it to a cousin) at present , so can I make use of the 7.10 live CD?

---

### Post by unutbu on 2008-06-27
> **bhadotia said:**
> I have a directory called 'bin' in my home folder and it contains links to the IE4Linux script. The link target is :"/home/abhishek/.ies4linux/bin/ie6".


We're going to have to do some work to fix the symlinks. To help me get a sense of what will need to be changed, please post 

```

find . -type l -print0 | xargs -0 ls -l
```

> 
How do we make use of the ~/Desktop directory?... In my case it is empty because I like clean desktop.

Good. If your Desktop is empty, then you are not "making use of" the ~/Desktop directory. Gnome will create the directory in the sda1 home if/when it is needed. You are free to delete the /data/Desktop directory if it is empty.

> 
Also I don't have my 8.04 live CD (gave it to a cousin) at present , so can I make use of the 7.10 live CD?
No problem. The 7.10 LiveCD will work fine.

---

### Post by bhadotia on 2008-06-27
Here you go:
```
abhishek@ubuntu:~$ find . -type l -print0 | xargs -0 ls -l
lrwxrwxrwx 1 abhishek users    53 2008-06-23 02:56 ./.adobe/Acrobat/8.0/Cert/curl-ca-bundle.crt -> /usr/lib/Adobe/Reader8/Reader/Cert/curl-ca-bundle.crt
lrwxrwxrwx 1 abhishek users    53 2008-06-26 19:28 ./.beagle/Log/current-Beagle -> /home/abhishek/.beagle/Log/2008-06-26-19-28-27-Beagle
lrwxrwxrwx 1 abhishek users    60 2008-06-26 19:38 ./.beagle/Log/current-BeagleConsole -> /home/abhishek/.beagle/Log/2008-06-26-19-28-27-BeagleConsole
lrwxrwxrwx 1 abhishek users    58 2008-06-26 19:29 ./.beagle/Log/current-IndexHelper -> /home/abhishek/.beagle/Log/2008-06-26-19-29-50-IndexHelper
lrwxrwxrwx 1 abhishek users    65 2008-06-26 19:38 ./.beagle/Log/current-IndexHelperConsole -> /home/abhishek/.beagle/Log/2008-06-26-19-29-50-IndexHelperConsole
lrwxrwxrwx 1 abhishek users    68 2008-06-26 19:31 ./.beagle/Log/current-IndexHelperExceptions -> /home/abhishek/.beagle/Log/2008-06-26-19-29-50-IndexHelperExceptions
lrwxrwxrwx 1 abhishek users    33 2008-06-24 05:20 ./bin/ie6 -> /home/abhishek/.ies4linux/bin/ie6
lrwxrwxrwx 1 abhishek users    33 2008-06-24 05:22 ./bin/ie7 -> /home/abhishek/.ies4linux/bin/ie7
lrwxrwxrwx 1 abhishek users    26 2008-06-22 07:30 ./Examples -> /usr/share/example-content
lrwxrwxrwx 1 abhishek users    10 2008-06-23 04:04 ./.googleearth/instance-running-lock -> /proc/3283
lrwxrwxrwx 1 abhishek users    10 2008-06-24 05:20 ./.ies4linux/ie6/dosdevices/c: -> ../drive_c
lrwxrwxrwx 1 abhishek users     1 2008-06-24 05:20 ./.ies4linux/ie6/dosdevices/z: -> /
lrwxrwxrwx 1 abhishek users    22 2008-06-24 05:20 ./.ies4linux/ie6/drive_c/windows/profiles/abhishek/Desktop -> /home/abhishek/Desktop
lrwxrwxrwx 1 abhishek users    14 2008-06-24 05:20 ./.ies4linux/ie6/drive_c/windows/profiles/abhishek/My Documents -> /home/abhishek
lrwxrwxrwx 1 abhishek users    20 2008-06-24 05:20 ./.ies4linux/ie6/drive_c/windows/profiles/abhishek/My Music -> /home/abhishek/Music
lrwxrwxrwx 1 abhishek users    23 2008-06-24 05:20 ./.ies4linux/ie6/drive_c/windows/profiles/abhishek/My Pictures -> /home/abhishek/Pictures
lrwxrwxrwx 1 abhishek users    21 2008-06-24 05:20 ./.ies4linux/ie6/drive_c/windows/profiles/abhishek/My Videos -> /home/abhishek/Videos
lrwxrwxrwx 1 abhishek users     8 2008-06-24 05:20 ./.ies4linux/ie6/drive_c/windows/system -> system32
lrwxrwxrwx 1 abhishek users    10 2008-06-24 05:21 ./.ies4linux/ie7/dosdevices/c: -> ../drive_c
lrwxrwxrwx 1 abhishek users     1 2008-06-24 05:21 ./.ies4linux/ie7/dosdevices/z: -> /
lrwxrwxrwx 1 abhishek users    22 2008-06-24 05:21 ./.ies4linux/ie7/drive_c/windows/profiles/abhishek/Desktop -> /home/abhishek/Desktop
lrwxrwxrwx 1 abhishek users    14 2008-06-24 05:21 ./.ies4linux/ie7/drive_c/windows/profiles/abhishek/My Documents -> /home/abhishek
lrwxrwxrwx 1 abhishek users    20 2008-06-24 05:21 ./.ies4linux/ie7/drive_c/windows/profiles/abhishek/My Music -> /home/abhishek/Music
lrwxrwxrwx 1 abhishek users    23 2008-06-24 05:21 ./.ies4linux/ie7/drive_c/windows/profiles/abhishek/My Pictures -> /home/abhishek/Pictures
lrwxrwxrwx 1 abhishek users    21 2008-06-24 05:21 ./.ies4linux/ie7/drive_c/windows/profiles/abhishek/My Videos -> /home/abhishek/Videos
lrwxrwxrwx 1 abhishek users     8 2008-06-24 05:21 ./.ies4linux/ie7/drive_c/windows/system -> system32
lrwxrwxrwx 1 abhishek abhishek 16 2008-06-28 08:13 ./.mozilla/firefox/a9ws5uau.default/lock -> 127.0.1.1:+11550
lrwxrwxrwx 1 abhishek users    17 2008-06-25 16:57 ./.openoffice.org2/user/config/arrowhd_en-GB.soe -> arrowhd_en-US.soe
lrwxrwxrwx 1 abhishek users    17 2008-06-25 16:57 ./.openoffice.org2/user/config/arrowhd_en-US_en-ZA.soe -> arrowhd_en-US.soe
lrwxrwxrwx 1 abhishek users    17 2008-06-25 16:57 ./.openoffice.org2/user/config/classic_en-GB.sog -> classic_en-US.sog
lrwxrwxrwx 1 abhishek users    17 2008-06-25 16:57 ./.openoffice.org2/user/config/classic_en-US_en-ZA.sog -> classic_en-US.sog
lrwxrwxrwx 1 abhishek users    18 2008-06-25 16:57 ./.openoffice.org2/user/config/hatching_en-GB.soh -> hatching_en-US.soh
lrwxrwxrwx 1 abhishek users    18 2008-06-25 16:57 ./.openoffice.org2/user/config/hatching_en-US_en-ZA.soh -> hatching_en-US.soh
lrwxrwxrwx 1 abhishek users    16 2008-06-25 16:57 ./.openoffice.org2/user/config/modern_en-GB.sog -> modern_en-US.sog
lrwxrwxrwx 1 abhishek users    16 2008-06-25 16:57 ./.openoffice.org2/user/config/modern_en-US_en-ZA.sog -> modern_en-US.sog
lrwxrwxrwx 1 abhishek users    17 2008-06-25 16:57 ./.openoffice.org2/user/config/palette_en-GB.soc -> palette_en-US.soc
lrwxrwxrwx 1 abhishek users    17 2008-06-25 16:57 ./.openoffice.org2/user/config/palette_en-US_en-ZA.soc -> palette_en-US.soc
lrwxrwxrwx 1 abhishek users    16 2008-06-25 16:57 ./.openoffice.org2/user/config/styles_en-GB.sod -> styles_en-US.sod
lrwxrwxrwx 1 abhishek users    16 2008-06-25 16:57 ./.openoffice.org2/user/config/styles_en-US_en-ZA.sod -> styles_en-US.sod
lrwxrwxrwx 1 abhishek users    31 2008-06-23 06:41 ./.picasa/dosdevices/c: -> /home/abhishek/.picasa/drive_c/
lrwxrwxrwx 1 abhishek users     1 2008-06-23 06:41 ./.picasa/dosdevices/z: -> /
lrwxrwxrwx 1 abhishek users    22 2008-06-23 06:41 ./.picasa/drive_c/Documents and Settings/abhishek/Desktop -> /home/abhishek/Desktop
lrwxrwxrwx 1 abhishek users    54 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/buttons -> /opt/picasa/wine/drive_c/Program Files/Picasa2/buttons
lrwxrwxrwx 1 abhishek users    56 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/cdautorun -> /opt/picasa/wine/drive_c/Program Files/Picasa2/cdautorun
lrwxrwxrwx 1 abhishek users    51 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/i18n -> /opt/picasa/wine/drive_c/Program Files/Picasa2/i18n
lrwxrwxrwx 1 abhishek users    58 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/Picasa2.exe -> /opt/picasa/wine/drive_c/Program Files/Picasa2/Picasa2.exe
lrwxrwxrwx 1 abhishek users    58 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/Picasa2.scr -> /opt/picasa/wine/drive_c/Program Files/Picasa2/Picasa2.scr
lrwxrwxrwx 1 abhishek users    61 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/picasai18n.dll -> /opt/picasa/wine/drive_c/Program Files/Picasa2/picasai18n.dll
lrwxrwxrwx 1 abhishek users    70 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/PicasaMediaDetector.exe -> /opt/picasa/wine/drive_c/Program Files/Picasa2/PicasaMediaDetector.exe
lrwxrwxrwx 1 abhishek users    63 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/PicasaUpdate.exe -> /opt/picasa/wine/drive_c/Program Files/Picasa2/PicasaUpdate.exe
lrwxrwxrwx 1 abhishek users    54 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/plugins -> /opt/picasa/wine/drive_c/Program Files/Picasa2/plugins
lrwxrwxrwx 1 abhishek users    60 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/qtsupport.dll -> /opt/picasa/wine/drive_c/Program Files/Picasa2/qtsupport.dll
lrwxrwxrwx 1 abhishek users    54 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/runtime -> /opt/picasa/wine/drive_c/Program Files/Picasa2/runtime
lrwxrwxrwx 1 abhishek users    60 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/Uninstall.exe -> /opt/picasa/wine/drive_c/Program Files/Picasa2/Uninstall.exe
lrwxrwxrwx 1 abhishek users    53 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/update -> /opt/picasa/wine/drive_c/Program Files/Picasa2/update
lrwxrwxrwx 1 abhishek users    50 2008-06-23 06:41 ./.picasa/drive_c/Program Files/Picasa2/web -> /opt/picasa/wine/drive_c/Program Files/Picasa2/web
lrwxrwxrwx 1 abhishek users    49 2008-06-23 06:41 ./.picasa/drive_c/Program Files/wine_gecko -> /opt/picasa/wine/drive_c/Program Files/wine_gecko
lrwxrwxrwx 1 abhishek users    38 2008-06-23 06:41 ./.picasa/drive_c/windows/fonts -> /opt/picasa/wine/drive_c/windows/fonts
lrwxrwxrwx 1 abhishek users    36 2008-06-23 06:41 ./.picasa/drive_c/windows/inf -> /opt/picasa/wine/drive_c/windows/inf
lrwxrwxrwx 1 abhishek users    79 2008-06-23 06:41 ./.picasa/drive_c/windows/profiles/All Users/Start Menu/Programs/Picasa2 -> /opt/picasa/wine/drive_c/windows/profiles/All Users/Start Menu/Programs/Picasa2
lrwxrwxrwx 1 abhishek users    28 2008-06-23 06:41 ./.picasa/generic.ppd -> /opt/picasa/wine/generic.ppd
lrwxrwxrwx 1 abhishek users    34 2008-06-23 02:55 ./.themes/aud-Default -> /usr/share/audacious/Skins/Default
lrwxrwxrwx 1 abhishek users    10 2008-06-23 06:56 ./.wine/dosdevices/c: -> ../drive_c
lrwxrwxrwx 1 abhishek abhishek 13 2008-06-27 00:41 ./.wine/dosdevices/d: -> /media/cdrom0
lrwxrwxrwx 1 abhishek users     9 2008-06-24 03:22 ./.wine/dosdevices/d:: -> /dev/scd0
lrwxrwxrwx 1 abhishek users     1 2008-06-23 06:56 ./.wine/dosdevices/z: -> /
lrwxrwxrwx 1 abhishek users    22 2008-06-23 06:57 ./.wine/drive_c/windows/profiles/abhishek/Desktop -> /home/abhishek/Desktop
lrwxrwxrwx 1 abhishek users    14 2008-06-23 06:57 ./.wine/drive_c/windows/profiles/abhishek/My Documents -> /home/abhishek
lrwxrwxrwx 1 abhishek users    20 2008-06-23 06:57 ./.wine/drive_c/windows/profiles/abhishek/My Music -> /home/abhishek/Music
lrwxrwxrwx 1 abhishek users    23 2008-06-23 06:57 ./.wine/drive_c/windows/profiles/abhishek/My Pictures -> /home/abhishek/Pictures
lrwxrwxrwx 1 abhishek users    21 2008-06-23 06:57 ./.wine/drive_c/windows/profiles/abhishek/My Videos -> /home/abhishek/Videos
```

---

### Post by bobbob1016 on 2008-06-27
I don't think there will be too many issues.  I'd say back everything up first, as in back up the '.' config files/folders.  Your files should be ok.  I'd say open a terminal, type "pwd" without quotes.  To make sure you are in your home dir, it should say /home/(yourusername), then type "sudo chmod -R 777 *" without quotes to change permissions so everyone can read and write to your home dir.  DO NOT DO THIS TO YOUR ROOT DIRECTORY.  Then SUSE should work.  The only issue I can think of is branding, as in Ubuntu's logo won't work in SUSE, so you'd need to pick a neutral theme for everything so SUSE and Ubuntu would have the themes.

I could be wrong though.

---

### Post by unutbu on 2008-06-27
All symlinks not mentioned below are fine (I think).

These links need fixing:
```

lrwxrwxrwx 1 abhishek users    22 2008-06-24 05:20 ./.ies4linux/ie6/drive_c/windows/profiles/abhishek/Desktop -> /home/abhishek/Desktop
lrwxrwxrwx 1 abhishek users    14 2008-06-24 05:20 ./.ies4linux/ie6/drive_c/windows/profiles/abhishek/My Documents -> /home/abhishek
lrwxrwxrwx 1 abhishek users    20 2008-06-24 05:20 ./.ies4linux/ie6/drive_c/windows/profiles/abhishek/My Music -> /home/abhishek/Music
lrwxrwxrwx 1 abhishek users    23 2008-06-24 05:20 ./.ies4linux/ie6/drive_c/windows/profiles/abhishek/My Pictures -> /home/abhishek/Pictures
lrwxrwxrwx 1 abhishek users    21 2008-06-24 05:20 ./.ies4linux/ie6/drive_c/windows/profiles/abhishek/My Videos -> /home/abhishek/Videos
lrwxrwxrwx 1 abhishek users    22 2008-06-24 05:21 ./.ies4linux/ie7/drive_c/windows/profiles/abhishek/Desktop -> /home/abhishek/Desktop
lrwxrwxrwx 1 abhishek users    14 2008-06-24 05:21 ./.ies4linux/ie7/drive_c/windows/profiles/abhishek/My Documents -> /home/abhishek
lrwxrwxrwx 1 abhishek users    20 2008-06-24 05:21 ./.ies4linux/ie7/drive_c/windows/profiles/abhishek/My Music -> /home/abhishek/Music
lrwxrwxrwx 1 abhishek users    23 2008-06-24 05:21 ./.ies4linux/ie7/drive_c/windows/profiles/abhishek/My Pictures -> /home/abhishek/Pictures
lrwxrwxrwx 1 abhishek users    21 2008-06-24 05:21 ./.ies4linux/ie7/drive_c/windows/profiles/abhishek/My Videos -> /home/abhishek/Videos
lrwxrwxrwx 1 abhishek users    22 2008-06-23 06:41 ./.picasa/drive_c/Documents and Settings/abhishek/Desktop -> /home/abhishek/Desktop
lrwxrwxrwx 1 abhishek users    22 2008-06-23 06:57 ./.wine/drive_c/windows/profiles/abhishek/Desktop -> /home/abhishek/Desktop
lrwxrwxrwx 1 abhishek users    14 2008-06-23 06:57 ./.wine/drive_c/windows/profiles/abhishek/My Documents -> /home/abhishek
lrwxrwxrwx 1 abhishek users    20 2008-06-23 06:57 ./.wine/drive_c/windows/profiles/abhishek/My Music -> /home/abhishek/Music
lrwxrwxrwx 1 abhishek users    23 2008-06-23 06:57 ./.wine/drive_c/windows/profiles/abhishek/My Pictures -> /home/abhishek/Pictures
lrwxrwxrwx 1 abhishek users    21 2008-06-23 06:57 ./.wine/drive_c/windows/profiles/abhishek/My Videos -> /home/abhishek/Videos
```

Solution:
At the clean up stage, after you've separated /home on sda2 into a small /home on sda1 and /data on sda2:```

cd
ln -sf /data/Desktop Desktop
ln -sf /data/Music Music
ln -sf /data/Pictures Pictures
ln -sf /data/Videos Videos
ln -sf /data ".wine/drive_c/windows/profiles/abhishek/My Documents"
ln -sf /data ".ies4linux/ie6/drive_c/windows/profiles/abhishek/My Documents"
ln -sf /data ".ies4linux/ie7/drive_c/windows/profiles/abhishek/My Documents"

```
Needs fixing:```

lrwxrwxrwx 1 abhishek users    33 2008-06-24 05:20 ./bin/ie6 -> /home/abhishek/.ies4linux/bin/ie6
lrwxrwxrwx 1 abhishek users    33 2008-06-24 05:22 ./bin/ie7 -> /home/abhishek/.ies4linux/bin/ie7

```
Solution:
We need to find and alter your $PATH variable. 

```

gedit ~/.profile

```

Add this to the end of your ~/.profile:
```

pathmunge () {
	if ! echo $PATH | /bin/egrep -q "(^|:)$1($|:)" ; then
	   if [ "$2" = "after" ] ; then
	      PATH=$PATH:$1
	   else
	      PATH=$1:$PATH
	   fi
	fi
}
pathmunge /data/bin after
```

Explanation:
When I type 
```
echo $PATH
```
I get```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/fan/bin
```
The PATH variable tells your terminal shell where to look when a command is typed. If it isn't in one of these directories, then it returns "command not found".

If your PATH includes /home/abhishek/bin, then when you type 
```
ie6
```
the shell (bash) looks for it in /usr/local/sbin, then /usr/local/bin, etc, until it finds an executable called ie6 in your /home/abhishek/bin.

We are changing things so ie6 is now in /data/bin.
So I'm changing your PATH to include /data/bin. That way programs you put there can be found automatically and run from the terminal without you having to type the full path to the program.

[Edit:
Now that I think about it, a simple alternative solution would be

```
cd
ln -sf /data/bin bin
```
Then you don't have to screw with your PATH. It's up to you. I find the pathmunge function useful, and if you think it might like altering your PATH some more, then do the pathmunge solution. If you think this is all a big bother, just execute

```
cd
ln -sf /data/bin bin
```
and you should be fine.]

---

### Post by bhadotia on 2008-06-27
K.... Thanks I will boot into the live CD now.

I will see you later and tell you what happened.

---

### Post by bhadotia on 2008-06-27
I think I've screwed up bigtime!

When I rebooted into ubuntu after doing the live cd work and tried to log in a message popped up saying that the "......../home does not appear to exist........".

What went wrong :  I don't know?:(

Also I noticed when copying some files said that "permission was denied". May be that prevented some files from being copied. 

I am using the live CD now to browse the net. I've just opened the /home on sda1 to see how many files were copied . But there is only one file named abhishek there with no other hidden files even. When I double click on abhishek this message pops up:

> Couldn't display "/media/disk/home/abhishek".


The attempt to log in failed.



The files on sda2 are intact.  And the /etc/fstab was successfully edited. Which is the reason why ubuntu could not find my home: No files were copied and the /data was mounted on sda2.

Any suggestions on how to fix this ? Otherwise I can just edit /etc/fstab to mount /home on sda2 again.

---

### Post by unutbu on 2008-06-27
It sounds like /home/abhishek on sda1 is a file instead of a directory. Let's be careful and check this:

```
cd /home
ls -l
mount
```

---

### Post by bhadotia on 2008-06-27
Sorry, but I edited my /etc/fstab to mount /home on sda2 to see if it worked and its fine.

Now I have again logged into live environment . How should I execute those commands? I mean if I do cd /home , I cd to the /home of the live CD. Should not I chroot or something like that first?

---

### Post by unutbu on 2008-06-27
Boot from the LiveCD.
Do these commands again, but this time we'll check that they worked. If at any time you do not see what I say you should see, or if you get an error, stop and post the complete terminal buffer (your commands and the output). 

```
export user=abhishek
echo $user
```

The output should say "abhishek"

```
sudo mkdir /Ubuntu
ls -ld /Ubuntu
```

You should see
```
drwxr-xr-x 2 root root 4096 2008-06-27 14:52 /Ubuntu

```
```
sudo mount /dev/sda1 /Ubuntu
mount
```

One of the lines should say
```
/dev/sda1 on /Ubuntu type ext3 (rw)
```
```

sudo mkdir /Ubuntu/home
sudo chmod 755 /Ubuntu/home
ls -ld /Ubuntu/home

```
You should see
```
drwxr-xr-x 2 root root 4096 2008-06-27 14:52 /Ubuntu/home
```
```

sudo mkdir /Ubuntu/home/$user
sudo chown -R $user:$user /Ubuntu/home/$user
ls -ld /Ubuntu/home/$user
```

You should see
```
**drwxr-xr-x** 2 root root 4096 2008-06-27 14:52 /Ubuntu/home/abhishek
```
Make sure there is a "d" at the beginning of the line. If there is no "d", then /Ubuntu/home/abhishek is a file, rather than a directory. If /Ubuntu/home/abhishek is a file, then
```

sudo rm /Ubuntu/home/$user
sudo mkdir /Ubuntu/home/$user
sudo chown -R $user:$user /Ubuntu/home/$user
ls -ld /Ubuntu/home/$user

``` 


```
sudo mkdir /oldhome
ls -ld /oldhome
```

You should see
```
drwxr-xr-x 2 root root 4096 2008-06-27 14:52 /oldhome
```
```

sudo mount /dev/sda2 /oldhome
mount
```

One of the lines should say
```
/dev/sda2 on /oldhome type ext3 (rw)

```
```
cd /oldhome/$user
pwd

```
You should see
/oldhome/abhishek

```
find . -print | grep  "^\./\."     # This will show you what you are about to copy over

find . -print0 | grep -zZ "^\./\." | cpio --null --sparse -pvd /Ubuntu/home/$user

sudo chown -R $user:$user /Ubuntu/home/$user
cd /Ubuntu/home/$user
ls -laR
```
You should see all your dot files and dot directories.

---

### Post by bhadotia on 2008-06-27
Just one little question when some times the terminal window is full and I want to see the very first command I am unable to do that even if I reach the top of the terminal it shows things somewhere between. 


Why does this happen? And if it does happen how do I get back the omitted text?

---

### Post by unutbu on 2008-06-27
Go to Edit>Current Profile. See (first attachment)
You may have to select it twice... mine is buggy that way. 

Then click on Scrolling tab. (See second attachment) Change the buffer size to the maximum number of lines, which I believe is 100000. That should suffice.

---

### Post by bhadotia on 2008-06-27
```
ubuntu@ubuntu:~$ ls -ld /Ubuntu
drwxr-xr-x 2 root root 60 2008-06-28 01:27 /Ubuntu
```

The number after root is different than yours , is that a problem?

---

### Post by unutbu on 2008-06-27
You are fine. As long as the parts in bold are the same, continue.
```
**drwxr-xr-x** 2 **root root** 60 2008-06-28 01:27 **/Ubuntu**
```

---

### Post by bhadotia on 2008-06-27
```
 sudo mkdir /Ubuntu/home
mkdir: cannot create directory `/Ubuntu/home': File exists
```Is this a problem that the /Ubuntu/home already exists ? Sorry if I ask too many questions:).

Also look at this (this is important!):
```
ubuntu@ubuntu:~$ ls -ld /Ubuntu/home
drw-r--r-- 3 root root 4096 2008-06-27 23:04 /Ubuntu/home
```
It is different than yours:
```
 
drwxr-xr-x 2 root root 4096 2008-06-27 14:52 /Ubuntu/home 
```

---

### Post by unutbu on 2008-06-27
Don't worry. Fire away with the questions.
> 
mkdir: cannot create directory `/Ubuntu/home': File exists

This is fine, you must have already run this command the previous time.

> 
ubuntu@ubuntu:~$ ls -ld /Ubuntu/home
drw-r--r-- 3 root root 4096 2008-06-27 23:04 /Ubuntu/home

Run
```
chmod 755 /Ubuntu/home
```

ls -ld /Ubuntu/home should then look like this:
```
drwxr-xr-x 3 root root 4096 2008-06-27 23:04 /Ubuntu/home
```
If you don't set the 'x' permission for 'group' and 'other' then normal users will not be able to change directory into /Ubuntu/home. That would cause you to be homeless (like what happened to you) when you try to log in. 

Thanks for catching this.

---

### Post by bhadotia on 2008-06-27
The operation is not permitted:
```
ubuntu@ubuntu:~$ chmod 755 /Ubuntu/home
chmod: changing permissions of `/Ubuntu/home': Operation not permitted
ubuntu@ubuntu:~$ ls -ld /Ubuntu/home
drw-r--r-- 3 root root 4096 2008-06-27 23:04 /Ubuntu/home
```

---

### Post by bhadotia on 2008-06-27
sudo worked:
```
ubuntu@ubuntu:~$ sudo chmod 755 /Ubuntu/home
ubuntu@ubuntu:~$ ls -ld /Ubuntu/home
drwxr-xr-x 3 root root 4096 2008-06-27 23:04 /Ubuntu/home
```

---

### Post by unutbu on 2008-06-27
Yes, you need sudo. Sorry!

---

### Post by bhadotia on 2008-06-27
This is a problem , I think:
```
ubuntu@ubuntu:~$ sudo mkdir /Ubuntu/home/$user
mkdir: cannot create directory `/Ubuntu/home/abhishek': File exists
ubuntu@ubuntu:~$ sudo chown -R $user:$user /Ubuntu/home/$user
chown: `abhishek:abhishek': invalid user
ubuntu@ubuntu:~$ ls -ld /Ubuntu/home/$user
drw-r--r-- 66 root root 4096 2008-06-27 23:33 /Ubuntu/home/abhishek
```

---

### Post by unutbu on 2008-06-27
Okay, sorry. My mistake again.

Run 

```
sudo chown -R 1000:1000 /Ubuntu/home/$user
```

This will work as long as you are the first and only user on your machine.

---

### Post by bhadotia on 2008-06-27
It still did not work:
```
ubuntu@ubuntu:~$ sudo chown -R 1000:1000 /Ubuntu/home/$user
ubuntu@ubuntu:~$ ls -ld /Ubuntu/home/$user
drw-r--r-- 66 1000 1000 4096 2008-06-27 23:33 /Ubuntu/home/abhishek
```
I am the only user . I don't know if I am the first though:)

---

### Post by unutbu on 2008-06-27
It may not look right to you, but it worked. 
You are user 1000. Go on.

Erm. Let's get those permissions right

```
chmod 755 Ubuntu/home/$user
```

---

### Post by bhadotia on 2008-06-27
This came when I ran that last command:
```
chmod 755 Ubuntu/home/$user
chmod: cannot access `Ubuntu/home/abhishek': No such file or directory
```


The permissions are unchanged:
```
 ls -ld /Ubuntu/home/$user
drw-r--r-- 66 1000 1000 4096 2008-06-27 23:33 /Ubuntu/home/abhishek
```

---

### Post by unutbu on 2008-06-27
What is going on with me today?
```
sudo chmod 755 /Ubuntu/home/$user
```

---

### Post by bhadotia on 2008-06-27
Don't worry! Happens with me everytime :)

```
ubuntu@ubuntu:~$ sudo chmod 755 /Ubuntu/home/$user
ubuntu@ubuntu:~$ ls -ld /Ubuntu/home/$user
drwxr-xr-x 66 1000 1000 4096 2008-06-27 23:33 /Ubuntu/home/abhishek
```

---

### Post by unutbu on 2008-06-27
Ok, looking good. Proceed.

---

### Post by bhadotia on 2008-06-27
When I do:
```
find . -print | grep  "^\./\."
```I see many such things (though compared to others there number is small):
```
find: ./.openoffice.org2: Permission denied


find: ./.gconf: Permission denied


find: ./.purple: Permission denied
find: ./.googleearth: Permission denied



```Are these problems? I mean that "Permission denied".

---

### Post by unutbu on 2008-06-27
Yes, these are problems, and they are my fault. Sorry.
Try this:
```
sudo find . -print | grep  "^\./\."     
sudo find . -print0 | grep -zZ "^\./\." | sudo cpio --null --sparse -pvd /Ubuntu/home/$user

sudo chown -R 1000:1000 /Ubuntu/home/$user
```

---

### Post by bhadotia on 2008-06-27
I think it worked:

```
 ls -laR
.:
total 596
```

There was a long list after that which I did not post. 

What do you think?

---

### Post by bhadotia on 2008-06-27
I've booted into ubuntu . The /home/abhishek has got the . files and directories but when  I go into /data I see nothing . When I do:
```
abhishek@ubuntu:~$ sudo mount -a
mount: mount point /data does not exist
```

In Gparted I see that sda2 has no nothing mounted on it . Also sda2 (37 GB drive) is not there in the Computer window along with my other partitions.

---

### Post by bhadotia on 2008-06-27
I did this :

```
abhishek@ubuntu:~$ sudo mount -a
mount: mount point /data does not exist
```
And that did the trick . Thank you vvvvvvvvvvvvveeeeeeeeerrrrrrrrrryyyyyyyy much:)

---

### Post by unutbu on 2008-06-27
Um, I'm not sure what you did at the end, but if you say it works, I'm very happy! :popcorn:

---

### Post by bhadotia on 2008-06-27
There are still some problems every folder I create in the new home folder shows up on the desktop it seems the home is also behaving like the Desktop folder (there I also see the same emblem on the abhishek folder that I used to see on my desktop folder in the old home folder).

The sda2 does not show up as a 37GB media in the computer window of the nautilus.

Any suggestions on how to remove these?

---

### Post by unutbu on 2008-06-27
Please post
```

ls -ld ~/Desktop
```

> The sda2 does not show up as a 37GB media in the computer window of the nautilus.
I'm not very familiar with nautilus. Where is it supposed to show up? Perhaps post a small picture...

---

### Post by bhadotia on 2008-06-27
Look at this:
```
 
 ls -ld ~/Desktop
ls: cannot access /home/abhishek/Desktop: No such file or directory
```Here is the screen shot of the nautilus computer window(the filesystem is my 17GB ubuntu / partition):

---

### Post by bhadotia on 2008-06-27
> **unutbu said:**
> Um, I'm not sure what you did at the end, but if you say it works, I'm very happy! :popcorn:
Sorry pasted the wrong terminal output:). The actual thing I did was:

"sudo mkdir /data
sudo mount /dev/sda2 /data"

---

### Post by unutbu on 2008-06-27
Have you made the links described in this post [http://ubuntuforums.org/showpost.php?p=5273956&postcount=21](http://ubuntuforums.org/showpost.php?p=5273956&postcount=21)

This should make ~/Desktop a symlink to /data/Desktop.

---

### Post by bhadotia on 2008-06-27
Sorry I forgot to do that but after making the the links I see all the links placed on my desktop. Also the correct commands were:
```
ln -sf /data/abhishek/Desktop Desktop
abhishek@ubuntu:~$ ln -sf /data/abhishek/Documents/ Documents
abhishek@ubuntu:~$ ln -sf /data/abhishek/Music/ Music
abhishek@ubuntu:~$ ln -sf /data/abhishek/Pictures Pictures
abhishek@ubuntu:~$ ln -sf /data/abhishek/Videos/ Videos
```

And not :
```
ln -sf /data/Desktop Desktop
ln -sf /data/Music Music
ln -sf /data/Pictures Pictures
ln -sf /data/Videos Videos

```
These just placed broken links.

I am not sure about these commands . Should these also be changed as above?
```
ln -sf /data ".wine/drive_c/windows/profiles/abhishek/My Documents"
ln -sf /data ".ies4linux/ie6/drive_c/windows/profiles/abhishek/My Documents"
ln -sf /data ".ies4linux/ie7/drive_c/windows/profiles/abhishek/My Documents"
```

---

### Post by unutbu on 2008-06-27
Oh yes. Once again my mistake.
/dev/sda2 used to be mounted at /home, so the first directory in /dev/sda2 is abhishek. I had been thinking it was just the data inside abhishek. Mea culpa.

Still, even though I made a mistake, you don't have to live with it.

I think having all your data at /data/abhishek will make things a bit inconvenient. Wouldn't you rather have it at /data? If so, move the data up one folder then delete the empty /data/abhishek directory, and then
run
```
ln -sf /data/Desktop Desktop
ln -sf /data/Music Music
ln -sf /data/Pictures Pictures
ln -sf /data/Videos Videos
ln -sf /data ".wine/drive_c/windows/profiles/abhishek/My Documents"
ln -sf /data ".ies4linux/ie6/drive_c/windows/profiles/abhishek/My Documents"
ln -sf /data ".ies4linux/ie7/drive_c/windows/profiles/abhishek/My Documents"
```

If you prefer the data at /data/abhishek, then indeed you should change the other ln commands to
```

ln -sf /data/abhishek ".wine/drive_c/windows/profiles/abhishek/My Documents"
ln -sf /data/abhishek ".ies4linux/ie6/drive_c/windows/profiles/abhishek/My Documents"
ln -sf /data/abhishek ".ies4linux/ie7/drive_c/windows/profiles/abhishek/My Documents"
```

---

### Post by bhadotia on 2008-06-27
Yes but all the links now appear on my desktop . My /home is the same as /home/Desktop.

---

### Post by unutbu on 2008-06-28
What happens when you make ~/Desktop a simple empty directory:

```
rm ~/Desktop
mkdir ~/Desktop
```

Does that make your desktop clean?

---

### Post by |{urse on 2008-06-28
im confuzzled. With one kernel or two? I've heard of using transient home directories. definitely would be cool. Wouldn't it be easier to schedule a cron job to run a script (using dd perhaps) that would populate your settings and files across a few seperate /home(s)?

---

### Post by unutbu on 2008-06-28
Suppose Ubuntu uses GIMP 2.4 and SUSE uses GIMP 4.0 (I know that's not true, but just suppose). Suppose both versions wrote to a config file called ~/.gimprc (I know this is not true either, but bear with me! :))
Then when bhadotia logs in to Ubuntu and uses GIMP for the first time a ~/.gimprc version 2.4 is written. And when he then logs in to SUSE, GIMP 4.0 will complain that he is using an old ~/.gimprc -- or worse, it will simply crash. 

Sorry I don't have a better example than picking on good old GIMP, but I hope this hypothetical example gives you one reason why you just can't copy config files across two distributions.

---

### Post by bhadotia on 2008-06-28
After using the above commands I still have all the links placed on my desktop . There is also a folder named dwhelper ,about which I forgot to tell you,which belongs to a firefox plug-in download helper . It was there in my old home directory. It always comes back even if I delete it.

---

### Post by bhadotia on 2008-06-28
This is what I did : alt+f2 , gksudo nautilus , copied the whole /data into /home merging and replacing files and directories which already existed (I could do that coz I had only 10 GB data on /data and some 12 GB space left on /) and then restarted and everything was back to normal.

Ok.. enough  experimenting, I think I will reinstall my whole system now (including suse) to clean up all the mess I,ve created.

Any advices on what should be the  partitioning scheme to get the best out of both distros?

---

### Post by the8thstar on 2008-06-28
I used the same /Home for Ubuntu and Ubuntu Studio on a different partition. Both were 8.04. 

The only problem I encountered was that my desktop was always reverted to the ugly default Gnome icons in Ubuntu Studio, no matter what I did in Ubuntu Standard to change them.

Loading time was also longer.

---

### Post by bhadotia on 2008-06-28
I think I have a problem . I just reinstalled ubuntu. I mounted  /data on a 43 GB partition. But I not the owner of /data so I cannot write or read from there. Can some please tell me how to change the permission. Here is how my partition table looks like now:
```
abhishek@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000837a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7627    61263846    5  Extended
/dev/sda2            7870        9729    14940450   83  Linux
/dev/sda3            7628        7869     1943865   83  Linux
/dev/sda5               1        1824    14651217   83  Linux
/dev/sda6            1825        2152     2634628+  83  Linux
/dev/sda7            2153        2334     1461883+  82  Linux swap / Solaris
/dev/sda8            2335        7627    42515991   83  Linux
```
/data is on sda8.
Also , please comment what you think about this partition scheme. I've made separate 2.5 GB partitions for /home of both suse and ubuntu. Some 15 GB is partitions for / of ubuntu and suse. swap will obviously be shared.

---

