---
title: "How to Clone a Ubuntu"
date: 2010-06-08
forum: Programming Talk
---

### Post by huangyingw on 2010-06-08
Hello all,
	I am permitted to "get" my Ubuntu to company's lab, where Internet access is limited.
	But the problem is how to "get" my Ubuntu into lab?
	My current solution is to use tar to tar the root directory from my home Ubuntu and untar it 
	to a whatever version of Ubuntu in lab, to form my favorite Ubuntu in lab.
	I run this command with root right in my home machine
	```

	tar -cvpzf /media/sda7/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media / 
	
```
	And move the backup.tgz to my target machine and run the following command with root right:
	```

&#12288;tar -xvpzf /media/sda7/backup.tgz -C / 
	
```
	But after hard reset, the target machine could not boot. 
	So, it seems that I need to exclude more files, or some important files is not tared?
	Could someone help me with a good "tar" command or a new and convenient solution?

---

### Post by Glenn nl on 2010-06-08
Try getting a Ubuntu One account and installing deja dup, and than move the deja dup backup file in your Ubuntu one file, now install deja dup on the other pc and add that pc to your ubuntu one account and now open the backup file with deja dup.

---

### Post by huangyingw on 2010-06-08
> **Glenn nl said:**
> Try getting a Ubuntu One account and installing deja dup, and than move the deja dup backup file in your Ubuntu one file, now install deja dup on the other pc and add that pc to your ubuntu one account and now open the backup file with deja dup.
Seems that the Ubuntu one account, need Internet connection. While in my lab, Internet connection is forbidened:(

---

### Post by mdurham on 2010-06-09
> **huangyingw said:**
> Hello all,
	I am permitted to "get" my Ubuntu to company's lab, where Internet access is limited.
	But the problem is how to "get" my Ubuntu into lab?
	My current solution is to use tar to tar the root directory from my home Ubuntu and untar it 
	to a whatever version of Ubuntu in lab, to form my favorite Ubuntu in lab.
	I run this command with root right in my home machine
	```

	tar -cvpzf /media/sda7/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media / 
	
```
	And move the backup.tgz to my target machine and run the following command with root right:
	```

&#12288;tar -xvpzf /media/sda7/backup.tgz -C / 
	
```
	But after hard reset, the target machine could not boot. 
	So, it seems that I need to exclude more files, or some important files is not tared?
	Could someone help me with a good "tar" command or a new and convenient solution?

It appears that you already have some form of Linux on the destination machine and that you are overwriting the system that you are running with the command "tar -xvpzf /media/sda7/backup.tgz -C / "
This can't possibly work. Try installing using a Live CD. And what about booting, and the UUID of the partition which will be different.

---

### Post by huangyingw on 2010-06-10
> **mdurham said:**
> It appears that you already have some form of Linux on the destination machine and that you are overwriting the system that you are running with the command "tar -xvpzf /media/sda7/backup.tgz -C / "
This can't possibly work. Try installing using a Live CD. And what about booting, and the UUID of the partition which will be different.
So, I should ignore some files/directories, like /boot/, and what anyone else? 
Any way, I have found a tool called: remastersys.
I have not tried in detail. Just a rough look at its behavior, it use rsync to copy the directories like /var, and /home into a temp directory, and tar it into an installable ISO file. Finally I got an installable ISO. I will try this in detail after work.
I will try both ways.

---

### Post by dv3500ea on 2010-06-10
You can use a program called [remastersys]("http://www.psychocats.net/ubuntu/remastersys") to create a custom live cd from your installation. Alternatively you could try [clonezilla]("http://clonezilla.org/") to create an image of your hard drive.

---

### Post by huangyingw on 2010-06-10
> **dv3500ea said:**
> You can use a program called [remastersys]("http://www.psychocats.net/ubuntu/remastersys") to create a custom live cd from your installation. Alternatively you could try [clonezilla]("http://clonezilla.org/") to create an image of your hard drive.
Yes, thanks, I am trying remastersys. 
Mentioning the clonezilla, I have failed. Even with the original backup files, I could not restore my Ubuntu on the same PC.
maybe clonezilla is too complicated for me:(.

---

