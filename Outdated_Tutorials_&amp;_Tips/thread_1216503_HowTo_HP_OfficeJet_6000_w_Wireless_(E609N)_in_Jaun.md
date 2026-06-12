---
title: "HowTo: HP OfficeJet 6000 w/ Wireless (E609N) in Jaunty Jackalope"
date: 2009-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Rocket2DMn on 2009-07-18
[SIZE="4"][COLOR="Red"]**_Background Information_**[/COLOR][/SIZE]

Setting up the [HP OfficeJet 6000 Wireless Printer]("http://www.shopping.hp.com/product/printer/inkjet/1/storefronts/C9295A%2523B1H") (model E609N) is straightforward in Ubuntu 9.04 "Jaunty Jackalope."

For HPLIP information related to this model printer, see - [http://hplipopensource.com/hplip-web/models/officejet/officejet_6000_e609n.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_6000_e609n.html)

Known problems with HPLIP 3.9.6 - [http://hplipopensource.com/node/335](http://hplipopensource.com/node/335)

[SIZE="4"][COLOR="Red"]**_Setting Up_**[/COLOR][/SIZE]

First unpack the printer, install the ink, and power it on as described on the paper that came with the printer.  Give it a few minutes to align itself and print a configuration page.  Do not plug it in to the computer yet.

Because this printer requires a newer version of HPLIP than is available in the Jaunty repositories, we should first uninstall the existing version.  The required version of HPLIP is 3.9.6, and the repositories only have 3.9.2.  I believe the installer will automatically remove the old version for you, but I did it myself beforehand.
```
sudo apt-get remove hplip
```

Now you can download the latest HPLIP version here - [http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)
Save the file to your home folder, open a terminal and set executable permissions on the file, then run the installer.  If you are using a newer version of HPLIP, simply substitute the name of the .run file:
```
chmod +x hplip-3.9.6b.run
./hplip-3.9.6b.run
```
[SIZE="4"]
[COLOR="Red"]**_Installing_**[/COLOR][/SIZE]

Follow the directions of the installer, you should be able to select the defaults on everything.  Of course, be sure to have the Universe and Multiverse repositories enabled, as explained in the installer.  If you are setting up for wireless, when prompted about restarting the computer or the printer, simply choose ignore or press Enter to continue.  Follow directions to setup for your wireless network.  If you are using wireless encryption (which you should!), you will need your WEP or WPA key.  If it tells you that it failed to configure, give it a few minutes to refresh automatically, sometimes it just takes awhile for the printer to grab an IP, esp. if you are using wireless encryption.

When I installed, it failed to print a test page at the end of running the installer, but afterward when I opened the "**Printer Properties**" under "**System->Administration->Printing**," it worked fine.

[SIZE="4"][COLOR="Red"]**_Post-Configuration (Optional)_**[/COLOR]
[/SIZE]
Go to "**System->Administration->Printing**."  If you want this to be your default printer, right click the icon, and select "**Set As Default**."

For other standard printer options, a more friendly user interface can be found under "**Applications->Accessories->HP Device Manager**."  You can also use this tool to setup new printers (or re-setup this one).
Here is where you can enable double sided printing, too: On the "**Printer Settings**" tab choose "**Two sided (long edge)**" for "**Duplex**."

[SIZE="3"]**[COLOR="SeaGreen"]_Setting up Static IP_[/COLOR]**[/SIZE]

If you want to setup a static IP on the printer, navigate to the printer's current IP in your browser.  If you don't know the IP, you can grab a link from the **HP Device Manager** by clicking "**Open printer's web page in a browser**."  This will take you to the printer's configuration page.  Click on the "**Networking**" tab at the top, then select "**Wireless (820.11)**" on the left side under "**Connections**."  Now click the "**IPv4 Configuration**" tab.

I am using a Linksys WRT54G wireless router.  Your information may be different, depending on your router's make/model, but the type of information is the same.  Here is my setup:
```
Manual IP Address: 192.168.1.250
Manual Subnet Mask: 255.255.255.0
Manual Default Gateway: 192.168.1.1
```
The IP address that you assign should be outside of your router's DHCP allocation range (mine is 192.168.1.[100-149]) in order to prevent possible IP conflicts.
The default gateway is the router's IP address.
```
Manual Preferred DNS Server: 192.168.1.1
```
The manual DNS server is likely also going to be your router's IP address, unless you happen to have a separate DNS server on your network.

Apply the changes.  You will change your URL to use the new IP in order to connect to the printer's web interface again.  Don't forget to update the IP in the "**Printer Properties**" by double clicking the printer's icon under "**System->Administration->Printing**" and editing the "**Device URI**."

---

### Post by Psumi on 2010-02-25
For those of you having XFCE and do not wish to install the printer using a gnome app:

1. Install hplip, as of karmic though. If you have an older ubuntu, you will have to get hplip from the website.

2. Go into cups: [http://localhost:631/admin](http://localhost:631/admin)

3. Add the printer (if not already added.)

**Scanner not Scanning?**

Then you need to follow extra steps:

4. copy the IP of your printer. If you have it hooked up via USB, you will use lsusb to get the location of the printer instead. (IE: Bus 003 Device: 011 = 003:011 instead of the IP.)

5. In terminal: **hp-makeuri <USB/IP Address>**

6. COPY THE CUPS hp:/ ADDRESS (DO NOT CLOSE TERMINAL.)

7. CLOSE YOUR CUPS BROWSER TAB/WINDOW. You cannot have it open when modying the next bit.

8. In terminal again: **sudo <favorite text editor> /etc/cups/printers.conf**

9. Edit the line that has device URI to have the URI made in step 5.

10. restart CUPSD. (sudo killall cupsd then sudo cupsd)

Your printer should now scan too.

---

