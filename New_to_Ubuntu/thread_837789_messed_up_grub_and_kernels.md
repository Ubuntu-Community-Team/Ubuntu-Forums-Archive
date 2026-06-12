---
title: "messed up grub and kernels"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by trucker33377 on 2008-06-22
Hi i was trying to cleanup my grub entries and deleted the wrong kernel.

after trying a few things i thought if i get rid of kubuntu then the grub may work it didnt.

/dev/sda (465.76 GiB) ubuntu
/dev/sda1 ext3 455.62 GiB
/dev/sda2 extended 10.14 GiB
/dev/sda5 linux-swap 10.14 GiB

/dev/sdb 279.46 GiB xp and kubuntu
/dev/sdb1 141.40 GiB ntfs boot (also has a orange triangle with ! on it)
/dev/sdb2 ext3 138 GiB

this is what my partitions look like.
ive deleted the kubuntu out removed partition

used supergrub to fix linux boot. 

i can find hardy 8.04 on supergrub but it wont boot

when i did fix boot of linux supergrub says it fixed but all the entries are for gutsy and theres no windows on the list

I can get windows to boot

need help here ubuntu has got to be there somewhere

---

### Post by trucker33377 on 2008-06-23
update still need help.

got the grub fixed

now i have windows and gutsy sharing a HD
and my old op sys on other HD (should be hardy)

I look at synaptic and search linux-image but what one do i need to install?

I would like to remove the ones not needed.

installing gutsy 7.10 is how I got the grub to work right. thought that may work and it did

still grub shows all gutsy kernels, But booting supergrub theres a hardy 8.04 in there

so something is messed up still

---

