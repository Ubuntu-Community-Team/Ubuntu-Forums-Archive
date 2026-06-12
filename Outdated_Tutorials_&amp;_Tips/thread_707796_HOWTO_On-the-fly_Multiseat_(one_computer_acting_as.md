---
title: "HOWTO: On-the-fly Multiseat (one computer acting as several physical ones)"
date: 2008-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by motin on 2008-02-25
The purpose of this tutorial is to aid starting a separate X session with a dedicated mouse and keyboard on demand (ie without needing a restart of X nor the computer).

When finished, you will have launched a new GNOME user session in a nested X window in which one mouse and one keyboard operates independently from the underlying session. The underlying session's mouse and keyboard can control also this 2nd session if necessary. 

This comes in very handy when you have one or more friends over and you'd like to work on the computer on the same time but independently from each other.

Big thanks to Jori Liesenborgs that wrote Xevdevserver which makes this possible without patching X as well as for writing [the original tutorial on how to accomplish multiseat using Xgl](http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.DualSeatX) !

Ok, here we go:

[SIZE="5"]0. Preparations[/SIZE]

**Definitions**
The 1st seat - Refers to your ordinary X session - the one you logged in with when starting your computer. 
Multiseat - The virtual seats running in nested windows with a dedicated pair of mouse and keyboard.

**Actual preparations**
We are going to launch the Multiseats in separate windows, so if you want them to appear on a different monitor than the one belonging to the 1st seat - you better first get an extended desktop configuration working. That is beyond the scope of this tutorial, so look into a tutorial on xrandr for this.

Then, before we continue, be sure to plug in all mice and keyboards that we are going to use. You need at least one pair per multiseat. Usually, only the 1st seat can use the built-in keyboard and touchpad of laptops. 

Lastly preparation-wise - I recommend you to add a second user to your system. I have had bad experiences with gnome panel icons disappearing after logged in with the same user in more than one session. 

[SIZE="5"]1. Get and install the necessary software[/SIZE]

**Xgl**
*I had problems trying to accomplish this using Xnest, mainly with the cursor not showing in the multiseats. Using Xgl's software cursor, this was no longer a problem. Also, Xgl could provide support for direct rendering for the multiseats (dependant of graphics card - works with ATI cards? - and configuration). *

Install the xserver-xgl package (along with Dbus in case it is not installed) using Synaptic or by running the following in a terminal:
```
sudo apt-get install xserver-xgl dbus-x11
```

Now, you may not want Xgl to be enabled for your original session (at least I don't). To disable Xgl for the current user, execute the following:
```
mkdir -p ~/.config/xserver-xgl/
touch ~/.config/xserver-xgl/disable
```

**Xevdevserver**
*The backbone in the multiseat setup is the ability to assign a mouse and keyboard to each multiseat. Jori Liesenborgs has developed Xevdevserver, a program that launches in the background and accomplishes just that. Thanks Jori!*

First, download the tar.gz for XevdevServer from [http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.XevdevServer](http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.XevdevServer)

Then, install build dependencies:
```
sudo apt-get install libx11-dev libxtst-dev gizmod libncurses5-dev
```

Finally, extract the XevdevServer archive and execute to following in the extracted directory:
```
./configure
make
sudo make install
```

**detect-and-assign-multiseat-mouse-and-keyboard.sh**

Previous versions of this guide had a fairly complicated step regarding how to detect and assign a mouse and keyboard to your 2nd seat. This script automates this process. 

Save the following shell-script as "detect-and-assign-multiseat-mouse-and-keyboard.sh"

```
#!/bin/bash
# detect-and-assign-multiseat-mouse-and-keyboard.sh
#
# Description:
# Detects a mouse and keyboard and assigns these devices
# to a target DISPLAY (using xevdevserver)
#
# In addition to xevdevserver, you will need "gizmod" installed:
# sudo apt-get install gizmod
#
# Acknowledements and version history:
# v20080320 - Fredrik Wollsén
#
# License GPL v3
#
# Feel free to provide feedback on this script here:
# http://ubuntuforums.org/showthread.php?p=4550796
#
# THIS SOFTWARE IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY EXPRESS OR
# IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
# WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
# ARE DISCLAIMED. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY
# DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
# DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE
# GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER
# IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
# OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN
# IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

# Make sure that gizmod is available
if [ ! -x `which gizmod` ] ; then
  echo "You need to have gizmod installed for device detection to work";
  echo "Please install gizmod (sudo apt-get install gizmod) and re-run this script";
  exit 1
fi

TMP_FILE=`mktemp -t gizmod.XXXXXX`

usage() {
  BN=`basename $0`
  echo
  echo "Usage: $BN TARGET_DISPLAY"
  echo "For instance: $BN :1 if the devices are to be assigned to display :1"
}

if [ "$1" == "" ] ; then
  echo No TARGET_DISPLAY argument was supplied
  usage
  echo
  echo Exiting...
  exit 1
else 
  TARGET_DISPLAY=$1
fi

detect_input_device() {
COUNTER=0
INPUT_DEVICE=""
while [  $COUNTER -lt 10 ]; do
  echo \n\n\n\n\n\n\n\n\n\n\n\n > $TMP_FILE
  #echo The counter is $COUNTER
  let COUNTER=COUNTER+1 
  sleep 1
  DEVICE_CANDIDATE=`cat $TMP_FILE | tail -n 10 | grep /dev/input | tail -n 1 | sed -r 's/[^\/]*(\/dev\/input[^ ]*).*/\1/g'`
  if [ -a "$DEVICE_CANDIDATE" ] ; then
  if [ ! -d "$DEVICE_CANDIDATE" ] ; then
    if [ "$DEVICE_CANDIDATE" == "$MOUSE" ] ; then
      echo "The keyboard device cannot be the same as the mouse device... Keep pressing that keyboard"
    else
      INPUT_DEVICE=$DEVICE_CANDIDATE
      COUNTER=1000
    fi
  fi
  fi
done
}

no_device_detected() {
  echo "Error: Could not detect any device within 10 seconds. Make sure you connected the device and try to run this script again"
  exit 1
}

echo "Starting device detection application in background... "

sudo bash -c "gizmod -g > $TMP_FILE &" || exit 1

sleep 2

echo Done.

echo
echo "Move and/or press a button or two on the mouse that you will use for the 2nd multiseat"
detect_input_device
MOUSE=$INPUT_DEVICE;

if [ "$MOUSE" == "" ] ; then
  no_device_detected
else
  echo "Device detected!"
fi

echo
echo "Now for the next few seconds, stroke a couple of keys on the keyboard that you will use for the 2nd multiseat"
detect_input_device
KEYBOARD=$INPUT_DEVICE;

if [ "$KEYBOARD" == "" ] ; then
  no_device_detected
else
  echo "Device detected!"
fi

echo
echo -n "Shutting down detection application... "
sudo killall gizmod -s 9

echo "Done with detection!"

# export KEYBOARD
# export MOUSE

echo
echo MOUSE and KEYBOARD variables populated as follows:
echo MOUSE = $MOUSE
echo KEYBOARD = $KEYBOARD

echo 

echo -n "Assign these devices to display $TARGET_DISPLAY? [Y/n]"
read ANS
if [ ! "$ANS" == "n" ] ; then
  DISPLAY=$TARGET_DISPLAY sudo `which xevdevserver` -fork -d $TARGET_DISPLAY -k $KEYBOARD -m $MOUSE
fi

echo "Script finished."

exit 0
```

Now, put it somewhere in your PATH (eg /usr/local/bin/) and make it executable:

```
sudo cp detect-and-assign-multiseat-mouse-and-keyboard.sh /usr/local/bin/
sudo chmod +x /usr/local/bin/detect-and-assign-multiseat-mouse-and-keyboard.sh

```

[SIZE="5"]2. Launch that 2nd seat[/SIZE]

First, we start a terminal (gnome-terminal, konsole or similar) in our main seat and set the variables that we will use. Be sure to replace the variables with your own values. 

```

# Any unused X display number...
export SEAT2_DISPLAY=:1.0

# The username that is to use the 2nd seat
export SEAT2_USER=louise

# The parameter to decide the geometry of the X window. Tip: Use an empty value here while testing as fullscreen can be hard to get out from!
export SEAT2_GEOMETRY=-fullscreen

# Launches a GNOME session. I don't know the command to correctly launch KDE atm
export SEAT2_SESSION="dbus-launch --exit-with-session gnome-session"

# Adjust to your keyboardmap. Use "us" for US keyboards
export SEAT2_KEYBOARDMAP=se

# Save the current display variable for later use
export MAIN_DISPLAY=$DISPLAY
```

Then, we launch the following ONE-AT-A-TIME:
```
# Launch the Xgl server in a window
DISPLAY=$MAIN_DISPLAY sudo /usr/bin/Xgl -dpi 86 -ac -accel glx:pbuffer -accel xv:pbuffer -softcursor $SEAT2_GEOMETRY :1.0 &

# A window with checkers and a cross-symbol for the mouse should display.

# Detect and assign mouse and keyboard:
detect-and-assign-multiseat-mouse-and-keyboard.sh $SEAT2_DISPLAY

# Now, your designated mouse should only be able to move the mouse within the window

# Switch to the desired user
sudo su $SEAT2_USER

# Launch the session
DISPLAY=$SEAT2_DISPLAY exec $SEAT2_SESSION &

# Wait until you are logged in...

# I find the following commands solving some issues with how the keyboard is interpreted - they may or not be needed for your setup. 
# NOTE: If you experience troubles when issuing these, use a new separate terminal to issue them

# Set keyboard map (which often gets set erreneously) - ignore eventual errors from "The XKEYBOARD keymap compiler". If the keyboard seems stuck on some key, try pressing various keys from all connected keyboards until it stops... hopefully
setxkbmap $SEAT2_KEYBOARDMAP

# Re-enable Autorepeat (I found it was off after launching the 2nd seat...)
DISPLAY=$MAIN_DISPLAY xset r on
DISPLAY=$SEAT2_DISPLAY xset r on

```

Now move that X window to an appropriate place on the desktop so that the second user can see it and use it ;)

After ending your multiseat, you may want to make sure xevdevserver is shut down (to be able to use your devices normally again):
```
sudo killall xevdevserver
```

That should be it! Enjoy your multiseat setup!

**Some last notes**
Even if this tutorial only instruct how to set-up that 2nd multiseat, you can use similar instructions to set up a 3rd and 4th seat etc. The actual amount of useable multiseats you can configure depends on the amount of mouse/keyboard-pairs you have and how many monitors you can connect to your computer (and extend your desktop to) versus how many users are willing to share monitors. 

There are probably many other ways to accomplish this, and most likely ways to do more exotic setups etc. This is merely the result of one man's nightly fiddling that resulted in the above method and have not been tested currently by anyone else that I am aware of. That said - please don't be surprised if this doesn't work for you right away...

I'd love to hear how this works for you!

UPDATE 20-mar-2008 13:55: Added a shell script that automates the mouse and keyboard detection and assignment - no need for figuring out the correct device paths any longer: mouse and keyboard is detected by simply moving/pressing buttons/keys on each device.

UPDATE 27-maj-2008 19:10: Updated guide according to mayeulk's feedback. Thanks!

---

### Post by it.henrik on 2008-02-27
Great guide! IT gives me ideas on how to setup my next home PC so I dont need a specific server and client model.

---

### Post by motin on 2008-03-01
> **it.henrik said:**
> Great guide! IT gives me ideas on how to setup my next home PC so I dont need a specific server and client model.

Glad you liked it! Don't forget to tell me in case I made some typos or the like. 

Cheers!

---

### Post by UbuWu on 2008-03-13
Multiseat is supposed to get easier in hardy due to xorg 7.3 with xephyr and xrandr. Do you know how to setup multiseat properly in hardy?

---

### Post by trolldown on 2008-03-19
Is it possible to use USB Sound & USB Webcameras for individual terminals??

---

### Post by motin on 2008-03-20
> **trolldown said:**
> Is it possible to use USB Sound & USB Webcameras for individual terminals??

I haven't got a clue ;)

Currently sound is shared between the two users, but routing sound to different outputs may be possible using a sound server such as PulseAudio or JACK. You'd probably be better off starting a new thread for that matter though. 

If Skype is this only concern here, it may also be possible to configure Skype to use a separate pair of USB sound + webcamera for each user...

Also, currently Xgl seem only to perform well using ATI drivers. On my Intel 915gm (laptop) this second user gets sluggish video and firefox scroll performance. Webcamera usage may be rather CPU-consuming as well. 

Remember that there are other ways to achieve multiterminal set-ups which may be more suited for web café installations. if that's what you are looking for to achieve. This above here is mainly for being able to spontaneously share your computer with a co-worker which has no laptop at hand currently.

---

### Post by ryanhaigh on 2008-03-20
There is an application in the repositories called something userfull that doesn't require XGL and has a nice easy setup eg. Click a button on the mouse infront of this monitor.

If i remember correctly it did nag you till you registered but registration if free for two seats. I set if up with a nvidia agp card and s3 pci card and it worked great, the only problem being that the users couldn't shutdown easily, but modification to one of the bash scripts fixed that.

---

### Post by motin on 2008-03-20
> **ryanhaigh said:**
> There is an application in the repositories called something userfull that doesn't require XGL and has a nice easy setup eg. Click a button on the mouse infront of this monitor.

If i remember correctly it did nag you till you registered but registration if free for two seats. I set if up with a nvidia agp card and s3 pci card and it worked great, the only problem being that the users couldn't shutdown easily, but modification to one of the bash scripts fixed that.

Gotta keep on par with the competition ;) :
> UPDATE 20-mar-2008 13:55: Added a shell script that automates the mouse and keyboard detection and assignment - no need for figuring out the correct device paths any longer: mouse and keyboard is detected by simply moving/pressing buttons/keys on each device. 

