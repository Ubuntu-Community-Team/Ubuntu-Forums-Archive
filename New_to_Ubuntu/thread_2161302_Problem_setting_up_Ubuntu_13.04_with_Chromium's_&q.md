---
title: "Problem setting up Ubuntu 13.04 with Chromium's &quot;Cloud Print&quot; feature"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by Matthew999 on 2013-07-10
Hello,

I installed Ubuntu 13.04 on my HP Pavilion laptop last night because I thought it would be fun to try a different Operating System (I also use Windows 8 and OS X Mountain Lion on other machines) - I'm currently trying to setup the "Cloud Print" feature of Chromium [COLOR=#303942][FONT=Ubuntu]28.0.1500.52 and am having some difficulty:

My printer is an HP Deskjet 3050a J611 that has Wireless and E-Print currently turned on , it's connected to my other computers via Wireless, through my home network, and can print perfectly to my other computers. According to HP's Support Pages, there are currently no E-Print drivers available for Linux so I've been trying to connect to Cloud Print as a "Classic Printer" as per Google's instructions. While I've apparently succeeded in connecting my printer as a "classic printer" (Chromium's cloud print manager told me I set up the printer correctly), what I'm unclear on is how do I print to it now that it's supposedly a cloud printer? Google's Support Page tells me to simply press Ctrl+P to print my document (I'm printing from Google Docs) yet, when I press Ctrl+P, the Ubuntu Print Box pops up and tells me I can "Print to a file" and not via Cloud Print.

I did a global search, on the Ubuntu Forums, for "cloud printing" and I received several results for topics such as "MAAS", "VPN", and "Openstack" but not printing. I also checked the first 4 pages of both the "Absolute Beginners" forum and the "Networking" forum, yet didn't find information about printing. I tried various Google searches, using terms like "cloud printing linux", "eprint alternatives linux", and "cloud printing chromium linux" and still did not find what I needed. I did find some information about something called a "CUPS Server" though I'm not sure if that would apply to what I'm trying to do.

If anyone could point me to an appropriate tutorial, or website, that explains how to setup cloud printing with Chromium I'll be very grateful.  [/FONT][/COLOR]

---

### Post by newb85 on 2013-07-10
Disclaimer: I have no experience with cloud printing.

First, you should know, Chromium and Chrome are not exactly the same.  They are very similar, but don't always behave identically.  I would expect Google's support pages to be aimed at Chrome, not Chromium.  Perhaps you could link to the page you're talking about?

---

### Post by Cfossy2 on 2014-01-15
Have you tried going into the printers admin page as when you do you can then run the wireless wizard which then allows you to print from the cloud. You should be able to see the printer's email address so that you can add the printer as a printer either in HP cloud printing or google cloud. If you cannot get to the printers admin page via your browser, contact HP and they will direct you to the latest HPLIP for linux. Hope this helps.

---

