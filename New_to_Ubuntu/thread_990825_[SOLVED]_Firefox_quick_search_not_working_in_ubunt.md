---
title: "[SOLVED] Firefox quick search not working in ubuntu?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by bhadotia on 2008-11-23
Ever since I installed ubuntu 8.10 [this]("http://en.wikipedia.org/wiki/Features_of_Mozilla_Firefox#Find_as_you_type") feature is not working for me.

Has anyone else noticed it? Its working fine with my firefox (3.04) in windows.

Or, is this a bug I don't know about.

---

### Post by ibuclaw on 2008-11-23
I have not come across this whilst working in 8.10.

Everything seems to be functioning as expected for me.


Only option I can think to suggest is for you to check your **about:config** configurations.

Though I wouldn't know what to look for.

Here is my version and apt-cache policy:
[PHP]
$ firefox --version
Mozilla Firefox 3.0.4, Copyright (c) 1998 - 2008 mozilla.org

$ apt-cache policy firefox-3.0
firefox-3.0:
  Installed: 3.0.4+nobinonly-0ubuntu0.8.10.1
  Candidate: 3.0.4+nobinonly-0ubuntu0.8.10.1
  Version table:
 *** 3.0.4+nobinonly-0ubuntu0.8.10.1 0
        500 http://gb.archive.ubuntu.com intrepid-updates/main Packages
        500 http://security.ubuntu.com intrepid-security/main Packages
        100 /var/lib/dpkg/status
     3.0.3+nobinonly-0ubuntu2 0
        500 http://gb.archive.ubuntu.com intrepid/main Packages
[/PHP]

Regards
Iain

---

### Post by nhasian on 2008-11-23
yes i tested this feature and it worked fine to me too.

---

### Post by Michael.Godawski on 2008-11-23
There was a bug some years ago as it seems:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/8383](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/8383)

What happens if you add this feature manually like shown here:
[https://addons.mozilla.org/en-US/firefox/addon/3650](https://addons.mozilla.org/en-US/firefox/addon/3650)

---

### Post by bhadotia on 2008-11-23
Hi all and thanks  for replies. 
@Michael
I installed the addon you pointed me to. But this is  still not working for me. 

@Iain
How come you have the 3.04 version? There is no upgrade here (or that my mirror is behind the schedule a few days). 
And I will try fiddling with about:config a bit.

@nhasian
Thanks for cofirming.

---

### Post by bhadotia on 2008-11-23
Solved: Just looked at my preferences in the Advanced>General tab and found that "Search for text when I start typing was disabled". Actually looking at the about:config page gave the hint to that it was disabled:
```
accessibility.typeaheadfind;false
```
This is the default option and I left it that way this time (unlike I do everytime).

---

