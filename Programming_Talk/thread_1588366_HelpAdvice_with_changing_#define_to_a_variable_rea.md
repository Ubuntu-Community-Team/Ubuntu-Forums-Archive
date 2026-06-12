---
title: "Help/Advice with changing #define to a variable read from gtkrc (Murrine Gtk engine)"
date: 2010-10-04
forum: Programming Talk
---

### Post by SoftwareExplorer on 2010-10-04
I been trying to implement the requested feature at [http://www.cimitan.com/murrine/node/204](http://www.cimitan.com/murrine/node/204) . Previously, the opacity of widgets was set with #define s in support.h, which makes it so you have to recompile the whole thing if you want to change the opacity. 
I have the code I am experimenting on at [https://code.launchpad.net/~erik-b-andersen/gtk2-engines-murrine/MurrineGtkrcOpacity](https://code.launchpad.net/~erik-b-andersen/gtk2-engines-murrine/MurrineGtkrcOpacity).  First, I tried making the 'variables' defined in support.h into extern floats in support.h and actually setting them in some other file (I've forgotten which one now) and it worked. However, I couldn't figure out how to read from a file to set them when it runs, so I decided to make it loaded from the gtkrc. I figured if I do that, the data should be stored along with other theme data, which would probably be the most correct way to do it anyway. I tried it and it seems to work great when I am compiling for murrine_draw.c, however, in murrine_draw_rgba.c I keep getting errors that say that the 'murrine_style' is undefined, which the variables are a member of. I'm not quite sure how the functions in murrine_draw_rgba.c should be given the data. I could possibly modify some of the struct s that all the functions are passed to have the data, or I could maybe change what the functions are passed (if I found all the places they were called, which may be just making me problem larger), or I could possibly email the developer (but I don't know if I should bother him) and ask him what would be better. 

I would like to do this the correct way, because I would like to propose it upstream when I get it working.
[https://code.launchpad.net/~erik-b-andersen/gtk2-engines-murrine/MurrineGtkrcOpacity](https://code.launchpad.net/~erik-b-andersen/gtk2-engines-murrine/MurrineGtkrcOpacity)

---

### Post by SoftwareExplorer on 2010-10-05
Ok, I got my problem solved. I changed the WidgetParameters in murrine_types.h type to include the data and changed murrine_style.c to set the new data in the murrine_set_widget_parameters, and then updated murrine_draw_rgba.c to use the new variables.

---

