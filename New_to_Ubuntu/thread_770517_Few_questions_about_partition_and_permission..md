---
title: "Few questions about partition and permission."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by adnansanni on 2008-04-27
Hey I have download Hardy and install on my laptop and I just love it. This is the best Linux I&#8217;ve seen. I&#8217;ve few questions because I&#8217;m going to reinstall it as clean install.

1)	I did partition my HDD with this way

	#1 primary	25.0 GB		ext3	/
	#5 logical	5GB		swap	swap
	#3 primary	50 GB		ext3	/adnan

So the question is what is the difference between primary and logical? Should keep all primary or only / as primary? Hope someone can clear me in this point. Is swap 5 GB is OK or just waste of space? I have 1GB ram.

2)	I made a partition /adnan for store data because in future, clean install won&#8217;t need to delete data from this partition. The problem is I can&#8217;t write anything in this partition as it is say &#8220;Owner: root&#8221;. So how can I write something in this partition as root? I can&#8217;t login as root.

3)	Is there any good tutorial for command lines? I used to sometimes fedorian and also newbie so I really need that one.

4)	How to change permission for files and folders I mean what are the commands?
Hope some Guru can help me.

---

### Post by hackle577 on 2008-04-27
> **adnansanni said:**
> Is swap 5 GB is OK or just waste of space? I have 1GB ram.

5 gigs of swap is way too much, I'd go with just 1 GB.

> **adnansanni said:**
> Is there any good tutorial for command lines? I used to sometimes fedorian and also newbie so I really need that one.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

EDIT: Here's an even more detailed guide to the command line: [https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

---

### Post by artir on 2008-04-27
The partition should be mounted in /media/adnan to acces it in the normal way

A 5 GB sawp is too much. I have 2 GB and i have 2 gb swap just  in case i want to hibernate. If you dont want to hibernate, 1 gb is enough unless you render 3d stuff.

To learn the art of the console, go here: [http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php](http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php)

To change permission you can a)Use the built in menu in nautilus(right click) and if you cant, use sudo nautilus.
The b method is to use sudo chown -R yourmane fileorfolder
THat will bring that folder or file under  your control.

To make a file executable, chmod +x filename

Welcome to ubuntu!

---

### Post by Michael.Godawski on 2008-04-27
Here are some sites about planning partitions and such:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by southernman on 2008-04-27
> So the question is what is the difference between primary and logical?You can only have 4 primary partitions. 

If you use one "extended" partition (not given the option in installer, ubuntu sets them up automatically if you choose to have even one logical setup), you could feasibly setup more partitions than you'd care to... 64 or 254 of them I think but maybe that's misinformation on that number. Either way, you'll be able to use more than you'll care to setup.

So you could have

4 primary
sda1, sda2, sda3, and sda4

or 

3 primary and one extended (extended contains logicals) logical right? ;)
sda1, sda2, sda3 <--- all primary
sda4 <--- is your extended
sda5, sda6, sda7, sda8, sda9 and so on <---- is your logical partitions.

Clear as mud now, right?

###############

As for your partitioning scheme, this is how I do mine. Future upgrades don't affect my personal data (movies, music, business stuff) or my home partition.

sda1 = 100MB (setup as /boot)
sda2 = 10GB (setup as /)
sda3 = 7GB (setup as /home)
sda4 = extended
-- sda5 = 200GB (setup as /media/multimedia)
-- sda6 = 10GB (setup as /media/business)
-- sda7 = 1GB (setup as swap)

That's on a 250GB drive and gives me a little padding.

> Should keep all primary or only / as primary?It's totally a personal preference. Makes no difference how you setup your partitions. I keep the /boot separate and in front cause it's been drilled into me to do it this way by my linux users group.

I keep my swap at the end of the drive, and yes... more than 1gb, even if you have 4gb of psychical ram is more than enough. I run 2GB + 1GB swap. My swap never gets used... well barely any of it.

