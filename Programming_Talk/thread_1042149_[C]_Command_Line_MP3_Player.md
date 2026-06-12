---
title: "[C] Command Line MP3 Player"
date: 2009-01-17
forum: Programming Talk
---

### Post by loganwm on 2009-01-17
I wrote up this small audio player with C to check out the SDL mixer and to experiment with multi threading. If anyone gets a bit of time, can you test it out and give me some input on efficiency and such?

Any help is much appreciated.

Edit: By the way, I haven't implemented many of the "in case of error" scenarios, I wanted to get my algorithms in line first.

Compile with:
gcc -Wall -o audio audio.c -lpthread -lSDL -lSDL_mixer

```
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <string.h>
#include <SDL/SDL.h>
#include <SDL/SDL_mixer.h>

/*	Global Variabls:
	music: current song data is loaded here
*/
Mix_Music *GLOBAL_MUSIC = NULL;

/*	Function Declarations:
	void UnloadSong(void): called upon completion of a song to clear from memory
	void LoadSong(void): called to load a new song into the player
*/
void UnloadSong();
void LoadSong(char*);
void Play(int);
void CloseProgram();
void listentothis(int);

int main(void) {
	int done = 0;

	pthread_t Listener;
	int ListenerThread;

	SDL_Init(SDL_INIT_AUDIO);
	Mix_OpenAudio(22050, AUDIO_S16, 2, 4096);


	while (!done) {
		if (GLOBAL_MUSIC == NULL) {
			ListenerThread = pthread_create(&Listener, NULL,listentothis,0);
			LoadSong("test.mp3");
			Play(0);
			pthread_join(Listener,NULL);
			Mix_HookMusicFinished(UnloadSong);

		}
	}
	/* This is the cleaning up part */
}

void listentothis(int code) {
	char input[256];
	int THREAD_DONE;

	while (!THREAD_DONE) {
		//Recieve input from user forever until thread terminated
		fgets(input,256,stdin);
		
		//Strip the newline character from input\
		//sets index at LENGTH-1 of string to null to get ride of NEWLINE
		input[strlen(input)-1] = 0x00;

		//NewLine character is stripped from input
		//be careful with input comparison
		if (strcasecmp(input,"exit") == 0) {
			exit(0);
		}
		if (strcasecmp(input,"pause") == 0) {
			Mix_PauseMusic();
		}
		if (strcasecmp(input,"resume") == 0) {
			Mix_ResumeMusic();
		}
		if (strcasecmp(input,"rewind") == 0) {
			Mix_RewindMusic();
		}

		if (strcasecmp(input,"change") == 0) {
			//Prompt user for FILENAME of song
			printf("Filename: ");

			//Get input
			fgets(input,256,stdin);
			//Strip NEWLINE character
			input[strlen(input)-1] = 0x00;

			//unload current song if one exists
			UnloadSong();

			//Load our new song
			LoadSong(input);

			//Play our new song
			Play(0);
		}
		SDL_Delay(50);
	}
}

void LoadSong(char* filename) {
	GLOBAL_MUSIC = Mix_LoadMUS(filename);
}

void UnloadSong() {
	Mix_HaltMusic();
	Mix_FreeMusic(GLOBAL_MUSIC);
	GLOBAL_MUSIC = NULL;
}

void Play(int Loops) {
	Mix_PlayMusic(GLOBAL_MUSIC, Loops);
}

void CloseProgram() {
	Mix_CloseAudio();
	SDL_Quit();
	exit(0);
}
```

---

### Post by ibuclaw on 2009-01-17
Pretty impressive.

What I have to mention is that the last function, CloseProgram() is not used in the main loop.

My guess is that the code is supposed to look like this:
```

//NewLine character is stripped from input
		//be careful with input comparison
		if (strcasecmp(input,"exit") == 0) {
**			CloseProgram();**
		}

```

Also, to fix the Warning Errors:
**Line 56**
```
ListenerThread = pthread_create(&Listener, NULL, **(void*)&listentothis**,0);
```
**Line 65**
```

    /* This is the cleaning up part */
    **return 0;**
}

```
Afterall, an int must be returned in an int function. ;)

**Line 73**
```
        //Strip the newline character from input
```
Haha, good job though :)

Regards
Iain

---

### Post by tenach on 2009-01-17
I will have to test this out when I get home!

---

