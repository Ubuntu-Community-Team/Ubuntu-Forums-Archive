---
title: "[Challange] Fractals"
date: 2008-11-20
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-20
I got the idea for this challange from the Ulam Spirel one...I will be interested to see what everyone comes up with

I will have a vote for the winner at the end if there are enough entries

here is the wikipedia link for fractals: [http://en.wikipedia.org/wiki/Fractal](http://en.wikipedia.org/wiki/Fractal)

I advise using some type of form and drawing to it

THE CHALLANGE:

Make a program to create a Sierpinski Triangle Fractal to the iteration idicated by the user

EXTRA CREDIT:

Make the Koch Snowflake also avalible

Add a magnifier because fractals may get very detailed

magically doing this in a console app

---

### Post by jacensolo on 2008-11-20
I'll look into it... Keep this open for a couple of days.

---

### Post by jimi_hendrix on 2008-11-20
ill keep it open until it seems we have plenty of entries then i will put up the voting poll

---

### Post by mkrahmeh on 2008-11-20
> **jacensolo said:**
> I'll look into it... Keep this open for a couple of days.

a couple of days to decipher the jargon in the wiki page :)

---

### Post by jimi_hendrix on 2008-11-20
just throw squares on top of eachother in the pattern of the graphic on the left of the page

---

