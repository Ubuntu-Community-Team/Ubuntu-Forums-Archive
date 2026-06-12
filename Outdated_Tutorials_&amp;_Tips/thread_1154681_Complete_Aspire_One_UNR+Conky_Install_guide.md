---
title: "Complete Aspire One UNR+Conky Install guide"
date: 2009-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by relst-nl on 2009-05-10
Hy All,
This is my first tut here, normally I would publish them on my own website: [http://relst.nl]("http://relst.nl"). But i want to make them better, and that can only be done with your help. So Please give some tips an suggestions about how i can make this tutorial better.

 This is my ideal Ubuntu Configuration For yer Netbook. Follow this steps to get a good netbook. (In My Opinion.)

The guide has 4 main parts:
1- Installing UNR
2- LXDE + Conky
3- SSD Fixes
4- Media Codecs 

I hope you like it, and please comment for suggestions :)
 Install Ubuntu Netbook Remix: 

(You need at least a 1 gigabyte USB Stick. It cannot be an SD card, The Aspire one cannot boot from that.) 
Making the USB Key

Visit this page and download the .img file: [http://www.ubuntu.com/getubuntu/download-netbook]("http://www.ubuntu.com/getubuntu/download-netbook"). 

Download Disk Imager from [https://launchpad.net/win32-image-writer/+download]("https://launchpad.net/win32-image-writer/+download") 

Insert your USB Stick 

Note the drive letter assigned to your USB key (Like E:\ or F:\.)

Start Disk Imager 

Select the downloaded file and target device, and click "Write" 

Remove your USB Key when the operation is complete 
Installing UNR

Then put your USB Key in the Aspire One and boot it. Press F12 on the ACER Logo and select your USB key. 

Select your desired language and start UNR with the Install option.
Follow all the steps on the screen, but when partitioning select Manual, then remove all partitions (You will loose all your data so make sure you have a good backup.) Make a 256 MB swap partition, and use the remaining space for an EXT2!!! formatted partition with mount point /. Then continue with the installation.



Tweaking:

UNR needs some tweaking to make it very fast and good. You can do all sub-steps individually, but please do not skit the step for the SSD. Thats Important if you want to enjoy your Netbook a little longer.



1- LXDE
Installing LXDE

When UNR is installed boot it up and login. 
The first thing we are going to do is install LXDE and get rid of the heavy UNR interface. Copy and paste these things in the terminal:

**sudo apt-get install lxde**

Enter your password and if needed press Y. 
Then logout and select Session: LXDE. Make it the default session.
You will notice how fast it boots.

Adding Networkmanager to the LXDE Panel

We need to add the networkmanager to the panel so you just can use wireless and 3G networks when needed. 
Press ALT+F2 and type this: 

**gksu gedit /etc/xdg/lxsession/LXDE/autostart **

Enter your password, and then a text editor will open.

Now add this line at the bottom of the file:

```
@nm-applet
```

Then save the file and exit. At the next startup you will be asked to enter your password and Network Manager will start up. If you don't want to enter your password each time you login then make sure you give Networkmanager permissions to the keyring.



Installing Conky and make it work with LXDE

If we want to make conky work with LXDE and PcmanFM then we need to do this:

Paste this in a terminal:

**sudo apt-get install conky**

Enter your password and press Y if needed.

Then we need to make conky work with PcmanFM.

Paste the following in a terminal

```
wget http://relst.nl/downloads/.conkyrc && mv .conkyrc ~/.conkyrc -f -v
```(Don't know if this is allowed, if not, then remove it, the content can be found at the bottom pf the tut...)


(This will download a good conkyrc file and place it in your home directory.)

Then add conky to the startup file, Press ALT+F2 and enter this:

**gksu gedit /etc/xdg/lxsession/LXDE/autostart **

Then add this line at the bottom of the file:

*conky*

Then save and quit.

Now conky will start up and not interfere with PcmanFM.



Finishing the panel

The LXDE panel needs finishing, so we are going to add a battery monitor and a volume manager to it.

Right-click the panel and select: Panel Settings

Click the tab: Panel Applets

Click Add and select:

Battery Monitor

Click Add.

Do it again but then select: Volume Control. 

Optional: If you want to save space on the window list, you can click: Task Bar (Window List) and select Edit, and then mark: Icons Only. This will save a lot of space.

The click Close.




These were the most LXDE things. You can set a wallpaper or so, but this is about it.



SSD Fixes

These tips will save the most of your SSD. If you have a hard drive, then you can skip the entire SSD part. 

Fire up a terminal ( ALT+F2 &#8594; gnome-terminal).

The Bold lines can be just copied and pasted, the Itallic lines will require a little reading.
[B]
gksudo gedit /etc/fstab[/B]

Replace &#8220;relatime&#8221; with &#8220;noatime&#8221; everywhere you see it. (Probably 1 or 2 times.)

Add these lines(The Italic ones):

```
tmpfs /var/log tmpfs defaults 0 0
tmpfs /tmp tmpfs defaults 0 0
tmpfs /var/tmp tmpfs defaults 0 0
```

Save and close.

**gksudo gedit /boot/grub/menu.lst**

Find this line: 

**## ## End Default Options ##**

Underneath are the Boot menu options. You will need the first one. Not the recovery or the Memtest. 

After the: root line of the normal boot menu add this: ```
elevator=noop
```. 

Save and close.

**gksudo gedit /etc/rc.local**

Above the rule: **exit 0**; add this:

```
# Economize the SSD
sysctl -w vm.swappiness=1 # Strongly discourage swapping
sysctl -w vm.vfs_cache_pressure=50 # Don't shrink the inode cache aggressively
for dir in apparmor apt cups dist-upgrade kismet fsck gdm installer samba unattended-upgrades ;
do
if [ ! -e /var/log/$dir ] ; then
mkdir /var/log/$dir
fi
done
```



Save and close.

**gksudo gedit /etc/init.d/sysklogd**

Replace this:

```
fix_log_ownership()
for l in `syslogd-listfiles -a`
do
chown ${USER}:adm $l
done
}
```
with this:

```
fix_log_ownership()
{
for l in `syslogd-listfiles -a --news`
do
# Create directory for logfile if required
ldir=$(echo ${l} | sed 's/[^\/]*$//g')
if [ ! -e $ldir ] ; then
mkdir -p $ldir
fi

# Touch logfile and chown
touch $l && chown ${USER}:adm $l
done
} 
```




Save and close.


This was the SSD part. Now we are going to the Media Part.



Installing Video and Audio Codecs

Paste the following lines in the terminal:

[B]sudo synaptic
[/B]
This wil fire up synaptic. Do not close the terminal.

Search for mp3, and mark the following stuff:

[B]Gstreamer extra plugins 

Gstreamer ffmpeg video plugin 

Ubuntu restricted extras 

VLC media player 

Mplayer Movie Player 

SMPlayer 

Audacious 

gxine[/B]

Agree with all the windows, and install the packages. This will add flash player, MP3 support and good video support. At me I could play all the video's I needed.

We also need to add support for rar and 7zip. In the terminal paste this:

**sudo apt-get install rar unrar pk7zip-full**

And when needed press Y.


This was the media part and the last part of this tut.






Final Notes

This tutorial is all on your own risk, With me it worked. I hope you now have a good netbook. I atleastly have.







Made with help of: 

[http://sites.google.com/site/computertip/aa1](http://sites.google.com/site/computertip/aa1)

[http://lxde.org](http://lxde.org) 

 
The tut can also be found on: [this site.]("http://relst.nl/site/index.php/handleidingen/197-complete-aspire-one-install-guide-for-ubuntu-netbook-remix-in-english.html")


Contents of .conkyrc:

```
# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour black


# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_class Conky
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 4

gap_y 4

# stuff after 'TEXT' will be formatted on screen


TEXT
${color }$nodename ${hr}
${color #9fb6cd}Kernel:$alignr${color }$kernel
${color #9fb6cd}UpTime: $alignr${color }$uptime
${cpugraph 20,130 000000 ffffff}
${color #9fb6cd}Load: $alignr${color }$loadavg
${color #9fb6cd}Processes: $alignr${color }$processes
${color #9fb6cd}Running: $alignr${color }$running_processes
${color #9fb6cd}Highest CPU:
${color #ddaa00} ${top name 1}$alignr${top_mem cpu 1}
${color lightgrey} ${top name 2}$alignr${top cpu 2}
${color lightgrey} ${top name 3}$alignr${top cpu 3}
${color lightgrey} ${top name 4}$alignr${top cpu 4}
${color lightgrey} ${top name 5}$alignr${top cpu 5}
${color #9fb6cd}Highest MEM:
${color #ddaa00} ${top_mem name 1}$alignr${top_mem mem 1}
${color lightgrey} ${top_mem name 2}$alignr${top_mem mem 2}
${color lightgrey} ${top_mem name 3}$alignr${top_mem mem 3}
${color lightgrey} ${top_mem name 4}$alignr${top_mem mem 4}
${color lightgrey} ${top_mem name 5}$alignr${top_mem mem 5}
${color #9fb6cd}CPU TEMP:$alignr${color}${hddtemp /dev/sda}
${color #9fb6cd}MEM: $alignr${color } $memperc% $mem/$memmax
${membar 3,100}
${color #9fb6cd}ROOT: $alignr${color }${fs_free /}/${fs_size /}
${fs_bar 3,100 /}




${color #9fb6cd}${time %a, } $alignr${color }${time %e %B %G}
${color #9fb6cd}${time %Z, }$alignr${color }${time %H:%M:%S}
${color lightgray}${execi 40000 cal}
${texeci 60 pymetar EGBB}


```

---

### Post by jpeddicord on 2009-05-12
Approved; thanks for your tutorial contribution! :)

---

### Post by rreyes1316 on 2009-05-28
Have you had any problems with the mic? I have been looking for a solution to this problem and have been unsuccessful. I have UNR installed on an Aspire One 10" D150. My Mic does not work with Skype I have made sure that the mic is not on mute in the volume control and also tried to change the audio setting under the Preferences. I have done a complete reinstall and made sure to install medibuntu, restricted extras, keyring, and all codecs. This is just not working. I have tried to download the latest alsa drivers but do not know how to compile them for install or back up the old drivers just in case. Later, It occurred to me that perhaps I should try another app. Sure enough, the mic did not record using other mic supported apps. So that rules out skype as the problem. 

Anyone have a solution?

---

### Post by relst-nl on 2009-06-12
> **rreyes1316 said:**
> Have you had any problems with the mic? I have been looking for a solution to this problem and have been unsuccessful. I have UNR installed on an Aspire One 10" D150. My Mic does not work with Skype I have made sure that the mic is not on mute in the volume control and also tried to change the audio setting under the Preferences. I have done a complete reinstall and made sure to install medibuntu, restricted extras, keyring, and all codecs. This is just not working. I have tried to download the latest alsa drivers but do not know how to compile them for install or back up the old drivers just in case. Later, It occurred to me that perhaps I should try another app. Sure enough, the mic did not record using other mic supported apps. So that rules out skype as the problem. 

Anyone have a solution?
I have a A110, and I tried skype for this time, and it just works with webcam and mic. I cannot test it on a D150. Sorry.

---

### Post by amillionsheep on 2010-02-22
Wow, here's an easier way to do this and still use GNOME:

Assuming you already have Ubuntu Netbook Remix installed and running..

**System > Preferences > Startup Applications**

Uncheck _Netbook-Launcher_

**Press Alt+F2 and run gconf-editor**

Browse to:

apps > nautilus > preferences

On the right, scroll down and check 'show_desktop' to allow desktop icons and desktop right click popups.

**Reboot and log back in**

**Panel **

Right click the Ubuntu icon on far left and select 'Remove from Panel'
Right click the far left of the panel and select 'Add to Panel...' 
Select 'Main Menu' and click add.

Also, for viewing open windows I recommend using the Window Picker vs. Window List or Window Selector.

[B]Conky

[/B]Open a Terminal and type: _sudo apt-get install conky_
Go through the install like normal.

To use someone else's conky config file or edit your own, just download the .conkyrc and put it in your Home Folder. If you can't see it in the file browser it is because it is hidden. Click view in your Home Folder and check 'Show Hidden Files'.

NOTE: Make sure you run Conky as super user because some functions require permissions to access certain information. ie. Press Alt+F2 and type: _sudo conky_ 

Enjoy!

---

### Post by semiferger on 2010-02-23
Congratulations on a wonderful accomplishment - this looks like a great read!
Keep up the good work,

---

