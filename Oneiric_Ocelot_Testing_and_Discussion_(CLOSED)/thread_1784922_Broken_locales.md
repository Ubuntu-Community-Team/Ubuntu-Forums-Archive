---
title: "Broken locales?"
date: 2011-06-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 3vi1 on 2011-06-17
Anyone else got problems with locales after the most recent updates?

```
evil@saturn:~$ ccsm

(process:6123): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 93, in <module>
    import ccm
  File "/usr/lib/python2.7/dist-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.7/dist-packages/ccm/Conflicts.py", line 26, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.7/dist-packages/ccm/Constants.py", line 79, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.7/locale.py", line 531, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```

"sudo dpkg-reconfigure locales" fails too.  :\


**UPDATE:**  I fixed it by doing the following in order to get the reconfigure to run

```
export LANGUAGE=en_US.UTF-8
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
locale-gen en_US.UTF-8
sudo dpkg-reconfigure locales
```

---

### Post by Harry33 on 2011-06-17
Well at least after updating package locales (2.13+git20110617-1) I do not get the following error message anymore and locale settings seem to work OK.

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_GB:en",
	LC_ALL = (unset),
	LC_MESSAGES = "en_GB.UTF-8",
	LANG = "en_GB"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

---

### Post by 3vi1 on 2011-06-17
> **Harry33 said:**
> Well at least after updating package locales (2.13+git20110617-1) I do not get the following error message anymore and locale settings seem to work OK.

Hmmm... that's the same version I have.  I even tried reinstalling it, but it doesn't even reinstall properly:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en",
        LC_ALL = "en_US",
        LC_MESSAGES = "en_US.UTF-8",
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 363391 files and directories currently installed.)
Preparing to replace locales 2.13+git20110617-1 (using .../locales_2.13+git20110617-1_all.deb) ...
Unpacking replacement locales ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Processing triggers for lintian ...
Generating en_US.UTF-8 locale for internal Lintian use....
Setting up locales (2.13+git20110617-1) ...
/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_US)
Generating locales...
  en_AG.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_AU.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_BW.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_CA.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_DK.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_GB.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_HK.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_IE.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_IN.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_NG.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_NZ.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_PH.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_SG.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_US.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_ZA.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
  en_ZW.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_US)
up-to-date
Generation complete.

```

---

### Post by 3vi1 on 2011-06-17
I figured it out...  Updated first message with solution in case someone else encounters this.

---

### Post by 3vi1 on 2011-06-17
Spoke too soon.  I rebooted and found that the problem was back.

Searched around on a hunch it was LightDM and found it's not just me:
[https://bugs.launchpad.net/lightdm/+bug/797249]("https://bugs.launchpad.net/lightdm/+bug/797249")

---

### Post by seeker5528 on 2011-06-17
> **3vi1 said:**
> Searched around on a hunch it was LightDM and found it's not just me:
[https://bugs.launchpad.net/lightdm/+bug/797249]("https://bugs.launchpad.net/lightdm/+bug/797249")

I don't see anywhere on the login screen where lightdm gives the option to choose your language. Did I miss something?

If you want to change system wide you should be able to edit '/etc/environment'.

Mine currently shows ```
LANG="en_US.UTF-8"
```

Don't know where $LANGUAGE is being set, it's not in the '/etc/environment' file on my system and after setting $LANG in '~/.xprofile', locale still showed $LANGUAGE to be US english.

Since lightdm seems to be set up to handle setting the profile stuff now you can create a file named '.xprofile' in your home directory and export the stuff there, if you only want to change it in your user account.

My .xprofile looks like this currently 
```

# This file '~/.xprofile' should be used to customize the environment of your X login session similar
# to the way you would use '~/.profile' to customize the environment of your command line login session.

# export PATH="~/some_directory:$PATH"
# export WINDOW_MANAGER="/usr/bin/fluxbox"

# Eexport LIBOVERLAY_SCROLLBAR=1
export VTEST=FUBAR
setxkbmap -option terminate:ctrl_alt_bksp
export LANG=en_GB.UTF-8
export LANGUAGE=en_GB.UTF-8

```

After making the change, logging out, logging back in, opening a terminal window, and typing ```
locale
``` I get the following output 
```

LANG=en_GB.UTF-8
LANGUAGE=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES=en_US.utf8
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=

```

Later, Seeker

---

### Post by MacUntu on 2011-06-18
AFAIK '/etc/environment' by default shouldn't contain anything else but the PATH variable.

There was something wrong in my '~/.dmrc' (LANGUAGE=en_US instead of en_US.utf****8) a couple of days ago (I suspect lightdm, but have no prove).

**Edit**

Yes, that's the same issue this time. Just fix the LANGUAGE variable in your '~/.dmrc' file and log out/back in.

---

### Post by seeker5528 on 2011-06-18
> **MacUntu said:**
> AFAIK '/etc/environment' by default shouldn't contain anything else but the PATH variable.

I didn't find any information indicating there was a better place to put it if you want 'LANG=' to apply to the whole system.

> There was something wrong in my '~/.dmrc' (LANGUAGE=en_US instead of en_US.utf****8) a couple of days ago (I suspect lightdm, but have no prove).

I don't see how that would be the fault of lightdm, since it doesn't provide the option to select your language, the bug would be in whatever wrote the non-UTF-8 version of the setting in '~/.dmrc', probably a display manager, but if this is a new install that included lightdm as part of the OOBE, and the user account in question was the one created during installation, it could be something that made it's way in there when the account was created. 


On a related note...

It seems that gnome-language-selector is not able to set the language as it gives the appearance that it should and the 'Region and Language' applet the shows in gnome-control-center doesn't seem to work either. 

EDIT: Switched to the qt-kde greeter, it has place holders that I am guessing (but don't know) are intended to be the places where you can select language and keyboard layout, but nothing functional yet. Don't know if that is an indication that we can expect more stuff there soon or not.

Later, Seeker

---

### Post by MacUntu on 2011-06-18
> **seeker5528 said:**
> I didn't find any information indicating there was a better place to put it if you want 'LANG=' to apply to the whole system.

Was just saying that *by default* there is no LANG variable in '/etc/environment'. :)

> **seeker5528 said:**
> I don't see how that would be the fault of lightdm

The issue is the following: GDM writes 'Language=en_US' to '~/.dmrc' which works just fine as GDM doesn't set LANG to 'en_US' unlike lightdm (or whatever package) does.

**Edit:**

This is the 'real' bug report: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/793366](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/793366)

---

### Post by seeker5528 on 2011-06-18
> **MacUntu said:**
> This is the 'real' bug report: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/793366](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/793366)

Interesting. Apparently my googlefu failed me more than I thought. :P  When I initially googled for the language stuff none of the results said anything about '.dmrc' or '/etc/default/locale'.

 Later, Seeker

---

