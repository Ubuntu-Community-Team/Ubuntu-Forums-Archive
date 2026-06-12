---
title: "How-to compile and install conky 1.4.5 from source"
date: 2007-02-04
forum: Outdated Tutorials &amp; Tips
---

### Post by m.musashi on 2007-02-04
**Disclaimers and such.**
----------------------
[color=red]UPDATE: Conky 1.4.5 is now in the feisty repos. If you run feisty, it would probably be better to install using apt-get or synaptic[/color]

This is my first how to and it's really just a compilation of information I found on these forums. There are a number of good how-tos but it seemed I was looking here and there for everything. Hopefully this will simplify the situation. I also hope there isn't something like this already - I did try to find one. With any luck this might save others some time so here goes.

In case you are unaware, conky is a lightweight system monitor that displays on your desktop. See the screenshots below.

**There could very well be some mistakes here or steps I gloss over and shouldn't so if anyone has suggestions for improvement please post and I'll amend.**

These instructions are for installing the newest (at the time of writing) conky 1.4.5 from source on Ubuntu-Edgy. This is a simple program so it should work on other versions as well. This was much easier than I thought so don't be afraid.

There is an excellent how to for conky 1.4.2 [here](http://www.ubuntuforums.org/showthread.php?t=205865) so you might try that first. That version of conky works very nicely but 1.4.5 seems a bit faster and has some features for formatting that I found particullary useful for what I wanted (particularly the goto option for layout). The rest of the info came primarily from [here](http://www.ubuntuforums.org/showthread.php?t=324118). Thanks crimesaucer.

In order for CPU temps and other hardware sensing to work you will probably need to configure lm-sensors. [Here](http://www.ubuntuforums.org/showthread.php?t=2780) is a good how-to for that. It's a slightly confusing process but I eventually got it to work.
----------------------

Okay, lets get started.

**Install dependencies**

There are some needed packages to do the compile and for conky...

```
sudo apt-get install libxext-dev lm-sensors build-essential checkinstall wmctrl
```

I'm not sure about the wmctrl package or what, exactly, it does. Some how tos have a line in the .conkyrc for it. I deleted that line from my .conkyrc and it is not included below. There are some suggestions that it doesn't work with beryl.

These files are also apparently needed (thanks eXisor)

```
sudo apt-get install libglib2.0-dev libxft-dev libx11-dev libxdamage-dev
```

**Download Source**

Now you need to download and untar the source.

Visit [http://conky.sourceforge.net/](http://conky.sourceforge.net/) and follow the links to the download file. I'm not direct linking in case something changes. There are a couple option. I used the one entitled "conky-1.4.5.tar.gz (Platform-Independent Source .gz)". Others may work too. 

Save it where you want and untar. I just saved to the desktop and then right clicked and said extract here. Change directory to the untared folder.

**Begin the Install**

```
cd Desktop
cd conky-1.4.5
```

Now comes the fun part...

Do each of these one at a time. If you get any errors it's probably because of dependencies. I hope the above named packages are all that is needed but if you have problems post back and I'll see if I can figure it out.

```
./configure
make
```

A lot of stuff probably went flying by but you can safely ignore it. If you didn't receive any errors you are now ready to install. There are two ways to finish the install that I am aware of - a "traditional" method and potentially better method. Most source packages you download will give you traditional instructions. If you want to be able to uninstall the package later or easily reinstall it, use the second method.

**Traditional**

Type the following into the terminal after the "make" process finished
```
sudo make install
```
To clean up...
```
make clean
```
Conky is now installed and ready to use. See below for configuring instructions.

**Alternative "checkinstall" method**

This process will create a .deb file. A .deb is the standard format for a Debian based Linux distro. It is somewhat akin to a .exe in Windows. In Ubuntu (I don't know about other distros) double clicking a .deb will open a gui to do the install. This process will not only make the .deb but do the install as well. When it finishes you will have conky installed and a .deb file in the folder. You might want to save the .deb in case you need to reinstall later.
```
sudo checkinstall
```
Answer the questions. After you type in a description and press enter you have to press enter a second time to get it to continue. It then shows you a list of options you can change. I have no idea what any of them are for. Just press enter again and it will finish. When this finishes you are done. Save the .deb and trash the folder if you want.

If you want to remove conky at some time in a terminal type
```
sudo dpkg -r conky
```

**Edit xorg.conf**

You also need to make a slight modification to your xorg.conf file to help the display. I did not make this modification at first and I had no problems until I started to use beryl. It may not be necessary if you don't use beryl. This change does not seem to cause any problems.

```
sudo gedit /etc/X11/xorg.conf
```

Find the section called "Module" and add

```
Load "dbe"
```

Save and close. You may need to reboot or restart X (ctrl-alt-backspace) for that change to take effect.

**Create and Save conky config file**

If all that went well, conky is now installed but not yet ready to use. You need to create a config file in your /home/username called .conkyrc. The above mentioned 1.4.2 how to has great directions on how to do this. Here is a quick and dirty run through.

Here is a sample .conkyrc. It is a slightly modified version from the 1.4.2 how to for dual core cpu and a bit less output on the screen. You can copy this to start with and modify to your hearts content later. For more info on what variables and options are available go to the conky homepage and read the documentation.

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft no

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=9

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 3.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
# Use pseudo transparency with own_window?
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour #C0C8CD

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 3

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 35

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color black}$nodename $sysname $kernel on $machine
${color #C0C8CD}UpTime: ${uptime}   Load: ${loadavg}
${color black}$stippled_hr
${color black}CPU Usage: $cpu  %   CPU: ${freq}mhz ${alignr}Temp: ${acpitemp}
${color black}${cpugraph cpu0 000000 C0C8CD}
${color black} CPU0: ${cpu cpu1}% 
${color #C0C8CD}${cpubar cpu1} 
${color black} CPU1: ${cpu cpu2}% 
${color #C0C8CD}${cpubar cpu2}
${color black}Processes:${color #C0C8CD} $processes  ${color black}  Running:${color #C0C8CD} $running_processes

${color black}Name              PID     CPU%   MEM%
${color blue} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #C0C8CD} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #C0C8CD} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #C0C8CD} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color black}Mem usage
${color blue} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #C0C8CD} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #C0C8CD} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color black}$stippled_hr
${color black}RAM:     ${color #C0C8CD}$memperc% ${membar}
${color black}Swap:     ${color #C0C8CD}$swapperc% ${swapbar}

${color black}Root:     ${color #C0C8CD}${fs_size /} - ${fs_free_perc /}% free   ${fs_bar /}
${color black}Home:    ${color #C0C8CD}${fs_size /home} - ${fs_free_perc /home}% free   ${fs_bar /home}
${color black}$stippled_hr
${color black}Networking: ${color #C0C8CD}(${addr eth1})
${color black} Down:${color #C0C8CD} ${downspeed eth1} k/s${color black} ${alignr}Up:${color #C0C8CD} ${upspeed eth1} k/s
${color black}${downspeedgraph eth1 32,125 C0C8CD 0000ff} ${alignr}${color black}${upspeedgraph eth1 32,125 C0C8CD ff0000}
${color black}$stippled_hr
```

```
gedit /home/username/.conkyrc
```

Paste the above into the file modifying as you wish. Save and close.

To run, press alt-F2 and type "conky" (no quotes).

You should now see conky on your screen.

To have conky autostart on login create a small bash script called .conky_start.sh and save it to your /home.

```
gedit .conky_start.sh
```
copy the code below and past into the file. Save and close

```
#!/bin/bash
sleep 10 && conky;
```

This would start conky after 10 seconds after you login. The delay can be changed. Some sort of delay is desirable if you autostart beryl as well since conky works best if started after beryl. Make sure the script is executable:

```
chmod a+x .conky_start.sh
```

Now, add it to your startup programs (menu: system->preferences->session->startup programs).

Congrats. You are now the proud owner of your very own conky 1.4.5.

---

### Post by xtrm_redbull on 2007-02-12
Nice how to, and it works for me:) , but my desktop icon and conky disappears for a few seconds, but when i highlight it appears again.:confused:  I edit the xorg.conf like you said because I sometimes use beryl. Is there a way fix this?

Thanks:)

---

### Post by m.musashi on 2007-02-12
> **xtrm_redbull said:**
> Nice how to, and it works for me:) , but my desktop icon and conky disappears for a few seconds, but when i highlight it appears again.:confused:  I edit the xorg.conf like you said because I sometimes use beryl. Is there a way fix this?

Thanks:)

Are you using gnome or kde (or something else)? There are some issues with conky and kde with disappearing icons. I actually haven't tried 1.4.5 with kde but I suspect it's the same issue. There are some work arounds for kde. I'll find the links and post back. If gnome, these settings are supposed to take care of that:
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
# Use pseudo transparency with own_window?
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
If you have it set that way, you can also try setting own_window_type to desktop and see if that helps.

Let me know what window manager you're using and I'll see what else I can do.

---

### Post by xtrm_redbull on 2007-02-13
Im using gnome and xfce, window manager. I check my .conkyrc setting and I saw the codes in your post already there. Thanks

---

### Post by m.musashi on 2007-02-13
> **xtrm_redbull said:**
> Im using gnome and xfce, window manager. I check my .conkyrc setting and I saw the codes in your post already there. Thanks

Okay, I did a bit more research. Most of this comes from the how to for 1.4.2 that I referenced in the first post. As I don't have xfce right now I can't try this. If these fixes don't work I'll install it and see if I can replicate the problem.

If I understand, you are running Ubuntu with the xfce WM and sometimes use beryl. With this set up, conky and your desktop icons disappear from time to time (or is it all time?). The problem and fix probably has something to do with the settings I pointed out in the last post. Try changing them in various ways. For xfce, this is the recommended set up
```
own_window yes
own_window_type override
own_window_transparent yes
```
However, if you are using compiz (beryl is very similar) and AIGLX then this is recommended
```
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
Try them and see what happens. 

You might also add this to the end of the .conkyrc
```
${execi 30 wmctrl -a conky}
```
It is supposed to ensure that conky is on the root window. It does it every 30 seconds so if it disappears it should come back. You will have to have installed the wmctrl package as well. This line seems to cause some problems of it's own so you may solve one thing and end up with another.

If none of this works, can you log into gnome and see what it does there? It would help to know if it's specifically a xfce thing or not.

Hope this helps.

---

### Post by xtrm_redbull on 2007-02-14
Hi there, Ive tried the settings you gave, but conky still flickers, but the icons are ok, in both gnome and xfce. Anyway I decided to copy other .conkyrc in the forums to test it in my laptop, and ive found one that flickers less, maybe the problem is in my system specs, since all of the .conkyrc i tested flickers. Thanks again. :)

---

### Post by m.musashi on 2007-02-14
Hmm. flickers in gnome too. About all I've ever heard about flickering in gnome is solved by adding
```
Load "dbe"
```
to the xorg.conf file. If you followed that part in the how to and made sure it's in the right section then I'm not really sure what could be the cause. Sorry I can't be of more help. I'll post back if I find anything.

---

### Post by meander on 2007-02-21
i had conky running great on my ubuntu system a while ago, now im on a kubuntu machine and its not working right. it works, and has all the right info, it just looks wrong. instead of being transparent its black background, and some of the text is black too, so you cant see it.

---

### Post by m.musashi on 2007-02-21
Yeah, there are some issues with KDE that seem to be mostly related to how it draws (or doesn't draw) to the root desktop. Post your .conkyrc and I'll see if I see anything that you might change. Also, in KDE right click the desktop and choose properties (I think - I'm doing this from memory as I don't have KDE installed anymore). Somewhere in there is a checkbox for show icons on the desktop and another one underneath that. I forget which one is the important one so uncheck them both and apply and then recheck them. then launch conky and it should look transparent. This is temporary and the next time you log in it will be back to black. There is a fix that involves setting the desktop wallpaper to the root desktop but I don't remember how to do that. I'll try and find it.

---

### Post by u-blunt-2 on 2007-03-06
Magnificent HowTo !
If only everyone with conky bugs could read this post first...:guitar:

Ive noticed that some flickering occurs even when dbe is loaded in XORG.conf
Check your conky display: sometimes certain process names are longer and make conky appear to flicker... I overcame this by making the width larger :)

---

### Post by m.musashi on 2007-03-06
Thanks. I can't take all the credit (but I'll take what I can get :)).

---

### Post by ubu_n00b69 on 2007-03-10
This is a Great How To!
Thank you very much for all of the time you spent on this, it really helped me out.

I have successfully Installed Conky on a AMD 3200+ w/an Asus AV31 Mobo, 768MB of DDR400 Ram with a Radeon RV200 Chipset.

Following the How To, Conky is installed on the Bottom Left of my Desktop.
How would I edit .conkyrc to move it to the Upper Right corner of the Desktop?

Thank you for all of your time.:)

---

### Post by m.musashi on 2007-03-10
In the .conkyrc look for this section
```
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none
```
Remove the # from the position you want and put a # in where you don't want it (that's a poor sentence I hope it makes sense). In the one above it will be position top right for example. There is also a "goto" option in this version of conky and was the main reason I wanted to install it. I haven't figured out exactly how it works. It seems to go by pixels but sometimes the numbers and positions don't seem to agree. Anyway, if you play around with it you can have more control over where conky draws. It's a bit of pain and a lot of trial and error but eventually I got what I wanted.

---

### Post by jseiser on 2007-03-12
I tried this on feisty and it said checkinstall package not found and wouldnt work.. Is their anything different to make this work on feisty?

---

### Post by m.musashi on 2007-03-12
I haven't tried this on feisty but if the "checkinstall" package is available in the feisty repos then I think it would work. Try
```
sudo apt-get install checkinstall
```
and see what happens. If it installs then try again with the conky install. If you get an error about not available or similar then it won't work. If it says it's already installed then I'm stumped. Of course, you can always finish the install with
```
sudo make install
``` but you won't have the luxury of simple uninstall but that may not be a big deal.

---

### Post by notwen on 2007-03-28
Is there any command to run so I can figure out which version of Conky I'm running?  Looking forward to trying this how-to when I get home.

---

### Post by m.musashi on 2007-03-28
> **notwen said:**
> Is there any command to run so I can figure out which version of Conky I'm running?  Looking forward to trying this how-to when I get home.

try
```
conky -v
```

---

### Post by notwen on 2007-03-28
Finally got my conky config to my liking, check out the screenshot [here]("http://www.notwen.org/img/screen_02.png").  Although conky seems to load immediately after my login screen.  I've made a startup script like you specified and it seems beryl covers up conky everytime.  I have the delay set all the way to 180, any suggestions?  When I add conky to my startup, am I adding the 'conky' command or ".conky_start.sh"?  Just wanting to make sure. =] Thanks again for the great how-to.

EDIT: After reboot I've noticed that all icons/folders on my desktop seem to disappear, but i can highlight them, but they will disappear again shortly there after. Any ideas what may be causing this and what I can do to correct it?

---

### Post by m.musashi on 2007-03-28
As long as beryl loads first you should be okay. If that isn't the case, post your .conkyrc and I'll see if I can see any problem. I take it from the screenshot you are are using gnome. Is that correct? If so, my guess is something in .conkyrc. Post it and I'll see.

---

### Post by notwen on 2007-03-29
> **m.musashi said:**
> As long as beryl loads first you should be okay. If that isn't the case, post your .conkyrc and I'll see if I can see any problem. I take it from the screenshot you are are using gnome. Is that correct? If so, my guess is something in .conkyrc. Post it and I'll see.

Yes, it's gnome+beryl+avant window navigator.  Here you go sir.  I'm thinking conky for some reason is loading immediately after me logging in, it pops up during the Loading Gnome, Nautilus, etc screen.    Once my desktop is done loading, conky is no longer on the screen.  I have to kill the conky process and restart conky once my desktop finishes loading, but doing this is hiding my desktop icons/folders.  

```
# conky config
# edited by notwen @ efnet

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 130 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 5

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes
#Note: doesn't work in conky 1.2 =(

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none


# Possible variables to be used:
#
#      Variable         Arguments                  Description                

# 	addr              (interface)   IP address for an interface
# 	acpiacadapter                   ACPI ac adapter state.                   
# 	acpifan                         ACPI fan state                           
# 	acpitemp                        ACPI temperature.                        
# 	adt746xcpu                      CPU temperature from therm_adt746x       
# 	adt746xfan                      Fan speed from therm_adt746x             
# 	alignr            (num)         Right-justify text, with space of N
# 	alignc                          Align text to centre
# 	battery           (num)         Remaining capasity in ACPI or APM        
# 					battery. ACPI battery number can be      
# 					given as argument (default is BAT0).     
# 	buffers                         Amount of memory buffered                
# 	cached                          Amount of memory cached                  
# 	color             (color)       Change drawing color to color            
# 	cpu                             CPU usage in percents                    
# 	cpubar            (height)      Bar that shows CPU usage, height is      
# 					bar's height in pixels                 
# 	cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
# 					CPU usage graph, with optional colours in hex,
# 					minus the #.
# 	downspeed         net           Download speed in kilobytes              
# 	downspeedf        net           Download speed in kilobytes with one     
# 					decimal                                  
# 	downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
# 					Download speed graph, colours defined in
# 					hex, minus the #.
# 	exec              shell command Executes a shell command and displays    
# 					the output in conky. warning: this      
# 					takes a lot more resources than other    
# 					variables. I'd recommend coding wanted   
# 					behaviour in C and posting a patch :-).  
# 	execbar           shell command Same as exec, except if the first value
# 					return is a value between 0-100, it
# 					will use that number for a bar.
# 					The size for the bar is currently fixed,
# 					but that may change in the future.
# 	execgraph         shell command Same as execbar, but graphs values
# 	execi             interval, shell command
#  					Same as exec but with specific interval. 
# 					Interval can't be less than              
# 					update_interval in configuration.        
#	font		  font		Specify a different font.  Only applies
#					to one line.
# 	fs_bar            (height), (fs)Bar that shows how much space is used on 
# 					a file system. height is the height in   
# 					pixels. fs is any file on that file      
# 					system.                                  
# 	fs_free           (fs)          Free space on a file system available    
# 					for users.                               
# 	fs_free_perc      (fs)          Free percentage of space on a file       
# 					system available for users.              
# 	fs_size           (fs)          File system size                         
# 	fs_used           (fs)          File system used space                   
# 	hr                (height)      Horizontal line, height is the height in 
# 					pixels                                   
# 	i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
# 					may be omitted if you have only one I2C  
# 					device. type is either in (or vol)       
# 					meaning voltage, fan meaning fan or
# 					temp/tempf (first in C, second in F)
# 					meaning temperature. n is number of the  
# 					sensor. See /sys/bus/i2c/devices/ on     
# 					your local computer.                     
# 	if_running        (process)     if PROCESS is running, display
# 					everything if_running and the matching $endif
# 	if_existing       (file)        if FILE exists, display everything between
# 					if_existing and the matching $endif
# 	if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
# 					if_mounted and the matching $endif
# 	else                            Text to show if any of the above are not true
# 	kernel                          Kernel version                          
# 	linkstatus        (interface)   Get the link status for wireless connections
# 	loadavg           (1), (2), (3) System load average, 1 is for past 1     
# 					minute, 2 for past 5 minutes and 3 for   
# 					past 15 minutes.                         
# 	machine                         Machine, i686 for example                
# 	mails                           Mail count in mail spool. You can use    
# 					program like fetchmail to get mails from 
# 					some server using your favourite         
# 					protocol. See also new_mails.            
# 	mem                             Amount of memory in use                  
# 	membar            (height)      Bar that shows amount of memory in use   
# 	memmax                          Total amount of memory                   
# 	memperc                         Percentage of memory in use
# 	
# 	metar_ob_time
# 	metar_temp
# 	metar_tempf                     Temp in F
# 	metar_windchill
# 	metar_dew_point                 There are a bunch of these
# 	metar_rh                        and they are self-explanatory
# 	metar_windspeed
# 	metar_winddir
# 	metar_swinddir
# 	metar_cloud
# 	metar_u2d_time
# 	
# 	ml_upload_counter               total session upload in mb
# 	ml_download_counter             total session download in mb
# 	ml_nshared_files                number of shared files
# 	ml_shared_counter               total session shared in mb, buggy
# 					in some mldonkey versions
# 	ml_tcp_upload_rate              tcp upload rate in kb/s
# 	ml_tcp_download_rate            tcp download rate in kb/s
# 	ml_udp_upload_rate              udp upload rate in kb/s
# 	ml_udp_download_rate            udp download rate in kb/s
# 	ml_ndownloaded_files            number of completed files
# 	ml_ndownloading_files           number of downloading files
# 	
# 	mpd_artist			Artist in current MPD song
# 					(must be enabled at compile)
# 	mpd_album			Album in current MPD song
# 	mpd_bar           (height)      Bar of mpd's progress
# 	mpd_bitrate                     Bitrate of current song
# 	mpd_status                      Playing, stopped, et cetera.
# 	mpd_title			Title of current MPD song
# 	mpd_vol				MPD's volume
# 	mpd_elapsed                     Song's elapsed time
# 	mpd_length                      Song's length
# 	mpd_percent                     Percent of song's progress
# 	new_mails                       Unread mail count in mail spool.         
# 	nodename                        Hostname                                 
# 	outlinecolor      (color)       Change outline color                     
# 	pre_exec          shell command Executes a shell command one time before 
# 					conky displays anything and puts output 
# 					as text.                                 
# 	processes                       Total processes (sleeping and running)   
# 	running_processes               Running processes (not sleeping),        
# 					requires Linux 2.6                       
# 	shadecolor        (color)       Change shading color                     
# 	stippled_hr       (space),      Stippled (dashed) horizontal line        
# 			(height)        
# 	swapbar           (height)      Bar that shows amount of swap in use     
# 	swap                            Amount of swap in use                    
# 	swapmax                         Total amount of swap                     
# 	swapperc                        Percentage of swap in use                
# 	sysname                         System name, Linux for example           
# 	offset            pixels        Move text over by N pixels
# 	tail              logfile, lines (interval)
# 					Displays last N lines of supplied text
# 					text file.  If interval is not supplied,
# 					Conky assumes 2x Conky's interval.
# 					Max of 30 lines.
# 					Max of 30 lines can be displayed.
# 	time              (format)      Local time, see man strftime to get more 
# 					information about format                 
# 	totaldown         net           Total download, overflows at 4 GB on     
# 					Linux with 32-bit arch and there doesn't 
# 					seem to be a way to know how many times  
# 					it has already done that before conky   
# 					has started.                            
# 	top               type, num     This takes arguments in the form:
# 					top <name> <number>
# 					Basically, processes are ranked from 
# 					highest to lowest in terms of cpu
# 					usage, which is what <num> represents.
# 					The types are: "name", "pid", "cpu", and
# 					"mem".
# 					There can be a max of 10 processes listed.
# 	top_mem           type, num     Same as top, except sorted by mem usage
# 					instead of cpu
# 	totalup           net           Total upload, this one too, may overflow 
# 	updates                         Number of updates (for debugging)        
# 	upspeed           net           Upload speed in kilobytes                
# 	upspeedf          net           Upload speed in kilobytes with one       
# 					decimal                                  
# 	upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
# 					Upload speed graph, colours defined in
# 					hex, minus the #.
# 	uptime                          Uptime                                   
# 	uptime_short                    Uptime in a shorter format               
# 	
# 	seti_prog                       Seti@home current progress
# 	seti_progbar      (height)      Seti@home current progress bar
# 	seti_credit                     Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT


${color slate grey}$nodename - $freq_dyn_g ghz
${color slate grey}linux $kernel

${color slate grey}uptime: ${color }$uptime

${color slate grey}cpu:${color } $cpu% 
${cpugraph 20,130 000000 ffffff}
${color slate grey}proc: ${color } $running_processes ${color slate grey}/${color }$processes
${color slate grey}load: ${color }$loadavg
${color slate grey}mem: ${color } $mem/$memmax 
${membar 3,100} $memperc%
${color slate grey}swap: ${color } $swap/$swapmax  
${swapbar 3,100} $swapperc%
${color slate grey}net: 
${color}down: ${color }${downspeed eth0}k/s${color}
${downspeedgraph eth0 20,130 000000 ffffff}
${color}up: ${color }${upspeed eth0} k/s
${upspeedgraph eth0 20,130 000000 ffffff}

```

---

### Post by m.musashi on 2007-03-29
Couple of thoughts.

1. Set own_window to yes ```
# Create own window instead of using desktop (required in nautilus)
own_window [color=red]yes[/color]
```
2. Did you make the addition to the xorg.conf file ```
load "dbe"
``` That is usually to solve a problem with flickering which you didn't mention but worth checking.

3. It sounds like conky is starting right away rather than after the 180 seconds you specified. The start script should load fairly quickly but the "sleep" part should cause it to do nothing for the specified amount of time (in seconds) during which time beryl should load and you'd be good to go. One thought is that there is something wrong with the start up script. Sorry to so it, but you could post that too? If that is not the case, I can't imagine why it would load right away.

4. As a test, try disabling the start up script and manually loading conky as soon as you can. Create a panel launcher for example. If it seems to load okay when you do that it would seem further evidence that the script is loading it before the desktop.

---

### Post by notwen on 2007-03-29
I'm currently at work, but will try all the recommendations you've given.  I did modify my xorg.conf and that did reduce flickering.  I'll be sure to post my start up script when i get home.  I'm thinking I added conky and not the start-up script to my startup apps.  I'll check when I get home and make the needed changes and let you know how all turns out. Thanks again. =]

---

### Post by notwen on 2007-03-29
Got everything working finally.  The "own_window yes" fixed the covering up of the icon/folders on the desktop and as for the startup issue, I had only added .conky_start.sh not including my home/user/ before that.   Thanks a ton for helping me out throughout the whole process, you've been a  great help. =]

---

### Post by m.musashi on 2007-03-29
My pleasure. Glad to hear it all worked out.

---

### Post by WiFi Ed on 2007-04-01
Thanks for posting this guide:) 

I was able to get conky up and running only after "conking" my head against the wall for a few hours, but your guide and the posts by other users made it all work in the end.

[[IMG]http://img218.imageshack.us/img218/6264/conkytz4.th.png[/IMG]](http://img218.imageshack.us/my.php?image=conkytz4.png)
I'll post my .conkyrc file if anyone wants it, but it's basically the one in the first post with a few additions and re-arrangements...

---

### Post by m.musashi on 2007-04-01
Glad to hear it was useful.

---

### Post by bengar on 2007-04-08
Hello Everyone 

** m.musash**  I followed all the instructions, After all, when I boot my pc the conky is showed, but very short time, then it disappear and can't see it anymore.  I restart the pc and the conky appear once again a short time with all the information when the pc is shutdown. How can I fix it  to stay  on my desktop all the time. Thank you.

---

### Post by m.musashi on 2007-04-08
This is generally caused by conky loading before your desktop. Are you using gnome or kde? A quick test is to either stop conky from auto loading and then wait until your computer finishes loading and then running conky from a terminal or alt-f2. If it doesn't disappear then it's just a problem with loading too quickly. If it does then something else is up. Another way to test would be to run
```
killall conky (might need to do sudo killall conky depending on how it started)
```
and then starting it manually.

If it seems fine after a manual start then make sure you set up the auto start script correctly at the end of the how to and have the correct command in the start up programs.

Go to menu: system->preferences->session->startup programs and enter the name of the script including the full path (such as /home/user/.conky_start.sh)

If this doesn't work, post back with a few more details such as gnome or kde and a copy of the start up script you are using. You can also try changing the delay to more than 10. If you computer is loading the desktop a bit slowly try 30 or 60 instead and see what happens. Also, when you check you don't have to reboot. Just hit ctrl-alt-backspace and your session will restart and you will get back to a login screen.

Hope that helps.

---

### Post by bengar on 2007-04-08
Thank you very much for you fast responce, as soon as possible when I return to my home I will tryed again with your instructions. By the way I am using gnome, and that are the symptoms, conky is loading before my desktop and turn off before all the system.

---

### Post by bengar on 2007-04-09
m.mushani, Thank you very much is working, just type
> sudo apt-get kill allconky
and now is working perfect.

---

### Post by m.musashi on 2007-04-09
> **bengar said:**
> m.mushani, Thank you very much is working, just type

and now is working perfect.

Well, glad to hear you got it working. However, the code you listed shouldn't do any anything. In order to kill conky it should be 
```
sudo killall conky
```
or if it is not started by root you can just use
```
killall conky
```

It sounds like it is loading too quickly. Edit your startup script to have a longer delay or don't auto start and just do it manually.

---

### Post by bengar on 2007-04-10
Yeap you are all correct that isn't the code, thank you the the correction, but I will new to modified my script, because the problem continue when startup my pc now. I will try again.

> bengar@bengar-desktop:~$ sudo killall conky
conky: no process killed
bengar@bengar-desktop:~$

---

### Post by m.musashi on 2007-04-10
That just means that conky isn't running. If it auto started but isn't running then there might be another issue here. However, if it just isn't running becuase you never started it or previously killed it then just do alt-f2 and type
[code]conky[/conky]
or you can run it from a terminal. If it runs fine then I'd say it's just the start up script not waiting long enough.

---

### Post by bengar on 2007-04-10
Okay now is running again,  thanks, again.

---

### Post by notwen on 2007-04-23
I have conky 1.4.5 installed w/o issue, but I'm having issues getting my audacious info to show up.  Could anyone explain to me how to get this to work?  I've noticed that it is not detecting audacious, do I need a certain version of audacious?  Here is my 'conky -v' output.

```
notwen@notnix-01:~$ conky -v
Conky 1.4.5 compiled Wed Jan 31 22:04:34 UTC 2007 for Linux 2.6.15.7 (i686)

Compiled in features:

 X11:
  * Xdamage extension
  * Xdbe extension (double buffer)
  * xft

 Music detection:
  * mpd

 General features:
  * hddtemp
  * portmon


```

and here is my conky config if it helps.

```
TEXT


${color slate grey}$nodename - $freq_dyn_g ghz
${color slate grey}linux $kernel

${color slate grey}uptime: ${color }$uptime

${color slate grey}cpu:${color } $cpu% 
${cpugraph 20,130 000000 ffffff}
${color slate grey}proc: ${color } $running_processes ${color slate grey}/${color }$processes
${color slate grey}load: ${color }$loadavg
${color slate grey}mem: ${color } $mem/$memmax 
${membar 3,100} $memperc%
${color slate grey}swap: ${color } $swap/$swapmax  
${swapbar 3,100} $swapperc%
${color slate grey}net: 
${color}down: ${color }${downspeed eth0}k/s${color}
${downspeedgraph eth0 20,130 000000 ffffff}
${color}up: ${color }${upspeed eth0} k/s
${upspeedgraph eth0 20,130 000000 ffffff}

${color slate grey}audacious: 
${color}$audacious_title
${color}${audacious_bar 3,100}
${color}$audacious_status - ${audacious_position}/${audacious_length}
```

---

### Post by m.musashi on 2007-04-23
I havn't used that feature before so I'm probably not much help. You might get more feedback if you post a new thread.

However, You might try looking at whether or not the brackets {} are needed. If you are just getting text on the screen (the text in your conkyrc) then it's probably a problem with formatting the code right. If you are getting something different then I'm not sure. Maybe posting a screen shot would help clarify.

---

### Post by notwen on 2007-04-23
Looks like it's just printing out straight text.  Here you go.
[-screenshot-]("http://www.notwen.org/img/uf_conky_audacious.png")

---

### Post by m.musashi on 2007-04-23
Hmmm, I thought maybe it was a formating problem but I'm not so sure. You could try and remove the {} but I'm thinking that won't help. Dumb question but is audacious running? Maybe it won't print anything if audacious isn't open.

---

### Post by notwen on 2007-04-24
> Compiling

For users compiling from source, make sure you have the X development libraries installed. This should be a package along the lines of "libx11-dev or xorg-x11-dev".

Gentoo users -- Conky is in Gentoo's Portage... simply use "emerge app-admin/conky" for installation. There is also usually an up-to-date ebuild within Conky's package or in Svn.

Debian,etc. users -- Conky will be in Debian's repositories soon (by mid-September, hopefully), and then Ubuntu shortly thereafter. Until then, "dpkg -i" the .deb package to install.

Example to compile and run Conky with all optional components (note that some configure options may differ for your system):

sh autogen.sh # Only required if building from Svn
./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-own-window --enable-proc-uptime **--enable-audacious** --enable-bmpx --enable-hddtemp --enable-mpd --enable-xmms2 --enable-imlib2 --enable-portmon --enable-debug --enable-double-buffer --enable-xdamage --enable-x11 


Just asked a forum user in another post who had it working in their screen shot and I was informed I have to enable this during compiling.  Will try this after work and post my results this afternoon.

---

### Post by notwen on 2007-04-24
All goes well until the ./configure command.  Here's my results torward the end of the ./configure command(w/ --enable-audacious) :

> checking for AUDACIOUS... configure: error: Package requirements (audacious >= 0.1) were not met:

No package 'audacious' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AUDACIOUS_CFLAGS
and AUDACIOUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

notwen@notnix-01:~/Desktop/conky-1.4.5$ make
make: *** No targets specified and no makefile found.  Stop.
notwen@notnix-01:~/Desktop/conky-1.4.5$ 


Any ideas/recommendations?  All I want is audacious info on my conky. =]

---

### Post by m.musashi on 2007-04-24
I didn't know about those configure options. Thanks for the info. However, I know that own_window, uptime and others in that list work without using the config options so I don't know if that means they are redundant or what.

As for your error, it seems to be saying a needed package is missing but only lists audacious itself. Unless you actually don't have it installed I don't see why it's complaining. You might need to install some dev packages for audacious. Try searching in synaptic for anything with lib at the beginning or dev at the end with relation to audacious. I wouldn't go randomly installing packages (although as long as you pay attention to changes it probably won't cause too many problems) but you might be able to find something that sounds good.

Sorry I can't be more help. I never tried what you are doing so I don't have any experience with it.

---

### Post by notwen on 2007-04-24
> You might need to install some dev packages for audacious. Try searching in synaptic for anything with lib at the beginning or dev at the end with relation to audacious.

First I have to have the -dev package installed, did so through synaptic, secondly I have to compile using the --enable-audacity option.  Worked w/ the guys in #conky on freenode to finally get this working.  Here is my final result. -[screenshot]("http://www.notwen.org/img/uf_working_aud.png")-

---

### Post by m.musashi on 2007-04-24
Nice work. Sorry I wasn't more help but thanks for the info. I'll have to edit the how-to. You should post that in the april desktop thread. It looks very nice.

---

### Post by violin on 2007-06-14
ok i follow your instruction it work when i start to ubuntu then after second it dissappears.  when i write conky on the terminal it gives me this.


[PHP]Conky: can't load font 'arial'
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hda1': No such file or directory
Conky: desktop window (c00061) is subwindow of root window (185)
Conky: window type - override
Conky: drawing to created window (2c00003)
Conky: drawing to double buffer

[/PHP]

---

### Post by m.musashi on 2007-06-15
You probably need to edit the .conkyrc file to match your system. You might not have drives mounted on /media/hda1 and so on.

Also, did you make the changes to the xorg.conf file? I think it's adding "load dbe".

Are you running kubuntu by chance? It causes a different set of problems.

---

### Post by Nessa on 2007-07-17
Nothing happened. No errors but conky still isn't on my desktop. :(

(I have compiz-fusion running if that matters.)

---

### Post by m.musashi on 2007-07-18
Since this version is now in the repo (if you use feisty) I would just install it that way. Conky might not run well if it's launched before loading compiz. You can post your .conkyrc and I can look it over and see if there are any obvious errors.

---

### Post by benhagerty on 2007-07-19
Need some help. When I go to run Conky it says that I am trying to use more CPUs than I have. I think it has to do with this ```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft no

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=9

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 3.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
# Use pseudo transparency with own_window?
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour #C0C8CD

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 3

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 35

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color black}$nodename $sysname $kernel on $machine
${color #C0C8CD}UpTime: ${uptime}   Load: ${loadavg}
${color black}$stippled_hr
${color black}CPU Usage: $cpu  %   CPU: ${freq}mhz ${alignr}Temp: ${acpitemp}
${color black}${cpugraph cpu0 000000 C0C8CD}
${color black} CPU0: ${cpu cpu1}% 
${color #C0C8CD}${cpubar cpu1} 
${color black} CPU1: ${cpu cpu2}% 
${color #C0C8CD}${cpubar cpu2}
${color black}Processes:${color #C0C8CD} $processes  ${color black}  Running:${color #C0C8CD} $running_processes

${color black}Name              PID     CPU%   MEM%
${color blue} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #C0C8CD} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #C0C8CD} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #C0C8CD} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color black}Mem usage
${color blue} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #C0C8CD} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #C0C8CD} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color black}$stippled_hr
${color black}RAM:     ${color #C0C8CD}$memperc% ${membar}
${color black}Swap:     ${color #C0C8CD}$swapperc% ${swapbar}

${color black}Root:     ${color #C0C8CD}${fs_size /} - ${fs_free_perc /}% free   ${fs_bar /}
${color black}Home:    ${color #C0C8CD}${fs_size /home} - ${fs_free_perc /home}% free   ${fs_bar /home}
${color black}$stippled_hr
${color black}Networking: ${color #C0C8CD}(${addr eth1})
${color black} Down:${color #C0C8CD} ${downspeed eth1} k/s${color black} ${alignr}Up:${color #C0C8CD} ${upspeed eth1} k/s
${color black}${downspeedgraph eth1 32,125 C0C8CD 0000ff} ${alignr}${color black}${upspeedgraph eth1 32,125 C0C8CD ff0000}
${color black}$stippled_hr
```
So what should I change it to?

---

### Post by m.musashi on 2007-07-20
> **benhagerty said:**
> Need some help. When I go to run Conky it says that I am trying to use more CPUs than I have. I think it has to do with this So what should I change it to?

What sort of CPU do you have? This .conkyrc is for a dual core. If that's what you have then I'm not sure why you are getting that error. If you have a single core cpu then that's probably way. You will need to remove all the stuff about cpu0 and cpu1 and just use cpu (i think).

---

### Post by Predatorian on 2008-06-22
hi, i followed your tutorial and entered all the code in, but for some reason, ubuntu on my laptop, just doenst like conky. if i do the apt-get or aptitude install, it give me an error, and if i compile from source, it just doesnt run at all. when i had plain debian, it worked just fine with fluxbox as my desktop manager. any help or ideas?

---

### Post by hype on 2008-06-22
Predatorian,
the thread you are reading was written in July 2007.
Conky is now at version 1.5.1 on Ubuntu hardy.

You have many .conkyrc and screenshots on this thread :
[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

---

### Post by metalmaniac248 on 2009-02-17
i have followed the instructions on the origonal guide at thhe start of this thread, but i can only see conky when im in the skydome cube rotate thing, but not when im just on my desktop,

any ideas?  

PS. could this be anything to do with the fact that compiz is drawing my desktop not nautilus?

---

### Post by metalmaniac248 on 2009-02-19
problem solved just had to fidle with a few of the settings

---

### Post by juil on 2010-08-31
Hi guys, completely new to conky.
When I installed conky, I had no idea i had to RUN it and that 
it wouldn't be in the menus...

EDIT: Ok, such a noob question. How do you close conky?

---

### Post by Bugs318 on 2010-10-02
I had a slightly different problem in Lucid (where battery bar won't work from repos, only if installed from source), but even if I pin the source install afterwards any upgrade reinstalls the repo versions and the battery bar stops working again.

Does anyone know how I can make the source-install not upgrade from the repos?

Thanks in advance!!!

---

### Post by Fourty-Two on 2010-11-24
Great guide, very clear and stuff :)

It still won't work for me though, and when I tried running in the terminal I got this:

```
~$ Conky: /home/laurens/.conkyrc: 82: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: desktop window (22000a9) is subwindow of root window (c9)
Conky: window type - override
Conky: drawing to created window (0x4a00001)
Conky: drawing to double buffer
Conky: obj->data.i 2 info.cpu_count 1
Conky: attempting to use more CPUs than you have!

```I know this probaply means I don't have enough CPU (or maybe, because it was designed for a dualcore it doesn't work). It's a strange idea that my 3.2 GHz processor could handle games like KotOR, but not handle the "lightweight system monitor" software, so I guess it's the dualcore problem. What should I edit?
By the way, the rest of the output doesn't seem very encouraging either... though it does seem like the designer had some humor. "use_spacer should have an argument of left, right, or none. 'no' seems to be some form of 'false', so defaulting to none" :P

Anyway, before making my first post any more disastrous and embarrassing and stuff, any advice on this?

Edit: Nevermind, I now know what I did wrong and it's such a dumb error I'm even more embarrassed of my first post here. I kept editing the file .conkeyrc, but of course I had to edit .conkyrc. So I'd been changing the wrong config. Fail....

---

