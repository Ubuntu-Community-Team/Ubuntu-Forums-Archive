---
title: "Exit code 16?"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by Bozihome on 2012-03-20
I'm having a big problem today guys and I want to make this a learning experience but I'm getting a little irritated. I won't get irritated with you guys of course because your helping me but the process in general is frustrating.

Here's my story: My buddy gave me his tower to diagnose what was wrong with it, I boot it up and the hard drive starts making some clicky noises - imminent hard drive failure and the OS (Vista) is having a bunch of problems trying to boot up. I don't have the time to sit around and wait for it to repair itself if its already damaged and there's a ticking clock for the hard drive. My next step is to gain access and back up his data with my favorite live USB distro. I easily boot up in Ubuntu and head to the file manager. The hard drive is titled as OS and my live disc is titled casper-rw. I click on the OS and nothing shows up. I look in the permissions and it only gives me access to create and delete files on the free space of that hard drive. Not good enough, and I try to change the permissions but they automatically force themselves only to create and delete files. I'm locked out of this hard drive.

I try to unmount and remount the hard drive and I get this message:

Unable to mount OS

Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened.
The volume may already be mounted or another software may use it which could be identified for example by the help of 'fuser' command.

I do a bit of research and ask a few questions, and I'm told to try out these commands: 

sudo fdisk -lu

cat /etc/mtab

The results are here: [http://imgur.com/vHRYo,LcU6v,JTFi1#2](http://imgur.com/vHRYo,LcU6v,JTFi1#2)

Since its alot to type, I took a picture of it and posted it on imgur and hopefully you guys can help make something out of it. I know there are other ways to go about this but I want to be more experienced with linux and learn from this experience rather than using mini-XP to get the job done. So give me everything you got to help out, I appreciate it.

---

### Post by oldos2er on 2012-03-20
Closed, duplicate here: [http://ubuntuforums.org/showthread.php?t=1944060](http://ubuntuforums.org/showthread.php?t=1944060)

---