Available in the OP. Enjoy!

---

### Post by motin on 2008-03-20
> **UbuWu said:**
> Multiseat is supposed to get easier in hardy due to xorg 7.3 with xephyr and xrandr. Do you know how to setup multiseat properly in hardy?

Nope. I'll try this out eventually when Hardy is released. In the meantime, feel free to try this method in Hardy and report back how it works out for ya. 

Cheers,

Fredrik

---

### Post by ryanhaigh on 2008-03-20
Wow nice work with the quick update! Maybe you could have a look at userful and see if there are any other features you think would be valuable.

You may also be interested in the HWCursor/SWCursor options for xorg.conf which may mean your setup could operate without XGL. Here is a (slightly old but likely still accurate) site that has a little info on the cursor issue:  [http://www.x.org/archive/X11R6.8.0/doc/ati5.html](http://www.x.org/archive/X11R6.8.0/doc/ati5.html)

I noticed that in some of the code you have you say to do one step at a time, could you not automate these steps and make it a script just by using && on the end of each 'one at a time' line?

Finally you may want to look at/mention checkinstall which replaces the make install line and rather than just installing the software all over the place creates a nice deb and then installs that so that it may be easily uninstalled. I don't think it handles dependency checking or anything but it is still nice to be able to manage the software you have installed from source using the package manager. [http://ubuntuforums.org/showthread.php?t=2356](http://ubuntuforums.org/showthread.php?t=2356)

---

### Post by motin on 2008-03-21
> **ryanhaigh said:**
> Wow nice work with the quick update! Maybe you could have a look at userful and see if there are any other features you think would be valuable.

Thanks. ;) I have never tried the Userful Desktop Multiplier but I believe that this technique and the DM are basically different approaches to different demands. This is only for spawning windowed X sessions with assigned mice/keyboards and not for permanent multiseat setups. 

