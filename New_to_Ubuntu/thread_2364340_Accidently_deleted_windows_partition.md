---
title: "Accidently deleted windows partition"
date: 2017-06-22
forum: New to Ubuntu
---

### Post by krishprince on 2017-06-22
Unknowingly seletected delete previous operatig system option while installing ubuntu 16.04, Even though i stopped the installation process it is too late as partition changed from ntfs to Linux. I need some important data to be recovered from the hard disk. Is it possible.
I know from other theads and forum that it is not possible to get windows partition back. But data is needed, can it be recovered.

please help.

thanks

---

### Post by westie457 on 2017-06-22
Hello krishprince, welcome to Ubuntu Forums.

You might be able to recover some of your files using Testdisk and Photorec.

Boot your computer using the installation media to 'Try' mode. **Do not use the internal hard drive.**
For ease of use plug in an ethernet cable and open a terminal. run ```
sudo apt update
sudo apt install testdisk
``` When that has finished run testdisk in the terminal.

Accept the default suggestions and allow testdisk to find the previous partitions, you will probably need to do a 'Deeper Search' to find them.
When all searching has finished use the 'up and down' arrow buttons to select a partition and press P to list files. If (this is a big if) you are lucky enough to have files listed you can copy them to a different hard drive.

Photorec works differently and finds file header information and saves files with a number and extension :- eg 105.jpg, 12.mp3.
You have to sort through afterwards to rename the files. You will also need a hard drive with a very large capacity to recover all files found.

More information for testdisk and photorec can be found here. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Good Luck and I hope you have some success with this.

---

### Post by Mark Phelps on 2017-06-24
> **krishprince said:**
> Unknowingly seletected delete previous operatig system option while installing ubuntu 16.04, Even though i stopped the installation process it is too late as partition changed from ntfs to Linux. I need some important data to be recovered from the hard disk. Is it possible.
I know from other theads and forum that it is not possible to get windows partition back. But data is needed, can it be recovered.

please help.

thanks

My own experience recovering files in both Windows and Linux environments is that Windows utilities work best with Windows filesystems.

Your best bet for recovering data now is to do the following:
1) Remove the hard drive from the PC
2) Purchase a USB-to-Hard Driver adapter kit
3) Download and install this utility on a working Windows  PC: [http://www.majorgeeks.com/news/story/recover_data_in_3_steps_with_minitool_power_data_recovery_free_edition.html](http://www.majorgeeks.com/news/story/recover_data_in_3_steps_with_minitool_power_data_recovery_free_edition.html)
4) Connect the old drive to the working PC
5) Run the data recovery utility to see what can be retrieved from the old drive.
 
If that tools does not find what you need, an alternative is Recuva:  [http://www.piriform.com/recuva](http://www.piriform.com/recuva)
 
And, if that does not work well, the best tool out there is this one, but only the trial version is free:  [http://www.file-recovery.com/](http://www.file-recovery.com/)

Good Luck

---

