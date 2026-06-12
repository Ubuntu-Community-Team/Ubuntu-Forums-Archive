---
title: "Lost password"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by mzimmers on 2012-03-18
...I was playing with passwords, and now it seems my password is inaccessible to me. I log in automatically, but I can't authenticate on anything that requires administrator access.

I followed the instructions here:

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

But I get an error:

> passwd: Authentication token manipulation error
passwd: password unchanged

So...I've evidently really messed something up. Can someone please help me recover from this?

Thanks!

---

### Post by lindsay7 on 2012-03-19
i bet you are trying to use the same password you had before the screw up, put in a new password, something you never used before and see if it works.

---

### Post by HiImTye on 2012-03-19
make sure your user exists in both /etc/passwd and /etc/shadow, i.e.
```
sudo cat /etc/passwd | grep <username>
sudo cat /etc/shadow | grep <username>
```

---

### Post by ubuntu27 on 2012-03-19
This is a known bug. I thought it was already fixed.

There is a bug that when you select "autologin" for your user, the user's password is **deleted**. Since the password has been deleted, the system no longer recognizes your password.

I will look for the bug report or a forum referencing to it.


EDIT: I couldn't find the specific forum and bug report that I was looking for, but here are some forum thread:

[Keyring AND login AND general password problems ubuntu 11.10]("http://ubuntuforums.org/showthread.php?t=1873589")

[Login password prompt]("http://ubuntuforums.org/showthread.php?t=1885149")

[Password is rejected by synaptic]("http://ubuntuforums.org/showthread.php?t=1659544")

---

### Post by HiImTye on 2012-03-19
ignore me, Im silly

---

### Post by mzimmers on 2012-03-19
> **ubuntu27 said:**
> This is a known bug. I thought it was already fixed.

There is a bug that when you select "autologin" for your user, the user's password is **deleted**. Since the password has been deleted, the system no longer recognizes your password.

I will look for the bug report or a forum referencing to it.

OK...so, what are my options here? I could re-install from scratch...I don't have a ton of stuff installed on it yet. Or, is there a simpler way, such as wiping out the passwd file or something? (I probably can't even do that, since I can't authenticate.)

---

### Post by mzimmers on 2012-03-19
> **HiImTye said:**
> make sure your user exists in both /etc/passwd and /etc/shadow, i.e.
```
sudo cat /etc/passwd | grep <username>
sudo cat /etc/shadow | grep <username>
```

Can't do this...I can't supply a password to sudo. I tried my old password, and nothing...both failed. This problem really has me hamstrung right now.

---

### Post by HiImTye on 2012-03-19
> **mzimmers said:**
> Can't do this...I can't supply a password to sudo. I tried my old password, and nothing...both failed. This problem really has me hamstrung right now.
do it using the same method you used to try to change your password on psychocats, you won't need to authenticate

---

### Post by mzimmers on 2012-03-19
Oh, very good. And yes, it's in both files (with what appear to be identical entries).

---

### Post by HiImTye on 2012-03-19
identical? that sounds like your password has been erased then, as one should include a checksum of the password (a series of seemingly random human readable characters). it seems as though your password is missing. you might remedy it by disabling auto-login and then using the psychocats method to reset your password.

when you log in it may ask you to enter a password to access your keyring, it will be your old password.

---

### Post by mzimmers on 2012-03-19
I think the reason they're identical is that (and I'm going from ancient memory here) the password is the second field in a line in etc/password. For all the entries in /etc/password, they're represented by an "x".

And...how do I disable auto-login? I can't do it through the User Accounts settings; I need to authenticate to do that.

---

### Post by mzimmers on 2012-03-19
Is there a way to re-install from my CD, but only a portion of the build, like just the core system? That way, I wouldn't lose my mods, and my downloaded apps, which would be nice.

---

### Post by HiImTye on 2012-03-19
in /etc/shadow, the first entry after your username should be $6 (indicating that the checksum is SHA based) and then it should be followed by a hash and then something like :15360:0:99999:7:::

for instance, here is an account I have inactive, just in case:
```
tye@T:~$ sudo cat /etc/shadow | grep backup
backup:*:15259:0:99999:7:::
tyebackup:$6$VBN3YuS643B0n/n0$6Rp9JL6JfkEfKiaK.veNJgetNwiAqIxjw4X9qNusFeMNOxw.RG8RTUmvroZCq7FUKL2aLkInAMeOicU4IG25t0:15360:0:99999:7:::
```

---

### Post by mzimmers on 2012-03-19
Well, it's not on mine; mine looks like this:

mzimmers:x:1000:1000:mzimmers,,,:/home/mzimmers:/bin/bash

That's all...

---

### Post by HiImTye on 2012-03-19
```
sudo nano /etc/lightdm/lightdm.conf
```
will bring up an ncurses editor
remove your username from ```
autologin-user=
```

---

### Post by HiImTye on 2012-03-19
> **mzimmers said:**
> Well, it's not on mine; mine looks like this:

mzimmers:x:1000:1000:mzimmers,,,:/home/mzimmers:/bin/bash

That's all...
that's /etc/passwd

