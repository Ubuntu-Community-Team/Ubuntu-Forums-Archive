---
title: "dual boot ubuntu 20.04 / windows 10 cannot boot neither windows 10 nor ubuntu"
date: 2022-01-27
forum: New to Ubuntu
---

### Post by lennoxg on 2022-01-27
[LIST]
[*]Inexperienced Linux/ ubuntu user 
[*]ASUS Vivobook 
[*]Dual boot: Ubuntu 20.04  / Windows 10 
[/LIST]

I executed the command "R.e.i.s.u.b"; but Ubuntu did not reboot as expected but went to the setup menu instead.
I Used the following instructions from  the site in the link below to try and repair boot

sudo apt-add-repository ppa:yannubuntu/boot-repair sudo apt-get update

sudo apt-get install -y boot-repair

boot-repair

[https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)  

 but repair boot failed. the message i got  said i should create a bios-boot partition with Bios_grug flag and try again. 

I followed the instructions from this site  [https://www.youtube.com/watch?v=Lk6mvVU7GOU](https://www.youtube.com/watch?v=Lk6mvVU7GOU) to create the Bios-boot partition but repair boot failed again.

The system produced a Bootinfo summary which can be found here   [https://paste.ubuntu.com/p/CxNxBGCzxZ/](https://paste.ubuntu.com/p/CxNxBGCzxZ/)

Thanks for your help

---

### Post by oldfred on 2022-01-27
You do not need nor want a bios_grub partition. That is for the very old BIOS boot of grub on a Windows system installed in BIOS mode.
Microsoft has required vendors to install in UEFI boot mode on gpt partitioned drives since 2012 and release of Windows 8.

You do have UEFI Secure Boot on. Was it on when you installed Ubuntu? If not turn Secure boot off.
Did Windows or Ubuntu do a UEFI firmware update which probably reset some UEFI settings. Review the settings you changed before you installed Ubuntu. I have to keep a list as my Asus system has multiple settings that I change, some required & some optional to make system better.

You do always want to boot in UEFI mode. Your installed systems are UEFI.
But boot of a flash drive for repairs for either Windows or Ubuntu must be in UEFI mode so repairs are in UEFI mode.

---

### Post by lennoxg on 2022-01-28
OK I will read up and check it out and get back to you

Thanks

---

### Post by lennoxg on 2022-01-31
Hi oldfred

I didnt get the opportunity to try anything much over the weekend. so i dont have much to report

I will try some things today and i will get back to you
Thanks again

---

### Post by slickymaster on 2022-02-01
*Thread moved to **New to Ubuntu**.*

---

### Post by lennoxg on 2022-02-01
Hi oldfred 

I am about to use the the following grub boot loader reinstall procedure taken from [here]("https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition") to reinstall grub

             130         
                                                                                                         

             [B]Reinstall the GRUB boot loader to your Ubuntu installation in EFI mode this way ...
[/B]
[B]Boot from the Ubuntu installation medium and select 'Try Ubuntu without installing'.
(Boot your install medium in EFI mode, select the Ubuntu entry with UEFI in front.)[/B]
**Once you are on the Live desktop, open a terminal and execute these commands :**

 [B]sudo mount /dev/sdXY /mnt
sudo mount /dev/sdXX /mnt/boot/efi
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
grub-install /dev/sdX
update-grub  
[/B] **Note : sdX = disk | sdXX = efi partition | sdXY = system partition**


Below is a list of my main disk partitions. as listed by the command sudo fdisk -l   
i can identify my main disk as /dev/sda and my EFI partition.as /dev/sda4
I am not sure which one of the others is the  "system partition" 
Please tell me which one is the "system partition"
Thanks again

[B]Device          Start        End   Sectors   Size Type
/dev/sda1        2048     534527    532480   260M Microsoft basic data
/dev/sda2      534528     567295     32768    16M Microsoft reserved
/dev/sda3      567296  978100223 977532928 466.1G Microsoft basic data
/dev/sda4   978919424  979738623    819200   400M EFI System
/dev/sda5  1951885312 1953523711   1638400   800M Windows recovery environment[/B]

---

### Post by oldfred on 2022-02-01
Windows would normally have sda1 as the ESP - efi system partition.
And that would be FAT32 with boot, esp flags when using gparted.
But it now is FAT16, or how did that get changed?

So then it looks like new ESP as sda4 was created. You should only have one ESP per device or drive.
Your sda4 was a bios_grub partition for BIOS boot.

At this point I would deleted sda4, reset sda1 to a FAT32 partition and use Windows repair disk to totally reinstall Windows boot files, so sda1 has UEFI boot files for Windows. Then you can install Ubuntu to a new partition.
Your sda3 is NTFS so I assume that is your Windows partition.
You may need to shrink that to make room for an ext4 partition for Ubuntu, but only use Windows tools to shrink NTFS partitions.

---

### Post by rookie69 on 2022-02-02
Hi
I'm also new to ubuntu compare to other members here. But i do know a thing or two about dual boot since i have been usung dual boot for 6-7 months 
I have seen many videos where they tell us to create boot entry in windows but you don't need that (at least in my system)
Let me tell you what i did

_**I have uefi and my secure boot is on. **_
 
First install windows and let it run for some minutes and do restart several times. 
after that install ubuntu ( you can create as many partition as you like but do not create more than 4 primary partition, you can use logical if u like, And do not create another efi partition) **EDIT: You can use primary partition in uefi. No need to use logical partition. **
when you install ubuntu completely use ```
sudo update-grub
``` which will find windows and add entry to grub menu
Next thing you want to do is go to your uefi menu and Select ubuntu to boot first. (i think it is called boot order) 
And boom you can choose from grub menu what should boot (default is ubuntu) it's more hassle free.

---

### Post by ajgreeny on 2022-02-02
> **rookie69 said:**
> Hi
I'm also new to ubuntu compare to other members here. But i do know a thing or two about dual boot since i have been usung dual boot for 6-7 months 
I have seen many videos where they tell us to create boot entry in windows but you don't need that (at least in my system)
Let me tell you what i did

_**I have uefi and my secure boot is on. **_
 
First install windows and let it run for some minutes and do restart several times. 
after that install ubuntu ( you can create as many partition as you like but do not create more than 4 primary partition, you can use logical if u like, And do not create another efi partition)
when you install ubuntu completely use ```
sudo update-grub
``` which will find windows and add entry to grub menu
Next thing you want to do is go to your uefi menu and Select ubuntu to boot first. (i think it is called boot order) 
And boom you can choose from grub menu what should boot (default is ubuntu) it's more hassle free.
I think you have confused things even more than before by talking about a limit of 4 partitions and the use of primary and logical partitions.

A disk which is using GPT and UEFI rather than MBR, and UEFI is recommended on hardware that has been around for the past 12 years or thereabouts, is not limited to 4 partitions and as far as I'm aware will not even offer logical partitions; I think they àre all primary and that is what should be used.

---

### Post by rookie69 on 2022-02-02
> **ajgreeny said:**
> I think you have confused things even more than before by talking about a limit of 4 partitions and the use of primary and logical partitions.

A disk which is using GPT and UEFI rather than MBR, and UEFI is recommended on hardware that has been around for the past 12 years or thereabouts, is not limited to 4 partitions and as far as I'm aware will not even offer logical partitions; I think they àre all primary and that is what should be used.

Sorry about the partition thing. It's something a senior of mine suggested. Beside that which part is wrong brother?

I said you can create many logical partition in ubuntu but if you create more than 4 primary partition it causes problem with windows not sure about that. But making a logical partition causes no error as i can see. Sorry 'bout that i don't know exactly if you can create more than 4 primary partition or not.
Please refer to this link [https://unix.stackexchange.com/questions/71090/cannot-create-a-partition-after-the-4th#:~:text=PC%20partitions%20are%20a%20bit%20limited%20and%20awkward,partitions,%20you%20need%20them%20to%20be%20logical%20partitions](https://unix.stackexchange.com/questions/71090/cannot-create-a-partition-after-the-4th#:~:text=PC%20partitions%20are%20a%20bit%20limited%20and%20awkward,partitions,%20you%20need%20them%20to%20be%20logical%20partitions).

---

### Post by oldfred on 2022-02-02
Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012 and release of Windows 8.
The old BIOS boot with MBR(msdos) partition was Windows 7 and before back to DOS, but even Windows 7 could be installed in UEFI/gpt mode if Secure Boot off.

Users can install in old BIOS/MBR mode, but really should not, if hardware is newer.
Only MBR has the 4 primary partition limit. And if one partition is made the extended partition to act as container, then an unlimited number of logical partitions can be made.
Gpt has a soft or default of 128 partition limit, but even that can be increased.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

With Ubuntu you can use gpt with old BIOS boot, but then need a bios_grub partition.
Windows in BIOS mode must use MBR.
Windows in UEFI mode must use gpt.

---

### Post by rookie69 on 2022-02-02
> **oldfred said:**
> 
Windows in UEFI mode must use gpt.
Thank you i thought windows use mbr in uefi.

---

### Post by oldfred on 2022-02-02
Both Windows & Ubuntu default to gpt with UEFI.
But Ubuntu will let you install in UEFI mode to MBR drives and probably should not.

Both Windows & Ubuntu install in boot mode you use for installer. Or if you boot installer in UEFI mode, it installs in UEFI mode.
If drive is MBR, and you install Windows in UEFI mode, it will totally erase all partitions on drive. Do not know if Windows gives warning or not.

---

### Post by lennoxg on 2022-02-03
Hi oldfred

I did as you instructed. I deleted sda4 and i resetted sda1 as you can see in the image below
Next i used the windows repair disc to to totally reinstall Windows boot files, so sda1 has UEFI boot files for Windows.
but it failed at first giving me an error code  0xc0000185.   that error code indicated that i had to rebuild the Boot Configuration Data in windows using the bootrec command in windows command prompt.    after doing that i used the windows USB live flash disk to perform "startup repair" which was successful. Windows 10 is now up and running.

However on rebooting windows, i do not get the option to boot from my previously installed ubuntu 20.04 even though it is stated as one of the boot device

Below is a picture of my devices and partitions as seen in GParted

[B]NOTE: I tried to add an image of my GParted screen by copying and pasting, but it woukld not allow me to
Please let me know how i can send yo an image of my Gparted screen
[/B]
The un-allocated 464.34Gb partition seen in GParted, is where my previously installed unbuntu 20.04 operating system and my data files reside. i would like to boot my old 20.04  OS rather than do a fresh install.

Thanks again for your help


[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA8EAAAGXCAYAAACTAFLDAAAABHNCSVQICAgIfAhkiAAAABl0RVh0U29mdHdhcmUAZ25vbWUtc2NyZWVuc2hvdO8Dvz4AACAASURBVHic7N13fBR1 sDxz8xsySbZ9E4ghR567yKKHXs5z4bt7N553llOT089 3mWn3dnO/VU7A0LCiogUgVF6Z0EQkgCqZu2bWZ f2wSEkjIJqQpz/v1yguyO WZmd3sPvN8CwghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghhBBCtDuljeuFAolAJGAHtHaLSAghhBBCCCGEaJoOeIByoBCobu0GWpsEK0C60 mcnjVgwH3hoaFJmsWiKkpbc2khhBBCCCGEECI4pmmi /1GZXV1wcbNmtqKhYAOQAZrDbaE32qgBZWQMGPJuSnDzN7fHg9XrRdR3TDHp/QgghhBBCCCFEmyiKgqZp2Gw2Qux28vLzv9m0efMtwEaCTIRb04w5I2vAgOcT4uOnlbtc Hw DMNoU BCCCGEEEIIIURbGIaBz fD7fEQEx2d6QgN7VdUVLQYKAtmfTXI/YQ6nc7p8XFx01wVFVL5FUIIIYQQQgjRpUzTxFVRQUJ8/HSn03ksgbGrWhRsc iM0SNHfmuaZi9JgIUQQgghhBBCdBeKoqAoyq4fVq8 lkD/4MMKthIcqWlakiTAQgghhBBCCCG6E9M00TQtGYgKZvlgk2C7YRjWtoclhBBCCCGEEEJ0jNp81R7MssEmwZphGDIPkhBCCCGEEEKIbqc2Xw1q4GdLsBuVptBCCCGEEEIIIdqDAiRbDaK1wIxDJbpKgU8NfrLfg7QmXw06CRZCCCGEEEIIIY5EgsXg3GgPk8N8xFgaT7lb7FdZWmXlg1I7 /3BNlpuPUmChRBCCCGEEEJ0uLOjPFwe68amNF21jbUYnBHp4eQIL68WhzC7LKguvq0mSbAQQgghhBBCiA51Y3wNMyI9QS1rU0yujash2Wrw3H5Hu8fScTVmIYQQoh2okRmMnjaD82aMIKYbfWp117i6OzlvQghx9DknyhN0AtzQGZEezopq/XotkY8fIYQQXczB L98xuLlS/nkznGEHPSsbczv MfDd3PzBSOI7uR9H07HxtW9qPYoevTtQ2JrTlAzjqbzJoQQAuItBjNj3Y0fVA6Thh703OWxbuIO6jt8pKQ5tBBCiK7lGMX0KTGoxn6 Yn3C2v8evYdyso4b05/reXcta0UfTtEY3DrKY4bxtrl37GG/ bx3Z3D8569GmuGZNMRIiCqfuoKd/Hrk0/sPCjWXy4LI 23kdXnKfwyKf3MNmymecvuZo3drXvFxEhhBCdZ ny5Yd9ftKECe2 z/OjPY37ACsqUfe8jmfJZ9QseLfRso7jfoN98umU/f0yMAOfN3bF5LwoD88XtV zaEmChRBCdKmwsScwMVLFKFzE/DXeo2bfwVJjp/CnZx/gzIwQlPpHnSRkjuS48N3MeWUuYCc6KZHIEAXDU0WlV8MR1YOsSakMnHAMQx 6iru KKBN6auiomlKy8sJIYT4RWgu0W0pQW4LBZgY5mv8oGngXvIpEdc DBYrNV/NAiDkuAtwXvsQFS/fV58A15kc7uOFIkebp086mCTBQgghuo7iZNwJE3CqBvnffsMGHyjhAznr97/nt1OzSLC52LNPxQKNEzgtjtEX3cjVZ02mf7xGxZ61fPvmv3n i21UE8Upj3/E3ZPtFMhfMeW4UPlfTL/str1w/A/Plpfnvje SbB 9bI3HSVdxyzQxGZURjcZexL2c z97 DEvLzCDicjD62ie45ZTeJMWEYfGWsXvdAt569nnm7qxp4/mJ4tg/3MkZGSGYrnW899T/8f7y7RR7Q4jLGMrI2FxWu2nQuUln88tXce0bu1GjBnPxg09x9agYJpx3Ir3mvk/c7w4Tn9qT4264lnPGDSKzRyzhFg l2z/kb7flBjZtGch17yzlOsD381P85sb3KFQOcx1qv6kEdT2FEEL8KiVZDWKbaMrsXvAeQCARBky/l4hrH6bi5fvqk KGYi0GiVaDAl/79OaVJFgIIUSXUSImMH1cOKqey7ffbMKnJnDKPU9y6zFRKEYNZSUWklMjUWmYNIUy4oZneOK3mVh8ZeTvcxOdNpZz7 pDtHcm935dwsola/FMGkf0yDH01Vax0YxlxJjeaOhsWrKcQgOUyMb79sedwp8fuJyJDj/ledns8YSRFG/DW2WCmsDJLcblQw9PIt7mpnRfNY6YRDLHn89fEqrJmfkCm/1tOD xx3LGMdGoZg0/vHgP/5pbWLs/N3s3fsfew6zrL9vI10t3csWooWix8cSoLcSnpDHpzOMYEQa 6lLKqhyE65WU6LUbND2U5Rfi8oO/oAK9xetQjBnUeRNCCPFrFaM1/9feveA9FBSc1z4EQMULdx/SPLqhWE2SYCGEEL94ClGTTmBMmIKes4D5W/yoqSdwzoRIVD2Xj269midXugg75R98du/k mKnmnASM8/JwOJbzwtX3MgbO/0knPkEs 4Yz5QzjyV /ocULVvEOu9YxqSMZ1z682wqHsOEQVYU/xYWL83DQCH64H3360mKXcF0r bFm/7E7EId1WIBP6i9Wo4L/Kx56nxOedqGMzqS0Jhp3PH87xnTczjD4lU257c 7dNSM hpVUDfzeqf9h9IHJVwUgdmEmM1Kd 1gV2ug86saic6fRznntAXC6DvK2C/4SfvcPEV1a5s7uXDP17Is t0rFYNv OkwOP6Tt659UCfYDXhbP7a0nUI4noKIYQQnU2SYCGEEF1DiWHS9FE4FJ0dCxawXQctrQ9pFgWj AcW/eTCBPy xn2JtL6DGWBXUJTBXPfmIq5r8JyR1INEFfYVLWb TzczenwGEyf25OOCKQwLAd Gb1i42wAl9pB969nLWZb7W9LSx/Kndz7kpIWf8v6s91i4sxJLEHGhJjD ur9y63mjSHKoB/rv kNxHDKWh5XJf/uSR08Oq13OxDXnNs54cCmNtqooB7bTsCOUZRAX/ NJzojx8 09J3H3gvonyLrhXb674cCipr6Pb9 dRx6tiS wQ5/Pj9LMOCTBXIfSYM6bEEKIX60Svflbng37ANc1h27YR/hgxYfZVmtJEiyEEKJLqPHHMH1ECIp/KwsW7EAHVMxArmexNv8BpaqogOnZxoJ3l7KnQYHVKF9DoQGYxSz56gduHjeZvlNP5eyi0YThY803C8kzQE04dN 4f a5668n5 JLuWDGRIac8juGHDuFV268hjeCiCtsyg389eIxOCvX89FzH7Kuui9n3/pbhtnafo6MvbvZq5skWnoxcmQ8b2QXttCM2MTQ/fi8HmrKC8nZuIoFH77Np6uLcEy9r23xmbXHjoLScHysYK5DMNdTCCGOAl0xKnN3UOBTKfarh/QLDjnugib7ANf1ET44ES72qxS2U1NokCRYCCFEl1BJOGY6w zg3zSfhTmBD0d951Z2 k9maMREzjypBz9 nnfImnr2Nnb6T2KINRpb4Te8OXsHVQZYo5KJ8hawvzb5Kv3ucxaXTeKkrN8y02 B6qV8/nU BipJTewbSwTR5lbm/PtO5rzShyuefZWrB/VhyvievP5VS3GpxKT2IEwFfcsXvPbBXIotpYy84cJmkkwfS 6fzuT7D3 WjP3fMXfVtQyfGM7Iax7g tJ/8ObiHZRB44T0wNlh8wuXcO0buw9KllWSWhXfAaankkqvCY4kMjPCUHIqUCwWzCCugxrE9RRCiKNBd0pyO2IU6OaYwNIqK2dENpioT1EJmXTGIX2A6/oI2yefTs3XbzUaIXpJpbXdRoYGSYKFEEJ0BTWZqdOHYMXP vkL66uIxt4vef2L83j0jB4cc9fbfH5dCR57DFagbnwmI 8L3ph3Lg flsKUP7/OnOvLqTQdRIS5mfvnM3h4eW1z26oVfDJvLydemIrValA0bzbflZigpjS5b8uAy/jPf84hdN9e9ldaScrUwKwiP68EvcW4DPZt2UqJMZj4UTfxwsvHkVvhJMN5hFMLGfuY 9QzTOxzB8ckDOWih97gt6aBaSooamu2fQTx Tfx49pqTpgQxfT7P2LEHzyEVM/l1pmzWrwOwVxPIYQQnacrkvH3S 2cHOE9MFewaVD24GWHTIMEULPgXWoWvt/oOY p8H6ZvV1jknEphBBCdDo19VimZ1nAv4EF3 49ULU0y1n xI3c8eI81uZVYYmMJ9Lipmj3Jn5YtZ1yALOMpY/dwG3Pf8nPueX4QyKJsHnZv2MzhT57g7l0vaz/4APWeUxM/w4 fW8FVYfZt6a62JPjwhafQd8 ibBvA1 /cBdPflOGGURcnh f5 6n57Bur4/ofqMYPSoDh2sPm3/8ieyKtp8r/57Pueeqm/nnu9 xMa8Mtx8U00dVUS6bVnzF97uCG3a6zfEZ 5n7 AO8tTybMj2E6Bg7FRUebGoQ1yGY6ymEEOJXrciv8mpxSOMHm0iAm3vulaIQiv3tm7YGext54sjhw5e2656FEEIcpVTSZ77Ma9f1R//hn1z4hw/Z12nz5XTlvoUQQoij1/XxNY2bRQfhkzI7zxc1M0JjE1b//PMkYFlLy0lzaCGEEJ1LzWDa8X2wmB5Wz19EUWcmoV25byGEEOIo9tx B/k lSti3QeaRjfDayq8XBTCp Xt2wy6jiTBQgghOpXW93iOz7Rgulcy/7viFkY7/vXsWwghhDjazS6zs7jSyvlRHiaH w4ZNbrYr7K40sr7ZXZK2rkJdEPSHFoIIYQQQgghRKdSgESrQawWSISL9cA0SEcyCrQ0hxZCCCGEEEII0S2ZBOYRLmjH X DJaNDCyGEEEIIIYQ4akgSLIQQQgghhBDiqCFJsBBCCCGEEEKIo4YkwUIIIYQQQgghjhqSBAshhBBCCCGEOGpIEiyEEEIIIYQQ4qghSbAQQgghhBBCiKNG0PMEl5SWdmQcQgghhBBCCCFEhws6Cd60eXNHxiGEEEIIIYQQQrSZw EIajlpDi2EEEIIIYQQ4qghSbAQQgghhBBCiKOGJMFCCCGEEEIIIY4akgQLIYQQQgghhDhqSBIshBBCCCGEEOKoIUlwc8xifp79Cu vKsE8mmMQQjTP3MfSlx/imXl7MLo6FiGEEEIIEZRfVxJs1lCw8XtW76o 8qRRL2DFRx/x3c522FZ7xeDfyKvXns9VL6zBA 17vG1xcDxHm6Pl Jt7nQX7evw1nyejjC3Ll7E 3y03qoQQQgghfiGCnic4WGbNbpZ88DaffPsT2wrK8VmcJKZnMebUS7nipN44TBeLHruWJxaV4DVAtYQQEd L/mOO57wLT2dorNb2netbeP/vD7Dj3JcYkRbafgfVHsxSvrjrEp7 0XfQExb6X/Uiz/wmteU7EmoYcamp9IwPR4OOOV6zgoUPzuTx7Sfyj5evY/BBrxD/hhe4 rb5DLr3NW4be1A83clBrzPNFkZkQi/6j5jMKWfNYFxqyJHv4 Dr0ZW64n0V7OuxO52nOrXvx//Y/8T79x1HwxnlPIv zrmPV3Ld648yI1bpshCFEEIIIUTHaNck2Kxcy6t33st7efFMPO1C/pCVgLW6hPzsDeRUmdgA0Kkqd6EPvIiHrx5DiK a0rz1fP3ey9y5KpcH/nUTo8N/vV88LUMu5cErRtSeCwCV0KT44Eryahqn3/MUp3dYdIDiZOy0sYQvW8K3G65k8DBbgyd9bFq0hH1RE7l5hKNz4mmzutfZxTx85UhsvipK8rawct573H/DPE668xFunhh3ZE0hutXxd8H7Ktjj71bnSQghhBBCHO3aMQn2sGHWU7y/O41LnniUS/o1rK3MOGRpNaInWVlZgQrMsNGMz/Bxza2fMn3zF6io09cx7kb6//SIHLhyWyJ8NOvprfXzaGOBUwS1j1 r9487uN5BS48FpjmHTjM9w1DcDPxhcv56QXAWxMuftD7plqB38h37/9Em/NX0N2sU5U30mcf911zOgXhgLg3cOi/z3HrG/WklcTQtKATGyVJtb2O0GB43b2YODgwY0qT/VaisHIZtaNN7NgzD956cr tVW1Zo73CISNmsb4yEUsW7iO3w0bRf3WvBv4dmkxsZOPZ6i9mXiaPc9WVj99GfdsOoVn/zOT3hrg 4GnLrmPvZf8j8dPj0PBpHzevVzynI0/v3kPU8OO6DAAUCNSyao73yPGMfXkExn yB958ql/M3jAvRwfoxwmZgsr/3kp928/g3// xIyVACT4s/vZOar0fzl9d Q/eeDjt8oYc0HL/LKZyvZUeLHEd Ps25/hIuzrC2/BttBp76vpuwN7vXY1HJGMavffYFX56xkZ6lCTOZYTrvqWi4YHhO4MWEWsfi5J3h7ZQ75ReW4cRDXexznXHcjZw0Mb7fzFZTWXDeziKUvPsnbK3ayZ185XtVJ8sCJnHH5FZyRFdm5cQshhBBCiCa1XxLs Zkv5 cTOfU6zu3XZIp3WGqIA5ui4/XqgEJ01qlcdcd5xIWbFP38Ps/973Fe6v0qd04JRzHL2bJiBQUpl3H7zYNx6hWoqdEo5AIWep9/H7edEI KQliCDXCz/tW/8uDCBC64/m/cFFfBj2//i fue5Gk//6RMY4qfnzhrzy2IJQTZt7J9WkWijfM4 3N7Z8EN8tsawxNHe8Rcoxg jFxzP/uW9a4RzG2tuWwZ923LCtN4YTpA5uJ6fDneeDwQdjmb2GLy6R3tIKeu5HNLh9Fm7bhPT0OOz62bdwK/S9hUEe1ZrckcfxlZzD7 lnMXVzEcWc62XCYmAePHop94RrWFV9MRrwCVLP p61og25gcAhkN9q4hy2z/so9H pMvvSPzOznxFdSTniSpcVzM6aDjrdj31dNnuAglvOw bW7 dtshWOvvIOr002yv36dV /5K94nnuay/jYwK9i1bh2l6Zdz5x/6YXXn8f17r/Di318i9eU/Mqb1f2KaZup4vd5GzbR9fr3Bby1ct4PvN5kVZP 8hqK0mdxxc19s7gLWzHmTF/ yg6p/PslFfTrtL4oQQgghhGhGuyXBRtFu9lRpZAzsR1C9LWu/fKq Kopz1/LVK5 RYxvMjMGhgEJYxmgmZgQW7dcnnJxFN/LV5lz0KQNrg1YJzRjBuOH9D3yB9Qf sUf3ICM9pb7qYlYs48M5RYy6 QkumRKoxvS5uZAfLn T79bfxOj y/jkmyIGzHyJW85KDqw3JJwdX61kQ/ucnnreZY9y5omP1v uRJ/Kw2/ewsiqtsdw8PEeORuDTzyeHp/PYcGPVYydFAbU8PPCFbgyz2J6n6ZfNi2e5yEjGMCrrN3k5tSJIZSsW0eBIxxl41q2 ycwSMlm7foq0k4YTkwHlszUHn3oHWbwQ 5e/BXFh495 DiGaM ycnU5p58UheJex8q1OgMvH0GEUtF4w5Ur GD2LtIvep4/ndezUWLV0rkZM7adkqNOfF81NxxyS8uZlSt4/7NcMi56nj e2RMVGDa4BzU5N/D B99z7t1TCDQCUHD0GsroEf3RGMawuEJW/2E q7b5GTO0ff50eZf/g/Nn/OPQJ6wjArG2dN1GNbVVhdBewxg7MnAOR43OhJv yMcfruLsOyY23QpECCGEEEJ0mvarBJsmJqAoB/ey1Nnx1p 5d/kI7n36MvrXPt3oy6diISJ9PJfdexOnJiqAj/xlb/Lye4vZuKcEj9WJtVpHy/K2KTR9zw6y3dUU/vMiZjxZHzC6X8FeUo0/L5vdvngmZSV0eHNF67Ar cd1Y qbGCuWCJI10DsxhmBomSdwYr8PeOub7ymfeBwRVSv5Znk1g2ZOo2czHWlbOs MGcXYPs/z4eqt CZksu7nHAac9xtCPviWNXsMBlrXsmZfCmPGpHTasOUtxhwxlmOGq/xr Q 4TpxOyLrl/OgdzGUTYlFonAT7c7ey3R3PxKHJhwwA1dJ TNqnqWxnvq/aSs/dys7a81R/nbUeDB0cxxsrt7JHn0L/Jk6GmphCouqivKL9xmG2DL2MR64aRcN6tfenV7jrzdpYW7xuQbD1ZvSwaD74eSt5 kT6dJvRwYQQQgghjk7tlgSrsSkk2Q027sjBx7BGXyr97nJKy6vxN/jGaBl6GY9cPQaHNQRnbCKJUSH1X4iNnA946JFPUE 5nttu6Ee0soc5/3iYZcEE0lQmYZqgxnLcnx/mwr5ao4UdMU6U3QpggtHxk5woYQlk9O59SDXIr7Qxho7KmNUUjj91BG/96ysWF01l4uqvWaWM5Y/HHiZJb k8K05Gj0vnlXkr2VZVxapNPRh91TQca99iweoCjresJDt LDekdWyWYOzZyvYqlR49U9BajFlh7LGjUJ/5jpXlk4ha/D2eoVcyIVrhkAyo9kZQk1raTzsdW6e r45guba80xTNgoaJ0Y4T8qrhKfQbOLDx6ND7IlCoDPzS4nUrDGo/h94cFEIIIYQQXaX9KsEhw5k2MZLFC99h7lmDOCP18JtWw1PoN6B/k00DvdlbyTEG8/tLT2CEUwEzlB7OYL5E2rDboKqyGgPqq3FajwzSrLPZkWeQfFz6IQdt9uxLb/vH/LR6N/6szPafNyoIWptiaPp424dCzOQZTHrlAb6YuxTXyjWET72f8RHNZzktnWeA1EmTSZ/1FQs/KmFN1AjOS44jdEwG/102ly/UrcRPupreHXkB/Hv5 n fkR02lj9PicOitRxzxPgTmPDCI8z/ huivtcZc9NEomrvWTSk9cgk3foJ69bmow9s3Bw6mHPTHjrzfdXW5QKv9dmsW1uAMbB2ajA9j3Ubigjp3ZdUjWabWne2Fq9bXfdh8zBpvZHPhk3F2NMySJYqsBBCCCFEl2u/7 JKOOOvuJ5j1z3Gc3/6MzvOPo1xfeNxGBVsyq5u1aasPTPoYc7mize/Ie7YDCK1Igqqgqgdaan0ybQxe E7fDLgdDLMQsojJzA1axLnnPwOd733II9oF3HSoASs7v3sciVz4vQsQsMncP6Zadz27gM8xKWcOiQBm3sDeTXtXxk2XLtZv2ZNo0q56kiib782xNDs8bZTZTF0FGeenMIfPvgnef6eXHDrMA437rQS2cJ5VkDtMYWpfd7g1Xf3k3r U6RrCuqESaT/7xXeN1K54Jo 7ZogGuW7WbdmDTZ/DaV5m/n qzks2h3FyXfeyLQYBYWWY8YxkpOnRnHH6y iRZ7A/WObHp1YiZzEOae8w1/efIDHzYuYPjAWraoQd9IxTMwMYj8drN3fVwPatpwSPoHzzujJ7W8/xNOOmRyfZpL9zWu8nZPGOTeNox0GBW83Lb6m1QiinCaFa77jh7wejE0GMCha/gFv9ziWgfGQu3AWb 9I4uSrx3arYxNCCCGEOFq1a0FKiZvKbc/EkfX2u8yd8zwLiqvRLWFEJ/Rg5PiBxATZIlDrcz6331TMv997nntnV2FYHTije9I/uYXkTongmKtuZt0/XuH1B5aih6Uw rL HJOVxrDfPcp9kf9l1rzn Psb1RAWT8aUq5g8HUKxM Cyh3k44hVex5HnizAt3mJL7HECb1Cm3XFsf 9W9x921vNXrM0vsy/v3vS1ofQ7PH217Nay30Oe0shn38f2wedRanpLdUxgpt4TwDagrTThzKG1tLmXJMZqBamDyZY/q yjbjBE7IbK9SmUZYZATaT29zz 1vo1pDiUxIY8DI33DfnTMYl1o3fFsQMWNj0KknkfHZLPwnnsawZu8EOBh69SPcH/ESr895lvtfc6NF9mLKNSOYkBkXxH46Vru/rw5OgoNdDjsDZz7I/fYXePXdR7mrDKIzx/LbB67jgv5HNr1X 2vh9aEkctzF57H8/ bw0hcTGHVVoAZvs7hY/faTvL3PS3jqcE6/63pmDpMhsYQQQgghuoNgc6WJNTU1Szs0EiGE KVrci5vIYQQQgjRGRwOxyRoecgbGa1FCCGEEEIIIcRRQ5JgIYQQQgghhBBHDWkOLYQQQgghhBDiF0 aQwshhBBCCCGEEAeRJFgIIYQQQgghxFEj6CmS8vPzOzIOIYQQQgghhBCiwwWdBCcnJ3dkHEIIIYQQQgjA6/WyZ88eXC4XhmF0dThCdFuqqhIREUGPHj2w2 1Brxd0EiyEEEIIIYToWF6vly1btpCUlER6ejo2m62rQxKi2/J6vRQXF7N161b69 8f9HqSBAshhBBCCNFN7Nmzh6SkJGmFKUQQbDZb/XslLy8v6PVkYCwhhBBCCCG6CZfLRVxcXFeHIcQvSmxsLC6XK jlJQn hTgaBiY7Go7xl0SuhxBCCNH5DMPAarV2dRhC/KLYbDZ0XQ96eUmChRBCCCGEEEIcNSQJFkIIIYQQQghx1JAkWAghhBBCCCHEUUOSYCGEEEIIIYQQR41OmyJp/fr1 P3 oJcPDw8nNTWVkJCQDoxKCCGEEEKIX7aCggK //57du3ahcfjwePxYBjGYddRVRW73Y7dbictLY3x48eTmJjYSREL0bU6LQn2 XyMHj26xeV0XaeoqAiPx8OOHTtITk4mJiamEyJsnun14N djX/XDvTyUqipCTzhcKBGRmNL74PWMx3FZu/SOMUB27ZtRTcMFABFCfzb7P8VUEDTNDLSMzo91qYsXbq0foQ7TdOYNGlSF0ckhBBCiO6ooKCA1157jbS0NAYOHIjVasVisaAoymHXM00Tv9 Pz ejqKiI//3vf1xeWSCIujQqclwaZpYpombre7yecVRUHXdaqrqyksLKRv376YpkleXh4ej6drJgzX/bjXr8GzaS3WuDissdHY01JR7TZQwHB70Ssq8GZvxb9qObasoYQMGgpap51W0Qyvz0v/fgNatc7OnTs6KJrWqXuv1L3mi4qK0HUdTdO6ODIhhBBCdDfLly8nISGB0NBQSktLMQwD0zSDWldRFFRVJSwsjPj4eFasWMGZZ57ZwREL0fU6LVure0M296ZUFAXDMNB1Ha/PR0hICFFRUfh8PoqLi/H7vMlJsgAAIABJREFU/fTs2bOzwsWorqLiqzlodhthg4egqICvBsNVjGHUzkGlaqiaFXtKMrakZNy5uyjbuZ2IE09DDQ3rtFi7gmffLirWLwXAOWgS9sS0Lo6oMV3XMU2TwsLCoJZPTExs1dxi7WnHqjkYuq/ d7 poakx9Xdi9 /fx7aVX6ApB JTNSu9x5zW6bG2N8NTg2q1gfrLT/ANU fH7XOp9laSmTiM1Nh KIoMuyCEEKJj7dmzh7i4ONxuN6ZpoihKi1XghuqKVA6Hg927d3dgpEJ0H51eCW4uCa573DTB7/OhaRpOp7O X4PL5aK4uJjY2NgOj9WorqLss4 wx8Vjj43GKC3G1L0YuoFe48bQDUBBURUsDjuqRUPRbIQkp ApLqHss4 IOv2cX3wi7CvbR/naRZjuCqwxPYgYegyqzQFAxbolhCVEoNhCcK1bQnw3TYITEhKCWt40zS5Lgg3dR3hsav0H1rrsYnqmxuDxeACIiowid28VQzJi62OtLN7TJbG2F8PrpnztAvTyQlA0wgdMICSlb1eHdUR2F23CZoO qX3JKdzOrv3rGNRzCtHhSV0dmhBCiF8xj8eDqqqtTn4PpqoqXq 3HSMTovvqtDJFXSXYMIwmf3RdR1VVNE0lxOFg3ryvmDtvHj/9/DMlJSUAZGdnd3icpu6ndO4crFExWEJD8eXvRa qpmpfGVWFZRjRyVj6DsHSbwjE9aCqqIKqwjJ8ZS58 XuxhIZhjYqhdO4cTD34gcC6G9M0qFizgMi0RGIGZ2HRvJSu ALDF/jjqNdUoig6mt2OXl3ZxdEeqi0JbVclwQEm7qqywE9NDZu3bGHp0qUsXbqUrdu24a6pqX8egmvi1F0Zfi9lP84lLC6amGEjierXh4qNyzC8TXeV CXw6V6yC9aSlpiExeKhf2oqfXuksHbXt10dmhBCiF85r9eL1WqtT4Lb mO1WpvttniAScWmebwz 0f2N/V1xCxmzaf/48MfStv520oL z3squ0Zk5ttc97g862Vv/BvYx3FQ 6iN/nwZ1e3Pz dlgTXJcANK8INfwzDqH8DxsfFkZmZSWZmJhnpGfTs2YuYmJgg3phHrmrtGhRFxeZ04t /H8PnR3U4sUbGYFhshI8ZT2jWYEIHDsI5YTJxv7kEx/AxVJZW4q2qwb9/PzanE0VRqFq3tsPj7SiGuxpUUFQNo6YCR2ICtlCNsu /xNT9mAZgGIGfIPuddKa6SnBBQUGTP029BrsyCTZNE9MI/AzuGcawtPBGP4N7htU/H2w/n 7INHTKV39FWGIs1vAw9Ip9oKpoFg292tXV4bXZzoKfSI6JwWox8Rvl6GYNbp X8JCorg5NCCHEr1zduCGqqjb6MQyD4uJicnJy2LJlC1u3biUnJ4fi4mIMwzhkeU3TWhxRGrOM5W /yCfbvYQ3VXTWC1k5ezZLsqvaNwlqab H044xebe x9P//Y7d1W2vuP i Dfx2g0Xcu1LawmujYCCb 8q3nrmNVZXde/vq92mOTQEqsVWq5WQEAeqqqLrNhRFwWK1EhUZyY4dHTtwkeHxULF PRE9U/GVlKB7vHi9PkJRscXG4fd4Kfl6HrGnnIai1t4/UBQc/QegRUdT9OUXhJkKZnEx9phYXOvWEjpwEKr9lzdqtBYShuEz0T0eMA308iIciQmYeXspW/U1mCZmbaJJC38vu0JzzaHXrP0J0zApKMw/8EdfDXxw2EPsbNq8Ca3 A0FD1VSsFgs9eqR2aLyB90bjE1noDUVBRW3wwaapGqpHRY3o02Wxtplp4PppPvZIBzZnBL7yfFRLCHpVFYYfLM6uHQW rWq8leSVbGdMv/7oRjkKGmAnpyCHUb1P6erwhBBC/MrVDW7V8Du2y UiPz fmJgY vXrh9PpxDRNqqqqKCwsZOfOnaSkpBAREVG/Tl2T6sMxS79n8QY7o28bjqPDjqj77LdxEEUsnPU5peNu4uJhYSiAWbaWD154mc9W5uDSYuk74WyuvnoG/Z0KmGVs HQW7371PRv3uDDDUxg45Xx d8VxpB2UGtRkz GJ /6L 8JXePCUaJq7Cmbpl/z18mf56cBQMmg9L DJ/1xO3wbDqwS9vZpcln30Lp9 9xPbC1z4LU4S0gYy6uSLmXliJg41lNgeqaTGhQcqp2YFy579E/9aVIjL7QeLnbDoJDIHTeL0i85jYg87mWdfyfSv/8asOWcy4oJenVdxbaVuMzAWgN/vx2KxYLfbsFot6LqOoij1d7eOpJ9DMGp27UJzhILfj1FTQ7XHh6lZqKysJowiHDExuPL3U7pkCTHHHNNoXVtCIhFjx1Px4yrCAM0RihYaTs2uXYT169ehcXcIRSFyxHGUr5pHeFoyqmbBX15EaFIilbl5mHogCaYVIxB2puaqum63m0kTp7RqW7tzO2GQiCbeG16vr3vG2hamiWvtIix2g5CYRPxlhShWO7rXT0V2LhGjT0b5hY6qvm3vKnolxKOoPnTdi0WLZm/RPuIiUqUSLIQQolM07A9cXl5OQUEBQ4YMwWKx4PV6cblc9d pe/XqRXh4ONnZ2URGRjbaxuGZlKxYzIaQ0dw5rFNT4C7ab2NG7jd8sdbJtIcnEKkARh6fPfoA71Qey/X3/Z50/yY fu6//O3JEJ699wTiseLzaPQ//XrOTrZTsX0 b816hsfD0/m/SzLRAKMym6Wz32TWx9 T51EZ1kIMZk01NWpvzrv/DxwbW5teWqNIrU2AW7M9s2odr911Px/sjWfCKb/hpoEJ2GpKyM/ZyK5qExuAmsaMu59gRv1aOuX7CqnqeyEPXz4Ci7eKsvyNzP/gAx75axkP/OdGRjgGM PkdG6eN49N5/yOQd306123qgRDYD5hTdNQFAWbzVa/jt/v7/Bkq3LbNqw2O3plNT6fjt9USDnnXPI//piayhoclBIeH0vpnlwq1q/HOXhwo/XD ven7Icf8ft0qKrGYrVStX17t0qCTUOnctNKavZswfR5A8kXHOhmWneOG/xetiWbyMwU8HrwlRcR1iMJ06/XJsFm4KebMYzmR4du7ajRfp v5QWPUHPvje4Ya1tUbFqBYlThSO6Jv6wA0 8FQ6F8Rw6G36Bk8ezAgnWnQNXQQp3YE3oSmj4QS0T3rBJX1JRQUllAWnJvvP4SFDR8fsgrKmFC/9bdwBBCCCHaqq4S7Pf7yc/PZ8iQIQD1g2yqtS0Y65pI5 bmMvig77F1yzTLLGL54o04Rt/F0Lpc1JvH4tdf4M0F68ivsZPYPxNbpYm14Xr fax692XeXriGnGKDqD4TOPeaazi1r4UfnrqCB3fM4Jn/u4j0QKmR4i/u5qrXorj9f7cz0dHEfs0ads57iefeW8LW/R4skSmMu/w bpueGKh4thiTQd6Xj/DArNUUuHxYIlIZevKV3HTxaGKbPQUG Su/Z1f0WK7pF9iSkfsdX29ycOzfrmH6EBvQm5uu3MKVj3zJd/nHc25KGMMvuJ7hdZsY2oeaNUt5LnsXHjIJxaDg6xd5 Yc4Tv/Ljex84nnKDn8FMKsqqFLiSc/qQ Yh42ZnseNr75f3yY24uLHnuIi/o2vLlwaoNN5vDW72/h29GP89zl/agrNisRqQwYMCCQKA8dxciwPC5 fBObCg1GpKv0mDCBtLe YsX2Kxg0oHtmwd2qElzH7z90QKmg ikcIW9ZOSFRkRg1VXh9Oo7M3mh2O4mnnUbeRx9DRRUhJkTEx1L642q0iAhCe/WqX19RVULS0vFkb0d1u9HCI6gqbenl3LkqN63EV7yTyIwUVIsWuB4NfgLXx6yt8AKmUdv02Yfh84HPi9 vExIVillT2WQFs7toqjn0rt3ZrR41uqnXY3trqjl03ePdLdbWqt65BsO1F2dmb3xlBZieakzTRLVpRPZODSS ta870zBRqB1Az vHV5pNcfZ6QtKyiBw2GTq4NUhrbdqznLSEWAyjGl33Y7VEsbtwH6lx/Qmx/bJHhxdCCPHL0LA5dElJCYmJibXdCvUmE1ur1UpWVhZWqxWv14vP58Nut7fY6tLcv5wlm8MYe 5QQgDMKla/dC9PfBvG8ZfexnW9LBRt/Jp3t9Ag4XSz4bV7eXhRAuddcw83xFWw t3nePHvL5P4/O/JGj0E26K1rC/ LenxClDNhp 3oWVdx CQpvdr7PqYJ59bSdzFf axUTGYZXlUxcUEEuCgYlKIGngyV9x2DrFhJsVrPuSFN57g5cyXuW1SWDNNh91s37wLtc9ZZNRmT0Z1JVWE4gw/0A45JD2THqwgJ1eHlAbn3qgm/6fPWLA1nJFXD6pt0q2SctbDvHq2guJfxVOHucb118DlosKi4i0posIai9PWMNpWbM zhnkL8omYcg1n9z2C6rrpo2rfVr5euBE9YRKDkwLHrCb3p5/zLbZuLcUcEH/IOX3//fd59dVXD7vpiymIsvvrjtsbWgUyvBrZm8 2BHsm6wPNVuiIrE8PnRUQitnY7J6nSSfNqp5H3yOYpZhQ2FiLgYCuZ/S oZM7DFHqhSWWKice9UMXx NMBb4 nQmFurZs9WIjOSQPege/2BJNZoIhFu4v KCaZuYPqrA78bZu3gWF19VB3L5kSnA7VNQ7I9bWqty2hqi vfCX7cOoqcTUDRQl8OERaIXQ1I0YUFCwh1qxhUZTlbsJFyoRwyd1evy79m8EDHrFZTWa93d/ R78ejVR4Sl4/SWoio0aj49iVyVTsoZ0epxCCCGOXnXNoV0uF3369KkfcBYC/YPr5v/t1Ssw2CwEik5er5fdu3fTv3//FppDmxQuX8KW8LGcPyTQodWsWMFnC4rpd8lD3HxGUiDRGRxO9jer2Fi3VsVyPv6ymJE3PM5FkyNQgN437OPHq99i8YbrGTV0LIO1f7Pqp3JOOzEKxb2eVet0Blw2HKfS9H4NVxkuwhk5ZCgDeocAfQ5EGURMoBCWPorxtb/17R1OzuLf883mXPRJA5pOjoxiCvcbRA2KC1Q/Aa1nFgMcn7H4s8VMv2EqqXYvxQXFuE0/Pv B73SVC/7OzCdXUGNaSJp2K3 alnAgKVSUZvvrNsXrVXCGbuaVmy/nWSOctDEzuPK63zI6XmvV9oziXPZUa2QM6EtIK/Zfx7f0Mc6Z8RiYJoZpooSkM Mvv2FI3cbUOBLj4MfC/ejEH3JOzz//fIBmE GOToChGzaHbmn9jmSYYPh1DN3EMEzMBpVne1wc8dOmUrhwEVFmJVZnOM7IcHI/m0Ov887GGh7eYDsmpl67re5WJDVNTN0Avx44viaSXUyjNjEGpdHjQG0CU58Y1yXQ3ZBpmuzbt6/Jx5trYpyYmHjIYx1dXQ2cSqPZSnB3irVNTBPT58X01YCuB15/SoPnGt5ogcBrqv45H4qiEh4fgWvHOiyRMYRmDOy00HcU/My 8m1YNI38kp2MyJyO3RqKicmWvStIjYvAq1egGzqaJYTcfUX0Th6JRbO1vHEhhBCiHTSsBLvd7vruhHVyc3MZMmQIpmmyYcMGoqIC41WoqkpYWBhut7t AM5mE2GzgOWLtxI 9kJqc1H0vGxy/fFMzDq00ldHz9tJjruGwmcu5axn6jeG7lewl1RDxGimDFP5z/erqTjhOOwbvucn7yAuGVdX2T10v5aBp3LesOW8fPcNbDv2ZE497SQm9o5ECzIm8FGw4h1e/WAJm/aU4LE6sVbraAMOM/6x6cHjNbHa7fXbVcInctWfzuSx/3uKa89/AgWwhzrwGZEMiTxw0zxs3HX886mzKdy nNlvPsXtT1t56taJRLehcVvohJt5YcLNoFexd8NC3v7Pyzz0kJWn/vkb0rWW1z9wPIHukIp6cBA6O9 5g/u/H87dT1xCv2ZitIy4kn/ bhRWU8ddnsfGBe/x1sO3w71Pcd2IMBTFht1 oDl U5pLhDsjAYZObg5d9xOsN5ZMxeuvqv/dqoZzLOs6IjwAtBAHutcHKODXcRc3bsrszMzAU1pG2c9riXJVYHWG4wixk/v5XNLPPQvVaqGmqCSQYNqs6F4fir0t91c6TkiPvlTv3YEjIQrVagkkXiYoZqDSrtRWJJXaym gUmyg6DqG14tqmoCCotkwve4DleRuyDRN4uPjGz22OzfnsE2Mm7rR0tH9bOuqoc31Ce5OsbZFWO9hVO1aS1jPRAyfN/Ba001Ue0jgw7auU7pZ17888K/p94PfB6YfxTAJjwul/MfvsCX0wBIW0cJej1xJRT65RRvpl5qIRVMoKq9k2ebZDEs/jmqvC4sGoSFWvP4yNDUEV1U1bp9Bz9juMwaAEEKIX7 GSXDDeX8bPl XjNQtW6euYtxSEmzkL2Px9gjGXTK4vhJaWxU5/PdA0wQ1mmNveZAL jRsmq3iiAlMKTp66gjUZxezqnwCUUtW4hlyOeNrM8Qm92tN54z7X2T0z/P5/OPZPP2Hj/j0sr/z0AV9UYOIydj1EY889inqSddy67V9iVby OLJx1jR/FGAYsduU/B5PA2mWVKIHXMVj79 CeX7S/HYnHjm38tN78QwoEFGqoTFk943nvS g8hyFHL5U5 w LIJnBF/BF28tDBShs7gxsu3sOqRZazcez7pPYMfh1mNSSHJbrBpxy58DKXhrXu/20VZeQ3 wFf Jimh8fRKS6tdL5P g5Mo3/wn5sxfx1UjxmMzvXg8YLcfvihwcCLcWQkwdOPm0CYmVTVu7rjoX3j0Gjy av7z4f0dGqMlKhpPeQk2RcGCSfnOHJKOmdioH2LcqBF4S12U5 wisrwCR3g43hove bNp cp03Ht3IUTMBUFr9uLNSq6Q2NuLeeg8VSY4MrZguF1NxgAq0FSddAgWYqqEJkSXTs0Oqj2EFyFLsLDlEDS0j1z4Hbj6/BKcF0riSNvV97RsbZFWN/h6DVVVObuICw5FsPnCkwroJuU796H4a897gavO0VTcThDCAm3gscLfh3NYsXhUClbPp 448/q8P7B63MX0yshCtN04/a6iQoPx2bVWJMzHxPITIrB66vEME00xUp SQn9U8Y3ajIthBBCdIa6JNjhcFBTU0NY2IFxKQYOHMjGjYHGwIMGDWqUBNctW5cEN81g79Il7Iwcz8ysA0mNltqHDNunrPkpF//AjCaTCq1HBr2sn5K9Vyd5WlqTy0SMnc54MsmD fqJU6o6 vHX25mf0CoDhIGTGDa0Ycz T/3sJfPpvHxnP6MiyImLw529hlDOKmi49nuFMBM5QeLU0 rMaQEK9Str8IHwclUIqdyIQk/AXf8Njs7cROu5 xzWxPURQUdPR2 rrW5layIcOYOj6SJYve46szspiReoQpob aao JZrUG8gWjiH1FEJcYT0sF6vPPPx vN1CF76wEGLqgEtyaJNjjNfHqFbjc32NRB Dxdmy2FdGvN8UrSrBpKpppgl nZMNmYgY3bn6ZPG0yOz8up7y0hAhXBc6wMEr2F7H9w89ANwLrKipu3SS6X 8Ojbm1FFUjYugkIoa23LfSW1RAycJPcCaGoSmBypwS4qBynwtPhRtniL22X3D3zIKbe60FO JyXXNjvb3 UjXD5MhHh 6sWNsqYshEylbVUFOwl9C4SIxKF6oVIlJiceWXEzNlBra45PrlDU8N 7/5GLXajV1TAiOR6x5C7RbKSvOp3LyG8IHDD7PHIxceEkWxy0VyTDimqeLxlWO3OMhIiqbK7caimfh0NxY1hNLKSjQlhMSotA6NSQghhDhYw0pwQkICxcXFOJ3O uedTidTp04FAlNFNuw6VVJSQlxc3OErwUYeS5fsJGr8FTTMRZXwCZx3ek/ufP8hHuUiThmcgNW9kbyaBrXSiAmcdeJ73PPBozyuXcgJWfFY3fvZXZHM9OMGEqoAjhGceEwkd816GS3yeO4dUzs4VTP7NfJX8sVag/SMeEL8 1m7uxKckTiV4GKypqaTwqfMfWcBscekEakVU1jd0ndZB3369cKYu5Vs/1SyLAAmVfuy2VOwj5z1S/nys0UUpF7IvTOHBQa 8m5h7rubsPdPJ85hUrHnJ a8/T0MuIqxiS3fyDddy3j6lqfZPO4unr52OA4jn6UfLKYytQ/JTpXqvJ/54p3FeHtfwriUVt6AV8IYN/Napm54ghfuuIOdZ57C2D7xhJgVbM6parG ZZbvZuOGDVj8biqKclg9bzbzSlOYMS0LC2AUbmVbRSyD sYE1Ue5M5PfOt2uT/Czc6ZR460AINTuoMZXittbic1Sid v8OcXetU F8kDl7dv02hnRi/2LFqOI8SChkqY30ve0pXY42IJSzrQJFXRNNJmnMjWdz6h0l1FmFFFRIidktJynIYPU9PwGlDt1UnL6HWYPXZjpknp0rk44xxYFBOzugbFZqeyqAqcyZiunaAbgf7D3bBPsKZZWP3TD00 F yIy511XKZZNzBW20eH7o7XoBFFIWr0cZQs 5Lq/UWERoVhVFag2R2Ex4VRuuRLEk6/rH6uYNXuIGbSiRTNfQ9brD3QNF/XMf064WEWyjf82OFJ8PCM49mwewk5hQX0iA1DUcDrr0JVrESEOvD6qwMtuBWNfWWVDM Y3qHxCCGEEE1RFAWLxYKiKKSmprJixQqSk5MbVYPdbnf9/y2WwGdtVVUVRUVFjBs3DqB itKDGblLWZITw4TfDWw89RE2 l/yIH93vsobX7zIg29XYticxKYMZmLPulGWQxl61YPcG/kqb371Ag /WQ1h8aRPvoKJx0Fo7XayTj6RjC/ewjf9VIbaD79ff1k2yz6czcv5Ffgs4ST1GcfvbjmHTC24mNTe5/Ln60t4/v0Xuf TKgyrA2d0Kv2Sww TsKmkjBtPz7fms2L7FWQNsAB 1r1 J4 tDCEpI4vRlz7EX08cQlxtdmXWVLJ/x0IWztnN/iqDkOhUBo6/lgcvOZUeweasDRtcGjWU7fqBTz95l3yXH2tEMv3GXM59M88krTX9gWspcVO49clYBr77Pl99 RILi6sxLGFExacwYlx/YpqMUSMyPoGw797jr7e/BZqN0Mh4evabxNUPns9pQxyAQcGK5eTEjOXqPt1zeiRotqX3ISbW1NQsPZIdzZs3j9GjR7c4cM9D74/lxgsvxWqxYNE0FBTK3esJ0frh9fvxeL24vV7e/fJTnr4x50hCalLBqp8p XkDEZqC6fHgNQ0qFSspk8cQN6g/SoOmIp5yF1ve QSn7sVu0QKDaZmg2O24dJOYkUNIGjW0XeLKz88nOTm55QXbiV5VQfGXs4hMCIfqGhSblapKH35bDHEnnEXerH TEG1BTelJwfpsUi//wxHvszOOcdF3Cxkzelyr1ln1w/dMPWZaB0UEG5Z8TEhYBAe/HfdUKF0aa0dcD1P3U/ztp1iMCkLDbRjV1aiOUMryy4g69hxssY0H 6pY/wM161cQGW1H8XoDnwSaxr4iL6kzf9 usTUnt2gz2wtWkxztwGYFXXdDYCInLGoIZVV FKIZkXlCp8QjhBDi12316tWMHTs26OUff/xxpkyZUt /1 VysX79eoYOHdooEW6ooqKC9evXM2TIEJxOZ2DqQlVl8eLF3H777Q2WNMh 8/fcMn8oD794DYM6rw1pF 33MMz9fHnvDcxy/oHnbptMRPeatbH78KzjhRvvZeMJT/PUb9LozE5iK1euZNKkSZOAZS0t2 2aQ/s8UOV2UePbEUiCFQXDMCjVf8Dr8 H2 gixZuL2dEzlK2HEEIq37KSiqhqHZkP1 wjTdfKXrCJv WoiMnpij47ENAPzCvsNqMKC4jMwFQXFYqXaZ2CGhZE4fFCHxNgZVEcYWEIwvD5Uq5Uqlxev5iT uNMD1TrTDFSCje47T3Bzmhs1uqFg5 ZtD4qmUVNV3sQz0d0u1iOlaBZijplB0TcfoZTX4HA60D1edJ/Z5GBXzkGjqMnNpqaikDC7holJTaUPe2KPDo 1bhyD5Kg 2LRQNu5ZQozTSliIDb/uQUHBD5RWeBnTZxQ n69 MJKW5loUQggh2ktdFVjTAuXAuLg4hgwZwpo1a0hISKivCiuKQkVFBYWFhRQUFDB8 HBiYmIaFajqtlFPz2HJ0lziJtxA/85MRLtqv4ejxHP8Jafx2Z2v8/a6kVwzNLRV0xsdHXxkz36Fr/zHcudpvTo1AW6tbjcwlttjUFFdhsWSgGmomEBFTQ4OW09U/FhVP1XVZR3XP1hVSDt1Glve/wKf38Sh2sD049BNdN1H1eadVKgKCgqKYRCmgIqCT9FAteD2G3g0hYGnTQskxR0TZYdTVJWoSSdTsuRrzKpyrMlpxE06AdUWaKOiOsLxeStR9 1DczR9l7G7amrU6KaW6SxZE85o8vFF3y3sdrG2B9VqI27amRQv/pKqnDwUi43IsdNQQ5qYrF1RiJ16Cvu/mo27pAgAMyzq/9m76/CojraBw7 zvvEQI0ACBIJrcS9QoFCktKVuVN 3Xtq X72lXuruCjWgOLQUbXF3CxI0QkLcV b7I9IkJNkNhAh57uvKBbvHZs/MmZnnzBGC 1 YUdfCWzYK66rCf73NgXQOv4zdJ/8mJ8 Gn6cRUCSn5xLs2xQ9Zmw2W1HwW/pfCYiFEEJcKCZT/g2zhQFs4a1Ul112GQcPHmT//v1kZWUB4OnpSUhICMOHD0cphd1uL1rO4XBgtZZsix3Rq1lzKog D7aqvqChBrfriqn1dTw8UXHA6KjppNRSDnRBXbjuwfF0d/WwsRpWrSPBDofDdYddWfjsp6UAeFjNXDemK5m52eTZkvht7nbyCs5WeVl9qzR9hRWBzWbDadATNnowJxavJi87D4vSF5zJUOhR6Itu3dTjQMOBhlNp5DicYDURPqI/Dr2OnJwcjEZj0Rm6usYUFErD8beWOc2/zxCS1yyDdPDvN7SaUybqOp3FStCwq3BkZ6Ezm9F05d/MovfwImTcTdjOnAa5XDRlAAAgAElEQVSlMAYEl7gtoSoVBr7Fg DC/xs0Cx0bD FA3FoSUjPw9oCMHAeRwW1xOBxFDyUpfLpm4TEvo8JCCCEuJIvFgtPpLAqGgaLXJbVr146OHTsWtUNKKRwOBzabDaVUiZFfm81WYh0A pa38vncsvuCF1JNbdc1K63HTqR1TSej1rLQdMht1IXHhFb7SLArL9 2omj Rz/rTUrGGXJsWWTpksnMcvD76zEXOqkAGD2shI0aRMLuKFL3RaNDw DU0KMrWZHgxK5TOFH4tY0gsH0kRhfvxLoYWMMjsIZH1HQyzkldGjmtS2k9F3qrh1vzaZqGKTDE9YxVoHDktvj7FoGC4NZIu0aDOJq4ndOpR2kW0BmDzlRixLdwfhkBFkIIUR0aNWpEamoqPj4 Z/W1C0/mllb6smedTkdcXByNGjW6oGkVoraoliDYbrdjMBjYtm2b28sopcjJVSSlJheM0iaTm6eK1lXVNE3DaDSi1 ux2Ww4HA4MBgNNenQiuH0kqcdiSY0 SU5KBo48GwB6swmTry BEU3wDW IycOKTqdDr9ej1 sxGo0VvHNN1ISKnhpd0TI1oS6l9WJRfBS3cGS3cCS48ISEUorI0B5EhvYomrfw39KXQMvxL4QQ4kK75JJLmDNnDiaTiaCgIAwGAwaDwWUb5HQ6sdvt2O124uPjOX78OOPHj6 mVAtRs6qlx6xpGr17967UqJZSii9XmJg59993pHpavS/4yIpOp8NsNpdIh9PLC7/AANQl7Ut0houP/FT4fjVRa/TvN6Cmk C2upTWi03pjkPxALj4v8UD4OL/CiGEENWlYcOGjB8/nq1bt7JlyxZyc3PJy8vD4aj4vlW9Xo/JZMJsNhetIySkeq66EqKmVUsQrNfr8ff3r/RyC947WvWJqaTCp 2d9bQ8IUS9IUGuEEKI2iwkJISRI0fWdDKEqDPkWj0hhBBCCCGEEPWGBMFCCCGEEEIIIeoNCYKFEEIIIYQQQtQbEgQLIYQQQgghhKg3JAiuI0JDQ2s6CRdcffiNdYnkhxBCCFH9dDodNputppMhRJ2Sl5dXqQcZSxAshBBCCCFELeHt7U1iYmJNJ0OIOiUxMREvLy 355cgWAghhBBCiFoiODiYuLg4YmJiyMvLq nkCFGr5eXlERMTQ3x8fKXec10t7wkWQgghhBBCuObp6UnTpk1JSEggNjYWh8NR00kSotbS6/V4eXkRHh6Oh4eH28tJECyEEEIIIUQtodPp8Pb2xmQy4XA4UErVdJKEqLU0TUOv12MymdDp3L/IWYJgIYQQQgghahFN07BYLDWdDCEuWnJPsBBCCCGEEEKIekOCYCGEEEIIIYQQ9YYEwUIIIYQQQggh6o3zuid43G/j3Jpv7nVzS3y2Wq1uLZednV3i81MH/3IvYUIIIUQd9Xrk8BKf582bV0MpEUIIIS68sWPHlvjsbsxXur2sDHkwlhBCCFHLjRvnf9Z3c cmVziPTJfpMl2my3SZXhem1wS5HFoIIYSo5WpDh0EIIYS4WGhuztc3Ozt7Tekv5XJoIYQQomrJ5dBCCCHqk6q8HNpqtfYD1rpatkovh15822IARvwwolLLFb4EXNPcjcnzvdHKvWBaiPrGbB5W00kQQrjp0V0S5AohhKhfCi RdudKpzdaWTGbh1VpeymXQwshhBBCCCGEqDckCBZCCCFquXHj/Mt8OJYQQgghKk CYCGEEEIIIYQQ9Ya8IkkIIYQQQgghRLWp6bceyEiwEEIIIYQQQoh6Q0aChRBCiFqups YCyGEEBcTGQkWQgghhBBCCFFvSBAshBBCCCGEEKLa1PRbDyQIFkIIIYQQQghRb0gQLIQQQtRyNX3GXAghhLiYSBAshBBCCCGEEKLekKdDCyGEEEIIIYSoNjX91gMZCRZCCCGEEEIIUW/ISLAQQghRy9X0GXMhhBDiYiIjwUIIIYQQQggh6g0JgoWo1RTJ6//g9Y82ccJZxmTnGVZ 8i3vLk6irMnns92ktV/zyvt/cryyK3bGsPzDp3nrj7gqTpMQQgjhJpXIxp8/4KsVsfltUenPdYlKZvcfvzBvewqqptMiRBWp6bceSBAsRG2mkpn3 ud8stWGX1lHqyOORR/NYvaurKptGFU8c16ZxIdbcvCvbC3hiGbB8xc2eqNNZCCCFqhjONw5s3ceB0Tn5bVPrzhaayOR21lV0ns89/e87TbF20kA3HqritF6IekyBYiFpMxa9n5hozI67uind1bjduPtNXWRk5YeiF364znlUf/IeRnZvgazHjHdqBEQ9NZU/Whd6wEHVHTZ8xF0JUkuMw8999l nb02o6JUKIMkgQLEStpYid/w9rPXpw9aXWatyuk5i501ntOZIJQ6oh9NbM5GYb6f3AR8xcNI vJ3Xi5Nd3ceOb27Ff K0LIYQQQoh6Rp4OLURt5Uxk/u978Lr8WQZ5FXyXc5KZL37Gqz/t5HCGhWY9IrCkKMzFl7PFs/D1a3nlpxXsOuUguNuVPPHee/ynu5FFdzTnqm33s3nz83TUAyhiPh9Gi2dC PnoT4z3BpynmDtjLd6jpjPYC1DpbP96Eg8TubjmdiCopkzOsLmHpbs/yzaDlRTH/2ESZP/ZtD6R4079UZS3LxNDmI uJaxr2whOgzORgD2zD4rjf57MWRNNYDmh XPfkRlxXOPvgSMpbP4oEde8iiCz4XeDcLIYSoAfbdfPPAGxwd/Q4vjQ5BA9TpRbw4aT7hT33Ene1S2fDDZ8zadoLTZ9LJxUKDZpcw6raJjIz0RMNJ7NL3eGv6Lk5n5KH3bkz7ITdx14QuNHB3iMeZzK65P/Lr0m0cS9Xwa9qVy264hbEd/P8dJXKmsGfBVH75axtHU xYGrRg5ANPc3UrvRvbtxM19SGunwpgpNfD3zCprxkcCWydNY1Zq/dwPMmJb0QPxtx2G8MiPNAAbLGs /V7Zq7aR1y2ieCWTTFmgrEq978QNaym33ogQbAQtZTz5Bp 3 jJyEe74AmgMln6v2e54zcPbnrhSd5payBm7WLe3FQ84Mxh7fPPcu2Mdvzvvdl83CSJJa89wCPjH6fZnq/of/kgrL s4J YZ kYpgPSWLVsM4Z HzKgINB2npjDjPW XPH4YDwBx 73mPjgQhq/8CMrL2 EM/4AqWGh R0Elcpfk0Zxy83PryND5oZ TUmu94bUPxNOkI6XsPb0x7jMZ ilPL3 aR527liS4H elqv/wGv5AjjcNLP2bqZj Gv9UfL4QQQtRLKpMT /aTGnYdD94dgTEnjq3zfmHae9No9M69dLFq La6jBsfHEMDT0XS7vl8/9vHTGv2AQ/28izZtpQpj0PTX2fKnxr9rn AG8PgxD /8euUN7G98DITWhiBPA7//gZvLnTQ65p7uC7CC1tKOp7B d1n19s30GzM49w/KAANDY9AE5DL/l/e4P21gYy99XHuCMhg5 xv eHtqQS/cy9dLFns/PF1Pl7twcDrHuD2JgaS9q9g9iElQbAQVUiCYCFqJcXxef wybc3TwzIDydV0lozmR7s9/xSf3FQSh/b3YOXUj6wqXSl7LB98kMvyTH3n mkA0oOsnx/gz8iVmrP6YywePZqDxPhYtSeS O4LRMv9h0d92 rw8lAYagJNjc2awwW80Tw7yAMCZeJpE5c wQYPp3dUTuOTfVJ6Zy8dTT9Hzpb/44sGI/DQN9GfH94tYUzSXhm/HEYzrmP pe1d/dk/vxvfr92O/undRo548bTzht88lw2kk4qYf OHmpnK/hhAFavqMuRA1xdq4HZ07tEBPe9o1SGDnc6vYFu2gSzs9HuGd6V4wX0QzT46ve5K/D8bg7BWJ3sV6VeZm5v8VQ/j4N7nn8sbogPZtGpJ9/EnmL9jCFQ/3xiNzC/P/OEnY Df5z jGZ63Tne2b/EIJCwspCspVxiYWLk2i050vcnVvbzSg Z2J7Hh4Juv230Hnlpv5858kWl77DPdcXrBcW0 O/b2NA e7M4UQRSQIFqI2csYy9/co/EfdRP/8WBT7oWj25wUxrk9wucGh/eBhdmdmcezOJljvKloZ9jwd1tg0CBzJhMF6Hpi3mDMTb8Fj1TyWZPdn8thG et0RjN7xiYajH6WgQXbNfa9l/8Nnc3jwzuy YZ7 O99dzK axAGwH5wJ/vywhjfN7yCgDWXI3Nf4ckpM1l3IJYscwPM6XYMfXJKzOU75gPWrn Uo1vn8t6LExl0p4n1319FQ9en84UQQtQDuqCGBGnppGc4ASfxm2fx89wNHIxNJtfghTHHia6Vza11OWOiOZYbQPd2Df9tv/ShtGvbgJnbjhDr6E2zmCMcLZjn7KDadk7bd8Ye5XhuNgmf/5dbvij6Foddhyk5G0fsMU7ZA nZOtCN0WwhxLmSIFiIWshxZA2/b/Phiuc6UvRILE0DFMpZwQsSlAJdADd u4KnuhU/vHV4hTZA03SMun4Y v/MYFHCeIJnLiTr0tcYWxBpOg7PZsaWQMa8OPDf7Zo78uDCA4xc iOfvPsed/R4mw9f/pO/nuqOwY00OXa/w3U3fIT rvf5/oPuhGhRfHH7DcwtNZ/ON5yO3cPp2H0A/byiaXbHh8x4 UoeDJfxYCGEuOhoOnQ6cNjtKHAr4NP0evQonAqcJxbw/gd/ohtyG/dNbIEvsSz99AM2uZ0A5fp1Q8pZ7jxubb sH6UUaP70/TXNm8ePumw LvhXaqsF11 4cIUScVvvGgpq50kt6lELWOk8Nz/mFnYB u7msq tYQGUkn62lWLj1OXjlLGlo2p605hR0HHUS0aUObor9WNPHVAxoBo29jrMdKpv34I9MW2Bl525UEawAODs2awfagsUzobym5Ys2LlsPu470/tvHnI8Fs/Pgb1uaBoXU3OluPs3zJvnLTlLNrM7ud/fnPi7cxtHsHOnTtTqSLp5ZomoambNjcO6EvhBCirtF88PVRJMbEcy5Vve34EU6oNgybMIgOEWGENY godfZUadSqszPukYRNDWdYd/eeIriTUcs /YnYW4aQagedKFNaWI8w769cTgqu33NhMkEWZlZFI9n89eZyrFYJyGNG9O46C UAA9dQboS2b3zlLwhQYgLSEaChahtHCeZPesIwWPuok xWFTz78Ok/zZlxNsvcQu3cOeAYMwZeziY8W8DrwX048Hbf2XsW9dxk EZJvYLx5x5gj1JLbj9lj74aID3MO64LojLXngCY CtzBlV8HAqRxS/z9hByLg36Vdsu47DC/hipZMOncLwzDvByr3J0CCQBjrQ/MfxxAPtGPLG1VzPC9wzMBxzxlqiiqXJ3KYjkeojvnplKo2v60CQ4RRHU4t1SnI28NVr6/Do2ZEm3k6SDizls5fnQ5 3GN1MztMJATV/xlyIKqcLpVv3Jsya9zNfNbMxsKkXnD5Ousvh2XyGxuGEqj9YNmsVDfqG4aNLIqH4V1Xvh4KRL2rGdHbChdG5b6HNqNMSMa8dLsD/jKci0DwhTH//6NOScbM qOS/AA8O7BFUPm8Nrv7/KJuoqBrfzRZyaQG9ybri63H0rzcCN/rJnD4pbDCVcJpPl0p0 rHowaMofX57/PR/rxXNo6EGPuGU5khHDpgFZYPbsz9vImvDT3HT7gGoa2C8SYc4DYkncQCSHOkwTBQtQyjv2rmb2nAWOmtCv56iPM9HjuNeY1 JbJX37Oda n47B407hlR8a18Si4rMODQa /wZyQBUz 7hGumZwGvmF0uuYNrrq5IAjGQr 776DTZ5PJu/1eBhfcvY9zszd4cy7t0 JbZri9/JrLfe54nDZ8g1 tO82xje/fZxuhgArPSa/Cd/BDzF8589ylUvJ OwNKBJ5EDGt/VFB2hdn DHj2N46M1HGfthKg6TFw0atqZnC//8V2Kkp3Bi209M 3QPJ1KdeDZsTZ xH7B48n9o5erJJkIIIeooPU3HPcx/M75lxqyPWZvpxOjpT1DLDjT3dX0CVN9sDPffkcR3c39gyh9ZOA0WvPxCaRnimT DFkT/q0ez5eulTFvenc43RZb63IrIa5/kCdNUfp37EavSwLdpV678362MbVl4FZaVdjc9wxNe05i 9Bvenp6LwacRvW7uQLf rrbvTe8b72Tfp78w/d1NOKwN6XJtS3q3akL7m5/hce fmLnyB96dmQ0eAYT3upGeA8CKiZYTnuYpr5 ZvuQH3pmVidPoRUDDtvRo7CH3CQtRRdw9lvpmZ2evKf3luN/Glfi8 LbFAIz4YUSJ7 deV/LuP6vVWuJz4aUpmlYyOdnZ2SU P3XwrxKf32hVcj1C1H1Odr1yH/2ndWHRzv/Qz R6ibKYzcMquYSDnZO70fOHwSzZ/x4DznG7QojKe3TXvBKfX48cXuLzvHnzZCRYCCHERWvs2LElPpcV85nNw1y2lwBWq7UfsNbVNuVaQyFqE3s0s ecoPHYAfSozkDUvouZvnyZXX0EsCYCGEEEIIcRGTy6GFqEXsu1Yx 2AQYz9uTbXGwDtn8ntUGFd 3rNatyuEcI MAAshhBBVR4JgIWoRQ9fb2ZZ6e/Vv95JX2JPzSrVvVwghhBBCiOoml0MLIYQQQgghhKg248b5Fz3voiZIECyEEEIIIYQQot6QIFgIUf1s63imUxBtH1tJtuu5haj3avqMuRDiHDii PWJu5g0dS95NZ0WIUQJEgQLUas5ODFzCu18RjHo/RicpaYlblnK5DuepGerawgdPJ0oR/HpdhI2T W5W4fRpVkgDfpP4UCJ6WfL2PkZ48M9GfZFHKro21yiF77GLf1bEuhpwTO4FZfe9SmbUlS561EZ /j9xVu4tG0oPhYjZu8QWvW5koe 3U4GgM6Hxq1a07qJH3oAlcSsu9sQ4mPBoNNhMHsR0LQTQ25 kdlRWZXcZ0IIIeoWB4nrPuGhm27iuQXxqFLT0o78w2 fvML/HriLO56fR4yzMssXUKnsX/QVrz/xX26/ SZuu/dxXv3uH07mVjY9xVaZc4oNMz5m8qR7uf3mG7nptnt45Nm3 G7FUXIANA8ahDYitIFHfodbZbDxi0e55/abueH667nhplu58/4neOmjGWyMLTMhQogLRB6MJUStpUhc8jlXTtpOrrX0K71z2fnZK1zzeiK9Jo7i/z69mWZhjQjTF07PZsfHExj3yil633k3z3z5As3DWxKup0yO5J38/v6LvPDefA5m6hlcfGL630x5YiopYybx2VNNUft YfILD3G1IZJ9nw/Ds3SqU/7mmWFjmXIwjHH3Ps1nfcKxpMdyeNcadqcpLAD69tw3czX3FS1lI/H4UVK6PcOS14dhykkl/tAapk6ZwrUjTrNo16cM8zqPXSmEEKKWUqTt JE3vtuD3VS6rcvj2J/v8dasJCKHDOWqe64hOKAhgTp3ly/OgC3PQOTlE7kixEzGkb/5fcYXfOAVzhsTmqGv5PpU5l5 fWUK8 IC6X7ZeO5qFYgxO5n4Ewc4kQ1GAF0Thk96iX/fZOogLTGBzObjefbGThhsWaTGHeCfefN4/9U0nnz7TjpZKrHrhKjDavqtBxIEC1FL2Q8t4s57dzDoy0fxfPIl/ik2LWvtD9z2jp6nV37E7RFnH8ZZq5/jxikGnluzgTtbuHrpkYPo7x7hiT a8OBvn7L9loeILz7Zezgfbt J0WTM/3zFpRi3LuS69Ws57BhGpxKBdRarJ9/NW/va8fzKJTzfvXjk p9im9zFS9178vPl/7D79R5FFZEusDW9e/fGCnDpCEb4RRF64zrWRTsY1rGcCF4IIUSd5Yhdxief76H9f /BMvUd9hablrv/Nz6cp Oql19lSEjZXdaKli9B86TjlRPpWPi5fXNy9mzk26MnyaNZfrvj9vpyOTDzS afasLVLz7LNRHFI9dh//7XeZyZTz3Nmi6TefuGFkWBtubTiMjIyPxXErbrTGePWO79MIqo0046hctFmkJUBznShKiN8qJ5/ 6ppP7n/3htqC8lzkWrVOa8 wdHDQl8O/4WGjWcQIchb/PRutT8S7ZUKr /9TXRhpN8Pbo5Af7BtBowkffXJJZzSZeelo8sJXrjjzw tHGZ7wkuCoABnEnExufh2SKSxqVrkKzlfDPtCIHXPsuk7ucxdOvMJeXoKr6atgZb04EMiJAAWNRvc cm1/hZcyGqnP04Cz6bQdaIB7i5k0/JaSqNDfOXc1qfxPI3H DOO 7mkRc Y9GB9H/bsoqWr4gzm/idi1l12IPOPVpTFMK6u77cPSxfFY93n6sYHXEeQ7fKRmbCfpatOoA9qC1tQ6RbLkR1kZFgIWodO/s /pAPuIo/H2mBRYsqOTlvPyvW5tLksqFMursjEZ7prPvoY/7vqrfw2vgyE4P3s3xNFmHDbuaJ/wyghVcSa957kMfG3IbX9vncVdZZZp3OzTNieUR9cz vbO3GM/9cQ0CpK8Ucp/ZxINVAp97dz7pM2h25v9 It FGcDpxKIXm2YH7pz/NoHNZmRBCiFrMwclFX7OQK3hudDOMHCk52X6IPQdyCeg4gLHD2hBiyeDAwu/48c1PsEz5P4YEOitevhyZq97mvk83k6P0hPS/n/sGBBWcaHaRnmKcSSeJydITHtkC8zn8cvuGD7nthg9BKZxKoZnDGPHoeNqdy8qEEOdETjkJUcs4Y5bz3HsZ3PbmONqXMSyr0pKIy9TR7oqRXDkgkk6XXMK9793KSMc2flmQiCMtidgMPe3H3sVVg7rRudsw7vv4Ra5wLOOneac463kibstm71c3MPzxI4z78TcmdSwrcQoFaLrSVYud7a/2J7zXC2yyl78F07A32bB9O9t3bGX9sum8fa2RqdcM4uElKeU mEQIIUTdo5JW8cuCLC695XLCyhiSUVkpJOfoCOs hJ7tImga0Ynhd0zgEuduVm1Owuli fJ4dLudl199gf/ddTmBuz9l8ucbSVGu03NW gBNV/qeYQdHZz3Pfc/M4HAFD6I0dLyJV6dMYcqUN3j1uUe5uY ef959ke93ZkpbJ qNmn7rgYwEC1GrKM4sXsmSxBP8NewqPir4zmFz4HzubprsfIbodw0YNScpyZk4seafyfIMJKwBRCWkoYwF05NScOJVML0J4QFw4PQZnISdw9mvPKK voHhj0dz5U9/8cHo0DLXoW/UkuYeDtZu300ugyl kZgtI5H4hHTyFFDOs0Y0nzDadehQcG9WF3oNbE7i r58 uPfvDVsHPK8ECGEuBgo0ravZUfaKbZPvoNFBd857Q6cPz/GXcce4fPbDehRZGZkorDkNxuWBgR6Q0xaGqmulr /O8Yytqx5BBIeEUh4RBtaW07zwOd/sP667vTZ6f76dP4NCTY7iTp6AjvtS2zHkZtOalo2FZzvBY8AmoSFFdx 1IyWbYNJP/gsf/2zj5s7lZ1uIUTVkiBYiFpFo8FVj7Kpb86/Z4MdR/nwmjfZMv4lfnigLSav47RvCt s20fafwbgBzgTj7HntIGIlkHovex0aKb4as0G0u5vkj89YQ 74420iAzjXO6uTf/nGa6atJ R01bwYTkBMACeQ7hhXBAzf3mDbx7sx/2tXT2Uy4W8NFKzFEazWS5bEfVa4dlyuS9YXBw0vHvfy5TWxdo6dYJFUz7mUK//8dCoVhgspwgPViw7cIisEQF4AirtJCdS9YQ0DMSnu4vl3UmFBig7docb6Sm oLk9/br7sGHNHJZf3poRjc6zO23PIisP9EZDeeeIhRBVTIJgIWoZvW8QrXyLfWHPJsCkYQ5qSGSoFY1Ibr6jDZ89/y2PfOHFwz3srHz1J1YFDWbGKG80gxe33d2Lj59 ivs/9eOxXjaWT36Fv4NvYM6YBpA4mzt63sm6MdPZ MFleLtKkPM4U1/6jJj k7ktPJ6d2wueHa1ZCGnVhlBrsXk1P0a/ j7Xr7qFRwZdyvZH7mX0JWF4OZNYvyvV5WVezoR9rFm9GlNeJkknd/LXN /zdVxL7r 5X5kP7BJCCFE36TwCaORR7AtHLl4GDZNvCI38LWg0Z CQSP789Re /cuT0S3t7J45i70 /Xiimxd6D63C5UnfyGdPf87Bbo/y6u0dsdoOsWx2FOaW4TSwOMmI2cWSWVug1c10C9LQ6VylpxjNk27X30bf/R/zw4uTOTrqMrpFBGBxZhB1PMtlW6fSTnFg/34M9lwyko6xc/kilqU0ZMSA1tIxF6KayLEmRJ2jo/UDz/Bb1qc8aLDDqjo1H3wXzy z2M8NMAjTYP/8asrId58rXx9EnU0bjnDXwx721G mmoRFAF9 66xbaLjVuzSE5 nAF/FPve0I6n1 /g1W4lqxFdk2v5fl1j r72Jt98MYmfT6VhN/kSEh7JsDG9CC1zSNdIYFhT/H57jREDJ4PBgk9QOG17XM07i5/kv4NchupCCCEuKjoaj3qEx/K 5 fZb/NsukaDFv24 3 30MXTzfFSRVFbp7IzORO9ilV/neRMlsLsF0qrbrfzzLXDymmXKqYF9OG VxrQavZcViz9kTVJ2TgMHvgGNqRTt5b4lZlEPT6BgXiunc2rL84EnREPn0Aat jFrU9fybB21rIWEuKiVNNXNrl71UXf7OzsNaW/HPfbuBKfF9 2GIARP4wo8f3c6 aW Gy1ljzIlcqvojStZHKys7NLfH7q4F8lPr/RSioLIcpiNg9zPZMQolZ4dNe8Ep9fjxxe4vO8efPkcmghhBAXrbFjx5b4XFbMZzYPc9leAlit1n7AWlfblJFgIYQQopaT4FcIIYSoOvKsGSGEEEIIIYQQ9YYEwUIIIYQQQgghqk1NvydYgmAhhBBCCCGEEPWGBMFCCCFELVfTZ8yFEEKIi4kEwUIIIYQQQggh6g15OrQQQgghhBBCiGpT0289kJFgIYQQQgghhBD1howECyGEELVcTZ8xF0IIIS4mMqfz/B8AACAASURBVBIshBBCCCGEEKLekCBYCCGEEEIIIUS1qem3HkgQLIQQQgghhBCi3pAgWAghhKjlavqMuRBCCHExkSBYCCGEEEIIIUS9IU HFkIIIYQQQghRbWr6rQcyEiyEEEIIIYQQot6o0pHgET MOKflNE07p WejMo p WEuPjNq kECCGqUE2fMRdCCCFqSn7MV7V9W7kcWgghhKhDSj8gq3SALNNlukyX6TJdptfF6dVJLocWQgghhBBCCFGtavKtB 5eh9w3Ozt7Tekvx/02zq2F5143t8Rnq9Xq1nLZ2SUvd37q4F9uLSeEEELUVa9HDi/xed48ub1BCCHExWvs2LElPrsb85VuLwGsVms/YK2rZc8rCBZCCCGEEEIIIWoDd4NguRxaCCGEEEIIIUS9IUGwEEIIIYQQQoh6Q4JgIYQQQgghhBD1hgTBQgghhBBCCCHqDbffE7xly5YLmQ4hhBBCCCGEEOKCczsIBujXr9 FSoeoBXJycrBYLDWdDCFqJTk ai/Jm/Mn 7BukHyqGySf6gbJp4vPmjXuv8xILocWQgghhBBCCFFvSBAshBBCCCGEEKLekCBYCCGEEEIIIUS9IUGwEEIIIYQQQoh6o1IPxhJCCFEFVA6Jx48Tn5yLd4sOhHtrNZ0iUa480uLjSUjJxqNJJKGe55hXkudCVCmVm0p8fCIpeV40axGCRQ6pOkvy8hxJu3Je6sRIsHLkkJ6cTKa91ARbPNv mM6vvy9jf4qz0vMKIUS1KF3/OBM5sG4DW3cf5nSOqunUlavc rQ cZxm14qVrN20l1NZ55FXdSTP6yxp4 sdR x2lv 9li3748mp6cSI8yJ5eY6kXTkvVTMSrNKJWrmU7bGZ5DoUmqbHYPbAN6AhTVt3oHVjL/Tnuu68I6ycuYaTKoCuo0fSwfffsxwqK4HYpFxsznhiztho43HK/Xn9zOf3m sblcLOhQvZkaInqONQhnYOwlgwyRa9khmrT C0tuKyq3rRsE6cWhGiChUeH8lldL4NzRh4uX/J se76jbtzIxh7/bdHI49Q0aOE53ZE/ gJrTq0pUIv3OueSuse uUoryBwEvGcHl7H roL6nXXJVzaeNriOMka2as4IjNSPNLJ9A/rKDOccaw/vflHMzRET7gWgY1kwsPLxjJg4uXi77FoGuaV3 aLiJVdEQ4yMnMyg A9UaMeoU9N53EU kkxpzgdJ9RDGrheW4dD6VQ5Zzc0Hwj6dHDxrEcf1o2NYOjEvOKc6NsJOz6m7XelzMwwks6k0KUoumNGIqdCNKMBvQ F6j sZ9m69IV7EvLbyA1TcORk07CyVhCO3c7v3VXUPcKUa3cKOfSxgshLmZl9S1kzOn8VPFpIR0BnUdxeXsfVE4Ce1YtZ0dcDqcORJMW0YbsHcvZdDiFjBwbTr0Zn6CmtO/WlQg/A6g0jm3dzoHYRFLSs8lz6rH4t2bgEJ/8VTvPsG3eNLYBuuAeXDm8DZ7OBKK27uaI3RtCw leMKtb8wbpQGUTv28b26NOcibTgdEriPC2XejSKhAzgEomau1mDiamkZWTS55dw QVSFi7bnSLbFA0ElrvqGyOb1jFLp9hdAosqwjZidteUV4nc3DdFg4mpJCelYvNacAzIIwW4VaSjx4hNjkHLH6EtupGrw4N/703RGURt3cr26NOkZTlxOQdRHj7bnRt4V9/80LUMv/WgSVOEDlOsqZ4/dOgnMUrWcadZ45xPN0Jmh9tLxtOt4ZmsKWTcDoXL79cDi fzdpTDqytLmN8r4boUSTvWMjCncnoGvVm/NCWOE/tYNP2w8Sl5OA0mPH0bUq3S3vQRCvayNn1KS7Sea7HeI1wUV8VUtkcXzef6MwMbHovgpt3osclzfEtHGyX umCqbicFxQeR8k2vmvOWmasjMZWal06/85ccUUn/FyVYVHFFJnl1TUW3Dt 8s4QtWUze4 fIdNhwsdT4QQ5Ge8ud/q0uYdZPnMtpyi8AkgRv3E2Sw5kY2o5hGv6NEIneVkDyu9bHDtrXjfaNGcmMft2sOvQSc5k2MBgxsPLl4CIS jbNgC9qzy SFywkwg6SyDNG/uiASo7i2ylQ8vLJNOpx LpgUnlkBKzn3WrdnPGCTjTOHnwGPHJmdg0ExajIk8z8e1mP28sHHxwcfT5OLA8WdeW3Eb1nC0i2HOZ1uQzNo5KXFErVhCct3JeEAcGaScCKOpLRsbJgwGxW5aXEc3LCSrbH19SY5DYunB3p7IrvWbCUmt6yhIld5ncnp47GcScvBoTNj1tvJSDjMji27OZ6Uh86ow56VxPEd/7DpRG7BOm3Eb13Gsq3RJGRrWD2N2NJiObBuGeuOZlfj7xfiQql8GddMJkwAZJMUe5q0PIVm9Ca4cSAempnQJoHoUeTEx5KiAJXF6fhUFDoCGjfCkn2YDat2cSIpB52nL74eenKznOhNxbdSuj51I53ndIzXFBf1VRE7menZYDRAbhqx 9ewYktcQZAl9dOFVHE5L2cZoxVvn4Jy620puCVLw DhgUnyq/pVWNe4kR8qi8Nrl7Hx0GnSbRomk5P09BzkYpVKqKo reRlLeeqTcvl1MYlrNh6mNMZ4OHrh6cuj/SkOE7Ep Xng1t9g7rvwtwgoBzkpMaw/2gyTkDn4YmHpsO7x5Vc18NBXnYutpzjrF 8mdi0eE5nKQKsBctq3rQeOpbuQTqcTic6W3T 9zo/2g1x8740N ZVmUfYGZWKU/OgWb/L6dfcQsaBlfyxKYYze/dwqs0AwgtPEWhetBoylu6BWRxYOp NcVmcPJFIj9CG9fBSBA2fNv2IOL2aDSeiWLcphGGNSs jI9itvC7Yrz4nWT3vH6JzdDTqPZ6hLRxELZvHhtg84mLO4AxvhJYVza4DKTj1QXQdNYwOfjoyDy5n/voYThw8TlbT1uV2hoSoPk4St85l2tbCzzoadBnNqHaul1TnUMY1/9Zc0voE/ xPJn73SubtsxLQpAWt27UlItCCtVEYAbo4TqfHEJPWhQDraWLPOEEXSJNGHpCVToYdMDSky7AhtPLUUE5nydOjpepTlRXFWlfpLEqg 8d4zdWl7tZXnrS bBw9QzQyDq5k4YZTpB JIqZrQ8JtbuRdjf2 us9VOS r6tc17MYV47qR3ylfzLI9Oei8IujTpwXW7IOuy7C0J1VKVVDXuFP3WdOjiTqVi9K8aT10JD1DzeQdWcHMNScleKqs8 zTSl7WhMr0LSpu0xpwhN1H0nFqnrQYOIq YWaSdy5k4Y7kojVUlMcXkyoOgktnEqB5EN62Od5kEbNtLRsPxJFhL1bMdXbs5ZyA0uku3N52JieS5ADN0pgWTT3RAT4RzQneEsNJ2xkSUxXh/qUW0jwJDPRAi0sjNzsnP8C/YCmsxTQvWvbpw5mUFRw8upGNuR4lKy5Vybw2BRDkqxGdo7Db7CjNk4AAT7TYVGy5efmXyCQlcsYBkMC2 T zrXhyMtPJVEinRdQKJe/b0WHUu1cwnedUxi006jGSsU2PcejQYaJPxHPm2G7WHj/Mid4jGNQijGbBWzkdl8LJU m08Y7htAN0AeGEeWtojsY09tlLamoMG fO5kjTlrRt35amfuXXbG6ls/RCbhzjNVaXul1f6dDpNECHV1gYARtPEWtPIyVD0STzHPaJqAQX5byld7lXh2Uf38iavck4jEF0HdSTcKuG46S0J9VN8y2/rnG4UaeYU5NJdYJmDSU8JP e7wvZR6wXzrFPK3lZM9zuW7ho05zpSSQ7QLM0olljC5Rx6qGiPL6YVPlIsKbp0On1GMye AaG0qx1OyJDPLAfX82avbHkGYNo3aMVQcZkojbt5bTD1QoL/6NcnyGqzLznSKcvuAGsvj8xxtyYbn3akrB0L7Ex Q 0L9z9thNbK5fXmp7C k8V7FedvuiLgn d Xmq96dZ2yaUeBWaOVg6LKKWKOnTTXi55zGdfjERxBp AIOtlSiFqzlI0nsjm55xBJLboQ1iyErXExJB0/RrRvHHlKR0B4WP76DcFcMnwEfnt3s /QKRKO7CDh Ak6D7 cTkVPsC5Vn7qTztLVozvHeA2pdH0FKIcTJ4AGmsa57RNRSRWV864ElLGEyjjE vXRZGIlvOcA2jco6PJIe1J1NB16vQY2B7m5dih8F4gjjzy7AgqmV1DXtHcrPwq dDpxyLFUkrt5UIaz rSall nOZ04ynvTmORlDXC/b G6TSvM6wruwa6obxBwHm dqGWq/sFYXct6BYUiIz0dmwItIIKObSKwOmOI37rPdRCsN2HSA/ZMUlJt4GsqGJLXnZ15lZhX5x9EA/0R4nJPcfhYJg2bW8g4Es1pJ2BsQICPtIKuGEM606vNKZbsTeXfulKRfa55XQGdXwP8dNEkOHNweDajfaQfRg0cORnk6r2k0yLqFk1D02lALlmZNggyn1sZVxnEHUvFFBSMv6cRTW/Gw1JQrdtt2JRGQNOWNNkWy9HEPWxNsaP0QTRrWjBy5swlR2tAi0supUWnZHYuWcSOxBROxKTTsV3Z9al2UR2L51Jf5ZF48DCJTtAsAQR4aej0buyTMvJcuMllOS9rmXSi1m/hVC54texNr4h/31Ah7UkV0nzx99VBjoP4qN3ENOxEsDmH F37ibEDuoLpFdQ1HZq5zg/l3wB/3RFO553kYHQ6DVtW4Xvm6jp388AdBgsWowY56SQmZKH8rWfPI3lZe5zVrphctmk6X398ddEk5sRw Fg6QeEGsrJLXaZZUd8gwO ieYBZNb00TMMzoAEWLZGsuK38uegY3qY8UvPcOAWkC6BhkJHomFyOrppNvFWPwxDB0NGXEHge82qezekYuY/T 9M4unoOpzbqceTZcKKnQZv2NDEB5xG01Q8Ggjv1otWJJexPL8zL88jrCmjeEXSIOMDfhzI4sWEB07eaMWk2cm0GIgZfTd/GF8 ZKVEPaN74emuQmMexNQtYbxhH7yaVL Mq6SAbV 8mVQGaDh1OnApAw7NRYwJ0gKkJrZp7cmx/BjYbGBpF0NQrvwlzJu1m8eIobJ5eeBidZKY4ARNeXlY0namc rRdHT0WnSRum8dPxa/PM0UwsJ b9ZXKIGrFbI6RS3auA4WR4PZtCTW4WT Vmefy3k53uFXOS7XXOce2sSMuD4WOvNgtLJ67BQDNswX9h7aso2W4FtI8adY gr0JB8k4s5dls/cWn4hns/a08NFwJpZf1 jcOH40rwg6tNjPyoMZnFg3jxnbLRgcOTiop7elFedmHrjVp9UFEd7EyuFDWcRsnMeMXSZUbnaJC1kqajckL6tZGe1KDxd9cM27OW3D9rH6WCbRq cQXcZqK wbVNuPu/CqrbzpG3ZlUPcWBHvpyE6KIy4uFZvZm4CQEHwretqY5kFE7360b SLRbOTk 3AZNKVfQlFZebFSMPuwxjcpRmBXgYcdidG72BadL MoZ0CkCbQTcYQOnWLKHHm/JzzukIWmvQazuCuEQT7mNE5csl16PHwC8BTX941O0LUUpoPrXv3pGWwNyadEbNVz7mUcacxgPBmDfH3NKFHoTQjVp8gmnUcyGU9Gxe8jkJPcOtW YGCZiEssmnR/anKacbb14QzK5Xk5EzwCKJZl4H0aGauoD6tw8eiUqjif06FzlV9pfMkqEkI/l5mdLZssm06rP6NadNnOIPb RU0om7skzLzXLjDvXJenCK3YDQEnORlppGWVvCXnoO9LpfhWsjcuCfDB3clIsQHi0GHpjNi9QkhostghvcJx4KLusatus9M457DGdylOcHeRpy52eQ6DHj4BNAw1J L7KG1leZOHrjHSOPul9KzZQjeJoUtOweH3oJ3gxCaBHrkv/FF8rL2KKNdcdkH1zxo1m8El3aNJCw0mJBGTQkPKnjAYMGVsxXn8cXD3YC 7 rVq9f069fvgiZG1KycnBwslovoBWBCVKG6eHwopdA0yDm5jj9WHibTux0jRncj6CKLv pi3tQ2sg/rBsmnukHyqW6or/mUl5mBsnph1gGONPavWMSmWDu HUYypmtAnR7tXbNmDf379 8HrHU1r1yLJYQQFyUbx1fPZeNphSM7BxsWmnZqR BFFgALIYQQwl3ZHF03l42nDVitJlRuFtk2JxiCaBnRoE4HwJUlQbAQQlyMVDa5dh2OnGycZn atu9F7 YX1/08QgghhKgEZcPgGYivJZXMrEwcegu DRsT2akrbXzrVw9BgmAhhLgYaT60GnwVrWo6HUIIIYSoHTQfIvqMIKKm01ELyIPYhBBCCCGEEELUGxIECyGEEEIIIYSoNyQIFkIIIYQQQghRb1TqnuCcnJwLlQ5RS0geC1E OT5qL8mb8yf7sG6QfKobJJ/qBsmn qtSQXB9fJeWEEIIIYQQQoiLh1wOLYQQQgghhBCi3pAgWAghhBBCCCFEvSHvCRZCiEoa8cOI81p 8W2LqyglQgghhBCismQkWAghhBBCCCFEvVELg2BF0tqveeX9PznuLGOyM4blHz7NW3/EUdbkC7bdilywNIlaSyWy5stneWVWNI6aTosrUj6FEEIIIVyrS/07cV5qXxCs4pnzyiQ 3JKDf1mpc0Sz4P33mLkzFVWd263IhUpTXWVbxzOdgmj72EqyazotLqi0LXw2sR/N/S0YzT40u3M2qSqd6LULWbonrfz8dMay7LN3mLYp8cLkeVXuw8qWT3d v6iXyjxeXC4k5UmIInWofazXJJ/qhguRTxe6f1ectI81qtYFwSpuPtNXWRk5YSje9WC7GTs/Y3y4J8O iKu1B0D2rBvwMTbnv0vSyphqZbffAwD SDowXjjDofGrdqTesmfuirNaWVZWPjqzfx6Ipg7vv L1b/vYDvHu6Ht20Tb024muf/TKi5PKnJfVgbfr ohco5XlwuVk55csaz6oP/MLJzE3wtZrxDOzDioansySqcIZfoha9xS/ WBHpa8AxuxaV3fcqmFCmVFxd389lOwuapPHfrMLo0C6RB/ykcKBymcZzizxeupFOoF1bvJnS7fgr/JFRQTlzNX4n1nXf7qJKYdXcbQnwsGHQ6DGYvApp2YsjNLzI7KquMddZSLo9nKpdP7qwPqLBcFFN/8snV8eT6eHOeXsmbN3QnzMeCtUELBtzxMRuSXNW77uSDnePTb6Wl2Uzfdw6XeWVa/cmnAtLfqlG1LAh2EjN3Oqs9RzJhSHWGotW/XUfyTqa/cBU9 j/E/FO1 YILJwmnYsm1H O7pz5kl63kVBX7K8tZFsZwJxCQWVkr49981czZxHu2Cq/gS7z3mMVauOEXbN/3hk3EB69R7I4E7BteOgqCv7UNQfVX28aGZys430fuAjZi6ax9eTOnHy67u48c3t2AHS/2bKE1NJ6TeJz6b/znf/60nCLw9x9ZNLyay6XyVqmlv5nM2Oj6 kx h3ORg2nme nMNfX99KuB7Axu63JzDhncN0e Yn5nz/MBGbn fKm78kusz7P1zNX5n1VUX7aCPx FFSuj3DkrVr Xvx73z13JX4bpzCtSMeZ0lGVezkauDqeK5sPrlcH1RcLoqrR/nk6nhyNd0RxcfXjeOV/d15ef46Vv/2GE3XPsEVt3/PiXLvp3InHxQJix/liodWkGvVyllPPconUaf0Xb16tbrgHMfVJ0M8VMOJC1RG4XfZB9Rvj41U7YI9lMkaqFpfOlR19jOrnm/sV/bCefKOqgUvTFC9WwYqT6u/at5/ovp0U4pyqky1YGKwMnWZrHYWzexUpz4bqiwNblSz0srZrjNNbfvyLtU/wl ZDSblHdpe3fh9tHK4nSa7OvD5VapNiLcyG4zKq2FHNebZRepkURrs6uA7g1V4j1vUW4u VDcFWNRln8cq54Xbs fBpjY 2VqZmrRSLb1D1PUzEoulM0et/7 2ytqijWppDlR3LMrN/9q U03uYlGtn9yobIWz2mPV8jdvUr2b SmL2VMFthikXlqTo5QjVi167irVt02o8jEblcknXF37w6n8fW0/pZa8er3qGe6jzGZf1bTnDer1ZTH/5rurfHK1vH2nmtzFqICCP2N HuYuU/9tpCv2vUVd/Wtmyd1i36kmdzGpgC5D1YDIBspi8lQNO4xW/zfrkMr5d6aKy0FF6a/MPiztfMtnub/fVbmuP4Z/P/y8/uqk8o6Xcy5PpThPq68vNyvLuGkqteCrvNy8YjNkqFk3 Clj5xfVjnpY5i5mrvI5c9Vjql3YOPX1odyzF85Zpu4LM6lWj60pqnvTFtyhGpnaqCc32io/f6XWVwXtozNOfTHcrCzX/Kayiu FGdcpb2MXNXlnHS3spY/nyuaTq/UpF WihPqVT66Op4qm23e9pLqaG6l7Fv/7K9Pm3KKCzL3VlKiyf6M7 WCL lyNbNxBPbjwD/VkW6vq8/ahf/tq/85VO/LJrf6dct3HdGced9vH0sqNe1TFfUvHSTVr0gjVPbKh8jEblNEjWLUZcrf6aE1CGflRN61evVoBfd0JbmvFoFch54k5zFjvyxUTBuMJoFL5a9Iobvk6nr7PTmPh/O94arAv2bnFLxrIZPXTo7j2mwwuf302fy//nnv8l/LI Mf5M82D/pcPwrp/Bf/EFJ7CSmPVss0Y o1ggFfZ23Xsfo JDy7E964fWblxHX9ww3dw/N31lupUlHSN97eGPan6xet4Jpj7Zg15RbeWJOSsHlDnpaPrKU6I0/8vjQxrV8pM/JmdNn0HV8mHfu8mXeG5 zp A0rIr7jde/SmT08y9wWWAmp0 XNz6TzaaXrmDMKzuJfOAr5i ex/ev3MeQCCOoBDbNX8CRlg/y46JlLJnxEQ8NDEFHNhueH8XYN/bT4Ymp/PHHDzzWbg vjRnNS5tyABf55Mby XQ0v/MXtu/axa5d2/jlzuYFlx8b6fL4Inbs2sWuXVt4b6S1jN lyM4N4LL/ 4o587/n/7qd4NPrr D/VmYUrbuiclBx iuxD0skqSrKZ3m/353lxMWtrOPlXMtTMY40Dv/1MVM3 zH8yv54FS5lKla nUnExufh2SKSxrWq5RLnq8J8Vgn8/tbXRBtO8vXo5gT4B9NqwETeX5N/v57jyHo2xPvQb2g3zAWr8B5wGb0N0azfEHvWJZeu5rdVan1V0T6W4swl5egqvpq2BlvTgQyIqN03FZWpjOO5svnkan2uykVJ9SufXNWbFU13pqWQqnxo4P/vPJ6dutJK7WPX/n/H4Iu4kw95u3hn4ouk3j VKcMCKW8cuHblk6v nTt9THf7oe70N4urKO5xFcMksWv5Sk61e5Sp8/9kwc vcqVpMY PuILXtuW6uW/qn2oYCXaoI 8PUNZGd6s/C06COBN UGO8LKr/u4f/PUORt1o92txSNKrlPDNNjffxVVdOTSg6Y Q4/qEaZA5UExfmKOfpH9QYb0816pv4/OkZ89StQZ5q2OcnC9Z59nbzlt vmpjaqSfWFI1HF3EnTWex71GvdLOolo vU3mlp UuVBNr9Uhwqpo6zqJ8bpqjso5/rob7NlF3LUpTStnUjsldlbX902pT5hb1bHur6jUlKv/3lz4zl/ybutbfrHq9sU ddb63rBFPpZQz6Vd1jV/ MkX71LZHvdrdrPyvm6FSlIt8cmP58radf2bOXM6ZygrSbd nXu9pUr4Tfstf/1nLlCwHFaW/Uvuw O uivLpzu8va7l6pP6OBJdxvJw1X XKU9LUK5WXXlNoJhVx8y/qaJkrz1UHvhyjQv0GqLd2uhr1EXVXGfmcs0DdHmBUra5/T/2 crPavvkv9clNrZXFf5T66phD5a18UIWb2qqnNxcrOHkr1ANhJtXu6c1nlVVX82dVan1V0D4WjFxpml7p9Xql1zQFKM2zg3pgYVydG50p73iubD65Wp rclFSfc0nV/Xm2dOdSTPVDYFG1eLWn9T NIdS9kx1YuljqovRQ107M/vsVbjMhzy1Z0o/FdzvTbUrVyll26SeKnckuJbkkxv9O3f6mG71Q93tbxXjKu6pVN9SKaWyN6qnOhhV4M1zVNrZS9Q5dXMk2BnN7BmbaDD6GgZ65H9lP7iTfXlh9OkbXm5C7VHb2ZWZzoI7m2C1WLBYLHhEPsbqvHRiY9MgcCQTButZPW8xZxRkrZrHkuz TBjbKH dZWzX2Pde/jc0hQ Gd2TI3W8wY1tC0T0o7qQJcjky9zmu7deWsEA/AsJH80mUndycnHKXqLWcKSQlg4 fD4awm3n8Bj3T3/2JYymL eDLaIZMup9LLD74 kDKmeQyRwRt zezLTOMAYNaYHBzs/YDW9iRlb9M0Xk7QySDBjQmc/tmouwu8smN5aucvgV9e4eSvWcHh zgqhxUlP7S3N2HF7Z8XkTlWlSh8ysXvmM YO36lcz7/AGaLpvIoDtnEVeiIslm71c3MPzxI4z78Tcmdazd186Ic1V2PqvUWGIz9LQfexdXDepG527DuO/jF7nCsYyf5p3CiUJVMLZ0NlfzV2J9VdA FjINe5MN27ezfcdW1i bztvXGpl6zSAeXlK3rrQp/3iubD5VvD7X5aKYeplPrurNsqdr/uN56/uHabz0Dtr6mTCYfGg34Wv2OANpGHT2KKqrfLCf omn3k5h4tsP0sFV1V2b86lU/86dPuaF6oe6insMlehbAmDpwohLG5K2bTMHL0TfuBarNUGw4/BsZmwJZMyEgRRdCKBpgEI5KyiySoEulBu/3cz27dsL/naye 9OvrqmAZoWyKjrh6FfMYNFCRn8M3MhWZdez9iGWvnbNXfkwYUH2DP7cTqf/IY7erRl8Oub8x /7kaaHLvf4bobPuJ4t//j z9X8/e8t7m6aa3Z1ZWjUkn5f/buOzyKog/g Hev5NITUuggnRBC770LSJUiWEHsIooUXxUVQURAEEQUaaIUkaYoCNgpoUmvYpDeW0ghNoCGlAAAIABJREFU/e7m/SOFtCsJCQnw zwPz0Nud8rOzO3M7O7NRoGnlycaHrR97SWqbfuUt4dPYoXL4wzrXxKd5omXpyIyIir7R5qUNRcnHeU4jL16cia8PTnvq5NTtVpB06HhRDuwm/8sETt3PHnVPrM5/nuqXYs8k9v2lErnU5Ya9VvS7fnJrJjcmfCl01metgJLImFzH XBEf/RdfGvzOhm6 cC4u5mu541FxeMmpWI8Ihb/YtHacr6w7Ur16FoCYpyhUtX0i0wGX JC EaRUtkXbhN52B/Q07iy4v MfU4vcsQHBJCSI3aNGrbl2GzZ/NyuRMsXLCRu khRVvfZ0flbut7bSs R 0iQ1nfd/Xk6Lxpb7uOUl0 ZuPZcC6fCOP4hevseDsYnWcDmtTIegnefj1c48q67/jl6lGmti6Cq6srrp7N PjfeHa8VZ3Ap37MWGaFvJ7SjcG2M6OQ7N6XjT0bwnJ2PL1CzodMnx3mcKyXjCwn/fL2dfYHf6NndN 9RQtR613M7w52//kGgjpKFyTYJNV9h/zEKFoCCC0v5VobSPHtDw7zqA7u4bWLRgAYvWmOk8oCdFNdvpAqB5UqnDy0xdt5f1Q4vy94x5bE10Lk/xB3dxyNqcF98fQLv6IYTUqU9lv0JS1DlljSIiUuHu6YEG6KsO4tWOV/hu/g6qvTiEVu6A5oGnO0TbOCkZKteiuuksmzcet381Kn2YqvWo5XaWzRtP3HpZufkYm0LP416rHlVSz8V268mJ8NnR3HB3g8gbkfZ/p5RZwn5 23gJr9r1qGxwsh3YyH W8nCyDPOkfdo4/nuqXYs8k9v2lB1N09BUEkkpq4JGbxpFr2FH6bxwPdO7lizkr1wTuWW3nj2rEVJOcWDLDlJfmmK9ephDl41UrFwGlwqNaVQsii1/7U0b3N4M/Z3tSeVp3CjrRRO9g/2NOYkvD/pHmxKjiIxVGE2mwjJQy7H032dH5e7MMWY4PzhoFxna0H1WT47Om06dV3XuBD5QgRIxq3h36m5KPv4iXYpkM1uzWw9lKdp3DvuPHGJ/6mRt92IGlTdR6/XVbJnQLuOaOIW5njKN75wZYzo1Ds3FeNPxvAenx5YAWI6zddtF3KrXpKKzj2veIwrH4VrCWLl8P8V6TKRZurmoVqQHI18Jpu2E3vRnNM 3LIvp5lbCbt66WqEF9GToMx/R eN PG4YxdPNymKKOcvh8IoMfLIJ3hrg1YFB/QJpP3okxoCnWPWQb/KFFxvpWo6vYdYGKyE1y CReJYNR26AXwB OufyZAqqQWX1GXPGLaRUvxACDec5FXmXXmFRN4mOAQ8P9 Qy0wLpNWo8W/3C6fFMlZSTpwseHkYsNyK4qSDT5QS0gJ68/uxHdPygN0 pd3iycUmMEaeIKd XHiHZJ6sV6c6IwUG0Hd fFzzH8kR1xcEF7/LR4WCGzuiKD47qyXF4mwxVqFvTlelLJjCj0UvUUKe5Gtidfk38Ml2wU0T9s5Ff/orDI 4kf345hikn6zDq6854AWYH7cBe/rOUh70yrOWertzyoH3aOP7e91K7Fnkmt 2pX51jzB2/DfeGNSjtZSX839 Z cFqaPIxXcvpwHqGhWNncqH5GAaUvcyBfZeT49NcKVYliBKO1g4RdweH9VyXAc81YsbbbzH4C1 GN0rizzHj2Fj0UVZ180MzteClwXVZMO4lhlT6kP4ljjF35LfEtf6E5 oZUNd 4JmGz7Ct2zL /rQ9Xg72R dge3p50D mFcPVf9gSGopLYgzh5w7w67xpzL1UicFPNCvki2emiN/BHHvfZ30O68lhfA7aRfq83U/15Oj7ZHL0fVNEnj7A0ROnOLT5e2bNWMKJqu/w4/h2eEHWejLYrweDjz9V0w 4zDfxd9FwLVqBKiU9C3E92R/f4cwY05l9bPWPDU7yTq0mzGnyE fmdsqQZ0fzHo8TjsaWFs79NJnxlfvTuAwcXTKW8fvLM2jSQ/bHxvexfF0Yy3zwA1XHVE69ujGb172YL6mNnzytWlUOUG4GvXLxDFQV6nRQw39Mt5BU4hm17oNHVeMKfsrNYFBu/uVVoxeWqrPpfmVuPjRO1XMxqhrv7U37MbitdOO2fKjaVQ1U7gad0rv5q0rNB6oZf0fcSs9hnqLV3tnPqhYV/ZSrXq Mbj6qWPmaqtvUfVkXfyjsC2PFrVT9PUyq45zLdvKXoH59vpgyNZuijltU9j 8Tzyj1o/rrxqV81WuBhflVaKmGrj4rLLYW2zHfE79Oq6falDGW5lM3qpsw/5q/O 3lpZ3XE/2w9tb6CchbJF6oWlZ5e1iUG4BQerhLw5nXFTKclateK2dql0 QHm46JXRPVBVbfOsmp5hmXn77cBu/nNShlnK7fbbZ/bHn4N2fY ThbHSy117SrqyXr3btb4q7mDAaT8ildU3V6 Qu17WrKNzh jRpQREv36oiUf4bgjIvriLubM/VsPq9 /aCPqlvKS7mYfFT5Fi q QfSLfpiPqvWvttdhRR1VyaPEqrOIxPUhsvJZ0br1e/VwHK quqrv91a9MXO/k5tT5UX/aP1ulr5TBVV1NNF6TRN6YxuyrdkVdWkxxA1fcP5u bcanX0fVYqR/XkXHwO2kWq 6meHH2fHH7f4tWqJ4ootyKlVfVW/dSImRvU2XRramX/fXKyHpSyvzBWYaknp8Z3yvEY08l9sh1vJW5RwyqYVDVbi8bZmfc4HlumvP6pkp8yGd1VsZAu6o2VmV7/dBfLycJYzj6J3jQ0NHRLs2bNnJ82O83CgTH1aPhNG347OpUWd xSWkGlK4S423X8puNthf9lwC95lBMhhBBC3EvUjUU8XHYE/ktPMO8hd8cBnGU5yNj6Dfm20yYOfdSgkDwOnLe2bNlC8 bNmwFbHe1b8D9hMB9kxcqjlO7Zh0Z3ciJaUOkKIYQQQgghRDbi9/7N4dL9GdAmDyfAIosCvwhgPrCClWFl6Pllwzv6e4qCSlcIcfeTO7lCCCGEyA9ubafzzwEzBmNB5 TeVggehxZCCCGEEEIIIXLv7nocWgghhBBCCCGEuENkEiyEEEIIIYQQ4r6Ro98E//fff/mVDyGEEEIIIYQQIt/JnWAhhBBCCCGEEPcNmQQLIYQQQgghhLhvFPgrkkT iIyM5MTBw1zavpuYq9cA8AwMoFjT lSoHoyPj08B51CIu1flypVvK/yxY8fyKCdCCCGEECKnZBJ8j7FYLOzdFMrVH3 lsV8JmgZVxaNB8qutYq9e48Jfe9ixYi3 3TtQp2VzdDp5GEAIIYQQQghx/yiUk B9e3ezb/8hnnzqSfSZJmlWq4XFCxdSplxFWrdqccfStSc/85QTFouFTcu/x2vFH3T1CUB3/j StuznRmIimqahM7lQwseTbt5ebP/yOzZdvkLLvr1kIiwyKCztWdx5VquFjydOpESZcjz1xGMFnR0hhBBCiHxR6GY/SlmZ fkMDhw6ku1E1Gq18M3XX/PPv2F3NF178itPObV3Uyhui36mcYIOTp7DeuU6JMSjUwpNWSEhAeuV62inz9LMbMBr6Tr2bd6S5/kwmxPp3rUL4z6alOdx57WYmGje t8b1K9fj DgYN54cxRWpdi3dw9hYffnaugF1Z6VjXLP3J6c3U/knFJWdmzfxsVLlws6K0Lck Q8JcT9R8aahVOhmwRfv3aFnTv30qlz53s63Y1//Un/fo9Qq2ZNGjZqxJtvjSIyKjrX8UVGRnJ yY800blDbCyaxYJO09A0jYBP3yPg0/fQaaDpNDSLFW7G0EzvwYVlPxEVFWU37t9/WUtQUDU2bdmW7fZ5s2cSHBzCmfMXANA0jfLly1OieLFcH8 d8uXnM9iyfScfTZjEt99 y6CBT2ExJ/LqK6 wYXNoQWfvvmK2Ue6Z25Oz wkh7i1hR4/QumULFi1Zlu32w4cO8sbIEbRu1YpH j2G2WLJdj Lxcxnn06jaZPG1KpVm9eGDuN6 A2nt6d3u/2jUlbeHfUmdWrXpkqVKgQHB9OqVWuGDR/BiVOnnS4bIUThJWPNwqnQPQ795/4 LuQdOmje7ZdGNjbzJp4iRatm3HCyxInjx5g fQZ6owsfjh2dqzhPHDpM8MkrGAzuKIs1ebJLcoeLBhrJE2JNA9DQrFaM5iRqnonmxOEj1G7S2Gbcly9fxmIxM2XyFBo3 g4Xw61mc 3qZebM/Qqr1UJ4 A3KliqJXm/k089m5Oo47iSr1cKuXbvp2PkhOrRvl/Z5UlJCAeZKZOZse7pb2p0QImeioyL5ev58vpr/NbFxcdnus3jhN8z4YhZ9 vblgw97UrJkSQx6fbb7zp83hznzvmb4yBEUC/RnyscfM3z4SObNm41ep3O4Pb286B8vXrhIUPWa/G/kMBITEzh96hRzZs/m6YGDWLtuDR5ubrdZgkKIgiJjzcKrUN0JtlotrF27jpatWuOZctJPSIhn0oSPaNy4ETVq1OSpAU8TGZ3xjqnZnMSM6Z/SoX17atSoSb/ j3Lg0GEARr35Bt169CIp3RXhZUsWUb9BI6JjY7NNVynF8qXf0a5tW4KCgmjStBkrfvgxLbwzeVq2ZDFNmjQmKCiIxk2aMnXa9LSr0u7unqxavZr/vTGSNm3a8Myzz/Ng 7bs37cvQz5z4uK2XZQyeUBSUvIdX01LnghroCkAlTIJ1tDpQKdpkGimjMmNq3/vsRv3lStXKFa8OGdOHue33//MsG3B1/Nx9/LGoNcTnnKl3GJJolePbkycPDVtP4vFzLw5s2jTujXVq1enXbv27N67H6vVwvRpU nUsSPVq1enTp26rFz1U1qYWTM/p3WrllSvHkLvPn3Zun1HWpyO6slxeCsJCQl8PW82lStXpnLlysycPS9t 8cTPkz7fPXaXzIct71822uPjvJsL6ytNB21cXtxgnPtOf1xT/xoPB3at6d69erUrFmLJ54cwO69 zLsZ6/92yu77Mo9u/bk7H6O2oDVamH8uLHJZRMSQkhIDfo 0o89 /Zne/yFXVJSAi2bNWX2vK/TPjt/7jQ1Q2qwdcfOHB/vzegoej/cg2eff5HEpCSnwtsr8/fffZuHunZPa6uJiXE0b9KYBYu/Swv/w8pl1KlTnxuRkfdU3Yjc 37FMv7aFMrUT6dRxMc7y/a9u/9m1pz5LFm6lOHDXqdF8 ZUrFAh27gSE NZvOhb j32OAOefIJOnTrz7jtvs3PHNg4e/sfh9szyon8EKOLnR 3atWnYsBF9H nHyBHDuHL5EmfOnMttsQkhciG1n2vfrh0hKX3PwEHPsGTJt/R7pC 1atakSdNmzJozD6tSgP2xXU7Hmvk1vhRZFao7wZcvXWDf/kN88uxLQHLDmTh HKvWrOe1116jSuWK7N2zm0MHDmQIN23Kx6xa8wujRr1NieJFmf3lTF5 aTBr1/9Mi5Yt GnNei5fuUrpEsUBxdat26hTr37a1dXM6f4XdpSxY8fx0pAhtG7ZguvXrlG0eMkc5al23XpMnvIJPt7ebN 2halTp1MlKIgunR4EwGg0pu1rtVq4evUqZcuWzfHvkVPFX7mOj9GIFpeQdsdXS77ti0pIQFOK5KhTt4GmFF5GF KuXLUb97Vr16lctRpVK5Rh9qzZPNihHUa9nuvXrrB02UreGDWK6ZM/Jjz8us04Zs74jLnzFzJ4yCvUqhGSfLxlSqOUlQ1//UmZchUYPWYMFnMS5cpXBGDGp9OYv BbXh8 jKAqlVj1/fe8 PwLLFi8mNo1qtutJ2fCp rVpx/PPP0UAIGBRdM H/Ts8/R uAegUbLUrXgBu/m21x4vnztjN8/2wnq4umSbpoeLZreNfzLpI5txerm7OdWe0x/3ju3bqFC5KqPHjCEhLpYlS75l0MCnWbxkCSHBQYD99m v7ByVe3rO7OeoDShlZdfOnVSsEsSYDz4gPjaGObNn8 qQ11j3y1q83N1tpn83cnS87qZb56XExARGjhgOehOfTJmMi9GIxZLksLzslXmjxo1ZuWot4TciKBbgz8njxwm/EcH ffvg8f4A7Nmzh o1auDh7npf1Y2w7cmBzzBg0HMkJcVn2aaUlblz5qLT63jxuWe5dv06FStVZuQbb1C/bp0s 587e4ar18Jp0qRJ2mf1GjbExaBn3779eLsb7W5P33dA3vSP6VmtVi5evMCqH3 iZKnSlC1b2tliEkLkgdR skq16nz40UdERdzgo/HjmTzlAK 99hqvD6vIxr/ ZNqUydSuU4dG9es6HI C82PN/BpfiqwK1ST4j99 w93Lh4YN6wEQGXGDVatW8/LQ4Qx46kkAGjSoz/crVqaFiYq8wXffrWDUmLF07tQRgPdGv0eH9p3YuXMPjRo3wcWgY vWbTzS 2Hi4mLY8fdOBg8dkXw3NJt0IyJuYFWKho0aExwcnCGPzuQJoErVIKqk/L9atSDWr13L/v0H0ibB6X2/fBmH/glj4eL30/KUU1ry7V90yc9ApzwKnTIRvhmLSr07TMp2DTRd6h1j xPvyMgIfHx8Gfj006xY2YPQ0G20adWcZUu/w69ocTp17MDXc2Zx7Vr2nXx0VAQLFi7ihZcH89wzgzJss1iSAKhUuQpNGjfOEGbxt0t44eXBDHjyCQDq16/Pf8fC GreV3w6bYrdenImfCo/f3 qVKmS9nfqIyr AYEZPs9O5nw7ao/ebnqbeXYUtnWLxtmm6eHmYrON34yKsBtnvVrBTrXnzCpUrETzZsmv3mreojl9evXiq6/m88nkiYBz7T/zcdgq99Q2kpmj/XLSBspXqEjTlEFvieJF6dP3UQ4dOkKThvXtlsPdytbxNqxXC0i m/veqLc5cfoCCxctwNvL06nwIUGV7Jb5O2 PQIeVvXv306lDW3bv2oWbpyd79 wh0WxGryl279pDl4f7pl0QvN/qRmRl7w0GSUkJ7N6zl0bNWvLYo/3w9PDg66/m8sLzL7Dqpx8pU7JEhv3Dr19HAQEB/mmfmUyu Pr6cPXqVYfbM7vd/jFV8m L12O1WlFK4ebmwbTp0 VR6AIUFxdHUlJyv6JpOgwGvd2/vTKdJ8WdkV/19EC58jRq2BCAs6dPMnPO1zzSvx uRiN16tRi9U r2bVrN43q17U7Hk3l7FjT1rj4dsaXInuFZhKc khy67Zt0x6FPn3qJAlJZupmczU31amTJ4iJi2XUm2/wzlv/S/s8KSmJa9eu4lukGY0bN D33/ gT6 e7Nm5i7h4M 3bt7WZbq06dWnWtBGDBjxFl27deOLxx6keXM3pPAH8 fuvzJo9h5OnTmM0GomNiaF6nYZZ9luxdAnjJ0xm4uTJVKtaOWeFlo57sUBiT4Tj4 2JZrGkmwhrqBuRgELn4U7KT4STJ8cGPVFGPa6BATbjtVotREZGUb54WYqXKE33rp356quvqFcnhCVLlvHK68NxM7ni6eFBREREtnGcPHGcmNh4GjZs4PTxZBdGrzdQv349ft wFbPFYreenAmfH78FcNQeW3R/yGaeHYW1xbeIn8027ihOZ9uzPSaTG40bNSR0xx6SLBaMer3T7T8/5bYNlCxVGoNOIyIi8s5ltgBld7wrly8lLjae75Yvp2i6yYCj8I7K3KeIP9WDq7J161Y6tm/N9u07GDhoEAu/ms JE6dwN k4f EyLVtm/2qu 61uhGM3o6OJjYmlbbv2aQPW90aP5q9Wbfjjj78Y GT veorL/rHVE2atWTUW2 glOLGjXB WrWKoUNeYcaXX9KyWdN8OwZh2wfvv8fy71cBYDK581Dn9vyQ8lhqdn/v3LMTNxeXAsvv/epO1FOJEiWIi40jPi4eV6MRg8GIf4B/2sKy9sajeeV2xpcie4VmEnzu7GkOHT7KS68NT/ss9XFeq9VqM5xSCk3TMX7iJGpWz3jlIzCwKJqmo0vXrrzz7gdcD7/BunXraNC4cdrALrt0XVxcmTVnHtu2hvLVV1/Ru1cvhgx9ncEvPu9Unv4LO8rrr4 g1yP9ePe90WgavPnGyCz7rVz2HeMnTGbSlCm0b9vaYRnZU7RRXS78tYci7j4QH58y2U2e8cYtX4OmcesuccpEWGdy4Vx8NIENbE AlLISExODh4cHAE8OGMDDPfswfvxH6IyudHmoE5qm4e7uTrSN35GqlN9M5DV79XS7tFzekXfUHu3l2VFY23m13cYvnztlN86Tx/8F7LdnZ h0OpQ1uZ6dbf/ZH4tz5Z7b nGGPmUxndstk4KgaRp6vR6z2ex0mOyOt269 pw89i9jRo/mq6/m4ePtlaPwtuh0etq0ac13K34iKjqK3Xv28 qIN9i7Yxtbtm7D3WClaImSVK1SCch63rib60bkD6PRBU3TMkwy3dzd8fX1Ifx61ruvfv7 aJDhzmxiYgIREZEEBgY63J5eXvSPqTw8PTPcDWrQoD779 1j1Q8/yiS4gDz7wov07N0XSO5nfYv40KdvP5t/p18UTdw5d6KeDAYDSql041kNY8pnkPvxaE7GMrczvhTZKzQLY/32yy/4 AVQv96tCVn5ChVxdzOxdetWm EeKFceVxcjp06epkKFChn pT7y0LptW9xcDXz/w/f8tWETPR/umfbYcXbpQnLDbNqsBXPnzeeZgU weOEiEpKSnMrTsbB/MVvh1VeHEBISQrVq1fD18cmwz 6d2/lw/EQmTp582xNggArVgzlY2g rSYdmMKQ85py8AJZ73y649emSvChW6mPRRgNJRj37inlTobrtxyaUUkRFReOe8vu7cuUr0qplM77//gf6P/YYHm5uaJoONzdXm69aSq2jv//e6fTxpJZz jAWi5ndu/cQVK1a2qqfjurJUfjsaJqGq6vt47HHmfZoK8/OhLXFVht3FKcz7dkRi8XM3r37qFS5Mga93qn2nx1ny93Z/W6nDdytNE3D39 PE8eP31Y8lSpX5ZsF3xB 9RLDR4wkyclJtTNl3v7BB7l66QJfz/ aIgGBPFC2LK1ateT3335l/S /0q5DBxlMCqe5e3hQqlRJ9u7Zk3bZ5Eb4da5dD6dc XJZ9i9dpiyBAX7s2HFrgbw9O3eSaLZQu3Yth9vTy4v 0ZbExETi4uIyrB8i7qwKFSrSsGFDGjZsSIMG9alcqbLdv3O7pou4PYWlnmyN7eztn5Ox5u2ML0X2CsVIw2Ixs27detq2b4 byZT2uZe3L08 8ThzvpyJhqJhg/rE3owmJmVVZwDfIv707duLr bOxmDQUb9eXeJiYoiIiqZnj 4pV2G96NqlM59Pn45vkQBat2phN92zZ06x/e9dBFWtSlJSIsf O46Prw86nc6pPJWvUAFNWfj88y/o1qUzBoOe6Js307ZbrRZmfDaD2vUbUKpEMY4cOQIkX6EqV74cbq6uOS5DHx8fSjzSjS2fL6SNtz/cjAOrBU3TMNZIXqwocdnq5EehDXo0Tw823bxOyaeewNs762qbqZSyEhcXl9bJa5qOF196CU8fP/r17Z22n7u7O1cjb6atlJeebxF/HnmkNzNnTAdloW6d2kRHRlKydFmqVsl BU8vb1 eePwxZs/8Ag9317QFdo4eO8lboz9Aw3E9OQpvi15vICioKj v/onaNUPQofD186dundoO68FRezx39rTNPDsKa4 tNu4oTmfac3buN3KpYvS4nixfh59WoO/RPGvP NQsNx 89pudeqWT1X 91OG7hb6fVG2rVvx8xZX/FVcBDVqwVx/txpLLm4c1qqdFk xTnnxyIF/OnsuQl190GMaZMi/7QHmqB1dl9uw5PPPcixj1etq0a8cnU6djtsKIt97NxZGL 5Veb6Rfv75MmvIpixbXpW7tGnz 2XR8/AJp26Y1ETeu07tXH1q2e5DR77yFi4srjz/xGJ99PptyZUtTLNCfSRMn0qBRE2pUr4Zep7O7Pb286B9T3QgPZ/fu3SQlJXLp0iVWLFvG5Wvh9Hy4Z/4UnBAiz9gbj0L2/a zY5lUtzO FNkrFJPgk8f/49 w44x4 70s2wa/ ho vr4sWryEzz bjsnkSrny5ahU8dbkaeSbb Pr58 KFcuZMf1TvLy96djpIbp374Y 5Y5v30f6sfjbpTzcq1faQhO20g2/fp25s2dz swZjEYXgqtXZ8KEjzCm3DlylKeg4BqMHv0us2bPYdGCrzEaXQgICOCBsmUAMJsTOXzkH25ERrF5419p6er1Bpat/J6a1XP3DH dls3ZdPkKG1b QguPIrhYFCopiZj3Jic//mw0oLkYSTLo2XTzOhE9O9C8WRO7cVqtVmJj4/BItxJrteo1 PDDGhn2c3d35 a5KzYffR7 xpt4 xZh2ZJv XTqJxTx8 d/b71tcxIM8MprQzG5ujJv9pdcux5OULVgZs76kjo1QwDH9eQovC2apmP4yJG8MfINXh3yCh6enrw2dLhTk2Cw3x4d5dleWEeya OO4tRrmlPfscxcXAzMmjmTc fPU75CRaZMnZa2UJGj9m LrXLP3CE4ux/kvg3czQY9 zw3bkTw5RcziIqKxsvbm5q1auHv75fjuEJq1uG1VwczZdrntGndmmpVKzoM46jM9XoDvXo9zL6D/9ApZXGP0mUeoEZIMPEW3W2tjSDuT08MeJq4 ARmz5xB I1IatSsxaxZX Lr7UXEjetZ qWnn3mO2Nh4pk/7hJjYeFq3act7772bdofI0fZUedU/Fi9enDVr1/Poo4 i1 vx8/OjRs1azJs/n8ayAJwQhZ69sZ3Fkv0kOCdjmVS3M74UWTl7M6RpaGjolmLFiuVLJr6Y8SnLVq7ml1/XYbqDj/4UVLr5yWq1si90K5dXrqF nJUyAYF4enqioXEz9ibnr19lp5uOYg93pWazJnKFSOSIxZJE3169aNSiLf8b8XpBZ6fAVK58exO1Y8eO5VFOhBBCCCEEwOXLl2nevHkzwOHpXRSNAAAgAElEQVTv/Ar8TrDFksT69b/QrkOHOzoRLah085tOp6Nuy ZE1a7JicNH2Pf3HuKvXQPAvWgA/l2a06R6sN1HoIUQQgghhBDiXlXgk Cwo/9w4uQZ3vug032R7p3i7e1N7SaNoUljxzsLIXJE7uQKIYQQQty9CsXj0EIIIYQQQgghRG7l5HFo UGoEEIIIYQQQoj7hkyChRBCCCGEEELcN3L0m BKlSrlVz6EEEIIIYQQQohcuXz5stP7yp1gIYQQQgghhBD3DZkECyGEEEIIIYS4bxT4K5KEEOJu8/rBn24r/NQa3fMoJ0IIIYQQIqfkTrAQQgghhBBCiPtGIZwEK8K3zmXctPWcsWaz2XqBP6e/zcfrLpHd5nxL1558y5PIEakHIYQQQghxL5Hxbb4ofJNgdZlV44YxfXc8RbLLneUka6ZNZcWBSNSdTNee/MrT/SBpG6NqBlJt AbibjeunNaDiubk1p/5/XBU4aw3W/nLXGbO7idEQbPznVNRu5n5dDPKF3HFaPKm3DM/EFkgmRQiH8l5 e4g9XR3uEvqKdv LSdj0HttfFtIFLpJsLq0mmWb3ejctx1e92q61sts/vRFOtcqjY rCa8SIXR8dSGHY/M74VxQ4Xz/XBDFvF0x6HQYTJ74P1CTtk 8zw9heZBhnTelqlSlamlf9LcfW84k7eTjvr15b/3VwnmSsJW/zGXm7H5CFDSb37kk/v7wcV7/qygvf/0roRvXMP 1Zne0DxCFjZkzy56ikslE0ynHM939MHN110LefaoDtcsF4Nd8Ev9acrI9q5sHZvJwWQ86zLqUrm0mcPLn8TzZvBIBHq54FK1C62e/YGeE7R5D3fyHle8/SetqJfB2NWLyKkaVJj159at93ISs5 X87mPzhfPlkm255mYMZDnP tE9qVnCEzev0tTrP4lNV2 lZ72ygYmP1qeMtytufhVpMWgGO8KlnhzVk7o0iw6uGpp2658x G12mcmXerrF3vf7lnujnmz0b/k5Bi3s49tCopAtjGXlwo/LCPXozHdt7 Tw5w6nq5lIiDPS JXPGFbRnfDd3zB29LM8VqQGu8fULmSVksS1M6eIqDeK3z7qgEt8JJf/28LCSZN4pOMV1h78gg6etxG9vjovrwjl5TzL733A2TKTshV3C tpNm8 TZk 8xnaownGgs6PKGCKq7 8TpdX/yLBTcu0LY79M/rSY9x5Gj/zHKNmj6Z82UqU1Tu7PSPLjQOsnPY o6eu5liMnjbpN0ZvZNLIhUR0G8bMtx5A/bOEMaNfpbehMv982QGPzLmO2MioDt2ZdKwMPV54m5lNyuIafZHjB7dwKErhCtmcl/O5j80PTpSL3XLN8RgoiUOT 9J3SjR9Jizm4xJhzP3fu/R8wofd616gvApjRr8ejIt4lM9Wz6FG4jamDhlOl4Ee7F31NGUy3e6RerpVT9boKG7q6zDy57k8VjK5oDTXYlQxACqP6ymtHux9v2 5Z rJVv WeIfzIXKtaWhoqMp3ljPq87buqvjTa9TN1M/i/lVLh3dWwUXdlYtbgKraup2q5WtSDSccVebUfRJPqTWj 6rGlQKUh1sRVb750 qLnRHKqmLUmqeLKpfaY9SBtJ2t6vzMdsrV7zH1fZSNdK1Rau/sZ1XzCkWUyeCivEpUV499fVJZnM6TWf37ZS8VVMxLmQxG5Vm8hur2zlp1Li0PmVivqLmdTMq1xyIVmYfFmSesl9SsB03Ktc9SFZvu45vL ykvY2015oBZOTxee VpPqDG1HZVVd/8WyWlRm6 qP6c LhqXM5XuZo8VEDFVmrslvisebvdekj4Q71UUqeAlH uqvd3MY7DpWc5p74f1lHVr1xceZsMyuheVAW1fU59tuXqrfbiKD7LRbX23V6qaVAJ5W0yKhfvsuqRb84ri638ZS4zZ/dTSinzefXbh/1Vw7LeymTyUQ80fFR99MeFW98ly1m14tX2qk6l4srH1aAMrr7qgcZPqGnbbiirk03mfjD0wI 39e e5aj92G2rxnSfG5O/x47OxeKelBT2pepcKkQN XmderOam2oy b 0Oo/ZPFwFl mh5v6XkG1YR9szMqtjU9qosg2eVB vna0e93dV7b 8mOFcl5iQmO6vm r7R32Vsdb7an W/iBGbRpaWRk8GqsxO6PtJJnpvOxUH1v42C8Xx WagaMxUPwf6uUyLqrK8C0qdSQQtWaQKukSpN78O0mZD45VdUwl1fO/3CrBqFVPqkBTYzUpLHP5ST2lb79JO99SQR7d1cIIJyK7zXpKZe/7fUsB1lNqP1axmPJ2NSiDq5 q0nGE vzLUapfk0oqwN1VeZaopfpM3KyupzZqh PcbPo3m2NQVTjGt3ep0NBQBTR1ZnJbqB6Htp5dxfLtPnTp2yb5CquK5NdhD/Hk3Ms0fWcRP6 ez1ttfIhLSH9zP4bQtx/ikXk36fTRD2z882ueL/I7Qx8ewfood5p3aoXb0b/YdCH1YYsoNv xC0OzjrTwzD5dy6GpPD3kZ3yeXcCGv7ex/qtRPFG/RHJhOZUnHcWaPs EResJ3fYXi16vyMFJTzFyVUTWxxIsURz/dQYLd/nyYM/mFLYLiVlYE4g4tZk5i7aQ9EBLWlTQ4 h47ZZnFnHsHNuFbuMOUPmVOaz 5Se HvcybStkujeUZ/VgpPaItew/eJCDB3cztbObk FS8xHOwT83cD74dRauXs abz kp8svjOjYhfF7E5zLh7rKztVrOFFpCAvW/sFvyz/j1ZbFUsonu/xlx5n94tjx3kN0n3CUkJELWbfuG4YHH2Z8t66M3Rmfcjw3OLxpM5dDhrNoza sWzqJnvp1jOg7kl ibSQtRCqn2o ttqqj/DNL2HfwIAcP7mXJM UhR cOcU9IPMiUp98ncvBCJnUIIMN9InWVlR/P5aThHHO7lse/SFGqtHiaaVuupZ1L7W7PQk lob9z8u8FjGhXCpds9jC6pOt7rOFcvJyIR8XKlMrcCGP/ZN6iEwQ88g7D6t9GT55tH1v42C8Xx WaxokxkOXEdnZc9qZZu3qYUj7zatGexoaTbN9xEXNUBJHKG78it/LkUbMOVdQ/HDxqzhiZ1FOG9mu9fpVwo564i cIj7fz4Gwe1JMV7H /0yvIekrtx2q9ydL1f/DLt28R8u80hrz5G76PTWDx6lV88agHv48awAehybdzHY9zs/ZvyTnJpj8sLOPb 0AhevLWyulVy9nh25U3W7kDoK7/yIyF52k49ldmDamQ3JhaFmH/12vZkhJKha/ik9nnefDzjbzXJ/kLVefz06yvPJbloTPo1KYrLY0vs/a3a7w8qChazCbWbjTT5IN2 GnZp2u9doVrqggdWrWhcR0PoG5aLp3JE2j41OhIjxrJf9WvU4RDy rx9fajmHs3TnsU4saihyk78EduWo1UePwbvnnigUI7uEtY RhehsfAasWiFJpHCIOXvU0rD3B0vNgpzywiVjP5s8OEjNrHV8ODbDbQvKwHt JVCAmpmKHsnQl3i4Z3tTY81KEBBuDBjrXQGjTj00/W89rCHng5lQ8dPiHt6dK2wa1jTrSRPxu/bXO0n7rxE5O/OErNUfuY/UoQeqBNi8pEH6rL5ClrGPZdH3xSjscrqBWd2jXAQBtalzrFb00XsXZPEp1ayYOqwhE77adJ8h7Zt1UNl8CKVA8JSfsOJB3MwblD3AOSOPLpS3zC6/wxvDau2q6MmxP/5s8tsZTp8AQjX2xBRc9wtkwdwvBuA/Dct5pniznYXjabHlanc7LfTSRs3mDG7anHqE198M80erec/4d/Iw3UbFw/y2PSzrDfxxZmNsrFiXJ1dgxkvXKJqwRSomi6CYxbCUr6K45evIKuWlMaeX/G8hnLGDijP1Xd47lw4jwxKomExIxDe6mnjPUUH6fD32c7b9R5gBcsRajeZTCTpr9L5zK3Rl95VU9WinPU3vc7nYKvJw2vKs1o36oBBppR5r V/DwpmJ7P9 ZBF6ApbFrcg9DQE1haBNmdN6TGl7l/szXGU9cK0/j23lZ45lzWk/ywfCd XfvQMnkuivnYAf5JLEOTpmVtZtQcto DMdGseaY0bq6uuLq64l55OKGJ0Vy8GAUBnenbRk/oT79wXUHs5p/4La45fbuXTI4zm3SNTV/gjXYRfPpgDdo N4Hle6 Sei3RmTxBAid fJdHmlWjTIAv/mW78nmYmYT4 Ax7 XT7lK3bN/DTl6/wwB9P0 qZ77lUSC/FuHSYyI59 9i3fw/b/1jG5EeMLOzTitd i0A5OF575ZlZ0tFd7I0pQ4tWFe1eocnLesi7cClca9OxdXGi9u7imDkP4ssj5n93sz82uWzTuihDZVq1KEXMvl2E2agUfblKlNNd51q4LMwvcu522k9Ozh3i7mc9v5i3Jkfw9OQhhGRz 1BFXuTiTT3Vuz9Lr1b1qFWvAy/PeJ8ulj9Y/NN5LA625/4MFseROY/y4IgT9FiwlGE1ssucQgGaLnOPZGbfh80p22g0O 00Xvt9bGHlRLnY4fwYSKFs3zNEK/IwH3/9GqV H0Q1XxcMLt4E953LYWsAxQMz3fmTespQT949Z3Hk1AVuRF8n7Jex1AmbTJ/ekziYrgzyqp4cfb8zRlWY6klPidIl0G5e5Wrq2lqG4pQqBlERyas152VfVajHt/eYQjMJthz/geW7A jWtyVpD3JqGqBQVjtNVinQleCxr3axb9lH8HOHTkAHP6 KFpATzUvwP6v5az9upNNq34mdjW/eleXLOdrqkGQ37 l8M/jKDWuXkMalCNNh/tSl5 3Yk8WQ5Nod jn3Gm3v/4en0oG3 aTO8Hsha1zqcsNeq3pNvzk1kxuTPhS6ez/GzhnGho3mUIDgkhpEZtGrXty7DZs3m53AkWLthIrKPjtVeemSmrcyeovKqHbM7Xztaf3ezpdMlt83bjs92f5GI/latOWjMYMWDFUjibpijksrQfZ9s05OzcIe5yimvrvuOXq0eZ2roIrq6uuHo24 N/49nxVnUCn/qRRBcXjJqViPCIWxNaj9KU9YdrV66jHGzP3SkskbC5j/LgiP/ouvhXZnTL/nF8fclKlHe38MQyRk2pZ08xqXr0aTaOcEbK PzRxf4eBcudjj7BhIV7QERbnCpSvpHm Kv8SFcI2iJYqiQ0epLh z8Ww4l0 EcfzCdXa8HYzOswFNamS8nC71ZKOeDL5UavMyMz/qjdv H1hz7FZZ5009BRLu4PudvvwKWz0ZXYxoyoIldcypueBi1LBaU8asue2rsusPC/n49l5SSI7cwn/fL2dfYHf6NndN 9RQtR613M7w52//2FxEzVC5JsGmK w/ZqFCUBBBaf qUNpHD2j4dx1Ad/cNLFqwgEVrzHQe0JOimu10AdA8qdThZaau28v6oUX5e8Y8tiY6l6f4g7s4ZG3Oi 8PoF39EELq1Keyn/2i1jQNTSWRlORkkRW0xCgiYxVGk4lEZ47XRnlmZqhci qms2zeeNzuVbQ8qQfNDXc3iLwRmWFwlJv6y8BynK3bLuJWvSYVDbcRn4385Xa/5DI7y aNJ249KW0 xqbQ87jXqpe8GqQQ cnZNp0hjHPnDnG30/DvO4f9Rw6xP/WC9u7FDCpvotbrq9kyoR0untUIKac4sGUHUSmhrFcPc iykYqVy6B3tD0XuYreNIpew47SeeF6pnctaTsOj7Y82iOQC0smMO/fPGig6frYQjJQy8DpcnGSvTGQvkJjGhWLYstfe9MmMDdDf2d7UnkaN0o3qdO5E/hABUrErOLdqbsp fiLdCmSaSYg9WSX1d5NJ26nnkoS6Oj7nT6yu7GectpX2egPC/X49h5TOIa9ljBWLt9PsR4TaZZuLqoV6cHIV4JpO6E3/RnN8y3LYrq5lbCbt76kWkBPhj7zEZ0/7sfjhlE83awsppizHA6vyMAnm CtAV4dGNQvkPajR2IMeIpVD/kmXyCxka7l BpmbbASUrMMHoln2XDkBvgF4KdzLk moBpUVp8xZ9xCSvULIdBwnlOR6U4s8TuYM34b7g1rUNrLSvi/vzPzg9XQ5GO6liucjdF69R 2hIbikhhD LkD/DpvGnMvVWLwE83w8tlm93jtlWdmWkBPXn/2Izp 0Jun1Ds82bgkxohTxJTvS49a7rf2y4t6MFShbk1Xpi ZwIxGL1FDneZqYHd6OwqXhYVzP01mfOX NC4DR5eMZfz 8gya9BA gDnH8dnPX7 GudtPK9KdEYODaDu Py94juWJ6oqDC97lo8PBDJ3RNeX3wELkI2fbdIqcnDvE3U/vU4aq6U9E5pv4u2i4Fq1AlZKeaNRlwHONmPH2Wwz wpfhjZL4c8w4NhZ9lFXd/NAMvna3c 0HBjV8hm3dlvH3p 0dv4faeoaFY2dyofkYBpS9zIF9l5M/11wpViWIEunXH9R86frhNPpvfpKhrVqzb gLdK1bBk9rONsPRjp8CsdeH5uzh4zvgJyUS3YcjIHUtR94Jn09mVrw0uC6LBj3EkMqfUj/EseYO/Jb4lp/wnP1DIAi8vQBjp44xaHN3zNrxhJOVH2HH8e3y1rHUk 36snlOCsnLSciqC4V/XREhv3Bl OWEV93LN0r6/O8nvQ6R9/vdO6yespVX2WrP2xSmMa3AvL5FUnmgx oOqZy6tWN2bwGx3xJbfzkadWqcoByM iVi2egqlCngxr Y7rl9hPPqHUfPKoaV/BTbgaDcvMvrxq9sFSdTbfmuvnQOFXPxahqvLc37XUxttKN2/Khalc1ULkbdErv5q8qNR oZvwdcSs9h3mKVntnP6taVPRTrnq9Mrr5qGLla6puU/epJKWU9cp69W7X qq8v5syGEzKp3RN1enlL9S2q4XwJTTW62rlM1VUUU8XpdM0pTO6Kd SVVWTHkPU9A3nU8rS/vHaLc/sXuOTeEatH9dfNSrnq1wNLsqrRE01cPHZrEvo32Y9KKVUQtgi9ULTssrbxaDcAoLUw18cVmYnwt3KwwE1praL8q/dTrWo5KdMRndVLKSLemPlf pWq3IQX3ZlYC9/2ezv7H7KfE79Oq6falDGW5lM3qpsw/5q/O/pXpGUXZiIhaq7q5t6ZEU238/7lLwiyQYn2o/TbVU5cS4W97akneqtzK9QMZ9Xv37QR9Ut5aVcTD6qfIsX1fwDN2 FsbPdevV7NbCcr6r66m8qKnNaCT rpzO/yid jRpQREv3mpGUf4Zg9fauLL1BcvKXQtUXr3ZT9cr5KXejQbl4 Ksy1Rqrh179Th03q2xe6eJMH1vI5KRcsilXR2OgbOvJfFatfbe7CinqrkweJVSdRyaoDZdTW0W8WvVEEeVWpLSq3qqfGjFzgzrr4A1ZUk9JSiXuU1883kIFFfNURoOL8ioerNoOmqL upg8Isj7esoku 93JgVST9n0R/ErHlFupofU/NR3IpmPqA/ruapKI7aqRJWLcW6K7MegqnCMb 9SOXlFkrO/zmoaGhq6pVmzZjmbOjvFwoEx9Wj4TRt OzqVFnfsUlpBpSvuKZaDjK3fkG87beLQRw0KyaMVIr 9fvCn2wo/tUb3PMqJEEIIIYQA2LJlC82bN28GbHW0b8E/VGY yIqVRyndsw N7uREtKDSFUIIIYQQQghRYAr8xpX5wApWhpWh55cN7 jvKQoqXSHE3U/u5AohhBBC3L0KwePQQgghhBBCCCFE7t1dj0MLIYQQQgghhBB3iEyChRBCCCGEEELcN3L0m ArfcvnVz6EEEIIIYQQQojcGbrI6V3lTrAQQgghhBBCiPuGTIKFEEIIIYQQQtw3CvwVSUIIcbfZ0HfibYVvvfx/eZQTIYQQQgiRU3InWAghhBBCCCHEfeP mARrJTE9/hlebctn//fdRCuGy0Mjca8TWNA5EUIUdnLuE0IIIYTI4v6YBOv8MTZ4EGNRj z/zm aB/qqbXEp43n7cenK4NLlGUwPeN1 XEKIe5uc 4QoXPR18ZiyB/8BjdEKOi9CCHEfuz8mwQVNXwv34TPxqO1f0DkRQog7R859Itf06Jt gv SMIp0eyDLNl3Fh/EYsgi/L/YQ MEL6LOMZuyFT6EFYHzoQ3wnbyPw2zAC5/yC76CHMZhymp90XCthemQqRab9TeC3xwhcuAv/D2fj1TY4edKrbmK9cBzz9aiUPPhievEPAhb8S9FlJyi65DABM9fjpQTCXcnCgnIYQQuSELYwkhhBCiENHQ1X4Pn0FN0BJVpm2uGDp9jk f4iT98R0xs6ZhuXYaq9XZ8OklormYSVr/PrGX4tBV6I17v4l4x/xL NIjOY/PoxGe787FvcQFEn77nOiwCyjXougfqI/BTUMBWMOIm9KXuLRABnQBpdFOzCDi21CU0Qtd8fq49ngBn3f9iRj2LonxzpabEEIIZxWOSbChKV5fzMew kFurD6d/FnRQRSZ9hzm8S2JPuyPaeBkPOpWQe9fBI1YLCf/JO6b0cSGRQF69B1m4NuvBTpPE0QfJ/GPCUQv25CpY7RDVwyXnqPw6NAGg4/Cevov4hZ/SOyhK n2CcSl29t4dGyLwdeACj9I3GdPEfOvxYn0DRif2kDRpwASSJhah8itcaAvhUvvt/Fo0QSDnw7riV J/foD4o5HJwczlsf06Ht4tGyE3i0e67EjKI UzlQIcXeTc5 c 0RWJR7F 6XGJH3xJuqpLzGm26QFDcO7p4XYUT2Ju5yU4/AZqCgSV40mMfXvw4fQanTC84EqaBy51dacis8NY98JuJc RszoJ4g5Hptu2 Jb/9VVxWPij7jue4Triw/c jz6BElhe5PTPLyJxJjyBAyti7GonsQzFltHIIQQIpcKxyTYEc0HQ3ADdGcmEzX7EMr0AC493sBz2NuYX3 TxDgr1n XcHP6XCwxGvqQ5/Ds/wmep1oTtT3KiQRcMfabj09nRcK3rxNzTkPfahieb85De78PMf8lJO/T9yt8uhhJWP4mMccjoUgR1GUzoJxI34z5pxeI2ngBUKir8YA7xsfm49PsPLFfP090uC8uD4/Fc QoLK /SWK8Fy4D5 PdPJr4717n5rkkdFX74lFZBoJC3Bfk3CfnvvuNoSruLw9FWz Qm/v1ZPj1uuaHqUd/9JZTuL61GQ9fI rsn8QtHk/s0RuOw9uj80RfcwCuFaNIXLDzVjtzNj5TE9xalsG69QNiM0yAc0hzQQuohVvL nB1PUmXZQIshBD54e6YBAOgUBd2kHDwALCNxPDSuHz4MKbyBhKPmFFnNpFwJnlP88lIDE1X41q5Imzf6zhqj/a4d6yI fuHiFp/PPmzf06hK7MG925tiZ26DuXRDvfOVZL3WX08a 6cSF9FnMR85vStQJ4P4t6hOIlz xGzPbkDN88themz13Ct9h6Jxzrg1rI45qVPEb0uJfIjURjatLF9ZVsIcY Rcx8g5777ggHDQ NwZx4Rq4 gqJFpc21cqrphPbCK2F93Yon3wdh1DJ5vTkGNeJa4azr74W3QWs4iYHAHNM2MZfNwojafdy4/6flVQu9uwRx2IFcXarRGnxK49FPQdKBpkBBG3Cefk5iQi8hE3jB5ohlSfmyuklAWvf2/Y Oyj0fkL6knkUt30SQ4k6unsSpfNE8d4IK wRA8e3TGWLIomCPAVQ9h2a5ukVWpGhhMF0k4km6QZjlJ4j XcK9bE4N HUmlambdJ00u0y8ZjMHkgf6l7QS mPqhDs1gRfl6QokgDIaLJPx73l4sQoj7iZz7xL3Kryce3b2Jn/QNZjOgz7TdPRCdqwXzru9IOJJ8t9U8bxou9Sdjql MuL b2Q9vg9o1hhtvz0NfvgNuj3yM70tJ3Ph8PdYiDvKTQcpazyrz7xD0GHp9h2 DrUS M5UkGzNkdWAiNxZsBAxo3uUwtnwZj FLYeLDRB9w5qkOkbdccHl2M76tfZP/TFpPzLbGeLS09fdaIgcMJsHGE/oiv0g9idwrHJNgZQUroM9BdixJKHRoOqDsc/gMHYD6YyxR8w9gVRVwGzwdJ4eB4NSLCuzs40z6ti4NqyvEfzGAmBPpH3myom5EQumUdDV5kYIQ9yQ598m5T6TQ0NXphot3RXh/P24pn2kGAzz KwHlXuH6Vylt39MbSHnkOP4ilmhw8fFzHP6z37JvjrEXMB /gPn4TpLiy D/8kBM3/1GQq0cxHfjNJYEHcZyVdHYliEdzc0PzdvBg9lxF7CcCUsJd4Skf86iq/I9bq0acfOAjXyLfJSEedVz3NhgSFnVOxxLlDeJf9r6 3ryhRJxh0k9idwrJJPgcKyRGvpSD6BxPMcne61sDfTaTqKXrSTxpgLtJuab1qwDwcwDqtS/zx/EnDgAY3BZCDuR/Jm PMag4nDqIGYLcPEfzEkDMAY/AGEZHwl0mL6KRyWC5pnp/ZYXj2JOehpDCT3WzWFZj/v8QcyJA3GpWQkt7Kh0gkLca TcJ c kUJh3fYm4Ufdb32kq4L7/6Zi3P4skT/vQcVXwnJFw7VqHbT165LbhXcVDD5mLBcvYN3lILxTuVCgGdD0TuQnfcCErSTsDMe1 Uu4rttF3IXbvNVk8EJzAWVOdLyvyAcK6/ldWDM9jGI5Z/9vcadJPYncKxyTYOtxEnaG4d7zf3idMhF/OgKKVkXn5E0Adf5fLNoA3Ho/jHVrGFZLMfTu6QJbI7BGa hDHsKlxEkSL2X6LvxK4/jm vz/CK/4SEsxr6VsPxKHOM2Hl/Jnd00b8S 8fL PaZiTcziD92GTxKo11ZS4LD9E9iPp2Ae7OXcD 2CDOl0EX9TnzYr8T9 TI 3WfgbZlB3L8XwFQCvecZ4jftQcX8Ruz6Y/g /CXeTCPunwvgWg Dq9wdEeKeIOc OfeJW2IvYkm/ppTeHWVWqMizWG7EAoeJ 30fbo 9gVfHKGKPGXDpO7woZrYAACAASURBVARj1E9E7o6AWGU/vFdHvCdMxLhrMOHzt6CMtXHrVRf1379Y4jR0JZvj1qc9hI0n4aoVrI7yk46KImHJWOKrTcVr7HcY1nxL4smLKM0HY1kvx89ceFfCGFQfZXBH5x ES9tBuPmeJnbTLrkIJIQQ aBwTIKxYP7xVaK9xuLR xNcPfSomCtYjm3DHOHEez5OziJqXjG8er6Lz0NeaOZYrBEnSLoUmbxdnSN 5VxcnnsUz/a/Eb5wb6a/95C0dBCRCaPw6DkNV2 wnv6LmInjiP0v9QV9MSQteorI6LfwePADfPq7QdRxEhZsISHUUfo3SFj8HnGDR Ix/EGIO03id/uJDztG4oIniYx6E4827 HT1xNiL2LePpGETaCIJ2npACKi38Dzwffw6eMNSZFYL/5NwrnofKkJIcSdJOc OfcJ51mwrH2FSNNoPHvNooiXFet/PxE9YTyJMU5OFdM/FeHmja58T1w7VkbvrkNFnCBp1xgili7G4uwrxtK7/jNRb18mqdeLuD34Dq5 nmCORl07ReKufVizzaIZ6/XzqKaD8R37GlgTUFEXMP 3nuhxM4k7EpOLjAghhHDE2cvqTUNDQ7dUnvZEvmZGCCHuBhv6Tryt8K2X/y PciKEEEIIIQCODV1E8 bNmwFbHe2ruwP5EUIIIYQQQgghCoVC8ji0EELcPeROrhBCCCHE3UvuBAshhBBCCCGEuG/IJFgIIYQQQgghxH1DJsFCCCGEEEIIIe4bOfpNcNHlJ/MrH0IIIYQQQgghRK4c27LF6X3lTrAQQgghhBBCiPuGTIKFEEIIIYQQQtw35BVJQgiRQ68f/Om2wk t0T2PciKEEEIIIXJK7gQLIYQQQgghhLhvFMJJsCJ861zGTVvPGWs2m60X HP623y87hLZbc63dO3JtzyJHJF6EEIIIYQQuaWuETrzTcasOIElt3E4Mx4t6DFrQadfCBS SbC6zKpxw5i O54i2eXOcpI106ay4kAk6k6ma09 5el kLSNUTUDqTZ8A3G3G1dO60FFc3Lrz/x OKpw1put/GUuM2f3E6Kg2fnOqajdzHy6GeWLuGI0eVPumR ILJBMCpGP5Lx8d5B6ujvkRz1ZL/Ln7E9Zsvt69mNDZ9J0Zjxa0HOHzOnfh22 0E2C1aXVLNvsRue 7fC6h9NVl2bRwVVD0279Mwb/v737jq/p/OMA/rm5K3tJQmQQEgliqxUxq2oErVFFqdHWbim/VlXtUaW7tUuFqr0VNSupXSF2a1M7IhFZ997v748QSdybe0NC9H7er1deL697zn3Os5zzfM9zznM/wQHdMzh4XkgcVrwTgqLOtlDZ2ECldUSREhXRqMsorDx9/ nTt3GGT5lgBPu6Qvn0qeVN n580b4tPtt4s3AGwabyl7POLN2P6Hkz X8uHfvGd8ag7V7oO28zonauw9z3w57uXCy3saSLDxzUNrCxsYHa1gXFytTGa4NmYPeNB/f35TpmNrXNdh7O NOg5uenMmcB5N4JLB/VBfXLesNZq4atiy8qNO6KcRuvZN5Bl8TjWDa6KxqWKw5nWy0cPANRq 1Q/LT/VsY EodF7dygLj0YUWmPZzct kMEaoqi29pE8/kyVza5g7Xd/aD27IBfb2avaV3sOFS3dUXT6ecLzd1/SYjBnL4vI9jDDlp7D5Rp2BuzDmW5UaK/go0j26CityPsnHxRreNk/JG1XOa255SP6SWveBPO6gD0 T3ByFYdjn9eG/baevjm/IPaznleLuhrbIHQ4eKSrgjUalFn6pkH/SgV59ZPwFt1A HhYAsHrzJo0OtH7I9/vN7uHZmG1/wd0GTGtVyvveb6hdl k4XVtJPhOnZ90xvNKvnCxVYLJ 9QNB0YiWMPsqj/Zwpqa3KeVxRQKOzQbnHGTnmp16yMt6vl/QJ4Qdrpvzq2 q WKxeFbGEsA/5dvQRRDs3wa6NnGQI/MaEhNwT1kFQ9fPRqfiGfciFLZFUaaQtQiQjlsXzyO 2nD8PrEJNCl3cf2faEROnowOTW9gQ yPaOL4FMkry6Pvsij0zbf8WgFL64x1Sy8KwwXs2nUBfu3m4oPWtaHOl0R1iL95G7pan2Lj583gkJaA66e3Y9aEgWi87QK27J6AOnYZe2rqjcS68S/DLvO7NnAK8IcSgMTvxPAmrTD5bz 0fncYfqxdEo4p13B89zbEJamhACC3t2Jokzb4 kIQ3uj/Gd6rWhyqW0ex8adv0bveKuyK3IE57XzQvFNzuK5ejl jJ6BuQ9sseU3FniUrcNGrDX5s7ATgvpl8JZgtW4tRI9B41UBM/O4vvD6mGjQAIDexYvx3OF7uA0R1L1k47oJLHNYMaIH e pj8sIo1He9hNWj qFfKx18js1Gc d0HJ3SHu2nJqLdpIX4wvs0Zn80Am26uODgb 8hwMbc9pwHzM/0DLh55SpSdRcwd9i36NvgU1TI0nnl6q/49It9SDaUwbWbBqCkjZHzcgFfY/Od4OamQWgxcDtS7RSPPk7ciclDIxEfMRjThpWAnFiE0SMHoq0qCCemN4EDAP2dI1j 9SiM/Got/k5SomGuhzHTL5zM9ZusiVlROym0SE1Wo1b/7zC4tD3iDv6MMSN7oZNbBRwcXRkq386YHVUXiZl3wHQ4G9kHvZb64pXqWgv Pz5 yFzb1YJ 8cgL0k7/1bHVf7Vc aBOVFSUFDj9Rfmhkb0U675O7j38LPmULP6wmZTzsheNnYcEN2gslVy1UmPSSdE93CftvKwb2V5qBXqIg52bBNTtLj/ujxeDJMm67l6iqTxajmTubJAr0xqLrXsnWZFg4riGBDk0s5fULeUmWpVGnLzLS6d550RvcZ50cmr66xJS1Em0KrU4FqsgEZ9ukMuZeRBJ3z9MQhxaSWR8QVVmPjFckxmvaMW23WK5n Xje0vfECd1ZRl9RCdmy5tbfeqOyOjKthL88T5Jf5i47qps 7yz1CrpKrZaB/EoXV/GRKc8nrenbYfUrdKnuI0AePBnK21/TTL/vaz0l2XF4KZSPaiYOGtVorb3kpBG78h30Tcf9Rdz6emvyoYRr0udEG9x1qpF4 wvHX6 InpT ctZZ5buJyKiuyK/j 8oNfydRat1kRI13pSJW/999H9Jf0mWDXxZqgQWExdblahsXaVErS7y9e47YrCwy1iDD46sfqq//yxz/SfXvqrO8rk64/ xuXNxbh6eu9oslMQsH9/b K74qLzlvd9TTe7zSJL88UGQqJzqyNgDxvcQuSfb pcSlUt9mXz4fvZNqX/LjBaeoiraSZbdMogkrpPuxVTi8 6mbOdTSd4qff3UUnLgTknJJe95KpukyuGx1cXOtanMOJdRY0lRQ6SstpT0/f2u6Xp71lK3SG9vW6n75dnMdk3/61MJ1YbIsP3pIilbpa fRsp8GC0PrwIJ63pIcU2IfLzPgu055Wt66bLv42DR JaRQKei0nHprSznyRTZ81FZsSsdIoFaD mxITXj45znZYuusYVH unp0swnVAas/00 Lmsntaf8k9luaalpWfa8JyvedBV1pVFyWCciopO/pzYU/5feki82zJTORWzl5elXTV9XzPULc9uz59rq2imT4YbMflUrtq0XiLH/9fqz0 QVNw9pOedCRj3mqV5FLGnX3PtFVoWknXRHZHRljTj4BUtpD3vR5LyOGRtbWRKrPFU8I08/PjN3/MfKZcFYWH9Ndk7tJnVLu4utWi327v5SIby9fHPQWF95NqKiogRAHUuC20JxI/ghw6VVWLrHBS3aN8y4OyR3sXlwc7w1 zrqfLoA69fOxbCGLkhOzfoYRRKiPmmODnPu4dWJK7Fz2zy867YFH7w2BBsT7FH31fqwO7kdf/z78LZXAnZtPQBVWFOEOxo/rv7oV g YD1ces3Hjn27sfGn4ehS3TujsizKkw2K1nkXkxZsRNTu7VgwqDRiJ3fF0FXxmY IGG7fRJxaieSrlxGXUigfxjXOkIr487swa0E00kvUQ3gpJcyVN9f6fEwy9o9pgYhxRxDUfxbWblqDeeP6olGpHHND dQOgBqVh2zA4dhYxMYexFfN7Cz83sN8xCF22w5cKTcIkWs3Yt0v49FGswlDmrbAhEOpluVDbmL/2nU4GzgA8zdsxe9Lv8PAekUf1I x/BljyX7J2PtZc7SadBKhQyPx228/48NyxzAhoiXG7E95UJ47OPbHLlwP/RAL1m3Gb4sno43yNwxpPxSbEk0cmughi/qPqb5qg4CeixATG4vY2ENY1DMAyNO5wzJad3c44j7u37fgvHt/G YsOAevjp9hcDUT0wf3t2Heoovw7jQC/Svm H nCUT3z3qg9O3VmLfuNsSxMbq298WNNYuxPenRbsl/LMaq64F4863a0D550XKUTYOKg75CX 8dGPnRUlxLjcU3g6fhbtvJGNnYyHTO86L0R2CAAsc3/4YzaQCgx5V9 3G5SC3UDlJBf3YP9l53Rljjapl14xT MmqpzmHP3qtIN7M95yPf ZueAbdv3IZNhfcxtZcL1kyajmMPXmmSa4sxcdYttPxsJF72SMKNG0mwiNFrbCGRFoup3Ufhbr9ITG7iAUWOzWpNluu0IQ5Xr6fBoXQQfGwAQInAD7bg3L75GNLYJ PJhNyY6Rdmt2djZe30kD4BZzZ/j8gDrnilTV08dgaTO1g/Zhz 8O HMW/5Z5xX81SvgCXtmnu/yKpwtZN9SDuMnrcGG5d/iXaajabHQZaMR586nsHTjc8sOn5O5sbCydg/ujmajdiD4r1 wKrNm7D8y2bAno3Ye/GJlxQrlJ7BTLBezn4dLnbF35GNSRmfGG7 LBGOtlL3yzOP7vynRcmgANvMOxeG2wvkNWcXaRN5M/NOiP7it1Jf6yHd16eI4cbPEuHkIM3nXM/Yfm NdPV0kCbTLz9I8/Hjpm3rJ76acjI0OnM OpMleXqM7piMq2YrgUN2y8P7YXdXvitlS3iLq62NKNRFJLTNZ7Lh4vO7c2LSg7tqCoVSlEqlKBUKASAKh1Dpv/6a8RmZHOXNrT4fu/N0Z7F0cNNKzUknJLfayJd2SN0qfYprs93JNspI 5nMv4hI8j4ZFqoWjy6rJCHn/sbSM5ZGbvkzOhNsfj9D3K/SzjWjbjPrJ/2YjK uFbc3lkq8ibykH/hEymn8ZcCOx0pvtTgTbIK5/mNpn34g13OHOdlmSw2iS74jFw tllFNiorKu7Msv2nI3AeZM9AZfzZF35FNqSK605Olllorr8y8ZvJO 8N9mv90y/g 95fJG44qCf4oo2zpB4dLebWndF7x8DGgRFn7djHRVp8gxzOfnsk9XxaVLSMhubOpt5TS EmzdmHi6tlK5l20aB79mbp36HtpXcJWXMu2kF69XpVSxerI8B0Z9Zm2Y4D4a8rKJwey9Iy07dLfTyPlPjkg981sz3kdyd/07kpka1tx7rxK7l cLq 4 EqvDQkiki6HR1cRu/KfyP6kg/JpeTupOfm08dmWJ7nGPhdpcmxymHiFfS6xqSKSvl G5ZgJfiRVTs2MEG/XcPniSOrjSaWul 7mZoIl935hyfZHrKmdMsRFthFHpUKg0EipLovkvJEBlf6fryTc3ks6LrmZrc4sr9cczLarmX5RWNrJ2HXs4HAp//A6lnNsZUmskg/xzNOMzywaM5sai2bWS46xa/xSecNNI5VHxsjD1jRcnyVNtU7SaaWRpzefkRdzJthwDiuX7od7y3aoZ5/xke7vIziR5ofadfxNZlR3OgaxSYlY19MXdra2sLW1hX3Qh4hKS8TVqwmARzO0b6hE1JpNuC3A/V1r8HtyXbRvVTwjTSPHVdd5D/9rHI9vXqmARu9MwtJDN/FwvSpL8gSk4uzqEegQVhZ Hq4o4t8SP5zWITUlJXMP5zYzcPz8v7iTeBunN41BldNT0K7tZMQWtoWxHtA0 Rx7Y2IQc/gv7Nm6BFM6qBHZrj7e/z0eYqa8udVnTuknD BQkh/C65fO9YX1/GqH/P3eA7aV0bRBMSQcOoC/dfmQXj7RnTqIw/cz6jbzXqgqCPXDfZAUcwCnTTSKsmQgStrcxq24wrKMDr1Inqb/5OXcYUrKqs5wUthAZecG/6ptMT3pdczY8CNe83g0j6VtOAHRhw7h0IO/v7aOQG01ABEIAIUi90ulZc/yZOylqtQNb1dPxLrIdbglgNzZgMg1iQh7uxOCc0xSmMyXxWVTwLXJOHzTRYHNK46j5tiv0cWv8Fz2MxiQcOkkLuhD0aFnC5TSCGySYrHy5y24oAMAgTw255iVue153T8P6RniEXcHcHZ1hsqvC4a8qcSSLxfiQvwmfDPzHBoN7oeqts5wcQbib9/JtZ/kfo19/gxXFmLYlHh0nzIAoblO4ybj Kw38cqQs2g9fzEGVzA752vqiGb6hbntWZOynnZ6yCXiG/y5ZwfWTO PElu7o37PFbiWLYM6xMybjX3FOqFvq6yz nmo1zyxoF8U4nZSlgxECRPXMYtilXyIZ4zl29Lrq2Vj5pxyH7vqTu7HoSRfNGpSzvyTHYVUobka6s sxNKDHohoX /RIiAKBQCBGHLpsiKAjTc6/XQAMTExD/6O4OjxI5jVzh0KhQead2wC5fal2HDzHv5Yth73G3REq2IK08fVVsCA9adwbOUQVLo8Bz1eKouGEw9kLBluQZ70R6fijTe/w8VqH2HexijsXDMFbUuYqGqVKwIb9sW0iW1hd3gl1v1dOB8hUDj7oVxoKEIrVEbNRu0xeOZM9C15FpHzd K ufLmVp85icGyE1R tYORsU6e2s9U9mxsMvrm06Zn6djOov3kiU7 CpUaKhigZwxMT Cx/pOXeCUv5w5TSTScgOhDMTgUNRMd/RTQOVdEeKhztmwoXEqgYuXKqPzgr1J5PzgpAKVPEEo56HEi5ihSTaSvLF4GQU56xB6IgbHbWulHD JIigaBwQEZN5 Ugejy7svA5nlYdlmHayt/xkZFc7zb8fHBial85aVsUBRBk4i6sFeVx6uvlCh0q35K/GoM7RWJ4qNWY9qHfTDsh404tLkf1L8MwIj1ibDx8oYXbuDajSzXxpRr DdOAS9vL6jMbM9Zp/mantxFfALg6OQIBRzQ6P0 KLv7G3zy4WQs03TG4I7FYaNwhJOj4G58Qq6rced2jTXV954dwa3ffsWmmyfxVQM32NrawtYxDF cSsHeYeXh2XX1gzym4fTsN/HKkH/QcuFmfB/x5K8umOsX5rZnT8xa2ukRGxd/VKheDxHvTsGyKc0Qt/hbLL2UpWS6Q1iy9B UaNsRtbK8g5GnerWYhf2iELeTQqkyPQ6yJFbJj3jGWLKWjs8sOX4O5sauotdBDxVUqrxc1AuXQhIE6/HPiqWI8WyF9nUfrZipCq6GSnYXse33EzDyixIZ wRVRDntDRz W49SISEIyfwrA18XJQAFirTshlb2O7Bg/nwsWKdDs25t4KUwfVwAgMIRgU364qvfDmHjB17Y9/0c/JlmWZ5SYg/gqKEueo/qhsbVQxFapTqC3HOvakMeOmahkJaAu/cFaq0WaZaU10R95qQKqoTy2kvYtfNMrjMdIOCjvY2wF379zNdjJ9kvbLRn8Gf 6 CrvyFVFa9RTpmcjfk 6XUWeXsGtnlh A1/2NP6KuwL5StUK4Mjn951jap7N9x7Jzh8mvu5RAxcqVUDmsF2YseB/eO/6H7l/GmjxvZGPfCG 28cK/v0zC7FMmhk4OjdC1gy u/jIB04/lCIPTz2L uDn4260l3mr5cLZFgWKvv4fXnHdh5pyV GnGdrh2eBcRRfI kHiqshUShstHceyuG8oEe2YOSBwrh6OqcwIunL8NRalaqFk0AdHbD2UOXu9FbcGe9ADUqukNtZntOc 0yvxMz5CA LsCe0cHKAAog3tgYNMb HXuXpTtPQD17QEoHOBoDySaGbQ/Jss19vkP1BQo0n4WDh8/isMPB cHF6JHgBaVBq1F9KTG0ABI/GM4Xh98Es0iN LblsWf6oaLuX6hM7M9W11bTTsZp1AooJB0pKc/ kx/ciM2n/dCk ZVsq3Gb67en ReuMX94gVtJ4tilXyJZwo2jzmZG7uqSpdFkPIiduWGh bi vCsewV38ay5ceRtHWnyMsSyyqcGuNof3LodGktuiIkXi3nj 09/7E6XuPAkaFRxt80HMimn3xBjqrhqN7mD 0SZdwLK403n6rNpwVAJyaoMcbnnh55FCoPbpiVXPXjMGIiePqz6zDjB0GhFb0g0PaJew4fgdw94C7jWV50oZUQJB8h1njIuHzRig8VVdw/m7W3yA8g WTlyI pCpKu9vg7umtmD5uCVKqjkGroMJ2nz6D4eYJREdFQZOWhLjLR7B5zteYfS0Q/bqEwclld67lza0 c1J4tMGgXhPRdGxbdJVP8Vat4lDHn0dSQHu0rmT/aL/8aAdVGVStaItvF03C9zX7oIJcwE3PVmhr7nuP0ePymimYENQRtfyAk4vGYMLhAPSY3BwuAHR5Ti/3/L1R48n2U7i1wpB IWg0oSPecxyDLuUFsfNHYOKxcvjg 5ZwMZ8joqdjaZ9 IC/nDvMUcA4fgzlDt6H uH74LmIbPgzJ2GK4dQK7duxA1mWtbBwDUK16CbQY9zU67uyCQfUa4NDAd9C8ii8c9XE4FxONs6UGYVLnUnh57HT0 7Mt/tcgHDEDe6NVteJQ3ozFxjnf4Kd9Dnjj5y/QzjNLkOvcFP17BKLO1J74Oz0E/5vdAPZ4nMl8Vctx09ZY2coWjsu7OcrS9dHAbxwih32C6uM7o5JjHPbNGYkViSH4oJ4vbLQ 6NOvKuaP64MBgePR0ftvzB76C5IbfIl3qqkAm/Bct8utlehZoyd2RyzBvm9ehpM29/3NpZeN3ENiEuDgYJ8xplB44vXhE/Cnexxa9yzzYLCvgYODGvo78bgnQM6Weyi3a2xheNRQ6eKH4KwXCd09FNEoYOtVCmWKO0JhuIjIMdPwb93R6OZ/HUdirmfsp7BF0TIh8Da1puMDj7WTmX6hNtdvsiVuPe2ElL2YNWE37GtUgK TAXGntmDa2LVA7S/QsuTDWhHE7duNk6rqGFIle67N/X9U3FqJHlnbyVx 8tIvXtB2sihWyY94xlxGdAcxvFJtzKq9Bpdnv5qtnJYcPydzY2iF12vo02E02o7tgkGOI9AuRIGz6xfjiA65//zZC6hAF8bSxY6VKtqSMnCnkRepdddk55fdpX6Qh9iplKJx9JRSVZrIh6uzvHifdlF G/um1CrlLnYqldgVCZCa7y2WS1negNcdHSfVNGqp8NmhzBe TR03OXq8NA72FHuVjSjtikhg3bfl 33xj45nNk JcmhmLwkv7S62SqWo7VykaEBFifgqJuPYaTHyY dwCSnqKGqVRpyKlZNGPabK9quFcIl9w21Z3rOMeDlqxEahEBu1nbgWD5barQfItzuuPKjL3Muba30aexE/7aJsHNdRapZ0FVuVRpy8K8rbCy89vqDB07aDiKSeXiDv1fEXZ41K7DxC5LUfj4nOgu89ykPGUvpFKjeW8EB30artpWhoC/nf8n/kUa8yk14uixEYzZ R/S3dT3SXZfO4N QlP2fRap3Fv0ZHmbAly08kGftOfKS0srWTDsue30IHhQ0XxjLBgv5jcV8VC87FuTH1M0P3dsngEI24R8yVyzrjC1ABEHWWn9bTXYuSHwdGSLWS7mKvVonW0VNKvdRS s8/lrlYnuHuEVk0vKPUDS4qjlqN2LmXlOqt3pfpf143ulCf/uJ0ecXRRlwi5sq/OQtkYmGszHylW1C2LCfMlJWdxElTV746W9iW78mQdHyRfNiigng7aUSldRHfKq1l2MozmYutiO6SbBjRSkK97EXr4C1VOkySHdezXuBNbzfcXCFvl3SV4IG/P1qo8CnSyyZ5uXR00ErTWddz6ZOpsvndoqINmypn9GJkIR9LrrGFUM6FsVLWSTc3xeN9VlUu yJjIkYXUDLWTub6hdl 85AVtZPhxkYZ0bK6BBSxE5VKKy6 FeXVvj/K7pvZfrRIdg8JFE3QUNljJOO51avR/08PGVsYKy/9orC0k7nrmNGxlQWxytPGM bylRYtg0tppayRBQEtOv5j6ZsfCxsSYmROn5cl1MdZtPZFJbTBS KvcpG3Vr8YC2NZ vxVnaioqOiwsDBLg Y80OPI6Gqo8XND/H7yK4Q/s1tpz u49J ij8WY6jXwy6t/4OjElwrJoxVU0AbFrnmq739VoVU 5YSIiIisndxZgNf8h6DI4rOY09zYs0UFT39iAmpWnYuG24/ji1pq818oANHR0ahbt24YgD/N7fv8x y6WCxbfhK bX5AzWcZiD6v4xIREREREeWTlEP7cMy3I Y0fFYBsA7Hlv A3YYyCPRxgzL GFZP/gbHAt7Gd5WfTwCcV889CNYdWYblp/3QZnqNZ/o xfM6LhG9 DiTS0RERIWFXaNvceKIDqpnFX/KXZzfswJf/noUF28kwuDog9AGvfDL7BGobepl7UKmEDwOTURERERERPTk8vI4dGFd0Z2IiIiIiIgo3zEIJiIiIiIiIqvBIJiIiIiIiIisBoNgIiIiIiIishoMgomIiIiIiMhqMAgmIiIiIiIiq8EgmIiIiIiIiKwGg2AiIiIiIiKyGgyCiYiIiIiIyGowCCYiIiIiIiKrwSCYiIiIiIiIrAaDYCIiIiIiIrIaDIKJiIiIiIjIajAIJiIiIiIiIqvBIJiIiIiIiIisBoNgIiIiIiIishoMgomIiIiIiMhqMAgmIiIiIiIiq8EgmIiIiIiIiKwGg2AiIiIiIiKyGgyCiYiIiIiIyGowCCYiIiIiIiKrwSCYiIiIiIiIrAaDYCIiIiIiIrIaDIKJiIiIiIjIajAIJiIiIiIiIqvBIJiI3m0BagAACnlJREFUiIiIiIisBoNgIiIiIiIishqqvOwcHR1dUPkgIiIiIiIiKnAWB8HVqlUryHwQERERERERFTg Dk1ERERERERWg0EwERERERERWQ0GwURERERERGQ1GAQTERERERGR1WAQTERERERERFaDQTARERERERFZDQbBREREREREZDUYBBMREREREZHVYBBMREREREREVoNBMBEREREREVkNBsFERERERERkNRgE05OR24hZ9ROW7o DPO 8EBERERERWYhBcF5IMq4d34u/LtzPHvjpjmPue 3Rc8ZhpD6vvD1r mvYs2IF/jj7oC6ssQ6IiIiIiOiF82yCYMMt7J8/Cu91bIWWrTuh7/gliL37As4f6k9h6dgxmL8/PvvnNg7w8PWFn6cjlM8nZ88f64CIiIiIiF4AqoI/hA7nl47DuGX3Ed7zY7zjfgW/zZmHkZMc8OOEFiimKPgcFDibEogY8RUinnc nifWARERERERvQAKPghOP4q1a06jSMspeL91OagBlNdcRI/RK7Dh9KvoEZxj3tBwG38tnoG56/fh7B0F3EvVQIue76FDZfeMaWu5heiZX2LRnrO4fOMu0myc4F22Dlq93R2tyrkgM6bWXcfeRbPwy9bDOHdbD9egMLTv3RstyzhAIXHYP/97LPzjOM5fS0Ca2h1h/b7BJ03ccGX9OIycfxDXEtKhcvFDpVd7YWDXl CROWeuw/GZb6PpTADQIHz4cowI/xcL g3AtpemYlaP4IyZUAvKsWvaFCzadx5Xb91FCuzgUbomXu/dD23KOkIhyTjz23T8sHgXTt1IgcrFB7V7jsNHTYoi232DfKkPM3kBgLTL2DlvGhZsOYIrybYoFlIKmnsCdWa7ncteB5akKXcQu2I25q7dg9M3kqGwc0fxEiFo1ncY2gRyPpmIiIiIiPJfgQfBhqsncPKOA8pXCcoMmOwqVEVZ5TacOBkHCfbMEtSl4uTPwzFylQINenyEXiUF536fj7kjPkXalK/RNVgDSCLOxRzGrRLd8NGAIGhSruHw oWYOewMkqZ iU6BagApODr3U4zb7oUOfUaiv0ciDi76HtNGzUSx2YPwku1dnNqzB9eKd8X/BoTCSZ8IG183KKCAW7nm6PlRO3g4Cm7FLMW0eZMxq/RcfBz IHCDCqXbj8LQJp6wgQIOXhojpbasHBdiY3Gn5Nv4 P0yUKdcwd4lP2Hm2FnwnTMI1a4tx5Qf9sLjrY8wpXoRyJ1LSPJyx2MT5/lSH7nn5SXbJByc8Sk 32aPJt0 Rp8SKtw tgmLTmYJgo3kK9c07VJxKnI4PlmaglqdB2BUWTfIjR2Y/dU2nLxhABgEExERERFRASj4IDj Du7CBe6uWV4/1rijiLPgUlw8DPDMfIdU7u3B0rWXENBpOga19oMNgEqhPkg 3xdLl 1F2 HhcAAAKGDvXwk1qmbMularXgroPwgrl /Hax/VgW3in1i /haqDZiCLuEZs6GBA67jwNsL8cfR/nipOgDYwD6gCmpWDs72DqtDQHXUCcj4d5lAR5zf2Q bT16CPrxsZmVp3XwQULL4o4DUkL3MeSmHnX9FVK8SDCUqoZLHdfz1/lbs/1uHKhKPu KEqhUroWygLYDAXGo5P rDdF6ql/gTq7fcQki3WfigjXdGuSs44szmfTiWa ubTvOl0vuwbNV5 Hb4Hh91LAUVAIn/FysV23JNkYiIiIiI6Gk8g3eCBfL4/KVR kuncTbFE3Uqej9asUvpg4qhHojcdxqX9eEINpaUpjSqV3LDspjTuKKvg5KXz Bcyn1cn9oJLb98lA 9TgFt3P1cftInHVf/XIg5S3bh OU4pKqdoL6vh7JcWh7KTlsClaHEVtEnA3UaCq0QIdqkRj5sfv4nTD5oiIaIawQBfLFp3Kh/rImhf9lXO4mO6JsHJeFrakcdnSvHQKZ1I8UbOq/7PohERERERERACeQRBs4 oOV8QjLt4APAzh0u/gdqICru6ujy1P/aRrRisUWVISAWyKoNGQCegYlDVsVMDO3QkKxBlNw3B GcZPXA2bZn0wtG8ZuCkuY/0XE/BntgNZlp8nKYdCqYISAoMBgDoAbcb9hBqHtmDN8uWY2n8ZVr09ARM7loHWkrSesj6y5UWhyCiR4elW9M6aphj0MEAJpfK/sDIaERERERG9KAr8J5JsvMsixC0Jx2L QfqDz5KP/oUTumIoG5L9HVelXxBKa28i9si1R08Y668g9tgt2JYOgq paVDDVRw7cRvaEgHwVgJKnwCUUMfjzBUDvP384Jf55wsPB9NFTjt3GucNoWj5VhNUKVMSJQPLwMcp6/4aaDVA0r37OZ AzuaJy5GTwg7Fq0ag9/hpmPC6K06u3ojjOgu l0/1kb08N3Dor4uw5PCWUHr7w0d5A8eP33jiGx9ERERERER5VfBPoqpDEdEqCFtRY/ HRHA/cr G3mdqRWeg/NymSPBhWOtdGulR/ t2g8vrbrhsYlBOe2/IxF50vg9f41H7xHCwAG3Nq9DIt8GqCsJ3Bp wIsOlMMr/aqkbGPSxhef/VXfLJkHCYqO6FpeS oU27iQoI3Xnm5HOxNZdUvAD6yChsWboFHgwC4KG/hWlKWEE3pi8BSGqza/itWh0QgQK7jrktt1A/Jno7l5TDN8O9erD9iQMkAT9jqbuLwhXuAkzOcjE6cFkx9ZC1P 9YlMHTxGIzHW2hewQualGO4kvzk4avCNQwt60VizMLPMc2uM r5AVf37cRZPVD5iVMlIiIiIiLK3TN4HVOFku1H4NOU7zBr3lj8nuKAEjW7YFS/FvB LKDTomy3cRitnYG5iyfhk3jArVQNvDmmNzoEZ38IWKNKwF LvsSiG2lw9K2MiE/6oFsluwdb7VHpnUkY5TIbCzZNw9jI 4CDJwLCe6LuyzAZ9CkD2 N//W/jhyXT8dmqJBjUdnBy80Owt1PGjLXCGfV6DkDsFz9h/pho6B2Ko3rXYNQLyZmS5eUwRRd/FlFLVmDm1QSkq5xQLKgWen/YHqVNzCIXRH1kLU9I1wmY4PwTfl47HWMWJkKvcYKnTwWE ds/2XvCCmfU6j8OH9jOxPLI8VifqIVPiBdUChvY8AlpIiIiIiIqIJaGG3WSk5OjCzQnlsr5e7TPOz/P23 oPgwXF2FA302o/MVsvFOWy2UREREREZHl7OzswoDsSzoZw0iDnhM9Luxag Pii IejlDeu4A/l6zEhWKvoF9pdksiIiIiIioYjDbo ZAkXDsZheXbz NGfDLErghKVmqGYYM7o5zmeWeOiIiIiIj q168x6GJiIiIiIiIcrD0cegC/4kkIiIiIiIiosKCQTARERERERFZDQbBREREREREZDUYBBMREREREZHVYBBMREREREREVoNBMBEREREREVkNBsFERERERERkNRgEExERERERkdVgEExERERERERWQ2XpjnZ2dmEFmREiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIiIioufu//2NDhgLka7rAAAAAElFTkSuQmCC[/IMG]

---

### Post by tea for one on 2022-02-03
> **lennoxg said:**
> I tried to add an image of my GParted screen by copying and pasting, but it woukld not allow me to
Please let me know how i can send yo an image of my Gparted screen

Take a screenshot of your Gparted window.
Save the screenshot.

Advanced reply > Attachments (Icon on top row) > Manage attachments

---

### Post by oldfred on 2022-02-03
Both Windows & Ubuntu with major updates or an install reset its own boot loader to default.
HP systems seem to ignore grub's use of efibootmgr to change boot order & those users need to use UEFI settings menu (not UEFI boot menu).

Grub only boots working Windows. Or Windows cannot be hibernated nor fast start up on which sets hibernation flag. And if Windows NTFS needs chkdsk, you have to do that from Windows or your Windows repair flash drive.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by lennoxg on 2022-02-03
OK Thanks

---

### Post by lennoxg on 2022-02-03
MY Devices status as displayed by Gparted  and fdisk

---

### Post by lennoxg on 2022-02-03
Hi  oldfred

Here is the link to my Boot-info Summary

[https://paste.ubuntu.com/p/k5RzbH5b8b/](https://paste.ubuntu.com/p/k5RzbH5b8b/)

---

### Post by oldfred on 2022-02-03
I thought you had Ubuntu installed, report only shows Windows in UEFI boot mode on gpt partitioned drive.

If posting terminal output, just copy & paste that, do not use screenshots.
And if longer, use Code Tags which are easy to add with Forum's advanced editor and the # icon.

---

### Post by lennoxg on 2022-02-05
The report does not show the now un-allocated 463.34 Gb partiton where my Ubuntu OS and data files should be residing, but the Gparted display shows  the 463.34 Gb un-allocated  partition. Does the un-allocated status of that partition means that Ubuntu OS and data files is unrecoverable? would i have to do a new install or can we fix the problem? while waiting on your reply i would continue to read-up  [COLOR=Navy]"UEFI boot install & repair info - Regularly Updated" to see if i can find the solution.

I do not know how that 463.34 Gb Partition became un-allocated
Thanks again
[/COLOR]

---

### Post by oldfred on 2022-02-05
All the reports have shown sda3 as NTFS, not a linux install.
Did you have Ubuntu installed? Or just live installer?

Ubuntu cannot install to NTFS partition.

---

### Post by linux-sysop on 2022-02-06
I may not be of much help as I don't care for EFI over MBR.  But the future is what it is, so I deal with it.  I apologize in advance, if the following information is not helpful.

First thing you should know about my system, I have a total of 3 drives.  A few years ago, I installed Linux Ubuntu 18.04, removed Gnome and run pure OpenBox with Tint2 panels.  I am a minimalist and don't care for extra baggage or bloat.  This is a 240 GB SSD, GPT, and I allocate 200MB fat32 for the EFI.  This boots up without seeing the grub menu what-so-ever.

On the original spinning HDD at 1 TB, MBR, I installed Windows 10 - using the download from Microsoft and my OEM number from my case - to the separate physical drive.  I told my Linux to ignore the drive in the UDEV rules.  I don't use grub to boot the Windows 10 (since it is not used often) I hit F9 and get a boot menu choose the SATA drive and it boots from the MBR.  I only allocated 400 GB for the Windows partition.  This gets used only when I need to test a program in Windows or I have to compile test code for Windows.  I probably boot into Windows twice a month.

The third drive is a 2 TB SSD, also formatted EXT4, GPT, 500MB fat32 for the EFI, and it boots Xubuntu 20.04 which I recently installed to replace my 18.04.  I am in the process of customizing it.  I always hang back 1 LTS to give it ample time to be the most stable.  The OS is given 100GB and the remainder is for transient files.

If you are running just 1 drive, cannot afford to install another, or just don't have the space, I would recommend getting Linux set up prior to Windows 10.  As long as you own a license, you can download the installer from Microsoft.  
As a side note; I find it very odd, Windows 10 support ends on October 2025, and Windows 11 ends on October 2023.  Very strange indeed, I am sure they have their reasons.

---

### Post by tea for one on 2022-02-06
> **lennoxg said:**
> The report does not show the now un-allocated 463.34 Gb partiton where my Ubuntu OS and data files should be residing, but the Gparted display shows  the 463.34 Gb un-allocated  partition. Does the un-allocated status of that partition means that Ubuntu OS and data files is unrecoverable? would i have to do a new install or can we fix the problem? while waiting on your reply i would continue to read-up  [COLOR=Navy]"UEFI boot install & repair info - Regularly Updated" to see if i can find the solution. I do not know how that 463.34 Gb Partition became un-allocated Thanks again [/COLOR]

Un-allocated means that there is no filesystem., therefore no files, no data, no OS.
It is now free space waiting to be formatted and allocated for use.

Do you have a backup of your personal data from Ubuntu?

---

### Post by lennoxg on 2022-02-06
Thanks for the info

---

### Post by lennoxg on 2022-02-06
I had Ubuntu installed. As i mentioned in my first post, i was running a  dual boot with Ubuntu 20.04 and windows 10. i was using the Ubuntu OS when  the system crashed.

The un-allocated 463.34 Gb space in the Gparted display shown in the attachment is where my Ubuntu OS and data files resided.
See the attachment.

i know that i can do a new install and simply restore my data. the problem is i am not sure that my latest data files are backed up. if i can recover all my data files from that 463/34 Gb space i would be grateful. The reason why my latest data files may not have been backed is this.   i was using Deja Dup backup App. and it was working well. Deja Dup documentation stated that backups will continue even if the storage device became full, as Deja Dup will delete old data files to create room for new backup data. However Deja Dup did not delete the old data files as stated in the documentation. This caused my latest backups just before the system crashed. to fail because of a lack of space on the backup disk, In my research i found that other Ubuntu users have the same problem with Deja Dup, If we can recover all of my data files, i would appreciate it. if we cannot, then just tell me that we cannot and i will go ahead and do a new install using whatever data i did manage to backup. However I understand from this [Ubuntu Documentation]("https://help.ubuntu.com/community/DataRecovery") that my data may be recoverable. what do you think i should do?[URL="https://ubuntuforums.org/."] 

Thanks Much
[/URL]

---

### Post by oldfred on 2022-02-06
Then what does testdisk show.
Or if you know it was one partition or sizes of partition parted rescue often is easier.
Why my rsync backup includes multiple extra commands to make sure in /home I have latest system configuration info.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) & 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

Testdisk Instructions, new versions use sectors, old ones were CHS
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)

---

### Post by lennoxg on 2022-02-07
Thanks for the info
I am going to take some time to thoroughly read through the documentation before attempting recovery procedure. so my next post would be in the next 24 to 48 hours
Thanks much

---

### Post by lennoxg on 2022-02-08
[B]I used TestDisk to recover "lost" partition
[/B]I checked all partitions for files and i was able to list the files using the "P" command
Quick search showed up two #4 partitions  one with no files. that one was left designated as "D" and was not recovered  [B]

Find Bootinfo Summary here> [/B][https://paste.ubuntu.com/p/RP9hCww5wq/](https://paste.ubuntu.com/p/RP9hCww5wq/)[B]

fdisk display after recovering /dev/sda3  464.3G ext4 Linux filesystem partition[/B]

Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000LM035-1RK1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 24D2FE0B-1606-4609-BF58-6314AABA3389

Device          Start        End   Sectors   Size Type
/dev/sda1        2048     534527    532480   260M EFI System
/dev/sda2      567296  978100223 977532928 466.1G Microsoft basic data
/dev/sda3   978100224 1951885311 973785088 464.3G Linux filesystem
/dev/sda4  1951885312 1953523711   1638400   800M Microsoft basic data


Disk /dev/sdb: 14.54 GiB, 15597568000 bytes, 30464000 sectors


**TestDisk "Analyse" display after recovering /dev/sda3  464.3G ext4 **[B]Linux filesystem partition
[/B]
TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
[https://www.cgsecurity.org](https://www.cgsecurity.org)

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P EFI System                  2048     534527     532480 [EFI System Partitio
 2 P MS Data                   567296  978100223  977532928
 3 P Linux filesys. data    978100224 1951885311  973785088
 4 P MS Data               1951885312 1953523711    1638400 [RECOVERY
Disk model: Ultra           
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x003f729d

[B]See attachment for Gparted display of devices and partitions

What is our next step? Do we try to repair Grub and boot or do we copy the files from the partition?

[/B]

---

### Post by oldfred on 2022-02-09
If you do not have a good backup always best to do that first.

But you reinstall grub, not sure if restore would boot or not as UEFI & ESP still have boot info & if UUID did not change, it may boot.

But you can totally reinstall grub using Boot-Repair's advanced mode.

---

### Post by lennoxg on 2022-02-09
OK will attempt to do backup and then reinstall Grub. need time to read up
Thanks much

---

### Post by lennoxg on 2022-02-11
Hi oldfred

I will be using rescuezilla to backup my Linux Filesystem. i will be doing that later today as i have to purchase another external Hard Drive to do so. i will then try to reinstall grub
Thanks for the lessons. i am learning so much;)

---

### Post by lennoxg on 2022-02-12
Hi oldfred
i did not get my backup drive as expected yesterday. i will have it by this Wednesday. so i would resume work on this issue on Wednesday coming. 
Thanks for your patience

---

### Post by MAFoElffen on 2022-02-13
@oldred

Hint... More going on under the covers. 

First boot-info script: [https://paste.ubuntu.com/p/CxNxBGCzxZ/](https://paste.ubuntu.com/p/CxNxBGCzxZ/)
Line 114 in his install... That is the LiveCD...
```

Disk sdb: 14.54 GiB, 15597568000 bytes, 30464000 sectors
Disk identifier: 0x2cf4ba3a
      Boot   Start      End  Sectors  Size Id Type
sdb1  *          0  5999871  5999872  2.9G  0 Empty
sdb2       5271500  5279499     8000  3.9M ef EFI (FAT-12/16/32)
sdb3       6000640 30463999 24463360 11.7G 83 Linux

```
This is the only media between the two that has a bootable flag anywhere...

Line #79. Disk is marked as BIOS bootable. No partitions on sda have a boot flag. Nor was there any partition with a Linux filesystem.
```

sda    : is-GPT,    hasBIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

```
Only ESP between the two disks is on sdb (the LiveCD), which is not the Win disk... MBR/CSM? But, the system is set to UEFI boot and SecureBoot. Which both would be wrong for how sda is laid out...

Just saying...

My suggestion(?) Dump the first sector of /dev/sda... and filter it through hexdump.

---

### Post by oldfred on 2022-02-13
I think many partitions were deleted, particularly those for a UEFI boot of Windows.
It may be best to just start over. And restore all data from backups.
Total reinstall of Windows and reinstall of Ubuntu, both in UEFI boot mode. No legacy/CSM/BIOS mode at all.

Windows in UEFI mode need lots of partitions.
BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) &

---

### Post by lennoxg on 2022-02-15
Hi oldfred
I am now seeing your latest post after i booted up Ubuntu.  i was able to boot Ubuntu after backing up my "home" directory and totally reinstalling grub.
I did not use rescuezilla again. i learnt of SystemRescue CD. I made a SystemRescue flash disk and used the procedure "How to recover files to another Disk" to backup my "home" Directory.  Next i used the procedure at [this website ]("https://www.techzim.co.zw/2021/01/how-to-restore-ubuntus-efi-partition-in-ubuntu-20-04/")to totally reinstall Grub using the chroot command.

After reinstalling Grub i was able to boot my Ubuntu 20.04. However i observed the following issues
[LIST=1]
[*]Ubuntu boots very slowly, taking about 1Min 50secs to boot 
[*]when i power-down and power-on my laptop again, i am not presented with the boot options . The boot defaults to windows 10. 
[*]If i try to restart Ubuntu, again it defaults to Windows 10 
[*]To boot from Ubuntu after power on, i have to press the "esc" key to be presented with the boot options 
[/LIST]

I will take your advice and do a new install of Windows and Ubuntu

**Note: **while waiting on my external drive, i did a reset of my windows system. I suppose that is equivalent to a Windows new install.

Can you show me the command to backup my system using Rsync
I read up a procedure at [this website ]("https://www.techzim.co.zw/2021/01/how-to-restore-ubuntus-efi-partition-in-ubuntu-20-04/")in which the author suggested the following command.

sudo rsync -aAXv --delete --dry-run --exclude=/dev/* --exclude=/proc/* --exclude=/sys/* --exclude=/tmp/* --exclude=/run/* --exclude=/mnt/* --exclude=/media/* --exclude="swapfile" --exclude="lost+found" --exclude=".cache" --exclude="Downloads" --exclude=".VirtualBoxVMs"--exclude=".ecryptfs" / /run/media/alu/ALU/

I understand most of the command. I understand also that i have to remove "--dry-run" when executing the command. however i don't understand two things:
1. I do not understand how to specify the path to my external backup drive  would it be something like   /dev/sdx where sdx is the external drive system?
2. Isn't there a more straightforward way of backing up my home and other folders instead of this command with all these directory exclusions.
What is the advantage of the command line with all the Directory exclusions?

---

### Post by oldfred on 2022-02-15
With a command like rsync you have to have a valid path.
I create a /mnt/backup and then mount my backup partition to that mount point.
I have a script that exports list of installed apps, runs the old bootinfoscript which does not require a gui, but provides documentation of my current configuration like Boot-Repair's summary report. Report is better & I periodically run it & save in /home so it is also backed up.

Parts of my script:
> 
my_mount="/mnt/backup"
my_user="/home/fred"

# multiple commands to check that mount works. I have labeled backup partition backup_b
/usr/bin/mount -L backup_b $my_mount
#I used to do this, but when flash drive plugged in it is sdb4, not my HDD's sdb4 (becomes sdc4)
 #/usr/bin/mount -t ext4 /dev/sda4 $my_mount
# I backup each folder in my data partition which is not in /home, but linked into /home
rsync -aruvlP /mnt/data/Documents /mnt/backup
#etc for every folder but have another text file with all the excludes
rsync -aurvlP --exclude-from=backup_excludes.lst /home /mnt/backup/bu_$(hostname)



Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

More better info, as TheFu is really the expert and more professional as he backs up multiple systems.

What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) &
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) & 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[https://ubuntuforums.org/showthread.php?t=2311501](https://ubuntuforums.org/showthread.php?t=2311501)
[https://ubuntuforums.org/showthread.php?t=2419993](https://ubuntuforums.org/showthread.php?t=2419993)
Simple manual rsync & rdiff theFu
[https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689](https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689)

---

### Post by lennoxg on 2022-02-17
I Did as you said. i did a new install of Ubuntu, and everything is working well. 
I will try the Rsync command and script you suggested and get back to you in the weekend.
Do i now check this issue as resolved?

---

### Post by lennoxg on 2022-02-22
lots of reading o do
will get back to u by weekend
Thanks much

---

### Post by lennoxg on 2022-03-06
Hi oldfred
i haven't yet gotten around to tackling the backup using Rsync. i guess its because its not that critical at the moment.
i will leave things as is for the moment. i will tackle it in the coming weeks.

I thank you very much for the assistance you gave to me to resolve the problem with my Ubuntu operating system. When i get the Rsync backup going i will let you know. 
Thanks much again

---

### Post by lennoxg on 2022-03-06
Hi oldfred
i haven't yet gotten around to tackling the backup using Rsync. i guess its because its not that critical at the moment.
i will leave things as is for the moment. i will tackle it in the coming weeks.

I thank you very much for the assistance you gave to me to resolve the  problem with my Ubuntu operating system. When i get the Rsync backup  going i will let you know. 
Thanks much again

---

