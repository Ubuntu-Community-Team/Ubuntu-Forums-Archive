---
title: "Problem with getting script to start at startup rc.local"
date: 2017-09-17
forum: New to Ubuntu
---

### Post by christianhau on 2017-09-17
Hi!

I am trying to get my HomeSeer to start up when booting up my ubuntu server. 

I have made a script autostart_hs_christian that is started from rc.local:
rc.local:
[HTML]
#!/bin/sh## rc.local## This script is executed at the end of each multiuser runlevel.# Make sure that the script will "exit 0" on success or any other# value on error.## In order to enable or disable this script just change the execution# bits.## By default this script does nothing.
# Starting Homeseersh /home/christian/HomeSeer/autostart_hs_christian &exit 0
[/HTML]

autostart_hs_christian:
[HTML]

#!/bin/shsleep 30# HomeSeer install directoryHomeSeer_HOME="/home/christian/HomeSeer"cd ${HomeSeer_HOME}./go[/HTML]

sudo systemctl status rc-local.service gives:


 rc-local.service - /etc/rc.local Compatibility
   Loaded: loaded (/etc/systemd/system/rc-local.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/rc-local.service.d
           &#9492;&#9472;debian.conf
   Active: active (exited) (Result: exit-code) since Sun 2017-09-17 20:15:31 CEST; 7h left
  Process: 1612 ExecStart=/etc/rc.local start (code=exited, status=0/SUCCESS)
 Main PID: 1635 (code=exited, status=127)
    Tasks: 0 (limit: 4915)
   Memory: 0B
      CPU: 0
   CGroup: /system.slice/rc-local.service


Sep 17 20:15:31 homeseer systemd[1]: Starting /etc/rc.local Compatibility...
Sep 17 20:15:31 homeseer systemd[1]: Started /etc/rc.local Compatibility.
Sep 17 20:15:31 homeseer rc.local[1612]: sh: 0: Can't open /home/christian/HomeSeer/autostart_hs_christian
Sep 17 20:15:31 homeseer systemd[1]: rc-local.service: Main process exited, code=exited, status=127/n/a

I can run the autostart_hs_christian script with a sh command and its starts up perfectly, but trying to run it from rc.local it fails, any clues?

---

### Post by ubfan1 on 2017-09-17
What permissions do you have on autostart_hs_christian ?  Please post the output of ls -l autostart_hs_christian   
and maybe try to clean up the newlines in your original post so the scripts make sense.

---

### Post by christianhau on 2017-09-18
Thanks for the reply, I will get back to you, but I started anew trying to do it with systemd instead and ran into problems there too. So I will pursue systemd first as I have posted on here: [https://ubuntuforums.org/showthread.php?t=2371780&p=13688174#post13688174](https://ubuntuforums.org/showthread.php?t=2371780&p=13688174#post13688174)

If I can't get that working I will come back to this a little bit more old school attempt :)

---

