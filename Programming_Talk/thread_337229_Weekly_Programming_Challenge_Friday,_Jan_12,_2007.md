---
title: "Weekly Programming Challenge: Friday, Jan 12, 2007"
date: 2007-01-12
forum: Programming Talk
---

### Post by jblebrun on 2007-01-12
This week's programming challenge is meant to encourage a little bit of creativity. 

The challenge is to generate a Mandelbrot fractal using ONLY console output. How you chose to do it exactly is up to you, but the final result must be generated using standard 8-bit ASCII characters.  Anything that will display on either ANSI or VT102 style terminals 80 characters wide is acceptable.

If you are not familiar with Mandelbrot fractals, just do a google search. You'll recognize the image immediately. It's VERY easy to generate the fractal, even though it looks very complicated. You can find the algorithm in lots of places. 
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/2/21/Mandel_zoom_00_mandelbrot_set.jpg/322px-Mandel_zoom_00_mandelbrot_set.jpg[/IMG]

What I am looking for is creativity in the output style! 

I'm happy to post more hints and suggestions, if requested!

---

### Post by pizzutz on 2007-01-12
You know these weekly challenges have come a long way from "Write a program that inputs one string and outputs it backward" and "Write a program to fill in a 10x10 multiplication table"

Well, I think it sounds harder than it is, although I thought that last week, and never finished.

We shall see :)   good one, though.

---

### Post by Wybiral on 2007-01-12
I tried to do the console thing... I have to be honest, the console just isn't big enough to display a fractal... Maybe it's just me.

I did write one that creates a file though... Compile this with "g++ thisProgram.cpp" and it will create the file "output"

Open up output and view it with a VERY VERY tiny font (I used Courier New, Size 3, Bold) Basically any font that is visible at a SUPER tiny size (it doesn't have to be readable, just visible).

Anyway, here's the program...

```

#include <fstream>

using namespace std;

char map[4] = {' ', '.' , '*', '#'};

int main(){
	ofstream output("output");
	int width=640;
	int height=480;
	int value;
	float realMin = -0.10;
	float realMax =  0.05;
	float imgMin  = -0.10;
	float imgMax  =  0.05;
	float realWidth = realMax - realMin;
	float imgHeight = imgMax  - imgMin;
	float cImg  =  0.46;
	float cReal = -0.62;
	float realPart, imgPart, prevItReal, prevItImg, itReal, itImg;
	int maxIterations = 100;
	for(int y = 0; y<height; y++){
		for(int x = 0; x<width; x++){
			realPart = realMin + realWidth * ((float)x / width);
			imgPart = imgMin + imgHeight * ((float)y / height);
			prevItReal = realPart;
			prevItImg = imgPart;
			for(int c = 0; c<maxIterations; c++){
				value = c;
				itReal = prevItReal * prevItReal - prevItImg * prevItImg + cReal;
				itImg = 1.99 * prevItReal * prevItImg + cImg;
				if(itReal*itReal + itImg*itImg > 4){break;}
				prevItReal = itReal;
				prevItImg = itImg;
			}
			output << map[value/30];
		}
		output << endl;
	}
	output.close();
}

```

BTW, this is a julia fractial...

---

### Post by jblebrun on 2007-01-12
You can easily display a recognizable Mandelbrot set on the console... I wrote a solution myself before posting the problem. You need to scale the image to fit in the available space of the terminal that the user is using. 

By the way, I asked for the Mandelbrot set, not the Julia set... so you should modify your solution to fit the request in the problem.

---

### Post by Wybiral on 2007-01-12
I mean this in a non-offensive way... But with rules this specific and constrictive, it doesn't really sound fun or educational to me.

Now, a "text based fractal" would be cool, and would allow for varying types of entries and and algorithms...

But "MUST BE TERMINAL AND MANDELBROT" is pretty constrictive and all it teaches people is the Mandelbrot algorithm.

This is, of course, just my opinion.

---

### Post by jblebrun on 2007-01-12
Wybiral, I ran your program, nice output. You can make very trivial changes to display properly on the console. You should also make a similar trivial change to display the *entire* interesting part of the Julia set. You have zoomed in on a part of it.

And finally, change your code to display the Mandelbrot set, instead. :-)

---

### Post by jblebrun on 2007-01-12
> **Wybiral said:**
> I mean this in a non-offensive way... But with rules this specific and constrictive, it doesn't really sound fun or educational to me.

Now, a "text based fractal" would be cool, and would allow for varying types of entries and and algorithms...

