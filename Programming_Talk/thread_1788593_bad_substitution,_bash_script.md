---
title: ": bad substitution, bash script"
date: 2011-06-22
forum: Programming Talk
---

### Post by slashwannabe94 on 2011-06-22
Hello all, 

I'm trying to write a script to install conky and check if .conkyrc exists, if not then append the code to the ~/.conkyrc file. But when i run this part of the script i receive the error " :bad substitution" Here is my code. 

```
echo "Checking if .conkyrc exists..."      
if [ -f .conkyrc ]; then
    echo ".conkyrc exists and is executable!"
    exit
else
    clear
    echo ".conkyrc does not exist, would you like to create it?"
fi

echo "Enter yes to create .conkyrc"
echo "Enter no to exit the program"
read choice
case $choice in
   yes) cat <<EOF > ~/.conkyrc;
# sTaTiC's .conkyrc
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer true
use_xft true

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase yes  # set to yes if you want all text to be in uppercase

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
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 50

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color #ddaa00}${time %a, } ${color }${time %e %B %G}
${offset 240}${color #ddaa00}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color #ddaa00}UpTime: ${color }$uptime
${offset 240}${color #ddaa00}Kern:${color }$kernel
${offset 240}${color #ddaa00}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 #ddaa00}
${offset 240}${color #ddaa00}Load: ${color }$loadavg
${offset 240}${color #ddaa00}Processes: ${color }$processes  
${offset 240}${color #ddaa00}Running:   ${color }$running_processes

${offset 240}${color #ddaa00}Highest CPU Processes:
${offset 240}${color lightgrey} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color #ddaa00}Highest RAM Processes:
${offset 240}${color lightgrey} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color #ddaa00}RAM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color #ddaa00}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color #ddaa00}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color #ddaa00}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}

#ppp0 interface graphs
${offset 240}${color #ddaa00}NET PPP0: 
${offset 240}${color}Up: ${color }${upspeed ppp0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed ppp0}k/s${color}
${offset 240}${downspeedgraph ppp0 20,130 000000 ffffff}

#wlan0 interface graphs
${offset 240}${color #ddaa00}NET WLAN0:
${offset 240}${color}Up: ${color }${upspeed wlan0} k/s
${offset 240}${upspeedgraph wlan0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed wlan0}k/s${color}
${offset 240}${downspeedgraph wlan0 20,130 000000 ffffff}

#mon0 interface graphs
${offset 240}${color #ddaa00}NET MON0:
${offset 240}${color}Up: ${color }${upspeed mon0} k/s
${offset 240}${upspeedgraph mon0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed mon0}k/s${color}
${offset 240}${downspeedgraph mon0 20,130 000000 ffffff}

#eth0 interface graphs
${offset 240}${color #ddaa00}NET ETH0:
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
EOF
esac


```

thanks 
SlashWannabe94

---

### Post by slashwannabe94 on 2011-06-22
Any pointers on how to make my code more readable please share. I'm still developing my own style of coding and would appreciate some veteran tips. 
thanks
SlashWannabe94

---

### Post by gmargo on 2011-06-23
You're getting "bad substitution" from nearly every dollar sign in the text.

If the here-document delimiter (EOF in this case) is quoted, then the
here-doc text is treated literally.  If unquoted, then the text is subject to
parameter expansion, command substitution and arithmetic expansion.

So change:
cat <<EOF

to:
cat <<'EOF'

---

### Post by geirha on 2011-06-23
+1 on gmargo's answer.

On the rest of the script, first of all, you're missing the most important line, the shebang. 

Secondly, at the start you're testing if the file .conkyrc exist, but later on you attempt to write to ~/.conkyrc. The two filenames point to the same file if you happen to run the script from your homedir, but from any other dir, the script won't do what you expect.

I recommend reading the [BashGuide](http://mywiki.wooledge.org/BashGuide) to learn bash's syntax and good scripting practices.

---

### Post by Martin Witte on 2011-06-23
I would recommend to use commands according to syntax, your use of the case switch works, but is not as it is supposed to be, a correct example of your logic would be:

```

read choice
case "$choice" in
   yes) echo 'yes entered' 
        ;;
   no)  echo 'no entered'
        ;;
   *)   echo 'invalid input entered'
        ;;
esac
```
For more examples see some [documentation]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_03.html")

---

### Post by geirha on 2011-06-23
> **Martin Witte said:**
> 
For more examples see some [documentation]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_03.html")

Ah, the closing ;; was missing. I completely missed that. 

Though, the TLDP bash guides are outdated and littered with bad practice as usual. Parsing df -h output, piping together awk and grep, failing to quote parameter expansions and sh-extension on a bash script are the bad practices I spotted right away. I recommend referring to the BashGuide at the wooledge wiki instead. 

[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Choices_.28case_and_select.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Choices_.28case_and_select.29)

---

### Post by slashwannabe94 on 2011-06-23
Quoting EOF worked :) thanks so much guys, you helped me out here. I will refer to the bash guide for anymore problems i may run into. 

Many thanks, 
SlashWannabe94

---

### Post by slashwannabe94 on 2011-06-23
> **Martin Witte said:**
> I would recommend to use commands according to syntax, your use of the case switch works, but is not as it is supposed to be, a correct example of your logic would be:

```

read choice
case "$choice" in
   yes) echo 'yes entered' 
        ;;
   no)  echo 'no entered'
        ;;
   *)   echo 'invalid input entered'
        ;;
esac
```For more examples see some [documentation]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_03.html")

Will this suffice? 
```
read choice1
case $choice1 in
   yes) echo "Installing conky..."
        sudo apt-get install conky 
        echo "Conky has been installed"
        ;;
   no)  echo "no selected, exiting program now!"
        sleep 5
        exit;;
   *)   echo "Invalid option selected, leaving program now!"
        exit
        ;;
esac  
```

---

