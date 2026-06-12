---
title: "Cannot grasp partition scheme(s) and how swap partition is created in ubuntu 8.04.1"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by cbarnes48 on 2008-09-12
I want to do a Manual installation of Unbunut 8.04.1 so I can partition my single 160GB SATA hard drive more optimally than the Automatic option. However, when I get to step 4 of the manual installation process, I am asked to choose what type and size of partition I want to create.  What is driving me nuts is that when I click on the downward arrow in the Partition Table there is NO swap partition listed!!  :mad::confused:

For a complete newbie, who can't seem to do **anything right** so far, is it even worth the trouble to try to do a manual install?  On this and another forum, I see widely differing opinions.  How am I supposed to know which to believe and follow?

I am also aware that some of the more or most experienced of you get pretty frustrated and/or disgusted with newbies at times and their questions.  What can I tell those of you?  Like I said, although I read what I think is pertinent information that will clear the fog from my head, carrying out and succeeding at the recommended steps is another thing.

Here are three quick examples of exactly what I mean.  One forum member says to skip creating the swap partition altogether.  Reason the member gives:  "...if you have lots of RAM (I have 2GB of SDRAM) there's no need for a swap partition unless you want to use suspend."  My PC is an Acer Aspire desktop, so does this advice even apply?

On the size of the swap space or partition, one forum member states:  "Make swap from 512 megabytes to 1 gigabyte," while another says: "I recommend a swap size that is twice the size of RAM."  This would be 4GB in my case.  A third member said he recommended a "conservative" size of 1 1/2 times the amount of RAM.

Finally, how many and what kinds of partitions make sense?  I'm not looking for a "one size fits all" or perfect answer, here.  Honestly.  However, some well-worn or tested schemes would help greatly.  Here again, I am lost in all the conflicting opinions.  Especially since during a Manual install,, the Partition Table does NOT even list either the /bin or /swap partitions!!

The Table does list ones like /usr, /, /home, /var, and /tmp (I think).  So, how do I choose wisely amongst all these choices?  I don't care how many of your more advanced or knowledgeable members call me a dumbshit or worse.  I would love to be able to work smart and **_not_** so hard, so I could get this damn distro finally installed properly.

Unfortunately, these installation problems I am having are just the tip of the iceberg.  I read one page of documentation from the wiki pages, forum threads/postings, or wherever else and come away with ten more questions.  Work smart, not hard.  An excellent idea or concept.  Not sure I'll ever reach it with this supposedly "user-friendly" distro, though.

cbarnes48

---

### Post by I wanted to leave on 2008-09-12
Hey I'm a NooB but I can answer part of your dilema
When manually partitioning, create the root partition etc, not worrying about selecting partition type at that stage. When you have all partitions in place you can select each one (before going to next screen) and edit each one then. This is where you select partition type. 

Personally I've read its best to not use a swap larger than RAM size, in your case 2GB, however, with that RAM and a further 2GB swap, I don't think you would ever need it unless you know you will. I have a 1GB Ram + 1 GB swap and have had no problems. 

Partition 'lables' are your choice; I use a /home for the purpose of being able to re-install to the root partition without losing data on /home
Hope I've helped you some...

PS - I have found this forum very willing to help Noobs like me without any attitude, just hang in there. All things well, you'll be laughing at this in a matter of hours!
cheers

---

### Post by oilchangeguy on 2008-09-12
> **cbarnes48 said:**
> I want to do a Manual installation of Unbunut 8.04.1 so I can partition my single 160GB SATA hard drive more optimally than the Automatic option. However, when I get to step 4 of the manual installation process, I am asked to choose what type and size of partition I want to create.  What is driving me nuts is that when I click on the downward arrow in the Partition Table there is NO swap partition listed!!  :mad::confused:

For a complete newbie, who can't seem to do **anything right** so far, is it even worth the trouble to try to do a manual install?  On this and another forum, I see widely differing opinions.  How am I supposed to know which to believe and follow?

I am also aware that some of the more or most experienced of you get pretty frustrated and/or disgusted with newbies at times and their questions.  What can I tell those of you?  Like I said, although I read what I think is pertinent information that will clear the fog from my head, carrying out and succeeding at the recommended steps is another thing.

Here are three quick examples of exactly what I mean.  One forum member says to skip creating the swap partition altogether.  Reason the member gives:  "...if you have lots of RAM (I have 2GB of SDRAM) there's no need for a swap partition unless you want to use suspend."  My PC is an Acer Aspire desktop, so does this advice even apply?

