---
title: "Need help with extending the root drive size on Ubuntu 20.04"
date: 2021-12-13
forum: New to Ubuntu
---

### Post by kkran on 2021-12-13
I have an ubuntu VM Spun up and we extended the disk size from 50GB to 500 GB. My root drive is showing the size as 27GB. I want to extend it to 400 GB . I tried vgextend that shows the max size as 50GB. How can I extend the entire 500GB under SDA3 to [COLOR=#DADADA]ubuntu--vg-ubuntu--lv[/COLOR]

root@pd-dx-sy-soc:~# df -h                                                                                                                                                                          
Filesystem                         Size  Used Avail Use% Mounted on                                                                                                                                 
udev                               7.8G     0  7.8G   0% /dev                                                                                                                                       
tmpfs                              1.6G  1.2M  1.6G   1% /run                                                                                                                                       
/dev/mapper/ubuntu--vg-ubuntu--lv   27G   13G   13G  51% /                                                                                                                                          
tmpfs                              7.9G     0  7.9G   0% /dev/shm                                                                                                                                   
tmpfs                              5.0M     0  5.0M   0% /run/lock                                                                                                                                  
tmpfs                              7.9G     0  7.9G   0% /sys/fs/cgroup                                                                                                                             
/dev/loop2                          62M   62M     0 100% /snap/core20/1270                                                                                                                          
/dev/loop0                          62M   62M     0 100% /snap/core20/1242                                                                                                                          
/dev/loop1                          56M   56M     0 100% /snap/core18/2246                                                                                                                          
/dev/sda2                          976M  213M  697M  24% /boot                                                                                                                                      
/dev/loop4                          68M   68M     0 100% /snap/lxd/21835                                                                                                                            
/dev/loop3                          56M   56M     0 100% /snap/core18/2253                                                                                                                          
/dev/loop5                          43M   43M     0 100% /snap/snapd/14066                                                                                                                          
/dev/loop6                          44M   44M     0 100% /snap/snapd/14295                                                                                                                          
/dev/loop7                          68M   68M     0 100% /snap/lxd/21803                                                                                                                            
tmpfs                              1.6G  8.0K  1.6G   1% /run/user/115                                                                                                                              
tmpfs                              1.6G     0  1.6G   0% /run/user/0                                                                                                                                
root@pd-dx-sy-soc:~# [COLOR=#000000] [/COLOR]                 

root@pd-dx-sy-soc:~# lsblk                                                                                                                                                                          
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT                                                                                                                                       
fd0                         2:0    1    4K  0 disk                                                                                                                                                  
loop0                       7:0    0 61.9M  1 loop /snap/core20/1242                                                                                                                                
loop1                       7:1    0 55.5M  1 loop /snap/core18/2246                                                                                                                                
loop2                       7:2    0 61.9M  1 loop /snap/core20/1270                                                                                                                                
loop3                       7:3    0 55.5M  1 loop /snap/core18/2253                                                                                                                                
loop4                       7:4    0 67.2M  1 loop /snap/lxd/21835                                                                                                                                  
loop5                       7:5    0 42.2M  1 loop /snap/snapd/14066                                                                                                                                
loop6                       7:6    0 43.3M  1 loop /snap/snapd/14295                                                                                                                                
loop7                       7:7    0 67.2M  1 loop /snap/lxd/21803                                                                                                                                  
sda                         8:0    0  501G  0 disk                                                                                                                                                  
&#9500;&#9472;sda1                      8:1    0    1M  0 part                                                                                                                                                  
&#9500;&#9472;sda2                      8:2    0    1G  0 part /boot                                                                                                                                            
&#9492;&#9472;sda3                      8:3    0  500G  0 part                                                                                                                                                  
[FONT=Verdana]  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0   27G  0 lvm  /    [/FONT]

---

### Post by kkran on 2021-12-13
No worries...this is fixed. Thank you.

---

### Post by QIII on 2021-12-13
Would you care to share the solution with the community so that others do not have to guess the solution if they need it?

These forums exist to profit the entire community, not just to profit ourselves.

---

