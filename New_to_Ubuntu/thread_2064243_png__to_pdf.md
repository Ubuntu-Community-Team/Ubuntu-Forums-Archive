---
title: "png  to pdf"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by pete1977x on 2012-09-28
I have a png picture on the desktop. I need to change it to a pdf text file. It isnt a picture, just a prt Scr of a note.
Staples couldnt even print it out for me cause they didnt know the program it was from. How can I convert it to a pdf??

---

### Post by ajgreeny on 2012-09-28
Use the **convert** command from imagemagick.

In its simplest form it is ```
convert image.png image.pdf
```but you can add many options to fine-tune the output if needed.

See "man convert" in terminal, though you may find it a bit convoluted.

---

### Post by jerrrys on 2012-09-28
More info [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=png+to+pdf&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

---

### Post by uRock on 2012-09-28
Open the file with the default picture viewer, then click the print button. When the print window opens select Print to File and you will see the circle to click in order to make it a PDF.

---

### Post by pete1977x on 2012-09-29
is there a converter for png to pdf that has a gui that will install on the desktop?? or will option on a right clik???

 12.04

---

### Post by spjackson on 2012-09-29
Gimp has a GUI and will open png. File->Print->"Print to file" will create a pdf. Or LibreOffice.

---

### Post by deadflowr on 2012-09-29
> **spjackson said:**
> Gimp has a GUI and will open png. File->Print->"Print to file" will create a pdf. Or LibreOffice.

Shotwell does the same thing. Open file, print, select print to file. I think it drops the pdf file in the documents folder.

---

### Post by HermanAB on 2012-09-29
CUPSPDF provides a generic PDF print function.

---

### Post by coffeecat on 2012-09-29
Threads merged. 

@pete1977x, please do not open more than one thread on the same topic.

---

