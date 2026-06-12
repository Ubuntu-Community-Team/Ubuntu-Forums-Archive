---
title: "Cannot get full resolution on 8.04"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by guitarguy2112 on 2012-01-23
Yes, yes, 8.04 is old school. I've installed it for nostalgic purposes. Anyway...

I'm currently running on an nVidia GeForce GTS 450. I have a 1080p display and my highest supported resolution is 1280x1024. and 74hz refresh. Something about the letterbox look is really hurting my eyes. I'm not really sure where to begin. It's been a long time since I've used Ubuntu... Any help will do! Thank you in advance!:guitar:

---

### Post by guitarguy2112 on 2012-01-23
OK. So I downloaded the drivers from nVidia's website, and try to run the shell script(.run). I get the error "Could not open the file (filename)" gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file. Select a character coding from the menu and try again.

---

### Post by Nick_Kats on 2012-01-23
Hmm...
What is the command you type in order to execute the script?
Also, have you checked the permissions of the script. If not, make sure that you have +x permissions on it.

---

### Post by guitarguy2112 on 2012-01-23
That was it. Permissions. It's unpacking now. Thanks a ton!!!

---

### Post by Nick_Kats on 2012-01-23
> **guitarguy2112 said:**
> That was it. Permissions. It's unpacking now. Thanks a ton!!!

I am glad I helped you :D
Enjoy Ubuntu!

---

### Post by guitarguy2112 on 2012-01-23
Err... Well. It unpacked. Sort of. I tried using hotwire and got this message: 
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 290.10.......................................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.

Apologies. Got ahead of myself in all of the excitement.

In the terminal, if I do a sh (location) it just simply says, Can't open (file)

---

### Post by Nick_Kats on 2012-01-23
> **guitarguy2112 said:**
> Err... Well. It unpacked. Sort of. I tried using hotwire and got this message: 
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 290.10.......................................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.

Apologies. Got ahead of myself in all of the excitement.

No worries :D
Execute it as super user (sudo ./<<script_name>>)

---

### Post by guitarguy2112 on 2012-01-23
"aaron@aaron-desktop:~$ sudo sh NVIDIA-Linux x86_64.10.run
sh: Can't open NVIDIA-Linux"

If I click the actual file itself and open in the terminal it says must be installed as root. I'm sure the answer is crazy obvious here, but it's 5AM where I live and I've been up for 24 hours now. Bare with me! :o

---

### Post by Nick_Kats on 2012-01-23
Why don't you try sudo ./NVIDIA-Linux x86_64.10.run

No problem mate :D

---

### Post by guitarguy2112 on 2012-01-23
aaron@aaron-desktop:~$ sudo ./NVIDIA-Linux x86_64.10.run
sudo: ./NVIDIA-Linux: command not found
aaron@aaron-desktop:~$ sudo sh ./NVIDIA-Linux x86_64.10.run
sh: Can't open ./NVIDIA-Linux

...Am I doing something wrong here?

Omit above. Somehow managed to get it to work sort of... got an error that's referring me to the readme. Something about X server or something....

More edits!!

I ran 
sudo gdm stop
Then did the sh thing as root. It kept looping me back into this same fullscreen msdos looking page. Then I got tired of hitting no and hit yes.
It was like I was in college again. A bad acid trip, man... It took me back to the login page, and I don't think the drivers actually installed.

---

### Post by Nick_Kats on 2012-01-23
I really can't see anything wrong in that.
Why don't you try sudo bash NVIDIA-Linux x86_64.10.run (I do not think it will work either, but it is ok to try).
Try to give all the permissions to the .run file.
If the above won't work either, I do not know anything else to suggest :( sorry mate.

---

### Post by overdrank on 2012-01-23
Hi and if I am not mistaken you will need to cd ( change directory) to where the file it located.
Also you will need build-essential to install the drivers. Which could be a issue with Hardy reach end-of-life.

---

### Post by guitarguy2112 on 2012-01-23
> **Nick_Kats said:**
> I really can't see anything wrong in that.
Why don't you try sudo bash NVIDIA-Linux x86_64.10.run (I do not think it will work either, but it is ok to try).
Try to give all the permissions to the .run file.
If the above won't work either, I do not know anything else to suggest :( sorry mate.

It's the strangest thing. It worked until the acid trip took effect. Now it's doing the same thing.

---

### Post by guitarguy2112 on 2012-01-23
> **overdrank said:**
> Hi and if I am not mistaken you will need to cd ( change directory) to where the file it located.
Also you will need build-essential to install the drivers. Which could be a issue with Hardy reach end-of-life.

Aye, the directory is in the correct spot. 

I do recall having tons of issues with 64bit hardy in the past. Or maybe it was feisty...

Regardless, after that's done, I'm brianfried at the x server point. If you gents would be willing to help, I would be forever in your debt. :D

---

### Post by guitarguy2112 on 2012-01-23
Alright. I can get it to work in hotwire using the same command in terminal. Strange...

But yes, X server.... Err... From the looks of other posts on this forum, I'm scared this may be beyond my expertise unless I have a straight up specific an organized how-to...

---

