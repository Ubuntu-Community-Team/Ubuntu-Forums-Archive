---
title: "[SOLVED] Introduce me to flash and actionscript"
date: 2008-08-24
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-08-24
I want to learn animating with actionscript. Could you give me some beginner's tutorials, 
open-source software, and tell me how to do a simple animation with actionscript?

---

### Post by tom66 on 2008-08-24
I would recommend SVG/SMIL as a good thing to try instead of Flash, which is proprietry software. But at the moment, few browsers support it. I know Opera has reasonable support for it, and Firefox will be coming with it soon.

But anyway, open up Flash. Create a new document, ensure the Timeline is empty. Draw an object on the Stage. Let's make it a red circle/oval. Right click on the object, and select 'Convert to Symbol'. Give the object the name 'circle'.

Now, right click on the Timeline at about frame 60, or whereever you want your animation to end at. Select 'Insert Keyframe'. Then, at frame 60 or whatever you chose, move the object, rotate it, stretch it, etc. Do what you want to it. I don't think coloring is possible. 

Finally, right click somewhere between frame 1 and frame n (whatever you chose) and select 'Create Motion Tween'. Press Enter. Sit back, and admire your animation.

---

### Post by crazyfuturamanoob on 2008-08-24
Whoa, too fast :confused: First all, what is that 'flash' you are talking about? Which program?

---

### Post by mr.propre on 2008-08-24
I don't really think there is opensource software for creating flash, its hard enough making an opensource player. At least I never discovered one and Flash is one of the few reasons why I keep using windows on my desktop.

The best way to learn flash is still by reading a book and have patience; Like they say: Rome wasn't build in one day. ;-)

---

### Post by crazyfuturamanoob on 2008-08-24
I don't know any more about flash than when I made this topic. I want a name of a program which to make flash animations with? (no need to be opensource this time)

---

### Post by Bachstelze on 2008-08-24
Moved to Programming Talk.

---

### Post by WitchCraft on 2008-08-24
> **crazyfuturamanoob said:**
> Whoa, too fast :confused: First all, what is that 'flash' you are talking about? Which program?

