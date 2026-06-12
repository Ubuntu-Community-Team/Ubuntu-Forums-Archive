---
title: "Can't get Conky to install right."
date: 2013-10-27
forum: New to Ubuntu
---

### Post by b|ackhole on 2013-10-27
So I thought I could do it but it seems that something is happening and I'm just not skilled enough to figure out what it is. Oh the woes of being a n00b.

I am running on Ubuntu 12.04 LTS.
I've been following the guide for Setting up Conky here: [https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)
In the step **Running & Configuration** I am asked to put in:
```
conky &
```
When I do I receive this terminal message:
```
[1] 23448
krystal@Bamboo:~$ Conky: invalid configuration file '/home/krystal/.conkyrc'


Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:


    imlib_context_free();


    With the parameter:


    context


    being NULL. Please fix your program.



```

How do I resolve this?

(Again, if this issue has been resolved elsewhere and I was just unable to find the thread, please share it with me and I will go there.)

Thanks so much!

---

### Post by ajgreeny on 2013-10-27
Can we see your ~/.conkyrc file which is obviously faulty in some way./

---

### Post by b|ackhole on 2013-10-27
**Home** > **.conkyrc** > ***~/.conkyrc***

```
# Conky settings #background no
update_interval 1


cpu_avg_samples 2
net_avg_samples 2


override_utf8_locale yes


double_buffer yes
no_buffers yes


text_buffer_size 2048
#imlib_cache_size 0


temperature_unit fahrenheit


# Window specifications #


own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below


border_inner_margin 0
border_outer_margin 0


minimum_size 200 250
maximum_width 200


alignment tr
gap_x 35
gap_y 55


# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no


# Text settings #
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5


uppercase no


temperature_unit celsius




default_color FFFFFF


# Lua Load  #
lua_load ~/.conky/clock_rings.lua
lua_draw_hook_pre clock_rings


TEXT
${voffset 8}${color FF6600}${font caviar dreams:size=16}${time %A}${font}${voffset -8}${alignr 50}${color FFFFFF}${font caviar dreams:size=38}${time %e}${font}
${color FFFFFF}${voffset -30}${color FFFFFF}${font caviar dreams:size=18}${time %b}${font}${voffset -3} ${color FFFFFF}${font caviar dreams:size=20}${time %Y}${font}${color FF6600}${hr}
${voffset 140}${font caviar dreams:size=10}${alignr}HOME${font}
${font caviar dreams:size=12}${color FFFFFF}${alignr}${weather [http://weather.noaa.gov/pub/data/observations/metar/stations/](http://weather.noaa.gov/pub/data/observations/metar/stations/) LQBK temperature temperature 30} °C${font}
${image ~/.conky/new-ubuntu-logo.png -p 64,125 -s 70x20}


${color FFFFFF}${goto 25}${voffset 35}${cpu cpu0}%
${color FF6600}${goto 25}CPU
${color FFFFFF}${goto 50}${voffset 23}${memperc}%
${color FF6600}${goto 50}RAM
${color FFFFFF}${goto 75}${voffset 23}${swapperc}%
${color FF6600}${goto 75}Swap
${color FFFFFF}${goto 100}${voffset 23}${fs_used_perc /}%
${color FF6600}${goto 100}Disk
${color FFFFFF}${goto 125}${voffset 25}${downspeed eth0}
${color FFFFFF}${goto 125}${upspeed eth0}
${color FF6600}${goto 125}Net






${color FFFFFF}${font caviar dreams:size=8}Uptime: ${uptime_short}
${color FFFFFF}${font caviar dreams:size=8}Processes: ${processes}
${color FFFFFF}${font caviar dreams:size=8}Running: ${running_processes}




${color FF6600}${font caviar dreams:size=8}${alignr}${nodename}
${color FF6600}${font caviar dreams:size=8}${alignr}${pre_exec cat /etc/issue.net}  $machine
${color FF6600}${font caviar dreams:size=8}${alignr}Kernel: ${kernel}
```

---

### Post by LuvLinuxOS on 2013-10-27
> I am running on Ubuntu 12.04 LTS.
I've been following the guide for Setting up Conky here: [https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)
In the step **Running & Configuration** I am asked to put in:

