---
title: "What are your bad programming habits?"
date: 2009-08-30
forum: Programming Talk
---

### Post by pepperphd on 2009-08-30
I'll start.  Some of my identifiably bad habits while programming are:

-Using code that just works instead of code that both works and looks like it works.
-Lack of planning.  Just fire up vim and start coding.

---

### Post by CptPicard on 2009-08-30
> **pepperphd said:**
> 
-Lack of planning.  Just fire up vim and start coding.

Hey, exploratory hacking can be fun. Leave the UML diagrams to the corporate code monkeys. :)

---

### Post by credobyte on 2009-08-30
> **pepperphd said:**
> 
-Using code that just works instead of code that both works and looks like it works.

Any examples of [COLOR=RoyalBlue]code that works but doesn't look like it should[/COLOR] ( except bugs ) ?

---

### Post by RocketRanger on 2009-08-30
My top three:
- Lack of documentation/planning before starting to code.
- Not taking breaks to clear my head when coding.
- Sometimes using too cryptic acronyms for variable names.

Even though admitting these things are half the battle I have no idea how to proceed from here...

---

### Post by JordyD on 2009-08-30
- No planning
- Not enough testing (sometimes)

---

### Post by Mirge on 2009-08-30
Lack of documentation would be my biggest. I put in plenty of comments, they just could be worded better sometimes.. : ) ~

---

### Post by pepperphd on 2009-08-30
> **credobyte said:**
> Any examples of [COLOR=RoyalBlue]code that works but doesn't look like it should[/COLOR] ( except bugs ) ?

What you quoted is poorly worded. I should have said ' code that works but isn't what many would consider semantically correct.

---

### Post by Can+~ on 2009-08-30
> **CptPicard said:**
> Hey, exploratory hacking can be fun. Leave the UML diagrams to the corporate code monkeys. :)

I have the opposite "bad habit". I can't write a single line of code without thinking out the whole problem. (Not necessarily with UML diagrams, but having a rough idea of everything)

Many times I just want to do *exploratory hacking*, but as soon as I start coding, there's a little thing on the back of my head that says  "you still don't know how to solve problem ______ that will come up later!".

---

### Post by nrs on 2009-08-30
I write a lot of code that is used to test a hypothesis or whatever but somehow manages to become permanent. Actually, it becomes permanent because it (mostly) works and I'm too lazy to figure out "proper" way to structure things. I abuse globals, etc. I'm more disciplined when working with stuff other people use. 

Shameful example: 
I can't remember how this all works, but goes something like: isolateObject performs a recursive flood fill operation on _PIxels creating a list of end points on each line (used for hit detection later on: i.e, if(x >= endpoint.left and x <= endpoint.right and y == endpoint.line), it's in that object) and operates on _BoundaryLayer which is a blanked array with the dimensions of the image, filling the area that corresponds to flooded area on _Pixels with 1's. Back in createObject it takes _BoundaryLayer and basically if pixel _x is 1 and there are 1's to the N,W,E,S it sets it to 2. this basically makes the inside of the blob 2 and outer edge 1. traceObject takes _BoundaryLayer and files the 1's into a sorted (clockwise) array of points(x,y) and pushes it into the current globalObjs obj, simplifyObject accesses that array and simplifies it using the douglas-peucker algorithm so instead of 1,5 - 2,5 - 3,5 - 4,5 - 5,5 - 6,6 - 7,7  ... you just have 1,5 - 5,5 - 6,6 - 7,7 ... this is used to draw the border of the object and detect its neighbors later on. 
[php]
  void MapImage::createObject(int x, int y) 
{
    const int w = getWidth();  const int h = getHeight(); 
    const SDL_PixelFormat *format = getFormat(); 
    
    int *Pixels = _Pixels; 

    int oldColor = Pixels[y*w+x]; 
    int newColor = SDL_MapRGB(format, 0, 0, 0); 
    if(oldColor == newColor)
        return; 

    _BoundaryLayer = new int[h*w](); 

    Object obj;
    isolateObject(x, y, oldColor, newColor); 
    obj.endpoints = floodResults; 
    obj.id = numObjs++;
    floodResults.clear(); 
    globalObjs.push_back(obj);
    

    for(int A = 0; A < h; A++) 
        for(int B = 0; B < w; B++) 
        {
            if(_BoundaryLayer[A*w+B] && 
               _BoundaryLayer[A*w+(B-1)] && 
               _BoundaryLayer[A*w+(B+1)] && 
               _BoundaryLayer[(A-1)*w+B] && 
               _BoundaryLayer[(A+1)*w+B])
                _BoundaryLayer[A*w+B] = 2; 
        }

    HACKPOINT.clear(); 
    
    for(int A = 0; A < h; A++)
        for(int B = 0; B < w; B++) 
            if(_BoundaryLayer[A*w+B] == 1) 
                traceObject(B, A);

    simplifyObject(1); 

    delete[] _BoundaryLayer; 
}
[/php]this code is from my younger days when I was irritated with the immigration/colonization scheme in the Paradox games (Victoria, Europa Universalis) and decided the only sensible thing to do was create my own game.

