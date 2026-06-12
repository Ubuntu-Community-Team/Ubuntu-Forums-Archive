---
title: "HOWTO: Brother HL-2070N network install"
date: 2005-09-23
forum: Outdated Tutorials &amp; Tips
---

### Post by hangfire on 2005-09-23
I bought this printer to share on the network, and decided I would try to get it installed first on Linux. It took a little figuring out but here's what I got.

1. Unpack, install drum, plug in, turn on. Print test page. Turn off, hook up to network, turn on.

2. Go to your Router's admin web page (usually 192.168.0.1) and look at attached devices. What you are looking for is the DHCP address of the printer. Reserve that address for that printer. This keeps the printer from moving around if that DHCP address is reassigned while the printer is turned off. Remember this IP.

3. In your favorite web browser, go to the web address for the printer (in my case, [http://192.168.0.4)](http://192.168.0.4)). Change the passwords. At first it seems that you need the password to change the password. However when you fail to log in you'll get a help screen explaining the default usernames and passwords.

4. Download brhl2070nlpr_1.1.2-3_i386.deb from [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

5. Download cupswrapperhl2070n_1.0.0-1_i386.deb from [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

6. Run:
    sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
    sudo dpkg -i brhl2070nlpr_1.1.2-3_i386.deb
    sudo dpkg -i cupswrapperhl2070n_1.0.0-1_i386.deb

7. Bring up CUPS setup (In KDE this is CC->Peripherals->Printers, Admin Mode). Delete annoying USB printer entry.

8. Add network printer, using the IP address you remembered from step 2. For example:

```
socket://192.168.0.102:9100
```
or maybe
```
socket://192.168.0.102
```

9. Print test page, enjoy your new networked printer, set up without help from any other OS.  :razz:

**8 Feb 2010 Note**- Thanks for everyone's comments. I tried the 2060 driver and had problems with it, then and now, thus this how-to.

---

### Post by hangfire on 2005-09-26
Some have asked questions off-line, I'll try to summarize the answers here.

*Why didn't I just scan for the printer on my LAN as part of the install process?*

 I did. The problem is, the new printer, even though it gets an IP addr from DHCP, doesn't respond yet to queries on port 9100. The printer arrives in some kind of Demo mode, where you can hit the Go button and it prints a splash page. In this Demo mode, the printer doesn't respond to port 9100 (yet).

The Windoze drivers do an SNMP broadcast, looking for Brother printers amongst the replies. My procedure allows you to set up and get the printer to print that important first page, resetting the Demo mode. After that, new Linux driver installs will auto-detect the printer.

So, if you've already set up the printer under either Windoze or Linux, it will autodetect on a scan, but besides, you probably already know its IP anyway.

*Why do I have to install Brother's propriety drivers? Can't I just copy the .PPD file from the CDROM and use either the HL or PCL6 Open Source driver?*

Yes, you can do it that way.

*What are the Gnome setup steps for Step 7 & 8?*

7. Bring up the printing folder (System -> Administration -> Printing). Delete annoying USB printer entry.

8. Configure HL2070N by right clicking and choose "settings" and then select "connection" . Choose cups and type in your IP address from step 2.

*Thanks to _kresten for Gnome help.*

*Why reserve (lock) the IP address of the printer in step 2? Shouldn't you do that in the printer's Web setup, setting it to static?*

The Windoze drivers find the printer via SNMP each bootup, so if it changes its IP address it is still found. CUPS expects it to stay at that IP address. This is best done in the router/DHCP Server. Setting it to static in the printer may guarantee it always comes up on that address, but it doesn't guarantee that the DHCP Server won't also give that address to another device, creating a conflict.

HF

---

### Post by _kresten on 2005-11-22
Nice howto!

>  *What are the Gnome setup steps for Step 6?*

I don't know, perhaps a Gnome user can fill us in.

I suppose that you mean Step 7? If so, I can tell you what to do in Gnome. I have a danish Ubuntu, so it'll be my translation...

7. Bring up the printing folder (System -> Administration -> Printing). Delete annoying USB printer entry ;) 

8. Configure HL2070N by right clicking and choose "settings" and then the pane "connection" (my translation from danish). Choose cups and type in your IP address from step 2.

Thanks again for the "how to".

---

### Post by hangfire on 2005-12-01
Thanks, Kresten. I incorporated your notes and correction into post #2 in this thread. Glad to know you like the HOWTO.

HF

---

### Post by todomartinez on 2005-12-01
I've followed all of the steps and I still can not print.  I've gotten to the point where you select the printer and I send the test page to the printer.  At that point the job just stays cued and does not print.  I am a brand new UBUNTU/Linux user but I've been messing with computers since MSDOS. I'm running the latest distrubution of Ubuntu on a Toshiba Laptop (3.06 HT, 1GB RAM and 802.11G) and everything else works fine (Even the WIFI!).  The Hl-2070N is plugged directly into the Belken 802.11 G router and the other two computers print to it okay (running WinXP).   

I'm not sure if I entered the IP address correctly.  From the Desktop, (Gnome?) I went to System/Administration/Printing and I now have the HL-2070N-for-CUPS visable in the printers folder and it shows that it is Ready.

For the location,  I just entered 192.168.2.2, do I have to enter it as http:/192.168.2.2 or some other format?

Thanks In Advance

---

### Post by Sebby on 2005-12-08
I've got the same problem as todomartinez. This guide is great as I could not find anywhere how to install the drivers properly. I have a Brother MFC-3820CN, and I have now installed the drivers. I add a new network printer and put in its IP address (192.168.0.11), and am able to now select the right driver. However, it just doesn't print.

Can anyone help?

---

### Post by neilbuntu on 2006-04-16
Hi there.  I'm a new Ubuntu user, too.   Just have to say that I've been using Linux on servers for over 10 years, and this is the first time that I installed it on my notebook, and I absolutely love it.

I followed the directions and got my HL2070N to print just fine.  For the IP address, type in:

ipp://192.168.1.100 

(or whatever your IP of your printer is)

---

### Post by bigpup on 2006-04-16
I've been trying to install a networked Brother HL1870N that I 've been using for years with Windows. The instructions were a little incomplete (for me), as far as the path to the file. Yelp 2.12.1 gives a good tip:

> To drag a file name into a terminal window:
> 
>    You can drag a file name to a terminal from another application such as a 
> file manager. The terminal displays the path and the full name of the file.

So I drag the file path/name after prompt: ~$  sudo dpkg -i 
Then when I run the command, I get:

> dpkg: error processing hl1870nlpr (--install):
>  subprocess post-installation script returned error exit status 127
> Errors were encountered while processing:
>  hl1870nlpr

any tips?

---

### Post by morphet on 2007-01-01
If anyone has a PPC (Mac), you might want to try Jeecool's tip at [http://www.ubuntuforums.org/showthread.php?t=254311&highlight=2070n](http://www.ubuntuforums.org/showthread.php?t=254311&highlight=2070n)

(Install the 2060 driver that comes out of the box) :o

---

### Post by aevernon on 2007-01-06
This is how I installed my Brother HL-2070N under Ubuntu 6.10 Edgy Eft:

[LIST=1]
[*]Unpack, install drum, plug in, turn on. Print test page by pressing Go button. Turn off, hook up to network, turn on.
[*]Press Go button three times to produce Print Settings pages.
[*] Go to System > Administration > Printing.
[*] Double-click New Printer.
[*] Select Network Printer as Printer Type, then choose UNIX Printer (LPD) from the menu.
[*] For Host, enter the IP Address from page 3 of the Print Settings that you printed above. It will look similar to 192.168.2.104.
[*] For Queue, enter the Node Name from page 3 of the Print Settings. It will look similar to BRN_8A20A6. Click Forward.
[*] Select Brother as the Manufacturer and HL-2060 as the Model. Leave the Driver alone. Click Forward.
[*] Put whatever you like for the Name, Description, and Location. Click Apply.
[*] Find the printer you just added in the Printers window, right-click it, and select Properties.
[*] Verify the settings in the General, Paper, and Advanced tabs.
[/LIST]

---

### Post by Schowie on 2007-01-08
Hi,
Great with a clear instruction. Anyhow my printer, Bother DCP 315CN is not listed as one of the models. I have also tried to install from Brother MFC210, which they claim should be used instead - but how do I then find this driver? (Was found here [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html))

---

### Post by chrisby on 2007-01-26
Hangfire's post worked in part for me, but cups through the menu did not

Hangfire's post:
 
I bought this printer to share on the network, and decided I would try to get it installed first on Linux. It took a little figuring out but here's what I got.

1. Unpack, install drum, plug in, turn on. Print test page. Turn off, hook up to network, turn on.

2. Go to your Router's admin web page (usually 192.168.0.1) and look at attached devices. What you are looking for is the DHCP address of the printer. Reserve that address for that printer. This keeps the printer from moving around if that DHCP address is reassigned while the printer is turned off. Remember this IP.

3. In your favorite web browser, go to the web address for the printer (in my case, [http://192.168.0.4)](http://192.168.0.4)). Change the passwords. At first it seems that you need the password to change the password. However when you fail to log in you'll get a help screen explaining the default usernames and passwords.

4. Download brhl2070nlpr_1.1.2-3_i386.deb from [http://solutions.brother.com/linux/s...r_drivers.html](http://solutions.brother.com/linux/s...r_drivers.html)

5. Download cupswrapperhl2070n_1.0.0-1_i386.deb from [http://solutions.brother.com/linux/s...s_drivers.html](http://solutions.brother.com/linux/s...s_drivers.html)

6. Run:
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
sudo dpkg -i brhl2070nlpr_1.1.2-3_i386.deb
sudo dpkg -i cupswrapperhl2070n_1.0.0-1_i386.deb

I followed the steps and cups didn't work through the system menu, it doesn't want to take the ppd file and didn't work right using other drivers.  Following the directions from brothers website did work from this point though:

[http://solutions.brother.com/linux/sol/printer/linux/cups_ps_install.html](http://solutions.brother.com/linux/sol/printer/linux/cups_ps_install.html)

---

### Post by syxbit on 2007-01-28
great, thanks a lot.
you probably should have mentioned that you need to choose the 2060 (the 2070 doesn't show up)
does that mean you don't even need to install the drivers, as i don't think you're using them anyway, just the 2060's

still, it works great
thanks a lot

---

### Post by Athanasius on 2007-02-11
Thanks for the great how-to!  

One of the things that I found is that on the 2070n is that when I change the paper size and print area from A4 to Letter the top and bottom margins are off about an inch.  Has anyone else found this?  I just keep it on A4 and everything seems alright.

---

### Post by Athanasius on 2007-02-11
Oh, I forgot...

What does this command do anyways?

```
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
```

---

### Post by EugeneH on 2007-02-19
In hopes that this may help someone in the future, here are some things I struggled with in setting up the HL-2070N printer. Finally I got it working, and it wasn't that difficult, although various documentation seems to be missing one or two important points.

Documentation referenced:
- Brother's own linux site (formatting was terrible!)
- Instructions provided in this thread above.

I wasn't rigorous in noting down the steps, but here you go:
- I'm using Edgy Eft 6.10, CUPS 1.2.4, setting up HL-2070N for network access
- Set up the printer, printed test page, attached Ethernet to router
- Installed the two .deb packages downloaded from Brother
- Found the IP address of the printer (difficult for me, since my router configured for DHCP didn't seem to recognize the printer as a client, though it did connect it!)
- Went to IP address of the printer, poked around and set a static IP address (since my router doesn't seem to have that feature, I had to set it in the printer).
- Configured CUPS: (via [http://localhost:631](http://localhost:631)) A couple of tricks here:
  - set up a LPD/LPR printer, and the Device URI as: lpd://xx.xx.xx.xx/binary_p1 (as per Brother's instructions)
  - when choosing a printer model, don't choose any of the options. instead, there's a place for you to set up using a PPD driver, and browse to /usr/share/cups/model/HL2070N.ppd (other users have suggested using the Brother 2060 driver at this point - well, that's the wrong driver).
- configure the Printer options, switch from A4 to letter.
- print test page, and it worked for me!

I didn't find using Ubuntu's System | Administration | Printing menu item useful. It made more sense to me to configure it directly in CUPS.

maybe I did something wrong to make my life difficult, but I found those extra steps necessary for my setup.

hope it helps!

---

### Post by Jim Darrough on 2007-03-10
I did the CUPS changes but CUPS wants a password and won't accept my user password, so I cannot make the changes. Any help for that? I am sure it wants root, but I  don't have a root password set up Ubuntu 6.06LTS.

---

### Post by fjm03 on 2007-04-24
First, thanks for tutorial. Especially the translation from Debian to Ubuntu (*sudo ln -s /etc/init.d/cupsys /etc/init.d/cups*).

But please be advised that installing the Brother's CUPS wrapper may crash the Open Office 2.2 suite on systems running Feisty.

---

### Post by LunA^tic on 2007-05-06
Thanks for this HOWTO, hangfire. It worked perfectly for me. 

Greetings,
LunA^tic

---

### Post by gtfourdreams on 2007-05-18
> **Jim Darrough said:**
> I did the CUPS changes but CUPS wants a password and won't accept my user password, so I cannot make the changes. Any help for that? I am sure it wants root, but I  don't have a root password set up Ubuntu 6.06LTS.

i tried root. it didnt work, so i dont think thats what it wants. i used the original username which i setup with original password. (keep in mind this is a fresh install)

so far, EugeneH's way works the best. at least the HL2070N option came up. now if i could only get it centered right on the page....

*EDIT* fixed the centering problem. use CUPS administration (instead of Printers) to change the settings of the printer. then test print works just fine.

---

### Post by ehntoo on 2007-05-24
> **EugeneH said:**
> In hopes that this may help someone in the future, here are some things I struggled with in setting up the HL-2070N printer. Finally I got it working, and it wasn't that difficult, although various documentation seems to be missing one or two important points.

Documentation referenced:
- Brother's own linux site (formatting was terrible!)
- Instructions provided in this thread above.

I wasn't rigorous in noting down the steps, but here you go:
- I'm using Edgy Eft 6.10, CUPS 1.2.4, setting up HL-2070N for network access
- Set up the printer, printed test page, attached Ethernet to router
- Installed the two .deb packages downloaded from Brother
- Found the IP address of the printer (difficult for me, since my router configured for DHCP didn't seem to recognize the printer as a client, though it did connect it!)
- Went to IP address of the printer, poked around and set a static IP address (since my router doesn't seem to have that feature, I had to set it in the printer).
- Configured CUPS: (via [http://localhost:631](http://localhost:631)) A couple of tricks here:
  - set up a LPD/LPR printer, and the Device URI as: lpd://xx.xx.xx.xx/binary_p1 (as per Brother's instructions)
  - when choosing a printer model, don't choose any of the options. instead, there's a place for you to set up using a PPD driver, and browse to /usr/share/cups/model/HL2070N.ppd (other users have suggested using the Brother 2060 driver at this point - well, that's the wrong driver).
- configure the Printer options, switch from A4 to letter.
- print test page, and it worked for me!

I didn't find using Ubuntu's System | Administration | Printing menu item useful. It made more sense to me to configure it directly in CUPS.

maybe I did something wrong to make my life difficult, but I found those extra steps necessary for my setup.

hope it helps!

Thanks for the location of that .ppd.  After working on my printer for an hour but having serious centering and other problems, just changing the PPD fixed everything.

You rock.

---

### Post by tutwabee on 2007-09-27
I have had problems with improper Brother drivers for the last year for this printer.  All pages printed fine except for the fact that everything was shifted down 1.5 inches (the bottom of the page was frequently cut off).

Thanks a lot for this tutorial!  It worked like a charm.

---

### Post by hawthornso23 on 2009-09-03
An alternative to setting up a static IP address for your printer is to install it by netbios name. The 2070N has its own netbios name already set up. 

To use netbios names you need to have winbind installed - part of samba. If you have samba installed you probably already have it. Check in synaptic. However for some reason netbios addressing is not turned on in samba by default. To enable it you need to edit /etc/nsswitch.conf . (If you can't figure out how to edit this file, you probably shouldn't be attempting this.)

Find the line that starts  'hosts:' and insert 'wins' just in front of where it says 'dns'. For example in my case the lines before and after were

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

The exact entries vary depending on what else you have installed so yours may look different. Be careful as this is a somewhat important configuration setting. Order matters. 

Find the netbios name of your printer by querying your router. Mine turned out to be  BRN_7A2D6F. Test that netbios addressing is working by running

ping -nc 5 BRN_7A2D6F

from the commandline.

Open up System-Administration-Printing and add the printer as before (or edit the properties of your existing printer to change device/URI). It'll find network printer for you by IP address. Just copy/paste the netbios name (in my case BRN_7A2D6F) over the IP address portion of the URI instead. It'll ponder for a second while it checks that the URI works - then should install. You will end up with an installed network printer with Device/URI looking something like

socket://BRN_7A2D6F:9100

Print test page. Enjoy.

---

### Post by joe110010 on 2009-10-09
I went through the process yesterday and it worked fine printing the test page from the CUPS admin, and the printer was in my system--admin--printers.  Between then and now it disappeared, and going back into the CUPS admin it's not there either, and the .ppd file isn't in my cups/model folder - it's empty.  So, I just added the printer again over the network and used the 2060 driver and it works fine.

---

### Post by t35t0r on 2010-08-14
More specifically, you should use the 2060 hpijs-pcl5e driver. I've also tried these 2060 drivers on the hl-2070n and they don't work very well, whereas the hpijs-pcl5e has none of the problems mentioned below:

1) 2060 pxlmono - won't wake the printer up from sleep. Sometimes doesn't print
2) 2060 postscript - prints garbage, wastes lots of paper

The 2070 brother driver won't print at all (ubuntu karmic 10.04 64 bit force installed).

---

### Post by jimbobs on 2011-08-13
> **t35t0r said:**
> .....
2) 2060 postscript - prints garbage, wastes lots of paper
...... 

I've had a similar experience with that driver: one line of text and the printer then empties the paper tray but doesn't print anything on them, so at least they can be reused.

---

