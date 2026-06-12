---
title: "GDM startup script..."
date: 2010-10-20
forum: Programming Talk
---

### Post by Moozillaaa on 2010-10-20
Ubuntu/Wiki page [here ]("https://wiki.ubuntu.com/X/Config/Resolution")says to add codestring into this file - **[COLOR=Navy]/etc/gdm/Init/Default[/COLOR]**. I caught a syntax error in the procedure, so I'm feeling good enough to really trash my 'fix' LOL. [http://ubuntuforums.org/showthread.php?t=1598322](http://ubuntuforums.org/showthread.php?t=1598322) 

I found the file, and need to figure out what text to add. **I'd like to figure it out with as little help as I can too...**

So, would it happen only to be addition of the xrandr commands into the file, like so:

> 
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --gdm-session --daemon
fi

[COLOR=Red][I]xrandr --newmode "1280x1024" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

xrandr --addmode VGA-0 1280x1024

xrandr --output VGA-0 --mode 1280x1024[/I][/COLOR]  

initctl -q emit login-session-start DISPLAY_MANAGER=gdm

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH

(rest of file deleted for brevity)
Or would it be something similar to a startup script I needed for wireless in Gutsy, that Wieman01 posted in Tutorials and Tips?

> Create startup script:
Quote:
sudo gedit /etc/init.d/wireless-network
Add this line & save file:
Quote:
/etc/init.d/networking restart
Change permission (executable):
Quote:
sudo chmod +x /etc/init.d/wireless-network
Create symbolic link:
Quote:
sudo ln -s /etc/init.d/wireless-network /etc/rcS.d/S40wireless-network
[Note: You may have to choose a boot sequence other than S40.]

Restart...
Last edited by wieman01; April 7th, 2009 at 02:23 PM.. I hope to figure this out with only a little help here...

---

### Post by Moozillaaa on 2010-10-20
The first option is correct, at least in part... So now this is a syntax question.

X starts up with the right login-screen resolution, but the desktop is in reduced resolution. I need to set the modes with the first choice, but how???

man xrandr page says --auto or --preferred is the parameter for this, but I don't know which, or where in the textline.

Each choice below left no mode as first choice (for VGA-0 output):

chuckhtpc@chuckhtpc-desktop:~$[COLOR=Red] xrandr  --output  VGA-0  --auto[/COLOR]
[COLOR=Black]chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 1024, maximum 1360 x 1360
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  [/COLOR]
   1280x1024      59.9* 
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
chuckhtpc@chuckhtpc-desktop:~$[COLOR=Red] xrandr  --output  VGA-0  --mode 1280x1024  --auto[/COLOR] 
chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 1024, maximum 1360 x 1360
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   1280x1024      59.9* 
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
chuckhtpc@chuckhtpc-desktop:~$ [COLOR=Red]xrandr  --output  VGA-0  --preferred[/COLOR]
chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 1024, maximum 1360 x 1360
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   1280x1024      59.9* 
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
chuckhtpc@chuckhtpc-desktop:~$ [COLOR=Red]xrandr  --output  VGA-0  --auto  --mode 1280x1024[/COLOR]
chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 1024, maximum 1360 x 1360
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   1280x1024      59.9* 
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
chuckhtpc@chuckhtpc-desktop:~$ [COLOR=Red]xrandr  --output  VGA-0  --preferred  --mode 1280x1024[/COLOR]
chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 1024, maximum 1360 x 1360
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   1280x1024      59.9* 
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
chuckhtpc@chuckhtpc-desktop:~$ [COLOR=Red]xrandr  --output  VGA-0  --mode 1280x1024  --preferred[/COLOR]
chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 1024, maximum 1360 x 1360
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   1280x1024      59.9* 
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
chuckhtpc@chuckhtpc-desktop:~$

---

### Post by Moozillaaa on 2010-10-21
[COLOR=black]I moved the 3 xrandr command strings in the file - [/COLOR][COLOR=black]/etc/gdm/Init/Default, closer to the beginning[/COLOR][COLOR=Black], and [/COLOR][COLOR=Navy][COLOR=Black]it has made no difference.[/COLOR] 
[/COLOR]> [COLOR=Navy]
[/COLOR]#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

[COLOR=Red][I]xrandr --newmode "1280x1024" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

xrandr --addmode VGA-0 1280x1024

xrandr --output VGA-0 --mode 1280x1024[/I][/COLOR]  

PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --gdm-session --daemon
fi

[COLOR=Red]**FROM HERE**[/COLOR]

initctl -q emit login-session-start DISPLAY_MANAGER=gdm

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH

(rest of file deleted for brevity) 			 		

