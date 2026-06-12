---
title: "cairo dock"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-07-22
how can i install the cairo dock,i tried using synaptic....but it is not there.

---

### Post by overdrank on 2008-07-22
> **stonecoldjha said:**
> how can i install the cairo dock,i tried using synaptic....but it is not there.

Hi and this link should help
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by billgoldberg on 2008-07-22
To download this dock, visit [this site]("http://developer.berlios.de/project/showfiles.php?group_id=8724") and download &#8220;cairo-dock_v1.5.6_i686.deb&#8221; and &#8220;cairo-dock-plug-ins_v1.5.6_i686.deb&#8220;.

First install the dock, then the plugin package.

Install them by double-clicking the file.

You&#8217;ll need to enter your password. Then press the big button on the top right.

After you installed both packages, go to &#8220;applications -> system tools -> cairo-dock&#8221;.

You&#8217;ll be greeted by a little wizard that will help you select the theme, &#8230;

You can easily change it&#8217;s option by right-click the dock, go to &#8220;cairo-dock&#8221; and press &#8220;configure&#8217; or &#8220;manage themes&#8221;.

To start the dock when you boot up your pc, go to &#8220;system -> preferences -> sessions&#8221;, press &#8220;add&#8221; and in the middle field enter &#8220;cairo-dock&#8221; (without the &#8221; &#8220;). You can make up what you put in the other fields.

*(taken from my customizing Ubuntu guide)*

---

### Post by overdrank on 2008-07-22
> **billgoldberg said:**
> 
*(taken from my customizing Ubuntu guide)*

Thats right I forgot and is in the FAQ's in my signature. :KS

---

### Post by BoarderX2k3 on 2008-07-22
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=535383]("http://ubuntuforums.org/showthread.php?t=535383").

AWN is better supported and easier to install/configure. But it's not necessarily the better window navigator. You should decide which dock will suit you better.

---

### Post by stonecoldjha on 2008-07-22
i installed the cairo dock and its plugins,but when i launch it,it causes my system to crash....gradually all processes start slowing down,and finally the system becomes inresponsive....and i have to restart uncleanly.i like the cairo dock and dont want to part from it........how do i fix this?

---

### Post by stonecoldjha on 2008-07-22
i installed the cairo dock and its plugins,but when i launch it,it causes my system to crash....gradually all processes start slowing down,and finally the system becomes inresponsive....and i have to restart uncleanly.i like the cairo dock and dont want to part from it........how do i fix this?

---

### Post by tech0007 on 2008-07-22
Run 'cairo-dock' on terminal, then run 'top' on another window to check if it's really eating up your ram. btw, what's your ram and your graphics card?

---

### Post by stonecoldjha on 2008-07-22
i have the following specs
core2duo 2Ghz
2 GB RAM
an nvidia geforce 6200 card(VRAM 256 MB)
i think the configuration is good enough for the purpose.i also have xp installed in dualboot.rocket dock does very well in xp,and i have the skin of mac OS dock in it,it never lets me down.....so what's the matter with cairo in ubuntu?

---

### Post by stonecoldjha on 2008-07-22
i installed the cairo dock and its plugins,but when i launch it,it causes my system to crash.... the system becomes inresponsive....and i have to restart uncleanly.i like the cairo dock and dont want to part from it........how do i fix this?
i have the following specs
core2duo 2Ghz
2 GB RAM
an nvidia geforce 6200 card(VRAM 256 MB)
i think the configuration is good enough for the purpose.i also have xp installed in dualboot.rocket dock does very well in xp,and i have the skin of mac OS dock in it,it never lets me down.....so what's the matter with cairo in ubuntu?

---

### Post by Inxsible on 2008-07-22
Your system looks good enough for it to handle Cairo definitely. I am not sure what the problem would be. Are you sure you are using the proprietary nVidia drivers as opposed to the generic ones? could you post your xorg.conf, so we can have a look?

Also there are other docks out there. AWN for one, is the most popular. I have also found AWN to be a lot less buggier than Cairo.