### Post by loganwm on 2009-01-17
I cleaned up my current model and reworked a couple of items.  Thanks for the help on that warning.

BTW: Works for .ogg as well, try other formats.

Usage is pretty simple, it's a real small function set so far, but I'll type up a small usage guide with this post. And the program is mostly documented.

change - change song, it will prompt for filename (I'm not sure if it'll work outside it's current directory yet)
pause - pause song
resume - resume song
rewind - restart song
exit - exit program


I'm going to implement the following as well:
playlists
a simple seek function (fast-forward, rewind)
volume
more intuitive way of pulling up your songs
possibly looking into a lightweight library setup

Any input is appreciated, I'm going for lightweight altogether as opposed to the graphical monstrosity that is iTunes and Windows Media.

Suggestions/Input/Criticism welcome!

```
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <string.h>
#include <SDL/SDL.h>
#include <SDL/SDL_mixer.h>

/*	Global Variabls:
	GLOBAL_MUSIC: current song data is loaded here
*/
Mix_Music *GLOBAL_MUSIC = NULL;

/*	Function Declarations:
	void UnloadSong(void): called upon completion of a song to clear from memory
	void LoadSong(void): called to load a new song into the player
	void PlaySong(int): called to play a song that's looaded into memory, arg is loops! -1 for infinite
	void PauseSong(): called to pause a playing song
*/
void UnloadSong();
void LoadSong(char*);

//these are just abstracted forms of the MIXER functions
void PlaySong(int);
void PauseSong();
void ResumeSong();
void RewindSong();

//close and clean up function
void CloseProgram();

//called by thread to handle input during song
void InputHandler();

int main(void) {
	int done = 0;

	// create our PTHREAD which calls InputHandler
	pthread_t Listener;
	int ListenerThread;

	SDL_Init(SDL_INIT_AUDIO);
	Mix_OpenAudio(22050, AUDIO_S16, 2, 4096);


	while (!done) {
		if (GLOBAL_MUSIC == NULL) {
			//create our thread to get input parallel to playing music
			ListenerThread = pthread_create(&Listener, NULL,(void*)&InputHandler,NULL);
			//is this necessary? my knowledge of threads is weak.
			pthread_join(Listener,NULL);
			//upon finish, dump it.
			Mix_HookMusicFinished(UnloadSong);
		}
	}
	// If we get this far (and we shouldn't) then we should return
	return 0;
}

void InputHandler() {
	//input buffer
	char input[256];
	//store status of thread
	int THREAD_DONE;

	while (!THREAD_DONE) {
		//Recieve input from user forever until thread terminated
		fgets(input,256,stdin);
		//Strip the newline character from input\
		//sets index at LENGTH-1 of string to null to get ride of NEWLINE
		input[strlen(input)-1] = 0x00;
		//NewLine character is stripped from input
		//be careful with input comparison
		if (strcasecmp(input,"exit") == 0) {
			CloseProgram();
		}
		if (strcasecmp(input,"pause") == 0) {
			PauseSong();
		}
		if (strcasecmp(input,"resume") == 0) {
			ResumeSong();
		}
		if (strcasecmp(input,"rewind") == 0) {
			RewindSong();
		}
		if (strcasecmp(input,"change") == 0) {
			//Prompt user for FILENAME of song
			printf("Filename: ");
			//Get input
			fgets(input,256,stdin);
			//Strip NEWLINE character
			input[strlen(input)-1] = 0x00;
			//unload current song if one exists
			UnloadSong();
			//Load our new song
			LoadSong(input);
			//Play our new song
			PlaySong(0);
		}
		//keep our loop from eating up CPU time
		//fgets should prevent loop from continuously running, but just a precaution
		SDL_Delay(50);
	}
}

//should impliment a check to see if file EXISTS
void LoadSong(char* filename) {
	GLOBAL_MUSIC = Mix_LoadMUS(filename);
}

void UnloadSong() {
	Mix_HaltMusic();
	Mix_FreeMusic(GLOBAL_MUSIC);
	GLOBAL_MUSIC = NULL;
}

//none of my input handlers get loop count yet
void PlaySong(int Loops) {
	Mix_PlayMusic(GLOBAL_MUSIC, Loops);
}

void PauseSong() {
	Mix_PauseMusic();
}

void ResumeSong() {
	Mix_ResumeMusic();
}

void RewindSong() {
	Mix_RewindMusic();
}

//end and clean up
void CloseProgram() {
	Mix_CloseAudio();
	SDL_Quit();
	exit(0);
}
```

---

### Post by PmDematagoda on 2009-01-17
Hmm, I am not sure if it is my PC or the command I'm using to compile your program, but I get some errors during compilation:-

Edit:- Scratch the compile error, I realised that the pkg-config command did not return -lSDL_Mixer. Sorry.:)
```
/tmp/cc8wLri5.o: In function `main':
sdl_player.c:(.text+0x44): undefined reference to `Mix_OpenAudio'
sdl_player.c:(.text+0x96): undefined reference to `Mix_HookMusicFinished'
/tmp/cc8wLri5.o: In function `LoadSong':
sdl_player.c:(.text+0x212): undefined reference to `Mix_LoadMUS'
/tmp/cc8wLri5.o: In function `UnloadSong':
sdl_player.c:(.text+0x224): undefined reference to `Mix_HaltMusic'
sdl_player.c:(.text+0x231): undefined reference to `Mix_FreeMusic'
/tmp/cc8wLri5.o: In function `PlaySong':
sdl_player.c:(.text+0x258): undefined reference to `Mix_PlayMusic'
/tmp/cc8wLri5.o: In function `PauseSong':
sdl_player.c:(.text+0x265): undefined reference to `Mix_PauseMusic'
/tmp/cc8wLri5.o: In function `ResumeSong':
sdl_player.c:(.text+0x272): undefined reference to `Mix_ResumeMusic'
/tmp/cc8wLri5.o: In function `RewindSong':
sdl_player.c:(.text+0x27f): undefined reference to `Mix_RewindMusic'
/tmp/cc8wLri5.o: In function `CloseProgram':
sdl_player.c:(.text+0x28c): undefined reference to `Mix_CloseAudio'
collect2: ld returned 1 exit status
```
The command I used was:-
```
gcc sdl_player.c -o sdl_player `pkg-config --libs --cflags sdl`
```