So this startup script (really it's just an addition to an existing script), is being over-ridden by another script.

Can anybody tell me where to look here?

---

### Post by P4man on 2010-10-21
No idea. I can only say that using an xrandr command to rotate the screen does work when you put in the location you had it originally. I just found that out:
[http://ubuntuforums.org/showthread.php?t=1602481](http://ubuntuforums.org/showthread.php?t=1602481)

Maybe you can try using another name as VGA-0?

---

### Post by Moozillaaa on 2010-10-21
I think VGA-0 is the correct designation to use. I think this because after the desktop has loaded, at the wrong resolution, I can enter into the CLI the following:

> chuckhtpc@chuckhtpc-desktop:~$ xrandr --output VGA-0 --mode 1280x1024
chuckhtpc@chuckhtpc-desktop:~$ and the resolution changes from the lower resolution to the desired 1280 x 1024 resolution.

> chuckhtpc@chuckhtpc-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 1024, maximum 1360 x 1360
**[COLOR=Red]VGA-0[/COLOR]** connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   1280x1024      59.9* 
HDMI-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
chuckhtpc@chuckhtpc-desktop:~$ 
Placement of the 3 xrandr command strings makes no difference, of the 2 positions in the file that I had them -shown above.

In either position, only the login screen came up in the correct resolution. The desktop loads in the wrong resolution, until the command is executed again. 

Something is trumping the command, as it is executed from the /etc/gdm/Init/Default file.

---

### Post by Moozillaaa on 2010-10-21
So I removed the 3 xrandr lines from the file, re-booted, and the desired mode - 1280 x 1024 - disappeared from the list of modes.

The addition to the script file works, but the desktop resolution is getting another signal, which over-writes the desired resolution.

What processes follow execution of /etc/gdm/Init/Default script???

Help?

---

### Post by Moozillaaa on 2010-10-21
I found this in my syslog file, from startup processes:
> 
WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory

Since I've added the 3 xrandr command strings to the /etc/gdm/Init/Default file, am I supposed to compile a custom.conf file?

---

### Post by P4man on 2010-10-22
Do you have that custom.conf? I do but it was generated by the login screen app (system > admin > loginscreen), I have it set to a timed login, I think the file is optional.

HAve you tried rotating your login screen like I did ? If that works, then your resolution settings get  verridden somewhere (I assume you have not set a rotation by default). If it doesnt work, then those commands dont get executed. Perhaps its running the failsafeXServer scripts in gdm?

---

### Post by Moozillaaa on 2010-10-22
No, I don't see a custom configuration file anywhere, that's been created by default. If I have to do it, I haven't gotten that far yet.

What parameter would I add to the xrandr command string(s) in my gdm file, to set it to rotate?
> 
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

[B][COLOR=Red][I]xrandr --newmode "1280x1024" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

xrandr --addmode VGA-0 1280x1024

xrandr --output VGA-0 --mode 1280x1024[/I][/COLOR][/B]  

PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --gdm-session --daemon
fi

initctl -q emit login-session-start DISPLAY_MANAGER=gdm

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH

(rest of file deleted for brevity)                      
Yes, I think there IS something over-riding the command, because the login screen APPEARS (I cannot be 100% certain) to be at the desired resolution. That would be determined later tho'...

I added a shell script in 2 places:
```

/etc/init.d/display-init
```and even one on DESKTOP, thinking it might run AFTER THE DESKTOP loads,
```

/home/chuckhtpc/Desktop/display-init  
```but although they both execute **manually** from the CLI AFTER desktop loads, neither executes automatically, as the system loads. Each is symlinked at rc5.d which is the second-highest level. **CAN I CREATE A LEVEL 7, THAT WOULD EXECUTE LAST IN SYSTEM BOOT PROCESS???**

---

### Post by P4man on 2010-10-22
> **Moozillaaa said:**
> 
What parameter would I add to the xrandr command string(s) in my gdm file, to set it to rotate?

xrandr -o 1

[http://ubuntuforums.org/showpost.php?p=10007063&postcount=3](http://ubuntuforums.org/showpost.php?p=10007063&postcount=3)

To rotate it back after logging in, press alt+f2 and execute

```
xrandr -o 0
```

---

### Post by Moozillaaa on 2010-10-22
Suspicion confirmed!

I added the rotate parameter (removing the resolution-per-output '[COLOR=Red]*--output VGA-0 --mode 1280x1024*[/COLOR] '):

> #!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

[COLOR=Red][I]xrandr --newmode "1280x1024" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

xrandr --addmode VGA-0 1280x1024[/I][/COLOR][B][COLOR=Red][I]

[SIZE=2]xrandr -o 1[/SIZE][/I][/COLOR][/B]

PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --gdm-session --daemon
fi

initctl -q emit login-session-start DISPLAY_MANAGER=gdm

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH

(rest of file deleted for brevity)                      and the login screen was rotated. Then the desktop loaded...[SIZE=2]**NOT**[/SIZE] rotated.

I have 2 options:

1) Find out what function is over-writing the command, between login screen display and desktop load...

OR

2) Write in a script which executes AFTER the last function - desktop loading.

I believe option 2 will be easier. The question is, can I create a 'new' highest runlevel, beyond rc6.d??? I tried rc5.d, and it did not work. I tried rc6.d (I thought), but no-go. I tried level 7, but that does not exist. There is a level rcS.d, but I don't know what that level is.

IDEAS???

---

### Post by Moozillaaa on 2010-10-22
Of the 121 people who've viewed this thread, I bet 100+ know the answer to my question.

Thanks tho'...

:|

---

