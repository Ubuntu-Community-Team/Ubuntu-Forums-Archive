---
title: "Ubuntu, Raspberry Pi B+: Problem with corrupted SD partition"
date: 2014-10-13
forum: New to Ubuntu
---

### Post by elisavet2 on 2014-10-13
[FONT=Times New Roman, serif]Hello, [/FONT] 
 [FONT=Times New Roman, serif]I am new in Ubuntu, Raspberry Pi and PanStamp. So, I found a “tutorial” to help me understand how can I work with them. I found this: [/FONT] 
 [FONT=Times New Roman, serif]https://code.google.com/p/panstamp/wiki/RaspberryPi [/FONT] 
 

 [FONT=Times New Roman, serif]The steps seem easy. [/FONT] 
 [FONT=Times New Roman, serif]1. Download the latest image here: [http://www.panstamp.org/lagarto_images/lagarto_rpi_0.8_2gb.zip](http://www.panstamp.org/lagarto_images/lagarto_rpi_0.8_2gb.zip) [/FONT] 
 [FONT=Times New Roman, serif]2. Unzip and write the image to the SD card (at least 2 GB) according to the Raspberry Pi Wiki: [/FONT] 
 [FONT=Times New Roman, serif]For Windows, use Win32 Disk Imager [/FONT] 
 [FONT=Times New Roman, serif]For Linux, use dd if=lagarto_rpi_xyz.img of=/dev/sdc [/FONT] 
 [FONT=Times New Roman, serif]3. Insert the SD card in your Raspberry Pi and boot it up. [/FONT] 
 [FONT=Times New Roman, serif]4. By default, Raspbian comes with with DHCP enabled so you need to get the IP-address from your DHCP server. [/FONT] 
 [FONT=Times New Roman, serif]5. Once started, you should be able to access: [/FONT] 
 [FONT=Times New Roman, serif]http://ip-address:8001 for Lagarto-SWAP [/FONT] 
 [FONT=Times New Roman, serif]http://ip-address:8002 for Lagarto-MAX [/FONT] 
 [FONT=Times New Roman, serif]6. You can SSH to the Raspberry and login using username "pi" and password "raspberry" [/FONT] 
 

 [FONT=Times New Roman, serif]My first target is to write the Lagarto Server into the SD Card. My SD Card has already Raspbian and has 3 partitions. The 3 partitions are: [/FONT] 
 [FONT=Times New Roman, serif]1)file system FAT32, with size 1,43GB (SETTINGS)[/FONT]
 [FONT=Times New Roman, serif]2) file system FAT32, with size 60MB (BOOT)[/FONT]
 [FONT=Times New Roman, serif]3) file system ext4, with size 5,68GB (root)[/FONT]
 

 [FONT=Times New Roman, serif]So I try to write the image in the 3rd partition, because Lagarto demands 2GB. The 3rd partition was /dev/sdb6. I edit the command above, as: if=lagarto_rpi_xyz.img of=/dev/sdb6[/FONT]
 [FONT=Times New Roman, serif]I waited enough time but no error was showed. So, I supposed that the procedure was fine. [/FONT] 
 

 [FONT=Times New Roman, serif]Then, I put out the SD card from the laptop and carefully, I put it in the Raspberry Pi B+. [/FONT] 
 [FONT=Times New Roman, serif]But, it shows me problem. [/FONT] 
 “ [FONT=Times New Roman, serif]No filesystem could mount root, tried: ext4” [/FONT] 
 “[FONT=Times New Roman, serif]kernet panic – not syncing: VFS: Unable to mount root FS on unknown -block (179,6)” [/FONT] 
 

 [FONT=Times New Roman, serif]So, I turn off the Raspberry and I put the SD card again to the laptop. [/FONT] 
 [FONT=Times New Roman, serif]I run Gparted and I noticed that “/dev/sdb6” has problem. [/FONT] 
 “[FONT=Times New Roman, serif]File system is damaged”, “file system is unknown to Gparted”, “The device entry /dev/sdb6 is missing”. [/FONT] 
   
 [FONT=Times New Roman, serif]Obviously, I have stuck in Step 2. [/FONT] 
 [FONT=Times New Roman, serif]What should I do now, so I can continue my work?[/FONT]
 [FONT=Times New Roman, serif]How can I un-done the command “if=lagarto...” or I repair the “damaged” partition? [/FONT] 
 

 [FONT=Times New Roman, serif]Best regards, [/FONT] 
 [FONT=Times New Roman, serif]Elisavet[/FONT]

---

### Post by tgalati4 on 2014-10-13
If I understand correctly, you had a working Raspian image on /dev/sda3 (the 3rd partition on the SD card, formatted as Ext4).  Then you overwrote that image with the Lagarto image (which is based on Raspian--but possibly a different version).  You still have the original FAT partitions that contain the original Raspian configuration and boot images.  I'm not surprised that it does not work.

I would wipe the SD Card and start again.  Format the entire card as Fat32 with just one partition.  Burn the Lagarto image onto the entire SD card.  Burn, not copy.  Put into the Pi and see if it boots.

SD cards are cheap.  You should have several.  You should keep one card with just plain Raspian (as you had before).  This is useful for testing your hardware if you suspect something is wrong.  Then use a second SD card to experiment with (Lagarto or any other distro).

The wiki shows overwriting an entire SD card, not a partition:

```
dd if=lagarto_rpi_xyz.img of=**/dev/sdc**
```

It's possible that the image has multiple partitions in it.  I don't know.  I haven't used it.

---

### Post by elisavet2 on 2014-10-14
i did not write this: 
dd if=lagarto_rpi_xyz.img of=[B]/dev/sdc
I change it. I wrote
dd if=lagarto_rpi_xyz.img of=[B]/dev/sdb6

because when i put the SD card in the laptop it "see" it like 3 partitions. So, i choose the partition with the biggest free capacity. 

That`s why the Boot and Settings partitions are fine. And the only partition I "lost" is the "Root" partition. 

Do you think that i can Format the "corrupted" partition only and then write (not copy) the image with Lagarto in it?
Or I have to format all the SD and loose the other two partitions?
[/B][/B]

---

### Post by elisavet2 on 2014-10-14
With NOOBS I managed to re-install Raspbian. 
Now, if i write again "dd if=lagarto_rpi_0.8_2gb.img of=/dev/sdc" but this time to write the img to SD and not to a partition, it will work? Or i have to install all the parts of Lagarto (pyserial, ZeroMQ with the Python bindings and Barrel), so to be sure?

---

### Post by tgalati4 on 2014-10-14
I don't know anything about Lagarto.  I am only following the original instructions that show burning the image to the entire device (/dev/sdc) not to a partition (/dev/sdc3).

Keep your working Raspian SD card separate.  Take a NEW SD card and write Lagarto and boot from it.

---

### Post by elisavet2 on 2014-10-15
The first mistake i did, it was that i burn the image to partition and not to entire device. Now, with help from NOOBS i restore the Raspian and work normaly the Raspberry. 
Then, i create an image from the current state of SD card and keep it to my laptop. After, i try to write Lagarto img (it is based on Raspbian), there was no problem. But then when i put the SD to Raspberry it did not boot. It did not do anything. Why this is happening? Do you have any idea?

---

### Post by elisavet2 on 2014-10-15
I brought back the correct image of the SD. And I try to install Lagarto step by step by this link [https://github.com/panStamp/panstamp/wi ... stallation]("https://github.com/panStamp/panstamp/wiki/lagarto#installation"). I did the procedure twice, but it did not work. I can find where is the server files and i cannot run the servers.

---

