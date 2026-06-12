---
title: "[SOLVED] Partition Ubuntu"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by donniezazen on 2008-10-01
Hello Friends,

I want to partition my hard drive in such a way that i can clean install Ubuntu as it come after each 6 months without removing all my data. A data drive where i can save all my data and it would be safe when i reinstall new Ubuntu version.

I have read few thread about it but as a noob i can understand those threads but their were no instruction to follow. Can somebody please give me instruction to do it. 

I have 120 GB hard drive(Dell 6400\E1505). I want to install Ubuntu in 10 GB partition(I think that would be sufficient) and remaining as data drive. Will it be possible make that data partition as home folder. I will later on install games and virtual machine i hope that should not interfere. Can games and virtual machine be installed in this newly created data partition?

Thank you.

---

### Post by Tatty on 2008-10-01
This is quite possible, I have a similar setup on my laptop, although I have two partitions for Ubuntu installs along side a /hom partition.  This is so I can install each new version of Ubuntu along side the current one, so i can switch between the two until I am satisfied that the new release is working for me.

Will this be a fresh install or are you wanting to alter an existing Ubuntu installation to do this?

---

### Post by Michael.Godawski on 2008-10-01
If you already have installed Ubuntu without a separate home partition have a look here:


[LIST]
[*][http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[/LIST]

---

### Post by k3lt01 on 2008-10-01
Do a 10gb / (root), 2gb SWAP, and the rest as /home. Then when a new release comes out all you do is install it into the 10gb / (root), that way all your personalised settings say the same.

It is advisable to have a back up of your personalised settings though.

---

### Post by donniezazen on 2008-10-01
> **k3lt01 said:**
> Do a 10gb / (root), 2gb SWAP, and the rest as /home. Then when a new release comes out all you do is install it into the 10gb / (root), that way all your personalized settings say the same.

It is advisable to have a back up of your personalized settings though.

Do you mean that even if clean install new release, my system settings will not change? 

What will happen of the softwares i have?

How to create 10GB /root, 2GB SWAP, and rest as /home? I already have Ubuntu installed. It's not a dual boot.

Thank you all of you.
SK

---

### Post by donniezazen on 2008-10-01
Two more questions

1. Will i be able to resize this newly created /home partition? Like we do with any other partition using Gparted.

2.Where are the Virtual Machines and games installed in root partition or /home?

Thank You
SK

---

### Post by k3lt01 on 2008-10-01
> **soham_1207 said:**
> Do you mean that even if clean install new release, my system settings will not change?  Only the sytem settig that are in .hidden filesin your /home partition.

> **soham_1207 said:**
> What will happen of the softwares i have?  this depends on how you upgrade to a newer version. If you upgrade through Synaptic your software will update at the same time. If you do a clean install through a live cd the you will reformat your / (the forward slash means root) partition and you will have to reinstall any software that you added after your previous install.

> **soham_1207 said:**
> How to create 10GB /root, 2GB SWAP, and rest as /home? I already have Ubuntu installed. It's not a dual boot. If you do this you MUST back up your home folder and I would advise you to make a list of all your programs you have and use (even if they are not in your applications list. Step by step. I can't and wont take responsibility if you lose info or stuff the install.

1. Get your live cd and start your machine as you did when you installed Ubuntu last time.

2. Go through the processes as you did before until you get to partitioning the hard drive.

3. When you get to the partitioner you have few options chose the "manual partition option.

4. Click in the hard drive partition shown and then click edit partition.

5. Now you have to decide whether your willing to start again with total new install or whether your willing to risk resizing the / partition. f I were you I'd do a totally new install as you should have backed up your important info anyway. Now here you can click either delete this partition or edit this partition. If you click delete it WILL take you back to a totally clean install.

6a. Delete partition option chosen. Click on the blank partition (Free Space) and click new partition. This will bring a box up showing how big your hard drive is, adjust the number to 10000. Now go down to "Mount point" and click the down arrow to select "/" (this is your root partition),  then click to format this partition and it will ask you what format to use chose ext 3 Journaling File System, now save these changes.

6b. Now you need to click on the "Free Space" again, "New Partition" again, make the size 2000 choose "SWAP" in the file format click to make the change.

6c. Same process again but use the remaining free space and choose "home" in the mount option.

7. Go through the rest of the install as you did before.

8. Make sure you put the files you backed up from your old /home partition back into your new one so you keep your old settings.

9. Re-install any programs you need that are not in the standard system which you had before.

10. Remember to let Ubuntu update itself after this is all done.

Last and most importantly enjoy your system and update your "/"partition when you want to want to upgrade to a new version.

> **soham_1207 said:**
> 1. Will i be able to resize this newly created /home partition? Like we do with any other partition using Gparted.Yes

> **soham_1207 said:**
> 2.Where are the Virtual Machines and games installed in root partition or /home?/home for Virtual, if your games are Linux games they will be in / if they are Windows games they will e in /home

---

### Post by donniezazen on 2008-10-01
Thank You so much for your help. Thats why i like Ubuntu/Linux.

One more Question.

1. What do you mean by Linux games and Windows games?
2. I don't really play games  but ya i would like to leave some space if in future i want to install games. I think 10 GB / partition would be fine because minimum system requirement is 4 GB and at most i will install 2-3 games at a time.

Thank you.
SK

---

### Post by Kellemora on 2008-10-01
HELP, I need some clarification here on all this!

I must have learned something totally WRONG I guess.

I THOUGHT that if you backed up your /home, /usr and /var directories that you would have saved any programs and their associated data that you installed.

Thus if you did a clean install and wrote these three files back, you would maintain all of your separately loaded non-system files.

In the Doze, I have a Folder for Program files, not part of DOZE, a Folder for Documents, a Folder for Images, etc.
No I realize that many Doze programs install all over the place, but some don't and you can install all the dll's and other necessary requirements right in the Program Folder for that particular game.  Only works with some games of course, others need to be installed.

I thought Linux HELD 100% of a program in one or two folders?

Can somebody clarify for me, since Linux does not have a registry.

TTUL
Gary

---

### Post by k3lt01 on 2008-10-01
> **soham_1207 said:**
> Thank You so much for your help. Thats why i like Ubuntu/Linux. You are welcome. I see this as "Paying it forward", we all learn sometime and if everyone can help people learn what they have learned from others then the community is working.

> **soham_1207 said:**
> 1. What do you mean by Linux games and Windows games?  Linux games are games designed to run on Linux systems without any mucking around to get them to work. This is called working natively. Windows games are games designed to run on Windows, some will run on Linux through WINE.

---

### Post by k3lt01 on 2008-10-01
> **Kellemora said:**
> I THOUGHT that if you backed up your /home, /usr and /var directories that you would have saved any programs and their associated data that you installed.

I thought Linux HELD 100% of a program in one or two folders? 
I only ever backup my /home partition, you may be right about /usr and /var though.

---

### Post by donniezazen on 2008-10-02
I created a 20 Gb partition so that i can save my data and format other part and create a separate /home. Thanks to earlier post i succeed in that. I have moved my data back to newly created /home partition. But i am not able to add that partition to /home. I used Ubuntu Live Desktop Cd and when i try to resize newly created i can only reduce the space but not increase it. How to extend this /home partition?

Thank you.

---