Also, in the InputHandler() function, don't you think you should initialise the THREAD_DONE variable to 0 before using it in the while loop which checks to see if it has no value in the first place?

---

### Post by loganwm on 2009-01-18
Basic functions are shaping up nicely thus far.

Pause
Resume
Load/Unload song
Mute
Unmute
Restart


All control is done through command line at the moment but I'm thinking of implementing a toggle system for control.

Hot Key or Command. I can use NCurses for instant command shortcuts via the keypad and retain usage of full commands on the command line.

I'm going work up a rudimentary playlist file skeleton tomorrow so I can have it functioning as a music player while I'm programming it :)

I'm trying to avoid a GUI at all costs to keep this program lightweight and fast, so if anyone has any usability concerns or suggestions, please feel free to interject.  Accessibility and functionality are slowly advancing as I'm working on this and I hope to have a decent enough prototype to release soon.

---

### Post by DocForbin on 2009-01-18
fwiw, have you considered using mpd?

---

### Post by loganwm on 2009-01-18
> **DocForbin said:**
> fwiw, have you considered using mpd?

I hadn't, but after reading your post I did a bit of searching.  It's alright though, I've already go the basis of my player working already, so I'm past that stage.

I'm looking into parsing m3u playlists so I don't have to design my own, and I'm also looking into mp3 tag information.

---

### Post by DocForbin on 2009-01-18
> **loganwm said:**
> I hadn't, but after reading your post I did a bit of searching.  It's alright though, I've already go the basis of my player working already, so I'm past that stage.

I'm looking into parsing m3u playlists so I don't have to design my own, and I'm also looking into mp3 tag information.

Which is one of many things mpd would make your project easier for ;)

[http://mpd.wikia.com/wiki/Development](http://mpd.wikia.com/wiki/Development)

---

### Post by loganwm on 2009-01-18
> **DocForbin said:**
> Which is one of many things mpd would make your project easier for ;)

