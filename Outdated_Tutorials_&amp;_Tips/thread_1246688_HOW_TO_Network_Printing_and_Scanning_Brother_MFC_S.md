---
title: "HOW TO: Network Printing and Scanning Brother MFC Series"
date: 2009-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by sad1sm0 on 2009-08-22
This is my first attempt at a tutorial so bare with me.  I've found most of this information throughout the forums, but it seems to be incomplete and difficult to find so I'm attempting to just get it all in one place.  This tutorial is designed to cover a complete installation of the Brother Printer/Scanner Model MFC-420cn specifically, although I think it applies to all brother mfc models with a few variations.  I haven't confirmed that this works on hardy or older, so if anyone has any input on those versions, I would appreciate it.  

[SIZE="4"]**Printing**[/SIZE]

[SIZE="3"]**Installation**[/SIZE]

The first step has recently gotten a lot easier than it used to be.  There is now an ubuntu package containing the necessary cups and lpr files needed to wrap the brother mfc series printers along with some others.  Open a terminal and type [COLOR="RED"]sudo apt-get install brother-cups-wrapper-extra[/COLOR] (package with MFC420cn files.  Check Synaptic for other models).  this will also install the lpr drivers for the printer and all of the common cups files needed to get us up and running.

[SIZE="3"]**Setup & Configuration**[/SIZE]

There's a really easy to use gui utility for printer setup in **System -> Administration -> Printing**.  Basic printer setup is pretty straight forward from here.

  Select **Server -> New -> Printer**.  A dialog will popup while the server searches for available printers on the network.  Mine was found and another dialog popped up with the printer name, ip address, and port number.  If it doesn't automatically detect it, there's an option to search for network printers.  Make sure your printer is online (try [COLOR="RED"]ping -c 4 192.168.x.x[/COLOR] if you're unsure) and try again.

  Once your printer is found, the configuration utility will search for suitable drivers (the ones we just installed).  It may ask you to select your printer from a list, or just load the correct drivers automatically.  I've had different results here with different computers and setups.  After the drivers have been selected, you will be given a chance to provide human readable name, description, and location information for your printer.  Once you click continue, the utility will ask you to print a test page.  If you are unhappy with the quality of the test, don't fret.  I've found with a bit of tweaking and messing around with the settings, you can get quality printing from this printer.  Right Click on the newly installed printer and choose properties.  In the dialog menu select printer options.  I had to turn off Bi-directional printing and make some color enhancements and all was well.  You can reprint the test page from the Settings menu item.  This was all that was needed on my 3 ubuntu machines.





[SIZE="4"]**Scanning**[/SIZE]

[SIZE="3"]**Installation**[/SIZE]

I don't think that there is an aptitude package for the scanner functionality.  However, Brother fully supports linux from what I can tell and there are a variety of tools directly downloadable from their website.  Both RPM and debian files are available for both 32 and 64 bit architectures.  I am only going to cover the debian files in this tutorial.

Download the appropriate brscan and brscan-key files from Brothers [[COLOR="blue"]website[/COLOR]]("http://solutions.brother.com/linux/en_us/download_scn.html") for your printer and architecture.  Install these packages thru gdebi or the console.

[SIZE="3"]**Setup**[/SIZE]

To finish up open up a console and type the appropriate brsaneconfig command (e.g. [COLOR="RED"]brsaneconfig2 -a name=MFC-420CN ip=192.168.x.x[/COLOR] ) and if no errors pop up, you should be good to go.  Go to **Applications -> Graphics -> Xsane Image Scanning Program**.

This is the method that has worked for me to get both functions available to me.  I can't guarantee that the same will work for you, but it seems pretty consistent across my network.  I have not yet tried to use the fax so I'm not covering that.

---

### Post by roycaboy on 2010-10-20
I have the same printer on my network and I'm very new to Ubuntu, this tutorial was a great help to me.
thanks

---

