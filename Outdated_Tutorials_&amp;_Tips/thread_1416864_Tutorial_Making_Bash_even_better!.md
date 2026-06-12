---
title: "Tutorial: Making Bash even better!"
date: 2010-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Camaguey on 2010-02-26
I wanted to share some simple bash customizations that can improve functionality and awesomeness. 
All changes can be undone by deleting the added text or commenting out a line
These edits can be safely **appended (**do not overwrite!) to your ~/.bashrc file, but only change that one file:
For best results, add your own customizations to taste.
```

#########################
#Various Edits:
#########################
#This changes what the terminal displays before the cursor
export PS1="GLaDOS, "
#bash remembers the last 3000 commands
export HISTFILESIZE=3000

# Define a few Color's
BLACK='\e[0;30m'
BLUE='\e[0;34m'
GREEN='\e[0;32m'
CYAN='\e[0;36m'
RED='\e[0;31m'
PURPLE='\e[0;35m'
BROWN='\e[0;33m'
LIGHTGRAY='\e[0;37m'
DARKGRAY='\e[1;30m'
LIGHTBLUE='\e[1;34m'
LIGHTGREEN='\e[1;32m'
LIGHTCYAN='\e[1;36m'
LIGHTRED='\e[1;31m'
LIGHTPURPLE='\e[1;35m'
YELLOW='\e[1;33m'
WHITE='\e[1;37m'
NC='\e[0m'              # No Color
# Sample Command using color: echo -e "${CYAN}This is BASH
#${RED}${BASH_VERSION%.*}${CYAN} - DISPLAY on ${RED}$DISPLAY${NC}\n"

# Source global definitions
if [ -f /etc/bashrc ]; then
    . /etc/bashrc
fi

# enable programmable completion features
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# Alias's to modified commands, the fun part
alias home='cd ~'
alias ping='ping -c 5'
alias openports='netstat -nape --inet'
alias ns='netstat -alnp --protocol=inet | grep -v CLOSE_WAIT | cut
-c-6,21-94 | tail +2'
alias la='ls -Al'               # show hidden files
alias ls='ls -aF --color=always' # add colors and file type extensions
alias lx='ls -lXB'              # sort by extension
alias lk='ls -lSr'              # sort by size
alias lc='ls -lcr'      # sort by change time
alias lu='ls -lur'      # sort by access time
alias lr='ls -lR'               # recursive ls
alias lt='ls -ltr'              # sort by date
alias lm='ls -al |more'         # pipe through 'more'
#the next edit requires mplayer and a song, but it let's you play music in bash! 
alias sing='mplayer -really-quiet ~/Music/"Theme Songs"/"Still Alive - Theme Songs.mp3"'
#a very useful alias when working on this file. nano can be substituted for gedit, etc. 
alias editbash='nano ~/.bashrc'
#update and upgrade in one command
alias upgrade='sudo apt-get update && sudo apt-get -y upgrade'

#alias for lynx. requires lynx, let's you browse websites in bash
alias nytimes='lynx -term=vt100 http://nytimes.com'
alias mail='lynx -term=vt100 http://gmail.com'
# NOTES
#######################################################
# To temporarily bypass an alias, we precede the command with a \
# eg. the ls command is aliased, but to use the normal ls command you would
# type \ls
#######################################################
```I can guarantee the functionality of all these edits, but I am not the sole author. Some are from [http://www.novell.com/coolsolutions/tools/17142.html](http://www.novell.com/coolsolutions/tools/17142.html)
Post your own edits

---

### Post by Camaguey on 2010-02-27
[FONT=Courier New]After six hours of tweaking I've finally managed to get bash to 1)play the portal theme song 2)print the lyrics slowly 3 AND 3)print the aperture logo!
```

alias sing='mplayer -really-quiet ~/Music/"Theme Songs"/"Still Alive - Theme Songs.mp3" < /dev/null & echo -n "T" && sleep .05 && echo -n "h" && sleep .08 &&  echo -n "i" && sleep .05 && echo -n "s" && sleep .05 && echo -n " " && sleep .05 && echo -n "w" && sleep .1 && echo -n "a" && sleep .1 && echo -n "s" && sleep .03 && echo -n " " && sleep .05 && echo -n "a" && sleep .1 && echo -n " " && sleep .1 && echo -n "t" && sleep .1 && echo -n "r" && sleep .1 && echo -n "i" && sleep .1 && echo -n "u" && sleep .1 && echo -n "m" && echo -n "p" && sleep .1 && echo "h" && sleep 4.3 && echo "

                  .,-;;//;\=,. 
               . 1H@@@MM@M#H/ ,+;,
            ,/X+ +M@@M@MM% ,-%HMMM@X/,  
          -+@MM; SM@@MH+- ;XMMMM@MMMM@+-
         ,@M@@M- XM@X;. -+XXXXXHHH@M@M.--.    
        ,%MM@@MH ,@%=            ..--=-=;=,.
        +@#@@@MX .,              -%HXSS%%%+; 
       =; .@M@M$                  .;@MMMM@MM;
       X@= -#MM/                    .+MM@@@M#;
      ,@M@H; ;@1                     . =X#@@@@
      ,@@@MMX, .                    /H- ;@M@M=
      .H@@@@M@+,                    %MM+. %#$.
       /MMMM@MMH\.                  XM@MH; =;
        /%+%SXHH@#=              , .H@@@@MX,
         .,,.,,..,,,           -%H ,@@@@@MX,  
          %MM@@@HHHXM++;;-- .;SMMX =M@@MM%. 
           =XMCAMAMAGUEY ,-+HMM@M+ /MMMX=
             =%@M@M#@S .=#@MM@@@M; %M%=
               ,;+#+- /H#MMMMMMM@= =,
                 --. =++%%%%+/;-.
"'

```
:popcorn:

[/FONT]

---

### Post by Deadite81 on 2010-03-01
Here's mine. I added lots of comments to explain things!
Also, it seems the more aliases and features you pile on top of gnome-terminal
the slower it loads, so just put stuff in there you actually need!
I usually add stuff that is super convenient or super long but useful all the same.
And some are there out of pure laziness;)

