---
title: "Pong"
date: 2008-03-19
forum: Programming Talk
---

### Post by King Buttons I on 2008-03-19
I am trying to make a Pong clone. Can somebody help me make an AI for the other paddle? If code is posted Java is preffered.
Buttons

---

### Post by Wybiral on 2008-03-19
Make it follow the ball... The less accurate you make it, the easier.

---

### Post by Lster on 2008-03-19
[QUOTE=Wybiral] Make it follow the ball... The less accurate you make it, the easier.[/QUOTE]

I programmed a simple Pong clone once where it predicted the motion of the ball. I couldn't beat it - it was just too fast! ;)

---

### Post by King Buttons I on 2008-03-19
Is there any other way that makes the AI  see random?

---

### Post by King Buttons I on 2008-03-19
Lster
Would you be willing to share the code for your pong clone? 
Buttons

---

### Post by Wybiral on 2008-03-19
> **King Buttons I said:**
> Is there any other way that makes the AI  see random?

Yes, randomize it a little (randomly slow it down, stall it, or make it follow a randomly offset position).

---

### Post by Lster on 2008-03-19
[QUOTE=King Buttons I]Would you be willing to share the code for your pong clone?[/QUOTE]

Sorry to disappoint but I don't have it any more. I only wrote the program as a learning exercise and have deleted that since. I would recommend you to program it yourself, though, as a learning task! :)

Aim simple at first and experiment with new ideas.

---

### Post by Triggerhapp on 2008-03-19
Get the AI to calculate where the ball is going, and store the X co-ordinate, but give it a maximum increment in that direction per frame, higher increment means its alot more likely to reach the position in time.
Just a thought.

---

### Post by Kadrus on 2008-03-19
This code is an example code from [http://www.cppgameprogramming.com](http://www.cppgameprogramming.com)
it's in C++...i don't know if you will understand the code..but it's a pong game
```

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

```
It's done with allegro libraries...

---

### Post by King Buttons I on 2008-03-19
Kadrus that is for two player pong, but thanks for the help. Any more ideas? I have tried multiple ways and none of them work.
Buttons

---

### Post by pmasiar on 2008-03-19
pong in 30 lines of Python, as found at [http://planetpython.org/](http://planetpython.org/)

[http://billmill.org/pong.html](http://billmill.org/pong.html)

Enjoy!

---

### Post by Natr0n on 2008-03-19
> **King Buttons I said:**
> Any more ideas? I have tried multiple ways and none of them work.
Like what, exactly? If you post the code you've written that you're having problems with I'm sure there will be people willing help you get it working.

---

