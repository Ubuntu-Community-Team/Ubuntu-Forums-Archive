---
title: "Allegro Code::Blocks sound error. Please help."
date: 2010-03-04
forum: Programming Talk
---

### Post by Logan513 on 2010-03-04
Okay, so I am using Allegro 4.2 (I think) and Code::Blocks IDE on my Ubuntu 9.04 machine...

Recently I have been learning Allegro and doing some test codes to get more familiar with the library. When I tried this sample code (with all the proper image files and sound files in the same directory as the source file);

```
#include <allegro.h>
#include <iostream>
using namespace std;

void InitAllegro(){
    /* Initialization */
    allegro_init();
    install_keyboard();
    install_timer();
    install_sound( DIGI_AUTODETECT, MIDI_AUTODETECT, NULL);
    set_color_depth(16);
}

volatile long counter = 0;
void IncCtr(){counter++;}

class Object {
    public:
    int x,y,z,f;
};

int manFrame = 0;

int main(){

    InitAllegro();
    set_gfx_mode(GFX_AUTODETECT_WINDOWED, 640, 480, 0, 0);

    LOCK_VARIABLE( counter );
    LOCK_FUNCTION ( IncCtr );
    install_int_ex( IncCtr, BPS_TO_TIMER(90));

    BITMAP *buffer = create_bitmap( 640, 480 );
    BITMAP *imgGrass = load_bitmap("back.bmp", NULL);
    BITMAP *imgHello = load_bitmap("hi.bmp", NULL); // loads & creates the bitmaps

    SAMPLE *sndBlah = load_sample( "tip.wav" );

    Object stickMan;
    stickMan.x=100;
    stickMan.y=100;
    stickMan.z=1;
    stickMan.f=0;

    while ( !key[KEY_ESC] ){
        while (counter > 0){

            if ( key[KEY_SPACE] ){
                play_sample( sndBlah, 255, 128, 1000, false );
            }

            if ( stickMan.f == 0 ){
                manFrame = 0;
            }
            if ( stickMan.f == 1 ){
                manFrame = 32;
            }
            // Get input
            // Update data
            counter -= 1;
        }
        blit ( imgGrass, buffer, 0, 0, 0, 0, 640, 480);
        masked_blit( imgHello, buffer , manFrame, 0, stickMan.x, stickMan.y, 32, 32); // Draw the stickdude to the buffer

        blit( buffer, screen, 0, 0, 0, 0, 640, 480 ); // draw the buffer to the screen
        clear_bitmap( buffer ); // clear the buffer

        if ( manFrame == 32 ){
            stickMan.f = 0;
        }
        if ( manFrame == 0 ){
            stickMan.f = 1;
        }

    } // Game loop ends

    destroy_bitmap( buffer );
    destroy_bitmap( imgGrass );
    destroy_bitmap( imgHello ); // destroy the bitmaps

    destroy_sample( sndBlah );

    return 0; // end the program
}
END_OF_MAIN()

```The sound simply does not work. I don't get any errors, any glitches, or crashing of the program. Just no sound. So I wondered to myself "What am I doing wrong?". And I went to my old buddy Google. Looking for some documentation on the allegro library and what I am doing wrong. Nothing wrong... So I Googled 'Ubuntu Allegro 4.2 sound' only to get people who are complaining about errors with Allegro not being compatible with '**PulseAudio**'.

I have researched this for about a week now only to come up empty handed. I don't think that I am experienced enough with Linux and Allegro to understand exactly what the error is and how I can fix it. So could someone please explain to me (in a way that a complete n00b (which is what I am) could understand) what's going on, why it's going on, and how to fix this so I can not make this mistake in the future.

Thanks for taking the time to read this.
-Logan-

P.S. Almost forgot - somewhere I though I heard someone saying that if you install the newest version of allegro the problem goes away. I don't know if I really read that or if it was just my head making things up since it was two or three days ago.

Also I don't know if this is relavent but in Code::Blocks under linker settings, under other linker options I have this;

```
`allegro-config --libs --static`
```

---

### Post by Logan513 on 2010-03-04
Here's some links to where I found people complaining....

[https://bugs.launchpad.net/ubuntu/+source/allegro4.2/+bug/445945](https://bugs.launchpad.net/ubuntu/+source/allegro4.2/+bug/445945)

[http://pulseaudio.org/ticket/133](http://pulseaudio.org/ticket/133)

The answers probably right in front of my face... I just can't understand it... :-(

---

### Post by Logan513 on 2010-03-05
Anybody got anything?

---

### Post by Logan513 on 2010-03-06
C'mon guys! Is it really that complicated? Can someone at least please post the bash to un-install Allegro 4.2 and install the newer version? :neutral:

Please??? [-o< :cry:

---

### Post by marsteegh on 2010-03-19
> **Logan513 said:**
> C'mon guys! Is it really that complicated? Can someone at least please post the bash to un-install Allegro 4.2 and install the newer version? :neutral:

Please??? [-o< :cry:


since pulseaudio is esound compatible, the allegro esound driver seems to work
it's not autodetected though :-(
if I use 
install_sound(DIGI_ESD, MIDI_NONE, NULL);
to force it I can at least use non-midi sound (or you could use DIGMID for midi).

It sortof works, but as nearly half a second lag :-( so it is not perfect.

---

