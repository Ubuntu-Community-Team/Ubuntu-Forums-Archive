---
title: "Install Ubuntu enterprise cloud 11.04 on preinstalled windows laptop"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by Ranpred on 2013-03-12
Hi Everybody,

My requirement is that I am trying to boot Node controller module UEC 11.04 using eucalyptus on external hard disk mounted on laptop. The Acer Aspire one laptop is preinstalled with Windows 8 and has AMD-c70 processor (I guess it supports virtualization) with 2GB RAM and 320GB hard drive. I am planning to install and run the node controller to boot from an 1TB external hard disk. Do you guys think this can be done and please suggest some links that might help me in achieving this. 

I have come across many forums and threads which discusses several related topics, but it would be helpful if everything is available at single place :tongue:. Also, I am doing this for a University project, so it is necessary that I have to use UEC 11.04 version.

Cheers

---

### Post by mellocode on 2013-03-13
So basically you want to install ubuntu onto an external hard drive?

---

### Post by Mark Phelps on 2013-03-13
> **Ranpred said:**
> Also, I am doing this for a University project...


We are not a homework service. Please see code of conduct which you agreed to.

[http://ubuntuforums.org/index.php?page=policy]("http://ubuntuforums.org/index.php?page=policy")

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

### Post by mastablasta on 2013-03-13
ah come on Mark this is too easy for a homework.

to the OP - during install select the pluged in external hard disk for instalation. make sure you also put the grub on external disk. then during boot select external disk in bios. this should start grub and and you should boot into ubuntu. you may need to disable the secure boot and you may need to use 12.04 or 12.10. as i do not know if 11.04 will support booting next to win8. though you could try.

---

### Post by Ranpred on 2013-03-30
Hi All..  @[**[COLOR=#000000]Mark Phelps[/COLOR]**]("http://ubuntuforums.org/member.php?u=311399") I know this is not a home work service and I am not expecting anybody to do my work. My intention of specifying "Also, I am doing this for a University project..." was to insist that I have to use "11.04".. coz I saw lots of threads where people had suggested to use 12.04.. 

Now that I have setup my cloud network but used win7 instead of win8... Now my issue is that when I lookup for availability zones the vpcu displays to be 0 all the time.. I guess my node controller is not registered properly.. I tried several steps to re-register but in vain.. Any help is appreciated.. I can provide you any details in case you need.. Thanks in advance !!!

---

