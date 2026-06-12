---
title: "Why Won't Suspend or hibernate work ?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-19
I seem to have an issue with getting the suspend and or hibernate to work. on Ubuntu 8.04 (see my system specs in my tag line) 

Any time I put the computer into suspend we I go to bring it back up it never works I either have a white screen or no screen.  

One thing I find funny is if I bring it back up right after I have taken into suspend it seems to work fine. It is only after it has been in suspend mode for longer then say 5 min. that I have this issue.  

Anyone got any ideas? 

thanks 
~D

---

### Post by KenBW2 on 2008-05-19
I spy Nvidia card :)

Do you use Compiz? If so that could be the cause of the problem, as was mine. Try disabling your Nvidia driver from System > Administration (or was it Preferences?) > Restricted Drivers and hibernating.

If Hibernate works after that there's a solution that worked for me. I can't find it at the moment (Google Web History, you fail me) but I have a link on my main PC. I'll get it up tomorrow (it's 2:21am here :( ) and post it here so you can try it.

Let me know how it goes :)

---

### Post by hardyn on 2008-05-19
make sure you have sufficient swap.

---

### Post by hufferd on 2008-05-19
Swap I think is ok  question though how do i adjust swap in ubuntu? I didn't know you could I thought that was handled auto .... 

and yes  I have a nvidia card I will try to mess with the drivers on tuse and let you know how it works out and post here on tuse... if you could post the other info for me that would be great


thanks

D

---

### Post by gibberish on 2008-05-19
I have similar problem. On Dell 530s. No NVIDIA card, no effects. Plenty of swap (2.5x RAM). 
I have read various fixes, all too complicated for me. Anyone know if this is being adressed in updates?

---

### Post by KenBW2 on 2008-05-20
Here's the link I promised:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

Just make the changes shown there and Hibernate should work :)

If you're worried about swap I prefer to use gparted to change partitions. To install it run
> sudo apt-get install gparted
How much swap do you have?

Let me know how it goes, or if you need any help with that

---

### Post by hyper_ch on 2008-05-20
how much swap and how much ram do you have?

---

### Post by pbeesley on 2008-05-20
ok not to hijak the thread or anything but I can hibernate my PC but whenever it comes back up it gives me an error saying that it couldn't hibernate.....but It did cause i was still logged on and all apps still open.....anyone know how to make the message go away? :) Thanks

---

### Post by KenBW2 on 2008-05-20
Weird I know - mine does it as well. Just click "Don't show this message again" or whatever it is when the message pops up
:)

---

