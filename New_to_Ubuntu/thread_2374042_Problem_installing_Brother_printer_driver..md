---
title: "Problem installing Brother printer driver."
date: 2017-10-12
forum: New to Ubuntu
---

### Post by bobsone on 2017-10-12
Hi
I have a Lenovo Ideapad 310 with dual boot Ubuntu Mate (16.04) and Win10..
I am trying to get a Brother DCP-135c printer to work.  When I first connected the printer I saw a message stating that there are no drivers installed for this printer.
After some searching I found a thread discussing the printer and the drivers and driver install instructions at the following links.
  [https://askubuntu.com/questions/203536/how-to-install-a-brother-dcp-135c-printer](https://askubuntu.com/questions/203536/how-to-install-a-brother-dcp-135c-printer) 
[http://support.brother.com/g/s/id/linux/en/download_prn.html#DCP-135C](http://support.brother.com/g/s/id/linux/en/download_prn.html#DCP-135C)
[http://support.brother.com/g/s/id/linux/en/instruction_prn3.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_prn3.html?c=us_ot&lang=en&comple=on&redirect=on)

As I understand things, I need to install the LPR and cupswrapper .deb drivers, however using the Brother listed install method resulted in the LPR driver producing a broken dependency fault.
I then tried to install the drivers with:
[HTML]sudo apt-get install ~/Downloads/Brother/dcp135clpr-1.0.1-1.i386.deb[/HTML]
[HTML]sudo apt-get install ~/Downloads/Brother/dcp135ccupswrapper-1.0.1-1.i386.deb[/HTML]

This method was "more" successful, both drivers installed and when print is selected (e.g. Pluma >print) the printer DCP-135c is now listed as a printer option  but the print task isn’t completed.
In the Print window General Tab;  DCP135c is listed as "Waiting for printer to become available"  and in the Document Print Status window; the printer is listed as DcP135c and the printer status is always reported as "Processing"

I don’t know where to go from here, any suggestions appreciated.

Thanks.

---

### Post by bobsone on 2017-10-12
It is working now.
I rebooted and the printer didn&#8217;t work.
Then I ran ***_sudo apt-get autoremove_*** and** *_sudo apt-get autoclean_***  the printer still didn&#8217;t work.
I then rebooted and ran ***_sudo apt-get update_*** followed by ***_sudo apt dist-upgrade_***, still no printer, rebooted and now the printer is working. :-)

---

