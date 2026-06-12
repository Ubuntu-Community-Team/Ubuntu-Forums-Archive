---
title: "touchpad misbehaving"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by bharuchas on 2011-10-03
Hi,
I am using UNR 10.04 LTS on my Benq Joybooklite, All was functioning okay till last week, when my right click and vertical scrolling on the touchpad stopped, for the past week i have been trying all sugestions on the forum, and have managed to mess things further. 

Regards,
Sohrab.

---

### Post by anewguy on 2011-10-03
Have you installed synaptiks?

Dave ;)

---

### Post by Denver Dave on 2011-10-03
I also have an issue with my touchpad - Acer Aspire 7741.  The vertical right edge scroll has never worked with ubuntu 11.04 - works fine with Windows 7.  I'm running the standard install from the DVD to create a USB boot.  I've poked around in some of the config files and see synaptiks mentioned, but I've not installed anything special.

[http://ubuntuforums.org/showthread.php?t=1851807](http://ubuntuforums.org/showthread.php?t=1851807)

---

### Post by bharuchas on 2011-10-03
> **anewguy said:**
> Have you installed synaptiks?

Dave ;)
Thanks dave,
its not in the ubuntu software centre, can you guide me on how to do that?
Regards,
Sohrab.

---

### Post by bharuchas on 2011-10-03
> **bharuchas said:**
> Thanks dave,
its not in the ubuntu software centre, can you guide me on how to do that?
Regards,
Sohrab.

Have installed Gsynaptics, howeverin touchpad, when i click it leaves this message:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Please help....

---

### Post by anewguy on 2011-10-06
> **Denver Dave said:**
> I also have an issue with my touchpad - Acer Aspire 7741.  The vertical right edge scroll has never worked with ubuntu 11.04 - works fine with Windows 7.  I'm running the standard install from the DVD to create a USB boot.  I've poked around in some of the config files and see synaptiks mentioned, but I've not installed anything special.

[http://ubuntuforums.org/showthread.php?t=1851807](http://ubuntuforums.org/showthread.php?t=1851807)

Sorry, forgot to get back to this thread.  The packages are the xserver-xorg-input-synaptics and tpconfig.


dave ;)

---

### Post by anewguy on 2011-10-06
> **bharuchas said:**
> Have installed Gsynaptics, howeverin touchpad, when i click it leaves this message:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Please help....

This would be an option set in the input section for the touchpad in the xorg.conf file - a file which tells X (what is providing all those neat GUI things you like ;) ) how it needs to configure itself.  However, with the "new" X the file isn't there by default as X is supposed to self-configure.

So, I know you could create an entire xorg.conf file, but I think you can also create it with only those things defined for which you want to redefine what was auto-configured.  In this case, I think you could have an xorg.conf file with just the input section for the touchpad with the option SHMConfig defined as true.

If you need help on that please post back - remember Google/Yahoo!/Bing, etc., are your best friend when looking to learn about these things.

Dave ;)

---

### Post by bharuchas on 2011-10-07
Dear Dave thanks, I understood why i do not have that file.

I did try to create a new Xconfig.org file with the sugesstions as in various threads on this forum, but it did not work. Could you please give me the exact details of what I should put into that as I am a real newbie in this.
Regards,
Sohrab. 

> **anewguy said:**
> This would be an option set in the input section for the touchpad in the xorg.conf file - a file which tells X (what is providing all those neat GUI things you like ;) ) how it needs to configure itself.  However, with the "new" X the file isn't there by default as X is supposed to self-configure.

So, I know you could create an entire xorg.conf file, but I think you can also create it with only those things defined for which you want to redefine what was auto-configured.  In this case, I think you could have an xorg.conf file with just the input section for the touchpad with the option SHMConfig defined as true.

If you need help on that please post back - remember Google/Yahoo!/Bing, etc., are your best friend when looking to learn about these things.

Dave ;)

---

### Post by anewguy on 2011-10-07
Try booting to recovery mode at the boot menu.  Then do:

sudo sudo X -configure

This should create a new file called xorg.conf.new (I think this will be in the root folder).

Then:

cp xorg.cong.new /home/<your userid>/xorg.xconf.new.txt 

Reboot:

