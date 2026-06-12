---
title: "How to set up a Samsung 2152w network printer in Kubuntu Edgy under TCP/IP"
date: 2006-12-25
forum: Outdated Tutorials &amp; Tips
---

### Post by MoebusNet on 2006-12-25
The following guide is unsupported. I am running the described printer on the system in my signature on a 54g wireless network. Source documentation for the sections on Setting Network Protocols and Configuring TCP/IP is the Samsung ML-2150 series Setup Guide and is quoted almost verbatim except for my comments in parentheses. Please feel free to post constructive comments and corrections. This guide may contain errors and/or omissions of facts. As a newby, I just wanted to contribute to the community.

Let's get started! 

Unpack your printer and install the toner cartridge as directed by the manufacturer. If you don't have documentation, check the manufacturer's website [http://www.samsungelectronics.com](http://www.samsungelectronics.com) or the website of a supplier selling toner cartridges for directions. 

Plug your printer into your electrical power source and connect the printer to your computer with Ethernet  cable; we will set up the wired network first before worrying about wireless.

A. Assign a fixed network address to the printer
(This example will use 192.168.11.9 as the assigned address.)

Setting Network Protocols (This is done on the printer front panel)

When you first install the printer, all supported network protocols are enabled when you turn the printer on. If a network protocol is enabled, the printer may actively transmit on the network even when the protocol is not in use. This may increase network traffic slightly. To eliminate unnecessary traffic, you can disable unused protocols. 

1 Press the Menu button until you see &#8220;Network&#8221; on the bottom line of the display.
 
2 Press the Enter button to access the menu. 

3 Press the scroll button until &#8220;Config Network&#8221; displays on the bottom line. Press the Enter button.
 
4 Press the scroll button to display &#8220;Yes&#8221; and press the Enter button. Then press the Upper Level button.
 
5 Press the scroll button until you see the desired protocol on the bottom line. 
You can choose AppleTalk or Netware. 

6 Press the Enter button. 

7 Press the scroll button to change the setting to &#8220;On&#8221; (enable) or &#8220;Off&#8221; (disable). 

8 Press the Enter button to save the selection. 
 
Configuring TCP/IP (This is done on the printer front panel)

Your printer can be set up on a variety of TCP/IP networks. There are several ways in which your printer can be assigned a TCP/IP address, depending on your network. 

&#8226; Static Addressing: TCP/IP address is assigned manually by the network administrator. 
&#8226; Dynamic Addressing BOOTP/DHCP(default): TCP/IP address is assigned automatically by the server.
 
Static Addressing (This is what we're going to do.)

To enter the TCP/IP address from your printer&#8217;s control panel, take the following steps: 

1 Press the Menu button  until you see &#8220;Network&#8221; on the bottom line of the display. Press the Enter button  to access the menu. 

2 Press the Enter button when &#8220;Config Network&#8221; displays on the bottom line.

3 Press the scroll button to display &#8220;Yes&#8221; and press the Enter button.
 
4 Press the Upper Level button, then use the scroll button.
 
5 Press the Enter button when &#8220;Config TCP&#8221; displays.
 
6 Press the scroll button to display &#8220;Yes&#8221; and press the Enter button.
 
7 Press the Upper Level button, then use the scroll button.
 
8 Press the Enter button when &#8220;IP Get Method&#8221; displays.

9 Press the scroll button to display &#8220;Static&#8221; and press the Enter button.
 
10 Press the Upper Level button, then use the scroll button. 
 
11 Press the Enter button to access the IP Address menu. The IP address consists of 4 bytes. Enter a number between 0 and 255 for each byte. 

12 Press the scroll button to enter a number between 0 and 255 and press the Enter button.
 
13 Repeat Step 12 to complete the address from the 1st byte to the 4th byte. (Steps 11, 12 & 13 &#8211; enter the assigned printer address 192.168.11.9)
Each of the four groups of numbers separated by the period sign is considered a byte. For example, 192 is a byte, 168 is a byte, 11 is a byte and 9 is a byte. You enter each byte separately as steps 11 through 13 describe.)

14 To select other parameters, such as Subnet Mask or Gateway, press the Upper Level button, then use the scroll button. Press the Enter button.
 
15 Repeat steps 12 and 13 to configure the other TCP/IP parameters. (Steps 14 & 15 apply to a larger network. If you just have a small home network with just a couple of computers and a couple of printers you probably don't need to change this.)

B. Set up the computer

Using your web browser, enter the network address of the printer 192.168.11.9 (Use the assigned printer address). This will bring you to the Samsung Printer Status Page. Click &#8220;Print Test Page&#8221; to test that the printer will work.

From the Kubuntu desktop, Kmenu > System Settings > Printers > Add > Add Printer/Class. This opens the KDE Add Printer Wizard. Select Network printer (TCP) and click &#8220;Next&#8221;.

Printer Address is 192.168.11.9 (Use the same fixed network address you assigned to the printer.)
Port is 9100 (This is the default printer port.)
Click the Scan button so that the wizard can find the printer. Then click &#8220;Next&#8221;.

Printer Model selection is Samsung (left column) then ML-2152W (right column). Leave Postscript printer and Raw printer boxes unchecked. Click &#8220;Next&#8221;.

Driver Selection is Samsung ML-2152W (Foomatic + pxlmono) [recommended] Click &#8220;Next&#8221;.

This is the Printer Test Page. Click the Test button to print a test page to confirm that you can print from the computer. Click &#8220;Next&#8221;.

This is the Banner Selection page. The default selection is No Banner for starting and ending banners. Don't change this unless you want a banner at the beginning, end or both of ALL your print jobs without exception. Click &#8220;Next&#8221;.

This is the Printer Quota Settings page. The default setting is No quota, No size limit, No page limit. Don't change this unless you are in a multi-user network environment that requires limits on how and how much users may print. Click &#8220;Next&#8221;.

This is the Users Access Settings page. Don't change this unless you are in a multi-user network environment that requires certain users to be denied printing privileges. Click &#8220;Next&#8221;.

This is the General Information page where you must give your printer a name that identifies it in the print menu. (Don't just name it &#8220;Printer&#8221; unless it is the only one on the network. Even then it is better to be specific like &#8220;Laser Printer&#8221; or &#8220;Samsung ML-2152W&#8221; or &#8220;Workgroup Printer&#8221; if you think you might add another printer to the network later. Use the location box to remind yourself of where the printer is on the network; enter 192.168.11.9 (Use the network address you assigned to the printer.) Click &#8220;Next&#8221;.
If you used spaces in the Printer Name, a dialog box will pop up offering to strip the spaces out of the Printer Name. I recommend you click &#8220;Strip&#8221; to avoid possible problems.

This is the Confirmation window that shows you all of your selections in the setup dialog. If any of your selections are incorrect, this is your last chance to change them by clicking &#8220;Back&#8221;.

If you are happy with your selections, click &#8220;Finish&#8221;.

C. Set up wireless networking

Using your web browser, enter the network address of the printer 192.168.11.9 (Use the assigned printer address). This will bring you to the Samsung Printer Status Page.

Click &#8220;Network Administrator&#8221;. Click &#8220;Wireless&#8221; in the left column to access the Wireless Configuration page. If you already have a wireless network up and running, this page is where you set up your WEP Authentication and Encryption. If you are running an encrypted wireless setup (HIGHLY RECOMMENDED!) a good idea would be to get everything working in unencrypted mode before you re-enable your wireless encryption.

Once you have everything working, unplug your Ethernet cable. Try to print a test page.

You should be done.

Try out your new network printer!

---

