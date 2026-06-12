---
title: "Partitions"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by RGNOME on 2011-12-06
Hello,
My hard drive has several partitions
NTFS for windows
sda5 ext 4
sda3 boot
sda6 home

the problem that I have is with sda3 boot.  when I created that partition i followed instructions from the internet.  at the time it was advised to make that partition with 100 mb and i did so.

recently i tried to download the recommended download and my pc advise me that i did not have enough space i check the disk and it is true, sda3 boot is full.

I downloaded Gparted live and resized the adjacent partition.  i took aprox 3 gb. Until here, "happy days" no problems.

However, when i tried to increase sda3 (with those 3 gb I took from the other partition) i couldn't.  

Soooo, can i increase the size of a partition?

I am quite new in Ubuntu, so if there is a solution could you explain it in simple terms?

I rather reinstall the whole drive again than going back to windows.  

As donkey said "Please I don't want to go back there, you don't know what its like to be considered a freak....."

---

### Post by westie457 on 2011-12-06
Hi a screenshot - press 'PrtSc' button on the keyboard - of the partitions on your hard drive (either Disk Utility or Gparted if it is installed) would be helpful. A picture can say a thousand words.

Any advice other than to make backups of your files ATM would purely be guesswork and might fowl things up. Not a good thing to do.

Future advice on this though tried and tested always has a chance of going wrong.

---

### Post by RGNOME on 2011-12-06
You are right Westie457.
here it go.

[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by Paqman on 2011-12-06
You can't modify any partition while it's in use. Boot up into your LiveCD/USB and launch Gparted from there. Right click on your swap partition and "swapoff" (the LiveCD automatically mounts any swaps it sees to improve performance). You should then be able to make any changes you want.

Tbh, you don't need a /boot partion if you've got a normal EXT4 / and /home partitions anyway, but it's probably more hassle than it's worth to get rid of it now. Next time you reinstall I'd advise switching to just / and /home to save hassle and conserve space.

---

### Post by westie457 on 2011-12-06
Looking at the screenshot to make space without reinstalling is going to take a lot of time and patience.
How much space are you thinking of freeing up?
And all of the necessary operations need to be done from a LiveCD/USB Desktop.

Let us know how much space you want. The instructions will look complicated but will be very easy to follow as they will be written in step by step format, ie do this step wait for it to finish then it will be on to the next step and wait. It will be to stop you getting too bored and to minimise any chance of something going wrong.

---

### Post by RGNOME on 2011-12-06
Ok, I will try that.

cheers

---

### Post by RGNOME on 2011-12-06
Westie457,
I already free 2.44 gb (unallocated 5th line from the top of the screen shot).
Now i want to engolf the unallocated space into boot.  Pls note that although they appear not to be adjacent, they are.

thanks

---

### Post by westie457 on 2011-12-06
Get the LiveCD and boot into 'Try' mode. Open Gparted and double check that you are looking at the correct drive if you have more than one. Any partition with a key next to it right-click and unmount. Turn the swap off as paqman has already stated in a previous post.
That is the easy bit now it gets more involved.

Select sda5 and 'Resize/Move' slide to the right as far as allowed. Click the 'Resive/Move' button then click the 'Apply' (green tick) and 'Okay to confirm. Wait for this to finish.

If /dev/sda7 has nothing of importance in it then delete it otherwise repeat the above step.

After that the /dev/sda4 (extended partition can be resized as above.

Nearly there. 

Now select /dev/sda3 and resize to cover the unallocated space.

One final optional step though it should not be necessary. 

Open a terminal and run ```
sudo update-grub
```

Hope this is easy to understand.

---

### Post by RGNOME on 2011-12-06
Guys,

Thank you very much for your reply.

Tomorrow i will try Westie457's plan of attack.

Thanks again.

---

### Post by RGNOME on 2011-12-06
That worked.

Excellent!

Thanks again.

---

