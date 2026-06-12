---
title: "No xev output on 2 keys."
date: 2012-08-08
forum: New to Ubuntu
---

### Post by MibunoOokami on 2012-08-08
Hi all, this is actually a follow up from this thread [http://ubuntuforums.org/showthread.php?t=2038084](http://ubuntuforums.org/showthread.php?t=2038084) so it may need to be merged and that one unsolved.

My netbook is HP 110 mini which I installed Ubuntu 12.04 on and the brightness keys (F2 & F3) have never worked. I started this thread [http://ubuntuforums.org/showthread.php?t=1974334](http://ubuntuforums.org/showthread.php?t=1974334) in May which didn't get a reply but shows what I had tried. Yesterday after I received help how to remap a key, I suddenly got the idea to see what happens if I press the brightness keys in xev. Nothing happened, it was like I didn't press a button at all. I also tried sudo showkey -k same thing. I'm assuming this is the main reason I can't adjust my brightness. Xmodmap -pke shows that brightness controls do exist, so I don't understand why there is no output in xev.

> keycode 237 = XF86KbdBrightnessDown NoSymbol XF86KbdBrightnessDown NoSymbol XF86KbdBrightnessDown
keycode 238 = XF86KbdBrightnessUp NoSymbol XF86KbdBrightnessUp NoSymbol XF86KbdBrightnessUp


Can anybody please offer some ideas? Sorry for the long post, I figure the more info I can give, the better it will be. Also, even though I use a different keyboard layout, that isn't the cause of this problem because I've tried it with the standard US layout. Thanks.

---

### Post by GreatDanton on 2012-08-08
Maybe try this: [http://askubuntu.com/questions/34979/how-to-change-the-shortcut-to-adjust-brightness](http://askubuntu.com/questions/34979/how-to-change-the-shortcut-to-adjust-brightness)

It's not exactly the solution but this will help us to continue.

---

### Post by Toz on 2012-08-08
Also, I was just reading your previous thread and noticed what might be a typo. Can you try the following grub kernel parameter string:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```

Run **sudo update-grub** and reboot to test the brightness keys and xev/showkey again.

---

### Post by Mark Phelps on 2012-08-08
While the link be GreatDanton may help, unfortunately, if the keys produce no output the kernel can see (as displayed in xev), there's no "event" that you can bind to a keypress.  

Had to abandon the use of a Tablet PC because the next Ubuntu version included a kernel version that NO LONGER saw the keypresses I needed to be able to rotate the screen.

---

### Post by MibunoOokami on 2012-08-08
> **Toz said:**
> Also, I was just reading your previous thread and noticed what might be a typo. Can you try the following grub kernel parameter string:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```Run **sudo update-grub** and reboot to test the brightness keys and xev/showkey again.

Thanks for your reply. I've done as you suggested, no luck though. Still nothing with xev or showkey either.

> **Mark Phelps said:**
> While the link be GreatDanton may help, unfortunately, if the keys produce no output the kernel can see (as displayed in xev), there's no "event" that you can bind to a keypress.  

Had to abandon the use of a Tablet PC because the next Ubuntu version included a kernel version that NO LONGER saw the keypresses I needed to be able to rotate the screen.

Since there's no output, is there any point trying the suggestions in that thread GreatDanton linked? Is this a clash between the kernel and the hardware in my specific netbook?

---

### Post by Toz on 2012-08-08
Hmmm, just found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1001767]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1001767").

---

### Post by MibunoOokami on 2012-08-08
> **Toz said:**
> Hmmm, just found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1001767](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1001767).

Thanks. That looks quite technical but I think I got the gist. This is a bug which has been reported and is currently being dealt with but not yet fixed. Is that right?

---

### Post by Toz on 2012-08-08
Yes. It would be a good idea to add your name to the list. However, according to that bug report, it looks like the setpci command works to affect brightness. You could script something and assign it to a different keystroke combination to at least give you some brightness control.

To test this, try running the following command:
```
sudo setpci -s 00:02.0 F4.B=xx
```
...where xx is a hexidecimal value between 0 (no brightness) and 255 (full brightness) [try 88 as a mid-point value] and 00:02.0 is the bus address of your video controller that you can get from:
```
lspci | grep VGA
```

If setpci does work for you, and you want to use it as a workaround to control brightness, we can adapt this script to work for your machine: [http://ubuntuforums.org/showpost.php?p=11024962&postcount=7]("http://ubuntuforums.org/showpost.php?p=11024962&postcount=7").

---

### Post by MibunoOokami on 2012-08-09
> **Toz said:**
> Yes. It would be a good idea to add your name to the list. However, according to that bug report, it looks like the setpci command works to affect brightness. You could script something and assign it to a different keystroke combination to at least give you some brightness control.

To test this, try running the following command:
```
sudo setpci -s 00:02.0 F4.B=xx
```...where xx is a hexidecimal value between 0 (no brightness) and 255 (full brightness) [try 88 as a mid-point value] and 00:02.0 is the bus address of your video controller that you can get from:
```
lspci | grep VGA
```If setpci does work for you, and you want to use it as a workaround to control brightness, we can adapt this script to work for your machine: [http://ubuntuforums.org/showpost.php?p=11024962&postcount=7](http://ubuntuforums.org/showpost.php?p=11024962&postcount=7).

Toz, thanks for your help, the setpci command has worked and what an improvement. It's a lot better without that strong bright screen now. I dropped it to 45 because 88 seemed still a bit bright, I tried different values and learned that the max value is 99. Can I copy and paste that script replacing dell with hp or is there a bit more too it?
I forgot to mention in my old brightness thread and in this one, the option to adjust the brightness manually in the brightness and lock setting is a bit faulty. When you open the settings window there's an adjustable bar that disappears in less than a second. That probably doesn't matter now but thought I should mention it whilst I remember, just in case there is some relevance.

Thanks also to GreatDanton and Mark Phelps for your input too.

---

### Post by Toz on 2012-08-09
> **MibunoOokami said:**
> Toz, thanks for your help, the setpci command has worked and what an improvement. It's a lot better without that strong bright screen now. I dropped it to 45 because 88 seemed still a bit bright, I tried different values and learned that the max value is 99.
Interesting.
> Can I copy and paste that script replacing dell with hp or is there a bit more too it?
You'll need to identify the proper backlight interface. The code has:
```
b=`cat /sys/class/backlight/dell_backlight/brightness`;
```
...check your /sys/class/backlight folder to see what the name of your interface is. You'll also need to adjust the hex values in the case statement to work for you. In that script it has 16 steps. You can adjust that to fewer brightness steps (increments/decrements) by changing the number of case statements.

And once you get the script working the way you want to, you can assign it to a key combination so that you have quick access to it.

If you would like some further help with the script, post back the name of your backlight interface and let me know how many steps you would like.

---

### Post by Mark Phelps on 2012-08-09
> **MibunoOokami said:**
> Since there's no output, is there any point trying the suggestions in that thread GreatDanton linked? Is this a clash between the kernel and the hardware in my specific netbook?

The problem is specific to those individual keys.  As long as OTHER keys generate codes that xev sees, you can always choose to bind an event to some other key.

I had to abandon my efforts because on my Tablet PC, there were only 4 keys on the bezel -- and xev wasn't showing key info for ANY of them.

---

### Post by MibunoOokami on 2012-08-09
> **Toz said:**
> check your /sys/class/backlight folder to see what the name of your interface is. 

Umm....... The /sys/class/backlight folder is empty... I pressed ctrl+h thinking the files may be hidden but there are none.

---

### Post by Toz on 2012-08-09
> **MibunoOokami said:**
> Umm....... The /sys/class/backlight folder is empty... I pressed ctrl+h thinking the files may be hidden but there are none.

No worries. I'll adjust the script so that we use setpci to get the value of the register as well. What is the bus address of your video card and how many brightness steps would you like?

---

### Post by MibunoOokami on 2012-08-09
> **Toz said:**
> No worries. I'll adjust the script so that we use setpci to get the value of the register as well. What is the bus address of your video card and how many brightness steps would you like?

Hi, the bus address was also 00:02.0. I have no idea how many steps I need, I don't think I'd need the brightness lower than the 45 I tried yesterday or at it's max brightness, so maybe just a few between those values? What would you recommend? Thanks

---

### Post by Toz on 2012-08-09
Lets give this script a try. 

1. Edit your /etc/rc.local file:
```
gksudo gedit /etc/rc.local
```
...and add the following _above_ the line that reads *exit 0*:
```
setpci -s 00:02.0 F4.B=45
echo 0 > /tmp/BR
chmod 666 /tmp/BR

```

2. setpci requires root privileges to run if being run as a regular user. To enable your system to allow running this script (which in turn runs setpci) without a password:
```
sudo visudo
```
...and add to the end of the file:
```
<USERNAME> ALL = NOPASSWD: /usr/bin/setpci
```
...where <USERNAME> is your username on the system.

3. Create the script in /usr/local/bin:
```
gksudo gedit /usr/local/bin/br
```
...with the following content:
```

#!/bin/bash

CURRENT=`cat /tmp/BR`
NEW=$CURRENT
case $1 in 
	up)
		if [ $(($CURRENT+1)) -le 4 ]; then
            		NEW=$(($CURRENT+1))
        	fi
    	;;
    	down)
        	if [ $(($CURRENT-1)) -ge 0 ]; then
            		NEW=$(($CURRENT-1))
        	fi
    	;;
    	*)
    	;;
esac

echo $NEW > /tmp/BR
VAL=45

case $NEW in
	0) VAL=45 ;;
	1) VAL=60 ;;
	2) VAL=75 ;;
	3) VAL=90 ;;
	4) VAL=99 ;;
esac

#echo "$CURRENT / $NEW / $VAL"
sudo /usr/bin/setpci -s 00:02.0 F4.B=$VAL

exit 0

```
...and make the script executable:
```
sudo chmod +x /usr/local/bin/br
```

4. Reboot

5. Test by running:
```
br up
```
...and
```
br down
```

6. Map **sudo br up** and **sudo br down** to key combinations.

---

### Post by MibunoOokami on 2012-08-09
Quick question, do I need to put a # in front of the lines I'm adding to each of these? Thanks.
```
sudo gedit /etc/rc.local
```
```
<USERNAME> ALL=(ALL) NOPASSWD: /usr/local/bin/br
```

---

### Post by GreatDanton on 2012-08-09
There is a typo in the first command. For graphical apps (like Gedit) use Gksudo so in this case:
```
gksudo gedit /etc/rc.local
```
Regards.

---

### Post by MibunoOokami on 2012-08-09
> **GreatDanton said:**
> There is a typo in the first command. For graphical apps (like Gedit) use Gksudo so in this case:
```
gksudo gedit /etc/rc.local
```Regards.

Is there a difference? I've edited that one (or something) without the gk in front of it.

---

### Post by GreatDanton on 2012-08-09
For difference between sudo and gksudo take a look here: [http://crunchbanglinux.org/forums/topic/8468/please-clarify-sudo-vs-gksugksudo/](http://crunchbanglinux.org/forums/topic/8468/please-clarify-sudo-vs-gksugksudo/)

---

### Post by MibunoOokami on 2012-08-09
> **GreatDanton said:**
> For difference between sudo and gksudo take a look here: [http://crunchbanglinux.org/forums/topic/8468/please-clarify-sudo-vs-gksugksudo/](http://crunchbanglinux.org/forums/topic/8468/please-clarify-sudo-vs-gksugksudo/)

Sorry, I read that thread but was unable to understand what the difference is. I'm assuming the difference is negligible?
Can you tell me if I need to put a # in front of the lines I've added? Thanks.

---

### Post by Toz on 2012-08-09
> **GreatDanton said:**
> There is a typo in the first command. For graphical apps (like Gedit) use Gksudo so in this case:
```
gksudo gedit /etc/rc.local
```
Regards.

Thanks for the catch. I'll update the original post.

---

### Post by Toz on 2012-08-09
> **MibunoOokami said:**
> Quick question, do I need to put a # in front of the lines I'm adding to each of these? Thanks.
```
sudo gedit /etc/rc.local
```
```
<USERNAME> ALL=(ALL) NOPASSWD: /usr/local/bin/br
```

No. Not for those. The pound sign indicates a comment. There are a few in the actual script file. Just copy/paste the commands and file contents.

Make sure you replace <username> with the actual username on the computer.

---

### Post by MibunoOokami on 2012-08-09
> **Toz said:**
> No. Not for those. The pound sign indicates a comment. There are a few in the actual script file. Just copy/paste the commands and file contents.

OK, I'll just reboot now and see what happens. Thanks.

---

### Post by MibunoOokami on 2012-08-09
> **Toz said:**
> 
Make sure you replace <username> with the actual username on the computer.

I added my username but left the <> around it. I'm going to remove them now because I just tried sudo br up and sudo br down but nothing happened, so I guess that's the reason. Thanks.

---

### Post by MibunoOokami on 2012-08-09
> **MibunoOokami said:**
> I added my username but left the <> around it. I'm going to remove them now because I just tried sudo br up and sudo br down but nothing happened, so I guess that's the reason. Thanks.

I must have forgotten to save it after adding that line because it wasn't there when I went to edit it. That said though, I've edited it twice now, once with the <> and once without but the brightness doesn't change.

---

### Post by GreatDanton on 2012-08-09
Some links for understanding the difference between gksudo and sudo. It's a lot of text to read but it's important to know the difference IMO.

1. [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

2. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Regards.

---

### Post by Toz on 2012-08-09
> **MibunoOokami said:**
> I must have forgotten to save it after adding that line because it wasn't there when I went to edit it. That said though, I've edited it twice now, once with the <> and once without but the brightness doesn't change.

Can you post back the contents of /etc/rc.local and /usr/local/bin/br? And can you paste back the exact command you added via "sudo visudo"?

If you enter these commands directly into a terminal, does the brightness change?
```
sudo setpci -s 00:02.0 F4.B=45
sudo setpci -s 00:02.0 F4.B=60
sudo setpci -s 00:02.0 F4.B=75
sudo setpci -s 00:02.0 F4.B=90
sudo setpci -s 00:02.0 F4.B=100
```
...and are you asked for a password?

---

### Post by MibunoOokami on 2012-08-09
> **Toz said:**
> Can you post back the contents of /etc/rc.local and /usr/local/bin/br? And can you paste back the exact command you added via "sudo visudo"?

If you enter these commands directly into a terminal, does the brightness change?
```
sudo setpci -s 00:02.0 F4.B=45
sudo setpci -s 00:02.0 F4.B=60
sudo setpci -s 00:02.0 F4.B=75
sudo setpci -s 00:02.0 F4.B=90
sudo setpci -s 00:02.0 F4.B=100
```...and are you asked for a password?

Sure thing.

/etc/rc.local
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
setpci -s 00:02.0 F4.B=45
echo 0 > /tmp/BR
exit 0
```/usr/local/bin/br
```
#!/bin/bash

CURRENT=`cat /tmp/BR`
NEW=$CURRENT
case $1 in 
    up)
        if [ $(($CURRENT+1)) -le 4 ]; then
                    NEW=$(($CURRENT+1))
            fi
        ;;
        down)
            if [ $(($CURRENT-1)) -ge 0 ]; then
                    NEW=$(($CURRENT-1))
            fi
        ;;
        *)
        ;;
esac

echo $NEW > /tmp/BR
VAL=45

case $NEW in
    0) VAL=45 ;;
    1) VAL=60 ;;
    2) VAL=75 ;;
    3) VAL=90 ;;
    4) VAL=100 ;;
