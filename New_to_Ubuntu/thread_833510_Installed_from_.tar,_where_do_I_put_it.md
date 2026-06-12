---
title: "Installed from .tar, where do I put it?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-06-18
Yesterday I installed the new version of Sauerbraten from its website (it just came out 2 days ago so it wasn't in the repos).  Originally I extracted it to the desktop, which was the default location.  I then moved it to /bin since I didn't want it on my desktop.

Right now, in order to run it, I need to do this:
```

cd /bin/sauerbraten
./sauerbraten_unix

```

I actually seem to have to be in the sauerbraten directory to run it; I can't do:
```

 /bin/sauerbraten/sauerbraten_unix

```

If I try that, I get this:
```

Your platform does not have a pre-compiled Sauerbraten client.
Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed.
2) Change directory to src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.

```

I would try that, but apparently I don't have an src directory.

So I have a couple of questions:

1) I would like to be able to run it by just typing 'sauerbraten' in the command line.  I tried moving the whole archive to /bin, but it didn't change anything.  How do I set up a PATH name so that I can just type 'sauerbraten' and have it start?  Do I have to move the file somewhere else?

2) I would also like a menu option for it to be in Applications > Games.  How do I set that up?

3) I still have the .tar file sitting on my desktop.  Now that I've extracted it, can I delete that file?

Thanks.

---

### Post by cariboo on 2008-06-18
For programs you install yourself they should always be in /usr/local/bin.

> /bin - In contrast to /sbin, the bin directory contains several useful
commands that are used by both the system administrator as well as
non-privileged users. This directory usually contains the shells like
bash, csh etc. as well as much used commands like cp, mv, rm, cat, ls.
There also is /usr/bin, which contains other user binaries. These binaries
on the other hand are not essential for the user. The binaries in /bin
however, a user cannot do without.

I would suggest you move sauerbraten to /usr/local/bin then change the ownership to root and permissions to 755.

By the way /src is located in /.

If  sauerbraten is located in /usr/loca/bin you will be able to run it from the command line

You can add to the games menu by right clicking on Applications and click Edit Menus, then select Games and click Add.

You can delete the tar file after your done with it.


JIm

---

### Post by N.N. on 2008-06-18
There's probably no harm in doing it, but as a rule you shouldn't move directories to the /bin directory, as it is reserved for essential user programs, such as filesystem commands. Normally that directory doesn't receive modifications after installation unless one of the essential programs contained therein are upgraded.

Now an attempt to answer your questions:

1) Programs, documentation, and so on normally go in the /usr directory, hence that would also be a good place to store your sauerbraten directory. You could move the sauerbraten directory to /usr/local/games, for instance. Making the game launch when you type 'sauerbraten' in the terminal, then, should be achievable by pointing to the executable sauerbraten file from a place that is included in the shell's PATH environment variable, such as the /usr/bin directory. This can be done by means of a symbolic link: ```
sudo ln -si /usr/local/games/sauerbraten/sauerbraten_unix /usr/bin/sauerbraten
```

2) Right-click on a top-level menu and choose *Edit Menus*. In the left-hand pane of the menu editor that then shows up, select the *Games* submenu. Finally, choose *New Item* and fill in *Name*, *Comment*, *Command* (assuming that you've succeeded in getting the game to run when you type 'sauerbraten' in the terminal, simply fill in 'sauerbraten' in this field), and *Icon*.

3) Yes, you can safely delete that file.

---

### Post by gr4nf on 2008-06-19
Sauerbraten is available over aptitude, which is probably way easier. Just use:
```

sudo apt-get install sauerbraten

```

---

