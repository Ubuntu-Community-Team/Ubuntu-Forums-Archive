---
title: "how to install onto  HDD"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by arranskye on 2013-04-06
Hi  I have partitioned my existing 40GB HDD into 2  x  20GB primary partitions. The C: drive has XP Pro installed  (32 bit) and I want to install ubuntu on the other F: drive.

I have had several attempts but no joy. It is an HP Pavillion desktop (circa 2001)
40GB  HDD & 512 MB ram   

I keep hitting a "root" problem as if the drive is not formatted or something and I cant find a straight forward option to install on the F: drive.

Im not very good at this, even failed to understand the forum Q & A's so please straight forward step by step instructions would be very much appreciated.  thanks

Sorry, I was hoping to be able to dual boot but if that it too complicated I can change the F: drive to logical if ubuntu will still operate on it ok.

---

### Post by Impavidus on 2013-04-06
You don't have to prepare a partition for Ubuntu beforehand. Just leaving enough unallocated space on the drive is enough. The installer has to format the partition anyway, as windows cannot make the required ext3/4 partition. Anyway, the F drive won't be known as F drive in Linux. Drive letters are windows terminology.

But 512MB is very small. I recommend you try to install Lubuntu. Which model HP pavillion is this exactly? Which processor is in it?

---

### Post by arranskye on 2013-04-06
Hi,  Thanks for your superfast reply.    Its an HP Pavillion 7916 and the CPU is intel(R) Celeron 1.2. In 2001 it came with 128 mb ram running XP home. Upgraded ram to 256mb to run XP Pro which it did pretty well for several years, then upgraded again to 512MB.  (max)  A bit of a surprise to find Ubuntu needs more ram as I thought that XP Pro would have been more memory hungry.  Right I think I understand what you mean and it fits in with what I was thinking while trying to install. I will certainly give it another try.  thanks.  Does it matter if the drive is primary or logical?            Can it be set up to boot from the HDD or will I still have to use the dvd to start up???   Also I am more than happy to buy lubuntu if you think it will be better.  Thanks again

---

### Post by nerdtron on 2013-04-06
> **arranskye said:**
>  
(1) A bit of a surprise to find Ubuntu needs more ram as I thought that XP Pro would have been more memory hungry.  Right I think I understand what you mean and it fits in with what I was thinking while trying to install. I will certainly give it another try.  thanks. 
(2)Does it matter if the drive is primary or logical? 
(3)Can it be set up to boot from the HDD or will I still have to use the dvd to start up??? 
(4)Also I am more than happy to buy lubuntu if you think it will be better.  Thanks again

1. Ubuntu is constantly being developed and it is more modern that a decade old Windows XP. The desktop environment is mostly the reason for it to need more RAM.
2. Nope. If you are going to use the "Do Something Else" option in the Ubuntu Installer to manually choose partitions just be sure to select the correct drive and mount point for it. Also be sure to install GRUB bootloader in sda or hda for it to takeover the bootprocess.
3. Nope. Once ubuntu is installed in the hard drive, you don't need the dvd to startup. 
4. Yup. With that low RAM, it will be a lot better if you use Lubuntu instead.

Goodluck with your install and keep us posted.

---

### Post by grahammechanical on 2013-04-06
Are we answering your question? Or, creating other questions?

Ubuntu needs at least two partitions. One for Ubuntu and one for swap. So I suggest that you run the Ubuntu live session and once at the desktop you open Gparted. It is in the Dash and then turn that F: drive/partition into an Extended partition. Then you create two logical partitions inside that Extended partition. The first of these logical partitions should be almost the size of the partition except for about 1GB which is what will become the swap partition.

1) Create 20GB Extended partition
2) Inside Extended partition create 19GB logical partition and 1GB logical partititon.
3) When those operations have been applied, run Install Ubuntu
4) choose the Do Something Else Option
5) At the partitioner stage

a) Select the 19GB partition and click Change. You will get a dialog box which will let you
Re-size the partition, give it a file system, a mount point, mark it to be formatted. You do not need to re-size. Select the files system as Ext4, tick to format, give it a mount point of / . Accept these changes and you will get back to the partition selection screen.

b) Select the 1GB partition and click Change. At the dialog box give this partition the mount point of swap and accept these changes and continue with the install.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

System Requirements

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

> 
[LIST]
[*=left]700 MHz processor (about Intel Celeron or better)[FONT=inherit][/FONT]
[*=left]512 MiB RAM (system memory)[FONT=inherit][/FONT]
[*=left]5 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)[FONT=inherit][/FONT]
[*=left]VGA capable of 1024x768 screen resolution[FONT=inherit][/FONT]
[*=left]Either a CD/DVD drive or a USB port for the installer media[FONT=inherit][/FONT]
[*=left][FONT=inherit][Internet access]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") is helpful[/FONT]
[/LIST]

