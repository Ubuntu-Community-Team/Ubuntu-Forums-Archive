---
title: "VMWare only likes .iso files"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by Ketman on 2012-02-26
I've downloaded Win95 as a .rar file to use in VMWare, and now I find it only accepts either a bootable CD, or else an .iso file. Can I do a conversion, or do I have to search online for the right format? (The .rar took an hour to download).

---

### Post by LinuxFan999 on 2012-02-26
You will need to extract the .iso file from the .rar file, since .rar files are archives. This can be done with Ubuntu's archive manager or 7zip.

---

### Post by Ketman on 2012-02-26
I should have mentioned I tried Archive Manager, but it said "archive type not supported". I don't seem to have  7zip, but I'll look around for it.

---

### Post by Lisiano on 2012-02-26
I think due to RAR being a proprietary format, Archive Manager can't do anything with it until the needed software is manually installed. Just click [here]("apt://unrar") or open a Terminal (Ctrl+Alt+T) and type in ```
sudo apt-get install unrar
```
Or just find "unrar" in Ubuntu Software Center manually.

---

### Post by Ketman on 2012-02-26
I've just installed p7zip from the software center, but it isn't listed under applications, and Search For Files fails to find either P7zip or 7zip. I tried "man P7zip" and "man  7zip" at the terminal. In the first case I get "No manual available". In the second, I get "(Alternatively, what manual page do you want from section 7zip?)".

How would I run this thing from the terminal?

Edit: Just done the same with unrar. Again, never appears in my Applications. Again, Search for Files fails to find it. But terminal responds to "man unrar" with a page of switch options.

What command would I need to make it extract all the files into the current folder?

---

### Post by Lisiano on 2012-02-26
The second you installed p7zip, Archive manager (Or file-roller) automatically "learned" how to use it.
> p7zip can be used with popular compression interfaces (e.g. file-roller and nautilus)
Also, I have it installed and it didn't do anything to my .rar archive. Just install unrar as I said above, p7zip will only work on 7z and 7za archives (I think).

EDIT: Just use Archive Manager after you installed unrar or in a terminal
```
unrar x file.rar
```

---

### Post by Ketman on 2012-02-26
I've just used Archive Manager, and it seemed to work. At least it said "extracting files", but the result is one .vhd file, which VMWare won't recognize. Nothing with ".iso" suffix.

---

### Post by Lisiano on 2012-02-26
[http://en.wikipedia.org/wiki/VHD_(file_format](http://en.wikipedia.org/wiki/VHD_(file_format))
.vhd is a "hard drive" so you need to connect it as a hard drive instead of a disk.

---

### Post by LinuxFan999 on 2012-02-26
> **Ketman said:**
> I've just used Archive Manager, and it seemed to work. At least it said "extracting files", but the result is one .vhd file, which VMWare won't recognize. Nothing with ".iso" suffix.
Virtualbox will recognize .vhd files, and is faster than VMware, so I would recommend trying that. [http://www.virtualbox.org](http://www.virtualbox.org)

---

### Post by Ketman on 2012-02-26
> **LinuxFan999 said:**
> Virtualbox will recognize .vhd files, and is faster than VMware, so I would recommend trying that. [http://www.virtualbox.org]("http://www.virtualbox.org/")

Thanks, but I'll leave it for tomorrow now. I've had a long and  frustrating day with this machine on several fronts. I thought I was  home and dry with VMWare, only to run into a brick wall at the end of  it. I need a good night's sleep. But virtualbox sounds good. If it's  faster than VMWare, then I'll give it a go - tomorrow.

---

### Post by Ketman on 2012-02-27
> **LinuxFan999 said:**
> Virtualbox will recognize .vhd files, and is faster than VMware, so I would recommend trying that. [http://www.virtualbox.org](http://www.virtualbox.org)

  [SIZE=2]I've been through the process of setting up a VM in virtualbox about five times, just in case I've missed anything. The last time I made notes as I went. 

[/SIZE][SIZE=2]1. I click on New. Up comes the wizard. I  press Next  

[/SIZE][SIZE=2]2. I name the new machine "Win95".
[/SIZE][SIZE=2]Under OS_Type I choose "Microsoft Windows", and under Version, "Windows 95". 
I press Next  

[/SIZE][SIZE=2]3. Memory. I leave the default 64Mb. I press Next.

[/SIZE][SIZE=2]4. It says: [/SIZE][SIZE=2][COLOR=Red]
Select a hard disk image to be used as the boot hard disk of the virtual machine. You can either create a new hard disk using the New button or select an existing hard disk image from the drop-down list or by pressing the Existing button (to invoke the Virtual Media Manager dialog).  [/COLOR][/SIZE][SIZE=2][COLOR=Red]If you need a more complicated hard disk setup, you can also skip this step and attach hard disks later using the VM Settings dialog.[/COLOR]

[/SIZE][SIZE=2]Radio buttons give me two choices:[COLOR=Red]
o Create a new hard disk or 
o Use an existing hard disk[/COLOR]  

[/SIZE][SIZE=2]The first is set up as the default, so I leave it as it is. I press Next.  

[/SIZE][SIZE=2]5. Wizard says, 
[COLOR=Red]This wizard will help you to create a new virtual hard disk for your virtual machine.[/COLOR] 
I press Next.  [/SIZE][SIZE=2]

6. I am asked to choose between "dynamically expanding" and "fixed-size storage". I choose the first. I press Next.  [/SIZE][SIZE=2]

7. It says, 
[COLOR=Red]Press the Select button to select the location of a file to store the hard disk data or type a file name in the entry field[/COLOR] 

There's no Select button, but there is an icon to the right of the location window. I click on it.  [/SIZE][SIZE=2]New dialogue box says:[COLOR=Red] 
Select a file for the new hard disk image file.[/COLOR] 

Possibly they mean "select a name". I write "Win95". 
Below it says “[COLOR=Red]Save in folder:"[/COLOR] followed by a drop-down list. The default is a folder called "HardDisks". I leave the default. I click on Save.  

[/SIZE][SIZE=2]8. It goes back to the previous window. My choice is now showing in the Location box. I select the default 2.00 Gb as the size of the virtual disk. I press Next. 

[/SIZE][SIZE=2]9. The next page summarizes what I've done. I click Finish. 

[/SIZE][SIZE=2]10. Next page is much the same. [/SIZE][SIZE=2]

[COLOR=Red]You are going to create a new virtual machine with the following parameters:  

[/COLOR]  [/SIZE][SIZE=2][COLOR=Red]Name: Win95 
[/COLOR][/SIZE][SIZE=2][COLOR=Red]OS Type: Windows 95 
[/COLOR][/SIZE][SIZE=2][COLOR=Red]Base Memory: 64 MB [/COLOR][/SIZE][SIZE=2][COLOR=Red]
Boot Hard Disk: Win95.vdi (Normal, 2.00 GB)  [/COLOR][/SIZE][SIZE=2]

I click Finish again.  

[/SIZE][SIZE=2]I am returned to the main page, where my new machine is shown in the left hand pane. "Win95".   [/SIZE][SIZE=2]

11. It doesn't say what you should do next. So I just double-click on my Win95 icon. Up comes a page, that says:  

[/SIZE][SIZE=2][COLOR=Red]You have started a newly created virtual machine for the first time. This wizard will help you to perform the steps necessary for installing an operating system of your choice onto this virtual machine.
[/COLOR]  
[/SIZE][SIZE=2]I click Next.  

[/SIZE][SIZE=2][COLOR=Red]Select the type of media you would like to use for installation  [/COLOR][/SIZE][SIZE=2][COLOR=Red]Media Type 
 [/COLOR][/SIZE][SIZE=2][COLOR=Red]o CD/DVD -ROM Device [/COLOR][/SIZE][SIZE=2][COLOR=Red]
o Floppy Drive  
[/COLOR][/SIZE][SIZE=2]
[COLOR=Red]Select the media which contains the setup program of the operating system you want to install. This media must be bootable, otherwise the setup program will not be able to start.
[/COLOR] [/SIZE]  [SIZE=2][COLOR=Red]
Media Source : 
[/COLOR] 
[/SIZE][SIZE=2]That's a drop-down menu with just two choices: 

“[/SIZE][SIZE=2]Host HL-DT-ST RW/DVD GCC-4243N (sr0)” or 
 “[/SIZE][SIZE=2]win95.vhd (228.06 MB)”. 

The second of those is my file, the one I extracted with unrar. I select that.  [/SIZE][SIZE=2]I click Next  

[/SIZE][SIZE=2][COLOR=Red]You have selected the following media to boot from:
 Type: CD/DVD-ROM Device
   Source: win95.vhd (228.06 MB)

[/COLOR][/SIZE][SIZE=2][COLOR=Red]If the above is correct, press the **Finish** button. Once you press it, the selected media will be temporarily mounted on the virtual machine and the machine will start execution.
 
Please note that when you close the virtual machine, the specified media will be automatically unmounted and the boot device will be set back to the first hard disk. Depending on the type of the setup program, you may need to manually unmount (eject) the media after the setup program reboots the virtual machine, to prevent the installation process from starting again. You can do this by selecting the corresponding **Unmount...** action in the **Devices** menu.
[/COLOR][/SIZE]  [SIZE=2]
[This is the first indication I've had that they might be referring to a real CD, not just an image file]  [/SIZE][SIZE=2]

I click Finish. It runs.   

[/SIZE][SIZE=2][COLOR=Red]FATAL: No bootable medium found! System halted.  [/COLOR][/SIZE][SIZE=2][COLOR=Red]
[/COLOR] 
I close the virtual machine.  [/SIZE][SIZE=2]Looks like they *were* referring to a real CD. 

I delete “Win95” altogether and start again. This time when I reach step 11, I put a blank CD in the tray to see if that's what it wants. But apparently not. Same result: [COLOR=Red]“FATAL:.....”  [/COLOR][/SIZE][SIZE=1][SIZE=2][COLOR=Red]
[/COLOR] 
I'm out of ideas.

[/SIZE]
[/SIZE]

---

### Post by LinuxFan999 on 2012-02-27
> **Ketman said:**
> [SIZE=2]I've been through the process of setting up a VM in virtualbox about five times, just in case I've missed anything. The last time I made notes as I went. 

[/SIZE][SIZE=2]1. I click on New. Up comes the wizard. I  press Next  

[/SIZE][SIZE=2]2. I name the new machine "Win95".
[/SIZE][SIZE=2]Under OS_Type I choose "Microsoft Windows", and under Version, "Windows 95". 
I press Next  

[/SIZE][SIZE=2]3. Memory. I leave the default 64Mb. I press Next.

[/SIZE][SIZE=2]4. It says: [/SIZE][SIZE=2][COLOR=Red]
Select a hard disk image to be used as the boot hard disk of the virtual machine. You can either create a new hard disk using the New button or select an existing hard disk image from the drop-down list or by pressing the Existing button (to invoke the Virtual Media Manager dialog).  [/COLOR][/SIZE][SIZE=2][COLOR=Red]If you need a more complicated hard disk setup, you can also skip this step and attach hard disks later using the VM Settings dialog.[/COLOR]

[/SIZE][SIZE=2]Radio buttons give me two choices:[COLOR=Red]
o Create a new hard disk or 
o Use an existing hard disk[/COLOR]  

[/SIZE][SIZE=2]The first is set up as the default, so I leave it as it is. I press Next.  

[/SIZE][SIZE=2]5. Wizard says, 
[COLOR=Red]This wizard will help you to create a new virtual hard disk for your virtual machine.[/COLOR] 
I press Next.  [/SIZE][SIZE=2]

6. I am asked to choose between "dynamically expanding" and "fixed-size storage". I choose the first. I press Next.  [/SIZE][SIZE=2]

7. It says, 
[COLOR=Red]Press the Select button to select the location of a file to store the hard disk data or type a file name in the entry field[/COLOR] 

There's no Select button, but there is an icon to the right of the location window. I click on it.  [/SIZE][SIZE=2]New dialogue box says:[COLOR=Red] 
Select a file for the new hard disk image file.[/COLOR] 

Possibly they mean "select a name". I write "Win95". 
Below it says “[COLOR=Red]Save in folder:"[/COLOR] followed by a drop-down list. The default is a folder called "HardDisks". I leave the default. I click on Save.  

[/SIZE][SIZE=2]8. It goes back to the previous window. My choice is now showing in the Location box. I select the default 2.00 Gb as the size of the virtual disk. I press Next. 

[/SIZE][SIZE=2]9. The next page summarizes what I've done. I click Finish. 

[/SIZE][SIZE=2]10. Next page is much the same. [/SIZE][SIZE=2]

[COLOR=Red]You are going to create a new virtual machine with the following parameters:  

[/COLOR]  [/SIZE][SIZE=2][COLOR=Red]Name: Win95 
[/COLOR][/SIZE][SIZE=2][COLOR=Red]OS Type: Windows 95 
[/COLOR][/SIZE][SIZE=2][COLOR=Red]Base Memory: 64 MB [/COLOR][/SIZE][SIZE=2][COLOR=Red]
Boot Hard Disk: Win95.vdi (Normal, 2.00 GB)  [/COLOR][/SIZE][SIZE=2]

I click Finish again.  

[/SIZE][SIZE=2]I am returned to the main page, where my new machine is shown in the left hand pane. "Win95".   [/SIZE][SIZE=2]

11. It doesn't say what you should do next. So I just double-click on my Win95 icon. Up comes a page, that says:  

[/SIZE][SIZE=2][COLOR=Red]You have started a newly created virtual machine for the first time. This wizard will help you to perform the steps necessary for installing an operating system of your choice onto this virtual machine.
[/COLOR]  
[/SIZE][SIZE=2]I click Next.  

[/SIZE][SIZE=2][COLOR=Red]Select the type of media you would like to use for installation  [/COLOR][/SIZE][SIZE=2][COLOR=Red]Media Type 
 [/COLOR][/SIZE][SIZE=2][COLOR=Red]o CD/DVD -ROM Device [/COLOR][/SIZE][SIZE=2][COLOR=Red]
o Floppy Drive  
[/COLOR][/SIZE][SIZE=2]
[COLOR=Red]Select the media which contains the setup program of the operating system you want to install. This media must be bootable, otherwise the setup program will not be able to start.
[/COLOR] [/SIZE]  [SIZE=2][COLOR=Red]
Media Source : 
[/COLOR] 
[/SIZE][SIZE=2]That's a drop-down menu with just two choices: 

“[/SIZE][SIZE=2]Host HL-DT-ST RW/DVD GCC-4243N (sr0)” or 
 “[/SIZE][SIZE=2]win95.vhd (228.06 MB)”. 

The second of those is my file, the one I extracted with unrar. I select that.  [/SIZE][SIZE=2]I click Next  

[/SIZE][SIZE=2][COLOR=Red]You have selected the following media to boot from:
 Type: CD/DVD-ROM Device
   Source: win95.vhd (228.06 MB)

[/COLOR][/SIZE][SIZE=2][COLOR=Red]If the above is correct, press the **Finish** button. Once you press it, the selected media will be temporarily mounted on the virtual machine and the machine will start execution.
 
Please note that when you close the virtual machine, the specified media will be automatically unmounted and the boot device will be set back to the first hard disk. Depending on the type of the setup program, you may need to manually unmount (eject) the media after the setup program reboots the virtual machine, to prevent the installation process from starting again. You can do this by selecting the corresponding **Unmount...** action in the **Devices** menu.
[/COLOR][/SIZE]  [SIZE=2]
[This is the first indication I've had that they might be referring to a real CD, not just an image file]  [/SIZE][SIZE=2]

I click Finish. It runs.   

[/SIZE][SIZE=2][COLOR=Red]FATAL: No bootable medium found! System halted.  [/COLOR][/SIZE][SIZE=2][COLOR=Red]
[/COLOR] 
I close the virtual machine.  [/SIZE][SIZE=2]Looks like they *were* referring to a real CD. 

I delete “Win95” altogether and start again. This time when I reach step 11, I put a blank CD in the tray to see if that's what it wants. But apparently not. Same result: [COLOR=Red]“FATAL:.....”  [/COLOR][/SIZE][SIZE=1][SIZE=2][COLOR=Red]
[/COLOR] 
I'm out of ideas.

[/SIZE]
[/SIZE]
.vhd stands for "virtual hard disk". So you will need to delete the virtual machine and start over, but this time, where it asks you whether you want to create a virtual hard disk or use an existing image, select "use an existing hard disk", then find the .vhd file.

---

### Post by Ketman on 2012-02-27
I can't. There is no browse button that will let you select anything other than what is in the drop-down menu. The only options for "Use an existing hard disk" are four .vdi files, each of 8.5 Kb, that virtualbox itself has created over the course of my experiments today.

---

