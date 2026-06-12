---
title: "Where is &quot;System&quot; (total newbie question, I know)"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by kristamaranatha on 2012-01-14
I've been using Ubuntu for 3 days and am pretty ignorant to the workings of it. I am trying to share a printer from my Windows XP computer and am trying to follow these instructions ([http://www.unixmen.com/how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui/](http://www.unixmen.com/how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui/)). I am trying to access the Samba GUI and can't seem to get there.  ("First open GUI samba  server configuration tool by going to [B]System&#8211;> Administration&#8211;>Samba") Where is System? 

Thanks!
[/B]

---

### Post by lechien73 on 2012-01-14
Did you install the Samba GUI?

```
sudo apt-get install system-config-samba
```

When you have installed that, you can find Samba by clicking on the Ubuntu logo on the sidebar and typing *samba*. The **System** menu has been replaced in Ubuntu 11.x, so the guide is incorrect (even though the title says it's for 11.04 and 11.10)

It will prompt you to put in your Ubuntu password, and then bring up the configuration window.

Click **Preferences -> Server Settings** and set the workgroup to be the same as your Windows workgroup. Hopefully this will get your printer working (I'm posting here, rather than replying to the other thread :))

---

### Post by kristamaranatha on 2012-01-14
Okay... where is Preferences? ](*,)

(If you're talking about the Preferences menu in Samba Server Configuration, my problem is that when I click on Samba and type in my password nothing happens)

---

### Post by lechien73 on 2012-01-14
Hokay...it was supposed to be the preferences menu in Samba, but if it doesn't work....

Try the following to set your workgroup:

Open a terminal window
Type:

```
gksu gedit /etc/samba/smb.conf
```

Enter your password when requested.

In the text editor, scroll down until you find *workgroup = WORKGROUP* line. Change this to the name of your workgroup.

Save the file and quit from the text editor. Now, in the terminal window run:

```
sudo restart smbd
```

Which will restart Samba, and the new configuration settings will take effect.

---

### Post by Drowz0r on 2012-01-14
Don't forget, even if you share the printer you'll need ubuntu drivers for it :)

I found this most tricky with older printers.

---

### Post by kristamaranatha on 2012-01-15
So where do I find the driver? I have found that my printer driver is incompatible with my Windows 7 laptop, although it works with all my XP computers

Samba still not working... is there a way to uninstall and reinstall to see if I can get the GUI to work?

---

### Post by Paqman on 2012-01-15
> **kristamaranatha said:**
>   ("First open GUI samba  server configuration tool by going to [B]System–> Administration–>Samba") Where is System? 


The guide you're following is for an old version of Ubuntu. We used to have menus at the top of the screen ("Applications", "Places" and "System"). In the new interface you just hit your Windows key and type the name of what you want, in this case the Samba preferences. So just start typing "Samba" and it should come up.

As for drivers, check in Additional Drivers. If there's nothing there, tell us exactly what model of printer you have.

---

### Post by kristamaranatha on 2012-01-15
When I type in Samba it shows up, but when I click on it NOTHING happens.

I installed the updated drivers from hpliopensource.com and the printer works now if I plug it in directly, but I would really like to get it printing from the network as it is plugged into the PC on my desk (running XP)

---

### Post by mastablasta on 2012-01-15
you need to install the printer in linux under printers. when it asks you for the printer location you select printer connected via SAMBA and then you need to type in the path to printer. to see samba shares (the path) use 

smbtree 

command in terminal.

---

### Post by JRV on 2012-01-15
See Next post.

---

### Post by JRV on 2012-01-15
There is no need to mess with samba to install a network printer located on a Windows XP system.

 This will work if you have not messed up samba, and the driver is available in Ubuntu.

These instructions are for Ubuntu 11.10.(Oneiric)

First load XP and make sure the printer is shared.

On the Ubuntu system, click the icon in the upper right corner.
Click System Settings.
Click Printing.
Click Add.
Click the little triangle to expand Network Printer.
Click Windows Printer via SAMBA.
Click Browse.
Locate your printer, highlight it, and click OK.
Select Authorization method and click Verify.
(It should tell you that the Printer share is accessable.)
Click Forward.
Locate your printer and select the driver.
Click Forward.
Change the name if you want to, and click Apply.

---

