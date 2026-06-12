---
title: "changing from linux mint 14 to ubuntu"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by BFVSFOREVER on 2012-12-10
Hi, I currently use linux mint 14 and want to switch to Ubuntu due to printer not being supported by mint 14, what should I do make the switch?

---

### Post by Jmackxxx on 2012-12-10
1st of all are you running Gnome...if you are ... you can add ubuntu PPA's to your computer to find that Driver....If you are running gnome more likely ubuntu will not have the printer support you need I don't know what type of printer you have but..You can always download Turbo Print for your Printer to work.. there is a 30 day free trail.   Hope this helps

---

### Post by Jmackxxx on 2012-12-10
if you just wanna switch backup your data and Fresh install

---

### Post by pqwoerituytrueiwoq on 2012-12-10
if your printer does not work with mint 14 it wont work with ubuntu 12.10

try to add a printer using *system-config-printer*
it may need a special driver and it may help you install it
telling us what printer you have would be more helpful in solving your issue

---

### Post by NightsShadeQueen on 2012-12-10
Yeah, Linux Mint 14 is based off of Ubuntu 12.10.

One thing that may happen - some things look at your distro name for configuration purposes. Pretty sure this isn't the case here, but if it's failing with a message like "your distro of Ubuntu isn't supported", then this might be what's causing it.

If this is the case, you can sometime figure out a way to lie to it.

Example (this is from the debathena installation script)

```

distro=`lsb_release -cs`
aptitude=aptitude
case $distro in
  squeeze)
    ;;
  hardy|lucid)
    ubuntu=yes
    ;;
  natty|oneiric|precise)
    ubuntu=yes
    aptitude=apt-get
    ;;
  quantal)
    ubuntu=yes
    aptitude=apt-get
    output "The release you are running ($distro) is not supported"
    output "and installing Debathena on it is probably a bad idea."
    if ! test -f /root/pxe-install-flag; then
    ask "Are you sure you want to proceed? [y/N] " n
    [ y != "$answer" ] && exit 1
    fi
    ;;
  lenny|intrepid|jaunty|karmic|maverick)
    error "The release you are running ($distro) is no longer supported."
    error "Generally, Debathena de-supports releases when they are no longer"
    error "supported by upstream.  If you believe you received this message"
    error "in error, please contact debathena@mit.edu."
    exit 1
    ;;
  *)
    error "Unsupported release codename: $distro"
    error "Sorry, Debathena does not support installation on this release at this time."
    error "(New releases may not be supported immediately after their release)."
    error "If you believe you are running a supported release or have questions,"
    error "please contact debathena@mit.edu"
    exit 1
    ;;
esac
```

Now, I'm running Linux Mint 12, lisa, so this script gets confused because it doesn't know what lisa is. But I can replace distro=`lsb_release -cs` with distro=oneiric.

But this can get pretty complicated, and it's probably not your issue. It is, however, one of few things that can cause an install to fail on Linux Mint 14 but not Ubuntu 12.10.

Another thing is that 12.10 is still pretty new; there's a (slim) possibility that your printer driver just doesn't work yet on 12.10. If this is the case, moving to Ubuntu 12.04 probably will solve your issue. Unfortunately the only way to get to Ubuntu 12.04 is to do a clean install - in other words, back everything up and install Ubuntu 12.04 over your current Linux Mint 14.

So, yeah, what printer do you have?

---

### Post by BFVSFOREVER on 2012-12-10
sorry, my mistake, it is a Lexmark Pro 205, turbo print say's it doesn't and will not support Lexmark printers
:(

---

### Post by BFVSFOREVER on 2012-12-10
OK, so I will probably have to go back to windows 7, gawd, I love Linux so much, Thanks for your help :(

---

### Post by NightsShadeQueen on 2012-12-10
Looks like Lexmark has Linux Mint 13 and Ubuntu 12.04 drivers, actually; perhaps they'll come out with the Mint 14 drivers soon?

[http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_PROSPECT_PRO205&page=product&frompage=null#2](http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_PROSPECT_PRO205&page=product&frompage=null#2)

---

### Post by levlaz on 2012-12-10
This specific printer seemed to have worked for a [previous user.]("http://ubuntuforums.org/showthread.php?t=1378789") Try this out before making the switch back to Windows.

---

### Post by sammiev on 2012-12-10
It's a little dated but may work.  [Lexmark Prospect Pro 205]("http://ubuntuforums.org/showthread.php?t=1378789")

---

### Post by BFVSFOREVER on 2012-12-10
just finished with Lexmark, I have to contact them tomorrow when the Linux team comes back to work, missed them by 45 minutes, Thanks for the help and yes it is the same for Ubuntu, driver does not support new version

---

