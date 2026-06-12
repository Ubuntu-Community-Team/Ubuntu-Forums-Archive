---
title: "Most useless comment ever"
date: 2008-07-23
forum: Programming Talk
---

### Post by DrMega on 2008-07-23
In the course of my job, I find myself today having to modify a piece of code written by my colleague some time ago. There is quite a lot going on so I thought I'd lean on the comments a bit to guide me through what my colleague intended when he wrote the original (after all, that's what comments are for).

So, I come across this:

> //if there are no letters with the action use different SQL

I just thought I'd share this with you all. Certainly it is promising right up to the point where it says "use different SQL". Why? I ask. Why should we use "different SQL". What should the "Different SQL" do? So should the "different SQL" make us a cup of tea? Perhaps it should join every table in the database to every other table and bring the system to its knees? The comment my as well say "do something else".

So, to all programmers I say this: If you are going to use comments in your code, lets make them useful.

---

### Post by NilsE on 2008-07-23
Many many years ago I wrote a systems management tool for mainframe disk storage that listed all datasets and their size and age to determine what if any cleanup could be done.

When I wrote this I added an awful amount of error routines for diagnostic purposes but knowing that as much as IBM changes software I should have one catch all error/exit routine.  So anyway, I got a call at 3AM one morning about 10 years after I stopped maintaining it (didn't even know they were still running it) and when I had them read me the dump over the phone they found the following message:

"It is 3 AM and I have no idea why the hell I am here"

Obviously this was a useless message since it failed at 2:45 AM and I was off on the time.

---

### Post by themusicwave on 2008-07-23
That is a pretty useless comment.  It is one of those ones you almost wish wasn't there so you could you didn't have to try to figure out what some magical different SQL was.

I also enjoy reading through my predecessors code.  There are few comments, but when they are there, they are just dozens of lines of actual code commented out.

Sometimes it will start with:

//THIS DOES NOT WORK
/*
 <20 lines of code here>
*/

It always leaves me wondering whether that code needs to be finished or he decided not to use it and left it there anyway.  I hate when people comment out code and leave no explanation.

Due to this, I just rewrote the whole application.  Without any comments other than those it was almost impossible to figure out and it wasn't too big a application anyways.

---

### Post by drubin on 2008-07-23
This is proberbly my best comment i have ever come across. It was part of an open source JavaScript Libary.

```
// f***g IE is too stupid for window names
function makeWindowName(wName) {.....
```

---

### Post by bfhicks on 2008-07-23
One of my favorite things to do is search google codes for some random comments.

[[COLOR="Red"]smoking crack?[/COLOR]]("http://www.google.com/codesearch?q=smoking+crack&hl=en&btnG=Search+Code")

---

### Post by Tony Flury on 2008-07-23
the best i saw was a comments in a very large proprietary comms package which went along the lines of : 

```

/*=====================================*/
/* According to the manual this system call should not work */
/* I have no idea why it works but it does */
/* I am not even sure what it does - but if you remove it everything else fails */
/* do not change this code without my permission */

```

---

### Post by cacycleworks on 2008-07-23
:) hehehe, thanks for the chuckles! We all a lot of this is caused by lack of planning on management's part. I've done my fair share of needing crack (RedBull had juuuust come out then) to pound through code to get something, anything, sellable out the door.

Then I'd spend 1-2 days commenting the code, which would lead to a week's worth of redesign then or later on.

We all had to "sign" our work in the code (in comments or whatever). I've seen a number of previous employees, so when I was there, I'd add the note that they're long gone and no one else knows what this is doing either.

And f***ing magic numbers? PLEASE at least #define them at the top of the file. Or include a magic_numbers.h. Sheeeesh. 

Some of my favorites are special variable names:
" thing "
foreach( $murder as $crow )
" mystery_number "
" coworkersName_mashup "

=) 
Chris

---

