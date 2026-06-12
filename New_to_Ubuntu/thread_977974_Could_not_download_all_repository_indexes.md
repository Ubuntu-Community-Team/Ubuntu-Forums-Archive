---
title: "Could not download all repository indexes"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by graemebothwell on 2008-11-10
Hi,

I'm new to Ubuntu, Linux, and these forums, but I would be very grateful if someone wiser than I, were able to help me sort this problem out. My system has not updated for 10 days now...


The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Pro-reason on 2008-11-10
Open up your Software Sources.  You can do this from the menu, or type “gksu software-properties-gtk” into a terminal.

Use the resulting dialogue box to remove the CD-ROM from the list of sources.

Then install the package “medibuntu-keyring”.  You can do this in Synaptic, or by typing this into a terminal: “sudo apt-get install medibuntu-keyring”.

---

### Post by graemebothwell on 2008-11-10
Thank you Pro-reason for your help mate, but now it's coming up with the following message, after doing the processes you explained previously. 

 

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Pro-reason on 2008-11-10
It seems you didn't manage to remove the CD-ROM from the list.  Let's do it manually, then.

Put this into a terminal:

```

gksu gedit /etc/apt/sources.list

```

Edit the file to get rid of the lines mentioning the CD-ROM.

Save and close.

After making any change to your list of sources (either manually or via the dialogue box that we used before) you need to reload the list.  Do this by clicking on “Reload” in Synaptic, or by doing this in a terminal:

```

sudo apt-get update

```

---

### Post by graemebothwell on 2008-11-11
Cheers mate, worked a dream through the terminal. Many thanks.:)

---

### Post by billytalent on 2009-01-09
Just wanted to say a quick thank you for this, i had the same problem and your last post worked for me, nice job mate ;)

---

### Post by jeromer43 on 2009-02-05
I have this same problem, but with a bit of a twist.

I get the same message.  Could not download all repository indexes and it list two repository's

[http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia)
and
[http://archive.ubuntu.com/ubuntu/dist/hardy/restricted/binary-lpia](http://archive.ubuntu.com/ubuntu/dist/hardy/restricted/binary-lpia)

When I try to remove those repositorys from the  sources.list   They do not appear on the list at all.   

What's up?   How do I stop the update manager from looking for them, if they are not on the sources.list in the first place.

Dell Mini9 w Hardy

---

### Post by Yannick Le Saint kyncani on 2009-02-05
> **jeromer43 said:**
> When I try to remove those repositorys from the  sources.list   They do not appear on the list at all.

Hi jeromer43, there is also a /etc/apt/sources.list.d/ directory, any file in it will be included in the repos list I think.

The two repos you're looking for may be somewhere there.

---

### Post by jeromer43 on 2009-02-05
Thanks for that.  Did not find these repositories on any of the other list, but I do now note that if I change sources I get a slightly different response.  Also if I add another source, like "universe" the message returns 3 repositories as 404.     

They all have to do with the binary-lpia packages.   

Could my problem be that the binary-lpia packages are actually down or have been removed?

---

