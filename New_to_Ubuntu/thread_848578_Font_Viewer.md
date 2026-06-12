---
title: "Font Viewer"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by spud.dups on 2008-07-03
I have a package of over 12,000 fonts.  In Windows I used to use a program called AMP Font Viewer, where I could view the fonts that I have and install/uninstall them as I wished.  This helped keep my system running faster and cleaner.  Two questions:

-Would it slow down my computer like in Windows to install so many fonts all at once? (Running Hardy)

-Does there exists a font viewer/installer program that I can use to install fonts as I need them?

Thanks

---

### Post by Daveth on 2008-07-03
I cannot vouch for any of them but these exist to view

[http://opcion.sourceforge.net/](http://opcion.sourceforge.net/)

[http://gfontview.sourceforge.net/](http://gfontview.sourceforge.net/)

[http://www.linux.com/articles/48472](http://www.linux.com/articles/48472)

[http://www.associatedcontent.com/article/727765/fontmatrix_a_great_font_viewer_and.html](http://www.associatedcontent.com/article/727765/fontmatrix_a_great_font_viewer_and.html)

etc etc

Might be worth poking around in Synaptic to see if there is anything in there in addition.

---

### Post by spud.dups on 2008-07-08
Thanks for that list.  So you know Opcion is the easiest to use.

---

### Post by pterosky on 2012-10-29
Opcion Font Viewer is a great little program, thanks guys :)

How to install a .jar file like Opcion_v1.1.1.jar and create a shortcut to it:

Download the file to your desktop from here: [http://opcion.sourceforge.net/](http://opcion.sourceforge.net/)

Create a folder called "opcion" and put the file Opcion_v1.1.1.jar in it. Extract the file (right-click > 'Extract here') if you want to add an icon later, though it's not necessary.

Then move the folder to Ubuntu's programs folder, in terminal:
```
sudo mv ~/Desktop/opcion/ /usr/share/
```

To create a shortcut (in Gnome, I am not sure how in 12.04 Unity): Right click on 'Applications' in upper left corner, select 'Edit menus' > 'Graphics' and click 'New Item'. 

Name: Opcion font viewer
Command: java -jar /usr/share/opcion/Opcion_v1.1.1.jar

If you extracted the folder, you can add an icon: Click on the trampolin icon to the left and navigate to /usr/share/opcion/Opcion_v1.1.1/FontViewer/resources/icons and select IconSmall.png

---

### Post by coffeecat on 2012-10-29
Old thread - closed.

---