---

### Post by mehaga on 2009-08-30
not being able to pick one language/technology/framework/library/tool/whatever, and become exceptionally good with it, but experiment all the time.

---

### Post by Nevon on 2009-08-30
Often when I think I've figured out a problem, but it turns out my approach doesn't work, I just randomly hack stuff on my original solution until it does work - making it completely unreadable and extremely inefficient.

---

### Post by lisati on 2009-08-30
My biggest bad habit would be to think in terms of "First I do this then this", tacking the bits of code on towards the end as I think of them, and end up with a program which is one large chunk of poorly organized sequential code.

---

### Post by Mirge on 2009-08-30
This is almost a "people not to hire" thread :lolflag:

---

### Post by credobyte on 2009-08-30
> **Mirge said:**
> This is almost a "people not to hire" thread :lolflag:
SEO makes it even worse .. traces will stay there for years :)

---

### Post by pepperphd on 2009-08-30
> **credobyte said:**
> SEO makes it even worse .. traces will stay there for years :)

Good thing nobody actually knows me as Dr. Pepper, then.

---

### Post by Mirge on 2009-08-30
> **pepperphd said:**
> Good thing nobody actually knows me as Dr. Pepper, then.

And now I understand your name, rofl...

---

### Post by Spencer Caplan on 2009-08-30
> **lisati said:**
> My biggest bad habit would be to think in terms of "First I do this then this", tacking the bits of code on towards the end as I think of them, and end up with a program which is one large chunk of poorly organized sequential code.

Yeah, my code can become to much of onehugeblock. All of the it works, it just needs more precoding planning, and then it would fit better.

---

### Post by soltanis on 2009-08-30
My worst habit is believing I can come up with a better solution to a problem, working a little into that solution, then realizing that I was wrong and should have read the mainstream solution better before I started -- then scrapping everything I just wrote before realizing that I might've had something going. Cycle repeats.

---

### Post by slavik on 2009-08-31
> **pepperphd said:**
> I'll start.  Some of my identifiably bad habits while programming are:

-Using code that just works instead of code that both works and looks like it works.
-Lack of planning.  Just fire up vim and start coding.
organise it in *some* way ... even if it is determined to suck later on (because if you code sucks but is readable, the best you can do is be consistant in how you do things). ;) (I do have code right now that I decided could be written better, but it is readable and consistant).

---

### Post by Fallen_Demon on 2009-08-31
I use Java (SHOCK!!!:O) regularly (DOUBLE SHOCK!!!:O:O)

---

### Post by nvteighen on 2009-08-31
For sure:
-Premature abstraction... This comes actually from working with incomplete data or incomplete design.
-Insufficient testing.

---

