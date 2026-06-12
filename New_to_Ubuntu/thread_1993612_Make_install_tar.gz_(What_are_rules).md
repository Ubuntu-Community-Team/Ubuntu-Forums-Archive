---
title: "Make install tar.gz (What are rules????)"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by vailixi on 2012-06-02
I so don't get this whole installing a tarball thing. So put the thing in home folder, I extract it, cd into /src and configure. It works up to this point but when I go use make and sudo make install I get some messages telling me I need something like rules and target.

What are rules?
What are targets?
What am I missing?
What other book should I read?

Thanks in advance for any help.

---

### Post by steeldriver on 2012-06-02
'rules' and 'targets' are what the 'make' program reads from the makefile during the build

it's usually hierarchical e.g. there are rules to make object files from source code files (aka compile), then rules to make executables from object files and libs (aka link) then often additional rules to install the resulting binaries somewhere

you shouldn't need to mess with any of that if the configure step works right, there are lots of guides on the web to using 'make', but if you prefer a book there's an O'Reilly called "Managing Projects with make" that's a pretty comprehensive reference (although imho it's not an easy read)

[http://shop.oreilly.com/product/9780937175903.do](http://shop.oreilly.com/product/9780937175903.do)

---

### Post by yeats on 2012-06-02
> I so don't get this whole installing a tarball thing. So put the thing in home folder, I extract it, cd into /src and configure. It works up to this point but when I go use make and sudo make install I get some messages telling me I need something like rules and target.

Okay, first of all, if you're just trying to install something, have you checked whether the program exists in the Ubuntu repositories?

If after doing so you still want to install from source, you'll need to provide some more information:

1) which program you're trying to install

2) a paste (in CODE tags - available by clicking the # symbol when composing) of the full error messages you're receiving

3) it would be helpful if you share a link to any tutorial or set of instructions you're following. 

> What other book should I read?

[This thread]("http://ubuntuforums.org/showthread.php?t=1909108") has a huge list of linux command line resources.  I'm sure many of them touch on installation from source.

---

### Post by vailixi on 2012-06-17
OK better question:

Hypothetically this is my program stupid pong game for example (but it could be any stupid code snippet or simple program): How do I compile, make, install, run, whatever in linux? Say just any old .cs, .cpp, or .c file?

