---
title: "Script to clean recycle bins"
date: 2013-01-04
forum: Programming Talk
---

### Post by mackconsult on 2013-01-04
I have a qnap TS259 that runs ubuntu.  I am trying to create a script that would clean up the recycle bin's for everything older than 3 months, by default the web GUI of the administration page does it every 12 months.

here is the script I have currently:

```
#!/bin/sh
####################################
#
# simple script that will walk thru the
# recycle bins on NAS and delete everything
# older than 90 days
#
####################################

/usr/bin/find /share/HDA_DATA/"Network Recycle Bin"/*.* -mtime +90 -rm {} \;
```

here is the response when I try to run it:

```
[/share/Data/templates] # ./cleanrecyclebin.sh
BusyBox v1.01 (2012.12.04-18:29+0000) multi-call binary

Usage: find [PATH...] [EXPRESSION]

Search for files in a directory hierarchy.  The default PATH is
the current directory; default EXPRESSION is '-print'

EXPRESSION may consist of:
        -follow         Dereference symbolic links.
        -name PATTERN   File name (leading directories removed) matches PATTERN.
        -print          Print (default and assumed).

        -type X         Filetype matches X (where X is one of: f,d,l,b,c,...)
        -perm PERMS     Permissions match any of (+NNN); all of (-NNN);
                        or exactly (NNN)
        -mtime TIME     Modified time is greater than (+N); less than (-N);
                        or exactly (N) days

[/share/Data/templates] #
```

Any help greatly appreciated.

---

### Post by r-senior on 2013-01-04
I think you need something more like:

```
/usr/bin/find /share/HDA_DATA/"Network Recycle Bin"/ -mtime +90 -exec rm {} \;
```

It's always safest to try the command with -print instead of the -exec before commiting to deletion of course. You'll need a recursive delete and -f flag to handle directories which starts to get dangerous if it goes wrong.

---

### Post by Vaphell on 2013-01-04
*-exec rm* is not necessary, you can use *-delete* flag

---

### Post by mackconsult on 2013-01-04
I have tried both of your suggestions, still the same response occurs.

---

### Post by dannyboy79 on 2013-01-04
i believe it's because you have spaces in your directories name, you need to include the entire path within the quotes or escape the spaces with \ example:
```
/usr/bin/find "/share/HDA_DATA/Network Recycle Bin/*.*" -mtime +90 -rm {} \;
```

OR

```
/usr/bin/find /share/HDA_DATA/Network\ Recycle\ Bin/*.* -mtime +90 -rm {} \;
```

---

