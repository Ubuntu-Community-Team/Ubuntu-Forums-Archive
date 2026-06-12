---
title: "Xboxdrv and game start up script"
date: 2012-09-20
forum: Programming Talk
---

### Post by Geezanansa on 2012-09-20
Have been trying to get xboxdrv running xbox360 controller in ubuntu 12.04.
The way i get xbox 360 controller running is by 
```
sudo xboxdrv -s --ui-clear --deadzone 9000 --dpad-as-button --trigger-as-button --deadzone-trigger 15% --ui-axismap x1^resp:-32768:-4000:0:4000:32767 --ui-axismap "x2=REL_X:25:25,y2=REL_Y:25:25,x1=KEY_A:KEY_D,y1=KEY_W:KEY_S" --ui-buttonmap "tl=KEY_LEFTSHIFT" --ui-buttonmap "b=KEY_C:KEY_LEFTCTRL:500" --ui-buttonmap "a=KEY_SPACE,x=KEY_1,y=KEY_R" --ui-buttonmap "lb=KEY_Q,rb=KEY_E" --ui-buttonmap "lt=BTN_RIGHT,rt=BTN_LEFT" --ui-buttonmap "dl=KEY_4,dr=KEY_F,du=BTN_MIDDLE,dd=KEY_TAB" --ui-buttonmap "back=KEY_ESC,start=KEY_ENTER"
```The game that xboxdrv is mapped for is run through Steam.  Steam on this system is run through PlayOnLinux which uses wine.
Steam client is latest version.
PloyOnLinux is 4.1.7 version.
Wine is 1.5.13 version.

The game was installed through playonlinux by installing steam and then the game through Steam.  A desktop shortcut for the game was then made from the steam virtual drive.
If the destop shortcut for game is launched get -"no steam found error".  So using playonlinux to launch game opens steam as expected from there the game can be launched successfully.

So xboxdrv is controlling xbox 360 controller mapped the way i wish for working with game.


Xboxdrv manual has proven to contain everything needed to run xboxdrv just my lack of knowledge and understanding has been more than a hinderence
xboxdrv man says
     Quote:
                                                >  [SIZE=2]When you want full game specific configurability and automatic  launching of xboxdrv, it is easiest to write little startup scripts for  your games that will launch xboxdrv, launch your game and then when the  game is finished tear down xboxdrv:

```
#!/bin/sh  exec xboxdrv \    --trigger-as-button -s \   -- \   your_favorite_game  # EOF #         


```Here your_favorite_game is the  executable of your game and is passed to  xboxdrv as last argument. This  will cause xboxdrv to start the game and keep running as long as the  game is running, when the game is done, xboxdrv will quit automatically.
        If you want to pass parameters to the game you have to add a --  separator, as otherwise your options to the game would be eaten up by xboxdrv. [/SIZE][SIZE=2]                     [/SIZE]           

Having a script to 1) unload xpad 2) load uinput and joydev 3) launch  xboxdrv 4) launch application 5) shutdown xboxdrv when application  closed - all automagically would be awesome.


but if 
```
 #!/bin/sh

       exec sudo xboxdrv -s --ui-clear --deadzone 9000 --dpad-as-button --trigger-as-button --deadzone-trigger 15% --ui-axismap "x1^resp:-32768:-4000:0:4000:32767" --ui-axismap "x2=REL_X:25:25,y2=REL_Y:25:25,x1=KEY_A:KEY_D,y1=KEY_W:KEY_S" --ui-buttonmap "tl=KEY_LEFTSHIFT" --ui-buttonmap "b=KEY_C:KEY_LEFTCTRL:500" --ui-buttonmap "a=KEY_SPACE,x=KEY_1,y=KEY_R" --ui-buttonmap "lb=KEY_Q,rb=KEY_E" --ui-buttonmap "lt=BTN_RIGHT,rt=BTN_LEFT" --ui-buttonmap "dl=KEY_4,dr=KEY_F,du=BTN_MIDDLE,dd=KEY_TAB" --ui-buttonmap "back=KEY_ESC,start=KEY_ENTER" \
-- \
playonlinux


       # EOF #
```is run will return -" playonlinux can not be run as root"

Ultimately all i want to achieve is making a script to 1) unload xpad 2) load uinput and joydev 3) launch  xboxdrv 4) launch application 5) shutdown xboxdrv when application  closed.

Any advice on where i should start in educating myself in order to do this would be great.

Thanks in advance.

---

