---
title: "Need help writing a script to switch config file on button press"
date: 2012-09-16
forum: Programming Talk
---

### Post by spezticle on 2012-09-16
So, I'm not very experienced with fun scripts like this so I need help and insight from those who are good at this sort of thing.

A little background:
My mouse broke. In the meantime i plugged my xbox controller in, installed xboxdrv, and created a config file defining and customizing all the buttons for mouse operation.
It works great. That was easy. I've actually gotten used to it and if I can make this script work the way I see it in my head, I might never use a mouse again.

So, the details:
Basically, when I press the xbox button (xboxdrv recognizes it as "guide") I want it to cycle through a list of different profiles for different usage scenarios. Profile 1 being standard desktop operation, profile 2 is mostly the same but the R and L buttons have different functions for music control, so on and so forth. I have all of the different config files already created but currently, i switch manually.

in all the config files, the xbox button is set to XK_XF86Close which as far as I can tell, does nothing by default. next, I opened up the keyboard shortcuts gui and defined a custom shortcut which will run /home/user/joy_profile_switch.sh

this switch.sh script basically has to read which number profile that it's on and advance to the next one, if at the last then it will start back at the first again, and that's pretty much it. each profile illuminates a different led light on the controller for visual feedback of which profile i'm on.

any help, insight, or suggestions would be much appreciated.
if somebody wants to reply with a suggestion that there's already a neat gui application for this...
what fun would that be? :-P

thanks in advance

---

### Post by Bucky Ball on 2012-09-16
*Thread moved to **Programming Talk***

---

### Post by Ryan Dwyer on 2012-09-16
Here you go:

```

#!/bin/bash

LIVE_CONFIG_FILE=live-config.conf

# Determine which file number is currently being used
CURRENT_NUM=`ls -l | grep "$LIVE_CONFIG_FILE" | awk '{print $11}' | cut -d '/' -f 2`

# Determine how many configs we have available
NUM_AVAILABLE=`ls configs | wc -l`

if [ $CURRENT_NUM -eq $NUM_AVAILABLE ]; then
    NEW=1
else
    NEW=$(($CURRENT_NUM+1))
fi

rm $LIVE_CONFIG_FILE
ln -s "configs/${NEW}" $LIVE_CONFIG_FILE

echo "Config changed to #${NEW}"

```The script will need to be placed in the same directory as the config file. Make a subdirectory called configs and put your files in there, named 1, 2, 3, etc. It works by symlinking the live config file to your available ones, incrementing it each time it's run.

Your keyboard shortcut command will have to be something like:
```

cd /home/user/.config/whatever/ && ./joy_profile_switch.sh

```Or even:
```

cd /home/user/.config/whatever/ && notify-send "`./joy_profile_switch.sh`"

```...which will display a notification in the top right with what config you switched to.

---

### Post by Geezanansa on 2012-09-19
The xboxdrv manual gives options for doing exactly as you wish in using the guide(xbox) button to change controller configurations.

To see the manual Try ```
man xboxdrv
``` or go to [http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv.html]("http://pingus.seul.org/%7Egrumbel/xboxdrv/xboxdrv.html")


With reference to the xboxdrv manual ;  thought this is what you could be looking for.
> **Config Slot Options**

          You can use multiple configurations, called config slots,  with your controller. You switch between those multiple configurations  by pressing the Guide button by default, but you can also set another  button via the option --toggle.
                     --config-slot *NUM*               Select the config slot *NUM*.
             --next-config               Allows the creation of an alternative uinput  configuration to which one can toggle at runtime by pressing the  ui-toggle button (defaults to guide).
               $ xboxdrv \     --mouse \   --next-config      --ui-axismap X1=ABS_X,Y1=ABS_Y \     --ui-buttonmap A=JS_0,B=JS_1                 The above configuration would install mouse emulation  as first configuration and a simple joystick emulation as second  configuration. Allowing toggling between mouse emulation and joystick  handling by pressing the guide button.
                Not that --next-config is currently limited to only configurations done with --ui-buttonmap and --ui-axismap, autofire, throttle emulation, deadzones and all other things can currently not be switched at runtime.
             --toggle *XBOXBTN*               Sets the button that will be used to toggle between  different different configurations. A value of 'void' will disable the  toggle button. If no toggle button is specified, the guide button will  be used to toggle between configurations.




