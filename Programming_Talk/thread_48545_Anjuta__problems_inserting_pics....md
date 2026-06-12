---
title: "Anjuta : problems inserting pics..."
date: 2005-07-12
forum: Programming Talk
---

### Post by troutrou on 2005-07-12
Hello everybody,

I just completed the 'Hello World' tutorial from Anjuta, which did its magic and got me started with Anjuta. So I am now slowly learning all the bits and bobs I will need to code my own project. I am starting with the GUI part of the project, and this is where I have my first problem:

In Glade, to insert a pic I click on "GTK+ Basic" on the palette tool, then I insert a "Gtk Image" type widget. I didn't see any other widget to add pics, so I hope this is the right one.
Then in the widget properties window, I click on the 3 dots of the 'icon' property field, and I browse my /home folder to pick up the desired picture. I noticed that Glade put a copy of the picture, in the "pixmaps" folder of the project.
It seems to go fine (Glade displays the pic where intended), so I do as per the tutorial : Save, Build, then I exit Glade to go back to Anjuta. Then I "Build all", then I "Execute".

And there is the problem : my program loads okay, the GUI pops up etc, but my pic does not display ! :-/  In the terminal window, an error message says the pic could not be found :-/  
One thing that's strange is that the erro message was expecting the pic to be /pengu-scan/home.png  wherease Glade put it in  /pengu-scan/pixmaps/home.png.

That's strange enough, but is more strange is that even if I put a copy of the pic in /pengu-scan , where the error message pretends to be looking for the file, well, even in this case, it still complains that it can't find it !

What am doing wrong ?  If anybody managed to insert pics in a Gnome 2.0 (C language) project successfully, could you give me guidance please ?

I had a look at the Anjuta website for help material, but there isn't anything of particular interest. I wanted to subscribe to their user maling list, thinking it would be full of gurus to sort me out in seconds, but, big disappointment : their mailing list is absolutely useless, it is dead. their archives reaveals an averga of 10 messages per MONTH. Yes, not per day... per month. :-/ :o((((


Thank you very much in advance for any help...

--
Vince

EDIT: I noticed that Anjuta didn't automatically add my pic to the project tree. So I clicked on Project->Add File -> Pixmap file ,  and browsed to the copy of the pic that Glade put in the pixmap folder. Then Anjuta successfully added it to the project tree, I save the project, I "Build All" then "Execute", hoping for the best.... and getting the worst !  Yep, my pic still won't show up !! :o(
I can't believe that such a simple thing is causing me so much problems, heeeelp... :o(((

---

