---
title: "Failed to execute child process &quot;/usr/games/PlaneShift/uninstall&quot; (Permission denied)"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by vlad1975 on 2008-05-27
Could someone please tell me how to manually uninstall this. i just sick of trying to make this work now its telling me that i cant even uninstal it

---

### Post by sharks on 2008-05-27
just type sudo aptitude remove (package name)

---

### Post by Trail on 2008-05-27
You need root permitions for what you are trying to do (sudo).

---

### Post by vlad1975 on 2008-05-27
is this the right command?

sudo apt/remove/Planeshift

?????

---

### Post by sharks on 2008-05-27
sudo aptitude remove PlaneShift

---

### Post by billgoldberg on 2008-05-27
> **vlad1975 said:**
> is this the right command?

sudo apt/remove/Planeshift

?????

it should be

```
sudo aptitude remove planeshift
```

"sudo" means you need root access

"aptitude" is the package manager you are using

"remove" speaks for itself

and "planeshift" is the program you want to remove

---

### Post by Wilbefast on 2009-09-06
Ubuntu can be really patronising at times - you can't so much as pick your noise without it whining about permissions. I'm new to this so I'm still trying to figure out how to shut it up for good - until I do though, here's a quick fix:

```
sudo chown {username} {Planeshift directory} -R
```

In English this reads "as super-user (sudo) change the rights for the Planeshift directory (chown) and all files inside it (-R) so that it belongs to this user".

You can also put a group after the username ({username}:{group}) to allow a whole group access.



William

---

### Post by 3rdalbum on 2009-09-06
> **Wilbefast said:**
> Ubuntu can be really patronising at times - you can't so much as pick your noise without it whining about permissions. I'm new to this so I'm still trying to figure out how to shut it up for good

That's the wrong approach and the wrong attitude. You can't write to locations outside your home directory and /tmp unless you are root. This is the way things have been on Unix since its inception in the 1960s, it's the way Linux has always been since the 1990s, and it's the way Linux and Unix will always be. It's also the way that Apple and Microsoft operating systems are moving, too, because it's still the best way to run the system securely without stuffing things up.

If you don't like Ubuntu telling you permission denied, then work within the system and elevate to root whenever necessary. Stop thinking in the Windows mindset and start thinking in the Linux mindset, and you'll automatically put "sudo" before any modification outside your home directory.

Chmodding random directories can cause a heap of problems.

Oh, and the people advising to run "sudo apt-get remove planeshift", there is no package by that name in the Ubuntu repositories. Please check for this (sudo apt-cache show planeshift) before advising this way.

**To the original poster**: run:

```
sudo /usr/games/PlaneShift/uninstall
```

You need to be root in order to modify anything outside your home directory. The "sudo" before the command says "Run the rest of this command as root". The rest of the command is actually just the location of the uninstaller program.

In future it's easier to stick with the software repositories, or add third-party repositories or Debian packages. They are easier to add, remove, and otherwise manage.

---