sudo shutdown -r now

Then attach it to a reply back here.  We'll work on it from there.


Dave ;)

---

### Post by bharuchas on 2011-10-07
Dear Dave,
Thanks so much for the revert, not being from this line, i have (quite proudly) managed to find (:) through google) how to go into recovery mode. and have made all the changes, as you said below. But when i try to go to the root folder to access xorg.xconf.new.txt, it says permission denied, how can i access it. By the way now the right click works but the vertical scrolling does not. Also the Touchpad application still shows the same error.
Regards,
Sohrab


> **anewguy said:**
> Try booting to recovery mode at the boot menu.  Then do:

sudo sudo X -configure

This should create a new file called xorg.conf.new (I think this will be in the root folder).

Then:

cp xorg.cong.new /home/<your userid>/xorg.xconf.new.txt 

Reboot:

sudo shutdown -r now

Then attach it to a reply back here.  We'll work on it from there.


Dave ;)

---

### Post by anewguy on 2011-10-07
Sorry about that - when copying from/to the /etc/X11 folder you must put "sudo " on the front of the copy command.  It will ask for a password - just enter your normal password (it won't show on the screen).

Also note a typo on my part:

cp xorg.cong.new /home/<your userid>/xorg.xconf.new.txt 

Should be:

cp xorg.conf.new /home/<your userid>/xorg.conf.new.txt 

Also note that in a previous post I had 2 "sudo "'s on the front of the X -configure statement -> it should be only 1.

Fat fingers, little keyboard!  ;)

Dave ;)

---

### Post by bharuchas on 2011-10-07
Dear Dave,
I am really greatful for all this bothering I am doing, thanks figured it out, my file was in /root and now understood the syntax of the copy command. Have attached the file. 
Now please guide me on the next step.
Regards,
Sohrab.

---

### Post by bharuchas on 2011-10-10
Dear Dave,
Please do not forget me.
Regards,
Sohrab.

> **bharuchas said:**
> 
Dear Dave,
I am really greatful for all this bothering I am doing, thanks figured it out, my file was in /root and now understood the syntax of the copy command. Have attached the file. 
Now please guide me on the next step.
Regards,
Sohrab.

---

### Post by anewguy on 2011-10-14
Sorry about that - I actually thought this was solved.

I just spent some time searching for benq lite, ubuntu and touchpad together to see if there is perhaps a special driver.  Nothing is very promising in that regard.

I did find an ubuntu how-to that suggests doing the following in a terminal window, so please do so and post the results back here.  It might give me more to go on.

xinput list


Thanks,
Dave ;)

---

### Post by bharuchas on 2011-10-14
> **anewguy said:**
> Sorry about that - I actually thought this was solved.

I just spent some time searching for benq lite, ubuntu and touchpad together to see if there is perhaps a special driver.  Nothing is very promising in that regard.

I did find an ubuntu how-to that suggests doing the following in a terminal window, so please do so and post the results back here.  It might give me more to go on.

xinput list


Thanks,
Dave ;)
Dear Dave,
Thanks, I agree no promises :) but hope is eternal, here is the xinput list:
sohrab@sohrab-laptop:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Synaptics TouchPad                 	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB Webcam                              	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
sohrab@sohrab-laptop:~$
REgards,
Sohrab

---

### Post by anewguy on 2011-10-14
Well, at least it does think it's a Synaptics TouchPad so we don't have to worry about an Alps or other driver.  I found the following Ubuntu Manpage online that shows some of this - I'm going to do some looking to be sure I understand how to incorporate this into the "new" Xorg since it auto-configures.  Your xorg.conf didn't show a touchpad as input so we do need to add the definition.

You may want to look at the manpage while I do my checking.  Probably won't get back to you now until late Friday U.S. time.

[http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html]("http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html")


Dave ;)

---

### Post by anewguy on 2011-10-14
You should check in synaptics package manager and see if the following package is installed - if not, install it:

xserver-xorg-input-synaptics


I'll keep looking for more info.

Dave ;)

---

### Post by anewguy on 2011-10-14
After you have installed or verified that the xorg server package for touchpad is installed, do the following in a terminal window:

- gksudo gedit /etc/X11/xorg.conf