But "MUST BE TERMINAL AND MANDELBROT" is pretty constrictive and all it teaches people is the Mandelbrot algorithm.

This is, of course, just my opinion.

I'll accept criticism about the lack of creativity when you've properly solved the challenge. And even your solution done properly would leave room for improvement of the display.

This challenge will help people explored methods for displaying "graphical" things in the console. So the challenge teaches more than just the Mandelbrot algorithm. I chose the Mandelbrot fractal specifically because I'm most interested in creative output displays, so if each entry shows the same thing, then there is a consistent basis for comparison. I'm not sure how a "text based fractal" is different from something displayed on the console, unless you want to allow variable-width fonts, as well? If you want to write a program that generates all kinds of different fractals, then feel free, as long as one of the options is the entire view of the interesting part of the Mandelbrot set. :-)

---

### Post by Wybiral on 2007-01-12
```

#include <math.h>
#include <iostream>

#define width  80
#define height 24

using namespace std;

int main(){
	int n;
	float xf=25.00;
	float yf= 8.00;

	float zr, zi, zr0, rX, rY;
	for(int y=0; y < height; y++){

		for(int x=0; x < width; x++){

        rX=-2.2+x/xf;

        rY= 1.5-y/yf;

        n=0; zr=0; zi=0;

        while ((zr*zr)+(zi*zi)<=4 && n!=16){

            zr0=(zr*zr)-(zi*zi)+rX;

            zi=2*zr*zi+rY;

            zr=zr0;

            n++;

        }
		cout << "\033[" << 43+(int)(cos(n)*4) << "m ";
		}
		cout << endl;

	}
	cout << "\033[0m";

}

```


Ok... Now that I've written a valid solution (it may not be perfect, but it works and is what you said)...

What I mean by text based is... Almost every language can write to a file, and since files allow for larger viewports, why not be able to save the image to a file instead of the terminal (I hope everyone following these challenges can write to the terminal by now!)

And... Even the Mandelbrot set is different from image to image (what with zoom and color algorithm differences)... so why not other fractals?

But, it's cool. I submitted two ways of doing a text based fractal, so I am happy.

Once again, compile it with "g++ thisProgram.cpp" execute with "./a.out"

This one uses a 80x24 terminal to display (colors must be on)

This one is similar, but it's animated to zoom in...

```

#include <iostream>

#define width  80
#define height 24

using namespace std;

int main(){
	int n;
	float yf = 8.0;
	float zr, zi, zr0, rX, rY;
	for(float xf = 25.00; xf<500000.00; xf*=1.02){
		cout << endl; yf *=1.02;
		for(unsigned char y=0; y < height; y++){

			for(unsigned char x=0; x < width; x++){

        rX=-1.4017+x/xf;

        rY=((yf*10+yf)/(yf*yf))-y/yf;

        n=0; zr=0; zi=0;

        while (zr*zr+zi*zi<=4 && n<140){

            zr0=(zr*zr)-(zi*zi)+rX;

            zi=2*zr*zi+rY;

            zr=zr0;
						n++;

        } cout << "\033[" << 47-(n/20) << "m ";
			}

		} usleep(50000);
	} cout << "\033[0m";
}

```

(looks best about 10 feet away from the monitor)

---

### Post by jblebrun on 2007-01-12
> 

Ok... Now that I've written a valid solution (it may not be perfect, but it works and is what you said)...

What I mean by text based is... Almost every language can write to a file, and since files allow for larger viewports, why not be able to save the image to a file instead of the terminal (I hope everyone following these challenges can write to the terminal by now!)

And... Even the Mandelbrot set is different from image to image (what with zoom and color algorithm differences)... so why not other fractals?

But, it's cool. I submitted two ways of doing a text based fractal, so I am happy.

Once again, compile it with "g++ thisProgram.cpp" execute with "./a.out"

This one uses a 80x24 terminal to display (colors must be on)

Sure, files allow for larger viewports, but I want something that shows me something cool on my console screen, not in a file. I want to be able to run the submitted programs over a network connection to a single board computer and see a result. If I was going to allow people to write to arbitrary sizes, I might as well just make it a challenge to display graphical output.  Furthermore, for base cases, saving to a file is EXACTLY the same as writing to the console (stdout is just a file, in Linux). So allowing people to "write to a file" would be a trivial modification.

Plus, when you write to a file, you can't do cool ANSI tricks like the ones you do in your second submission. You also could use, for example, ncurses. 

