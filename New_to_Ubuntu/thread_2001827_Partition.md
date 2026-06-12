---
title: "Partition ?"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by nu2this2 on 2012-06-11
Hello,

I Have win xp home edition and would like to install Ubuntu 11.10 as a dual boot. From the live disk in the installation tab I am given 4 choices.

1. Erase Ubuntu 10.04 LTS and reinstall.
2. Upgrade from 10.04 to 11.10.
3. Erase everything and reinstall.
4. Something else such as create or resize partitions or choose multiple partitions for ubunu.

In as much as I want to run Ubuntu alongside windows, I believe my choice should be #4.

When I choose #4, an installationtype window appears. There are 4 choices here as well.
1.sda 2 (fat32).
2.sda 1 (ntfs).
3.sda 5 (ext4)
4.sda 6 (linux-swap)

Which one should I choose?

Thanks for any input.

---

### Post by timcowchip on 2012-06-11
3 is your linux partition. choose 3 to install 11.1 over 10.4.

---

### Post by nu2this2 on 2012-06-11
Thanks for getting back. If I choose #3 won't I erase everything, including the Windows OS?

 There is a warning with #3. "This will delete all your programs, documents, photos, music and other files in both microsoft windows and ubuntu 10.04 LTS"!!

---

### Post by timcowchip on 2012-06-11
select the mount point "/" for partition 3 and check "format" for that partition only and the installer should leave the other partitions as they are.

---

### Post by deadflowr on 2012-06-11
> **timcowchip said:**
> 3 is your linux partition. choose 3 to install 11.1 over 10.4.

What timcowchip means is that this is the partition to choose from  the "something else" installation selection.

number 3)sda5 (ext4)

This is where your current 10.04 install resides. Simply select it, click change, choose your file system (ext4), in the other dropdown  click and select /. click ok, it will reload the partition page, when it is done install now, and set the defaults like time, keyboard and first user as asked.

---

### Post by nu2this2 on 2012-06-11
Additionally, I don't have 10.04 installed. Only windows xp. I Am working from a live disc for 11.10

---

### Post by deadflowr on 2012-06-11
> **nu2this2 said:**
> Additionally, I don't have 10.04 installed. Only windows xp. I Am working from a live disc for 11.10

Somehow you do, otherwise the install would never mention it.

---

### Post by wilee-nilee on 2012-06-11
> **nu2this2 said:**
> Additionally, I don't have 10.04 installed. Only windows xp. I Am working from a live disc for 11.10

Take a screen shot of gparted looking at the hard drive **before you do anything here**, and use the paper clip in the reply panel to post it.

Gparted is on the live cd.

---

### Post by nu2this2 on 2012-06-11
WOW!!

Now this is really confusing me. A couple of years ago I did install Hardy Heron on this very same laptop. I used a dual boot system for a while then the computer completely crashed, It wouldn't even boot up. I reinstalled windows from a disk and never used Ubuntu again.

Now the computer is so slow I want to see if this version of Ubuntu will be faster.

I don't know what to say about the install program thinking I have 10.04. With this in mind, should I still choose #3? I don't want to lose information OI have in XP.

---

### Post by wilee-nilee on 2012-06-11
> **nu2this2 said:**
> WOW!!

Now this is really confusing me. A couple of years ago I did install Hardy Heron on this very same laptop. I used a dual boot system for a while then the computer completely crashed, It wouldn't even boot up. I reinstalled windows from a disk and never used Ubuntu again.

Now the computer is so slow I want to see if this version of Ubuntu will be faster.

I don't know what to say about the install program thinking I have 10.04. With this in mind, should I still choose #3? I don't want to lose information OI have in XP.

Take a screen shot of gparted looking at the hard drive **before you do anything here**, and use the paper clip in the reply panel to post it.

Gparted is on the live cd.

---

### Post by oldfred on 2012-06-11
Best to follow wilee-nilee's suggestion on post screenshot.

We need to be careful which #3 we are talking about. The #3 on the install menu will overwrite everything on the drive. Always best to have good backups just in case you click on the wrong thing. (I have installed to the wrong partition, so it is not all that hard to do.)

Using #4 Something Else or manual install then requires you to specify which partition to format and use a / (root) or create & format new partitions. That will overwrite that partition but not the drive. If you have swap it will find it and reuse it.

