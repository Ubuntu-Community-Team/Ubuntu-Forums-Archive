---
title: "Searching my files?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by jimi_hendrix on 2008-07-23
hi

so i recently downloaded conky.  It works perfectly (except for the upload download speed meter if u know why this may be please reply :)) but i read that you could add a weather forcast to it and was directed to this forum post

[http://ubuntuforums.org/showthread.php?t=760527]("http://ubuntuforums.org/showthread.php?t=760527")

i already had python installed on my machine coincidentally without knowing that it powered conky so when i got to step 2 and it asked me to extract the fonts to the desktop i didnt know where the python file was saved so i opened up my home folder, clicked the search button, and no program files or font files came up yet if i click on the applications menu and go down to the programming thing i see "python (2.5)"

what do i do to find where the fonts/program file is saved

---

### Post by stevoo on 2008-07-23
Most probably you need to edit the conky script a bit and set your own Ethernet or wireless there.
if you do not now which one it is you can find it by opening the terminal and typing ifconfig
a  list will appear find the one with an IP and select that ethernet that will be on the site, perhaps it will be something like
eth1 or eth0

so open a terminal and write :
gedit conkyrc

This will open up the text editor 
scroll down until you see this :
```
${color orange}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1 
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
```
or something like that.

We have you network card now, so just fill in where it says eth1, or eth0 with your one. If you still have trouble post your conkyrc here and the results of your ifconfig 

sTevoo

---

### Post by stevoo on 2008-07-23
:) I didnt read the whole post :) But that still may help you with the network

On your matter :
most probably if you copy pasted the command 
the file should be in here
home/<your account>/.fonts/
the . before makes it hiden folder

---

### Post by jimi_hendrix on 2008-07-23
> **stevoo said:**
> :) I didnt read the whole post :) But that still may help you with the network

On your matter :
most probably if you copy pasted the command 
the file should be in here
home/<your account>/.fonts/
the . before makes it hiden folder

went there the folder was empty

---

### Post by jimi_hendrix on 2008-07-23
> **stevoo said:**
> Most probably you need to edit the conky script a bit and set your own Ethernet or wireless there.
if you do not now which one it is you can find it by opening the terminal and typing ifconfig
a  list will appear find the one with an IP and select that ethernet that will be on the site, perhaps it will be something like
eth1 or eth0

so open a terminal and write :
gedit conkyrc

This will open up the text editor 
scroll down until you see this :
```
${color orange}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1 
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
```
or something like that.

We have you network card now, so just fill in where it says eth1, or eth0 with your one. If you still have trouble post your conkyrc here and the results of your ifconfig 

sTevoo

ok heres the stuff...

