---
title: "Compiz-Checker"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-18
I got the Compiz-Checker program, and I get the following output:

```


Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         S3 Inc. VT8375 [ProSavage8 KM266/KL266]
 Driver in use:         savage
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on the whitelist. 

Would you like to know more? (Y/n) 

```

and when i press Yes.. 

```

Would you like to know more? (Y/n) y

 Your driver is not widely known to work with Compiz and thus may be
 blacklisted on certain distributions.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) 

```

Is there any chance of me running compiz?

---

### Post by HDave on 2008-07-18
You will first need to enable your restricted (proprietary) graphics driver.  If you don't have a restricted graphics driver then you can't run compiz.

Otherwise, why not just try it?  If you're running Hardy, it's already installed.  Go to system->preferences->appearances and select "normal" on the desktop effects tab.  If it works, your good, if it reverts to "none" then you can't run compiz.

---

### Post by overdrank on 2008-07-18
> **adobrakic said:**
> I got the Compiz-Checker program, and I get the following output:

```


Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         S3 Inc. VT8375 [ProSavage8 KM266/KL266]
 Driver in use:         savage
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on the whitelist. 

Would you like to know more? (Y/n) 

```

and when i press Yes.. 

```

Would you like to know more? (Y/n) y

 Your driver is not widely known to work with Compiz and thus may be
 blacklisted on certain distributions.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) 

```

Is there any chance of me running compiz?

Hi and as the warning stated the S3 graphics are not well supported and if you do try you could loose your GUI ( desktop). If this happens then you may reboot into recovery mode and use the option xfix. Hopefully this will correct any issue cause by the action.

---

