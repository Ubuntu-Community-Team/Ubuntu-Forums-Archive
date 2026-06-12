---
title: "HOWTO: Install git-compiz through synaptic in Intrepid"
date: 2008-11-04
forum: Outdated Tutorials &amp; Tips
---

### Post by loomsen on 2008-11-04
I'm basically just reassembling 
[this thread before it will die, hence it's got some quite usefull information](http://ubuntuforums.org/showthread.php?t=966030)

First, some prerequisites we might need:
/etc/init.d/brain  start

If you don't know what git is, this probably isn't for you.
If you prefer your OS to be ultrastable and reliable, this probably isn't for you neither.
If you're a bug:[img=http://ecx.images-amazon.com/images/I/312TVXQD44L._AA280_.jpg][/img]

Everybody else, herre we go.

We're going to add shames git-repository, probably one of the best maintained to our sources list. Then we're going to remove our compiz shipped with intrepid completely. Finally we're going to pull compiz from git easily through synaptic.

1. Drastically improving compiz through protobuf:
```

sudo apt-get install libprotobuf0 libprotobuf-dev libprotobuf-java protobuf-compiler python-protobuf
```

[Info about protobuf](http://dev.compiz-fusion.org/~cornelius/2008/10/19/startup-time-improvements-part-1/)

And hence protobuf is enabled by default, we've got nothing else to do in this section.

Note: the protobuf extension will probably cause heavy tearing and loads after initial setup, as it's building the cache then. Stay logged in for like 5-10 minutes, log out and back in, and feel the difference :)
But that l8r.

2. Now we've got to remove our old compiz installation completely, otherwise we'll get some broken dependency messages and our update notifier going nuts for this last update he isn't able to install.

In the thread above is shown what you can do if you're already facing that problem, here we're going to do it right.

So, for now, as we're going to purge everything right away, you should have thought about doing a backup yourself already. To export your profile, go to ccsm -> preferences and hit export profile :) name and place it foo.bar-whatever and place it to your prefered backup location.

Now you should change your window decorator if you've got emerald or compiz running.
```
metacity --replace
```

Now search synaptic for compiz, but don't take the quick search as it will maybe not show everything we want. Mark all installed packages now for complete removal. Sort them by status, and then mark every package you see, rightclick, mark for complete removal.
[[img]http://www.ubuntu-pics.de/thumb/5213/screenshot_63_2a7cHi.png[/img]](http://www.ubuntu-pics.de/bild/5213/screenshot_63_2a7cHi.png)

You may omit cairo-clock if you like :)screenlets, awn and sim-dock as well if you have any of them installed. Everything else should be removed.


3. Add shames repo to your list:
I assume you have intrepid, then do this for instance:
```

sudo -i
echo 'deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./' >> /etc/apt/sources.list.d/custom.list
apt-get update
wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
[color=red]exit[/color]

```

Alright, sources set up, now lets get this working:

---

