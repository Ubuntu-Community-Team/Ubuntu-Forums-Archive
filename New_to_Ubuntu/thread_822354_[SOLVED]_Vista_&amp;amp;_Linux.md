---
title: "[SOLVED] Vista &amp;amp; Linux"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Dutch70 on 2008-06-08
Hello, 
 
 I am running on the Live CD right now(until marked solved), trying to get up my nerve to finish this Ubuntu install via gparted. 

I used Vista to shrink the hdd. and then let the live cd do its thing to install. This is the current set up. ....(I tried sceen shot...sorry)

              *********************************************

dev/sda1...........ntfs-(vista)..........229.70 GiB 

dev/sda2...........extended-..............96.30 GiB 
..dev/sda5.........ext3...................92.43 GiB
..dev/sda6.........linux-swap..............3.96 GiB...(2GB RAM)

dev/sda3...........ntfs-(Factory Image)....9.35 GiB  

               *****************************************

 I need help setting up my "home" partition, just a little guidance if you dont mind sharing your knowledge or experience on this, I dont fully understand the home and all that, not too concerned about dual booting right now, or should I be? any advice on operating gparted? linux terminology is very new to me. 

Thanks

---

### Post by kamaji792 on 2008-06-08
"home" is like Window "Documents and Settings" directory.

So it will have a directory for each user and that directory will contain all there personal setup files and data files.  You usually want a fair bit of space for this.

---

### Post by UnWarierMage224 on 2008-06-08
Personally, I would create a separate partition for the /home directory. 

/home in Linux is basically the equivalent of My Documents in windows... it's where your user profile stores all its stuff (Music, Photos, Videos, etc). You can create home as a folder within your Linux partition but doing so will make it difficult to change from distribution to distribution. From what I've read Ubuntu is pretty frequent with new distributions - new one every six months or so. I am something of a new guy to linux myself so I am just parroting stuff I've read - I have no idea what complications having a separate home partition will create when it comes time to install the next version of Ubuntu. 

gParted is useful for partitioning up your hard drive... I don't understand what you mean by "running gParted"... 

Also, I'm not sure if it will be easy for you to do but I would suggest creating a separate partition for your My Documents folder and moving all your stuff to that partition - that way BOTH Linux and Windows will be able to see it and use it. If you have your My Documents as a folder within your Windows partition you'll have to mount your entire windows partition just to get at your stuff... I would create the extra partition so as to avoid the inadvertent deletion of a critical windows file... just to be extra-safe. 

EDIT: I hardly use my /home directory because I have my My Documents on a separate partition. 

Best, 

-'Mage

---

### Post by Thanatos10 on 2008-06-08
From your description ir appears that Linux is loaded on sda5 and your swap file is on sda6.

Well if Vista well remain your primary OS, I'd suggest EasyBCD to modify your windows boot manager.  Gurb works well, but most folks like to use MS Windows (vista) boot manager.

If you use Grub just accept the default settings and all will be well.  If you choose to use windows boot manager, then press the advanced button on the last setup screen (7 of 7 I believe).  There you'll direct Grub to load on sda5.

Either way, both will work well for you.  Just some people who are just experimenting with Linux don't want to mess with their MBR.

If I confused you let me know and I'll try to answer your questions.  Let us know how it works out for you.

---

### Post by Dutch70 on 2008-06-08
I am ok with it booting to Ubuntu, and I can always change that later, correct?
 use grub?, does that mean boot to linux? 
windows boot manager? I'm running on the live cd(Ubuntu) now. with gparted opened and dont know where to start...lol, or what button to push first.

windows "documents and settings" ha, noob at windows too!

about creating a partition for a "my documents folder" so I can access things like music and pics from vista and linux, is this something I can do after I get my home partition done?

edit: I can take screenshots, are they easy to post? and How?.

---

### Post by Dutch70 on 2008-06-08
I am ready to resize the sda5 partition, should I use free space preceding or following, and 20GB is that about right? and would that be 20000 MiB?

---

### Post by bumanie on 2008-06-08
You seem to have done pre-reading which is good. I personally would just format the drive (where there is no other OS/restore partition) to ext3 and choose manual at the partitioning stage of the installation. Good pratice is to have 10g /; 1-2g swap and the rest can be allocated to /home, which is where you data will get stored. I can understand your apprehension if you haven't done a ubuntu install before, but the partitioning stage, even in manual mode, is not hard, one just needs to be careful. It certainly is no harder than what you are trying to now, ie pre-partitioning. However you decide to tackle this, welcome to ubuntu and I hope all goes well. Post again if you have any queries. Doing the partioning at the installation stage is a better way to go in my opinion, but that is entirely up to you. As long as you don't alter your vista partitions, if it doesn't come out right the first time, you can do another install.

---

### Post by Dutch70 on 2008-06-08
linux is already installed, I have just booted to the live cd so that I am not mounted to the Partition that I am working on. see my current partitions in the first post, 

to create the space for the new partition w/gparted should I choose free space preceding or free space following. and would it be 20,000 MiB for 20GB.