---

### Post by stonecoldjha on 2008-07-23
how do i get my xorg.conf?

---

### Post by xochi on 2008-07-23
This page will tell you how to open the 'xorg' file:

[http://ubuntuforums.org/archive/index.php/t-642728.html](http://ubuntuforums.org/archive/index.php/t-642728.html)

---

### Post by stonecoldjha on 2008-07-24
i installed the cairo dock and its plugins,but when i launch it,it causes my system to crash.... the system becomes inresponsive....and i have to restart uncleanly.i like the cairo dock and dont want to part from it........how do i fix this?
i have the following specs
core2duo 2Ghz
2 GB RAM
an nvidia geforce 6200 card(VRAM 256 MB)
i think the configuration is good enough for the purpose.i also have xp installed in dualboot.rocket dock does very well in xp,and i have the skin of mac OS dock in it,it never lets me down.....so what's the matter with cairo in ubuntu?

---

### Post by phidia on 2008-07-24
Are there any errors about this reported-recorded in /var/log/messages?

---

### Post by LowSky on 2008-07-24
Have you tried trying to figure if maybe its only one of the plug-ins?
Does the system crash with just cairo running or after you use a certain plug-in?

---

### Post by stonecoldjha on 2008-07-24
how can i uninstall the cairo dock and all its plugins?i'll do things afresh...i.e. install it again.is cairo dock unstable?is there any stable version?

---

### Post by stonecoldjha on 2008-07-24
i installed the cairo dock and its plugins,but when i launch it,it causes my system to crash.... the system becomes inresponsive....and i have to restart uncleanly.how can i uninstall the cairo dock and all its plugins?i'll do things afresh...i.e. install it again.is cairo dock unstable?is there any stable version?

---

### Post by Frenske on 2008-07-24
Did you install it through synaptic manager? Anyway, just go to System -> Adminstration -> Synaptic Package Manager and search for cairo. There should be several items marked as installed. Select the cairo-dock to remove and it will give option to remove the plug-ins as well. Don't remove the rest of cairo stuff.

---

### Post by Darkade on 2008-07-24
you can check a howto on cairo dock here
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)
It's resent so it should work

---

### Post by stonecoldjha on 2008-07-24
i reinstalled the cairo dock and its plugins.while launching it this time i apprehended it would make my system hang up just as it had done last time.so,before launchng it i turned on system monitor.and then i launched the dock.the memory usage within seconds surged to 1.9GB from a mere value of some 300 MB before the launch.then swap came to be used.while this was happening my system was totally inresponsive.and i finally restarted.how do i fix this?i have seen screenshots of the desktops successfully running this dock.

---

### Post by stonecoldjha on 2008-07-25
i reinstalled the cairo dock and its plugins.while launching it this time i apprehended it would make my system hang up just as it had done last time.so,before launchng it i turned on system monitor.and then i launched the dock.the memory usage within seconds surged to 1.9GB from a mere value of some 300 MB before the launch.then swap came to be used.while this was happening my system was totally inresponsive.and i finally restarted.how do i fix this?i have seen screenshots of the desktops successfully running this dock.

---

### Post by pedro_orange on 2008-07-25
cairo-dock is heavy eye candy.

What are your system specs?
If you're not running a decent machine you probably won't be able to run all the gnome eye candy.

---

### Post by fabounet on 2008-07-25
Cairo-Dock can run smoothly on an EeePC ...
it depends on how you configure it (how many icons, how many applets, which view, which size, etc)
the more you add eye-candy, the more you need power. The advantage is that you can completely set up the "eye-candy level".
but in this case it probably reflects a bug.
try a "cairo-dock --maintenance", and deactivate some applets, maybe one is going crazy.
also you can try to move your ~/.cairo-dock, and relaunch the dock, and then select one of the available themes.

---

### Post by bapoumba on 2008-07-25
stonecoldjha, I have merged all your cairo dock threads in this one. It is not advised to start multiple threads on the same subject, threads are difficult to follow and people helping you may not be seeing all of them.

---

