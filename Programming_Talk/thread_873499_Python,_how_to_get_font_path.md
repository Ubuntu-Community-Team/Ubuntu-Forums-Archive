---
title: "Python, how to get font path?"
date: 2008-07-29
forum: Programming Talk
---

### Post by denham2010 on 2008-07-29
Hi,

I am trying to do some image manipulation in Python by adding text to existing images.

I am using the imported modules Image, ImageDraw and ImageFont.

Now adding the text to the image is the easy part. The problem I am having is I need to allow the user to select a font, using the gtk.FontSelectionDialog widget. With this, I am able to get the name of the selected font, but not the path to the selected font's .ttf file.

To set the font using ImageFont, I need the path to the .ttf font file.

I have searched for hours on google and a variety of forums, but have not been able to find a solution.

Hoping someone can help me to work out how to get the selected font's path (from a gtk.FontSelectionDialog) in python so I can pass it to ImageFont.

Thanks for your assistance.

---

### Post by denham2010 on 2008-07-31
Sorry, BUMP...

Hoping someone has a solution.

Thanks.

---

### Post by Cecilio on 2008-10-15
I have the same problem. Today I was googling to try to find an answer and found your post. Did you get a solution?

Thanks
Cecilio

---

### Post by unutbu on 2008-10-15
Perhaps this helps?

[http://www.pygtk.org/pygtk2tutorial/examples/calendar.py](http://www.pygtk.org/pygtk2tutorial/examples/calendar.py)
Check out the 
calendar_select_font method. When the ok button is clicked, the calendar_font_selection_ok method is called, and the font is set with 
```

self.font = self.font_dialog.get_font_name()
        if self.window:
            font_desc = pango.FontDescription(self.font)
            if font_desc: 
                self.window.modify_font(font_desc)
```

The code comes from this pygtk tutorial:
[http://www.pygtk.org/pygtk2tutorial/sec-FontSelectionDialog.html](http://www.pygtk.org/pygtk2tutorial/sec-FontSelectionDialog.html)

---

### Post by Cecilio on 2008-10-16
Thank you very much for the information. It is a great help!

Best reagards,
Cecilio

---

### Post by JuanC on 2008-12-05
Now i get pango.FontDescription(font_name) , how to use ImageFont from PIL to load this font?

---

### Post by unutbu on 2008-12-05
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=995195](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=995195)

---

### Post by JuanC on 2008-12-05
How to get font path from pango.FontDescription to use with ImageFont.truetype or ImageFont.load?

---

