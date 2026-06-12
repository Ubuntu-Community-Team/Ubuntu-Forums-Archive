---
title: "BASH: count the number of monitors connected"
date: 2010-12-11
forum: Programming Talk
---

### Post by ethernaly on 2010-12-11
Hello everybody, is there a way to count the number of monitors connected ?

I've a mediacenter and I use two script (on startup) to start 2 software.

The first on DISPLAY 0.0, and the second one on 0.1 .
But sometimes the second monitor is not wired, so the second script open the second software in the first monitor (overlaying the second to the first).

So I need to do something like this:

if (monitors == 2) than {
DISPLAY =0.0 firstapp
DISPLAY =0.1 second app
}
else if (monitors == 1) than {
DISPLAY =0.0 firstapp
}
else {
echo "no monitors connected"}


Someone know how to verify the real number of monitors connected (not of the virtual monitors)


Thanks in advance!

Have a nice day!

---

### Post by ssam on 2010-12-11
the output of xrandr would probably give you enough info.

---

### Post by ethernaly on 2010-12-12
thanks,

I tried with:
xrandr -q| grep "connected"

but the output is :
Can't open display

maybe because I'm trough SSH connection.. 

any suggestions? :]

Thanks in advance!

---

### Post by worksofcraft on 2010-12-12
I don't know how to do it in bash script, but in C and some other languages too you can call a function in the X11 library:
```

int XScreenCount(x11_display *pDisplay)

```
pDisplay specifies the connection to the X server (each computer on the network is considered a "display" in X11).

It returns  the number of available screens... I suppose it wouldn't be too hard to output that so it can be used by your script?!

What I thought was funny is your script echoing that there are no screens... I just wondered how the user is going to read your error message :D

p.s. Meh... here is the code if you can't do it any other way
[php]
// g++ -o x11screens x11screens.cpp -lX11
#include <cstdio>
#include <X11/Xlib.h>
int main(int argc, char *argv[]) {
	Display *pDpy = XOpenDisplay(NULL); // default
	if (!pDpy) return !!fprintf(stderr,"failed to open X11 display\n");
	unsigned iScreenCount = ScreenCount(pDpy);
	XCloseDisplay(pDpy); // disconnect this app from X server
	return !printf("screens = %u\n", iScreenCount);
}
[/php]
outputs:
```

$> ./x11screens
screens = 1

```
Mind you I have no idea it it works with more than one and can't be bothered to test it with zero ;)

---

### Post by worksofcraft on 2010-12-13
p.s. I never heard of xrandr but the following command works just fine on my computer:

```

xrandr -q -d localhost:0.0

```

---

### Post by potat on 2010-12-13
Setting the DISPLAY variable to run xrandr worked for me.

```

DISPLAY=:0 xrandr -q | grep ' connected' | wc -l

```

should give you the number of monitors connected. I'm not sure if you need to set DISPLAY=0.0 (I've only seen the :# format before).

EDIT:
Alternatively, the aforementioned -d option will do the trick.
```

xrandr -d :0 -q | grep ' connected' | wc -l

```

---

### Post by ethernaly on 2010-12-16
Hello,

I tried with:
```
#!/bin/bash
NR_OF_MONITORS=$(/usr/bin/xrandr -q | /bin/grep " connected [0-9]\+x[0-9]\+" | /usr/bin/wc -l )
if [ $NR_OF_MONITORS = "2" ]; then
sleep 10
DISPLAY=:0.0 sudo sh ./run.sh > /dev/null 2>&1
else [ $NR_OF_MONITORS = "1" ];
echo $NR_OF_MONITORS
fi
```

but the problem is this line:
```
NR_OF_MONITORS=$(/usr/bin/xrandr -q | /bin/grep " connected [0-9]\+x[0-9]\+" | /usr/bin/wc -l )
```
the result, even if I connected 2 monitors, is always "1"


In your opinion if I'll try with:
```
NR_OF_MONITORS=$(xrandr -d :0 -q | grep ' connected' | wc -l)
```

can be the trick?


alternatively, is there a way to check if the HDMI output is "connected" or not?
Because my system works with DVI (first monitor) and hdmi (second monitor), but hdmi isn't always connect.