Hey b|ackhole,

                         I think you need to try an external source for a solution and sometimes the best thing to do is purge so that you can start over. Since you are a n00b I think you best bet would be to use the GUI (graphical user interface) interface for apt-get (i.e. Ubuntu Software Center and Synaptic Package Manager) both of them come preinstalled on your Ubuntu Distro. Once you have removed or better yet purged conky from your system follow these steps to install conky... you might want to reboot between purging and installing just for good measures. [http://fauzimh.wordpress.com/2012/02/22/lubuntu-little-tweaks-1/](http://fauzimh.wordpress.com/2012/02/22/lubuntu-little-tweaks-1/)... Just Conky!!! LOL!!! :D\\:D/[-X


Be Blessed...I Am!!!

[> ~LuvLinuxOS~]("http://luvlinuxos.blogspot.com")

---

### Post by b|ackhole on 2013-10-27
Hey LuvLinuxOS,

I've uninstalled Conky three times fully from my system using SPM (and hand deleting any files left over that I could find), and tried 2 different Conky installs outside of the ubuntu one I linked. I mean, yes I'm new but I've successfully installed everything else so far that I'm customising without an issue. I'll clean it out of my system again and try from your source and see how that goes.  Also does it make a difference that the link you've shared is for Lubuntu, or do all the --buntu OS's receive these things equally?

And why the 'shame on you' emote? :/

---

### Post by QIII on 2013-10-27
If you believe you still have conky installed, could you please let us know if you can start conky with

```
conky -c /home/yourusername/.conky/.conkyrc
```

(or whatever the complete path to your conkyrc is)

or paste back the terminal messages if it does not.

---

### Post by b|ackhole on 2013-10-27
I just deleted everything again, I'm debating on going through the link that Lub shared to the Lubuntu Little Tweaks or if I should go through the Ubuntu help page again I originally linked? Or is there a better guide I should follow for Ubuntu 12.04 LTS?

Terminal: (hopefully I have gotten everything uninstalled)
```
The program 'conky' can be found in the following packages: * conky-cli
 * conky-std
Try: sudo apt-get install <selected package>
```

---

### Post by QIII on 2013-10-27
You need not go through that particular tutorial.

Install conky

```
sudo apt-get install conky-all
```

Create a new file for your conkyrc.  I use /home/myusername/.conky/conkyrc

Let me know when you get to that point.  I'm looking for a simple conky you can start working with.

---

### Post by b|ackhole on 2013-10-27
All right I've done the apt-get. I don't have a username under my .home folder, I disabled multiple accounts so possibly this is why. Either way I have made .home/.conky/??

I have made a blank text document named conkyrc.  Does that need to be named .conkyrc, or am I ready to go?

---

### Post by deadflowr on 2013-10-27
Ninja'd by QIII

And +1 to QIII's suggestion of using the -c flag.
That will make it call the conky file where ever it is and under whatever name you give it.

Aside from conky-all, I don't see anything you might need beyond that, but I don't know what the lua script might be calling/needs.

---

### Post by QIII on 2013-10-27
You won't see your user name as a separate folder in your /home.  When you go to /home, you are already put into your user's directory.

If you are using a file manager, just go to /home, create a new folder named .conky, go into that and create a new file called conkyrc

From the terminal, you qualify that path as /home/yourusername/.conky/conkyrc.

Be careful of terminology, here.

. means a hidden file
/ means a directory

---

### Post by b|ackhole on 2013-10-27
@deadflower:  Thanks for pointing out what the -c does in the code! It's a long process learning all these little nuances, so knowing a break down of what the code is doing is really helpful!

---

### Post by b|ackhole on 2013-10-27
> **QIII said:**
> You won't see your user name as a separate folder in your /home.  When you go to /home, you are already put into your user's directory.

If you are using a file manager, just go to /home, create a new folder named .conky, go into that and create a new file called conkyrc


File is made and ready to go.

---

### Post by QIII on 2013-10-27
OK.  This is a little much.  I just cut down an old conky.  This should make you see the words "your text here" in the upper left of your screen.


```
####
#  general startup settings
####

background yes
update_interval 0.5
text_buffer_size 1024
total_run_times 0
alignment top_left
gap_x 35
gap_y 65
minimum_size 300 950
maximum_width 300

####
#  Some window setup
####
own_window_class Conky
own_window yes
own_window_type normal
own_window_argb_visual yes
own_window_transparent yes
own_window_argb_value 0
own_window_hints below,skip_pager,skip_taskbar,undecorated,sticky
background yes
# font defaults:
use_xft yes
xftfont RadioStars:size=7
xftalpha 0.9
override_utf8_locale yes

####
# images, buffering, shading
####
imlib_cache_size 60
double_buffer yes
draw_shades yes
default_shade_color 000000

####
# misc text formatting
####
short_units yes
pad_percents 2
border_inner_margin 0
uppercase no
use_spacer right

####
# outlines and borders
####
draw_outline no
draw_borders no
draw_graph_borders no
border_width 0

####
# stdout/console printing
####
out_to_ncurses no
out_to_console no

####
## process settings
top_name_width 4
#no_buffers yes
####

####
# sampling
####
cpu_avg_samples 2
net_avg_samples 2

#### end config

####
## everything below 'TEXT' is drawn on screen
####
     
TEXT
####
#  Headers
####
${color green}your text here
```

to start it, go to the terminal and do

```
conky -c /home/yourusername/.conky/conkyrc
```

or /.conkyrc if you made that file hidden.

---

### Post by b|ackhole on 2013-10-27
So I copy and pasted that into the new conkyrc document I created, and when I pressed save a new file appeared in my /.conky folder named "conkyrc~" along with the original "conkyrc".  Is that normal?

---

### Post by deadflowr on 2013-10-27
> **b|ackhole said:**
> @deadflower:  Thanks for pointing out what the -c does in the code! It's a long process learning all these little nuances, so knowing a break down of what the code is doing is really helpful!


When conky is launched, its default location to look is first the .conkyrc file in the users home folder.
If it isn't there then it goes to the /etc/conky system folder for a file called conky.conf(or something like that).
If you have the -c(also can be --config) option, or it looks for that first, then the .conkyrc file, then the /etc/conky/conky.conf.

---

### Post by QIII on 2013-10-27
Yes.  Most text editors save a copy.

---

### Post by deadflowr on 2013-10-27
> **b|ackhole said:**
> So I copy and pasted that into the new conkyrc document I created, and when I pressed save a new file appeared in my /.conky folder named "conkyrc~" along with the original "conkyrc".  Is that normal?

Yes, if you edited the file in gedit.
Gedit automatically makes backups and saved files you were working on.
the ~ symbol at the end means backup, or old.

---

### Post by b|ackhole on 2013-10-27
Okay great, so long as it's normal! This is the terminal message I got and what I entered: (Something's not playing nice.)

