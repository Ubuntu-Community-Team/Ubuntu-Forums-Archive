---
title: "LVM - Increase swap partition size..."
date: 2011-10-06
forum: New to Ubuntu
---

### Post by Hendrikdewilde on 2011-10-06
Hi Guys

I added more RAM to my Ubuntu 10.4 Server.
And I did resize my SWAP from 475mb to 4.46 GiB.

But Ubuntu only still see 475mb.

#lvdisplay
  --- Logical volume ---
  LV Name                /dev/devel/swap_1
  VG Name                devel
  LV UUID                LAJiQm-eXAr-D5os-ozde-u21T-EG3v-7x6bAi
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                4.46 GiB
  Current LE             1143
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:1

#free -m
                    total       used       free     shared    buffers     cached
Mem:          3019        1285       1734          0         95           863
-/+ buffers/cache:        325       2694
Swap:           475            0          475

How can I fix this problem?

Thanks
Newbee

---

### Post by Elfy on 2011-10-06
moved to new thread

Please run these and post the results

```
sudo blkid |grep swap
cat /etc/fstab |grep swap
```

Did you reboot? If not you can try

```
sudo swapoff -a
sudo swapon -a
```

---

### Post by Hendrikdewilde on 2011-10-06
#blkid |grep swap
/dev/mapper/devel-swap_1: UUID="974aa8ac-af05-42a6-bd10-315ba30a9d12" TYPE="swap"

#cat /etc/fstab |grep swap
/dev/mapper/devel-swap_1 none            swap    sw              0       0

I did reboot but it didn't help.
No change.

I did not run:
sudo swapoff -a
sudo swapon -a

More Info:
#cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/mapper/devel-swap_1                partition       487416  0       -1

---

### Post by Hendrikdewilde on 2011-10-06
I did run:

**#swapoff -a**

#cat /proc/swaps
Filename                                            Type            Size    Used    Priority

#free -m
                   total       used        free     shared    buffers     cached
Mem:          3019       1329       1689          0        102          899
-/+ buffers/cache:       327       2691
Swap:            0            0            0     

**#swapon -a**
    
#cat /proc/swaps
Filename                                            Type            Size    Used    Priority
/dev/mapper/devel-swap_1                partition       487416  0       -1          

#free -m
                   total       used       free     shared    buffers     cached
Mem:          3019       1330       1688          0        102        899
-/+ buffers/cache:       327       2691
Swap:          475           0          475        

                                          
So it didn't help.

Any other thing I can try?

---

### Post by Elfy on 2011-10-06
Never had very much to do with logical volumes.

You could try changing fstab to use UUID instead of the /dev mapping. Not holding out much hope though tbh.

If you want to do so - backup and edit the file (I assume your using command line with the server, hence the text editor)

```
sudo cp /etc/fstab /etc/fstab.0610
```

Change 

```
/dev/mapper/devel-swap_1
```

to 

```
UUID=974aa8ac-af05-42a6-bd10-315ba30a9d12
```

Then save Ctrl+X, Y and enter

Try the swapoff and swapon commands again

Edit - question - is this encrypted?

---

### Post by Hendrikdewilde on 2011-10-10
Hi

Thanks for the reply.

I did as you said:
# cp /etc/fstab /etc/fstab.1010

# nano /etc/fstab

Change 
/dev/mapper/devel-swap_1 none            swap    sw              0       0

to
UUID=974aa8ac-af05-42a6-bd10-315ba30a9d12 none            swap    sw              0       0


# swapoff -a
# free -m
             total       used       free     shared    buffers     cached
Mem:          3019       2238        780          0        165       1719
-/+ buffers/cache:        353       2665
Swap:            0          0          0                                      

# swapon -a
# free -m
             total       used       free     shared    buffers     cached
Mem:          3019       2239        780          0        165       1719
-/+ buffers/cache:        354       2665
Swap:          475          0        475                                                   

And still the same.
It only see 475mb and not 4450mb.

No, we don't use encryption.

Wouldn't it help if I delete the SWAP partition and re-create it and add it again?
And if so, how would I do it?

Thanks

---

### Post by Elfy on 2011-10-10
You're using LVM are you not - it appears that way. I've not used that but from what I've seen adding partitions is not the same. If it is though then I Would use gparted to do it. 

How did you resize it in the first instance - post #1

---

### Post by Hendrikdewilde on 2011-10-11
Yes, I am using LVM.

I used the following to resize the swap file:
# lvextend -L+4G /dev/devel/swap_1

The problem is that I can't use gparted because The data center where we host in are thousands of miles away. So I can't boot to a CD or use the GUI.

---

### Post by Elfy on 2011-10-11
As I said previously lvm is something I've never needed to look into - that said looking for and at the man page I wonder - and I reiterate that I wonder - what the difference is between the 

lvextend command you used and lvextend (Extend the size of a logical volume)

I have edited the thread title, perhaps someone in the know will see it.

---

### Post by Hendrikdewilde on 2011-10-12
Thanks again for your help so far.

Lets hope someone can help with this problem.

Hendrik

---