[http://mpd.wikia.com/wiki/Development](http://mpd.wikia.com/wiki/Development)

Are you affiliated with the MPD project?

---

### Post by DocForbin on 2009-01-18
> **loganwm said:**
> Are you affiliated with the MPD project?
no

---

### Post by loganwm on 2009-01-18
> **DocForbin said:**
> no

Ah that's alright, I was just curious.

I'll consider it, but rather than writing up a client, I'd like to design a fully self sufficient player.

I am looking into it though, It's very neat!

---

### Post by DocForbin on 2009-01-18
> **loganwm said:**
> Ah that's alright, I was just curious.

I'll consider it, but rather than writing up a client, I'd like to design a fully self sufficient player.

I am looking into it though, It's very neat!

It's always fun to roll your own :) good luck!

I didn't mean to discourage you, btw, just thought you might dig mpd based on what you were after. It's super lightweight too. I serve ~15,000 mostly lossless files from a ps3 (256 MB memory) and barely notice it running performance wise. It's fun writing clients for it and there are lots of libraries to get started fast.

---

### Post by loganwm on 2009-01-18
> **DocForbin said:**
> It's always fun to roll your own :) good luck!

I didn't mean to discourage you, btw, just thought you might dig mpd based on what you were after. It's super lightweight too. I serve ~15,000 mostly lossless files from a ps3 (256 MB memory) and barely notice it running performance wise. It's fun writing clients for it and there are lots of libraries to get started fast.

Personally I love Amarok and full featured Music Players, but I hate the bogged down resource heavy mess sometimes when I'm just trying to get things done.

I'm big into my music, it's a lot of Beatles and Oasis mostly, but I'm building a respectable collection of a few thousand songs.

How do you like the PS3? I've had mine for a while, considering running it under linux or as an outlet for media hosted elsewhere throughout my home, what do you use it for?

PS: If you're ever on LittleBigPlanet hit me up on PSN, I'm always building ridiculous machines.

---

### Post by DocForbin on 2009-01-18
right on. I picked up littlebigplanet a while back, but haven't had a chance  to play much. Very cool game though.

My ps3 is booted into gentoo more often than the game os, but I love it for games and it's a sweet dvd/bluray player. In gentoo I mainly use it as a music/file server. I use mpd to play music on my home stereo from any computer in the house. I have a couple usb drives that sync for backups via rsync and store pretty much everything on it. I sometimes start x and use it to play videos or surf or whatnot on, but mostly it's a headless server.

---

### Post by efexD on 2009-01-19
Looks good.

---

### Post by loganwm on 2009-01-19
Hot Key mode is now functional and mute/unmute functions have been implemented.

To enter the new "Live Mode" for hotkeys type "live" at the prompt. To go back to command mode hit the tilde key "~".

The commands for hot key mode are as follows:
p pause
r resume
m mute
u unmute
q restart song
x exit
~ exit live

Compile with:
gcc audio.c -o audio -lSDL -lSDL_mixer -lpthread -lncurses

```
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <string.h>
#include <time.h>

#include <ncurses.h>
#include <SDL/SDL.h>
#include <SDL/SDL_mixer.h>

/*	Global Variables:
	GLOBAL_MUSIC: current song data is loaded here
	GLOBAL_TMP_VOLUME: saves volume before muting, used later to unmute
*/
Mix_Music *GLOBAL_MUSIC = NULL;
int GLOBAL_TMP_VOLUME;

/*	Function Declarations:
	void UnloadSong(void): called upon completion of a song to clear from memory
	void LoadSong(void): called to load a new song into the player
	void PlaySong(int): called to play a song that's looaded into memory, arg is loops! -1 for infinite
	void PauseSong(): called to pause a playing song
*/
void UnloadSong();
void LoadSong(char*);

//these are just abstracted forms of the MIXER functions
void PlaySong(int);
void PauseSong();
void ResumeSong();
void RewindSong();
void MuteSong();
void UnmuteSong();

//these start and stop live key events
void StartLiveMode();
void EndLiveMode();

//close and clean up function
void CloseProgram();

//called by thread to handle input during song
void InputHandler();

int main(void) {
	int done = 0;

	// create our PTHREAD which calls InputHandler
	pthread_t Listener;
	int ListenerThread;

	SDL_Init(SDL_INIT_AUDIO);
	Mix_OpenAudio(22050, AUDIO_S16, 2, 4096);


	while (!done) {
		if (GLOBAL_MUSIC == NULL) {
			//create our thread to get input parallel to playing music
			ListenerThread = pthread_create(&Listener, NULL,(void*)&InputHandler,NULL);
			//is this necessary? my knowledge of threads is weak.
			pthread_join(Listener,NULL);
			//upon finish, dump it.
			Mix_HookMusicFinished(UnloadSong);
		}
	}
	// If we get this far (and we shouldn't) then we should return
	return 0;
}

void InputHandler() {
	//input buffer
	char input[256];
	//store status of thread (0 = Not Done)
	int THREAD_DONE = 0;

	int LIVE_MODE = 0;

	int KEY_PRESSED;

	while (!THREAD_DONE) {
		if (LIVE_MODE) {
			KEY_PRESSED = getch();
			if (KEY_PRESSED == 'x') {
				EndLiveMode();
				CloseProgram();
			}
			if (KEY_PRESSED == '`') {
				EndLiveMode();
				LIVE_MODE = 0;
			}
			if (KEY_PRESSED == 'p') {
				PauseSong();
			}
			if (KEY_PRESSED == 'r') {
				ResumeSong();
			}
			if (KEY_PRESSED == 'q') {
				RestartSong();
			}
			if (KEY_PRESSED == 'm') {
				MuteSong();
			}
			if (KEY_PRESSED == 'u') {
				UnmuteSong();
			}
		}
		else
		{	//Recieve input from user forever until thread terminated
			fgets(input,256,stdin);
			//Strip the newline character from input\
			//sets index at LENGTH-1 of string to null to get ride of NEWLINE
			input[strlen(input)-1] = 0x00;
			//NewLine character is stripped from input
			//be careful with input comparison
			if (strcasecmp(input,"exit") == 0) {
				CloseProgram();
			}
			if (strcasecmp(input,"pause") == 0) {
				PauseSong();
			}
			if (strcasecmp(input,"resume") == 0) {
				ResumeSong();
			}
			if (strcasecmp(input,"rewind") == 0) {
				RewindSong();
			}
			if (strcasecmp(input,"mute") == 0) {
				MuteSong();
			}
			if (strcasecmp(input,"unmute") == 0) {
				UnmuteSong();
			}
			if (strcasecmp(input,"live") == 0) {
				//set volume to what it was before mute
				LIVE_MODE = 1;
				StartLiveMode();
			}
			if (strcasecmp(input,"change") == 0) {
				//Prompt user for FILENAME of song
				printf("Filename: ");
				//Get input
				fgets(input,256,stdin);
				//Strip NEWLINE character
				input[strlen(input)-1] = 0x00;
				//unload current song if one exists
				UnloadSong();
				//Load our new song
				LoadSong(input);
				//Play our new song
				PlaySong(0);
			}
		}
		//keep our loop from eating up CPU time
		//fgets imeshould prevent loop from continuously running, but just a precaution
		SDL_Delay(50);
	}
}

