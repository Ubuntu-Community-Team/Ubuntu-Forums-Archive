---
title: "NVIDIA Driver"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by pras8421 on 2012-05-04
Hi,
I have upgraded ubntu 11.10 to 12.04 recently and I installed NVIDIA driver latest version 295.40(I'm not sure of the number).
I just wanted to know how to use it.

---

### Post by strask on 2012-05-04
Look for a program in your applications called "NVIDIA X Server Settings". :)

---

### Post by pras8421 on 2012-05-04
When I try to run this x-config settings I will get error message.I've uploaded the screen shot.

I tried to run this as root.First I got a warning.Then I got this.....

prasanna@ubuntu:~$ sudo nvidia-xconfig
[sudo] password for prasanna: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf' 

I tried again,I got the same error message...

---

### Post by pras8421 on 2012-05-04
After the reboot it the screen resolution got changed completely.....
Now the screen is as if it's trimmed on both the sides.....
I couldn't even see the resolution option...

---

### Post by mörgæs on 2012-05-04
For the time being it's best to stick to the open-source Nvidia drivers. The closed-source ones are buggy:

[http://ubuntuforums.org/showthread.php?t=1959416](http://ubuntuforums.org/showthread.php?t=1959416)

---

### Post by pras8421 on 2012-05-04
Okay.How can I disable NVIDIA graphics options?

---

### Post by pras8421 on 2012-05-04
Can I overcome this by removing NVIDIA driver?
Can you suggest me how to remove......

---

### Post by zombifier25 on 2012-05-04
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch)
Note: If I read correctly, the last step should be ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by grahammechanical on 2012-05-04
You say that you installed the Nvidia driver. How? How did you do this?

It is usual to use the Additional Drivers utility. When we select one of the drivers to activate, the utility will download and install the Nividia driver for us. It will do all the work. We do not need to do anything to use the driver. Except reboot.

The first error message indicates that the driver was not activated.

Early this morning I installed 12.04 on another partition with the purpose of converting it into 12.10 development branch. By using Additional Drivers and rebooting (just that and nothing else) I am now running Nvidia 295.40 and I get the Ubuntu 3D effects. And the Nvidia X Server Settings utiltyn is filled with useful information.

Regards.

---

### Post by pras8421 on 2012-05-04
Ha ha..that's true...After all it's a machine...
I installed by running the following commands

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

---

### Post by kryten2k35 on 2012-05-04
Don't you just type nvidia-settings in the terminal?

---

### Post by pras8421 on 2012-05-04
But display property is very poor now.....I can't even see the the options at the extreme ends and some get overlapped...
If you observe the minimize and maximize options at the left top corner in the following screen shot,they are overlapped...

Moreover,the maximum resolution of my laptop is 1366x768(I'll get in windows)...If am correct,I used to get the same in ubuntu as well,but I'am not sure...
However,it's,of course not less than 1024x768....But if I run xrandr it shows maximum resolution as 800x600(current resolution as well as the same)....Is this the max. resolution attached to NVIDIA GPU???

---

### Post by kryten2k35 on 2012-05-04
> **pras8421 said:**
> But display property is very poor now.....I can't even see the the options at the extreme ends and some get overlapped...
If you observe the minimize and maximize options at the left top corner in the following screen shot,they are overlapped...

Moreover,the maximum resolution of my laptop is 1366x768(I'll get in windows)...If am correct,I used to get the same in ubuntu as well,but I'am not sure...
However,it's,of course not less than 1024x768....But if I run xrandr it shows maximum resolution as 800x600(current resolution as well as the same)....Is this the max. resolution attached to NVIDIA GPU???

hmm type nvidia-settings --mode=1366x768

---

### Post by pras8421 on 2012-05-04
I got this typing  nvidia-settings in the terminal(shown in the screenshot)......
When I type nvidia-settings --mode=1366x768,I got
prasanna@ubuntu:~$ nvidia-settings --mode=1366x768
nvidia-settings: unrecognized option: "--mode"

ERROR: Invalid commandline, please run `nvidia-settings --help` for usage
       information.

prasanna@ubuntu:~$

---

### Post by pras8421 on 2012-05-04
One more thing.......I removed nvidia settings from startup applications and restarted the system...The resolution became worse i.e., 640x480,I guess....Again I restarted in recovery mode and the display resolution got increased to 800x600..

The same thing had happened when I had restarted the system after installing the driver..I'd done the same thing and the resolution had been increased...However I'd not removed NVIDIA settings from startup.........
How should I get the optimal resolution back?

---

### Post by pras8421 on 2012-05-04
Else can you please at least suggest me to increase the screen resolution??????

---

