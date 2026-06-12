---
title: "Colour Hex Codes"
date: 2007-03-27
forum: Programming Talk
---

### Post by TheForkOfJustice on 2007-03-27
I'm trying to make a bootsplash and I need a way to tell the hex code of a colour.  The HTML colour codes displayed in GIMP probably won't do so I was hoping you could all help.

I think what I'm looking for are hex codes...

0x0
0x154
0x67

...and so on...

I'm looking for something called 'Palette Indexes'.

---

### Post by Wybiral on 2007-03-27
Hex color values aren't usually palletized... They're usually in the form of "#rrggbb" but with hex values.

#FF0000 = Red
#00FF00 = Green
#0000FF = Blue

Likewise...

#000050 = a darker blue

---

### Post by TheForkOfJustice on 2007-03-27
> **Wybiral said:**
> Hex color values aren't usually palletized... They're usually in the form of "#rrggbb" but with hex values.

#FF0000 = Red
#00FF00 = Green
#0000FF = Blue

Likewise...

#000050 = a darker blue

Okay so what I'm looking for is NOT the hex codes.  I need to know the palette index for a 256 colour palette.  Y'know a picture or program that can display what number a colour is on a 256 colour palette.

---

### Post by pmasiar on 2007-03-27
[http://www.program-transformation.org/TWiki/StandardColors](http://www.program-transformation.org/TWiki/StandardColors) - sample colors and links to color picking websites

---

### Post by TheForkOfJustice on 2007-03-27
> **pmasiar said:**
> [http://www.program-transformation.org/TWiki/StandardColors](http://www.program-transformation.org/TWiki/StandardColors) - sample colors and links to color picking websites

That should do fine.  I think i'm getting the hang of this hex code thing.  It seems the letters/numbers after the '0x' can be translated into an integer number.

Thanks.

---

### Post by Mirrorball on 2007-03-27
The colors to know are:
Red: #FF0000
Green: #00FF00
Blue: #0000FF
Yellow: #FFFF00
Magenta: #FF00FF
Cyan: #00FFFF
White: #FFFFFF
Black: #000000

After you learn these, the others are easy to guess. For instance, #FF9900. It looks like yellow, with less green, but not red. It must be orange.

---

### Post by Wybiral on 2007-03-27
00 to FF is your range for RGB... It's just mixing colors... It's not that hard.

I don't get what you mean by palette?

---

### Post by TheForkOfJustice on 2007-03-30
> **Wybiral said:**
> 00 to FF is your range for RGB... It's just mixing colors... It's not that hard.

I don't get what you mean by palette?

When you switch an image from RBG to indexed colour it goes by a palette.

You need an indexed image as a usplash bootsplash.

I also need to define background colours, progressbar colours and text colours by a palette colour number entry when I compile the bootsplash.

---

### Post by Wybiral on 2007-03-30
So you're using some image format?

---

### Post by TheForkOfJustice on 2007-03-30
> **Wybiral said:**
> So you're using some image format?

Here's by bootsplash

[http://ubuntuforums.org/showthread.php?t=397474](http://ubuntuforums.org/showthread.php?t=397474)

You start by making PNGs made with RGB colouring. Then you need to convert those images from 'RBG' to 'Indexed' images.  This is done by going into GIMP and selecting

Image -> Mode -> Indexed...

from the menu.  Then you save the image.

Usplash only handles indexed images, which is not surprising since it creates a huge decrease in file size.

---

### Post by Wybiral on 2007-03-30
Thats pretty cool looking. But GIMP does that for you, so why do you need to know how the indexing system works?

---

### Post by TheForkOfJustice on 2007-03-31
> **Wybiral said:**
> Thats pretty cool looking. But GIMP does that for you, so why do you need to know how the indexing system works?

The bootsplash has to be compiled and there are settings in the *.c file (lfc-theme.c in the bootsplash zip file that I linked to) that need numbers that belong to the palette.  I'm trying to decipher what numbers correspond to what colour.

---

