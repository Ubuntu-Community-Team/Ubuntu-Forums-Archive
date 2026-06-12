---
title: "[SOLVED] Just created home, now what?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Dutch70 on 2008-06-08
Hello, I am still on the live cd, I just used gparted to create a 15gb partition for home, now what do I do?... What goes there?, and how do I put it there?

dev/sda5-80gb is the drive I cut, and sda7-15gb is the new empty one, now that I have it. what do I do with it?


 I have studied endlessly, but as I am new to PC's perioid, I really dont understand..... docs and settings in windows either for that matter. I would really appreciate a little guidance if you dont mind. Thanks for taking the time to read my post.

---

### Post by fhmanas on 2008-06-08
Why did you create a home directory?  You should mount that partition to be able to access it.

If your intention is to try Ubuntu, why don't you just install Ubuntu on the partition you created and dual-boot.  Any configuration you make with the Live CD will not be stored even if you save it in the 'home' partition.

If you don't want dual-booting, install Ubuntu in a Virtual Machine, you can use either VirtualBox or VMWare, I use VirtualBox as it has lower overhead in Windows.

BTW, the live cd already has it's own limited home directory stored in RAM, not really useful.

---

### Post by Dutch70 on 2008-06-08
I installed ubuntu about 3-4 days ago, I am just using the live cd to try and create the home directory so I can do a fresh install when new versions come out, not just trying ubuntu, I am determined to have it on here permanenlty, 
 
 I dont understand the whole concept of dual booting. I have researched many sites, but I am undecided on how I am going to combine linux and vista music and pics and such. So do I need to take the live cd out and boot up to where I have linux installed in order to finish,

---

### Post by Paqman on 2008-06-08
> **Dutch70 said:**
> What goes there?, and how do I put it there?


The point of a home partition is to be able to mount your /home folder there. /home contains all of your personal data, and all your settings for your apps. For example, if you customise your desktop, all the changes are stored in /home.

The advantage of it is that it separates the system's info from the user's info. So if you want to reinstall you can just overwrite the system's partition, leaving your settings intact. That's very, very handy.

---

### Post by xravexheavenx on 2008-06-08
I would just dual boot.  A DVD drive can only read so fast and you would get much better performance from it running off the HD.  If you are new to Ubuntu, or Linux alltogether, I would use the built in partitioning tools to resize and install.  ntfs-3g can read off your NTFS partitions unlees you are booting Vista and in that case Vista uses a new partitioning scheme.  Make sure you configure your bootloader right to load both OSes properly and you should have a fully working system.  Always make sure you do your research first though.  You can break something quite easily if you do not know what you are doing.

---

### Post by Sef on 2008-06-08
1) To dual boot from the Live CD - Read [psychocat's tutorial]("http://www.psychocats.net/ubuntu/").  

  -) With Vista, use the Vista partitioner to shrink the Vista partition.

