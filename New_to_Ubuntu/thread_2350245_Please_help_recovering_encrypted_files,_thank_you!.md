---
title: "Please help recovering encrypted files, thank you!"
date: 2017-01-22
forum: New to Ubuntu
---

### Post by m00sejerky on 2017-01-22
Good afternoon,

I'm a linux noob so please and thank you in advance for your patience with me!


I have a Dell M3800 with Ubuntu 16.04 LTS installed. I opted to turn on the cryptsafe/ecryptfs/whatever-it's-called function during the 16.04 setup so my drive and files are now encrypted. However, I have been having hardware issues with 16.04 so Dell support had me edit my precisionm3800.conf file and then update my initramfs via a terminal command and reboot, at which time I immediately stopped being able to boot into the OS, getting these errors instead (note, at this point Dell stopped giving me any help claiming that they don't support encryption and that I'm on my own):


[ATTACH=CONFIG]273327[/ATTACH]


I have a bootable 16.04 USB key so I am able to access the laptop. I have already attempted to follow the guide here with no luck:


[noparse]https://help(dot)ubuntu(dot)com/community/EncryptedPrivateDirectory[/noparse]


I also tried to boot into an older version of the kernel, also unsuccessfully


[ATTACH=CONFIG]273329[/ATTACH]

[ATTACH=CONFIG]273328[/ATTACH]


And then I also tried to follow the steps in these two guides, also without success


[noparse]http://askubuntu(dot)com/questions/653408/mounting-encrypted-luks-partition-from-live-cd[/noparse]


[noparse]https://evilshit(dot)wordpress(dot)com/2012/10/29/how-to-mount-luks-encrypted-partitions-manually/[/noparse]


Following the steps on those two sites, my ```
blkid
``` tells me that sda3 is the one with the crypto, but I also have an entry for ```
[COLOR=#000000][FONT=verdana]/dev/mapper/luks-78165293-aacf-4a1c-a041-2ad7c3c0cd29: UUID="RsOezT-oYvV-nK9B-x54e-ihUO-r2Hu-PSHkTq" TYPE="LVM2_member"[/FONT][/COLOR]
``` Attempting to access either one ```
[COLOR=#000000][FONT=verdana]eg: cryptsetup luksOpen /dev/sda3/ crypthome[/FONT][/COLOR]
``` gives me the error of ```
[COLOR=#000000][FONT=verdana]Device /dev/sda3/ doesn't exist or access denied[/FONT][/COLOR]
```

If at all possible, I'd appreciate help starting from scratch thru to unlocking the files _**and**_ decrypting the file names, so that I can copy them to an external drive and then wipe everything & start anew. Thank you all in advance for your assistance!

---

### Post by m00sejerky on 2017-01-22
Addendum: I _do_ know my boot login password, and if that fails, I do have my MOUNT passphrase available as well.

Note that my attempts at doing the sudo ecryptfs-recover-private have failed so I must be doing something incorrectly (hence request to start from scratch please with your fresh sets of eyes guiding me along)

---

### Post by QIII on 2017-01-22
Hello!

Many of our users have slow internet connections or data limitations.

When adding images, please use the attach functionality (the paperclip button above the text input area), which will add a clickable thumbnail image users may enlarge as they choose.

Thanks and welcome to the forums!  Best wishes!

---

### Post by m00sejerky on 2017-01-22
> **QIII said:**
> Hello!

Many of our users have slow internet connections or data limitations.

When adding images, please use the attach functionality (the paperclip button above the text input area), which will add a clickable thumbnail image users may enlarge as they choose.

Thanks and welcome to the forums!  Best wishes!

Hi **QIII**,

Thank you for letting me know & double-thanks for editing my post. I'll bear that in mind going forward.

---

### Post by mc4man on 2017-01-24
I'm just copying this from an answer several years ago, should still work.

Boot to the live cd/usb, choose the Try me option. Once on the Desktop click on the power cog indicator > System Settings > User Accounts. If a password is requested just press enter on the keyboard. (no password

Create a new user, use the _exact same name as the user whose directory is to be recovered_. Click on Account type, pick Administrator. Once created click on "Account disabled" & enable the account. The password doesn't matter,  whatever is accepted will do.

Now log out & at the login screen pick the new user, login. Once logged in open nautilus and mount the partition where the encrypted directory is. Then open a terminal & run this

```
sudo ecryptfs-recover-private
```

It may take a bit to find, when prompted, if the directory found is the one desired then choose y

When prompted for a " LOGIN passphrase" use the [U]password of the user whose encrypted files are to be recovered
[/U]
Here is an Ex.

> doug@ubuntu:~$ sudo ecryptfs-recover-private 
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/03b449b1-3c0b-481d-a917-afeb3e528a5a/home/.ecryptfs/doug/.Private].
Try to recover this directory? [Y/n]: y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [4b308179ad1441de] into the user session keyring
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.NgZaH4ds]. 

