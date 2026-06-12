---
title: "Problem modifying file in /sys"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by hydrurga on 2008-11-26
I apologise wholeheartedly for posting this on the Ubuntu forum but I've already tried the Puppy and Linux forums without success, and I was wondering whether any of you guys might be able to help. It may well be a general Linux problem. As you may have guessed, I am a Linux newbie...

In order to get wireless to work on my Amilo Li1718 under Puppy 4.1.1 (full hard disk install), I need to load a module called acer-wmi to do two things: (i) enable the wireless adapter, (ii) switch on the PC's wireless button. I therefore run 'modprobe acer-wmi' which appears to work fine and enables the wireless adapter.

The problem is that, in order to switch on the button, I have been advised to change the contents of a file called 'wireless' created by that module in a /sys subdirectory, using the command 'echo 1 > /sys/devices/platform/acer-wmi/wireless'. Simply, this doesn't work, and any attempts to modify this file fail. In fact the original file, as created by the modprobe, is created as a 4096 byte sized file but then as soon as I try to write to it or modify it in any way it becomes a 0 byte sized file. In fact, experimentation has shown that I cannot change any file in the /sys branch. Trying to load the module with 'modprobe acer-wmi wireless=1' does not work.

I have searched about and noticed that many people seem to have successfully been able to echo data into files in /sys. Why is it that I can't? With Puppy, everyone runs as root so I don't think that it is a question of permissions.

Pete

---

### Post by Diabolis on 2008-11-26
Do you get any error messages?

I would do it like this:
```
sudo echo 1 > /sys/devices/platform/acer-wmi/wireless
```

Notice that in your command **">"** means overwrite the content of the file with a 1. Thats why the file size changes. If you want to append the 1, then use **">>"**.

The echo command is just writing text to your file. Maybe you'll find it easier to open the file with a text editor and modify it yourself.
```
sudo gedit /sys/devices/platform/acer-wmi/wireless
```

---

### Post by aeiah on 2008-11-26
by fail, what do you mean? what error is produced when you attempt to do this? and could you show us where the tutorial or discussion is that told you to do this, it might make it a bit clearer.

---

### Post by hydrurga on 2008-11-27
Sorry for the delayed reply Diabolis and aeiah - many thanks for your posts!

Puppy is by default a single user system where that user is root - sudo isn't available (as far as I know) or necessary.

Here are my steps along with all responses:

> # modprobe acer-wmi

# ls -l /sys/devices/platform/acer-wmi/wireless

-rw-rw-rw- 1 root root 4096 2008-11-28 01:00 /sys/devices/platform/acer-wmi/wireless

#cat /sys/devices/platform/acer-wmi/wireless

0

# echo 1 > /sys/devices/platform/acer-wmi/wireless

# ls -l /sys/devices/platform/acer-wmi/wireless

-rw-rw-rw- 1 root root 0 2008-11-28 01:02 /sys/devices/platform/acer-wmi/wireless

# cat /sys/devices/platform/acer-wmi/wireless

0

# geany /sys/devices/platform/acer-wmi/wireless

<shows a single digit 0 - nothing can be added/modified> - at foot of window "The file /sys/devices/platform/acer-wmi/wireless" could not be opened properly and has been truncated. This can occur if the file contains a NULL byte. Be aware that saving it can cause data l...".

# geany /sys/devices/platform/acer-wmi/temp
<enter a single digit 1 and click Save> -"Error saving file (no such file or directory)" 

If I use the >> redirect as suggested by Diabolis then exactly the same occurs as listed above but the resulting Wireless file remains at 4096 bytes.

My original post on the Puppy forum, including the advice and a link to further information, is at [http://www.murga-linux.com/puppy/viewtopic.php?p=251218#251218](http://www.murga-linux.com/puppy/viewtopic.php?p=251218#251218).

Thanks guys, I really appreciate your help on this. Please let me know of any further info that you need.

Pete

---

### Post by Diabolis on 2008-11-28
Did you try the solution offered in the Puppy linux forums, this one:
```
rmmod acer-wmi
modprobe acer-wmi wireless 1
```

As I understand, all the files in the diretory /sys are created dinamically by the drivers and kernel. That could be the reason why you are having trouble at editing one of them.

You can also copy a file to the directory. Create the **wireless** file in your home folder and then copy it.
```

echo > 1 ~/wireless
cp ~/wireless /sys/devices/platform/acer-wmi/

```

---

### Post by hydrurga on 2008-11-28
> **Diabolis said:**
> Did you try the solution offered in the Puppy linux forums, this one:
```
rmmod acer-wmi
modprobe acer-wmi wireless 1
```

As I understand, all the files in the diretory /sys are created dinamically by the drivers and kernel. That could be the reason why you are having trouble at editing one of them.

You can also copy a file to the directory. Create the **wireless** file in your home folder and then copy it.
```

echo > 1 ~/wireless
cp ~/wireless /sys/devices/platform/acer-wmi/

```

Thanks Diabolis. Here is what happened...

> 
# modprobe acer-wmi wireless 1
FATAL: Error inserting acer_wmi (/lib/modules/2.6.25.16/kernel/drivers/misc/acer-wmi.ko): Invalid argument


> 
# cd /root/my-documents
# echo 1 > wireless
# cat wireless
1
# modprobe acer-wmi
# ls -l /sys/devices/platform/acer-wmi/wireless
-rw-rw-rw- 1 root root 4096 2008-11-28 18:08 /sys/devices/platform/acer-wmi/wireless
# cp wireless /sys/devices/platform/acer-wmi
# ls -l /sys/devices/platform/acer-wmi/wireless
-rw-rw-rw- 1 root root 0 2008-11-28 18:08 /sys/devices/platform/acer-wmi/wireless
# cat /sys/devices/platform/acer-wmi/wireless
0


Pete

---

### Post by Diabolis on 2008-11-30
> 
Goodness knows why I have different results on the two computers given that I did a full install of Puppy Linux 4.1.1 from the same Live CD on both. The only difference between the two computers that I can see, apart from hardware, is that the one where modprobe acer-wmi actually succeeds is a grub-loaded multi-partition with Puppy and Vista, whereas the other machine is a grub-loaded single partition Puppy machine.[quote]("http://www.murga-linux.com/puppy/viewtopic.php?p=252939&sid=7e62938a8bb0051a35791f3c2721d391")

Hardware is all what matters, so your machines have different network cards. To find out which one you have type:
```
lspci | grep Network
```

Does **dmesg** shows additional information or the same fatal error?

---

