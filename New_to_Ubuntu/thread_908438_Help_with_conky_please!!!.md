---
title: "Help with conky please!!!"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by 71CH on 2008-09-02
Hi all
I borrowed a conky setup from the "Post your conky" thread and I have a couple of issues with it.  I have it set up for the bottom right hand corner.  As you can see in the screen it's pretty much flush with the right hand side but there's a slight gap between the conky and the bottom of the screen.  How can I "lower" the conky so that it's closer to the bottom?  Also, in the screen you can see that the right hand side of conky has some dots and lines.  This happens when the numbers get larger and smaller and the conky expands and shrinks.  Any way to not have those dots and lines?  BTW, since I borrowed this conky I don't really know what "Quality" means.  Any idea?  Thanks for any help guys!

```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type override

# Minimum size of text area
minimum_size 250 5
maximum_width

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black
color1 white #00FF00
color2 white #EEAA00
color3 white #9933FF

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 40

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
none

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#  Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               



# blue color ${color 246eb5}

# stuff after 'TEXT' will be formatted on screen

TEXT
Down:${color green}${downspeedf wlan0} Kb/s$color	${goto 145}Up: ${color red}${upspeedf wlan0} Kb/s$color 	${goto 280}CPU Temp: ${color orange}${acpitemp}°C${color} 
${downspeedgraph wlan0 10,110 00FF00 00FF00 100}	${goto 145}${upspeedgraph wlan0 10,110 FF0000 FF0000 100} 	${goto 280}Quality:   ${color 78e6e4}${wireless_link_qual_perc wlan0} %${color}
CPU1: ${cpu cpu1}% ${freq_g} GHz 			${goto 145}CPU2: ${cpu cpu2}% ${freq_g} GHz  			${goto 280}RAM: $memperc% ${mem}
${cpubar cpu1 5,110}					${goto 145}${cpubar cpu2 5,110} 				${goto 280}${membar 5,110}
${exec acpi -b}
${exec cat /proc/cpuinfo | grep 'model name' | sort -u | cut -c 14-59} | Uptime: $uptime
```

---

### Post by unutbu on 2008-09-02
To move the conky closer to the bottom edge, set 
```

gap_y to 10
```

gap_y is the number of pixels from the bottom edge. (See [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html))

I am running conky with your posted .conkyrc, but I have not been able to reproduce the dots and lines. In your attached png I see them on the left-hand side, but in your post you say you see them on the right-hand side? Anyway, this may or may not work since I can't reproduce the problem, but you might want to try setting
```

use_spacer yes
```

use_spacer seems to add/adjust some space between the text strings. Maybe by keeping the bottom text line from shrinking you can avoid the ghosting problem.

[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html) says the argument following use_spacer should be left, right or none, but on my system 'yes' also has an effect on conky that does not correspond to left, right or none. So you might want to try them all to see what works for you.

Quality I believe refers to the quality of the wireless signal from the adapter to the router. You might also see that number in the output of "iwlist scan".

If you search the .conkyrc for the word quality, you'll find that the number being displayed is controlled by the wireless_link_qual_perc variable.
For more info on variables you can use, see [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

Another setting that you might want to play with is border_margins and border_width.
I had to set 
```

border_margin 10
```

to prevent the right-side RAM bar from getting chopped off.

Finally, you might want to comment out 
```

# on_bottom yes
```

and
```

# maximum_width
```

At least on my version of conky (and in the on-line documentation) there are no such options.

---

### Post by 71CH on 2008-09-02
Hey
Thanks for your help!  I think it's working so far.  And yea I meant to say dots and lines on the left side.  Can you help me with one more thing?  How can I line up the Battery Info with the left side?  Thanks.

---

### Post by unutbu on 2008-09-02
Near the bottom of the ~/.conkyrc, change 

```
${exec acpi -b}
```

to

```
${exec acpi -b | sed -e 's/^\ *//'}
```

---

### Post by 71CH on 2008-09-02
Thanks again!

---

### Post by 71CH on 2008-09-02
Uh oh.  The problem with the dots and lines on the left side got worse. A little help please :)

---

### Post by 71CH on 2008-09-02
Bump

---

### Post by unutbu on 2008-09-02
The screenshot you posted has a width of about 510 pixels.
Your ~/.conkyrc has 
```

minimum_size 250 5
```

So this means conky is free to resize the image down to 250 pixels wide if it can.
Perhaps if you increase 250 to say 510
```

minimum_size 510 5
```

maybe the problem will be prevented?

---

