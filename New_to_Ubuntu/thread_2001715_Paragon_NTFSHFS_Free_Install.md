---
title: "Paragon NTFS/HFS Free Install"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by mrmeister on 2012-06-11
Hi,
I'm fairly new to Linux. I've used Ubuntu before, but only ever on a rubbish laptop as a free way of creating documents before I got a version of Office for my Mac. I've now decided to resurrect this same rubbish laptop with Ubuntu 12.04 (LTS) and we're using it as a shared web surfing laptop for the living room in our student house. We're a house of Mac and Windows, so i figured i'd try and get complete support for all of our files on this laptop so we can plug in whatever external hard drives we have with no issue. After a bit of looking around, i saw the software company Paragon do a driver for Windows' NTFS and Mac's HFS, and better yet, they do a free version :)

I downloaded it (only a tiny 3.4MB file) and now i have no idea what to do. First, the instructions and commands in the Read Me text file and the User Manual pdf differ slightly, but i just can't seem to get it unpacked using the terminal. I tried doing it with the GUI and told it to extract to my Downloads folder, then tried to run the install.sh using "sudo ./install.sh" and it started to install via terminal, but when it got to building the actual driver it failed and couldn't go any further. I think this is because i extracted using the GUI to Downloads, instead of using terminal to extract to usr/tmp.

Can anyone help me out here please?
Thanks in advance
mrmeister

---

### Post by coffeecat on 2012-06-11
Ubuntu has read-write support for NTFS out of the box - has done for years. It also has read-only support for HFS+ (the journalled version) out of the box, and read-write if you create a non-journalled HFS+ filesystem in MacOS. Has done for years! :)

**EDIT**: the problem with using HFS+ for an external drive with Ubuntu is one of Unix permissions, which are used in both MacOS and Ubuntu/Linux. Your UID (userid) in Ubuntu and in MacOS will be different and this can lead to some "entertaining" moments trying to access your files.

---

### Post by mrmeister on 2012-06-11
I just want it so that i can use it as a 'hub' computer, so that we can drag and drop, and easily transfer large files, such as our projects (music and film based) and large HD movies. Obviously, FAT32 was the first choice, but a lot of our stuff is bigger than 4GB, so it'd be easier to get full read/write support on NTFS and HFS+

---

### Post by coffeecat on 2012-06-11
First - with regard to the Paragon drivers. Few if any forum members are likely to have experience of these because of the reason I posted - out of the box support for both ntfs and hfs+ in Ubuntu - so we will need to know more about the install instructions to be able to help you. Unpacking the downloaded file ih the GUI or via the terminal would make no difference, so the problem doesn't lie there. If the readme text file is not too big,can you post the relevant part so that we can see it, and see what you need to do?

Having said that, installing the NTFS driver in Ubuntu is quite pointless in my view because of what I said in my previous post. The HFS+ driver might be useful if it offers read-write support for the journalled version of HFS+, but you are still likely to encounter file ownership/permissions problems unless the Paragon people have found some way of circumventing that.

I have another suggestion for you. Ubuntu offers reliable read-write NTFS support out of the box - no need to install anything. MacOS can read NTFS out of the box but not write. Can you cope with having read-only for NTFS in MacOS? If so, one advantage of using NTFS as your sole transfer filesystem between Windows, MacOS and Ubuntu is that NTFS does not support the Unix/Linux/MacOS system of ownership and permissions. You neatly sidestep the permissions issue between MacOS and Ubuntu if you use NTFS. If you need NTFS write in MacOS, you could install the open-source Mac ntfs-3g driver, but you'd need to search for how to do this. Last time I did this was with Snow Leopard about a year or two ago. It worked, but slower than in Ubuntu, but things may have changed now. Alternatively, does Paragon do a free NTFS driver for MacOS? I guess that would be easier to install and then you would have NTFS read-write in all three OSs.

---

