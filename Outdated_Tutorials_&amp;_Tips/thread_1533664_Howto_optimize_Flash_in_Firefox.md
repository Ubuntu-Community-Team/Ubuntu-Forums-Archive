---
title: "Howto optimize Flash in Firefox"
date: 2010-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by dentaku65 on 2010-07-18
Hi,
this is a renewed guide for optimize flash on firefox browser based on my [old guide]("http://ubuntuforums.org/showthread.php?t=1346226") plus new hints.

This guide is intended for poor old 32bit pc (like mine) with Lucid, Firefox 3.6.6 and Flash 10.1.x. Of course, anyone can give a try.

I do not guarantee that these instructions works for you. On my box these settings improve the performances pretty much.

**1) Install flash plugin**
```
sudo apt-get --purge remove gnash adobe-flashplugin swfdec-mozilla && sudo apt-get install flashplugin-nonfree 
```
**2) Optimize Firefox**
Open Firefox
```
Choose the menu Edit -> Preferences -> Advanced -> Network -> Connection -> Settings
and choose No proxy option, then click Ok, then Close
```
In the address bar type **about:config** and filter/change the following settings:
```
network.dns.disableIPv6 **true**
network.http.max-connections **96**
network.http.max-connections-per-server **32**
network.http.max-persistent-connections-per-server **8**
network.http.pipelining **true**
network.http.pipelining.ssl **true**
network.http.pipelining.maxrequests **8**
network.http.proxy.pipelining **true**
network.prefetch-next **false**
network.dns.disableipv6 **true**
browser.sessionstore.interval **240000**
mousewheel.accelleration.factor **5**
mousewheel.accelleration.start **3**
```
**3) Install Firefox extensions**
Install Flashblock extension: [https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)
Install LSO, this is a handy privacy FF extension for Flash: [https://addons.mozilla.org/en-US/firefox/addon/6623](https://addons.mozilla.org/en-US/firefox/addon/6623)
Install ADBlock Plus extension: [https://addons.mozilla.org/en-US/firefox/addon/1865/](https://addons.mozilla.org/en-US/firefox/addon/1865/)
Install BetterCache extension (and leave the default values): [https://addons.mozilla.org/en-US/firefox/addon/6371/](https://addons.mozilla.org/en-US/firefox/addon/6371/)
Install Load Tabs Progressively extension: [https://addons.mozilla.org/en-US/firefox/addon/91919/]("https://addons.mozilla.org/en-US/firefox/addon/91919/")

Now restart Firefox and close Firefox

**4) Disable xgl**
```
mkdir ~/.config/xserver-xgl
touch ~/.config/xserver-xgl/disable
```
**5) Set OverrideGPU**
```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" > ~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```
**6) Disable Pango**
Edit this file:
```
gedit ~/.bashrc
```
and add this line at the end of the file, save and close
```
export MOZ_DISABLE_PANGO=1
```
**7) Disable localhost for IPv6**
Edit the file:
```
sudo gedit /etc/hosts
```
remove [COLOR="Red"]localhost[/COLOR] entry in IPV6 section of /etc/hosts
Before:
```
# The following lines are desirable for IPv6 capable hosts
	::1     [COLOR="Red"]localhost[/COLOR] ip6-localhost ip6-loopback
```
After:
```
# The following lines are desirable for IPv6 capable hosts
	::1     ip6-localhost ip6-loopback
```
Be careful on this setting if you are using IPV6 (I'm not usisg it), see: [https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/301430](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/301430)

**8 ) Optimize FF sqlite (updated)**
Install sqlite3
```
sudo apt-get install sqlite3
```
Close Firefox
Create & edit script for cron:
```
sudo touch /etc/cron.daily/start-sqlite-ff
sudo chmod +x /etc/cron.daily/start-sqlite-ff
sudo gedit /etc/cron.daily/start-sqlite-ff
```
Insert the following text and save:
```
#!/bin/bash
PROC=`pgrep -n firefox`
if [ "$PROC" != "" ]; then echo "Firefox is running"; exit 1; fi
find $HOME/.mozilla/ \( -name "*.sqlite" \) -exec sqlite3  {} "vacuum" \;
```
Run the script:
```
sudo /etc/cron.daily/start-sqlite-ff
```
Done.

**9) Xorg optimization**

