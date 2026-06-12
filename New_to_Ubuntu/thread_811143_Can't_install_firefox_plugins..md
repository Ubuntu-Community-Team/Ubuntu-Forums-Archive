---
title: "Can't install firefox plugins."
date: 2008-05-28
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-05-28
I have tried installing multiple addons but no luck with any of them I keep getting the same error. 

The first screen shot is of the error I received. The second one is of error console like it told me to go to.

Edit: This is Firefox 2.

---

### Post by alienexplorers on 2008-05-29
Did you try to make a new profile for firefox 2.  Run in terminal:
> firefox -profilemanager
let the profile manager create its default.user profile.
start up firefox from the profilemanager.
try installing the extensions again.
If it works, shutdown firefox and run firefox -profilemanager again.
delete the default profile.  Start firefox. shutdown.
restart firefox in the normal way.

---

### Post by iaculallad on 2008-05-29
Try visiting [kb.mozillazine]("http://kb.mozillazine.org/Firefox_:_Issues_:_Can't_Install_Themes_or_Extensions") to find out what other reasons you're not able to install firefox's extensions.

---

### Post by ImThatNerd on 2008-05-30
> **alienexplorers said:**
> Did you try to make a new profile for firefox 2.  Run in terminal:

let the profile manager create its default.user profile.
start up firefox from the profilemanager.
try installing the extensions again.
If it works, shutdown firefox and run firefox -profilemanager again.
delete the default profile.  Start firefox. shutdown.
restart firefox in the normal way.

```
ryan@ryan-desktop:~$ firefox -profilemanager
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
ryan@ryan-desktop:~$ 


```

I got firefox 2.

---

### Post by ImThatNerd on 2008-06-02
Anyone know? I really need help ASAP.

---

### Post by SunnyRabbiera on 2008-06-02
hmm, interesting error.
are you sure these addons have linux compatibility, I know some dont.

---

### Post by iaculallad on 2008-06-02
Had you tried doing this? (Base on Error -203)

Quote from Support.Mozilla.com

```
Corrupt extension files

Corrupt extension configuration files can cause problems when trying to install an extension. Deleting these files will make Firefox recreate them (removing any corruption) the next time it starts. You won't lose your extensions or their settings by deleting these files.

1. From the menu at the top of the Firefox window, select File and then select the Exit menu item. 
2. Go to your [profile folder]("http://support.mozilla.com/en-US/kb/Profiles").
3. Delete the following files:
          * extensions.ini
          * extensions.cache
          * extensions.rdf 
4. Restart Firefox.
```

---

### Post by ImThatNerd on 2008-06-02
> **iaculallad said:**
> Had you tried doing this? (Base on Error -203)

Quote from Support.Mozilla.com

```
Corrupt extension files

Corrupt extension configuration files can cause problems when trying to install an extension. Deleting these files will make Firefox recreate them (removing any corruption) the next time it starts. You won't lose your extensions or their settings by deleting these files.

1. From the menu at the top of the Firefox window, select File and then select the Exit menu item. 
2. Go to your [profile folder]("http://support.mozilla.com/en-US/kb/Profiles").
3. Delete the following files:
          * extensions.ini
          * extensions.cache
          * extensions.rdf 
4. Restart Firefox.
```
Yeah I forgot to close firefox when I deleted them, but it ended working anyways. I did not come across that extensions.ini file but I deleted the other two and closed and reopened firefox and my extensions were there. Thanks a ton.

---

### Post by iaculallad on 2008-06-02
You're welcome, Go Ubuntu.

---