result of ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1e:33:41:75:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:36332532624 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:33:41:75:22  
          inet addr:169.254.3.198  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:251 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123880 (120.9 KB)  TX bytes:123880 (120.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:a9:b1:6d  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fea9:b16d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3790148 (3.6 MB)  TX bytes:584846 (571.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-A9-B1-6D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

my conky script which i so totally ripped from some guy's forum post (i can do little more then declare variables in python :))

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed wlan0} k/s
${offset 240}${upspeedgraph wlan0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed wlan0}k/s${color}
${offset 240}${downspeedgraph wlan0 20,130 000000 ffffff}
```

NOTE: i changed all eth0 in theres to wlan0

---

### Post by stevoo on 2008-07-23
your conky script seems correct you do have wlan0 -> wirelless so it should be working .... 
try restarting it and see
in a terminal type : 
kill conky
conky

Now for the fonts, perhaps you didnt copied them. 
Check your desktop are they there ? if not try donwloading it again and re copying it and check what ttf files you have first in the directory before copying to make sure you have something.

---

### Post by jimi_hendrix on 2008-07-23
```
bash: kill: conky: arguments must be process or job IDs
```

i get when i do that

---

### Post by stevoo on 2008-07-23
my bad there 
pkill conky

---

### Post by jimi_hendrix on 2008-07-23
but that doesnt matter it now works and thats all i need...now to find those fonts :)

---

### Post by stevoo on 2008-07-23
So i found the fonts ... try redownloading them again. 
Have them on the desktop
go to the command prompt
you should be here
/home/account nam/Desktop/
On the extract it extracts everything in a folder 
the folder was named Fonts
so 
```

cd Fonts
cp ~/Desktop/*.ttf ~/.fonts/ && fc-cache -f -v

```
try this .... and see ! most pobably you didnt copy anything the first time

---

### Post by jimi_hendrix on 2008-07-23
in /home/vincent/.fonts i see nothing so i cannot move them to my desktop folder

---

### Post by stevoo on 2008-07-23
it should be the other way around

[http://ubuntuforums.org/attachment.php?attachmentid=74412&d=1213737106](http://ubuntuforums.org/attachment.php?attachmentid=74412&d=1213737106) 

Download that file at the desktop.
Go there and select extract here.
It should extract it on a folder name Fonts

go to the command prompt
you should be here
/home/account nam/Desktop/
On the extract it extracts everything in a folder
the folder was named Fonts
so
Code:

cd Fonts
cp ~/Desktop/*.ttf ~/.fonts/ && fc-cache -f -v

---

### Post by jimi_hendrix on 2008-07-23
```
 vincent@vincent-laptop:~$ cd ~/Desktop
vincent@vincent-laptop:~/Desktop$ cd ~/Desktop/Fonts
vincent@vincent-laptop:~/Desktop/Fonts$ cp ~/Desktop/*.ttf~/.fonts/&& fc-cache -f-v
cp: missing destination file operand after `/home/vincent/Desktop/*.ttf~/.fonts/'
Try `cp --help' for more information.

```

i got that

and ty for your patients

---

### Post by unutbu on 2008-07-23
Try 
```

cp ~/Desktop/*.ttf ~/.fonts/ && fc-cache -f-v

```
(you were missing a space).

PS. To find files by name on your system, type

```

find / -type f -name "Fonts*" -print
```
This will search your entire filesystem starting at root (/). This can take many seconds. To search only your home directory, 

```

find $HOME -type f -name "Fonts*" -print
```

Change Fonts* to the name of the file you are searching for. (find understands *, the wildcard character).

PPS. Suggestion (for firefox): click Edit>Preferences. click the Main tab. Enable the "Always ask me where to save files" button. This way you'll get an explicit message about where firefox is about to download a file.

---

### Post by jimi_hendrix on 2008-07-24
```
cp: cannot stat `/home/vincent/Desktop/*.ttf': No such file or directory

```

i pasted what u said and got

---

### Post by unutbu on 2008-07-24
Ok, this means you have no ttf files in your Desktop directory.

What do you get when you type

```
ls -l $HOME/Desktop/Fonts*
```

(This will check if the Fonts.tar.gz file is in Desktop). If it isn't then try

```
find $HOME -type f -name "Fonts*" -print
```

This will search your entire home directory (/home/vincent) for any file starting with 'Fonts'

---

### Post by jimi_hendrix on 2008-07-24
for the first one i got ```
-rw-r--r-- 1 vincent vincent 18921 2008-07-23 21:17 /home/vincent/Desktop/Fonts.tar.gz

/home/vincent/Desktop/Fonts:
total 4
drwx------ 2 vincent vincent 4096 2008-06-03 05:12 Fonts (2)


and the second one

[CODE]/home/vincent/Desktop/Fonts.tar.gz

```

---

### Post by unutbu on 2008-07-24
Copy and paste this into a terminal

```
cp ~/Desktop/Fonts/Fonts\ \(2\)/*.ttf ~/.fonts/ && fc-cache -f -v
```

---

### Post by jimi_hendrix on 2008-07-24
ok what did that do it worked :)

---

### Post by unutbu on 2008-07-24
If you open up a nautilus window and navigate to Desktop, you'll see a directory called
Fonts. Go inside that directory, and you'll see another directory called "Fonts (2)".
Your ttfs are inside there. The command
```

cp ~/Desktop/Fonts/Fonts\ \(2\)/*.ttf ~/.fonts/
```

copies those ttfs to a directory called ~/.fonts. The crazy backslashes are there to "protect" the spaces and the parentheses from being eaten up by bash.

The "fc-cache -f -v" command makes the new ttf fonts accessible for the rest of the system.

You are free to delete the Fonts directories from your Desktop now that you have the ttf files installed in ~/.fonts.

---

### Post by jimi_hendrix on 2008-07-24
thanks the rest of that page is equally confusing but thats for a different post and not ur job to answer

---

