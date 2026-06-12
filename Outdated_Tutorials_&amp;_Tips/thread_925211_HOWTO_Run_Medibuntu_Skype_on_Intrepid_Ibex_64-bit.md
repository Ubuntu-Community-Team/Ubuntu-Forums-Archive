---
title: "HOWTO: Run Medibuntu Skype on Intrepid Ibex 64-bit"
date: 2008-09-20
forum: Outdated Tutorials &amp; Tips
---

### Post by hyper_ch on 2008-09-20
[SIZE="6"]HOWTO: Run Medibuntu Skype on Intrepid Ibex 64-bit[/SIZE]

[SIZE="5"]Introduction[/SIZE]

Skype is only available as 32-bit application. Even when you use the Medibuntu repos it's only 32-bit. However the current Medibuntu build lacks a few 32-bit libraries as dependencies. This can be "easily" solved by manually adding the required libs.

[SIZE="5"]The Script[/SIZE]

Well, first the little script that makes it work:
```

#!/bin/bash

mkdir /tmp/skype
mkdir /tmp/skype/tmp
cd /tmp/skype

wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.4.2-0ubuntu2_i386.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.4.2-0ubuntu2_i386.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.4.2-0ubuntu2_i386.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.4.2-0ubuntu2_i386.deb
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.4.2-0ubuntu2_i386.deb

dpkg -x libqtgui4_4.4.2-0ubuntu2_i386.deb /tmp/skype/tmp
dpkg -x libqt4-network_4.4.2-0ubuntu2_i386.deb /tmp/skype/tmp
dpkg -x libqtcore4_4.4.2-0ubuntu2_i386.deb /tmp/skype/tmp
dpkg -x libqt4-xml_4.4.2-0ubuntu2_i386.deb /tmp/skype/tmp
dpkg -x libqt4-dbus_4.4.2-0ubuntu2_i386.deb /tmp/skype/tmp

cp -a /tmp/skype/tmp/usr/lib/* /usr/lib32/

```

[SIZE="5"]Step 1: Install Skype from Medibuntu[/SIZE]

First, install Skype from the Medibuntu repos. Go to the website here and follow the Repository Howto link: [http://www.medibuntu.org/](http://www.medibuntu.org/)

Once you have done that, get Skype by issuing:

```

sudo apt-get install skype

```

[SIZE="5"]Step 2: Run my script[/SIZE]

Now open a text file (e.g. script.sh), paste the content of the script in there. Once done, run it by issuing:

```

sudo sh script.sh

```

[SIZE="5"]Step 3: Enjoy[/SIZE]

That's all that is required. Thx goes also to **jdong** for giving me a few pointers.

[SIZE="5"]Step 4: Pulseaudio[/SIZE]

If you continue having problems on getting this to run and you are running Ubuntu or Xubuntu (or any flavour with PulseAudio), you also need to do this here:

```


Another workaround that works for me:
1. Create /etc/ld.so.conf.d/alsa32.conf with the following contents:
/usr/lib32/alsa-lib

2. Create /etc/ld.so.conf.d/alsa64.conf with the following contents:
/usr/lib/alsa-lib

3. sudo ldconfig

4. Open /usr/share/alsa/pulse.conf in the editor and remove the "/usr/lib/alsa-lib/" prefix from the libasound_module_conf_pulse.so file.

```
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6)

Thx goes to Slavik for pointing this out and to dmitry to actually post that solution on launchpad.

---

### Post by iamjfarrell on 2008-09-22
I followed your instructions exactly and it did not work for some reason. I had skype working on 8.04 but now that I upgraded it doesn't seem to want to work! Help Please!

---

### Post by hyper_ch on 2008-09-22
it seems, that I had, with some other package, another library isntalled that's required...

run this additionally and I'll update my code up there:

```

cd /tmp/skype
wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.4.1-0ubuntu2_i386.deb
dpkg -x libqt4-dbus_4.4.1-0ubuntu2_i386.deb /tmp/skype/tmp
sudo cp -a /tmp/skype/tmp/usr/lib/* /usr/lib32/

```

---