- if there is anything in the file just clear it out

- add the following, so they are the ONLY lines in the file:

Section "InputClass"
        Identifier "enable synaptics SHMConfig"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Option "SHMConfig" "on"
EndSection


- save the file, exit the editor, exit the terminal window
- reboot
- after the reboot you should have the xorg touchpad working and gsynaptics should run now as well.


Dave ;)

---

### Post by bharuchas on 2011-10-14
Dear Dave,
Did all that you suggested, but the edge scrolling is still not on and neither can i get the touchpad programme tro work, its still showing an error. 
Will await your return to my world. Thank you for all the help, awaiting your inputs.
Regards,
Sohrab.

---

### Post by anewguy on 2011-10-14
Gsynaptics should be working now.  Found a large touchpad reference on the net.  The following is taken from that:


> Scrolling does not work anymore

Probably the scroll variables must be set.

You can try it on the fly if SHMConfig is enabled:

  synclient VertEdgeScroll=1
  synclient VertScrollDelta=45
  synclient HorizEdgeScroll=1
  synclient HorizScrollDelta=45

If this works for you, you can add this configuration to your /etc/X11/xorg.conf Synaptics InputDevice section:

  Option      "VertEdgeScroll"    "1"
  Option      "VertScrollDelta"  "45"
  Option      "HorizEdgeScroll"   "1"
  Option      "HorizScrollDelta" "45"


So, the ones that start with "synclient" you just type in a terminal window, then go and see if scrolling is working.

The lines that begin with "Option" actually go in the /etc/X11/xorg.conf file, right after the option for shmconfig.  Use the editor again to edit this (remember gksudo at the front!), then save the file and the easiest thing is to just reboot.

Let me know how any of that turns out or if you have more problems.

Dave ;)

---

### Post by bharuchas on 2011-10-15
Dear Dave,
Thanks tried that, got this revert
sohrab@sohrab-laptop:~$ synclient VertEdgeScroll=1
Couldn't find synaptics properties. No synaptics driver loaded?
SO do i now need to enable SHM Config

Regards,
Sohrab.

> **anewguy said:**
> Gsynaptics should be working now.  Found a large touchpad reference on the net.  The following is taken from that:





So, the ones that start with "synclient" you just type in a terminal window, then go and see if scrolling is working.

The lines that begin with "Option" actually go in the /etc/X11/xorg.conf file, right after the option for shmconfig.  Use the editor again to edit this (remember gksudo at the front!), then save the file and the easiest thing is to just reboot.

Let me know how any of that turns out or if you have more problems.

Dave ;)

---

### Post by anewguy on 2011-10-15
You did install the xserver-xorg-input-synaptics package as per a previous post, right?

You did create a xorg.conf file via gksudo gedit /etc/X11/xorg.conf and you did load it with just the lines I specified, right?

If so, I don't understand why the driver wouldn't be loaded, unless there was an error in the xorg.conf file.

Post back here and attach the /var/log/Xorg.0.log file so I can see if there are any error messages coming up in it.


Dave ;)

---

### Post by Enterpart on 2011-10-15
Using Easystroke you can set up the scrolling wheel and also add up to 4 scroll wheels using the corners. and even use them as tap zones for keystrokes or scripts. check this out

link [http://ubuntuforums.org/showthread.php?t=1859936]("http://ubuntuforums.org/showthread.php?t=1859936")

and how to configure the tap zones

[http://ubuntuforums.org/showthread.php?t=1824870]("http://ubuntuforums.org/showthread.php?t=1824870")

---

### Post by bharuchas on 2011-10-15
Dear Dave,
Yes, I did them all, whatever you had specified, everything was done.
Attached is the file. The upload manager was not accepting as it exceeded 19.5KB so changed format to .doc file
Regards,
Sohrab.

> **anewguy said:**
> You did install the xserver-xorg-input-synaptics package as per a previous post, right?

You did create a xorg.conf file via gksudo gedit /etc/X11/xorg.conf and you did load it with just the lines I specified, right?

If so, I don't understand why the driver wouldn't be loaded, unless there was an error in the xorg.conf file.

Post back here and attach the /var/log/Xorg.0.log file so I can see if there are any error messages coming up in it.


Dave ;)

---

### Post by bharuchas on 2011-10-15
thanks enterpart, will try and revert.
Regards,
Sohrab.

---

### Post by anewguy on 2011-10-15
I forgot to have you put the driver statement in the xorg.conf file.  It should have a statement like this added:

Driver		"synaptics"


So, you will need to edit the xorg.conf file again (gksudo gedit /etc/X11/xorg.conf).  It should look like this when you are done (addition is in red):

Section "InputClass"
Identifier "enable synaptics SHMConfig"
[COLOR="Red"]Driver		"synaptics"[/COLOR]
MatchIsTouchpad "on"
MatchDevicePath "/dev/input/event*"
Option "SHMConfig" "on"
EndSection

Remember to save the file before exiting the editor! ;)