EDIT:
My xorg.conf:
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[2]-0" 0 0
	Screen         "amdcccle-Screen[2]-1" 1280 0
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x720"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x720"
	Option	    "TargetRefresh" "50"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-1"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:2:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-0"
	Device     "amdcccle-Device[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-1"
	Device     "amdcccle-Device[2]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Actualy only the DVI monitor is connected, so this:
```
xrandr -d :0 -q
```
answer with:
```
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1776x1000+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080      60.0 +   50.0     30.0     25.0     24.0  
   1776x1000      60.0*+   50.0     30.0     25.0  
   1600x1200      60.0  
   1680x1050      60.0     50.0  
   1400x1050      60.0     50.0  
   1280x1024      75.0     60.0     50.0  
   1440x900       59.9     50.0  
   1280x960       60.0     50.0  
   1280x800       60.0     50.0  
   1152x864       75.0     60.0     50.0  
   1280x768       59.9     50.0  
   1280x720       60.0     50.0  
   1024x768       75.0     70.1     60.0     50.0  
   1152x648       60.0     50.0  
   800x600        72.2     75.0     60.3     50.0  
   720x576        50.0  
   720x480        59.9     50.0  
   640x480        75.0     72.8     60.0     50.0  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)
```

---

### Post by ethernaly on 2010-12-18
after a lots of tests I tried to put in startup "sessions" (graphic mode) this script:

```
#!/bin/bash
sleep 5
cd /home/mediacenter/script
DISPLAY=:0.1 sudo /usr/bin/gnome-terminal > monitor.txt  2>&1
CCC=$(cat /home/mediacenter/script/monitor.txt | grep " Impossibile aprire il display" | wc -l)
if [ $CCC = "1" ];then
sleep 3
touch TEST
cd /opt/client1/python/
DISPLAY=:0.0 sudo sh ./run.sh > /dev/null 2>&1
else
sleep 4 && touch interni && cd /opt/client1/python/ && DISPLAY=:0.1 sudo sh ./run.sh > /dev/null 2>&1;
sleep 10 && touch esterno && cd /opt/client2/python/ && DISPLAY=:0.0 sudo sh ./run.sh > /dev/null 2>&1;
fi
```

but seems to not work.

EDIT:
FINALLY I found a solution.
```
#!/bin/bash
sleep 5
cd /home/mediacenter/script
DISPLAY=:0.1 sudo /usr/bin/gnome-terminal > monitor.txt  2>&1
CCC=$(cat /home/mediacenter/script/monitor.txt | grep " Impossibile aprire il display" | wc -l)
if [ $CCC = "1" ]
then
touch TEST
cd /opt/client1/python/
sudo cp configSOLO.cfg config.cfg
DISPLAY=:0.0 sudo sh ./run.sh > /dev/null 2>&1
elif [ $CCC = "0" ]
then
touch DOPPIO
cd /opt/client1/python/
sudo cp configDOPPIO.cfg config.cfg
DISPLAY=:0.1 sudo sh ./run.sh > /dev/null 2>&1
else
touch nomonitors
fi
```

If two monitors are connected, file called DOPPIO will be create. But maybe there's a syntax error to launch the software because software doesn't start.

EDIT2:
```
#!/bin/bash
sleep 5
cd /home/mediacenter/script
DISPLAY=:0.1 sudo /usr/bin/gnome-terminal > monitor.txt  2>&1
CCC=$(cat /home/mediacenter/script/monitor.txt | grep " Impossibile aprire il display" | wc -l)
if [ $CCC = "1" ]
then
touch TEST && sudo rm DOPPIO
cd /opt/client1/python/
sudo cp configSOLO.cfg config.cfg
DISPLAY=:0.0 sudo sh ./run.sh > /dev/null 2>&1
elif [ $CCC = "0" ]
then
touch DOPPIO && sudo rm TEST
sudo killall /usr/bin/gnome-terminal
cd /opt/client1/python/
sudo cp siteDOPPIO.cfg site.cfg
sudo sh /home/mediacenter/script/interno.sh &
sudo sh /home/mediacenter/script/esterno.sh &
else
touch nomonitors
fi

```
probably this is the right solution. (first case works fine, and tomorrow I'll try the second case)

---