### Post by madinc on 2012-10-04
> **Geezanansa said:**
> Any advice on where i should start in educating myself in order to do this would be great.

did you find a solution or not?

---

### Post by madinc on 2012-10-20
> **madinc said:**
> did you find a solution or not?
The reason i ask is that maybe i can help you

---

### Post by Geezanansa on 2012-10-21
Sorry and thx madinc.

Have been playing games on "an alternative OS" lol and email notifications are not alerting me due to set up....

Still would like to get xboxdrv working more automagically.

Just upgraded to 12.10 so working on getting graphics/booting/shutdown etc working as expected.  

Trying to get ready for Steam on Linux coming but am concerned at my lack of know how regard nvidia card set up with ubuntu and 12.10 has changed display manager so still trying get a fully working os.  


Guess what i am trying to say is it would be nice to have a working game never mind playing a game with a xbox controller  0)

---

### Post by Geezanansa on 2012-10-22
Any help in achieving > Having a script to 1) unload xpad 2) load uinput and joydev 3) launch xboxdrv 4) launch application 5) shutdown xboxdrv when application closed - all automagically would be awesome.
 
I am using cli to launch xboxdrv with different mappings for different games; if and when the game or application needs it.(Doing this by just copying and pasting a saved txt file into cli)
 
Realise need different start up scripts for different games just have not done one yet!

---

### Post by madinc on 2012-10-26
Well its not all automagically because you must put password but maybe you like it this is what i use in Quake Wars for this example.

the name of this script is ETQW not etqw so that when you put ETQW in the terminal runs the script and the game i have all my scripts in /home/USER/bin the scrip will look for the xboxdrv configuration file that is in the game directory.

```
#!/bin/bash

#script needs root permissions
if [ $(id -u) != 0 ]; then
    printf "\n%s\n%s\n\n" "The \"$0\" Script Requires Root Permissions." \
           "Please Enter Your Password."
    sudo "$0" "$@"
    exit
fi

#unload the xpad driver:
rmmod xpad

#load the uinput module:
modprobe uinput

#load the joydev module:
modprobe joydev

#kill any running instance of xboxdrv:
killall xboxdrv

#run xboxdrv with configuration file and start the game:
exec xboxdrv --config ~/ETQW/etqw.xboxdrv ~/ETQW/etqw +set s_alsa_pcm plughw:0 +set s_driver alsa

#kill any running instance of xboxdrv just to be sure:
killall xboxdrv

#exit with success:
exit 0
```
and this is the configuration file the name is etqw.xboxdrv

```
[xboxdrv]
silent=true
deadzone=6000
dpad-as-button=true
trigger-as-button=true

[ui-axismap]
x2=REL_X:10
y2=REL_Y:-10
x1=KEY_A:KEY_D
y1=KEY_W:KEY_S

[ui-buttonmap]
a=KEY_SPACE
b=KEY_G
x=KEY_X
y=KEY_C

[ui-buttonmap]
lb=KEY_R
rb=KEY_F

[ui-buttonmap]
lt=KEY_LEFTSHIFT
rt=BTN_LEFT

[ui-buttonmap]
dl=KEY_4
dr=KEY_2
du=REL_WHEEL:-1:150
dd=REL_WHEEL:1:150

[ui-buttonmap]
back=KEY_M
start=KEY_ESC

[ui-buttonmap]
tl=KEY_H
tr=BTN_RIGHT

# EOF #
```i hope you understand everything if not just ask.

---

### Post by Geezanansa on 2012-10-28
Thank you madinc for sharing an example.  i like a lot.
It is appreciated.   Can see everything there to do is instructed in your last post but just need to work it out for my game.   Can see it so simple.  Am so close to getting this done.
Just acknowledging post and that my hope is that  i do not need to ask.:)  Would feel so much better as i have tried but not yet succeeded.
Have bin, have script, have config.  Just need to work out > xboxdrv configuration file that is in the game directory.  So i might need to ask but dont tell me yet.  One way or another will post back soon.:)

---

### Post by madinc on 2012-10-29
> **Geezanansa said:**
> Thank you madinc for sharing an example.  i like a lot.
It is appreciated.   Can see everything there to do is instructed in your last post but just need to work it out for my game.   Can see it so simple.  Am so close to getting this done.
Just acknowledging post and that my hope is that  i do not need to ask.:)  Would feel so much better as i have tried but not yet succeeded.
Have bin, have script, have config.  Just need to work out .  So i might need to ask but dont tell me yet.  One way or another will post back soon.:)

It's all good :)

---

