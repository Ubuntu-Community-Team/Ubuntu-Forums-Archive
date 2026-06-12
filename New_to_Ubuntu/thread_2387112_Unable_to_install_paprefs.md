---
title: "Unable to install paprefs"
date: 2018-03-14
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-03-14
Ubuntu 16.04.

I am unable to install **paprefs**, due to the absence of dependency. I think paprefs depends on the older versions(**1:8.0-0ubuntu3**) of  libpulse0, pulseaudio, but I have newer version(**1:8.0-0ubuntu3.7**). Please let me know how to diagnose this issue.

```
sudo apt-get install paprefs
 The following packages have unmet dependencies:
 paprefs : Depends: pulseaudio-module-gconf but it is not going to be installed
           Depends: pulseaudio-module-zeroconf but it is not going to be installed
```
           
           
```
sudo apt-get install pulseaudio-module-zeroconf
 pulseaudio-module-zeroconf : Depends: libpulse0 (= 1:8.0-0ubuntu3) but 1:8.0-0ubuntu3.7 is to be installed
                              Depends: pulseaudio (= 1:8.0-0ubuntu3)
```
 
```
sudo apt-get install libpulse0
 libpulse0 is already the newest version (1:8.0-0ubuntu3.7).
```


 ```
sudo apt-get install pulseaudio
 pulseaudio is already the newest version (1:8.0-0ubuntu3.7).
```

**Why do I am installing paprefs?**
I would like audio to be played through **both** *bluetooth* and [I]head-phone jack.


TIA[/I]

---

