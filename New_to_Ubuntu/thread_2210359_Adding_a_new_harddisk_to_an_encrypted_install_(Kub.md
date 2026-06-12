---
title: "Adding a new harddisk to an encrypted install (Kubuntu)"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by bcarney on 2014-03-10
I am adding another HD to my LVM Encypted install (running on another drive). I need directions for encrypting the new drive. I would also like to only use 1 encryption password to unlock both drives. I am fairly new to Ubuntu so looking for detailed directions. 

Thanks in advance

---

### Post by Herman on 2014-03-11
Hello bcarney,

Look for the 'Ubuntu Software Center'or whatever it's called in Kubuntu. In Ubuntu it's in the sidebar. Open that and you should be able to do a search and find a program called 'Logical Volume Management', also known as system-config-lvm. That's the program you will be able to use for working with your logical volumes.

You'll also need GParted partition editor, so if you don't already have it, install that too.

First, use GParted to create a MBR in the new hard disk, ('Device', 'Create Partition Table'). Make sure you are formatting the correct hard disk before you do anything, and have all your data backed up in case you make a mistake. This will not erase the disk, but you will lose access to any file systems in the disk along with any files. You said it's a new disk so that's okay, just make sure you pick the right one.

Create an empty partition in the disk. It doesn't matter if you create any file system in it, just an empty partition will do.

Now you can close GParted and start Logical Volume Manager.
Logical Volume Manager doesn't open in my Ubuntu 13.10 64-bit OS unless I open a terminal up first and enter the following command,
```
sudo /usr/share/system-config-lvm/system-config-lvm.py;
```

When you have Logical Volume Manager open, go to the black text in the left-hand side-bar which says 'Uninitialised Entities'. When you click on the little triangle before it, another piece of text should come down out of it, with the words '/dev/sdb' or something like that. If you have a number of disks in your computer you may get a whole list of devices and you will again need to be sure you choose the correct one.
To check and see if it's the right one, again click on the little triangle before '/dev/sdb' or whatever it says and you should be presented with an image which resembles a horizontal black cylindrical object in the middle pane.
Looking further over to the right, in the upper part of the right-hand side bar you should see some information about the disk. the size of the disk may be a useful clue to help you confirm you're about to initialise the correct disk, providing your computer doesn't have other disks the same size.

When you're sure it's the right disk, you can go 'Tools', 'Initiailze Block Device', and that will cause the partition in the new hard disk to be registered as a PV, or 'Physical Volume' for LVM.

I'm not finished yet but I want to be able to try out my own instructions as I'm typing to make sure I give you the right advice. That means I need to boot into one of my other Ubuntu installations which is suitable for performing this kind of operation.

---

### Post by Herman on 2014-03-11
Now you should be able to see some new text in your left-hand side bar with the words 'Unallocated Volumes'. If you click on the little triangle in front of that, again some more lines will drop down and you should see your devices listed again as ' /dev/sdx ' or whatever. 
When you again click the little triangle before one of those lines, (I have a number of them but you might only have one), you should see some red text with the words 'Partition 1', and an image that looks like a red horizontal cylindrical object should be showing in the middle pane. It should be labelled as 'Unallocated Physical Volume'.


Looking down along the bottom of the 'Logical Volume Manager' dialob box, you should now see a row of three buttons, 'Create New Logical Volume', 'Add to exisitng Volume Group', and 'Remove volume from LVM'. 
It's the middle button we want to use this time, 'Add to existing Volume Group'. So click on that one.



[IMG]http://members.iinet.net/%7Eherman546/2014_02_15_Ubuntu_LVM_Four_USBs/Screenshot%20from%202014-03-11%2017:37:37.png[/IMG]
I have more than one volume group in my computer to choose from so I see a list in the next dialog, titled' Add Physical Volume to VG', so I select the appropriate volume group and click on the 'Add' button.
Yours will be simpler most likely.

Back in a few minutes ...

---

### Post by Herman on 2014-03-11
Now this time look in the left-hand side bar again, and up close to the top should be the words 'Volume Groups', again with a little black triangle before it that you can click on for a drop-down list of all your volume groups if you have more than one in your PC. Yours will just show one I would imagine, so that should once again make it easy to choose.

When you click on it the drop-down list should show some red font and some blue coloured font.
The red font has the words 'Physical View', and the blue font displays 'Logical View'.
Click on the blue 'Logical View' words.


[IMG]http://members.iinet.net/%7Eherman546/2014_02_15_Ubuntu_LVM_Four_USBs/Screenshot%20from%202014-03-11%2017:39:13.png[/IMG]
When you click on the Blue label, 'Logical View' in your Logical Volume Management' left-hand sidebar, you should see a blue cylindrical object in the center pane.
The drop-down list from 'Logical View' should show you your file systems. Mine are called 'root', and 'swap_1'. I presume you want to extend your 'root' volume.





[IMG]http://members.iinet.net/%7Eherman546/2014_02_15_Ubuntu_LVM_Four_USBs/Screenshot%20from%202014-03-11%2017:51:52.png[/IMG]
Click in the word 'root', (in blue in the left-hand side bar).
Now you should see three buttons across the bottom, below the center pane called 'Remove Logical Volume', 'Create Snapshot', and 'Edit Properties'.
It's the 'Edit Properties' button we want to use now.




[IMG]http://members.iinet.net/%7Eherman546/2014_02_15_Ubuntu_LVM_Four_USBs/Screenshot%20from%202014-03-11%2017:56:55.png[/IMG]
After clicking the 'Edit Properties' button, a new dialog should pop up, entitled (you guessed it), 'Edit Properties'. 
There's a slider about in the middle of it, which you can slide to the right to increase the size of your Logical Volume, and expand it across the new disk you just added. Slide it across the the right and click the 'Okay' button, and wait a few seconds while 'Logical Volume Management' does some work.


That's it! You can close 'Logical Volume Management' now and you should now have a lot more usable space in your encrypted Ubuntu installation. If you want to check, you can use the command 'df -h' in your terminal and it should show your /dev/mapper/ubuntu-root file system as being quite a lot larger than it was before.
```
df -h
```

Ubuntu (or Kubuntu), will behave as if it is installed across both hard drives, and it will seem to you as if you only have one large hard drive in your computer, not two separate disks. When you boot you will only need to type your LUKS encryption password once.

---

### Post by online3 on 2014-10-25
Herman, you've provided well laid out and carefully explained instructions on how to add and include a new volume into a LVM volume group. I follwed these instructions, and was pleased with how smoothly both the LVM config package and your instructions worked for me. 

However, I should make clear that your instructions only show how to add a new partition to the LVM group. They **don't **show clearly whether or how they will also make the new partition encrypted. In my case, as far as I can see the added partition is **NOT ENCRYPTED**. 

I'm using Debian, which requires that - during installation - one must first manually encrypt the partition intended for use as the LVM group, and then only afterwards do the LVM stuff. I know that Ubuntu installer will automatically provide an encrypted home folder during installation, but I've never worked with LVM on Ubuntu, so I may be wrong here. All the same, I'm wondering whether it is also the case with Ubuntu that the encryption is done first and then that encrypted partition is operated upon by LVM. 

It's my thinking that, if Ubuntu does follow Debian's procedure (albeit possibly transparently), when one adds a volume into the LVM group, one is only doing exactly that and no more. The new volume works as though it's part of the LVM group (which it is), but it is not encrypted, because the only part of the disk that was encrypted was that which was encrypted originally.

It could be that the Ubuntu version of system-config-LVM works seamlessly with dm-crypt/LUKS (the encyption software), so that any disk space added to an encrypted LVM group is also automatically encrypted. Alternatively, it may be that Ubuntu's method for providing encrypted LVM setups works differently to Debian's. But without some explicit assurance of the opposite, or without some means of verifying afterwards, I think it would be best to assume that when the LVM is built on top of an existing encrypted partition, one cannot make any other partition encrypted simply by adding it to the LVM group.

---

