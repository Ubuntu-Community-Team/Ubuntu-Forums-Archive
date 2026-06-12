---
title: "How do I solve &quot;unrecognised disk label&quot;"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by djmiles on 2013-01-10
There are a few glitches in my newly setup Ubuntu 12.10 Server install. Here is one I can't work out how to solve.

On boot, something like this message appears
the disk drive for dev/mapper/ubuntu-swap_1 is not ready

I found some guides that suggested the following steps
swapon -s
fdisk -l
parted /dev/sda print all

The results are included below. The last command produces this line
"Error: /dev/mapper/ubuntu-swap_1: unrecognised disk label" which is obviously related to my boot issue, but I have no idea how to resolve this.

Help?

sudo swapon -s
Filename                                Type            Size    Used    Priority                                                                                                               
/dev/mapper/cryptswap1                  partition       3133436 0       -1     
***************************************************
sudo fdisk -l                                                                                                                                                                                                
Disk /dev/sda: 250.1 GB, 250059350016 bytes                                                                                                                                                    
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors                                                                                                                          
Units = sectors of 1 * 512 = 512 bytes                                                                                                                                                         
Sector size (logical/physical): 512 bytes / 512 bytes                                                                                                                                          
I/O size (minimum/optimal): 512 bytes / 512 bytes                                                                                                                                              
Disk identifier: 0x0007b74e                                                                                                                                                                    
                                                                                                                                                                                               
   Device Boot      Start         End      Blocks   Id  System                                                                                                                                 
/dev/sda1   *        2048      499711      248832   83  Linux                                                                                                                                  
/dev/sda2          501758   488396799   243947521    5  Extended                                                                                                                               
/dev/sda5          501760   488396799   243947520   8e  Linux LVM                                                                                                                              
                                                                                                                                                                                               
Disk /dev/mapper/ubuntu-root: 246.6 GB, 246587326464 bytes                                                                                                                                     
255 heads, 63 sectors/track, 29979 cylinders, total 481615872 sectors                                                                                                                          
Units = sectors of 1 * 512 = 512 bytes                                                                                                                                                         
Sector size (logical/physical): 512 bytes / 512 bytes                                                                                                                                          
I/O size (minimum/optimal): 512 bytes / 512 bytes                                                                                                                                              
Disk identifier: 0x00000000                                                                                                                                                                    
                                                                                                                                                                                               
Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table                                                                                                                           
                                                                                                                                                                                               
Disk /dev/mapper/ubuntu-swap_1: 3208 MB, 3208642560 bytes                                                                                                                                      
255 heads, 63 sectors/track, 390 cylinders, total 6266880 sectors                                                                                                                              
Units = sectors of 1 * 512 = 512 bytes                                                                                                                                                         
Sector size (logical/physical): 512 bytes / 512 bytes                                                                                                                                          
I/O size (minimum/optimal): 512 bytes / 512 bytes                                                                                                                                              
Disk identifier: 0x00000000                                                                                                                                                                    
                                                                                                                                                                                               
Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table                                                                                                                         
                                                                                                                                                                                               
Disk /dev/mapper/cryptswap1: 3208 MB, 3208642560 bytes                                                                                                                                         
255 heads, 63 sectors/track, 390 cylinders, total 6266880 sectors                                                                                                                              
Units = sectors of 1 * 512 = 512 bytes                                                                                                                                                         
Sector size (logical/physical): 512 bytes / 512 bytes                                                                                                                                          
I/O size (minimum/optimal): 512 bytes / 512 bytes                                                                                                                                              
Disk identifier: 0x363c3c51                                                                                                                                                                    
                                                                                                                                                                                               
Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
*************************************************
sudo parted /dev/sda print all                                                                                                                                
Model: ATA TOSHIBA MK2546GS (scsi)                                                                                                                                                             
Disk /dev/sda: 250GB                                                                                                                                                                           
Sector size (logical/physical): 512B/512B                                                                                                                                                      
Partition Table: msdos                                                                                                                                                                         
                                                                                                                                                                                               
Number  Start   End    Size   Type      File system  Flags                                                                                                                                     
 1      1049kB  256MB  255MB  primary   ext2         boot                                                                                                                                      
 2      257MB   250GB  250GB  extended                                                                                                                                                         
 5      257MB   250GB  250GB  logical                lvm                                                                                                                                       
                                                                                                                                                                                               
                                                                                                                                                                                               
Model: Linux device-mapper (crypt) (dm)                                                                                                                                                        
Disk /dev/mapper/cryptswap1: 3209MB                                                                                                                                                            
Sector size (logical/physical): 512B/512B                                                                                                                                                      
Partition Table: loop                                                                                                                                                                          
                                                                                                                                                                                               
Number  Start  End     Size    File system     Flags                                                                                                                                           
 1      0.00B  3209MB  3209MB  linux-swap(v1)                                                                                                                                                  
                                                                                                                                                                                               
                                                                                                                                                                                               
Error: /dev/mapper/ubuntu-swap_1: unrecognised disk label                                                                                                                                      
                                                                                                                                                                                               
Model: Linux device-mapper (linear) (dm)                                                                                                                                                       
Disk /dev/mapper/ubuntu-root: 247GB                                                                                                                                                            
Sector size (logical/physical): 512B/512B                                                                                                                                                      
Partition Table: loop                                                                                                                                                                          
                                                                                                                                                                                               
Number  Start  End    Size   File system  Flags                                                                                                                                                
 1      0.00B  247GB  247GB  ext4

---

