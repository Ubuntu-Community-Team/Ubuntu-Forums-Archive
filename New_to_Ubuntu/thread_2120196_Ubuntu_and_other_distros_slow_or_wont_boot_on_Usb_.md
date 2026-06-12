---
title: "Ubuntu and other distros slow or wont boot on Usb drive larger than 4gb"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by italianman on 2013-02-25
Hi, I have been trying several Ubuntu based distros on a Usb with persistent. I tried Ubuntu 12.04 on 16gb Kingston, and it was slow as molasses. I tried Bodhi, and it wouldn't boot or it would be slow on the 16gb drive. When I use a sandisk 4gb, everything was smooth with Bodhi and fast. It seems anything over 4gb just wont work for me. Tried a PNY 16gb, and the same thing. Is this due to fat 32 only recognizing 4gb ?  Are larger Usb pen drives flakey when it comes to running distros persistent etc ?

---

### Post by KnownSyntax on 2013-02-26
For me I've been able to install Ubuntu onto a 8GB flash drive and it ran just as fast as if it was on a 4GB flash drive. Are you making sure that you are formatting it correctly and testing it on the same computer?

---

### Post by sudodus on 2013-02-26
Welcome to the Ubuntu Forums :-)

I have good experiences with USB drives larger than 4 GB, for example 16 GB. I think the important thing is the read/write speed of the flash memory, which is often slower than the USB 2 interface. So if you get a fast drive, for example a USB 3 pendrive, it will be faster also in a USB 2 port of the computer.

But there is a drawback with the persistence compared to a live system. If you have stored a lot of data files and installed a lot of program packages, it means that there will be a lot of reading at boot and shutdown, before the system is ready. And USB 2 is very inefficient reading many small files, so it will be slow but not because of the size of the USB drive (except that a larger size allows more data to manage for persistence).

---

### Post by italianman on 2013-02-26
Hi Knownsyntax, I make sure it is formatted to fat 32, tried the fast format in windows, and did a long format that fixes bad sectors, and it still is extremely slow. Is yours running fast as a live usb, or with persistence ? And yes I am testing it on the same computer. I first tried 12.04 and it was very slow.Was not bad live cd, but terrible with usb persistence. Then Bodhi wich is small and fast. works perfect on sandisk 4gb, and slow and or boot error on 16 gig kingston or PNY.  THANK YOU for taking the time to help :)

---

### Post by italianman on 2013-02-26
Hi sudodus, I did not know USB 3 drive would be faster even in a USB 2 port. That is GREAT info to know. I will experiment and try ubuntu live. Since it actually runs pretty good on live cd, I imagine it will be majorly faster live vs persistence. What stumps me now is why bodhi would fly on my 4gb and slow and freeze on the 16gb like ubuntu. Even with the 16 gig I tried with a persistence of only 2gb.

What do you recommend for a fast USB Stick ?   And Thank You for taking the time to help people :)

---

### Post by oldfred on 2013-02-26
If you have 16GB why not a full install. I have Ubuntu installed in 8GB with 8GB for data.

I just posted here, so as not to repeat it.
[http://ubuntuforums.org/showthread.php?t=2120498](http://ubuntuforums.org/showthread.php?t=2120498)

---

### Post by sudodus on 2013-02-26
> **italianman said:**
> Hi sudodus, I did not know USB 3 drive would be faster even in a USB 2 port. That is GREAT info to know. I will experiment and try ubuntu live. Since it actually runs pretty good on live cd, I imagine it will be majorly faster live vs persistence. What stumps me now is why bodhi would fly on my 4gb and slow and freeze on the 16gb like ubuntu. Even with the 16 gig I tried with a persistence of only 2gb.

What do you recommend for a fast USB Stick ?   And Thank You for taking the time to help people :)

1. As oldfred wrote, you can also make a normal installation of Xubuntu or Lubuntu to the USB drive. It works well, better for long-time performance than persistent live.

2. I have two USB3 16 GB pendrives branded Transcend and Sandisk. The market changes so fast, that you need to check in a few web-shops, what is the best buy right now. Look at the read/write specs, they must be given with numbers.

See this link

