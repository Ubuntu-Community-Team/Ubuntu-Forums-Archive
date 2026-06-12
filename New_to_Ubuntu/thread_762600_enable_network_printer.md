---
title: "enable network printer?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by stevek123 on 2008-04-22
noob w/ 7.10... ubuntu unit is new toy made of old comp parts i had 'round here- hsp internet w/ router hub is new here too. Main fam comp is winXP pro. I've enabled network shared files in win and here on ubuntu. Shares music well. I've enabled print share in win also and tried to configure ubuntu to use the printer on the win unit. Ubuntu print config gives menu to add the path and then verify. I have /(network)/SharedDocs in there, and it 'verifies'. When I send a file to print, it shows up as a file in SharedDocs on the win unit but doesnt print. I've tried several paths including the printer name but they dont 'verify'. As it is now, Win/SharedDocs/(file) doesnt show the extension and the format is not recognized. Not sure what to do next. (please be 'gentle' - I get lost in ubuntu language pretty easily).... 

I'd also like to enable write permissions for text/word documents, if you'd care to add that (it reads and lets me save with new name but that just takes up file space and doubles up unnecessarily)....

---

### Post by mikeyphi on 2008-04-22
Hi there and welcome!

Have you setup 'Shared Folders' in Ubuntu?
In Shared Folders, under the 'General Properties' tab, you should enter the MS workgroup name and also 'tick' the 'This computer is a Wins server' box.

Once setup for sharing, you should find that Ubuntu automatically picks up the printers on the local network.

---

### Post by stevek123 on 2008-04-22
> **mikeyphi said:**
> Hi there and welcome!

Have you setup 'Shared Folders' in Ubuntu?
In Shared Folders, under the 'General Properties' tab, you should enter the MS workgroup name and also 'tick' the 'This computer is a Wins server' box.

Once setup for sharing, you should find that Ubuntu automatically picks up the printers on the local network.

DOH! I missed that Wins server tab....:rolleyes: I checked the tab - it listed across all the shared folders. I went to Admin->Printing and hit 'change' for the device. A browse there gave me printer options (I have 2 there). I applied it - it updated. It printed a test page like a champ!.... something so simple yet easily overlooked :shrug: Thanks!

---