I will still of course listen to suggestions for improvement. 

> **ryanhaigh said:**
> I noticed that in some of the code you have you say to do one step at a time, could you not automate these steps and make it a script just by using && on the end of each 'one at a time' line?

Eventually I guess I'll wrap it together in a shell script. The problem right now is that I ran into many breakages on the steps before adjusting the strategy and methods and I am almost certain that my instructions will not work for many types of hardware. Wrapping everything in a script is a bit to much when it isn't tested more. 

> **ryanhaigh said:**
> You may also be interested in the HWCursor/SWCursor options for xorg.conf which may mean your setup could operate without XGL. Here is a (slightly old but likely still accurate) site that has a little info on the cursor issue:  [http://www.x.org/archive/X11R6.8.0/doc/ati5.html](http://www.x.org/archive/X11R6.8.0/doc/ati5.html)

Problem with these options is that I don't see how to specify them on the command line. Only Xgl seem to have the -swcursor switch, but I guess one could figure out a way to use gdmflexiserver with some X init script or maybe Xephyr etc but as long as the Xgl version Works For Me I'll leave it up to any user to contribute with a way to accomplish this. 

If I get more success stories how these instructions works with different drivers and setups then I'll have no second thoughts about bunching it together ;)

> **ryanhaigh said:**
> Finally you may want to look at/mention checkinstall which replaces the make install line and rather than just installing the software all over the place creates a nice deb and then installs that so that it may be easily uninstalled. I don't think it handles dependency checking or anything but it is still nice to be able to manage the software you have installed from source using the package manager. [http://ubuntuforums.org/showthread.php?t=2356](http://ubuntuforums.org/showthread.php?t=2356)

I usually write my instructions using checkinstall, but since this "make install" only copies a single binary to /usr/local/bin then I judged it as overkill for this guide. Especially since it is not yet ready for anyone not familiar with Linux in the first place. 

Thanks for the feedback!

Cheers,

Fredrik

---

### Post by trolldown on 2008-03-21
> **motin said:**
> Remember that there are other ways to achieve multiterminal set-ups which may be more suited for web café installations. if that's what you are looking for to achieve. This above here is mainly for being able to spontaneously share your computer with a co-worker which has no laptop at hand currently.

yeah.. my intention is for a net cafe. what are the other ways that you are talking about??

Thanks

---

### Post by andersja on 2008-03-25
I'm also very keen to see this expanded in Hardy or Hardy+1 to allow for simple sharing of one computer to several monitors/keyboards on a permanent basis (think: buying one more powerful computer for the whole family, allowing 2+ persons to work/play independently of each other, sharing one computer?

See also:
[http://brainstorm.ubuntu.com/item/206/](http://brainstorm.ubuntu.com/item/206/)
[http://brainstorm.ubuntu.com/idea/383/](http://brainstorm.ubuntu.com/idea/383/)
[http://brainstorm.ubuntu.com/idea/3153/](http://brainstorm.ubuntu.com/idea/3153/) (_***incorrectly ***_listed as "Implemented")

---

### Post by andersja on 2008-03-25
See also: [http://ubuntuforums.org/showthread.php?t=583037](http://ubuntuforums.org/showthread.php?t=583037)

---

### Post by mayeulk on 2008-04-28
libncurses5-dev has some required headers. The script uses dbus.
Hence my full list of packages to install becomes:

```
sudo apt-get install xserver-xgl libx11-dev libxtst-dev gizmod libncurses5-dev dbus-x11
```

I also needed to download and compile errut from the same website as xevdevserver-2.0.0

```
cd /errut-1.0.0/
./configure
make
sudo make install 
```

before doing this:

```
cd ../xevdevserver-2.0.0/
./configure
make
sudo make install
```

In addition, for completeness about the .sh script:

```
sudo cp detect-and-assign-multiseat-mouse-and-keyboard.sh /usr/local/bin/
sudo chmod +x /usr/local/bin/detect-and-assign-multiseat-mouse-and-keyboard.sh

```




Still, I have problems.

```
# Any unused X display number...
export SEAT2_DISPLAY=:1.0
```
Can you be more specific?
```
echo  $MAIN_DISPLAY
``` returns ```
:0.0
```
Is :1.0 OK?

Is the following empty value OK?
```
# Tip: Use an empty value here while testing as fullscreen can be hard to get out from!
export SEAT2_GEOMETRY=

```

Where could I find inormation on how to "correctly launch KDE atm" ? (I Googled a bit, without success).
Anyway, I'm far from it.
Doing
```

DISPLAY=$MAIN_DISPLAY ; sudo /usr/bin/Xgl -dpi 86 -ac -accel glx:pbuffer -accel xv:pbuffer -softcursor $SEAT2_GEOMETRY :1.0 &
```
Has no effect.



I assume it is correct to do all the above in a graphical command line Konsole.

Thank you for your help.

---

### Post by andersja on 2008-05-07
See also (and vote for!) 

[http://brainstorm.ubuntu.com/idea/3442/]("http://brainstorm.ubuntu.com/idea/3442/")

---

### Post by andersja on 2008-05-13
[[IMG]http://brainstorm.ubuntu.com/idea/3442/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3442/)

---

### Post by arfarean on 2008-05-18
I've success spawn 2 independent Xgl process by following this thread instruction, using Ubuntu 8.04. 

I wonder how to make it automated and make it without "frame" like this: [IMG]http://research.edm.uhasselt.be/~jori/page/uploads/Misc/multiseatsinglescreen.jpg[/IMG]

from [http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.DualSeatX](http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.DualSeatX)

---

### Post by EdGato on 2008-05-19
> **motin said:**
> I haven't got a clue ;)

Currently sound is shared between the two users, but routing sound to different outputs may be possible using a sound server such as PulseAudio or JACK. You'd probably be better off starting a new thread for that matter though. 

If Skype is this only concern here, it may also be possible to configure Skype to use a separate pair of USB sound + webcamera for each user...

Also, currently Xgl seem only to perform well using ATI drivers. On my Intel 915gm (laptop) this second user gets sluggish video and firefox scroll performance. Webcamera usage may be rather CPU-consuming as well. 

Remember that there are other ways to achieve multiterminal set-ups which may be more suited for web café installations. if that's what you are looking for to achieve. This above here is mainly for being able to spontaneously share your computer with a co-worker which has no laptop at hand currently.

> **trolldown said:**
> yeah.. my intention is for a net cafe. what are the other ways that you are talking about??

Thanks

Me too! For a cafe... does audio work on individual stations? Where can I get the cheapest USB keyboards, mice, and speakers? I can't as yet afford Userful's DiscoverStation..... however, at $99, I think it's cheap enough for those with the money, though...

---

### Post by arfarean on 2008-05-19
My goal is using splitscreen as Point of Sales (PoS) terminal or Paid Parking Terminal. This approach will saving resources.

---

### Post by EdGato on 2008-05-26
Motin, are both your keyboard/mouse sets USB, or is one pair PS/2 and one USB?

To everyone here, do you think this setup (and also userful's) will work well with PCI-Express cards?

---

### Post by motin on 2008-05-27
> **mayeulk said:**
> libncurses5-dev has some required headers. The script uses dbus.
Hence my full list of packages to install becomes:

```
sudo apt-get install xserver-xgl libx11-dev libxtst-dev gizmod libncurses5-dev dbus-x11
```


Thanks, I have updated the guide accordingly. 

> **mayeulk said:**
> 

I also needed to download and compile errut from the same website as xevdevserver-2.0.0

```
cd /errut-1.0.0/
./configure
make
sudo make install 
```

before doing this:

```
cd ../xevdevserver-2.0.0/
./configure
make
sudo make install
```


This is a bit odd, I never had do do this - what distribution are you using?

> **mayeulk said:**
> 

In addition, for completeness about the .sh script:

```
sudo cp detect-and-assign-multiseat-mouse-and-keyboard.sh /usr/local/bin/
sudo chmod +x /usr/local/bin/detect-and-assign-multiseat-mouse-and-keyboard.sh

```


Thanks, I have added this to the guide. 

> **mayeulk said:**
> 

Still, I have problems.

```
# Any unused X display number...
export SEAT2_DISPLAY=:1.0
```
Can you be more specific?
```
echo  $MAIN_DISPLAY
``` returns ```
:0.0
```
Is :1.0 OK?



:0.0 is the default main display number and :1.0 should be perfectly fine for that 2nd seat.

> **mayeulk said:**
> 

Is the following empty value OK?
```
# Tip: Use an empty value here while testing as fullscreen can be hard to get out from!
export SEAT2_GEOMETRY=

```


It sure is! It omits the -fullscreen parameter from the command that launches Xgl.

> **mayeulk said:**
> 

Where could I find inormation on how to "correctly launch KDE atm" ? (I Googled a bit, without success).
Anyway, I'm far from it.



Sorry, I am in the same position. Anyone else?

> **mayeulk said:**
> 

Doing
```

DISPLAY=$MAIN_DISPLAY ; sudo /usr/bin/Xgl -dpi 86 -ac -accel glx:pbuffer -accel xv:pbuffer -softcursor $SEAT2_GEOMETRY :1.0 &
```
Has no effect.


The launch of Xgl is done before launching KDE, so the above command should be the same regardless of desktop environment used. Also, there is a semicolon in your command that should not be there for the first part to make sense. 

> **mayeulk said:**
> 

I assume it is correct to do all the above in a graphical command line Konsole.

Thank you for your help.

That is correct. Always glad my guide came to some use! Thanks for your feedback!

> **arfarean said:**
> I've success spawn 2 independent Xgl process by following this thread instruction, using Ubuntu 8.04. 

I wonder how to make it automated and make it without "frame" like this: [IMG]http://research.edm.uhasselt.be/~jori/page/uploads/Misc/multiseatsinglescreen.jpg[/IMG]

from [http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.DualSeatX](http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.DualSeatX)

To make it automated, you best follow another guide, since this guide is specifically about how to acccomplish multiseat on demand... About that frameless 2x2 solution: Jori used a certain window manager with a name that has slipped my name unfortunately. It is very lightweight having the ability but to split the screen into 2x2, 3x3 patterns. 

You may also have some luck in using Devilspie - with which you probably can make the Xgl windows frameless and with a fixed position upon startup. 

> **EdGato said:**
> Motin, are both your keyboard/mouse sets USB, or is one pair PS/2 and one USB?

To everyone here, do you think this setup (and also userful's) will work well with PCI-Express cards?

I am using the built-in mouse+keyboard of my laptop together with a pair of USB ditos. 

This current setup requires X to be able to provide an extended desktop to the other graphic outputs. It it's possible to extend the desktop to more than 2-3 outputs then yes it will work, but otherwise you still have to dwelve into xorg.conf into such a degree that you might have better luck following a guide that is targeted for permanent multiseats. 

Cheers

---

### Post by kacperpl1 on 2008-07-09
Hi! I have a problem with this tutorial. Following the steps from the first page i stopped on make in XevdevServer dir because of some error. Meanwhile i discovered that my second keyboard isnt working(thought its maybe cause plug and play doesnt works as it should) and maybe because of that i should make ./configure again after restarting system. The thing now xserver starts without any pointer and keyboard working and restarts twice and after that i cant do anything on blank screen. I have no idea what can i do else. Im pissed because if i reinstall system ill have to go with my pc box near the access point and connect it by wire and configure wireless. So first can anybody tell how to restore this to defaults or sth like that? Second is how to make this all working on dual headed video card from nvidia.

---

### Post by motin on 2008-07-09
> **kacperpl1 said:**
> Hi! I have a problem with this tutorial. Following the steps from the first page i stopped on make in XevdevServer dir because of some error. Meanwhile i discovered that my second keyboard isnt working(thought its maybe cause plug and play doesnt works as it should) and maybe because of that i should make ./configure again after restarting system. The thing now xserver starts without any pointer and keyboard working and restarts twice and after that i cant do anything on blank screen. I have no idea what can i do else. Im pissed because if i reinstall system ill have to go with my pc box near the access point and connect it by wire and configure wireless. So first can anybody tell how to restore this to defaults or sth like that?

Since you only performed the first steps in the tutorial, and since trying to compile or install xevdevserver will not interfere with your X settings, I can only conclude that your misfortune is due to the installation of xserver-xgl. How that could affect your keyboard availability right away I have no idea though... Anyway:

xserver-xgl will attempt to autostart when installed, thus I added instructions on how to disable xserver-xgl autostart:
mkdir -p ~/.config/xserver-xgl/
touch ~/.config/xserver-xgl/disable

If you are sure that you performed that step correctly, then you can try to uninstall xserver-xgl:
sudo apt-get remove xserver-wgl

If you cannot use X at all, then restart in rescue mode by chosing rescue mode for your kernel in the grub menu on computer boot, then run the above commands. 

All in all, nothing in this tutorial except for the installation of xserver-xgl, should affect your system upon a reboot.

> **kacperpl1 said:**
> Second is how to make this all working on dual headed video card from nvidia.

Can you configure an extended desktop with your graphics card? If so, then this guide will work for you. That is the only prerequisite to be able to use one monitor for each desktop.

---

### Post by kacperpl1 on 2008-07-09
Im still unable to make the file.
> kacper@QuadK8:~/xevdevserver-2.0.0$ make
Making all in src
make[1]: Entering directory `/home/kacper/xevdevserver-2.0.0/src'
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xevdevserver\" -DVERSION=\"2.0.0\"  -I. -I.     -g -O2 -MT xevdevkeyinfo.o -MD -MP -MF ".deps/xevdevkeyinfo.Tpo" -c -o xevdevkeyinfo.o xevdevkeyinfo.cpp; \
	then mv -f ".deps/xevdevkeyinfo.Tpo" ".deps/xevdevkeyinfo.Po"; else rm -f ".deps/xevdevkeyinfo.Tpo"; exit 1; fi
xevdevkeyinfo.cpp: In function ‘void printUsage()’:
xevdevkeyinfo.cpp:40: error: ‘exit’ was not declared in this scope
xevdevkeyinfo.cpp: In function ‘int processDeviceEvents()’:
xevdevkeyinfo.cpp:136: error: ‘u_int8_t’ was not declared in this scope
xevdevkeyinfo.cpp:136: error: expected `;' before ‘buffer’
xevdevkeyinfo.cpp:145: error: ‘buffer’ was not declared in this scope
make[1]: *** [xevdevkeyinfo.o] Error 1
make[1]: leaving directory `/home/kacper/xevdevserver-2.0.0/src'
make: *** [all-recursive] Error 1
I dont know what to do now. errut make crashes too.

EDIT: Ive managed that i had to include <cstring> and <cstdlib> in every bugged .cpp file because of newer (4.3) and a bit bugged version of gcc.

EDIT2: Ive managed how to launch it but dunno why it stays with cross instead of the arrow and with dotted background. I am running xubuntu so ive changed gnome-session to xfce4-session and nothing changed.
EDIT3: After running this script for check only
> #!/bin/bash
export SEAT2_SESSION="dbus-launch --exit-with-session xfce4-session"
DISPLAY=$DISPLAY sudo /usr/bin/Xgl -dpi 86 -ac -accel glx:pbuffer -accel xv:pbuffer -softcursor :1.0 &
DISPLAY=$DISPLAY exec sudo dbus-launch --exit-with-session xfce4-session &
i get crashes like this:
> kacper@QuadK8:~$ sh ND_SEAT.sh 
kacper@QuadK8:~$ 
** (xfwm4:10064): WARNING **: Another Window Manager is already running
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
** Message: xfce4-panel already running

** (xfce4-session:10054): WARNING **: Unable to launch "nm-applet --sm-disable" (specified by autostart/nm-applet.desktop): Nie mo&#380;na wykona&#263; procesu potomnego "nm-applet" (No such file or directory)

** (update-notifier:10360): WARNING **: not starting because user is not in admin group

WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy

still nothing opens in newly opened Xgl. Maybe its because of drivers or because of xfce4.
My system specs: Xubuntu Intrepid 32bit
Nvidia 177.13 xen patched, installed from binary
Quad AMD K8 and a single 9600GT(because of that i cant use 169 drivers, and 173 drivers are still not available for intrepid so i must build them from binary and 173 wont patch for xen kernels)

---

### Post by motin on 2008-07-10
> **kacperpl1 said:**
> Im still unable to make the file.
I dont know what to do now. errut make crashes too.

EDIT: Ive managed that i had to include <cstring> and <cstdlib> in every bugged .cpp file because of newer (4.3) and a bit bugged version of gcc.

EDIT2: Ive managed how to launch it but dunno why it stays with cross instead of the arrow and with dotted background. I am running xubuntu so ive changed gnome-session to xfce4-session and nothing changed.
EDIT3: After running this script for check only

i get crashes like this:


still nothing opens in newly opened Xgl. Maybe its because of drivers or because of xfce4.
My system specs: Xubuntu Intrepid 32bit
Nvidia 177.13 xen patched, installed from binary
Quad AMD K8 and a single 9600GT(because of that i cant use 169 drivers, and 173 drivers are still not available for intrepid so i must build them from binary and 173 wont patch for xen kernels)

Great that you managed to build xevdevserver!

As for the script, it is dependant that the $DISPLAY variable is set. Without it, it will try to start in your desktop environment, and not in the window. Therefore, make sure that you have run all the "export" commands in the terminal found under "2. Launch that 2nd seat" before running the commands that launch dbus/gnome etc.

---

### Post by kacperpl1 on 2008-07-10
I know what do u mean but i'm still unable to run xfce or gnome int that xgl. MY starting script:> #!/bin/bash
DISPLAY=:0.1 sudo /usr/bin/Xgl -dpi 86 -ac -accel glx:pbuffer -accel xv:pbuffer -softcursor -fullscreen :1.0 &
DISPLAY=:0.1 exec sudo dbus-launch --exit-with-session xfce4-session & 
And crap ejected by terminal:> kacper@QuadK8:~$ sudo sh 2ND_SEAT.sh 
kacper@QuadK8:~$ Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

[COLOR="Red"]** (xfwm4:6353): WARNING **: Another Window Manager is already running
** Message: xfce4-panel already running[/COLOR]
WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy


** (xfce4-session:6343): WARNING **: Unable to launch "nm-applet --sm-disable" (specified by autostart/nm-applet.desktop): could not exec descendant process "nm-applet" (No such file or directory)
Connection failure: Connection refused


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...

** (trackerd:6381): WARNING **: Tracker daemon is already running - attempting to run in readonly mode
starting HAL detection for ac adaptors...none found
Throttle level is 0

** (update-notifier:6387): WARNING **: not starting because user is not in admin group

WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy

EDIT: Can u tell me what distro are u using and what xserver do u have? I'm just unable to launch multiple gnome/xfce4 sessions using almost clear xubuntu hardy or intrepid. Give more spec about your system where all this does work. I just don't get it how is this possible that none of those simple tutorials and howto's works in my xubuntu.

---

### Post by motin on 2008-08-12
> **kacperpl1 said:**
> I know what do u mean but i'm still unable to run xfce or gnome int that xgl. MY starting script:

I don't see where you got :0.1 from, I usually only use :0.0 and :1.0. Also, the Xgl should use :0.0 and the dbus command should use :1.0 in ordered to be started within the Xgl window. 

For that part, it should then read:
```
#!/bin/bash
DISPLAY=:0.0 sudo /usr/bin/Xgl -dpi 86 -ac -accel glx:pbuffer -accel xv:pbuffer -softcursor -fullscreen :1.0 &
DISPLAY=:1.0 exec sudo dbus-launch --exit-with-session xfce4-session &
```

My suggestion is that you follow the guide point by point and make sure that works before trying to automate the process through a script. 

> **kacperpl1 said:**
> EDIT: Can u tell me what distro are u using and what xserver do u have? I'm just unable to launch multiple gnome/xfce4 sessions using almost clear xubuntu hardy or intrepid. Give more spec about your system where all this does work. I just don't get it how is this possible that none of those simple tutorials and howto's works in my xubuntu.

Ubuntu Hardy Heron 8.04, although when I wrote the guide I used Gutsy 7.10, or even Feisty 7.04. 

X.org version: 1:7.3+10ubuntu10.2

---

### Post by bodhi.zazen on 2008-11-17
Very nice how to.

May I add some general information. X sessions are numbered starting with 0 , ie :0 , :1 ., etc.

With multiple monitors we add a . , so first session, first screen == :0.0
first session, second screen == :0.1

second session, first screen (with default numbering) == :1.0
second session, second screen == :1.1

and on ...

although not the same, you may be interested in these links as well :

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674") 

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948")

If I may, keep in mind that the Ubuntu wiki is also user maintained (hint)

[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

---

### Post by Augustino on 2008-11-17
When I put this in terminal:

> 
DISPLAY=$MAIN_DISPLAY sudo /usr/bin/Xgl -dpi 86 -ac -accel glx:pbuffer -accel xv:pbuffer -softcursor $SEAT2_GEOMETRY :1.0 &


say me 

Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 81 requests (81 known processed) with 0 events remaining.

[1]+  Exit 1                  DISPLAY=$MAIN_DISPLAY sudo /usr/bin/Xgl -dpi 86 -ac -accel glx:pbuffer -accel xv:pbuffer -softcursor $SEAT2_GEOMETRY :1.0

I will testing [http://es.wikibooks.org/wiki/Multiterminal/Usando_Xephyr](http://es.wikibooks.org/wiki/Multiterminal/Usando_Xephyr)

is for debian sarge but I will testing

Will it work?

---