```

#File saved in ~/.bash_aliases
#it is possible, in ubuntu 9.10 anyway, 
#to save your aliases here istead of .bashrc

# More cool commands can be found here: http://www.commandlinefu.com/
# Many of these commands came from there!

#File management shortcuts

# add colors and file type extensions
alias ls='ls -aF --color=always' 

#checkout the file system!
alias topfiles="watch -d -n 2 'df; ls -FlAt;'" 

# Navigate up the directory using cd followed by number 
# (i.e. cd4 goes back 4 directories)
alias cd1="cd .."
alias cd2="cd ../.."
alias cd3="cd ../../.."
alias cd4="cd ../../../.."
alias cd5="cd ../../../../.."

# Apt shortcuts 

# Install repo key (add last 8 digits of key)
alias apt-key="sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys " 

# add "package name" to install a package
alias install="sudo apt-get install " 

# add "package name" to remove a package and it's configuration files
alias purge="sudo apt-get purge " 

# add "package name" to remove a package (but keep it's config files)
alias remove="sudo apt-get install --remove " 

# edit souces file
alias sources="gksu gedit /etc/apt/sources.list" 

# update package database as well as install all availible package updates
alias upgrade='sudo apt-get update && sudo apt-get -y upgrade' 


#List cron jobs (enabled and not enabled)
alias lscron="ls /etc/cron*" # list cron jobs 


 # Show disk drives UUIDs
alias uuid="sudo blkid"

# Show hard drive's current temperature (you may need to change the hdd location and must have hddtemp installed, of course)
alias temp="hddtemp /dev/sda" 


#Network shortcuts

# Show mac addresses
alias mac="ifconfig -a| grep -o -E '([[:xdigit:]]{1,2}:){5}[[:xdigit:]]{1,2}'"  

# View programs using an internet connection
alias ports="lsof -i -n -P"        

# View only established sockets
alias estab="ss -p | grep STA"        

# View open ports
alias openports="netstat -nape --inet"

# Lists all listening ports together with the PID of the associated process
alias netpid="netstat -tlnp"        

# View only the process name using an internet connection   
alias appson="netstat -lantp | grep -i stab | awk -F/ '{print $2}' | sort | uniq"   

 # View network device info
alias network="sudo lshw -C network"   

# View DNS numbers
alias dns="cat /etc/resolv.conf"    

# List your device's transfer info (you may need to change your device, and you must have tcptrack installed)
alias tcptrack="sudo tcptrack -i wlan0"    

# NOTE: I've modified netstat to not require sudo. It is much easier to use it with conky and,
# for that matter, from the shell. You must add 'sudo' if you want the netstat aliases to function
# propperly without modifying the permissions.  The same goes for the hddtemp alias.


# Record the desktop (saving to /tmp/out.mpg, which may be changed to whatever)
# This can be quite cpu intensive, slower boxes be wary...
alias record="ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq /tmp/out.mpg"


# This command will dowload a webpage to your hdd in a folder named after the page you are downloading.
# This folder will be saved in the directory from which you run the command.
# Cool for tinkering with other people's designs in various ways. Be warned, however, that websites can be quite huge.
# This incluses everything...images, etc. change parameters (-p) for something different
# Stop it at any time with <ctrl c>
# Add this to limit dl rate "--limit 20k" (no quotes, where as '20' can be whatever)
# Add this to log output to specific file "-o $HOME/wget_log.txt" (no quotes, change to wherever you like, as long as you have permission!)

alias dlwebpage="wget --random-wait -r -p -e robots=off -U mozilla http://" 
#i.e. "dlwebpage www.webpage.com"

```

