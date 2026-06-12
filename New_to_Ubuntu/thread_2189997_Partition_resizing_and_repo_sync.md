---
title: "Partition resizing and repo sync"
date: 2013-11-25
forum: New to Ubuntu
---

### Post by sohail.connected on 2013-11-25
[ATTACH=CONFIG]248082[/ATTACH]

Okay so this is my doubt: i want to resize my ext4 partition using the unallocated space before the partition. But g-parted states that it can affect boot. I used g-parted during boot(ubuntu live disk). How do i resize my ext4 partiton without any probs. And is it possible to pause: ```
repo sync
``` and resume it later?? It is still going on and i want to boot to win 8. Thanks in advance. I cant search as repo is syncing and my speed is dead slow.

---

### Post by insidekitty83 on 2013-11-25
[This]("http://askubuntu.com/questions/24027/how-to-resize-a-ext4-root-partition-at-runtime") should help with your windows partition, and [this]("http://source.android.com/source/using-repo.html") should help with your repo sync. nutshell version: repo sync is an android process... and while no one worries about upsetting a droid, i wouldnt suggest pausing. the least that would happen is you would have to start completely over, and dont play around too much with your partitions for 2 reasons 1)windows doesnt play well with others and 2)it actually degrades the hard drive if you keep messing with it. ps, i would really suggest having a boot disc for windows handy if you absolutely need to resize that partition
with love,
          Proud owner of several bricked hard drives
pps, i know it says that ive only been kicking about since august, but ive been using ubuntu since feisty fawn and played around with openSuse, mint, fedora, red hat, linspire *shudder*, and damn small.

---

### Post by sohail.connected on 2013-11-25
> **insidekitty83 said:**
> [This]("http://askubuntu.com/questions/24027/how-to-resize-a-ext4-root-partition-at-runtime") should help with your windows partition, and [this]("http://source.android.com/source/using-repo.html") should help with your repo sync. nutshell version: repo sync is an android process

That dint help. The first link says unallocated drive after the root partiton(mine is before). And the second helped but dint answer my question of pausing. Thanks anyway :)

---

### Post by insidekitty83 on 2013-11-25
> **insidekitty83 said:**
>  nutshell version: repo sync is an android process... and while no one worries about upsetting a droid, i wouldnt suggest pausing. the least that would happen is you would have to start completely over, and dont play around too much with your partitions for 2 reasons 1)windows doesnt play well with others and 2)it actually degrades the hard drive if you keep messing with it. ps, i would really suggest having a boot disc for windows handy if you absolutely need to resize that partition

 
sorry about the archaic bits of the message. basically put, I would advise *against* pausing the repo sync, and i would also recommend that if you really want that windows partition to be bigger, make sure you have a windows boot disc (or windows installation disc) handy in case it goes badly and your windows won't boot

---

### Post by westie457 on 2013-11-25
Moving the start point of a partition changes the UUID of the partition however the UUID listed in /etc/fstab is not changed and your system will not boot. In that respect 'Gparted' is right to give the warning.

It is possible but be aware that this could hose your system to the point that you will need to reinstall.

Boot using a LiveDVD/USB into 'Try' mode and open a terminal. Run ```
sudo blkid
``` to get a list of UUIDs for your current set-up. Save as a text file or write them on paper.
 Start Gparted and resize/move the partition you want to work on. For you that would be /dev/sda3. exit the pop-up window and then 'Apply', agree to the final warning if there is one and wait for this to finish. **Do not interrupt **because you will kill your system.

If the resize fails you will have to reinstall using the 'Something Else' option and reset the partitions.

Assuming Gparted is successful you can go to the next stage.
Open a terminal and again run ```
sudo blkid
``` to get an updated list of UUIDs. The UUID for /devsda3 should have changed. Copy this UUID - everything inside the quote-marks.
Still in the terminal ```
gksudo gedit /etc/fstab[-code]
Find the part that says /was on /dev/sda3  UUID= xxxxxxxxxxxxxxxxxxx (numbers,letters and '-'s)
Delete the ID and paste in the new one. Proof read the changes, save the file and exit.

This next bit is not absolutely necessary but will not hurt.[code]sudo update-grub
```

Now for the moment of truth, keeping fingers crossed reboot the system. Hopefully everything went as planned and you are now working again.

As stated earlier if this fails you will need to reinstall Ubuntu from scratch.

Hope this goes well for you. Good luck

---

