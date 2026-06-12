---
title: "problems with Epson printer not receiving commands"
date: 2016-04-18
forum: New to Ubuntu
---

### Post by Amelia_Hayner on 2016-04-18
Hi! LOVE Ubuntu, and I am sure this glitch can be solved. Installed the printer, I think I put in the right driver for it, but not sure- and cannot find that page again. However, it DID print a lovely test page. and nothing since. this is a real problem, I want to put stuff on Ebay and won't be able to print postage unless this is working. thanks for any help.

---

### Post by oldfred on 2016-04-19
My HP sometimes turns off the on line setting.
I have to go into HP's control panel & tell it to be one line.

Your Epson probably has settings in System Settings, Printers.

If you have multiple copies of driver installed it can get confused also. You want green check mark for active or enabled.

  An Epsom salts are good for many things, but not really printing. :)
(My spell check also wanted to change Epson to Epsom.)

---

### Post by sammiev on 2016-04-19
Have you checked your firewall settings? 

I made that mistake before. :(

---

### Post by Amelia_Hayner on 2016-04-20
I don't think that's the problem. I think, after it printed the initial page, that I muddled it up trying to install a "correct" driver and should have left well enough alone. now I don't know how to go and look there.

i may also want to change Epson to Epsom by the time I am through here. DON'T GO ANYWHERE!!! I am going now in search of system settings, printers. This may require a Dr. Livinston hat. I hope to return soon.

I went in and fiddled around a bit, found the printer page site, found that the driver was available, and it appears to have been installed. BUT it asks me for a device URI. what is that????

---

### Post by oldfred on 2016-04-20
Found this on an older Brother printer site. Changed Brother to Epson

Open a web browser and go to **"http://localhost:631/printers"**.
Check if the Device URI of your printer is **"usb://Epson/(your printer's model name)"**

If the device URI is different from the example above,  please go to  "Modify Printer" of your printer to select proper device  and driver.       If your printer is not listed on "http://localhost:631/printers",  please go to **"http://localhost:631/admin"** and click "Add printer" and select proper device and driver.

---

### Post by Amelia_Hayner on 2016-04-20
tried to install Epson stylus nx110 printer. let it search for drivers. there were none for that particular model. Ubuntu suggested NX105, and printed a test page - very nicely.
since then, I have tried and tried, and there are now 16 !!! jobs lines up - ( tried to cancel or delete them with no success)
tried to download different driver, like C110 - no success.
what to do? this is of some urgency- husband would like to list many items on Ebay and I will need to print the postage! 
any help greatly appreciated!!!
( the printer is listed as idle)

---

### Post by SeijiSensei on 2016-04-20
I presume you tried all the hardware options like turning the printer off and on and checking the integrity of the USB connection.  Try removing and reconnecting the USB cable if you haven't done that.

If none of those work, open a browser on the machine to which the printer is connected and point it to [http://localhost:631/](http://localhost:631/).  That will give you the CUPS interface which has buttons for various tasks.  Look at the queue of jobs and see if you can release or delete them there.  Enter your login name and password when prompted just like you would to run a command with sudo.

If all else fails, try removing the printer and installing it again.

You can remove all the jobs from the queue manually by deleting the cNNNNN and dNNNNN files in /var/spool/cups.  You'll need to use sudo for this.  Also on my machine /var/spool/cups/tmp is empty.  You might want to reboot after this.

---

### Post by oldfred on 2016-04-20
Threads merged, Please do not post two threads with same topic.
You can bump once every 12 hrs, if not getting answers.

---

### Post by Amelia_Hayner on 2016-04-20
I found that page, thank you very much. However, it doesn't like my user name/password - where do I go to find that? I used the same one I used for ubuntu.

ok, sorry, newbie here.

ok. I rebooted computer, got the page where you start the printer. it asked if I wanted CUPS encrypted, did not check that box. so it looked for drivers for my printer, Epson Stylus NX110, and said that they were available. it started the installation, and seemed to finish, then a note came up that said "CUPS error- broken pipe" what in the WORLD is that???

thank you, yes I have unplugged numerous times. thank you for your response.

well, probably doing this wrong as well, making a reply to thread instead of quick reply. yep, just tried it again, and exact same thing happened. it appeared to install, it asked to authentication, then I got the same message about the broken pipe. I am done for the day.

---

### Post by Geoffrey_Arndt on 2016-04-20
Suggest you try what Seiji wrote (using the CUPS (common unix print server) - - use your browser to clear/flush all print jobs, delete the pritner, and reboot.  

Then get the "deb" installer file from OpenPrinting.org - - the driver is listed under the Epson Stylus NX 115:   (don't use the RPM installer - - use deb for LSB 3.2)

Install it using "gdebi" - - which is another installer program available from the standard repos . . . then, go back to the downloaded deb, right-click it, and choose open with gdebi, and click on the install button.  

Would then suggest you reboot the system again, connect the printer via usb, and re-add it via CUPS interface or via System Settings>Printer>Add

Another option to try is to google for "Epson Cloud Print" and see if it will work via that method also.


 [URL="http://www.openprinting.org/printer/Epson/Epson-Stylus_NX115"]http://www.openprinting.org/printer/Epson/Epson-Stylus_NX115  




[/URL]

---

### Post by Amelia_Hayner on 2016-04-22
thank you for that very detailed reply. I will try all of the above.

---

### Post by Amelia_Hayner on 2016-04-28
ok! that did it! the printer is working! thank you!!! went to OpenPrinting, the link posted, and there it was. just invaluable help. now. how do I post that this issue is solved???

---

### Post by oldfred on 2016-04-28
See my signature:
Or:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

