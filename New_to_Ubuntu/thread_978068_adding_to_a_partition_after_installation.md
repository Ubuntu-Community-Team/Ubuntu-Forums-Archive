---
title: "adding to a partition after installation?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by aszxcv on 2008-11-10
[http://i34.tinypic.com/28rpoi1.jpg](http://i34.tinypic.com/28rpoi1.jpg)

i want to add more space to 76 gb taking it away from windows

at installation of ubuntu i set aside 80gb now i want to make it bigger but i dont know how

---

### Post by taurus on 2008-11-10
If you want to resize your harddrive, first thing is back up your important files before you're playing around with it in case something goes wrong.

Then, you have to use gparted (System -> Administration) from the LiveCD since you cannot resize a partition (linux) while you are using it.  Otherwise, you can also use GParted LiveCD if you wish.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by aszxcv on 2008-11-10
ok so once i go to (System -> Administration) from the LiveCD my partition should  get bigger

ok i try 

thanks

---

### Post by aszxcv on 2008-11-10
it seem i cant add more space to ext3 

it say i am limited to a size of 78522

sucks for me i wanted to add 7500gb more to get a total 0f 150gb for ubuntu

but it seem the most linux can have is 80gb

---

### Post by taurus on 2008-11-10
Perhaps there is something that you did to get that warning message because I have a 200GB harddrive and Ubuntu doesn't have any problem using it.  And I bet there are a bunch of people who have 500GB harddrive running Ubuntu or Linux.  (I am going to get one, 500GB HD, myself in a few weeks...)

---

### Post by aszxcv on 2008-11-10
maybe but i am a newbie i dont know what i did

i follow all the directions to the best of my abilities

---

### Post by kansasnoob on 2008-11-10
> **aszxcv said:**
> [http://i34.tinypic.com/28rpoi1.jpg](http://i34.tinypic.com/28rpoi1.jpg)

i want to add more space to 76 gb taking it away from windows

at installation of ubuntu i set aside 80gb now i want to make it bigger but i dont know how

Ok. Boot into Ubuntu and go to System > Administration > Partiton Editor, if it's not there go to terminal and install it:

```
sudo apt-get install gparted
```

Then send a screenshot of Gparted.

Also this looks like Win Vista, please verify that.

---

### Post by aszxcv on 2008-11-10
i have it  gpart already

i went to gpart from ubuntu  live cd as instructed

yes i have vista
but it just limit me to 78522

---

### Post by handydan918 on 2008-11-10
Vista partitions need to be resized from within Vista. 
after shrinking the Vista partition from within Vista, you can reboot to the live CD and use gparted to expand the ext3 partitoion. 
There is certainly no 80GB limit on partition sizes in Linux....

---

### Post by aszxcv on 2008-11-10
ok i shrink it and see what happens

i post again if i need help

you are very helpful if you can you help me with my opening dvd question i'll be grateful not that i am not now

---

### Post by kansasnoob on 2008-11-10
> **handydan918 said:**
> Vista partitions need to be resized from within Vista. 
after shrinking the Vista partition from within Vista, you can reboot to the live CD and use gparted to expand the ext3 partitoion. 
There is certainly no 80GB limit on partition sizes in Linux....

+1!

I'd still like to see a screenshot the OP's gparted.

---

### Post by aszxcv on 2008-11-10
i tried to shrink from windows disk management  but i got logical disk manager access denied


my hd is ntfs

i guess i just have to stick with 76gb and get external hard drive when that runs outs :(

---

### Post by kansasnoob on 2008-11-10
I could tell much better what's going on with a simple screenshot of Gparted!

---

### Post by aszxcv on 2008-11-11
here are the pics
[http://i33.tinypic.com/1448y8k.png](http://i33.tinypic.com/1448y8k.png)

[http://i34.tinypic.com/33dbl1s.png](http://i34.tinypic.com/33dbl1s.png)

---

### Post by aszxcv on 2008-11-11
any help

---

### Post by aszxcv on 2008-12-06
any help i want to expand by partition but going to windows and trying to expand isnt working

---

