---
title: "Upgrading from 10.10 to 11.04 then 12.04"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by Grace_Palazzolo on 2013-08-15
Hello, I am trying to upgrade from 10.10 (maverick) to 11.04 and then 12.04. I do not have the capability to burn a CD on my very very old computer, and it does not boot from a USB stick so I have to to it this way.

The problem is that the upgrade to 11.04 failed. On the advice of the [URL="https://help.ubuntu.com/community/EOLUpgrades#Requirements"]EOLUpgrade page
[/URL]I added some lines to /etc/apt/sources.list and it got the update manager to begin the process when I used "sudo update manager -d" at the command prompt. However, after I clicked the "Upgrade" button, the upgrade to 11.04 failed. I got as far as a window labeled "Distibution Upgrade" and it succeeded with "Preparing to upgrade" but when it got to the next step, "Setting new software channels", an error popped up: 

Error during update
A problem occurred during the update. This is usually some sort of network problem.
W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Also, Here is what I got in my terminal window:
$ sudo update-manager -d
authenticate 'natty.tar.gz' against 'natty.tar.gz.gpg' 
extracting 'natty.tar.gz'
WARNING: Failed to read mirror file
$ 

I think the problem is the sources.list maybe? The files are no longer at us.archive.ubuntu.com, so do I need to make more changes to sources.list?

---

### Post by oldos2er on 2013-08-15
You'd need to go from 10.10 -> 11.04 -> 11.10 -> 12.04. That's a lot of upgrading and a large potential for problems to occur. 

The repositories you're looking for are old-releases.ubuntu.com; open the sources.list in your favorite text editor, do a search and replace of us.archive.ubuntu.com to old-releases.ubuntu.com

If possible I'd suggest you do a clean install of 12.04.02, you'd save yourself a lot of grief.

---

### Post by fantab on 2013-08-15
Yes that is lot of upgrading, there WILL be issues. Do a FRESH 12.04.2 install.

---

### Post by deadflowr on 2013-08-15
Your machine sounds very old and quite possibly it will have a hard time running 12.04.

That said changing the sources.list is quite simple.
Here's a command I've used several times and works well
```
sudo sed -i -e 's/[COLOR=#b22222]us.[/COLOR]archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
```

I changed the line for you(added the us. in red) otherwise without it the new line would read us.old-release.ubuntu.com, which doesn't exist.

Personally, though, I would look into finding a third party to burn a lighter distro as Ubuntu is much fatter on 12.04 than 10.10.
And a machine that can't burn or boot from USB might be too old.

---

### Post by philinux on 2013-08-15
Grace.

When you say old what are the specs of this machine.

---

