---
title: "[SOLVED] Did sudo chmod 777 kill my hard drive?"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by iansane on 2008-09-19
I'm using a new drive now. The other one was old laptop with adapter so it worked in my desktop so maybe it just finally failed at the same time but here's what I did.

I used gparted to format ext3 over my old windows on the drive so I could use it for other things.

I was having permission denied on some things even using sudo so I tried
```

sudo chmod -R 777 /dev/hda

```

When I first formatted it not thinking about grub being in the mbr, to my surprise grub was still fine but after the chmod when I rebooted it gave me "error 15 file not found". 

I tried restoreing grub several ways each one claiming success only to get the same error.

So, I just did a full format and reinstall of ubuntu on the first drive. (the one in question). Same report of success and same error when trying to boot.

I totally wiped both drives and installed fresh ubuntu on first one and still the same error. I replaced the drive and everything is fine.

So did "sudo chmod -R 777 /dev/hda" kill the drive and is there a way to fix it?

---

### Post by mojoman on 2008-09-20
> **iansane said:**
> I'm using a new drive now. The other one was old laptop with adapter so it worked in my desktop so maybe it just finally failed at the same time but here's what I did.

I used gparted to format ext3 over my old windows on the drive so I could use it for other things.

I was having permission denied on some things even using sudo so I tried
```

sudo chmod -R 777 /dev/hda

```

When I first formatted it not thinking about grub being in the mbr, to my surprise grub was still fine but after the chmod when I rebooted it gave me "error 15 file not found". 

I tried restoreing grub several ways each one claiming success only to get the same error.

So, I just did a full format and reinstall of ubuntu on the first drive. (the one in question). Same report of success and same error when trying to boot.

I totally wiped both drives and installed fresh ubuntu on first one and still the same error. I replaced the drive and everything is fine.

So did "sudo chmod -R 777 /dev/hda" kill the drive and is there a way to fix it?

I don't think it shouldn't have killed the HD per se really, it just makes all those security precautions that goes with Linux totally obsolete. Now, a chown would definitely have bungled the system totally (as e.g. root would not own certain files) but I don't see how a chmod would have bungled the system. (Though it does, as I said, compromise security enormously.)

---

### Post by iansane on 2008-09-23
Right. I know it compromises security but it was going to be a drive for which I cared nothing about security of the files on it.

I just can't figure out why a complete wipe, format, and fresh install didn't fix the problem. It's like the chmod affected the mbr of the drive making it unaccesible.Should chmod even go near the mbr if I use it that way? I thought it would just change the partition and not the mbr too.

---

### Post by Tatty on 2008-09-23
I think you may have to re-install.

I am in no way an expert on the reasons why, but Linux relies upon file permissions for its smooth running, so nuking them is not a good idea.  For example, it will mess things up if you move your /home folder to an ntfs partition, as all the permissions will be lost.

What were you having permission denied problems with?

EDIT: sorry i just re-read your first post... so youre saying that even after formatting the drive and doing a fresh install you could still not get it to boot?  That seems rather odd, there is no way the chmod could have caused that as far as i can see.

---

### Post by lwvmobile on 2008-09-23
Are you running your computer now with 2 hard drives installed. I wasn't clear about that, but I think the error 15 in grub is saying its trying to boot the image but its not on the hard drive its looking for the image on, meanings its probably on the other hard drive, if you do have 2 hard drives. If not, then just ignore my idiocy.:lolflag:

---

### Post by jemate18 on 2008-09-23
chmod 777 just gives read write execute to your hard drive.. It doesnt kill it

---

### Post by iansane on 2008-09-23
> **lwvmobile said:**
> Are you running your computer now with 2 hard drives installed. I wasn't clear about that, but I think the error 15 in grub is saying its trying to boot the image but its not on the hard drive its looking for the image on, meanings its probably on the other hard drive, if you do have 2 hard drives. If not, then just ignore my idiocy.:lolflag:

No no idiocy. I did make it kind of confusing trying to give all the detail.

I was running two hard drives. At one time had windows on the first one. formatted it and was just using it as extra storage. Then was unable to delete a file or something. I can't remember now. I wasn't paying much attention. Just hastily did a chmod on the whole drive with -R . It was the one with grub on hd0 but ubuntu was on the second drive.

I ended up wiping, formating and installing on both drives one at a time and either way I got the same "error 15 file not found" I replaced the two small drives with one 320GB drive and everything is great now.

I didn't think chmod would do that. It's probably just coincidence that it happened next time I rebooted after chmod.

They were both older used drives so it's likely one of them was causeing problem with IDE controler or something like that.

I just wanted to see whay you guys had to say about "chmod -R /dev/hda" and if that can cause damage like that.

Thanks

---

### Post by lwvmobile on 2008-09-23
Yeah, sometimes when you run multiple hard drives and you install ubuntu and grub, grub will point to the wrong hard drive, especially if the hard drive order in BIOS changes(cough:typical award bios). Since it sounds like you got it going with just one in there then great, but if you need more than one going and you have the same problem, try doing an 'e' at the grub menu when booting and look at the line

hd(0,0)

this line refers to hard drive and partition 0,0 - or hard drive 0, partition 0

changing the first number to 1 normally does it for 2 hard drive systems. 

Anyway, just something to try if you get in that situation again.

---

### Post by iansane on 2008-09-24
Thanks all for the input and some solutions for next time. I was able to mount it and format it to fat32 but one time it mounted. another time it didn't mount so I threw it in a drawer. Maybe I'll take it apart and play with the shiny little disks.:-)

---

