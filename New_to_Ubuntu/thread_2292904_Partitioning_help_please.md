---
title: "Partitioning help please"
date: 2015-08-31
forum: New to Ubuntu
---

### Post by dgra128 on 2015-08-31
Hard disk in windows looks like: Pic 1

but this is how the hard disk looks when install ubuntu parallel with windows 7: Pic2

So how to appear hard disk like windows? please help you.

---

### Post by ajgreeny on 2015-09-01
Hi dgra128 and welcome to the forum.

I have changed the thread title to make it more useful for forum users who might be able to help you.

Can you please use thumbnails for images in future as some users have slow web-connections which make large images such as you used used difficult to view.

I have edited the post this time but in future, use the "Reply to Thread" button, click on the paperclip icon in the toolbar, browse to, and double click the image on your hard drive, and then finally click "upload"

The post will then look as it does now.

To your problem which I don't think I can help with apart from suggesting that you[LIST=1]
[*]Read through the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) as I think UEFI may be at the root of your problem
[*]Use the Boot-Repair item in my signature below and follow the info there to run the script from a live ubuntu system.  Post back here the link to pastebin that you will get from the script.  Do not accept the default repair at this stage, just post the link.
[*]
[/LIST]

---

### Post by oldfred on 2015-09-01
Did you choose the LVM or LVM with full drive encryption install options?
Those options erase the entire hard drive.

You are not showing any NTFS partition. But it does show the 100MB Windows boot partition? 
And Ubuntu does not use ext3 any more for installs.

---

