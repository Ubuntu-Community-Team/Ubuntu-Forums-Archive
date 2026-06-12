---
title: "How do I install a linux driver/application."
date: 2008-09-24
forum: New to Ubuntu
---

### Post by netnode on 2008-09-24
I have a disc with a linux driver and software for my Uninterrupted Power Supply.

I have no idea on how to load this.  

In windows it just comes up, click a few buttons and it's installed, however, this doesn't seem to be the case in ubuntu.

The instructions that I have no idea on how to implement are &#9830;     
Software Installation (see p47)
  1.Log in as the super-user. 
  2.Insert UPSilon CD in CD-ROM Driver.
    (1)Mount the UPSilon CD into Unix file directory '/cdrom'. For
       instance, in Linux, type:
        # mount -t iso9660 /dev/hdd /mnt/cdrom
         (Please use device name of your system. Reference Appendix
        B for more information.)
    (2)Copy the files in directory '/cdrom' into '/tmp'
        # cp /cdrom/unix/* /tmp
  3.Execute the installation program:
        # cd /tmp
        # chmod 555 install
        # ./install
  4.Select the target system from the menu, and configuration the
     UPSilon (make sure no other process uses the same serial port), the
     installation program will launch the UPSilon daemon process
     automatically.
    Note: If the UPSilon has been installed in the FreeBSD v4.x
            by the ‘UPSilon bsd-3.Z,’ please install the
            “unix/patch/FreeBSD_4.x/compat3.x/install.sh” of the
            setup CD. For even higher version, please update the
            system with ‘compat3.x’ from the WEB site). :lolflag:

The above is all Greek to me.

Can anyone please tell me simply how to get this going? :confused::confused::confused::confused::confused::confused:

---

### Post by Axerthon on 2008-09-24
> **netnode said:**
> I have a disc with a linux driver and software for my Uninterrupted Power Supply.

I have no idea on how to load this.  

In windows it just comes up, click a few buttons and it's installed, however, this doesn't seem to be the case in ubuntu.

The instructions that I have no idea on how to implement are &#9830;     
Software Installation (see p47)
  1.Log in as the super-user. 
  2.Insert UPSilon CD in CD-ROM Driver.
    (1)Mount the UPSilon CD into Unix file directory '/cdrom'. For
       instance, in Linux, type:
        # mount -t iso9660 /dev/hdd /mnt/cdrom
         (Please use device name of your system. Reference Appendix
        B for more information.)
    (2)Copy the files in directory '/cdrom' into '/tmp'
        # cp /cdrom/unix/* /tmp
  3.Execute the installation program:
        # cd /tmp
        # chmod 555 install
        # ./install
  4.Select the target system from the menu, and configuration the
     UPSilon (make sure no other process uses the same serial port), the
     installation program will launch the UPSilon daemon process
     automatically.
    Note: If the UPSilon has been installed in the FreeBSD v4.x
            by the ‘UPSilon bsd-3.Z,’ please install the
            “unix/patch/FreeBSD_4.x/compat3.x/install.sh” of the
            setup CD. For even higher version, please update the
            system with ‘compat3.x’ from the WEB site). :lolflag:

The above is all Greek to me.

Can anyone please tell me simply how to get this going? :confused::confused::confused::confused::confused::confused:
1. We'll do this later, using **sudo**. 
2. Insert it. 
3. It is automatically mounted.
Go to the main menu, **Applications**, **Accesories**, **Terminal**.
Okay, here we write:
```

sudo cp /media/cdrom0/unix/* /tmp/

```
It will ask you for the root password, the one you set up when you installed Ubuntu.
3. Now let's execute the install program:
```

cd /tmp
sudo chmod 555 install
sudo ./install

```
4. Done!

---

### Post by Idefix82 on 2008-09-24
You basically just follow the instructions but some things will be done for you. So you insert the CD, copy the content of the unix directory on the CD into the /tmp folder which you can do from the GUI by clicking on the CD icon on your desktop, selecting the content of the unix folder, hitting Ctrl+c, then browsing to File System->tmp and hitting Ctrl+v,
then you open a terminal and type in line by line
```
cd /tmp
chmod 555 install
sudo ./install
```
and all should be fine.

edit: Axerton (apart from being faster) is right, you will need root privileges to copy the files into tmp so you better follow his advice.

---

### Post by tarps87 on 2008-09-24
You should be able to login to your normal user, put the cd in and it should auto mount then type
```
cp media/cdrom0/unix/* /tmp
```
you may need to do
```
sudo cp media/cdrom0/unix/* /tmp
```
the
```
cd /tmp
```
```
sudo chmod 555 install
```
```
sudo ./install
```
This should start the installation

Edit: beaten to it

---

### Post by lazyart on 2008-09-24
Insert the CDROM
Nautilus should open up a window automatically. If not, go to you menu and select Places>Computer and open the CDROM
Right click on the unix directory and select copy.
Open your home folder
Right click and select paste

Now open a terminal window
Type```
sudo chown netnode unix -R
```substituting your username for netnode
```
cd unix
chmod 555 install
sudo ./install

```
Now follow step 4.

---

### Post by medic2000 on 2008-09-24
2-)Ubuntu automounts the cdrom you do not need to mount manually.(so you don't need to log-in as super-user)

(2)You can copy the drivers anywhere you want.Make a directory in desktop named Upsilon and copy the content just by doing right click copy,then paste.

3-) So now we copied the files from cd-rom.Unlike Windows, Ubuntu prevents programs executed automatically(you can not know if it is virus,spyware etc...)
  The point is to make the install script of driver executable.For this:

-Open a terminal.(you can press alt+f2,write gnome-terminal) 
-Change directory by typing(if the program is in desktop):"cd /home/your_username/Desktop/name_of_driver_directory
-Write "sudo(makes you super-user temporary) chmod 755(changes the mode of file the executable as if say simply) install(name of the file)" 
"sudo chmod 755 install"
-Now run the install program by typing "./install"

Note: Normally installing a program in Ubuntu is so much simpler. By using "adept package manager"

And for basics of Ubuntu visit:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by netnode on 2008-09-24
> **medic2000 said:**
> 2-)

Note: Normally installing a program in Ubuntu is so much simpler. By using "adept package manager"

And for basics of Ubuntu visit:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Thanks for all the help, how do I get the adept package manager please?

---

### Post by Sef on 2008-09-24
> netnode 	 		

 		 	Quote:
 	 	 		 			 				 					Originally Posted by **medic2000** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5846220#post5846220") 				
 				[I]2-)

Note: Normally installing a program in Ubuntu is so much simpler. By using "adept package manager"

And for basics of Ubuntu visit:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)[/I]
 			 		 	 	 
Thanks for all the help, how do I get the adept package manager please? 	

Medic2000 is wrong.   If you have Ubuntu, there is synaptic package manager.   System > Administration > Synaptic Package Manager.   Adept is for Kubuntu.  Synaptic and Adept are both package managers.  

Now the real easy way to install is Applications > Add/Remove.  It has many of Synaptics packages.

---