### Post by nvteighen on 2008-07-23
> **Tony Flury said:**
> the best i saw was a comments in a very large proprietary comms package which went along the lines of : 

```

/*=====================================*/
/* According to the manual this system call should not work */
/* I have no idea why it works but it does */
/* I am not even sure what it does - but if you remove it everything else fails */
/* do not change this code without my permission */

```

And how should we figure what you are doing, dear coder?

Hey, it's very funny to search comments and random strings in Google Code!

This is a good one:
```

/*
 * 10 Sin
 * 20 Goto hell
 * (I welcome you if-else hell)
 */

``` ([here]("http://www.google.com/codesearch?hl=en&q=%22goto+hell%22+show:mJjsjC6eoD8:9mb6gPYF9lw:uUlc3AsfKLo&sa=N&cd=10&ct=rc&cs_p=http://www.angstrom-distribution.org/unstable/sources/src.usr.bin.cvs_anoncvs.ca.openbsd.org__20060814.tar.gz&cs_f=cvs/file.c#l693"))

---

### Post by LaRoza on 2008-07-23
You can also start grepping the Linux source. Some of it is shocking :-)

---

### Post by loganwm on 2008-07-23
Back when I used to do a bit of scripting I had a program so bugged and intertwined that if you affected a certain function it skewed the whole program into a state of absolute chaos.

So after 2 weeks of attempting to debug it, and too much time invested to do a full rewrite, I just commented it: "Do Not Open Until Christmas" and moved on.

---

### Post by LaRoza on 2008-07-23
[html]
<!-- This is a comment -->
[/html]

A useless comment, obviously, but there can be times when they are needed. My site has a useless comment "<!--tm-->", because it is the default argument for a function which generates the markup (which would be used for other metatags, if needed)

---

### Post by Reiger on 2008-07-23
I've been doing some XSLT as of late, and one of the pitfalls you will need to avoid is <script ... />. Okay it's of course entirely valid; but that won't stop MSIE from freaking out an making sure *nothing* whatsoever to do with scripts works anymore.

So, easiest thing to do was the following: <!-- This is a comment to help older browsers (particularly MSIE) -->. Considering that also may occur with <p></p> tags ...

---

### Post by Darkade on 2008-07-23
Hehehe, for most things I've programed when I finish I usually comment a song's lyric in the main module, I like **Soda Stereo** (An Argentinian Rock Band for those of you don't know) and **Jaguares** (A Mexican Rock Band) so most times I use their songs hehehe.
```

//Ella usó mi cabeza como un revolver
//E incendio mi conciencia con sus demonios!

```
:guitar:

EDIT:
I know it's really useless/pointless/and whatever you want to say. But It makes things personal LOL.

---

### Post by loganwm on 2008-07-23
> **Darkade said:**
> Hehehe, for most things I've programed when I finish I usually comment a song's lyric in the main module, I like **Soda Stereo** (An Argentinian Rock Band for those of you don't know) and **Jaguares** (A Mexican Rock Band) so most times I use their songs hehehe.
```

//Ella usó mi cabeza como un revolver
//E incendio mi cocincia con sus demonios!

```
:guitar:

EDIT:
I know it's really useless/pointless/and whatever you want to say. But It makes things personal LOL.

I usually put "goo goo g'joob" in the header :)

Google "I Am The Walrus"

---

### Post by Darkade on 2008-07-23
> **loganwm said:**
> I usually put "goo goo g'joob" in the header :)

Google "I Am The Walrus"
Beatles classic!

EDIT:
BTW I misspelled cocincia it was supposed to be Conciencia LOL

---

### Post by loganwm on 2008-07-23
> **Darkade said:**
> Beatles classic!

EDIT:
BTW I misspelled cocincia it was supposed to be Conciencia LOL

The entire song is nonsensical, I love tossing lines out anywhere to see if people catch em, and my code is not excluded, haha

---

### Post by samjh on 2008-07-23
Just found some from an old program of mine.

