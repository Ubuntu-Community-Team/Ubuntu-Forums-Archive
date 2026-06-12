---
title: "Adobe Flash"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by torgrot on 2008-08-01
Why, oh Why, can they not remove the adobe flash player package from the restricted-extras.  I am sitting here at try:13 to get install_flas_player_9_linux.tar.gz   It isn't there hasn't been there since adobe bought them.  I know how to install adobe flash player, the restricted-extras is a necessary package, but it is a pain in the behind to install because of the broken link to this package.

torgrot

---

### Post by chris200x9 on 2008-08-01
in add and remove just type flash and check the first package then hit apply.

---

### Post by tuxxy on 2008-08-01
This may be of use to install Flash9,

[http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu](http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu)

---

### Post by torgrot on 2008-08-01
I already have installed flash,  I am in the process of trying to install the ubuntu-restricted-extras.  It wants to install flash from a location that doesn't exist.  

torgrot

---

### Post by Thelasko on 2008-08-01
How are you trying to install it?  The only correct way is:
```
sudo apt-get install flashplugin-nonfree
```
If that doesn't work then try:
```
sudo apt-get remove --purge flashplugin-nonfree
```
and try it again.

Further information [here.]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890")

---

### Post by Thelasko on 2008-08-01
> I am in the process of trying to install the ubuntu-restricted-extras. It wants to install flash from a location that doesn't exist.
Did everything else install correctly?

---

### Post by torgrot on 2008-08-01
I don't want to install the flash plugin.  I want to install ubuntu-restricted-extras.  It contains a broken link to flash and the package ubuntu-restricted-extras will not complete because of the broken link.   Can't you people read.  It is trying to download from [http://fpdownload.macrocmedia.com](http://fpdownload.macrocmedia.com)  there is nothing there.  You can't ping, you can't go there with firefox.  It ain't there it is broken.

torgrot:confused:

---

### Post by Thelasko on 2008-08-01
> I already have installed flash
Then why are you installing it again?

> Can't you people read.
Insulting us wont help.  If people aren't answering your question, perhaps you need to rephrase it.

From what I gather you are trying to install the restricted extras but you already have flash.  When it bombs out on the flash install, does it install the other packages?  You can install the other packages individually too.  [Here is a list.]("http://packages.ubuntu.com/hardy/ubuntu-restricted-extras")

---

### Post by tuxxy on 2008-08-01
You could manually download the files you needed,

[http://packages.ubuntu.com/hardy/ubuntu-restricted-extras](http://packages.ubuntu.com/hardy/ubuntu-restricted-extras)

---

### Post by Thelasko on 2008-08-01
> It is trying to download from [http://fpdownload.macrocmedia.com](http://fpdownload.macrocmedia.com) there is nothing there.I don't think the link you posted is the full URL.  I went to Adobe and it gave me this page.
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

---

### Post by torgrot on 2008-08-01
I tried to change the title of the post, it doesn't seem to work.  

I am trying to install the ubuntu-restricted-extras.  That package contains the adobe flash player.  I already have the adobe flash player installed.  The package is still trying to download from a location that doesn't exist.  It hasn't existed since adobe bought macromedia.  I am frustrated with this installation.  The help for getting the restricted codecs tells you to download the restricted extras package.  As long as that package has the broken adobe link in it, it won't complete.

This was a problem on Gutsy which I thought might have been repaired on Hardy, how foolish is that?  It has attempted the download from the broken link 27 times now.  The package won't complete.

torgrot

---

### Post by t0p on 2008-08-01
> **torgrot said:**
> I don't want to install the flash plugin.  I want to install ubuntu-restricted-extras.  It contains a broken link to flash and the package ubuntu-restricted-extras will not complete because of the broken link.   Can't you people read.  It is trying to download from [http://fpdownload.macrocmedia.com](http://fpdownload.macrocmedia.com)  there is nothing there.  You can't ping, you can't go there with firefox.  It ain't there it is broken.

torgrot:confused:

**Torgrot**, I can understand your frustration at some of the people who've replied - you have repeatedly said you don't want to install (again) the flash player, yet folk keep telling you how to install it! *but* if you insult them, people will be less inclined to help you.  You're right, of course - some of these bozos clearly *can't* read - but what you need to do it restate your problem in clear, simple terms that even an idiot will be able tro grasp! ;)

As for your problem: I'm pretty sure that all the drivers etc in ubuntu-restricted-extras are also available to download separately.  You'll have to do that.

---

### Post by torgrot on 2008-08-01
Thank you for reading what I was saying.  I am sorry if I am frustrated and losing patience and have insulted anyone.  That was certainly not my intent.  If I go to the link in firefox this is what is returned
Not Found

The requested URL /get...9_linux.tar.gz was not found on this server.
Apache/2.0.52 (Unix) Server at download.macromedia.com Port 8000

It is broken....

torgrot

---

### Post by tuxxy on 2008-08-01
Just install these packages from synaptic and your done

[LIST]
[*]gstreamer0.10-ffmpeg 
[*]gstreamer0.10-pitfdll [i386]
[*]gstreamer0.10-plugins-bad 
[*]gstreamer0.10-plugins-bad-multiverse  
[*]gstreamer0.10-plugins-ugly 
[*]gstreamer0.10-plugins-ugly-multiverse 
[*]icedtea-gcjwebplugin 
[*]libdvdread3 
[*]liblame0  
[*]msttcorefonts 
[*]unrar
[/LIST]

---

### Post by Thelasko on 2008-08-01
> It is broken....
Works for me.  Are you behind a firewall or something?

---

### Post by Thelasko on 2008-08-01
Wait, Port 8000?  That's odd, That's Intel Remote Desktop Interface.  It probably should be 8080, HTTP alternate.  Do you have some funky port forwarding settings?  Either that, or Adobe is running their server on the wrong port.  If they are on the wrong port, why didn't I catch it?

---

### Post by torgrot on 2008-08-01
Hitting control-c often enough convinced it to give up on flash and complete the rest of the installation.  The normal sudo apt-get flash... works every time.  I don't know what is wrong with the restricted extras package, it gets stuck on flash regardless.  The link it prints out doesn't exist  If I just go to adobe the full link is [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)  The package indicates that it is trying to download [http://fpdownload.macromedia.com/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/install_flash_player_9_linux.tar.gz)  they aren't the same links.

torgrot

---

### Post by forger on 2008-08-01
can you post back with the output of the following commands:
```

apt-cache policy ubuntu-restricted-extras flashplugin-nonfree

```

---

### Post by Thelasko on 2008-08-01
Now I see what you mean.  I never had that problem.  I recommend installing the packages individually and [writing a bug report.]("https://bugs.launchpad.net/ubuntu")

---

### Post by forger on 2008-08-01
> **torgrot said:**
> The link it prints out doesn't exist  If I just go to adobe the full link is [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)  The package indicates that it is trying to download [http://fpdownload.macromedia.com/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/install_flash_player_9_linux.tar.gz)  they aren't the same links.


It shouldn't do that, ubuntu-restricted-extras is a metapackage (in other words a "shortcut") to install the packages that depend on it. In other words, it just installs the flashplugin-nonfree.
If you reinstall ubuntu-restricted-extras it doesn't reinstall the dependant packages automatically.

It could be a faulty package from backports, that's why I asked the output of the cache policy in the previous post.

If you don't want to install the flashplugin-nonfree, then just get the dependencies of the ubuntu-restricted-extras:
```
apt-cache depends ubuntu-restricted-extras
```
..install separately the packages you need

If you want to object to it being included in ubuntu-restricted-extras, try [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)

---