esac
```sudo visudo
```
MNO ALL=(ALL) NOPASSWD: /usr/local/bin/br

```All of the brightness commands work except the last one because the range only goes to 99. Password asked for and entered each time.
```
 setpci: Value "100" is out of range.
Try `setpci --help' for more information.
``` Thanks.

---

### Post by Toz on 2012-08-09
Sorry, found some typos/errors. 

1. The last part of /etc/rc.local should look like this:
```
setpci -s 00:02.0 F4.B=45
echo 0 > /tmp/BR
chmod 666 /tmp/BR
exit 0

```

2. The sudo command should be:
```
MNO ALL = NOPASSWD: /usr/bin/setpci
```

3. You seem to be missing the last part of /usr/local/bin/br (don't know if it's an omission). There were a couple of changes there, so use this version of the script:
```
#!/bin/bash

CURRENT=`cat /tmp/BR`
NEW=$CURRENT
case $1 in 
	up)
		if [ $(($CURRENT+1)) -le 4 ]; then
            		NEW=$(($CURRENT+1))
        	fi
    	;;
    	down)
        	if [ $(($CURRENT-1)) -ge 0 ]; then
            		NEW=$(($CURRENT-1))
        	fi
    	;;
    	*)
    	;;
esac

echo $NEW > /tmp/BR
VAL=45

case $NEW in
	0) VAL=45 ;;
	1) VAL=60 ;;
	2) VAL=75 ;;
	3) VAL=90 ;;
	4) VAL=99 ;;
esac

#echo "$CURRENT / $NEW / $VAL"
sudo /usr/bin/setpci -s 00:02.0 F4.B=$VAL

exit 0

```

