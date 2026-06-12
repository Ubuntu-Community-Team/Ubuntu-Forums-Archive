---
title: "SDL_mixer issue sound effect not playing"
date: 2009-06-08
forum: Programming Talk
---

### Post by shadylookin on 2009-06-08
I wrote this small program to try and play a sound effect. Everything appears to go smoothly(no errors supposedly) but there is no sound. When I used the Mix_PlayMusic function on the same file it played just fine. 

The code in question 
[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <SDL/SDL_events.h>
#include <SDL/SDL.h>
#include <SDL/SDL_mixer.h>


int main(int argc, char** argv) {

    SDL_Surface *screen;
    SDL_Event event;
    Mix_Chunk *test;

    //init everything
    if(SDL_Init(SDL_INIT_EVERYTHING) != 0){
        fprintf(stderr, "error initiazling sdl\n");
    }
    atexit(SDL_Quit);
    
    //create screen at 640 by 480
    screen = SDL_SetVideoMode(640,480,16,SDL_ANYFORMAT);

    //if there is an error making the screen notify the user
    if(screen == NULL){
        fprintf(stderr, "there was an error creating the screen %s",
                SDL_GetError());
    }

    //initialize the mixer
    if(Mix_OpenAudio(22050, MIX_DEFAULT_FORMAT, 2, 4096)){
        fprintf(stderr, "error opening audio\n");
    }

    
    
    test = Mix_LoadWAV("/home/shadylookin/tap.ogg");

    if(test == NULL){
        fprintf(stderr, "unable to load file %s\n", Mix_GetError());
    }

    
    if((Mix_PlayChannel(-1, test, 0)) == -1){
        fprintf(stderr, "unable to play sound effect %s", Mix_GetError());
    }
     

       
    for(;;){
        if(SDL_PollEvent(&event) != 0){
            if(event.type == SDL_QUIT){
                break;
            }
        }
    }

    
    Mix_FreeChunk(test);

    return 0;

}
[/PHP]

Admittedly I'm not really very knowledgeable about computer sound. I tried all of my green audio out ports and none of them make the sound effect play. Supposedly setting the sound channel in Mix_PlayChannel to -1 will search for any plugged in device and play out over it. So any ideas?

---