2) To dual boot from the alternate cd and create a create a shared FAT32 partition- Read the [Illustrated Dual Boot's Windows XP + Ubuntu Hardy Heron LTS]("http://users.bigpond.net.au/hermanzone/p3.htm").  Installation is the same with Vista, except for the partitioning issue already mentioned.

---

### Post by Dutch70 on 2008-06-08
I apologize, I didn't explain very well...been at it too long.

 I think I may be starting to understand, in simple terms, now that I have my disk partitioned correctly, all I need to do is boot up to my prior install and move my home folder to my new empty(home) partition.
 
the system is currently installed on the 80gb drive, so I just need to boot up to that drive and then move my home folder to the smaller 15gb drive. and thats it?

I have been following psychocats tutorial, just cant seem to put it together, I know it is something stupid that I am missing, like trying to fix your stereo, and finding out it was the volume knob the whole time. or looking everywhere for your keys, and they're in your pocket. or.., ok thats enough..lol

---

### Post by xravexheavenx on 2008-06-08
Wait a second...  

So, you created a home partition...  Then you intalled ubuntu...  If you set your mountpoints correctly you should be able to access your home directory as if it was the only one there.

---

### Post by Dutch70 on 2008-06-08
No, I shrinked my hhd from within vista, then I put in the live cd and let it install on its own. It created a partition for itself, and a swap, I played on it for a couple of days, and now I want to have that home whatever place, so I can do the upgrades with a fresh install when they come out, thats all. now I have a fresh new empty spot on my hdd for that. but confused about the next step,

---

### Post by xravexheavenx on 2008-06-08
First off, you will be able to upgrade without having to download the iso for the new version all over again.

Secondly, to set the mountpoint, 

mount /dev/<partition label here> /home

---

### Post by Dutch70 on 2008-06-09
well Ive used all my proper search engines and cant seem to find out what "set the mountpoint menas exactly, or why I would want to do that. but i'll keep looking, 

Seems that all I need to do is take this live cd out, boot up to installed ubuntu, and copy and paste my home folder to the newly created partition, does that sound about right?

---

### Post by xravexheavenx on 2008-06-09
You should have no problem with doing that whatsoever.  Unless you set the mountpoint for your /home to hit that new partition, it won't be your actual home location but you can still save files there no problem.  

Also, a mountpoint is the location that tells the kernel where to look for certain devices.  For your example, a hard drive partition.  I searched around and found a better explanation for you here: 
[http://www.gnulamp.com/mountpoint.html](http://www.gnulamp.com/mountpoint.html)

---

### Post by sam_delta on 2008-06-09
time to give this guy a quick and good explanation about ubuntu system and separate /home partition

alrigh man lets start

ubuntu linux system consists of a set of directories and files that in fact are the whole system. those directories and files are commonly known/refered as "root" "/" "system" and so on. within your linux system, theres a folder called "/home" folder, this folder contains your personal information/files, that means that all your music, videos, documents, multimedia, settings flies that are of YOURS, are stored in this /home folder, everything outside this folder are "system files" located at "/" or root. This "/home folder" is actually a folder located inside "/" or "root folder" or "system" whatever you want to call it, BUT it is posible to make a separate partition for this own folder. so all the files and personal info/files you have on home, are in their own partition.... the good thing about having them in their own partition, is that you can reinstall ubuntu system files WITHOUT EVEN TOUCHING your personal files, that means that if you want to reinstall or for some reason your system get broken or you simply want to move to a newer ubuntu version, you can simply reinstall "/" or "root" without loosing all your settings/personal info which are in a separate partition than the system files.

the system files wont take more than 5-10 gigs, but your personal files will probably exceed that, so it is recomended to have 

10gig partition ext3 for your "filesystem" or "root" or "/" 
and the rest you can afford of ext3 for your "/home"

i think that the simplier thing to do right now is reinstall ubuntu, but make sure you click on "manual partitioning" when your installing, so you can select how much space you want your home partition, and how much for your swap and filesystem partitions, and the rest of the work will be done by the installer (all the setup and mountpoints etc, will be done by the installer)

also, dont touch vista's partition, also make sure you do not delete it or mess with it and itll be fine

i hope you get a better understanding on why a separate home, and what it does, any debts, post em here, i think you cannot find a better constumer support than ubuntu forums hahahah


EDIT---- hey i just copied the same info from the past thread + a few more things that i added, i did this because i want sure if you would keep track and read the old thread

sam

---

### Post by Paqman on 2008-06-09
No, you need to edit your /etc/fstab for it to work. Go through the Psychocats tutorial carefully. You can start from the section "Using the new partition", and just substitute your partition numbers.

---

### Post by fhmanas on 2008-06-09
Seems to me, that you are new to the whole linux concept and is more akin to Windows.  Please tell us your proficiency in linux so we can properly describe what we want you to do and not assume that you know.

In any case, as sam_delta has explained linux is basically a system of directories (folders in Win) including all the devices, ie. cdrom, usb, printers, video, etc.  They all appear as directories, I know this is confusing coming from Win, but eventually this will be all clear to you.

Any way, /home is basically the Documents and Settings folder in Win. If your installation is still new, it would be easier if you reformat and do manual partition set your mountpoints the way you want it.

BTW, mountpoints are basically a term to point to the mounted device.

---

### Post by steve101101 on 2008-06-09
install ubuntu with windows. This will allows you to delete ubuntu just like any windows program if you want, but will also set up duel booting without any issues. This is what i have done and it has worked perfectly. Just pop the ubuntu disk when windows is running and double click the disk to run the autorunner. 

if you have any questions send me a private message

---

### Post by Dutch70 on 2008-06-09
Ok, this doesnt liik good, after researching all the info I have been given, and I have to say thanks again to everyone! 

 Appearently, when I partitioned my disk, in order to create /home ,I didnt make it big enough, 15 GiB, thinking that this was where I was going to move "/" to that smaller partition...(yeah, yeah, I know) so, essentially, I have them backwards now, so even if I point /home to the new partition, I will be pointing it at 15GiB, and leaving "/" in an 80GiB partition. I certainly dont need to explain how stupid that is...not much in the mood to ask anymore stupid questions right now.So I am going to go do some research on that little problem, and what my options are now, so if you have any suggestions, please share, and I'll check back here from time to time, thanks again.

---

### Post by philinux on 2008-06-09
You can resize them with the live cd. Root needs about 10 gig or less.

---

### Post by Dutch70 on 2008-06-10
Well I believe I've got it, 
 I deleted that 15GB partition and then grew my "/" partition back to full size just to be sure, then I created the 80GB partition for /home. so "/" is in the 15GB part. now. I did all that with gparted though, then I reinstalled everything for a fresh start, and another oppurtunity to learn haha, not only about partitioning and installing, but also about how to search for the info I need.  

 Have to give mention of sam_delta for taking me to school on "/" and /home. Thats why I couldn't ask my question properly so that everyone could understand what I was asking clearly. this is truly embarrassing. My initiation I guess.

That plus the info and links everyone gave me helped to get it figured out. 

I apologize for being so difficult, its hard not to when you don't even know what it is you don't know...ok gotta go get it updated now....Thanks very, very much to everyone!

---

### Post by sam_delta on 2008-06-10
hey, im glad your now up and running, dont worry about the questions, thats why we are here for, we want and enjoy helping people, and we want people to know ubuntu and enjoy it at its full. hows people supposed to enjoy ubuntu if they dont even know how it works?, thats why we are here.  

anytime you have questions, feel free to post, theres no 'stupid' questions

enjoy ubuntu bro
sam

---

### Post by bumanie on 2008-06-10
Hi Dutch70, today, I've come in at the end of your trials, rather than near the start. It's good that you got everything working. In one sense you did this the hard way, which sometimes is the best way because it stretches your skills and helps one learn. Hope everything works from now on.

---

