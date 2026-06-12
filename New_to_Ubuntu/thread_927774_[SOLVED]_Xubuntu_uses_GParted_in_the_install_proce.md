---
title: "[SOLVED] Xubuntu uses GParted in the install procedure?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by meindian523 on 2008-09-23
Does Xubuntu use GParted for disk partitioning in the install process?

I ask because I lent a friend an Xubuntu 8.04 CD to allow him to rescue data from his P3,128MB RAM machine,but I'm unsure whether Xubuntu uses GParted to do partitioning operations,and if it is not GParted,or the partitioner used in the Ubuntu install process,I'm unsure whether I can guide him through partitioning,which he can't do himself,because he is a Windows user,and knows very little about computers.

---

### Post by snowpine on 2008-09-23
> **meindian523 said:**
> Does Xubuntu use GParted for disk partitioning in the install process?

I ask because I lent a friend an Xubuntu 8.04 CD to allow him to rescue data from his P3,128MB RAM machine,but I'm unsure whether Xubuntu uses GParted to do partitioning operations,and if it is not GParted,or the partitioner used in the Ubuntu install process,I'm unsure whether I can guide him through partitioning,which he can't do himself,because he is a Windows user,and knows very little about computers.

Yes, the Xubuntu Live CD includes GParted. (It's in the Applications->System menu as Partition Editor if I remember correctly.)

---

### Post by meindian523 on 2008-09-23
That's ok,but does it incorporate it into the install process?Or could I prepare the partition beforehand and allow Xubuntu to ladle itself into that plate? :-P

---

### Post by kansasnoob on 2008-09-23
> **meindian523 said:**
> That's ok,but does it incorporate it into the install process?Or could I prepare the partition beforehand and allow Xubuntu to ladle itself into that plate?:P

Yes. That's my preferred method of simple installation. I just free up at least 10GB of space (as little as 6 GB would work), don't format it at all, and then choose: Guided - use the largest continuous free space.

Then the installer just does it's thing.

---

### Post by meindian523 on 2008-09-23
Have you done that in Xubuntu,kansasnoob?

---

### Post by snowpine on 2008-09-23
If you are helping your friend with data recovery, installing Xubuntu will over-write the data he's trying to recover. :-)

Also, according to xubuntu.org, you can run the Live CD with 128mb of ram (for example to run gparted) but you need 192mb to install. You need the Alternate CD (which does not have a Live CD mode) to install with 128mb, and I would certainly recommend 256mb for good performance. 

So I'm confused what your question is; are you trying to help your friend get the data off his old computer (in which case there is no need to install), or to get the computer up and running with a Linux OS (in which case Xubuntu is not a good choice)?

---

### Post by meindian523 on 2008-09-23
The situation is that he has two partitions,of which one holds all his data,so that's what I'm trying to help him recover,because,presently there's no functional OS on his box.

I was thinking of also allowing him to install it,because I want to rescue it from becoming landfill,because he has bought a new box anyway,but presently it's looking like installing Xubuntu on the old box won't be possible either.

So,I think the way forward is to recover his data,(now the problem is that he doesn't have portable storage at hand...argh,we are going around in circles) and install Xubuntu(if possible) or maybe just tell him to install XP on his old box and be done with it,instead of downloading another distro,in which case Puppy or DSL are probably good choices.

And then we dual boot his new box which has good specs and will be able to handle the GNOME load with all the effects of Compiz.I think that sounds like a plan...any opinions?

---

### Post by snowpine on 2008-09-23
> **meindian523 said:**
> The situation is that he has two partitions,of which one holds all his data,so that's what I'm trying to help him recover,because,presently there's no functional OS on his box.

I was thinking of also allowing him to install it,because I want to rescue it from becoming landfill,because he has bought a new box anyway,but presently it's looking like installing Xubuntu on the old box won't be possible either.

So,I think the way forward is to recover his data,(now the problem is that he doesn't have portable storage at hand...argh,we are going around in circles) and install Xubuntu(if possible) or maybe just tell him to install XP on his old box and be done with it,instead of downloading another distro,in which case Puppy or DSL are probably good choices.

And then we dual boot his new box which has good specs and will be able to handle the GNOME load with all the effects of Compiz.I think that sounds like a plan...any opinions?

Heh, I didn't even notice you have more posts here than I do. :) I'm not saying installing Xubuntu on that machine is *impossible*. It's just that I've seen too many negative reviews of Xubuntu on 128mb systems and I don't want your friend to go around telling people "Xubuntu sucks; I installed it on my old laptop and it was soooo slooooow." 

I like your idea of setting up a dual boot on his new computer. If he still has any use for the old one, my vote is either install something he's familiar with (XP?) or something that will give decent performance (Puppy? Fluxbuntu? Debian+Xfce?). 

Xubuntu Live CD (or maybe GParted Live CD--it is available as a stand-alone ISO) plus a USB drive is a good way to get his data off the old laptop.

Good luck!

---

### Post by meindian523 on 2008-09-23
1]The beans don't matter.If you read the story behind the beans,you would have read the statement,"Many members of the forums with but a few beans can code circles around much of the staff,while some of us with huge collections of beans would be happy if they could give a helpful answer on occasion" in so many words.

2]It's a desktop.

3]I think we might go with XP,because he plans to use it in the business his father owns,and Daddy dearest needs Tally.So we need something that's familiar.