```
#include <allegro.h> #include <cstdlib> #include <time.h>   int ball_x = 320; int ball_y = 240;  int ball_tempX = 320; int ball_tempY = 240;  int p1_x = 20; int p1_y = 210;  int p1_tempX = 20; int p1_tempY = 210;  int p2_x = 620; int p2_y = 210;  int p2_tempX = 620; int p2_tempY = 210;  time_t secs;    //The seconds on the system clock will be stored here                 //this will be used as the seed for srand()  int dir;     //This will keep track of the circles direction             //1= up and left, 2 = down and left, 3 = up and right, 4 = down and right  BITMAP *buffer; //This will be our temporary bitmap for double buffering  void moveBall(){      ball_tempX = ball_x;     ball_tempY = ball_y;      if (dir == 1 && ball_x > 5 && ball_y > 5){                if( ball_x == p1_x + 15 && ball_y >= p1_y && ball_y <= p1_y + 60){                   dir = rand()% 2 + 3;          }else{                      --ball_x;                  --ball_y;          }                        } else if (dir == 2 && ball_x > 5 && ball_y < 475){           if( ball_x == p1_x + 15 && ball_y >= p1_y && ball_y <= p1_y + 60){                   dir = rand()% 2 + 3;          }else{                      --ball_x;                  ++ball_y;          }      } else if (dir == 3 && ball_x < 635 && ball_y > 5){           if( ball_x + 5 == p2_x && ball_y >= p2_y && ball_y <= p2_y + 60){                   dir = rand()% 2 + 1;          }else{                      ++ball_x;                  --ball_y;          }      } else if (dir == 4 && ball_x < 635 && ball_y < 475){           if( ball_x + 5 == p2_x && ball_y >= p2_y && ball_y <= p2_y + 60){                   dir = rand()% 2 + 1;          }else{                      ++ball_x;                  ++ball_y;          }      } else {           if (dir == 1 || dir == 3)    ++dir;         else if (dir == 2 || dir == 4)    --dir;      }              acquire_screen();     circlefill ( buffer, ball_tempX, ball_tempY, 5, makecol( 0, 0, 0));     circlefill ( buffer, ball_x, ball_y, 5, makecol( 128, 255, 0));     draw_sprite( screen, buffer, 0, 0);     release_screen();          rest(5);  }      void p1Move(){       p1_tempY = p1_y;       if( key[KEY_W] && p1_y > 0){               --p1_y;                    } else if( key[KEY_S] && p1_y < 420){               ++p1_y;                    }               acquire_screen();     rectfill( buffer, p1_tempX, p1_tempY, p1_tempX + 10, p1_tempY + 60, makecol ( 0, 0, 0));     rectfill( buffer, p1_x, p1_y, p1_x + 10, p1_y + 60, makecol ( 0, 0, 255));     release_screen();            }    void p2Move(){       p2_tempY = p2_y;       if( key[KEY_UP] && p2_y > 0){               --p2_y;                    } else if( key[KEY_DOWN] && p2_y < 420){               ++p2_y;                    }               acquire_screen();     rectfill( buffer, p2_tempX, p2_tempY, p2_tempX + 10, p2_tempY + 60, makecol ( 0, 0, 0));     rectfill( buffer, p2_x, p2_y, p2_x + 10, p2_y + 60, makecol ( 0, 0, 255));     release_screen();            }      void startNew(){      clear_keybuf();     readkey();     clear_to_color( buffer, makecol( 0, 0, 0));     ball_x = 320;     ball_y = 240;      p1_x = 20;     p1_y = 210;      p2_x = 620;     p2_y = 210;  }      void checkWin(){      if ( ball_x < p1_x){         textout_ex( screen, font, "Player 2 Wins!", 320, 240, makecol( 255, 0, 0), makecol( 0, 0, 0));          startNew();     } else if ( ball_x > p2_x){         textout_ex( screen, font, "Player 1 Wins!", 320, 240, makecol( 255, 0, 0), makecol( 0, 0, 0));          startNew();     }         }      void setupGame(){       acquire_screen();     rectfill( buffer, p1_x, p1_y, p1_x + 10, p1_y + 60, makecol ( 0, 0, 255));     rectfill( buffer, p2_x, p2_y, p2_x + 10, p2_y + 60, makecol ( 0, 0, 255));       circlefill ( buffer, ball_x, ball_y, 5, makecol( 128, 255, 0));     draw_sprite( screen, buffer, 0, 0);     release_screen();          time(&secs);     srand( (unsigned int)secs);     dir = rand() % 4 + 1;              }      int main(){      allegro_init();     install_keyboard();     set_color_depth(16);     set_gfx_mode( GFX_AUTODETECT, 640, 480, 0, 0);          buffer = create_bitmap( 640, 480);           setupGame();          while( !key[KEY_ESC]){          p1Move();         p2Move();         moveBall();         checkWin();         }              return 0;  } END_OF_MAIN();
```

---

### Post by MG&amp;TL on 2012-06-17
> **vailixi said:**
> OK better question:

Hypothetically this is my program stupid pong game for example (but it could be any stupid code snippet or simple program): How do I compile, make, install, run, whatever in linux? Say just any old .cs, .cpp, or .c file?

