---
title: "Getting a start-up script to run in Xubuntu 12.04"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by RangerK on 2013-06-29
So, I'm thrilled to have figured out how to map keys on my strange keyboard.  Thanks for the help, guys ([http://ubuntuforums.org/showthread.php?t=2158261](http://ubuntuforums.org/showthread.php?t=2158261)).

My problem is now getting a script to run at startup.  I've read that different distributions of linux have different standards for this.  I'm using Xubuntu 12.04

I tried to figure this out myself.  It seemed like something that shouldn't be too complex.  No luck so far.

Here's what I tried:

1) make a script and add it to Applications>Setting>Autostarted Application (I have "Sessions and Startup" instead of "Autostarted".)

[http://ubuntuforums.org/showthread.php?t=943114](http://ubuntuforums.org/showthread.php?t=943114)

It allowed me to add my script, but it doesn't seem to have run.

2) adding a line (xmodmap -e "keycode 94 = slash") to /etc/rc.local

I forget where I read these directions.  In the file rc.local it says "This script is executed at the end of each multiuser runlevel."

3) making a script and putting it in /etc/init.d/

sudo mv /filename /etc/init.d/
sudo chmod +x /etc/init.d/filename
sudo update-rc.d filename defaults

[http://stackoverflow.com/questions/7221757/run-automatically-program-on-startup-under-linux-ubuntu](http://stackoverflow.com/questions/7221757/run-automatically-program-on-startup-under-linux-ubuntu)

Also, same instructions here: [http://linux.mjnet.eu/post/955/how-to-add-script-at-boot-time-with-ubuntu/](http://linux.mjnet.eu/post/955/how-to-add-script-at-boot-time-with-ubuntu/)

4) put a script in /etc/profile.d/

[http://stackoverflow.com/questions/3036/files-and-scripts-that-execute-on-boot](http://stackoverflow.com/questions/3036/files-and-scripts-that-execute-on-boot)

Maybe I wasn't writing the script file correctly.  It's contents were:
------------
#!/bit/bash
xmodmap -e "keycode 94 = slash"
------------

Any help is appreciated.

---

### Post by DeathByDenim on 2013-06-29
I've also got a somewhat weird keyboard and I had to resort to the same xmodmap stuff as you. I managed to get it to to be permanent, by creating a file called "/etc/xprofile". Just put your xmodmap -e "keycode 94 = slash" in there. It should work the next time you reboot then. (Or restart your Xserver, I guess)

---

### Post by JKyleOKC on 2013-06-29
I believe that it will work if you add the single command (no need for the script) to the ".bashrc" file in your home directory. This is a script that runs each time you log in, and I set all my convenient alias definitions in it. Doing it this way you won't need the two-line script!

---

### Post by RangerK on 2013-06-29
JKyleOCK, that's a 98% solution and might be good enough.  It seems that .bashrc only runs when a terminal executes.  So after Xubuntu launches, I have to then open a terminal to make sure the change goes into effect.  If I go straight into, say, firefox, without opening a terminal, .bashrc will not be executed and the change won't be made.

DeathByDenim, can you tell me more about that xprofile file?  Is it a script?  Do you start with #!/bit/bash?  What permission?

---

### Post by JKyleOKC on 2013-06-29
> **RangerK said:**
> JKyleOCK, that's a 98% solution and might be good enough.  It seems that .bashrc only runs when a terminal executes.  So after Xubuntu launches, I have to then open a terminal to make sure the change goes into effect.  If I go straight into, say, firefox, without opening a terminal, .bashrc will not be executed and the change won't be made.While the first three lines of .bashrc seem to imply that it's never executed by a login shell, take a look at the .profile file as well. It's executed at each login, and at line 15 it will execute .bashrc if such a file exists in the home directory.

The /etc/profile file is executed by all users at login; the $HOME/.profile file is executed for the individual user. Either could be used; but I do my login-time settings in .bashrc so that they apply in any terminal I open, and will still take effect at login...

---

### Post by RangerK on 2013-06-29
I've implemented your suggestions.  Putting the line "xmodmap -e "keycode 94 = slash" in .bashrc causes the keymapping to happy only after I've opened a terminal.

Putting it in .profile seems to have no effect.  I've tried putting it both at the end of .profile and toward the beginning.

---

### Post by erind on 2013-06-29
Add a *sleep* command before *xmodmap*, and leave the script in the "Sessions and Startup" section:

```
#!/bin/bash

[COLOR=#0000ff]sleep 8 [/COLOR]    ## change 8 to other value if needed.

xmodmap -e "keycode 94 = slash"

```
*xmodmap *needs to have** X** fully up, before it can run successfully, and that's why *sleep *is needed.

---

### Post by JKyleOKC on 2013-06-30
If you've not found the "Sessions and Startup" section mentioned by erind, it's in the Applications -> Settings -> Settings Manager menu, in its "System" group of icons. The section has a tab labelled "Application Autostart" with an "Add" button.

Perhaps the need for a "sleep" command is why putting the line into the .profile file failed to work. However using the script and having it autostart is probably a better solution.

---

### Post by RangerK on 2013-06-30
erind, -- Perfect.  Adding a 'sleep 8' line to my script worked. Thank you.

---

