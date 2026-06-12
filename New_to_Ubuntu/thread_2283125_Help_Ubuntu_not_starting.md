---
title: "Help Ubuntu not starting"
date: 2015-06-19
forum: New to Ubuntu
---

### Post by ymurti2 on 2015-06-19
Ubuntu 14.04.2 LTS  not starting. Pease help.

---

### Post by grahammechanical on 2015-06-19
They say a picture speaks a thousand words. But you do have to talk to us. What is the hardware specification of that machine? Does Ubuntu 12.04 load correctly? Is it only Ubuntu 14.04 that does not load correctly?

There are disk errors. What happens when you press F to fix the errors or I to ignore the errors.

You can try running a Ubuntu Live session and using the Disks utility to check the Smart data of the disk. Or, you can select Advanced options for Ubuntu and then select recovery mode at the recovery menu and then you can select fsck - check all file systems.

Recovery menu>resume - resumes normal boot.

Regards.

---

### Post by ymurti2 on 2015-06-19
> **grahammechanical said:**
> They say a picture speaks a thousand words. But you do have to talk to us. What is the hardware specification of that machine? 

**Acer**    Model:** AO725    **Processor: **AMD C-70 APU with Radeon (tm) HD Graphics  1.00 GHz**


Does Ubuntu 12.04 load correctly? **NO**

There are disk errors. What happens when you press F to fix the errors  **It comes back to the first screen**  



You can try running a Ubuntu Live session and using the Disks utility to check the Smart data of the disk. **I do not have a CD or pen drive to do that. I am travelling abroad presently.**


Or, you can select Advanced options for Ubuntu and then select recovery mode at the recovery menu and then you can select fsck - check all file systems.
[B]
I have tried that but did not work.[/B]

Recovery menu>resume - resumes normal boot.

Regards.

I have answered your questions above. Thank You very much for your help.

---

### Post by Bucky Ball on 2015-06-19
What happens when you hit 'S' for skip on the last screen you have posted?

---

### Post by ymurti2 on 2015-06-19
> **Bucky Ball said:**
> What happens when you hit 'S' for skip on the last screen you have posted?


I  get this on the screen.

That is the result of fsck:

---

### Post by Bucky Ball on 2015-06-19
In the screen in post 5, log in! Just type your name and password (you won't see your password). Are you still in the CLI (at a terminal)? If so, issue:

```
sudo service lightdm restart
```

Try to follow the instructions it is giving you on the screen after you carry out our instructions. They can help. Keep going til you get stuck and there are no more instructions then report the situation. In the screenshot in post 6, what happens when you press enter then choose the 'Resume' option?

---

### Post by ymurti2 on 2015-06-19
Here it is the result of the command:

sudo service lightdm restart

---

### Post by Bucky Ball on 2015-06-19
No idea where you are there or what you're doing, just that it doesn't seem to understand sudo.

Boot the machine, log in to the terminal, issue the command before doing anything else. Looks like you are halfway through something there so don't confuse the issue. Do it straight away, post the output. Thanks.

---

### Post by ymurti2 on 2015-06-19
Dear Bucky,  I did it straight away and the result is the same as above. Any other instruction?

---

### Post by leunam12 on 2015-06-19
You have to check the HDD's health, if the drive is bad and has bad sectors and errors you have to replace it and re-install. 

1-Boot from your live USB stick or DVD.
2-on the Unity bar on the left you will see, right in the middle, above  the Amazon logo, the Ubuntu Software Center button; open it.
3-Search for "gsmartcontrol"
4-There will be no option to install probably, just click on "more info"  and on the next screen it will tell you that the package is available  from the "Universe" repository. Click on "Use this source".
5-After it's done querying the repository it will give you the option to install it. Install it.
6-Open GsmartControl, it will show you the available drives. the main  hard drive is usually the one on the left. If the icon is red, there is  nothing else to do; the drive is really bad and you have to replace it.
7-If the icon is gray double-click it and it will open a window with many tabs. 
8-On failing drives some of those tabs are highlighted in pink or red.  Look at the error log and see how many errors are recorded.
9-The last tab allows you to perform tests, run the short and the long test.
10-Post results and pictures.

---

### Post by cariboo on 2015-06-19
> **leunam12 said:**
> You have to check the HDD's health, if the drive is bad and has bad sectors and errors you have to replace it and re-install. 

1-Boot from your live USB stick or DVD.
2-on the Unity bar on the left you will see, right in the middle, above  the Amazon logo, the Ubuntu Software Center button; open it.
3-Search for "gsmartcontrol"
4-There will be no option to install probably, just click on "more info"  and on the next screen it will tell you that the package is available  from the "Universe" repository. Click on "Use this source".
5-After it's done querying the repository it will give you the option to install it. Install it.
6-Open GsmartControl, it will show you the available drives. the main  hard drive is usually the one on the left. If the icon is red, there is  nothing else to do; the drive is really bad and you have to replace it.
7-If the icon is gray double-click it and it will open a window with many tabs. 
8-On failing drives some of those tabs are highlighted in pink or red.  Look at the error log and see how many errors are recorded.
9-The last tab allows you to perform tests, run the short and the long test.
10-Post results and pictures.

Instead of going to all that  trouble just open the dash, and type:

```
disks
```

and press enter.

Once open go the menu icon in the upper right and select SMART Data & Self-tests see the screenshots.

---

### Post by ymurti2 on 2015-06-19
Dear Cariboo, here it is the result,

---

### Post by Kale_Freemon on 2015-06-19
> **ymurti2 said:**
> Dear Cariboo, here it is the result,

Is that after you've booted from a live CD or USB?

---

### Post by ymurti2 on 2015-06-20
Dear Kale,  
No it is not. It is after following the instructions that Cariboo gave.
I do not have a live CD or USB with me as I am abroad now.

):P  I managed to get a live USB and I followed the intructions that leunam12 gave here goes the results that GSmartCotrol gave:

More reports attached from gsmartcontrol:

Thank you for the help.

---

### Post by Bucky Ball on 2015-06-20
Why didn't you read and try cariboo's suggestions in post 12?

---

### Post by ymurti2 on 2015-06-20
Dear Bucky Ball, Please see post 13. I tried it.

Now I managed to open Disks with the live USB. Here goes the results, First the short self test:

Here are the results of the extended self test:

---

### Post by leunam12 on 2015-06-20
As stated in the reply to your PM, my suggestion is that you replace that drive.

---

### Post by Bucky Ball on 2015-06-20
> **leunam12 said:**
> As stated in the reply to your PM, my suggestion is that you replace that drive.

Thanks for keeping that on the thread.

@ymurti2: Please keep support on the thread for the benefit of the community and yourself. PMing for support is not encouraged here and 99% of users will either not reply to you or will let you know that they do not give one-on-one PM support. Avoid the rejection. Thanks.

---

### Post by ymurti2 on 2015-06-20
Is there a way to recover the hard drive so I can boot Ubuntu and save my data that is in it?

---

### Post by leunam12 on 2015-06-20
Boot a live session from USB, open Nautilus and click on the left pane your hard drive and navigate to the directory(ies) where your files are stored and save them to a removable hard drive or USB flash drive.

---

### Post by ymurti2 on 2015-08-03
Thank you to all of you that have written to this Thread. I am going to mark it as solved because I have realized that my hard drive had a problem. I changed it and now I am up and running again.  Thank You

Ymurti2

---

### Post by Bucky Ball on 2015-08-03
Thank you for marking as solved. Enjoy. ;)

---

