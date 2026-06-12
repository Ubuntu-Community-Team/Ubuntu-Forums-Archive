---
title: "Possible to get a variable from Grub2?"
date: 2011-04-07
forum: Programming Talk
---

### Post by Jose Catre-Vandis on 2011-04-07
Have setup a system (one linux OS) that can either be a command line or gui experience and would like to be able to select which version to run at the grub2 menu.

I have carried out a command line installation of Xubuntu 10.04 then added openbox. I use SLiM (Simple Login Manager), which has an entry in rc.local to run it.

Xubuntu offers no way of booting to the cli - that I can find, and SLiM seems to offer no way of turning it off.

So is there any way a bash script could pick up which menu entry in grub2 was selected to be run, to then select whether SLiM should be run or not? I am thinking if I have custom / bespoke menu entries then these would be easier to find.

Example script (in English!) to put in rc.local:

```
!#/bin/bash

menu=Collect name of grub2 entry selected  << how to do this bit?

if $menu = SLiM then

/usr/bin/slim

endif

done
```

Or is there a better way?

( no, the "text" kernel option doesn't work with SLiM)
( I can't find a way to start up with runlevel 1 without invoking recovery mode or dropping to a root shell)

Happy to try just about anything (apart from working with animals or children) to solve this!

Thanks

---

### Post by amauk on 2011-04-07
Easiest way is to make menu items that boot to different runlevels

You can specify which runlevel to boot into by appending the number to the end of the kernel line in grub
Eg.```
linux /boot/vmlinuz-2.6.38-8-generic.....quiet splash [COLOR="Red"]3[/COLOR]
```

Ubuntu defaults (I think) to runlevel 2
so runlevel 3 can be your CLI only option

You'll need to read up on how to create sysV init scripts, and how to specify which runlevels the script will execute under
Then make an init script for your graphical login manager, and bind it to runlevel 2 only

---

### Post by Jose Catre-Vandis on 2011-04-07
Thanks amauk

SLiM shows up on runlevel 3 as well.

I'll go away and have a read up on sysV init scripts :?

EDIT

Hang on you've given me an idea.

```
who -r
``` tells me which runlevel I am on so if I can check this in my script I can do this?

---

### Post by dwhitney67 on 2011-04-07
> **amauk said:**
> 
Ubuntu defaults (I think) to runlevel 2


Are you sure? I always thought that it was runlevel 5.

---

### Post by ajgreeny on 2011-04-07
> **dwhitney67 said:**
> Are you sure? I always thought that it was runlevel 5.
No it is runlevel 2!  Try the ```
who -r
``` command.

---

### Post by amauk on 2011-04-07
> **Jose Catre-Vandis said:**
> Hang on you've given me an idea.

```
who -r
``` tells me which runlevel I am on so if I can check this in my script I can do this?
Yes,
but I'd advise against rolling your own custom solution

I'd personally stick with init scripts,
mainly because they're standardised and there's an entire framework behind their operation

Say you're in CLI mode, and wish to switch to GUI
How do you do this, with confidence that everything is loaded and working as it should?

On switching runlevels
- All the 'stop' init scripts for the current runlevel get executed and all loaded services stop
- Runlevel changes
- All the 'start' init scripts for the new runlevel get executed and all services that should be running at this runlevel are started


*edit*
Btw, if you do roll your own custom solution
a better way to get the current runlevel is```
runlevel | grep -o '[0-9]\+$'
```

---

### Post by Jose Catre-Vandis on 2011-04-07
Thanks amauk, and thanks for the one liner

I get what you are saying.

I had a look at directories rc2.d and rc3.d and they have exactly the same symlinks in each. Does that mean they do the same thing? Is it that I just haven't installed a program yet that needs a specific run-level to operate?

---

### Post by amauk on 2011-04-07
Doing a simple```
CUR_RUNLVL=$(runlevel | grep -o '[0-9]\+$')
if [ "$CUR_RUNLVL" -eq 2 ]; then
	/usr/bin/slim
fi
```is certainly easy,
but I do still have reservations about bypassing init scripts (which were designed for this very purpose, specifying what gets run at specific runlevels)

Certainly use rc.local as a first prototype,
but I would have an init script for SLiM as an end-goal

---

### Post by Jose Catre-Vandis on 2011-04-07
Well, I couldn't resist :) so i went ahead and tried it out.

Here is the script I put in /etc/rc.local:

```
!#/bin/bash

slimtest=`who -r`
runl=${slimtest:19:1}

#alt method
#slimtest=`runlevel | grep -o '[0-9]\+$'`

if [ "$runl" == "2" ]; then 

/usr/bin/slim

fi
```

I rebooted, selected the recovery mode menu entry, edited it to remove single and add a 3, pressed CTRL+X, and it booted up to a command prompt login :)

I logged in, checked dmesg, nothing odd there, and then typed startx.

```
runlevel | grep -o '[0-9]\+$'
```returned "**3**"

Worked fine booted up the normal way too

Have more testing to do, and will have to see if I can break it!

---

### Post by Jose Catre-Vandis on 2011-04-07
I've also just had a look at the rc2.d and rc3.d directories on my main system which i have had running for over a year, updated from lucid to meerkat, and packages installed to the hilt, and loads of configuration. The contents of each folder are exactly the same.

So what have Ubuntu / Xubuntu been up to? Is there no difference at all between these two run-levels, aside from one supposedly being for cli mode?

---

### Post by sisco311 on 2011-04-07
> **Jose Catre-Vandis said:**
> 

( no, the "text" kernel option doesn't work with SLiM)



Edit the /etc/init.d/slim file to look like this:
```

...

case $1 in
  start)

[B]    for ARG in $(cat /proc/cmdline)
    do
      case "${ARG}" in
        text|-s|s|S|single)
          plymouth quit || :  # We have the ball here
          exit 0
          ;;
      esac
    done
[/B]
    if [ "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" ] &&
       [ -e $DEFAULT_DISPLAY_MANAGER_FILE ] &&
       [ "$(cat $DEFAULT_DISPLAY_MANAGER_FILE)" != "$DAEMON" ]; then
      echo "Not starting X display manager (slim); it is not the default display manager."
    else
      echo -n "Starting X display manager: slim"
      start-stop-daemon --start --quiet $SSD_START_ARGS || echo -n " already running"
      echo "."
    fi
  ;;
...

```

> **Jose Catre-Vandis said:**
> 
( I can't find a way to start up with runlevel 1 without invoking recovery mode or dropping to a root shell)


then create a  **text mode** boot option:
[http://ubuntuforums.org/showpost.php?p=9644518&postcount=3](http://ubuntuforums.org/showpost.php?p=9644518&postcount=3)

---

### Post by Jose Catre-Vandis on 2011-04-07
> **sisco311 said:**
> Edit the /etc/init.d/slim file to look like this:
```

...

case $1 in
  start)

[B]    for ARG in $(cat /proc/cmdline)
    do
      case "${ARG}" in
        text|-s|s|S|single)
          plymouth quit || :  # We have the ball here
          exit 0
          ;;
      esac
    done
[/B]
    if [ "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" ] &&
       [ -e $DEFAULT_DISPLAY_MANAGER_FILE ] &&
       [ "$(cat $DEFAULT_DISPLAY_MANAGER_FILE)" != "$DAEMON" ]; then
      echo "Not starting X display manager (slim); it is not the default display manager."
    else
      echo -n "Starting X display manager: slim"
      start-stop-daemon --start --quiet $SSD_START_ARGS || echo -n " already running"
      echo "."
    fi
  ;;
...

```



then create a  **text mode** boot option:
[http://ubuntuforums.org/showpost.php?p=9644518&postcount=3](http://ubuntuforums.org/showpost.php?p=9644518&postcount=3)

Looks good sisco311 (I like your work all over the forum :)), 

but no /etc/init.d/slim file on my setup :(

---

### Post by sisco311 on 2011-04-07
How did you install slim? An Ubuntu deb package should provide an init script. Either a Sys-V style one in /etc/init.d or an Upstart job in /etc/init.

---

### Post by dwhitney67 on 2011-04-07
> **ajgreeny said:**
> No it is runlevel 2!  Try the ```
who -r
``` command.

You're right!  I ran both the command you indicated above (and runlevel as suggested by amauk).

To have some "fun", I edited the /etc/init/rc-sysinit.conf file so that the default setting on my system is level 5... just like Red Hat and Fedora.

Btw, so far I cannot see any discernible difference between levels 2 and 5, and from looking at the respective /etc/rc<N>.d directories, there probably isn't.

---

### Post by Jose Catre-Vandis on 2011-04-07
> **sisco311 said:**
> How did you install slim? An Ubuntu deb package should provide an init script. Either a Sys-V style one in /etc/init.d or an Upstart job in /etc/init.

from source

```
wget http://download.berlios.de/slim/slim-1.3.2.tar.gz
```

I didn't realise it was back in the repos, it disappeared a while back :o

---

### Post by sisco311 on 2011-04-07
> **Jose Catre-Vandis said:**
> from source

```
wget http://download.berlios.de/slim/slim-1.3.2.tar.gz
```

I didn't realise it was back in the repos, it disappeared a while back :o

You could create your own Upstart job or Sys-V style init script.

Or install it from the repositories. 

Here is an Upstart job which should work in Maverick and Natty:

/etc/init/slim.conf:
```
# SLIM - Simple Login Manager
#
# A Desktop-independent graphical login manager for X11, 
# derived from Login.app.
#
# based on gdm.conf by William Jon McCann <mccann@jhu.edu>

description     "Simple Login Manager"
author          "sisco311"  

start on (filesystem
          and started dbus
          and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
stop on runlevel [016]

emits starting-dm

env XORGCONFIG=/etc/X11/xorg.conf

script
    if [ -n "$UPSTART_EVENTS" ]
    then
	[ ! -f /etc/X11/default-display-manager -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/bin/slim" ] || { stop; exit 0; }

	# Check kernel command-line for inhibitors
	for ARG in $(cat /proc/cmdline)
	do
	    case "${ARG}" in
		text|-s|s|S|single)
                    plymouth quit || :  # We have the ball here
		    exit 0
		    ;;
	    esac
	done
    fi

    if [ -r /etc/default/locale ]; then
	. /etc/default/locale
	export LANG LANGUAGE
    elif [ -r /etc/environment ]; then
	. /etc/environment
	export LANG LANGUAGE
    fi
    export XORGCONFIG

    exec slim
end script

```

---

### Post by Jose Catre-Vandis on 2011-04-07
Thanks again cisco311 - I'll have a bash at this tomorrow and report back.

---

### Post by Jose Catre-Vandis on 2011-04-08
I installed from the repos and edited the /etc/init.d/slim file as above.

On reboot I manually edited the recovery mode option from the grub menu, replacing "single" with text, and got my cli prompt :)

I haven't tried out creating the grub menu entry as the install I am working on is a second install, being picked up by the primary installs grub2, and I am not chainloading the second install. I have another setup running in a VM so will test there.

Will this all persist if I do a remastersys dist on it and create an installation CD, or does this have to be done after installation?

I am going to mark as solved :) Thanks to all :)

---

### Post by Jose Catre-Vandis on 2011-04-09
Follow up.

On my standalone setup, I edited the /etc/init.d/slim file as above, then followed the howto to to edit /etc/grub.d/10_linux.

This all works nicely, apart from the fact that the "text mode" entry, whilst avoiding plymouth, still ends up with slim presenting itself for a login. As previously, slim ignores the "text" kernel option, so it behaves differently to gdm (et al).

Anyway to fix this?

I have discovered that if I change "text" to "3" in this line in 10_linux, 
```
"text ${GRUB_CMDLINE_LINUX}" > "3 ${GRUB_CMDLINE_LINUX}"
```
that 3 shows up in the menu entry, so could use the script as above? But that doesn't work, because now slim is installed from a deb (repos) there is an init script firing it up, as opposed that having to be manually called. :(

If I remove the executable bit from /etc/init.d/slim, and put the runlevel finding script back into rc.local it all works as I want :) although I do see a small complaint coming through about init scripts (S & K) not running, but I would expect that.

---

### Post by El_Belgicano on 2011-04-11
> **sisco311 said:**
> <snip>
```

...
[B]    for ARG in $(cat /proc/cmdline)
    do
      case "${ARG}" in
        text|-s|s|S|single)
          plymouth quit || :  # We have the ball here
          exit 0
          ;;
      esac
    done
[/B]
...

```
<snip>

Voilà, integrated in my **/etc/init.d/slim**, and assuming it's SLiM that isn't working properly, your little piece of code allows me to do some testing with it.

Thank you for that.

I'll post my problem in a new thread in a moment...

**EDIT:** _[The problem]("http://ubuntuforums.org/showthread.php?t=1726890")_

---

