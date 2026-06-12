---
title: "Ubuntu Software Center NOT working in 11.04"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2011-10-05
Hi,
I've tried everything and scoured the internet for an answer. How do I get Ubuntu Software Center to work? Updating/upgrading in the terminal does nothing. What gives?

---

### Post by wildmanne39 on 2011-10-05
Hi, please run this command in a terminal and post all the errors here:
```
sudo apt-get update && sudo apt-get upgrade
```
Thank you

---

### Post by mikewhatever on 2011-10-05
Perhaps you mean the Software Center doesn't launch or open. If not, what exactly doesn't work?

---

### Post by Ranger_Joe on 2011-10-05
No it launches/opens. But when I search for programs or click on a category, it just sits there and thinks and thinks and thinks. Nothing ever comes up.

Yes, my internet connection works.

---

### Post by ezroller on 2011-10-05
same thing happening to me... it worked one hour ago. now it doesn't even open.

---

### Post by wildmanne39 on 2011-10-05
Hi, the command from post to should give us a clue.
Thank you

---

### Post by ezroller on 2011-10-05
i ran the command in the terminal and now its updating 25 new things, no error. hoewever, when i try to open the software center the windows is white, nothing happens.

---

### Post by dniMretsaM on 2011-10-05
> **ezroller said:**
> i ran the command in the terminal and now its updating 25 new things, no error. hoewever, when i try to open the software center the windows is white, nothing happens.

Do you get any errors when you open the Software Center from the command line? Run this in terminal and post the output:
```
software-center
```

---

### Post by ezroller on 2011-10-05
i had to restart after the update was complete. now it works fine... i guess a simple restart does the thing! thank you

---

### Post by wildmanne39 on 2011-10-05
Hi, open synaptic package manager and see if it is working if so then uninstall software center, restart your computer, then reinstall it.

If that does not work open software center in the terminal, that way if it does not open it will give errors.
```
gksu software-center
```
Thank you

---

### Post by adityaghante on 2011-10-06
> **wildmanne39 said:**
> Hi, please run this command in a terminal and post all the errors here:
```
sudo apt-get update && sudo apt-get upgrade
```Thank you

aditya@Aditya-ThinkPad-R61:~$ sudo apt-get update && sudo apt-get upgrade
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-natty.list
E: The list of sources could not be read.
aditya@Aditya-ThinkPad-R61:~$ 
 this is the error that i get when i invoke that command:(

---

### Post by dniMretsaM on 2011-10-06
> **adityaghante said:**
> aditya@Aditya-ThinkPad-R61:~$ sudo apt-get update && sudo apt-get upgrade
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-natty.list
E: The list of sources could not be read.
aditya@Aditya-ThinkPad-R61:~$ 
 this is the error that i get when i invoke that command:(

Please post the output of this command:
```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-natty.list
```

I /think/ I remember having this issue when I added the Wine PPA.

---

### Post by Deficit on 2011-10-09
hey having a similar problem with ubuntu software uodate but in my case it doesn't download the update when i ran the sugestions form the previous replys in the terminak this message showed up
W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://br.archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://br.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://br.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to br.archive.ubuntu.com:http:

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://br.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to br.archive.ubuntu.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.

never mind find out how to solve it was a server problem just switched from brazil server to us server

---

### Post by shredready on 2011-10-20
> **wildmanne39 said:**
> Hi, open synaptic package manager and see if it is working if so then uninstall software center, restart your computer, then reinstall it.

If that does not work open software center in the terminal, that way if it does not open it will give errors.
```
gksu software-center
```Thank you

thanks I had the same problem I entered gksu software-center  it seems to work but does not have any of my installed software listed

---

### Post by wildmanne39 on 2011-10-20
Hi, if you have synaptic installed I recommend completely removing software center by right clicking on it in synaptic then mark for complete removal then restart your computer, then install it again using synaptic.
Thank you

---

### Post by shredready on 2011-10-20
> **shredready said:**
> thanks I had the same problem I entered gksu software-center  it seems to work but does not have any of my installed software listed


this is the error I get

2011-10-20 22:49:32,851 - softwarecenter.db - ERROR - failed to add apt-xapian-index
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/database.py", line 158, in _get_new_xapiandb
    axi = xapian.Database("/var/lib/apt-xapian-index/index")
  File "/usr/lib/python2.7/dist-packages/xapian/__init__.py", line 3408, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
DatabaseOpeningError: Couldn't stat '/var/lib/apt-xapian-index/index' (No such file or directory)
2011-10-20 22:49:34,044 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-10-20 22:49:34,430 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2011-10-20 22:49:52,806 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2011-10-20 22:49:54,713 - softwarecenter.db - ERROR - failed to add apt-xapian-index
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/database.py", line 158, in _get_new_xapiandb
    axi = xapian.Database("/var/lib/apt-xapian-index/index")
  File "/usr/lib/python2.7/dist-packages/xapian/__init__.py", line 3408, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
DatabaseOpeningError: Couldn't stat '/var/lib/apt-xapian-index/index' (No such file or directory)
2011-10-20 22:49:54,961 - softwarecenter.db.categories - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2011-10-20 22:49:55,813 - softwarecenter.db.categories - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2011-10-20 22:49:57,542 - softwarecenter.ui.gtk3.views.catview_gtk - WARNING - No 'new' category found!!
2011-10-20 22:49:57,970 - softwarecenter.db.categories - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2011-10-20 22:49:59,601 - softwarecenter.db - ERROR - failed to add apt-xapian-index
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/database.py", line 158, in _get_new_xapiandb
    axi = xapian.Database("/var/lib/apt-xapian-index/index")
  File "/usr/lib/python2.7/dist-packages/xapian/__init__.py", line 3408, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
DatabaseOpeningError: Couldn't stat '/var/lib/apt-xapian-index/index' (No such file or directory)
2011-10-20 22:50:01,299 - softwarecenter.db.categories - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2011-10-20 22:50:04,556 - softwarecenter.db.categories - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2011-10-20 22:50:06,186 - softwarecenter.db.categories - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2011-10-20 22:50:12,583 - softwarecenter.backend - WARNING - axi can not be updated 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.debian.AptXapianIndex was not provided by any .service files'

---

### Post by wildmanne39 on 2011-10-23
Hi, I did some research but I did not find an answer to your problem and I am out of ideas, I am sorry.

---

### Post by Unterseeboot_234 on 2011-10-26
> **wildmanne39 said:**
> Hi, if you have synaptic installed I recommend completely removing software center by right clicking on it in synaptic then mark for complete removal then restart your computer, then install it again using synaptic.
Thank you

/synaptic will inform you this action affects other packages, for details click down arrow.

>Desktop

If you continue with that, you will fry your Ubuntu.

//////////////////////////

I am beginning to suspect ndiswrapper (used for wireless connectivity). I happened to notice that ndiswrapper lives on through a re-format and a Ubuntu Natty install. Not only will ndiswrapper fail to connect a multi-core CPU, it makes any Ubuntu box unstable over time.

---

