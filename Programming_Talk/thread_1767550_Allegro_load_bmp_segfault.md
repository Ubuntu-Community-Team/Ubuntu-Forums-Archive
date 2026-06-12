---
title: "Allegro load_bmp segfault"
date: 2011-05-25
forum: Programming Talk
---

### Post by airborne2k10 on 2011-05-25
Hello. I'm using the allegro to try to create some simple graphics. Im trying to initialize an object with the file path to the .bmp file so that allegro can load it. This will compile, but for some reason when I run it, it produces a segmentation fault.


#include <iostream>
#include <allegro.h>
#include <cstdlib>
#include <cmath>
#include <string>

using namespace std;

class Enemies {
    private:
        int hp;
        int down;
        int up;
        int left;
        int right;

        BITMAP *image;

    public:
        BITMAP* getImage(){return image;}

        Enemies(char *imgfile){
            image = load_bitmap(imgfile, NULL);
        }
};

int main(){

    Enemies *Collin = new Enemies("bomberman.bmp");

    allegro_init();
    set_gfx_mode(GFX_SAFE, 640, 480, 0, 0);

    install_keyboard();
    BITMAP *buffer = create_bitmap(640, 480);
    while(! key[KEY_ESC]){
        poll_keyboard();
        clear(buffer);
        //blit(Collin->getImage(), buffer, 0, 0, 0, 0,20,20);
        blit(screen, buffer, 0, 0, 0, 0, 640, 480);


    }
}

---

### Post by Arndt on 2011-05-26
> **airborne2k10 said:**
> Hello. I'm using the allegro to try to create some simple graphics. Im trying to initialize an object with the file path to the .bmp file so that allegro can load it. This will compile, but for some reason when I run it, it produces a segmentation fault.


#include <iostream>
#include <allegro.h>
#include <cstdlib>
#include <cmath>
#include <string>

using namespace std;

class Enemies {
    private:
        int hp;
        int down;
        int up;
        int left;
        int right;

        BITMAP *image;

    public:
        BITMAP* getImage(){return image;}

        Enemies(char *imgfile){
            image = load_bitmap(imgfile, NULL);
        }
};

int main(){

    Enemies *Collin = new Enemies("bomberman.bmp");

    allegro_init();
    set_gfx_mode(GFX_SAFE, 640, 480, 0, 0);

    install_keyboard();
    BITMAP *buffer = create_bitmap(640, 480);
    while(! key[KEY_ESC]){
        poll_keyboard();
        clear(buffer);
        //blit(Collin->getImage(), buffer, 0, 0, 0, 0,20,20);
        blit(screen, buffer, 0, 0, 0, 0, 640, 480);


    }
}

Could it be the case that you must call allegro_init before load_bitmap? I don't know - I haven't used Allegro.

Where in the program does it crash? Have you used the debugger on it?

---

