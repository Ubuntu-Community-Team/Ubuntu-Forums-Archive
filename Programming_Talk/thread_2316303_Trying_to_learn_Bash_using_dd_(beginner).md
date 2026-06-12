---
title: "Trying to learn Bash using dd (beginner)"
date: 2016-03-07
forum: Programming Talk
---

### Post by Andreas_Andersson on 2016-03-07
Hi, i am trying to learn bash and now im trying to do a script for burning isos.
I made the number "4" command to make sure the variables were ritgh.

the messege i get when i complete my program and execute dd i.e "command nr 5"

> 
./burn2.sh: line 39: /home/anon/dotsh/sudo dd if=/home/anon/Downloads/OS/Windows/Win10homepro/Win10.iso of=/dev/sdb1 bs=1M: No such file or directory


But i know there is such file there. It does not matther if i put the iso in the script folder either,

```

#!/bin/bash
#set -vx
speed=512K
iso_file="iso.txt"
dev_file="dev.txt"
speed_file="speed.txt"
while true
do
    clear
    echo "============================="
    echo "    Burning menu using dd    "
    echo "============================="
    echo "Enter 1 for full path to iso."
    echo "Enter 2 for media"
    echo "Enter 3 to set bs speed 512K default"
    echo "Enter 4 to save to files"
    echo "Enter 5 to execute dd command"
    echo "Enter q to exit q:"
    echo -e "\n"
    echo -e "Enter your choice \c"
    read -r choice
    case "$choice" in
        q) exit ;;
        1) echo -e "Enter path to iso \c"
           read -r iso ;;
        2) echo -e "Enter device"
           read -r device ;;
        3) echo -e "Enter bs speed \c"
           read -r speed ;;
        4) echo "$iso" > $iso_file
            echo "$device" > $dev_file
            echo "$speed" > $speed_file ;;
        5) echo -e "Going to format $device, are you sure (y/N?) \c"
            read -r $ans
        if [[ "$ans" != "y" && "$ans" != "Y" ]]; then
            echo "Clearing screen"
            sleep 2
            clear
            exec "sudo dd if=$iso of=/dev/$device bs=$speed"
            echo "Burning done!"
            sleep 3
            exit
        fi
    esac
done

```

hope you can help, thanks in advance

---

### Post by Bucky Ball on 2016-03-07
*Thread moved to **Programming Talk**.*

You want to be VERY careful using dd to experiment with. I'd strongly advise you take your learning curve in another direction.

You are aware dd is also known as 'disk destroyer'??? If you get it wrong it will obliterate anything on the target, no questions asked. There are no second chances with dd. You won't be asked 'Are you sure?' or anything like it. Bang. Gone in the time it takes you to think 'Oops, wrong target' or 'wrong command'.

Just thought I'd mention it and make sure you were completely aware of how dd works and what it does. Good luck.

---

### Post by vasa1 on 2016-03-07
And if you want to see how others do it, take a look at the code for mkusb by our very own Sudodus: [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by sudodus on 2016-03-07
Welcome to the Ubuntu Forums :-)

I think this is the error: **of=/dev/sdb[COLOR="#FF0000"]1[/COLOR]**

When you flash an iso file to a USB pendrive (or other mass storage device), the target should be the whole device, not a partition. Use **/dev/sdb** (not /dev/sdb1, no digit).

It seems you are starting with a project similar to what I developed into mkusb, where I wrap a safety belt around dd. Have a look at it! mkusb is also a bash script.

