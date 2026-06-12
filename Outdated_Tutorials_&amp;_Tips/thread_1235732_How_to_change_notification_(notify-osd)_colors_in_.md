---
title: "How to: change notification (notify-osd) colors in Jaunty"
date: 2009-08-09
forum: Outdated Tutorials &amp; Tips
---

### Post by johnl on 2009-08-09
I changed my wallpaper and theme yesterday and was quite happy with it, until one of those cool new notifications popped up in it's default white-on-black color scheme.  I couldn't find a way to change it's colors, so I downloaded the source, poked around, and hacked this together.  Check the attached screenshots for final results.

default.png - this is what your notifications look like now.
blueish.png, uglyred.png - these are some changed colors using the following howto.

**this code is not supported by the notify-osd authors at all.**  But it's a pretty small hack :)

Follow these steps to build a version of notify-osd that allows you to change the background color/opacity and text color/opacity.  Note that this is only tested on the current Ubuntu Jaunty version, 0.9.11

**1. download & install dependencies**
install basic development tools:
```
sudo apt-get install build-essential libnotify-bin
```
get the required libraries to build notify-osd:
```
sudo apt-get build-dep notify-osd
```

**2. download notify-osd source including any ubuntu patches**
*note that you should not use 'sudo' for this next command.  I am doing this in my '/tmp' directory, but you can do it wherever you please.  If you do it elsewhere, make sure wherever you see /tmp below you use your directory.*
Get the source:
```

cd /tmp
apt-get source notify-osd

```
You should now have a folder named 'notify-osd-0.9.11'

**3. download and apply the attached patch file**
right click on the attached .patch.txt file.  choose to save it in the same directory you fetched the source (in my case, /tmp).

Apply the patch:
```

cd /tmp
cd notify-osd-0.9.11/src
patch < ../../notify-color-hack.patch.txt

```
There should not be any errors.

**4. build a new notify-osd**
Configure and build notify-osd:
```

cd /tmp/notify-osd-0.9.11
./configure --prefix=/usr
make

```
There should not be any errors.

**5. Test that it works**
*save the following file as  ".notify-osd" in your home directory:*
```

bubble-background-color = 6D84B4
bubble-background-opacity = .85
text-title-color = ffffff
text-title-opacity = 1.0	
text-body-color = ffffff
text-body-opacity = 1.0

```
stop the current notify-osd:
```
killall notify-osd
```
start our new notify-osd:
```

cd /tmp/notify-osd-0.9.11/src
./notify-osd

```
You should see the following:
*reading settings from '/home/<youruser>/.notify-osd'*
And the program should stay open.  If it says:
> 
** (notify-osd:5373): WARNING **: Another instance has already registered org.freedesktop.Notifications

Then go back to the 'killall' step and try again.

Now, do something to cause a notification.  In a new terminal window enter:
```
notify-send "test" "this is a test"
```

You should (hopefully) see your notification in white text on a dark blue background.

You can now kill the notify-osd we started earlier by hitting control+C in it's terminal window.

**6. Install our new notify-osd**
Install our new notify-osd over the current install:
```

cd /tmp/notify-osd-0.9.11
sudo make install

```
Now make sure our version is the running version:
```

killall notify-osd
notify-send "test" "this is a test"

```


**7. Customizing the colors**
edit the file ~/.notify-osd to edit the colors.  Because this is a quick hack, make sure that each line follows the format "key = value" *including the spaces around the equals sign*.  It's lame, I know.

*-color entries change the color of that item.  For example, bubble-background-color changes the notification window color.  The value for these entries is a html-style color without the leading "#".   E.g,

```
bubble-background-color = c0c0c0
```

will give you a light gray window.

*-opacity entries change the opacity (transparency) of that item when compiz is enabled.   "1.0" means entirely opaque.  "0.0" means entirely transparent (invisible).  E.g,

```
bubble-background-opacity = 0.75
```

Will give you a window that is 75% opaque.



**If you make changes to the configuration file you must kill the current running notify-osd process ('killall notify-osd') before you will see the changes.** You don't need to restart it as it will restart automatically next time it is needed.


Hope this is useful for someone!

---

### Post by Wanas on 2009-08-17
That was cool 
but is there a way to hack this notify-osd to appear while watching videos (not in a full screen) because pidgin notification wont appear while watching videos in totem

---

### Post by Labello on 2009-08-17
> **Wanas said:**
> That was cool 
but is there a way to hack this notify-osd to appear while watching videos (not in a full screen) because pidgin notification wont appear while watching videos in totem

well it does in vlc.

---

### Post by Wanas on 2009-08-17
> **Labello said:**
> well it does in vlc.

Is there a way to make it work for totem and other media players ?

---

### Post by Pagamim on 2009-09-13
hi, im trying to ONLY change the position of it but i could not do it, i just wanted to change from the upper corner to the down corner, maybe its a pretty easy task but i could not do it lol.

can anyone help me?

thanks

---

### Post by johnl on 2009-09-15
> **Pagamim said:**
> hi, im trying to ONLY change the position of it but i could not do it, i just wanted to change from the upper corner to the down corner, maybe its a pretty easy task but i could not do it lol.

can anyone help me?

thanks

Unfortunately notify-osd does not allow you to change the position.  This is something I wanted to fix as well but it's not as simple a task as changing the color.  Perhaps in the future I will have time to come up with a patch for that :).

---

### Post by Pagamim on 2009-09-15
> **johnl said:**
> Unfortunately notify-osd does not allow you to change the position.  This is something I wanted to fix as well but it's not as simple a task as changing the color.  Perhaps in the future I will have time to come up with a patch for that :).

thanks for the reply :D

i will keep that in mind,

thanks a lot :D

---

### Post by Vish... on 2010-04-21
> **johnl said:**
> 
[...][B]
this code is not supported by the notify-osd authors at all.[/B]  But it's a pretty small hack :)
[....]
Hope this is useful for someone!

Hi Johnl,

In case you aernt subscribed to the ayatana mailing list, Your UI modification prefs were discussed on the mailing list and I wanted to bring to your attention this reply from Mark> [https://lists.launchpad.net/ayatana/msg01337.html](https://lists.launchpad.net/ayatana/msg01337.html)

Kindly have a look at [https://help.launchpad.net/Code/Review#Proposing%20a%20merge](https://help.launchpad.net/Code/Review#Proposing%20a%20merge)

We can get it merged into the main branch, And supported by the notify-osd authors ;)

---

### Post by SilverWave on 2010-04-26
Thanks, this was one of two posts that helped point me in the right direction with my issues re notify-osd.

My solution was just to reduce the pop-up time.

Its amazing how much that changes my appreciation of the  notifications... I have found the annoyance is mainly based on them  being on screen too long.

I have created a PPA and it has a notify-osd that is set to 3secs not  10secs.
The best is yet to come…

     **[notify-osd – Now with 70% Less Annoy :-)]("http://silverwav.wordpress.com/2010/05/08/notify-osd-now-with-70-less-annoy/")**

> 
                                                 sudo  add-apt-repository ppa:silverwave/apps-0
 > [B]Lucid
[/B] 
These work for me and my environment...

---

