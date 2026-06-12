---
title: "Ubuntu 11.04 will mot connect to internet"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by Enigmaman on 2011-09-26
I have installed Ubuntu 11.04 on a dual boot with Windows XP.

For a while I had no problem connecting to the internet in Ububtu.

However it has now ceased to work. I have unclhecked the 'Work Offline' option in the File menu but it makes mno difference. 

Can anyone help please?

---

### Post by technosysind on 2011-09-26
I think the info you have provided is not enough. Maybe you can check your log files. It might help

---

### Post by Enigmaman on 2011-09-28
Thanks for your reply. 

What information do you need to know? 

How do I check the log files? 

TIA

---

### Post by technosysind on 2011-09-28
please check log files from the following location

system>>administration>>log file viewer

Look for errors

---

### Post by grahammechanical on 2011-09-28
Here is something that you need to clarify:

> I have unclhecked the 'Work Offline' option in the File menu 

I guess that you are referring to the web browser not being in off-line mode. So, what has ceased to work? Network manager connecting to your modem/router or the web browser loading web pages?

What messages does Ubuntu give you when the desktop loads?

If you see Network Discovery Service Disabled, then you are not connected to your Internet Service supplier even though the router is switched on and Ubuntu is connected to it.

If you see Network Disconnected you are now offline then there could be three or four things wrong.

a) Enable networking is not ticked.

b) If you are using an ethernet connection then the cable is uplugged. If you are using a wireless connection then Enable wireless is not ticked.

c) the router is switched off

If you do not tell us the messages that Ubuntu is giving you and you do not describe the network manager icon and the information that network manager gives when you click the icon, then we cannot help you.

You do not even say if this is a wired (ethernet) or wireless connection.

Regards.

---

### Post by Enigmaman on 2011-10-05
Thanks for the further replies. 

The Checked "Work Offline" option was of course in Firefox's file menu and I have unchecked it, so the problem clearly seems to lie with the Network connection. 

I am connecting through a wired Ethernet connection.It is the same hardware setup which works fine with Windows. so I presume that the problem lies with the network settings.

When the desktop loads, Ubuntu gives me no error message.

I cannot see Network Discovery Service anywhere but I have spotted the small Network icon at the top of the screen is covered with a red exclamation mark and when I mouse over it, it shows a "No network connedtion" message. 

This despite the fact that I have checkced tre "Enable Networking".

 option, which was not ticked.

I
And...I think this was the problem, as I am now connected! Thakyou everyone.:)

---