Try doing that edit and rebooting, then let me know how it goes.

If it still doesn't have scrolling enabled, try gsynaptics again, and failing all else, add the lines I mentioned before into the xorg.conf file.

Dave ;)

EDIT:  Forgot to mention on your question about SHMConfig - we are turning it on automatically in the xorg.conf file.  Once the driver is defined so X accepts the touchpad definition, it should all be there.  Gsynaptics won't run because I had forgotten to have you define the driver in the xorg.conf file.

---

### Post by Enterpart on 2011-10-15
bharuchas this is much easier and safer way and quick to
to enable SHMConfig

do this by the following method

Enter this command, it will give you access to change files on nautilus

```
sudo nautilus
```

Enter Password -> go to "File System" -> "USR" -> "share" -> "X11" -> "xorg.conf.d" -> "50-synaptics.conf"

now you should see this

Section "InputClass"
        [INDENT]Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"[/INDENT]
EndSection

you want to add **Option "SHMConfig"  "true"** so it looks like this 

[ATTACH]204448[/ATTACH]

save and exit
did that help?
then reboot
all this is giving in the second link I posted in my previous post and much more. tell me how it went on

---

### Post by anewguy on 2011-10-15
> **Enterpart said:**
> bharuchas this is much easier and safer way and quick to
to enable SHMConfig

do this by the following method

Enter this command, it will give you access to change files on nautilus

```
sudo nautilus
```

Enter Password -> go to "File System" -> "USR" -> "share" -> "X11" -> "xorg.conf.d" -> "50-synaptics.conf"

now you should see this

Section "InputClass"
        [INDENT]Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"[/INDENT]
EndSection

you want to add **Option "SHMConfig"  "true"** so it looks like this 

[ATTACH]204448[/ATTACH]

save and exit
did that help?
then reboot
all this is giving in the second link I posted in my previous [http://www.microcenter.com/single_product_results.phtml?product_id=0325752poshttp://www.microcenter.com/single_product_results.phtml?product_id=0325752t](http://www.microcenter.com/single_product_results.phtml?product_id=0325752poshttp://www.microcenter.com/single_product_results.phtml?product_id=0325752t) and much more. tell me how it went on

I've just been having them mess in xorg.conf so that we don't mess up what might aleady be there in the new "X" configuration files.  If you look through the X.0.log I had them attach, you'll see that it appears the synaptics driver isn't being loaded.  By keeping any changes in the xorg.conf, they are extremely easy to isolate and won't "break" anything included.  Judging by the problems, I'd say that the default touchpad definitions delivered by Ubuntu weren't working.  Easiest way to avoid trouble - edit xorg.conf for settings that will override the defaults.a separate file there in the high number range so it will override th 

I do understand exactly where you are coming from.  By preference, I would prefer to see it in the default "rules" section of the file system, bua separate file there in the high number range so it will override th t instead of modifying that which is delivered (it could be overwritten by an update or upgrade), I prefer to create a separate file there in the high number range so it will override the 50- file.  That new file shouldn't be messed with by an update, and can be saved for a future install (such as doing a clean install at 12.04).

Those are just my preferences for myself, and I'd really like to keep working with this user, preferably until my path is exhausted, since we've already done a lot of work together (albeit fruitless to date ;) ).  The OP may not realize it, but this is giving me a chance to learn as well - that's probably very selfish of me, but if they can hold on just a little bit I think all will be well, then I'll have them copy the xorg.conf over to something like 90-touchpad-overrides.conf so it will be in the correct place.

