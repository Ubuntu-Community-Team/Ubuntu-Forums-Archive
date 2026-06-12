---
title: "Ubuntu 12.04 LTS install"
date: 2013-09-12
forum: New to Ubuntu
---

### Post by Shrinathsuresh on 2013-09-12
A good looking Ubuntu 12.04 got installed in my system. This is the first time am installing ubuntu in my machine..

By luck i allocated my 50 GB space as 

root - 10 GB
swap - 8 GB
ext4 - 32 GB

but am really not sure why i did like this and what is the use of allocating space for root and swap . 

Can someone please explain why we need root and swap and also how much space need to be allocated for them .. 

Now , After installing i created a user .. But there is a user called root which i should login using the command "su" . But , whats the password. Is there any default password set for root ?

---

### Post by ajgreeny on 2013-09-12
With just that space for ubuntu I would have left everything except swap in the root partition, but having now got that situation I suggest you leave it as it is for now.

Swap is the same as windows virtual memory or swap file, but is a separate partition normally in Linux.  How much swap will be used, or even if it's really needed is dependent on your hardware and size of RAM, but I have always had swap on my systems, and even now with 8GB of RAM I have an 8GB swap partition to allow hibernation when I need it.
See [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) for details.

Ubuntu does not use a root acount as most other distros do but instead uses a sudo for root permissions system.
See RootSudo in my signature for all the details of that.

---

### Post by TheFu on 2013-09-12
> **Shrinathsuresh said:**
> A good looking Ubuntu 12.04 got installed in my system. This is the first time am installing ubuntu in my machine..

By luck i allocated my 50 GB space as 

root - 10 GB
swap - 8 GB
ext4 - 32 GB

but am really not sure why i did like this and what is the use of allocating space for root and swap . 

Can someone please explain why we need root and swap and also how much space need to be allocated for them .. 

Now , After installing i created a user .. But there is a user called root which i should login using the command "su" . But , whats the password. Is there any default password set for root ?

/ (root) - is where programs and the OS fit.  I'd make it a little larger ...15G.  10G is just a little too small to avoid common problems running out of storage.  On UNIX systems, NEVER let this file system get more than 95% full - bad things happen and you can get to a difficult to recover situation. It can be very bad if full.  This partition should also be ext4, unless you have a specific reason to use some other type of file system..

swap is "virtual memory" ... disk is used as RAM becomes filled. There is no exact answer for how large is needs to be, especially as systems get more and more RAM these days. The type of workload and RAM matter for this decision. 8G seems like too much swap.  1-2x the amount of RAM was the old rule of thumb .. if you used hibernate mode or standby there are other considerations too.  Swap is supposed to let you "feel" that the computer is getting slower as we overuse RAM.

ext4 is the name of a type of file system, not the name for a mount-point.  You probably want that to be /home ... were all your personal settings and files are placed by default.

---

### Post by mastablasta on 2013-09-12
for 50 GB disk space just create / and /swap
/ is like c:\ in windows
and /swap is like pagefile

if you let it autoinstall (not manual) then it will set these values appropriately to your hardware and disk space.

---

### Post by Shrinathsuresh on 2013-09-12
The documentation links were awesome . They are pretty straight forward. I read all the articles. Thanks for your help .

---

