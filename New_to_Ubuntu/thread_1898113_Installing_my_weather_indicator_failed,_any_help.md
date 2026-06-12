---
title: "Installing my weather indicator failed, any help?"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by xverxs on 2011-12-20
Been having trouble trying to install my-weather-indicator. When I added the ppa: "ppa:atareao/atareao" through terminal it gave me this output.

Terminal```
sudo apt-get install my-weather-indicator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-dateutil python-lxml
Suggested packages:
  python-lxml-dbg
The following NEW packages will be installed:
  my-weather-indicator python-dateutil python-lxml
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,671 kB of archives.
After this operation, 5,882 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package python-dateutil.
(Reading database ... 90%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'plymouth-theme-lubuntu-text': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Any idea of what I should try to fix this? :confused:

---

### Post by Frogs Hair on 2011-12-20
Hello and Welcome 

Is the PPA compatible with Lubuntu ? I couldn't find anything on the Launch pad page to indicate that it is or isn't . I did use the PPA with Ubuntu 11.04 . [https://launchpad.net/~atareao/+archive/atareao](https://launchpad.net/~atareao/+archive/atareao)

---

### Post by amjjawad on 2011-12-22
> **xverxs said:**
> Been having trouble trying to install my-weather-indicator. When I added the ppa: "ppa:atareao/atareao" through terminal it gave me this output.

Terminal```
sudo apt-get install my-weather-indicator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-dateutil python-lxml
Suggested packages:
  python-lxml-dbg
The following NEW packages will be installed:
  my-weather-indicator python-dateutil python-lxml
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,671 kB of archives.
After this operation, 5,882 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package python-dateutil.
(Reading database ... 90%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'plymouth-theme-lubuntu-text': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```Any idea of what I should try to fix this? :confused:

Hello and Welcome to Ubuntu Forum :)

Thanks for using Lubuntu. I'll do my best to help you.

First of all, I need more information (check my signature for how to write informative thread).

Please open LXTerminal and post the output of:

1- ```
lsb_release -a
```2- ```
uname -r
```When posting, please wrap up the text with "CODE" tags:

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]


Also, please run these commands and see if everything is ok:

```
sudo apt-get clean
```
```
sudo apt-get update
```


By the way, I have added a weather indicator which is in the repositories already. If you are interested, let me know and I'll help you with that but let's first make sure everything is ok with your system.

---