Edit this file (if not exist, as supposed to be, create it):
```
sudo gedit /etc/X11/xorg.conf
```
Paste the following text:
```
Section "DRI"
 Mode 0666
EndSection

Section "Extensions"
 Option "Composite" "Enable"
EndSection

```
Save the file and exit. This boost a lot.
(Thx Labello & Lovinglinux for this)

**10) Optimize RWIN settings**

Go to [http://www.speedtest.net/](http://www.speedtest.net/) test your connection speed and track down the values.

On terminal window paste this command:
```
sudo sysctl -w net.core.rmem_default=524288 net.core.rmem_max=524288 net.core.wmem_default=524288 net.core.wmem_max=524288 net.ipv4.tcp_wmem="4096 87380 524288" net.ipv4.tcp_rmem="4096 87380 524288" net.ipv4.tcp_mem="524288 524288 524288" net.ipv4.tcp_rfc1337=1 net.ipv4.ip_no_pmtu_disc=0 net.ipv4.tcp_sack=1 net.ipv4.tcp_fack=1 net.ipv4.tcp_window_scaling=1 net.ipv4.tcp_timestamps=1 net.ipv4.tcp_ecn=0 net.ipv4.route.flush=1
```
Then go back on [http://www.speedtest.net/](http://www.speedtest.net/) and re-test your connection; the results should be improved in evident way, **if so**, make the command implemented above permanent; open the file:
```
sudo gedit /etc/sysctl.conf
```
And add the following at the end of the file:
```
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

```
Save and close; then:
```
sudo sysctl -p
```
Source: [http://swik.net/Ubuntu/Only+Ubuntu/How+to+Optimize+your+Internet+Connection+using+MTU+and+RWIN/cbnda](http://swik.net/Ubuntu/Only+Ubuntu/How+to+Optimize+your+Internet+Connection+using+MTU+and+RWIN/cbnda)

**11) Fix css *fixed background* bug **

Bug source: [https://bugzilla.mozilla.org/show_bug.cgi?id=438911](https://bugzilla.mozilla.org/show_bug.cgi?id=438911)
Edit this file:
```
gedit ~/.mozilla/firefox/*.default/chrome/userContent.css
```
Past the following lines and save:
```
/* Smooth Scrolling: Disable Fixed Background Images */
body {
background-attachment: scroll !important;
background-repeat:no-repeat;
}
```

**12) Tune memory + FF cache in RAM (at least with 1GB RAM on board)**

Edit this file:
```
sudo gedit /etc/sysctl.conf
```
and past the following lines at the end:
```
# Improve memory
vm.swappiness=10

# Improve file/folder browsing speed
vm.vfs_cache_pressure=50

# Set maximum amount of memory allocated to shm to 256MB
kernel.shmmax = 268435456
```
Save and do the following command:
```
sudo sysctl -p
```
Open Firefox and type in the address bar **about:config**; then with right click on window choose New -> String and insert **browser.cache.disk.parent_directory** and as a value **/dev/shm**
Close Firefox

Now reboot your pc and enjoy!

-------------------------------------------------------------------------
*11/14/2010 Updated extensions
*10/23/2010 Tune memory
*10/18/2010 Updated RWIN optimization
*10/17/2010 Added userContent.css workaround
*10/16/2010 Remove Ondemand tweak and added Xorg optimization
*10/16/2010 Added RWIN optimization

---

### Post by lovinglinux on 2010-07-24
Thanks for sharing.

For item 8 I would recommend [SQLite Optimizer]("https://addons.mozilla.org/en-US/firefox/addon/11198/") or using the command below:

```
find $HOME/.mozilla/ \( -name "*.sqlite" \) -exec sqlite3  {} "vacuum" \;
```

They both will guarantee all sqlite databases are optimized and not only the default ones, after all several extensions create databases of their own.

Also check my Firefox and Flash optimization tutorials at [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)

---

### Post by Dencrypt on 2010-10-04
Just wanted to give a big thanks for this. I can now see flash in fullscreen on my celeron/x1300 laptop! (running crunchbang however but still)!

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

Dentaku65 / Lovinglinux! You rule!

---

### Post by alswar on 2010-11-14
Hi,

thanks a lot for your help, now flash videos are much better than before. Still I can't run smoothly 720p video but at least it's usable.

Just one thing: flash videos are not played automatically when you open a web page with some of them. How can I change this setting?

Thanks

---

### Post by soldier1st on 2010-11-14
what is xgl? also is there any side effects from disabling it?also what is pango and why should you disable it?

---

### Post by rolnics on 2010-11-14
Great Howto, only problem I had was with the Xorg section, giving me a parsing error, should have looked at which line it was, but I've just assumed its from here, so commented out for now. Will play around with it soon, just not yet, just spent most of the weekend getting my xorg right!

Otherwise great Howto, Thanks

---

### Post by dentaku65 on 2010-11-15
> **alswar said:**
> Hi,

thanks a lot for your help, now flash videos are much better than before. Still I can't run smoothly 720p video but at least it's usable.

Just one thing: flash videos are not played automatically when you open a web page with some of them. How can I change this setting?

Thanks

This is the Flashblock extension: [https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)
If you remove it you'll get flash video play automatically or you can keep it and choose (white list) in which site to disable this extension.

---

### Post by dentaku65 on 2010-11-15
> **rolnics said:**
> Great Howto, only problem I had was with the Xorg section, giving me a parsing error, should have looked at which line it was, but I've just assumed its from here, so commented out for now. Will play around with it soon, just not yet, just spent most of the weekend getting my xorg right!

Otherwise great Howto, Thanks

Can you post your xorg.conf?
As far I can tell the conf posted on #1 it is workig well on my old Intel card.
Are you not running compiz?

---

### Post by dentaku65 on 2010-11-15
> **soldier1st said:**
> what is xgl? also is there any side effects from disabling it?also what is pango and why should you disable it?

Xgl it is an old architecture of X server [http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl) replaced by AIGLX

Disable Pango it is useful only if you have a Firefox version compiled with --enable-pango; the Pango option will slow down scrolling and rendering fonts on FF

---

### Post by soldier1st on 2010-11-16
> **dentaku65 said:**
> Xgl it is an old architecture of X server [http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl) replaced by AIGLX

Disable Pango it is useful only if you have a Firefox version compiled with --enable-pango; the Pango option will slow down scrolling and rendering fonts on FF

i use the default firefox app that comes with ubuntu. also does ubuntu use aiglx and xgl was just left in for compatability reasons?i'm asking these questions as i don't want to fubar my install.

---

### Post by dentaku65 on 2010-11-16
> **soldier1st said:**
> i use the default firefox app that comes with ubuntu. also does ubuntu use aiglx and xgl was just left in for compatability reasons?i'm asking these questions as i don't want to fubar my install.

For FF package I don't know if the default one has pango enabled or not
For xgl hint, in my case, makes flash video runs smoothly with compiz active

For both hints you can reverse them quite easily:
xgl: rm -R ~/.config/xserver-xgl
pango: remove the indicated line in .bashrc file

Well, I recall my preamble at #1 is: *I do not guarantee that these instructions works for you. On my box these settings improve the performances pretty much.*
That is far from "fubar your or any intall" :-)

---

### Post by nej_simon on 2010-11-16
Hello!

> **dentaku65 said:**
> **4) Disable xgl**
```
mkdir ~/.config/xserver-xgl
touch ~/.config/xserver-xgl/disable[/

**9) Xorg optimization**

Edit this file (if not exist, as supposed to be, create it):
[CODE]sudo gedit /etc/X11/xorg.conf
```
Paste the following text:
```
Section "DRI"
 Mode 0666
EndSection

Section "Extensions"
 Option "Composite" "Enable"
EndSection

```
Save the file and exit. This boost a lot.
(Thx Labello & Lovinglinux for this)

