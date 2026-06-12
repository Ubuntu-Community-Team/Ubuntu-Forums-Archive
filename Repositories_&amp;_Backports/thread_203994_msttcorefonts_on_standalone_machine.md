---
title: "msttcorefonts on standalone machine"
date: 2006-06-26
forum: Repositories &amp; Backports
---

### Post by SoftGround on 2006-06-26
Is there any way to get msttcorefonts without having a local internet connection?

The deb install requires an internet connection to do a wget from sourceforge.

If I download the <font>.exe files on another machine, can I use them with the deb install or will it ignore them/try to overwrite them?

---

### Post by SoftGround on 2006-06-27
OK So I looked further back in the search results and found this.
(Thanks to jonathanjg who originaly posted it)
[ msttcorefonts thread Page 2]("http://www.ubuntuforums.org/showthread.php?t=76655&page=2&highlight=msttcorefonts")

Incase anyone is interested. What I did was:

It works on a standalone machine or a machine with too slow a modem (e.g. connexant with free linuxant driver!)

Download all the *.exe font files from [Source Forge corefonts page (see: 'the fonts')]("http://sourceforge.net/project/showfiles.php?group_id=34153") on your networked machine. (7.5M in total)

Install [**msttcorefonts **]("http://packages.ubuntu.com/dapper/x11/msttcorefonts")with _no internet connection_ (partially fails)
(needs  [**cabextract**]("http://packages.ubuntu.com/dapper/utils/cabextract"), so you may need that installed first)
 I have UbuntuPlus installed - there may be other dependencies if you do not.

Make a new directory /tmp/mstt
Copy the *.exe font files into the /tmp/mstt directory.

Run the script:
```
sudo /usr/sbin/update-ms-fonts /tmp/mstt
```
Delete the temporary directory

Then to tidy up the install do:
```
sudo apt-get install msttcorefonts
```

Regards
[B][I]
Soft Ground[/I][/B]

---

### Post by lipidicman on 2008-05-16
Forgive me if I shouldn't be bumping an old thread, but this is still a problem and last night with no net access and my aptoncd attempt broken I was getting annoyed.  Thanks for the help

---

### Post by lipidicman on 2008-05-19
I had no 'update-ms-fonts' in usr/sbin/
help?

---

