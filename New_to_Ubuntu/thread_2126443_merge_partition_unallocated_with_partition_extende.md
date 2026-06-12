---
title: "merge partition unallocated with partition extended?"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by smemamian on 2013-03-17
how i can merge partition unallocated with partition extended ?

I'm having trouble moving this unallocated space to the linux portion.

  picture :

[IMG]http://axgig.com/images/24401517022029176145.png[/IMG]

---

### Post by oldfred on 2013-03-17
I have never liked moving partitions left. And everytime someone posts that the partition move was interrupted by some power failure like kid, cat, dog, foot tripping switch or pulling cord and other excuses on why they lost power and then fully corrupted system reinforces my opinion.
 
But it works and for many it is ok. But have really good backups, just in case.

You have to have unallocated next to extended partition so the third partition has to be moved left into the unallocated. That may be a long process depending on how much data you have in it. Then you have to move Extended to included unallocated, and then can move partition inside extended left. Somewhat like the old slide puzzles in moving things around.

What I suggest is just use the partition as a /mnt/data partition and put whatever data you want into that partition, mount it with fstab and link that data into your /home so it behaves just like more space in / (root).

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by Impavidus on 2013-03-17
Indeed, you can just fomat this unallocated space as a data partition and mount it automatically at boot. It's slightly less flexible and a bit more secure compared to making one big partition, but in any case easier to set up.

But I have to say your partitioning is a bit peculiar. The drive is 1TB. It starts with a 35GB windows partition, which is small for windows partitions, although probably doable. Next is your unallocated space, then a large linux partition labeled "C". That label seems to suggest it's a windows system partition, but it's formatted ext4, so it's linux, probably a data or home partition. But then, why don't you merge the unallocated space to this partition? That would be easy. Finally there's your extended partition, with two linux partitions and a swap partition inbetween. Do you have two linuces without a shared home partition? Which one do you want to enlarge (if that's what you want)?

---