### Post by iamjfarrell on 2008-09-24
I am now getting 404 errors when I try to run your script. I have to switch to windows to run skype! :( Let me know if I can help in any way.

---

### Post by hyper_ch on 2008-09-24
plz post the output

did you reboot the system meanwhile?

---

### Post by benjym on 2008-09-24
I followed the instructions and got the following output from each file i tried to download.

--2008-09-25 07:59:35--  [http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.4.1-0ubuntu2_i386.deb](http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.4.1-0ubuntu2_i386.deb)
Resolving mirror.switch.ch... 130.59.10.36
Connecting to mirror.switch.ch|130.59.10.36|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2008-09-25 07:59:37 ERROR 404: Not Found.

Tried again with versions 4_4.4.2-0 and it works. Seems that those libraries have been updated in the last couple of days.

---

### Post by hyper_ch on 2008-09-24
ah, today's updates changed the version of all those files...

--> [http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/q/qt4-x11/](http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/q/qt4-x11/)

Run the new altered script now.

---

### Post by benjym on 2008-09-25
the latest script works to install skype, and it loads. when i try to login, however, i get the following errors:

ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)

any ideas?

---

### Post by iamjfarrell on 2008-09-25
There we go! now it is working, but whenever I try to make a call it just closes.

---

### Post by hyper_ch on 2008-09-25
> **benjym said:**
> the latest script works to install skype, and it loads. when i try to login, however, i get the following errors:

ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)

any ideas?
a problem with pulseaudio... using Kubuntu I don't run it.


> **iamjfarrell said:**
> There we go! now it is working, but whenever I try to make a call it just closes.
run skype from the command line and then you'll get some output of what's going on.

---

### Post by iamjfarrell on 2008-09-25
When I ran Skype in the terminal this is what I got when I made a call and it crashed...
```
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)

```

---

### Post by moremix on 2008-09-25
I get the same error :
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)


But I think this may be because of a more general error in the PulseAudio/ALSA in which case it may depend more on the bug fix than on anything else:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693)

---

### Post by iamjfarrell on 2008-09-26
> **moremix said:**
> I get the same error :
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)


But I think this may be because of a more general error in the PulseAudio/ALSA in which case it may depend more on the bug fix than on anything else:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693)

Is there any workarounds? I see a few posted on the BUG site, but I don't know if they will work. I guess I'll give it a shot and report back!

---

### Post by hyper_ch on 2008-09-26
disable pulseaudio... use kubuntu...

---

### Post by iamjfarrell on 2008-09-26
This workaround worked for me! 

**Temporary workaround:** in the /usr/share/alsa/alsa.conf comment out the line that says:
"/usr/share/alsa/pulse.conf"

---

### Post by Gedemins on 2008-09-26
worked for me too, but you cannot call then, only chat.

---

### Post by slavik on 2008-09-27
a workaround has been posted by dmitriy, I have tried it and it works like a charm. :)

permalink:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6)

> Another workaround that works for me:
1. Create /etc/ld.so.conf.d/alsa32.conf with the following contents:
/usr/lib32/alsa-lib

2. Create /etc/ld.so.conf.d/alsa64.conf with the following contents:
/usr/lib/alsa-lib

3. sudo ldconfig

4. Open /usr/share/alsa/pulse.conf in the editor and remove the "/usr/lib/alsa-lib/" prefix from the libasound_module_conf_pulse.so file.


---

### Post by L3oN on 2008-10-01
Tnx a lot! :)

---

### Post by hyper_ch on 2008-10-03
There has been a ia32libs update and on the bug site people have reported it to be working now out-of-the-box with that update. Anyone can confirm this?

---

### Post by Cuppa-Chino on 2008-10-05
No dice. Just updated to latest medibuntu (2.0.0.72-0medibuntu3 from today)  still get the alsa error:

```
~$ skype
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)

```

---

### Post by hyper_ch on 2008-10-05
well, that's not the fault of skype but of pulseaudio ;)

---

### Post by Tiftof on 2008-10-07
script not working anymore because of dead links? I would like to try it out. Just trying out 64bit ubuntu

---

### Post by hyper_ch on 2008-10-07
you shouldn't be needing it anymore.

---

### Post by Tiftof on 2008-10-07
> **hyper_ch said:**
> you shouldn't be needing it anymore.

Indeed not... thanks anyway!

---

