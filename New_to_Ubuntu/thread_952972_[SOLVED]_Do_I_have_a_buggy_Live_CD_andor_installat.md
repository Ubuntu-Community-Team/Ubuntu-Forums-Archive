---
title: "[SOLVED] Do I have a buggy Live CD and/or installation?"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by ranch hand on 2008-10-19
I bought a Live CD to install Ubuntu and I am wondering if it could be a little off.  This is a 3rd party DVD.  I think the outfit has a good reputation.

I have become worried about the main security problem I have, me.  So I post asking about dual booting Ubuntu/Ubuntu.  Got some much better suggestions.

Among other things, a separate partition for my home files.  So I get out the DVD and fire it up that way.  Gparted is there but there is no functionality.

I have  sudo nautilus  ed on occasion.  I did say that I am the security risk.  I have always gotten an error message.

I decided to try that under the DVD and sure enough I get the same thing.

I want to try and make a Live CD of my installation but it would be nice to know that it was basically good before I start.

Here is what I am getting:

** (nautilus:7769): WARNING **: Unable to add monitor: Operation not supported 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory 
Please ask your system administrator to enable user sharing. 

If I go to  File System  and  /var/lib  I do not find  /samba  at all.

I went to synaptic and ran a search for  samba  and found these marked as installed:

libsmbclient,  Nautilus Share,  samba-common,  smbclient

So;  A-What do I do to correct this?  and  B-Is the lack of functionality of gparted under the DVD and the error in nautilus related to a buggy DVD?

Thank you for your time.

---

### Post by mkvnmtr on 2008-10-19
It sounds like maybe you are getting ahead of yourself. I take it you have not installed yet. First boot to the live disk. Then check if the disk is good. There should be an option to check disk. Then if it is good go to the desk top and use several apps just like you will later to check that things work like you want. You don't need to start out changing partitions or altering anything until you are sure Ubuntu works like you want. When you are ready to install defragment you other system a time or two. Then when you start the install from the live disk and get to the partition step pause and study what you options are. At that point if you are not sure back out and come back to the forums to ask how to do what you want. You can get to the partition step 20 and back out without hurting anything. Don't proceed to format until you are sure you have it like you want. The first time I installed I got to that step 6 or 7 times before I was sure.

---

### Post by Pro-reason on 2008-10-19
Do you wish to set up a Samba network?

---

### Post by ranch hand on 2008-10-19
mkvnmtr;  Well, I sure was not clear on that at all.  I am running on nothing but Ubuntu 8.04.1.  It is installed on a Dell XPS 420 that we bought to replace our old computer.
It came with Vista installed.

I left Vista alone, for emergency use, and put in another HDD and unplugged the one with Vista on it.  Hardy is a much better OS.

This box has a quad core CPU 240 GHz, 320Gb WD HDD, 3Gb ram.

With that "little" ram, Vista wrote to the swap files all the time.  Have never used more than 20% with Hardy and that was doing some heavy work in Gimp on several large (4 to 5 meg) images with at least 6 up at once.

I just want to get a way to have the system rebootable so I can play with it in my ignorance and maybe be able to recover.

I will admit to clean reinstalling 4 times because of my doing thing I don't understand.  This is a fine way to learn but has draw backs if you want to keep files.

---

### Post by ranch hand on 2008-10-19
Pro-reason;  I do not want to set up a samba network.  Well maybe I would but I don't know what it is.  I just want to get rid of the error message.

---

### Post by oldos2er on 2008-10-19
When you first boot the Live CD, there's a menu option to 'Check CD for defects.' You should run that before doing anything else.

---

### Post by ranch hand on 2008-10-19
I will do that tomorow some time.  No time tonight, should be in bed.

Vet coming in morning to do health inspection on our calves so we can ship Wednesday.  I need the trailer on the truck, horse sadled, loaded by 7:30 (sun up at 7:25).  Vet at could be here any timefrom then to 8.  Do calves here.  Go to other end of ranch (10 miles) check calves there.  Vet leaves.  Some nieghbors coming to sort some of their pairs off (fenses sometimes leak) about 9.

Another thing I am going to do is get the error message (I forgot this one) that I got when I tried to configure my modem under the Live CD.  I tried it after install and knew all the settings to see if it worked but there was a problem.

Thanks again, I didn't really remember that option just the mem test.

I'll git er done.

---

### Post by ranch hand on 2008-10-27
I have have had a busy week shipping calves, enjoy your beef.

It really helps if you CLEAN your CD every once in a while.  Ran the CD check and it is amazing what a difference a soft cloth will make.

Gparted worked great.

Thanks

---