These two aren't necessary unless you're running some old version of ubuntu. Xgl has been dropped by upstream and isn't included in ubuntu anymore so disabling it has no effect. And composite has been on by default for a few years now.

---

### Post by dentaku65 on 2010-11-16
> **nej_simon said:**
> Hello!



These two aren't necessary unless you're running some old version of ubuntu. Xgl has been dropped by upstream and isn't included in ubuntu anymore so disabling it has no effect. And composite has been on by default for a few years now.

Yes this is correct. But, in my case the xorg entries make a big difference of performance when I launch flash video (I can watch them in full screen with compiz enabled without any problem), otherwise without this specific optimization flash streaming is not fluid. See also: [http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

For xgl, in my case, optimize scrolling and flash on FF (and, maybe this is depending by compiz).

---

### Post by nej_simon on 2010-11-16
> **dentaku65 said:**
> Yes this is correct. But, in my case the xorg entries make a big difference of performance when I launch flash video (I can watch them in full screen with compiz enabled without any problem), otherwise without this specific optimization flash streaming is not fluid. See also: [http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

For xgl, in my case, optimize scrolling and flash on FF (and, maybe this is depending by compiz).

I highly doubt it. :) Composite makes X render to an offscreen buffer that a composite manager (ie. compiz) can use to draw the desktop. This allows for some nice features like desktop effects and double buffering but for flash it will only make it slower (if anything), since the rendering will have to go trough the offscreen buffer. The DRI-setting changes permission for the DRI. That should only be nessescary if DRI doesn't work for non-root users due to permission errors (which shouldn't be the case unless you're affected by some bug). Anyway, if you have compiz running then you already have working DRI and composite.

About XGL, there is not even a package for it in ubuntu anymore. If that option does anything then that's a bug, but I don't see what effect it could possilby have.

---

### Post by dentaku65 on 2010-11-16
> **nej_simon said:**
> I highly doubt it. :) Composite makes X render to an offscreen buffer that a composite manager (ie. compiz) can use to draw the desktop. This allows for some nice features like desktop effects and double buffering but for flash it will only make it slower (if anything), since the rendering will have to go trough the offscreen buffer. The DRI-setting changes permission for the DRI. That should only be nessescary if DRI doesn't work for non-root users due to permission errors (which shouldn't be the case unless you're affected by some bug). Anyway, if you have compiz running then you already have working DRI and composite.

