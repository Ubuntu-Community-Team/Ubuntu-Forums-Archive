---
title: "C program- Simple key input help"
date: 2010-11-28
forum: Programming Talk
---

### Post by maedez on 2010-11-28
I know what the program does but I don't know why it does it like that. Does someone understand and can explain the code?

I want to modify this to actually do something after entering your desired choice. like a simple printf statement per choice.

```
#include <stdio.h> 
#include <ncurses.h> 
 
#define WIDTH 30 
#define HEIGHT 10  
 
int startx = 0; 
int starty = 0; 
 
char *choices[] = {
            "Choice 1", 
            "Choice 2", 
            "Choice 3", 
            "Choice 4", 
            "Exit", 
          }; 
int n_choices = sizeof(choices) / sizeof(char *); 
void print_menu(WINDOW *menu_win, int highlight); 
 
int main() 
{    WINDOW *menu_win; 
    int highlight = 1; 
    int choice = 0; 
    int c; 
 
    initscr(); 
    clear(); 
    noecho(); 
    cbreak();    /* Line buffering disabled. pass on everything */ 
    startx = (80 - WIDTH) / 2; 
    starty = (24 - HEIGHT) / 2; 
         
    menu_win = newwin(HEIGHT, WIDTH, starty, startx); 
    keypad(menu_win, TRUE); 
    mvprintw(0, 0, "Use arrow keys to go up and down, Press enter to select a choice"); 
    refresh(); 
    print_menu(menu_win, highlight); 
    while(1) 
    {    c = wgetch(menu_win); 
        switch(c) 
        {    case KEY_UP: 
                if(highlight == 1) 
                    highlight = n_choices; 
                else 
                    --highlight; 
                break; 
            case KEY_DOWN: 
                if(highlight == n_choices) 
                    highlight = 1; 
                else  
                    ++highlight; 
                break; 
            case 10: 
                choice = highlight; 
                break; 
            default: 
                mvprintw(24, 0, "Charcter pressed is = %3d Hopefully it can be printed as '%c'", c, c); 
                refresh(); 
                break; 
        } 
        print_menu(menu_win, highlight); 
        if(choice != 0)    /* User did a choice come out of the infinite loop */ 
            break; 
    }     
    mvprintw(23, 0, "You chose choice %d with choice string %s\n", choice, choices[choice - 1]); 
    clrtoeol(); 
    refresh(); 
    endwin(); 
    return 0; 
} 
 
 
void print_menu(WINDOW *menu_win, int highlight) 
{ 
    int x, y, i;     
 
    x = 2; 
    y = 2; 
    box(menu_win, 0, 0); 
    for(i = 0; i < n_choices; ++i) 
    {    if(highlight == i + 1) /* High light the present choice */ 
        {    wattron(menu_win, A_REVERSE);  
            mvwprintw(menu_win, y, x, "%s", choices[i]); 
            wattroff(menu_win, A_REVERSE); 
        } 
        else 
            mvwprintw(menu_win, y, x, "%s", choices[i]); 
        ++y; 
    } 
    wrefresh(menu_win); 
} 

```

---

### Post by GregBrannon on 2010-11-28
This sounds like you've found a partial or possible answer to a homework problem, but you don't understand it well enough to modify it to do what you really need.  You won't find that kind of help here.

If the circumstances are different than I've suggested, please explain.

---

