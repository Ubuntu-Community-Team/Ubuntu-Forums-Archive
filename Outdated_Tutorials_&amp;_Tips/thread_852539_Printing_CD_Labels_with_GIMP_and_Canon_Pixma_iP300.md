---
title: "Printing CD Labels with GIMP and Canon Pixma iP3000"
date: 2008-07-07
forum: Outdated Tutorials &amp; Tips
---

### Post by SirArthur on 2008-07-07
After reading some tutorials on how to do it with OpenOffice Draw and got really lousy 256 color results, I came up with my own method for printing CD Labels with the Canon Pixma iP3000 using GIMP.

My method is as follow:

==== NEEDED SOFTWARE: GIMP ====
If you don't have it, install GIMP trough apt, aptitude, synaptic... whatever you like.

==== FIRST PART: CREATE A PRINTER CLASS ====

On this part we will create a printer class that will save us time on configuring the printer each time we need to print a CD.

#1 . Open System Configuration and click on "Printers" then "Add Printer".
On the wizard select: 

1) Printer Class -> NEXT

2) If you're using TurboPrint (recommended), select tp0 (or the number of your Pixma printer), otherwise select iPxxxx (where xxxx is the model of your printer) and press the arrow (->) on the middle to add the printer to the class. -> NEXT

3) Name now your printer CD_Label_Printer leave location and description blanked. -> NEXT -> FINISH

4) Now you must have another printer on the list named "CD_Label_Printer", click on it to select the printer than the tab "Instances" and with (default) select on the list below, press Configure.

5) Select on the first tab:

Page Size: CD Printable
Paper kind: CD Printable
Paper Origin: CD Tray

leave the rest as is and, if you're using TurboPrint, select the last tab "Controller Configuration", otherwise is done.

If you are using TurboPrint set the Print Quality to 1200 dpi or over (default CUPS driver just has 300 or 600 dpi).

==== USING GIMP WITH OUR PRINTER ====

1) Start GIMP and create an image of 800 x 800 pixels with some color background. If need use the bucket and fill the background with some weird color.

2) Create a new layer with transparent background, name it "mask" for an instance.

3) With the new layer selected, choose the circle selection tool and draw and adjust a circle to fill the canvas, then select Selection -> Invert Selection

4) Select the forecolor white and the bucket fill tool and fill the selection with it.

You must now have a "your background" color circle on the middle.
*I added mine as attachment to this post

5) Open your CD label image on GIMP and copy it to clipboard.

6) With background layer selected paste the CD label image.

7) The image must now be a new floating selection, with it selected click on "New layer". Now the image must be rasterized between the background and the mask.

8) Adjust your image, add text, etc. When you're done press "Print" (CTRL+P)

9) Select your "CD_Label_Printer" and go then the tab "Image Settings"

10) Set the following values:

Check the box "Ignore page margins"

Width: 120.00 mm
Height: 120.00 mm
(I'm European so I use the metric system, sorry)

Position: Center -> none

Top: 85.00
Left: 5.00

Put your CD on the tray and Print it.

---

