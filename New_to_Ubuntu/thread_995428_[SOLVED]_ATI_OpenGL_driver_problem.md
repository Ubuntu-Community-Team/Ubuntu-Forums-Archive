---
title: "[SOLVED] ATI OpenGL driver problem"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by WitchCraft on 2008-11-27
Hi, I have a problem with OpenGL.

I wiped Wubi and installed IntrepidIbex.

I reinstalled OpenArena, and immediately recognized that it was running on Software GL (horribly slow)...

I did glxinfo | grep "direct rendering" and output was yes, however that certainly is wrong.

Now, I thought I'd have to install the ati driver.

So I did
```

lspci | grep "VGA"
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
user@toshiba:~# 

```

Went to ATI'S website and downloaded the driver for Radeon HD 2400 x64:
ati-driver-installer-8-11-x86.x86_64.run

Installed the driver, and thought it would be good on restart.
However, bad luck:
```

 glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
user@toshiba:~# 

```

What's wrong? The driver worked on x64 wubi... ???


```

cat /var/log/Xorg.0.log|grep "(EE)"
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) RADEON(0): Acceleration initialization failed
(EE) RADEON(0):  ParseTable said: CD_INVALID_OPCODE
(EE) RADEON(0):  ParseTable said: CD_INVALID_OPCODE


```

---

### Post by WitchCraft on 2008-11-28
bump.

---

### Post by skymera on 2008-11-28
I suggest to download the driver through ENVYNG.

The reason being is that it'll still work even on a newer kernel.

```
 sudo apt-get install envyng-gtk 
```

That will download, configure and install your ATi driver.

---

### Post by WitchCraft on 2008-11-28
> **skymera said:**
> I suggest to download the driver through ENVYNG.

The reason being is that it'll still work even on a newer kernel.

```
 sudo apt-get install envyng-gtk 
```

That will download, configure and install your ATi driver.

Many thanks, that did the job. 

However, envyng-gtk doesn't work yet, you need envyng-qt

---

### Post by skymera on 2008-11-28
> **WitchCraft said:**
> Many thanks, that did the job. 

However, envyng-gtk doesn't work yet, you need envyng-qt

Happy to help

---

### Post by WitchCraft on 2008-11-29
Now, just out of curiosity:

What did envyng do that I didn't?
Some option switch ?

---

