---
title: "[SOLVED] Firefox won't open... With the icon, at least."
date: 2008-06-09
forum: New to Ubuntu
---

### Post by IAmMe1 on 2008-06-09
Hello, I just installed Ubuntu on my new laptop, and I'm having a rather odd problem. When I click on the icon for Firefox, I get the little bar at the bottom of screen that says "starting Firefox," but then that bar goes away and Firefox doesn't open. Even if I go into Terminal and type "firefox" nothing happens. If I open it with sudo, it works, but that's kind of a pain/hassle and I'd like to avoid that. Anyone know what I can do?

Thanks.

EDIT: SOLVED.

---

### Post by Separ on 2008-06-09
Try hitting Alt+F2 and typing
```
killall firefox
```

and then try opening it again :)

---

### Post by IAmMe1 on 2008-06-09
No such luck. It didn't change anything...

---

### Post by IAmMe1 on 2008-06-12
Anyone have any ideas? It's still giving me trouble.

---

### Post by Xiong Chiamiov on 2008-06-12
You say running it from terminal causes nothing to happen.  Do you get some sort of anything in the terminal, but it just doesn't launch?  Could you please post what you get?

---

### Post by sam_delta on 2008-06-12
yeah, what error messages you get when you type it in the terminal?

sam

---

### Post by sdowney717 on 2008-06-12
try reinstalling firefox

open synaptic system-admin-synaptic
search firefox
do a complete remove
then reinstall

---

### Post by sdowney717 on 2008-06-12
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

you can also try another browser like seamonkey

---

### Post by ChameleonDave on 2008-06-12
Start the browser from the console like this:

```
firefox -ProfileManager
```

This will allow you to create a clean profile.  Does it work like that?  Is the problem with your old profile?  Tell us what output there is on the console if it crashes.

----

> **sdowney717 said:**
> try reinstalling firefox

open synaptic system-admin-synaptic
search firefox
do a complete remove
then reinstall

That's an extreme solution.  A complete removal will destroy his bookmarks, etc.  He may have a lot of important information there.  Try a fresh profile first.

---

### Post by drs305 on 2008-06-12
Try running this and seeing if *any * firefox resources are being used:

```
ps aux | grep firefox*
```

If you find something, like firefox-bin, use the following command combined with the **number** in the second column from the previous command to kill the process:
```
sudo kill -9 **XXXX**
```.

If that doesn't work, see if firefox is locked:
```
sudo find /home | grep *lock
```
Look for something like .parentlock and delete it if found.

The reason it works with sudo is that it uses different configuration files than when you open it as user.

---

### Post by sdowney717 on 2008-06-12
he just installed ubuntu so likely has no bookmarks

Firefox 3 uses two different formats for the bookmarks the 'classic' HTML format that is still available via Bookmarks > Organize Bookmarks > Import & Backup (Import and Export HTML) and JSON backups via the Backup and the Restore entry in that menu.
Restoring a JSON backup replaces all the bookmarks and importing a HTML file merges the imported bookmarks with the current bookmarks.

---

### Post by IAmMe1 on 2008-06-13
OK, here's the deal. I get no error messages whatsoever when trying to run Firefox. Nothing happens, period. When I tried firefox -ProfileManager, nothing happened without being root, and I got a normal window when I added sudo.

Searching for processes gives me: 

```
7615  0.0  0.0   3004   768 pts/1    S+   16:48   0:00 grep firefox*
```

Even though that appears to be the process of my searching for Firefox, I killed it anyways. That wasn't useful.

The sudo find /home etc. didn't work, here's the output:
```

find: /home/[my username]/.gvfs: Permission denied
```

I'd prefer not to uninstall Firefox if at all possible, I already transferred my bookmarks and whatnot over from my other computer... Anyone have any other ideas before I reinstall?

Thanks for the help though.

---

### Post by kansasnoob on 2008-06-13
This is probably just downright lame, but it's free:)

The first three things I do whenever something malfunctions are:

1. I open synaptic and click reload and then I look at the bottom of the screen where it shows xxxxxx# of packages installed, broken, etc. Hey I'm a nOOb, I'm old, not that smart, and I break things ........ so once in a while it'll show a broken package.

2. To resolve any possible unmet dependencies I might have created I execute one of the few commands I've memorized: sudo apt-get -f install.

3. I restart in "recovery mode" and watch for any "failures" and I come here to the forums and ask what the heck to do next (I quite often don't even know what the final lines of recovery mode text are telling me to do).

I know this is silly, but hey:confused:

---

### Post by iamjay on 2008-06-13
This happened to me too. Until I noticed that my hard drive was full. Clear up your hard drive and it should works. The reason that firefox still works with the root account is because the file system reserves some disk space for root user.

---

### Post by ChameleonDave on 2008-06-14
> **IAmMe1 said:**
> OK, here's the deal. I get no error messages whatsoever when trying to run Firefox. Nothing happens, period. When I tried firefox -ProfileManager, nothing happened without being root, and I got a normal window when I added sudo.

Hmm, your situation kind-of reminds me on this comic: [http://xkcd.com/149/](http://xkcd.com/149/).

Anyway, try this:

```
killall firefox
cd ~/.mozilla/firefox
mv profiles.ini profiles.ini.backup
firefox
```

That should force it to use a fresh profile as user.  Does it still fail?

Or else:

```

sudo apt-get purge firefox
sudo apt-get install firefox
firefox

```

Perhaps there is some sort of permissions problem.  In that case, do this:

```

sudo chown -R **YOURUSERNAME**:**YOURUSERNAME** /home/**YOURUSERNAME**
chmod u+rw -R /home/**YOURUSERNAME**

```

I can't think of anything else.

---

### Post by IAmMe1 on 2008-06-14
Well the profile change fixed it, but it deleted my bookmarks. Ah well, I can pretty much replenish those. Thanks!

---

### Post by ChameleonDave on 2008-06-14
> **IAmMe1 said:**
> Well the profile change fixed it, but it deleted my bookmarks. Ah well, I can pretty much replenish those. Thanks!

Great!

Your bookmarks are still backed up in a directory at ~/.mozilla/firefox.  You should be able to extract them somehow.

---

### Post by InHisName on 2008-09-14
Thanks guys, for the clues to helping me solve my similar problem.

I ran firefox from terminal once. I happend to be in sudo bash mode. That was my undoing.  By starting up firefox with sudo, I inavertedly used root instead of the normal user. Now the new saved items have root ownership and the normal user cannot open them any more.

As sudo user I can chgrp back to users and chown back to user. THEN when I started firefox all worked just fine once again.

Whew! one more problem fixed.

---

