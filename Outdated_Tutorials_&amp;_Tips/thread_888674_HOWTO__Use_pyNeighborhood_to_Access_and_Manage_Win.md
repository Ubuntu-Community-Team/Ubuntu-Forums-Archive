---
title: "HOWTO:  Use pyNeighborhood to Access and Manage Windows and Linux Shares on a Network"
date: 2008-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by MatthewPlanchard on 2008-08-13
Hello, all.

pyNeighborhood is a really great program that allows you to access your local network, mounting and unmounting shared folders so that you can access them from your computer.  It works with both Windows and Linux shares, and requires no command line input.  It is available in the repositories, but requires a little bit of setup to get working properly. I just got it set up and working on my computer, so here is my how to to get pyNeighborhood up and running properly.


_Step One:  Install pyNeighborhood_

Open up Synaptic Package Manager and do a search for samba.  Mark pyNeighborhood, samba-common, smbclient, and smbfs for install.

Apply changes and close the package manager.


_Step Two: Create a Folder for Mounting Shares_

Open up your home folder by going to Main Menu -> Places -> Home Folder.

Click on File, Create New Folder (Ctrl + Shift + n) and name the new folder 'mnt' without quotes.  In the new 'mnt' folder, create another new folder called 'lan' without quotes.

Close the file manager.


_Step Three:  Configure pyNeighborhood_

Open pyNeighborhood through Main Menu -> Internet -> pyNeighborhood

Go to Edit -> Preferences

in the General tab, change the Mount folder to read

```
/home/[your user name]/mnt/lan
```

Check the box that says 'Remove mount points after unmount'

Note: if you require a username and password to log into your networks shared folders, you can uncheck 'Always use anonymous login' and enter that here.

Next, navigate to the Network tab.

If you need to specify a Workgroup in order to access your network, here you can uncheck 'Always use msbrowse' and enter the name of the Workgroup.

Also, check the box 'Try to retrive IP address when adding a machine from the group browser'

Navigate to the SMB tab.

Make sure that 'Enable SMB' is checked, and look at the current Mount and Unmount commands.  They should say 'smbmount' and 'smbumount' respectively.

These commands have to be run with root priviledges.  Add the word 'sudo' to the beginning of each command, withou the quotes, so they read:

```
sudo smbmount
sudo smbumount
```

Now navigate to the CIFS tab, and do the same thing here that you did under the SMB tab:

Ensure that 'Enable CIFS' is checked

Add 'sudo' to the beginning of the 'mount.cifs' and 'umount.cifs' commands so they read

```
sudo mount.cifs
sudo umount.cifs
```

Now navigate to the File Managers tab

Highlight the 'xterm -e mc' entry and click on the button that says' Remove'

Now click on the Add... button and add

```
nautilus
```

Note: You can replace nautilus with your file manager of choice (thunar, pcmanfm, dolphin, etc.)

Once you have added your file manager, click 'Ok' at the bottom of the preferences menu.

pyNeighborhood should now be configured to work properly with your network


_Step Four:  Using pyNeighborhood_

To mount shares, start in the left pane, where it should say 'Groups'

Right click and click 'Scan'

Your local workgroup should appear here, so right click on it and click 'scan' to show the machines in your workgroup

Choose a machine to browse, right click on it, and click add. (you can also double click)

Try to retrieve the machine's IP address if it is not already entered, and then click 'Ok'

The machine should now appear in the right hand pane.

Right click on the machine and click 'scan' to show the machine's shared folders.

To mount a share, right click on it and click 'mount -> mount as SMB' (note: if SMB does not work the share will automatically be mounted through CIFS).

Now navigate to the 'Mounts' tab, where you will see your freshly mounted share.

Right click on the share and click 'File Manager' to view the share as if it were a folder on your own computer!

Repeat the process for any other shares you wish to browse.

And that's it!


Note:  to allow Windows or Linux users to access your shared folders without a user name and password, you will have to edit your /etc/samba/smb.conf file to contain the following:

```
security=share
```


_Note: Potentially Hazardous gkSudo Access Fix_

There is another tutorial on these forums that recommends altering pyNeighborhood's main menu command to read 'gksudo pyNeighborhood' and running the whole program as root.  The problem with this is that it opens your file manager with root access as well, allowing for potentially hazardous file altering and deletion.

If you have previously followed those instructions (found [_here_]("http://ubuntuforums.org/showthread.php?t=500734&highlight=pyNeighborhood") and elsewhere on the internet) and you would like to undo them, complete the following steps:

Go back through Main Menu -> System -> Preferences -> Main Menu, go to the Internet tab, right click on the pyNeighborhood tab, and click on properties.