People know how to write to a terminal, but this isn't just "writing to the terminal" it's displaying structured mathematical data in a meaningful way on the terminal. That is less trivial. 

The Mandelbrot set will never look different shape wise when you're displaying the entire set within viewable range (i.e, entirely zoomed out). That's why I specified that. As for colors, that's one avenue for creativity that I was talking about. 

By the way, it's inaccurate to say that the Mandelbrot set is "different" at different zoom levels. I know what you were trying to say, but it's still the same Mandelbrot set, you're just looking at it differently. There's only one set. 

I liked the direction in which you were headed with your first submission, better (using different ascii characters to get a shading effect). You should make a new coloring algorithm that combines the ANSI coloring and the different ascii characters.

---

### Post by xtacocorex on 2007-01-12
I'm working on my submission, but FORTRAN won't let me output color to the terminal. :(

So, unless I figure that out, I'll be using C++.

---

### Post by tomchuk on 2007-01-12
These are not mine (I'm not nearly insane or drunk enough to be writing obfuscated perl), but I had them bookmarked from a while ago:
```

#!/usr/bin/perl
$"=q/#j%u*sXtQ Oa^n+o-t.hPe;rK 'p]eErFl,DhGa/;sub b{my($w,$x,$v)=@_;while(($y=
$w*$w)+($z=$x*$x)<4&&(++$v<9)){$x=2*$w*$x+$_[1];$w=$y-$z+$_[0];}return$v;}$".=
q/.cWk,e(r)/;@@=split/[^a-z ]/,$";@,=split/[a-z ]+/,$";foreach(0..3119){print
$,[b(($_%78-40)/20,(int($_/78)-19)/10)].(($_%78^77)?"":" $@[int($_/78)]\n");}

```
```

#!/usr/bin/perl
sub b{my($w,$x,$v)=@_;while(($y=$w*$w)+($z=$x*$x)<4&&(++$v<9)){$x=2*$w*$x+$_[1
];$w=$y-$z+$_[0];}return$v+0;}foreach(0..3119){print"\033[4".b(($_%78-40)/20,(
int($_/78)-19)/10)."m ".(($_%78^77)?"":" \033[0m\n");}

```

---

### Post by Wybiral on 2007-01-12
I added an animated version to my second submission.

And, off subject, this is an SDL+OpenGL fractal I wrote...

I call it "Your drug on brains"

```

#include <math.h>
#include <GL/gl.h>
#include <SDL/SDL.h>

#define width  640
#define height 480 

	// Wait for event...
void waitForEvent()
{
	SDL_Event event;
	while(true)
	{
		while(SDL_PollEvent(&event))
		{
			switch(event.type)
			{
				case SDL_QUIT: SDL_Quit(); exit(0); break;
				case SDL_KEYDOWN: if(event.key.keysym.sym == SDLK_ESCAPE){ SDL_Quit(); exit(0); }
			}
		}
	}
}

void mainLoop()
{
	int c;
	float realPart;
	float imgPart;
	float itReal, itImg;
	float cimg, creal;
	float prevItReal, prevItImg;
	
	// Render fractal
	for(int y = 0; y<height; y++)
	{
		glBegin(GL_POINTS);
		imgPart = -0.0006*y;
		for(int x = 0; x<width; x++)
		{
			realPart = -0.0003*x;
			prevItReal = realPart;
			prevItImg = imgPart;
			for(c = 0; c<80; c++)
			{
				itReal = prevItReal*prevItReal - prevItImg*prevItImg -.62;
				itImg = 2*prevItReal*prevItImg + .46;
				if(itReal*itReal+itImg/itImg > 4){ break; }
				prevItReal = itReal;
				prevItImg = itImg;
			}
			glColor3f(cos(c+x*.01), cos(c+y*.01), sin(c+x*.01));
			glVertex2i(x, y);
		} glEnd(); SDL_GL_SwapBuffers();
	}
	waitForEvent();
}

int main()
{
	// Initialize SDL
	const SDL_VideoInfo* info = NULL;
	SDL_Init(SDL_INIT_VIDEO);
	info = SDL_GetVideoInfo();	
	int vidFlags = SDL_OPENGL | SDL_GL_DOUBLEBUFFER;
	if (info->hw_available){vidFlags |= SDL_HWSURFACE;}
	else{vidFlags |= SDL_SWSURFACE;}
	SDL_SetVideoMode(width, height, info->vfmt->BitsPerPixel, vidFlags);
	// Setup OpenGL for 2d
	glMatrixMode(GL_PROJECTION);
	glLoadIdentity();
	glOrtho(0,width, height,0,-1,1);
	glMatrixMode(GL_MODELVIEW);
	glLoadIdentity();
	glDisable(GL_DEPTH_TEST);
	// Call main loop
	mainLoop();
}

```

Compile it with "g++ thisProgram.cpp -lSDL -lGL"

(you need the mesa dev files and the sdl dev files)

---

### Post by jblebrun on 2007-01-13
> **Wybiral said:**
> I added an animated version to my second submission.



Very cool! Although, by default, it zooms in on a completely black region of the fractal ;-)

---

### Post by lloyd mcclendon on 2007-01-13
sounds to me like someone got this for a homework assignment and has found a clever way to get other people to do it for them.

---

### Post by jblebrun on 2007-01-13
> **lloyd mcclendon said:**
> sounds to me like someone got this for a homework assignment and has found a clever way to get other people to do it for them.

I'd written a more verbose answer, but I've decided not to feed the troll.

Let it suffice to say that it's certainly not my "homework", and I've not had a "homework" assignment in a number of years now.

---

### Post by johnnymac on 2007-01-14
Here's my simple solution...I implemented as an XML-RPC solution using perl - cause I was bored....some of the stuff inside I found (cause I don't know much about the fractal algorithm)...

