---
title: "How to get rid of Vista?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by SLaCK3r on 2008-04-27
OK. So I am installing Ubuntu 8.04 and once it's done, i want to know how to get rid of Vista. I don't want to dual boot. I don't have the CD for Ubuntu by the way. So how do i get rid of Vista after installing Ubuntu?

Please do this in beginner talk because I have never used a Linux OS before (obviously :P)

---

### Post by jimv on 2008-04-27
Once you have the Ubuntu CD and are doing the install of Ubuntu, it will ask you how you want to partition your harddrive.  There is an option for "Use entire disk".  That will erase everything on your harddrive, including Vista, before it installs Ubuntu.

---

### Post by daimaru on 2008-04-27
> **SLaCK3r said:**
> OK. So I am installing Ubuntu 8.04 and once it's done, i want to know how to get rid of Vista. I don't want to dual boot. I don't have the CD for Ubuntu by the way. So how do i get rid of Vista after installing Ubuntu?

Please do this in beginner talk because I have never used a Linux OS before (obviously :P)
well during install you can just choose to use the whole hardisk as your ubuntu partion and there will be no more vista. but since you say your new to this you might want to try ubuntu first, and make sure everything works to your liking before getting rid of windows. I don't know if you have a original vista cd, in case you have to go back to it if you don'T like ubuntu.

---

### Post by Tatty on 2008-04-27
If you want Ubuntu to be the only OS on your computer then you can tell ubuntu to use the entire drive when you are installing.  Its an option on the partitioning screen - something along the lines of "erase entire disk"

However If you are new to linux then i strongly reccomend you dual boot, as everyone struggles at first when going from windows -> linux.  It will take time to learn (being experienced with windows does not help too much as it is a very different OS) and in the mean time you dont want to be left unable to do what you want.

---

### Post by Bodsda on 2008-04-27
Go to Applications--> Accessories--> Terminal

once that pops up copy and paste this command

```
sudo apt-get install gparted
```

if it says nothing installed thats fine, if it says things installed thats fine also.

then enter this command

```
sudo gparted
```

now in the top right of this window it tells you which disk is selected -- use the drop down menu to select your vista disk -- if your dual booting on 1 hard drive just select that.

right click on the partition u dont want -- and select unmount (if your dualing on 1 hard drive you will have to do this through the live cd not a hd boot) right click again and select delete.

be careful though -- you can destroy your system if you delete the wrong partitions

hope this helped

---

### Post by SLaCK3r on 2008-04-27
OK :) Thanks :D The fast replies...wow :D I will see if I like it and if I get any problems I will tell you. oh, and even if I am not installing from a CD I will still get the partition screen, am I correct?

---

### Post by Google Spider on 2008-04-27
> **SLaCK3r said:**
> OK. So I am installing Ubuntu 8.04 and once it's done, i want to know how to get rid of Vista. I don't want to dual boot. I don't have the CD for Ubuntu by the way. So how do i get rid of Vista after installing Ubuntu?

Please do this in beginner talk because I have never used a Linux OS before (obviously :P)


You have never used Linux before and you want to get rid of windows!?!:-|

Anyway, choose the "use full drive" option while installing if you want to do that. But best is to dual boot. I've been using Linux since 6 months and I still have my windows partition there...though I hardly ever boot into it.:guitar:

---

### Post by puifais on 2008-04-27
Highly recommend making sure you have internet on your new Ubuntu before deleting the Windows part cuz that internet access on Windows was very helpful to me to figure out how to get internet working in Ubuntu.

---

### Post by Tatty on 2008-04-27
> **SLaCK3r said:**
> OK :) Thanks :D The fast replies...wow :D I will see if I like it and if I get any problems I will tell you. oh, and even if I am not installing from a CD I will still get the partition screen, am I correct?

How are you installing?

---

### Post by Dani Filth on 2008-04-27
> **SLaCK3r said:**
> OK :) Thanks :D The fast replies...wow :D I will see if I like it and if I get any problems I will tell you. oh, and even if I am not installing from a CD I will still get the partition screen, am I correct?

I've used GParted before, to modify my HD partitions, and it worked without error, so I think you should be fine unless you choose the wrong partition.

Btw, just curious, how do you install Ubuntu without CD??? :popcorn:

---

### Post by SLaCK3r on 2008-04-27
I dunno, I extracted the 8.04 zip and it has install...apparently it's installing :) I hope I'm doing this right :/

---

### Post by SLaCK3r on 2008-04-27
YAY! it worked! I have internet too :D I love Linux so far <3

---

### Post by zaussome on 2008-04-27
z

---

### Post by SLaCK3r on 2008-04-28
Ok, so I installed Ubuntu on my D:\ (60 G)...I want to know how to access the D:\. Also, I deleted some files which I think were in the C:\ (Windows, McAfee, etc.). Are any Linux files stored in the C:\ if I installed it to the D:\? Sorry, I am 100% sure I want Ubuntu.

---

