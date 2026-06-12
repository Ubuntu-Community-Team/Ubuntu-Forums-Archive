---
title: "HOWTO: Choose Xorg layout automatically based on ddcprobe"
date: 2007-04-22
forum: Outdated Tutorials &amp; Tips
---

### Post by matja on 2007-04-22
**Description:**
This guide should be able to make GDM (Gnome Display Manager) choose Xorg server layout at startup, based on what you have connected to your VGA port. For instance, if you have a laptop it can automatically start X with a dual monitor setup if an external monitor is connected to the VGA port.

**How it works:**
We create a wrapper script that GDM uses to start X. The script utilizes *ddcprobe* to scan the device connected to the VGA port and find it's *eisa* identifier, which is given to X as the server layout to use. The script makes sure that there exist an identical layout identifier in [COLOR="DarkSlateGray"]xorg.conf[/COLOR], otherwise X is started with the default layout.

*_Note_*: I have not been able to find much information about *ddcprobe*. I chose the *eisa* entry as the identifier based on my very limited range of monitors I connect to my laptop, as it existed and had a unique value for each of them. It shouldn't be a problem to use some other entry of *ddcprobe* as a replacement, just replace every occurence of "eisa" with another entry name in the [COLOR="DarkSlateGray"]startx-custom[/COLOR] script below.

**Credits:**
[LIST]
[*]This is basically [[COLOR="Sienna"]_mfremont_[/COLOR]]("http://ubuntuforums.org/member.php?u=225904")  idea from this [[COLOR="Sienna"]_post_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=347741"), I just modified it a bit (and wrote this guide ;)).
[*][[COLOR="Sienna"]_Joseph Brown_[/COLOR]]("http://ubuntuforums.org/member.php?u=225368") for the idea to use *ddcprobe* to scan the VGA port.
[/LIST]

**Prerequisites:**
[LIST=1]
[*]_Server layouts_ in [COLOR="DarkSlateGray"]xorg.conf[/COLOR] for whatever you want to connect to your computer. This is actually not a real prerequisite as the default server layout will be chosen if the connected device is unrecognized but without them this guide is pretty pointless.
[*]According to the [[COLOR="Sienna"]_documentation_[/COLOR]]("http://packages.debian.org/unstable/x11/xresprobe") I found, *ddcprobe* should work on _i386 and powerpc_ architectures and be able to scan _VGA, DVI and HDMI connectors_. *However, this is only tested on an i386 architecture with a VGA port*.
[*]_GDM_ as display manager, which probably means you're running Gnome. I'm sure this can be done with other display managers too, but this guide will describe how to do it with GDM.
[/LIST]
This is tested on Ubuntu 7.04 (a.k.a. *Feisty Fawn*) Desktop Edition (32bit), with an Intel Mobile 945GM Express chipset laptop.

**Uninstallation:**
Revert [COLOR="DarkSlateGray"]gdm.conf-custom[/COLOR] to it's original state (preferably from a backup made).

**Support:**
I offer [COLOR="Red"]no support[/COLOR] for this guide and it is to be used [COLOR="Red"]at your own risk![/COLOR] I will however _try_ to answer the questions I can if you should post any below.


**The Guide:**
Ok, with all that out of the way, lets begin the guide :)

First off, we need to install the *xresprobe* package if you shouldn't have happened to installed it earlier.
```
$ sudo apt-get install xresprobe
```
This could be a good opportunity to try *ddcprobe* and see if you have an eisa entry. If so, that should be the name of the server layout for your current setup.
```
$ sudo ddcprobe
```
A sample of the output could look like this:
```

id: 1514
eisa: AUO1514
serial: 00000000
manufacture: 1 2005
input: analog signal.
screensize: 26 16
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1280x800@59
monitorid: AUO
monitorid: B121EW01 V5

```
This is (part of) the output for my setup when I have nothing connected to the external VGA port.   Notice that the *eisa* entry is "AUO1514", a string that changes to "DEL700c" (along with a lot of other changes in the output of ddcprobe) when I connect my desktop monitor to the VGA port and restart the computer. In [COLOR="DarkSlateGray"]xorg.conf[/COLOR] I have server layouts accordingly:
```

Section "ServerLayout"
      Identifier "AUO1514"
      *single monitor layout options...*
      ...
EndSection

Section "ServerLayout"
      Identifier "DEL700c"
      *dual monitor layout options...*
      ...
EndSection

```
Next we should create the wrapper startup script for X. You can name it anything you want but this guide will assume it has the full path [COLOR="DarkSlateGray"]/etc/gdm/startx-custom[/COLOR]. The guide also assumes you have gedit as your favorite editor, but you can of course use whichever you like.
```
$ sudo gedit /etc/gdm/startx-custom
```
Copy and paste the following into the file.
```

#!/bin/sh

# Custom script to start X for GDM with the ability to choose server
# layout as the eisa entry of ddcprobe

# Path to xorg.conf
XORG_CONF=/etc/X11/xorg.conf

# Find the current eisa entry of ddcprobe and write it to
# /var/log/gdm/custom
EISA_ENTRY=`ddcprobe | sed -n 's/eisa: //p'`
echo "eisa entry: $EISA_ENTRY" > /var/log/gdm/custom

# Check if the eisa entry is a defined server layout in xorg.conf
# (otherwise X will be started with the default layout)
LAYOUT=""
if [ -f $XORG_CONF ]; then
    if test `sed -n '/section "serverlayout"/I,/endsection/Is/^[ \t]*identifier[ \t]\+"\(.*\)".*/\1/Ip' $XORG_CONF | grep -c -x $EISA_ENTRY` -eq 1; then
	LAYOUT="-layout $EISA_ENTRY"
    else
	echo "did not find $EISA_ENTRY in $XORG_CONF, using default layout" \
	    >> /var/log/gdm/custom
    fi
else
    echo "$XORG_CONF does not exist" >> /var/log/gdm/custom
fi

# run the X server with the eisa entry as layout (if it was defined in
# xorg.conf)
exec /usr/X11R6/bin/X $LAYOUT $*

```
The basic user shouldn't need to modify this script, but since I can count the number of scripts I've created on one hand I might be wrong ;) If you should have changed anything in your setup (such as the location of your [COLOR="DarkSlateGray"]xorg.conf[/COLOR] file), I assume you know Linux sufficiently well to change my script too!

