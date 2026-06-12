---
title: "HP Wireless printer cannot be found by HPLIP wireless configuration"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by Graeme_Davidson on 2013-09-29
I have setup an HP1102w wireless printer on my home network and my macbook pro and iPhone 4s have been able to print to it wirelessly for some time. I have recently installed lubuntu 13.04 on my wife's laptop and would like to make the printer available to this computer wirelessly too. I have downloaded the latest version of HPLIP from the web and installed the plugins etc as per instructions I have found in various forums. When I run HP wireless configuration it fails to find the printer, even after configuring it via usb.
What can I try to get this printer and computer speaking to each other?

---

### Post by Rich53201 on 2013-12-29
Another lubuntu 13.10 newb here.  Wifi-connected network HP printer.  Found your thread while trying to solve my own problem.  I think it's solved.  The problem was the firewall.

My 'system-config-printer' (the provided cups gui) did not find the HP printer even after I used Synaptic to install hplip and recommended associated packages.

I had earlier installed 'gufw', a simple gui firewall manager, and activated the firewall.  I started 'gufw' and disabled the firewall.  Then 'system-config-printer' showed the printer without further trouble & I was able to print a test sheet.  I re-enabled the firewall, added a rule to Allow, incoming, network, printing, chose 'hplip' from the list, and all seems well now.  (My firewall currently allows all outgoing, so didn't have to add a rule for that.)

---

### Post by walterorlin on 2013-12-31
First lubuntu does not have hplip installed by default. I have found this to be a terminal but easy way to go through is 

<code> sudo hp-setup -i</code>
if you have qt installed you can have 
<code>sudo hplip</code>
in a gui way.
and then follow the simple prompts that you want to set it up.

---

### Post by Bucky Ball on 2013-12-31
Just install hplip via software centre. Go to 'Printing'. Add printer>Network Printer. Give it a little time to find the printer on the network. You should see if pop up in the Network Printer list. Select it and follow your nose and you should find the correct driver for it when it offers drivers.

---

