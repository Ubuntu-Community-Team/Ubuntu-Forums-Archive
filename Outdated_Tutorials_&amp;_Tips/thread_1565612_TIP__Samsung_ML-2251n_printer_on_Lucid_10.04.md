---
title: "TIP : Samsung ML-2251n printer on Lucid 10.04"
date: 2010-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by james_fried on 2010-09-01
Just had some trouble getting this old Samsung ML-2251n printer working on Lucid, so thought that I would share the simple answer I found.

There are older posts on the forum which are now outdated by the new printers functionality in the latest versions of ubuntu. ([http://ubuntuforums.org/showthread.php?t=371827]("http://ubuntuforums.org/showthread.php?t=371827"))

[LIST]
[*]Open System > Administration > Printing
[*]Select Add, then click network printer. Be patient, ubuntu will now scan your network for printers and should find the Samsung in 30 seconds or so.
[*]Ubuntu will detect the printer as a Samsung ML-2250, but that will work fine. Select the printer.
[*]In the description field, ubuntu will show "IPP network printer via DNS-SD" by default. This didn't work for me.
[*] **This is the key part :** Click connection at the bottom of the page, and select "LPD network printer via DNS-SD", click Forward.
[*]Ubuntu will search for drivers, you can now name the printer as required and click Apply.
[*]That's all - the printer should now work fine over the network.
[/LIST]

If there are any problems with the printer, you can always access System > Administration > Printing again and either:
[LIST]
[*]Remove the printer by right clicking on it and selecting delete.
[*]Adjust the settings by right clicking and selecting properties.
[/LIST]

Happy printing - hope that is useful.

---