manglebrot-xml-rpc-messenger.pl
(use this to send the request to the server)
example:  ./mandlebrot-xml-rpc-messenger.pl --method=showMandlebrot --params="79:30:16:-2.0:1.0:-1.0:1.0" --server=localhost
(notice the "colon delimiters in params" they are needed but you can use your own numbers)
```

#!/usr/bin/perl
#example:  ./mandlebrot-xml-rpc-messenger.pl --method=showMandlebrot --params="79:30:16:-2.0:1.0:-1.0:1.0" --server=localhost
use strict;
use Frontier::Client;
use Getopt::Long;
my ($method,$params,$server,$server_url);

my $results = GetOptions("method=s" => \$method,
                                          "params=s" => \$params,
                                          "server=s" => \$server);

if(!defined $method || !defined $params || !defined $server){die "Need method, params, and server passed\n";}

$server_url = 'http://' . $server . ':8080/RPC2';
$server = Frontier::Client->new(url=>$server_url);

if($method eq 'showMandlebrot')
{
      my $result = $server->call('mb.showMandlebrot',$params);
}

```

Here's the server:
mandlebrot-xml-rpc-server.pl
```

#!/usr/bin/perl -w
use strict;
use Frontier::Daemon;

#setup method defs for daemon
my $methods = {'mb.showMandlebrot' =>\&showMandlebrot};

system("clear");
print "Sure wish someone would send me some work...\n";
Frontier::Daemon->new(LocalPort => 8080, methods => $methods) or die "Couldn't Start HTTP server: $!";

sub showMandlebrot
{
      my($params,@paramArray,$col,$lines,$miter,$min,$max,$minl,$maxl,
            @chars,$loop1counter,$loop2counter,$loop3counter);
      system("clear");
      $params = shift;
      @paramArray = split(":",$params);
      if(scalar(@paramArray) != 7){die "Ooops, you didn't specify the right number of parameters";}
      $col=$paramArray[0];
      $lines=$paramArray[1];
      $miter=$paramArray[2];
      $min=$paramArray[3];
      $max=$paramArray[4];
      $minl=$paramArray[5];
      $maxl=$paramArray[6];

      @chars=(' ','.',',','-',':','/','=','C','O','D','E','M','O','N','K','E','Y');

      for($loop1counter=$minl;$loop1counter<=$maxl;$loop1counter+=($maxl-$minl)/$lines)
      { 
            for($loop2counter=$min;$loop2counter<=$max;$loop2counter+=($max-$min)/$col)
            {
                  my $zr=$loop2counter; 
                  my $zi=$loop1counter;
                  for($loop3counter=0;$loop3counter<$miter;$loop3counter++)
                  { 
                        my $a=$zr*$zr; 
                        my $b=$zi*$zi;
                        if($a+$b>4.0) { last; }
                        $zi=2*$zr*$zi+$loop1counter; $zr=$a-$b+$loop2counter;                        
                  }                  
                  print $chars[$loop3counter];
            }
            print "\n";
      } 
}


```

Anyway - just some fun - but pass whatever params you want and see what you get....

---

