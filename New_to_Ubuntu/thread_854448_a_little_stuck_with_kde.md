---
title: "a little stuck with kde"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by techno-mole on 2008-07-09
hello.
ive just installed kubuntu, but im a little puzzled, i have previously used ubuntu and thought id try kubuntu.
but i cant seem to install anything, for example according to the documentation to install firefox you go to add /remove programs etc etc (pretty much the same as gnome) but its not there, ive got all the repos enabled but theres hardly anything in the add /remove section.

also the max resoultion i can get on my monitor is 640 x 480 as i cant seem to adjust it any higher than that (normally run the monitor at 1200 x 800)
i also tried to install the nvidia-settings application, but its not there either.

im assuming that kubuntu isnt that different from ubuntu ? eg - you can still install nvidia-settings and other stuff.

any ideas would be helpful

---

### Post by OffAxis on 2008-07-09
> ive got all the repos enabled but theres hardly anything in the add /remove section.
have you run an update since enabling them?
```
sudo apt-get update
```

try installing firefox from konsole
```
sudo aptitude install firefox
```

> also the max resoultion i can get on my monitor is 640 x 480 ...
Have you enabled the Restriced Driver?
System Settings-->Advanced Tab-->Restricted Driver.
(I think that's it; haven't used kde in a while.)
Also, pertaining to the settings, there's an 'Administrator Mode' button in the lower right corner that you may not see if you're at 640x480. You can drag the window around by holding down the Ctrl key and left clicking to unveil it if necessary.

> im assuming that kubuntu isnt that different from ubuntu ? eg - you can still install nvidia-settings and other stuff
yes.

---

### Post by techno-mole on 2008-07-09
cheers, although i have found the problem, that being for some reason my router decided not to assign me an ip address, and because of that nothing was working.
cheers for the help

---

