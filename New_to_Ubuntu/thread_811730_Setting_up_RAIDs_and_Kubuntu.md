---
title: "Setting up RAIDs and Kubuntu"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by pancakelizard on 2008-05-29
Currently, I am in the process of backing up all data on my computer and will be ghosting my system drive in case for some reason I can't get Kubuntu to install correctly with what I want to do.

Afterwards, I am (wanting to anyway) create a RAID 1 with two 160 gig drives and then RAID 5 my 4 750 gig drives. It will be my main computer but also the file/print server within my house.

For RAID 1, I purchased this controller:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815158036](http://www.newegg.com/Product/Product.aspx?Item=N82E16815158036)

For RAID 5, my motherboard has a built in RAID 1/0/5 controller on it:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128034](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128034)

Having never setup a RAID with use in Linux before I just have some questions.

1. It seems the install guide for the software/fakeraid is about 14 pages! Well the one I printed out. Is there an easier way or is this the only current method?

2. Every guide I have seen says to install mdadm before setting up the RAID or installing the OS but how is this done if the RAID has not been configured or formatted? Last time I checked (atleast with windows) the RAID had to be setup before installing the OS.

3. Can this be done with the Kubuntu 8.04 with KDE 4 setup CD or will I need another CD to perform the setup?

4. If the RAID cards I have are not true hardware RAIDS (which I don't think they are) if I go the fakeraid method with them, how much of a performance hit should I expect?

5. What is a good RAID monitoring program for [k]ubuntu?

---

### Post by quelx on 2008-05-29
You are correct in your estimation regarding those cards.  I would not even use the RAID capability on them (they probably won't work anyway since extra drivers are needed) and just use **mdadm** to manage the arrays

Here is a nice guide for Ubuntu 7.10 (Kubuntu 8.04 still uses the same mdadm utils) notice you need the **alternate** iso image.

[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

Performance will not be too degraded.  You would take the same hit even if the onboard raid were used (since it's really software anyway and needs the main CPU for data calculations)  The best method would be to have a true RAID card (I bought an Adaptec/Dell 6Port SATA adapter off ebay for ~$150; newegg sells many true hardware adapters, search **lsi**, **3ware**) and all the processing is done by the card.

**mdadm** manages and reports on the arrays, make sure your email is setup properly on the server and it will email you when changes occur on the array.

---

### Post by pancakelizard on 2008-05-29
Hey thanks for the link. I printed it out and will use it whenever I go to do the install.

---