### Post by Biggus on 2007-01-14
> **jblebrun said:**
> I'd written a more verbose answer, but I've decided not to feed the troll.


Maybe there is more to this than meets the eye, but it doesn't look as if lloyd mcclendon was trolling to me.

More likely they are simply attempting to interject a little bit of humour into a topic which can be somewhat dry?

---

### Post by jblebrun on 2007-01-14
> **Biggus said:**
> Maybe there is more to this than meets the eye, but it doesn't look as if lloyd mcclendon was trolling to me.

More likely they are simply attempting to interject a little bit of humour into a topic which can be somewhat dry?

It seemed more like an attack of character, than a joke. If I'd seen something that indicated that the poster was actually joking (like an appropriate emoticon), then I wouldn't have interpreted the post in that way.

And if it *was* an attempt at humor, it simply wasn't very funny ;-)

---

### Post by eteran on 2007-01-15
lloyd mcclendons comment looks for me like kind of trolling also.
I for instance appreciate the challenges. If you don't, you're free to ignore them.
P.S. I will try to solve the challenge later on. Just haven't found time yet :(

---

### Post by jblebrun on 2007-01-16
> **johnnymac said:**
> Here's my simple solution...I implemented as an XML-RPC solution using perl - cause I was bored....some of the stuff inside I found (cause I don't know much about the fractal algorithm)...
 
...

Anyway - just some fun - but pass whatever params you want and see what you get....


Hey, cool submission! I noticed when I ran it that the fractal is output on the server. I'm not familiar with the RPC API that you're using, but I wonder, would it be a trivial change to allow the output to appear at the client, rather than the server?

But anyway, I really like this submission!

---

### Post by &lt;mawe&gt; on 2007-01-16
Ok, here are a Lisp and a Haskell version (they are not mine. While I'm currently trying to learn Haskell, I'm not that good right now):
```
(loop for y from -1 to 1.1 by 0.1 do
      (loop for x from -2 to 1 by 0.04 do
            (let* ((c 126)
                   (z (complex x y))
                   (a z))
              (loop while (< (abs
                               (setq z (+ (* z z) a)))
                             2)
                    while (> (decf c) 32))
              (princ (code-char c))))
      (format t "~%"))
```

```
import Complex
import Char

main = putStrLn $ unlines [ mrow y | y <- [-1,-0.9..1] ]
  where mrow y = [ mchr (x :+ y) | x <- [-2,-1.96..1] ]
             mchr a = chr . (126-) . length
                            . takeWhile ((<2).magnitude) . take 94
                           $ iterate (\z -> z*z + a) a
```

---

### Post by Peepsalot on 2007-01-16
```

sudo apt-get install xaos
xaos -driver aa

```
:p

Hehe, i might do a real submission later if I have some free time.

---

### Post by johnnymac on 2007-01-16
No - it would be fairly easy.  You could have the server "randomly" generate the required parameters and return those to the calling system - then display those using the algorithm.

The RPC module for perl Frontier::Daemon and Frontier::Client are very easy to implement - and it's just as easy to do with C++, Python, etc.

J

---

### Post by jblebrun on 2007-01-16
> **johnnymac said:**
> No - it would be fairly easy.  You could have the server "randomly" generate the required parameters and return those to the calling system - then display those using the algorithm.

The RPC module for perl Frontier::Daemon and Frontier::Client are very easy to implement - and it's just as easy to do with C++, Python, etc.

J

Well, I was thinking more along the lines of having the server do all the computation and just return the result (the ASCII characters) to the client. That is the point of RPC in many cases--to have a resource-rich server do the "hard" work and then just return the result to the client.

---

### Post by jblebrun on 2007-01-16
> **Peepsalot said:**
> ```

sudo apt-get install xaos
xaos -driver aa

```
:p

Hehe, i might do a real submission later if I have some free time.

LOL. Well, that's a nice reference image, in any case!

---

### Post by Lux Perpetua on 2007-01-19
FWIW, this was the first weekly programming challenge that actually grabbed my interest. To actually contribute something to the discussion, I wanted to do it properly, i. e., make the most out of the character set. In theory, you could manually examine the entire character set and work with it that way, but that isn't acceptable if you think you might change the font to something drastically different and still have an optimized picture, so you'd really want to be able to extract information programmatically from a font file. Needless to say, I didn't have enough time to implement this. If only I could, given a bitmap (monospaced) font, "render" each of its characters into an array of booleans:

```
[FONT="Courier New"]bool characters[256][width][height];[/FONT]
```

I know how to do the rest.

---