Thanks for the input!  I really don't mean to be arguing with anyone, so please don't take it that way!  I'm just trying help the OP (as we all are) and trying to learn a little something along the way.  I have ubuntu on my desktop, but my laptop is too new for me to want to take a chance on something happening hardware-wise (not related to Ubuntu) and messing up my warranty.  So, I'm selfishly trying to learn something here, too.

So......bharuchas, do what ever you might want to do from any of these posts to solve your problem.  I was just selfishly hoping to continue so I can learn a little something along the way as well.

Above all, do what you want to solve the problem in the way you want it solved.  And to everyone else who has posted - I'm sorry I'm selfish on this one, and I hope that isn't distracting from helping the OP.  Thank you all for your input as I'm am learning from that as well.

Dave ;)

If you follow the previous post, make these minor changes:

- rather than starting nautilus as super user, user gksudo gedit to edit the file - we won't have to worry about some accidental typing messing something else up

- the path to the file is /usr/share/X11/xorg.conf.d/50-synaptics.conf, NOT /USR/share/X11/xorg.conf.d/50-synaptics.conf

---

### Post by Enterpart on 2011-10-15
Hey anewguy I completely understand bud. I respect your learning curve and I just want to add that I'm a complete noob and I think I understand what your saying about the higher level. The workaround I gave was learnt by what others have wrote so I cant really explain what it means so that's why I respect what your trying to do. I just like to say that the information that I supplied which was taken from a different post suggested its dangerous to mess around with higher order levels as you are suggesting and can have severe consequences. whereas the lower level stuff can't really mess you up. I can see that you care about this and have good intentions, I hope you help him out and learn in the process. 

heres the link from where I got that information from.

[http://ubuntuforums.org/showthread.php?t=1603683&highlight=tap+zones]("http://ubuntuforums.org/showthread.php?t=1603683&highlight=tap+zones")

Peace

---

### Post by anewguy on 2011-10-15
> **Enterpart said:**
> Hey anewguy I completely understand bud. I respect your learning curve and I just want to add that I'm a complete noob and I think I understand what your saying about the higher level. The workaround I gave was learnt by what others have wrote so I cant really explain what it means so that's why I respect what your trying to do. I just like to say that the information that I supplied which was taken from a different post suggested its dangerous to mess around with higher order levels as you are suggesting and can have severe consequences. whereas the lower level stuff can really mess you up. I can see that you care about this and have good intentions, I hope you help him out and learn in the process. 

heres the link from where I got that information from.

[http://ubuntuforums.org/showthread.php?t=1603683&highlight=tap+zones]("http://ubuntuforums.org/showthread.php?t=1603683&highlight=tap+zones")

Peace

Glad you're on board with Ubuntu!  1 thing I did learn when they started the new "X" - that is, no xorg.conf supposedly needed as it tries to configure itself.  They put default defs for some things - like what you see for the touchpad - in files usually lower than 90.  This allows you to override what they are doing by creating your own file with a name that starts with a number higher than the number on the default file.  So, I've just been putting mine in the 90's.  I also learned the hard way that to make the edits to the default files can result in loss of your changes when X is updated.  So, that's why I recommend that.  If you ever take a look at the device rules in udev, you'll see they work the same way, and you should create your own file there as well.  Obviously with either of these you want to keep a copy of these somewhere so that if you have to reinstall or you do a clean install of a new release, you can put the files back and everything "should" work.  Don't know if I explained that very well but I hope you get enough from it.

Glad you took everything the right way - sometimes I make people upset when I never meant to!  ;)

Have a good one, and feel free to post anything else you might find!

Dave ;)

---

### Post by anewguy on 2011-10-16
bharuchas:  just wondered if you've made any progress?

One thing that should be noted is in the xorg.conf I have you working on needs a change:

Option "SHMConfig" "on"

should indeed be:

Option "SHMConfig" "true"


I guess I must have mis-read what I was looking at.  After seeing Enterpart's use of "true" I went looking on the net and indeed it is supposed to be "true", not "on".

Dave ;)

---