### Post by maximinus_uk on 2009-08-31
Premature optimisation - I can't help it after years of programming assembly language in the 80's :(

Also, I tend to follow the mantra, get it working, then get it to look good. But it often happens that I stop as soon as the code works. From experience this means it takes longer to understand the code when (if) I ever go back to it.

On the flip side, I reckon I spend LESS time re-understanding code than I would making it look nice, and I tend to do this step whenever I re-visit old code anyway.

---

### Post by Bodsda on 2009-08-31
I don't plan anything. If I have stopped typing for more then a few seconds then it means that my brain is not moving fast enough.
```

count = 1
while count != 3:
    This usually leads me to write some very, very strange code, which,
    after I think about, could be written a lot simpler, so I scrap my 
    attempt and start again with count/3rd of a plan
    count += 1

Finally I have something useful
```

---

### Post by achron on 2009-08-31
Defer writing the unit tests until 'later'...
There's always some execution path I forget/overlook that doesn't get run through my tests that clients will manage to find. They seem to live their lives at what I consider 'edge' cases.

---

### Post by koonsolo on 2009-08-31
For me:

[LIST]
[*]Too much focus on the happy-path, and not handling exceptions/errors correctly (or not at all ;)
[*]Logging... I love logs, but hate log statements in code ;).
[/LIST]

---

### Post by moster on 2009-08-31
Writing too slow, too big (due copy/paste) and too memory demanding programs due lack of knowledge/thinking/planing and eager to get it done fastest as possible :D

---

### Post by MindSz on 2009-08-31
The ones I have trouble with:
- Lack of documentation which makes me spend a lot of time trying to understand old programs.
- Modifying original code when re-visiting old programs instead of using a copy (sometimes it ends up not working at all!)

---

### Post by Sockerdrickan on 2009-08-31
I don't have any, except unfinished projects of course. But that's a part of this field.

---

### Post by TheBuzzSaw on 2009-08-31
I can't think of any off the top of my head (though I have many). I just always think back to my friend who, out of frustration, moves his private member variables to public just to save himself some pain.

---

### Post by uljanow on 2009-08-31
Others have critized me for 

**writing only few comments**. I tend to write comments which only indicate why is something non-obvious done to increase the understanding. If people need addional comments to understand your code than they're bad programmers or the code is not well written. 

**Focusing to much on the programming itself**, like writing beautiful code, as few lines of code as possible and having a tight syntax. Consequently it takes longer to write the initial code.

---

### Post by Copernicus1234 on 2009-08-31
I try to make my code too generic so it becomes much more complicated than it has to be.

And do I reuse my generic code so I get something out of it? Rarely.

Not sure why I do this...

---

### Post by Reiger on 2009-08-31
Sometimes I fall into that trap as well. My true bad habit in w.r.t. programming is that I do the documentation too much _after_ coding, not _while_ coding. Although I think I've found an acceptable middle ground: do a batch of code, then do a batch of documentation.

---

### Post by gjoellee on 2009-08-31
-I usually publish my work too early, but when I get finished it is quite nice and bug free though
-Not good planing, I just have some images in my head
-I may sometimes use offensive variables

---

### Post by petrus4 on 2009-08-31
> **maximinus_uk said:**
> Premature optimisation - I can't help it after years of programming assembly language in the 80's :(

Also, I tend to follow the mantra, get it working, then get it to look good. But it often happens that I stop as soon as the code works. From experience this means it takes longer to understand the code when (if) I ever go back to it.

The thing that bothers me about the subject of code aesthetics is that I feel that most people's idea of what looks good is screwed up, to be honest.

To me, good looking code is code I can read, end of story.  I'll write a 50 branch if statement quite happily if it means I'm going to be able to randomly come back to that if statement, eight months (or years) down the line, and still be able to figure out what I was thinking at the time.

Most people I've seen online seem to think that good looking code is code that's the opposite; squashed together as tightly as possible.  They seem to think that it makes them cool if they can still read stuff like that.  I think that's crazy.

---

### Post by petrus4 on 2009-08-31
> **uljanow said:**
> 
**Focusing to much on the programming itself**, like writing beautiful code, as few lines of code as possible and having a tight syntax. Consequently it takes longer to write the initial code.

Yeah, but is it as few lines as possible because your actual concept is simple, or is it as few lines as possible because you think it's elegant to try and cram 100 lines into 5, even if your method of solving the problem is still really that complex?

---

### Post by PowerSource on 2009-08-31
when i place a function indside an if() I often only place one ) at the end wich results in irritating extra-work.