The entry for Command should currently say 'gksudo pyNeighborhood' without the quotes.

Change it so that it says 'pyNeighborhood' or simply erase the 'gksudo' part, again without quotes.

If you changed the shortcut in system tools as well, you can change that one back as well.

Close the Main Menu editor.



Post here with whether or not this works for you, along with any relevant specifics if it's not working.

---

### Post by foxy123 on 2008-08-16
It does not work for me. The problem I guess is that although sudo is added to the mounting commands in Preferences, it does not ask for password.

---

### Post by haydemon on 2008-09-03
It doesn't work for me. I followed all the steps, but it fails to scan the groups. The only thing that there was no instruction for was on the Network tab, "client command" and "network command" the default is "smbclient" and "nmblookup" respectively; I didn't change those values. Could that be the problem? Thanks!

---

### Post by NTolerance on 2008-09-04
Can this program make mounts persistent after a reboot?

---

### Post by haydemon on 2008-09-04
> **NTolerance said:**
> Can this program make mounts persistent after a reboot?
I don't understand the question. :confused: (I'm still somewhat of a newbie.)

---

### Post by NTolerance on 2008-09-04
> **haydemon said:**
> I don't understand the question. :confused: (I'm still somewhat of a newbie.)

Do the shares stay mounted after you reboot your system?  Or do you have to mount them again?

---

### Post by Crafty Kisses on 2008-09-05
Nice tutorial, I give you props on this one man. :)

---

### Post by haydemon on 2008-09-05
> **NTolerance said:**
> Do the shares stay mounted after you reboot your system?  Or do you have to mount them again?
Shares do not stay mounted. There is nothing in the Groups. They never mount in the 1st place.

---

### Post by shankhs on 2008-09-05
Ok I installed pyNeighborhood and I accessed it using Applications->Internet->pyNeighborhood.
But I am not getting any "edit" tab here????!!!!!:confused:

Attached here is the pyNeighborhood.

---

### Post by shankhs on 2008-09-06
Nobody has any solution?
Am I doing something wrong?

---

### Post by Serneg on 2008-11-01
I have had a problem with pyNeighborhood failing to scan workgroups unless always use anonymous logins is checked, but then failing to scan individual computers unless using a specific user.  Does this option always have to be changed between scanning workgroups and computers?

---

### Post by davej45 on 2008-12-23
Here are my Notes for Setting up pyNeighborhood 0.4 on Ubuntu 8.10 successfully:

[B][U]A. Setting It All Up
[/U][/B]

Open a terminal window:

Code:

   [COLOR="Blue"]$ cd /mnt
   $ sudo mkdir lan
   $ sudo chown root:plugdev lan
   $ sudo chmod g+w lan
   $ sudo chmod +s /usr/bin/smbmount
   $ sudo chmod +s /usr/bin/smbumount
   $ sudo chmod +s /usr/bin/mount.cifs
   $ sudo chmod +s /usr/bin/umount.cifs[/COLOR]

(The last two lines were added in from the original post, since I forgot to put them in! - dlj)

Close the terminal window.


**_B. Configure pyNeighborhood_**

Open pyNeighborhood through Main Menu -> Internet -> pyNeighborhood

Go to Edit -> Preferences

in the General tab, change the Mount folder to read

Code:

[COLOR="Red"]/mnt/lan[/COLOR]

Check the box that says 'Remove mount points after unmount'

Note: if you require a username and password to log into your networks shared folders, you can uncheck 'Always use anonymous login' and enter that here.

(So far, for me at least, anonymous login seems to work just fine for everything)

Next, navigate to the Network tab.

If you need to specify a Workgroup in order to access your network, here you can uncheck 'Always use msbrowse' and enter the name of the Workgroup.

look at the current Client and Lookup commands. They should say 'smbclient' and 'nmblookup' respectively.

Also, check the box 'Try to retrive IP address when adding a machine from the group browser'

Navigate to the SMB tab.

Make sure that 'Enable SMB' is checked, and look at the current Mount and Unmount commands. They should say 'smbmount' and 'smbumount' respectively.


Now navigate to the CIFS tab, and do the same thing here that you did under the SMB tab:

Ensure that 'Enable CIFS' is checked and look at the current Mount and Unmount commands. They should say 'mount.cifs' and 'umount.cifs' respectively/

Now navigate to the File Managers tab

Highlight the 'xterm -e mc' entry and click on the button that says' Remove'

Now click on the Add... button and add

Code:

[COLOR="Red"]nautilus[/COLOR]

