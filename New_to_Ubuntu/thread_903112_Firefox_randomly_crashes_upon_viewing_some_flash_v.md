---
title: "Firefox randomly crashes upon viewing some flash videos. Where are the error logs?"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by inktri on 2008-08-27
Firefox seemingly randomly crashes upon viewing some flash videos. Where are the Firefox error logs located?

---

### Post by Crafty Kisses on 2008-08-28
Should be in this folder:
```
/.firefox
```

---

### Post by inktri on 2008-08-28
thanks for the response, but:

/.firefox didn't exist, so I tried /.mozilla/firefox which exists but where are the error files? :S

---

### Post by sdennie on 2008-08-28
I don't know if there are any but, if there were I don't think they would give you useful information.  It's not uncommon for Flash to regularly crash Firefox and there is nothing really that can be done about it because the Flash player is created by Adobe and closed source.  The only real recourse to your problem is to politely e-mail Adobe and ask them if they will improve their Flash support on linux.

---

### Post by Bakon Jarser on 2008-08-28
Yup, everybody has that problem.  Hopefully these will be fixed when flash 10 comes out.

---

### Post by pi.boy.travis on 2008-08-28
Nothing you can do if Adobe keeps it closed source. . . 

We are Linux users living in a Windows world. . .

---

### Post by MegaJim on 2008-08-28
Well, firefox could try to do something a bit smarter like running flash in a separate thread/container so that at least it could fail gracefully rather than needing to be killed by sysman.

---

### Post by chrisod on 2008-08-28
If you start Firefox from the command line you'll see the error messages in your terminal window when it crashes. For me, it's always a seg fault, with is particularly unhelpful.

I'm on the RC candidate of Flash 10 and the crashes do seem less frequent.

---

### Post by vierdreieins on 2008-08-28
> **MegaJim said:**
> Well, firefox could try to do something a bit smarter like running flash in a separate thread/container so that at least it could fail gracefully rather than needing to be killed by sysman.

Agreed, Opera handles it much more gracefully, and I switched to that full time. There are far too many flash videos I get regularly that Firefox has been rendered almost worthless to me.

---

### Post by JaspSoft on 2008-08-28
I'm starting to get really sick of firefox crashing. I find myself restarting firefox dozens of times a day. (Should a plugin really be allowed to take down the browser anyway?)

Perhaps more work should be put into gnash.

---

### Post by stonecoldjha on 2008-08-28
i too had the same niggling problem.and now it is all solved,thanks to the person who gave me the following link:
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")
just do all that is described,it installs flash 10.i tell you it has almost ben a month and not a single damn crash occurred since then.

---

### Post by t0p on 2008-08-28
> **Bakon Jarser said:**
> Yup, everybody has that problem.  Hopefully these will be fixed when flash 10 comes out.

It certainly has been improved!!  [Click here]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") to learn how to install Flash 10 now!

---

### Post by Bakon Jarser on 2008-08-28
> **stonecoldjha said:**
> i too had the same niggling problem.and now it is all solved,thanks to the person who gave me the following link:
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")
just do all that is described,it installs flash 10.i tell you it has almost ben a month and not a single damn crash occurred since then.

I'll certainly give this a try.  I've followed one of his guides before with great success.  Thanks.

---

### Post by Slug71 on 2008-08-28
It was doing it to me today wicked bad too, had all these little boxes popping up too.
I uninstalled firefox 3.0.1 from synaptic and removed the flashplugin-nonfree from there too. Restarted then reinstalled firefox and then flash again and im not having any problems since. I havent rebooted the pc since then though. So hopefully it will still work fine tomorrow.

---

### Post by kansasnoob on 2008-08-28
Some have found that just installing Flash 10 beta works (after removing flsah 9). That's never solved it for me.

What has worked for me is:

```
apt-get remove --purge flashplugin-nonfree libflashsupport
```

```
apt-get install nspluginwrapper
```

```
apt-get install libflashsupport
```

```
apt-get install flashplugin-nonfree
```

If those commands throw any errors post the outcome.

---

### Post by lswb on 2008-08-28
Try uninstalling Adobe flashplayer and install either version 9r124 or 10b218 (the 1st version 10 beta release for linux) The 2nd ver 10 beta and the recent release version 10 are causing many reports of firefox crashes. That has also been my personal experience. Running either ver 9 or 10b218 I have no crashes with any flash content.

---

### Post by lovinglinux on 2008-08-28
> **JaspSoft said:**
> I'm starting to get really sick of firefox crashing. I find myself restarting firefox dozens of times a day. (Should a plugin really be allowed to take down the browser anyway?)

Perhaps more work should be put into gnash.

I can complain, because Firefox 3 crashing a lot on Windows was the primary motive that made me switch to Linux. Perhaps the best thing you could do is sending bug reports to Mozilla.

> **MegaJim said:**
> Well, firefox could try to do something a bit smarter like running flash in a separate thread/container so that at least it could fail gracefully rather than needing to be killed by sysman.

I know is not a solution, but you could use NoScript extension to block all flash from running automatically and enable just the necessary ones. If you visit a particular flash site a lot you could also consider installing Prism and converting the site to Prism application. I'm almost sure that if flash crashes the Prism application, Firefox will continue to run smoothly.

---

### Post by tuxxy on 2008-08-28
What flash version are you running, how did you install it?

---

### Post by nicedude on 2008-08-29
I am having nice success with Flash 10 as well, but I just installed mine from a simple deb package and didn't have to do anything like what those install guides suggested. I just removed Flash 9 then ran the deb and it was done and has worked fine since.


So finding a deb might be easier for some people and it is also quicker for sure.

---

### Post by tuxxy on 2008-08-29
Flash 9 is usually fine for me :confused:

---

### Post by kansasnoob on 2008-08-29
[http://phorolinux.com/how-to-install-adobe-flash-player-10-beta-2-on-ubuntu-804-hardy-heron.html](http://phorolinux.com/how-to-install-adobe-flash-player-10-beta-2-on-ubuntu-804-hardy-heron.html)

But I'm telling you ................... loud and clear ...................follow my last instructions with either flash 9 or 10!

Look here:

[http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox](http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox)

Luckily now everything you need is in the Ubuntu repos.

---

### Post by MegaJim on 2008-08-29
> **lovinglinux said:**
> I can complain, because Firefox 3 crashing a lot on Windows was the primary motive that made me switch to Linux. Perhaps the best thing you could do is sending bug reports to Mozilla.



I know is not a solution, but you could use NoScript extension to block all flash from running automatically and enable just the necessary ones. If you visit a particular flash site a lot you could also consider installing Prism and converting the site to Prism application. I'm almost sure that if flash crashes the Prism application, Firefox will continue to run smoothly.

I use flashblock and noscript, but it's hardly the point.  I want my Internets !

---

### Post by NWAdawg on 2008-08-29
kansasnoob thanks for the link. I upgraded to flashplayer 10. So far my Firefox hasn't crash yet.

---

