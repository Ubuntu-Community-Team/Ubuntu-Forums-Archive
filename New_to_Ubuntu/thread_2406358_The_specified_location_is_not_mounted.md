---
title: "The specified location is not mounted"
date: 2018-11-19
forum: New to Ubuntu
---

### Post by eli3777 on 2018-11-19
Ok, please be easy on me. I have kinda been going in over my head with ubuntu.

A while back somebody showed me Nextcloud so I threw stock Ubuntu on a spare desktop I had to try it out. (I have no idea how command line linux works, so I wanted to start with a non server version)
I fallowed some guide and used a cheap domain and had it all up and running. I have messed up something (I think with the domain settings but I cant login local so idk) and I want to just start over, but I want to get the files off the server. I found that they are stored in var/snap/nextcloud/common/nextcloud/data/[nextcloud un]. They all look to be there, but when I try copy them to somewhere like the desktop I get a "error while copying". The extra details say the specific location is not mounted, and I have no idea where to go from here.

Thanks in advance.

---

### Post by angisky on 2018-11-19
Where are you trying to copy them to?

---

### Post by eli3777 on 2018-11-19
The desktop/ a usb drive to get the files off the system to my main pc.

---

### Post by oldos2er on 2018-11-19
Can you please copy and paste the exact command you ran and the error message you saw?

---

### Post by eli3777 on 2018-11-20
> **oldos2er said:**
> Can you please copy and paste the exact command you ran and the error message you saw?
I was using the file explorer

---

### Post by mitesh.agrwl on 2018-11-20
> **eli3777 said:**
> I was using the file explorer

Regarding how to use command line in Ubuntu, from the menu open a Terminal (Short cut keys Alt+Ctrl+t). If you want to copy a directory use the command **cp -R**** <path to directory> <path of destination folder>**.

To check where your disk is mounted use command ```
 lsblk 
```

In your case the code will be (assuming you are using a usb drive  which is mounted on  /media/<your_username>/<UUID_of_USB_Disk>
 
```
 cp -R /var/snap/nextcloud/common/nextcloud/data/  /media/<your_username>/<UUID_of_USB_Disk> 
```

If error is 'permission denied' try the same command using 'sudo' before cp.

---