About XGL, there is not even a package for it in ubuntu anymore. If that option does anything then that's a bug, but I don't see what effect it could possilby have.

Seems that you know my box better than me, what can I say? Ok, perfect.

---

### Post by soldier1st on 2010-11-16
> **dentaku65 said:**
> Seems that you know my box better than me, what can I say? Ok, perfect.

i can't use compiz or nautilus will act up. with using metacity it is fine and if i use compositing then videos will have horizontal lines in them but if i have compositing disabled the videos are fine. if some fix could be provided that would be nice. also does composting speed up the system?

---

### Post by nej_simon on 2010-11-16
> **dentaku65 said:**
> Seems that you know my box better than me, what can I say? Ok, perfect.

Well, at least I know some stuff about Linux, having used it for quite some time.

> **soldier1st said:**
> i can't use compiz or nautilus will act up.  with using metacity it is fine and if i use compositing then videos will  have horizontal lines in them but if i have compositing disabled the  videos are fine. if some fix could be provided that would be nice. also  does composting speed up the system?

That might be due to faulty hardware or a buggy driver. Have you tried running memtest86+? Composite makes X render to an offscreen buffer and then the composite manager draws the desktop from that buffer. This adds an extra overhead so in most cases rendering will be slower. But then, all windows become double buffered so there will be less redraws occurring. So depending on what hardware you have it can be both ways. For example, with composite scrolling in firefox will be slower but moving a window over the firefox window will use less resources since the firefox window wont have to redraw.

---

### Post by dentaku65 on 2010-11-16
> **soldier1st said:**
> i can't use compiz or nautilus will act up. with using metacity it is fine and if i use compositing then videos will have horizontal lines in them but if i have compositing disabled the videos are fine. if some fix could be provided that would be nice. also does composting speed up the system?

In my case my machine is slower with metacity so, I do not use it.
For what concern your issue with compositing I think that this guide is out of scope for your needs; indeed I suggest to investigate in other areas more specific with the compatibilities between compiz (or metacity with compositing enabled) and your graphic card for example.

---

### Post by soldier1st on 2010-11-16
> **nej_simon said:**
> Well, at least I know some stuff about Linux, having used it for quite some time.



That might be due to faulty hardware or a buggy driver. Have you tried running memtest86+? Composite makes X render to an offscreen buffer and then the composite manager draws the desktop from that buffer. This adds an extra overhead so in most cases rendering will be slower. But then, all windows become double buffered so there will be less redraws occurring. So depending on what hardware you have it can be both ways. For example, with composite scrolling in firefox will be slower but moving a window over the firefox window will use less resources since the firefox window wont have to redraw.
my hardware is fully working. i think it may be a compatability issue with my video card (Geforce 9500GT 1GB),
dentaku65: it seems disabling Pango did help.

---

### Post by dentaku65 on 2010-11-16
> **soldier1st said:**
> my hardware is fully working. i think it may be a compatability issue with my video card (Geforce 9500GT 1GB),
dentaku65: it seems disabling Pango did help.

There is an official documentation for nVidia card/driver

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by soldier1st on 2010-11-16
> **dentaku65 said:**
> There is an official documentation for nVidia card/driver

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

the part on that page does indicate my problem but only when compiz is turned on(Visual effects=compositing)

