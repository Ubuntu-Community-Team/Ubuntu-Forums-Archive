---
title: "HOWTO: Use the xplanet-gnome script in Ubuntu"
date: 2007-02-01
forum: Outdated Tutorials &amp; Tips
---

### Post by cactaur on 2007-02-01
This HOWTO explains how to use the xplanet-gnome script which gives you a real-time image of the Earth on your Desktop. The original page is [here]("http://stef.tvk.rwth-aachen.de/~nazgul/linux-hacks.php#xplanet-gnome2"). I found that the original web site isn't very clear, and is really confusing. So I decided to make this HOWTO so other people don't have to go through that. This is my first HOWTO, so bear with me.

I tested this on Edgy 32 bit, but it requires Gnome 2, which I believe is on every supported release of Ubuntu (Dapper and Breezy). The other program you need is Xplanet. Along with xplanet, you'll need the accompanying xplanet-images planet, which can be installed by:

```
sudo apt-get install xplanet xplanet-images
```
(or aptitude)

If you want, you can make a folder where you could put many customized maps if you feel creative. I'm not going to go into this, but just in case, just go:

```
mkdir ~/xplanet-maps
```

Now that we have all the dependencies, we can start:

1. Download the script from the web site:

```
wget http://stef.tvk.rwth-aachen.de/~nazgul/files/xplanet-gnome
```

(If you want to put the ".sh" at the end, feel free to. It will still work.)

2. Edit the script so that it knows where to put the file. On Ubuntu, there is no such directory as /multimedia/wallpaper, so you'll have to change it. If you put the ~/xplanet-maps, then you would change line 7 from

```
PREFIX=/multimedia/wallpapers/
```
to
```
PREFIX=/home/gregory/xplanet-maps
```
Gregory is the name of my account, you should change it to whatever account you're using this in for the rest of this HOWTO.

3. Run the script in the terminal. You should get something that says:

```
rm: cannot remove '/home/gregory/xplanet-maps/2xplanet.png
```

Don't worry about that, it'll go away the next time we run it.

4. Have the desktop recognize the file as a background.

Right-click your desktop and click "Change Desktop Background". Pick "Add", and navigate to /home/gregory/xplanet-maps. Click the newly created xplanet.png and set it as your background. Now, as long as your script runs, the backgrond will continually update itself every 30 minutes.

5. Have the script run when you start up.

Go to System>Preferences>Sessions> "Startup Programs" tab> Add > type in "/home/gregory/xplanet-gnome"

Ok, that's it. I'll try and take any problems if you have any. If it happens that you don't like this, simply go back and Change the Desktop Background to something you do like. If you really don't like it, even delete the ~/xplanet-maps and the xplanet-gnome script. That's all.
--------------------------------------------------------------------------------------------------------------------------
Thanks to EisenPM, I found a way to put the map as a screensaver.

Instead of or in addition to Step 4, you can do this procedure:

1. Change the input folder for the personal slideshow
```
sudo gedit /usr/share/applications/screensavers/personal-slideshow.desktop
```

Look for a line that looks like > Exec=slideshow --location=Pictures and change "Pictures" to the directory of your maps, xplanet-maps in my case. Save and close.

Now, go to System>Preferences>Screensaver and put the screensaver on "Pictures Folder". You should now be able to set the xplanet-gnome map as your picture.

---

### Post by tribble222 on 2007-02-15
Thanks!  Exactly what I was looking for!

---

### Post by Bossieman on 2007-02-15
So, how do I change what body to be shown? Say I want the moon instead of the earth?

---

### Post by tribble222 on 2007-02-15
You would add

-body moon

to the command the script generates, and then edit your /usr/share/xplanet/config accordingly

In the config find the section with

[moon]
"Moon"
color={100, 100, 100}

And add in options, such as

image=/usr/share/xplanet/images/my_moon_image.jpg