### Post by CptPicard on 2008-11-20
[http://ubuntuforums.org/showthread.php?t=730735&highlight=sierpinski](http://ubuntuforums.org/showthread.php?t=730735&highlight=sierpinski)

---

### Post by jimi_hendrix on 2008-11-20
.........................................

this is why i am not a next gen fan...

---

### Post by CptPicard on 2008-11-20
> **jimi_hendrix said:**
> 
this is why i am not a next gen fan...

Well, I didn't have to take the Enterprise back in time or anything to fetch that by the search function.. ;)

---

### Post by jimi_hendrix on 2008-11-20
well if it makes you happy you can make a koch snowflake

---

### Post by CptPicard on 2008-11-20
In my first year of university I once wrote a Mandelbrot renderer/zoomer.. I wonder if I still have it here somewhere...

[http://www.voittoporukka.fi/~eero/fracttest.html](http://www.voittoporukka.fi/~eero/fracttest.html)

Yeah, right there. Really crappy but hey, it was 1999.. :) you can really also see how doubles run out of precision pretty fast.

---

### Post by jimi_hendrix on 2008-11-20
new rule..cptpicard's score is multiplied by -1

---

### Post by Reiger on 2008-11-20
> **CptPicard said:**
> In my first year of university I once wrote a Mandelbrot renderer/zoomer.. So did I. But either I misread (quite possibly) or this thread/challenge is about Sierpinski with as an added bonus snowflakes by Koch....

---

### Post by jimi_hendrix on 2008-11-20
> **Reiger said:**
> So did I. But either I misread (quite possibly) or this thread/challenge is about Sierpinski with as an added bonus snowflakes by Koch....

correct...

---

### Post by Kilon on 2008-11-21
> **jimi_hendrix said:**
> correct...

Can we use internet reference for the math and maybe source code from similar things. I promise to change any code I get and not simply copy paste , the thing is that I am very crappy with maths but have no problem learning something. Sorry for asking , but I have never participated in a challenge like this before.  I am also new with Java and have no idea how JAVA2d works but I want to learn because I am planning to use it in the future.

Also let me take this oportunity and ask , is Java2d better , SDLJAVA or JOGL ? By better I mean , easier and faster in execution for 2d graphics.

---

### Post by samjh on 2008-11-21
JOGL is fastest, but Java2D is easiest.

---

### Post by jimi_hendrix on 2008-11-21
@Kilon...yes but dont copy and paste a whole program...and first try and find an algorithem without the code

---

### Post by Kilon on 2008-11-21
Thank you both, it is all crystal clear now. I promise I will put as much effort to this as I can and no mindless copies. The mathematics at first sight seem to make sense, so I will try to implement my own way of doing it. It  is a also an opportunity to learn Java2d.

---

### Post by skullmunky on 2008-11-22
Fractals are what got me into programming in the first place.  For most kids it's trying to write games; for me it was the mandelbrot set, in BASIC on the Apple II.

Seventh grade - the year I discovered Van Halen, girls, and iterated function systems over the complex number plane.

---

### Post by jimi_hendrix on 2008-11-23
i got these two programs in a PM from Skullmunky:

fractal.py
```
import random

def printout (image):
	for row in image:
		s=''
		for pixel in row:
			if pixel==0:
				c=' '
			elif pixel < 10:
				c='.'
			else:
				c='*'
			s=s+c
		print s
		
		
def plotPoint (x,y,image):
	w=len(image[0])
	h=len(image)
	
	c=int(w * x / 2)
	r=int(h * y)
	
	image[r][c]=image[r][c]+1

###################################

width=200
height=80

maxIterations = int(raw_input("how many iterations would you like? "))


fractalImage=[]
for y in range(0,height):
	fractalImage.append([])
	for x in range (0,width):
		fractalImage[y].append(0)
	
x=0.0
y=0.0

for i in range(0,maxIterations):
	r=random.randint(0,2)
	if r==0:
		x=x/2
		y=y/2
	elif r==1:
		x=x/2+.5
		y=y/2+.5
	elif r==2:
		x=x/2+1
		y=y/2
	
	plotPoint(x,y,fractalImage)
	
printout(fractalImage)
```

fractal.pde

```

/ in Processing
// because I'll take any excuse to make fractals

float x=0;
float y=0;

void setup ()
{
  size(800,800);
  background(0);
  stroke(255);
}
void draw ()
{
  int r;
  point(x,y);
  
  r=int(random(3));
  
  if (r==0)
  {
     x=x * .5;
     y=y * .5; 
  }
  else if (r==1)
  {
   x=x * .5 + width/4;
   y=y * .5 + height/4;
  }
  else if (r==2)
  {
    x=x * .5 + width/2;
    y=y * .5;
  }
}

```

i did not test the second one because i have not installed a processing compiler yet

---

### Post by skullmunky on 2008-11-23
oh, sorry, i didn't know if we were supposed to post entries back to the thread or not ... 

you can download Processing from Processing.org ... It's essentially an IDE and a base Java applet and application class with a ton of functionality wrapped up in a tidy manner.  I felt bad for "cheating" with it 'cause it's so ridiculously easy to use. :)

---

### Post by jimi_hendrix on 2008-11-23
lol...i like the console app you did...i would have had no clue how to do that

---

### Post by Lux Perpetua on 2008-11-23
I've written several Sierpinski triangle programs over the years. I wrote the main part of the following algorithm earlier this year (after I posted my Sierpinski challenge here), but I wrote a new coloring algorithm yesterday. 

Code: ```
%!PS-Adobe-3.0 EPSF-3.0
%%BoundingBox: 0 0 612 544

% Usage:
%   gs -sDEVICE=x11alpha -dEPSCrop [options] sierp_color.eps
%
% Options:
%   -dIterations=i (default: i=10)    specify number of iterations
%   -dBase=b       (default: i=0.8)   tune color tinting
%   -dVerbose      (default: false)   show progress on console
%
% Other suggested gs flags:
%    -r144 -dBATCH

9 dict begin

/default { 1 index where { pop pop pop } { def } ifelse } bind def

/Iterations 10 default
/Base 0.8 default
/Verbose false default

/repos [ { } {exch 1 sub exch} {1 sub} ] bind def

/trans [ [1 0] [0 1] [-1 1] [-1 0] [0 -1] [1 -1] ] def

% interface:
%   iterations draw_tri sierpinski -
%
% iterations is self-explanatory; draw_tri should be a subroutine:
%   x y draw_tri -
% that draws (or more generally processes) the triangle whose lower
% left endpoint is x y and has sides of length 1
/sierpinski {
    6 dict begin
    /draw_tri exch def
    /it exch def
    /p Base it exp Base Iterations exp sub def

    /tint { 1 p sub mul p add } bind def

    /find_color {
        /b exch 1 3 div add 2 it exp div def
        /a exch 1 3 div add 2 it exp div def
        1 a sub	tint   1 b sub tint   a b add tint
        setrgbcolor
    } bind def
    
    0 0 0
    1 1 3 it exp {
        % x y n k
        % (draw this triangle)
        4 1 roll 3 copy
        2 idiv repos exch get exec
            2 copy find_color
        draw_tri fill

        % k x y n
        % (move the current point)
        dup 4 1 roll
        trans exch get aload pop exch
        4 1 roll add 3 1 roll add exch

        % k n x' y'
        % (rotate the current vector)
        3 -1 roll 4 -1 roll
        dup 2 mod exch
        {
            dup 3 mod 0 ne { exit } if
            3 idiv exch 1 add exch
        } loop
        3 mod add 2 mod 2 mul neg 7 add add 6 mod
    } for
    pop pop pop
    end
} bind def

50 50 translate 512 512 scale [1 0 0.5 0.5 3 sqrt mul 0 0] concat

Verbose {
    /buffer 256 string def
    /stdout (%stdout) (w) file def
} if

0 1 Iterations {
    Verbose {
        stdout (Iteration ) writestring
        dup buffer cvs stdout exch writestring
        stdout (...\n) writestring
        flush
    } if


    dup Iterations lt {
        {
            % This looks more complicated than it needs to
            % be (in theory, we should draw a triangle, not
            % a weirdly shaped hexagon), but I think something
            % like this is necessary to ensure that the output
            % is antialiased properly.
        
            exch 0.5 add exch moveto
            0.125 0.25 rlineto
            -0.125 0.25 rlineto
            -0.25 0.125 rlineto
            -0.25 -0.125 rlineto
            0.25 -0.375 rlineto
            closepath
        }
    } {
        {
            moveto
            1 0 rlineto
            -1 1 rlineto
            closepath
        }
    } ifelse
    
    sierpinski
    0.5 0.5 scale
} for

end
```Save it to a file, say sierp_color.eps. You'll need a PostScript interpreter like gs-gpl from the repositories. Then run the program using, say, ```
gs -sDEVICE=x11alpha -dEPSCrop -dBATCH -r144 sierp_color.eps
```There are other options, documented in the source code comments, that you can put before sierp_color.ps in the command line to tweak certain parts of the behavior. You probably shouldn't change the -dEPSCrop or -dBATCH options, but omitting the -r144 or changing 144 to a different number will change the resolution. The program should produce good output at any resolution; if it doesn't, that's a bug. ;-)

I'm attaching example output generated using ```
gs -sDEVICE=png16m -dGraphicsAlphaBits=4 -sOutputFile=example.png -dEPSCrop -dBATCH -dNOPAUSE -r36 sierp_color.eps
```

---

### Post by Kilon on 2008-11-24
> **skullmunky said:**
> oh, sorry, i didn't know if we were supposed to post entries back to the thread or not ... 

you can download Processing from Processing.org ... It's essentially an IDE and a base Java applet and application class with a ton of functionality wrapped up in a tidy manner.  I felt bad for "cheating" with it 'cause it's so ridiculously easy to use. :)

Thank you for bringing this to my attention Processing looks quite interesting , too bad it does not work very well with Swing , but I will give it a try. The IDE is also pretty straightforward and it is ultra cool that generates executable files for MACOS,WINDOWS,UBUNTU and the Java source code . Very nice. Also very simple synthax , much simpler than JAVA.

---

### Post by jimi_hendrix on 2008-11-24
@lux...what language is that?

---

### Post by Majorix on 2008-11-24
> **jimi_hendrix said:**
> @lux...what language is that?

I also wonder that, but it certainly is confusing :confused:

---

### Post by jimi_hendrix on 2008-11-24
i want to know because there is a picture with some code fragments in the background in my mathbook that look like they are from that language

---

### Post by pp. on 2008-11-24
I would guess that it's PostScript.

---

### Post by Lux Perpetua on 2008-11-24
My program is indeed PostScript. I'm sorry the code is confusing (and I agree). I considered rewriting the procedure "sierpinski" to be more understandable, but I was reluctant to risk breaking it. That's probably the bottleneck for understanding my code (if you're already reasonably familiar with PostScript); I think the rest is pretty standard. 

It occurred to me after writing my last post that there's an easier way to run my program: you can just open the file in evince (document viewer). It should take care of everything. As far as I know, you can't specify command line options this way, but I tried to make the defaults as good as possible, so it should be fine. 

skullmunky, I'm interested by your second program. How should I run it? (I've located processing.org and a big tarball called processing-0157.tgz. Now what?)

---

### Post by Wybiral on 2008-11-25
Here's mine from the last one: [http://ubuntuforums.org/showpost.php?p=4558021&postcount=3](http://ubuntuforums.org/showpost.php?p=4558021&postcount=3)

---

### Post by skullmunky on 2008-11-27
@Lux: Love the postscript program!  Awesome!  Haven't looked at that language in ages.

To get started with processing: Actually, they've just made it to a 1.0 release, after about 3 years.  So if you want you might download that; but processing-0157 will work fine too.

1. extract it
2. you'll see a shell script called "processing".  Run that.
3. a weird little minimalist Java IDE opens.  To make sure it's working, go to File->Examples and choose one of the example programs (they're called "Sketches").  Click the Play button to run the program, or go to Sketch->Run or Sketch->Present.
4. to run mine, open a new program, paste in the code, and run it.

---

### Post by Lux Perpetua on 2008-12-02
Thanks, skullmunky. That worked perfectly. 

All right, Koch snowflake time. I haven't done one of these in a while. I wrote these two very different nonrecursive PostScript programs yesterday. 

The first is similar to skullmunky's program and uses randomness to approximate a filled Koch snowflake:

**koch_rand.eps**
```
%!PS-Adobe-3.0 EPSF-3.0
%%BoundingBox: 0 0 612 612

% Usage:
%   gs -sDEVICE=x11alpha -dEPSCrop [options] koch_rand.eps
%
% Options:
%   -dPoints=p                (default: 1000000)  number of points
%   -dPointScale=s            (default: 0.5)      size of points
%   -sMode=[uniform|variable] (default: uniform)  choose version
%
% Other suggested gs flags:
%   -dBATCH

9 dict begin

/default { 1 index where { pop pop pop } { def } ifelse } bind def

/Mode (uniform) default

/uniform { } def
/variable { 2 sub } def

/Points 1000000 default
/PointScale 0.5 default

/pointrad PointScale Points sqrt div def

/draw_point {
    2 copy exch pointrad add exch moveto
    pointrad 0 360 arc fill
} bind def

/t [
    [1 3 div 0 2 copy exch 0 2 3 div]
    5 {
        dup 60 matrix rotate
        dup concatmatrix
    } repeat
    
    1 3 sqrt div dup matrix scale 30 matrix rotate dup concatmatrix
    dup
    dup
] def

306 dup translate
256 dup scale

0 0
Points 1 sub {
    2 copy draw_point
    t rand 9 Mode cvx exec mod get transform
} repeat
draw_point

end
```It's based on the observation that a filled Koch snowflake can be divided into seven smaller versions of itself (the center one being larger  than the others and rotated by 30 degrees). The default options will produce a uniformly filled snowflake: ```
gs -sDEVICE=x11alpha -dBATCH -dEPSCrop koch_rand.eps
```To help visualize the decomposition into smaller snowflakes (or just produce a cool picture), use: ```
gs -sDEVICE=x11alpha -dBATCH -dEPSCrop -sMode=variable koch_rand.eps
```If it takes too long, add the option -dPoints=p, where p is a number less than 1000000 (the default). On the other hand, if you want a better picture and don't mind waiting, use more points. 

I'm attaching example output using -sMode=variable.

Here's the second program, which is similar to my Sierpinski triangle program but much simpler. It also produces a filled snowflake. 

**koch_arith.eps**
```
%!PS-Adobe-3.0 EPSF-3.0
%%BoundingBox: 0 0 612 692

% Usage:
%   gs -sDEVICE=x11alpha -dEPSCrop [options] koch_arith.eps
%
% Options:
%   -dIterations=i (default: i=7)  specify number of iterations
%
% Other suggested gs flags:
%   -dBATCH

3 dict begin

/default { 1 index where { pop pop pop } { def } ifelse } bind def

/Iterations 7 default

/trans [ [1 0] [0 1] [-1 1] [-1 0] [0 -1] [1 -1] ] def

306 50 moveto

50 50 translate 512 512 scale [1 0 0.5 0.5 3 sqrt mul 0 0] concat
1 3 Iterations exp div dup scale

2
3 {
    1 1 4 Iterations exp {
        trans 2 index get aload pop rlineto
        {
            dup 4 mod dup 0 eq { pop 4 idiv } { exch pop exit } ifelse
        } loop
        2 mod 0 eq { 4 } { 1 } ifelse add 6 mod
    } for
    3 add 6 mod
} repeat
pop

closepath fill

end
```The default options should work fine here: ```
gs -sDEVICE=x11alpha -dBATCH -dEPSCrop koch_arith.eps
```

---

### Post by jimi_hendrix on 2008-12-02
very nice

---

### Post by brian77095 on 2008-12-02
This as been a very informative thread thanks Jim for starting it and everyone else for contributing!!

I miss the Challenges another use to write...:(

---

### Post by jimi_hendrix on 2008-12-02
ya...and i was tired of seeing challanges like "get the 2,000 didgit in the  15,000,00 iteration of pie, then figure out how many composite numbers it forms and use that information to calculate the square root of x" (over exagurated, yes) so i thought we could get a little graphical

---

