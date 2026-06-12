---
title: "Ubuntu 16.04 running a script when desktop loads"
date: 2017-10-24
forum: New to Ubuntu
---

### Post by chris420 on 2017-10-24
Hi all,

I just want to run the following script from start up to kill pulseaudio and put Jack in control 

```

#!/bin/bash
killall -9 jackdbus
pasuspender -- qjackctl

```

I remember the good old days regarding the running on batch scripts in MS-DOS; you just put them in ye olde AUOTEXEC.BAT why is it so hard on Ubuntu? Can anyone tell me a really easy way of running the above code when the desktop loads so qjackctl runs with these commends too?

thanks

---

### Post by ajgreeny on 2017-10-24
Assuming that script runs as you want when you run it manually you can simply point to it in the session's startup applications list.

Open the dash (top icon in the launchbar) and type startup and the correct dialogue will appear for you to add a new item.

Just make sure the script is executable or it will not work for you.

---

### Post by TheFu on 2017-10-24
MS-DOS was a single user solution. Linux is multi-user, with remote users possible. A little more complex.

Audio stuff is normally tied to a login session, not something that gets started "system-wide."  Because there are many different ways to begin a session and manage a session post login, there are multiple "takes" on how that should happen by each team who created their own login/session manager.  

Never forget that the GUI is just another application on Linux systems.  It is **NOT** the operating system.  You can swap in or out 1 of 50-ish different GUIs on Linux.  That is very powerful ... and can be confusing to noobs.  Each of those GUIs can have a different method to automatically start/stop programs.  The configuration management for the different GUIs are usually different as well.  A few have pretty GUI applications that provide access to 10-20% of the settings.  Most just use text files.

For example, I use openbox for my X11 window manager. I do not use any DE (desktop environment).  To make something run after login, there is a file - ~/.config/openbox/autostart ... where commands can be placed.  That should work for any GUI based on openbox, like LXDE.  Other GUIs would have a different method.  I would suggest finding the "desktop guide" for the GUI you are using and looking for the application startup section.  Google found this: [https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html) though I don't know which release it applies to of the normal, standard, "Ubuntu Desktop" - could be gnome-specific or Unity specific. I don't know.  Haven't used the normal Ubuntu desktop since around 2011.

---

### Post by chris420 on 2017-10-24
Thank you all for the replies. I've put my script newjackscript in session and startup application on 16.04.

[IMG]https://drive.google.com/file/d/0B7Ues3pSIgEWc3ZGb3d2cGlMSGs/view?usp=sharing[/IMG]

No joy with it starting though, I've enabled the script executable 
[IMG]https://drive.google.com/file/d/0B7Ues3pSIgEWc3ZGb3d2cGlMSGs/view?usp=sharing[/IMG]

Any help would be great

Thanks :)

---

### Post by leunam12 on 2017-10-25
I am no expert but, could it be that the script is running but is attempting to kill the processes before they have started? Maybe it needs a little delay at the beginning like sleep 15 or 20 seconds. Worth a try.

---

### Post by TheFu on 2017-10-25
> **chris420 said:**
> Thank you all for the replies. I've put my script newjackscript in session and startup application on 16.04.

[IMG]https://drive.google.com/file/d/0B7Ues3pSIgEWc3ZGb3d2cGlMSGs/view?usp=sharing[/IMG]

No joy with it starting though, I've enabled the script executable 
[IMG]https://drive.google.com/file/d/0B7Ues3pSIgEWc3ZGb3d2cGlMSGs/view?usp=sharing[/IMG]

Any help would be great

Thanks :)

A nice **ls -al** would help, as proof.

---

### Post by chris420 on 2017-10-25
ls -al gives

```
-rwxr-xr-x  1 me me       56 Oct  6 08:26 newjackscript
```

and the script is green so I think that means it's executable ??? It works when I manually double click it on the Desktop Qjackctl then loads fine.

---

### Post by again? on 2017-10-25
> **chris420 said:**
> ls -al gives

```
-rwxr-xr-x  1 me me       56 Oct  6 08:26 newjackscript
```

and the script is green so I think that means it's executable ??? It works when I manually double click it on the Desktop Qjackctl then loads fine.
Are you using the full path to the script in startup applications?
eg
```
/home/chris420/Desktop/newjackscript
```

---

### Post by VMC on 2017-10-25
> **leunam12 said:**
> I am no expert but, could it be that the script is running but is attempting to kill the processes before they have started? Maybe it needs a little delay at the beginning like sleep 15 or 20 seconds. Worth a try.
You may be right. I needed to pause 'plank' for another issue. Into the command it would look like this '***sh -c "sleep 7;plank"***'. Replace'plank' with your script name.

---

### Post by chris420 on 2017-10-30
when I put 

```

sh -c "sleep 7;newjackscript"



```

in terminal directory where the executable newjackscipt is


I get


```
sh: 1: newjackscript: not found
```

What am I doing wrong? Thanks :)

---

### Post by TheFu on 2017-10-30
Your PATH doesn't include that location.
It is a best practice to always specify the full path to any program run inside a script.  That is what prior posts have suggested above.

/home/chris420/bin/newjackscript - for example. Also, newjackscript needs to have execute permissions - and all programs inside it should similarly point to the full path for each program.

---

