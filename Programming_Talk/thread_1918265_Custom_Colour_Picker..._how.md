---
title: "Custom Colour Picker... how?"
date: 2012-01-31
forum: Programming Talk
---

### Post by fallenshadow on 2012-01-31
Hey there,

Does anyone know how to design something like this?

[IMG]http://ubuntuone.com/0kDGmnXBUejGrlMCVQhHiV[/IMG]

Im using Gtkmm and Glade... I know Glade woudn't be able to help me... so does that mean I would have to do some kind of custom widget in Gtkmm?

---

### Post by Hetepeperfan on 2012-01-31
I think Gtk and gtkmm have a special widget for that:

[http://developer.gnome.org/gtkmm/stable/classGtk_1_1ColorSelection.html](http://developer.gnome.org/gtkmm/stable/classGtk_1_1ColorSelection.html)

for gtkmm

and 

[http://developer.gnome.org/gtk/stable/GtkColorSelection.html](http://developer.gnome.org/gtk/stable/GtkColorSelection.html)

for gtk. Thus no need to create it.

cheers

---

### Post by fallenshadow on 2012-02-01
Yes but it looks nothing like what I posted and does not provide the same functionality.

It allows you to pick a single colour:
[IMG]http://developer.gnome.org/gtkmm/stable/colorselectiondialog1.png[/IMG]

The first example I posted allows 2 different colours to be picked and colour selection without opening any kind of dialog.

---

### Post by epicoder on 2012-02-01
The GIMP uses the GPL license, so as long as you also release your software under the GPL and credit the GIMP team for the original code, you can use their code with your modifications. They have implemented a color picker functionally identical to what you are looking for. Only a small modification would be required to add the color palette shown in the image.

[GIMP 2.6 source](ftp://ftp.gimp.org/pub/gimp/v2.6/)

---

### Post by fallenshadow on 2012-02-01
Yes I thought of this idea when I opened up GIMP... however I downloaded their source code and just got lost in all the folders and files.

Ive no idea where the code for the colour selection is. I probably wouldn't be skilled enough to use it anyway. Im still a pretty novice developer! :D

You are right though, it would be the right approach to just use their code and give credit.

---

### Post by fallenshadow on 2012-02-02
The GIMP source was a bit complicated for me. For now I might just try and use a colour selection button.

However I am having trouble placing it... here is where I want to put the button:

[IMG]http://ubuntuone.com/2sSiAtMKTwbGO0D6onqdDK[/IMG]

Unfortuately Glade doesn't seem to allow placement of it there. Glade file attached if anyone wants to take a look.

---

### Post by pbrane on 2012-02-02
I sent you an email with the modified glade file. Have a look at it. Basically you just select the toolpalette placeholder widget and right-click -> add-parent, choose a vbox with two positions and then move the toolpalette placer holder widget to the second position. Add the color button to the first position in the new vbox, done. You could even modify this to use a custom color picker using a placeholder widget instead of the colorbutton, or even just replace the colorbutton itself in code, much like the toolpalette placceholder.

---

### Post by fallenshadow on 2012-02-02
Thanks!

---

