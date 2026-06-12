---
title: "howto install latest nightly build of WENGO"
date: 2006-09-07
forum: Outdated Tutorials &amp; Tips
---

### Post by pau on 2006-09-07
Hi,

wengo is a GPL option to skype. It works very fine but the latest deb package offered in their eb site is buggy; the sound for instance is not working at all. 
If you want to use wengo you'll have to go to the bleeding edge and download one of the latest nightly builds. This script here below will install the **latest** nightly build of wengo in your home directory.

You'll need lynx, wget and gawk for it...

```
sudo apt-get install lynx wget gawk
```

To start
it just type ./Engega_wengo.sh in the directory ~USERNAME/wengo or click the icon.

To install just use the script as follows:
```

chmod u+x instal_wengo.sh && ./instal_wengo.sh
```

This is the script:

```
#!/bin/sh
clear;
echo -n "Installation latest nightly build of WENGO...";

echo -n "";

sleep 3;
lynx -dump http://download.wengo.com/nightlybuilds/binary/NG/GNULinux/rc2/ | tail -1 | gawk '{print $2}' > > /tmp/Wengo.txt&&
wget `cat /tmp/Wengo.txt`&&
tar xvfj wengophone*&&
rm wengophone*&&
mv wengo* $HOME/wengo&&
cd $HOME/wengo&&
wget www.aei.mpg.de/~pau/Engega_wengo.sh&&
chmod u+x Engega_wengo.sh&&
clear;
echo "The latest nightly build of WENGO has been installed in `whoami`/wengo To start it run ./Engega_wengo.sh or click the icon..."
```

enjoy...

---

### Post by jis on 2006-12-16
I think your script is outdated since there are newer versions of Wengo NG at 
[http://download.wengo.com/nightlybuilds/binary/NG/GNULinux/2.0/](http://download.wengo.com/nightlybuilds/binary/NG/GNULinux/2.0/) than at [http://download.wengo.com/nightlybuilds/binary/NG/GNULinux/rc2/](http://download.wengo.com/nightlybuilds/binary/NG/GNULinux/rc2/).

BTW I downloaded WengoPhone-2.0-linux-bin-x86.tar.bz2 from [http://www.wengo.com/index.php/mp_download_wp_lin](http://www.wengo.com/index.php/mp_download_wp_lin) and it does not work any better than the version installed from Ubuntu Dapper's repository :(

---

### Post by Praxicoide on 2007-01-30
I've just downloaded Wengo 2.1 through the latest nightly build and it really buggy, with none of the toolbars working and no way of making calls.

Is there anything I might be doing wrong?

---

### Post by Praxicoide on 2007-01-30
I tried with a 2.0 build and still no luck. Even before I log in it says "your profile could not be loaded."

I tried another profile and the same.

---

### Post by solotim on 2007-03-26
Why is it so complicated?
What you should do is download the wengophone 2.1 rc2 directly from wengo's website.
unpack it and run wengophone.sh.

that's all.

it works.

---

### Post by lexarrow on 2007-05-29
did that and I can't connect + my webcam doesn't work

---

### Post by jis on 2007-05-29
lexarrow, try deleting ~/.wengo and/or ~./wengophone and relogin in WengoPhone 2.1.

Couldn't make sound in test call (to 333) work anyway.

---

