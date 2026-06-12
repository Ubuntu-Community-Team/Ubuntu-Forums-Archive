---
title: "kernel panic - not syncing:VFS:"
date: 2008-04-15
forum: Philippine Team
---

### Post by antemon on 2008-04-15
spamming at a different section, baka na encounter nyo na to guys :(

=========================

my ubuntu loading screen, the one before log-in, wasn't showing after getting XFCE and KDE on ubuntu Gutsy.
Did'nt really notice it till yesterday since I often just hit the switch and walk away to do something else then come back.

searching the forums, found this:
[http://ubuntuforums.org/showthread.php?t=699492](http://ubuntuforums.org/showthread.php?t=699492)
Did what y-lee said

> **y-lee said:**
> You may have a misconfigured resolution for usplash. This seems to happen sometimes on fresh Gutsy installs. To fix it, edit **/etc/usplash.conf **as root and set the **xres** and **yres** lines to the horizontal and vertical resolutions that your screen supports.

Then do

```
sudo update-usplash-theme usplash-theme-ubuntu
```

If you don't know how to edit a file as root:


```
sudo gedit
```

Open the file make the changes and save the file.

Post back and let us know if that works or not.

and sure enough, it was set at a resolution my old CRT couldn't handle. changed it to 1024*768. Restarted to see if it worked, but coughed up an error. selected recovery mode, same error. here are the last few lines:

```


Using IPI No-shortcut mode
 Magic Number 4:857:821  [COLOR="Red"]<- this cracked me up...[/COLOR]
 hash matches device ptyt1
input: AT Translated set 2 keyboard as /class/input/input1
VFS: Cannot open root device "UUID=69a8923-ef49-4968-878a-c543ff437cf3" or unknown-block (0,0)
please append a correct "root=" boot option; here are the available partitions:
[COLOR="Red"]>> nothing stated or didn't even want my input... :( <<[/COLOR]
kernel panic - not syncing:VFS:unable to mount root fs on unknown-block (0,0)


```


help?

---