```
// Put formula here.
```
The formula is already there.

```
/**********************************************************************
*	Specifies audio format required of input line
*	May be irrelevant in the final program
*/
```
Nice way of showing that my testing was inadequate.

```
// The following three not applicable. Ignore them.
```
I don't know why I coded that part.

---

### Post by bobbocanfly on 2008-07-23
Good code search is brilliant fun:

```
//
// Compute the eigen values of a covariqance matrix. F**k knows what it's doing eaxclty.
//

```

```
    /* AAAAAAAAAAAAAAaaaaaaaaaaaaaaaaaaaaaaaaaaaaahhhhhhhhhhhhhhhhhhh! */

```

```

* All rights reserved
MODULE_LICENSE("GPL");

```

Not a comment but i thought this would be suitable to post. Found on Matthew Garretts live journal with the heading 'No, seriously' (I would post a link but this is Matthew Garrett we are talking about so I'd probably get an infraction for linking to it).

```


#if LINUX_VERSION_CODE >= 0x020400
#else
#ifndef KERNEL26
#include <linux/kcomp.h>
#endif
#define vm_pgoff vm_offset
#ifndef KERNEL26
#define virt_to_page MAP_NR
#endif
#endif
```

```

void * MKIA_API
mkia_strncpy(char *s1, char *s2, int len)
{
 return strncpy(s1,s2,len);
}
EXPORT_SYMBOL(mkia_strncpy);

```

---

### Post by clash on 2008-07-24
We had a very unstable box in a testing network once. We had 12 boxes and the software on each had to be started in a particular order as well as the boxes themselves. 

Anyways we wrote scripts and there was one particular machine that was as unstable as a young heroin addicted pyromaniac on withdrawl, standing in the middle of a bomb factory with a can of petrol and a box of matches. It put us through hell for two weeks. 

Anyways, someone added something similiar to this to the script for this particular box. 

/* Procedure to start streaming server. Otherwise known as that big black bitch.

- Sacrifice a small puppy to the Gods of mobile ip. If no puppies are availible, use two cats.
- Spin around 3 times in your chair clockwise and 5 times anti-clockwise.
- Pledge your soul to Steve, the blacksmith of dodgy wireless card drivers.
- run ./startup_you_*******_piece_of_****.sh and click your heels 90 times with your eyes closed while mumbling the words "work you miserable cunt". 

Warning: Any attempt to run this procedure more then 1000 times (Yes everyone we've beena at this for 3 ******* days) will result in permanent insanity. */

Maybe its one of those things you have to be there for ... :D

---

### Post by drubin on 2008-07-24
> **clash said:**
> We had a very unstable box in a testing network once. We had 12 boxes and the software on each had to be started in a particular order as well as the boxes themselves. 
.......


OMG that is funny.. keep them coming this is almost as funny as bash.org

---

### Post by guilly on 2008-07-24
The best one I've seen in my short time in the industry is:
//This program does whatever it's supposed to do.

THATS IT!!!

---

### Post by drubin on 2008-07-24
This has by far been my best thread on this forum!!

---

### Post by Diabolis on 2008-07-24
> **clash said:**
> We had a very unstable box in a testing network once. We had 12 boxes and the software on each had to be started in a particular order as well as the boxes themselves. 

Anyways we wrote scripts and there was one particular machine that was as unstable as a young heroin addicted pyromaniac on withdrawl, standing in the middle of a bomb factory with a can of petrol and a box of matches. It put us through hell for two weeks. 

Anyways, someone added something similiar to this to the script for this particular box. 

/* Procedure to start streaming server. Otherwise known as that big black bitch.

- Sacrifice a small puppy to the Gods of mobile ip. If no puppies are availible, use two cats.
- Spin around 3 times in your chair clockwise and 5 times anti-clockwise.
- Pledge your soul to Steve, the blacksmith of dodgy wireless card drivers.
- run ./startup_you_*******_piece_of_****.sh and click your heels 90 times with your eyes closed while mumbling the words "work you miserable cunt". 

Warning: Any attempt to run this procedure more then 1000 times (Yes everyone we've beena at this for 3 ******* days) will result in permanent insanity. */

Maybe its one of those things you have to be there for ... :D

Very funny, I even gave him a thanks for the story. :lolflag:

---

### Post by loganwm on 2008-07-24
The best one I've seen is an argument between two of the programmers throughout the code in the form of comments, I'll post some excerpts:

comment: //this function doesn't work, good work genius
response from the other: //you spelled it wrong.

comment: //what is this?
response from the other: //I don't remember, but don't screw with it

comment: //this is idiot-proofing
response: //wrong. that exits the program?.
comment: //exactly.

comment: //why?
response: //I honestly don't even know.
comment: //Can I delete it?
response: //if you like 400 useless lines of code :)

There was some better ones, but I can't remember them completely.

---

### Post by DrMega on 2008-07-24
> **LaRoza said:**
> [html]
<!-- This is a comment -->
[/html]

A useless comment, obviously, but there can be times when they are needed. My site has a useless comment "<!--tm-->", because it is the default argument for a function which generates the markup (which would be used for other metatags, if needed)

When I can be bothered to work on dynamic websites, I often use HTML comments as a means of debugging without presenting any debug info to the screen.

---

### Post by spadewarrior on 2008-07-24
> **Diabolis said:**
> Very funny, I even gave him a thanks for the story. :lolflag:

Haha!

I like the way the f-word is censored but the c-word isn't. A nice touch.

---

### Post by cacycleworks on 2008-07-24
> **DrMega said:**
> When I can be bothered to work on dynamic websites, I often use HTML comments as a means of debugging without presenting any debug info to the screen.

Another trick I use for that is to check the IP of the visitor. If the visitor is from the permanent IP from my business site, some pages dump debug code, $_POST, etc. :)

