---
title: "Gnome Classic (no effects) - 2 issues"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by Szymoninho on 2012-08-06
Hi, I'm using Ubuntu 12.04 with Gnome Classic (no effects) and there are 2 very simple issues that I can't deal with:

1) I cannot install global menu applet. I tried using Synaptic and here it says that this package is broken. When I'm trying to fix it I get back:

[I]E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies[/I]

Has anyone faced similar problems with the global menu?

2) this may sound funny but I have no idea how to adjust icon spacing in the top panel. Has anyone ever wondered how to do it?

I will appreciate any kind of help. Sorry if I didn't notice any threads that show solutions to these problems.

---

### Post by chamber on 2012-08-06
Try,

```
sudo apt-get clean && sudo apt-get update
```

---

### Post by Szymoninho on 2012-08-06
thanks for your suggestion, unfortunately I still have the same problem, *sudo apt-get update* wrote back (after many lines of web addresses):

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by chamber on 2012-08-06
Have you added in any specific PPA's outside of the standard?

You can look here to see about adding the keys for the PPA's that you are using:

[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

---

### Post by audiomick on 2012-08-06
> **chamber said:**
> Have you added in any specific PPA's outside of the standard?

I'd say yes. The error message lists a couple. My guess that it is not that the key is missing, but rather that the PPA is no longer there.

I would try and figure out what program or packages came from those PPA's and consider removing them. I would probably wait a week or so, just in case the PPA's are having temporary issues, and might reappear in time.

---

### Post by philinux on 2012-08-06
Try this.

```
sudo dpkg --configure -a
```

Post back the full error list if any.

---

### Post by Szymoninho on 2012-08-06
> **chamber said:**
> Have you added in any specific PPA's outside of the standard?

I have when I was experimenting a bit with my Ubuntu themes etc. Do you think removing all PPA's should fix the issue? I don't think I need any of them right now. I tried using the ppa-purge package but I'm having problems with deleting all PPA's at one time. Help doesn't mention such command although when I launch ppa-purge in Terminal it says:
> ppa-purge will reset all packages from a PPA to the standard
versions released for your distribution.

---

### Post by Szymoninho on 2012-08-06
> **philinux said:**
> Try this.

```
sudo dpkg --configure -a
```

Post back the full error list if any.

It doesn't mention any errors.

---

### Post by philinux on 2012-08-06
Ok.

Post back the full errors from this.

```
sudo apt-get install -f
```

---

### Post by Szymoninho on 2012-08-06
> **philinux said:**
> Ok.

Post back the full errors from this.

```
sudo apt-get install -f
```

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxcb-render-util0 libgnomenu0-2 libbonoboui2-common libbonoboui2-0
  libgnomecanvas2-0 libglobalmenu-gnome libgnomecanvas2-common
  gnome-globalmenu-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 318 not upgraded 
```
After I autoremoved them it says:
```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 318 not upgraded.

```
... but the bug still appears - I can't install the gnome-applet-globalmenu package (via synaptic)

---

### Post by audiomick on 2012-08-06
> **Szymoninho said:**
> I have when I was experimenting a bit with my Ubuntu themes etc. Do you think removing all PPA's should fix the issue?

First of all, don't let me distract you from following philinux's advice. He know rather a lot more about this stuff that me... ;)

As far as the PPA's go, if you are sure you are not using them anymore, then you can remove them, or at least uncheck them in the list of package sources in the software centre. I don't know if this will fix your issue, but it is definitely not a bad thing if the software centre / synaptic or whatever is not trying to find stuff in PPA's that are not to be found.

---

### Post by Szymoninho on 2012-08-06
> **audiomick said:**
> As far as the PPA's go, if you are sure you are not using them anymore, then you can remove them, or at least uncheck them in the list of package sources in the software centre.

I have a problem with removing PPA's (all at once) - I tried using the package called ppa-purge and I can't find a command in manual that should do the thing. Moreover when I look for "ppa" in Ubuntu Software Center and in Synaptic they don't show any of them. Could you show me an easy way to remove the PPA's?

---

### Post by Szymoninho on 2012-08-06
And I have one more question: does Compiz work under Gnome Classic (no effects)? I've quite recently switched from Unity and it does not work under Gnome for me by now...

---

### Post by philinux on 2012-08-07
Post up your sources list.

cat /etc/apt/sources.list

Don't forget to wrap it in code tags.

---

### Post by kansasnoob on 2012-08-07
> **philinux said:**
> Post up your sources list.

cat /etc/apt/sources.list

Don't forget to wrap it in code tags.

+1!

Perhaps also the output of:

```
ls /etc/apt/sources.list.d

```

---

### Post by kansasnoob on 2012-08-07
Once you get the software sources mess straightened out you may find answers to some of your "gnome classic" issues here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

