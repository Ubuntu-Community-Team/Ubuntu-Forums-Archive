---
title: "[SOLVED] Movine Home to a seperate disk"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by HittingSmoke on 2008-11-27
Ok, I finally took the last step in converting my PC to 100% Linux by backing up all my data on my NTFS storage drive and converting it to ext3 with the help of these fine folks [http://ubuntuforums.org/showthread.php?t=993489](http://ubuntuforums.org/showthread.php?t=993489)

I've always intended to put my Home partition on this drive but took a lot longer getting around to it then I thought, so now I have a bunch of customizations and packages that i really dont want to do over with a reinstall.

I've found numerous posts and articles on google about moving my home partition while keeping my Ubuntu install in tact but all of them are years old and I was hoping to get some updated info on it.

Is there an easy way to move my Home folder to a new partition?

I'm currently running Hardy and would like to continue to do so without reformatting.

---

### Post by drs305 on 2008-11-27
Have you read this one. It's still good:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

And here is the community documentation (last edited 6 October):
[Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

---

### Post by Locutus_of_Borg on 2008-11-27
In regards to the instruction on psychocats.

When you get to this step: ```
find . -depth -print0 | cpio --null --sparse -pvd /new/
``` before doing that run ```
sudo chown -R YOUR_USER_NAME: /new/
``` elsewise you will get an error since the directory was created as root, and you do not want your user's home directory owned by root

otherwise the instructions work perfectly

---

### Post by HittingSmoke on 2008-11-28
Thanks! I'm giving it a try now and ill post my results.

---

### Post by HittingSmoke on 2008-11-28
> **drs305 said:**
> Have you read this one. It's still good:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

And here is the community documentation (last edited 6 October):
[Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

I tried to second one you posted because it looked like a better way to do it but after the first step when I use
```
sudo mount -a
```
I get this output
```
mount: mount point /media/home does not exist

```

---

### Post by drs305 on 2008-11-28
You must make the mountpoint:
```
sudo mkdir /media/home
```
The error occurs because the mountpoint /media/home does not exist by default until you create it. 
(Note: If you are confusing it with your current *home*, your current home is located at /home/*yourusername*, not /media/home, and /media/home is not a folder that would normally exist ).

In the guide, it says that it will use */media/home* in the examples so once you create it you should be set to follow the rest of the guide. It would be best just to cut & paste unless you have to insert your username or other personal information.

---

### Post by a0u on 2008-11-28
> **HittingSmoke said:**
> I tried to second one you posted because it looked like a better way to do it but after the first step when I use
```
sudo mount -a
```I get this output
```
mount: mount point /media/home does not exist

```

Before you can mount a partition to a directory, that directory must first exist.

For example:
```
sudo mkdir /media/home
```

---

### Post by HittingSmoke on 2008-11-28
> **a0u said:**
> Before you can mount a partition to a directory, that directory must first exist.

For example:
```
sudo mkdir /media/home
```

lol thanks, would have been nice to have that step in the guide :)

Copying stuff now. Cross your fingers.

---

### Post by HittingSmoke on 2008-11-28
Ok, I followed [this]("https://help.ubuntu.com/community/Partitioning/Home/Moving") guide and everything seems to have went smooth except that when I rebooted I got this error message

```
Couldn't find "/media/home/chris".
Please check the spelling and try again.
```
This also pops up every time I open my new Home folder. Did I do something wrong? I seem to have full access to my Home folder and as far as I can tell it's running from my second HDD now.

---

### Post by drs305 on 2008-11-28
Your new home should be /home (and your's specifically at /home/chris). Since you are getting error messages your new home may NOT be where you think it is. 

Try this:
```

touch $HOME/myfile

```
See where the file "myfile" is created (it should be in /home/chris/). THAT is where the system says your home is located.

You can PM me if you have questions or of course post them here.

**Added:** My suspicion is that there is still an entry in fstab still referencing /media/home. Do not remove this entry until you positively ensure this is not still being used as your 'home' folder.

One of the instructions near the end was:
*Edit fstab so that your new home partition actually points to /home, by changing /media/home to /home *

This may not have been completed properly.

---

### Post by HittingSmoke on 2008-11-28
> **drs305 said:**
> Your new home should be /home/chris. Since you are getting error messages your new home may NOT be where you think it is. 

Try this:
```

touch $HOME/myfile

```
See where the file "myfile" is created. THAT is where the system says your home is located.

You can PM me if you have questions or of course post them here.

I ran that command and it did put myfile under /home/chris in Nautilus

But, if I go to /media/home where everything was supposedly moved, there are no files there.

If I right click on my user folder under the Home link in Nautilus and go to properties, it says Volume:unknown but under free space it reports 6.5 GB which would only be true if I was looking at the drive Home is supposed to be on. I know for a fact that the files moved to the right drive, and I'm pretty sure Home (via Nautilus) is pointing to that drive.

And I only got that error twice, when the system first booted after finishing the changes, and once more when I opened up my Home folder. Its not coming up anymore.

I hope I put that in an understandable way, this is all a bit confusing to me. I still don't have the intricacies of the Linux file structure figured out.

---

### Post by HittingSmoke on 2008-11-28
Ok, I rebooted and no error this time.

I think what happened was I rebooted with the /media/home folder open, and after changing the name to /home and rebooting, the system tried to re-open the /media/home folder.

So, as far as I can tell, everything is perfect now. Thanks for the help everyone. It's made this a lot less scary of a transition.

---