:) Chris

PS - I had to run a grep on the code running on our site: (I edited the result)
```

wp-content/plugins/xinha4wp/xinha_core$ grep -iRn "fu*k" *
htmlarea.js:5316:  // check for function objects (as usual, IE is fu*ked up)
plugins/ContextMenu/context-menu.js:373:                        var IE_IS_A_FU*KING_**** = '>';
plugins/ContextMenu/context-menu.js:376:                                IE_IS_A_FU*KING_**** = " unselectable='on' style='height=1px'>&nbsp;";
plugins/ContextMenu/context-menu.js:378:                        td.innerHTML = "<div" + IE_IS_A_FU*KING_**** + "</div>";
plugins/SpellChecker/spell-check-ui.js:45:  // we should use innerHTML here, but IE6's implementation fu*ks up the
popupwin.js:152:      // size to content -- that's fu*kin' buggy in all fu*kin' browsers!!!

```

hehehe, this was all in a wordpress plug-in. :D

---

### Post by Reiger on 2008-07-24
Yeah well anyone with a soul who does work on getting done some decent website will come to associate IE with lotsa asterisks.

---

### Post by bobbocanfly on 2008-07-24
```
/* Program Starts Here */
int main (int argc, char** argv)
{
   ....lots of code
}
/* Program Ends Here */
```

---

### Post by drubin on 2008-07-24
> **bobbocanfly said:**
> ```
/* Program Starts Here */
int main (int argc, char** argv)
{
   ....lots of code
}
/* Program Ends Here */
```

I would tend to disagree with that one :) Although allot more handy when you have stuff like this...

[PHP]
if($a){
	if($b){
		if($c){
			if($d){
			}//End $d
		}//End $c	
	}//End $b
}//End $a
[/PHP]

No imagine that it was a little more complex then $a  and the "if" statements were longer then 2 lines it gets confusing where functions/blocks end and where they start. Some people just get into the habit of ALWAYS using them...