Problems with Video Playback
If you have problems with video playback, e.g. in mplayer, gxine, or mythtv frontend with a legacy card, it may be due to too high a color depth (e.g. using NT6 Vanta/Vanta LT "nvidia" driver, I experienced flickering vertical bars & blue screen flashing). To fix this, manually edit /etc/X11/xorg.conf and change DefaultDepth to 16.

---

### Post by WinRiddance on 2010-11-29
Don't forget ...
The more input ... the higher the risk for problems later on ... ;)

I don't know what kind of hardware you're running but I followed your howto guide for my HP laptop with AMD 64bit AthlonX2 processor. The graphic HD3200 chip is pretty lousy, but it works. My setup has tons of RAM (4 GB) and no dual-boot that's being shared with Windows. Just plain ol' Ubuntu 10.04 which I've freshly installed a few days ago due to massive, **and I do mean massive**, upgrade problems after upgrading to 10.10 a couple of weeks ago.

Anyway, I had to skip the last two lines in step 2 because nothing showed up for a mouse i.e. mousewheel at all and there wasn't a field for me to edit separately, probably due to the fact that I'm using a wireless mouse.

**I skipped all of step 3 entirely** since I work on a lot of web development for which I keep my cache emptied permanently, don't use it. I also don't like the progressive tab loading, on/off control for flash, etc. In other words, if I had no real productive use out of those extensions, then why bother to install them ... just to have one or more items that could potentially behave buggy down the road, as other versions and file changes within FF are released?

**I also skipped step 4 entirely** because most machines these days with the newest versions of Ubuntu (starting with 9.10 methinks?) don't even use xgl anymore.

**Additionally I skipped step 9** because I believe this too no longer has any bearing for most Ubuntu users with newer machines and the latest Ubuntu versions.

Finally, for step 11, I wasn't able to make that step work since I received a message that the changes couldn't be saved due to the fact that the file in question couldn't be found. That was pretty weird though since the file did indeed open up initially with gedit, but wouldn't allow me to change/save it even though sudo was being used.

**Bottom line ... I think this is a great tutorial** for many people, probably just about anyone who uses FF as their default browser. I've been leaning more and more in the direction of Chrome because the speed of Chrome is downright astonishing, especially if you're often working with 6 or more open tabs at the same time. But Chrome too, does have a some issues that still need to be worked out. Can't get all of my flash video working there by default, right after the installation, either ... :(

Great work though! I'm sure many will appreciate this. Keep it up !!! =D>

**[COLOR="DarkRed"]UPDATE ...[/COLOR]**

After rebooting my system with a cold start (shut down, wait a minute and then start up again) all of the above changes actually caused my wireless connection to fail completely. It was still there, just couldn't get going no matter how hard I tried, reentered password, etc. Testing all throughout the house on 3 other machines showed that only my machine was affected (the other machines had remained untouched to begin with). So I ended up backtracking and undoing everything except for step 1 and 2 of this thread. Now everything is running decently again. Live and learn ...

---

### Post by dentaku65 on 2010-11-30
> **WinRiddance said:**
> Don't forget ...
The more input ... the higher the risk for problems later on ... ;)

I don't know what kind of hardware you're running but I followed your howto guide for my HP laptop with AMD 64bit AthlonX2 processor. The graphic HD3200 chip is pretty lousy, but it works. My setup has tons of RAM (4 GB) and no dual-boot that's being shared with Windows. Just plain ol' Ubuntu 10.04 which I've freshly installed a few days ago due to massive, **and I do mean massive**, upgrade problems after upgrading to 10.10 a couple of weeks ago.

Anyway, I had to skip the last two lines in step 2 because nothing showed up for a mouse i.e. mousewheel at all and there wasn't a field for me to edit separately, probably due to the fact that I'm using a wireless mouse.

**I skipped all of step 3 entirely** since I work on a lot of web development for which I keep my cache emptied permanently, don't use it. I also don't like the progressive tab loading, on/off control for flash, etc. In other words, if I had no real productive use out of those extensions, then why bother to install them ... just to have one or more items that could potentially behave buggy down the road, as other versions and file changes within FF are released?

**I also skipped step 4 entirely** because most machines these days with the newest versions of Ubuntu (starting with 9.10 methinks?) don't even use xgl anymore.

**Additionally I skipped step 9** because I believe this too no longer has any bearing for most Ubuntu users with newer machines and the latest Ubuntu versions.