On the size of the swap space or partition, one forum member states:  "Make swap from 512 megabytes to 1 gigabyte," while another says: "I recommend a swap size that is twice the size of RAM."  This would be 4GB in my case.  A third member said he recommended a "conservative" size of 1 1/2 times the amount of RAM.

Finally, how many and what kinds of partitions make sense?  I'm not looking for a "one size fits all" or perfect answer, here.  Honestly.  However, some well-worn or tested schemes would help greatly.  Here again, I am lost in all the conflicting opinions.  Especially since during a Manual install,, the Partition Table does NOT even list either the /bin or /swap partitions!!

The Table does list ones like /usr, /, /home, /var, and /tmp (I think).  So, how do I choose wisely amongst all these choices?  I don't care how many of your more advanced or knowledgeable members call me a dumbshit or worse.  I would love to be able to work smart and **_not_** so hard, so I could get this damn distro finally installed properly.

Unfortunately, these installation problems I am having are just the tip of the iceberg.  I read one page of documentation from the wiki pages, forum threads/postings, or wherever else and come away with ten more questions.  Work smart, not hard.  An excellent idea or concept.  Not sure I'll ever reach it with this supposedly "user-friendly" distro, though.

cbarnes48

why do some linux users try to make their lives so difficult? i've used ubuntu now for over two years and never felt the need to do any manual partitioning. why try and second guess the people who wrote the program? if people would stop screwing around with the operating system this forum would not have reason to exist.

---

### Post by mrsteveman1 on 2008-09-12
The partitioner isn't the most intelligent piece of software involved here :D I've seen it do some wacky stuff, but unless you have windows already installed you should just let the installer do whatever it wants. If you have windows installed it should still be ok, but just take notice of what it wants to do before you let it do it.

If you do things manually, it's a good idea to create a swap partition if for no other reason than because hibernate expects to find one, and if you ever need to hibernate the machine (powerfailure or UPS situation for instance), you will want to let it do its thing.

The size of the swap over and above the amount of ram you have doesn't mean much unless you use LOTS of memory. As long as swap is = the amount of ram you are fine, and linux by default doesn't use much swap anyway unless it needs to.

Putting /home on another partition can help if you need to reinstall later on, but otherwise most users should use a single partition for root. I don't even use a separate /boot partition.

---

### Post by Znupi on 2008-09-12
As bra10n said, create the partitions. Here's what I recommend:
1. The root partition. Mounted as ' / ', 7GB.
2. The home partition. Mounted as ' /home ', 152GB
3. The swap partition. The swap partition isn't mounted!, 1GB. (I have 512mb ram and 560mb swap and have no problems)

How to:
1. Delete all/any partitions
2. Create a new partition. Right-click it and choose 'Edit' or 'Properties' or whatever, I forget. Set filesystem to ext3 and mountpoint as '/' and size 7GB
3. Create a new partition. Right-click choose 'Edit'. Set filesystem to ext3 and mountpoint as '/home' and size 152GB
4. Create a new partition. Right-click choose 'Edit'. **Set filesystem to "swap"!** and size to whatever is left.
5. Enjoy :)

---