---

### Post by mssever on 2008-07-25
> **rubinboy said:**
> [php]if($a){
 *****if($b){
 *********if($c){
 *************if($d){
 *************}//End $d
 *********}//End $c****
 *****}//End $b
 *}//End $a[/php]No imagine that it was a little more complex then $a  and the "if" statements were longer then 2 lines it gets confusing where functions/blocks end and where they start. Some people just get into the habit of ALWAYS using them...
  When you get into code like that, it's probably time to refactor... :)

EDIT: Where did all those asterisks in the quote come from? Time to switch to a Real Browser. Opera seems to not get along very well with these forums.

---

### Post by LaRoza on 2008-07-25
> **mssever said:**
> 
EDIT: Where did all those asterisks in the quote come from? Time to switch to a Real Browser. Opera seems to not get along very well with these forums.

Opera works fine for me...

---

### Post by drubin on 2008-07-25
Firstly I didn't use Opera. Does any one else see those asterisks because I still don't (on my post).

> When you get into code like that, it's probably time to refactor... 

It was just an extreme situation. mostly I do it when my functions/blocks of code are long and would like to remember by looking at the end what i was doing at the top.

---

### Post by 3rdalbum on 2008-07-25
> 
 pathstart = "/home/"+username+"/"
 #assumption: User is not running Blacklight as root.
 # Blacklight does not run on Windows or the iPhone thankfully, otherwise this assumption
 # would be pretty dumbass.


> 
if (extension == "flac"):
	#somebody please explain why sox doesn't read FLAC!


Both of those appeared in my Blacklight2.

> #THANKS FOR ALL THE COMMUNITY INVOLVEMENT IN FINDING THIS BUG!!!

I experimented with irony in HfsBrowser. I guess nobody saw that comment, as nobody read the HfsBrowser code, hence the comment :-)

---

### Post by LaRoza on 2008-07-25
> **rubinboy said:**
> Firstly I didn't use Opera. Does any one else see those asterisks because I still don't (on my post).


If you copied and pasted the code, they may have been invisible, but pasted.

---

### Post by LittleLORDevil on 2008-07-25
I am working for Autodesk and they threw me into a ginormous project with almost no documentation and very few descriptive comments.  Pretty useless to me.

---

### Post by drubin on 2008-07-25
> **LaRoza said:**
> If you copied and pasted the code, they may have been invisible, but pasted.

Please can some one explain if and how other people saw stars in my post? 

Attached are the screen shots of both my original post, as well as mssever's quote with the stars.. :s

I am using Firefox3.0  Ubuntu :)

---

### Post by LoneWolfJack on 2008-07-25
it always makes me flinch when I see something like this (which happens far too often)

```
// do some stuff
```

---

### Post by LaRoza on 2008-07-25
> **rubinboy said:**
> I would tend to disagree with that one :) Although allot more handy when you have stuff like this...

[PHP]
if($a){
	if($b){
		if($c){
			if($d){
			}//End $d
		}//End $c	
	}//End $b
}//End $a
[/PHP]

No imagine that it was a little more complex then $a  and the "if" statements were longer then 2 lines it gets confusing where functions/blocks end and where they start. Some people just get into the habit of ALWAYS using them...
Quoting to see stars...

---

### Post by LittleLORDevil on 2008-07-25
> **LoneWolfJack said:**
> it always makes me flinch when I see something like this (which happens far too often)

```
// do some stuff
```I worked on a project with a buddy, his code standards were horrible.  He made names for thigns that didn't closely relate to what they were suppose to do.  So first thign I did was rip his code apart and rebuild it.

---

### Post by NovaAesa on 2008-07-30
I was looking at some code of one of my friends at uni, and he had comments like this:

//this is a for loop

//this is a do... while loop

//this declares an int

//do binary selection

It was almost like a commentary of exactly what each line did or what particular structure it was!

---

