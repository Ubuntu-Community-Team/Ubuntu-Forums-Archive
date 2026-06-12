---
title: "USB Thumb for accessing from LIVE USB - Permission Problem"
date: 2020-06-18
forum: New to Ubuntu
---

### Post by lovix on 2020-06-18
Been working hours on this

Seems super simple

I have a USB Linux encrypted flash drive with files on it.  I want to also access from a Live USB.

But when I try, says I don't have permission

So I did:

sudio fdisk -l

to find the USB drive   (location was /dev/sda)

then  
sudo chmod u=rwx,g=rwx,o=rwx /dev/sda

That produced no errors. So I boot up my Live USB, but get a permission error

So I tried chmod for the 2 partitions:
sudo chmod u=rwx,g=rwx,o=rwx /dev/sda1
sudo chmod u=rwx,g=rwx,o=rwx /dev/sda2

But with the same result.

I decided to check that permissions are actually getting set but that really stumped me because nowhere can I find how to do that.  
   
[COLOR=#000000][COLOR=#000000][FONT=Monaco, Lucida Console, monospace]
[/FONT][/COLOR][/COLOR]

---

### Post by sudodus on 2020-06-18
I think there is some partition on the drive, and you should mount that partition. Please run the following commands,

```

lsblk -f
lsblk -m

```

Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

With this output I or someone else will be able to suggest how to mount the partition (or partitions) on the drive, and then you should be able to see the files.

---

### Post by lovix on 2020-06-18
You are correct, there are two partitions on that USB flash drive. Thank you for your offer to help, but I'm going to decline on posting all of that information because I don't know what it means. I was hoping I could just slide in the drive while running the live Ubuntu and look at it in the same way I would look at it with my Ubuntu operating system which created the drive.

---

### Post by CelticWarrior on 2020-06-18
> I'm going to decline on posting all of that information because I don't know what it means
I can't imagine any way to help you without knowing what's in there.

> I was hoping I could just slide in the drive while running the live  Ubuntu and look at it in the same way I would look at it with my Ubuntu  operating system which created the drive. 				
Such expectation is quite unreasonable. If encrypted it must be decrypted and to know how to decrypt users helping you need to know what kind of encryption and partitioning. In any case you must have had a reason to encrypt it, so you should also be aware that's exactly what encryption was invented for - prevent access to something except to those authorized to do so, with a decryption key (password, passphrase, etc.) -, otherwise anyone with a live session or other Ubuntu/Linux could access what you don't want to be accessed.

---

### Post by lovix on 2020-06-18
Sorry, I guess that was confusing.  I have no problem with the encryption. I included that information in case it changes how to approach the problem. Its only when I run a live version of Ubuntu, do I have a problem accessing the drive after I unlock it. The files are not accessible after properly entering the encryption password. The error message speaks of permissions.

---

### Post by GhX6GZMB on 2020-06-18
I think the issue is quite simple.

When you boot/run Ubuntu from a live USB/DVD, you have no own user account and therefore no admin rights (unless you created it yourself with all necessary users/groups).
The only user and group is "ubuntu", PW "ubuntu", and this gives problems when accessing other drives which have a different user/group definition.

I don't know how to get around this, live booting has its limitations. The only thing that comes to mind is doing a sudo chown ubuntu:ubuntu for the USB drive you want to access.

---

### Post by sudodus on 2020-06-18
I think you should mount the partitions and you should keep an eye on permissions and ownership. It would be easier to help you, if you post the output I asked for. Now I can refer to advice given to other users.

[How to unmount and mount pen drive in ubuntu via command line](https://askubuntu.com/questions/859787/how-to-unmount-and-mount-pen-drive-in-ubuntu-via-command-line/859798#859798)

[Mount NTFS partition in a USB drive with custom permissions and owner](https://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition/956072#956072)

Edit: But you are on your own concerning encryption, because we don't know enough about it.

---

### Post by lovix on 2020-06-18
Hmm. I was able to make some progress by using the file manager to adjust the permissions. Apparently they were not getting adjusted using the terminal commands, though I didn't receive an error.  One of my partitions contains a text file and the other contains a Libre office document. I am able to make adjustments to the text file but not the office document. The two separate partitions have exactly the same permissions. Apparently text files are treated more leniently than office documents?  

I am much closer to having a solution that I'm looking for.

Encryption is not an issue for me at this time anyway, lol.

File system is EXT4.

I will read up about mounting. I'm confused by it because it's not something I have to think about generally, however that occurs, it's happening without my direct involvement.

In summary, adjusting permissions via the file manager allows me to access the files in the live environment, but I'm only able to adjust the files on one of the partitions even though each partition carries the exact same permissions.

---

### Post by sudodus on 2020-06-18
Is the file system ext4 in both partitions?

Can you copy the problematic file from the partition, where it seems to be read-only? And work with it somewhere, where you can write.

By the way, did you check the ownership (not only the permissions)?

---

### Post by lovix on 2020-06-18
Update: I tried it again and everything's working as intended. I don't know why things were locked down before in that one partition. I will mark this question as solved. Thanks for the moral support. It's people like yourself, who are willing to try to help, which makes Linux worth trying to figure out, for people like me.

---

