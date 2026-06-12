---
title: "getmouseclick() in C++ (please help me)"
date: 2010-07-09
forum: Programming Talk
---

### Post by bahador.saket on 2010-07-09
Dear All

I faced with specific problem in my program.
I want to use mouse and setcursor with together in my program.
for example: when I click on search bottom my cursor should go to x=30,y=20 and i will input a string in this location by keyboard.

unfortunately, when I am using the  setcursor() function before using the getmouse() function I can get  input from keyboard but when I call it  after calling  getmouse()  function I can not get input from keyboard.

my editor is codeblock.

please attend to my code and if it is possible modify my program.

```



#include<iostream>
#include <windows.h>
#include<conio.h>
using  namespace std;
enum MyColor
{
    BLACK1,
    DARKBLUE1,
     DARKGREEN1,
    TEAL1,
    MAROON1,
    PURPLE1,
     OLIVE1,
    LIGHTGRAY1,
    DARKGRAY1,
    BLUE1,
     GREEN1,
    CYAN1,
    RED1,
    PINK1,
    YELLOW1,
     WHITE1
};
static MyColor foreground = WHITE1;
static MyColor  background = BLACK1;
static HANDLE hOut =  GetStdHandle(STD_OUTPUT_HANDLE);
static COORD largestWindow =  GetLargestConsoleWindowSize(hOut);

// setCursorXY() will change  the situation of the curser
void setBackgroundColor(const  MyColor& color)
{
    background = color;
     SetConsoleTextAttribute(hOut, foreground + (background << 4) );
}
/****************************************************************************/
/*
 *  Set current foreground color
 *
 * @color: color for foreground  (16 choices from INTERFACE.H)
 */
void setForegroundColor(const  MyColor& color)
{
    foreground = color;
     SetConsoleTextAttribute(hOut, foreground + (background << 4) );
}
void  setCursorXY( int x, int y )
{
    COORD coord;
    coord.X =  static_cast<SHORT>(x);
    coord.Y =  static_cast<SHORT>(y);
    SetConsoleCursorPosition
     (GetStdHandle(STD_OUTPUT_HANDLE),coord);
}
struct MouseClick
{
     enum Button
    {
        Left   = FROM_LEFT_1ST_BUTTON_PRESSED,
         Middle = FROM_LEFT_2ND_BUTTON_PRESSED,
        Right  =  RIGHTMOST_BUTTON_PRESSED
    };
    int    x;
    int    y;
     Button button;
};
//=============================================================  class Console{};
class Console
{
private:
    int height;
     int width;
public:

    bool has( int x, int y )const
    {
         return(0 <= x)&&(x <= 8)&&(0 <= y)&&(y  <= 10);
    }

    bool setCursorPosition( int x, int y )
     {
     // If (x,y) is inside the console screen
         if((0<=x)&&(x<width )
          &&(0<=y)&&(y<height))
        {
             COORD coord;
            coord.X = static_cast<SHORT>(x);
             coord.Y = static_cast<SHORT>(y);
            if(  !SetConsoleCursorPosition
                  (GetStdHandle(STD_OUTPUT_HANDLE),coord) )
            {
                 // To get extended error information, call GetLastError
             cerr <<"-------------\n"
                     <<"System  Error:\n"
                     <<"-------------\n"
                      <<"SetConsoleCursorPosition"
                      <<"(GetStdHandle(STD_OUTPUT_HANDLE),coord) failed\n";

                 exit(EXIT_FAILURE);
            }
            return true;
         }
        else
        {
            // (x,y) is NOT inside  the console screen
            return false;
        }
    }
     MouseClick getMouseClick()
    {
        // Prepare console for  mouse input
        HANDLE stdIn =  GetStdHandle(STD_INPUT_HANDLE);

         if(    stdIn == INVALID_HANDLE_VALUE )
        {
            //  To get extended error information, call GetLastError

             cerr <<"-------------\n"
                 <<"System  Error:\n"
                 <<"-------------\n"
                  <<"GetStdHandle(STD_INPUT_HANDLE) failed\n";

             exit(EXIT_FAILURE);
        }
        if(  !SetConsoleMode(stdIn,ENABLE_MOUSE_INPUT) )
        {
             // To get extended error information, call GetLastError

             cerr <<"-------------\n"
                 <<"System  Error:\n"
                 <<"-------------\n"
                  <<"SetConsoleMode(stdIn,ENABLE_MOUSE_INPUT) failed\n";
             exit(EXIT_FAILURE);
        }

        // Listen for  mouse-click
        MouseClick mouseClick;
        bool   doLoop =  true;
        while( doLoop )
        {
            // Get  upto 100 queueing console-inputs
            static           INPUT_RECORD input[100];  DWORD   totalInput=0;

            if(  !ReadConsoleInput( stdIn,input,sizeof(input),&totalInput) )
             {
                // To get extended error information, call  GetLastError

                cerr <<"-------------\n"
                      <<"System Error:\n"
                      <<"-------------\n"
                      <<"ReadConsoleInput() failed\n";

                 exit(EXIT_FAILURE);
            }

            // Process the  queued console-inputs
            for( DWORD i=0; i<totalInput;  ++i )
            {
                if( input[i].EventType ==  MOUSE_EVENT )
                {
                     MOUSE_EVENT_RECORD& event = input[i].Event.MouseEvent;
                     if( event.dwEventFlags == 0 )
                    {
                         switch( event.dwButtonState )
                        {
                             case MouseClick::Left  :
                            case  MouseClick::Middle:
                            case  MouseClick::Right :
                            {
                                 // Process the mouse-click event
                                 doLoop       = false;
                                mouseClick.x =  event.dwMousePosition.X;
                                mouseClick.y  = event.dwMousePosition.Y;
                                 mouseClick.button
                                 =  static_cast<MouseClick::Button>
                                               (event.dwButtonState);
                            }
                             break;
                        }
                    }
                 }
            }
        }
        return mouseClick;
    }
};

int  main()
{
    string s;
    Console object;
     object.getMouseClick();
    setCursorXY(43,30);
     setBackgroundColor(BLUE1);
    setForegroundColor(WHITE1);
     cin>>s;
    getch();
}


```Regards,
Bahador Saket

---

### Post by Some Penguin on 2010-07-09
Why do you persist in posting Windows API-specific questions on a Linux programming forum?

---

### Post by nvteighen on 2010-07-10
This sort of stuff is done in GNU/Linux using ncurses. ncurses is a C library, but has C++ bindings (now I can't recall the name of it)... you could, of course, the C library, but your code will look a bit uglier.

---

