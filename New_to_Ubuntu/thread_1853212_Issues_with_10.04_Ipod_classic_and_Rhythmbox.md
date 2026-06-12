---
title: "Issues with 10.04 Ipod classic and Rhythmbox"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by hellolife on 2011-10-01
First of all, I was able mount and connect my ipod classic black 80gb  to my computer (Dell Inspiron e1505) and open with rhythmbox once with Lucid Lynx 10.04.

Then suddenly it wouldn't work.

I've been sitting here for the last two hours trying to research and I'm getting pretty frustrated. Here's what's happened now:

My ipod simply won't mount. It won't show up on the desktop nor in Rhythmbox.
While researching I made some changes:

I followed these instructions:
[http://ubuntuforums.org/showpost.php?p=9277776&postcount=7](http://ubuntuforums.org/showpost.php?p=9277776&postcount=7)
to see if I could get it working in banshee. When I did this it would show up in banshee but just as read only.

Then I went to synaptic and removed the libgpod-common.
Upon doing that and then restarting my computer and opening rhythmbox then connecting my ipod, rhythmbox would close just as my ipod would mount.

So now I have no idea what's going on, what to do, and am getting really frustrated. Any help would be excellent.

---

### Post by ptn107 on 2011-10-06
libgpod4 and libgpod-common should be installed.  Don't remove them.  

Verify that:
1 - You're running the latest version for lucid (rhythmbox 0.12.8-0ubuntu7)
2 - rhythmbox-plugins is installed as well (0.12.8-0ubuntu7).
3 - The plugin 'Portable Players - iPod' is enabled within rhythmbox.

Post the result of
```
cat /etc/mtab && ls -l {/media,/mnt}
```
_after_ you plug in the iPod

---

### Post by wolfen69 on 2011-10-06
Try gtkpod. Always worked for me.

---

### Post by owiknowi on 2011-10-06
maybe this might be of use to you as well (it's mainly about kde, though):
[http://worldforum.pardus-linux.nl/index.php?topic=4069.msg21894#msg21894](http://worldforum.pardus-linux.nl/index.php?topic=4069.msg21894#msg21894)
and
[http://forum.pardususer.de/index.php?topic=2272.msg25962#msg25962](http://forum.pardususer.de/index.php?topic=2272.msg25962#msg25962)

translate the last with babelfish or g00gle

---

