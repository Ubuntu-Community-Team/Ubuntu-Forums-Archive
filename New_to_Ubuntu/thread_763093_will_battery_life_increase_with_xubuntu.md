---
title: "will battery life increase with xubuntu?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by eeeandrew on 2008-04-22
hi, at the minute I@m running ubuntu 7.07 on a Toshiba Equium L40-10X laptop. It always runs quickly and cleanly. Basically my qustion is: would running XUbuntu make much difference to performance on a modern laptop? Also would running XUbuntu give me longer battery life?

thanks once again to this forum for their continued support to a linux newb,
Andrew

---

### Post by sdennie on 2008-04-22
On a newer laptop, you might seem some difference in speed using Xubuntu but, probably not enough to convince you to convert if you prefer Ubuntu.  As for battery life, I don't think you will see much, if any, difference by switching to Xubuntu.

---

### Post by st33med on 2008-04-22
Yeah, what vor said. If you want to see a decent speed boost, try installing Fluxbuntu:
```
sudo apt-get install fluxbuntu
```
Then, you can set what window manager you want at the log in screen.

If you haven't installed Ubuntu (or any other varients) yet, [install Fluxbuntu here]("www.fluxbuntu.com"). You won't have as much freedom with this as GNOME or Xubuntu, but it does pretty well.

---

### Post by martrn on 2008-04-22
If you are using a laptop xubuntu should run very much faster than other versions such as kubuntu and ubuntu.  I would of thought you would see little or no improvement in battry life.

I think (and say think), it would be a kernel issue / kernel re-compile if you wish to make any effort at saving battry life on your laptop.

---

### Post by sdennie on 2008-04-22
Actually, if you want to save power on Ubuntu, you could check out [http://www.lesswatts.org/](http://www.lesswatts.org/).  It has lots of tips and tricks for power savings.

---

### Post by shae on 2008-04-22
Your battery life might actually decrease because Gnome has been optimized to cause as few CPU interrupts as possible.  Fewer of these allows your cpu to stay in a lower power state longer.

---

### Post by eeeandrew on 2008-04-23
Thanks for all the feedback. I think I will continue using ubuntu at the moment. Thanks to vor for that link. I'm gonna have a look at some of those programs and see if theres anything that can be tidied up.

Quick question while am here. how do you exit the man pages in terminal. eg. I type man ls and then the only way to get back to the $ is to exit the terminal and open a new one. Is there an exit key? I notice that ctrl+c doesn't work.

---

### Post by Cadmus on 2008-04-23
> **eeeandrew said:**
> Quick question while am here. how do you exit the man pages in terminal?

Press the 'q' key.

---

### Post by eeeandrew on 2008-04-23
that works. thanks! Apologies for my incompetance:lolflag:

cheers,
Andrew

---

### Post by Trail on 2008-04-23
Check 'powertop' as well.

---

### Post by eeeandrew on 2008-04-23
I've had a look at powertop. I'm having a bit of trouble with it though. Its asking me to enable kernel modules and I'm not sure how to do that. it says:

> No detailed statistics available; please enable the CONFIG_TIMER_STATS kernel op
This option is located in the Kernel Debugging section of menuconfig
(which is CONFIG_DEBUG_KERNEL=y in the config file)
Note: this is only available in 2.6.21 and later kernels

Suggestion: Enable the CONFIG_NO_HZ kernel configuration option.
This option is required to get any kind of longer sleep times in the CPU.


Anyone able to help?

thanks in advance,
Andrew

---

### Post by sdennie on 2008-04-23
Are you using Ubuntu 7.04?  If so, it won't have support for powertop and possibly not many of the things described at lesswatts.org.

---

### Post by eeeandrew on 2008-04-23
yes I am using 7.04

---

### Post by lespaul_rentals on 2008-04-23
> **st33med said:**
> Yeah, what vor said. If you want to see a decent speed boost, try installing Fluxbuntu:
```
sudo apt-get install fluxbuntu
```
Then, you can set what window manager you want at the log in screen.

If you haven't installed Ubuntu (or any other varients) yet, [install Fluxbuntu here]("www.fluxbuntu.com"). You won't have as much freedom with this as GNOME or Xubuntu, but it does pretty well.

Actually, it's called Fluxbox.  Ubuntu != Linux.  :roll:

Also, how can you say that Fluxbox offers less "freedom" than Gnome or Xfce?  It actually offers far more "freedom," if by that word you mean the ability to customize and fine-tune your GUI experience.

---

### Post by bharadwaj on 2008-04-23
check this link..[http://spidertools.com/ub_power.php](http://spidertools.com/ub_power.php)

---

### Post by bharadwaj on 2008-04-23
may be this one will also help you out!
[http://www.theinquirer.net/gb/inquirer/news/2007/10/31/ubuntu-eats-lappy-hard-drive](http://www.theinquirer.net/gb/inquirer/news/2007/10/31/ubuntu-eats-lappy-hard-drive)

---

### Post by RyanBFS on 2008-04-23
I could be wrong but from what I hear the new Kernel will have a lot of AMD power saving options in 8.04 when it comes out tomorrow... but not sure if I'm being accurate.

---

### Post by eeeandrew on 2008-04-23
Baradwaj: have you tried this fix? I don't want to go trashing my HDD if I@m not sure it'll work.

thanks,
Andrew

---

