---
title: "Can't Shutdown Ubuntu 15.10"
date: 2016-03-23
forum: New to Ubuntu
---

### Post by rabbit2 on 2016-03-23
Hi Community,

So I decided to turn my Laptop from Windwos 8.1 into a dualboot with  Ubuntu and thus installed Ubuntu 15.10 through a memory stick. My goal  was that I could choose between the OS I want everytime I start up.

  After some initial expenditure I seemed to get the OS working fairly  well, and thanks to GRUB I can choose the OS I want every time I boot.

  However, the one huge issue I could not fix is Ubuntu simply wont  shut down. Instead the screen just freezes, so I have to force shutdown  everytime by pressing the button.
  When starting up, I get an error named "Secure Boot Violation" Invalid signature detected. Check Secure Boot Policy in Setup.
  After pressing ok the laptop boots normally however. 


  I tried so far: changing GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" into GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
--> Did not work.

  I reinstalled Grub through Bootrepair and let it run through.  ( [http://paste.ubuntu.com/15473378](http://paste.ubuntu.com/15473378) )

  --> Did not work either


  Furthermore, I cannot reboot, I cannot sign out, I cannot log off, and I cannot shutdown by commandline (tried sudo -shutdown -h now) it all results into freezing
  Now before I mess up too much I wanted to ask you guys for help. 


  **I am using a MSI MS-16H2 Notebook**


  [HR][/HR]  
Where I suspect the error might be situated in:

  Gparted does always give me an error message when I run it, first:

  "The Argument is invalid, while /dev/sda was positioned for reading."
  When I click ignore, I get another error called:
  "The backup GPT table is corrupt, but the primary appears OK, so that will be used."
  --> After clicking ok. I can use Gparted normally.


  After I ran boot-repair, I was told that I should make sure that the boot-partition is located in /dev/sdc
  --> Now here I think where the error is. 
  Because I find a BOOT-Partition (fat32, /boot/efi) in: 
  /dev/mapper/isw/dddegaaaac_RAID0IMSVolume2
  And then I find the BIOS_RVY Partition in /dev/sdc

  (where I was told the boot-partition must be)


  Do you guys think this might be the error? And if not, what else  might I have to consider so that my Notebook will finally shut down?  Furthermore, if I change the Location of the Boot-Partition now, could  this harm the Windows-OS?

  --> If someone could tell me how I can rename this Raid's horrible name I'd be quite happy too.


  Also, there are 2 Disks à 119 GB (/dev/sda and /dev/sdb) which are  labelled "not assigned" --> I think this is where the initial error  message in Gparted comes from. Can I use them or may I not change them  because they contain some curcial windows-data or something?

  I posted the Images of Gparted and the Link after boot-repair to make it more clear. 


  Thanks alot for dealing with my issues.

---

### Post by howefield on 2016-04-06
Free bump...

---

### Post by mastablasta on 2016-04-06
are you using some form of fakeraid on windows? why do you have raid0?

booting stuff should be on separate disk. I am not sure what the exact setup is in case of raid. but you could set it in windows so that all boot related stuff are on sdc disk.

---

### Post by rabbit2 on 2016-04-13
Hey, Concerning this beeing a duplicate post, can you tell me how to instead bump a post?
thanks.

Thanks for your reply,

I haven't changed much in the windows-raid settings before decided to install ubuntu. Maybe I splitted up a partition but thats about it.
Can you recommend me a tool to arrange all my boot-related stuff to sdc disk?

greetings

---

### Post by howefield on 2016-04-13
> **rabbit2 said:**
> Hey, Concerning this beeing a duplicate post, can you tell me how to instead bump a post?
thanks.

You have just done it by posting to the thread. Feel free to "bump" your thread back to the top around once(ish) per day if you haven't received a response.

---

### Post by mastablasta on 2016-04-14
Well you could install the bootloader to sdc:  => No boot loader is installed in the MBR of /dev/sdc.

though it could be this is not the issue at all.

what happens if you shut down via command line?

```
sudo shutdown -h now
```

---

