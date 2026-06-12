---
title: "Run a script everytime shutdown or reboot computer"
date: 2023-05-08
forum: New to Ubuntu
---

### Post by netw844f on 2023-05-08
Hello,

I intend execute a script everytime my system shutdown. To do this I followed this article (I don't know if it is the best option): [https://www.golinuxcloud.com/run-script-with-systemd-before-shutdown-linux/](https://www.golinuxcloud.com/run-script-with-systemd-before-shutdown-linux/)

After I ran the command "$ systemctl enable /etc/systemd/system/works.service" I received this message:

```

The unit files have no installation config (WantedBy=, RequiredBy=, Also=,
Alias= settings in the [Install] section, and DefaultInstance= for template
units). This means they are not meant to be enabled using systemctl.

Possible reasons for having this kind of units are:
• A unit may be statically enabled by being symlinked from another unit's
  .wants/ or .requires/ directory.
• A unit's purpose may be to act as a helper for some other unit which has
  a requirement dependency on it.
• A unit may be started when needed via activation (socket, path, timer,
  D-Bus, udev, scripted systemctl call, ...).
• In case of template units, the unit is meant to be enabled with some
  instance name specified.

```

My script is:

```

-rwxrwxr-x 1 user user 148 may  8 4:11 Desktop/work.sh

```

and my file in /etc/systemd/system/ is:

```

-rwxr-xr-x 1 root root 216 may  8 4:12 /etc/systemd/system/works.service

```

and 

```

$ cat /etc/systemd/system/works.service
[UNIT]
Description=Run my custom task at shutdown
DefaultDependencies=no
Before=shutdown.target

[SERVICE]
Type=oneshot
ExecStart=/home/user/Desktop/work.sh
TimeoutStartSec=0

[INSTALL]
WantedBy=shutdown.target

```

What kind configuration can I try or what am I doing wrong?
Thank you

---

### Post by Holger_Gehrke on 2023-05-08
I'm not totally certain, but since most of Linux is case sensitive and all the unit-files I've ever seen used mixed case, I think those sections in your unit file should be '[Unit]', '[Service]', and '[Install]' instead of '[UNIT]', '[SERVICE]', and '[INSTALL]'.

Holger

---

### Post by netw844f on 2023-05-08
I didn't see that detail. This "specification" was mention on original article.
Thank you for you clue

Do you how can I add an option "log out"  as I did with shutdown.target?

---

### Post by MAFoElffen on 2023-05-10
Note that in the replies to the article, that for Debian branches to call the custom script, it worked for shutdown, but not reboot, unless they changed the end of the service file like this:
```

....
[Install]
WantedBy=shutdown.target [COLOR=#ff0000]reboot.target[/COLOR]

```
Just an observation, based on what you said you wanted it to do.

---

### Post by netw844f on 2023-05-10
I didn't need this parameter "reboot.target". Only with command "shutdown.target" worked as expected.
Thank you for your clue.
I was referring when I need block my screen through sequence key "windows key + L" or when I choose the option "Log out" available in option shutdown on Kubuntu (Please see this image: [https://preview.redd.it/4c4in5vrv1u51.png?width=429&format=png&auto=webp&5b71ae78](https://preview.redd.it/4c4in5vrv1u51.png?width=429&format=png&auto=webp&5b71ae78))

Thank you

---

