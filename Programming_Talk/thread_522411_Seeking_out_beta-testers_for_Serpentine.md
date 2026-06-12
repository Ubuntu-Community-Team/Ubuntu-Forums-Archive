---
title: "Seeking out beta-testers for Serpentine"
date: 2007-08-10
forum: Programming Talk
---

### Post by cogumbreiro on 2007-08-10
I am in dire need for beta testers for [Serpentine](="http://s1x.homelinux.net/projects/serpentine/"). I am tackling [bug #345270]("http://bugzilla.gnome.org/show_bug.cgi?id=345270") from [the bug list for the next release]("http://tinyurl.com/38lfsr"):

[LIST]
[*][#333281]("http://bugzilla.gnome.org/show_bug.cgi?id=333281"): Persistent options
[*][#345270]("http://bugzilla.gnome.org/show_bug.cgi?id=345270"): Removing WAVs during recording may ruin it
[*][#463180]("http://bugzilla.gnome.org/show_bug.cgi?id=463180"): New totem.plparser API
[*][#465352]("http://bugzilla.gnome.org/show_bug.cgi?id=465352"): Cannot record if the same file is listed twice
[/LIST]

The only thing you need to do is try to run latest development version and write a CD with Serpentine.
My [CD recorder is not recognized by Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114307"), so I cannot test my latest changes. The development version is available at:

[http://bazaar.launchpad.net/~cogumbreiro/serpentine/main]("http://bazaar.launchpad.net/~cogumbreiro/serpentine/main")

If someone helps out fast I will make a release and postpone [#465352]("http://bugzilla.gnome.org/show_bug.cgi?id=465352"), since that obligates me to install alot of packages from source or install Gutsy.

PS: this is based on [this post]("http://irrepupavel.blogspot.com/2007/08/seeking-out-beta-testers-for-serpentine.html").

---

### Post by steve.horsley on 2007-08-12
That link to the dev version isn't working. 404 error.

---

### Post by bruce89 on 2007-08-12
> **steve.horsley said:**
> That link to the dev version isn't working. 404 error.

I believe [https://code.launchpad.net/~cogumbreiro/serpentine/main](https://code.launchpad.net/~cogumbreiro/serpentine/main) is the right link.

Good to see Serpentine has been resurrected.

---

### Post by cogumbreiro on 2007-08-13
The link is correct. It is just not for the browser. It is to be used with [bazaar]("http://bazaar-vcs.org/"). To download the development version of Bazaar you must do:
```

sudo apt-get remove serpentine
sudo apt-get install bzr
bzr branch http://bazaar.launchpad.net/~cogumbreiro/serpentine/main serpentine
cd serpentine
./autogen.sh
./configure
make
sudo make install

```

If you want to remove the development version from your system you just have to open a terminal and
```

cd path/to/serpentine/sources
sudo make uninstall

```

---