That is when running xboxdrv --daemon.
There is at least one other option to do what you want in the manual which would be the making of config files for each configuration.
> 
**Config File Options**

                     -c, --config *FILE*               Reads configuration information from *FILE*. Configurations from file are handling as if they would be command line options at the position of --config *FILE*.
                The syntax of *FILE*  is the familiar INI syntax used for many configuration files. Regular  key/value pairs must go into the [xboxdrv] section. '#' and ';' can be  used for comments. Key names have for most part the same name as command  line options. Command line options that take a list of input mappings  (--ui-buttonmap, --ui-axismap, --evdev-absmap, ...) can be split of into  their own section for better readability.
                The examples/ directory contains some example configuration files.
               [xboxdrv] silent=true deadzone=6000 dpad-as-button=true trigger-as-button=true  [ui-axismap] x2=REL_X:10 y2=REL_Y:-10 x1=KEY_A:KEY_D y1=KEY_W:KEY_S  [ui-buttonmap] a=KEY_LEFTSHIFT b=BTN_C x=BTN_EXTRA y=KEY_C  [ui-buttonmap] lb=BTN_RIGHT rb=KEY_SPACE  [ui-buttonmap] lt=KEY_Z rt=BTN_LEFT  [ui-buttonmap] dl=KEY_4 dr=KEY_2 du=REL_WHEEL:-1:150 dd=REL_WHEEL:1:150  [ui-buttonmap] back=KEY_TAB start=KEY_ESC  # EOF #              --alt-config *FILE*               A shortcut for writing --next-config --config *FILE*.
                To load multiple configuration options use:
               xboxdrv --config first.ini --alt-config second.ini --alt-config third.ini              -o, --option *NAME=VALUE*               Set an option as if it would come from a config file from the command line.
             --write-config *FILE*               Write an example configuration file to *FILE*.
                      







Better  chance of xboxdrv --daemon working running on latest version of  xboxdrv.(0.8.4)  To get the latest version just add the appropriate ppa  for your flavour from xboxdrv developers website following instructions  at [https://launchpad.net/~grumbel/+archive/ppa]("https://launchpad.net/%7Egrumbel/+archive/ppa")
then from terminal
 ```
sudo apt-get update
sudo apt-get upgrade
```


Plenty of reading at [http://pingus.seul.org/~grumbel/xboxdrv/]("http://pingus.seul.org/%7Egrumbel/xboxdrv/")




I  am like you and have managed to get xboxdrv running and using it for  what is wanted. To get all this happening at a double click or even  automagically at start up/connection would be nice.  Hence why you ask  for help with writing script.  Understand where you are coming from but  can not do bash. ...yet!:lolflag:





 but the manual says it is as simple as 



> 
When you want full game specific configurability and automatic  launching of xboxdrv, it is easiest to write little startup scripts for  your games that will launch xboxdrv, launch your game and then when the  game is finished tear down xboxdrv:
       #!/bin/sh  exec xboxdrv \   --trigger-as-button -s \   -- \   your_favorite_game  # EOF #         Here your_favorite_game is the  executable of your game and is passed to xboxdrv as last argument. This  will cause xboxdrv to start the game and keep running as long as the  game is running, when the game is done, xboxdrv will quit automatically.
        If you want to pass parameters to the game you have to add a -- separator, as otherwise your options to the game would be eaten up by xboxdrv.




That  would be good for assigning xboxdrv config to specific applications and  starting stopping xboxdrv by opening closing application.  Totally  automagical.


Maybe post your /home/user/joy_profile_switch.sh and list what you intend doing with different configs?  

Have you tried xboxdrv --mouse?

Keyboard shortcuts are cool.  Mice are vermin!

---

