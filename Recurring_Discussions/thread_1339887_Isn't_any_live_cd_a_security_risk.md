---
title: "Isn't any live cd a security risk?"
date: 2009-11-28
forum: Recurring Discussions
---

### Post by ankspo71 on 2009-11-28
Hi Everyone,

This is a question for those who practice maximum security. I keep all of my passwords in a text file on my hard drive, so I will just use them as an example. Well, the passwords are generally protected with my Ubuntu username and password (and login password), which provides enough protection from the internet. However, if someone were to have a live cd, those passwords text file can be retrieved. I won't say how though.

Anyways, my question is, how do you protect your files from people who know how to use a live cd?

Do you encrypt your entire system or /home directory? (If so, what program is recommended that is effective against live cds?)
Do you encrypt individual files?
More importantly, why isn't there a warning about the security risks of live cds somewhere (and advise people to learn how to use drive/file encryption)?

Thanks,
James.

---

### Post by staf0048 on 2009-11-28
Your question assumes the perp. has physical control of your computer - a major security breach in and of itself.  So now you're just left with encryption methods for your HDD or storing all your info on the "cloud" so to speak.  Which is more secure?  Might depend on where you live I suppose.

I know the alternate install CD contains a way to encrypt your entire HDD, but I have not tested access with a live CD.  I'd be interested to know if there is the same 20 character password required to gain access to it.

---

### Post by ankspo71 on 2009-11-28
Hi,
Yes this is what I mean. I would like to be prompted for a password if I try to access my personal files and directories with a live cd. 

The Karmic live cd has a way to encrypt the home directory now, but I chose not to use it because I didn't know if I would be able to access my own files if I needed to repair my system with a live cd. Also, when it comes to certain things, I like to know those certain things are available in every linux distro. Encryption programs is one of those things because they all use different methods of encryption.

Does anybody know the name of the encryption program used in the Ubuntu 9.10 live cd installer? 
Thanks for the reply.
James

---

### Post by wilee-nilee on 2009-11-28
Your password can be easily rewritten on the computer as well. A encrypted thumb would be a better storage I think.

---

### Post by pietjanjaap on 2009-11-28
In 5 minutes you can change your password of ubuntu(and windows).
With livecd you can read everything.

The only option is encrypt your whole harddisk, and do not leave your pc onn wenn you leave your home. Wenn systen is onn then with special software you could read memory or haddisk , wenn your in the same room of pc.

Wenn system crashes you have of course a big problem, you cannot read files.
So you need to learn how to backup the encrypted part of your harddisk, so you can put it back if a haddisk error occurs. After this you can read the rest of the files.

---

### Post by mocoloco on 2009-11-28
What about setting your BIOS to not boot from CD (or flash driver or anything but the HD), then password protecting the BIOS?  Also locking out grub so they can't customize the line before boot or load the recovery mode.
AFAIK if the BIOS is locked the only way past that is by opening the machine to reset the little switch inside (am I wrong on that?). So then it's a matter of having your case physically locked.

---

### Post by ankspo71 on 2009-11-28
Ahh, thanks for the advice everyone.

When I discovered how easy it was to bypass ubuntu's default security with a live cd, I started feeling like I needed to destroy my live cds for the feeling of maximum protection. I like having live cds though, so I think I will go by a thumb drive and see what encryption program will work best with it. I am experimenting with truecrypt at the moment.

I am used to using programs like cryptext (an easy to use windows encryption application that stores the password inside the encrypted file) so I hope to find a similar application like that for linux. I'm not used to using keyrings and keyfiles and things like that.

Btw, I didn't know it was that easy for someone to tamper with existing user passwords either. This has been a real eye opener for me #-oFor now, I am going to tar-encrypt all of my sensitive data, until I get a nice sized thumbdrive.

Thanks for the help,
James

---

### Post by wilee-nilee on 2009-11-28
You can buy thumbs with built in encryption. There was another thread a couple of days ago about encrypting your whole HD but since the startup isn't a mod suggested that if you were really in their words paranoid you could have grub I think on a thumb instead of the computer.

---

### Post by ankspo71 on 2009-11-28
> **mocoloco said:**
> What about setting your BIOS to not boot from CD (or flash driver or anything but the HD), then password protecting the BIOS?  Also locking out grub so they can't customize the line before boot or load the recovery mode.
AFAIK if the BIOS is locked the only way past that is by opening the machine to reset the little switch inside (am I wrong on that?). So then it's a matter of having your case physically locked.


Hi, 
Another excellent idea, thanks. I knew about my bios having passwords but didn't know it locks the device boot order too. So I changed the boot order it and it works. I don't know why I didn't think of this before. :D 

I have to boot back into bios because I need to see what the difference is between "set supervisor password' and 'set user password'.  I tried user password and it didn't ask for a user, so I better check that out to be safe.

thanks,
James

---

### Post by cascade9 on 2009-11-28
this is the thread wilee-nilee mentioned-