---

### Post by deadflowr on 2012-06-11
> **nu2this2 said:**
> WOW!!
I don't know what to say about the install program thinking I have 10.04. With this in mind, should I still choose #3? I don't want to lose information OI have in XP.

Yeah, I don't know how well the installer reads past installations beyond lucid, it might be that you only have hardy installed and the installer can only read back to lucid.
At this point, yeah, choice 3)sda5(ext4) is the one to select.
However, so we can verify everything's kosher, do what wilee-nilee suggests and post a screenshot of gparted.

---

### Post by nu2this2 on 2012-06-11
What is Gparted and where do I find it on the live cd?

---

### Post by timcowchip on 2012-06-11
Its in the Administration section of the menu. It is a Disk partition utility. Screenshot is in the Accessories section.

---

### Post by deadflowr on 2012-06-11
Gparted is a graphical partition editor, but for our purposes we won't be using it to do any partitioning.(at least not yet)
To open it up, in the leftside of the liveCD screen, should be a row of icons, click on the top icon, which will open the dash. Inside the dash, you can either type in gparted in the search pane, or manually search for it through the installed apps area.
Once you've found it, open it up, and take a screenshot using the prt scrn button on your keyboard. It should save to something like the Pictures folder.

---

### Post by nu2this2 on 2012-06-11
> **deadflowr said:**
> Gparted is a graphical partition editor, but for our purposes we won't be using it to do any partitioning.(at least not yet)
To open it up, in the leftside of the liveCD screen, should be a row of icons, click on the top icon, which will open the dash. Inside the dash, you can either type in gparted in the search pane, or manually search for it through the installed apps area.
Once you've found it, open it up, and take a screenshot using the prt scrn button on your keyboard. It should save to something like the Pictures folder.

Thanks,

I think I found it, took the screen shot and saved it to a folder named pictures.Did this screen shot go into "My Pictures" in windows?

---

### Post by oldfred on 2012-06-11
No, it just is in memory as part of liveCD. If you shut down it will disappear. You can copy it to XP, but do not need to. And I normally suggest not to write too much directly into  a system partition.

Fomr a message here, click on the paperclip icon in the edit panel above the message. It will open a upload & search box to upload the screenshot. Sometimes things save in different places so if unsure you can search with Nautilus to know where it did save.

---

### Post by deadflowr on 2012-06-11
I think technically, it saves the picture in /home/ubuntu/pictures when using a livedisk. But when you go to upload it, the pictures folder accessed will be the livedisk's.(unless you've mounted the other partitions)

---

### Post by nu2this2 on 2012-06-11
> **oldfred said:**
> No, it just is in memory as part of liveCD. If you shut down it will disappear. You can copy it to XP, but do not need to. And I normally suggest not to write too much directly into  a system partition.

Fomr a message here, click on the paperclip icon in the edit panel above the message. It will open a upload & search box to upload the screenshot. Sometimes things save in different places so if unsure you can search with Nautilus to know where it did save.

Thanks, . I'm using the laptop with the live cd. But I'm posting on this forum with another computer because I can't get the wireless to connect on the one with the live CD:(  . So I won't be able to post the screenshot----------suggestions?

---

### Post by timcowchip on 2012-06-11
Copy the screenshot to a USB memory stick or flash disk if your laptop is capable.

---

### Post by nu2this2 on 2012-06-11
That's a good idea! I might also be able to connect to the internet with an ethernet cable to my modem.

Right now it's late and I will try this tomorrow. But **THANKS **to all of you for the help I really appreciate it!!

---

### Post by nu2this2 on 2012-06-12
Well, finally was able to take a screen shot while using the live cd. I have connected a flash drive but don't know how to get the pic onto the drive. I'm sure it's a simple thing.  Any help?

Another thing, since I can't get on the internet with the live cd I will have to paste the screen shot unto the forum with another "puter" using windows 7. Will I have any problems doing that?

---

### Post by oldfred on 2012-06-13
It should have saved in Pictures. 

So use Nautilus and open Home then Pictures. You should just copy and paste into the flash drive. Flash drive should be in /media or otherwise show in the left panel of Nautilus.

Have not tried using paperclip with Windows 7 but I would think it should work.

---