The different command line options are explained here [http://xplanet.sourceforge.net/README](http://xplanet.sourceforge.net/README) and the different config file options are explained here [http://xplanet.sourceforge.net/README.config](http://xplanet.sourceforge.net/README.config)

---

### Post by pgilmon on 2007-02-16
Hey, I followed your instructions and it worked right away. The results are impressive. Thanks a lot!

---

### Post by EisenPM on 2007-03-13
it works great as desktop image. but I'd prefer to use it only as a screensaver. Any ideas how to get that working?

---

### Post by cactaur on 2007-03-13
> **EisenPM said:**
> it works great as desktop image. but I'd prefer to use it only as a screensaver. Any ideas how to get that working?

Ok, I'm basically basing my answer off [this]("http://ubuntuforums.org/showthread.php?t=230576") howto, but it should work. I tried it and it worked, but I'm not sure if it updates (if that's important). If you can give me the status on that, that would be great, and I could probably add it to the post. So, here's the basic process:

open the file that controls the screensaver slide show.
```
sudo gedit /usr/share/applications/screensavers/personal-slideshow.desktop
```

Edit the line which holds the path to the slide show. In my file it's line 115. It looks kinda like this:
```
Exec=slideshow --location=Pictures
```

Change "Pictures" to the folder where your xplanet maps are (in my example, xplanet-maps). Your screensaver should now open that file. As I said, I don't know if this updates, but I believe it should.

EDIT: I verified it for myself. It works. Thanks for leading me to this discovery EisenPM. I'll add it to the tutorial.

---

### Post by EisenPM on 2007-03-14
cactaur: thanks fpr the quick answer. unfortunately it doesn't work for me and I actually don't understand the background thing completely...

I actually don't understand the purpose of this line:

```
PREFIX=/home/gregory/xplanet-maps
```

This directory doesn't have to exist, right? and my (only) image file is 

xplanet-maps2xplanet.png

and it was automatically generated in /home/eisenpm

Interestingly, I didn't have to select the desktop background after executing the script, it was already the xplanet image had already been selected.

Now it comes to the screensaver; despite the things above, the background image actually works, but what am I going to enter as the picture location? since xplanet-maps is empty or doesn't have to exist, and I don't want to enter my whole /home/ directory... :confused:

---

### Post by cactaur on 2007-03-14
Ok, well, the PREFIX variable basically states where you want your map to go. In your case, I'd highly recommend making a "xplanet-maps" folder in your home directory. That way, all of the action occurs inside "xplanet-maps" and doesn't interact with the rest of your directory. Yeah, and with an "xplanet-maps" directory, it'll make the screensaver part much easier to do.

All-in-all, make the "xplanet-maps" folder.

As for the script automatically changing the background, I haven't been able to reproduce the result. But if that happens, just change the background back to what you want it to be and it should work fine.

---

### Post by EisenPM on 2007-03-15
alright, now everything works, I forgot to put a slash behind the prefix folder.... :roll: 

still, after executing the script, the background changes automatically. doesn't matter, it works!

---

### Post by ebp on 2007-07-14
I can't download the script, is it hosted somewere else?

---

### Post by cactaur on 2007-07-14
You're right. I think the site is down for some reason. Well, I've attached the original file to this post, so I think you can temporarily get it from here if you would like.

---

### Post by pkjm17 on 2007-07-16
I can't get Xplanet to work. The earth.jpg on my desktop background doesn't change, it's just the original picture that comes with XPlanet when you download the Xplanet images. My PREFIX is /usr/share/xplanet/images/ and my OUTPUT is earth.jpg. I noticed in your example you use your home directory. Does the prefix have to be my home directory?

---

### Post by cactaur on 2007-07-16
> **pkjm17 said:**
> I can't get Xplanet to work. The earth.jpg on my desktop background doesn't change, it's just the original picture that comes with XPlanet when you download the Xplanet images. My PREFIX is /usr/share/xplanet/images/ and my OUTPUT is earth.jpg. I noticed in your example you use your home directory. Does the prefix have to be my home directory?

Well, I would highly recommend putting it in your home folder, because if you put it in /usr/share/xplanet/images/ you'll need to run it as root. I think it would be much easier if you put it in your home folder, because you won't have to mess around with permissions and all that.

---

### Post by pkjm17 on 2007-07-19
Ok, so I got the image of the earth to what I want it to be, and have it for my background, but for some reason I can't get it to update itself automatically. I was wondering if there is an alternative to the System->Preferences->Sessions, since that doesn't seem to be working for me.

---

### Post by cactaur on 2007-07-19
Hmmm.....I don't think the problem is with the sessions. The default refresh interval for the map is every 30 minutes. That could be changed by finding the line in the script which says:

```
DELAY=30m
```

You can change that by changing 30 to, say 1. Then it'll update every 1 minute. I think that'll help, because unless the script has some sort of an error in it, it should remain running.

---

### Post by Roconda on 2008-11-02
> **pkjm17 said:**
> Ok, so I got the image of the earth to what I want it to be, and have it for my background, but for some reason I can't get it to update itself automatically. I was wondering if there is an alternative to the System->Preferences->Sessions, since that doesn't seem to be working for me.
First of all, sorry for posting in an old topic(but I tought it would be useful). My desktop didn't auto-refresh my background too. 
Open the .sh code. 
Change the line 
```
 #update Gnome backgound
gconftool -t str -s /apps/nautilus/preferences/background_filename "$PREFIX$OUTPUT"
sleep $DELAY
exec $0 
```
into
```

#update Gnome backgound
gconftool -t str -s /desktop/gnome/background/picture_filename "$PREFIX$OUTPUT"
sleep $DELAY
exec $0
```

It works for me,,.. would be nice if it will help more people:)

,Roconda

---

### Post by dcstar on 2009-08-02
> **Roconda said:**
> First of all, sorry for posting in an old topic(but I tought it would be useful). My desktop didn't auto-refresh my background too. 
Open the .sh code. 
Change the line 
```
 #update Gnome backgound
gconftool -t str -s /apps/nautilus/preferences/background_filename "$PREFIX$OUTPUT"
sleep $DELAY
exec $0 
```
into
```

#update Gnome backgound
gconftool -t str -s /desktop/gnome/background/picture_filename "$PREFIX$OUTPUT"
sleep $DELAY
exec $0
```

It works for me,,.. would be nice if it will help more people:)

