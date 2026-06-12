---
title: "Partition Strategies"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Rad1 on 2008-07-26
hi.

i bought a new 160-gig drive for my laptop, so i could install ubuntu.

already d/l'ed and burned iso to CD.

reading up on partitioning strategies.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

currently have single 18-gig ext3 partition, but after reading psycho, seems i should also make /home partition .. for reasons he outlines.

my question > If i have 18 gigs to play with .. how much should be / and how much /home?

psycho says "5-10" for / 

does 9 + 9 sound right? (/ and /home)

here is screen shot of my current drive.

also, does the swap being way by itself at the end lead to problems?

i could shrink the C drive from the outside, to make more room for ext3, but i'd rather not, unless absoluetly necessary.

what would be the best utility to bust up that ext3 partition into two parts?

[IMG]http://radified.com/gfx4/linux_partitions.gif[/IMG]

---

### Post by SunnyRabbiera on 2008-07-26
with so many partitions I dont reccomend a separate home partition as there is a limit.
Your partitioning scheme doesnt seem like that good of an idea sorry to say.

---

### Post by Rad1 on 2008-07-26
> as there is a limit
what limit are you talking about? 

the 4 primary partition limit?

i won't exceed that.

> Your partitioning scheme doesnt seem like that good of an idea 
what would you recommend?

---

### Post by boblemur on 2008-07-26
/ is your file system it holds everything within it, its perfectly fine to keep /home as just another folder within your filesystem

however, sepperating /home allows you to reformat your filesystem without affecting your settings (most of them) and your programs prefrences. /home is basily the linux equivelant to "My Documents" however it also stores alot more of your settings in it than windows does in my docs.

i think its a good idea to sepperate them but with that little space its going to be quite hard, is their any specific reason why you need to have f: and d: separated? because if you were to have them joined and especialy because d: is rarther empty, you chould use 8gb for / then the rest of the ext3 and however much more of D: you would like to dedicate, however i dont like keeping alot of my data on the /home parition if i oftern use windows, because it means that your data is restricted to linux only ( windows wont read ext3 by default) however if you keep all your data on a large ntfs partition you can use that to share between the opperating system (this too has its probs)

