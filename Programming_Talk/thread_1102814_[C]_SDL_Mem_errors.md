---
title: "[C] SDL Mem errors?"
date: 2009-03-22
forum: Programming Talk
---

### Post by OutOfReach on 2009-03-22
Hey, I'm starting out with SDL and I've been slowly but surely making a Tic Tac Toe game. I have check with the KDE system monitor and my program is usually in the 2mb range. Now, Valgrind is reporting all kinds of things.
These are the errors that it gives me after the game has finished normally:
```

==1472== ERROR SUMMARY: 14 errors from 8 contexts (suppressed: 50 from 2)                                                                   
==1472== malloc/free: in use at exit: 2,620,841 bytes in 2,447 blocks.                                                                      
==1472== malloc/free: 17,828 allocs, 15,381 frees, 5,961,308 bytes allocated.                                                               
==1472== For counts of detected errors, rerun with: -v                                                                                      
==1472== searching for pointers to 2,447 not-freed blocks.
==1472== checked 2,649,216 bytes.
==1472==
==1472==
==1472== 27 bytes in 1 blocks are definitely lost in loss record 17 of 152
==1472==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)
==1472==    by 0x6AD6EF9: XauFileName (in /usr/lib/libXau.so.6.0.0)
==1472==    by 0x6AD713E: XauGetBestAuthByAddr (in /usr/lib/libXau.so.6.0.0)
==1472==    by 0x68C69A1: _xcb_get_auth_info (in /usr/lib/libxcb.so.1.1.0)
==1472==    by 0x68C6708: xcb_connect (in /usr/lib/libxcb.so.1.1.0)
==1472==    by 0x65CCE59: _XConnectXCB (in /usr/lib/libX11.so.6.2.0)
==1472==    by 0x65B54DC: XOpenDisplay (in /usr/lib/libX11.so.6.2.0)
==1472==    by 0x4E689A6: X11_Available (in /usr/lib/libSDL-1.2.so.0.11.2)
==1472==    by 0x4E58B9B: SDL_VideoInit (in /usr/lib/libSDL-1.2.so.0.11.2)
==1472==    by 0x4E2F4E6: SDL_InitSubSystem (in /usr/lib/libSDL-1.2.so.0.11.2)
==1472==    by 0x4E2F52E: SDL_Init (in /usr/lib/libSDL-1.2.so.0.11.2)
==1472==    by 0x40278D: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)
==1472==
==1472==
==1472== 192 (16 direct, 176 indirect) bytes in 1 blocks are definitely lost in loss record 34 of 152
==1472==    at 0x4C23A51: realloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)
==1472==    by 0x65D8D61: add_codeset (in /usr/lib/libX11.so.6.2.0)
==1472==    by 0x65D960A: load_generic (in /usr/lib/libX11.so.6.2.0)
==1472==    by 0x65DA8D4: initialize (in /usr/lib/libX11.so.6.2.0)
==1472==    by 0x65DB145: _XlcCreateLC (in /usr/lib/libX11.so.6.2.0)
==1472==    by 0x65F9F5F: _XlcDefaultLoader (in /usr/lib/libX11.so.6.2.0)
==1472==    by 0x65E30AA: _XOpenLC (in /usr/lib/libX11.so.6.2.0)
==1472==    by 0x65E3197: _XlcCurrentLC (in /usr/lib/libX11.so.6.2.0)
==1472==    by 0x65E376C: XSetLocaleModifiers (in /usr/lib/libX11.so.6.2.0)
==1472==    by 0x4E67EEB: create_aux_windows (in /usr/lib/libSDL-1.2.so.0.11.2)
==1472==    by 0x4E68C5B: X11_VideoInit (in /usr/lib/libSDL-1.2.so.0.11.2)
==1472==    by 0x4E58AD3: SDL_VideoInit (in /usr/lib/libSDL-1.2.so.0.11.2)
==1472==
==1472==
==1472== 41,716 (30,984 direct, 10,732 indirect) bytes in 1 blocks are definitely lost in loss record 143 of 152
==1472==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)
==1472==    by 0x4046B16: TTF_OpenFontIndexRW (in /usr/lib/libSDL_ttf-2.0.so.0.6.3)
==1472==    by 0x40319C: DisplayText (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)
==1472==    by 0x402AA1: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)
==1472==
==1472==
==1472== 135,680 (88 direct, 135,592 indirect) bytes in 1 blocks are definitely lost in loss record 148 of 152
==1472==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)
==1472==    by 0x4E554FF: SDL_CreateRGBSurface (in /usr/lib/libSDL-1.2.so.0.11.2)
==1472==    by 0x4047752: TTF_RenderUNICODE_Blended (in /usr/lib/libSDL_ttf-2.0.so.0.6.3)
==1472==    by 0x4047B34: TTF_RenderText_Blended (in /usr/lib/libSDL_ttf-2.0.so.0.6.3)
==1472==    by 0x4031DE: DisplayText (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)
==1472==    by 0x402AA1: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)
==1472==
==1472== LEAK SUMMARY:
==1472==    definitely lost: 31,115 bytes in 4 blocks.
==1472==    indirectly lost: 146,500 bytes in 17 blocks.
==1472==      possibly lost: 0 bytes in 0 blocks.
==1472==    still reachable: 2,443,226 bytes in 2,426 blocks.
==1472==         suppressed: 0 bytes in 0 blocks.
==1472== Reachable blocks (those to which a pointer was found) are not shown.
==1472== To see them, rerun with: --leak-check=full --show-reachable=yes

```
They all seem to have to do with SDL itself. Now another interesting errors that pops up is when I display some text on the screen (to say who won of course), this is what it gives me:
```

==1472== Invalid write of size 1                                                                                                            
==1472==    at 0x4C24574: memcpy (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x402A78: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==  Address 0x6579e73 is 4 bytes after a block of size 7 alloc'd                                                                      
==1472==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x40189C: setPlayerName (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                     
==1472==    by 0x40290D: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==                                                                                                                                    
==1472== Invalid write of size 1                                                                                                            
==1472==    at 0x4C2457D: memcpy (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x402A78: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==  Address 0x6579e72 is 3 bytes after a block of size 7 alloc'd                                                                      
==1472==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x40189C: setPlayerName (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                     
==1472==    by 0x40290D: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==                                                                                                                                    
==1472== Invalid write of size 1                                                                                                            
==1472==    at 0x4C24587: memcpy (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x402A78: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==  Address 0x6579e71 is 2 bytes after a block of size 7 alloc'd                                                                      
==1472==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x40189C: setPlayerName (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                     
==1472==    by 0x40290D: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==                                                                                                                                    
==1472== Invalid write of size 1                                                                                                            
==1472==    at 0x4C24591: memcpy (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x402A78: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==  Address 0x6579e70 is 1 bytes after a block of size 7 alloc'd                                                                      
==1472==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x40189C: setPlayerName (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                     
==1472==    by 0x40290D: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==                                                                                                                                    
==1472== Invalid write of size 1                                                                                                            
==1472==    at 0x4C245D4: memcpy (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x402A78: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==  Address 0x6579e6f is 0 bytes after a block of size 7 alloc'd                                                                      
==1472==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x40189C: setPlayerName (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                     
==1472==    by 0x40290D: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==                                                                                                                                    
==1472== Invalid read of size 1                                                                                                             
==1472==    at 0x4C240A4: strlen (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x4047AF8: TTF_RenderText_Blended (in /usr/lib/libSDL_ttf-2.0.so.0.6.3)                                                      
==1472==    by 0x4031DE: DisplayText (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                       
==1472==    by 0x402AA1: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==  Address 0x6579e6f is 0 bytes after a block of size 7 alloc'd                                                                      
==1472==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x40189C: setPlayerName (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                     
==1472==    by 0x40290D: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==                                                                                                                                    
==1472== Invalid read of size 1                                                                                                             
==1472==    at 0x40457C0: LATIN1_to_UNICODE (in /usr/lib/libSDL_ttf-2.0.so.0.6.3)                                                           
==1472==    by 0x4047B26: TTF_RenderText_Blended (in /usr/lib/libSDL_ttf-2.0.so.0.6.3)                                                      
==1472==    by 0x4031DE: DisplayText (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                       
==1472==    by 0x402AA1: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==  Address 0x6579e6f is 0 bytes after a block of size 7 alloc'd                                                                      
==1472==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x40189C: setPlayerName (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                     
==1472==    by 0x40290D: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==                                                                                                                                    
==1472== Invalid read of size 1                                                                                                             
==1472==    at 0x40457D3: LATIN1_to_UNICODE (in /usr/lib/libSDL_ttf-2.0.so.0.6.3)                                                           
==1472==    by 0x4047B26: TTF_RenderText_Blended (in /usr/lib/libSDL_ttf-2.0.so.0.6.3)                                                      
==1472==    by 0x4031DE: DisplayText (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                       
==1472==    by 0x402AA1: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                              
==1472==  Address 0x6579e70 is 1 bytes after a block of size 7 alloc'd                                                                      
==1472==    at 0x4C2391E: malloc (in /usr/lib/valgrind/amd64-linux/vgpreload_memcheck.so)                                                   
==1472==    by 0x40189C: setPlayerName (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)                                                     
==1472==    by 0x40290D: main (in /home/oor/Code/C/Tic-Tac-Toe/TicTacToe)

```
I do not quite get what this all means. Here is my main function:
```

int main(void)
{
    .....
    /* Setting up SDL, etc here. */
    .....
    
    while (SDL_WaitEvent(&event) >= 0)
    {
        switch (event.type)
        {
            case SDL_MOUSEBUTTONDOWN:
                if (SDL_GetMouseState(&mouseX, &mouseY) & SDL_BUTTON(1))
                {
                    cellPoint = GetClickedCell(mouseX, mouseY);
                    if ( !(isPointNull(cellPoint)) )
                    {
                        if (SetCell(cellPoint, user.symbol, screen) < 0)
                        {
                            PDEBUG("[GUI.c][Func main]: SetCell returned an error, exiting%s\n", "...");
                            exit(1);
                        }
                        SDL_UpdateRect(screen, 0, 0, 0, 0);
                        if (hasWon(user.symbol))
                        {
                            SDL_Rect textLocation;
                            textLocation.x = 200;
                            textLocation.y = 200;
                            SDL_Color textColor;
                            textColor.r = 255;  /* Will create a red color. */
                            textColor.g = 0;
                            textColor.b = 0;
                            DisplayText(screen, "/usr/share/fonts/TTF/DejaVuSans.ttf", 70, strcat(user.name, " won!"), textColor, textLocation);
                            SDL_UpdateRect(screen, 0, 0, 0, 0);
                            SDL_Delay(6000);
                            displayBoard();
                            free(user.name);
                            free(secondPlayer.name);
                            exit(0);
                        }
                        
                        if (isBoardFull() == 1)
                        {
                            printf("Draw!\n");
                            SDL_Delay(6000);
                            exit(0);
                        }
                        
                        aiPoint = aiTurn(secondPlayer.symbol, cellPoint, 0);
                        if (SetCell(aiPoint, secondPlayer.symbol, screen) < 0)
                        {
                            PDEBUG("[GUI.c][Func main]: SetCell returned an error, exiting%s\n", "...");
                            exit(1);
                        }
                        SDL_UpdateRect(screen, 0, 0, 0, 0);
                        if (hasWon(secondPlayer.symbol))
                        {
                            SDL_Rect textLocation;
                            textLocation.x = 200;
                            textLocation.y = 200;
                            SDL_Color textColor;
                            textColor.r = 255;  /* Will create a red color. */
                            textColor.g = 0;
                            textColor.b = 0;
                            DisplayText(screen, "/usr/share/fonts/TTF/DejaVuSans.ttf", 70, strcat(secondPlayer.name, " won!"), textColor, textLocation);
                            SDL_UpdateRect(screen, 0, 0, 0, 0);
                            SDL_Delay(6000);
                            displayBoard();
                            free(user.name);
                            free(secondPlayer.name);
                            exit(0);
                        }
                        
                        if (isBoardFull() == 1)
                        {
                            printf("Draw!\n");
                            SDL_Delay(6000);
                            exit(0);
                        }
                    }
                }
                break;
            case SDL_QUIT:
                SDL_FreeSurface(screen);
                SDL_FreeSurface(board);
                TTF_Quit();
                SDL_Quit();
                free(user.name);
                free(secondPlayer.name);
                exit(1);
        }
    }
    free (user.name);
    free (secondPlayer.name);
    SDL_Quit();
    return 0;
}

```

