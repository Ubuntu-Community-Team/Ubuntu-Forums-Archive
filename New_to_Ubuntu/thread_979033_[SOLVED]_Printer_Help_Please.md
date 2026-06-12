---
title: "[SOLVED] Printer Help Please"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by pjtb on 2008-11-11
I have installed Ubuntu 8.10 on desktop PC as dual boot - no problems and as a result decided to install 8.04.1 on Acer Aspire One following directions on this site. Everything works except printer through XP over wireless network.

I have followed the recommended method

System-Administration-Printing-New Printer-Windows printer via Samba.

Then in the 'smb:\\' box I used 'Browse', Found the printers using this method and installed drivers.

Then 'Test Print' - nothing gets printed.

So I have uninstalled and followed the same method for finding the printer this time using 'Verify' prior to installing drivers.

I get the message 'Inaccessible - The printer share is not accessible'

I have enabled share on the PC and can print from my other laptop running XP. I could print from the Linpus Lite originally installed on the Acer One. I have also tried setting the XP to static IP address and typing 'IP address/(printer_name)'. I have search through the threads and followed some advice but nothing seems to resolve this issue.

I am hoping there is a simple solution to this problem as this is the only issue I have had with Ubuntu since installing this week.

Any help will be gratefully recieved - Thank you in anticipation.

---

### Post by NewJack on 2008-11-12
First, what printer are you using?  I don't use Samba, but maybe it has to do with incompatibility with Linux.  You can go here: [http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting) and check to make sure your printer will work with Linux. 

Hope that helped.

---

### Post by pjtb on 2008-11-13
> **NewJack said:**
> First, what printer are you using?  I don't use Samba, but maybe it has to do with incompatibility with Linux.  You can go here: [http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting) and check to make sure your printer will work with Linux. 

Hope that helped.

Thanks for the reply - I was tempted to 'bump' the post due to the shear amount of traffic on this site - obviously a popular site.

I use an OkiB4100 laser for which I have the 'ppd' file and this works with UBUNTU on my main PC and an HP 5740 for which the driver is available in cups.

Is there an alternative to Samba? If so, please, advice so that I can try an alternative. Like I say, I can see the printers through samba but cannot access them.

---

### Post by superprash2003 on 2008-11-13
hope these help
1) To setup network printer in ubuntu - [http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html)
2) To connect to a network printer in ubuntu - [http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html](http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html)

---

### Post by pjtb on 2008-11-13
Thanks superprash2003 - I think I used the guide when first installing.

Using your second link I can get through the whole process, but when I try to print anything (including test print), nothing happens. Going through again and trying 'Verify' at step 8 I get the 'Inaccessible - The printer share is not accessible'.

In fact I cannot access the shared folder on the XP machine either. Although I was able to on Linpus Lite on the same machine and my other PC's. I have used the account details in step 8 also - to no avail.

I have checked for compatibility thanks to NewJacks post also.

Any thoughts?

---

### Post by steve-shinn on 2008-11-13
I suspect the IP tables (Firewall) need modifying to allow other pcs to connect to your Ubuntu box.

Use UFW (uncomplicated firewall)

---

### Post by superprash2003 on 2008-11-14
are you able to ping the xp machine from ubuntu via ip?? the xp machine has the printer right?

---

### Post by Kellemora on 2008-11-14
Hi PJTB

Type smbtree in your terminal, this should show ALL shared files and printers, etc.  Plus the names of the computers.

If you don't have smbtree then type to install:
```
sudo apt-get install smbtree
```

While your at it also install smbclient, same code, just replace smbtree with smbclient.

You can do this also from Synaptic which might be easier for you.
And while there, if you see a checkmark in front of smbfs, remove it.

Make SURE the printer is shared (which it obviously is if you are using it from another computer), but if it does not show using smbtree, unshare it and reshare it again.

Now, if you CAN see the printer in smbtree and you cannot print to it.  You can try restarting Samba or just reboot your computer.

There is usually no need to mess with the smb.conf file you see mentioned so often here.  If you are using Gnome, Nautilus looks to the file /var/lib/samba for the configuration file, which is a Binary File and cannot be edited by humanoids.

