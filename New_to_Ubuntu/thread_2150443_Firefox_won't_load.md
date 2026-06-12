---
title: "Firefox won't load"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by markjmcg on 2013-06-01
Hi,
New to ubuntu 12.10 & I am struggling to get Firefox to run. Error is: " Your profile cannot be loaded. It may be missing or inaccessible".

I have tried the following (searching via 'google'):

1. removed .mozilla dir
2. sudo chown $USER:$USER $HOME
3. uninstalled & reinstalled from cmd line, using, " [FONT=Ubuntu Mono]sudo apt-get purge/install firefox firefox-globalmenu firefox-gnome-support "

I run sudo firefox and it works, but not what I would like, would prefer an icon for the sidebar.

Any help would be appreciated. Thx

Mark
[/FONT]

---

### Post by flanagan on 2013-06-01
I would suggest following the guidance at [https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles]("https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles") to create a new empty profile before starting Firefox (without the sudo). When you deleted the .mozilla folder, you also deleted whatever profiles previously existed.

---

### Post by claracc on 2013-06-01
It is not advisable to run firefox using sudo since as you use your user profile, you will change the ownership of certain  files in the user profile. You better use gksudo, as it is addressed in this informative link:[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Changing the firefox profile hast to fix your problem

---

### Post by markjmcg on 2013-06-01
thx for the replies, will try :)

Mark

---

