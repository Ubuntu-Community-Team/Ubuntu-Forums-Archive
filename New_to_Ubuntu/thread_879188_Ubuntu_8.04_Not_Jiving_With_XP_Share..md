---
title: "Ubuntu 8.04 Not Jiving With XP Share."
date: 2008-08-03
forum: New to Ubuntu
---

### Post by theragingking on 2008-08-03
Hey all,

So, I've recently had to clean install 8.04 Hardy because of a botched upgrade from 7.10 Gutsy. Now my wireless XP tablet and my roommate's Vista (gag) lappy can't see my machine. The Tablet still displays the shares from the 7.10 installation, and does register a "Berith" (name of comp) being connected... But double clicking and entering the password just gets me a blank entry screen.

From the Ubuntu end of things, I can see and open both the XP and Vista share's, but 

1) I can't copy files from the XP share. I get the message: 

```
Error while copying -file-.
There was an error copying the file into -folder-.
```

And in the little drop down Detail area:
```
Permission denied
```

2) I can't see any of the Vista Share's folders. Not a huge problem, but it'd be cool if we fixed that. I guess.

Any idea what's wrong?

Thanks for your time,
TRK~

---

### Post by northern lights on 2008-08-04
Navigate to "System > Administration > Software Sources". Enable all
repositories but 'proposed' and 'backports'.

Then run ```
sudo apt-get update && sudo apt-get install samba samba-common smbclient smbfs gsambad
```

Then```
gksu gsambad
```to configure your samba shares.

---

### Post by theragingking on 2008-08-04
Thank you, but how do I configure this? In gutsy, I never had to deal with this; it just automatically read my windows shares.

Help?

---

### Post by theragingking on 2008-08-05
Bumping, cause I still need an answer.

---

### Post by cariboo on 2008-08-05
Have a look here, this might help you:

[http://www.ubuntugeek.com/howto-setup-samba-server-with-tdbsam-backend.html](http://www.ubuntugeek.com/howto-setup-samba-server-with-tdbsam-backend.html)

Jim

---

### Post by theragingking on 2008-08-08
Well, this is no good; followed everythign to a tee and now not only can my windows machines not see my ubuntu machine, but now my ubuntu machine can't see my windows machines.

Why can't I just share them via a windows network like I did in 7.10 without all of the setup crap? What changed that I have to go through this now?

Someone please explain, and maybe even toss a little more help my way; this is really starting to make me mad. :mad:

TRK

---

### Post by John_K on 2008-08-08
> **theragingking said:**
> Well, this is no good; followed everythign to a tee and now not only can my windows machines not see my ubuntu machine, but now my ubuntu machine can't see my windows machines.TRK

You "got a witness."  I followed a [similar set of instructions]("http://ubuntuforums.org/showthread.php?t=202605") this morning and got the same results.  I finally have time now to sit down and scour the forum/fora. [In the past I've just un-installed & reinstalled the packages I've b0rked but I tend not to learn much that way.]  Anyway, I'd appreciate hearing more on this myself.

Thanks in advance to all.

---

### Post by John_K on 2008-08-08
Oh, well. I took the lazy way out:
. opened up pckg mgr;
. uninstalled anything samba-related
. rebooted box [Windoze habit from way back...]
. opened package mgr
. reinstalled about 75% of samba-related stuff
    . package manager presented dialog box to tell me
      there was an existing smb.conf file and would i
      like to over-write or re-use.  As editing this
      appeared to be the beginning of [most of] my
      headaches, i opted to over-write
. fired up Smb4k
. everything works!  At least now I don't reinstall
  the entire distro to fix my screw-ups.  Thank the
  FSM -- and Debian -- for the packaging system.

Not exactly the way of the warrior geek but there's paying
work to be done.  Now, on to my next f***-up.  \\:D/

---

### Post by dmuir on 2008-08-14
Make sure you've got the ports open for Samba sharing. Took me a while to figure out that the reason why I couldn't see my shares anymore was because it was firewalled. I'm using Firestarter, so all I had to do there was go to the Policy tab and add a rule under the "Allow Service" section. Pick Samba (SMB) from the dropdown list of names and hit "Add". Hope that helps.

Now I just wish that it would give me a more friendly error such as "connections through this port have been blocked" or something to that effect, so you know it's the firewall. Instead it dies silently, so you have no idea what went wrong...

---

