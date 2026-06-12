---
title: "Creating application &quot;toggle button&quot;"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by capleton on 2008-04-26
I found the following code [here.]("http://ubuntuforums.org/archive/index.php/t-150463.html") ```
#!/bin/bash
#
# Checks to see if process "compiz.real" is running.
# If it is, it will kill it.
# If it isn't, it will start it.
#
# By andysl@aniport.com

pid=`ps --no-heading -C compiz.real | cut -d "?" -f1`;
if [ -n "$pid" ]; thenkillall gnome-window-decorator
metacity --replace
elsegnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
fi

```

Would it be possible to substitute Gkrellm for "compiz.real" and create something that would open and close GKrellm?

Thanks in advance!

---

### Post by Bubba64 on 2008-04-26
In add ons there is a custom button maker.
[https://addons.mozilla.org/en-US/firefox/addon/5066](https://addons.mozilla.org/en-US/firefox/addon/5066)

---

### Post by sdennie on 2008-04-26
You could use a script like the following to toggle a command on/off.  It checks if a command is running, if so, it kills it.  If not, it starts it:

```

#!/bin/bash

if ! pgrep $1 ; then
   $@
else
   pkill $1
fi

```

Whatever program name you pass to the script will be toggled.

---

### Post by capleton on 2008-04-26
Sorry, my first post might not have been very clear.

It's not in firefox that I'm trying to create a toggle button, it's in ubuntu itself.  I'd like to make an application launcher that would launch  a small program (based on the code above) that could toggle between opening and closing GKrellm.  Given that I am very new to ubuntu there's a good chance that I've bitten off more than I can chew, but nevertheless, is this possible?  

And please let me know if what I've asked doesn't really make sense, or if I've poorly articulated any of this

---

### Post by sdennie on 2008-04-26
I think the script I posted will do exactly what you want.  For instance, if you save it as "toggle-app.sh" and then create a launcher that runs:

```

sh ~/toggle-app.sh gkrellm

```

(Assuming you save the script in your home directory and call it toggle-app.sh)

---

### Post by amohanty on 2008-04-26
> **vor said:**
> You could use a script like the following to toggle a command on/off.  It checks if a command is running, if so, it kills it.  If not, it starts it:

```

#!/bin/bash

if ! pgrep $1 ; then
   $@
else
   pkill $1
fi

```

Whatever program name you pass to the script will be toggled.

Might want to use pgrep -o in case you dont want to spell out the entire name ie gtk-window-decorator :)

---

### Post by capleton on 2008-04-26
> **vor said:**
> I think the script I posted will do exactly what you want.  For instance, if you save it as "toggle-app.sh" and then create a launcher that runs:

```

sh ~/toggle-app.sh gkrellm

```

(Assuming you save the script in your home directory and call it toggle-app.sh)

Thank you for the help.  I created a file called toggle-app.sh with ```
#!/bin/bash

if ! pgrep $1 ; then
   $@
else
   pkill $1
fi
``` and in "properties" for the app launcher is ```
sh ~/toggle-app.sh gkrellm
``` 
But I couldn't figure out how to get permission for the "home" directory, so I put it in my username subdirectory (/home/<username>) in the hopes that that this directory might also be considered "home"?

It doesn't appear to be working, even when I use "sh ~/<username>/toggle-app.sh gkrellm" instead.  

What am I doing wrong?

---

### Post by capleton on 2008-04-26
Success!!!

I changed ```
sh ~/toggle-app.sh gkrellm
``` to ```
sh /home/usrname/toggle-app.sh gkrellm
``` and now it works!  

I wonder why "~" wasn't working?



Anyway, thanks for all the help!

---

### Post by amohanty on 2008-04-26
~/ = /home/username/

hence

~/toggle-app.sh = /home/username/toggle-app.sh

AM

---

