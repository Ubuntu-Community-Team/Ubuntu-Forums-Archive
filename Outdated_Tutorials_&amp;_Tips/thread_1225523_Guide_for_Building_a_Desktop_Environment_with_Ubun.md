---
title: "Guide for Building a Desktop Environment with Ubuntu Minimal"
date: 2009-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Buce on 2009-07-28
This thread is intended as a starting point for people who want to build their desktop environment from the ground up using Ubuntu. It assumes you know how to install ubuntu on your computer, and know how you want your hard drive partitioned. Above all, it assumes you are familiar and comfortable with the command line. Bash scripting might also come in handy, but it's certainly not necessary. Actually, I might not even include the one script I use; I'm just putting things down as I think of them, in an order that hopefully bears some resemblance to sanity. Forgive me for how sparse this is; I wish I had the time to do a comprehensive how-to, but I guess you'll just have to make do with getting what you pay for. But consider this guide to be released under the WTF License -- if you want to take it, make it better, and make it your own, be my guest. Until someone does that, feel free to post comments, corrections and suggestions. I'll try to add them to this post in a not-too-infrequent manner.

I did this with Ubuntu Hardy Heron (8.04) on a Dell Inspiron E1505 Laptop. My goal was to get a simple personal computing environment running using the fluxbox desktop manager, which is a much more lightweight than GNOME, KDE, or even XFCE (or so I'm told). 

The general procedure here is:
0. Back up your data
1. Get a working commandline install of ubuntu on your computer (Use the Alternate CD instead of the Minimal CD if you don't have ethernet)
2. Get internet so you can update everything (I have no ethernet access, so this means getting wireless up manually from the commandline, using the CD as a repo if necessary)
3. Install xorg and a Window Manager (WM) or Desktop Environment (DE) of your choice (fluxbox in my case)
4. Install a web browser of your choice (Firefox in my case) so you can google things
5. Install and configure everything else you need, starting with drivers and working your way up to apps you use for personal use

I'll embed headings in pentuple-hash-symbols, so just hit Ctrl+F and search for '#####' (without the quotes) to get a more comprehensive rundown of what's going on in this guide.

##### Install Ubuntu #####

So, we're installing a minimal/command-line-only version of Ubuntu. First and foremost, BACK UP ALL YOUR PERSONAL FILES AND DATA. Download and burn either the Ubuntu MinimalCD or AlternateCD image. Pop it into your computer, boot to it, and install from it. If you're using the AlternateCD, hit F4 at the first screen to pop up and select the option that says something like 'command line install' before continuing through the prompts. If you're used to the LiveCD, this might be scary, as it's a bunch of ugly blue and grey screens, but don't worry. It's pretty user friendly if you just read the text.

Be absolutely careful about partitioning, as it's a good way to lose all your data and personal files. Hopefully you've backed it all up anyway so it's not a problem, but think really hard when you get to the partitioning step about whether there's anything you forgot to back up. There's no turning back after formatting the drive.

Also, the step that tries to automatically configure your network might fail, as it did for me. No worries, we can do it manually later -- but you can do it manually now if you want and know how.

##### Assemble Internetz #####

Hopefully, you've got a working command line when you boot up now. If not, find a better guide that will walk you through installation, and try again. Google is your friend. That is, if you have access to a computer with google after botching the install. If not, try booting from a live cd such as Ubuntu's LiveCD, Puppy Linux, or Damn Small Linux for internet access. I'd recommend trying them in that order.

Ethernet - Get internet access on your fresh install. For most people, this will hopefully mean plugging in an ethernet cord, typing the commands 'sudo ifconfig eth0 up' and 'ping google.com', and getting a response other than 'ping: unknown host google.com'. If you don't see that error message, you can continue on to the next step. If you do see it, find your ethernet device with 'sudo lshw | less' and use its logical name in place of 'eth0' in those first two commands. If that still doesn't work, you're driver's probably not installed correctly (or at all, maybe). You're on your own.

Wireless - Type this command:
```
sudo lshw | less
```
Find your wireless device. You'll need it's logical name -- mine says it's wmaster0, but I know it's really wlan0. I forget why that is. Sorry. Anyway, in the next bit, replace 'wlan0' with your device's logical name for all commands. Read the comments, don't just copy-paste, and make sure to replace the angled brackets, ie <>, with whatever's relevant.
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
# If you have WPA, doing something like the following might work,
# but I haven't tested this command and it depends on the
# wirelesstools package, I think.
wpa_supplicant -B -Dwext -i wlan0 -c /path/to/wpa/passkey/file.conf
# If you have WEP, do this:
iwconfig wlan0 essid '<network name>'
iwconfig wlan0 key <hex key> # or s:<ascii key>
# If your network isn't encrypted, just use:
iwconfig wlan0 essid '<network name>'

# Whether or not your network is encrypted, type:
dhclient wlan0
ping google.com
```
If you get an error that reads 'ping: unknown host google.com', try configuring your network again. Read the man pages on the commands listed above, maybe, or find a better tutorial for connecting to the internet with the command line. If nothing works, maybe the next paragraph will give you some ideas on how to wing it.

I mentioned you can use the AlternateCD (but not the MinimalCD) as a repository for installing packages you might need. This is really handy when you don't have internet. To do this, type 'sudo nano /etc/apt/sources.list' and uncomment any lines that have 'cdrom' in them. Save and exit (Ctrl+O, Ctrl+X) and then type 'sudo apt-get update'. It'll spew out a bunch of errors, but there should be a line or two starting with 'Hit' indicating that it successfully detected your CD. For this all to work, I think you need to have installed from the Alternate CD, and that CD needs to be in your CD drive. If it works, you should hopefully be able to install any packages you might need to get your internet working. You might even be able to install a GNOME Desktop capable of running nm-applet, which should do all the dirty work for you. But I'll let you and google figure that out.

##### Update Your System #####

If you used the CD as a source to install packages from, edit /etc/apt/sources.list again and comment out all lines that have 'cdrom' in them with a # symbol.

Now, type the commands 'sudo apt-get update' and 'sudo apt-get upgrade'. If you want the newest kernel, type 'sudo apt-get dist-upgrade'. Keep in mind that if you ever add repositories for a newer version of Ubuntu (eg, if you add Intrepid repos to a Hardy install), apt-get will try to upgrade you to the latest version listed in your sources.list file. At least, I think that's how it works.

Anywho, hopefully those commands work and you can go on to the next step. While we're at it, though, let's install hal and esd with 'sudo apt-get install hal esd'. hal is the Hardware Abstraction Layer, and just generally makes life much easier with linux. esd will make your sound work (hopefully -- if not, make sure your soundcard's driver is installed correctly), but will be uninstalled later if you install pulseaudio. Even if you plan to do so, install esd for now so to make sure sound works.

##### Install X #####

Now we need to install a graphical environment so that we can at least access the internet if we need help from google or the ubuntu forums. 'sudo apt-get install xorg fluxbox firefox' will get you everything you need, although you may want to install something other than fluxbox if it doesn't suit you.

If you're new to fluxbox, everything is configured in ~/.fluxbox, so have a look at those files and dig around a bit for some tutorials on how to configure it. My favorite file is ~/.fluxbox/keys, but ~/.fluxbox/startup is definitely worth looking into. Look into adding better themes, too. I don't remember what files or folders control that.

##### File Browser/Manager #####

Using cd and ls is nice, but you might want to have a GUI app to peruse your files, and fluxbox doesn't have one by default. I prefer Thunar, which has a plugin that makes mounting usb's, cd drives, and other devices easy. To install thunar and the optional volume manager plugin, use 'sudo apt-get install thunar thunar-volman'. Assuming you installed hal earlier, all should be well.

##### PulseAudio #####

Quick note: This section describes how to add the canonical repository. You need that repository to install acroread. Just so ya know.

Er, this section gets a bit hairy. The next paragraph is the first thing I tried, with limited success. The paragraph after that is what ultimately worked for me, but I'm not sure if there's anything in the first paragraph that is essential, so I'm leaving it for now. If anybody could try the second thing first and report back on whether or not the first thing is necessary, I'd be very appreciative.

The probably-unnecessary part: I use pulseaudio so that I can mute Flash sounds from the browser without affecting sounds coming from other programs. Install it with 'sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter'. This will uninstall esd, which is no problem, so don't worry. To use pulseaudio, a user must belong to the "pulse-access" and "pulse-rt" groups, so do that with the 'sudo adduser <user> <group>' command.

The necessary part: Follow this guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

After following that guide, sound should (hopefully) work, but flash streams might not show up in pavucontrol. To get them to work, add the canonical repository by adding (or uncommenting, if they're already there) these lines to /etc/apt/sources.list:

```
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
```

Update apt-get, then install the adobe-flashplugin package. Flash should now work with PulseAudio.

##### Configure Touchpad #####

I don't like the default touchpad settings, where the mousepad also lets you scroll and tap-click. To change these settings, open up /etc/X11/xorg.conf with a text editor and find the "SynapticsTouchpad" section. This is what controls your touchpad. I changed mine to look like this:
```
Section "InputDevice"
   Identifier  "SynapticsTouchpad"
   Driver      "synaptics"
   Option      "SendCoreEvents"        "true"  # send events to CorePointer
  #Option      "Device"            "/dev/input/mice"
   Option      "Device"            "/dev/psaux"
   Option      "Protocol"          "auto-dev"
   Option      "SHMConfig"         "false" # configurable at runtime? security risk
#   Option      "LeftEdge"          "1700"  # x coord left
#   Option      "RightEdge"         "5300"  # x coord right
#   Option      "TopEdge"           "1700"  # y coord top
#   Option      "BottomEdge"        "4200"  # y coord bottom
#   Option      "FingerLow"         "25"    # pressure below this level triggers release
#   Option      "FingerHigh"        "30"    # pressure above this level triggers touch
#   Option      "MaxTapTime"        "180"   # max time in ms for detecting tap
   Option      "VertEdgeScroll"    "false"  # enable vertical scroll zone
   Option      "HorizEdgeScroll"   "false"  # enable horizontal scroll zone
   Option      "CornerCoasting"    "true"  # enable continuous scroll with finger in corner
#   Option      "CoastingSpeed"     "0.30"  # corner coasting speed
#   Option      "VertScrollDelta"   "100"   # edge-to-edge scroll distance of the vertical scroll
#   Option      "HorizScrollDelta"  "100"   # edge-to-edge scroll distance of the horizontal scroll
#   Option      "MinSpeed"          "0.10"  # speed factor for low pointer movement
#   Option      "MaxSpeed"          "0.60"  # maximum speed factor for fast pointer movement
#   Option      "AccelFactor"       "0.0020"    # acceleration factor for normal pointer movements
   Option      "VertTwoFingerScroll"   "true"   # vertical scroll anywhere with two fingers
   Option      "HorizTwoFingerScroll"  "true"   # horizontal scroll anywhere with two fingers
   Option      "TouchpadOff"  "2"          # disable scrolling, clicking with touchpad
EndSection
```
Hash marks are comments, just like in BASH. I keep them there in case I ever want to change those settings.

##### GNOME Stuff #####

So, you probably noticed that Firefox looks so ugly you almost wish that IE was an option. You can get some pretty nice-looking gtk2 themes from [http://art.gnome.org/themes/gtk2/](http://art.gnome.org/themes/gtk2/). For these to work, you need to first install the clearlooks engine with 'sudo apt-get install gtk2-engines'. Download and extract the themes you want to ~/.themes, then open up ~/.gtkrc-2.0 with a text editor. Change this line:
```
include "/home/woody/.themes/<name of theme>/gtk-2.0/gtkrc"
```
This seems to make firefox and thunar look nice and pretty, but OpenOffice doesn't take on the theme. If you want it to, you need to make sure that the $OOO_FORCE_DESKTOP variable is set to 'gnome' before OOo is ever started. For fluxbox users, you can do this by adding 'export OOO_FORCE_DESKTOP=gnome' to ~/.fluxbox/startup, making sure to put it above the line that says 'exec fluxbox'. If you're not using fluxbox, you'll have to shop around for where to put that line. You might have to put it outside your home directory, which I hate because I mount /home on a separate partition, ensuring that any configurations changes I make there will be preserved when I install a new distro.

I like to be able to use ctrl+u and ctrl+k in the normal linux way with, say, the address bar in firefox. To get this working, add the following to a new file called ~/.gtkrc-2.0.mine:
```
binding "gtk-clear-text-entry" {
bind "<ctrl>k" {
  "delete-from-cursor" (paragraph-ends, 1)
}
bind "<ctrl>u" {
  "move-cursor" (paragraph-ends, -1, 0)
  "delete-from-cursor" (paragraph-ends, 1)
}
}
class "GtkEntry" binding "gtk-clear-text-entry"
class "GtkTextView" binding "gtk-clear-text-entry"
```
With this code, ctrl+u doesn't quite do the right thing, but it's close enough for me. I just copied this code from somewhere else ages ago, and I'm not sure how to modify it correctly. Nor do I care, really, as I've gotten used to this setup.

##### Firefox Fonts #####

For some reason, you can't select which fonts are used by default for the 'cursive' or 'fantasy' family of fonts. The 'cursive' family is supposed to be displayed as some kind of handwritten font. On Microsoft, I think the default is Comic Sans, which doesn't seem very cursive to me. At any rate, I prefer for cursive fonts to display as some kind of Chancery font. On Ubuntu, your best bet for this is Free Chancery, which can be installed with 'sudo apt-get install t1-cyrillic'. To get Free Chancery to be displayed for cursive fonts in firefox, create a file called ~/.fonts.conf with these contents:

```
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
  <alias>
    <family>cursive</family>
    <prefer>
      <family>Free Chancery</family>
    </prefer>
  </alias>
</fontconfig>
```

It should be apparent from the syntax, I hope, how you would do something similar for the fantasy family.

##### The End #####

That's it. Hope this helps.

---

### Post by Buce on 2009-08-02
Added info on how to force OO.o to use gtk.

---

