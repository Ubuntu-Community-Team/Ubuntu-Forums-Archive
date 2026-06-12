---
title: "HOW TO WORKAROUND BROKEN CUPS 1.2 Sharing with CUPS 1.1"
date: 2006-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by tagra123 on 2006-08-27
HOW TO WORKAROUND BROKEN CUPS 1.2 Sharing with CUPS 1.1 using samba

DAPPER CUPS 1.2 does not play well with CUPS 1.1.X

I tried this workaround because I needed to share with a windows Virtual Machine from a Windows box, but it works with other Ubuntu machines too, The printing had worked fine using Breezy but something in Dapper broke the sharing which had been working fine under cups 1.1.X (BREEZY)

My solution was to involve samba. Even though samba has to work with cups it appears to get past the sharing problems. Of course you have to have a working printer to share.

Here are the steps:

Install cupsys (It should have been installed as part of the default installation)

```
sudo apt-get install cupsys*
```

Add a new printer using the Panel Menu: System > Administration > Printers

Click on Add Printers and follow the wizard screens.

**Print a Test Page. _If the test page works continue on._**



Sharing with Samba instead of IPP or HTTP (CUPS)

Install Samba
```

sudo apt-get install samba smbfs
```

Next, add a samba user ( If you are sharing files you may have already done this)

```
sudo smbpasswd -a YourUserName
sudo gedit /etc/samba/smbusers


```

Add the following line(This might be the only line in that file)

```
system_username = "YourUserName"
```

Save the file and exit the text editor.

Next, make a backup of smb.conf

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.original.backup
```

Edit the smb.conf file 


```
gedit /etc/samba/smb.conf
```


Uncomment these two lines:

 [B]printing = cups
 printcap name = cups[/B]


*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_
ADDED Jan-08-2006
In windows the status of the printer may display "Unable To Connect" but the printer will still print.

To avoid seeing this message

Find the line in smb.conf that Reads 
[B]
Comment = All Printers[/B]

After that line add

**use client driver = yes**

*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_*_


Save the file and exit the text editor.

Next make sure that the Domain Name of all computers that are going to be using this printer are set to the same name. Since the Windows Virtual Machine was already set for the MSHOME network thats what I used too. No flames please. Any name will work here as long as all are in the same domain name

To check or change the domain from the Panel Menu Select: System > Administration > Networking

Click on the "General" Tab

Make Sure Domain name :  is set to MSHOME (Unless you chose another name)


Restarting cupsys should make everything accessible, if not reboot the computer.

Try 

```
sudo /etc/init.d/cupsys restart

```
or Reboot.


If you are having trouble with connecting to or accessing the shared printer then make sure your Domain Name matches on the computers is set Correctly and that your firewall (IPTABLES or FIRESTARTER) is allowing samba connections.


**Set the other computers to use the shared printer:**

_For WINDOWS:_
Once windows can see the printer  then you will want to load the drivers using windows ADD PRINTER from the Control Panel. 

_FOR UBUNTU:_

Using the Panel Menu Select: System > Administration > Networking

Click on the "General" Tab

Make Sure Domain name :  is set to MSHOME (Unless you chose another name)

Next

Using the Panel Menu Select: System > Administration > Printing

Select Add Printer.

Choose Network Printer (Windows SMB)
Fill in the username and password, host and printer information.

Click on OK and print a test page.

NOTE:

I would have preferred to use CUPS, instead of samba, to do this exactly as done in Breezy by simply typing [http://192.168.1.X/printer/X125](http://192.168.1.X/printer/X125)  as the network printer but it just doesnt work right now.


For more information about setting up samba without  authenication  or to share files see:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Dapper#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

---

### Post by tagra123 on 2006-08-27
Yes you can share printers through samba -- as far as the other computers know its a printer on a windows machine

The two lines I was referring to are in the smb.conf

Edit the smb.conf file


```
gedit /etc/samba/smb.conf
```



Uncomment these two lines (about mid way through he smb.conf file:

It will look like this:
```
#printing = cups
#printcap name = cups
```


Make it look like this

```
printing = cups
printcap name = cups
```

Save the file and exit the text editor.

Read through the rest of this and the link above if you are having trouble.

It should only take 5 to 10 minutes following the directions in the how to.



Next make sure that the Domain Name of all computers that are going to be using this printer are set to the same name. Since the Windows Virtual Machine was already set for the MSHOME network thats what I used too. No flames please. Any name will work here as long as all are in the same domain name

To check or change the domain from the Panel Menu Select: System > Administration > Networking

Click on the "General" Tab

Make Sure Domain name : is set to MSHOME (Unless you chose another name)


Restarting cupsys should make everything accessible, if not reboot the computer.

Try

Code:

sudo /etc/init.d/cupsys restart

or Reboot.

---

### Post by MetalMusicAddict on 2006-09-07
This all works fine for printing the test page but I cant print from Firefox.

---

### Post by tagra123 on 2006-09-09
> **MetalMusicAddict said:**
> This all works fine for printing the test page but I cant print from Firefox.

If you can get the test page to print and follow the steps to share than you should be able to print from firefox on the machine that is sharing the printer.

The other computer will need to be set up to use the shared printer and then you can use the print dialog from firefox to print to that printer.

---

