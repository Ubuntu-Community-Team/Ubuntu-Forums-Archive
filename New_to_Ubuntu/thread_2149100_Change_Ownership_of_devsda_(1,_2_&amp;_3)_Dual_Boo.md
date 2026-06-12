---
title: "Change Ownership of /dev/sda (1, 2 &amp; 3) Dual Boot 12.04 with 13.04"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by Rekhillbill on 2013-05-27
[SIZE=3]Hello,

I just installed 12.04 ( /dev/sda7 ) in lieu of Windows 7 in dual boot with 13.04 ( /dev/sda5 ).

How do I change ownership of /dev/sda1, 2 & 3 and all the folders and files?

Now, root has ownership of all three, reference the following image:[/SIZE]


[ATTACH=CONFIG]243134[/ATTACH]

[SIZE=3]I have tried the following:

bill@bill-Satellite-L500D:~$ chown bill /media/bill/2be4ba71-c07a-4f12-a878-5a9011b1af16
chown: changing ownership of ‘/media/bill/2be4ba71-c07a-4f12-a878-5a9011b1af16’: Operation not permitted
bill@bill-Satellite-L500D:~$[/SIZE]

[SIZE=3]Any help would be greatly appreciated.

Thanks,
Bill[/SIZE]

---

### Post by deadflowr on 2013-05-27
You use sudo.

But I wouldn't change the ownership on any partition that contains system files.
Like /boot or /.

Only on personal data partitions.

Otherwise changing system file ownership will result in a need to reinstall.

---

### Post by Paqman on 2013-05-27
> **Rekhillbill said:**
> [SIZE=3]
bill@bill-Satellite-L500D:~$ chown bill /media/bill/2be4ba71-c07a-4f12-a878-5a9011b1af16
chown: changing ownership of ‘/media/bill/2be4ba71-c07a-4f12-a878-5a9011b1af16’: Operation not permitted


You're on the right track. Try:
```
sudo chown -R bill /media/bill/2be4ba71-c07a-4f12-a878-5a9011b1af16 
```

What's the difference?

sudo = Super User Do. Since the drive is currently owned by root you need to have root's authority to change anything.
chown -R = Recursively change owner. The -R switch applies the command to everything on that drive, instead of just the actual mount point

---

### Post by Rekhillbill on 2013-05-27
I want to use the Data partition, hopefully /dev/sda2 for both 12.04 & 13.04.

When I installed 12.04, 13.04 was already installed in dual boot with Windows 7, I used a combination of "Something Else" and "Install along side 13.04 in dual boot".

I selected /dev/sda2 for the install of 12.04 and then I resized the space for 12.04 to about 30 GiB with the idea of using the remaining 105 GiB for a data partition.

After that, I went back to "install along side 13.04" and selected that install option.

I was a bit surprised to find that "Boot" was installed in this partition, i.e., /dev/sda2.

With deadflowr's following comment, I am uncertain what I should do next?

> But I wouldn't change the ownership on any partition that contains system files.
Like /boot or /.

Only on personal data partitions.

Otherwise changing system file ownership will result in a need to reinstall.

The other two partitions, i.e., /dev/sda1 & /dev/sda3 or another issue best left for another thread.

But, I am very new at this and don't want to mess something up, since both 12.04 and 13.04 are working OK.

BUT, if I don't change ownership, I can't use any of those partitions!

So, Paqman's comment below, seems to be a good way to go:

> sudo = Super User Do. Since the drive is currently owned by root you need to have root's authority to change anything.
chown -R = Recursively change owner. The -R switch applies the command  to everything on that drive, instead of just the actual mount point         


I don't suppose "moving" the boot or creating another patition without the boot in it is good idea?

If it is, it probably does not belong in this thread either?

Please let me have your comments or suggestions.

Thanks,
Bill

---

### Post by deadflowr on 2013-05-27
Yep, Paqman's advice is definitely the way to go.
I just always advise to double check that the partitions in question contain your files, like photos and music and documents, and that they don't contain system stuff, like the /etc/, or /usr, or /lib directories.
Your stuff is your stuff and the permissions set are up to you.
But system stuff gets mucked up when permission get changed, so I just want you to be cautious, that's all.

---

### Post by Rekhillbill on 2013-05-27
deadflowr

I appreciate the advise about being "cautious"!

That's why I want to ask about the boot, as it relates to your following comment:

> But system stuff gets mucked up when permission get changed, so I just want you to be cautious, that's all.         

Since my "future" Data partition /dev/sda2 contains the boot location...is that something I have to be careful about changing permissions?

Thanks,
Bill

---

### Post by Rekhillbill on 2013-05-27
deadflowr

OK.  After running the following code suggested by Paqman, I now have permission as "bill" to work with not only the /dev/sda2 but also the folder & files within.

    
```
sudo chown -R bill /media/bill/2be4ba71-c07a-4f12-a878-5a9011b1af16
```

The above code applies to /dev/sda2 only.  So, I'll have to do the same for /dev/sda1 & /dev/sda3.

Also, I needed to "re-boot" before the permission was changed.

I went to /dev/sda2 and checked the "show hidden files" box but could not find any hidden files.

Nor could I find any evidence of the Boot.

So, I am going to continue to use this device [ /dev/sda2 ] for my main Data folder.

deadflowr,  Thank you and Thanks, also, to Paqman

I really appreciate all the help.

Best,
Bill

---

### Post by Paqman on 2013-05-27
> **Rekhillbill said:**
> 
Nor could I find any evidence of the Boot.


The partition has the boot flag set on it (which doesn't really make any difference on Linux), but it isn't an actual boot partition for your Linux install. For a start, you would have had to specifically set your machine up that way, as it's a non-default setup. So you'd know if you had a boot partition. Also, the screenshot you showed above shows that the partition isn't mounted at /boot.

---

