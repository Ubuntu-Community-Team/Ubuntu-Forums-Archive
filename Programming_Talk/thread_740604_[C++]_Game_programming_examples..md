---
title: "[C++] Game programming examples."
date: 2008-03-30
forum: Programming Talk
---

### Post by Sockerdrickan on 2008-03-30
Hello, here we will gather small and clean examples of how to write games in C++. It is recommended to comment each others code and improve it. Another important thing is to write standardized code, please use -Wall and -Wextra at least.

1. Pong
[PHP]/*
FreePong
 Written by Robin Stjerndorff 2008
License: GPLV3
*/

#include <string>
#include <sstream>
#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include "SDL/SDL_ttf.h"
#include "SDL/SDL_mixer.h"
using namespace std;

const int Framerate=60;

bool run=true, BallDirection=false, UseBot=true;
int r_width=1024, r_height=768;
int Player1X, Player2X;
int Player1Score=0, Player2Score=0, MaxScore=15;
double BallY, BallX, BallAngle=0, Player1Y, Player2Y, MoveSpeed=3, BallSpeed=6;

SDL_Surface *bar, *bar2, *ball;
Mix_Chunk *SndGame, *SndHit, *SndScore;
TTF_Font *Font;

class Timer {
	private:
		int startTicks;

	public:
		Timer():startTicks(0) {}

	void start() {
		startTicks=SDL_GetTicks();    
	}

	int get_ticks() {
		return SDL_GetTicks() - startTicks;
	}
};

void RenderImg(SDL_Surface* a,SDL_Surface* b,int x,int y) {
	SDL_Rect c={x,y,0,0};
	SDL_BlitSurface(a,0,b,&c);
}

void ResetScene() {
	BallAngle=0;
	Player1X=10;
	Player1Y=r_height/2-bar->h/2;
	Player2X=r_width-12;
	Player2Y=r_height/2-bar->h/2;
	BallX=r_width/2-ball->w/2;
	BallY=r_height/2-ball->h/2;
	BallSpeed+=0.3;
	MoveSpeed+=0.3;
}

double SetBallAngle(double PlayerY) {
	if(BallY>PlayerY+bar->h/2+bar->h/4)
		return MoveSpeed;
	else if(BallY<PlayerY+bar->h/2-bar->h/4)
		return -MoveSpeed/1.5;
	else if(BallY>PlayerY+bar->h/2+bar->h/12)
		return MoveSpeed;
	else if(BallY<PlayerY+bar->h/2-bar->h/12)
		return -MoveSpeed/3;
	return 0;
}

void UpdateScore(SDL_Surface *screen) {
	static SDL_Color TextColor={28,28,28,0};
	SDL_Surface *tmp;
	string tmpstr;

	if(Player1Score<MaxScore && Player2Score<MaxScore) {
		stringstream sstream;
		sstream<<Player1Score<<" - "<<Player2Score;
		tmpstr=sstream.str();

		tmp=TTF_RenderUTF8_Blended(Font,tmpstr.c_str(),TextColor);
		RenderImg(tmp,screen,r_width/2-tmp->w/2,r_height/2-tmp->h/2);
		SDL_FreeSurface(tmp);
	}
	else {
		Player1Score=0;
		Player2Score=0;
		BallSpeed=8;
		MoveSpeed=3;
		ResetScene();
	}
}

