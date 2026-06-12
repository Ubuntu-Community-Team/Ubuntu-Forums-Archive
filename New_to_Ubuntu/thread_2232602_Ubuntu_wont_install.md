---
title: "Ubuntu wont install"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by don23 on 2014-07-03
im trying to install ubuntu desktop 14.04 with a flash drive and whenever i boot off of it i get a black screen with a blinking cursor in the corner and i cant type or do anything
im new to linux

---

### Post by ajgreeny on 2014-07-03
Do you see any ubuntu screen at all, or does it go straight to the blinking cursor in the top left of the screen?

What hardware do you have?  If you have an nvidia graphic card you may need to boot with the **nomodeset** option, but I can't remember how you get to that option with a USB install; try hitting F6 as soon as you see any screen at all appear, but if you never see anything I'm afraid you may have to wait for other posts.

---

### Post by yancek on 2014-07-03
There are a number of different methods which can be used to create a bootable flash drive.  Which one did you use?  Also, do you have another computer on which to test it to see if it boots?

---

### Post by sandyd on 2014-07-03
Moved to absolute beginners section

---

### Post by stalkingwolf on 2014-07-03
Depending on the specs of your machine it can take some time to boot to the desk top.  with usb1 and 1 gb of ram ive seen it take up to 15 minutes to get from that screen to the desktop.

On the other side if there is something wrong with the drive  it usually tells me very quickly.

---

### Post by sp40140 on 2014-07-03
1] What kind of computer do you have (Hardware specs)? 
2] Does it have any Operating System installed currently? Does it work?
3] Howe did you create bootable Ubuntu install drive?
4] Do you see anything on screen when you try to boot from flash drive? BIOS info, if it's a machine from standard maker, their logo like Dell or HP?

---

### Post by whitesmith on 2014-07-04
Usually a blinking cursor on a black screen means no operating system is present -- i.e., the boot loader that's part of your BIOS handed off control to a non-existent OS. The post immediately preceding mine kind of sums it all up.

---

### Post by squakie on 2014-07-05
Naw - if it's trying to boot and is at a point it wants the graphic driver, sometimes all you need are things like nomodeset or any of the other available boot options.

That's why it's important for the OP to tell us 3 things:

- what is the hardware environment - cpu,memory,video adapter
- how did you create the usb flash - via something like unetbootin?  You can't just copy the files to the drive - it won't have any of the things needed to actually boot
- if it is booting, then stops at this screen after a while, please describe each step it has gone through prior to the screen going blank.  Did you get a screen with little dots?  Did you get a screen asking to Try Ubuntu or Install Ubuntu?

There are other things to do, especially if you want to actually run an Ubuntu installation on the flash drive.  But please provide the above information first - it will give us somewhere to start.

---

