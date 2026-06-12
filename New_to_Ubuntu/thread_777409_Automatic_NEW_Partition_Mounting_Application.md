---
title: "Automatic *NEW* Partition Mounting Application"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by turezky on 2008-05-01
Please, don't start beating me right away for starting this post. I know the question was risen quite a cosmic number of times on this forum, and on many other forums, however I am looking for something specific.
**_Preambula: _**
A few months ago I was using Gutsy, and then I decided to remove my Windows from the HD and move it completely to my VirtualBox VM. So I deleted my C: drive and formatted it to ext3. Then I faced the problem the first time, when I had to mount the newly created partition each time after boot. And it was annoying. I think everyone would agree with this. I google'd a lot then, and searched the forums, but everywhere there are talks about *fstab* which I don't actually like to modify manually. And then like a miracle this search result from the google popped. It was some weird site, containing this *application*. I gather it was saying about itself as an alternative to gparted. And what I remember it was once included into official Ubuntu repos, but then somewhy removed from there. But this app worked like a wonder-stick (automatically detected non-automatically-mounted partitions and proposed me to put it into auto-mount list, and, I'm not sure actually, proposed to change the label of the partition), and healed all my troubles right away. Bad for me, I didn't keep the copy of the app.
**_Ambula:_**
I few days ago, I made the most critical decision. To get rid of all remaining NTFS partitions, and make a clean install of Hardy. And I did it. However there was a problem. I should definitely report it if I found how. The installer wouldn't create the 90Gig large ext3 partition. So I created to small partitions, installed Ubuntu. In new Ubuntu I created a new partition without any flaws. Now I got all my data copied back there, but I have to mount it each time I boot my PC eventually.
**_The Question:_**
Did anyone use **this _automounter_ app**, and how can I solve my problem without putting my hands on fstab (I hate fstab). I know reinstalling Ubuntu again would be an option, but I would hate to go through my "polishing" phase again. I also stumbled upon some app called  [PyMou]("http://www.gnomefiles.org/app.php/PyMou") on the net. It had the functionality, but I could not get it running. I also found [PartitionConfigure]("https://wiki.ubuntu.com/PartitionConfigure") stuff. But it's state is undefined.
Again, pleeeaaaase, can anyone help me!
**_P.S:_**
Sorry for the long post, but I am **really** pissed off with this automounting problem. And pleeeeaaaase, don't suggest "sudo gedit /etc/fstab" cuz it's kinda pointles. Thanks for your consideration in advance, hope to see some posts here.

---

### Post by eriqjaffe on 2008-05-01
Well, there's [PySDM](http://pysdm.sourceforge.net/), which at least means you don't have to manually edit fstab...but that's probably not what you're looking for.

---

### Post by turezky on 2008-05-01
Thanks, eriqjaffe!
This app somehow resembles the one I was looking for, but what is more important it just worked for me as I wanted. I needed the functionality, not the same problem. Though it has somewhat less user-friendly interface. No more automounting problem :)
Just love Ubuntu community :)

P.S: That was easy :). How come I didn't find this app? :(

---

### Post by eriqjaffe on 2008-05-01
> **turezky said:**
> P.S: That was easy :). How come I didn't find this app? :(It was the second hit when I Googled "fstab gui".  ;)

---