I'll update my original post.

---

### Post by MibunoOokami on 2012-08-10
I've made the changes per your last post Toz and it's working as it should. I'm a little confused though, did I make some errors when copying and pasting some or all of the codes the first time round?
I'm going to try remap those commands to my menu key which I never use. If I'm successful I'll report back and then mark this thread as solved. Thanks everyone for all the help.

---

### Post by MibunoOokami on 2012-08-10
> **MibunoOokami said:**
> I'm going to try remap those commands to my menu key which I never use. If I'm successful I'll report back and then mark this thread as solved. Thanks everyone for all the help.

That didn't quite go as planned. It's not as simple as I had thought, but I think I understand why it didn't work, I need a good keysym name. I'll check the list GreatDanton linked in my remapping thread.

```
xmodmap -e "keycode 135 = sudo br down sudo br up"
xmodmap:  commandline:1:  bad keysym name 'sudo' in keysym list
xmodmap:  commandline:1:  bad keysym name 'br' in keysym list
xmodmap:  commandline:1:  bad keysym name 'down' in keysym list
xmodmap:  commandline:1:  bad keysym name 'sudo' in keysym list
xmodmap:  commandline:1:  bad keysym name 'br' in keysym list
xmodmap:  commandline:1:  bad keysym name 'up' in keysym list
xmodmap:  6 errors encountered, aborting.

```

