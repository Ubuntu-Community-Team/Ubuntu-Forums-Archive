---
title: "Allegro, C++ &amp; Pong Like Movement"
date: 2009-08-31
forum: Programming Talk
---

### Post by matmatmat on 2009-08-31
I have this code - mostly taking from [here]("http://www.cppgameprogramming.com/"):
```

#include <allegro.h>
#include <cstdlib>

int x = 100;
int y = 100;
int tempX;
int tempY;

BITMAP *ball;

int dir = 1; //This will keep track of the circles direction
            //1= up and left, 2 = down and left, 3 = up and right, 4 = down and right

void moveCircle(){

    tempX = x;
    tempY = y;

    if (dir == 1 && x != 20 && y != 20){

        --x;
        --y;

    } else if (dir == 2 && x != 20 && y != 460){

        --x;
        ++y;

    } else if (dir == 3 && x != 620 && y != 20){

        ++x;
        --y;

    } else if (dir == 4 && x != 620 && y != 460){

        ++x;
        ++y;
    } else {

        if (dir == 1){
            dir += 2;
        }else if (dir == 2){
            dir += 2;
        }else{
            dir = 1;
        }

    }

    acquire_screen();
    circlefill ( screen, tempX, tempY, 30, makecol( 0, 0, 0));
    draw_sprite( screen, ball, x, y);
    release_screen();

    rest(10);

}

int main(){

    allegro_init();
    install_keyboard();
    set_color_depth(16);
    set_gfx_mode( GFX_AUTODETECT, 640, 480, 0, 0);
    ball = load_bitmap( "data/ball.bmp", NULL);
    while( !key[KEY_ESC]){
        moveCircle();
    }

    return 0;

}
END_OF_MAIN();

```
The ball should move like the ball in pong, but it just stays still?

---

### Post by Namtabmai on 2009-08-31
You've missed the bit of code to get the key press and update "dir" variable.

In the original tutorials it's the p1move and p2move functions.

---

### Post by matmatmat on 2009-09-01
Sorry, i meant [http://www.cppgameprogramming.com/cgi/nav.cgi?page=alleganimation]("http://www.cppgameprogramming.com/cgi/nav.cgi?page=alleganimation"), I haven't even looked at the example - I was going to write it myself & then see how they did it.

---

### Post by Namtabmai on 2009-09-01
Sorry looking at the wrong code.

You've still missed out

```

    } else { 

        dir = rand() % 4 + 1;

    }   

```

thou.

---

