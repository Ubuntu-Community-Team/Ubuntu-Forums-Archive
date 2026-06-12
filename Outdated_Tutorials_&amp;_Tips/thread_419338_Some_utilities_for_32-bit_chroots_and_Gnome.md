---
title: "Some utilities for 32-bit chroots and Gnome"
date: 2007-04-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Tristan Schmelcher on 2007-04-22
I use a 32-bit chroot on a 64-bit system to run Firefox with flash, and I've developed some simple tools to make managing the chroot as painless as possible, so I thought I'd share them. (See [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575) for details on setting up such a chroot.)

After I set up my chroot, I found two problems with it. First, because Firefox runs in the chroot, it can't launch any programs to read downloaded files unless you install those programs in the chroot too, which would be wasteful and tedious. Second, lots of data-only packages (e.g., fonts, documentation) are the same in both the chroot and the main system, so that data ends up being duplicated.

To solve the first problem, I wrote a simple program in C that lets the chroot run programs outside of itself, plus a script to synchronize the list of applications that are used to open downloaded files. To use, assuming that you've downloaded all the attached files to (say) ~/tmp and removed the .txt extensions, do this:

```
dchroot -d -q
sudo apt-get install gcc libc6-dev
gcc -o unchroot ~/tmp/unchroot.c
sudo chown root:root unchroot
sudo chmod +s unchroot
sudo mv unchroot /usr/local/bin/
```

That installs the program that allows your 32-bit chroot to run all of your 64-bit programs. (Note: you can remove gcc and libc6-dev afterwards.) As an example, if you want to let the Firefox in your 32-bit chroot run Evince (a.k.a. the Gnome document viewer) in order to view PDFs that you download, then you can create a symlink for it while inside the chroot, like this:

```
ln -s unchroot /usr/local/bin/evince
```

Running "evince FILE" inside the chroot will now work. First it will run unchroot, which will escape to the real root, and from there it will run your 64-bit Evince. Provided that FILE is in a directory that is visible in both environments (e.g., /tmp or /home, assuming you're following the above-mentioned guide), then your document will open as normal. If you also copy the /usr/share/applications data for Evince into your chroot, then Firefox will know to run it when it downloads a PDF. However, doing all of this for everything that you want to run from Firefox would be a pain, so I wrote a script to set it up for every app on your system!

First edit the syncApps.pl file and change the "/var/chroot/testing-ia32" path to be the location of your chroot. Then run it (from outside the chroot):

```
sudo ~/tmp/syncApps.pl
```

This will read the configuration data in /usr/share/applications, duplicate it in your chroot, and create symlinks as above. Some of the .desktop files in /usr/share/applications outside of your chroot may be changed by this process in order to make them compatible with the chroot, but back-ups will be made automatically. (However, any files in /usr/share/applications _inside_ your chroot might be _overwritten_.) Obviously, I take absolutely no responsibility for any damages that may be incurred from you running this. But I haven't had it destroy any of _my_ data yet, so it's at least somewhat safe. :)

After running the above, all of the registered applications in your main 64-bit system will also be registered and executable inside your chroot. Provided that you have firefox-gnome-support installed in your chroot, that means that Firefox will now be able to run all of your handler applications properly.

With regard to the second problem that I mentioned of data packages being duplicated, the attached "install-everywhere.sh" is meant to solve it. You give it a list of APT packages on the command line. It will install them in both your main system and your chroot (if they aren't installed already) and then check if all their files are the same. If so, it will combine them with hard-links to cut disk usage in half. For example, I have a bunch of Japanese fonts installed on my system and I want to be able to use them in Firefox, so I would run the following:

```
sudo ~/tmp/install-everywhere.sh ttf-sazanami-mincho ttf-sazanami-gothic ttf-kochi-mincho ttf-kochi-gothic
```

Since those four packages are all just TrueType fonts whose data is the same on every platform, the install-everywhere script will combine their data after download to save on space. (Note that you don't need to do this specifically for fonts if you are using the above guide, because it sets up /usr/share/fonts to be the same in both environments.)

Lastly, I have included a script called run-ia32-dchroot, which is the version of do_dchroot that I use to launch the 32-bit programs in my chroot from outside. (See the above-mentioned guide for info about do_dchroot.) run-ia32-dchroot is based on code that I found from someone else which has the advantage that it properly escapes any special characters in the command line arguments.

---

### Post by Tristan Schmelcher on 2007-05-07
I just recently made another simple tool that you will need if you switch between different networks often. Download it, remove the .txt extension, make it executable (i.e., run "chmod a+x chroot-resolv-sync-daemon.sh") and install it to, say, /usr/local/sbin. Then launch it in in the background from your /etc/rc.local (i.e., add "chroot-resolv-sync-daemon.sh &" to that file) and reboot. You will need the inotify-tools package to run it.

(For those that care about the gory details, this program will make sure that whenever your main system joins a network with a different gateway, the chroot will be updated to use the new one. Without this, you'd have to manually run a different command every time you switched networks, or else Firefox/Iceweasel wouldn't be able to get to the Internet.)

---

### Post by Tristan Schmelcher on 2007-05-07
Incidentally, the "chmod a+x ..." step for the script in my last post should actually be done for the three other ones from my original post, too, but I forgot that when I originally wrote it. Also, in the original post I mentioned how you have to edit syncApps.pl and put in your chroot's real path, but in fact you also have to do that for install-everywhere.sh and for the chroot-resolv-sync-daemon.sh that I just posted. The "ia32" in the last line of run-ia32-dchroot also must be changed to the actual name of your chroot in /etc/dchroot.conf.

---

### Post by p1977p on 2007-07-14
how can i run pdnsd for my 32 bit chroot? thenetworking is very slow without it? (P.S. I've been running it comfortably in 64 bit)

(Running 64 bit Xubuntu on AMD 64 laptop dual boot with XP)

---

