---
title: "HOWTO: Polished Text in GIMP"
date: 2006-12-26
forum: Outdated Tutorials &amp; Tips
---

### Post by bwhite82 on 2006-12-26
[CENTER][B]HOWTO: Polished Text in GIMP
Level: Intermediate
[/B]
Have you ever seen those spankin' new, clean looking logos on all of those "Web 2.0" sites that are all the hype these days? Well, now you can make your own in a few easy steps with the help of The GIMP and a popular font called Trebuchet MS Bold.[/CENTER]

After completing this HOWTO, you will have the following:

[CENTER][IMG]http://i97.photobucket.com/albums/l202/soldierboy101st/howto/polishedText1.png[/IMG][/CENTER]

*Prerequisites: Linux w/ Gnome or KDE, GIMP, Trebuchet MS Bold font installed
My setup: Ubuntu Edgy Eft 6.10(i686), Gnome, GIMP 2.2

**Credit to Dan Solomon, this is a rehash of his [same tutorial for Photoshop.]("http://pxlgfx.com/tutorials/Polished_Text/")

***I PROVIDE ZERO SUPPORT FOR THIS HOWTO, A.K.A. AS-IS
Since I put “Intermediate Level” at the top of this, I will assume you know how to navigate yourself around GIMP, some navigation details will be left out. You have been forewarned.

Lets get started!

[INDENT]**STEP1:** Install msttcorefonts package:

            sudo apt-get install msttcorefonts
                                   or
           Search for msttcorefonts in Synaptic, install it

If apt-get cannot locate this package, make sure all of your repositories are enabled (search for a howto on these forums on how to do this). Would also advise adding third-party repositories as I can't remember exactly where this package came from.[/INDENT]
[INDENT]
**STEP2:** Once your fonts are all installed, fire up The GIMP. Create a new image 500 X 200px with background set to white. Set your foreground color to, 13171b and your background color to, 01b6eb.

Select the “Fill Bucket” tool, and click on your canvas to fill it with the black.

Select the “Text” tool and under that tool's options, set the font to “Trebuchet MS Bold” and set the size to 60px. Using the background color (blue), click on your canvas and put whatever words you like in the popup. Center the text.[/INDENT]

[INDENT]**STEP3:** Time to make the text a little blingtastic. First make sure your “Layers Palette” is open and that you currently have your text layer active. Then,

On the menu: Script-Fu>Shadow>Drop-Shadow and set the following in the dialog:

Offset X: 4
Offset Y: 0
Blur Radius: 10
Opacity: 70

Click OK. You now have a barely-noticeable but highly-effective (trust me) drop shadow on your text.

Now select your “Gradient Tool”. Set the following tool options:

Opacity: 100
Mode: Overlay
Reverse: Checked
Gradient: FG to BG (should be dark at the left then gets brighter toward the right with your colors you have set)

On your canvas, while holding down CTRL, drag the tool from the top of your text to the bottom. You should end up with this:[/INDENT]

[IMG]http://i97.photobucket.com/albums/l202/soldierboy101st/howto/step3-2.png[/IMG]

[INDENT]**STEP4:** Create a new layer and position it so that it is at the top of your “Layers Palette” (it should be by default). Then select your “Elliptical Marquee” tool and select the top half of your text like so:[/INDENT]

[IMG]http://i97.photobucket.com/albums/l202/soldierboy101st/howto/step4-1.png[/IMG]

[INDENT]Select your “Fill Bucket” tool and fill the selection with white:[/INDENT]

[IMG]http://i97.photobucket.com/albums/l202/soldierboy101st/howto/step4-2.png[/IMG]

[INDENT]**STEP5:** In your layers palette, click on your text layer. Then select the “Magic Wand” tool and start clicking on all of your text until it-and only it-is selected:[/INDENT]

[IMG]http://i97.photobucket.com/albums/l202/soldierboy101st/howto/step5-1.png[/IMG]

[INDENT]NOTE: I'm sure there is an easier way to do that, if you know, comment below. Thanks.
Now in layers palette click on the highlight layer (the one you filled in with white). And do the following on the top menu:
Select>Invert
then:
Edit>Cut

You should end up with this:[/INDENT]

[IMG]http://i97.photobucket.com/albums/l202/soldierboy101st/howto/step5-3.png[/IMG]
[INDENT]
You can now deselect the selection and set your highlight layer's opacity to 46. Then do: Filters>Blur>Blur. Should give it nice crisp edges.[/INDENT]

[IMG]http://i97.photobucket.com/albums/l202/soldierboy101st/howto/step5-4.png[/IMG]

[INDENT]**STEP6:** Now to get that sleek reflection that everyone craves for. Start by merging your top two layers (highlight and text). Do this: Layer>Merge Down

Then right click on the newly merged layer and select “Duplicate Layer”. Drag this duplicate layer below your text layer in the palette. Then do: Layer>Transform>Flip Vertically

Use your “Move” tool to move the layer so it is below your text with a little space:[/INDENT]

[IMG]http://i97.photobucket.com/albums/l202/soldierboy101st/howto/step6-1.png[/IMG]

[INDENT]Lower the Opacity to like 30 something then click on your Gradient tool. Add a gradient to that mirror layer, play around with the settings. I used:

Gradient: FG to Transparent
Mode: Hardlight[/INDENT]

Then simply add one of those trendy “New” buttons, and like magic! A web2.0-like text. (Refer to first image at the top).

Credit to GIMP Galore for their tutorial on creating that red button, [snag it here.]("http://gimpgalore.pandela.net/tutorials/button_orb.html")

Enjoy! Make sure to post your creation in a comment!

---

### Post by Lord Illidan on 2006-12-30
Pictures are worth a 1000 words..

---

### Post by Vadi on 2008-10-12
How do you center the text?

---