[[COLOR="Red"]http://www.whoratesit.com/Best-Flash-Drive/Comparison/1[/COLOR]]("http://www.whoratesit.com/Best-Flash-Drive/Comparison/1")

---

### Post by italianman on 2013-02-26
> **oldfred said:**
> If you have 16GB why not a full install. I have Ubuntu installed in 8GB with 8GB for data.

I just posted here, so as not to repeat it.
[http://ubuntuforums.org/showthread.php?t=2120498](http://ubuntuforums.org/showthread.php?t=2120498)

Hi OldFred :)  I remember I watched a youtube vid doing a full install and formatting to ext4 and followed it closely. It ran real slow (ubuntu 12.04) I am going to sift through all your helpful links and see what I can try to do/ or doing wrong. Again thank you for taking time out of your day to help.

---

### Post by italianman on 2013-02-26
> **sudodus said:**
> 1. As oldfred wrote, you can also make a normal installation of Xubuntu or Lubuntu to the USB drive. It works well, better for long-time performance than persistent live.

2. I have two USB3 16 GB pendrives branded Transcend and Sandisk. The market changes so fast, that you need to check in a few web-shops, what is the best buy right now. Look at the read/write specs, they must be given with numbers.

See this link

[[COLOR="Red"]http://www.whoratesit.com/Best-Flash-Drive/Comparison/1[/COLOR]]("http://www.whoratesit.com/Best-Flash-Drive/Comparison/1")

 Everything works great on my Sandisk 4gb, and the Kingston 16gb and PNY 16gb just pooped out. I'm definitely going to look at the link and go for a 3.0 :)

I will experiment with a full install on my 4gb sandisk, and try on the 16gb and see what happens. i will post what I get.

Thanks to you to for taking the time out of your day to help people with linux issues. i have worked very hard the past year learning linux and it has been great. I will never go back to another mac/pc. Its fun to learn and the rewards are amazing using linux.

---

### Post by sudodus on 2013-02-27
> **italianman said:**
> Everything works great on my Sandisk 4gb, and the Kingston 16gb and PNY 16gb just pooped out. I'm definitely going to look at the link and go for a 3.0 :)

I will experiment with a full install on my 4gb sandisk, and try on the 16gb and see what happens. i will post what I get.

Thanks to you to for taking the time out of your day to help people with linux issues. i have worked very hard the past year learning linux and it has been great. I will never go back to another mac/pc. Its fun to learn and the rewards are amazing using linux.
You are welcome :-)

It's nice to help, when there is time for it. Anyway, it is possible to make a full install of Lubuntu on a 4GB pendrive, but there is not much margin to install extra packages or own files. I recommend at least 8 GB for that purpose. See this link how to do it on a 4 GB drive

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1872303[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1872303")

---

### Post by italianman on 2013-03-15
Hi all !!!  Been busy so have not had time to fuss with this BUT !!!!  I installed 12.04 LTS on my sandisk 4 gig with persistantce and it works flawlessly !!??!!  

So....  The only thing I can think of as what is going on are these issues.

1) 16/32 gig pen drives are flakey with runnning os on them.

2) Linux doen not like PNY or kingston.

When I have time im going to pick up a 8 and 16 gig sandisk and see what happens with them.  ALL times i tried, I only used 2gig for persistance and the darn 16 and 32 gig sticks just sucked they were so slow. And keep in mind I treid all differnt distros, and small ones with either slowness or errors. Also tried other computers as well. Would really love to know if there is anybody out there with the same issues.  Thanks again !!   Chris

I also tried a FULL install with slow slow results as well.

Typing this using 12.04 on the 4 gig sandisk :)

---

### Post by sudodus on 2013-03-15
> **italianman said:**
> Hi all !!!  Been busy so have not had time to fuss with this BUT !!!!  I installed 12.04 LTS on my sandisk 4 gig with persistantce and it works flawlessly !!??!!  

So....  The only thing I can think of as what is going on are these issues.

1) 16/32 gig pen drives are flakey with runnning os on them.

Do you mean very slow or errors? Please specify what problems you have!

I think that speed makes a difference, and I have seen no disadvantage with larger drives (I have 1, 4 and 16 GB drives).

