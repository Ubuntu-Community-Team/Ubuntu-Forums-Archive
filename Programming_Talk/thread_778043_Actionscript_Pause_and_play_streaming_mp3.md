---
title: "Actionscript Pause and play streaming mp3"
date: 2008-05-01
forum: Programming Talk
---

### Post by anfractuosities on 2008-05-01
I am making an audio player for the web. I am streaming the mp3 with
LoadSound("...", true)

I am also using .position to get the time in milliseconds.

I am trying to get the song to play from the point it stopped, and when I unpause it it plays like a 1/8 of a second from where it was paused, and then stops.

Is the song not loading anymore and the stream is stopping?

If so can I code the position it starts loading the stream from?


Here is my code with only 1 song option for space saving:

```

SLIDER= 0;                  //for controling slider(a later problem to work out) and getting location of song
PAUSEVAR= 0;           // Boolean for pause or not pause

DotKids._alpha=0;         //bullet for song thats playing

Play.onPress = function()
	{
		Songs.call();
	}
	
KidsKnow.onPress = function()          //if you click on the song title
	{
		SONGNUM= 1 ;
		Songs.call();
	}
	
	

Pause.onPress = function()                      //checks to see if pauseed or not
	{
		if (PAUSEVAR === 1)
			{
									
				KidsSong.start(SLIDER);					
				PAUSEVAR = 0;
			}

		else if (PAUSEVAR === 0)
			{
				
				PAUSEVAR=1;
				SLIDER= KidsSong.position * 1000;									
				stopAllSounds();
			}
	}
	
Stop.onPress = function()
	{
		DotKids._alpha=0;
		stopAllSounds();
	}



stop();

function Songs()
	{

	DotKids._alpha=100;
	KidsSong = new Sound(KidsSoundLoader);
	KidsSong.loadSound("kidsknow.mp3", true);
	
	}
 
           


```

---

### Post by lapubell on 2008-05-01
hmm... not that i will be of much help, as I can't see the problem in your code, but I would set up a preloader for that song and see if the loading stops in the bandwidth profiler when testing the movie.

---

### Post by anfractuosities on 2008-05-02
SOLVED!!...I needed to divide the position by 1000 instead of multiply....Silly math...

---

