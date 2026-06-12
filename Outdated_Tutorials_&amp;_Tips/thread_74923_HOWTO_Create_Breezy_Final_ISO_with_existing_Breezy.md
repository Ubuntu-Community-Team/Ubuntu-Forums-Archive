---
title: "HOWTO: Create Breezy Final ISO with existing Breezy Preview CD (Less download!!)"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by chanders on 2005-10-13
Step 1:Create a directory for the files and cd into it

	chanders@ubuntu:~$ mkdir Breezy
	chanders@ubuntu:~$ cd Breezy
	chanders@ubuntu:~/Breezy$

Step 2:Install jigdo-file

	chanders@ubuntu:~Breezy$ sudo apt-get install jigdo-file

Step 3:Get the necessary files for Breezy in jigdo to work

	chanders@ubuntu:~Breezy$ wget [http://releases.ubuntu.com/5.10/ubuntu-5.10-install-i386.jigdo](http://releases.ubuntu.com/5.10/ubuntu-5.10-install-i386.jigdo)
	chanders@ubuntu:~Breezy$ wget [http://releases.ubuntu.com/5.10/ubuntu-5.10-install-i386.template](http://releases.ubuntu.com/5.10/ubuntu-5.10-install-i386.template)

Step 4:Insert your Breezy Preview CD and make sure it is mounted (will be mounted as /media/cdrom0 usually)

Step 5:Run jigdo

	chanders@ubuntu:~Breezy$ jigdo-lite ubuntu-5.10-install-i386.jigdo

	when prompted for cd location type '/media/cdrom0' without the quotes, then press enter


Step 6:After it is finished, when prompted for mirror location enter 'http://us.archive.ubuntu.com/ubuntu/' without the quotes

Step 7:You will see all the extra files being downloaded.... be patient.....

Step 8:Make sure when it is all finished you see 'OK: Checksums match, image is good!' 

Step 9:You should now have a brand spanking new ISO to burn! Right click on the file in Nautilus -> Burn to disk

Step 10:Enjoy Breezy!

---

### Post by Manny C on 2005-10-13
Regarding Step 2: You should install jigdo-file and not jigdo-lite (this last package does not exist). 
```
 sudo apt-get install jigdo-file 
``` 

Regarding Step 3: I needed to download the .template file **(note that this is a Kubuntu release)** also
```
 wget http://82.211.81.153/kubuntu/5.10/kubuntu-5.10-install-i386.template
``` 

Regarding Step 5: After this process is completed, press enter to go to the next step.

Regarding Step 6: It is then, that you input the correct mirror details

 Otherwise, thanks for the HOWTO :)

---

### Post by chanders on 2005-10-13
Thanks Manny C....  HOWTO fixed :D

---

### Post by Manny C on 2005-10-13
Can confirm that this worked (at least to the point of having a cd with correct md5sums).

Yet to install. Waiting to get home and to my wireless network and WEP config.

---

### Post by khantozavri on 2005-10-13
Hi,

If I do normal upgrade isn't it goin to upgrade the distribution?

---

### Post by Manny C on 2005-10-13
Yep...but it won't be a clean install (ie. config files may not be updated and new breezy default settings may not be all right).

Procedure above, reduces d/l needed for a Breezy Badger ISO. Can confirm it worked perfectly now.

---