---

### Post by Toz on 2012-08-10
First off, there is no need to run br as sudo now. Just run:
```
br up
```
...and
```
br down
```

Secondly, when mapping, the easier way (instead of xmodmap) is to use the Keyboard app that comes with the DE. I don't use Unity, but I believe its located in Settings -> Keyboard -> Shortcuts tab.

---

### Post by MibunoOokami on 2012-08-10
> **Toz said:**
> First off, there is no need to run br as sudo now. Just run:
```
br up
```...and
```
br down
```Secondly, when mapping, the easier way (instead of xmodmap) is to use the Keyboard app that comes with the DE. I don't use Unity, but I believe its located in Settings -> Keyboard -> Shortcuts tab.

I had a look at that app when trying to remap another key in my previous thread, but I haven't got a clue how to use it  or what any of the jargon means. It's like another language.

---

### Post by Toz on 2012-08-10
Try using xbindkeys:

1. Create the config file:
```
xbindkeys --defaults > ~/.xbindkeysrc
```

2. Use "xbindkeys -k" to get the the snippet. For example, Ctrl+Alt+= returns:
```
"(Scheme function)"
    m:0xc + c:21
    Control+Alt + equal

```
...and Ctrl+Alt+- returns:
```
"(Scheme function)"
    m:0xc + c:20
    Control+Alt + minus

```