Note: You can replace nautilus with your file manager of choice (thunar, pcmanfm, dolphin, etc.)

Once you have added your file manager, click 'Ok' at the bottom of the preferences menu.


Scan Groups, add entries as previously discussed in this topic, and mount as smb. Open the file browser while in pyNeighborhood and you will go right to your mounted share. When you unmount, the mount points are deleted. 


***Thanks to Matthew Planchard, for his original advice here on the Ubuntu Forums-***
[http://ubuntuforums.org/showthread.php?t=888674](http://ubuntuforums.org/showthread.php?t=888674)

***Thanks to Daniele Salatti at Salatti.NET-***
[http://www.salatti.net/pyneighborhood-the-gui-frontend-for-samba-tools/](http://www.salatti.net/pyneighborhood-the-gui-frontend-for-samba-tools/)

***Thanks to Warren Butler @ grumpymole-***
[http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html](http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html)

[B][U]BTW, for those that asked-
[/U][/B]
If you have Samba installed and properly configured, permanent mounts can also be created by making the appropriate entries in your fstab-


First, make sure you have installed Samba, and made the appropriate edits to the smb.conf file. Also make sure the appropriate Samba daemons (nmbd and smbd) start when you boot.

Code:

[COLOR="Blue"]$sudo mkdir /home/{yourusername}/LANMOUNT/{sharename}
$sudo cp /etc/fstab /etc/fstab.bu
$sudo gedit /etc/fstab[/COLOR]

at the bottom enter the following line:

Code:

[COLOR="Blue"]\\{networkaddress}\{share} /home/{yourusername}/LANMOUNT/{sharename} smbfs  defaults  0  0[/COLOR]

Example:
\\192.168.0.8\shares  /home/myname/LANMOUNT/MYSHARE  smbfs  defaults  0  0

save fstab and when you reboot- your shares will not only be available, you get a nifty disk drive icon on your desktop which will take you to your shares using your default file browser.

You can add as many lines as you have permanent shares to be mounted this way, using different values for {networkaddress} ,{share} , and {sharename} as needed.

davej45

---

### Post by haydemon on 2008-12-23
---------------- Now playing: [Mozart, Wolfgang Amadeus - Sonata For Violin & Piano No. 20 In C Major, K. 303 (K. 293c)](http://www.foxytunes.com/artist/mozart%2c+wolfgang+amadeus/track/sonata+for+violin+%26+piano+no.+20+in+c+major%2c+k.+303) via [FoxyTunes](http://www.foxytunes.com/signatunes/)Does this work with Ubuntu 8.04 too?

---

### Post by davej45 on 2008-12-23
haydemon-

I can't think of any reason why not, since all of the terminal commands are standard linux commands for all distributions. 

Actually, I certainly hope that the method for setting up permanent mounts works in 8.04, since I am planning on using it to set up a local web/ftp server in the near future.  But then, since I cobbled 8.10 up a bit in order to install webmin, and will do the same on the server running 8.04, it could be that might have had an impact on how/why it all works, but I can't really think of a reason why it would. 


I did just notice that I should have added two additional commands in the first terminal session, seems I forgot to write them down in my original notes.

The correct sequence of commands for section A should have been:

[B]A. Setting It All Up
[/B]

Open a terminal window:

Code:

[COLOR="Blue"]$ cd /mnt
$ sudo mkdir lan
$ sudo chown root:plugdev lan
$ sudo chmod g+w lan
$ sudo chmod +s /usr/bin/smbmount
$ sudo chmod +s /usr/bin/smbumount
$ sudo chmod +s /usr/bin/mount.cifs
$ sudo chmod +s /usr/bin/umount.cifs
[/COLOR]
Close the terminal window.


If I can figure out how to edit the original post I will make the needed additions...

davej45

---

### Post by Xhip on 2009-02-05
Hello!

I think I got a way of running pyNeighborhood as a root (to avoid problems on mounting and unmounting the shares) and still run the file manager without root privileges, avoiding all potential problems related to it...

Running pyNeighborhood as a root, on the File Managers tab, I simply put this command (running Xubuntu here):

sudo -u <username> Thunar

This launches Thunar not as a root, but under user privileges, avoiding all potential dangers related...

Can you give your feedback on this? Here in my box, seemed to work without any problems...

Regards!

---

### Post by paulkaye on 2009-02-17
It looks like noone has answered / has been able to answer NTolerance's original question: **Is it possible to prevent mounts from being lost upon restart? **
There was an answer that I (as a newbie) didn't understand which used the command line but the question was really: **Can this be done purely with pyNeighborhood?**
Can anyone help me/us?
Thanks in advance,
Paul

---

