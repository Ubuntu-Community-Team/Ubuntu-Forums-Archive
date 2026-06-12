---
title: "Installing Firefox 3.6 &quot;Namoroka&quot;"
date: 2009-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by collinp on 2009-12-06
***NOTICE: This tutorial is made for the latest stable release at the time of writing, Karmic.***
***NOTICE #2: Due to the way the firefox-stable PPA works, it and as effect, this tutorial will upgrade the currently installed version of Firefox to Firefox 3.6.***

This is a tutorial on installing Firefox 3.6 "Namoroka" on Ubuntu.

This tutorial is divided into three sections:

[LIST]
[*] [COLOR=DarkRed]Section 1: Installation[/COLOR]
[*][COLOR=DarkRed] Section 2: Removal[/COLOR]
[*][COLOR=DarkRed]Section 3: Troubleshooting[/COLOR]
[/LIST]
   [CENTER][B][SIZE=4][COLOR=DarkRed]Section 1 - Installation[/COLOR][/SIZE]

[/B][LEFT]Open up a Terminal window (Applications - Accessories - Terminal). Type in the following commands, in order, entering your password when needed (if one of them throws an error **DO NOT** continue with the installation. Post the error here.):

```
echo "deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ `lsb_release -cs` main" | sudo tee /etc/apt/sources.list.d/firefox-stable.list
echo "deb-src http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ `lsb_release -cs` main" | sudo tee /etc/apt/sources.list.d/firefox-stable.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
sudo apt-get update
sudo apt-get install firefox
```That command above does the following:

[LIST]
[*]Adds the [Ubuntu Mozilla Daily Build PPA]("http://ppa.launchpad.net/ubuntu-mozilla/daily/ppa/ubuntu") to your sources.list
[*]Imports the GPG key used to sign the packages contained in the above said repo
[*]Updates your package cache
[*]Pulls and installs Firefox 3.6 (will upgrade your previous version of Firefox)
[/LIST]
[CENTER][B][SIZE=4][COLOR=DarkRed]Section 2 - Removal[/COLOR][/SIZE]
[/B][LEFT]
If, for some reason, you don't want Firefox anymore and want to completely remove it, execute the following commands:
```
sudo apt-get remove firefox && sudo apt-get autoremove
```

If you just want Firefox 3.5 back, execute the following in a terminal:
```
sudo rm /etc/apt/sources.list.d/firefox-stable.list && sudo apt-get update && sudo apt-get install firefox
```

If, at any time, you wish to reinstall Firefox 3.6, re-execute the commands listed under "Installation".

[CENTER][B][SIZE=4][COLOR=DarkRed]Section 3 - Troubleshooting[/COLOR][/SIZE]

[/B][LEFT]**Problem**: My Firefox 3.6 install imported my plugins, but I can't use any of them! It says they are incompatible with my version!

**Solution**: Until the plugin author supports development releases and/or your firefox release, you have to install the Nightly Tester Tools addon.

[B]_NOTE: If you follow on with these directions and enable plugins not designed for your release, you may damage or destroy your Firefox profile. Use at your own risk._

