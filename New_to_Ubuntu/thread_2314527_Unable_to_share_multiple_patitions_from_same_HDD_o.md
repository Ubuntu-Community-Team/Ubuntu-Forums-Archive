---
title: "Unable to share multiple patitions from same HDD on local network"
date: 2016-02-21
forum: New to Ubuntu
---

### Post by Exelios on 2016-02-21
Hello everyone. 

I recently had the idea to set up a local media storage place in my appartement so my roommates and I can share All our musique, videos, etc. I decided to install Ubuntu 14.04 LTS on my old PC. 

My problem:

I only have one HDD 4TB with two 1 TB partitions I wish to share on the local network. Using solutions from these threads [http://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition/91054#91054](http://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition/91054#91054) and [http://askubuntu.com/questions/342791/file-permissions-wont-change](http://askubuntu.com/questions/342791/file-permissions-wont-change) I was able to mount and share one partition. I can access it from my windows 7. However with the same configuration, the other partition is impossible to access from windows and therefore cannot be accessed by my roommates.

I'm kind of stumped so if anybody has an idea on how to fix this issue it's gladly welcomed.

---

### Post by leunam12 on 2016-02-22
What procedure are you using for sharing? is it something like this?

[http://ubuntuhandbook.org/index.php/2015/02/share-a-folder-in-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2015/02/share-a-folder-in-ubuntu-14-04/)

---

### Post by christiaan3 on 2016-02-23
Personally I would recommend you to use samba (I don't know if you are already)
On the bottom of the /etc/samba/smb.conf, your configuration should look something like this:
This is not the perfect example of creating a secure share but it will work like this, if you want to make it more secure
tell me and I will explain you in a next post.

[Partition1]
comment = First partition
path = your path
browsable = yes
guest ok = yes
read only = no
create mask = 777

[Partition2]
comment = Second partition
path = your path
browsable = yes
guest ok = yes
read only = no
create mask = 777

---

### Post by Morbius1 on 2016-02-23
Just a suggestion but you might want to post the output of the following commands so the good people here can see how you are set up:
```
cat /etc/fstab
```
```
testparm -s
```
```
net usershare info --long
```
It may already look like christiaan3's examples, it may not, or you may have been using usershares all of which will be revealed by those commands.

[COLOR=#0000cd]*And a special note about the links you used to mount the partitions:*[/COLOR] Once upon a time there was a user that went around this forum and at askubuntu with his hair on fire beside himself with giddiness after discovering an obscure ntfs option called: "permissions".

The problem was he never thought it through and he never used it if Windows was also going to access the partition:
> Check out the link I gave earlier: [b.andre.pagesperso-orange.fr/permissions.html]("http://b.andre.pagesperso-orange.fr/permissions.html")  It shows how to map users properly. [COLOR=#0000cd]I've not used it as I do not use  Windows[/COLOR] and I hear Microsoft made some changes to ntfs with windows 7.  Good luck to you
It came from another askubuntu question: [http://askubuntu.com/questions/92863/mount-ntfs-partition-at-startup-with-non-root-user-as-owner/517223#517223](http://askubuntu.com/questions/92863/mount-ntfs-partition-at-startup-with-non-root-user-as-owner/517223#517223)

And the victim .. um ... user had issues:
> However, when I try to access files on the partition from Windows, the  security settings are all messed up. On all the files (of those few I've  examined) a new account called Account Unknown(long GUID)  has been added to the list of users, and has full rights. Rigths for  most other users are decreased so that I don't have rights to do stuff I  expect. Notably "Everyone" does no longer seem to have right to  "Traverse folder / execute".

The answer to your original link's question: "How do I use 'chmod' on an NTFS (or FAT32) partition?" is simple. You don't. You mount the partition with a set of permissions equal to or greater than what you are setting your samba shares authorization.

---

### Post by Exelios on 2016-02-23
Thank you all!

Christiaan3's reply gave me a solid lead on how to configure samba. It allowed me to solve the major problem. I just need to adjust the settings to make the share a little more secured.

And thank you Morbius1 for the great advice on ntfs permissions. One of my roommates is using a windows OS and I will take all this information into consideration so he can also use this share correctly. I will keep you updated on the situation. 

Again thank you for your help.

---