Then add those snippets to ~/.xbindkeysrc like this:
```

#increase brightness
"br up"
    m:0xc + c:21
    Control+Alt + equal

#decrease brightness
"br down"
    m:0xc + c:20
    Control+Alt + minus
```

Make sure xbindkeys is running (add it to your startup apps).

Source: [https://wiki.archlinux.org/index.php/Xbindkeys]("https://wiki.archlinux.org/index.php/Xbindkeys")

---

### Post by MibunoOokami on 2012-08-10
Thanks. This hasn't quite worked, brightness won't change but menu key doesn't work so must be halfway there. Here is how my .xbindkeysrc file looks, I can't spot any difference other than the second line of the snippet which I changed for my machine. Unless it's because the menu key doesn't usually have a dual usage and I've effectively canceled both commands having them assigned to the same key?

```
#increase brightness
"br up"
    m:0x1 + c:135
    Shift + Menu

#decrease brightness
"br down"
    m:0x0 + c:135
    Menu
```

---

### Post by Toz on 2012-08-10
Which key is the menu key? 
Is xbindkeys running?

My ~/.xbindkeysrc file:
```

"br up"
    m:0x40 + c:21
    Mod4 + equal

"br down"
    m:0x40 + c:20
    Mod4 + minus

```
...Mod4 is my Windows key.

---

### Post by MibunoOokami on 2012-08-10
> **Toz said:**
> Which key is the menu key? 
Is xbindkeys running?

Menu is a key between right alt and right shift. xbindkeys -k and xev call that key a menu key. I think it represents a right click of a mouse. Thanks.

---

### Post by Toz on 2012-08-10
Oh. When I set it up to use the menu key, it works:
```

"br up"
    m:0x0 + c:135
    Menu


"br down"
    m:0x1 + c:135
    Shift + Menu
```

Is xbindkeys running?
```
ps -ef | grep xbindkeys
```

---

### Post by MibunoOokami on 2012-08-10
> **Toz said:**
> Is xbindkeys running?
```
ps -ef | grep xbindkeys
```

I'm not sure. 
```
ps -ef | grep xbindkeys
mno       1617     1  0 08:52 ?        00:00:00 /usr/bin/xbindkeys -f /home/mno/.xbindkeysrc
mno       6433  2605  0 13:11 pts/1    00:00:00 grep --color=auto xbindkeys

```

---

### Post by Toz on 2012-08-10
Hmmmm. Lets have another look at your files:

- /etc/rc.local
- /usr/local/bin/br
- /home/mno/.xbindkeysrc
- the last line from 'sudo visudo'
- the results of:
```
ls -l /tmp/BR
cat /tmp/BR
```

And just to confirm: does it work when you issue the command "br up" and "br down" manually?

---

### Post by MibunoOokami on 2012-08-10
> **Toz said:**
> Hmmmm. Lets have another look at your files:

- /etc/rc.local
- /usr/local/bin/br
- /home/mno/.xbindkeysrc
- the last line from 'sudo visudo'
- the results of:
```
ls -l /tmp/BR
cat /tmp/BR
```And just to confirm: does it work when you issue the command "br up" and "br down" manually?

Issuing the commands manually works, but I'm still asked for a password which I didn't think I need anymore, so perhaps that's the problem. Thanks.
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
setpci -s 00:02.0 F4.B=45
echo 0 > /tmp/BR
chmod 666 /tmp/BR
exit 0
``````
#!/bin/bash

CURRENT=`cat /tmp/BR`
NEW=$CURRENT
case $1 in 
    up)
        if [ $(($CURRENT+1)) -le 4 ]; then
                    NEW=$(($CURRENT+1))
            fi
        ;;
        down)
            if [ $(($CURRENT-1)) -ge 0 ]; then
                    NEW=$(($CURRENT-1))
            fi
        ;;
        *)
        ;;
