---
title: "gksudo nautilus segfault error"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by jtclicker on 2008-06-02
I can't launch nautilus as root. When I check dmesg I get the following error


[ 103.417975] nautilus[5934]: segfault at 00000000 eip 00000000 esp b63b725c error 4

This happened after a system upgrade. Any ideas how to fix it?

---

### Post by iaculallad on 2008-06-02
What about if we are to re-install nautilus?

```
sudo apt-get install nautilus -y
```

---

### Post by jtclicker on 2008-06-02
Thanks i tried that in my efforts to fix this but got this 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
nautilus is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
julian@julian-desktop:~$ 

I was wondering what would happen if I first 'purge' nautilus and then reinstall, but one of the packages to be deleted would be the ubuntu desktop and don't like the sound of doing that!

Thanks for the suggestion!

---

### Post by iaculallad on 2008-06-02
(Strange..) It's worth giving it a try, uninstall (then reinstall) both nautilus and gnome-desktop to trace the culprit.

---

### Post by jtclicker on 2008-06-02
Ok, did sudo apt-get purge nautilus followed by sudo apt-get install nautilus.

Then did gksudo nautilus and got nothing. Dmesg now shows two errors
[ 2673.733636] nautilus[6652]: segfault at 00000000 eip 00000000 esp b63b025c error 4
[ 5147.124466] nautilus[6835]: segfault at 00000000 eip 00000000 esp b630b25c error 4

---

### Post by iaculallad on 2008-06-02
I don't know if this will work your case :( , like I said, it's worth giving it a try:

Did you try uninstalling ubuntu-desktop? (ubuntu-desktop->nautilus)
Re-install ubuntu-desktop->Nautilus.

---

### Post by jtclicker on 2008-06-02
When I tried that, after gksudo I got

julian@julian-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

but no nautilus, and then dmesg shows...

[ 2673.733636] nautilus[6652]: segfault at 00000000 eip 00000000 esp b63b025c error 4
[ 5147.124466] nautilus[6835]: segfault at 00000000 eip 00000000 esp b630b25c error 4
[ 6044.124737] nautilus[6978]: segfault at 00000000 eip 00000000 esp b4eca25c error 4

---

### Post by ryanhaigh on 2008-06-02
Not sure whats causing your issue but while you are trying to diagnose it here is a possible workaround:

[LIST=1]
[*]Install [nautilus-actions]("apt://nautilus-actions")
[*]Open System>Preferences>Nautilus Actions Configuration
[*]Enter the details as shown in the attached image
[*]Restart nautilus by either logging out and back in or press alt-f2 and enter nautilus -q to quit nautilus then go to places>home to restart nautilus.
[*]You should now have the option to open as administrator when right clicking on a file.
[/LIST]

If gksudo nautilus isn't working then this may not work either (depends what you are trying to open). I would try removing any configuration information for the root user, for example I have a .nautilus folder in my root users home directory (/root), perhaps the new nautilus is having issues with specific configuration options. There are no guarantees that this is the only location where configuration info is stored though, you will have to go through /root and see what you think is relevant.

---

### Post by iaculallad on 2008-06-02
What version of Nautilus are you currently using:

Why not try to download Nautilus [v2.22.23]("http://www.icewalkers.com/download/Nautilus/1191/dls/") stable version and manually [compile]("http://ubuntuforums.org/showthread.php?t=654652") it.

---

### Post by jtclicker on 2008-06-02
Ok Thanks, the nautilus actions works which will holdme for a while. As this problem came up after a system upgrade I feel maybe a later release will sort itself out????

As regards the manual compile, I'm already using the latest nautilus release, is there any benefit to manually compiling it?

---

### Post by jtclicker on 2008-06-02
is there anyway of getting to the /root directory in a graphical interface now that my root nautilus is dead?

---

### Post by ryanhaigh on 2008-06-02
> **jtclicker said:**
> is there anyway of getting to the /root directory in a graphical interface now that my root nautilus is dead?


You could install any one of the many alternate file managers available from the repos such as thunar or [pcmanfm](apt://pcmanfm) and then start it using alt-f2 > gksudo pcmanfm.

---

### Post by mnavasuk on 2008-09-08
I have the same problem as jtclicker. Since your bug report was closed due to lack of debug info, I've had to create a new report (launchpad using Apport). I can use PCMan, but I can't use it to make a folder/directory shared. Or is there a way? sudo nautilus isn't working. I get the same type of segfault error.
Any ideas?

---

### Post by ryanhaigh on 2008-09-08
Its a workaround but at least on my Gutsy system there is something like shared folders in system>admin, you should be able to share your directories from there.

---

