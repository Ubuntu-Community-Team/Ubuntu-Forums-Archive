---
title: "c++ sdl error"
date: 2013-04-04
forum: Programming Talk
---

### Post by virtapoika on 2013-04-04
[COLOR=#000000]Hi guys! I'm having problems with sdl-library and its keyboard event. The main idea of the program is: save char in to char array and meanwhile listen if ctrl+alt+character, then save char array to .txt file called "character (pressed one)" Or ctrl+character is pressed and read "pressed character named txt file". At the end of program loop everything is going to be saved in .txt file. [/COLOR]

[COLOR=#000000]Sorry about my variable names and my bad English, it is not my native languague =D[/COLOR]

[COLOR=#000000]My code:[/COLOR]
[COLOR=#000000]#include <unistd.h>[/COLOR]
[COLOR=#000000]#include <sstream>[/COLOR]
[COLOR=#000000]#include <stdio.h>[/COLOR]
[COLOR=#000000]#include <stdlib.h>[/COLOR]
[COLOR=#000000]#include <iostream>[/COLOR]
[COLOR=#000000]#include "/usr/include/SDL/SDL_keyboard.h"[/COLOR]
[COLOR=#000000]#include "/usr/include/SDL/SDL.h"[/COLOR]
[COLOR=#000000]#include <iostream>[/COLOR]
[COLOR=#000000]#include <ncurses.h>[/COLOR]

[COLOR=#000000]using namespace std;[/COLOR]
[COLOR=#000000]void inputoutput(SDL_KeyboardEvent *key, SDLMod mod, char mikakirjain,char teksti,char lopullinen,char luettelo,FILE * tiedosto);[/COLOR]


[COLOR=#000000]int main( int argc, char* args[]) {[/COLOR]
[COLOR=#000000]SDL_Event event;[/COLOR]

[COLOR=#000000]char mikakirjain;[/COLOR]
[COLOR=#000000]int nro = 1 ;[/COLOR]
[COLOR=#000000]char teksti[256];[/COLOR]
[COLOR=#000000]char lopullinen[256];[/COLOR]
[COLOR=#000000]char luettelo;[/COLOR]
[COLOR=#000000]string kirj; [/COLOR]
[COLOR=#000000]string stringi;[/COLOR]
[COLOR=#000000]FILE * tiedosto;[/COLOR]




[COLOR=#000000]initscr();[/COLOR]
[COLOR=#000000]raw();[/COLOR]


[COLOR=#000000]if ( SDL_Init(SDL_INIT_VIDEO) < 0) {[/COLOR]
[COLOR=#000000]fprintf( stderr, "\"[/COLOR][COLOR=#417394]SDL[/COLOR][COLOR=#000000] initializion\" mokasi: %s \n", SDL_GetError() );[/COLOR]
[COLOR=#000000]exit( -1);[/COLOR]
[COLOR=#000000]}[/COLOR]


[COLOR=#000000]if( !SDL_SetVideoMode(320, 200, 0, 0 ) ) {[/COLOR]
[COLOR=#000000]fprintf(stderr, "Video moodia ei saatu suoritettua: %s \n", SDL_GetError());[/COLOR]
[COLOR=#000000]SDL_Quit();[/COLOR]
[COLOR=#000000]exit( -1 );[/COLOR]


[COLOR=#000000]}[/COLOR]



[COLOR=#000000]SDL_EnableUNICODE( 1 );[/COLOR]


[COLOR=#000000]while(nro == 1) {[/COLOR]



[COLOR=#000000]while( SDL_PollEvent ( &event ) ) {[/COLOR]
[COLOR=#000000]kirj = getch();[/COLOR]
[COLOR=#000000]stringi = teksti + kirj;[/COLOR]



[COLOR=#000000]if( event.type ) {[/COLOR]

[COLOR=#000000]if (SDL_KEYDOWN) {[/COLOR]
[COLOR=#000000]inputoutput(&event.key, char mikakirjain,char teksti,char lopullinen,char luettelo,FILE * tiedosto);[/COLOR]

[COLOR=#000000]}[/COLOR]





[COLOR=#000000]}[/COLOR]
[COLOR=#000000]endwin();[/COLOR]

[COLOR=#000000]}[/COLOR]




[COLOR=#000000]} [/COLOR]

[COLOR=#000000]}[/COLOR]
[COLOR=#000000]void inputoutput(SDL_KeyboardEvent *key, SDLMod mod,mikakirjain, teksti, lopullinen, luettelo,FILE * tiedosto) {[/COLOR]
[COLOR=#000000]if(event.key.keysym.sym) {[/COLOR]
[COLOR=#000000]luettelo = "%s", SDL_GetKeyName(key->keysym.sym ); [/COLOR]
[COLOR=#000000]if(SDLK_LCTRL, SDLK_"%c", luettelo) {[/COLOR]

[COLOR=#000000]tiedosto = fopen("%c",mikakirjain,"w+");[/COLOR]
[COLOR=#000000]teksti = fread("%c.txt",mikakirjain);[/COLOR]
[COLOR=#000000]sprintf(lopullinen,"espeak -v fi \"%s\"", teksti);[/COLOR]
[COLOR=#000000]system(lopullinen);[/COLOR]
[COLOR=#000000]teksti = "";[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]else if(SDLK_LCTRL, SDLK_LALT, SDLK_"%c",luettelo) {[/COLOR]

[COLOR=#000000]tiedosto = fopen("%c",mikakirjain,"r");[/COLOR]
[COLOR=#000000]fwrite(teksti);[/COLOR]
[COLOR=#000000]teksti = "";[/COLOR]

[COLOR=#000000]}[/COLOR]

[COLOR=#000000]}[/COLOR]
[COLOR=#000000]return teksti;[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]}[/COLOR]

[COLOR=#000000]compiling code gcc -lSDl programsname programsname.cpp[/COLOR]
[COLOR=#000000]result:[/COLOR]
[COLOR=#000000]70:26: error: expected primary-expression before âcharâ70:43: error: expected primary-expression before âcharâ[/COLOR]
[COLOR=#000000]70:55: error: expected primary-expression before âcharâ[/COLOR]
[COLOR=#000000]70:71: error: expected primary-expression before âcharâ[/COLOR]
[COLOR=#000000]70:90: error: expected primary-expression before â*â token[/COLOR]
[COLOR=#000000]At global scope:[/COLOR]
[COLOR=#000000]error: âmikakirjainâ has not been declared[/COLOR]
[COLOR=#000000]error: âtekstiâ has not been declared[/COLOR]
[COLOR=#000000]89:74: error: âlopullinenâ has not been declared[/COLOR]
[COLOR=#000000]89:86: error: âluetteloâ has not been declared[/COLOR]
[COLOR=#000000]In function âvoid inputoutput(SDL_KeyboardEvent*, SDLMod, int, int, int, int, FILE*)â:[/COLOR]
[COLOR=#000000]90:4: error: âeventâ was not declared in this scope[/COLOR]
[COLOR=#000000]91:3: error: âluetteloâ was not declared in this scope[/COLOR]
[COLOR=#000000]92:19: error: âSDLK_â was not declared in this scope[/COLOR]
[COLOR=#000000]92:24: error: expected â)â before string constant[/COLOR]
[COLOR=#000000]94:27: error: âmikakirjainâ was not declared in this scope[/COLOR]
[COLOR=#000000]95:5: error: âtekstiâ was not declared in this scope[/COLOR]
[COLOR=#000000]96:13: error: âlopullinenâ was not declared in this scope[/COLOR]
[COLOR=#000000]100:40: error: expected â)â before string constant[/COLOR]
[COLOR=#000000]102:27: error: âmikakirjainâ was not declared in this scope[/COLOR]
[COLOR=#000000]103:12: error: âtekstiâ was not declared in this scope[/COLOR]
[COLOR=#000000]109:8: error: âtekstiâ was not declared in this scope[/COLOR]
[COLOR=#000000]109:8: error: return-statement with a value, in function returning 'void' [-fpermissive][/COLOR]
[COLOR=#000000]At global scope:[/COLOR]
[COLOR=#000000]111:1: error: expected declaration before â}â token[/COLOR]

---

### Post by r-senior on 2013-04-04
```
if (SDL_KEYDOWN) {
inputoutput(&event.key, [COLOR="#FF0000"]char[/COLOR] mikakirjain,[COLOR="#FF0000"]char[/COLOR] teksti,[COLOR="#FF0000"]char[/COLOR] lopullinen,[COLOR="#FF0000"]char[/COLOR] luettelo,[COLOR="#FF0000"]FILE *[/COLOR] tiedosto);

}
```
This is a function call, not a declaration. I think you have accidentally put the datatypes here instead of on the function itself:

```
void inputoutput(SDL_KeyboardEvent *key, SDLMod mod,[COLOR="#FF0000"]mikakirjain, teksti, lopullinen, luettelo[/COLOR],FILE * tiedosto) {
...
```

The parameters in the function call don't match those declared in the declaration.

This function is also returning a value when it is declared to return void:

```
return teksti;
```

Please use [code ]...[/code] tags or the '#' button in the posting toolbar for code. It makes it easier to read.

---

### Post by mörgæs on 2013-04-05
Please don't double-post.
I have deleted the other one.

---

### Post by virtapoika on 2013-04-05
Sorry, I'm newbie here =P

---