Now browse to /tmp, you will be the owner of the ecryptfs.XXXXXXXX directory & can freely view & copy any files

---

### Post by m00sejerky on 2017-01-25
> **mc4man said:**
> I'm just copying this from an answer several years ago, should still work.

Boot to the live cd/usb, choose the Try me option. Once on the Desktop click on the power cog indicator > System Settings > User Accounts. If a password is requested just press enter on the keyboard. (no password

Create a new user, use the _exact same name as the user whose directory is to be recovered_. Click on Account type, pick Administrator. Once created click on "Account disabled" & enable the account. The password doesn't matter,  whatever is accepted will do.

Now log out & at the login screen pick the new user, login. Once logged in open nautilus

Good evening **mc4man**, 

And thanks for responding to my query! I'm good following you up to this part, no sweat.

[COLOR=#FF0000]**Edit: **[/COLOR]Thought I had this, but no dice. After I created the new account using the same name as before, logged out and tried to log in, after entering the password the screen flickers to black for a second and then comes back to the login screen with a short trill/error sound.

> **mc4man said:**
> and **mount the partition where the encrypted directory is. **

But this here is my first stumbling block. How do I go about doing that please?

> **mc4man said:**
> Then open a terminal & run this

```
sudo ecryptfs-recover-private
```

It may take a bit to find, when prompted, if the directory found is the one desired then choose y

When prompted for a " LOGIN passphrase" use the [U]**password of the user whose encrypted files are to be recovered**
[/U]
Here is an Ex.

Now browse to /tmp, you will be the owner of the ecryptfs.XXXXXXXX directory & can freely view & copy any files

The rest seems easy enough to follow I hope? But just to clarify and be 100% accurate and not make mistakes, this refers *not* to the on-boot passcode, and also *not* the MOUNT passphrase, but rather specifically the *password *for _my user account_ that I would normally use to actually log into the OS, correct?

---

### Post by m00sejerky on 2017-01-25
> **m00sejerky said:**
> Good evening mc4man, 

And thanks for responding to my query! I'm good following you up to this part, no sweat.

**Edit: Thought I had this, but no dice. After I created the new account using the same name as before, logged out and tried to log in, after entering the password the screen flickers to black for a second and then comes back to the login screen with a short trill/error sound.**

But this here is my first stumbling block. How do I go about doing that please?

The rest seems easy enough to follow I hope? But just to clarify and be 100% accurate and not make mistakes, this refers not to the on-boot passcode, and also not the MOUNT passphrase, but rather specifically the password for my user account that I would normally use to actually log into the OS, correct? Ok I tried something else, using a capital letter instead of all lower-case for the username (even though I'd thought it was lower case before), and then I chose to use the same password for the new account as I'd used before. So... I am now successfully logged into my <username> account, and have nautilus open (that's just the file manager, correct?), and I think I mounted the encrypted directory? For me, the drive in the laptop shows up as a 494GB volume in the left-hand pane, and when I double-click it, I get a password prompt which only accepts the on-boot passcode. After entering that, the 494GB volume gets a little eject icon next to it and I can open it up and navigate around somewhat. The new stumbling block is getting the sudo ecryptfs-recover-private to work. When I run that, I get the following errors:

```
INFO: Searching for encrypted private directories (this might take a while)...
find: '/run/user/1000/gvfs': Permission denied
find: File system loop detected; '/sys/kernel/debug/pinctrl' is part of the same file system loop as 'sys/kernel/debug'.
```

---

### Post by m00sejerky on 2017-01-29
I don't know what the appropriate etiquette is for this forum - please let me know if it's OK to bump a thread sooner than 3 or 4 days, thank you.

---

### Post by howefield on 2017-01-29
> **m00sejerky said:**
> I don't know what the appropriate etiquette is for this forum - please let me know if it's OK to bump a thread sooner than 3 or 4 days, thank you.

Once a day where there is no response is fine, even slightly more often than that would be fine if needed.

---

### Post by m00sejerky on 2017-01-30
Bump please.

---

### Post by LostFarmer on 2017-01-31
Just been testing out encrypt with lvm.  This is for Mint but ubuntu is the same .except the name.  replace "mint-vg" with 'ubuntu-vg''.  at step #5 the correct name will be displayed for latter commands.  You will have to use gui program 'disk' or terminal command 'fdisk' to find out the correct dev name ' /dev/sdxy'  where x is hdd number and y is partition 'likeyly sdx3.

[https://forums.linuxmint.com/viewtopic.php?f=50&t=198706&p=1043424&hilit=mount+lvm#p1043424  ]("https://forums.linuxmint.com/viewtopic.php?f=50&t=198706&p=1043424&hilit=mount+lvm#p1043424")

added: the last post by Derek_S

if you with to correctly unmout the hdd after step #10 add :sudo vgchange -an mint-vg  Note: use ubuntu-vg not mint-vg  
then do the last step #11

---

