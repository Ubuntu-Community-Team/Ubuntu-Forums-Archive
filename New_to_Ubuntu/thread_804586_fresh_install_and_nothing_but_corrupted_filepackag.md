---
title: "fresh install and nothing but corrupted file/package error msgs"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by satanic-yobbo on 2008-05-23
i finished  a fresh hardy install on a brand new system and when i went to run the updates i get nothing but error messages about corrupted package archives saying :

 E: /var/cache/apt/archives/libvlc0_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/libwxbase2.6-0_2.6.3.2.2-2ubuntu4_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/ttf-dejavu-extra_2.23-1_all.deb: corrupted filesystem tarfile - corrupted package archive
 
as i am still relativeley new to linux could anyone give me any ideas on how to fix this please as i wish to prove the guy that built my computer for me yesterday wrong by showing him a great pc does not need windows to make it better but linux to make it perform like it should do

---

### Post by Nepherte on 2008-05-23
Did you retry the update already? Otherwise you might want to choose another mirror.

---

### Post by t0p on 2008-05-23
Ooops! Ignore this

---

### Post by satanic-yobbo on 2008-05-27
re tried all updates and changed source from australian server to main server but this did not do anything for me any other ideas ?

---

### Post by satanic-yobbo on 2008-06-01
...bump

---

### Post by bumanie on 2008-06-01
Did you do a md5checksum on your original .iso download? Did you do a check cd for errors? These are you first steps. If they come up OK, you should try a reinstall and maybe pre-format you hard drive to ext3 via gparted live cd.
I'm from Australia and use a Australian mirror and find I have less downloading problems re updates than when using an overseas mirror.
[Here]("https://help.ubuntu.com/community/HowToMD5SUM") you can learn how to doa md5 checksum. You could also re-burn the .iso at 4x speed to reduce burn errors.

---

### Post by satanic-yobbo on 2008-06-01
yeah i did the checksum and burnt it at low speed and have used this disk to install on 3 different computers now with my own comp. being the only one i had trouble with at all and i have tried 3 different complete re-installations and even tried re-downloading the iso files again but i keep getting error messages that the source could not be read or the one full d/l i got failed the checksum so that kills that idea for now too. I am also from australia and usually use the aussie mirror for this too so ill give it one more shot at d/ling a fresh copy soon and see what happens. cheers for the quick reply too mate

---

### Post by bumanie on 2008-06-01
Have you enabled the repositories as yet, ie software sources and updated them? If they haven't been enabled and updated, you will get error messages.

---

### Post by satanic-yobbo on 2008-06-01
yeah all repo's enabled and it is when i go to update them that i get the errors they tell me i got corrupted tarfiles and packages and the like. is there anyway i can clear the downloaded updates and packages that wont install and re-do it all without doing a fresh install again ?

---

### Post by kansasnoob on 2008-06-01
I never enable the (Source Code) repos anymore, or for that matter the Pre-Released or Unsupported Updates. I used to but got tired of breaking my system.

---

### Post by satanic-yobbo on 2008-06-01
hahahaha yeah thats about the strength of it i should have known that  myself but probably just too eager lol i think i am going to re install again with a new disk from a new d/l thats about 30 mins from finishing so we'll see how that works out

---

### Post by bumanie on 2008-06-01
> I never enable the (Source Code) repos anymore, or for that matter the Pre-Released or Unsupported Updates. I used to but got tired of breaking my system. I guess ensuring they are not enabled is not a bad idea, other than that, at this point in time I'm out of ideas mate. If I think of something I'll message you. Hopefully someone else on the forum will have come across this before and come up with something. Personally, although a bit of a pain, I'd try a reinstall from scratch and format before installing again and format again at the partitioning stage.
> is there anyway i can clear the downloaded updates and packages that wont install and re-do it all without doing a fresh install again ?
 you can uncheck the ones you don't want see what happens, they will keep coming back unless you choose to continue to ignore the packages - I wouldn't do that at this point though. Download the ones you think install OK and go from there. Also ensure you don't have the cd-rom enabled as a source.

---

### Post by Kevbert on 2008-06-01
Best thing is to run the following in terminal:
```
sudo apt-get install -f
sudo apt-get update
```
The first bit of code will repair any incomplete/damaged packages on your PC.

---

### Post by satanic-yobbo on 2008-06-01
ok i ran sudo apt-get install -f and this was the response i got from it which was different than i have been getting from it prior to this 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 172 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up openssh-client (1:4.7p1-8ubuntu1.2) ...
chgrp: cannot access `/usr/bin/ssh-agent': No such file or directory
dpkg: error processing openssh-client (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ssh-askpass-gnome:
 ssh-askpass-gnome depends on openssh-client | ssh (>= 1:1.2pre7-4) | ssh-krb5; however:
  Package openssh-client is not configured yet.
  Package ssh is not installed.
  Package ssh-krb5 is not installed.
dpkg: error processing ssh-askpass-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openssh-client
 ssh-askpass-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

this error code 1 has been a recurring error in the last 3 fresh installs on this particular comp. but not on any other i have used the disk on

---

### Post by Kevbert on 2008-06-01
Before you had the package problem did you get any unexpected crashes on this computer ?  It may be a memory problem, try running memtest for an hour (from either the live CD or grub menu.  It you get any failures it could be a badly fitting memory stick or bad memory.

---

### Post by satanic-yobbo on 2008-06-01
haven't had any troubles before the errors but the memtest idea is a good one anyway cause i haven't done one yet since i bought this machine (silly i know ) was just too eager to get it up and running when i got it built just over a week ago so i will do this as soon as the files i am d/ling finish cheers for the idea

---

### Post by quinnten83 on 2008-06-01
wasn't ssh part of the security bug we had a few weeks ago?
Perhaps something goes wrong when installing.
You can try de-installing ssh in synaptic and reinstalling again. or try a repair broken packages in synaptic.

But I would just do a fresh install with a new CD from a brand spanking new ISO.

---

### Post by satanic-yobbo on 2008-06-01
yeah i am going to go with the brand spanking new install from the brand new iso and see where that takes me. will post back with the results as soon as i finish the procedure

---

### Post by satanic-yobbo on 2008-06-05
ok brand new install from a freshly downloaded iso and still getting errors telling me corrupted filesystem tarfile subprocess paste killed by signal (broken pipe)
subprocess usr/bin/dpkg returned error code 1 and i cannot install any security updates because of this or install any new programs or applications either as anything i try and install gives me the same error

---

### Post by satanic-yobbo on 2008-06-05
ok i have done 2 re-installs tonight in like the past 3 hours and about 6-7 in the past week because of broken packages that couldnt be fixed with the knowledge i have and i cant seem to find anyone that knows whats happening either..i have received a lot of advice but unfortunateley none has helped and i keep getting corrupted package and tarfile errors..i have not changed anything in the sources except for adding 3rd party canonical sources  i am wondering could this be a bigger problem than just bad luck ?? could there be some bigger issue here that i am not finding with my limited experience or knowledge of linux ??

---

