---
title: "Netbeans will not compile Allegro code!!!!!!"
date: 2010-10-28
forum: Packaging and Compiling Programs
---

### Post by kdizil on 2010-10-28
I installed allegro 4.4 and i am now trying to compile and run a program in netbeans 6.9.1 but it will not work here is the code and error message that i get ```
#include <allegro.h>
#include <cstdlib>
#include <time.h>


int ball_x = 320;
int ball_y = 240;

int ball_tempX = 320;
int ball_tempY = 240;

int p1_x = 20;
int p1_y = 210;

int p1_tempX = 20;
int p1_tempY = 210;

int p2_x = 620;
int p2_y = 210;

int p2_tempX = 620;
int p2_tempY = 210;

time_t secs;    //The seconds on the system clock will be stored here
                //this will be used as the seed for srand()

int dir;     //This will keep track of the circles direction
            //1= up and left, 2 = down and left, 3 = up and right, 4 = down and right

BITMAP *buffer; //This will be our temporary bitmap for double buffering

void moveBall(){

    ball_tempX = ball_x;
    ball_tempY = ball_y;

    if (dir == 1 && ball_x > 5 && ball_y > 5){

         if( ball_x == p1_x + 15 && ball_y >= p1_y && ball_y <= p1_y + 60){
                  dir = rand()% 2 + 3;
         }else{
                 --ball_x;
                 --ball_y;
         }

    } else if (dir == 2 && ball_x > 5 && ball_y < 475){

         if( ball_x == p1_x + 15 && ball_y >= p1_y && ball_y <= p1_y + 60){
                  dir = rand()% 2 + 3;
         }else{
                 --ball_x;
                 ++ball_y;
         }

    } else if (dir == 3 && ball_x < 635 && ball_y > 5){

         if( ball_x + 5 == p2_x && ball_y >= p2_y && ball_y <= p2_y + 60){
                  dir = rand()% 2 + 1;
         }else{
                 ++ball_x;
                 --ball_y;
         }

    } else if (dir == 4 && ball_x < 635 && ball_y < 475){

         if( ball_x + 5 == p2_x && ball_y >= p2_y && ball_y <= p2_y + 60){
                  dir = rand()% 2 + 1;
         }else{
                 ++ball_x;
                 ++ball_y;
         }

    } else {

        if (dir == 1 || dir == 3)    ++dir;
        else if (dir == 2 || dir == 4)    --dir;

    }

    acquire_screen();
    circlefill ( buffer, ball_tempX, ball_tempY, 5, makecol( 0, 0, 0));
    circlefill ( buffer, ball_x, ball_y, 5, makecol( 128, 255, 0));
    draw_sprite( screen, buffer, 0, 0);
    release_screen();

    rest(5);

}

void p1Move(){

    p1_tempY = p1_y;

    if( key[KEY_W] && p1_y > 0){

        --p1_y;

    } else if( key[KEY_S] && p1_y < 420){

        ++p1_y;

    }

    acquire_screen();
    rectfill( buffer, p1_tempX, p1_tempY, p1_tempX + 10, p1_tempY + 60, makecol ( 0, 0, 0));
    rectfill( buffer, p1_x, p1_y, p1_x + 10, p1_y + 60, makecol ( 0, 0, 255));
    release_screen();

}

void p2Move(){

    p2_tempY = p2_y;

    if( key[KEY_UP] && p2_y > 0){

        --p2_y;

    } else if( key[KEY_DOWN] && p2_y < 420){

        ++p2_y;

    }

    acquire_screen();
    rectfill( buffer, p2_tempX, p2_tempY, p2_tempX + 10, p2_tempY + 60, makecol ( 0, 0, 0));
    rectfill( buffer, p2_x, p2_y, p2_x + 10, p2_y + 60, makecol ( 0, 0, 255));
    release_screen();

}

void startNew(){

    clear_keybuf();
    readkey();
    clear_to_color( buffer, makecol( 0, 0, 0));
    ball_x = 320;
    ball_y = 240;

    p1_x = 20;
    p1_y = 210;

    p2_x = 620;
    p2_y = 210;

}

void checkWin(){

    if ( ball_x < p1_x){
        textout_ex( screen, font, "Player 2 Wins!", 320, 240, makecol( 255, 0, 0), makecol( 0, 0, 0));
        startNew();
    } else if ( ball_x > p2_x){
        textout_ex( screen, font, "Player 1 Wins!", 320, 240, makecol( 255, 0, 0), makecol( 0, 0, 0));
        startNew();
    }

}

void setupGame(){

    acquire_screen();
    rectfill( buffer, p1_x, p1_y, p1_x + 10, p1_y + 60, makecol ( 0, 0, 255));
    rectfill( buffer, p2_x, p2_y, p2_x + 10, p2_y + 60, makecol ( 0, 0, 255));
    circlefill ( buffer, ball_x, ball_y, 5, makecol( 128, 255, 0));
    draw_sprite( screen, buffer, 0, 0);
    release_screen();

    time(&secs);
    srand( (unsigned int)secs);
    dir = rand() % 4 + 1;

}

int main(){

    allegro_init();
    install_keyboard();
    set_color_depth(16);
    set_gfx_mode( GFX_AUTODETECT, 640, 480, 0, 0);

    buffer = create_bitmap( 640, 480);

    setupGame();

    while( !key[KEY_ESC]){

        p1Move();
        p2Move();
        moveBall();
        checkWin();

    }

    return 0;

}
END_OF_MAIN();

"/usr/bin/make" -f nbproject/Makefile-Debug.mk QMAKE= SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/kdizil/NetBeansProjects/CppApplication_4'
"/usr/bin/make"  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/cppapplication_4
make[2]: Entering directory `/home/kdizil/NetBeansProjects/CppApplication_4'
mkdir -p dist/Debug/GNU-Linux-x86
c++     -o dist/Debug/GNU-Linux-x86/cppapplication_4 build/Debug/GNU-Linux-x86/main.o build/Debug/GNU-Linux-x86/newfile.o  
make[2]: Leaving directory `/home/kdizil/NetBeansProjects/CppApplication_4'
make[1]: Leaving directory `/home/kdizil/NetBeansProjects/CppApplication_4'
build/Debug/GNU-Linux-x86/newfile.o: In function `main':
/home/kdizil/NetBeansProjects/CppApplication_4/newfile.cpp:4: multiple definition of `main'
build/Debug/GNU-Linux-x86/main.o:/home/kdizil/NetBeansProjects/CppApplication_4/main.cpp:175: first defined here
build/Debug/GNU-Linux-x86/main.o: In function `acquire_screen':
main.cpp:(.text+0x76): undefined reference to `screen'
build/Debug/GNU-Linux-x86/main.o: In function `release_screen':
main.cpp:(.text+0x8b): undefined reference to `screen'
build/Debug/GNU-Linux-x86/main.o: In function `moveBall()':
main.cpp:(.text+0x43e): undefined reference to `makecol'
main.cpp:(.text+0x488): undefined reference to `makecol'
main.cpp:(.text+0x4c1): undefined reference to `screen'
main.cpp:(.text+0x4ee): undefined reference to `rest'
build/Debug/GNU-Linux-x86/main.o: In function `p1Move()':
main.cpp:(.text+0x50e): undefined reference to `key'
main.cpp:(.text+0x541): undefined reference to `key'
main.cpp:(.text+0x58f): undefined reference to `makecol'
main.cpp:(.text+0x5eb): undefined reference to `makecol'
build/Debug/GNU-Linux-x86/main.o: In function `p2Move()':
main.cpp:(.text+0x652): undefined reference to `key'
main.cpp:(.text+0x685): undefined reference to `key'
main.cpp:(.text+0x6d3): undefined reference to `makecol'
main.cpp:(.text+0x72f): undefined reference to `makecol'
build/Debug/GNU-Linux-x86/main.o: In function `startNew()':
main.cpp:(.text+0x787): undefined reference to `clear_keybuf'
main.cpp:(.text+0x78c): undefined reference to `readkey'
main.cpp:(.text+0x7a8): undefined reference to `makecol'
build/Debug/GNU-Linux-x86/main.o: In function `checkWin()':
main.cpp:(.text+0x82a): undefined reference to `makecol'
main.cpp:(.text+0x848): undefined reference to `makecol'
main.cpp:(.text+0x84e): undefined reference to `font'
main.cpp:(.text+0x854): undefined reference to `screen'
main.cpp:(.text+0x880): undefined reference to `textout_ex'
main.cpp:(.text+0x8b5): undefined reference to `makecol'
main.cpp:(.text+0x8d3): undefined reference to `makecol'
main.cpp:(.text+0x8d9): undefined reference to `font'
main.cpp:(.text+0x8df): undefined reference to `screen'
main.cpp:(.text+0x90b): undefined reference to `textout_ex'
build/Debug/GNU-Linux-x86/main.o: In function `setupGame()':
main.cpp:(.text+0x940): undefined reference to `makecol'
main.cpp:(.text+0x99c): undefined reference to `makecol'
main.cpp:(.text+0x9f8): undefined reference to `makecol'
main.cpp:(.text+0xa31): undefined reference to `screen'
build/Debug/GNU-Linux-x86/main.o: In function `main':
main.cpp:(.text+0xabd): undefined reference to `_install_allegro_version_check'
main.cpp:(.text+0xac2): undefined reference to `install_keyboard'
main.cpp:(.text+0xace): undefined reference to `set_color_depth'
main.cpp:(.text+0xafa): undefined reference to `set_gfx_mode'
main.cpp:(.text+0xb0e): undefined reference to `create_bitmap'
main.cpp:(.text+0xb35): undefined reference to `key'
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/cppapplication_4] Error 1
make[1]: *** [.build-conf] Error 2
make: *** [.build-impl] Error 2

BUILD FAILED (exit value 2, total time: 188ms)


```
Please help :confused:

---

### Post by SevenMachines on 2010-10-28
You need to add libs and flags for allegro to your netbeans project settings, sorry i dont know how to do that but, if your simple file is called example.cpp then
> $  g++ -o example example.cpp `allegro-config --libs --cflags` 

allegro-config sets the right includes and linkage parameters (no i dont know why it doesnt use package config :) )

---

### Post by kdizil on 2010-10-30
Thank you seven but i switched to codeblocks because netbeans would not allow me to add libraries but now i have a new problem it seems code::blocks does not recognize the >> operator so its like out of the frying pan and into the fire

---

### Post by GabrielYYZ on 2010-10-30
> **kdizil said:**
> Thank you seven but i switched to codeblocks because netbeans would not allow me to add libraries but now i have a new problem it seems code::blocks does not recognize the >> operator so its like out of the frying pan and into the fire

in netbeans you can add libraries (unless i'm completely mistaken)

open netbeans, then Tools > Libraries and then there's "new library..." or the classpath and/or sources tabs. i'm pretty new at this, so i apologize in advance if that's not what you're talking about.

---

