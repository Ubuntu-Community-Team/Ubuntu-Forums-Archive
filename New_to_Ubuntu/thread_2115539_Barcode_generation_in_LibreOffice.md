---
title: "Barcode generation in LibreOffice"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by Pradeep Varma on 2013-02-13
Hi All,

I am in a mess.
I want to generate Barcode in LibreOffice calc.

for the same i went through some articles and followed the steps.
In doing so, I had to install the "IDAutomationVB.bas" Macro and further on proceeded with the barcode generation.

link found on youtube to generate barcode : [http://www.youtube.com/watch?v=wfDzfMQAG7k]("http://www.youtube.com/watch?v=wfDzfMQAG7k")

It was successful. But the problem I'm facing is the barcode generated is not being read by any barcode reader/scanner.

Kindly help asap.

Thanks in advance.

---

### Post by U202E on 2013-02-13
It could be a software bug, your printer isn't working correctly or it's just the wrong ink/paper...

First look here: [http://www. on linebar code reader .com/]("http://www.*******arcodereader.com/") <-- remove the spaces after coping this, if I paste the link it turns into [http://www.*******arcodereader.com/](http://www.*******arcodereader.com/)
if this page can read you barcode it's probably not libre office' fault.
but if this can't read your codes you have to change the distance between the characters or so.

as far as I know there are online bar-code generators so you don't need libre office for that...

I hope this helped.

---

### Post by shawncox on 2013-04-02
sorry, new here. What is "LibreOffice calc."? it is developed in [[COLOR=#000000]Java[/COLOR]]("http://www.barcodelib.com/java_barcode/barcode_symbologies/java_barcode_eclipse_birt.html") or [[COLOR=#000000].NET[/COLOR]]("http://www.barcodelib.com/net_barcode/main.html")? or it is something like microsoft office? I am a java developer(to be more specific, student) and I just finished a academic project in which there are some [[COLOR=#000000]barcode generation[/COLOR]]("http://www.barcodelib.com/net_reporting_services/main.html") part. So maybe I can help you a little.

---

### Post by Derxst on 2013-04-10
Another thing to consider - barcodes come in different formats. Do you know what format you need?

---

### Post by gscratch on 2013-05-03
There are also Windows software packages that allow you to create a barcode and then save it as a bitmap which you might be able to (copy over and then) paste into a Libre document

---

### Post by makaveil4202 on 2013-11-27
Maybe something went wrong with the barcode generation process. You can follow the [[COLOR=#000000]barcode integration and generation[/COLOR]]("http://www.keepautomation.com/font_tools/openoffice_barcode_font_encoder.html") guide below again and see if it works:

1. Create an area in the spreadsheet column for the barcode in Calc. 
2. Adjust the column size with enough space to hold barcodes.
3. Center the column to display text in center to leave white space, the quiet zone, for generated barcodes.
4. Enter the formula in the cell to format text that will be used by barcode font.  
5. Apply the barcode font to the cell and adjust the cell size.  
6. If barcode creation in other cells in the column is necessary, highlight these cells, copy the formula and paste it into them.

then verify those barcodes by scanners or readers to see if the data encoded correctly.

And I agree with U202E, you may try some [[COLOR=#000000]online free barcode generators[/COLOR]]("http://www.keepautomation.com/online_barcode_generator/") if it is not a force for you to use libre office, they are quite effictive and convenient.

---