```
#include <allegro.h> #include <cstdlib> #include <time.h>   int ball_x = 320; int ball_y = 240;  int ball_tempX = 320; int ball_tempY = 240;  int p1_x = 20; int p1_y = 210;  int p1_tempX = 20; int p1_tempY = 210;  int p2_x = 620; int p2_y = 210;  int p2_tempX = 620; int p2_tempY = 210;  time_t secs;    //The seconds on the system clock will be stored here                 //this will be used as the seed for srand()  int dir;     //This will keep track of the circles direction             //1= up and left, 2 = down and left, 3 = up and right, 4 = down and right  BITMAP *buffer; //This will be our temporary bitmap for double buffering  void moveBall(){      ball_tempX = ball_x;     ball_tempY = ball_y;      if (dir == 1 && ball_x > 5 && ball_y > 5){                if( ball_x == p1_x + 15 && ball_y >= p1_y && ball_y <= p1_y + 60){                   dir = rand()% 2 + 3;          }else{                      --ball_x;                  --ball_y;          }                        } else if (dir == 2 && ball_x > 5 && ball_y < 475){           if( ball_x == p1_x + 15 && ball_y >= p1_y && ball_y <= p1_y + 60){                   dir = rand()% 2 + 3;          }else{                      --ball_x;                  ++ball_y;          }      } else if (dir == 3 && ball_x < 635 && ball_y > 5){           if( ball_x + 5 == p2_x && ball_y >= p2_y && ball_y <= p2_y + 60){                   dir = rand()% 2 + 1;          }else{                      ++ball_x;                  --ball_y;          }      } else if (dir == 4 && ball_x < 635 && ball_y < 475){           if( ball_x + 5 == p2_x && ball_y >= p2_y && ball_y <= p2_y + 60){                   dir = rand()% 2 + 1;          }else{                      ++ball_x;                  ++ball_y;          }      } else {           if (dir == 1 || dir == 3)    ++dir;         else if (dir == 2 || dir == 4)    --dir;      }              acquire_screen();     circlefill ( buffer, ball_tempX, ball_tempY, 5, makecol( 0, 0, 0));     circlefill ( buffer, ball_x, ball_y, 5, makecol( 128, 255, 0));     draw_sprite( screen, buffer, 0, 0);     release_screen();          rest(5);  }      void p1Move(){       p1_tempY = p1_y;       if( key[KEY_W] && p1_y > 0){               --p1_y;                    } else if( key[KEY_S] && p1_y < 420){               ++p1_y;                    }               acquire_screen();     rectfill( buffer, p1_tempX, p1_tempY, p1_tempX + 10, p1_tempY + 60, makecol ( 0, 0, 0));     rectfill( buffer, p1_x, p1_y, p1_x + 10, p1_y + 60, makecol ( 0, 0, 255));     release_screen();            }    void p2Move(){       p2_tempY = p2_y;       if( key[KEY_UP] && p2_y > 0){               --p2_y;                    } else if( key[KEY_DOWN] && p2_y < 420){               ++p2_y;                    }               acquire_screen();     rectfill( buffer, p2_tempX, p2_tempY, p2_tempX + 10, p2_tempY + 60, makecol ( 0, 0, 0));     rectfill( buffer, p2_x, p2_y, p2_x + 10, p2_y + 60, makecol ( 0, 0, 255));     release_screen();            }      void startNew(){      clear_keybuf();     readkey();     clear_to_color( buffer, makecol( 0, 0, 0));     ball_x = 320;     ball_y = 240;      p1_x = 20;     p1_y = 210;      p2_x = 620;     p2_y = 210;  }      void checkWin(){      if ( ball_x < p1_x){         textout_ex( screen, font, "Player 2 Wins!", 320, 240, makecol( 255, 0, 0), makecol( 0, 0, 0));          startNew();     } else if ( ball_x > p2_x){         textout_ex( screen, font, "Player 1 Wins!", 320, 240, makecol( 255, 0, 0), makecol( 0, 0, 0));          startNew();     }         }      void setupGame(){       acquire_screen();     rectfill( buffer, p1_x, p1_y, p1_x + 10, p1_y + 60, makecol ( 0, 0, 255));     rectfill( buffer, p2_x, p2_y, p2_x + 10, p2_y + 60, makecol ( 0, 0, 255));       circlefill ( buffer, ball_x, ball_y, 5, makecol( 128, 255, 0));     draw_sprite( screen, buffer, 0, 0);     release_screen();          time(&secs);     srand( (unsigned int)secs);     dir = rand() % 4 + 1;              }      int main(){      allegro_init();     install_keyboard();     set_color_depth(16);     set_gfx_mode( GFX_AUTODETECT, 640, 480, 0, 0);          buffer = create_bitmap( 640, 480);           setupGame();          while( !key[KEY_ESC]){          p1Move();         p2Move();         moveBall();         checkWin();         }              return 0;  } END_OF_MAIN();
```

...might want to put some newlines in there. ;)

You would normally use one of the GNU Compiler Collection to compile a single file, but large programs have build systems such as *make* that use rules to compile a lot of files in one command.

---

### Post by vailixi on 2012-06-23
I got c files to compile with gcc but make still doesn't seem to be working out for me. More reading to do. Thanks for the book suggestions.

---

### Post by HiImTye on 2012-06-23
[How to Install Anything in Ubuntu (Condensed)]("http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/")

I generally try to avoid anything that needs to be compiled from source as you need to take care of the libs yourself (and you may run into library conflicts) but sometimes you just can't avoid it. here's how I generally try to install:

1. check the repos
2. check for a PPA (preferably on LaunchPad)
3. check to see if the website has a .deb (as they generally include any lib requirements)
4. check if I can find an alternative
5. consider compiling

---

### Post by steeldriver on 2012-06-23
> **vailixi said:**
> I got c files to compile with gcc but make still doesn't seem to be working out for me. More reading to do. Thanks for the book suggestions.

if you post the makefile and errors in the Development and Programming / Programming Talk subforum I'm sure folks would be willing to help out

---

### Post by vailixi on 2012-08-21
Just started reading *GNU/Linux Application Programming* Second Edition by M. Tim Jones. It makes things look pretty straight forward. I was didn't really feel like waiting for shipping time on the Make book so I took a drive to the nearest Barnes and Noble which for me is about an hour and a half drive. I'll hit you guys when I finish reading this 667 pages of awesomeness.):P

---

