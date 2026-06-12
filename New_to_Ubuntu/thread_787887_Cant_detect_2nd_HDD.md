---
title: "Cant detect 2nd HDD"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-09
HI guys,

First sorry to be asking a very dumb question. I am a new Ubuntu user that i think am doing well but i just added 3 Hard Drive in my system but i cannot detect it.

Question:

- Whats the command to see what hard drive i have connected
- How do i mount it so i can access the HDD
 please help

---

### Post by aeiah on 2008-05-09
to get a clear picture of which hard drive is which, i like to use gparted (partition editor). you may have to install it via synaptic.

to manually mount a hard drive partition first make a folder for it to reside in
```
sudo mkdir /media/storagedrive
```

change storagedrive to whatever you want. then:
```
 sudo mount /dev/sda /media/storagedrive
```

sda probably isnt the name of the partition you want. like i said, the simplest way i find is to look at what gparted shows. you can also, from the terminal, do:
```
ls /dev/sd*
```

this will list all the devices that start with sd, which will be sata hard drives. hd* will be ide ones i believe.

to have them mount at startup however, you're going to have to add them to your /etc/fstab file. you should be able to find help for fstab on here and various examples. you could probably figure it out though from whats already in your fstab file, changing the bits you need for each partition you want adding

---

### Post by appoloin on 2008-05-09
Hi there and thank you.

I have installed gparted but i cannot find it in the application file. HOw do i use it?

---

### Post by bumanie on 2008-05-09
Gparted is under System --> Administration --> (and named) Partition editor. It should be clear how to use it once it has scanned your drives.

---

### Post by appoloin on 2008-05-09
Hello again,

I tried to do it but i must be doing something wrong.

I am using partition editor cant really figure out how to work it. Anyway.

my 120 gig i think i formatted it now its finally showing but when i try to add stuff i get You do not have the permissions necessary.

Question:

- Is there anyway to use partition editor without loosing my file and could you please give me instruction.

- Is there anyway i can fix my 120 gig problem? or did i do it all wrong?

Im sorry for a dumb question but this is the only hurdle i cant jump over.

---

### Post by aspen_dv on 2008-05-09
Can you do a command and post what you have
fdisk -l
Dont' usually mess with gparted unless you know what you're doing.
Where did you mount your 120GB drive, can you do
mount
and post the output.
You may have to check your fstab and see of you mount read/write for all users

---

### Post by appoloin on 2008-05-09
Sorry. but that did not mean anything to me. Could you give me the steps please?

---