//should impliment a check to see if file EXISTS
void LoadSong(char* filename) {
	GLOBAL_MUSIC = Mix_LoadMUS(filename);
}

void UnloadSong() {
	Mix_HaltMusic();
	Mix_FreeMusic(GLOBAL_MUSIC);
	GLOBAL_MUSIC = NULL;
}

//none of my input handlers get loop count yet
void PlaySong(int Loops) {
	Mix_PlayMusic(GLOBAL_MUSIC, Loops);
}

void PauseSong() {
	Mix_PauseMusic();
}

void ResumeSong() {
	Mix_ResumeMusic();
}

void RewindSong() {
	Mix_RewindMusic();
}

void MuteSong() {
	//It volume isn't already zero, then zero it and store old
	//prevents muting twice from deleting old value
	if (Mix_VolumeMusic(-1) != 0) {
		GLOBAL_TMP_VOLUME = Mix_VolumeMusic(-1);
		Mix_VolumeMusic(0);
	}
}

void UnmuteSong() {
	//set volume to what it was before mute
	Mix_VolumeMusic(GLOBAL_TMP_VOLUME);
}

void StartLiveMode() {
	//initiate NCURSES
	initscr();
	//Enable keyboard events
	keypad(stdscr,true);
	//don't require newline/carriage return for inpur
	nonl();
	//get each char
	cbreak();
	//don't show what we type
	noecho();
}

void EndLiveMode() {
	endwin();
}

//end and clean up
void CloseProgram() {
	Mix_CloseAudio();
	SDL_Quit();
	EndLiveMode();
	exit(0);
}