### Post by Vaphell on 2013-01-04
looks like that version of find is pathetic compared to the gnu find (my gut feeling based on googled [http://forum.qnap.com/viewtopic.php?t=23780](http://forum.qnap.com/viewtopic.php?t=23780)).
you have two choices:
- install gnu version
- use only mtime (it supposedly works) and then iterate the output, eg

```
find ... | while read -r f; do rm "$f"; done
```

---

### Post by mackconsult on 2013-01-04
Tried this ............

```
#!/bin/sh
####################################
#
# simple script that will walk thru the
# recycle bins on NAS and delete everything
# older than 90 days
#
####################################

find "/share/HDA_DATA/Network Recycle Bin/*" | while read -r f; do rm "$f"; done
```

And got this ......

```
[/share/Data/templates] # ./cleanrecyclebin.sh
find: /share/HDA_DATA/Network Recycle Bin/*: No such file or directory
[/share/Data/templates] #
```

---

### Post by dannyboy79 on 2013-01-04
is there a folder at that location? lol

Network Recycle Bin is not a folder that Ubuntu creates I know that much

---

### Post by lykwydchykyn on 2013-01-04
Looks more like busybox find can't do globbing.  Would leaving off the asterisk delete the trash bin directory?

---

### Post by Vaphell on 2013-01-04
* definitely needs to be outside the quotes to trigger globbing, wrapped in quotes it's just an ordinary char.

---

### Post by mackconsult on 2013-01-04
Yes there is


```
[/share] # cd HDA_DATA
[/share/HDA_DATA] # ls
Documents/           Network Recycle Bin/ Usb/                 charlie.mccormack/   pictures/            tempdownload/
Download/            Public/              Web/                 lost+found/          sheri.mccormack/     torrentdownload/
Multimedia/          Recordings/          aquota.user          music/               sydney.mccormack/    video/
[/share/HDA_DATA] # cd Network*
[/share/HDA_DATA/Network Recycle Bin] #
```


> **dannyboy79 said:**
> is there a folder at that location? lol

Network Recycle Bin is not a folder that Ubuntu creates I know that much

---

### Post by mackconsult on 2013-01-04
Ok it did something, but my network recycle bin did not shrink in size.  Its still 100 GB with stuff about 1 year old in it.  My goal once again is delete all files that more than 90 days old.


```
rm: /share/HDA_DATA/Network Recycle Bin/video/DVD_VIDEO_RECORDER: is a directory
rm: /share/HDA_DATA/Network Recycle Bin/video/DVD_VIDEO_RECORDER/VIDEO_TS: is a directory
rm: /share/HDA_DATA/Network Recycle Bin/Web: is a directory
rm: /share/HDA_DATA/Network Recycle Bin/Web/wordpress: is a directory
rm: /share/HDA_DATA/Network Recycle Bin/Web/wordpress/wp-content: is a directory
rm: /share/HDA_DATA/Network Recycle Bin/Web/wordpress/wp-content/uploads: is a directory
rm: /share/HDA_DATA/Network Recycle Bin/Web/wordpress/wp-content/uploads/2012: is a directory
rm: /share/HDA_DATA/Network Recycle Bin/Web/wordpress/wp-content/uploads/2012/10: is a directory
[/share/Data/templates] 
```

---

### Post by sudodus on 2013-01-04
> **mackconsult said:**
> I have a qnap TS259 that runs ubuntu.  I am trying to create a script that would clean up the recycle bin's for everything older than 3 months, by default the web GUI of the administration page does it every 12 months.

here is the script I have currently:

```
#!/bin/sh
####################################
#
# simple script that will walk thru the
# recycle bins on NAS and delete everything
# older than 90 days
#
####################################

/usr/bin/find /share/HDA_DATA/"Network Recycle Bin"/*.* -mtime +90 -rm {} \;
```
Going back to the original script:

I think it is quite close: just change *.* to *
The wild card * should ***not*** be within quotes

```
/usr/bin/find /share/HDA_DATA/"Network Recycle Bin"/* -mtime +90 -delete
```or
```
/usr/bin/find /share/HDA_DATA/"Network Recycle Bin"/* -mtime +90 -exec echo rm {} \;
```The use of -exec has the advantage, that you can test it with an echo inserted before doing the real thing: think -exec echo ... and check before
```
/usr/bin/find /share/HDA_DATA/"Network Recycle Bin"/* -mtime +90 -exec rm {} \;
```I use a similar alias to identify what was touched during the last seven days in the current directory

```
alias lastweek='sudo find * -ctime -7 -type f'
```

---

### Post by Vaphell on 2013-01-04
> Going back to the original script:
find used in that system is crippled and half the options from gnu find don't work, as evidenced by the very short list of allowed options printed.

> Ok it did something, but my network recycle bin did not shrink in size. Its still 100 GB with stuff about 1 year old in it. My goal once again is delete all files that more than 90 days old.
```
rm: /share/HDA_DATA/Network Recycle Bin/video/DVD_VIDEO_RECORDER: is a directory
```


*rm* can't remove directories by default, try adding *-rf* option (recursive, force). Be careful, *rm -rf* is serious business, one space in wrong place and you can wipe out everything.
you need to investigate by hand if the files that fit the criteria survive, temporarily use *echo "$f"* instead of *rm -rf "$f"* to get the printout and check the items.

---

### Post by sudodus on 2013-01-04
> **Vaphell said:**
> find used in that system is crippled and half the options from gnu find don't work, as evidenced by the very short list of allowed options printed.

*rm* can't remove directories by default, try adding *-rf* option (recursive, force)
you need to investigate by if the files that fit the criteria survive, temporarily use echo "$f" instead of "rm -rf "$f" to get the printout and check the items.

I see. So it is not 'vanilla' Ubuntu or Ubuntu Server. Would it be possible to install 'our standard find'? If not, why?

---

### Post by lykwydchykyn on 2013-01-04
> **Vaphell said:**
> 
*rm* can't remove directories by default, try adding *-rf* option (recursive, force). Be careful, *rm -rf* is serious business, one space in wrong place and you can wipe out everything.
you need to investigate by hand if the files that fit the criteria survive, temporarily use *echo "$f"* instead of *rm -rf "$f"* to get the printout and check the items.

It'd probably safer to run two find commands:  the first one specifying "-type f" and running rm, the second specifying "-type d" and running rmdir.

Since rmdir won't remove non-empty directories, you won't be deleting (for example) a folder more than 90 days old containing files that are less than 90 days old.  "rm -Rf" would do this.

---

### Post by lykwydchykyn on 2013-01-04
> **sudodus said:**
> I see. So it is not 'vanilla' Ubuntu or Ubuntu Server. Would it be possible to install 'our standard find'? If not, why?

The only reason would be space.  Busybox is a shell with "reasonable facsimiles" of common shell tools baked into it, all in a very tiny package.

If you want the real "find", I assume you'd have to install a real shell like bash or dash, and then the "findutils" package.

---

