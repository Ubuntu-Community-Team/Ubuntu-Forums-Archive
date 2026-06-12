---
title: "How to: change notification (notify-osd) colors in Karmic"
date: 2010-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by genaroneto on 2010-01-11
I was browsing over Google to find a way to change the colors of notify-osd and found johnl's [topic]("http://ubuntuforums.org/showthread.php?t=1235732"). Since it's a little bit outdated, i myself ported and improved his path to work flawlessly on Karmic's version. 

The patch was made to work with version **0.9.24**

**1. download & install dependencies**
install basic development tools:

```
sudo apt-get install build-essential libnotify-bin
```

get the required libraries to build notify-osd:

```
sudo apt-get build-dep notify-osd
```

Download the source from notify-osd

```
apt-get source notify-osd
```


**3. download and apply the attached patch file**
right click on the attached .patch files. choose to save it in the same directory you fetched the source (in my case, ~/notify-osd-0.9.24). There are two patches attached. One purely adds the feature to change the colors. The other one changes it and also puts the notify on the very top right, just like older jaunty version (thanks [Julien Lavergne]("https://launchpad.net/~gilir/+archive/updates/+packages")). 

Choose one of these patches and apply it. 

```
cd notify-osd-0.9.24
patch -p1 -i notify-color-hack-karmic.patch.txt
```

or

```
cd notify-osd-0.9.24
patch -p1 -i notify-color-position-hack-karmic.patch.txt
```


There should not be any errors.

**4. build a new notify-osd**

```
dpkg-buildpackage -rfakeroot -uc -b
```

This will create a deb package of your hacked notify-osd in your home folder. Install it with gdebi or dpkg.

```

cd ..
sudo dpkg -i notify-osd-0.9.24*.deb
```

Now you have to create the config file that will determine the colors of the notification bubble.

**5. customizing the colors**
save the following file as ".notify-osd" in your home directory:

```

bubble-background-color = DBDBDB
bubble-background-opacity = .65
text-title-color = 000000
text-title-opacity = 1.0
text-body-color = 527499
text-body-opacity = 1.0
text-shadow-opacity = .1
text-shadow-color = 000000
```

edit the file ~/.notify-osd to edit the colors. Because this is a quick hack, make sure that each line follows the format "key = value" including the spaces around the equals sign. It's lame, I know.

*-color entries change the color of that item. For example, bubble-background-color changes the notification window color. The value for these entries is a html-style color without the leading "#". E.g,

```
bubble-background-color = c0c0c0
```

will give you a light gray window.

*-opacity entries change the opacity (transparency) of that item when compiz is enabled. "1.0" means entirely opaque. "0.0" means entirely transparent (invisible). E.g,

```
bubble-background-opacity = 0.75
```

Will give you a window that is 75% opaque.

**If you make changes to the configuration file you must kill the current running notify-osd process ('killall notify-osd') before you will see the changes. **You don't need to restart it as it will restart automatically next time it is needed.

[ATTACH]143351[/ATTACH]

Thanks to [johnl]("http://ubuntuforums.org/member.php?u=95551") for the original Howto

---

### Post by blazemore on 2010-01-13
Thanks for this guide. I have themed a beautiful blue desktop based on Google Chrome and the default colours just didn't fit!

How do you get the position to revert back to Jaunty style?

---

### Post by genaroneto on 2010-01-13
> **blazemore said:**
> Thanks for this guide. I have themed a beautiful blue desktop based on Google Chrome and the default colours just didn't fit!

How do you get the position to revert back to Jaunty style?


