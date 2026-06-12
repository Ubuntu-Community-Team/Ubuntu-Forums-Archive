---
title: "Formating a Hard Drive"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Dr. Tom on 2008-05-31
I am trying to install Ubuntu 7.10 on my hard drive.

Hard Drive:  160 GB with no partitions.

The setup I use with Windows:

C:\System --> 20 GB for Windows XP Pro and motherboard drivers
D:\Programs --> 20 GB for all programs
E:\Visual Basic --> 40 GB for all Visual Basic activities
F:\Games --> 40 GB for all games
G:\Storage --> 40 GB for all downloads, files, pictures, etc.

I want to do something similar with Ubuntu.  So far I have managed to do very little.  What I have done:

- Loaded Ubuntu into memory(?)
- Opened the Install icon
- Got to the Prepare Partitions page.  I have the following:
-----/dev/sda
......free space.........................160041 MB

- Click on free space and set up the following:
-----/dev/sda
....../dev/sda1.....ext3.................20003 MB unknown
....../dev/sda5.....swap.................20003 MB unknown
....../dev/sda6.....ext3.................60019 MB unknown
....../dev/sda7.....ext3.................60015 MB unknown

- Now I edit the partitions to add the Mount Points:
-----/dev/sda
....../dev/sda1.....ext3...../...........20003 MB unknown
....../dev/sda5.....swap.................20003 MB unknown
....../dev/sda6.....ext3.................60019 MB unknown
....../dev/sda7.....ext3.................60015 MB unknown

This is as far as I get because I do not understand the Mount Points.  The choices I have are:
  /
  /boot
  /home
  /tmp
  /usr
  /var
  /srv
  /opt
  /usr/local

sda1 is assigned Primary and Beginning
sda5, sda6, and sda7 are assigned Logical and Beginning

What I am looking for is an explanation of the Mounting Points.
- Can I change names?  For example can I make one /usr/local_1 and another /usr/local_2?
- Which is the partition that gets the Ubuntu system files?  Is it "/"?  Is it "/boot"?  Is it "/home"?
- Am I limited to only four partitions?

I have two books on Ubuntu.  Both seem to assume that this is common information.  But right now I am very lost.

Thanks for any help you can give me.

---

### Post by Sef on 2008-05-31
Locked.  [Duplicate Post]("http://ubuntuforums.org/showthread.php?t=814608").

---

