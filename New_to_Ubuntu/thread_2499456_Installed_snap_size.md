---
title: "Installed snap size"
date: 2024-07-28
forum: New to Ubuntu
---

### Post by sunday28 on 2024-07-28
Hello.
I'm checking how much space an app installed as a snap package takes up.
For example:
```
snap info chromium | grep installed

```Result:
```
installed: 126.0.6478.182 (2910) 171 MB

```However, lsblk returns the result for the corresponding loop device
```
loop /snap/chromium/2910 size 163.8 M

```If I understand correctly, the size of the loop device should be exactly equal to the amount of space occupied by the program on disk.
 And the above numbers are just different units of measurement: 163.8 MiB = 171 MB.
Is this correct or am I doing something wrong?

---

### Post by currentshaft on 2024-07-28
> **sunday28 said:**
> 
If I understand correctly, the size of the loop device should be exactly equal to the amount of space occupied by the program on disk.

What facts or reasoning led to this understanding?

Also, why does it matter if the sizes are 4% different?

---

### Post by sunday28 on 2024-07-29
> **currentshaft said:**
> What facts or reasoning led to this understanding?

Also, why does it matter if the sizes are 4% different?

I wonder how snap works. And is it true that loop is, in fact, a snap program mounted in a virtual file system. That is why I compared the size of loop with the size of "installed" by empirical calculation. Of course, 4% doesn't matter. I am interested in the difference only in the given context. And there really is no difference, if it's just different units of measurement. Thank you for your  reply ;)

---

### Post by arubislander on 2024-07-29
I did the math on a few other snaps I had installed, and it would seem your hunch is correct.

---

### Post by sunday28 on 2024-07-29
Thank you, I see. I did the math not only with apps, but with system components (snapd, cups...) as well.

---

### Post by TheFu on 2024-07-29
Loop devices are just a way to provide access into the snap, read-only, file system.  They don't use any storage.  The storage used by snap packages are in /var/snap/..... for the packages with settings and data stored elsewhere like ~/snap/.... for personal snap data (I think.

The real problem with storage and snap packages is that by default, 3 snap versions for each installed snap are retained. It is possible to have the snap subsystem only keep 2 versions, but there it no way I can find to only have 1 version retained ... short of removing all versions of the snap package, then reinstalling it.  Due to the nature of snap packages and snap dependencies, there will always be bloat.  Both on disk use and for RAM used.

---

### Post by sunday28 on 2024-07-29
> [COLOR=#000000]The storage used by snap packages are in /var/snap/..... for the packages with settings and data stored elsewhere like ~/snap/.... for personal snap data (I think.[/COLOR]

I got a little confused. I looked at the paths. Very small storage on the disk are occupied there. Yes, /snap is only 146MB. While chromium alone downloaded 170 MB when installed. Where then were the snap programs installed?

> [COLOR=#000000]by default, 3 snap versions for each installed snap are retained.[/COLOR]

2 versions, AFAIK.

> [COLOR=#000000] but there it no way I can find to only have 1 version retained ... short of removing all versions of the snap package, then reinstalling it.[/COLOR]

I just manually remove old revisions after each update.
Thank you! It was interesting for me to read your answer.

---

### Post by deadflowr on 2024-07-29
> The storage used by snap packages are in /var/snap/
It's actually in /var/lib/snapd/snaps.
/var/snap is more or less the equivalent of the /etc directory for snap global configurations.

Well as far as equivalencies can go with snaps

---

### Post by TheFu on 2024-07-29
Sorry, I was winging the locations. If they weren't there, they were close enough  to easily fined (for me).  If not, there's always the **locate** command or **find**.

Plus, I remove all snaps and the snap subsystem from most of my computers, so looking doesn't always result in finding anything.  Sometimes I'm too lazy to bother ssh'ing into a different system.  Considering how trivial using ssh is for me, that just goes to show how completely lazy I can be.  ;)  OTOH, for people new to Unix systems, all these things can seem really hard, especially if you've never used/heard of them before. I forget what that was like sometimes.

---

### Post by sunday28 on 2024-07-30
> **deadflowr said:**
> It's actually in /var/lib/snapd/snaps.


Thank you very much.
The sizes of all snaps in this folder are exactly equal to the corresponding loop devices.
So, as far as I understand, the snap package installation and operation mechanism is as follows.
Installation creates a read-only loop device.
It actually plays the role of a sandbox.
Its size is exactly equal to the downloaded snap package.
These loop devices are mounted at login.
When the snap program is run, the data is unpacked using this loop device as sandbox.
That is, in fact, the loop device itself can be identified with the installed snap program.
The only thing that still needs to be taken into account: snap packages store their data in different places on the system, such as /var/snap/ and ~/snap/
Is that true or something wrong?

---