### Post by the_real_fourthdimension on 2008-07-30
```

/****************************************************************************
 I hate Windows :-).
****************************************************************************/

```

---

### Post by darthmob on 2008-08-10
I found this quote in the signature of a gamingforum:
```
// DAVE THE LARGE BROKEN DOOR STATE CHANGE NEEDS TO HAPPEN HERE
// DAVE ISN'T A LARGE BROKEN DOOR, WHO WROTE THIS
```
- scripts/maps/area22.script

---

### Post by lisati on 2008-08-10
Not exactly a comment, but this code fragment was quoted in a book I once had in my personal library (long since lost), long before Peter Jackson did his stuff with LOTR:
```
call gandalf
```

---

### Post by nvteighen on 2008-08-10
> **lisati said:**
> Not exactly a comment, but this code fragment was quoted in a book I once had in my personal library (long since lost), long before Peter Jackson did his stuff with LOTR:
```
call gandalf
```
Interesting case of magic programming.

---

### Post by drubin on 2008-08-10
> **nvteighen said:**
> Interesting case of magic programming.
hehe

---

### Post by cmay on 2008-08-10
```
/* ************************************************************************
 * aha.c                                                                  *
 * license : restricted by means of impossible usage                      *                                           * 
 * purpose : unknown                                                      *
 *  author : completly unknown and absolute unreachable by phone or email * 
 * *************************************************************************/

#include <stdio.h>
int main(int argc, char** argv)
{
if(argc != 2)
{
printf(" usage : makes [filename][type] default .txt unless else specified  \n");
return 1; /* why implicit declaretion of exit(1); ? */
}
else
printf("MESSAGE:look for the file you made in the ./ directory\n");
FILE *file_ptr=fopen(argv[1],"w");
fprintf(file_ptr,"the file is saved as %s \n is that not cool or what :)\n",argv[1]);
fclose(file_ptr); /* how to print to printer ? */
return 0;
}
```

---

### Post by nvteighen on 2008-08-10
> **cmay said:**
> ```
/* why implicit declaretion of exit(1); ? */
```

Whoever wrote this doesn't even know what header is needed for exit()...

---

### Post by andrewjoy on 2008-08-10
> **rubinboy said:**
> This is proberbly my best comment i have ever come across. It was part of an open source JavaScript Libary.

```
// f***g IE is too stupid for window names
function makeWindowName(wName) {.....
```


ha ha ha thats just classic

```
     int magic_mushroom;         /* Big fat spliff... */ 
```

random google code ftw

---

### Post by heikaman on 2008-09-10
"A wxImageList contains a list of images, which are stored **in an unspecified form**. Images can have masks for..."

:lolflag: :lolflag: :lolflag:

---

### Post by drubin on 2008-09-10
I am the culprit of the most USELESS comment ever. Yesterday I was working on some code with very tight dead lines so it was a very long day ended up leaving the office at 2:30am.

When I got in this morning I found this..
//Rebinds the events, as we have altered the matrix of time

WTF. I do not even remember writing that.  Also it makes no sense.

---

### Post by cb951303 on 2008-09-10
```

//TODO mutex for sprites
// I think this info thing is completely useless... But it's ok programming is fun anyway.
QuadNode * QuadNode::updateObject(GameID id, int info){
...

```

---

### Post by Diabolis on 2008-09-10
haha I like that one.

---

### Post by skullmunky on 2008-09-14
1. good runtime debugging output:

```

YOU SHOULD NOT BE HERE!
Segmentation fault (core dumped)

```

2. this forum auto-censors, right?  good, because here are some that I really love from quake III arena.  actually i don't think they're useless, actually quite helpful and descriptive.

```

grep -r **** *
i  = 0x5f3759df - ( i >> 1 );               // what the ****?
//FIXME: this is a ******* mess
// vm ****age
//NOW close the ******* brush!!
// FIXME: this code is a TOTAL cluster***
...

```

---

