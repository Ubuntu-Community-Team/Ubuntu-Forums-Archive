---
title: "Question about RAID5"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by paarono on 2013-03-16
I am setting up a home server, i have three 3TB disks and am about to set them up for RAID5. I also have an SSD that i am running 12.04 from. My question is, if my SSD dies or i upgrade the OS or make any other significant changes, will the RAID5 be usable by the new OS or by a new controller? Is there a way to remount all three of the disks that another version/install of the OS can still read write the data? Or does the 3 disks just turn to gibberish with out the original OS that set it up?

Thanks!

---

### Post by gtmurff on 2013-03-16
Assuming you're using hardware raid (because you mention a controller), as long as the raid controller doesn't fail, you shouldn't have an issue with putting in a new SSD, installing an OS and reading the RAID array.

---

### Post by paarono on 2013-03-18
Thanks gtmurff, I actually was planning on using 12.04 from the SSD as the controller, i can't seem to figure out how to use the motherboard to do RAID (intel DH77KC) so I am looking to do this with software via the OS. 

If I would lose all my data on the RAID 5 array as a result of the SSD failing then I wanted to find a new way to set these disks up.

---

### Post by Cheesemill on 2013-03-18
If you are going to be using software RAID then this isn't an issue.

You can install a new OS or move the drives to a different machine entirely and all of your data will still be available.
You just need to install the mdadm package and it should scan your drives and reassemble the array.

---

### Post by paarono on 2013-03-23
Thanks [COLOR=#000000]Cheesemill, this is exactly what i was looking for.[/COLOR]

---

### Post by paarono on 2013-04-07
After doing some deeper research on this topic and my specific situation I came across this super helpful walk-through and explanation. So far so good![URL="http://www.clearfoundation.com/component/option,com_kunena/Itemid,232/catid,24/func,view/id,44349/limit,10/limitstart,10/"]

http://www.clearfoundation.com/component/option,com_kunena/Itemid,232/catid,24/func,view/id,44349/limit,10/limitstart,10/[/URL]

---

### Post by Cheesemill on 2013-04-07
You should take a look at rubylaser's blog, it has a lot of good mdadm information on it...

[http://zackreed.me/articles?tag_id=22](http://zackreed.me/articles?tag_id=22)

---