Regards.

---

### Post by 3rdalbum on 2013-04-06
> **grahammechanical said:**
> a) Select the 19GB partition and click Change. You will get a dialog box which will let you
Re-size the partition, give it a file system, a mount point, mark it to be formatted. You do not need to re-size. Select the files system as Ext4, tick to format, **give it a mount point of / **. Accept these changes and you will get back to the partition selection screen.

Simply saying "I kept hitting a root problem" doesn't really give very much information. I think the error message you were referring to was "No root file system defined", which means you haven't actually told the Ubuntu installer where you want to install it. If this is the error message you've been getting, then the part in bold will fix it.

---

### Post by arranskye on 2013-04-06
> **3rdalbum said:**
> Simply saying "I kept hitting a root problem" doesn't really give very much information. I think the error message you were referring to was "No root file system defined", which means you haven't actually told the Ubuntu installer where you want to install it. If this is the error message you've been getting, then the part in bold will fix it.

Hi All, First a big thank you for your help.  Yes, as above, this was the error message.  I sort of guess that this was the problem so I clicked on mount but nothing happened.  Never mind I really want to try Ubuntu, and even more so now having experienced how helpful you guys are, so I will use the disc to get to know a bit about it until I can get a copy of Lubuntu.   What a binhead, I didn't even think about how old XP Pro was compared to the ever developing Ubuntu.      Its quite difficult to stop thinking in "windows" terms like MBR, full operating system on one partition/drive etc., and I have never come across a "swap" partition before.  It going to be a big learning curve but I will try to follow your instructions.  I put Ubuntu Puppy on my laptop a few days ago. Its so fast I just love it.  Do you think I could install it on the desktop PC please.   I have loads more questions but I will do some reading on the internet to find explanations.  I was very surprised that there were so many Ubuntu systems and I am interested to know the differences between them. When I am confident enough I will put the system best suited to me on my HP Compaq. Its a dual core 2.6 MHz with 4GB ram so it should accommodate most of the Ubuntu systems.   Thanks again :D

---

### Post by Impavidus on 2013-04-07
You can find Lubuntu [here]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu").

The main difference between the different Ubuntu flavours is the desktop environment. To a large extend it's the balance between eye candy and resource usage, in addition to some differences in style. The underlying system is the same. Your HP Compaq will handle any Ubuntu flavour – choose one, it's a matter of taste – but with 4GB RAM use a 64 bit OS. I'm quite sure the processor can handle that.

---

### Post by arranskye on 2013-04-07
Thanks,   Yes its a 64bit pc.   DONE IT Loaded Puppy onto my old Dell.Thank you all.  Took a while as it got the old brain matter going. I was not too sure about the last bit after choosing grub4dos,so just said ok.  It boots up fine, loads files & drivers in seconds, in fact it is much much faster than my 64bit HP compac & win 7.  Its perfect for me as I am not into films, streaming or editing videos etc.     Its not picking up my wireless card so I have used the E cable for now to connect but hopefully during the updates the drivers will arrive in due course.  If not I will search the forums as im sure there will be a way to utilise the drivers disc that I have.  I have activated the fire wall. Should I download an antivirus programme.   Again many thanks. I look forward to learning more about ubuntu.  Reminds me of the first computers I operated in 1986 using dos menus.  no sound, no graphics but we thought they were wonderful.

---

### Post by mastablasta on 2013-04-07
> **arranskye said:**
>       Its quite difficult to stop thinking in "windows" terms like MBR, full operating system on one partition/drive etc., and I have never come across a "swap" partition before. 

actually MBR (master boot record) exists inlinux as well. it's where GRUB is located which launches the linux operating system.

linux can be on one partition if you install it that way. but for security and convenience separating a few parittion is better. furthermore latest windows OS also have separate boot partitions.

you never came across swap partition but you did come across pagefile in windows. which sort of does the same thing as swap partition in linux. it stores the desktop from ram on disk when you suspend the system. it's also the part  that OS uses disk when your ram is full.

---

### Post by Impavidus on 2013-04-07
I've never used anti-virus in Linux. The main purpose of anti-virus in Linux is to protect the surrounding Windows machines. Most people don't use it, except for servers.

---

### Post by arranskye on 2013-04-08
Hi  Thank you for all your help.  Yes I found and ordered the book plus downloaded and subscribed to "Full Circle"  Sorry cant find the "solved" button so added it to header 

Will start a new thread now as I cant download Flash player so cant watch you tube videos.  Thanks again.   ):P

---

