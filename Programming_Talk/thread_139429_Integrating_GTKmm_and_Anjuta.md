---
title: "Integrating GTKmm and Anjuta?"
date: 2006-03-04
forum: Programming Talk
---

### Post by Zdravko on 2006-03-04
How do I integrate GTKmm into Anjta? I see that there is already a Project option for this, but I am unsure, whether all needed libraries are installed. Do I need to download anything additional?

---

### Post by Zdravko on 2006-03-04
Ok, I guess I managed some achievement.  installed GTK+, then GTKmm. I added the following options in the Anjuta's compiler/linker:
> 
`pkg-config gtkmm-2.4 --cflags`

> 
`pkg-config gtkmm-2.4 --libs`

The source looks in that simple way:
> 
#include <gtkmm.h>

int main(int argc, char *argv[])
{
    Gtk::Main kit(argc, argv);

    Gtk::Window window;

    Gtk::Main::run(window);
    
    return 0;
}

The compile process ends with no errors! :) But then the Generating process alerts that there is no target for make. What do I do next?

---

### Post by PsychoBrat on 2006-04-08
Where exactly in the options do the top two lines need to be added?

Cheers. :)

---

### Post by PsychoBrat on 2006-04-08
Ok, after a ainy bit of fiddling, the following worked for me:

The two lines given by Zdravko go in "Compiler Flags (CFLAGS)" and "Linker Flags (LDFLAGS)" respectively.

If you're going to do this, you'll want to use a generic console application, else Anjuta will try to link in all the gtkmm-2.0 stuff anyway.

The other option is to replace all instances of "gtkmm-2.0" with "gtkmm-2.4" in the file 'configure', which should be in the same folder as your project.

I'm not sure if any of this disadvantages you over a 'properly working' version (i.e. maybe function call tips might be missing) because I haven't had any experience with it, so don't know what to expect! If anyone else can fill this part in, I'd be grateful. :)

With any luck, Anjuta 2 will be more flexible; I'll look into this.

---

