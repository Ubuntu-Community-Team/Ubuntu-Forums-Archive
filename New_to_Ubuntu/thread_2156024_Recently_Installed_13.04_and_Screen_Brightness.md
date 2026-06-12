---
title: "Recently Installed 13.04 and Screen Brightness"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by JavaBeansAndOreos on 2013-06-20
Hello,

I'm running Ubuntu 13.04 from inside Windows 7 (using wubi). When I boot up with Ubuntu, I initially see a screen that allows me to select either "Ubuntu" or some Advanced Options. After I select "Ubuntu", I hear the familiar startup sound but there's a very very dim screen (nearly black). I cannot, under ordinary circumstances, navigate myself to a desktop with a screen that is not dimmed. 


The brightness buttons on my keyboard do not have any effect on the screen's brightness. I've read countless threads, here and elsewhere, and I believe that I've narrowed down the problem.

First, let me list a few things that I have already tried. 

(0) Yes, I understand wubi is quirky. But it's what I'm used to, so I'd like to continue using it.
(1) I had to type in "nomodeset" in place of "quiet splash" just to get access to a desktop that I can actually see and use.
(2) In Software & Updates, the "Additional Drivers" tab is blank. My computer has Intel drivers, not NVidia. So I doubt it's a driver problem.
(3) I removed lightdm, but that caused more problems, resulting in another fresh install.
(4) I've also tried **acpi_backlight=vendor **with no luck.

This thread: [http://ubuntuforums.org/showthread.php?t=1855199](http://ubuntuforums.org/showthread.php?t=1855199) has given me the most insight thus far. As suggested by Toz, I've run the following commands in the terminal:

```


lsmod | grep ^i915

Which returns:i915    600396  0 


```

And...
```


sudo add-apt-repository ppa:kamalmostafa/linux-kamal-mjgbacklight


```

And...
```


sudo apt-get update

```

And...
```


sudo apt-get dist-upgrade


```

All of which appeared to return the proper values and install the right updates, etc. However, after rebooting nothing was noticably any different.

Toz told the OP to run some commands that return the values of the screen brightness. After doing so, the OP was able to correct his/her problem by editing the screen brightness value (640) into the a file using the line:

```


echo 640 > /sys/class/backlight/intel_backlight/brightness

```

I tried the same command, but after rebooting, nothing was different. Then I took a look into my brightness files, which have the paths:

 sys/class/backlight/acer-wmi/actual_brightness (with a value of 9)
sys/class/backlight/acer-wmi/bl_power (with a value of 0)
sys/class/backlight/acer-wmi/brightness (with a value of 9)
sys/class/backlight/acer-wmi/max_brightness (with a value of 9)

All of which have values considerably smaller than 640, for instance. I tried a few ways to correct this:

(1) By typing...
```

echo 640 | sudo tee /sys/class/acer-wmi/brightness

Which returned: tee: /sys/class/backlight/acer-wmi/brightness: Invalid argument

```

(2) By typing...
```

sudo gedit /sys/class/backlight/acer-wmi/brightness

```

And attempting to edit the file and change the value of 9 into 640. But when I try to save the file it says: Could not create a backup file while saving /sys/class/backlight/acer-wmi/brightness. And will not let me save.

I'm fresh out of ideas. If anyone could help me hard code the proper values into these files, or help in some other fashion, it would be greatly appreciated. Thanks in advance!

---

### Post by 2F4U on 2013-06-20
> 
echo 640 > /sys/class/backlight/intel_backlight/brightness

No wonder this setting was lost upon the next boot since the /sys filesystem is not permanent, i.e. you have to apply the setting on every restart of the machine, either through a service or a script that runs during or at the end of the boot process. Usually, this can be achieved by adding such commands to /etc/rc.local:

[http://unix.stackexchange.com/questions/59929/whats-the-difference-between-etc-rc-local-and-etc-init-d-rc-local](http://unix.stackexchange.com/questions/59929/whats-the-difference-between-etc-rc-local-and-etc-init-d-rc-local)

---

### Post by Toz on 2013-06-20
Note that the PPA you reference was only valid for older releases of Ubuntu, not the version that you are running. In fact, alot of those changes have already been included in the newer kernel versions.

I would also suggest giving the following kernel parameters a try (one set at a time - make sure you run "sudo update-grub" and reboot with each attempt):
- **acpi_osi=Linux acpi_backlight=vendor**
- **acpi_osi=**
- **acpi_osi=\"!Windows 2012\"**

As for echoing values into the backlight interface files, your interface is called acer_wmi and holds a maximum value of 9. You should try something like:
```
echo 3 | sudo tee /sys/class/backlight/acer-wmi/brightness
echo 5 | sudo tee /sys/class/backlight/acer-wmi/brightness
echo 7 | sudo tee /sys/class/backlight/acer-wmi/brightness
```
...and see if it makes a difference.

If either of the kernel parameters allow your brightness keys to function again, then you are good to go.
If echoing the values works, you can follow @24FU's advice and make the change permanently in /etc/rc.local. Or, a workaround script can be created to give you the ability to change the brightness on the fly.

You neglect to mention the make and model of your notebook (an Acer of some sort?). It might be helpful to see if there are known issues related to it.

And by the way, welcome to the forums.

---

### Post by JavaBeansAndOreos on 2013-06-20
First of all, thank you both for the relpies. Ubuntu wouldn't be the OS that it is wihtout people like you helping people like me. And thank you Toz for the welcome.


The second kernel parameter "**acpi_osi=**" worked for me. It's beautiful. And I have a Gateway NV78, just in case anyone else is having similar trouble on a similar machine. My brightness buttons now work, but they are inverted, haha. Up turns the brightness down, and vice versa. But I'll take it!

Thank you again!

Also, I'm not sure how to mark the thread as [Solved]. If someone could point me in the right direction, I shall do it.

---

### Post by Toz on 2013-06-20
Glad to hear.

To mark a thread as solved:
1. Click on the "Edit" button in your _first_ post in this thread.
2. Click on "Go Advanced".
3. Change the value in the Prefix dropdown to "[SOLVED]".
4. Click on the Save button.

---

