---
title: "LiveCD and mounting partitions"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by jaynv0i on 2011-12-06
I am not sure if this is the proper place to post this, but since I am new to creating LiveCDs, it seems like the perfect place.

I have installed Ubuntu 11.10 server and have it configured the way I want it to be configured.  I created a LiveCD using bootcdwrite and I am able to boot from the cd without any problems.

When I try to access the first partition on the hard drive in the system /dev/sda1, I am able to mount the system without any problem, but the only thing visible is the contents of /boot.

When I try to do the following:
    sudo chroot /mnt /bin/bash, I receive a message stating /bin/bash cannot be found.  If my understanding is correct, this is because /bin/bash cannot be found on /dev/sda1 which is mounted to /mnt.

When mounting /dev/sda1, how can I make more than just the /boot directory visible?

Thanks for your help.


Jay

---

### Post by blackbird34 on 2011-12-06
Maybe there only is the /boot directory on /dev/sda1. What happens if you mount the other partitions? Does everything show up?

---

### Post by phidia on 2011-12-06
I'm trying to clarify if I understand your post-you are booting from the livecd and then mounting the hard drive partition sda1 to /mnt. I'm thinking /bin/bash isn't found because as you say it's not really where the booted environment expects it to be. What exactly do you have on sda1 is there a full (server) install there?

---

### Post by jaynv0i on 2011-12-06
The other two partitions are not mountable.  Basically, they are a logical drive inside of a physical drive for swap space.

However, your post did show me (when I examined what was mounted very carefully) / is mounted from /dev/mapper/LiveFSUbuntu-root.  When I mounted /dev/mapper entry when booted from the LiveCD, I was able to access the information on the drive without any problem.

What would be the best source to learn more about the disc hierarchy Ubuntu uses?

Thank you.

---

