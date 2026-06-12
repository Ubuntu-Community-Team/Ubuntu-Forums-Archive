---
title: "Failed To Fetch upgrading Natty as guest OS on Windows XP using VirtualBox 4.1.2"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by el_garicimo on 2011-09-29
Hey folks,

Complete n00b here, trying to run Ubuntu 11.04 as a guest OS on my EeePC netbook using Virtual Box.  I'm doing this so I can start to learn Rails development, so any resources on that too would be great.

Main problem:

After a clean install of Ubuntu 11.04 (Natty) on Virtual Box, and the update manager successfully updating everything, when I open the terminal and try to update using 

sudo apt-get update

I get lots of failed to fetch errors, as shown below.

*********************************************

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources)  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Index](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.

*****************************************************************


I'm definitely connected to the internet, and I don't know why I'm failing to fetch things from what I've been told is one of the main US repositories(is that the right lingo?) for Ubuntu stuff.


Second weird problem:

Can't run unity.  I enabled the 3d acceleration, put 64 MB of Video memory on, and of my netbook's 2 GB of RAM of I've assigned 1 GB to the my Virtual Machine.However, first time booting after the install still got a message saying something like "Seems you don't have the required hardware to run Unity.  Please select GNOME at the log in."  The netbook has 1.6GHZ and plenty of hard drive space (140 GB).  I guess it's not that big a deal, and I don't even know how I'd change that even if my hardware requirements magically started to be good enough, but it's still annoying that I don't know why it doesn't work, especially as i heard unity was specifically designed for netbooks.

Any help would be much appreciated!

---

### Post by wildmanne39 on 2011-09-30
Hi, the ones that have 404 by then either the server is down or the have been removed from it.

My guess is since the other ones say partial upgrade that the server is down for a little while you can try another server or wait for that one.

Also it is a bad idea to do a partial upgrade it usually breaks synaptic and update manager, partial upgrade usually means they are working on getting the packages updated give them some time then try again.

If you have already managed to get a partial upgrade we may have to fix it so you can install packages again.

3d issue make sure you have turned 3d support on in virtualbox and install guest additions.
Thank you

---

### Post by Old_Grey_Wolf on 2011-09-30
> **el_garicimo said:**
> Second weird problem:

Can't run unity.  I enabled the 3d acceleration, put 64 MB of Video memory on, and of my netbook's 2 GB of RAM of I've assigned 1 GB to the my Virtual Machine.However, first time booting after the install still got a message saying something like "Seems you don't have the required hardware to run Unity.  

Did you install the Virtualbox Extension Pack? Did you install the Virtualbox Guest Additions? Those should solve the hardware problem. You will need to download them from the Virtualbox website. The instructions on the Virtualbox website don't mention the Guest Additions on the first page, you have to search to find out about it.

In Ubuntu, try using a different update server. If you have problems connecting to a server, the server is slow, you cannot find a package you expect to find on the currently-selected server, or simply want to find a faster server, open the Update Manager and click on the "Download from" window. Select "Other", then "Best Server", and click "Select Server".

To fix the partial update, copy and paste these commands one at a time in the terminal:
```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get clean all

sudo apt-get update
```

---

### Post by el_garicimo on 2011-10-02
Thanks wildman, is there any way to check when servers are down?  And how long are the usually down for? I've been sort of trying to do this a couple weeks now. Thanks for the tip though on how partial upgrades are pretty much always a bad idea.

---

### Post by el_garicimo on 2011-10-02
thanks old gray wolf, didn't know I had to do those things!  I'll give 'em a try

---

### Post by wildmanne39 on 2011-10-02
Hi, the server should be back up by now, so I believe the ubuntu archive that has 404 by it is just no longer there.

You can open synaptic click on settings repositories,at the top of the window that opens click on other software and uncheck the ppa that says ubuntu archive, then reload synaptic and close it.

Then do what Old_Gray_Wolf said to clean up the partial list issue. The only time that list is present is after a partial upgrade and it prevents any downloads from working.
Thank you

---

### Post by Old_Grey_Wolf on 2011-10-02
> **wildmanne39 said:**
> 
You can open synaptic click on settings repositories,at the top of the window that opens click on other software and uncheck the ppa that says ubuntu archive, then reload synaptic and close it.

I didn't think http ://us.archive.ubuntu.com/ubuntu/...source/Sources was a PPA. Funny, the repo shows it was updated 1 Oct, so it could have been down or had other problems.

---

### Post by wildmanne39 on 2011-10-02
Hi, I believe you are correct, but I believe the method I suggested is how I removed my archive when it quit working, I did not want to tell him to manually edit his source list if I did not have too.
Thank you

---

### Post by Old_Grey_Wolf on 2011-10-02
> **wildmanne39 said:**
> Hi, I believe you are correct, but I believe the method I suggested is how I removed my archive when it quit working, I did not want to tell him to manually edit his source list if I did not have too.
Thank you

Yes, what you suggest will work; however, when they look for "the ppa that says ubuntu archive" they may get confused when they can't find a PPA. I don't think they need the source code anyway. The .../source/Sources should be a .bz2 or .gz; therefore, the reason it doesn't find it.

---