Use Macromedia Flash, or now adobe  flash:
[http://www.adobe.com/products/flash/?promoid=BPDEE](http://www.adobe.com/products/flash/?promoid=BPDEE)

Only 699 bucks.

And remember that downloading a torrent of a pirated copy might be illegal in your country :lolflag:

---

### Post by crazyfuturamanoob on 2008-08-24
> **WitchCraft said:**
> Use Macromedia Flash, or now adobe  flash:
[http://www.adobe.com/products/flash/?promoid=BPDEE](http://www.adobe.com/products/flash/?promoid=BPDEE)

Only 699 bucks.

And remember that downloading a torrent of a pirated copy might be illegal in your country :lolflag:

**_699_!?!?!?!?!? :confused: WTF?!?!:confused: Why the hell is it so expensive???? **:confused:[SIZE="1"]   

Bah, you never get caught when downloading torrents...[/SIZE]

---

### Post by LaRoza on 2008-08-24
> **mr.propre said:**
> Rome wasn't build in one day. ;-)

Yes it was. There had to be a day when Rome was one day old. Of course, it branched out, but "Rome" was built in a second.

And keep it legal people! Any more hints of illegal activity this thread is closed.

---

### Post by Dr Noam on 2008-08-24
OK, let another noob put his tuppenceworth in: Adobe Flash doesn't seem to work on my wubi after downloaded and attempts to install, not even the Linux ones. Is there a (reasonably simple) way to get Flash to work? If not, is there something else that will get youtube and Flash based games to work?

Thanks,
Noam

---

### Post by mssever on 2008-08-24
> **Dr Noam said:**
> OK, let another noob put his tuppenceworth in: Adobe Flash doesn't seem to work on my wubi after downloaded and attempts to install, not even the Linux ones. Is there a (reasonably simple) way to get Flash to work? If not, is there something else that will get youtube and Flash based games to work?

Thanks,
Noam
```
sudo aptitude install flashplugin-nonfree
``` You might need to enable the medibuntu repository first--I don't remember.

---

### Post by crazyfuturamanoob on 2008-08-25
700 dollars!?!?!? I don't get it. Why is it so expensive?

---

### Post by Kadrus on 2008-08-25
[mtasc]("http://www.mtasc.org/"):Motion Twin Action Script Compiler
The project has continued into [haXe]("http://haxe.org/"),a new programming language aimed for web applications.
It can be used as javascript,nekovm,actionscript(swf),and php files.
It's open source and cross platform.
I suggest having a look at it,it has a strong community as well,register at their mailing list,which is very active.
Wrox published a book,on haXe: [Professional haXe and Neko ]("http://www.amazon.com/Professional-haXe-Neko-Programmer/dp/0470122137")

---

### Post by Zugzwang on 2008-08-25
> **crazyfuturamanoob said:**
> 700 dollars!?!?!? I don't get it. Why is it so expensive?

Because Adobe decided to sell it for that price. It's their product, so they decide the price. If you don't want to buy it for that price, don't but it but use something different. However, other software products are often either not so mature or harder to use. The action script compiler above might be a possibility. However, there are also other programs producing flash but with limited capabilities. tom66's idea also seems to be reasonable. Maybe there will be a SVG/SMIL to Flash converter in the future.

If you are a student, you might want to look out for student versions of the Adobe Flash software. These are normally much cheaper but might be restricted in some way.

---

### Post by Kadrus on 2008-08-25
Well,there is something that you can call **similar** to Adobe Flash for Linux.
[Flash4Linux]("http://f4l.sourceforge.net/")
Have a look at it,but you will find a lot of difference between it and Adobe's.

---

### Post by crazyfuturamanoob on 2008-08-25
I think you misunderstood what I want. I don't want to learn programming games with flash. 
I want to do _exactly_ this: [http://www.youtube.com/watch?v=Y5Or01j-bkc]](http://www.youtube.com/watch?v=Y5Or01j-bkc]). I want to learn making
those animations with flash. And I'm not a student.

What is this 'SVG' you are talking about? Is it a text-editor, or is it similar to macromedia flash mx?
Can you do flash animations with SVG? Btw I have never actually seen any flash animation development software, or even had one.

---

### Post by nvteighen on 2008-08-25
> **crazyfuturamanoob said:**
> 
What is this 'SVG' you are talking about? Is it a text-editor, or is it similar to macromedia flash mx?
Can you do flash animations with SVG? Btw I have never actually seen any flash animation development software, or even had one.

SVG is an XML-based language that you can use to create vector graphics and also animations. It's very interesting, as you only need a text editor to use it and XML knowledge.

Most of the interactive features in a SVG document are done through ECMAscript (in other words, Javascript), so it's relatively easy to get a little application with not too much effort.

---

### Post by crazyfuturamanoob on 2008-08-25
> **nvteighen said:**
> SVG is an XML-based language that you can use to create vector graphics and also animations. It's very interesting, as you only need a text editor to use it and XML knowledge.

Most of the interactive features in a SVG document are done through ECMAscript (in other words, Javascript), so it's relatively easy to get a little application with not too much effort.

WTF!? People make animations with xml??? Must be VERY painfully and slow.. O.o

---

### Post by nvteighen on 2008-08-25
> **crazyfuturamanoob said:**
> WTF!? People make animations with xml??? Must be VERY painfully and slow.. O.o
Try it out and you'll be surprised how pleasant it can be. It's a long time since I don't code in SVG, but it's really fun... and, if you don't want to code everything by hand, GIMP supports SVG!

---

### Post by mssever on 2008-08-25
> **nvteighen said:**
> GIMP supports SVG!
As does Inkscape.

---

### Post by crazyfuturamanoob on 2008-08-25
I downloaded Inkscape, and tried it. ROFL! I thought you ment making animations with a text editor!
It turned out to be a nice graphical vector graphics editor. So, how do I make and animation with inkscape?

---

### Post by Kadrus on 2008-08-25
[http://wiki.inkscape.org/wiki/index.php/Animation-(Timeline)](http://wiki.inkscape.org/wiki/index.php/Animation-(Timeline))
[http://hk.youtube.com/watch?v=iwwqmMY-Lt8](http://hk.youtube.com/watch?v=iwwqmMY-Lt8)

---

### Post by nvteighen on 2008-08-25
> **crazyfuturamanoob said:**
> I downloaded Inkscape, and tried it. ROFL! I thought you ment making animations with a text editor!


Er... you can actually write SVG in a text editor, if you want :p

---

### Post by mssever on 2008-08-25
> **nvteighen said:**
> Er... you can actually write SVG in a text editor, if you want :p
And if you're insane. :)

---

### Post by Ruhe on 2008-08-25
Too much bad words about Adobe here)
First of all they did a great step to open source - [link]("http://opensource.adobe.com/wiki/display/site/Home").
Tamarin (flash VM), Flex SDK are open sourced.
Flex SDK gives you everything to compile and run flash applications.
It's more interesting to animate things programatically than drag&drop on timeline.

About IDE's:
As I remember there is only one free editor for action script, which works on linux - old good Scite.
FlashDevelop, wich should be crossplatform (as M$ told us), because it's running on .Net. But unfortunately it doesn't.
FDT - really greate plugin for Eclipse costs a lot, but you can apply for OS(open source) license if you run on OS project.

So you have free&os FlexSDK and Scite and tons of tutorials:
* at adobe site
* kirupa.com

Good luck.

---

### Post by LaRoza on 2008-08-25
> **nvteighen said:**
> Er... you can actually write SVG in a text editor, if you want :p

That is how I did it!

Although I didn't do much in animations. I just did graphics.

---

### Post by crazyfuturamanoob on 2008-08-26
I want to make animations, and I want it to be as easy as pivot stickfigure animator.
Making anims with inkscape is too painful and slow, because I have to hide all other parts of the motion tween but one in each images.
So is there any actionscript producer software that would have similar interface than pivot or flash mx?

I really don't want to use a text editor. Good animations can't be done by that way. GUI is what I want.

---

### Post by Ruhe on 2008-08-26
> **crazyfuturamanoob said:**
> I want to make animations, and I want it to be as easy as pivot stickfigure animator.
Making anims with inkscape is too painful and slow, because I have to hide all other parts of the motion tween but one in each images.
So is there any actionscript producer software that would have similar interface than pivot or flash mx?

I really don't want to use a text editor. Good animations can't be done by that way. GUI is what I want.


Then you have to buy Adobe Flash and use it only on win or mac (no linux version).
It's the only tool for flash animators. Others are silly toys.

---

### Post by Zugzwang on 2008-08-26
> **crazyfuturamanoob said:**
> I really don't want to use a text editor. Good animations can't be done by that way. GUI is what I want.

Sure they can! You need to have some intuition & experience with specifying coordinates, then it works quite well, especially if your animation mainly consists of moving objects around. There are also certain movements which are likely to be even easier in a textual description, like for example some object growing and shrinking representing a heart-beat. It's just not WYSIWYG!

Other good property of this textual description is that you can easily program applications outputting some of these graphics. For example, you could have a database and easily write a program that puts out some graphical animated representation of usage statistics or so (I know that this is not what you need, this is just to give a counter-example to your claim).

---

### Post by crazyfuturamanoob on 2008-08-26
How about ktoon? Can you do animations with it? Even good ones?

---

### Post by mssever on 2008-08-26
> **crazyfuturamanoob said:**
> How about ktoon? Can you do animations with it? Even good ones?
Try it and see.

---

### Post by memories on 2008-08-26
You can probably get Adobe Flash working on Linux using wine/crossoffice, but I've never tried. 

There is also something called swfmill. You can write actionscript and compile it to create an SWF. It's all done with source code, you never draw/drag anything. If you want an example of this, see "Flowplayer" It's a great (closed-source) flash video player for the web. 

Download the flowplayer skinning kit and you'll be able to read/write actionscript and compile it, seeing your changes in the player (in your browser). 

That's one way. I've never used swfmill and the other tools outside flowplayer. 

It's unfortunate there's no Adobe products for Linux. This will probably be the main reason I switch to OS X (which I don't plan on doing because Apple hardware breaks).

---

### Post by crazyfuturamanoob on 2008-08-27
Flash MX would be very good animating software. That's why I was looking after flash. 

But my target is only to get software, with which I can produce animations easily and fast, 
like pivot or flash mx. 

I am pretty good animator with such programs, but I ain't got good software. 
I have even made some stopmotion animations with my webcam.

Is there ANY free software that would let me do animations graphically?
I don't want to make anims with gimp, its too slow and difficult.

---

### Post by mssever on 2008-08-27
> **crazyfuturamanoob said:**
> Is there ANY free software that would let me do animations graphically?
Given that this thread has been going on for some time and it's gotten many replies, and given that no one has suggested suitable software, it's safe to assume that no software exists that fits your requirements.

---

### Post by crazyfuturamanoob on 2008-08-27
> **mssever said:**
> Given that this thread has been going on for some time and it's gotten many replies, and given that no one has suggested suitable software, it's safe to assume that no software exists that fits your requirements.
What about making one? Is it too hard to make one with python and pygame?

---

### Post by Ruhe on 2008-08-27
> **crazyfuturamanoob said:**
> What about making one? Is it too hard to make one with python and pygame?

Flash VM is opensourced and you somebody can give a try to make such simple program.
Don't get me wrong, but all free(some of the opensource) programs are far behind analogous Adobe products. And if you really want to make animations, so pay for Adobe Flash IDE. Sometimes we have to pay)
If you are really good animator, you'll receive spent for this IDE money in a week.

---

### Post by mock_turtle on 2008-08-27
crazyfuturamanoob,

i think you should try synfig
[http://www.synfig.org/]("http://www.synfig.org/")

you can download it directly from ubuntu repos. (universal)

apt-get install synfig

---

### Post by memories on 2008-08-29
Wow. Synfig looks great. 
[http://www.synfig.com/gallery.php](http://www.synfig.com/gallery.php)

One other suggestion is to try getting Flash MX working with CrossOffice or some other emu. I know emulators sound awful, but when the software is supported well, they seem to run as fast, if not faster, than they do on Windows, at least in my experience with games.

---

### Post by crazyfuturamanoob on 2008-08-29
> **memories said:**
> Wow. Synfig looks great. 
[http://www.synfig.com/gallery.php](http://www.synfig.com/gallery.php)

One other suggestion is to try getting Flash MX working with CrossOffice or some other emu. I know emulators sound awful, but when the software is supported well, they seem to run as fast, if not faster, than they do on Windows, at least in my experience with games.

I don't like emulators... often programs don't run on them at all. 
But anyway I don't want flash mx because it is so expensive.

And my own animation software is progressing quite well. 
Currently I can make .avi's with it and it has pen tool.
I am making it with python + pygame. If you are interested PM me.

---

