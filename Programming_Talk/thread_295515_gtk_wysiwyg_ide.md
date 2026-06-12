---
title: "gtk wysiwyg ide"
date: 2006-11-08
forum: Programming Talk
---

### Post by gareththegeek on 2006-11-08
Hi,

Can anyone recommend (does one exist?) an IDE for use with gtk and c/c++ (or other languages if u prefer) which will allow me to design GUI apps for gnome using a wysiwyg style of editing.

I am used to programming in Windows in IDEs like Delphi 6/.Net and Visual Studio .Net and I'm looking for something similar to ease my transition into the world of linux programming!

I click new form, drag a button on, double click it to add an event handler etc...

Thanks!
G

---

### Post by Choad on 2006-11-08
glade

---

### Post by Engnome on 2006-11-08
> **Choad said:**
> glade

Glade is good yes but not integrated into an IDE. I usually don't use IDE's and the only one having inbuilt gtk wysiwyg designer that I know of is monodevelop. I'm not sure if it can be used for c/c++.

---

### Post by Choad on 2006-11-08
> **Engnome said:**
> Glade is good yes but not integrated into an IDE. I usually don't use IDE's and the only one having inbuilt gtk wysiwyg designer that I know of is monodevelop. I'm not sure if it can be used for c/c++.
does it?

i am using it right now and i am using glade with it....

i cant see a gui editor in here.... (i could easily be wrong tho lol)

---

### Post by Engnome on 2006-11-08
> **Choad said:**
> does it?

i am using it right now and i am using glade with it....

i cant see a gui editor in here.... (i could easily be wrong tho lol)

Haven't used it (is it any good?) but according to [wikipedia]("http://http://en.wikipedia.org/wiki/MonoDevelop") it does have one.

---

### Post by Choad on 2006-11-08
its alright. it has so many features that i would just never use. the only thing i use it for is the management of resource files and stuff. can't be bothered to learn the command line methods for including glade files in to your project. oh and the predicive autocomplete thing is quite nice... but not really that neccessary. 

looked on wiki... aparently its an addon called "stetic" but i cant seem to find it. according to the add-in manager i have "gtk# visual designer" installed.... but no idea how to access it lol

---

### Post by gareththegeek on 2006-11-10
Thanks...

It seems you can use Glade with Anjuta and I thought I might look at that but still don't know what I'm doing lol

So do people normally write Linux apps by handcoding every aspect of the GUI themselves then or what?  I was happily following the Gtk+2 tutorials and it made perfect sense but then I realised I'd written tons of code just to make the simplest of programs...

What is the best way to quickly develop Linux native apps?

G!

---

### Post by Engnome on 2006-11-10
> **gareththegeek said:**
> Thanks...

It seems you can use Glade with Anjuta and I thought I might look at that but still don't know what I'm doing lol

So do people normally write Linux apps by handcoding every aspect of the GUI themselves then or what?  I was happily following the Gtk+2 tutorials and it made perfect sense but then I realised I'd written tons of code just to make the simplest of programs...

What is the best way to quickly develop Linux native apps?

G!

Well IMHO it's good to know what's going on under the hood in wysiwyg editors. It's a good thing you've written lots of code because then you have learnt how you do it the manual way and will have it easier understanding the wysiwyg stuff later.

Our teacher in html was very strict, no wysiwyg editor in the beginning, had we used them we would be like :confused: :confused: :confused: when we had to edit the code by hand later on to add php stuff.

Hadn't I had the basic GTK knowlegde before starting with glade I would have had alot more trouble I think.

I currently use Glade to generate a XML file containing the GUI. I then link that file into my application. This way I can keep GUI and code separated wich gives some benefits.

---

### Post by Choad on 2006-11-10
as is said above, it never hurts to know what is going on under the hood :)

but glade is the most popular wysiwyg editor for gtk (i know of no others really) and k-develop has a *very* visual basic-esque interface that is completely idiot proof for qt apps. but it is obviously not for the visual basic language so thats where the similarities end ;)

to get glade designed forms in to a program, you can either have glade export pure c/c++ code or you can get a glade module for your chosen language and feed it the .glade file. the latter is what im trying to do with c# atm

---

### Post by gareththegeek on 2006-11-10
Cool,

Thanks for the help. I will keep looking at it! ;) 

G!

---

