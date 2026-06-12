---
title: "mounting partition"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Dave B on 2008-09-12
hey all
I have just installed ubuntu on a laptop and am trying to figure out how to have a partition mount mount
 

thanks

Dave

---

### Post by Tatty on 2008-09-12
What partition are you trying to mount / what filesystem, and are you trying to get it to mount automatically on boot, or do you want to just mount it manually when you need it?

---

### Post by Dave B on 2008-09-12
im trying to mount /home in ext3

and have it show up in places so i can mount it from there

thanks

---

### Post by Tatty on 2008-09-12
Your /home should already be mounted otherwise ubuntu would not be able to log you in.

Or am i misunderstanding what you are asking?

---

### Post by Bucky Ball on 2008-09-12
[quote=Dave B]im trying to mount /home in ext3[/quote]

EXT3 is the file type. When you click the drop down menu, 'Places', what do you see? Any of your partitions there? If so they are already mounted.

Open a terminal (Applications->Accessories->Terminal) and copy and paste this:

**sudo blkid**

This will list all your drives and the partitions on them; eg sda1, sda5, sda6 means on Drive 1 you have 3 partitions.

Now, if you find the partition you want to mount, type in the terminal;

**sudo mount /dev/sda?** (?=number of the partition you are wanting to mount).

To get them to automount is a bit trickier but not much. See how you go with that first. :)

ps: as Tatty says, /home is where you are right now.

---

### Post by Dave B on 2008-09-12
i cannt access it and cant see it under places>

---

### Post by Bucky Ball on 2008-09-12
[quote=Dave B]i cannt access it and cant see it under places>[/quote]

Open a terminal and type:

**cd /home**

Hit enter. There you are. Home. If you want to see what is in your /home directory, type:

**dir**

Getting it? You are already there. If you go to 'Places' and open one of your other partitions, you will see 'Filesystem' in the column on the left. Click it. In there you will find home. /home is a directory. Not a partition, therefore you can't mount it, the partition the directory it is in is already mounted. :)

---

### Post by Dave B on 2008-09-12
here is what i get :

dave@lappy:~$ sudo blkid
[sudo] password for dave: 
/dev/sda1: UUID="e25f5003-9213-4d63-b423-d92750b52ab8" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="7051a2e9-d400-4b85-8c34-56c159629927" 
/dev/sda3: UUID="c4a4d1b2-3f18-4732-b126-9dbd9f71f13d" TYPE="ext3" 
dave@lappy:~$ 
dave@lappy:~$ sudo mount /dev/sda3
mount: /dev/sda3 already mounted or /home busy
mount: according to mtab, /dev/sda3 is already mounted on /home
dave@lappy:~$ 
dave@lappy:~$ 

under places i DONT see this partition

---

### Post by Bucky Ball on 2008-09-12
> **Dave B said:**
> here is what i get :

dave@lappy:~$ sudo blkid
[sudo] password for dave: 
/dev/sda1: UUID="e25f5003-9213-4d63-b423-d92750b52ab8" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="7051a2e9-d400-4b85-8c34-56c159629927" 
/dev/sda3: UUID="c4a4d1b2-3f18-4732-b126-9dbd9f71f13d" TYPE="ext3" 
dave@lappy:~$ 
dave@lappy:~$ sudo mount /dev/sda3
mount: /dev/sda3 already mounted or /home busy
mount: according to mtab, /dev/sda3 is already mounted on /home
dave@lappy:~$ 
dave@lappy:~$ 

under places i DONT see this partition

Okay, /dev/sda3 is mounted without a name at this point. You will find it under places as something like '20Gb' or something bland like that. If you follow my instructions about going to Filesystem you will find the directory Home.

As Tatty said originally, everything you are doing now is on the mounted partition /dev/sda3. :) 

You have no problem, all is as it should be. You can give your partitions names. I have to go out for awhile but will check back. In the meantime, someone else might spot your post and help you further, but again, everything is fine with your system by the looks.

---

### Post by Tatty on 2008-09-12
Home is mounted on your system correctly, dont worry about that.  The only problem here is that it is not showing up under Places whereas it should be.

Im not sure how to add Home to Places, but ill try to find out.  In the meantime you can still access your home folder by going to Places->Computer then itll be in /home/your-user-name

---

### Post by Bucky Ball on 2008-09-12
But now I get you ... the 'Home Folder' is missing from your 'Places' drop down menu! Duh, sorry.

From this page: [http://ubuntuanswers.wordpress.com/](http://ubuntuanswers.wordpress.com/)
> 
1.Open up **Nautilus File Browser** ( **applications>places>home folder**)
 In the left pane you will see a list of folders and drives in your Places menu, in the right pane you will see the folders within your home folder.
 2.**Create **a **new folder** ( shift+ctrl+n)  and name it whatever you wish and hit ( **enter**) If you already have a folder in mind skip the aforementioned and move along to (3)
 3.**Left click** on the folder and **drag **it into the left pane to the bottom of the list.
 Magically it appears, you can click and drag it into any position within the left panel that you like.
 To **remove **it from the left pane, **right click** the folder and select **remove**.
You would replace instruction 1. in your case (as you have no Home Folder there) with, in a terminal:

**sudo nautilus**

... and skip 2. as you already know what folder you want in there.

Now, this is a workaround rather than a fix, but for me, not satisfactory as it doesn't actually explain why the Home Folder is missing from 'Places'. I will dig deeper.

:confused:

* Update: this method works great and I have found it quite useful myself by adding some of my regularly accessed folders in there. But again ... why wasn't Home Folder there originally?? Make sure you place the folder in the bottom half of the left hand pane if you try it. :)

---

### Post by Dave B on 2008-09-12
thank you to everyone that helped.

/home IS mounted and i can write to it 

it is just not apearing in the way that i am used to and that was confusing to me.

thank you 

Dave

---

### Post by Bucky Ball on 2008-09-12
Good news. If you are used to Windoze, Ubuntu is a bit of a shift in thinking. You'll soon get used to it. You can mark your thread as solved by going to 'Thread Tools'. Welcome and good luck. :)

---