,Roconda

That works for my 9.04 system. Others will also want to change the default resolution/Latitide/Longitude settings to match their particular environment.

You can get your screen resolution using the **xrandr** command, and you can easily get your Latitude/Longitude from the Location Preferences in the Gnome Clock on the desktop.

---

### Post by dcstar on 2009-08-04
I have had a play around with this script and come up with one that works well on my 9.04 & 10.04 systems (the original script could result in multiple instances running), here it is for anyone else who may want to use/improve it.

This has been modified to clean up any left over lock files after a crash/reboot and to automatically get screen resolution and your location to center the display:

```
#!/bin/bash
#xplanet-gnome.sh shell script v1.1
#shows Earth on your Gnome desktop with current lighting conditions,i.e. day and night

DELAY=5m
PREFIX=~/
OUTPUT=.xplanet.png
#
# These should extract your current screen resolution and location from your system
# The location is found from the Gnome Clock Preferences Location.
#
GEOMETRY=$(xrandr | grep '*' | head -1 | cut -b 4-12)
LONGITUDE=$(gconftool -g /apps/panel/applets/clock_screen0/prefs/cities | cut -f5 -d " " | cut -f2 -d "=" | sed 's/"//g' )
LATITUDE=$(gconftool -g /apps/panel/applets/clock_screen0/prefs/cities | cut -f4 -d " " | cut -f2 -d "=" | sed 's/"//g' )
#
#default is no projection,i.e. render a globe
#rectangular is the flat world map. also try ancient, azimuthal,  mercator,..
PROJECTION=rectangular

# This stuff is to prevent multiple instances running if you log out and log in again
lockfile=$HOME/.xplanet.lock

# Check if timestamp of lock file is older than boot time:
if [ -e $lockfile ]; then
  CDATE=$(date +%s -r $HOME/.xplanet.lock)
  BOOTTIME=$(cat /proc/uptime | cut -f1 -d" ")
  CTIME=$(date +%s)
  FTIME=$(($CTIME - ${BOOTTIME/.*}))
  #
  # If older then it is a leftover - so delete it!
  if [[ $CDATE -lt $FTIME ]]; then
   rm -f $lockfile
 fi
#
fi

if [ ! -e $lockfile ]; then
   # Delete lockfile if program receives command to end:
   trap "rm -f $lockfile; rm -f $PREFIX$OUTPUT; exit" INT TERM EXIT
   # and let's make one now....
   touch $lockfile
else
   # Lockfile exists for this user profile, get me outa here!
   exit
fi

if [ -z $PROJECTION ]; then 
xplanet -num_times 1 -output "$PREFIX$OUTPUT" -geometry $GEOMETRY -longitude $LONGITUDE -latitude $LATITUDE
else
xplanet -num_times 1 -output "$PREFIX$OUTPUT" -geometry $GEOMETRY -longitude $LONGITUDE -latitude $LATITUDE -projection $PROJECTION
fi

# Update Gnome backgound - this works in Ubuntu 9.04 & 10.04
gconftool -t str -s /desktop/gnome/background/picture_filename "$PREFIX$OUTPUT"
sleep $DELAY
rm $lockfile
exec $0

```

---

### Post by mgmiller on 2009-08-21
dcstar....

Thank you.  I finally got it working in 9.04 thanks to your script.

Do you know how to do the cloud overlay?

---

### Post by Montybank on 2009-08-30
Hey, that solution is excellent. I've been looking to try to make this work for a while. Thanks, I learned a lot with this.

M

---

### Post by dcstar on 2010-12-28
> **dcstar said:**
> I have had a play around with this script and come up with one that works well on my 9.04 & 10.04 systems (the original script could result in multiple instances running), here it is for anyone else who may want to use/improve it.

**This has been modified to clean up any left over lock files after a crash/reboot and to automatically get screen resolution and your location to center the display**:
.........

Modified script available in this post:

[http://ubuntuforums.org/showpost.php?p=7730656&postcount=19](http://ubuntuforums.org/showpost.php?p=7730656&postcount=19)

---