---

### Post by mzimmers on 2012-03-19
Strange...I could have sworn I ran that on shadow as well, but I just checked, and it is indeed different:

mzimmers::15408:0:99999:7:::

I tried that nano command; it won't let me write the file: says it's a read-only file system. That's a cool trick, though; I'll have to remember it.

---

### Post by HiImTye on 2012-03-19
you have to run that command inside recovery mode, sorry I should have specified that again lol

---

### Post by mzimmers on 2012-03-19
> **HiImTye said:**
> you have to run that command inside recovery mode, sorry I should have specified that again lol

I did. It let me into the editor, and I got that error message when I tried to save the changes.

---

### Post by HiImTye on 2012-03-19
ok, load a liveCD and edit the file from that, it should let you save it (make sure to go to the path on your drive and not inside the liveCD or you won't actually change anything)

---

### Post by mzimmers on 2012-03-19
OK, I think I'd better call it a night and tackle this in the morning...I'm starting to get to that state where it's dangerous to be on a computer.

What command can I use from the command line to identify the internal drive for the path name?

Thanks for all the help tonight.

---

### Post by HiImTye on 2012-03-19
its pretty easy, the liveCD's paths will be what your regular paths are, the regular system's paths will be wherever you navigate to in Nautilus. hit the < at the top and it will show you 'Media' - look for your hard drive here and then the paths for other things will be thereafter (i.e. /media/Mblahblahblahblah/etc/lightdm/lightdm.conf)

any changes you make on the liveCD's files are discarded when you log out (unless you have a [persistent liveCD]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"))

---

### Post by mzimmers on 2012-03-19
When I boot from the CD, nautilus shows me the volume on the HDD, but it is still read-only. I went in and changed the permissions to allow root users read/write access, and changed the file.

Now, when I boot, I get a login prompt, and for my username, there's no request for a password, but when I hit "login," I get what I believe is referred to a kernel panic. The screen goes black, a little bit of tiny white text goes by, and it re-tries.

Something is still rotten with my user/passwd settings.

A naive question: what would happen if I just deleted my /etc/passwd file?

---

### Post by cryptotheslow on 2012-03-19
Just rewinding a little bit here. Regards having a read only filesystem when you boot into recovery mode. Before taking the option to drop to a root shell, use the option just above to remount the filesystem as read/write - then drop to the shell an continue.

[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/recoveryremount2.png[/IMG]

---

### Post by mzimmers on 2012-03-19
OK, that's good to know about, but...I've gotten the file edited. I now cannot log in. So...where should I go from here?

EDIT: I'd like to resolve this one way or the other pretty soon. I don't want to waste the forum's time searching for solutions, so if I don't find a fix in another hour, I'll just re-install from scratch.

---

### Post by HiImTye on 2012-03-19
now that it's edited to stop autologin to work around the bug that Ubuntu27 mentioned, follow the instructions that cryptotheslow gave you and then set your password using passwd

---

### Post by mzimmers on 2012-03-19
Let me make sure I'm clear on this. I should:

1. reboot (in recovery mode)
2. mount the disk read-write
3. drop into shell

and then do what?

If I just do steps 1 and 2, I get a login prompt. It doesn't ask me for a password, but if I click on "login" the screen goes dark for a few seconds, then returns to the login prompt.

---

### Post by HiImTye on 2012-03-19
do 1,2,3 then use passwd to set your passwd a la
```
sudo passwd <user>
```

you should be prompted to enter and then re-enter a new password (but not prompted for an old one as you are in recovery mode)

---

### Post by mzimmers on 2012-03-19
Oh, I gotcha. Well, I did that, and it said the password was successfully updated, but...upon reboot, I'm in the same situation: login screen and it doesn't ask for a password. Is there another file I should try editing?

---

### Post by HiImTye on 2012-03-19
> **mzimmers said:**
> login screen and it doesn't ask for a password.
any way for you to post a picture so I can understand what you're getting?

---

### Post by mzimmers on 2012-03-19
Well, it has to be a real picture, from a camera. This is the left side of my display:

[IMG]http://scopedin.com/images/screen.jpg[/IMG]

Nothing else on the display, really...a small menu bar across the top, and "ubuntu 11.10" at the bottom left.

---

### Post by HiImTye on 2012-03-19
ok let's stop doing this the hard way. let's make a backup account and fix things the easy way
```
sudo useradd mzbackup -m -s /bin/bash
sudo passwd mzbackup
<enter password>
sudo adduser mzbackup admin
```then log in as mzbackup and change your password for mzimmers

---

### Post by mzimmers on 2012-03-19
Well, I keep screwing myself into the ground worse and worse. I tried deleting some unnecessary partitions, and I seem to have wiped out GRUB. I'm looking into re-installing it now...I'll try your approach when I get booted again.

---

### Post by mzimmers on 2012-03-20
Resolution of this issue: I finally decided to just reinstall 11.10 and start over. This time I didn't enable the auto-login for my account. It's a bit more of a hassle, but will hopefully prevent me from getting into trouble again.

Thanks to all for the help; it was at least a learning experience.

---