esac

echo $NEW > /tmp/BR
VAL=45

case $NEW in
    0) VAL=45 ;;
    1) VAL=60 ;;
    2) VAL=75 ;;
    3) VAL=90 ;;
    4) VAL=99 ;;
esac

#echo "$CURRENT / $NEW / $VAL"
sudo /usr/bin/setpci -s 00:02.0 F4.B=$VAL

exit 0
``````
#increase brightness
"br up"
    m:0x1 + c:135
    Shift + Menu

#decrease brightness
"br down"
    m:0x0 + c:135
    Menu
``````
MNO ALL = NOPASSWD: /usr/bin/setpci

``````
ls -l /tmp/BR
-rw-rw-rw- 1 root root 2 Aug 11 13:29 /tmp/BR

``````
 cat /tmp/BR
3

```

---

### Post by Toz on 2012-08-10
The files look okay, but you shouldn't be prompted for a password. Is
```
MNO ALL = NOPASSWD: /usr/bin/setpci
```
...the last line in the file?

What does the following return?
```
whoami
```

---

### Post by MibunoOokami on 2012-08-10
> **Toz said:**
> The files look okay, but you shouldn't be prompted for a password. Is
```
MNO ALL = NOPASSWD: /usr/bin/setpci
```...the last line in the file?

What does the following return?
```
whoami
```

Hi, it's definitely the last line. Whoami returns ```
mno
``` Thanks.

---

### Post by Toz on 2012-08-11
> **MibunoOokami said:**
> Hi, it's definitely the last line. Whoami returns ```
mno
``` Thanks.

Change the line to read:
```
mno ALL = NOPASSWD: /usr/bin/setpci
```
...case is important.

---

### Post by MibunoOokami on 2012-08-11
> **Toz said:**
> Change the line to read:
```
mno ALL = NOPASSWD: /usr/bin/setpci
```...case is important.

Thanks, I should have picked up on that earlier coz terminal is always mno. Now that I've changed it to lower case, the menu key now adjusts my brightness.  I'm sure you've worked out by now, I'm not the smartest of people when it comes to using computers. Thanks so much for your patience and help.

---

### Post by Toz on 2012-08-11
No worries. I'm glad it works. Keep an eye on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1001767]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1001767") and check your brightness keys with every kernel upgrade - hopefully the issue will be fixed soon and you won't need this workaround anymore.

---

### Post by walkingdistance on 2012-08-16
Toz,

Your script workaround worked for me with Ubuntu 12.04, on an Acer Aspire One D270 netbook (20120816, with latest Update Manager kernel updates). I'm still a little vexed that the Fn+ brightness keys don't work as they should, but I'm glad to have discovered your help.

Thanks for taking the time and sharing.

---

### Post by Toz on 2012-08-16
> **walkingdistance said:**
> Toz,

Your script workaround worked for me with Ubuntu 12.04, on an Acer Aspire One D270 netbook (20120816, with latest Update Manager kernel updates). I'm still a little vexed that the Fn+ brightness keys don't work as they should, but I'm glad to have discovered your help.

Thanks for taking the time and sharing.

Hi walkingdistance and welcome to the forums.
I'm glad it worked. Hopefully this will be addressed in upcoming kernels and the workaround will no longer be required.

---

### Post by YannBuntu on 2012-08-23
Similar problem (but the workaround doesn't work) [http://ubuntuforums.org/showthread.php?p=12191735#post12191735](http://ubuntuforums.org/showthread.php?p=12191735#post12191735) Thanks for any suggestion

---