---

### Post by Frak on 2009-08-31
-Try to end logical expressions with semicolons (if(true);{})
-I tend to write things that span over many languages.

---

### Post by moster on 2009-09-01
Tend to too much got frustrated and then go to quake live and make few hundred kills. After that I am good only for sleeping.

---

### Post by Thesuperchang on 2009-09-01
- Typecasting C to oblivion.
- Binge coding.
- Poor cross platform compatibility.
- Global variables out of laziness.

Last two have come into play as of the last two months.

---

### Post by Greyed on 2009-09-01
A: Not practicing enough because....
B: ...I don't have enough projects.

Sometimes I go months without touching a line of Python.  It's amazing I can remember it at all sometimes.  :(

---

### Post by CptPicard on 2009-09-01
> **Greyed said:**
> A: Not practicing enough because....
B: ...I don't have enough projects.

Hear, hear. I have come to notice that an annoying side-effect feature of programming is that there are diminishing returns in terms of intellectual gratification... it's been years since I have actually bothered to touch any kind of a hobby project. I hope my newfound interest in writing parsers at least makes me do some Lisp...

---

### Post by ntom-taylor on 2009-09-01
[LIST]
[*]Lack of comments ( Comments are *somtimes* there but may be too vague or just outdated ) 
[*]Poor Variable naming
[*]Over complicating simple jobs
[*]Spending more time working code that I like rather than coding stuff which will increase sales
[*]Error checking and debugging for just as much time as it takes to code the app, and trying to handle ever possible outcome of results
[/LIST]

---

### Post by nvteighen on 2009-09-01
> **CptPicard said:**
> Hear, hear. I have come to notice that an annoying side-effect feature of programming is that there are diminishing returns in terms of intellectual gratification... it's been years since I have actually bothered to touch any kind of a hobby project. I hope my newfound interest in writing parsers at least makes me do some Lisp...

Hm... it's an interesting idea, actually... But I guess it's universal to all things; I mean, when you profesionalize your hobby or likes, you end up fighting over your passion and your job... It's something I experience in my Philology studies: I love to read, but I just can't read for fun anymore... I have no time and when I have it, I feel saturate...

---

### Post by Copernicus1234 on 2009-09-01
> **Greyed said:**
> A: Not practicing enough because....
B: ...I don't have enough projects.

Sometimes I go months without touching a line of Python.  It's amazing I can remember it at all sometimes.  :(

I dont see how there can be lack of projects. There is tons of stuff Ubuntu could use. You could take almost any application that comes with Ubuntu and write your own version with more features, and it wouldnt take that long either since most of them only have the basics to keep them simple and neat.

Or you could write a GUI for a command line program you use a lot.

Possibilities are like endless...

---

### Post by nvteighen on 2009-09-01
> **Copernicus1234 said:**
> 
Possibilities are like endless...

And that's why one gets easily lost...

---

### Post by tom66 on 2009-09-01
Overcommenting, e.g. "add 1 to a", "divide by the data set size..." I've recently reduced the amount of this that I do.

---

### Post by mcla0203 on 2009-09-01
I love copy-paste. =]

They really should remove that function from developer machines =P

---

### Post by Greyed on 2009-09-01
> **Copernicus1234 said:**
> I dont see how there can be lack of projects. There is tons of stuff Ubuntu could use.

What others could use and what interests me or what I need are two different things.  I could make my own version of some tool, but why?  That tool is already there and adequate for my needs or a tool I don't need in the first place.

---

### Post by socool274 on 2009-09-02
I like to just start coding, too. I do almost no forward planning, except for the math. I plan out the math before I use it. I code messily. I use nearly no comments.

---