### Post by bharuchas on 2011-10-17
Morning David,
Sorry but we have been experiencing an electricity shortage in my part of the world, so cannot get online as frequently.
However, decided to go with your suggestions, have amended the xorg file as below:

Section "InputClass"
Identifier "enable synaptics SHMConfig"
Driver	 "synaptics"
MatchIsTouchpad "on"
MatchDevicePath "/dev/input/event*"
Option "SHMConfig" "true"
EndSection 

But no luck as of now on the scrolling. What do you suggest now?
Regards,
Sohrab.

> **anewguy said:**
> bharuchas:  just wondered if you've made any progress?

One thing that should be noted is in the xorg.conf I have you working on needs a change:

Option "SHMConfig" "on"

should indeed be:

Option "SHMConfig" "true"


I guess I must have mis-read what I was looking at.  After seeing Enterpart's use of "true" I went looking on the net and indeed it is supposed to be "true", not "on".

Dave ;)

---

### Post by anewguy on 2011-10-17
> **bharuchas said:**
> Morning David,
Sorry but we have been experiencing an electricity shortage in my part of the world, so cannot get online as frequently.
However, decided to go with your suggestions, have amended the xorg file as below:

Section "InputClass"
Identifier "enable synaptics SHMConfig"
Driver	 "synaptics"
MatchIsTouchpad "on"
MatchDevicePath "/dev/input/event*"
Option "SHMConfig" "true"
EndSection 

But no luck as of now on the scrolling. What do you suggest now?
Regards,
Sohrab.

That should have gotten you to where you can try gsynaptics or try the synclient lines.  If those work, add the option lines I put in that same post.  Since I'm not using one and don't have the problem it's hard for me to test -  you may need to use sudo on the front of gsynaptics of the synclient lines.

Dave ;)

---

### Post by bharuchas on 2011-10-17
Dear Dave,
Tried and results as below:
sohrab@sohrab-laptop:~$ synclient VertEdgeScroll=1
Couldn't find synaptics properties. No synaptics driver loaded?
sohrab@sohrab-laptop:~$ synclient VertScrollDelta=45
Couldn't find synaptics properties. No synaptics driver loaded?
sohrab@sohrab-laptop:~$ synclient HorizEdgeScroll=1
Couldn't find synaptics properties. No synaptics driver loaded?
sohrab@sohrab-laptop:~$ synclient HorizScrollDelta=45
Couldn't find synaptics properties. No synaptics driver loaded?
sohrab@sohrab-laptop:~$ sudo synclient VertEdgeScroll=1
[sudo] password for sohrab: 
Couldn't find synaptics properties. No synaptics driver loaded?
Is the result.
Regards,
Sohrab.

> **anewguy said:**
> That should have gotten you to where you can try gsynaptics or try the synclient lines.  If those work, add the option lines I put in that same post.  Since I'm not using one and don't have the problem it's hard for me to test -  you may need to use sudo on the front of gsynaptics of the synclient lines.

Dave ;)

---

### Post by anewguy on 2011-10-18
Original line here was edited out as it didn't belong here.


Try the following:

gksudo gedit /usr/share/X11/xorg.conf.d/90-xtra-touchpad.conf 

put the following in the file (you can just copy/paste):


Section "InputClass"
Identifier "enable synaptics SHMConfig"
Driver "synaptics"
MatchIsTouchpad "on"
MatchDevicePath "/dev/input/event*"
Option "SHMConfig" "true"
EndSection


Save the file, exit the editor, exit the terminal and reboot.  Don't worry about the scrolling yet: try the synclient lines again.  If they fail with the same error messages, post back here and attach the /var/log/Xorg.0.log file to the post.

Thanks,
Dave ;)

---

### Post by bharuchas on 2011-10-18
Dear Dave,
Thanks for the revert, there is no xorg.conf.d file in x11 folder.
Where did i mess up?
Regards,
Sohrab.
> **anewguy said:**
> Enter Password -> go to "File System" -> "USR" -> "share" -> "X11" -> "xorg.conf.d" -> "50-synaptics.conf"

Try the following:

gksudo gedit /usr/share/X11/xorg.conf.d/90-xtra-touchpad.conf 

put the following in the file (you can just copy/paste):