4]I can't conceive of a plan to recover data using the GParted CD,could you explain?

5]So,this effectively means I need to wait till his USB drive comes back,he's lent it to a friend.If he installs Xubuntu in the meantime,no problems,and he was mentioning that he would get an XP CD tomorrow(pirated,but of course),so I think we will use that for installing.

6]Thanks for the wishes.

---

### Post by snowpine on 2008-09-23
You can use GParted to copy the entire partition bit-by-bit from his hard drive to the USB drive, then sort through the files at your leisure using a faster computer.

Or, your original plan is good too. Get Xubuntu running, then mount the data partition and use Thunar file manager to copy selected files and folders to the USB drive. 

Whatever method you think will be easiest and most familiar. I recommend backing up the data before installing any OS (Linux or Windows) to eliminate the risk of overwriting the data partition during installation.

---

### Post by kansasnoob on 2008-09-23
> **meindian523 said:**
> Have you done that in Xubuntu,kansasnoob?

Yes. The installer works just like Ubuntu. Just boot the live CD (run without changes to computer), then go to gparted (aka: partition editor), shrink Windows as little as 6GB (I'd prefer 10Gb to allow for file manipulation, etc). Then just leave that free space completely unformatted (greyed out) and you should get four choices from the installer:

Guided resize and use freed space
Guided - use entire disk
Guided - use the largest continuous free space
Manual

Just be sure you choose: Guided - use the largest continuous free space.

---

### Post by meindian523 on 2008-09-23
Good.But,the installation plan has been shelved because the box has only 128 MB RAM,while 192 MB is required for installation.Still,it's good to know.

---

### Post by snowpine on 2008-09-23
> **meindian523 said:**
> Good.But,the installation plan has been shelved because the box has only 128 MB RAM,while 192 MB is required for installation.Still,it's good to know.

Just so there's no confusion, here is the "official" answer from xubuntu.org/get

> (Xubuntu 8.04) Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

---

### Post by meindian523 on 2008-09-23
Isn't there an option to run just the installer?Not using the Live session?There is such an option on the Ubuntu Live CD.I guess 128MB RAM should be enough to run just the installer.

---

### Post by snowpine on 2008-09-23
> **meindian523 said:**
> Isn't there an option to run just the installer?Not using the Live session?There is such an option on the Ubuntu Live CD.I guess 128MB RAM should be enough to run just the installer.

You can use the Alternate CD to run a text-based installer that requires less ram.

---

### Post by meindian523 on 2008-09-23
I meant an option in the Live CD,not the Alternate CD.The option I'm speaking of is available as "Install Ubuntu" on the Ubuntu Live CD,it runs only the installer,ubiquity.

---

### Post by snowpine on 2008-09-23
> **meindian523 said:**
> I meant an option in the Live CD,not the Alternate CD.The option I'm speaking of is available as "Install Ubuntu" on the Ubuntu Live CD,it runs only the installer,ubiquity.

It's been a little while since I last installed Xubuntu, but yes I believe it does, just like the Ubuntu Live CD.

---

### Post by snowpine on 2008-09-23
I found this page for you, it has some nice screen shots:

[http://gdisauro.com/2008/05/xubuntu-hardy-installation/](http://gdisauro.com/2008/05/xubuntu-hardy-installation/)

:)

---

### Post by meindian523 on 2008-09-24
Never mind,my friend returned Xubuntu to me without touching it,as happens with almost all bravado-filled "I'll try it out myself" claims.

---

