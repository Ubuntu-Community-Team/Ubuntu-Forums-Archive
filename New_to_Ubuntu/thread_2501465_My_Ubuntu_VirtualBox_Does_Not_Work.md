---
title: "My Ubuntu VirtualBox Does Not Work"
date: 2024-10-08
forum: New to Ubuntu
---

### Post by gar2024 on 2024-10-08
Greetings fellow Ubuntu users:

I am a relative newcomer to the Linux Operating System. A few years ago I purchased the Udemy course and have been practicing the lessons over and over, at least until I have gained a solid grasp on Ubuntu.

However, I have encountered several issues with the present version that I am using, Version 7.0.18. I will outline them here and see what you make of them:


[LIST]
[*]I cannot save anything! Whenever I click on the "power off, power on" button, I lose whatever input I have done from the lessons. The slate is wiped clean, which was not the case with the previous versions I have worked with. 
[*]When I want the "ncal" feature (the present month calendar), I fist have to download the package with the information needed to install it. Again, if I power off and back on again, I must also reinstall the calendar. 
[*]Ditto with the "date," which is usually incorrect, at least by a day. This was not the case with previous versions; I would always get the correct date without having to do anything special. 
[*]Version 7.0.18 does not make allowances for me to create a Username or password. I can still work on the terminal but without the personal identifying features that ought to show up on the terminal. 
[*]The issue that bothers me the most is that I cannot transfer documents from my Windows machine to the VirtualBox. Some of the Udemy lessons have to be downloaded to a file, which cannot be done on the VirtualBox. I have to manually copy those lessons onto the VirtualBox; you can imagine how long that takes! I was able to transfer files with limited success with previous versions, but I cannot do it here. 
[/LIST]

Whew. That's enough for now. Despite all of the above, I really like the Linux system and intend to be good at it, at least for my own personal benefit. There is no age limit to learning (I am in my early 70s) so I want to make the most of my "schooling" here. If anyone reading this have any suggestions to make or, better yet, a solution to share, I am all ears, as they say.

Gary

---

### Post by yancek on 2024-10-08
What you are describing is what would be expected if you are booting the Ubuntu iso in VirtualBox and have not actually installed it.  Until you install it in VirtualBox, it will act the same way as a 'live' USB/DVD does and will not save any changes you make on reboot/restart.  Do an online search on how to install Ubuntu (whatever release version you have) in VirtualBox.

After you install Ubuntu in VirtualBox, the link below explains using Shared Folders.  You will need Guest Additions installed also which is mentioned on the page at the link below.  The 2nd link explains installing guest additions.

[https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/sharedfolders.html](https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/sharedfolders.html)

[https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html)

---

### Post by ActionParsnip on 2024-10-11
Is this an installed OS to the VirtualBox disks or are you simply booting the ISO?

---

