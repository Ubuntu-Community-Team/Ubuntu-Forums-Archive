---
title: "HOWTO: Print to HP DeskJet 460 wirelessly over Ad-hoc network"
date: 2007-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by akniss on 2007-01-02
After much googling, trial and error, gnashing of teeth, and absolutely no help from HP on the subject, I finally figured out how to print to my new HP Deskjet 460 wirelessly using an ad-hoc network in Ubuntu Dapper or Edgy (x86, 32bit).  I thought I'd post my steps here in case anyone else is trying to accomplish the same thing.  I have not tried this on Breezy or Feisty, so I would be interested in hearing from any of you that have success or failure trying this on either of these two releases. 
***Assumptions I am making before we start:*** 
[LIST]
[*]You have network-manager installed and nm-applet running.  If you do not, search the forums for instructions on how to do so.
[*]You have access to a Windows installation and the software that came with the printer.
[*]You have a wireless card installed in the printer, and you know about how the hardware profile switch works on the printer.
[/LIST]

**Setting the Printer's Wireless Profiles** 
[LIST=1]
[*]I'm not aware of any way to setup the wireless profiles on the printer in linux, so I installed the provided software in Windows in order to do this. Once installed, open up the HP Deskjet 460 Toolbox.
[*]On the Printer Services tab, click the box next to Wireless Profiles under Configuration.
[*]Choose one of the Edit Profile buttons.
[*]Enter the following information:
Wireless Network Name (SSID) > DeskJet460 (or anything you wish here)
Communication Mode > Ad-hoc
Channel > 10  (I'm not sure if this is necessary, but it seems to be on Mac and BSD according to some forum discussions)
Network Authentication > Open
Data Encryption > None


[*]Click on the Advanced Configuration button
Manual IP settings:
IP Address > 169.254.0.100  (you may use any address between 169.254.0.0 and 169.254.254.254)
Subnet Mask > 255.255.0.0
Default Gateway > 0.0.0.0
Under compatibility > Use Current Settings
[*]Click OK
[*]Click Save Profile
[*]Click Pint Current Settings to be sure everything is the way it should be
[/LIST] 

**Connect to the ad-hoc network in Ubuntu**
[LIST=2]
[*]Boot back into Ubuntu
[*]With nm-applet running, left-click on the applet and choose "Create New Wireless Network..."
[*]For the network name, type in the SSID you set up using the Windows configuration tool
[*]click Connect
Even if your network shows up in the network list in network-manager, go through the process of creating the network. Otherwise, network-manager will default to an infrastructure network and things will not work properly.  [If this has been fixed in Edgy or Feisty, let me know.]
[/LIST]

**Create the new printer in cups**
[LIST=3]
[*]Go to: System > Administration > Printing
[*]Double click the New Printer icon
[*]Select Network printer, and choose HP JetDirect from the drop down menu
[*]In the host field, type in the IP address you assigned previously in the Windows configuration tool (169.254.0.100 was used in this example)
[*]Leave the port as 9100
[*]click Forward
[*]Manufacturer > HP
Model > DeskJet 460
hpijs (recommended) should show up in the driver field
[*]click Forward
[*]Give the printer a name such as ADHOC-DJ460 (or you could just leave the default)
[*]Click Apply
[/LIST]

And that should be all.  Try printing a test page to the printer to see if it works!

If this howto doesn't work for you, let me know and we can try to change things to make them as universal as possible.  However, I am by no means a linux/cups/networking/ubuntu expert, and so my ability to help if these instructions don't work is limited.  They worked for me, and so hopefully it will save some of you some headaches.

---

### Post by phenest on 2007-11-17
Exactly what model is this?

Is it this one: [HP Deskjet 460]("http://h10010.www1.hp.com/wwpc/uk/en/ho/WF06a/5043-5047-5287-5287-5143-12232740.html")

If so, is it the cb or the wbt model? I'm thinking of getting one.

---