You need to let the slow USB interface finish writing before you pull the pendrive. Otherwise you will get file system errors or at least incompletely written files. You can type [SIZE=3][FONT=courier new]**sync**[/FONT][/SIZE] in a terminal window and wait until it returns to prompt.
> 
2) Linux doen not like PNY or kingston.

Can't they be read/written for data? Or do you mean that linux will not boot from them?
> 
When I have time im going to pick up a 8 and 16 gig sandisk and see what happens with them.  ALL times i tried, I only used 2gig for persistance and the darn 16 and 32 gig sticks just sucked they were so slow. And keep in mind I treid all differnt distros, and small ones with either slowness or errors. Also tried other computers as well. Would really love to know if there is anybody out there with the same issues.  Thanks again !!   Chris

Remember to check that they are fast: select USB 3 pendrives if possible, but also USB 2 pendrive have different read and write speed.

If you have a FAT 32 file system, the maximum size of a casper-rw file for persistence is 4 GB. But Ubuntu will recognize a casper-rw partition. So you can make a 1 GB FAT 32 partition for the operating system and a big partition (the rest of the drive) and set its label to 'casper-rw' and format it to the ext4 file system.

An installed system will be more stable than a persistent system, and it can be updated without limits, while the kernel cannot be upgraded in a persistent system. A persistent system may boot faster and a live system without persistence will be the fastest.
> 
I also tried a FULL install with slow slow results as well.

Typing this using 12.04 on the 4 gig sandisk :)

I am happy with an ***installed Lubuntu*** system on my USB 3 drive, but maybe you should try ***Knoppix***, which is made to run live or persistent live? That might be the best solution for you.

---

### Post by oldfred on 2013-03-15
Often with a USB flash drive, you also need the settings similar to a SSD to reduce writes. Flash drive just do not support trim.

 With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

Several of my older USB2 flash drives are Kingston and I have had no issues with them. Most of my flash drives are Microcenters house brand. My issue is Microcenter has a store nearby and just about every time I am there I add another flash drive to my inventory. They keep getting lower in cost so I think I am getting a bargain.

---

### Post by italianman on 2013-03-28
Well I just purchased a 32g Sandisk from wally world. and 1...2...3... I did a full install on it and it works perfectly.  SOOO  the Kingston 16G and the PNY 16G must have sucked !!  Unity is runnning ok, but I always change up LXDE to my liking, and use that. This thing flies now !! I tried it on my old Dell Pent 4 with a gig of ram, and it is really fast on their as well.

The Kingston and PNY were so slow it wouldn't even work. I installed EXACTLY the same on the 32G Sandisk and all is well :)

Still curios if anybody has used these two with trouble.

For the record, here are the two USB sticks that were a nightmare. 

[COLOR=#404040][FONT=Tahoma]**Kingston Champagne Data Traveler SE9 16GB Flash Drive**[/FONT][/COLOR]    

 [http://www.officemax.com/technology/drives-memory-storage/hard-drives-usb-drives/usb-flash-drives/product-prod4330130?R=23666169&ssp=true](http://www.officemax.com/technology/drives-memory-storage/hard-drives-usb-drives/usb-flash-drives/product-prod4330130?R=23666169&ssp=true)


**[FONT=Tahoma]PNY Compact Attache 16GB Flash Drive[/FONT]**


[http://www.officemax.com/technology/drives-memory-storage/hard-drives-usb-drives/usb-flash-drives/product-prod4330150?R=23753555&ssp=true](http://www.officemax.com/technology/drives-memory-storage/hard-drives-usb-drives/usb-flash-drives/product-prod4330150?R=23753555&ssp=true)

---

### Post by oldfred on 2013-03-28
Thanks for the update.

I have had good luck with older standard Kingston, but primary just buy Microcenter. They now have USB3 that may work a bit better even with USB2 ports.

---

### Post by sudodus on 2013-03-28
> **italianman said:**
> Well I just purchased a 32g Sandisk from wally world. and 1...2...3... I did a full install on it and it works perfectly ...

Congratulations :KS

---

### Post by italianman on 2013-04-10
I wanted to say THANK YOU !!!!!!!!!!!!!!!!!!!!!!!!!!!  for all the help you people have given me. So glad there still is a thing called freedom, and generosity, and its called Linux :)  I will mark as solved. Sincerely, Chris K

---

