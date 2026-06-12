---
title: "Error check internet connections ubuntu 11.10"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by Wilfred Padambo on 2011-11-17
I have installed ubuntu 11.10 but am struggling to run an application in terminal. It says error check internet connection. This happens also when I go to Ubuntu Software Center or to update Manager. It normally says error fetching http:/ .....
Surprisingly I can go on the internet with firefox. Where should I put the internet connection settings so that the Terminal and Updating should run without problems.

Thanks in advance,

Wilfred

---

### Post by sureshsaragadam on 2011-11-17
Some Times it may happen with Network Connections, Network Manager,

In my case, Ubuntu Software Center does not recognize my net connection when i used **wvdial** dialer, but here I am able to browse firefox,

You should be having a working apt-get with your net connection, Just check.

$sudo apt-get clean all
$sudo apt-get update
$sudo apt-get upgrade

IF NOT, Press the Super Button(windows button), and Find Network Connections

delete all the connections, and configure for a new connection of yours

and then try it.

---

### Post by Wilfred Padambo on 2011-11-18
Thanks for the suggestions. Look at the following error when I opened terminal and pasted the first instruction.

Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
 

Sorry am just a very newbie to linux but I really want to enjoy ubuntu. Please help!!!

Wilfred

---

### Post by Wilfred Padambo on 2011-11-18
Sorry it's me again and I felt I should send you the whole message to give you a good idea.

wilfred@wilfred-HP-dX2000-MT:~$ $sudo apt-get clean all
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
wilfred@wilfred-HP-dX2000-MT:~$ $sudo apt-get clean all
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory

Me again,

Wilfred

---

### Post by sureshsaragadam on 2011-11-18
Make sure that you don't have the Update Manager, Synaptic, etc. running struck (may be broken).
Please Check the thread below.

[http://ubuntuforums.org/showthread.php?t=954061](http://ubuntuforums.org/showthread.php?t=954061)

---

