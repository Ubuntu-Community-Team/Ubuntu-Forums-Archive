---
title: "Project getting started help needed"
date: 2011-02-11
forum: Programming Talk
---

### Post by TpwUK on 2011-02-11
Hi there, I am presently toying with an idea for creating a modular landscape garden design tool that would have independent  tools for creating patio/slabbed areas, shrubbery beds, herbaceous borders, pond design and decking. The design tool also needs to communicate to several mini data base applications that can be used for inserting symbols into the plan whilst still adding specifics about product type or plants.

I seem to have suffered from the over-whelming amount of information that is out there which has left me confused and dizzy, so i could do with some pointers if possible;


[LIST]
[*]which language is better for OpenGL
[*]is there an alternative to OpenGL
[*]are the Berkerley DB libs suitable as i want to try and keep dependencies down
[*]Since at this time, i dont need 3d support is OpenGL too adventurous
[*]WxWidgets, GTK or Qt4
[/LIST]
I am no expert programmer but have dabbled with C++, Delphi, Pascal & Basic so guidance along the lines of any of those languages would be appreciated but i am still open minded.

MTIA
TpwUK

---

### Post by TpwUK on 2011-02-11
PlantStudio was an interesting sounding application but not what the idea here is.

The database element for the plants/flowers will hold photographs of the plant in question and have a CAD like symbol that it can inject into the plan. The photo element being used in a pdf catalogue of the plants used in the plan with other details for cultivation and such.

I was looking at OpenGL for the NURBS possibilities, in particular the ability to add ellipsoid and then manipulate the handles to form better shapes with smoother outlines. Not knowing Cairo, i don't know if it would support gradients and transparency, if it does then i will certainly be taking a closer look at it :)

Thanks for the reply though

TpwUK

---

### Post by TpwUK on 2011-02-12
Well after looking into Cairo, it seems to do precisely what i want, but now i need to know if anybody has a good book for Cairo beginners ??

Any help appreciated

TpwUK

---

### Post by moephan on 2011-02-13
I would do this by using Quickly with Pygtk for your GUI widgets, and Goocanvas for your rendering. AIUI, goocanvas wraps up Cairo, so you can still get a CairoContext if you need. You can also output into pdf, png, etc... fairly easily.

1. Quickly will create the stub Gtk project for
$sudo apt-get install quickly 
$quickly create ubuntu-application plant-studio
(quit the running starter app)
$cd plant-studio
$quickly design
(delete the stuff in the main window you don't need)

Then I would create a [pygoocanvas]("http://people.gnome.org/~gianmt/pygoocanvas/") and use that for placing and moving objects, etc...

The Photobomb project has lots of example code for how to use GooCanvas. You can also get a taste of it from [this tutorial]("http://theravingrick.blogspot.com/2011/01/quickly-tutorial-for-natty-diy-media.html").

HTH

---

### Post by TpwUK on 2011-02-13
Thanks for the tips moephan, Quickly does indeed seem interesting. GooCanvas installed now, so many thanks for the tip there too ... 

Will be looking more closely at Quickly to see if it can cope with the modular approach that i have in mind. If i go into more detail, maybe you already know.

Pond, Shrubbery, Border, Arboretum, Decking and Flag Stones designer tools to be able to run as stand alone applications that can acess their own individual database sets holding CAD like symbols as SVG's and dimensions etc etc.

The main design tool being able to call each of the designing modules as needed but to have access to all the database sets in order to construct a catalogue of the total design to be saved/printed as PDF document for client approval. Any amendments made to the mini designs would still be updated to their save files as in OLE.

I think it might be too adventurous for my programming skills as they are, but hey, you never know, and those skills should improve as i progress

TpwUK

---

### Post by moephan on 2011-02-13
What Quickly does for you is to generate an application to get you started, then makes it easy to share your application via a PPA or other publishing mechanism. So using Quickly won't limit you from doing what you want.

The project you describe does sound ambitious, but you could do everything you want with Python and pygoocanvas, I think.

---

### Post by TpwUK on 2011-02-14
Never tried Python before - so will have to look at the too now ... I love linux but its soooo much reading fodder ... Many thanks though, it's appreciated

TpwUK

---