but their is no real need to separate / from /home unless you frequently reformat (like if you are trying different types of ubuntu, or you try developing software

but if you do reformat the entire drive ever keep in mind its better to sepperate /home for safty

---

### Post by Rad1 on 2008-07-26
> however, sepperating /home allows you to reformat your filesystem without affecting your settings (most of them) and your programs prefrences.
yes, i know. Configuring system settings each time is what suks about reformatting and reinstalling. Which is why the idea of separate /home is so attractive.

> is their any specific reason why you need to have f: and d: separated? because if you were to have them joined and especialy because d: is rarther empty, you chould use 8gb for / then the rest of the ext3 
i don't follow you. i already have 18 gigs.
or are you suggesting I use the D_drive (ntfs) for /home?
18 gigs is not enough space for a ubuntu install?

---

### Post by boblemur on 2008-07-26
i personaly setup separate / and /home all the time 

because of this, but cause im messing around with ubuntu alot and i oftern reformat

but its hard to redo your partitions at this point, if you want you can but you should backup your /home folder(carefull of not losing permissions and ownership when you do this..) and then boot into the live cd and i think you will need to reinstall ubuntu but i could be wrong

---

### Post by boblemur on 2008-07-26
not the whole thing but yes it might be a reasonable idea, your filesystem should take up more than 9gb ever but depending on what you are wanting to keep in home 9gb might not be enough

but its upto you, 9 + 9 is fine but home may get a little cramped

---

### Post by wrtpeeps on 2008-07-26
Personally, mine is setup as:

/boot - 65mb - ext2
swap - 4gb
/ - 20gb - ext3
/home - 160gb  - ext3

---

### Post by DGortze380 on 2008-07-26
Why so many partitions? One for Windows, One for / , One for /home, one for swap, and an NTFS Data Share.

---

### Post by Rad1 on 2008-07-26
> but its hard to redo your partitions at this point, if you want you can but you should backup your /home folder(carefull of not losing permissions and ownership when you do this..)
There is nothing on the ext3 partition. I have not yet installed Ubuntu. That's why I'm asking now.

---

### Post by Rad1 on 2008-07-26
> Why so many partitions? One for Windows, One for / , One for /home, one for swap, and an NTFS Data Share.
I use one partition to store my back-up image clones of WXP system partition, and another to do test-installs of beta O/S'es

Do those two extra partitions hurt anything?

---

### Post by DGortze380 on 2008-07-26
> **Rad1 said:**
> I use one to hold my back-up image clones of WXP system partition, and another to do test-installs of beta O/S'es

Do those two extra partitions hurt anything?

No not if you feel you need them. Seems like a lot to me but w/e. Side note, I would not keep my backups on the same disk as my install. If the disk fails your $crewed.

---

### Post by Rad1 on 2008-07-26
> Side note, I would not keep my backups on the same disk as my install. If the disk fails your $crewed.
Yes, thank you. Learned that the hard way. I *do* periodically transfer to external drive.

---

### Post by Yannick Le Saint kyncani on 2008-07-26
> **Rad1 said:**
> my question > If i have 18 gigs to play with .. how much should be / and how much /home?

Hi, Rad1. As boblemur said, if you have only 18G to play with, I would not create separate / and /home partitions as :

- it would be impossible to remove some data if you need to install a program and don't have any more space on /

- or on the opposite you could not easily use free space on / if your /home is full.

Beside, as of 8.04 hardy, you can reinstall and keep /home intact.

---

### Post by Rad1 on 2008-07-26
Anybody see a problem with using D_drive (NTFS) as /home, and also for some Windows file storage?

That would give me 18 gigs for / and 20-25 for /home.

---

### Post by boblemur on 2008-07-26
ohh right ok, well yes you should now if you have the chance make it 9 + 9 is prob best, however i still dont see why you need to many windows partitions, should you not have c: and then data? and why the strange order?

---

### Post by Rad1 on 2008-07-26
> however i still dont see why you need to many windows partitions, should you not have c: and then data? and why the strange order?
I answered this above. (Reply #11.) You must've missed it. What "strange order" are you referring to?

---

### Post by boblemur on 2008-07-26
yeh this is not really a good idea, because in linux you will see your data and your home files however in windows you will get all the hidden files that linux makes for its settings but windows will  not recognise them as hidden so you will get a whole lot of junk folders in windows.

---

### Post by boblemur on 2008-07-26
just the c: and then linux then windows drives then linux swap and then windows fat?

its a strange order to have your paritions in, makes no real diffrence except if you say run out of space on c or something you cant eat some of your data because linux is right their...

---

### Post by Rad1 on 2008-07-26
> makes no real diffrence except if you say run out of space on c or something you cant eat some of your data because linux is right their
40 gigs is *more* than enough room for Windows XP.

And I can always shuttle data to the D_drive (25 gigs) or F_drive (65 gigs) .. if necessary (which it won't be).

I am very familiar with partitioning for Windows. That's not what I need help with. I'm asking about what I need for Linux.

---

### Post by boblemur on 2008-07-26
thats not necessrialy true, i have been using xp for a long time and my program files oftern fills 40gb, im just saying...

either way splitting that ext3 parition would be a good idea unless you plan on installing something like steam then it would be better to keep them together

---

### Post by Rad1 on 2008-07-26
> thats not necessrialy true, i have been using xp for
I'm talking about for me.

---

### Post by Sef on 2008-07-27
> I am very familiar with partitioning for Windows. That's not what I need help with. I'm asking about what I need for Linux.

For Ubuntu, 8 - 10 GB is sufficent.  Also 1 GB swap at the most, and the rest for home.

---

### Post by Rad1 on 2008-07-27
Thanks.

I installed last night. Surprisingly painless.

Tho I have been unable to connect to internet, wirelessly, since that what I use/have.

I've spent several hours trying every combination I can think of .. still no dice. 

Not much I can do with no internet. I'm back in Windows now.

---

