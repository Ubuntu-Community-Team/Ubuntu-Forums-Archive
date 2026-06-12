---
title: "[SOLVED] Update Manager: The list of changes is not available"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by BassKozz on 2008-11-06
Ever since I've upgraded to Intrepid when ever I see updates in my Update manager the changes read "The list of changes is not available" :(

I am a big fan of reviewing the changes before I upgrade the packages, how come there unavailable?

Also is there a place I can go to look at the changes for the kernel,  i.e. linux-headers-2.6.27-7 ?

---

### Post by oldsoundguy on 2008-11-06
Hate to ask the obvious, but are all of your repositories enabled? (the proper ones for intrepid?)

---

### Post by BassKozz on 2008-11-06
> **oldsoundguy said:**
> Hate to ask the obvious, but are all of your repositories enabled? (the proper ones for intrepid?)

Think So:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/SoftwareSources-updates.png[/IMG][IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/SoftwareSources-UbuntuSoftware.png[/IMG][IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/SoftwareSources-ThirdParty.png[/IMG][IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/SoftwareSources-Authentication.png[/IMG]

---

### Post by philinux on 2008-11-06
Those look ok. Although I have partner enabled and backports.
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Sometimes the message changes not available does happen but there is also a link you can click to see the changes.

---

### Post by BassKozz on 2008-11-06
Phil,

I checked those but I still can't see anything listed in Changes:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/UpdateManager.png[/IMG]

---

### Post by philinux on 2008-11-06
Whats under the description tab?

---

### Post by BassKozz on 2008-11-06
The description is fine, it displays as it should:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/UpdateManager-2.png[/IMG]
It's only the changes that's not displaying anything, and this happens for all the upgrade packages (not just one one I took screenshots of).
:confused:

---

### Post by philinux on 2008-11-06
I think it could be caused by the fact you upgraded. A bug in effect. I would use synaptic to completely remove update-manager then reinstall it.

---

### Post by philinux on 2008-11-06
If that doesn't work I'd raise a bug at launchpad.
Also read this you're not alone.
[http://ge.ubuntuforums.com/showthread.php?p=6117851](http://ge.ubuntuforums.com/showthread.php?p=6117851)

---

### Post by Andre-D on 2008-11-06
you are not alone - same here.. did you register the bug ?

---

### Post by jtoppine on 2008-11-07
Same problem here on my fresh install (tried to just upgrade, but it seriously ****** up the system).

I just have the feeling it might have something to do with mirrors updating slowly. The changeslogs seem to become available if I do not update immediately and wait a day or two. I might be wrong though.

---

### Post by Fazer2 on 2008-11-07
Same problem here, upgraded from 8.04 to 8.10.

---

### Post by antiloop on 2008-11-07
Same problem. Running a fresh Wubi install.

---

### Post by louieb on 2008-11-07
:confused:It's normal.  I've seen that since Breezy (v5.10)  Sometimes security updates hit the repositories before the reason why get added. You can wait till the  the change verbiage  gets added.  

As long as your using** only** the official Ubuntu repositories, I feel safe in saying theres nothing in the update that will maliciously harm your system.

---

### Post by BassKozz on 2008-11-07
> **Andre-D said:**
> you are not alone - same here.. did you register the bug ?

I seems this problem has already been reported:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/40058](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/40058)
And it looks like they are working on a fix.

---

### Post by Fazer2 on 2008-11-07
I found the solution to this problem. I installed proposed updates for update-manager and update-manager-core. The changelogs are visible again.

---

### Post by kyozo on 2008-11-08
> **Fazer2 said:**
> I found the solution to this problem. I installed proposed updates for update-manager and update-manager-core. The changelogs are visible again.
I also just updated the update-manager and the update-manager-core, and now I see the changes too.

Thank you Fazer2.

/Kyozo

---

### Post by geirha on 2008-11-08
Excellent I was also missing the changelogs in Intrepid. I don't fancy enabling the proposed repository just for upgrading update-manager though, so I just downloaded the two needed files and installed them manually.

```

cd /tmp

# Download for 32-bit install
wget http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager{-core_0.93.34_i386.deb,_0.93.34_all.deb}

# Download for 64-bit install
wget http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager{-core_0.93.34_amd64.deb,_0.93.34_all.deb}

# Install
sudo dpkg -i update-manager*.deb && rm update-manager*.deb

```

And the changelogs are back :)

---

### Post by frenkel on 2008-11-09
> **geirha said:**
> Excellent I was also missing the changelogs in Intrepid. I don't fancy enabling the proposed repository just for upgrading update-manager though, so I just downloaded the two needed files and installed them manually.

```

cd /tmp

# Download for 32-bit install
wget http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager{-core_0.93.34_i386.deb,_0.93.34_all.deb}

# Download for 64-bit install
wget http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager{-core_0.93.34_amd64.deb,_0.93.34_all.deb}

# Install
sudo dpkg -i update-manager*.deb && rm update-manager*.deb

```

And the changelogs are back :)

Thanks man :)

---

### Post by jcrow on 2008-11-10
I tried to reinstall the update manager via synaptic, but it prompted me to insert the ubuntu disc. I have all of the repositories enabled. I reinstalled the update manager using the command line as shown above. I'll have to see if it works. I upgraded from 8.04 with the alternate CD.

---

### Post by geirha on 2008-11-10
> **jcrow said:**
> I tried to reinstall the update manager via synaptic, but it prompted me to insert the ubuntu disc. I have all of the repositories enabled. I reinstalled the update manager using the command line as shown above. I'll have to see if it works. I upgraded from 8.04 with the alternate CD.

Go to System -> Administration -> Software Sources and deselect the ubuntu CD as a repository. After that it shouldn't prompt you for the cd when installing applications.

---