Be sure to make the script executable.
```
$ sudo chmod u+x /etc/gdm/startx-custom
```
We need to tell GDM to use our new wrapper script. This can be done in [COLOR="DarkSlateGray"]/etc/gdm/gdm.conf-custom[/COLOR] with a [server-Standard] section that will override the one in [COLOR="DarkSlateGray"]/etc/gdm/gdm.conf[/COLOR]. First we'll make a backup which can be used to revert GDM to it's original state.
```

$ sudo cp /etc/gdm/gdm.conf-custom /etc/gdm/gdm.conf-custom.backup
$ sudo gedit /etc/gdm/gdm.conf-custom

```
Append the following to the end of this file.
```

[server-Standard]
name=Standard server
command=/etc/gdm/startx-custom -br -audit 0
flexible=true

```
You should make sure that this is just a copy of what is in [COLOR="DarkSlateGray"]/etc/gdm/gdm.conf[/COLOR] with the command entry replaced with the path to our wrapper script (but with the same arguments). While you're at it, check to see that the original command, which we substituted for the path to our wrapper script, is the same as the one at the end of that script, i.e. [COLOR="DarkSlateGray"]/usr/X11R6/bin/X[/COLOR].

This should be all the modifications needed. What's remaining is to create server layouts for all setups you may have with identifiers according to the *eisa* entry in ddcprobe. To aid in this task is the log file [COLOR="DarkSlateGray"]/var/log/gdm/custom[/COLOR], which should contain the *eisa* entry found at startup and a note if it was not found as a server layout in your [COLOR="DarkSlateGray"]xorg.conf[/COLOR].

I hope this will work for all of you! I think of this as a small payback to the Ubuntu community, so it would be a shame otherwise ;). Let me know if you have any use of it,

*Regards Mattias*

---

### Post by minerb on 2007-07-16
I would also like to share an alternative solution.  I am using dual-monitors, and it was a big pain to have to modify the xorg.conf file everytime I undocked my laptop.  So, I wrote a script that determines if an external monitor is attached and uses a specific ServerLayout in the xorg.conf file.

Please make sure that you backup your configuration files before continuing.  I lose many hours of my life when I ignore this advice.

The script uses ddcprobe to determine whether or not the external monitor was attached.  Based upon the output gathered when an external monitor was not present vs. the output gathered when it was present, I was able to get a 0 or 1 result from the following command: ddcprobe | grep --count '^edid: $'

Basically, if ddcprobe returned a line that only said "edid: ", then it would return 1; otherwise, 0.  The result is then stored into a variable.  Then, I use this command: sed '/^\tOption \"DefaultServerLayout\" /c \\tOption \"DefaultServerLayout\" \"Single-Monitor Layout\"' /etc/X11/xorg.conf > /tmp/xorg.conf.tmp

That finds all lines beginning with Option "DefaultServerLayout" and replaces them with Option "DefaultServerLayout" "Single-Monitor Layout".  Then the output is written to /tmp/xorg.conf.tmp.

This assumes that you have setup two ServerLayouts -- one identified by "Single-Monitor Layout" and the other by "Dual-Monitor Layout".  Please read the man page for xorg.conf if you are lost.

Finally, the tmp file replaces the xorg.conf file.

Save your script as 'extMonitor' and place it in the /etc/init.d directory.  Be sure to add 755 permissions using: chmod 755 extMonitor.

