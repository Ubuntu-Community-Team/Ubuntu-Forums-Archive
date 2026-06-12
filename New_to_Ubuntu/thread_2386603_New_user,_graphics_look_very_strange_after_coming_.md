---
title: "New user, graphics look very strange after coming out of suspend."
date: 2018-03-07
forum: New to Ubuntu
---

### Post by wdcook87 on 2018-03-07
I have an old Optiplex 320 with a 3.2 pent D, 1 gig ram and I put in a HD 6450 before I installed then immediately tried out the ```
apt-add-repository ppa:oibaf/graphics-drivers && apt-get update && apt-get dist-upgrade
``` to get my graphics driver updated since the HD 6450 is not supported in 16.04.  Well this problem does not ever happen when I leave the pc running but whenever I put it to Suspend mode and take it out there is about a 50% chance that it is going to come out of it looks like the pictures below with some distorted graphics and an awkward color scheme.  Turning the monitor off and on does not help and only rebooting fixes the problem, I removed the ppa and the first time I put it into suspend and took it out it looks like this still.  Are there any suggestions that I could try?  Thank you very much for the help in advance and let me know if there is any more info I could provide to help.

---

### Post by ajgreeny on 2018-03-08
I presume the command you showed (which I have now put within code tags for clarity) was a typo as the first part should be **sudo add-apt-repository**.

In  future please use **Code-Tags** for terminal output or commands you have used. See my signature below for a **How-to**

---

### Post by wdcook87 on 2018-03-08
Sorry about not having the tags around the code.  I forgot that when I did enter it into terminal that I did add the sudo.  I had it the same issue with the ppa installed and when I'm using the proprietary drivers.  Is there anything else that could be causing the screen to look like this?

---

### Post by monkeybrain20122 on 2018-03-08
Oibaf offers the latest beta mesa, it maybe a bit too bleeding edge so can be buggy. Maybe you can try instead the latest stable mesa release (17.3.6) from [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)

It is a lot newer than what comes with 16.04 so may support your card.

So here are the steps if you want to try

```
sudo apt install ppa-purge

sudo add-apt-repository ppa:paulo-miguel-dias/pkppa

sudo apt update

sudo ppa-purge ppa:oibaf/graphics-drivers
```

This will disable oibaf and downgrade all of oibaf's packages you installed to the next highest version in your sources which is the one in the stable mesa ppa.

Follow the prompt, when done, reboot.

---

### Post by wdcook87 on 2018-03-09
If I've already removed the oibaf ppa is there any problem with still following it as you have written?

---

### Post by mastablasta on 2018-03-09
are the strange colours only on some items? if so, it could be a desktop environment issue.

what happens if you change the theme when the issue occurs?

---

### Post by wdcook87 on 2018-03-09
The color issue seems to effect every part of the screen, I'm going to try and cause the problem with suspend and then try and change the theme when I get home.

---

### Post by wdcook87 on 2018-03-10
I tried the different drivers and they did not fix the problem but I did notice that if I change the resolution it goes back to normal then I can just revert the resolution back.  Is there anything that would cause this?

---

### Post by monkeybrain20122 on 2018-03-10
> **wdcook87 said:**
> I tried the different drivers and they did not fix the problem but I did notice that if I change the resolution it goes back to normal then I can just revert the resolution back.  Is there anything that would cause this?

No idea. But as a band aid may be you can use a script to change the screen resolution automatically when awake from sleep, the script may look like [this]("https://askubuntu.com/questions/512911/script-for-changing-resolution").

This probably would not work without modification since the scenario is a bit different (you want to execute the script when awake)  and Ubuntu has switched to systemd.

So consider modifying the script from link above along the line of [this thread]("https://ubuntuforums.org/showthread.php?t=2380045&p=13721671#post13721671"). If you want to pursuit this route and need further help, I suggest you start a new thread with title that says you need help for script change screen resolution when wake.

---

### Post by wdcook87 on 2018-03-10
Edit---- I read that when I first woke up and didn't notice you wanted it to run when it comes out of sleep, thanks a lot for the suggestion!!  I'll search around and see if anyone already has a guide out there for changing resolution coming out of suspend before I come back starting a new thread.

---

### Post by monkeybrain20122 on 2018-03-11
The workaround suggested above shouldn't be too hard to implement : you need two ingredients 1) commands to change resolution using xrandr , write in a bash script, make it executable and put it somewhere in your $HOME (say, $HOME/bin or $HOME/Scripts) , you can find those commands online. Test if the script works by running it in the terminal (or right click if you set in File Manager Preference to ask when click on executable text files), then go to step 2) Write another script to call the first script when computer awakes from suspension, put it in /lib/systemd/system-sleep, use the template 

```

#!/bin/bash

set -e

if [ "$2" = "suspend" ] || [ "$2" = "hybrid-sleep" ]; then
    case "$1" in
        pre) true ;;
        post) sleep 1 && **/path/to/first/script** ;;
    esac
fi
```

Now you may need something in the first script to connect to the x-server along the line of #6 in [https://ubuntuforums.org/showthread.php?t=2380045&p=13721671#post13721671](https://ubuntuforums.org/showthread.php?t=2380045&p=13721671#post13721671).
You may need to experiment a bit.


**EDITED**: Before doing all these, maybe should try a different kernel, that may fix your problem

See the steps in post #16 of this thread [https://ubuntuforums.org/showthread.php?t=2386359&page=2](https://ubuntuforums.org/showthread.php?t=2386359&page=2)

---