I have used the patch created by Julien Lavergne and merged with this one. It basically gets the bubble with dynamic, not fixed position. His patch can be found at [https://launchpad.net/~gilir/+archive/updates/+files/notify-osd_0.9.24-0ubuntu2~gilir1.tar.gz](https://launchpad.net/~gilir/+archive/updates/+files/notify-osd_0.9.24-0ubuntu2~gilir1.tar.gz) .

---

### Post by tommypayne on 2010-01-14
Nice guide! not only have you managed to complete my custom desktop but its fixed the positioning of the notifications which i must say has been bugging me A LOT!

Cheers man :D

---

### Post by monogo on 2010-01-14
Thank you very very much for this cool guide. Have been waiting a long time for such a possibility.


Just a question: What could I do to prevent "apt-get upgrade" to switch back to the original version from the sources? Anyone else with this "problem"?


edit: quite simple: forgot that I could lock the version in Synaptic...

---

### Post by vauge on 2010-01-14
Thank you.

---

### Post by WaCope on 2010-01-14
Thanks, great how-to.  Does anyone know a way to change how long it stays up?  The default seems to stay on screen way too long.

---

### Post by tylerannosaurus on 2010-01-14
> **genaroneto said:**
> I have used the patch created by Julien Lavergne and merged with this one. It basically gets the bubble with dynamic, not fixed position. His patch can be found at [https://launchpad.net/~gilir/+archive/updates/+files/notify-osd_0.9.24-0ubuntu2~gilir1.tar.gz](https://launchpad.net/~gilir/+archive/updates/+files/notify-osd_0.9.24-0ubuntu2~gilir1.tar.gz) .

How do I install this?

I tried extracting it, then doing a cd to the folder then ./configure but get this:

```
checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.16.0 gthread-2.0 gconf-2.0 gio-2.0) were not met:

No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by brk3 on 2010-01-30
It's pretty surprising/disappointing there isn't a better and more flexible way to customise these notifications.

I was hoping to theme it more than just changing the color?

---

### Post by k1piee on 2010-02-03
Awesome howto, just one question though.
What do I change in the patch to make it pop up in the bottom-right instead of top-right?

---

### Post by BOFH+ on 2010-02-10
> **brk3 said:**
> It's pretty surprising/disappointing there isn't a better and more flexible way to customise these notifications.

I was hoping to theme it more than just changing the color?

+1

I don't understand why it doesn't at least support a text or xml config file... sure we can hack notify-osd's source code, but that means having to reapply the patches at every update.

---

### Post by auh2o on 2010-02-13
Thanks for the tutorial, BUT, count me in among those who want to know how to edit the position of the notification! I want to move mine to the the bottom right corner, how do I do that?

---

### Post by dnascimento on 2010-03-15
Great Job man!! Thank you so much :D

---

### Post by leandro2000ar on 2010-04-04
> **k1piee said:**
> Awesome howto, just one question though.
What do I change in the patch to make it pop up in the bottom-right instead of top-right?

> **auh2o said:**
> Thanks for the tutorial, BUT, count me in among those who want to know how to edit the position of the notification! I want to move mine to the the bottom right corner, how do I do that?

Same problem. Please tell us how to change the position !!! Thanks

---

### Post by vitorbaptista on 2010-04-27
Hi,

As lots of people, I wanted the notifications to be at the left side of the screen. As I didn't found anything, I made my own. With my attached patches, you can put the notifies at top-right/middle-right (as usual), but also top-left/middle-left.

You need to download notification-osd's source from [https://launchpad.net/notify-osd](https://launchpad.net/notify-osd), and apply the patches attached. Then compile, install and change the location with gconf.

Use "gconftool-2 --set /apps/notify-osd/gravity --type int 2". Change the value from 2 to 0..4 and check the effects :)

---

### Post by murphymc on 2010-06-26
> **vitorbaptista said:**
> Hi,

As lots of people, I wanted the notifications to be at the left side of the screen. As I didn't found anything, I made my own. With my attached patches, you can put the notifies at top-right/middle-right (as usual), but also top-left/middle-left.

You need to download notification-osd's source from [https://launchpad.net/notify-osd](https://launchpad.net/notify-osd), and apply the patches attached. Then compile, install and change the location with gconf.

Use "gconftool-2 --set /apps/notify-osd/gravity --type int 2". Change the value from 2 to 0..4 and check the effects :)

Left/rightness is actually dictated by whether the language in use is left to right or right to left.  This is in defaults_get_top_corner of defaults.c toward the end of the function (line 2525 in my version).  If you want to adjust the side it shows up on, that is probably a better place to do it than in stack.c.  And it's easier too -- just reverse the if statement's logic.

---

### Post by vitorbaptista on 2010-06-27
> **murphymc said:**
> Left/rightness is actually dictated by whether the language in use is left to right or right to left.  This is in defaults_get_top_corner of defaults.c toward the end of the function (line 2525 in my version).  If you want to adjust the side it shows up on, that is probably a better place to do it than in stack.c.  And it's easier too -- just reverse the if statement's logic.

Thanks for the info. But changing in default.c, I would simply change the default, without giving an option for the user to choose, right?

If this is so, I prefer the way I did it. I appreciate to have options.

---

