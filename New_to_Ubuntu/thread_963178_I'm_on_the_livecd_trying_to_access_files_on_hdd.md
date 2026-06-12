---
title: "I'm on the livecd trying to access files on hdd"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-10-30
I'm on 8.04 Live CD trying to access my files on the HDD from 8.10 beta. My computer will not boot to 8.10 so I need to copy the files to a flash drive, but all of them say restricted and permission denied. How do I unlock these files?

---

### Post by brandoncolorado on 2008-10-30
Wait for some other responses (because I am not sure), but are you running the copy command as sudo?

You either didn't put sudo in front of all of those commands, or you're not using the proper username and password. Also, the login you used must be enabled to use sudo. Usually the first login created is given these permissions by default.

cp: The cp command will make a copy of a file for you. Example: "cp file foo" will make a exact copy of "file" and name it "foo", but the file "file" will still be there. If you are copying a directory, you must use "cp -r directory foo" (copy recursively). 

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by ewinslow on 2008-10-30
I'm in the same boat and I just grabbed some files successfully.

Open up a terminal and cd to the root level.
"cd /"
From there create a directory that you can mount your existing hard drive partition that you want to get data off of:
"mkdir mount_dir"
Now mount the desired partition to that just created directory. In my case I needed to grab something off of the root partition which is /dev/sda1 on my machine:
"sudo mount /dev/sda1 /mount_dir"

Now you can cd to "mount_dir" and see your files.
For the stuff you want to take off you'll need to change permissions on them in order to read and copy them.
I just needed one file so I just cd'd to the directory on the partition that was just mounted and changed permissions on that file:
"cd tmp"
"sudo chmod 666 filename_to_copy" (444 should suffice)

Then, with the graphical file browser, Nautilus, I just selected that file, hit Ctrl-C for copy, and pasted it where I wanted it on my USB key.

---

### Post by ImThatNerd on 2008-10-30
> **ewinslow said:**
> I'm in the same boat and I just grabbed some files successfully.

Open up a terminal and cd to the root level.
"cd /"
From there create a directory that you can mount your existing hard drive partition that you want to get data off of:
"mkdir mount_dir"
Now mount the desired partition to that just created directory. In my case I needed to grab something off of the root partition which is /dev/sda1 on my machine:
"sudo mount /dev/sda1 /mount_dir"

Now you can cd to "mount_dir" and see your files.
For the stuff you want to take off you'll need to change permissions on them in order to read and copy them.
I just needed one file so I just cd'd to the directory on the partition that was just mounted and changed permissions on that file:
"cd tmp"
"sudo chmod 666 filename_to_copy" (444 should suffice)

Then, with the graphical file browser, Nautilus, I just selected that file, hit Ctrl-C for copy, and pasted it where I wanted it on my USB key.

I cannot do the command mkdir mount_dir it says permission denied. When I am on the live cd and click '38.3GB Media(my hdd)' then inside that I can navigate to my home folder and desktop and everything like I could when I could launch to 8.04 before. I just need to copy a few folders off the desktop to a desktop and that's it.

---

### Post by bumanie on 2008-10-30
Try the command/s with sudo - making directories etc, needs to be done as super user, as far as I know.

---

### Post by ewinslow on 2008-10-30
> **ImThatNerd said:**
> I cannot do the command mkdir mount_dir it says permission denied. When I am on the live cd and click '38.3GB Media(my hdd)' then inside that I can navigate to my home folder and desktop and everything like I could when I could launch to 8.04 before. I just need to copy a few folders off the desktop to a desktop and that's it.

Yeah, you can see your files, but those are automatically mounted in read-only mode with the Live CD. The standard permissions just give access to a user that doesn't exist in the Live CD environment. That's why you need to create another mount point and mount the partitions off of that.

```

cd /  #drop to the root level of the Live CD environment
mkdir mount_dir  #or try sudo mkdir mount_dir
sudo mount /dev/sda1 /mount_dir  #use the partition you need files from
cd mount_dir/home/username  #going into old home directory for example
sudo chmod 444 *.txt #an example of changing all txt file to world-readable

```

Once that is done you can copy the affected files to your thumb drive, but make sure you access the files through the newly created mount point. Browse to /mount_dir that you'll now see in the file browser. Or just use the command line since you're already in the desired directory: cp *.txt /drive-1/.  
using whatever name was given to your USB drive.

I did this using a 7.10 cd.

Good luck.

---

### Post by ImThatNerd on 2008-10-30
> **ewinslow said:**
> Yeah, you can see your files, but those are automatically mounted in read-only mode with the Live CD. The standard permissions just give access to a user that doesn't exist in the Live CD environment. That's why you need to create another mount point and mount the partitions off of that.

```

cd /  #drop to the root level of the Live CD environment
mkdir mount_dir  #or try sudo mkdir mount_dir
sudo mount /dev/sda1 /mount_dir  #use the partition you need files from
cd mount_dir/home/username  #going into old home directory for example
sudo chmod 444 *.txt #an example of changing all txt file to world-readable

```

Once that is done you can copy the affected files to your thumb drive, but make sure you access the files through the newly created mount point. Browse to /mount_dir that you'll now see in the file browser. Or just use the command line since you're already in the desired directory: cp *.txt /drive-1/.  
using whatever name was given to your USB drive.

I did this using a 7.10 cd.

Good luck.

Thanks for the help, but I did it another way that I just found out. I was surprised I got this my first try since I am the biggest beginner at Ubuntu. In terminal I simply typed: 'sudo nautilus' and navigated to the mount_dir. :) Thanks though!

---

### Post by theolyons on 2009-03-17
hey, i'm having exactly the same problem. I'm running the live CD and don't have the permissions to copy my files to a flash drive.

how exactly did you deal with this? I'm really new to ubuntu, and don't really know how to use terminal, etc...

thanks -- i really really need to get some of these files back!

---

### Post by Arcnsparc on 2010-03-23
I am currently trying to recover files from a bad hdd using a live cd and running into the same permission problem...  any suggestions?

---

### Post by Arcnsparc on 2010-03-23
I used 'sudo chmod -R 666 /dev/sda2' and i got file permissions to work.

---

