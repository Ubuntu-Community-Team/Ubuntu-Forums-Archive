---
title: "ubuntu take 1:22 min to boot"
date: 2020-06-08
forum: New to Ubuntu
---

### Post by ryoksec on 2020-06-08
hello everyone i am not exactly new to ubuntu i have been using it for 3 months at least and i know a great amount of commands and so on and i have used it before as virtual machine but now i have installed it as main system 

well the problem is when i installed ubuntu for the first time it took 15 - 25 sec Max to boot it was very quick and graceful 
but now i don't know why but it takes 1:22 to reach the desktop and i don't know why my labtop is very good it has 8 giga ram and core i3 8th gen , 5400 rpm hard disk 
i have searched in many websites and so on so i will put the log here and pls guide me through this problem and how i should fix it :-

```
 systemd-analyze blame

34.941s plymouth-quit-wait.service                           
21.482s systemd-journal-flush.service                        
19.196s dev-sda3.device                                      
10.581s apport-autoreport.service                            
10.577s udisks2.service                                      
 9.007s dev-loop13.device                                    
 8.668s dev-loop9.device                                     
 8.587s dev-loop4.device                                     
 8.359s dev-loop7.device                                     
 8.281s dev-loop11.device                                    
 8.160s dev-loop10.device                                    
 8.027s dev-loop5.device                                     
 7.959s dev-loop1.device                                     
 7.904s dev-loop0.device                                     
 7.816s dev-loop8.device                                     
 7.732s dev-loop12.device                                    
 7.700s dev-loop3.device                                     
 7.700s dev-loop6.device                                     
 6.966s NetworkManager.service                               
 6.879s dev-loop2.device                                     
 6.517s man-db.service                                       
 6.382s avahi-daemon.service                                 
 6.327s iio-sensor-proxy.service 

```

i think this is the most important log if you ever need anything else pls feel free to contact me and i will add it.

about the startup programs i only have slimbook battery saver and i tried shutting it off and it didn't cut anything from the boot time so its effect as zero (it may take less than 1 sec to start)

the system is ubuntu 20.04 Lts 

i am ready to do anything necessary to solve this problem even if it meant to change the entire system although it would be annoying and as i heard ubuntu is the fastest 

Thanks in advance

---

### Post by oldfred on 2020-06-08
It can be a variety of issues. Even a bad entry in fstab where partition now does not exist.
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

I made these changes.
turned off NetworkManager-wait with systemctl
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

But I have a fast NVMe SSD so boot is really quick.

---

