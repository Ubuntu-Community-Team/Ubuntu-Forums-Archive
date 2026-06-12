---
title: "Need to do simple 2d animations"
date: 2009-01-28
forum: Programming Talk
---

### Post by buntoo on 2009-01-28
hi,
For a project, i need to write C (or C++) code for simple animations.
For example, drawing/moving rectangles on the screen. (or moving small images on the screen)
The moving pattern inputs will be a text file.
Now, my biggest problem is I do not know which graphics library to use. I have tried installing Mesa and couldnt get it to work. I installed Cairo, but its not suitable for what i'm trying. I've even tried using the port of graphics.h to linux. 
Do suggest some library which i could use for my application. Also do provide any links that can help.
thanks.

---

### Post by KIAaze on 2009-01-29
You should have asked this here:
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)
or here:
[http://forum.freegamedev.net/](http://forum.freegamedev.net/)
;)

I think the easiest would be to use a game engine since all you want to do is display sprites and move them around.

Here you can find a list of tutorials, libraries and game engines:
[http://wiki.freegamedev.net/index.php/Main_Page](http://wiki.freegamedev.net/index.php/Main_Page)

If you don't want to use a game engine, you can use SDL directly (or OpenGL for 3D).

Mesa and cairo are really low level as far as I know.

My personal recommendation for a game engine (since I work on it :) ):
[http://sourceforge.net/svn/?group_id=186694](http://sourceforge.net/svn/?group_id=186694)
[http://iteamgame.org/wiki/index.php?title=GP2D_Engine](http://iteamgame.org/wiki/index.php?title=GP2D_Engine)

The wiki is being rewritten currently, so it might not be of much help for now unfortunately.

---

### Post by slavik on 2009-01-29
opengl is not difficult for 2d. What problems are you having with mesa?

---

### Post by buntoo on 2009-01-29
Thanks guys for your replies..
@ KIAaze, I looked at the links you said, i think without much resources online, i would find it really difficult to program for it.
I think opengl should work for me.. 
@Slavik. I am not sure which problem to tell you.
The sample c files just dont compile. It says they need glut. even though i have installed it and set the correct enviornment variables.
though some of the demos compile using "cc" command, those that require glut give an error.

---

### Post by KIAaze on 2009-01-29
Well, tutorials for SDL are easy to find:
[http://www.libsdl.org/tutorials.php](http://www.libsdl.org/tutorials.php)
[http://gpwiki.org/index.php/C:SDL_tutorials](http://gpwiki.org/index.php/C:SDL_tutorials)
[http://lazyfoo.net/SDL_tutorials/](http://lazyfoo.net/SDL_tutorials/)

And for openGL, there's [http://nehe.gamedev.net/](http://nehe.gamedev.net/)

As for gamepower, if you check out the latest source code from gamepower/GP2D-new/trunk, it contains examples too.
But since it's alpha software, I wouldn't recommend using it if you aren't already familiar with svn, C++ and co.

---

### Post by matyasfalvi on 2009-11-18
Hi!

I have a rather complex problem, which seem to fit the title though. 
I wrote a program in c++, which models free way traffic. 

It is a very simple model not too fancy. 

It is basically a 2x100 array. Cars occupying one site in the array are advanced after every update v sites, where v is the speed of the cars. (Of course cars are accelerated, decelerated, they overtake each other etc.) 

The program outputs the 2x100 array into a text file after every update.

Sure enough my teacher told me to make an animation out of the whole thing ergo flash one update then erase it from the screen flash the next one etc. and also mark those sites where v=0 with red. To be more specific you will see the program below. I want to do the "animation" with the content of *output_traffic.txt*

I study math not IT so this is a little challenging for me. 

My first question:
Which one should I use: textmode, initgraph, setgraphmode?
As far as I'm concerned textmode would be enough for this one however I don't seem to find any good linux tutorials for this one. 

Here is the program so you can get an idea what I'm talking about here:

```
     

#include <algorithm>
#include <ctime>
#include <cstdlib>
#include <fstream>
#include <iostream>
#include <vector>

using namespace std;

int acceleration(int L[][100], int row, int column) 
{
	int m, acc;

	for(m=column+1; m<column+L[row][column]+2; m++) {
		if(L[row][m]!=-1 && m<100) {
			acc=0;
			m=column+L[row][column]+2;
		}
		else {	
			acc=1;
		}
	}
	
	return acc;
}

vector<int> cpos_jam(int L[][100])
{
	
	vector<int> wc_jam;
	
	for(int i=0; i<2; i++) {
		for(int j=1; j<100; j++) {
			if(L[i][j]==0) {
				wc_jam.push_back(j);
			}
		}
	}
	
	return wc_jam;
}

int deceleration(int L[][100], int row, int column) 
{
	int m, dec, dist=0;

	for(m=column+1; m<column+L[row][column]+1; m++) {
		if(L[row][m]==-1 || m>99) {
			dec=0;
			dist+=1;
			
		}
		else {	
			dec=L[row][column]-dist;
			m=column+L[row][column]+1;
		}
	}
	
	return dec;
}


float density_func(int L[][100])
{
	float density;
	int n_car=0;
	
	for(int i=0; i<2; i++) {
		for(int j=0; j<100; j++) {
			if(L[i][j]!=-1) {
				n_car+=1;
			}
		}
	}
	
	density = (float) n_car/200;
	
	return density;
}

int motion(int L[][100], int row, int column)
{
	int pos;
	pos=column+L[row][column];
	
	return pos;
}

int num_jam(int L[][100])
{
	
	int n_jam=0;
	
	for(int i=0; i<2; i++) {
		for(int j=1; j<100; j++) {
			if(L[i][j]==0) {
				n_jam+=1;
			}
		}
	}
	
	return n_jam;
}

int overtake(int L[][100], int row, int column) 
{
	int m, pos;

	for(m=column+1; m<column+L[row][column]+2; m++) {
		if(L[row][m]!=-1 && m<99) {
			switch(row)
			{
				case 0: if(L[1][column]==-1) {
							pos=1;
						}
						else {
							pos=row;
						}; break;
				
				case 1: if(L[0][column]==-1) {
							pos=0;
						}
						else {
							pos=row;
						}; break;
				
			}
			m=column+L[row][column]+2;
		}
		else {	
			pos=row;
		}
	}
	
	return pos;
}

void randomization(int L[][100], float p) 
{
	for(int i=0; i<2; i++) {
		for(int j=0; j<100; j++) {
			float rand_num = (float) rand()/RAND_MAX;
			if(L[i][j]>0 && rand_num<p) {
				L[i][j]=L[i][j]-1;
			}
		}
	}
}

vector<int> rpos_jam(int L[][100])
{
	
	vector<int> wr_jam;
	
	for(int i=0; i<2; i++) {
		for(int j=1; j<100; j++) {
			if(L[i][j]==0) {
				wr_jam.push_back(i);
			}
		}
	}
	
	return wr_jam;
}

int main(int argc, char** argv)
{

	//Initialization

	ofstream outtraffic("output_traffic.txt");
	ofstream outcontrol("output_control.txt");
	ofstream outadditional("output_aditional.txt");
	ofstream table("table.txt");

	// T=total number of jams; D=density; P=probability of random deceleration; G=guidance
	
	table<<"T     D     P     G"<<endl; 
	
	int v_max=5;
	int v_init=3;
	int rapid_dec=0;
	int total_n_jam=0;
	int iter_out=4;
	int iter_in=10;
	int g;
	
	float density;
	cout<<"Enter density for 0<density<1"<<endl;
	cin>>density;
	
	float p;
	cout<<"Enter probability 0<=p<=1 for random deceleration"<<endl;
	cin>>p;
			
	int occupancy;
	occupancy=200*density;
		
	int L1[2][100];	
	int L2[2][100];
		
	srand((unsigned)time(NULL));

for(int s=0; s<iter_out; s++) {	
		
	//Init L1
		
	for(int i=0; i<2; i++) {
		for(int j=0; j<occupancy/2; j++) {
			L1[i][j]=v_init;
		}
	}

	for(int i=0; i<2; i++) {
		for(int j=occupancy/2; j<100; j++) {
			L1[i][j]=-1;
		}
	}
		
	//Init L2
		
	for(int i=0; i<2; i++) {	
		for(int j=0; j<100; j++) {
			L2[i][j]=-1;
		}	
	}
	
	//Shuffle
		
	random_shuffle( L1[0], L1[0]+99 );
	random_shuffle( L1[1], L1[1]+99 );	
		
	for(int t=0; t<iter_in; t++) {
		
		outcontrol<<"Start"<<endl;
		for(int i=0; i<2; i++) {
			for(int j=0; j<100; j++) {
					if(L1[i][j]==-1) {
						outtraffic<<" .";
						outcontrol<<" .";
					}
					else {
						outtraffic<<L1[i][j];
						outcontrol<<L1[i][j];
					} 
				}
				outtraffic<<endl;
				outcontrol<<endl;
			}
		outtraffic<<endl;
		outcontrol<<endl;
		
		outadditional<<"At step: "<<t+1<<endl;
			
		//Overtaking
		
		if(s%2==1) {
		
			for(int i=0; i<2; i++) {
				for(int j=0; j<100; j++) {
					if(L1[i][j]!=-1) {
						L2[overtake(L1, i, j)][j]=L1[i][j];
					}
				}
			}
			
			for(int i=0; i<2; i++) {	
				for(int j=0; j<100; j++) {
					L1[i][j]=-1;
				}	
			}
			
			for(int i=0; i<2; i++) {
				for(int j=0; j<100; j++) {
					L1[i][j]=L2[i][j];
				}
			}
			
			for(int i=0; i<2; i++) {	
				for(int j=0; j<100; j++) {
					L2[i][j]=-1;
				}	
			}
			
			outcontrol<<"Overtaking"<<endl;
			
			for(int i=0; i<2; i++) {
				for(int j=0; j<100; j++) {
					if(L1[i][j]==-1) {
						outcontrol<<" .";
					}
					else {
						outcontrol<<L1[i][j];
					} 
				}
				outcontrol<<endl;
			}
			outcontrol<<endl;
		}
							
		//Acceleration
		
		for(int i=0; i<2; i++) {
			for(int j=0; j<100; j++) {
				if(L1[i][j]!=-1 && L1[i][j]<v_max) {
					L1[i][j]=L1[i][j]+acceleration(L1, i, j);
				}
			}
		}
		
		
		outcontrol<<"Acceleration"<<endl;
		
		for(int i=0; i<2; i++) {
				for(int j=0; j<100; j++) {
					if(L1[i][j]==-1) {
						outcontrol<<" .";
					}
					else {
						outcontrol<<L1[i][j];
					} 
				}
				outcontrol<<endl;
			}
			outcontrol<<endl;
		
		
		//Deceleration
		
		rapid_dec=0;
		
		for(int i=0; i<2; i++) {
			for(int j=0; j<100; j++) {
				if(L1[i][j]>0) {
					if(deceleration(L1, i, j)>1) {
						rapid_dec+=1;
					}
				}
			}	
		}
		
		outadditional<<"	Rapid deceleration = "<<rapid_dec<<endl;
		
		for(int i=0; i<2; i++) {
			for(int j=0; j<100; j++) {
				if(L1[i][j]>0) {
					L1[i][j]=L1[i][j]-deceleration(L1, i, j);
				}
			}	
		}
		
				
		outcontrol<<"Deceleration"<<endl;
		
		for(int i=0; i<2; i++) {
				for(int j=0; j<100; j++) {
					if(L1[i][j]==-1) {
						outcontrol<<" .";
					}
					else {
						outcontrol<<L1[i][j];
					} 
				}
				outcontrol<<endl;
			}
			outcontrol<<endl;
		
		//Randomization
		
		randomization(L1, p);
		
		outcontrol<<"Randomization"<<endl;
		
		for(int i=0; i<2; i++) {
				for(int j=0; j<100; j++) {
					if(L1[i][j]==-1) {
						outcontrol<<" .";
					}
					else {
						outcontrol<<L1[i][j];
					} 
				}
				outcontrol<<endl;
			}
			outcontrol<<endl;
		
		//Car motion
				
		for(int i=0; i<2; i++) {
			for(int j=0; j<100; j++) {
				if(L1[i][j]+j>99) {
					L1[i][j]=-1;
				}
				if(L1[i][j]!=-1) {
					L2[i][motion(L1, i, j)]=L1[i][j];
				}
			}
		}
		
		
		if(L2[0][0]==-1) {
			L2[0][0]=0;
		}
		
		if(L2[1][0]==-1) {
			L2[1][0]=0;
		}
		
		//Reset L1 & L2
		
		for(int i=0; i<2; i++) {
			for(int j=0; j<100; j++) {
				L1[i][j]=L2[i][j];	
			}
		}
		
		
		for(int i=0; i<2; i++) {	
			for(int j=0; j<100; j++) {
				L2[i][j]=-1;
			}	
		}
		
		//Outadditional
		
		vector<int> row;
		vector<int> column;
		
		row=rpos_jam(L1);
		column=cpos_jam(L1);
		total_n_jam+=num_jam(L1);
		
		outadditional<<" 	Density:"<<density_func(L1)<<endl;
		outadditional<<"	Number of Jams:"<<num_jam(L1)<<endl;
		
		for(unsigned int i=0; i<row.size(); i++) {
			outadditional<<"		Jam Position: "<<row[i]<<", "<<column[i]<<endl;
		}
		
		outadditional<<endl;
		
	}	
		g=s%2;
		table<<total_n_jam<<"   "<<density<<"   "<<p<<"   "<<g<<endl;
}

return 0;
}


```


Any help is much appreciated!

Thx!

---

### Post by PaulM1985 on 2009-11-18
I learned opengl quite recently and used these tutorials:

[http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup/home.php](http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup/home.php)

It is a video tutorial where a guy shows you what is on his screen, talks you through setting it up and then how to make graphics stuff.

I found it really useful since you are actually being shown how to do stuff rather than reading through loads of text and looking at pictures.  Also, some of the code is posted on there so you look through it and run it yourself.

Hope this is of some help.

Paul

EDIT
After reading the last post, I have noticed that this is kind of irrelevant.  I just looked at the original post and realised the date.  Sorry.

---

### Post by matyasfalvi on 2009-11-20
Thank you!

---

