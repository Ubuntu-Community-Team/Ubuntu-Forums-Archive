---
title: "Six Tips to Help With Installation"
date: 2007-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by gantww on 2007-05-29
Hello all,
I've installed Ubuntu on several machines now (5 or 6 depending on how you count them). Anyway, I've found the following tips to be very helpful to me, so I thought I'd share them. If anyone has anything to add, please do so, as I'm still pretty much a noob (aka, your tip might help me out too).

1) Get your network connection up first. This will save you the grief of transferring stuff over to a thumb drive and then moving it to your machine afterward. The only exception to this rule is when you can't get a GUI to load at all. Then you probably need to handle that first.
2) Make sure you have nano installed second so that it if you totally kill the GUI on your machine, you can fix it without having to use VI. Unless you like VI.
3) Use a wired connection when setting up if one is available. Sometimes odd stuff happens when all you have is wireless.
4) Be careful with fstab and xorg.conf. Make incremental changes and save at each step onto removable media (probably a thumb drive). This is so that if you totally break everything that you can fix things with a copy command or at worst a wipe, reinstall, and then a copy. Be careful about doing too many changes at once, as it makes it harder to diagnose the problem.
5) Script off your package installation. Use synaptic to find all the stuff you want and create a shell script with the install commands in it (you can usually figure out the package name from synaptic or adept if you are using Kubuntu). I usually do it one per line, but I imagine that someone with actual skill in shell scripting has a better way. The lines will look like this:

apt-get install mysql-admin -y

So, it's basically you are calling apt-get (the package grabber), telling it to install, telling it what to install, and then passing a -y, which tells it to basically assume yes for any prompts you encounter. Save the file with however many lines you have, then right click on it and go to Properties->Permissions and check the box to make it executable. Now you can run it with the following command:
sudo ./[filename]

This is a major timesaver if you are installing on multiple machines, by the way. I also find it helpful to have this backed up, as it makes it easier to recover a machine quickly. I usually have one line for each package, but you can combine them. I just don't because it is easier on me this way. I also script off the adding of additional repositories, where needed and the installation of keys.
6) Get your hardware working before you mess with any of the software. This makes software installation easier.
7) As soon as you get a system you are satisfied with, back up your configs. If you are like me and tend to tinker with your machine a bit too much, this will cut back on the suffering a bit.

Hope this helps someone out.

---