```

---

### Post by ibuclaw on 2009-01-19
Awesome, things are shaping up nicely.

What I would do at this point is move all functions to a header file, and just let the main.c file be the jelly that holds it all together.
That or make a C++ Class Object out of it ;)

Small note on the code you posted above, you have "RestartSong()" in one of your if statements, and it isn't defined anywhere in the rest of the code, so I renamed that line "RewindSong()" as I think that is what you wanted of it (it works as one would expect, anyway).
Also, why use an integer for the LIVE_MODE variable when it will only have 2 values? Use a boolean :)
[EDIT] Just noticed that you use integers with the value 0 around the code often.
```
--- audio.c	2009-01-19 18:19:06.000000000 +0000
+++ audio.c	2009-01-19 18:26:28.000000000 +0000
@@ -73,7 +73,7 @@
 	//store status of thread (0 = Not Done)
 	int THREAD_DONE = 0;
 
-	int LIVE_MODE = 0;
+	bool LIVE_MODE = false;
 
 	int KEY_PRESSED;
 
@@ -86,7 +86,7 @@
 			}
 			if (KEY_PRESSED == '`') {
 				EndLiveMode();
-				LIVE_MODE = 0;
+				LIVE_MODE = false;
 			}
 			if (KEY_PRESSED == 'p') {
 				PauseSong();
@@ -95,7 +95,7 @@
 				ResumeSong();
 			}
 			if (KEY_PRESSED == 'q') {
-				RestartSong();
+				RewindSong();
 			}
 			if (KEY_PRESSED == 'm') {
 				MuteSong();
@@ -132,7 +132,7 @@
 			}
 			if (strcasecmp(input,"live") == 0) {
 				//set volume to what it was before mute
-				LIVE_MODE = 1;
+				LIVE_MODE = true;
 				StartLiveMode();
 			}
 			if (strcasecmp(input,"change") == 0) {

```
What would be nice is a small gui to go with ncurses.
I could do a quick write-up, but I'll let you get on with it, as you seem to be just fine by yourself.

Keep up the interesting work.

Regards
Iain

---

### Post by loganwm on 2009-01-19
> **tinivole said:**
> 
What would be nice is a small gui to go with ncurses.
I could do a quick write-up, but I'll let you get on with it, as you seem to be just fine by yourself.

Keep up the interesting work.

Regards
Iain

Thanks for pointing out that bug, it was actually something I wrote in as I was in the process or posting it before I went out for a bit.  It's shaping up VERY nicely so far, I'm very pleased with progress.

If you'd like the do a small GUI in NCURSES you're more than welcome to write up one and I'll credit you when I release this. I'd be more than grateful.

I appreciate the help and support so far and if you want to get involved with this you're more than welcome to jump into this with me.

---

### Post by ibuclaw on 2009-01-19
> **loganwm said:**
> Thanks for pointing out that bug, it was actually something I wrote in as I was in the process or posting it before I went out for a bit.  It's shaping up VERY nicely so far, I'm very pleased with progress.

If you'd like the do a small GUI in NCURSES you're more than welcome to write up one and I'll credit you when I release this. I'd be more than grateful.

I appreciate the help and support so far and if you want to get involved with this you're more than welcome to jump into this with me.

Well, I've put in a quick hours work, its not much, but if you don't know ncurses, it serves a good example to start learning on.
All I've put on is a menu for everything you've implemented thus far. You can switch between CLI and Live Mode, pause in one, resume in the other, etc. Hotkeys for Live Mode still present, and you can change track in Live Mode now. (Press 'c')

Food for thought, think about how you will implement the "seeing" the length of the track and the remainder left, and how to control the volume of the song.

Anyway, good luck with making it.

Regards
Iain

---

### Post by loganwm on 2009-01-19
> **tinivole said:**
> Well, I've put in a quick hours work, its not much, but if you don't know ncurses, it serves a good example to start learning on.
All I've put on is a menu for everything you've implemented thus far. You can switch between CLI and Live Mode, pause in one, resume in the other, etc. Hotkeys for Live Mode still present, and you can change track in Live Mode now. (Press 'c')

Food for thought, think about how you will implement the "seeing" the length of the track and the remainder left, and how to control the volume of the song.

Anyway, good luck with making it.

Regards
Iain

I haven't had a chance to look at your code yet. BUT I've been struggling with my algorithm for navigating through the song. I can't manage to get or monitor my position and I'm driving myself nuts with it.

I've gotta write up and organize my ideas for it or I'm without a clue.  I've tried using timers but my issue involves the time in between pause and resume.

Volume should be easy peasy, I'll show it as soon as I put my words into code.

---

