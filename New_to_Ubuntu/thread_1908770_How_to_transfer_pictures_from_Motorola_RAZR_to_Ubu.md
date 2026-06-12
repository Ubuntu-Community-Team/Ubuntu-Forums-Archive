---
title: "How to transfer pictures from Motorola RAZR to Ubuntu via bluetooth"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by rocksockdoc on 2012-01-14
I've established the bluetooth connection between my Motorola RAZR V3 & the Ubuntu PC, but I can't figure out how to transfer the pictures from the RAZR to Ubuntu, en masse.

On the RAZR, I selected:

[LIST]
[*][SIZE=1]**Settings -> Connection -> BlueTooth Link -> Setup -> Find Me**[/SIZE]
[/LIST]
Then, on Ubuntu, I selected:

[LIST]
[*][SIZE=1]**System -> Preferences -> BlueTooth**[/SIZE]
[/LIST]
This found the Motorola phone and connected by bluetooth.

I then set up the "Bluetooth Preferences" options as shown in the screenshot below:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210814&stc=1&d=1326529285[/IMG]

Here are the details:

[LIST=1]
[*]First I set up the Motorola RAZR V3 to allow itself to be found by the PC:
[LIST]
[*]Settings -> Connection -> BlueTooth Link -> Setup -> Find Me
[/LIST]
 
[*]Then, I set up the Ubuntu PC to find the Motorola RAZR V3:
[LIST]
[*]System -> Preferences -> BlueTooth
[*]Ubuntu provided a 5-number passcode PIN to type on the Motorola RAZR
[*]The connection was established when I entered that PIN on the RAZR
[/LIST]
 
[*]Then, in the Motorola RAZR V3 I navigated to my stored photos:
[LIST]
[*]MyStuff -> Pictures -> select a picture -> menu -> Move -> Ubuntu PC
[LIST]
[*]Seeking: Ubuntu PC
[*]Connected: Ubuntu PC
[*]Moving: Filename
[*]Disconnected: Ubuntu PC
[*]Moved: Filename To Bluetooth
[/LIST]
 
[/LIST]
 
[*]This moved the selected picture file to the default folder on the Ubuntu PC:
[LIST]
[*]On the Ubuntu PC, a "File Received" popup said
[*]You have received the file &#8220;fname.jpg&#8221; over Bluetooth.
[/LIST]
 
[*]The desired picture then showed up in my Ubuntu "Downloads" folder
[/LIST]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210815&stc=1&d=1326530315[/IMG]

---

### Post by rocksockdoc on 2012-01-14
Unfortunately, I wasn't able to move all the picture files en masse, as the Motorola RAZR said "transfer rejected" after the first file.

[LIST=1]
[*]First I set up the Motorola RAZR V3 to allow itself to be found by the PC:
[LIST]
[*]Settings -> Connection -> BlueTooth Link -> Setup -> Find Me
[/LIST]
[*]Then, I set up the Ubuntu PC to find the Motorola RAZR V3:
[LIST]
[*]System -> Preferences -> BlueTooth
[*]Ubuntu provided a 5-number passcode PIN to type on the Motorola RAZR
[*]The connection was established when I entered that PIN on the RAZR
[/LIST]
[*]Then, in the Motorola RAZR V3 I navigated to my stored photos:
[LIST]
[*]MyStuff -> Pictures -> Mark All -> Move Marked Files -> Ubuntu PC
[/LIST]
[*]This moved **ONLY THE FIRST** selected picture files to the default folder on the Ubuntu PC:
[LIST]
[*]On the Ubuntu PC, a "File Received" popup said
[*]You have received the file &#8220;fname.jpg&#8221; over Bluetooth.
[/LIST]
[*]Unfortunately, **only the first of all the desired pictures then showed up** in my Ubuntu "Downloads" folder
[/LIST]
I am able to move the picture files via Bluetooth, one by one, from the Motorola RAZR V3 by selecting or viewing each file in the phone, pressing the menu key, pressing the 'Move" selection, and OK'ing the move on the Ubuntu PC side.

But, what is the trick to moving ALL the picture files, en masse?

---

