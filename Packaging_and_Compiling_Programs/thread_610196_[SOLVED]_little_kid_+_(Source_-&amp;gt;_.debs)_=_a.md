---
title: "[SOLVED] little kid + (Source -&amp;gt; .debs) = apt is happy (???)"
date: 2007-11-11
forum: Packaging and Compiling Programs
---

### Post by 1337455 10534 on 2007-11-11
OK, I know there is a tutorial for this somewhere, but, I couldn't find anything good (0 out of 6 promising hits). I need to know how to take source, making it into a working deb, and feed it to apt (via GDebi I believe) so that this doesn't happen:
```

family@Purple-Blanket:~$ sudo apt-get install pidgin
[sudo] password for family:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  pidgin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 603kB of archives.
After unpacking 1761kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy/main pidgin 1:2.2.1-1ubuntu4 [603kB]
Fetched 603kB in 2s (235kB/s)  
Selecting previously deselected package pidgin.
(Reading database ... 146246 files and directories currently installed.)
Unpacking pidgin (from .../pidgin_1%3a2.2.1-1ubuntu4_i386.deb) ...
Setting up pidgin (1:2.2.1-1ubuntu4) ...

family@Purple-Blanket:~$ sudo apt-get purge pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pidgin*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1761kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146279 files and directories currently installed.)
Removing pidgin ...
Purging configuration files for pidgin ...
family@Purple-Blanket:~$ pidgin -help
pidgin: invalid option -- e
Pidgin 2.2.2. Try `pidgin -h' for more information.
family@Purple-Blanket:~$ 

```

As you can see, Pidgin is still installed and working great but apt has no clue. So how do you make debs? I am comfortable with compiling so I dont need to be babied, but code examples would be extremely helpful.

Another thing, close attention to the install line up there shows apt getting 2.2.1, not 2.2.2.

---

### Post by 1337455 10534 on 2007-11-11
bump

---

### Post by dfreer on 2007-11-12
Well, one solution (not very elegant) is to install the "checkinstall" package. Then, follow your standard compiling steps like so:
```

./configure
make

```
When you get here, instead of doing a "sudo make install", do a "sudo checkinstall". It will ask you various questions about the package name/version number/etc (you'll need to practice with it a lot!), and then make a .deb file for you.
Now, this will probably work for you, but it may not work for other users (which is part of why it isn't very elegant).

The second method of making debian packages is one I use, although it isn't the real way to make a debian package, as long as you do it right it should work for all users. It probably won't stand up if you wanted to submit your package to the official repositories.
Here's the link that I used when I first started making my packages:
[http://linuxdevices.com/articles/AT8047723203.html](http://linuxdevices.com/articles/AT8047723203.html)

There's the official way also, of which I'm not too familiar. Involves making several different files for the repository to use, not just the .deb. Someone with more information about that than me will have to help you out there.

BTW, from the terminal output posted from above, it appears you:
[list]
[*] Installed pidgin from a repository
[*] Removed and purged the pidgin you installed from the repository
[*] found out that pidgin wasn't removed, as you can still get the version number from it.
[/list]
Just making an educated guess, it sounds like you at some point compiled and installed pidgin manually. Apt-get will not remove a manually compiled program, so basically you had two versions installed and only removed the apt-get version.
To remove the other version, you'll probably need to enter your pidgin source directory and run this command (I'm pretty sure this is the right one, I'm not at my linux box right now):
```
sudo make uninstall
```

EDIT: BTW, it often takes 24 or more hours before you get a response to a new thread. No need to bump so early :D

---

### Post by 1337455 10534 on 2007-11-12
Thank-you, and you nailed the situation.
[I'll keep teh bumpe advice in mind.]

---

