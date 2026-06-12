---
title: "What is .goutputstream?"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by hwyckoff on 2012-09-30
When I was in my terminal, I typed ```
ls -al
``` in my home directory and saw a whole bunch of files named ".goutputstream".  The file size was zero and I counted 22 of them just now. Do they serve a purpose?  I did a keyword search on Google and found nothing definitive.

Is this something I can or should clear out? Should I leave those files alone?

---

### Post by Bashing-om on 2012-09-30
hwyckoff;

A quick perusal indicates you may be a victim of a bug.
see launch pad to pursue this issue:
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785)

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by Hadaka on 2012-09-30
Hi, this is a known bug... Bug #984785
It is safe to delete them, I also used to get these but for unknown
reasons, i dont get them anymore,perhaps an update took care of
the problem, I really dont know.

```
rm .goutputstream* 
```

---

### Post by hwyckoff on 2012-09-30
Still learning more tricks. To delete those files, I had to type: ```
sudo rm ./.goutputstream*
```

I was able to verify their deletion by ```
ls -al
```

I apply all updates everyday. I am running Ubuntu 12.04 with a Cinnamon desktop. I wonder what is creating these goutputstream files.

---

### Post by Bashing-om on 2012-09-30
I did not do a lot of looking (the referenced launch pad link) but ....seems a lot of folks are presently asking the same question...maybe an answer by now ?

[INDENT]still learning even after all these years ==> BDQ

[/INDENT]

---

### Post by rai4shu2 on 2012-09-30
The problem is that this is such a low-level issue (some old migration issue from gio in glib2) that of course people are going to confuse it with everything from U1 to hardware issues or whatever. I doubt the problem exists on a purely gtk3 or qt4 setup. It's probably just gtk2 -> gtk3 related.

---

### Post by stephanvaningen on 2012-12-03
I had such a file after aborting a large file copy in nautilus: could that have something to do with it?

---

### Post by hwyckoff on 2012-12-03
I suppose it's possible, but I didn't do anything like that -- aborting file copies, that is.

---

### Post by vasa1 on 2012-12-03
[http://ubuntuforums.org/showthread.php?t=1973925](http://ubuntuforums.org/showthread.php?t=1973925)
[http://ubuntuforums.org/showthread.php?t=1938825](http://ubuntuforums.org/showthread.php?t=1938825)
and the already mentioned bug

---

### Post by Scorpio1953 on 2012-12-03
Hi Everybody, I was reading these messages and i found that i have the seem problem but i'm not able to remove the files with: sudo rm ./.goutputstream Any other idea? Thanks.

---

### Post by DuckHook on 2012-12-04
When working with the command line, you must be absolutely precise to make the command work as intended. Comments on your command are:

1. You do not need *sudo* unless you are trying to delete files outside of your /home directory. In fact, the use of *sudo* with the *rm* command must be done extremely carefully, as it has the potential to wipe out critical system files if used improperly. Since these files are owned by you, you can delete them without root privileges.

2. Your command is missing the critical wildcard character "*" which tells the *rm* command to delete all files that start with the *goutputstream* moniker, but don't just end there.

3. It is best, when using dangerous commands like *rm* to give it absolute paths to the files you want to delete so that you don't inadvertently delete files of the same name in an unintended directory. Therefore, the best way to structure this *rm* command is:

```
rm ~/.goutputstream*
```

where "~" means your /home directory. Remember the critical "*" wildcard.

As a side note, I am always very wary of recommending the *rm* command to new users because a slight mistyping can wreak havoc. Nautilus is quite effective for this particular job and has the added advantage that you can recover any unintended deletion from the trash. *rm* deletes files permanently, without recourse or warning, so must be used with extreme care.

---

### Post by Glasairman on 2013-02-19
> **stephanvaningen said:**
> I had such a file after aborting a large file copy in nautilus: could that have something to do with it?

I think you are right. I had a mass-copy hangup while copying from a home server to the Desktop. Had these mass "leftovers" too.

---

### Post by PshhPshh on 2013-04-02
Something outstreaming my system too ! Everything flows away, and I have no idea how to stop that !

---

### Post by Impavidus on 2013-04-02
Just delete all those .goutputstream-* files. It's a harmless bug.

---