Section "InputClass"
Identifier "enable synaptics SHMConfig"
Driver "synaptics"
MatchIsTouchpad "on"
MatchDevicePath "/dev/input/event*"
Option "SHMConfig" "true"
EndSection


Save the file, exit the editor, exit the terminal and reboot.  Don't worry about the scrolling yet: try the synclient lines again.  If they fail with the same error messages, post back here and attach the /var/log/Xorg.0.log file to the post.

Thanks,
Dave ;)

---

### Post by anewguy on 2011-10-19
My fault - forgot to edit out the first line in that post.  I'll get that corrected.  Note that xorg.conf.d is not a file, it's a folder/directory.  It's everything beyond that you want to do:

Try the following:

gksudo gedit /usr/share/X11/xorg.conf.d/90-xtra-touchpad.conf

put the following in the file (you can just copy/paste):


Section "InputClass"
Identifier "enable synaptics SHMConfig"
Driver "synaptics"
MatchIsTouchpad "on"
MatchDevicePath "/dev/input/event*"
Option "SHMConfig" "true"
EndSection


Save the file, exit the editor, exit the terminal and reboot. Don't worry about the scrolling yet: try the synclient lines again. If they fail with the same error messages, post back here and attach the /var/log/Xorg.0.log file to the pos

---

### Post by bharuchas on 2011-10-19
Dear Dave,
When I tried to save the file got this error" Could not find the file /usr/share/X11/xorg.conf.d/90-xtra-touchpad.conf."
What next.
Regards,
Sohrab.

> **anewguy said:**
> My fault - forgot to edit out the first line in that post.  I'll get that corrected.  Note that xorg.conf.d is not a file, it's a folder/directory.  It's everything beyond that you want to do:

Try the following:

gksudo gedit /usr/share/X11/xorg.conf.d/90-xtra-touchpad.conf

put the following in the file (you can just copy/paste):


Section "InputClass"
Identifier "enable synaptics SHMConfig"
Driver "synaptics"
MatchIsTouchpad "on"
MatchDevicePath "/dev/input/event*"
Option "SHMConfig" "true"
EndSection


Save the file, exit the editor, exit the terminal and reboot. Don't worry about the scrolling yet: try the synclient lines again. If they fail with the same error messages, post back here and attach the /var/log/Xorg.0.log file to the pos

---

### Post by anewguy on 2011-10-19
We are creating a new file, and it shouldn't give you that error.

I opened a terminal window, then used the mouse to highlight and copy the gksudo statement for the editor.  Pasted that into the terminal and it works fine.  I would suspect the path you typed is in error.  So, just use the mouse and cut and paste each line, including starting with the gedit line to start the entire thing.


Dave ;)

---

### Post by bharuchas on 2011-10-20
Dear Dave,
I think The reason I am geting that error is that there is no folder in X11 called Xorg.conf.d, I checked physically, and its not there.
regards,
Sohrab.

> **anewguy said:**
> We are creating a new file, and it shouldn't give you that error.

I opened a terminal window, then used the mouse to highlight and copy the gksudo statement for the editor.  Pasted that into the terminal and it works fine.  I would suspect the path you typed is in error.  So, just use the mouse and cut and paste each line, including starting with the gedit line to start the entire thing.


Dave ;)

---

### Post by anewguy on 2011-10-20
What release are you running?  BTW - your reply shows Xorg when it is xorg.  Just cut and paste the editor line.

---

### Post by bharuchas on 2011-10-20
Hi Dave,
Its Ubuntu 10.04 LTS Netbook edition. Using on BenQ Joybook Lite U101B.
That was a typo, I always cut and paste your instructions.
Regards,
Sohrab.

> **anewguy said:**
> What release are you running?  BTW - your reply shows Xorg when it is xorg.  Just cut and paste the editor line.

---

### Post by anewguy on 2011-10-20
I'm a litle confused now - I thought the auto-config X was delivered in 10.04.  I also thought the config files have always been in the same folder since then.  So, right now I don't understand why that folder isn't there, unless I messed up the typing, haven't seen it, and now am so used to it that my mind is seeing what it wants to.

Perhaps someone else knows if by chance the X configure files have moved since 10.04.

Dave ;)

---

