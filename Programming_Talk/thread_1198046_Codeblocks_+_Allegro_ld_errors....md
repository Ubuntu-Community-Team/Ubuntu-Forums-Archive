---
title: "Code::blocks + Allegro ld errors..."
date: 2009-06-26
forum: Programming Talk
---

### Post by Nuticulus on 2009-06-26
Hi,

I'm trying to set up Allegro with codeblocks. I have put ```
`allegro-config --libs --static`
``` in the linker settings, and have the following c++ code:
```
#include <allegro.h>

int main()
{
    //Initialize Allegro
    allegro_init();

    //Set the resolution to 640 x 480 with SAFE autodetection.
    set_gfx_mode(GFX_SAFE, 640, 480, 0, 0);

    //Install the keyboard handler
    install_keyboard();

    //Print your welcome message to the screen
    textout(screen, font, "Hello Dream.In.Code! This is my first Allegro Program", 1, 1, 10);
    textout(screen, font, "Press ESCape to quit.", 1, 12, 11);

    //Loop until escape is pressed
    while(! key[KEY_ESC])
        poll_keyboard();

    //Exit program
    allegro_exit();
    return 0;
}

END_OF_MAIN();
```

When I compile, I get the following error:
```
ld  -  cannot find -l-L/usr/lib -Wl,-Bsymbolic-functions -lalleg -lm -lXxf86vm -lXcursor -lXpm -lXext -lX11 -lpthread -ldl
```

Anyone know what's wrong?

---

### Post by babatunde on 2009-11-23
Hi!. Had been trying for some time now, but finally i had a breakthrough.
If u've installed everything correctly, i.e codeblocks and allegro. You can install allegro from command line. 
sudo apt-get install liballegro4.2-dev.

Next, go to application, system tools, konsole.
In the konsole type allegro-config --libs.
copy the path diplayed. Now go to codeblocks, to settings, to compiler and debbuger, click linker settings, in the other linkers option field paste the copied link, click okay and u're good to start programming game and graphics. Good luck

---

