---
title: "after installing updates, i get an error message.."
date: 2020-05-12
forum: New to Ubuntu
---

### Post by joe12122 on 2020-05-12
Hi.  I&#8217;m getting this error message: Unable to create io-slave, klauncher said; Error loading &#8216;/usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kio/file,so&#8221;..   How to now proceed?  PROBLEM SOLVED.  I was forgetting to turn off the computer at the end of day.  All good now.

---

### Post by monkeybrain20122 on 2020-05-13
[https://forum.manjaro.org/t/unable-to-create-io-slave-klauncher-said-error-loading-usr-lib-qt-plugins-kf5-kio-file-so/25866](https://forum.manjaro.org/t/unable-to-create-io-slave-klauncher-said-error-loading-usr-lib-qt-plugins-kf5-kio-file-so/25866)


Oh, didn't see that you solved the problem already.

---

### Post by vicsar on 2020-05-13
Turning  off the computer at the end of day hardly sounds like a solution, of course it depends on the environment where you use it... but still. Now, the post above explains that:
> [COLOR=#121112][FONT=&amp]That happens because Qt(Dolphin) loads this plugin, then you do an update and Qt conflicts the loadup of the new version, because its still holding the old version in RAM.[/FONT][/COLOR]
and that you should 
> run ```
dbus-launch dolphin
```
I am bringing the solution here for redundancy, in case the other gets deleted.

):P

---