wish I knew how to post screenshots

---

### Post by bumanie on 2008-06-08
OK, I missed that. 
Hmm, making a /home partition once already installed is a convaluted process, I think. Any way you can tackle that when it comes. 
20,000 mb is approximately 20gb - the partition will effectively be slightly smaller due to quirks of how mb and gb etc are rounded to the nearest thousand. As for where to have the unallocated space, it doesn't really matter as linux will boot from any partition. For sake of comformity, I always put / before /home, followed by swap, but as said it doesn't really matter, especially in your case as you are going to 'fill' the unallocated space with your new /home partition, right? Correct me if I'm on the wrong track. I would choose 'after.'

---

### Post by Sef on 2008-06-08
> ..dev/sda6.........linux-swap..............3.96 GiB...(2GB RAM)

Swap should not be more than 1 GB.  1 1/2 or 2 times was appropriate when ram was 768 or less.  At and after 1 GB ram, swap should only be 1 GB.  I have 2 GB ram  with 1 GB swap, and really don't need the swap.  I could do away with it and still run just fine.

---

### Post by Dutch70 on 2008-06-08
Hi, you are on the right track now...lol 

 do you think 20gb is overkill 


edit...wont let me resize the swap

---

### Post by bumanie on 2008-06-08
10gb for / should be ample. My / contains about 5.5gb on a fully configured system. My / is 10 gb.

---

### Post by Dutch70 on 2008-06-08
OK Great, I am ready to start that then, but before I do, What should I do with that 4GB swap file, option to resize is greyed out, so is it a use it or lose it deal, and if so will it hurt to use it, 

how do you post a screenshot, I already have it taken, then you could see my configuration.

btw, sure is nice to have help at times like these....Thanks to everyone!

---

### Post by Sealbhach on 2008-06-08
> **Dutch70 said:**
> 

how do you post a screenshot, I already have it taken, then you could see my configuration.

I upload the picture to [www.tinypic.com](www.tinypic.com) and then paste a link to there.

Have you looked at this?

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)


Also, this might help?

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


Good luck!

.

---

### Post by bumanie on 2008-06-08
It seems that even though you are operating off the live cd, the swap must be mounted. I read that this sometimes happens. Try right clicking on the swap partition from gparted (on the live cd) and you should have the option of choosing 'swapoff', then you should be able to resize it. After that go ahead and I guess add the former swap space to /home.

---

### Post by Dutch70 on 2008-06-08
ok swap is off now, Im gonna shrink it to 2gb as soon as I post this, how do I add it to home?

edit...wow it did that instanly

---

### Post by bumanie on 2008-06-08
By resizing/moving partitions as you've been doing. You may have to move/resize more than one partition. You could leave it unallocated if you wish, especially if you are happy with the space you have allocated to /home

---

### Post by Dutch70 on 2008-06-08
I havent created home yet, I think I am going to go with 15 GB on that, is there no way for me to make use of that 2 GB of unallocated space?.....short answer please

maybe use it to xfer files to and from vista, by making it ntfs???

---

### Post by bumanie on 2008-06-08
Hard to say when I can't see things, but by moving/sliding partitions, you should be able to use the space, as long as you are only changing things within the extended partition.

---

### Post by Dutch70 on 2008-06-08
I see what you mean,
 sorry for all the little questions, just a little nervous, everything has went so perfect so far. I dont want to goof it up now. I do see why it is better to do this when you first install it, but as you can see, I needed internet access while doing it, so in that instance this is much better.

---

### Post by bumanie on 2008-06-08
May be you have done this, but you should save any important data as partitioning sometimes does go wrong - even if there is momentary power interruption during the process, that will leave you with an useable file sytem on that partition. Don't worry about the questions, happy to help, but it can be hard when one has no visual to assist. I don't want to make a mistake and wreck things for you.

---

### Post by Dutch70 on 2008-06-08
uh oh,

1.)  I just created the home partition 15gb, and it made it ext2 when I     told it ext3, what do I do about that?

2.)  It said there is 4 warnings and trying to save it to the root folder...is it ok to save it there, especiallt using the live cd?
 
 3.) It put the new partition between sda5 and sda6, and it is labeled 
"new partition #1"...will that change when I close all these windows?

I have everything saved/backed up, just wanted to get this done so I can go break something...lol...jk

---

### Post by bumanie on 2008-06-08
Despite the time we have spent on this, as you have everything backed up, do you feel like doing a fresh install? I think it will be quicker and easier. 
Format to ext2 doesn't really matter, it can be converted to ext3 easily, I believe. The other two, I'm not sure about - warnings are not exactly positive, but not necessarily negative either.

---

### Post by Dutch70 on 2008-06-08
I have all the time in the world, but no idea how to even begin that from here as I have just been following steps one at a time, but if you are going to lead the way, lets go for it. Just be more experience for me to help other people with.

should I upload a screenshot so you can get a visual of my partitions?

---

