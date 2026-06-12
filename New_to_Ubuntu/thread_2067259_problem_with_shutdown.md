---
title: "problem with shutdown"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by grobar87 on 2012-10-06
Hi,
Sorry for my english first.
I just install Ubuntu 12.04 on my new laptop Acer Aspire v5-571 and everything works fine, only one problem.. when i want to shutdown my laptop reboot instead of shutdown.
I install laptop mode tools package and now i can shutdown laptop but only when is connected on ac power, when is on battery still reboot instead of shutdown.
I need help with this.
Thanks.

---

### Post by daslinkard on 2012-10-06
Are you able to shut down the PC by running the following sudo command:
```

sudo shutdown -h now
```

Also this [link]("http://askubuntu.com/questions/132143/stuck-on-reboot-and-shutdown") may help you....which is as follows:
```
sudo vi /etc/default/grub
```
then set
```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq quiet splash"
```
then 
```
sudo update-grub
```

---

### Post by offgridguy on 2012-10-06
> **grobar87 said:**
> 
I install laptop mode tools package and now i can shutdown laptop but only when is connected on ac power, when is on battery still reboot instead of shutdown.
I need help with this.
Thanks.

If you search the threads you will find this exact situation has been discussed
recently.  I will have a look and post a link when I find it,

---

### Post by offgridguy on 2012-10-06
Sorry but I can't seem to find the thread i want, lots of stuff under shutdown but the one that
mentioned AC power and batt. power, is still eluding me. I will let you know if I find it, I know it's there somewhere.

---

### Post by grobar87 on 2012-10-06
> **offgridguy said:**
> Sorry but I can't seem to find the thread i want, lots of stuff under shutdown but the one that
mentioned AC power and batt. power, is still eluding me. I will let you know if I find it, I know it's there somewhere.

Ok, thanks. I'll try to find that threat too.

---

### Post by grobar87 on 2012-10-06
> **daslinkard said:**
> Are you able to shut down the PC by running the following sudo command:
```

sudo shutdown -h now
```Also this [link]("http://askubuntu.com/questions/132143/stuck-on-reboot-and-shutdown") may help you....which is as follows:
```
sudo vi /etc/default/grub
```then set
```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq quiet splash"
```then 
```
sudo update-grub
```

I can't shutdown with "sudo shutdown -h now"... and i try your suggestion but problem is still there.

---

### Post by offgridguy on 2012-10-06
Here's the thread I was thinking of, however it doesn't look like what you need, sorry.

 					Originally Posted by **varunendra** 					[[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12235882#post12235882") 				
 				[I]In that case, the system wouldn't reboot also, while it does in OP's case. Reboot = full shutdown + re-start. :smile:

I have the same problem with my Asus X54C-261D laptop, albeit only when  it is plugged into AC power. When on battery, it shuts down normally.  Sometimes it also happens with Win7 I'm dual booting with, but rarely  there. I doubt it to be some **acpi** related bug, but didn't find enough time yet to dig it. Besides, I don't mind unplugging for a sec. if it does the job. :smile:[/I]
 			 		 	 	 
I don't think that characterizes the problem. I've seen it happen a  couple of times in the past week with the laptop unplugged (It's a  Toshiba L-655). I've also encountered it once when the laptop was  plugged in to AC power. So, this does seem to be a bug, but we've got to  characterize it.

If anyone is familiar with the process, can ask/help us to characterize  it. I'm sure there're a lot many people encountering this.

I'm going to try using the terminal for shutting down ubuntu for the next week.
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_offline.gif[/IMG]   		 		 		[[IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=12242074") 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=12242074") 		 		 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/multiquote_off.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=12242074")

---

### Post by grobar87 on 2012-10-07
Today i try Ubuntu 12.10 final beta .... but same problem :( I hope they will fix this soon. Thanks again for your replys.

---

### Post by bonzodog on 2012-12-05
The cause of this problem HAS been found, its caused by the way in which linux shutsdown systems. However, the cause of the problem is very technical. It s a failure of the kernel to properly powerdown the USB Busses, because of the way the EFI BIOS works.

There is a workaround for this, but it was only figured out for systemd based inits, ubuntu's upstart will need a script modification in the shutdown scripts to get it working properly.

Problem is highlighted here:

[http://www.pbehnke.com/main/node/11](http://www.pbehnke.com/main/node/11)

---

