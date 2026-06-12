---
title: "How to install the Canon 550i/580i/950i/ and iP90 printer"
date: 2007-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Seisen on 2007-07-19
**[SIZE="5"]How to install the Canon 550i/580i/950i/ and iP90 printer[/SIZE]**

*The iP90 printer uses the 550i driver.

The first step is to open up your source list and add this to it
```
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./
```
If you don't know how to open up your source list you can do it by putting this in the terminal

```
gksudo gedit /etc/apt/sources.list
``` you can use whatever text editor you like to edit your source list.

After adding that to your source list you need to do this in the terminal

```
sudo apt-get update
```

Next you need to install these files
```
sudo apt-get install libcnbj-2.2 bjfilter-2.2 pstocanonbj
```

Cupsys will be automatically restarted and you can select printer in cupsys configuration which is
[http://localhost:631]("http://localhost:631") or if you don't want to do that you can go to System>Admistration>Printer>Add Printer.

To add the printer through the cups, the first thing you do is click on add a printer. The next screen will ask you for the name of you printer, location and description the ony thing you really have to fill in is the name. After you done filling in the information click continue. The next page is asks you to select your printer. Hit continue and then it will ask you for your driver, select the Canon Pixus xxx ver.2.2  then click on add printer . 

To add the printer the other way once you click on add printer a new window will open up that say's add a printer at the top and Step 1 of 3: Printer connection. As long as your printer is turned on it should show up in **"Use a detected printer"**, if it doesn't you can select it in  **"Use another printer by specifying a  port"** and selecting your printer then click forward. The next page is where you select the printer driver. The manufacturer is Canon if it already isn't selected and the Driver is Pixus  xxx ver.2.2 then click forward. Finally the next screen is the printer information you don't really have to worry about filling in the rest of the information if you don't want to just click "Apply" and now your printer should show up under printers. 

Right click on your  printer and then click on Print a Test Page and your printer should crank out a test page, if it doesn't please let me know and we can try to figure out why.

This works on Ubuntu Edgy and Feisty and if you run into any problems feel free to ask questions.


[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/")

---

### Post by jalirious on 2010-03-07
For a Canon iP90 printer

System->Admin->Printing

Click "new"
Select "Canon"
Select the PIXMA iP2000 driver

Voila.

---

### Post by speedygeo on 2010-03-14
> **jalirious said:**
> For a Canon iP90 printer select the PIXMA iP2000 driver

Interesting!
It works well than the BJC-8200 Foomatic?

---

### Post by cuberts on 2010-04-21
I really cant get my canon 550 i printer to work with UBUNTU. I did what you told me to in the terminal, but for one of the commands, it says that there are broken packedges or whatever

---

