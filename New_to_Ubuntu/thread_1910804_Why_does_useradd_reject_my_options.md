---
title: "Why does useradd reject my options?"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by iamthepiguy on 2012-01-17
I am trying to make a new system user called "vnc" with home in */home/.manage/vnc/*. However, the useradd command keeps rejecting my options. I have tried several different orders and using both "--something" and "-(one letter)" options.

Here is my line in bash:
```
sudo useradd -r -g manage -m "/home/.manage/vnc" -k "/home/.manage/.skel" vnc
```

When I enter this, it just returns the useradd help text, nothing more.

---

### Post by Krytarik on 2012-01-17
This should work:
```
sudo useradd -r -g manage -m **-d** "/home/.manage/vnc" -k "/home/.manage/.skel" vnc
```> **-d, --home HOME_DIR**
           The new user will be created using HOME_DIR as the value for the
           user's login directory. The default is to append the LOGIN name to
           BASE_DIR and use that as the login directory name. The directory
           HOME_DIR does not have to exist but will not be created if it is
           missing.

**-m, --create-home**
           Create the user's home directory if it does not exist. The files
           and directories contained in the skeleton directory (which can be
           defined with the -k option) will be copied to the home directory.

           By default, if this option is not specified and CREATE_HOME is not
           enabled, no home directories are created.[http://manpages.ubuntu.com/manpages/oneiric/en/man8/useradd.8.html](http://manpages.ubuntu.com/manpages/oneiric/en/man8/useradd.8.html)

Regards.

---

### Post by iamthepiguy on 2012-01-17
Thank you, I failed to notice that one was the variable and one merely overrode the default.

---