To add this script to startup, use: sudo update-rc.d extMonitor defaults 12
On my system, Xorg runs at sequence #13.  Thus, 12 was picked for the sequence # for this script.  I would suggest reading up on update-rc.d using its man page.  You can also download a nice GUI Boot-up Manager under the package named 'bum' using: sudo apt-get install bum

Please feel free to email me with any questions: [email]TurnCoffeeIntoCode@gmail.com[/email]

Here's my script:
```

#!/bin/bash

#To add to startup, use: sudo update-rc.d extMonitor defaults 12

EXTMON=`ddcprobe | grep --count '^edid: $'`
#Will return 0 if an external monitor is NOT plugged in.
#Will return 1 if an external monitor IS attached.
#Requires xresprobe package containing ddcprobe.

echo -e -n " * Determining if an external monitor is present...\t"

if [[ "$EXTMON" == "0" ]]
	then
	echo -e "Ext. Monitor not detected.\n\tUsing single-monitor mode."
	#Replace lines beginning with "DefaultServerLayout" with "DefaultServerLayout" "Single-Monitor Layout"
	sed '/^\tOption \"DefaultServerLayout\" /c \\tOption \"DefaultServerLayout\" \"Single-Monitor Layout\"' /etc/X11/xorg.conf > /tmp/xorg.conf.tmp
else
	echo -e "Ext. Monitor detected.\n\tUsing dual-monitor mode."
	#Replace lines beginning with "DefaultServerLayout" with "DefaultServerLayout" "Dual-Monitor Layout"
	sed '/^\tOption \"DefaultServerLayout\" /c \\tOption \"DefaultServerLayout\" \"Dual-Monitor Layout\"' /etc/X11/xorg.conf > /tmp/xorg.conf.tmp
fi

#Copy /tmp/xorg.conf.tmp to /etc/X11/xorg.conf
cp /tmp/xorg.conf.tmp /etc/X11/xorg.conf
#Cleanup
rm /tmp/xorg.conf.tmp

```

---

### Post by uncoolbob on 2009-02-28
Thanks for the useful HOW-TO - saved lots of manpage reading...

I found with my Powerbook G4 (PPC) that ddcprobe only detects the built-in LCD, regardless of what's plugged in.  I found that dmesg contained enough information for me so:

/etc/gdm/startx-custom
```

#!/bin/sh

# Custom script to start X for GDM with the ability to choose config
# file based on dmesg output

# Path to xorg.conf
XORG_CONF=/etc/X11/xorg.conf.safe.internal

if (dmesg | grep Display-B > /dev/null); then
  XORG_CONF=/etc/X11/xorg.conf.safe.external
fi

# run the X server with the eisa entry as layout (if it was defined in
# xorg.conf)
exec /usr/X11R6/bin/X -config $XORG_CONF $*

```

Of course, this only works on reboot, but I think that with the "nv" open source driver (no proprietary binary-only drivers for PPC) this is the only option.

---

### Post by psyray on 2009-06-03
hi all,

Thanks for this great Howto.

But, this trick doesn't work with ubuntu amd64, because of non compatiblity with EDID 1.x.

I found a fix so maybe it helps someone.

So here the fix :

**First**, get last read-edid version [here]("http://www.polypux.org/projects/read-edid/read-edid-2.0.0.tar.gz") (2.0) - [Official site]("http://www.polypux.org/projects/read-edid/")

**Second**, compile & install
```

- sudo apt-get install libx86-dev
- tar xvzf read-edid-2.0.0.tar.gz
- cd read-edid-2.0.0.tar.gz
- ./configure
- make
- sudo make install
```

**Third**, modify the ***matja*** script (startx-custom)

Replace the line
```

EISA_ENTRY=`ddcprobe | sed -n 's/eisa: //p'`
echo "eisa entry: $EISA_ENTRY" > /var/log/gdm/custom
```
By
```

/usr/local/sbin/get-edid | /usr/local/sbin/parse-edid >> /root/eisa.txt
EISA_ENTRY=`grep ModelName /root/eisa.txt | sed 's/.*ModelName "\(.*\)".*/\1/'`
rm /root/eisa.txt
```

So instead of getting the EISA string, we get the ModelName string, which is unique for all model. So you can make it works for all the same model, with only one config.

To know screen ModelName type
```

get-edid | parse-edid >> ~/eisa.txt
cat ~/eisa.txt
```

Type it in your xorg.conf :D

++

---

### Post by matja on 2009-06-05
Hey guys,

Great job making this work on other architectures as well! I haven't actually used this since the new Xorg with xrandr came out, but it's good to see that at least some of you still have use for it.

*Regards, Mattias*

---

### Post by luisca on 2009-10-07
This solution does not work for Karmic, as the way to specify a custom startx command to GDM is not supported in the new, rewritten version. Anybody knows if there is an alternative way to make it work?

Thanks!

---

