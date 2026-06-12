---
title: "Canon C3380/C3380i printer setup"
date: 2008-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by weaccept on 2008-08-15
Here are instructions for getting a Canon C3380/C3380i printer set up under Ubuntu 8.04 (Hardy Heron).

The printer is connected to via IPP, and in my case the printer requires authentication (username/password and mailbox authentication).

_Drivers:_
[http://canon.codehost.com/](http://canon.codehost.com/)

The normal system drivers (Generic->PCL 5c, etc.) will not work, because they do not have support for mailboxes (mailbox ID, password).  If your printer is open to all and does not require mailbox authentication, then you may be able to use the normal system drivers.

The Codehost drivers are fully integrated with CUPS.  Once installed you can print from any application without any special Codehost-specific process.  Both color and black and white work.

NOTE: The most non-intutive part is that the username/password authentication for IPP and other protocols is not the same as mailbox authentication.  Both must be specified, and this requires using the Codehost drivers.

_Instructions:_
1. Install the Codehost drivers
2. Using codehost-config:
- Add a Printer
- A remote printer using a network protocol
- Discover network printers
- Enter IP address of printer, select Any protocol, Start Discovery
- Expand the found printer
- Select IPP line
- Select Printer

- Enter Login/Password provided by the printer administrator (same as mailbox/password), Next
- Make sure the next window is maximized to edit the settings on the right hand side
- Under the Mode header
-- Job Mode: Print
-- Job Password: Empty
-- Mailbox number: Mailbox number provided by printer administrator
-- User ID: Mailbox number provided by printer administrator
-- Password: Mailbox password provided by printer administrator
- Next, Next
- Print Test Page, should work

- If you get an error when printing saying "can't prompt for authorization", or if Firefox seems to work but actually does not, then do this:
-- In codehost-config, right click on the printer and select Duplicate.
-- Now print to the duplicated printer and it should work.

_Troubleshooting:_
- Check the CUPS error log file, it is very useful.

- If you see "client-error-not-authorized", that means the mailbox authentication was not sent (most likely) or not accepted (less likely).  This is the error you'll get when using the system drivers.

- You can log into the web interface for the printer and check the status of print jobs and see the log of previous print jobs.

- If you can't get the drivers working, you can also use the web interface on the printer to print PDFs and image files using Direct Print.

---

### Post by Pencilpen on 2009-08-08
[http://canon.codehost.com/](http://canon.codehost.com/) only allows their software to be used by clients in the US. That counts a lot of us out.

I have got this printer working pretty well, even putting my jobs into a mailbox rather than printing directly. 

But my problem is that my jobs all go only into mailbox 0 no matter what mailbox I enter in the Canon configuration utility cngplp. 

I found a thread [here]("http://www.linuxfoundation.org/en/OpenPrinting/Database/CanonFAQ#How_to_use_the_mailbox-feature_of_Canon_IR_multifunctiondevices_with_a_cups-printserver") which even gives me the ability to define the mailbox in the printer Options page of the Printer properties dialog but it doesn't seem to pass this on in the print job. I want my jobs to go to mailbox 29 but no matter what I do they only go into mailbox 0. 

Is it because I can't find anywhere to supply my id/passcode to the printer?

I guess it would be good if I could use the software in the Op but I'm not in the US so I can't use it.

---

