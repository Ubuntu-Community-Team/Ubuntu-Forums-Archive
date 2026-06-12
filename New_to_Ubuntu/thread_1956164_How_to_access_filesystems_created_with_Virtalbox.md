---
title: "How to access filesystems created with Virtalbox?"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by cheatos on 2012-04-10
Hi,

I have Win7 running in a Virtualbox and it is really laggy on my machine, so I wanted to save the data I have on there and just do a reinstall with more memory and maybe WinXP.

Somehow I screwed up the shared folders option, so I can't just pt all my data from my VM to my computer and from there to some external drives, so I need to get access to the filesystem created by Virtualbox.

I have already seen that there is some Virtualbox.vdi file but how can I read this out?

Thanks for any help!

---

### Post by jerome1232 on 2012-04-10
You could simply create a new virtual machine, go into the settings and add that vdi file as a second virtual disk to the new machine, it will then show up as another partition within the new machine and you can copy as usual.


On the new machine you would go into Settings->Storage-> click the small icon to add a new controller, Select "Choose Exisiting Disk", browse to your vdi file, and add it.

edit: Add the new controller after getting the machine setup with windows installed etc...

Or did I read the question wrong and your wanting to migrate the data out to a real installation?

---

### Post by androssofer on 2012-04-10
> **cheatos said:**
> Hi,

I have Win7 running in a Virtualbox and it is really laggy on my machine, so I wanted to save the data I have on there and just do a reinstall with more memory and maybe WinXP.

Somehow I screwed up the shared folders option, so I can't just pt all my data from my VM to my computer and from there to some external drives, so I need to get access to the filesystem created by Virtualbox.

I have already seen that there is some Virtualbox.vdi file but how can I read this out?

Thanks for any help!


not sure if you can just access it.. 

how did up mess up the shared folder? you should be able to add additional shared folders, even after creation etc.. 

open Virtual Box

click your windows VM

then hit settings

then on the panel on the left hit 'shared folders'

then on the far right near the top is a tiny icon with a + on it, click that. (it adds a new 1)

select where you want it to go in ubuntu, your home folder would do for now. then name it and select 'auto-mount'

then start you VM and it will come up in my computer on windows as 'virtual box share bla bla'

---

### Post by cheatos on 2012-04-10
First of all a great thanks for your help!

> then on the panel on the left hit 'shared folders'

then on the far right near the top is a tiny icon with a + on it, click that. (it adds a new 1)

select where you want it to go in ubuntu, your home folder would do for now. then name it and select 'auto-mount'

then start you VM and it will come up in my computer on windows as 'virtual box share bla bla' 	

Tried that already, no success, so I'll stick to jerome's method, hope that I won't lose all my data...
It's not that much, it's just my mails, but it'd be pretty sad if I lost the mail of the last week or so..

---

### Post by forrestcupp on 2012-04-10
Hold on partner. Did you install Guest Additions? It won't let you have shared folders unless you have installed Guest Additions within your guest virtual machine's OS.

I suspect that is a lot of your problem. If you don't have Guest Additions installed, it's going to run like crap, and you won't be able to set up a shared folder. I'll bet if you install that, you won't have to do anything at all.

And you should be able to change your RAM without reinstalling everything. You can't change a VM's settings unless it is shut down first. If you have it turned off in snapshot mode, you can't change the settings.

---

### Post by cheatos on 2012-04-10
Hi forrestcupp, I have installed guest additions and I already had 2 shared folders in my guest OS, but somehow the shared folder option got corrupted (I had to shutdown the computer once with the Virtualbox running, because my lubuntu desktop was frozen...) so now I'm just looking for a way to save my files.

---

### Post by forrestcupp on 2012-04-10
> **cheatos said:**
> Hi forrestcupp, I have installed guest additions and I already had 2 shared folders in my guest OS, but somehow the shared folder option got corrupted (I had to shutdown the computer once with the Virtualbox running, because my lubuntu desktop was frozen...) so now I'm just looking for a way to save my files.

Ok. I just wanted to make sure. You just never know.

[This blog post](http://muralipiyer.blogspot.com/2008/02/mounting-virtualbox-vdi-disk-authentic.html) suggests that it is possible to find the data offset of a VirtualBox file and mount it directly. It doesn't look easy, but it's probably going to be your best chance.

---

### Post by cheatos on 2012-04-10
Thanks for that one, I'll try to understand it tomorrow or so...

---

### Post by cheatos on 2012-04-12
So, I managed to do it just by making a new VM with the vdi file as image.

Thanks for your input guys!
I'm marking this as solved now.

---