Finally, for step 11, I wasn't able to make that step work since I received a message that the changes couldn't be saved due to the fact that the file in question couldn't be found. That was pretty weird though since the file did indeed open up initially with gedit, but wouldn't allow me to change/save it even though sudo was being used.

**Bottom line ... I think this is a great tutorial** for many people, probably just about anyone who uses FF as their default browser. I've been leaning more and more in the direction of Chrome because the speed of Chrome is downright astonishing, especially if you're often working with 6 or more open tabs at the same time. But Chrome too, does have a some issues that still need to be worked out. Can't get all of my flash video working there by default, right after the installation, either ... :(

Great work though! I'm sure many will appreciate this. Keep it up !!! =D>

**[COLOR="DarkRed"]UPDATE ...[/COLOR]**

After rebooting my system with a cold start (shut down, wait a minute and then start up again) all of the above changes actually caused my wireless connection to fail completely. It was still there, just couldn't get going no matter how hard I tried, reentered password, etc. Testing all throughout the house on 3 other machines showed that only my machine was affected (the other machines had remained untouched to begin with). So I ended up backtracking and undoing everything except for step 1 and 2 of this thread. Now everything is running decently again. Live and learn ...

Hi WinRiddance,
I really don't think, as far as I know, that the optimizations posted here can cause some damage to wireless configuration in some way, due to the fact that there is no connection between the info posted and the specific issue reported by you; the only global network implications are the steps 7 and 10 I will check on my side if these settings can cause such issue based on your indication.

For the step 11 may I ask you if you have multiple profile of FF? If so can be this the reason why the file cannot be open (this is a personal file, sudo it is wrong to use it).

As stated on post #1 this guide is for old computer like mine :-) with poor resources and even poor VGA card, your box rather seems pretty new and with enough resources for a good experience of browsing as is, or at least I supposed.

For concerning browsers, yes, my default browser is FF (and that's why I wrote this guide); sometimes I'm using Midori, at the moment I don't feel very comfortable with Chrome.

Thx for your feedback

---

### Post by johnpeterson on 2010-12-01
i will give this a try and see if this really works.

---

### Post by mektek69 on 2010-12-17
Just tried this on a new install of Firefox 3.6.13 on Linux Mint 10 Julia and it still works great. Pages load faster and flash works fine now. I can even watch 720p high def on an old computer with an amd athlon XP 3200 and a geforce 7300.

 Only made a couple of changes, I used the SQLite Optimizer extension for step 8 - Skipped step 9 as it is outdated - There is no chrome directory in my install so didn't need step 11 - and in addition to your about:config entries I also disabled the safe browsing filters that slow things down so much by setting 

browser.safebrowsing.enabled 
 -and- 
browser.safebrowsing.malware.enabled to false.

 Thank you so much for writing this guide. I was having to watch youtube videos in totem, and now I can watch them inside Firefox like I should be able to. :D

---

### Post by mr.suchy on 2011-02-11
> **dentaku65 said:**
> Hi,


**10) Optimize RWIN settings**

```
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

```Save and close; then:




HI,

I have ADSL with 250 kb/s download and 25kb/s upload. Is this config is good for me ? I don't know what put in this line (net.ipv4) ?

Best regards!

---

### Post by Sylslay on 2011-02-14
Just wanted to give a big thanks!!!!!!!

Specal for ponit 2.

Could not install add-on o firefox3.6 at ubuntu 10.04 at all.
In windows firewall setnigs where wrong but in linux I just change about:config

Now I will optimiaze, ofcourse ):P

:popcorn:
and point 12 is best tweak I ever did. 
System use 15 procent of CPU instead 25, I don't realy need store cache on HDD.
Is bit slower when You laod 1st time page, but after that is rocket....

---

### Post by Sylslay on 2011-02-15
Hi mr.suchy.
RWIN ??
I tested and in my case where slower speedtest.net 

Improve about 10% , after  set proper MTU (in router),

ping -f -l [www.netia.pl](www.netia.pl) 

command ping -f -l works under windows  and show maximum value of MTU,

But if You set to high MTU, some page won't be display in browser.

Recommed MTU to set is, max MTU-10, but I use max.

---

### Post by xokaido on 2011-07-17
Damn... You've killed my browser, it takes whole year to open a page....
Crazy stupid "optimization"....

---

### Post by Trolen on 2011-07-17
Can we use it into @Fast@ computers ?

---

### Post by geazzy on 2011-07-18
great tutorial :D

---

