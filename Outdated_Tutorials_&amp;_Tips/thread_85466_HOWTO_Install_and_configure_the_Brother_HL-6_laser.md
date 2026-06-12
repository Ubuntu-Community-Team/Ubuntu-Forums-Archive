---
title: "HOWTO: Install and configure the Brother HL-6 laserprinter (and probably many more)"
date: 2005-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Muffe on 2005-11-02
[SIZE="6"]Install the Brother HL-6 laserprinter (and perhaps a few others)[/SIZE]

[SIZE="4"]Introduction[/SIZE]
I have an old Brother HL-6 laserprinter, and have actually never got it 100% working with linux. But when I installed Breezy on my brand new computer, I thought why not get it to work properly?

The previous drives I had been using (in Horay) was either the Brother HL-6 driver or the HP LaserJet IIP driver. My printer can emulate a HP LaserJet IIP printer, so it's OK to use that driver too.

The problems with The Brother HL-6 driver was that it became two nasty smilies on the top left corner of each page, and the prints was a bit "blury" (maybe not the right word to use on a laserprinter, but you understand). The LaserJet IIP driver was on the other hand razor sharp and had no ugly smilys, and worked well, exept one thing: the margins. Everything i printed was placed too far up/left on the page, and the bottom/right margins became enormous. I could not find a way to adjust this, so I gave it up, until now:

[SIZE="4"]Installing the printer[/SIZE]
This is almost straight-forward, but only applies to GNOME-users. KDE has probably a similar tool. This is just to configure CUPS, so any method will be fine.
[LIST=1]
[*]Open the GNOME printer management (System -> Administration -> Printing) and double-click "New Printer". Select how the printer is attached to the machine (parallell port, network etc). Click "Forward".

[*]It's now time to choose driver. Selct teh "Generic" manufacturer, and choose "PCL4 Printer" as model. Also make sure that the "laserjet" is selected as driver. Press "Apply".

[*]You have now installed your printer. You can print a test page if you want to make sure the connection between the PC and printer is working. Do that by right-clicking the printer -> Properties -> "Print test page" If something comes out of your printer, and look reasonable is everything working all right. But don't bother if it's not aligned perfectly, we will fix taht soon.
[/LIST]

[SIZE="4"]Changing the printer name[/SIZE]
You have probably already recogniced taht you can't change the printer name. The printer is called PCL4-Printer, and that's not very describing. Let's do something with that. If you don't want to change, just jump right to the next chapter.
[LIST=2]
[*]Open a terminal

[*]Change directory to /etc/cups

[*]Take a backup of printers.conf

[*]Open the printers.conf (as root), and locate the line "<Printer PCL-4-Printer>"

[*]Change the "PCL-4-Printer"-part to a more suitable name. Without whitespaces!

[*]Save and exit

[*]Change directry to /etc/cups/ppd

[*]Locate the file PCL-4-Printer.ppd, and change its name to the EXACTLY same name as you entered into printers.conf at step 5 (remember the .ppd extension)
[/LIST]

[SIZE="4"]Configure the margins[/SIZE]
This is te most important part. And if you are not using this HOWTO to configure an Brother HL-6, but another printer, my values will probably not fit. It is asy to calculate your own margins, just remember to set all values to 0 before you begin.

[LIST=3]
[*]Go to the [LinuxPrinting.org CUPS Quick Start](http://www.linuxprinting.org/cups-doc.html) doc, and scroll down to section 6. Download the two files mentioned there.

[*]Chmod the "alignmargins" script to 0755

[*]Make sure your printer is on

[*]Run the script and select the number corresponding to your printer in the first step

[*]Watch a calibration page print. If you want to calculate your own values, follow the instructions on this page. It is often smart to set all values to 0 after this first print, and then print another calibration sheet, and use that. If you intend to use my values (if you have a Brother HL-6), just throw the calibration instructions.

[*]When you are asked about the "ml" values and etc, enter theese values (only applies to Brother HL-6):
[LIST]
[*]ml: 8
[*]mb: 14
[*]mr: 16
[*]mt: 12
[*]x: -30
[*]y: 6
[/LIST]

[*]Make a test print and check if everything is all right.[/LIST]

If someone has question, please feel free to ask.

[SIZE="4"]Enjoy printing![/SIZE]

---

