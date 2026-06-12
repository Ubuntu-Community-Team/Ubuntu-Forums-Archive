---
title: "Help needed for disk erasure application"
date: 2010-03-03
forum: Programming Talk
---

### Post by foosaa on 2010-03-03
hi gurus!

I am in the process of writing a disk erasure application in C. All I am doing it to zerofill a drive (Good or Bad) before I destroy it. During the erasure process, I need to record the number of bad sectors.

I am using 8.10 Intrepid with 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (ubuntu 4.3.2-1ubuntu10)) on a live cd with XFCE for some other tools to run across multiple systems.

I am having problems in writing to the HDD (Particularly bad ones.) The method used to write to the hdd involves opening the appropriate /dev block device using open() call with O_WRONLY flag, start issuing write() calls to fill the sectors. A 512 byte buffer filled with zero's is used. All calls are of 64bit enabled. (I am using _LARGEFILE64_SOURCE define).

The problem is, when the write call encounters a bad sector, it takes a bit longer than usual and writes the sector without any errors. (dmesg shows a lot of error messages embedded in the LIBATA error handling code!). The call never fails for any reason. Here is a summary of things I have attempted.

I know about the bad sector and it's location on the hdd, since it has been verified by using Windows based hex editor utilities, DOS based erasure applications, MHDD and many other HDD utilities.

I have tried using O_DIRECT (please don't jump on me for using it.(Linus has some hilarious comments)! :)) to failure (sure. with aligned buffers! :)

I have tried using fadvise, posix_fadvise functions, but still failed to identify the bad sectors.

The libata is not letting / informing the user mode program (executing under root) about the media / write errors / bad blocks and failures, though it notifies the kernel and logs to syslog. It also tries to reallocate, softreset, hardreset the block device which is evident from the dmesg.

What has to be done for my program to identify / receive the bad block / sector information during the read / write process?

I have coded the same application (well almost similar) in Win32 and it works fine on Windows systems. It tells me when it encounters a bad sector. DOS application works fine too. I am using ATA Commands from DOS (Written in assembly).

So, now one might think why don't I use the same raw i/o approach here too? 

But too is failing. I have used SG_IO and SAT translation (well, now anyways all the block devices are identified as scsi devices, right?) and it fails too. 

Inbuilt utils like sg_dd fails to identify the bad blocks too. But dmesg shows about the sector i/o errors and all the stuff that happens with the bad device. 

How can I receive the errors in my program? This is my only requirement and question.

I am currently out of options unless anyone from here can show some new direction!

My only option is to recompile the kernel with libata customization and changes according to my requirement. (I have to instruct to libata about skipping the error handling process and pass on certain errors to my program). Is this a good approach and recommended one? If not what should be done to achieve it? If yes, can somebody throw some light on it?

Please let me know if you have any queries in my above explanation.

Thank you for your time in reading this rather unusual and long post!!

---

### Post by lavinog on 2010-03-04
Can you not just use dd and zero the drive. Then check the drive afterwards that all bytes are zeroed?

Bad sectors are usually detected transparently by the drive's firmware.  If a drive has a bad sector, the OS won't know about it until all of the spare sectors are used.
The thing to look at is the number of sector relocations in SMART.

---

### Post by geirha on 2010-03-04
You could peek at the source code of coreutils's shred command and see how that does it.

---

### Post by foosaa on 2010-03-04
I have tried to use SMART values, but it does not give an accurate count of bad sectors (all it provides is the number of reallocated sectors, seek failures and other failure information.).

Yes. I have analysed the code of shred, dd, dd_rescue, sg_dd and such forensic utilities. The problem is if I use them, I am unable to get the exact count of bad sectors during the writing process, which is my primary requirement and strangely it never has reported any bad blocks on "known" bad drives!

thanks

---

### Post by lavinog on 2010-03-04
If a sector is reallocated due to a bad block, the kernel is not going to be notified...therefore your program wont be notified about the error.
If there are no more reserved sectors on the drive, or the drive just fails to reallocate the sector, you will then get a bad block error...in which case the message should be logged in the kernel messages /var/log/kern.log:
```
 
end_request: I/O error, dev sdc, sector 53175408
Buffer I/O error on device sdc, logical block 6646926

```

---

### Post by foosaa on 2010-03-04
yep. I perfectly got that error in the syslog. But is there a possibility of getting that error in my program?

The driver / kernel is catching the i/o error for a bad sector, but it is not propagating to the user mode program which caused that error operation.

---

### Post by psusi on 2010-03-04
An O_DIRECT write() should definitely fail on the bad sector.  What if you try READING from it instead of writing?

---

### Post by foosaa on 2010-03-04
O_DIRECT writing fails to identify the bad sector. O_DIRECT reading identifies the bad sector, but if used together in the same program, it fails to identify the bad sector. I am using 4k aligned buffer in the code.

---

### Post by psusi on 2010-03-04
Sounds like a kernel bug to me then.

---

### Post by foosaa on 2010-03-04
yep! I agree with you.

I have mailed the linux kernel mailing list and receiving some responses. Will soon post more information. Mean while, I wanted to check if there are any alternatives that can be tried, but looks like there are none!

---