This may not be accurate, but it's how I picture it:
One boot it reads the /var/lib/samba file.
Two boots within a short period of time, is like a force to read the smb.conf file.  
However, if you wait a long time before rebooting again, it will once again read the /var/lib/samba file which is unchanged.
The only way I've found to get this file to update itself is to do three boots within a short period of time.
1st boot reads /var/lib/samba and starts up.
2nd boot says, what's up here, and instead reads smb.conf
3rd boot rewrites /var/lib/samba with smb.conf
As I said, this may not be accurate, but it's how it appears to be working to me though.
I've been able to fix nearly every networking problem I've had by doing three boots within a short time frame.  Sometimes without making changes to smb.conf, sometimes I have to if somethings not just right there.

TTUL
Gary

---

### Post by pjtb on 2008-11-14
Thanks - steve-shinn/superprash2003/Kellemora - Appreciated.

I have run smbtree and get the following output:

WORKGROUP
        \\PETER-LAPTOP                peter-laptop server (samba, Ubuntu)
                \\PETER-LAPTOP\HPDeskje       HP Colour on Home PC
                \\PETER-LAPTOP\OKIB4100       OKI Laser on Home PC
                \\PETER-LAPTOP\PDF            PDF
                \\PETER-LAPTOP\IPC$           IPC Service (peter-laptop server (Samba, Ubuntu))
                \\PETER-LAPTOP\print$         Printer Drivers
MSHOME
        \\HOME-##########             Home
Error connecting to 195.238.237.136   (No route to host)
cli start connection: failed to connect to HOME-##########<20> (195.238.237.136) . Error NT_STATUS_HOST_UNREACHABLE

This is a good deal more info than 'Verify' in printer setup gave me, hopefully this will provide the route to a solution (with your help?).

Obviously this is not my IP address so it looks as though it may be looking for the wrong system. I don't know how to tell samba to look at my IP. 

Also I don't know how to use smbclient I assume some line commands may help the situation.

---

### Post by Kellemora on 2008-11-15
Hi PJTB

OK, smbtree proves that your printer is SHARED and VISIBLE on the Network.

Like you said, those are some weird IP numbers there!

Go to the System drop down box, to Administration then select Printing.

The first two lines under Description and Location can be anything you want them to be to make them easy to recognize, in other words unimportant to functioning.

The next line Device URI is VERY IMPORTANT!!!!

It should start with smb://

I don't know what SHARE NAME you gave to your printer, but if it's OKIB4100, your line should read like this, based on what I see above.

smb://WORKGROUP/PETER-LAPTOP/OKIB4100

Remember, where I have OKIB4100 might be different?

Give that a try and I'll check back tomorrow.

TTUL
Gary

---

### Post by pjtb on 2008-11-16
Thanks Kellamora for your continued help.

'PETER-LAPTOP' is the unit I am trying to connect to the printers from.

The network I am trying to connect through is the //MSHOME/HOME-########## and I have tried to connect through smb://MSHOME/HOME-##########/OKIB4100 in settings (I can even browse through to it using 'windows share via samba'). However, it still won't print.

If I now run smbtree I get the same output as before.

Running SMB4K - I can see the printers on the network and the correct IP address but when I try to print from here by double clicking on the printer and selecting a pdf file to print I get a similar message to the smbtree output including that strange IP address. However, using SMB4K I can access the shared documents folder on the XP machine. It all very strange!

Any further help greatly appreciated

---

### Post by pjtb on 2008-11-16
Sussed it!

Using the IP address shown (not the IP I had set myself?) in SMB4K and the name of the printers in XP for sharing I typed the following in URI:

smb://###.###.###.###/OKIB4100

et voila! it worked. I repeated for the colour printer and again worked first time!

Thanks to all that have helped - I appreciated the time spent to assist me. Now how do I marked this thread as solved?

---

### Post by Kellemora on 2008-11-16
Hi PJTB

Glad you got it working!

To mark a thread solved, in RED at the top is a drop down titled THREAD TOOLS, at the bottom of this drop down listing is the words Mark Thread Solved or just Marked Solved, don't remember which.  
You cannot see this IF you are not the author of the thread you are in at the time, which is why I can't give you the exact wording right now.

And You are Welcome my friend!

TTUL
Gary

---