---

### Post by Camaguey on 2010-03-02
Thanks for mentioning bash_aliases, and the 'install' alias is definitely going in my bash.

---

### Post by dragonboss on 2010-03-03
Please add screenshots of your bashes(is this correct?)

---

### Post by Camaguey on 2010-03-04
I'd say "terminals" but whatever works :p
[[URL=http://s93.photobucket.com/albums/l73/jackknife777/?action=view&current=Screenshot-1-1.png][IMG]http://i93.photobucket.com/albums/l73/jackknife777/Screenshot-1-1.png?t=1267682113[/IMG]]("http://s93.photobucket.com/albums/l73/jackknife777/?action=view&current=Screenshot-1-1.png")
[/URL]

---

### Post by Deadite81 on 2010-03-04
[http://img97.imageshack.us/img97/3872/screenshot008l.png](http://img97.imageshack.us/img97/3872/screenshot008l.png)

---

### Post by Deadite81 on 2010-03-04
Another cool function of bash is bash scripts.

You can use these for all sorts of stuff.

You could create a startup script for the iptables gui firestarter.
Not only that, but you can make it start minimized in the system tray!
Fire up your favorite text editor and type
```

#!/bin/bash
sleep 45 && sudo firestarter --start-hidden;

```These scripts always start with a [COLOR=Red]she-bang[/COLOR]&quot;#!&quot; which indicates the file is a script and should be executed by /usr/bash.

Next is your command, just like you would enter in your terminal:

&quot;sleep 45&quot; makes it wait 45 seconds before loading the command, giving your desktop time to load.

&quot;&&&quot; waits for the prior cmd to finish before executing the next (very useful for all sorts of things).

The rest is pretty obvious.  Note that &quot;--start-hidden&quot; is a firestarter cmd, it doesn't work for everything!

Save the file as whatever you like, mine is &quot;firestarter_startup.sh&quot;, making sure to add the &quot;.sh&quot;

Make the file executable by right-clicking it in Nautilus, selecting &quot;Properties&quot;, and then the &quot;Permissions&quot; tab.

Go to System-->Preferences-->Startup Applications in your main menu, set the command to run as the full path to your new file, and presto!  Bash will now execute your new script.  It's like an alias, but without having to open a terminal!

You can do this with all kinds of stuff...Conky, Thunderbird + Alltray (so TB always starts in the tray at boot), and whatever else you feel like!:D  You can even set a cron job to have bash run a script at certain times, hourly, daily, weekly, monthly, the sky's the limit!

---

### Post by Axolotl9250 on 2010-06-21
This looks really cool, I downloaded mplayer using pacman and  obtained an mp3. My current script is like this: 


**Code:**

# Check for an interactive session
[ -z "$PS1" ] && return

alias ls='ls --color=auto'
PS1='[\u@\h \W]\$ '

#########################
#Various Edits:
#########################
#This changes what the terminal displays before the cursor
export PS1="GLaDOS, "

alias sing='mplayer -really-quiet ~/Music/stillalive.mp3 < /dev/null & echo -n "T" && sleep .05 && echo -n "h" && sleep .08 &&  echo -n "i" && sleep .05 && echo -n "s" && sleep .05 && echo -n " " && sleep .05 && echo -n "w" && sleep .1 && echo -n "a" && sleep .1 && echo -n "s" && sleep .03 && echo -n " " && sleep .05 && echo -n "a" && sleep .1 && echo -n " " && sleep .1 && echo -n "t" && sleep .1 && echo -n "r" && sleep .1 && echo -n "i" && sleep .1 && echo -n "u" && sleep .1 && echo -n "m" && echo -n "p" && sleep .1 && echo "h" && sleep 4.3 && echo "

                  .,-;;//;\=,.
               . 1H@@@MM@M#H/ ,+;,
            ,/X+ +M@@M@MM% ,-%HMMM@X/,  
          -+@MM; SM@@MH+- ;XMMMM@MMMM@+-
         ,@M@@M- XM@X;. -+XXXXXHHH@M@M.--.    
        ,%MM@@MH ,@%=            ..--=-=;=,.
        +@#@@@MX .,              -%HXSS%%%+;
       =; .@M@M$                  .;@MMMM@MM;
       X@= -#MM/                    .+MM@@@M#;
      ,@M@H; ;@1                     . =X#@@@@
      ,@@@MMX, .                    /H- ;@M@M=
      .H@@@@M@+,                    %MM+. %#$.
       /MMMM@MMH\.                  XM@MH; =;
        /%+%SXHH@#=              , .H@@@@MX,
         .,,.,,..,,,           -%H ,@@@@@MX,  
          %MM@@@HHHXM++;;-- .;SMMX =M@@MM%.
           =XMCAMAMAGUEY ,-+HMM@M+ /MMMX=
             =%@M@M#@S .=#@MM@@@M; %M%=
               ,;+#+- /H#MMMMMMM@= =,
                 --. =++%%%%+/;-.
"'

(The Icon appears correct in real life when copied from above)

By my reasoning, this should set the cursor  to say Glados and when sing is entered it should do the whole singing  thing. When I type in sing and press enter, the song starts and the logo  apears but before the logo appears I get 
**Code:**

[1] 15711
Tmplayer: could not connect to socket
mplayer: No such file or directory
his was a triumph


And the lyrics stop at  triumph. Something's going on with mplayer I can see although I did use  pacman to install mplayer. I Googled Tmplayer but only got a polish  webpage. I think the Tmplayer thing is actually mplayer with the T from This was a triumph in front of it.

---

### Post by Windows Nerd on 2010-06-24
Hey guys, I was doing this and was not paying attention. I accidentally ran 
```
 rm ~/.bashrc
```
instead of
```
nano ~/.bashrc
```I know. Stupid me. That's what I get for having several terminals open at once and forgetting I had typed half a command in the other one.

Anyone have a copy of the default .bashrc for Jaunty? (or will the one work from Karmic that you posted above?)

Jesus, it's almost as worse as forgetting the extra ">" in the cat command when adding lines to a file (yes I have done that one too).

Scott

---

### Post by Drenriza on 2010-11-18
#9 
can you edit your post to remove smileys.

Thanks on advance.

---

