---
title: "Lightdm theme not showing"
date: 2011-08-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by DustinCasler on 2011-08-27
I have installed Oneiric Alpha 3 and all of the updates as of tonight 08/26/2011 and I can't seem to get the new LightDM theme to appear. Has anyone else had this issue?

---

### Post by cariboo on 2011-08-27
I moved this to a thread of it's own, so that it is more visible,

---

### Post by Harry33 on 2011-08-27
> **DustinCasler said:**
> I have installed Oneiric Alpha 3 and all of the updates as of tonight 08/26/2011 and I can't seem to get the new LightDM theme to appear. Has anyone else had this issue?

What greeter have you installed?
Try the default lightdm-gtk-greeter.

---

### Post by DustinCasler on 2011-08-27
I'm going to try to install again from today's daily build. If I still have the same issue or have to install again from Alpha 3 i'll try that. Thanks for the tip.

---

### Post by ratcheer on 2011-08-27
My system does not seem to display the lightdm theme, either. At this point in time, this is the only major problem I am having with Oneiric. I checked, and lightdm-gtk-greeter is installed. lightdm is definitely running:

```
ps -ef|grep lightdm
root       928     1  0 12:25 ?        00:00:00 lightdm
root       987   928  2 12:25 tty7     00:00:16 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
tim       1979  1924  0 12:37 pts/0    00:00:00 grep --color=auto lightdm
```I did a Google search to try to find instructions on setting up lightdm. All I can find is a lot of stuff saying "lightdm is now available in Oneiric" and stuff about how wonderful it is. It is not wonderful if it's not displaying. Even the lightdm site itself does not have any instructions for using it.

When I start Oneiric, I just get a login dialog that looks like a very old version of Windows NT. :(

Tim

---

### Post by Harry33 on 2011-08-27
> **ratcheer said:**
> My system does not seem to display the lightdm theme, either. At this point in time, this is the only major problem I am having with Oneiric. I checked, and lightdm-gtk-greeter is installed. lightdm is definitely running:

```
ps -ef|grep lightdm
root       928     1  0 12:25 ?        00:00:00 lightdm
root       987   928  2 12:25 tty7     00:00:16 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
tim       1979  1924  0 12:37 pts/0    00:00:00 grep --color=auto lightdm
```I did a Google search to try to find instructions on setting up lightdm. All I can find is a lot of stuff saying "lightdm is now available in Oneiric" and stuff about how wonderful it is. It is not wonderful if it's not displaying. Even the lightdm site itself does not have any instructions for using it.

When I start Oneiric, I just get a login dialog that looks like a very old version of Windows NT. :(

Tim

Do you have both Gdm and LightDM installed?
Have you tried to purge all lightDM packages and then do a clean installation of them with the proper configuring.  The installation should ask to do that.

---

### Post by ratcheer on 2011-08-27
Cool. Thank you Harry. Uninstalling and reinstalling lightdm and ubuntu-desktop seems to have resolved the problem. I now get a nice, modern lightdm login screen after starting Oneiric. :)

Tim

---

### Post by Harry33 on 2011-08-27
> **ratcheer said:**
> Cool. Thank you Harry. Uninstalling and reinstalling lightdm and ubuntu-desktop seems to have resolved the problem. I now get a nice, modern lightdm login screen after starting Oneiric. :)

Tim

Well nice to hear that did help. :P

---

### Post by garvinrick4 on 2011-08-27
Already solved.

---

### Post by .... on 2011-08-27
The best thing about lightdm being screwed up is that it turned me on to the DM for lxde.

---

### Post by unrater on 2011-08-28
Hi!

I'm having the same problem, something like that! I already purged lightdm and ubuntu-desktop and my system is updated! this is how it is showing:
[[IMG]http://i.imgur.com/F9kn0l.png[/IMG]]("http://i.imgur.com/F9kn0.png")

Well, I don't like this new lightdm, it does not have no support online (I only get results on google about how good it is) and I don't know any way to change something on it :\

Hope you know what is this problem :(

---

### Post by lucazade on 2011-08-28
> **unrater said:**
> 
Well, I don't like this new lightdm, it does not have no support online (I only get results on google about how good it is) and I don't know any way to change something on it :\


This is not the new lightdm theme but only a refuse of an old installation of Oneiric.
Latest livecd ships with the new and updated theme, so, instead of fighting with already fixed bugs, I suggest to reinstall oneiric (and to do this frequently up to release).

---

### Post by unrater on 2011-08-28
Downloaded it yesterday!  ;)

---

### Post by lucazade on 2011-08-28
well.. strange, installed yesterday daily on different machines and lightdm is ok here.

---

### Post by webme on 2011-08-28
> **unrater said:**
> Hi!

I'm having the same problem, something like that! I already purged lightdm and ubuntu-desktop and my system is updated! this is how it is showing:
[[IMG]http://i.imgur.com/F9kn0l.png[/IMG]]("http://i.imgur.com/F9kn0.png")

Well, I don't like this new lightdm, it does not have no support online (I only get results on google about how good it is) and I don't know any way to change something on it :\

Hope you know what is this problem :(

You need to install "unity-greeter" (sudo apt-get install unity-greeter)

---

### Post by bash on 2011-08-28
> **webme said:**
> You need to install "unity-greeter" (sudo apt-get install unity-greeter)

Just to add to this: If you have the package *unity-greeter* installed and it still uses the other theme, try setting the new theme manually. To do this edit or create */etc/lightdm/lightdm.conf* and add the following:

```

[SeatDefaults]
greeter-session=unity-greeter

```

---

### Post by mc4man on 2011-08-28
> **bash said:**
> Just to add to this: If you have the package *unity-greeter* installed and it still uses the other theme, try setting the new theme manually. To do this edit or create */etc/lightdm/lightdm.conf* and add the following:

```

[SeatDefaults]
greeter-session=unity-greeter

```
You can change greeters from the  cli (do make sure the greeter is actually installed
-g sets greeter
Ex.'s

```
sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter
```

```
sudo /usr/lib/lightdm/lightdm-set-defaults -g lightdm-gtk-greeter


```

---

### Post by colinnc on 2011-08-28
> **bash said:**
> Just to add to this: If you have the package *unity-greeter* installed and it still uses the other theme, try setting the new theme manually. To do this edit or create */etc/lightdm/lightdm.conf* and add the following:

```

[SeatDefaults]
greeter-session=unity-greeter

```

Installing the unity-greeter package and updating the lightdm.conf fixed the issue for me.

Thanks everyone!

---

