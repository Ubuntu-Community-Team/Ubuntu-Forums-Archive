---
title: "Error:unknown filesystem grub rescue"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by colestv on 2013-03-04
I turned on my Desktop and this error message came up. I would like to install windows on it if the OS has crashed but I have no idea how to boot from here.

---

### Post by presence1960 on 2013-03-04
More details please. OS(s) installed. What is the error message. make and model machine. specs of machine????????????????????????? The info you provided thus far is useless if you want help.

---

### Post by colestv on 2013-03-04
To be serious I don't know much about this desktop. i know it has a terabyte sata, 4 amd phenom, It had Ubuntu on it although I am not sure which version. I just recently bought it from my buddy, also it is a custom build.

---

### Post by colestv on 2013-03-04
If you need some specific info I might be able to help but over then that I am at my wits end. This is my first time using anything linux and i wanted to boot windows on it then this happened.

---

### Post by colestv on 2013-03-04
> **presence1960 said:**
> More details please. OS(s) installed. What is the error message. make and model machine. specs of machine????????????????????????? The info you provided thus far is useless if you want help.

I know I'm asking for a lot but I really need this desktop up and running again, but I don't have much info on it.

---

### Post by schragge on 2013-03-05
If you don't plan to use Ubuntu, and just want to install Windows, why can't you boot from Windows installation media?

---

### Post by audiomick on 2013-03-05
I assume the thread title is the error you are seeing. As far as I know, this generally means that the grub boot loader cannont find the drive it is looking for to boot from.

The first thing I would do is open the box and make sure all cables to the hard drive(s) are seated properly. You say this is a custom build that you have bought, so it has presumably been transported recently. That makes checking the connections inside all the more relelvant.

I assume the machine was working for your friend. Did the transport go well? No nasty knocks or anything? No chance of damage during transport?

I would probably also boot into the live environment and see if I can see the drive with the file manager there or with the drive management tools there. The live environment is when you boot an Ubuntu install CD or USB into the "try Ubuntu without installing" option. It is a useful way to look at a computer that wont boot by itself.

If you want to try and get the ubuntu boot running again, go here
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

You could try the boot repair that it offers, or generate the boot info as described there and post the link to it here so that people can see the state of the machine. Someone should be able to help you get it going. I would tend to the boot info to see if the machine is finding all the drives it has.


If you really don't have any interest in getting the Ubuntu going, then I can only second schragge's advice: stick the windows installer in it an boot that. If that doesn't work, someone might be able to help your if your describe exactly what it going wrong, but installing windows is more a question for a Windows forum.

---

### Post by colestv on 2013-03-05
> **audiomick said:**
> I assume the thread title is the error you are seeing. As far as I know, this generally means that the grub boot loader cannont find the drive it is looking for to boot from.

The first thing I would do is open the box and make sure all cables to the hard drive(s) are seated properly. You say this is a custom build that you have bought, so it has presumably been transported recently. That makes checking the connections inside all the more relelvant.

I assume the machine was working for your friend. Did the transport go well? No nasty knocks or anything? No chance of damage during transport?

I would probably also boot into the live environment and see if I can see the drive with the file manager there or with the drive management tools there. The live environment is when you boot an Ubuntu install CD or USB into the "try Ubuntu without installing" option. It is a useful way to look at a computer that wont boot by itself.

If you want to try and get the ubuntu boot running again, go here
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You could try the boot repair that it offers, or generate the boot info as described there and post the link to it here so that people can see the state of the machine. Someone should be able to help you get it going. I would tend to the boot info to see if the machine is finding all the drives it has.


If you really don't have any interest in getting the Ubuntu going, then I can only second schragge's advice: stick the windows installer in it an boot that. If that doesn't work, someone might be able to help your if your describe exactly what it going wrong, but installing windows is more a question for a Windows forum.

I have checked all the connections and I was the one who transported it. There was no issues when I got home and used it then. I have tryied to boot into windows from this screen but nothing happens  when I put in the cd so I assume that putting in a live ubuntu cd would  have the same issue.

---

### Post by audiomick on 2013-03-05
> **colestv said:**
> I have tryied to boot into windows from this screen but nothing happens  when I put in the cd so I assume that putting in a live ubuntu cd would  have the same issue.

With the Ubuntu CD, you have to have the CD in the drive when you power up the computer, and as far as I know, the windows cd is the same. Is this how you are trying the windows cd, or are you putting it in after you get the grub error message?

---

### Post by colestv on 2013-03-05
> **audiomick said:**
> With the Ubuntu CD, you have to have the CD in the drive when you power up the computer, and as far as I know, the windows cd is the same. Is this how you are trying the windows cd, or are you putting it in after you get the grub error message?

I have the cd in the drive before starting. It comes to a flashing - for a few minutes then returns to the grub error.

---

### Post by colestv on 2013-03-05
I have now connected my Hard Drive to my laptop with a usb cable, it also gives the hard drive power and I can hear it boot up but it doesn't appear anywhere on my laptop. Could this be because my laptop has windows and the hard drive has/had ubuntu?

---

### Post by audiomick on 2013-03-05
> **colestv said:**
> .Could this be because my laptop has windows and the hard drive has/had ubuntu?

Yes. Windows will not be able to read a drive that has a linux file system on it.

Going back to booting from a CD: you have gone into the BIOS and set the CD drive as first in the boot order, haven't you?

What you describe sounds like it is not even looking at the CD drive for a bootable medium

---