int main(int argc, char **argv) {
	Timer FPSTimer;
	SDL_Init(SDL_INIT_EVERYTHING);
	TTF_Init();
	Mix_OpenAudio(44100,AUDIO_S16SYS,2,1024);

	SDL_Event e;

	bar=IMG_Load("gfx/bar.png");
	bar2=IMG_Load("gfx/bar2.png");
	ball=IMG_Load("gfx/ball.png");

	SndGame=Mix_LoadWAV("sfx/game.wav");
	SndHit=Mix_LoadWAV("sfx/hit.wav");
	SndScore=Mix_LoadWAV("sfx/score.wav");

	Font=TTF_OpenFont("gfx/sans.ttf",40);

	SDL_Surface *screen=SDL_SetVideoMode(r_width,r_height,32,0);
	SDL_WM_SetCaption("FreePong","FreePong");
	SDL_ShowCursor(SDL_DISABLE);
	ResetScene();
	Mix_PlayChannel(-1,SndGame,0);

		while(run) {
			FPSTimer.start();
			SDL_PollEvent(&e); 
			if(e.type==SDL_QUIT)
				run=false;
			if(e.type==SDL_KEYDOWN) {
				switch(e.key.keysym.sym) {
					case SDLK_ESCAPE: run=false; break;
					case SDLK_F4:
						static bool fullscreen=false;
						fullscreen=!fullscreen;
						screen=SDL_SetVideoMode(r_width,r_height,32,fullscreen?SDL_FULLSCREEN:0);
					break;
					case SDLK_q:
						if(Player1Y>0)
							Player1Y-=MoveSpeed;
					break;
					case SDLK_a:
						if(Player1Y<r_height-bar->h)
							Player1Y+=MoveSpeed;
					break;
					case SDLK_o:
						if(!UseBot) {
							if(Player2Y>0)
								Player2Y-=MoveSpeed;
						}
					break;
					case SDLK_l:
						if(!UseBot) {
							if(Player2Y<r_height-bar->h)
								Player2Y+=MoveSpeed;
						}
					break;
					default:break;
				}
			}

			if(BallX<-ball->h) {
				++Player2Score;
				ResetScene();
				Mix_PlayChannel(-1,SndScore,0);
			}

			if(BallX>r_width+ball->h) {
				++Player1Score;
				ResetScene();
				Mix_PlayChannel(-1,SndScore,0);
			}

			//if ball hits player 1
			if(BallX<=Player1X && BallY>Player1Y && BallY<Player1Y+bar->h) {
				BallDirection=true;
				BallAngle=SetBallAngle(Player1Y); //update ball angle for a player 1 hit
				Mix_PlayChannel(-1,SndHit,0);
			}

			//if ball hits player 2
			if(BallX+ball->w>=Player2X && BallY>Player2Y && BallY<Player2Y+bar->h) {
				BallDirection=false;
				BallAngle=SetBallAngle(Player2Y);
				Mix_PlayChannel(-1,SndHit,0);
			}

			if(UseBot) {
				if(BallY>=Player2Y+bar2->h/2)
					Player2Y+=MoveSpeed*0.89;
				if(BallY<=Player2Y+bar2->h/2)
					Player2Y-=MoveSpeed*0.89;
			}

			if(BallDirection) {
				BallX+=BallSpeed;
				BallY+=BallAngle;
			}
			else {
				BallX-=BallSpeed;
				BallY+=BallAngle;
			}

			if(BallY<=1||BallY>=r_height-ball->h) {
				Mix_PlayChannel(-1,SndHit,0);
				if(BallAngle)
					BallAngle-=BallAngle*2;
				else
					BallAngle+=BallAngle*2;
			}

			SDL_FillRect(screen,NULL,0);
			UpdateScore(screen);
			RenderImg(bar,screen,Player1X,int(Player1Y));
			RenderImg(bar2,screen,Player2X,int(Player2Y));
			RenderImg(ball,screen,int(BallX),int(BallY));
			SDL_Flip(screen);
			if(FPSTimer.get_ticks()<1000/Framerate)
				SDL_Delay((1000/Framerate)-FPSTimer.get_ticks());
		}
	SDL_Quit();
	return 0;
}
[/PHP]
[B]Compiles with: g++ main.cpp -lSDL -lSDL_image -lSDL_mixer -lSDL_ttf
You can get all that you need with[/B]
```
sudo apt-get install build-essential libsdl-ttf2.0-dev libsdl-mixer1.2-dev libsdl-image1.2-dev libsdl1.2-dev
```

---