> 2) I made a partition /adnan for store data because in future, clean install won’t need to delete data from this partition. The problem is I can’t write anything in this partition as it is say “Owner: root”. So how can I write something in this partition as root? Quite simply, it's because you mounted it in the root (/) folder. It should be in /media/adnan and assigned as your /home partition maybe? your call. I strongly advise a separate /home partition though.

> Is there any good tutorial for command lines?

Yes... see here for one place to go:
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

A quick google on changing permissions will net you 1000's of hits. Take your pick.

Have fun, enjoy your ride on Ubuntu and Welcome!

---

### Post by vanadium on 2008-04-27
> 2) I made a partition /adnan for store data because in future, clean install won’t need to delete data from this partition. The problem is I can’t write anything in this partition as it is say “Owner: root”. So how can I write something in this partition as root?
Quite simply, it's because you mounted it in the root (/) folder. It should be in /media/adnan and assigned as your /home partition maybe? your call. I strongly advise a separate /home partition though.

You can mount your partitions where you want. The only issue here is that you need to set the proper permissions of the mount point or add the appropriate mount options in your /etc/fstab file. 

That said, conventionally, partitions are mounted under /mnt, and in Ubuntu under /media, and that is how I would do it.

Concerning the permissions, I consider it better practice to leave the mount poitn to the root, but create directories in the mounted volume, which are then given to the users of the system. You can then link to these partitions from within the home directory of the user. This way, the user must worry where the volume is actually mounted and he can access the drive space straight from within his home directory (no need to explore the system outside of his home!).

---

### Post by southernman on 2008-04-27
> **vanadium said:**
> You can mount your partitions where you want. The only issue here is that you need to set the proper permissions of the mount point or add the appropriate mount options in your /etc/fstab file. 

Yeah, I partially flubbed what I meant to say and actually said.

I meant to include that I mount the /home directory, on it's own partition. However, I still leave it under root. (/home/username)


as for the /adnan directory, which is where I assume you want to keep personal files that are not pertinent to your /home directory, like movies, business stuff and the like... Yes, the ubuntu way is to mount it to /media/adnan. Technically, you can put it any where you like as long as you set the permissions and your fstab file correctly.

---

### Post by adnansanni on 2008-04-27
Fast of all, thanks to you all for your help. These are very quick reply that I didn&#8217;t expect. Now I clear what I asked before. 
@southernman, thanks bro for your detail. Now I&#8217;m really clear as mud. :)

---

### Post by adnansanni on 2008-04-27
I have another question; I think it is best to ask her instant open a other thread.
What should I choose keyboard layout? 
Is USA> USA or USA> International (with/AltGr dead keys) or something else? 
What is the dead key? Is this layout could be change after install?
Mine laptop is Asus A6F.

---

### Post by Rrory on 2008-04-27
I am a true true noob; so please speak in easy language;-)

I had my computer, a toshiba partitioned, and tried to install Heron, from a live CD I burned, it wants to resize the partition (fine) but when I try to do so it stops with the message 'no root file system is defined' I have no idea what this means or what to do... heeeelp
  Rory

---

### Post by vanadium on 2008-04-27
Dear people, new problem = new thread.

---

### Post by adnansanni on 2008-04-27
Hey guys.
I&#8217;ve partitioned and mount as /media/adnan with clean install but it isn&#8217;t work, it still shows &#8220;owner: root&#8221; so I can&#8217;t write anything there.
I figure out to work with:
sudo nautilus /media/adnan
But why it&#8217;s happen? Is anybody has idea?

---

### Post by vanadium on 2008-04-28
Try the following

* Load nautilus with root permissions with following command from the terminal (or alt+F2): gksudo nautilus
* Navigate to your /media/adnan
* Create a directory there, named "data" (or any name you choose)
* Right-click the directory and change the owner to your username.
* Right-click the directory and select "Make Link". This creates a link in the current directory with the name "Link to data"
* Move this link to your home directory. There, rename it to "data"
* Close your gksudo nautilus instance as soon as you are done.

Now you will be able as a normal user to access the partition from within your home directory with full read and write permissions by navigating to the data directory in your home directory.

This is really how this should be done in unix/Linux.

---