And my setPlayerName function which is apparently involved with the last set of Valgrind errors.
```

int setPlayerName(Player *player, char name[])
{
    player->name = (char *) malloc(strlen(name)+1);
    if (player->name == NULL)
    {
        return -1;
    }
    strcpy(player->name, name);
    return 1;
}

```


Any help or explanations is much appreciated. (P.S. Forgive me for any grammar mistakes in this post, it's 12:30 am and I am very tired)

---

### Post by dwhitney67 on 2009-03-22
It would be helpful if you would eliminate the exit() calls that you have throughout your code, and instead have the application conclude at a single point (say, at the end of main()).

For instance, here's a section of code where there is no cleanup of the allocated memory:
```

...
if (isBoardFull() == 1)
{
  printf("Draw!\n");
  SDL_Delay(6000);
  exit(0);
}
...

```

---

### Post by OutOfReach on 2009-03-22
Ok, I've made it so whenever there is an error or when it wants to exit normally it breaks the main loop and executes the cleanup code at the end of main(), instead of using exit(). The cleanup code looks like:
```

    SDL_FreeSurface(screen);
    SDL_FreeSurface(board);
    TTF_Quit();
    SDL_Quit();
    free(user.name);
    free(secondPlayer.name);

```

But there continues to be errors in Valgrind. The errors that concern me are the second set of errors (shown in first post) which seems to involve the fonts.

---

### Post by dwhitney67 on 2009-03-22
Please post your code in it entirety.  I cannot deduce where you have a memory leak if I cannot run the app, much less see your initial declarations/setup in the main() function.

It is also possible that certain SDL functions are allocating memory, and the only way to properly free that memory is to call the appropriate SDL function that complements the action.

---

### Post by tneva82 on 2009-03-22
When I asked on another forum about similar issues with SDL/openGL(even most simple ones which barely do anything but set things up and quit) the reply was that the diagnosis tool isn't able to monitor memory allocations/deallocations(possibly because they happen in external library?). Not sure if this is correct but since there's nothing I could do to get rid of those I figured I'll just leave them. If they DO leak I have no interest in starting debugging SDL/openGL/font libraries I use thank you very much!

---

### Post by OutOfReach on 2009-03-22
Ok I will attach the files, just a heads up, I created a library to handle the background actions and I created 2 interfaces, one being command line and the other being SDL. I've tested the command line interface with Valgrind and found no leaks/errors, so I am guessing that the problem lies within the SDL interface (GUI.c)

Just run 'make' and you're all set. To use the command line interface just replace 'GUI.c' and 'GUI.o' in the Makefile with 'CLI.c' and 'CLI.o'

---

### Post by dwhitney67 on 2009-03-22
> **tneva82 said:**
> When I asked on another forum about similar issues with SDL/openGL(even most simple ones which barely do anything but set things up and quit) the reply was that the diagnosis tool isn't able to monitor memory allocations/deallocations(possibly because they happen in external library?). Not sure if this is correct but since there's nothing I could do to get rid of those I figured I'll just leave them. If they DO leak I have no interest in starting debugging SDL/openGL/font libraries I use thank you very much!

+1

I just tested a small app (very small!) with valgrind, and indeed SDL has memory leaks.

Here's my app:
```

#include <SDL/SDL.h>

int main()
{
  SDL_Init(SDL_INIT_VIDEO);
  SDL_Quit();
  return 0;
}

```
Built and tested with:
```

gcc SmallApp.c -lSDL
valgrind -v a.out

```

---

### Post by OutOfReach on 2009-03-22
Hmm so it is possibly not me, but instead SDL?

---

### Post by dwhitney67 on 2009-03-22
> **OutOfReach said:**
> Hmm so it is possibly not me, but instead SDL?

Well, I have proven that SDL does have leaks.  Whether you are adding to the "misery" is still undetermined.

I would not worry about the SDL leaks, and if your portion of the application should have any, just ensure that if you are allocating in a loop, that the proper cleanup for this memory is being done.  The memory allocations in a loop are the ones that can bite back if they are not properly cleaned up as the application progresses through its run.

---

### Post by OutOfReach on 2009-03-22
The only thing that I allocate in my program is the player's names (2 players) and of course I only use them in debug statements and at the end when it shows "%s won", %s being the name. Then I make sure I free both names at the end of main.

Anyways, I'll ignore SDL's 'leaks' as long as they seem harmless.

---

