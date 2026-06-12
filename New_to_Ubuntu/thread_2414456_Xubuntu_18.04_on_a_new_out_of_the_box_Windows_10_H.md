---
title: "Xubuntu 18.04 on a new out of the box Windows 10 HP Laptop Issues"
date: 2019-03-11
forum: New to Ubuntu
---

### Post by tazmo8448 on 2019-03-11
I reformatted a new Windows 10 HP cf0014dx laptop and booting into Xubuntu found that the WIFI card stopped working. Wired connection works fine. HP says that the WLAN card is an Intel Dual Band yet when I run lshw -c network it is showing Realtek being UNCLAIMED as the secondary card. The LAN card IS a Realtek.  Using this tutorial:
[COLOR=#111111][FONT=&quot]
Xubuntu supports a system known as **NDISWrapper**. This allows you to use a Windows wireless device driver under Xubuntu. To start using **NDISWrapper**:[/FONT][/COLOR]
[COLOR=#111111][FONT=&quot]
[LIST]
[*]Obtain the Windows driver for your network device and locate the file that ends with .inf

[*]Install the [IMG]https://docs.xubuntu.org/1810/libs-common/images/icon_package.png[/IMG]ndisgtk package

[*]Go to **[IMG]https://docs.xubuntu.org/1810/user/libs/images/icon_menu.png[/IMG] &#8594; [COLOR=#001166]*[IMG]https://docs.xubuntu.org/1810/user/libs/images/preferences-desktop.png[/IMG] Settings Manager*[/COLOR] &#8594; [COLOR=#001166]*Windows Wireless Drivers*[/COLOR]**

[*]Select **Install new driver**

[*]Choose the location of your Windows .inf file and click **Install**

[*]Click **OK**
[/LIST]
[/FONT][/COLOR]
What I found was the ndisgtk commands are no longer in use and not supported an Windows Wireless Drivers when launched created error messages. 

Any help would be greatly appreciated. If someone would show me how to grab the text from the Terminal showing all the info I have on it and post it that would probably make things a little less vague. As said I am new to this stuff.

---

### Post by oldrocker99 on 2019-03-11
That's unusual. It's been 8 years since I had to use ndiswrapper. Ever since, the wireless just works. 

To paste text using CTRL-V in a terminal, you need to use SHIFT-CTRL-V. There is also one of the greatest features of Linux: Highlight the text, and you can paste it using the middle mouse button, without using CTRL-C and CTRL-V.

---

### Post by tazmo8448 on 2019-03-11
Thanks for the heads up on the Ctrl-V & Shift-Ctrl-V...

Searching the net I found all sorts of tutorials but most were ancient and would not even run without jumping thru endless hoops. Most were dated in the early 2000's.  

I came across wireless.wiki.kernal.org that gave the command  lspci -nn  and that finally enabled me to put a name an number on my WLAN chipset ... (RTL8723DE 802.11b/g/n) .. prior to that commands just listed it as Realtek Semiconductor (UNCLAIMED) with no other information... what was odd was HP called the WLAN chip Intel with no model number or reference point to search for drivers. And trying to install Windows drivers was to me like putting a square peg in a round hole. Plus that .inf that was called for I never could locate. 

I then installed the related git packages then found the correct driver on GitHub using their smlinux tutorial for the Realtek RTL8723DE module.

---

### Post by ajgreeny on 2019-03-11
Great news! Please mark as SOLVED from the Thread Tools menu up-top if, as I believe, this is now solved to your satisfaction. 
It is a great help to users searching the forum.

---

### Post by tazmo8448 on 2019-03-11
BTW I found a tutorial that zeroed in on my particular issue and it is located at DigitalOcean on How To Install Git on Ubuntu 18.04 that gave a great walk thru.

---