### Post by anewguy on 2011-10-27
Okay, I went back to 10.10 - in other words, a patched 10.04.  I found the folder just fine - see the attached screen shot.  So, try the edit again, watching the spacing, case, spelling, etc., very closely.

When you create the file, also add the lines mentioned previously for scrolling, and change the identifier.  So, just cut and paste the below:

Section "InputClass"
Identifier "PS/2 Synaptics TouchPad"
Driver "synaptics"
MatchIsTouchpad "on"
MatchDevicePath "/dev/input/event*"
Option "SHMConfig" "true"
Option "VertEdgeScroll" "1"
Option "VertScrollDelta" "45"
Option "HorizEdgeScroll" "1"
Option "HorizScrollDelta" "45" 
EndSection

Save the file and try again.

Dave ;)

---

### Post by BillyBoa on 2011-10-27
Sometimes it's easier to re install the system. You need 45 min and you have a new computer.

---

### Post by anewguy on 2011-10-27
I try to avoid that when possible, but I'm leaning that way as well.  I don't understand why none of this is working - it should be.

So, I agree - save whatever you want to save then reinstall Ubuntu - be sure to tell it to format the partitions.


Dave

---

### Post by bharuchas on 2011-10-27
Dear Dave,
Thanks for all the help, Attached is the screenshot of my X11 folder.
I was trying to resolve it without the re-installation, as being a newbie, i am afraid I will mess something up.
But you are right, will re-install. Thanks for all your patience and help.
Warm Regards,
Sohrab.
> **anewguy said:**
> I try to avoid that when possible, but I'm leaning that way as well.  I don't understand why none of this is working - it should be.

So, I agree - save whatever you want to save then reinstall Ubuntu - be sure to tell it to format the partitions.


Dave

---

### Post by bharuchas on 2011-10-28
Well Dave, reinstalled, messed up a lot, now i have 3-4 versions of UNR running, but have git the touchpad, running beautifully.
I still dont have the folder in X11, but who cares. 
Thanks a lot for all the help.
Regards,
Sohrab.
> **bharuchas said:**
> Dear Dave,
Thanks for all the help, Attached is the screenshot of my X11 folder.
I was trying to resolve it without the re-installation, as being a newbie, i am afraid I will mess something up.
But you are right, will re-install. Thanks for all your patience and help.
Warm Regards,
Sohrab.

---

### Post by anewguy on 2011-10-29
I'm just glad it's working for you!

Best of luck!

Dave ;)

---

### Post by scubanix on 2011-11-09
discovered this thread yesterday and read it all hoping to find a solution for my problem trying to get the gsynaptics running...

tried it all, including re-installation and nothing worked.

can we continue trying? is there anybody out there who can help?

---

### Post by Denver Dave on 2011-11-09
I have an acer aspire laptop and the touchpad does generally work, the right scroll doesn't and I have an issue that the cursor will jump around in the text being edited.  Might be the touchpad and might not be, but I suspect I might lightly brush it, haven't tried with a separate keyboard.  Problem does not happen on my desktop.  

So in answer to your question, I haven't solved this or the quality of the Crystal Eye webcam is much worse with ubuntu than under Windows 7 - suspect driver.  Called Acer support, they were of no help and would not even talk about linux issues.

If any others with acer aspires have the same issue, night mention it and especially if you have found solutions.

The reverse question may be important in the future - are there webcams and laptops with touchpads that do work well with ubuntu?  Maybe I'll buy them next time around.

I'm running ubuntu 11.04 (soon to be on 11.10 on acer aspire 7741 Z 17"

Thanks for the post

---

### Post by Denver Dave on 2011-11-18
I have an issue, referred to earlier, with ubuntu 11.04 and 11.10 on my Acer Aspire laptop touchpad where the right edge scroll does not work.  However, there may be hope.

Today I tried out Knoppix 6.7 and AV Linux 5.0 to checkout something else that was later resolved with ubuntu and discovered that the right edge scroll worked fine with both of those installations.

So I'm thinking there may be a driver or something that just needs to be added to ubuntu to make the right edge scroll work.   Seems like a minor issue, but really does help having the scroll.

For others with touchpads - does your right edge scroll work?

Dave

---