```
krystal@Bamboo:~$ conky -c /home/krystal/.conky/conkyrc
Conky: forked to background, pid is 28880
krystal@Bamboo:~$ 
Conky: desktop window (1e00095) is subwindow of root window (84)
Conky: window type - normal
Conky: drawing to created window (0x8000002)
Conky: drawing to double buffer

```
* note, it just stops there and doesn't return to my krystal@Bamboo:~$:

@deadflower: Awesome! Thanks x2 for both of those explanations.

---

### Post by QIII on 2013-10-27
That's normal.  That indicates all has gone well.  You can close the terminal.

Now comes the fun:  Play around with conkyrc and watch the magic!


Edit:  I forgot to ask -- do you see the message in the upper left?

---

### Post by b|ackhole on 2013-10-27
I was about to say no then I remembered I have my TV plugged in through HDMI and left is reeaaaaally left and behind me. So yes! I can see it.

[COLOR=#000000]**QIII**, thanks so much for taking the time to walk me through this and get it to where it is, and also for your explanations.[/COLOR]
[COLOR=#000000]And to **darkflower**, thanks for breaking down how the symbols affect the inputs in terminal.

I'm really excited to get to know this community more.

*Edit: *Also now I have more than 10 Beans so I can have an identity! ... in and hour, when it updates.

*EDIT EDIT:*  Possibly a silly question, but what's the terminal code to reboot a program, like when I make an edit to the file?[/COLOR]

---

### Post by deadflowr on 2013-10-27
Oddly enough, with the conky file, when I save it, it restarts it.

If I remember though, there is a code to run something like
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo killall -SIGUSR1 conky[/FONT][/COLOR]
```
BUT, don't hold me to it.

---

### Post by b|ackhole on 2013-10-27
> **deadflowr said:**
> Oddly enough, with the conky file, when I save it, it restarts it.

If I remember though, there is a code to run something like
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo killall -SIGUSR1 conky[/FONT][/COLOR]
```
BUT, don't hold me to it.

That worked great. Now if only I can get changing alignment from "alignment top_left" to "alignment top_right" to move more than just the "your text here" ...
I shall explore the interwebs for things!

---

### Post by LuvLinuxOS on 2013-10-28
> Hey LuvLinuxOS,

I've uninstalled Conky three times fully from my system using SPM (and  hand deleting any files left over that I could find), and tried 2  different Conky installs outside of the ubuntu one I linked. I mean, yes  I'm new but I've successfully installed everything else so far that I'm  customising without an issue. I'll clean it out of my system again and  try from your source and see how that goes.  Also does it make a  difference that the link you've shared is for Lubuntu, or do all the  --buntu OS's receive these things equally?

And why the 'shame on you' emote? :/

Hey b|ackhole,

Just having some fun with the emotes!!! Now, my first version of Lubuntu was 12.04 and for the most part anything that can be installed in one Ubuntu flavor can be installed in the other.  Then main difference in the Ubuntu flavors is the DE.  Now, with that being said you might have some DE issues that needs researching for your Ubuntu 12.04 are you using Gnome or Unity.  I have heard of the horror stories and that is why I started using Lubuntu in the first place.  I have older hardware and I just could not get Unity to run properly.  I was only trying to get you to use a different process for you install as that helps when you can't get something to work one way try another.  Lastly, look at the following links and I hope this helps!!! [https://launchpad.net/~vincent-c/+archive/conky/+packages](https://launchpad.net/~vincent-c/+archive/conky/+packages) [http://ubuntuforums.org/showthread.php?t=1984685](http://ubuntuforums.org/showthread.php?t=1984685)

---

### Post by deadflowr on 2013-10-28
Here
[http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

And look at the section for config file settings.
That has all the up-to-date commands you can set in conky.

---

### Post by stinkeye on 2013-10-28
You don't need the sudo....
```
[COLOR="#FF0000"]sudo[/COLOR] killall -SIGUSR1 conky
```

You own the process so just use...
```
killall -SIGUSR1 conky
```

The main things to note from what's been said is if you save 
your conky config to **$HOME/.conkyrc** (ie a hidden file in your home folder),
simply running in the terminal... ```
conky
``` will load that config.


You'll find configs all over the web that you can try.
You will need any extra scripts, fonts and images that they use
and you will most likely need to change some things for your computer setup.

I save my main/favourite conky config to **$HOME/.conkyrc** so it will load with the "conky" command.
Any  other configs, I save in **$HOME/conky/configs** with descriptive names.
eg  **clock.conkyrc** (can name whatever you like)
Then to load one of these configs I would use  ....
```
**conky -c **[COLOR="#696969"]~/conky/configs/clock.conkyrc[/COLOR]
```
[ATTACH=CONFIG]247336[/ATTACH]


The conky config consists of two parts split by the line "**[COLOR="#FF0000"]TEXT[/COLOR]**".
Above **TEXT** are the config settings (how it is dispayed) and
below are the objects/variables (what is displayed). 
This is a sample config with good descriptions of the config settings
and shows same simple samples.
Save as **sample.conkyrc** to (eg) ~/conky/configs
```
###  Begin Window Settings  ##################################################
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
own_window_class Conky
own_window_title myconky
#own_window_colour gray

### ARGB can be used for real transparency
### NOTE that a composite manager is required for real transparency.
### This option will not work as desired (in most cases) in conjunction with
### own_window_type override
 own_window_argb_visual yes # Options: yes or no

### When ARGB visuals are enabled, use this to modify the alpha value
### Use: own_window_type normal
### Use: own_window_transparent no
### Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.
 own_window_argb_value 160

# Use the Xdbe extension? (eliminates flicker)
# It is highly recommended to use own window with this one
# so double buffer won't be so big.
double_buffer yes

minimum_size 280 300	## width, height
maximum_width 280	## width

#Text alignment on screen, {top,bottom,middle}_{left,right,middle} or none. Can also be abbreviated with first chars of position, ie. tr for top_right.
alignment tr

#Gap, in pixels, between right or left border of screen
gap_x 20	### horizontal
gap_y 60	### vertical


####################################################  End Window Settings  ###
###  Font Settings  ##########################################################
# Use Xft (anti-aliased font and stuff)
use_xft yes
xftfont ubuntu:bold:size=12

# Alpha of Xft font. Must be a value at or between 1 and 0 ###
xftalpha 1
# Force UTF8? requires XFT ###
override_utf8_locale yes

uppercase no
######################################################  End Font Settings  ###
###  Color Settings  #########################################################
draw_shades yes #no # amplifies text if yes
default_shade_color 000000

draw_outline no # amplifies text if yes
default_outline_color 000000

default_color DCDCDC #220 220 220 Gainsboro
#default_color C0C0C0 #192 192 192 Silver
#default_color B0E0E6 #176 224 230 PowderBlue
color0 8FBC8F #143 188 143 DarkSeaGreen
color1 778899 #119 136 153 LightSlateGray
color2 B0E0E6 #176 224 230 PowderBlue
color3 9ACD32 #154 205  50 YellowGreen
color4 FFA07A #255 160 122 LightSalmon
color5 FFDEAD #255 222 173 NavajoWhite
color6 00BFFF #  0 191 255 DeepSkyBlue
color7 5F9EA0 # 95 158 160 CadetBlue
color8 BDB76B #189 183 107 DarkKhaki
color9 CD5C5C #205  92  92 IndianRed
#####################################################  End Color Settings  ###
###  Borders Section  ########################################################
draw_borders no
# Stippled borders?
stippled_borders 0
# border margins
border_inner_margin 9
border_outer_margin 0
# border width
border_width 0
# graph borders
draw_graph_borders #no
#default_graph_size 15 40
#####################################################  End Borders Secton  ###
###  Miscellaneous Section  ##################################################
# Boolean value, if true, Conky will be forked to background when started.
background no

# Adds spaces around certain objects to stop them from moving other things
# around, this only helps if you are using a mono font
# Options: right, left or none
use_spacer none

# Default and Minimum size is 256 - needs more for single commands that
# "call" a lot of text IE: bash scripts
text_buffer_size 512

# Subtract (file system) buffers from used memory?
no_buffers yes

# change GiB to G and MiB to M
short_units yes

# Like it says, ot pads the decimals on % values
# doesn't seem to work since v1.7.1
pad_percents 2

# Imlib2 image cache size, in bytes. Default 4MiB Increase this value if you use
# $image lots. Set to 0 to disable the image cache.

imlib_cache_size 0

#   Maximum size of user text buffer, i.e. layout below TEXT line in config file
#  (default is 16384 bytes)
# max_user_text 16384

# Desired output unit of all objects displaying a temperature. Parameters are
# either "fahrenheit" or "celsius". The default unit is degree Celsius.
# temperature_unit Fahrenheit
##############################################  End Miscellaneous Section  ###

update_interval 1

[COLOR="#FF0000"]TEXT[/COLOR]
${font Sans:size=24}${color3}This is a sample${font}
${font Sans:size=14}${alignc}This line is centered${font}
${font Sans:size=12}${goto 20}20 pixels in from left${font}
${alignr}Default font aligned right

```
Then in terminal run....
```
conky -c ~/conky/configs/sample.conkyrc
```
and you should see something like this....
[ATTACH=CONFIG]247339[/ATTACH]



For help, in the terminal...
```
man conky
```

For configs and help see....
 [**_[COLOR="#B22222"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2236")

---

### Post by b|ackhole on 2013-10-28
@stinkeye: This was exactly what I needed!  If/when I successfully get my own custom one up and running I will share it.

---

### Post by newb85 on 2013-10-28
> **b|ackhole said:**
> I don't have a username under my .home folder, I disabled multiple accounts so possibly this is why.

Hello, what's this?  I've never heard of someone being able to disable multiple accounts in Ubuntu.  What makes you think you have done so? Put differently, how exactly did you go about this.

I suspect the reason you think you don't have a username under /home is because Nautilus actually displays /home/[username] as "Home".  (It can be a little confusing...)

---

