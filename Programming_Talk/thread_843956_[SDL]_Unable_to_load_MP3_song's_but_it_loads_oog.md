---
title: "[SDL] Unable to load MP3 song's but it loads oog"
date: 2008-06-28
forum: Programming Talk
---

### Post by rraj.be on 2008-06-28
This is the code

```
#include "stdlib.h"
#include "SDL/SDL.h"
#include "SDL/SDL_mixer.h"

//Function prototyping action!
void musicFinished();

int musicPlaying = 0;				//Is the music playing, or not?

int main(int argc, char *argv[])
{
	SDL_Surface *screen;			//Pointer to the main screen surface
	Mix_Music *music;			//Pointer to our music, in memory
	  
	int audio_rate = 22050;			//Frequency of audio playback
	Uint16 audio_format = AUDIO_S16SYS; 	//Format of the audio we're playing
	int audio_channels = 2;			//2 channels = stereo
	int audio_buffers = 4096;		//Size of the audio buffers in memory
	
	//Initialize BOTH SDL video and SDL audio
	if (SDL_Init(SDL_INIT_VIDEO | SDL_INIT_AUDIO) != 0) 
	{
		printf("Unable to initialize SDL: %s\n", SDL_GetError());
		return 1;
	}
	
	//Initialize SDL_mixer with our chosen audio settings
	if(Mix_OpenAudio(audio_rate, audio_format, audio_channels, audio_buffers) != 0) 
	{
		printf("Unable to initialize audio: %s\n", Mix_GetError());
		return 1;
	}
	
	//Load our OGG file from disk
	music = Mix_LoadMUS("/home/raj/c/music.ogg");
	if(music == NULL) 
	{
		printf("Unable to load OGG file: %s\n", Mix_GetError());
		return 1;
	}
	
	//Set the video mode to anything, just need a window
	screen = SDL_SetVideoMode(320, 240, 0, SDL_ANYFORMAT);
	if (screen == NULL) 
	{
		printf("Unable to set video mode: %s\n", SDL_GetError());
		return 1;
	}
	
	//Play that funky music!
	if(Mix_PlayMusic(music, 0) == -1) 
	{
		printf("Unable to play OGG file: %s\n", Mix_GetError());
		return 1;
	}
	
	//The music is playing!
	musicPlaying = 1;
	
	//Make sure that the musicFinished() function is called when the music stops playing
	Mix_HookMusicFinished(musicFinished);
	
	//Wait for the music to stop
	while(musicPlaying)
	{
		//Do nothing for a bit
		SDL_Delay(100);
	}
	
	//Release the memory allocated to our music
	Mix_HaltMusic();
	Mix_FreeMusic(music);
	
	//Need to make sure that SDL_mixer and SDL have a chance to clean up
	Mix_CloseAudio();
	SDL_Quit();	
	
	//Return success!
	return 0;
}

void musicFinished()
{
	//Music is done!
	musicPlaying = 0;
}
```

It plays ogg files well.

But when i change the load file option as

```

	music = Mix_LoadMUS("/home/raj/c/m.mp3");
```
it is displaying

```
raj@raj-desktop:~$ ./a.out
Unable to load OGG file: Couldn't read from '/home/raj/c/m.mp3'
raj@raj-desktop:~$ 
```


What should i change to playe mp3 files in this code.

---

### Post by rraj.be on 2008-06-28
i can load mp3 files now

But

	```
its just loading the file
	opening the screen
	and in a second the screen is vanished
	what should be the problem?
```

any solution please.

---

### Post by Zugzwang on 2008-06-30
That behaviour might be normal. You might need to redraw the screen from time to time. You might also need to react on events. However, I'm not sure but you should definitely try that. I would suggest that you read an SDL 2D tutorial for details.

---