[mkusb wiki/help page](https://help.ubuntu.com/community/mkusb)

[Ubuntu Forums tutorial "Howto make USB boot drives"](http://ubuntuforums.org/showthread.php?t=1958073)

---

### Post by Andreas_Andersson on 2016-03-07
Thanks for the help, but changing the sdb1 to sdb gave me the same error message that the file or folder does not exist.

---

### Post by sudodus on 2016-03-07
I think the problem is with sudo, but not my first guess:
> Are your running it with elevated permissions, with sudo?

```
[COLOR="#0000CD"]**sudo ./burn2.sh**[/COLOR]
```

I don't think regular users are allowed to write to the block device of a mass storage device

```
$ ls -l /dev/sdb
brw-rw---- 1 root disk 8, 16 mar  7 06:07 /dev/sdb
```

I noticed that you use sudo, but you call it with a strange path: **/home/anon/dotsh/sudo**

Try ```
[COLOR="#0000CD"]**sudo ./burn2.sh**[/COLOR]
``` when the current directory is where you store **burn2.sh**, and it has execute permissions, that you get via

```
chmod ugo+x burn2.sh
```

---

### Post by Andreas_Andersson on 2016-03-07
I remade the code and started useing sudo ./burn.sh (i dont know why i did not think of that)

```

#!/bin/bash
#set -vx
speed=512K
iso_file="iso.txt"
dev_file="dev.txt"
speed_file="speed.txt"
while true
do
    clear
    echo "============================="
    echo "    Burning menu using dd    "
    echo "============================="
    echo "Enter 1 for full path to iso."
    echo "Enter 2 for media"
    echo "Enter 3 to set bs speed 512K default"
    echo "Enter 4 to save to files"
    echo "Enter 5 to execute dd command"
    echo "Enter q to exit q:"
    echo -e "\n"
    echo -e "Enter your choice \c"
    read -r choice
    case "$choice" in
        q) exit ;;
        1) echo -e "Enter path to iso \c"
           echo -e "\n"
           read -r iso ;;
        2) echo -e "Enter device"
           echo -e "\n"
           read -r device ;;
        3) echo -e "Enter bs speed \c"
           echo -e "\n"
           read -r speed ;;
        4) echo "$iso" > $iso_file
           echo "$device" > $dev_file
           echo "$speed" > $speed_file
           echo "Informations is saved";;
        5) echo -e "Going to format $device, are you sure (y/N?) \c"
           read -r $ans
           echo "Clearing screen"
           sleep 2
           clear
           exec "dd if=$iso of=/dev/$device bs=$speed"
           echo "Burning done!"
           sleep 3
           exit
    esac
done


```

Getting this error message now

> 
./Burn.sh: line 42: /home/anon/dotsh/dd if=/home/anon/Downloads/OS/Linux/Security/Pentoo2015rc4.iso of=/dev/sdb bs=1M: No such file or directory


---

### Post by sudodus on 2016-03-07
I tried your script in a computer dedicated for testing in order to avoid dd, the 'disk destroyer', to go bärsärk in my production environment ;-)

1. ***The exec command*** adds a path to your current directory, which is not what you want. So ***I removed it***.

***Edit:*** I'm not using exec very often, and I think spjackson's explanation is better than mine. (See the next post.)

2. I also changed the output device to the full name to avoid getting '/dev/dev/sdb'. Of course this is optional.

*. I think it is a good idea to let the script ***unmount*** all partitions on the target device before starting to flash the iso file into it. (I did not add any such command in this test.)

See the diff output:

```
$ diff burn.sh burn0.sh 
42c42
<            dd if="$iso" of="$device" bs="$speed"
---
>            [COLOR="#FF0000"]exec[/COLOR] "dd if=$iso of=[COLOR="#FF0000"]/dev/[/COLOR]$device bs=$speed"
```

The following script:
```

#!/bin/bash
#set -vx
speed=512K
iso_file="iso.txt"
dev_file="dev.txt"
speed_file="speed.txt"
while true
do
    clear
    echo "============================="
    echo "    Burning menu using dd    "
    echo "============================="
    echo "Enter 1 for full path to iso."
    echo "Enter 2 for media"
    echo "Enter 3 to set bs speed 512K default"
    echo "Enter 4 to save to files"
    echo "Enter 5 to execute dd command"
    echo "Enter q to exit q:"
    echo -e "\n"
    echo -e "Enter your choice \c"
    read -r choice
    case "$choice" in
        q) exit ;;
        1) echo -e "Enter path to iso \c"
           echo -e "\n"
           read -r iso ;;
        2) echo -e "Enter device"
           echo -e "\n"
           read -r device ;;
        3) echo -e "Enter bs speed \c"
           echo -e "\n"
           read -r speed ;;
        4) echo "$iso" > $iso_file
           echo "$device" > $dev_file
           echo "$speed" > $speed_file
           echo "Informations is saved";;
        5) echo -e "Going to format $device, are you sure (y/N?) \c"
           read -r $ans
           echo "Clearing screen"
           sleep 2
           clear
           dd if="$iso" of="$device" bs="$speed"
           echo "Burning done!"
           sleep 3
           exit
    esac
done

```

works for me with the following dialogue:
```

lubuntu@lubuntu:~/Downloads$ [COLOR="#0000FF"]sudo ./burn.sh[/COLOR]





















=============================
    Burning menu using dd    
=============================
Enter 1 for full path to iso.
Enter 2 for media
Enter 3 to set bs speed 512K default
Enter 4 to save to files
Enter 5 to execute dd commandI removed it
Enter q to exit q:


Enter your choice [COLOR="#0000FF"]1[/COLOR]
Enter path to iso 

[COLOR="#0000FF"]/isodevice/lubuntu-14.04.2-desktop-i386.iso[/COLOR]









=============================
    Burning menu using dd    
=============================
Enter 1 for full path to iso.
Enter 2 for media
Enter 3 to set bs speed 512K default
Enter 4 to save to files
Enter 5 to execute dd command
Enter q to exit q:


Enter your choice [COLOR="#0000FF"]2[/COLOR]
Enter device


[COLOR="#0000FF"]/dev/sdb[/COLOR]








=============================
    Burning menu using dd    
=============================
Enter 1 for full path to iso.
Enter 2 for media
Enter 3 to set bs speed 512K default
Enter 4 to save to files
Enter 5 to execute dd command
Enter q to exit q:


Enter your choice [COLOR="#0000FF"]5[/COLOR]
Going to format /dev/sdb, are you sure (y/N?) [COLOR="#0000FF"]y[/COLOR]
Clearing screen










1406+0 records in
1406+0 records out
737148928 bytes (737 MB) copied, 143.46 s, 5.1 MB/s
Burning done!
lubuntu@lubuntu:~/Downloads$ 
```

I wrote to a cheap, slow but reliable Sandisk Cruzer Blade - 4 GB pendrive.

[hr][/hr]
Have a look at ***mkusb*** and particularly ***mkusb-nox*** (No X (i.e. text only), this script is simpler than mkusb and a good start to find out how I was thinking).

---

### Post by spjackson on 2016-03-07
> **Andreas_Andersson said:**
> 
```

           exec "dd if=$iso of=/dev/$device bs=$speed"
           echo "Burning done!"
           sleep 3
           exit

```

Because you are quoting a single argument to exec, it is trying to run the program '/home/anon/dotsh/dd if=/home/anon/Downloads/OS/Linux/Security/Pentoo2015rc4.iso of=/dev/sdb bs=1M' with no arguments. You don't have a program called /home/anon/dotsh/dd if=/home/anon/Downloads/OS/Linux/Security/Pentoo2015rc4.iso of=/dev/sdb bs=1M' so you get the error.
Also, if your exec were to succeed, bash stops so it will never execute the echo, sleep and exit.

Just do:

```

           dd "if=$iso" "of=/dev/$device" "bs=$speed"
           echo "Burning done!"
           sleep 3
           exit

```
or rather, try it with something less dangerous than dd, such as /bin/echo, until you understand what it's doing.

---

