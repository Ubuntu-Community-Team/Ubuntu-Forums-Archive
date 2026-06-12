---
title: "fstab script... help!?"
date: 2010-06-08
forum: Programming Talk
---

### Post by Cypher2 on 2010-06-08
Kind of bugged by the works of this little command sample i'm making to automate the mounting of my drive partitions upon install according to wether it is my desktop (MERCURY) or my laptop (SOLACE)...

It seems to work fine for the first case but not for second or third...

any help please?

thanks!

---------------------

# !/bin/bash
if hostname="MERCURY"
then
sudo echo /dev/sdb1 /media/Disk ext4 defaults 0 0 | sudo tee -a /etc/fstab
elif hostname="SOLACE"
then
sudo echo /dev/sda2 /media/Disk ext4 defaults 0 0 | sudo tee -a /etc/fstab
else
echo "Unknown hostname... Aborting"
fi

------------------------------------------

---

### Post by slavik on 2010-06-08
use 'else if' instead

---

### Post by Cypher2 on 2010-06-08
thank you.. i will try it out...

code should look like this?:

---------------

# !/bin/bash
if hostname="MERCURY"
then
sudo echo /dev/sdb1 /media/Disk ext4 defaults 0 0 | sudo tee -a  /etc/fstab
else if hostname="SOLACE"
then
sudo echo /dev/sda2 /media/Disk ext4 defaults 0 0 | sudo tee -a  /etc/fstab
else
echo "Unknown hostname... Aborting"
fi

--------------

---

### Post by Cypher2 on 2010-06-08
I've tried the new code as follows:

_____________________

# !/bin/bash
if hostname="MERCURY"
then
sudo echo /dev/sdb1 /media/Disk ext4 defaults 0 0 | sudo tee -a /etc/fstab
else if hostname="SOLACE"
then
sudo echo /dev/sda2 /media/Disk ext4 defaults 0 0 | sudo tee -a /etc/fstab
else
echo "Unknown hostname... Aborting"
fi
fi

____________

I've modified the hostname via the terminal to match the second case and it still does not echo the /dev/sda2 line to fstab as demanded...

any tip on how to solve this - I know for a fact that the easier it is, the harder it can be to find the error...

Thanks

---

### Post by hannaman on 2010-06-09
Try use the test brackets around the expression and backticks around hostname to run the command, like:
```
if [ `hostname` = "MERCURY" ]; then
   echo "..."
elif [ `hostname` = "SOLACE" ]; then
   echo "..."
else
   echo "..."
fi
```
Also, I would remove the sudo statements from inside the script and just run the script with sudo instead.

---

### Post by disabledaccount on 2010-06-09
> **Cypher2 said:**
> 
... echo /dev/sdb1 /media/Disk ext4 defaults 0 0
This is very "dirty" and unsafe method of creating fstab entries.
First of all, you should not use sata lib names to identify partitions -> the right way is to use its UUID. You can get into situation, where your sdb1 not exist, or it is completely different partition, f.e. your /(root). This is possible, because sd[] refers to bios device list, wich may be wrong in many situations.

Right way:
- list your partitions using blkid or >ls -l /dev/disk/by-uuid
- check if your filesystem (partition) is present on the list
- append fstab line, that refers to filesystem UUID or Label.

---

### Post by Cypher2 on 2010-06-09
Thank you for the responses.. I will try out the test bracket method...

As for the "dirty" way to do it... if i recall, pysdm uses that same input type to fstab.. I did not and still wouldn't know how to input by UUID  :(

Just a beginner here...

any tip to make it safer is much appreciated then

EDIT: the test brackets work perfect :D thank you so much... I'll try looking into the UUID subject in depth

---

### Post by disabledaccount on 2010-06-09
> **Cypher2 said:**
> I did not and still wouldn't know how to input by UUID  :(

any tip to make it safer is much appreciated then

This is really simple, take look at example:
```
#!/bin/bash

#search for:
path="/dev/disk/by-label"
fs_label="UsrData1" #your partition
#read dir:
fs_list=( $(ls /dev/disk/by-label) )
#check if filesystem label exist:
for  fs_entry in ${fs_list
[*]}; do
    if [ "$fs_entry" = "$fs_label" ]; then
        #optional log entry:
        echo "++ fstab entry: "$fs_entry >>/some/install_logfile
        #fstab entry:
        echo "LABEL="$fs_label" /home/all_users/disk1 ext4 defaults 0 2" >>/etc/fstab
        break
    fi
done
exit 0
```This is for label, UUID would be the same, only change dir to /by-uuid and keyword "LABEL" to ..."UUID" of course ;)
How to get filesystem label or uuid: this depends on filesystem, for EXT you should use tune2fs tool.

---

### Post by Cypher2 on 2010-06-09
so basically this piece of code:

-sets the working path
-sets the filesystem labeling as UDx (shouldnt it be SDx?)
-read the given directory by uuid
-checks if the uuid label exists to the corresponding uuid
-sets the fstab entry by uuid to /home/all_users/disk1 (for me it      
 would be /media/Disk)

the purpose is that i have fixed names for my machines... shouldnt i implement some kind of " for MACHINE = UUID" then set the script?

Thank you for taking time to explain :)

Heres what I whiped up from your example and explanations to fit my needs :confused::
______

#!/bin/bash

path="/dev/disk/by-uuid"
fs_label="UsrData1"
	fs_list=( $(ls /dev/disk/by-uuid) )
		for  fs_entry in ${fs_list[*]}; do
		if [ "$fs_entry" = "$fs_label" ]; then
			echo "UUID="$fs_label" /media/Disk ext4 defaults 0 0" | tee -a /etc/fstab
		break
	fi
done
exit 0

_____

---

### Post by disabledaccount on 2010-06-10
> **Cypher2 said:**
> so basically this piece of code:
-sets the filesystem labeling as UDx (shouldnt it be SDx?)

?? well, no - this is just label, "friendly name" of the filesystem -> you can name it "My_Cat" if you wish :) , but this must be real label that your filesystem use.
In case of using UUID,  propably renaming fs_label to fs_id or fs_uuid will make it more readable...
But, like I said before: you can use just label - under one condition, that it will be unique among your filesystems/partitions.

...again, with resolving hosts names and additionally - mount points:
```
#!/bin/bash

#which host:
case "$HOSTNAME in
     "MERCURY")
          fs_id=12345678-1234-5678-abcd-123456789abc
          mntpoint=/media/disk ;;
     "SOLACE")
          fs_id=12345678-1234-5678-abcd-123456789abc
          mntpoint=/home/disk ;;
     *)
          exit 1 ;; # <unknown host>          
esac
#search in:
path="/dev/disk/by-uuid"
#read dir:
fs_list=( $(ls $path) )
#check if filesystem exist:
for  fs_entry in ${fs_list
[*]}; do
    if [ "$fs_entry" = "$fs_id" ]; then
        #optional log entry:
        echo "++ fstab entry: "$fs_entry >>/some/install_logfile
        #fstab entry:
        echo "UUID="$fs_id" "$mntpoint" ext4 defaults 0 2" >>/etc/fstab
        break
    fi
done
exit 0
```

---

