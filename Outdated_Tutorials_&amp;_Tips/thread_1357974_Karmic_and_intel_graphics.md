---
title: "Karmic and intel graphics"
date: 2009-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by rahilm on 2009-12-17
I know it has been posted many times. But i decided to start a new thread because the method is a little controversial because i have only one computer to test it and i can't resist the excitement to post it here before i wander to test it to other computers.

It seems karmic has some problems with intel graphics (That's MY experience + some of the computers i tested). People are having problems getting a resolution after upgrading (via a clean install) to karmic. I faced the same problem, but kind souls here helped me with it and i finally managed to get the resolution i needed. The method I followed was this one: [http://ubuntuforums.org/showthread.php?t=1302475](http://ubuntuforums.org/showthread.php?t=1302475)

But, as always, I wasn't satisfied. So , one day, that's today, half an hour ago. I suddenly caught with this idea. The idea is:

If karmic cannot detect your preferred graphic settings, use a linux that can.

One thing I still can't understand is how **PUPPY LINUX** has better hardware support than ubuntu. Ubuntu devs should look into the puppy linux code at least for graphic support.

**[COLOR=Red]1)GET PUPPY LINUX[/COLOR]**[COLOR=Red]:
[http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)
[COLOR=Black]I used puppy 4.21 for this one. This is not the latest release. but i had it.
Burn the iso to a cd and then boot into it.

[B][COLOR=Red]2)TRY YOUR LUCK:
[/COLOR][/B][COLOR=Red][COLOR=Black]Does puppy linux has the correct settings for you graphic driver? It has a script for running X at the beginning. It detected my video hardware driver flawlessly.

**[COLOR=Red]3)The xorg.conf file[/COLOR]**
Puppy linux should have generated an xorg.conf file. It is in /etc/X11.
[/COLOR][/COLOR][/COLOR][/COLOR]
[LIST=1]
[*]Mount the karmic partition
[*]Make a backup of you existing /etc/X11/xorg.conf file if any (mostly you won't have an xorg.conf file in karmic)
[*]Replace the xorg.conf file with that of puppy linux.
[*]restart and boot into karmic
[/LIST]
(Note: puppy 4.21 does not mount ext4 partitions so i had to copy it in another partition and then copy it in karmic then restart karmic)

It solved my graphic issues. By not only loading 1280x1024 as the default resolution but also by displaying an array of other resolutions.

If anyone tries the above method[COLOR=Red][COLOR=Black] please post you experience. If puppy doesn't work for you, well, atleast you have the idea/ Try in different linuxes or take a look at this HOWTO;
[http://ubuntuforums.org/showthread.php?t=1346125](http://ubuntuforums.org/showthread.php?t=1346125)
[/COLOR][/COLOR]

---

