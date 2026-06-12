---
title: "reduce pdf size"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by amarumayo on 2013-03-08
I have a pdf that is 8MB which I need to reduce down.  I used ghostscript with this command:
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

This shrunk the file to 497KB but has now rendered the quality to low.  Is there a way I can specify the amount of reduction i.e. to about 4MB?

Thanks in advance,
Chris

---

### Post by amarumayo on 2013-03-08
I have found that these options can give you some flexibility in pdf size with ghostscript.  

[COLOR=#666666][FONT=Droid Serif]
[LIST]
[*]/screen - Lowest quality, lowest size
[*]/ebook - Moderate quality
[*]/printer - Good quality
[*]/prepress - Best quality, highest size
[/LIST]
[/FONT][/COLOR]

the /ebook reduced it down to 1.8 MB.

I still wonder if there is a better option.

---

### Post by SeijiSensei on 2013-03-08
You might take a look at [ImageMagick]("http://www.imagemagick.org/") and see if fiddling with the -quality settings help.

---

### Post by sudodus on 2013-03-08
Maybe you get inspired by this link

[[COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=2114418&p=12501849#post12501849[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2114418&p=12501849#post12501849")

Good luck :-)

---

