---
title: "SDL c++ problem"
date: 2013-04-04
forum: Packaging and Compiling Programs
---

### Post by virtapoika on 2013-04-04
Hi guys! I'm having problems with sdl-library and its keyboard event. The main idea of the program is: save char in to char array and meanwhile listen if ctrl+alt+character, then save char array to .txt file called "character (pressed one)" Or ctrl+character is pressed and read "pressed character named txt file". At the end of program loop everything is going to be saved in .txt file. 

Sorry about my variable names and my bad English, it is not my native languague =D

My code:
#include <unistd.h>
#include <sstream>
#include <stdio.h>
#include <stdlib.h>
#include <iostream>
#include "/usr/include/SDL/SDL_keyboard.h"
#include "/usr/include/SDL/SDL.h"
#include <iostream>
#include <ncurses.h>

using namespace std;
void inputoutput(SDL_KeyboardEvent *key, SDLMod mod, char mikakirjain,char teksti,char lopullinen,char luettelo,FILE * tiedosto);


int main( int argc, char* args[]) {
SDL_Event event;

char mikakirjain;
int nro = 1 ;
char teksti[256];
char lopullinen[256];
char luettelo;
string kirj; 
string stringi;
FILE * tiedosto;




initscr();
raw();


if ( SDL_Init(SDL_INIT_VIDEO) < 0) {
fprintf( stderr, "\"SDL initializion\" mokasi: %s \n", SDL_GetError() );
exit( -1);
}


if( !SDL_SetVideoMode(320, 200, 0, 0 ) ) {
fprintf(stderr, "Video moodia ei saatu suoritettua: %s \n", SDL_GetError());
SDL_Quit();
exit( -1 );


}



SDL_EnableUNICODE( 1 );


while(nro == 1) {



    while( SDL_PollEvent ( &event ) ) {
    kirj = getch();
    stringi = teksti + kirj;
    


if( event.type ) {
  
    if (SDL_KEYDOWN) {
    inputoutput(&event.key, char mikakirjain,char teksti,char lopullinen,char luettelo,FILE * tiedosto);
  
    }
    


  

    }
endwin();

}

    


    }    

}
void inputoutput(SDL_KeyboardEvent *key, SDLMod mod,mikakirjain, teksti, lopullinen, luettelo,FILE * tiedosto) {
if(event.key.keysym.sym) {
  luettelo = "%s", SDL_GetKeyName(key->keysym.sym ); 
   if(SDLK_LCTRL, SDLK_"%c", luettelo) {
    
    tiedosto = fopen("%c",mikakirjain,"w+");
    teksti = fread("%c.txt",mikakirjain);
    sprintf(lopullinen,"espeak -v fi \"%s\"", teksti);
    system(lopullinen);
    teksti = "";
   }
   else if(SDLK_LCTRL, SDLK_LALT, SDLK_"%c",luettelo) {
    
    tiedosto = fopen("%c",mikakirjain,"r");
    fwrite(teksti);
    teksti = "";
    
}

}
return teksti;
}
}
 
compiling code gcc -lSDl programsname programsname.cpp
result:
70:26: error: expected primary-expression before âcharâ70:43: error: expected primary-expression before âcharâ
70:55: error: expected primary-expression before âcharâ
70:71: error: expected primary-expression before âcharâ
70:90: error: expected primary-expression before â*â token
 At global scope:
error: âmikakirjainâ has not been declared
error: âtekstiâ has not been declared
89:74: error: âlopullinenâ has not been declared
89:86: error: âluetteloâ has not been declared
 In function âvoid inputoutput(SDL_KeyboardEvent*, SDLMod, int, int, int, int, FILE*)â:
90:4: error: âeventâ was not declared in this scope
91:3: error: âluetteloâ was not declared in this scope
92:19: error: âSDLK_â was not declared in this scope
92:24: error: expected â)â before string constant
94:27: error: âmikakirjainâ was not declared in this scope
95:5: error: âtekstiâ was not declared in this scope
96:13: error: âlopullinenâ was not declared in this scope
100:40: error: expected â)â before string constant
102:27: error: âmikakirjainâ was not declared in this scope
103:12: error: âtekstiâ was not declared in this scope
109:8: error: âtekstiâ was not declared in this scope
109:8: error: return-statement with a value, in function returning 'void' [-fpermissive]
 At global scope:
111:1: error: expected declaration before â}â token

---