[http://ubuntuforums.org/showthread.php?t=1318597&highlight=encryption](http://ubuntuforums.org/showthread.php?t=1318597&highlight=encryption)

If your really worried about security, then its probably a god idea to encrypt your whole hard drive. If someone can get access to your system, and your is not encrypted, then your data can be read. One way or another. Flash drives wont make it any harder (or easier) to crack. 

> **mocoloco said:**
> What about setting your BIOS to not boot from CD (or flash driver or anything but the HD), then password protecting the BIOS? Also locking out grub so they can't customize the line before boot or load the recovery mode.
AFAIK if the BIOS is locked the only way past that is by opening the machine to reset the little switch inside (am I wrong on that?). So then it's a matter of having your case physically locked.

Bingo, BIOS passwording is easy to get around, in 99% of cases. Just clear CMOS, or pull the battery for 10 minutes (sometimes longer) and the password is gone. I'm yet to see a computer case lock that would stop anyone with a decent drill, much in the way of lockpicking skills, or thermite LOL.  

BTW, I know of someone who hid a 2.5'' laptop drive into a router. Wasnt a fun job, but once it was done, you could SSH into the hdd, but from the outside it looked just like a normal router. That, plus encryption would make it hard to find the drive at all, and even if someone did find it, they wouldnt be able to use it. Not unless the encryption was cracked (just use a strong encryption).

---

### Post by BkkBonanza on 2009-11-28
Holy Moly. You guys are hitting this thing with a sledge hammer.

Nothing wrong with encrypting your drive if you need to secure everything.

But for stroing passwords the solution has existed for ages and works very well.

KeepassX - I believe it's in Synaptics for super quick install.

Program saves your passwords in an encrypted file and can be used in Linux, Windows and MAC easily. There's a portable version too I believe. 

I've been using this for years and it sores hundreds of my passwords and other tid bits of info. I even have a hot key assigned to it so when I need to enter a password I hit the hot key, enter my master password, select the appropriate password and paste it in. It also has a secure password generator built in. So this type of thing (like Password Safe on Windows, but multi-platform) is the way to go.

Another great tool is Truecrypt. You can create encrypted volume files that can be mounted as you need and be of any size. Great if you assign it to a hot key too.

---

### Post by pietjanjaap on 2009-11-28
Also make a good long password, with everything inside:
A
a
2
.
Upper, lower, numbers, special? and do not use names
40 character long at least.

---

### Post by Agent ME on 2009-11-28
Install [ecryptfs-utils](apt:ecryptfs-utils) and then in a terminal, run "ecryptfs-setup-private". Log out and log back in, and you'll then have a folder called "Private", and all files inside it are encrypted, and only available to your user account while you're logged in. This is the recommended way to secure a user's files in Ubuntu.

If you boot the system up with a LiveCD, you won't be able to get to the files (unless you decrypt them yourself with your password).

---

### Post by sgosnell on 2009-11-28
Lots of ways of doing this.  Truecrypt, any of several password safes, encrypting your /home directory, all work.  I prefer a password safe, which is designed for just this use.  They're set up to hold an account/user name, password, notes, and other such stuff, and can be set to as strong a password as you like.  Truecrypt will let you encrypt a file, a folder, a drive, or whatever, and works pretty well.  I use it to encrypt a folder of files, as well as having my password safe.

---

### Post by Shpongle on 2009-11-28
make a small  triple encrypted truecrypt volume and make it a readme in a theme folder or something, good luck finding that

---

### Post by bodhi.zazen on 2009-11-29
> **DillByrne said:**
> make a small  triple encrypted truecrypt volume and make it a readme in a theme folder or something, good luck finding that

It is easy to find encrypted partitions as the data from an encryptied partition or file, if you try to read it, is rather obvious.

Decrypting it is more difficult.
 
As has been stated in this thread, the only thing encryption buys you is to secure your data (and that may be all you want). The rest, BIOS passwords, etc, will be a deturent to casual crackers, but I would not rely on those methods.

Encryption has been cracked via a cold boot, so it is not foolproof. Encryption will not help you if your machine is on or your encrypted partition /data is in use.

Just a few cautions you should be aware of =)

You need to protect the /boot partition as it can not be encrypted as of yet and so you would be vulnerable to a spoofed kernel.

---

### Post by mmix on 2009-11-29
I use Fedora 12 with encrypted HDD.

The encryption supports when F12 installation.

---

### Post by cascade9 on 2009-11-29
> **BkkBonaza said:**
> Holy Moly. You guys are hitting this thing with a sledge hammer.

Nothing wrong with encrypting your drive if you need to secure everything.

IMO, the hot rodders were correct- overkill is just right. :D

---

### Post by ZankerH on 2009-11-29
No such thing as too much security.

Full HD encryption (ubuntu supports that at install now, right?), ccrypt the passwords file a few times with random extensions, then put it in a hidden truecrypt volume, run it through gpg between your most obscure email accounts and archive it as an attachment to message #43752.

---

### Post by BkkBonanza on 2009-11-29
From a practical point of view there can be too much security. The point at which you fail to bother going through all the hoops just to get your password is the point where it becomes too much. When strong cryptography is used there is very little to be gained by multiple passes, obscurity and labyrinthine access obstacles. One can posit cases where you may feel strongly that you need it but for most people in most cases such hassles are soon skipped over and either the data becomes forgotten and lost, or more likely neglected and unprotected.

For passwords, a password safe is adequate.

---

### Post by sgosnell on 2009-11-29
I agree.  Normal people have no need for elaborate security, because their data simply isn't valuable enough to be worth the effort, and because it's so burdensome to use the elaborate security that it is often not used at all.  A password safe will take care of your password needs, as long as you use a reasonable master password, and a simple Truecrypt volume will take care of other files.  You can use a hidden volume if you're really paranoid, but a common filename is good enough for most purposes.  The more complicated the security, the less it will be used.  AES encryption is more then enough to stop anyone other than a real expert with high-tech tools and extended access to the computer.  All this does assume reasonably strong passwords, of course.  Using 'password' as your password isn't a lot better than no security at all, but using a long, hard-to-remember password means it won't be used as much as it should be.  Everything involves a compromise of some sort, and some compromise toward reasonableness is usually necessary.  We aren't talking about nuclear launch codes here.

---

### Post by Chame_Wizard on 2009-11-29
not really,if you know what you are doing.

---

### Post by Bios Element on 2009-11-29
There was a thread about this a while back...to save you the hassle of reading it, here's the summery.




Physical Access is Root Access.

---

