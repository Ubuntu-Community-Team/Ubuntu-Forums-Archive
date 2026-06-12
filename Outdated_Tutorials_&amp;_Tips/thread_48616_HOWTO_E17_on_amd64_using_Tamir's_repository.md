---
title: "HOWTO: E17 on amd64 using Tamir's repository"
date: 2005-07-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Tamir on 2005-07-13
**## Based** [Tab's howto](http://www.ubuntuforums.org/showthread.php?t=4610) 

Hi all :) 
I made E17 CVS .debs for amd64 using smoon's script, and uploaded to my repository (thanks for smoon that hosted me!).

:arrow: First, add my repository to your **/etc/apt/sources.list** :

- deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) hoary main

:arrow: Now create this file:
```
gedit /etc/apt/preferences
```

and past these lines into:
```
Package: enlightenment
Pin: version 0.16.999.*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999.*
Pin-Priority: 999
```
it tells it to prefer the latest version of Enlightenment

:arrow: a little update:
```
apt-get update
``` 

:arrow: You can install now the basic enlightenment by:
```
apt-get install enlightenment eutils
```
:arrow: restart X. by:
```
ctrl+alt+Backspace
``` 

and log into Elightenment using gdm\kdm\entrance  :-P 

:arrow: you can also install extra EFL programs & E modules:
```
apt-get install emodules engage entrance eclair elicit entice examine evidence erss iconbar eclips
```
# You can only install evidence from this repository because  source forge made not an amd64 package.

**emodules** - These add functionality and eye-candy to the Enlightenment desktop outside of those included in E.
**engage** - An OSX-style dock.
**entrance** - Login manager.
**eclair** - Media player.
**elicit** - Magnifier/color dropper.
**entice** - Image viewer.
**examine** - Configuration utility.
**eclips** - Another image viewer.
**evidence** - plugin-based enlightenment/GTK2 file-manager

For Enlightenment themes, backgrounds, and more visit  [Get-E.org](http://get-e.org)and the [Edevelop Forum](http://www.edevelop.org/forum/).

\\ [COLOR=Green]Update - package eclips-0.0.4 is ready to install[/COLOR]

---

### Post by jerrybme on 2005-07-21
That's for compiling e17!

 I used your how to but when I try and log into enlightenment it throws an error complaining it can't find libedb.so.1 I did a seach for libegdb and didn't find it.

I installed all of the extra EFL programs & E modules, without seeing any errors. Any suggestions?

Thanks

**Edit**
Ok, I found it by searching synaptic for libedb and installed the package. Now E17 loads fine.

Thanks again for compiling this for us 64 bit users!

---

### Post by Tamir on 2005-07-24
Yeah I forget to add some depencies to the packages :)
The next version will include all depencies  :-P

---

### Post by xodeus on 2005-09-06
Now I got it working. Looks really nice.

---

### Post by srss on 2005-09-07
I cant install eutils because libe do not install. Althoug I have E17, libe doesn't see it. It request for E16. Any ideas?

Thanks,

---

### Post by acariquara on 2005-09-17
apparently there is a problem with libxine1

libemotion0:
 Depends: libxine1 (>=1-rc3a) but it is not installable

that makes a cascading dependency problem - could not install eutils

any help?

---

### Post by srss on 2005-09-18
Thanks!

Well, I think I'll have to wait then.

:c)

---

### Post by dp_wiz on 2006-08-06
Any updates? Repository has moved, and hoary switched to breezy and then dapper...

---

### Post by Erzei on 2006-10-22
> **dp_wiz said:**
> Any updates? Repository has moved, and hoary switched to breezy and then dapper...

Yes.. Please if someone can give a new repository...

:mrgreen:

---

### Post by tomdkat on 2007-03-11
Is this repository now dead?  

Peace...

---

