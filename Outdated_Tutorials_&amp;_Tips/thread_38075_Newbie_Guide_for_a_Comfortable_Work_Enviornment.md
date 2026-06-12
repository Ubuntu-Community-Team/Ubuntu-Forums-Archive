---
title: "Newbie Guide for a Comfortable Work Enviornment"
date: 2005-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by cinematography on 2005-05-29
Even though Ubuntu is one of the best, if not the best, Linux distributions available, it still lacks certain standard features many of us have become accustomed to. This tutorial will help point out easy ways to install and setup some useful things to make working in Ubuntu easier.

NOTE: This tutorial is still a work in progress. It's designed to be a simplified guide that doesn't overwhelm, and give you just what you need to feel comfortable with Ubuntu. For a more detailed guide, go here: [http://ubuntuguide.org/](http://ubuntuguide.org/)

[color=red][SIZE=3]*** Helpful Tip: Installing Programs**[/SIZE][/color]
Linux installs programs differently than Windows. Linux uses repositories (download links) to get and install programs. To add, remove, and update programs through these links, use the Symantic Package Manager under System -> Administration. It makes life a lot easier. apt-get is another great tool for getting programs. It is ran through the terminal. 


[color=red][SIZE=3]*** Helpful Tip: Updating Programs**[/SIZE][/color]
Some programs like Azureus apply updates automatically when you open them. To update these programs without hitches, be sure that you open them through your root terminal.


[color=red][SIZE=3]*** Editing your Repository Source File**[/SIZE][/color]
Enter [COLOR=Blue]*sudo gedit /etc/apt/sources.list*[/COLOR] into a terminal.
And then run the update: [color=blue]*sudo apt-get update*[/color]


[color=red][SIZE=3]*** Installing .deb files**[/SIZE][/color]
In the terminal, enter this command:
[color=blue]*sudo dpkg -i TheNameOfTheFile.deb*[/color]


[color=red][SIZE=3]*** Turning off Ubuntu Spatial**[/SIZE][/color]
If you want to keep the last folder open while navigating through folders.

Open Configuration Editer in Applications -> System Tools -> Configuration Editor. 

In the Configuration Editor, go to Nautilus Preferences under Apps -> Nautilus -> Preferences. 

Under Nautilus Preferences, find and select 'no_ubuntu_spatial'. 


[color=red][SIZE=3]*** Associating files with programs of your choice**[/SIZE][/color]
Right click the file -> Properties -> Open With


[color=red][SIZE=3]*** Installing codecs for mp3 and mpeg**[/SIZE][/color]
Ubuntu Addon Package: 
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

or Unofficial Ubuntu 5.04 Starter Guide
[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#codecs](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#codecs)


[color=red][SIZE=3]*** Installing TrueType fonts[/SIZE]**[/color]
Ubuntu Addon Package: 
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

Default font settings for Firefox Windows:
Proportional --- Serif --- 16
Serif --- Times New Roman
Sans-Serif --- Arial
Monospace --- Courier New --- 13

Minimum Font Size [none]


[color=red][SIZE=3]*** Installing Java for Firefox internet browser**[/SIZE][/color]
Ubuntu Addon Package: 
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

After you have Java installed, enter the following code into your root terminal: 
[COLOR=Blue][i]cd /usr/lib/mozilla-firefox/plugins
ln -s /usr/java/jre**[check directory for full name]**/plugin/i386/ns7/libjavaplugin_oji.so .[/i][/COLOR]


[color=red][SIZE=3]*** Installing a visible CD burning program with GUI**[/SIZE][/color]
To install Gnomebaker, the Nero for Linux Ubuntu, enter the following into your command line terminal: 
[color=blue]*sudo apt-get install gnomebaker*[/color]

[color=red][SIZE=3]*** Installing Rar for Linux**[/SIZE][/color]
Enter the following into a root terminal: 
[COLOR=Blue]*sudo apt-get install rar unrar*[/COLOR]


[color=red][SIZE=3]*** Installing Wine**[/SIZE][/color]
Open repository source file by entering the following into the root terminal:
[COLOR=Blue]*sudo gedit /etc/apt/sources.list*[/COLOR]

Paste these lines at end of file:
[COLOR=Blue][I]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/[/I][/COLOR]

Save and close the file.

Enter the following into root terminal:
[COLOR=Blue][I]sudo apt-get update
sudo apt-get install wine winesetuptk[/I][/COLOR]

(optional) Right click .exe file, left click 'open with other...", and enter 'wine' into the custom command space.


[color=red][SIZE=3]*** Accessing files on a Windows partition**[/SIZE][/color]
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

[COLOR=Blue][I]sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222[/I][/COLOR]

Then go to /media/windows to access your Windows files.


[color=red][SIZE=3]*** To navigate through the GUI as root**[/SIZE][/color]
Enter [COLOR=Blue]**gksudo nautilus**[/COLOR] into a terminal.


[color=red][Size=3]*** Hear multiple sounds using Both ESD & ALSA?**[/size][/color]
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

Following this guide could help solve other problems you may encounter with Realplayer and XMMS.

[QUOTE=Gandalf]Hello there,
This is just a clean and better organised guide of varunus's HowTo located [here](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound). So primarily all the credits go to him.

This HowTo will give you instruction on enabling software mixing, to avoid application problems like Audacity needing killall esd to work as well as Skype [now Skype will no longer crash if you receive a message or a call (when it try to play sound in fact)], so let's get to work shall we ?? :-P.


[list=1]We need to install libesd-alsa0 so
```

sudo apt-get install libesd-alsa0

```

[*]We need to create /etc/asound.conf, so
```

sudo gedit /etc/asound.conf

```
Insert into it:
```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}

```

[*]We need to change /etc/esound/esd.conf contents so:
```

sudo mv /etc/esound/esd.conf /etc/esound/esd.conf_backup
sudo gedit /etc/esound/esd.conf

```
Insert into it:
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

[*]Now **You** need to change ubuntu sound server to alsa (you can leave it ESD but better use alsa because it has better sound handling):
```

gstreamer-properties

```
Change both (in the Audio Tab not the Video) from ESD to ALSA so it looks just like the picture:
[[IMG]http://img104.echo.cx/img104/3140/screenshotmultimediasystemssel.th.png[/IMG]](http://img104.echo.cx/my.php?image=screenshotmultimediasystemssel.png)
[/list]
All that's left now is to restart your computer (after restart you must hear sound) to enable these changes. Also configure XMMS or Beep-media-player (or any player) to use ALSA instead of eSound/ESD. If you hear a strange sound, just change everything back to ESD. If everything worked correctly, now Audacity & Skype will work normally and all the program will play sound using either Alsa or ESD.
[INDENT]Correct beep-media-player configuration:
[[IMG]http://img100.echo.cx/img100/7397/screenshotbmppreferences3np.th.png[/IMG]](http://img100.echo.cx/my.php?image=screenshotbmppreferences3np.png)
[/INDENT]
***** If you couldn't play any sounds using ALSA then your /etc/asound.cond & /etc/esound/esd.conf needs some more advanced tweaking (or your sound card just won't support it).

***** The codes above are to be done inside a terminal window.

Thanks to [varunus](http://ubuntuforums.org/member.php?userid=2328) for the [original](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound) HowTo and to [Vaportrail](http://ubuntuforums.org/member.php?userid=5069) for the correct /ets/asound.conf contents.

Enjoy everyone :D.[/QUOTE]

[color=red][Size=3]*** Windows floppies have shortened file names and you want to see full name?**[/size][/color]
Make sure you make a backup of the fstab file before editing it.

Enter the following into your terminal: 
[color=blue]*sudo gedit /etc/fstab*[/color]

Replace this line: 
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

With this line: 
/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

Save and reboot.

---

### Post by rider343 on 2005-05-29
:) Great!!!

---

### Post by dejitarob on 2005-05-30
[http://ubuntuguide.org/](http://ubuntuguide.org/)
[http://ubuntuforums.org/showthread.php?t=22646](http://ubuntuforums.org/showthread.php?t=22646)

---

### Post by cinematography on 2005-05-31
[QUOTE=dejitarob][http://ubuntuguide.org/](http://ubuntuguide.org/)
[http://ubuntuforums.org/showthread.php?t=22646](http://ubuntuforums.org/showthread.php?t=22646)[/QUOTE]
Yeah. I know about those guides. They have too much information though. This guide is designed to just give you what you need to get started. And on a side note, the MP3 solution in the guide you posted didn't work for me. [-X

---

