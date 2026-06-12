---
title: "No video info output ??"
date: 2005-12-31
forum: Programming Talk
---

### Post by kudu on 2005-12-31
How come this program doesn't output any info ??

//kudu variation



//include SDL stuff

#include <SDL/SDL.h>



//include ability to exit program

#include <cstdlib>
#include <iostream>



//video information pointer

const SDL_VideoInfo* g_pVideoInfo = NULL;



//main function

int main(int argc, char* argv[])

{

	//initialize SDL

	if (SDL_Init(SDL_INIT_VIDEO)==-1)

	{

		//error initializing SDL



		//report the error

		fprintf(stderr,"Could not initialize SDL!\n");



		//end the program

		exit(1);

	}

	else

	{

		//SDL initialized



		//report success

		fprintf(stdout,"SDL initialized properly!\n");



		//set up to uninitialize SDL at exit

		atexit(SDL_Quit);

	}



	//grab video info pointer

	g_pVideoInfo = SDL_GetVideoInfo();



	//check for an error

	if(!g_pVideoInfo)

	{

		//report error and exit

		fprintf(stderr,"Could not get video info!\n");

		exit(1);

	}



	//report status of bit flags

	fprintf(stdout, "\nVideo Information:\n");

	fprintf(stdout, "hw_available? %d\n", g_pVideoInfo->hw_available);

	fprintf(stdout, "wm_available? %d\n", g_pVideoInfo->wm_available);

	fprintf(stdout, "blit_hw? %d\n", g_pVideoInfo->blit_hw);

	fprintf(stdout, "blit_hw_CC? %d\n", g_pVideoInfo->blit_hw_CC);

	fprintf(stdout, "blit_hw_A? %d\n", g_pVideoInfo->blit_hw_A);

	fprintf(stdout, "blit_sw? %d\n", g_pVideoInfo->blit_sw);

	fprintf(stdout, "blit_sw_CC? %d\n", g_pVideoInfo->blit_sw_CC);

	fprintf(stdout, "blit_sw_A? %d\n", g_pVideoInfo->blit_sw_A);

	fprintf(stdout, "blit_fill? %d\n", g_pVideoInfo->blit_fill);

	fprintf(stdout, "video memory(in K)? %d\n", g_pVideoInfo->video_mem);

	fprintf(stdout, "bits per pixel? %d\n", g_pVideoInfo->vfmt->BitsPerPixel);



	//report

	fprintf(stdout,"\nTerminating program normally.\n");



	//return 0

	return(0);

}


Program output:

EXECUTING:
/home/kudu/Projects/sdl/src/sdl1
----------------------------------------------
SDL initialized properly!

Video Information:
hw_available? 0
wm_available? 1
blit_hw? 0
blit_hw_CC? 0
blit_hw_A? 0
blit_sw? 0
blit_sw_CC? 0
blit_sw_A? 0
blit_fill? 0
video memory(in K)? 0
bits per pixel? 32

Terminating program normally.

----------------------------------------------
Program exited successfully with errcode (0)
Press the Enter key to close this terminal ...

What gives ?

---

