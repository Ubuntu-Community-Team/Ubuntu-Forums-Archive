---
title: "Code::Blocks and Allegro Error."
date: 2010-02-02
forum: Programming Talk
---

### Post by Logan513 on 2010-02-02
Okay, so I have Allegro installed on my computer. And I was starting to learn to use Allegro using this tutorial;

[http://www.youtube.com/watch?v=twCcrheACDY](http://www.youtube.com/watch?v=twCcrheACDY)

I fallowed EVERYTHING it said, and I'm not sure what I am doing wrong. Is it an error on my behalf or hers? Here is what my code looks like....

```
#include <allegro.h>
#include <iostream>
using namespace std;

int main(){

    /* Initialization */
    allegro_init();
    install_keyboard();
    install_timer();
    install_sound( DIGI_AUTODETECT, MIDI_AUTODETECT, 0);
    set_color_depth(16);

    set_gfx_mode(GFX_AUTODETECT_WINDOWED, 640, 480, 0, 0);
    BITMAP *buffer = create_bitmap( 640, 480 );

    while ( !key[KEY_ESC] ){
        rectfill ( buffer, 0, 0, 640, 480, makecol( 255, 0, 0 ) );

         /* Draw Functions */
        blit( buffer, screen, 0, 0, 0, 0, 640, 480 );
        clear_bitmap( buffer );
    }

    destroy_bitmap( buffer );
    return 0;
}
END_OF_MAIN();
```Yes, I did do the little linker thing...

[IMG]http://zaiddownloads.wikispaces.com/file/view/lal.png/117553149/lal.png[/IMG]

But when I try to Build and run the program.... I get all these great little errors telling me things like 'undefined reference to 'XPutImage'.' What do these mean? What's going on? And how do I fix the errors?

I'm sorry, but I am very new to Allegro and don't really know what I'm doing (but I am trying to learn). I am thinking that for some reason it just can't find the library Allegro... I did not include the allegro42.dll in the same file with my main.cpp file. Is that my problem? If so, where can I find this allegro42.dll file? :???:

I am so confused right now... :-|

Thanks,
-Logan- :smile:

---

### Post by Logan513 on 2010-02-02
Now that's odd, after re-watching the tutorial, it warns you about these kinds of errors. But it says that you only get them if I don't include END_OF_MAIN(); Which you can clearly see right there at the end of my code. What am I doing? Is the command that goes in the linker going to be different because it is Linux and not Windows?#-o

---

### Post by Logan513 on 2010-02-02
K, so now I am convinced it is because I did not include the .dll file in with the normal main.cpp. Where do I get the .dll so I can put it in with my file?

---

### Post by Logan513 on 2010-02-02
C'mon!!!! Does no one know? :frown:

---

### Post by Logan513 on 2010-02-03
Well you guys were a great help! I got it all figured out! :D

---