### Post by Thanoulis on 2008-09-12
Hello there!
You're right...too many opinions do not help...:(
But it is GNU/Linux my friend and we ought to have many options and opinions...the key is to have enough self-confidence to make your own-flavored installation-desktop...in theory... ;)
In my own opinion you do not need more than two partitions: one for */* and one for *home*. As for the swap size, make it as small or large you want (i made mine 3GBytes but now i believe it's too large).
If all this frustrates you, then just follow the auto-installation.
You'll find out with experience what options/settings suit you.

---

### Post by Znupi on 2008-09-12
Two more things to add:

1. Wow! Nobody told the OP how to actually create a SWAP partition!
2. About the whole "how big to make the SWAP partition" problem. Well, here's how I understand it: When Ubuntu runs out of RAM, it starts using the SWAP parition as RAM. Considering this, it means that the larger RAM you have, the less SWAP you need. E.g. if you have 10GB RAM you'll never run out of it so ubuntu will never need the SWAP partition. Following my theory the amount of RAM and amount of SWAP should be inversely proportional.

Hope I made sense

---

### Post by oilchangeguy on 2008-09-12
> **Znupi said:**
> Two more things to add:

1. Wow! Nobody told the OP how to actually create a SWAP partition!
2. About the whole "how big to make the SWAP partition" problem. Well, here's how I understand it: When Ubuntu runs out of RAM, it starts using the SWAP parition as RAM. Considering this, it means that the larger RAM you have, the less SWAP you need. E.g. if you have 10GB RAM you'll never run out of it so ubuntu will never need the SWAP partition. Following my theory the amount of RAM and amount of SWAP should be inversely proportional.

Hope I made sense

1. and neither did you.
2. if you've got a computer that needs to use swap/page file then you've got a computer with problems. most modern computers (1gb and up) have no need for swap. although ubuntu will assign a partition for it.

---

### Post by icyest on 2008-09-12
Since ubuntu seems to assign a swap partition by default, or at least from what i've observed in my case, your computer should be fine with a basic installation. Ignore the swap ordeal. That's what I did. Nothing happened. And it's not like you'll use up your entire Hard Drive.

---

### Post by adult swim on 2008-09-12
> **oilchangeguy said:**
> why do some linux users try to make their lives so difficult? i've used ubuntu now for over two years and never felt the need to do any manual partitioning. why try and second guess the people who wrote the program? if people would stop screwing around with the operating system this forum would not have reason to exist.

if no one ever second guessed the people who wrote the programs then no bugs would ever be fixed.  this forum would have many reasons to exist if people stopped messing around with the OS, broadcom wifi, ATI Nvidia anyone?  your post was useless to the OP. probably the guy he was talking about with respect to noobs.

OP if you can make partitions, the easy setup would be to create a partition that would be mounted as "/" which is root, and one for swap, somewehere around the amount of ram you have (if suspend or hibernate is something you use.)  
you can one up this setup, however, if you think you will reinstall or upgrade often.  you can create a partition for "/" of around 10GB, and then create a very large partition, mounted as "/home".  the /home partition would include all of the files you download, programs, music and such.  this way when you upgrade or reinstall you can specify the /home partiion and have all of the stuff you had before you reinstalled/upgraded.  with this setup, you would also want to make a swap partition the same as your ram again.

---

### Post by cbarnes48 on 2008-09-12
What is an "OP," please?

---

### Post by adult swim on 2008-09-12
you, the Origial Poster

---

### Post by cbarnes48 on 2008-09-12
&#8220;your post was useless to the OP. probably the guy he was talking about with respect to noobs.&#8221;  I don&#8217;t understand what you are trying to tell me at all with this statement, but I&#8217;m guessing you aren&#8217;t too happy with me or some other members threads or posts.  Who in the heck is the &#8220;OP?&#8221;  Oh, c***, another stupid question in your opinion, probably.

---

### Post by Znupi on 2008-09-12
> **oilchangeguy said:**
> 1. and neither did you.
2. if you've got a computer that needs to use swap/page file then you've got a computer with problems. most modern computers (1gb and up) have no need for swap. although ubuntu will assign a partition for it.
1. I beg your pardon, but I did (read my earlier post?). Your post was useless. Again.
2. I was simply posing a theory on how to determine if you need swap and how much of it. Seems like you didn't get the point. And no, if a computer uses a swap partition it doesn't mean it has problems. It means someone actually uses that computer, and does things that require a bit more memory. Of course I could browse the net all day with no swap partition, but open up a dozen or so tabs in firefox, start IMing, e-mailing, listening to music, designing, programming and running a virtual machine and you'll suddnely feel the need for some swap ;)

---

### Post by adult swim on 2008-09-12
not at all!  cbarnes, your question is a good question!  i quoted oilchange in that message he just added input with no help to the OP (you) and his comment was uncalled for. i guess i should i have specified more, but that first bit was directed at him.  your question was a valid one!

---

### Post by Znupi on 2008-09-12
> **cbarnes48 said:**
> &#8220;your post was useless to the OP. probably the guy he was talking about with respect to noobs.&#8221;  I don&#8217;t understand what you are trying to tell me at all with this statement, but I&#8217;m guessing you aren&#8217;t too happy with me or some other members threads or posts.  Who in the heck is the &#8220;OP?&#8221;  Oh, c***, another stupid question in your opinion, probably.
That part refered to **oilchangeguy** earlier post, which was totally useless to you, the O.P. (Original Poster).

---

### Post by mrsteveman1 on 2008-09-12
If you make the swap partition smaller than ram you are going to run into problems if you ever need to hibernate the machine, for instance if you have UPS and the power goes out, its supposed to hibernate in that case and it won't be able to, it'll have to shutdown or just run out of power :D

---

### Post by I wanted to leave on 2008-09-12
> **bra10n said:**
> PS - I have found this forum very willing to help Noobs like me, without any attitude, just hang in there.

Sorry for your experience here cbarnes48, but you'll find all types wherever you go. Might I also add that it's decent of other members to come to your defence when all you've done is ask for some guidance.

Hope you're all sorted now :)

---