### Post by bumanie on 2008-06-08
As I said way back, as long as you ensure you don't alter any vista partitions, there is no real damage you can do, especially as you have your important data backed up. You can try what you have now and see what happens - may be it will work, may be it won't. If you do try and it doesn't come out well, we can do a fresh install as described in my original answer to you when I didn't realise ubuntu was already installed. Just to reinforce the message - double check no vista partitions are involved before doing anything permanent.

---

### Post by Dutch70 on 2008-06-08
ok, I went through with the partitioning, everything looks good, Now I just need to figure out how to get everything to my home, and I'll be finished...I think!

How in the world should i go about doing that? here are the partitions now.

sda1- vista
sda3- vista....both are untouched.

ubuntu
sda2-   extended 96gb
...sda5   ext3.. 80gb....the one that I cut home out of
...sda7   ext3.. 15gb....new empty partition

...sda6 - swap file

i keep reading about hda...what is that. this is the site I am using, (toward the bottom) terminal commands.

---

### Post by bumanie on 2008-06-08
hda previously denoted ide drives. Have noticed in the last while that (at least on my computer) that all drives are denoted sda, sdb.... etc whether they are ide or sata. Which partition are you planning to have as /home? sda5 I guess?

---

### Post by Dutch70 on 2008-06-08
sorry, I haven't been able to post...security mismatch or something.

 I am just stuck, keep in mind, that I am totally new to computers period, about 4 mnths of windows. to sum it up, I just cut the partition that ubuntu is installed on and created a smaller 15 gb partition for home, it is empty, and I dont have a clue what I am supposed to be doing next.

here is the link I am following...[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) if thats any help. I dont really know how to enter those codes, you cant copy and paste, I tried that.

---

### Post by Dutch70 on 2008-06-08
Please understand I have about 6 pages open reviewing what ia have read and lookingfor more info, but I really dont understand this whole home thing, or documents and settings for that matter, I know what it looks like, but thats about it.If someone could help me with this last step I would be very greatful.

---

### Post by Paqman on 2008-06-08
> **Dutch70 said:**
> 
here is the link I am following...[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) if thats any help. I dont really know how to enter those codes, you cant copy and paste, I tried that.

You should be able to copy and paste any of that into your terminal window.

Incidentally, on linux you can just highlight to copy then tap the mouse wheel/middle button to paste. It's a lot quicker.

---

### Post by starcannon on 2008-06-08
+1 to creating a seperate /home partition, this should in my opinion be part of the default partitioning scheme, or at least offered as a wizard choice without having to have a new linux user go through manual partitioning (which isn't hard after you've done it once)

---

### Post by Dutch70 on 2008-06-08
first time i tried that, I thought I was going to put it in the terminal and then change the drive letters to match mine...(sda as opposed to hda) which is what is in that cade, but when I pasted it, it instanly said not found. I can try pasting it in a note first and then diong it. 

 Do I need to take out the live cd and boot normally to do it?

---

### Post by sam_delta on 2008-06-08
> **Sef said:**
> Swap should not be more than 1 GB.  1 1/2 or 2 times was appropriate when ram was 768 or less.  At and after 1 GB ram, swap should only be 1 GB.  I have 2 GB ram  with 1 GB swap, and really don't need the swap.  I could do away with it and still run just fine.

ive heard you need your swap to be at least your ram to hibernate, is that true?  it makes perfect sense since the os copy everything in the memory to the swap before cutting power...

sam

---

### Post by sam_delta on 2008-06-08
time  to give this guy a quick and good explanation about ubuntu system and separate /home partition

alrigh man lets start

ubuntu linux system consists of a set of directories and files that in fact are the whole system. those directories and files are commonly known/refered as "root" "/" "system" and so on. within your linux system, theres a folder called "/home" folder, this folder contains your personal information/files, that means that all your music, videos, documents, multimedia, settings flies that are of YOURS, are stored in this /home folder, everything outside this folder are "system files" located at "/" or root. This "/home folder" is actually a folder located inside "/" or "root folder" or "system" whatever you want to call it, BUT it is posible to make a separate partition for this own folder. so all the files and personal info/files you have on home, are in their own partition.... the good thing about having them in their own partition, is that you can reinstall ubuntu system files WITHOUT EVEN TOUCHING your personal files, that means that if you want to reinstall or for some reason your system get broken or you simply want to move to a newer ubuntu version, you can simply reinstall "/" or "root" without loosing all your settings/personal info which are in a separate partition than the system files.


i hope you get a better understanding on why a separate home, and what it does, any debts, post em here, i think you cannot find a better constumer support than ubuntu forums hahahah :) 

sam

---

### Post by Dutch70 on 2008-06-09
Thats just what I was looking for, between XP & Vista mixed tutorials and different booting methods, it all just became a big blur. 

 and yeah, I have many debts, might as well finish me off and educate me on the proper way to pay a debt to the wonderful people here at the ubuntu forums. such as...

bumanie
Paqman
Sef
Sealbhach
starcannon
sam_delta

 So the story goes basically, I have been finished for a long time, and didn't even know it...hahaha, can t wait to look back on this in about a year...

Thanks again everyone!

---