### Post by NullHead on 2008-03-30
n00b programing question here ... what do I do with the code? how can I compile it... :(

---

### Post by Sockerdrickan on 2008-03-30
Paste it in a file called main.cpp then run ```
g++ main.cpp -lSDL -lSDL_image -lSDL_mixer -lSDL_ttf
``` from a terminal in the correct directory.

---

### Post by NullHead on 2008-03-30
Thanks! I'm no good at programing ... C++ is something I know nothing about ... for that matter how to use gcc lol! I can however use a little bash .. but thats about it. I'll let you know if I fail at compiling pong.

---

### Post by Sockerdrickan on 2008-03-30
> **NullHead said:**
> I'll let you know if I fail at compiling pong.

If you want to succeed the first time you might want to get the right stuff needed ```
sudo apt-get install build-essential libsdl-ttf2.0-dev libsdl-mixer1.2-dev libsdl-image1.2-dev libsdl1.2-dev
```

---

### Post by NullHead on 2008-03-30
Well it all worked as anyone would've thought. It's actually very entertaining :D Thanks for this!

---

### Post by Sockerdrickan on 2008-03-30
Don't forget to change the source code, recompile and watch what it did.

---

### Post by NullHead on 2008-03-31
I dont' know any C++ remember? ;)

---

### Post by Sockerdrickan on 2008-03-31
That's what I mean!

---

### Post by NullHead on 2008-03-31
So guess on something and see what it does? Like just play with it a little and see what it does? Thats a good diea! :D

---

### Post by Sockerdrickan on 2008-03-31
Yes! Start with obviously easy tasks, such as changing the location of the media.

---

### Post by slavik on 2008-03-31
beware: old code!

[http://bcacm.org/~slavik/AI-Escape.tar.bz2](http://bcacm.org/~slavik/AI-Escape.tar.bz2)

no collision detection and it does a max of 100fps.

---

### Post by Lord Illidan on 2008-03-31
For a moment, I thought you were having me on when I saw PHP code at the top and g++ at the bottom :D

Nice one though.

---

### Post by Tom Mann on 2008-03-31
Are there any good tutorials online for SDL/C++ Game programming? I'm interested now! :-D

---

### Post by bobrocks on 2008-03-31
For 2d stuff, lazy foo is quite good. [http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

---

### Post by Mehashi on 2008-03-31
Excellent!
I have decided as well to learn c++ and this seems a good starting point! 
Thanks to TuxOr for the example as well, its really useful to have an example of some code to look at, I find I learn quicker seeing something 'in action' as such! Any more examples can only provide  better learning experiences for all!
Thanks again!
^_^

---

### Post by Sockerdrickan on 2008-03-31
> **Mehashi said:**
> I find I learn quicker seeing something 'in action' as such! Any more examples can only provide  better learning experiences for all!
Thanks again!
^_^

Me too! I will provide another game in the future (side scroller)

---

### Post by Ulrik04 on 2008-04-13
when i compiles it, it gives me an file named "a.out", but when i tries to run it it just comes with an error saying

"The filename "a.out" indicates that this file is of type "GULP Output File Format". The contents of the file indicate that the file is of type "executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file."

---

### Post by Zugzwang on 2008-04-13
> **Ulrik04 said:**
>  [...] To open the file, rename the file to the correct extension for "executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file."

There is no correct extension for executable in Linux, so I wonder what's the point here. Try running it from the terminal with
```

./a.out

```
after you switched to the directory in which you compiled it. You can also use the "-o" switch of G++/GCC to choose an output file name:
```

g++ main.cpp -o mygame -lSDL -lSDL_image -lSDL_mixer -lSDL_ttf

```

---

### Post by alberto ferreira on 2008-09-20
Sorry for the noob question but I copied the source into main.cpp, then i ran the  "g++ main.cpp -lSDL -lSDL_image -lSDL_mixer -lSDL_ttf" command in the directory containing main.cpp and the result was:

main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:175: error: expected `(' before &#8216;a&#8217;
main.cpp:175: error: &#8216;a&#8217; was not declared in this scope
main.cpp:175: error: expected `;' before &#8216;player&#8217;
main.cpp:177: error: expected primary-expression before &#8216;}&#8217; token
main.cpp:177: error: expected `;' before &#8216;}&#8217; token
main.cpp:177: error: expected primary-expression before &#8216;}&#8217; token
main.cpp:177: error: expected `)' before &#8216;}&#8217; token
main.cpp:177: error: expected primary-expression before &#8216;}&#8217; token
main.cpp:177: error: expected `;' before &#8216;}&#8217; token


I installed the tools you mentioned, so, what's wrong :s


Please answer!!

---

### Post by Sockerdrickan on 2008-12-16
> **alberto ferreira said:**
> Sorry for the noob question but I copied the source into main.cpp, then i ran the  "g++ main.cpp -lSDL -lSDL_image -lSDL_mixer -lSDL_ttf" command in the directory containing main.cpp and the result was:

main.cpp: In function ‘int main(int, char**)’:
main.cpp:175: error: expected `(' before ‘a’
main.cpp:175: error: ‘a’ was not declared in this scope
main.cpp:175: error: expected `;' before ‘player’
main.cpp:177: error: expected primary-expression before ‘}’ token
main.cpp:177: error: expected `;' before ‘}’ token
main.cpp:177: error: expected primary-expression before ‘}’ token
main.cpp:177: error: expected `)' before ‘}’ token
main.cpp:177: error: expected primary-expression before ‘}’ token
main.cpp:177: error: expected `;' before ‘}’ token


I installed the tools you mentioned, so, what's wrong :s


Please answer!!
It works without a hitch here? What version of Ubuntu / GCC?

---