[/B]In Firefox 3.6, navigate to: [https://addons.mozilla.org/en-US/firefox/addon/6543](https://addons.mozilla.org/en-US/firefox/addon/6543)
Click "Add to Firefox" when the page loads, and click "Install" in the popup window. Restart Firefox 3.6, then click "Tools - Add-ons". Click "Override All Compatibility". Restart Firefox 3.6 again.

If that did not work, you may have to go through and click "Enable" on all of the addons you wish to enable.


**Problem**: My themes don't work!

**Answer**: Follow the same directions as with plugins, but click the "Themes" tab once you open the Add-ons window, and click "Override all compatibility", then click "Use This Theme" next to the theme you wish to use, then restart.


**Problem**: Java does not work!

**Answer**: From what I can tell, the "classic" Java plugin does not work. As such, you will need to [manually install the "Next-generation" plugin](http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html) (see [http://support.mozilla.com/nl/forum/1/554389](http://support.mozilla.com/nl/forum/1/554389)).


**Problem**: I have a problem that is not listed here!

**Answer**: Go ahead and post your problem in the thread, and I will do my best to answer it or point you in the right direction.
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]

---

### Post by PatrickMB on 2009-12-06
```
Bash: /etc/apt/sources.list: Permission denied
```

That's the response I get in the terminal when trying to execute your first step.

---

### Post by drubin on 2009-12-06
> **Hellow said:**
> 

```
echo "deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main" >> /etc/apt/sources.list && echo "deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main" >> /etc/apt/sources.list && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE && sudo apt-get update && sudo apt-get install firefox-3.6
```That command above does the following:


Hey nice tutorial but the preffered way of adding ppa's or any other 3rd party repo's is not to add them to /etc/apt/sources.list but rather /etc/apt/sources.list.d/ppa.list.

```
echo "deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main" | sudo tee /etc/apt/sources.list.d/mozdaily.list && echo "deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main" | sudo tee /etc/apt/sources.list.d/mozdaily.list && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE && sudo apt-get update && sudo apt-get install firefox-3.6
```
[/QUOTE]

As for the permission denied that has to do with the permissions and content redirection. see above fix for that :)

All I changed was the default location to follow standards and make upgrading generally easier. (One shouldn't add 3rd party stuff to sources.list) and fixed the permissions on echo'ing to root owned files.

testing

---

### Post by drubin on 2009-12-06
I would also recommend posting each command as a separate step. With the && the next command only gets executed if the first was completely successful. If there was an error with any of of the commands it would be extremely hard to work out which one. :) 

Other then that nice tutorial.

testing

---

### Post by collinp on 2009-12-06
Ah, thanks for your input drubin! That also caught and fixed the "Permission denied" problem that I saw a person above was having.

---

### Post by drubin on 2009-12-06
something you can change to make this tutorial work with the older versions of ubuntu is .
> ```
echo "deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu `lsb_release -cs` main" | sudo tee /etc/apt/sources.list.d/mozdaily.list 

```

That will output the codename is karmic jaunty/intrepid/hardy I am pretty sure the daily ppa's have builds for the older versions they did for 3.5.

---

### Post by psych1610 on 2009-12-09
n/m I did it wrong. Thanks!

---

### Post by SilverWave on 2009-12-11
A new command in Karmic makes it easy to add a repository for a ppa and its key.

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa

Then install as below:

sudo apt-get update
sudo apt-get install firefox-3.6

---

### Post by ccleanerfan on 2009-12-12
With Firefox 3.6 beta 5, I can't use the java plugin with it.

---

### Post by collinp on 2009-12-13
> **ccleanerfan said:**
> With Firefox 3.6 beta 5, I can't use the java plugin with it.

I've been having the same problem. Unfortunately, I have not been able to find a fix for it yet. Rest assured, I'm working as hard as I can to find one soon.

If I can't, it will probably be fixed in the final release or, hopefully, sooner.

---

### Post by sgleo87 on 2009-12-15
I have the same problem with java...

Also, I cannot install the mplayer plugin. I tried the vlc plugin but it does not always work for me and the gxine plugin opens video or audio streams in a separate window which is kind of annoying. Any suggestions on how to get mplayer working or other alternatives?

---

### Post by collinp on 2009-12-15
> **sgleo87 said:**
> I have the same problem with java...

Also, I cannot install the mplayer plugin. I tried the vlc plugin but it does not always work for me and the gxine plugin opens video or audio streams in a separate window which is kind of annoying. Any suggestions on how to get mplayer working or other alternatives?

I haven't personally used the mplayer plugin, so I can't offer any advice on that, but I do know that Totem compatibility with Firefox 3.6 is great. Maybe you want to try that?

---

### Post by sgleo87 on 2009-12-16
Thanks for the suggestion...I tried it but still wasn't as happy with it as with mplayer so I switched back to Firefox 3.5 (also, I needed Java to work).

---

### Post by collinp on 2009-12-16
> **sgleo87 said:**
> Thanks for the suggestion...I tried it but still wasn't as happy with it as with mplayer so I switched back to Firefox 3.5 (also, I needed Java to work).

Heh, Firefox 3.6 is still beta software. The problems with Java and mplayer are probably software bugs on Mozilla's side. All of this will, more than likely, be fixed before the final release :).

---

### Post by astaticskyline on 2009-12-20
after following the first 3 steps in the terminal to install firefox 3.6, I get this message:

 Package firefox-3.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox-3.6 has no installation candidate

Any ideas to help me out? much appreciated if so...

---

### Post by moted on 2010-01-24
Has anyone managed to get the Java plugin working with 3.6 yet?

---

### Post by michael37 on 2010-01-25
Please consider removing these instructions in favor of firefox-stable ppa.  Running daily build in production is unsafe.

[http://ubuntuforums.org/showpost.php?p=8723004&postcount=11](http://ubuntuforums.org/showpost.php?p=8723004&postcount=11)

---

### Post by collinp on 2010-01-27
> **michael37 said:**
> Please consider removing these instructions in favor of firefox-stable ppa.  Running daily build in production is unsafe.

[http://ubuntuforums.org/showpost.php?p=8723004&postcount=11](http://ubuntuforums.org/showpost.php?p=8723004&postcount=11)

As stated, I updated the tutorial to use the firefox-stable PPA. For those whom have already followed the tutorial and wish to update to use firefox-stable, execute the following in terminal:

```
sudo rm /etc/apt/sources.list.d/mozdaily.list
```

Then re-follow the "Installation" section. Note: It will upgrade the currently installed version of Firefox (which should still be Firefox 3.5).

Also, for those whom are having difficulties with Java, I found a thread on the Mozilla support site that offers some help with the subject: [http://support.mozilla.com/nl/forum/1/554389](http://support.mozilla.com/nl/forum/1/554389)

---

### Post by isaacalves27 on 2010-02-04
Hello people...

I have updated to Namoroka but is crashing a lot...

_____________________
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 45 error_code 17 request_code 144 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
______________________

I wanted to have the 3.5 back cause I use this here install to work and with the browser going down I'm being forced to use Opera...

Tried to follow the steps to have 3.5 back but with no success.

btw Im using a hardy installation..

May I have any help from you?

Thanks a lot :D

Isaac

---

### Post by isaacalves27 on 2010-02-04
Can you help me to have my browser updated only to stable releases? (At least on this machine :))

Thanks again!

---

### Post by michael37 on 2010-02-04
> **isaacalves27 said:**
> Can you help me to have my browser updated only to stable releases? (At least on this machine :))

Thanks again!

Remove mozilla-daily from your Software Sources.  

Keep only firefox-stable there.

---

### Post by isaacalves27 on 2010-02-04
Thanks! I ll do it as you say.

have a nice day :)

---

### Post by michael37 on 2010-02-04
A few people asked about java-plugin for Firefox 3.6.  

Based on [http://ubuntuforums.org/showpost.php?p=8721917&postcount=25](http://ubuntuforums.org/showpost.php?p=8721917&postcount=25)

Install Java:
```
sudo apt-get remove --purge icedtea6-plugin
sudo apt-get install sun-java6-plugin

```

Icedtea does not have compatible plugin for Firefox 3.6.  Sun Java does. [More info about this change.]("http://java.com/en/download/faq/firefox_newplugin.xml")

32-bit Firefox: 
```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50 
```

64-bit Firefox:
```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib64/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so 50 
```

Enjoy!

---

### Post by isaacalves27 on 2010-02-06
sorry michael37

i tried to do what u say but i dont now how to.. too newbie on this..:(

i have managerd to install the java though.. but gmail is still making my mozilla crash.. any ideas why?

---

### Post by poiret on 2010-02-17
I've been experiencing a decrease in speed when loading flash files ever since I switched to 3.6. Some videos in youtube are taking too long to load. This [site]("http://www.showstudio.com/collections/seasons/newyorkwomenswearaw10/42494") in particular, I've let it sit for like 45 minutes now and it has only loaded like 2 minutes. I tried checking it with my brother's Windows laptop and the speed seems to be fine. What could be causing this problem?

---

### Post by collinp on 2010-02-22
> **poiret said:**
> I've been experiencing a decrease in speed when loading flash files ever since I switched to 3.6. Some videos in youtube are taking too long to load. This [site]("http://www.showstudio.com/collections/seasons/newyorkwomenswearaw10/42494") in particular, I've let it sit for like 45 minutes now and it has only loaded like 2 minutes. I tried checking it with my brother's Windows laptop and the speed seems to be fine. What could be causing this problem?

My only guess would be to set your proxy options to "No proxy" under Firefox's advanced settings.

---

### Post by jackdale on 2010-03-11
So, I just "upgraded" to 3.6 from 3.5.8.

So far I like the minor changes that I can see.

HOWEVER, I'm a little annoyed that I now have to choose between having a Theme or a Persona.  In 3.5.x I could choose to have both a custom theme with a persona.  Now they are mutually incompatible with.  What I find most annoying is that when I click on "Get Themes" in Add-ons, it takes me to the Personas page!  It seems that Mozilla likes its default icon set and wants to put their thumb on the themes dev community...

---

### Post by iClouseau88 on 2010-03-11
Hi,

I cannot upgrade from firefox 3.5.8 to 3.6 at all, despite following instructions from either post #3 by drubin or post #8 by Silver Wave.  Help>About keeps showing 3.5.8.

What should I do?

---

### Post by iClouseau88 on 2010-03-11
It's weird!  "Install firefox-3.6" did not upgrade the browser version at all, but "install firefox" just upgraded my browser from 3.5.8 to 3.6.2pre (Namoroka).  Other than the FF icon that needs to be reinstated, all bookmarks and extensions are intact.  Thank you all!

---

### Post by michael37 on 2010-03-11
> **iClouseau88 said:**
> It's weird!  "Install firefox-3.6" did not upgrade the browser version at all, but "install firefox" just upgraded my browser from 3.5.8 to 3.6.2pre (Namoroka).  Other than the FF icon that needs to be reinstated, all bookmarks and extensions are intact.  Thank you all!

Sounds like you updated using mozilla-daily ppa, not firefox-stable.  Be very careful, unless you are sure you know what you did.

---

### Post by old_salt on 2010-03-12
I can appreciate and support the use of signing keys however; every time I have to deal with these keys which I support andunderstand their usefullness, I have issues. Ubuntu needs to get some stable online servers in order to keep from making a lot of folks ticked off. Here's my error;

mobile@Mobile-IT1:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

---

