---
title: "Unable to enable POSIX share memory"
date: 2015-03-05
forum: New to Ubuntu
---

### Post by JoeJoeLove on 2015-03-05
Hello,

I'm a complete Linux noob and need some help. I wanted to install new ATI drivers and am supposed to have shared memory enabled. So I got to it and have been trying to figure out how. After some research I stumbled upon this thread: [http://ubuntuforums.org/showthread.php?t=122712](http://ubuntuforums.org/showthread.php?t=122712) with instructions on how to enable it.

Now here is my problem:

When I type **sudo gedit /etc/fstab** and enter my password I get **sudo: gedit: command not found**. 

On some other place in the internet someone suggested that I should use nano instead. After typing **sudo nano /etc/fstab** the file was opened and I typed in the line **# tmpfs /dev/shm tmpfs defaults 0 0***. *I just put it at the bottom. I have no idea if that's how I was supposed to do it. After saving everything I followed the last two steps from the link (**sudo mount /dev/shm** and **sudo mount | grep "shm"**) and got following line after commanding **sudo mount | grep "shm"** : **_none on /run/shm type tmpfs (rw,nosuid,nodev)_**.

I tried multiple times and at this point entering the last command prompts the **none on /run/shm type tmpfs (rw,nosuid,nodev) **message to pop up 6 times in a row. Can someone help me? Did I break it? :(

Regards

JoeJoe

additional Information: I got this Linux second hand from someone that didn't need it anymore, so I have no idea what his settings were before I got it. This is what /etc/fstab looks like from the terminal without editing it (Laptop is in german):

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=125325c3-b3f8-4009-8463-735a528f9331 /               ext4    errors=remo$s=remount-ro 0 
# swap was on /dev/sda5 during installation
UUID=c4b8f289-8bea-453e-af98-f95e1001460a none            swap    sw         $           0       0









                            [ 12 Zeilen gelesen ]
^G Hilfe     ^O Speichern ^R Datei öffn^Y Seite zurü^K Ausschneid^C Textmarke
^X Beenden   ^J Ausrichten^W Wo ist    ^V Seite vor ^U Ausschn. r^T Rechtschr.

edit: I use lubuntu. This is the information on the operating system - system information page:  **Kernel: **Linux 3.13.0-46-generic (i686)
                                                                                                                                **Compiled: **#76-Ubuntu SMP Thu Feb 18:52:49 UTC 2015
                                                                                                                                **Default** **C Compiler: **GNU C Compiler version 4.8.2 (Ubuntu 4.8.2-19ubuntu1
                                                                                                                                  **Distribution: **Ubuntu 14.04.2 LTS

---

### Post by ian-weisser on 2015-03-05
> **JoeJoeLove said:**
> and got following line after commanding **sudo mount | grep "shm"** : **_none on /run/shm type tmpfs (rw,nosuid,nodev)_**.

I tried multiple times and at this point entering the last command prompts the **none on /run/shm type tmpfs (rw,nosuid,nodev) **message to pop up 6 times in a row. Can someone help me? Did I break it?

That's the expected output.
You didn't break it.

That command asks the system for a full list of what is mounted, and then filters for anything containing "/run/shm"
The response tells you "why, yes, there *is *a filesystem that containing that path"

Be careful using instructions that are 9 years old. A lot may have changed.

---

### Post by JoeJoeLove on 2015-03-05
Oh, thank you very much for the response. Wow I really should have looked at the date of that post. 
Does this mean that POSIX shared memory is actually enabled? 
What does the "none on" mean?

I have tried looking it up, but am having trouble understanding anything due to me not being acquainted with the linux terminology... or linux in general for that matter. I am trying to cath up with tutorial videos but haven't found my answers yet.

---

### Post by ian-weisser on 2015-03-05
> **JoeJoeLove said:**
> Oh, thank you very much for the response. Wow I really should have looked at the date of that post. 
Does this mean that POSIX shared memory is actually enabled? 
What does the "none on" mean?

Nobody looks at the date of the post...until the first time it bites them. We all learn.
Yes, POSIX shared memory is enabled (it's enabled by default).
If you're not sure of the previous owner twiddled with arcane settings, feel free to reinstall. It's free and not difficult.

Did you, by chance, try: Software Center --> Software & Updates (or whatever it's called in Lubuntu) --> Additional Drivers
If a proprietary driver is offered, that can be a very easy, supported way to install it.

The straight answer to the rest of your questions: I don't myself know, and will defer to some more knowledgeable gurus on POSIX shared memory.

---

### Post by JoeJoeLove on 2015-03-06
> Did you, by chance, try: Software Center --> Software & Updates  (or whatever it's called in Lubuntu) --> Additional Drivers
If a proprietary driver is offered, that can be a very easy, supported way to install it.

Yes I did. It says that it does not use propietary drivers and that none additional drivers are available.
 Maybe they are already installed for all I know... will have to check on that. 
If not I will keep trying to install them manually and see how that works out. 

Thank you very much for the help. 
If it weren't for you I would probably still be goofing around as root on the terminal and mess up something:P

---

