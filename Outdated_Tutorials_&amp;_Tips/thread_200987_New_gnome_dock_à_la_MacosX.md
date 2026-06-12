---
title: "New gnome dock à la MacosX"
date: 2006-06-21
forum: Outdated Tutorials &amp; Tips
---

### Post by gnumdk on 2006-06-21
gnome-dock (cairo-dock) is a MacosX dock like app.

[http://www.gnome-dock.org/trac](http://www.gnome-dock.org/trac)

It works but is not really usable as this (no placement, ...)

Here is a version working on my laptop:
[http://hibbert.univ-lille3.fr/~cbellegarde/cairo-dock.tar.bz2](http://hibbert.univ-lille3.fr/~cbellegarde/cairo-dock.tar.bz2)

just put this in /opt and use make to build it.

How to use it:
1) I run it like this on Xgl: /opt/cairo-dock/cairo-dock --no-glitz --no-background
2) To add, remove, change applications, you need to directly change source code:

static Icon g_aIcons[] =
{
   {"/opt/cairo-dock/user-home.svg",      "Perso", "nautilus --no-desktop"},
   {"/opt/cairo-dock/gnome-terminal.svg",       "Terminal", "gnome-terminal"}
}
You just need to add elements to this array.

3) By default, MacSlow use screen width for dock width but i don't like this because i was unable to right click near the panel area.
So, if you add applications, you may need to change the dock width by changing this line in the source code:
g_iCurrentWidth = 750;

4) By default, gnome-dock doesn't remember it place on screen. To force screen placement, you will need to change this line in source code:
gdk_window_move(pWindow, 245, 655);  // 245=x, 655=y

The current dock placement is for 1280x800 resolution.

Here the result:
[http://hibbert.univ-lille3.fr/~cbellegarde/cairo-dock.png](http://hibbert.univ-lille3.fr/~cbellegarde/cairo-dock.png)

ps: Sorry for my english ;)

---

### Post by bohboh on 2006-06-21
Is it stable?

I tried Expocity and it sent my system mad, it just wouldnt work.

---

### Post by gookie on 2006-06-21
That looks pretty nice.
I tried executing the make file but it wont compile. It gave me literally hundred lines of error...

---

### Post by bohboh on 2006-06-21
[QUOTE=gookie]That looks pretty nice.
I tried executing the make file but it wont compile. It gave me literally hundred lines of error...[/QUOTE]

Same here.

---

### Post by madchicken on 2006-06-21
try with:

```
sudo apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev
```

This should work.

Bye

---

### Post by bohboh on 2006-06-21
[QUOTE=madchicken]try with:

```
sudo apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev
```

This should work.

Bye[/QUOTE]

I get this:

```

Reading package lists... Done
Building dependency tree... Done
librsvg2-common is already the newest version.
libglitz-glx1 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libglitz-glx1-dev: Depends: libglitz-glx1 (= 0.5.3-0ubuntu2) but 0.5.6-0ubuntu1 is to be installed
                     Depends: libglitz1-dev (= 0.5.3-0ubuntu2) but 0.5.6-0ubuntu1 is to be installed
  librsvg2-dev: Depends: libgtk2.0-dev (>= 2.4) but it is not going to be installed
E: Broken packages

```

Just out of curiosity (and for future reference), how did you find out which libraries it needed?

---

### Post by madchicken on 2006-06-21
I found the libraries reading the first line of 'make' output. Make was missing some libraries...
For your problem: it seems you have a problem with dependancies. I'm not a apt-get expert, so try using synaptic and see if it could resolve problems for you.
From the output I can see that you have only to install libglitz-glx1-dev and librsvg2-dev. They are needed to compile the program.

Bye

---

### Post by gookie on 2006-06-21
Yup. It finally compiled after getting the dependencies.
@bohboh, the libglitz-glx1 installed fine on mine...I have the xgl/compiz repository added on my sources list and I know they came there coz it's the only un-authenticated repository I have (had to add them for aiglx/compiz).

Anyhoo, cairo-dock is working...but I think I need to fiddle with the source (as per instruction)...it has no transparency (black box around it)...cud this be because I have aixgl/compiz on?

Edit: btw, I compiled from svn.

---

### Post by bohboh on 2006-06-21
[QUOTE=gookie]Edit: btw, I compiled from svn.[/QUOTE]

What do you mean?

---

### Post by gookie on 2006-06-21
I downloaded the source from gnome dock's SVN instead of the tar.gz on this post.

```
svn co http://www.gnome-dock.org/svn/
```

---

### Post by pianoboy3333 on 2006-06-23
Are you going to continue development on this? If so, can you post a link as to where I can get the latest source code?

---

### Post by pianoboy3333 on 2006-06-23
Wait, did you develop this? No you didn't you only modded it, I was wondering how to decrease the sensitivity range, becuase I like it, but then I can't click on links at the bottom of firefox and such, becuase the program picks up the mouse, I was wondering if there was a way in cairo-dock.c to decrease the mouse range, so that maybe I could only select something from it if my mouse was closer.

---

### Post by Wallakoala on 2006-06-23
[QUOTE=pianoboy3333]Are you going to continue development on this? If so, can you post a link as to where I can get the latest source code?[/QUOTE]

What makes you think that he didn't post the latest source code?

---

### Post by pianoboy3333 on 2006-06-24
[QUOTE=Wallakoala]What makes you think that he didn't post the latest source code?[/QUOTE]

He has modded the latest source, I want to know if he's going to mod anymore.

---

### Post by amoore on 2006-06-26
can you give more step by step instructions. I would very much like to get this eye candy up and running.

---

### Post by xoui on 2006-06-26
Thanks.
It really works well on my machine.

---

### Post by souled on 2006-06-27
I'm getting this error: ```
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:53:25: error: cairo-glitz.h: No such file or directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:181: warning: assignment makes pointer from integer without a cast
make: *** [cairo-dock] Error 1

``` 

I installed the above packages...

Hmm... Do you have to be using Xgl?

---

### Post by pjot on 2006-06-27
Great dock! However, does anyone have a .svg thunderbird logo? I've searched and searched and searched all night long but no logo is anywhere to be found :( 

**@souled:** Just looking at the output it looks as though you're missing 'cairo-glitz.h', however that's a bit strange as I don't have that file and the compilation gave me no error at all. Since he (gnumdk) recommends us to start the dock with --no-glitz you might get away with commenting out the lines in the source that handles the glitz. You'll probably get tons of error with the lines after the include line (line 53) if they're trying to access the code inside cairo-glitz.h, but it might be worth a try? :)

---

### Post by userundefine on 2006-06-27
[QUOTE=pjot]Great dock! However, does anyone have a .svg thunderbird logo? I've searched and searched and searched all night long but no logo is anywhere to be found :( [/QUOTE]
Yes, you may thank me. :-D 

30 seconds on google.  There does seem to be only one out there.  I found it in an incredibly roundabout way.

---

### Post by Schapie123 on 2006-06-27
[QUOTE=souled]I'm getting this error: ```
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:53:25: error: cairo-glitz.h: No such file or directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:181: warning: assignment makes pointer from integer without a cast
make: *** [cairo-dock] Error 1

``` 

I installed the above packages...

Hmm... Do you have to be using Xgl?[/QUOTE]

I'm having the same problem, and also don't use Xgl

---

### Post by spockrock on 2006-06-27
hmmm wont let me drag it with the middle mouse button.

---

### Post by chanders on 2006-06-27
[QUOTE=spockrock]hmmm wont let me drag it with the middle mouse button.[/QUOTE]

Try using ALT+Left mouse button...

---

### Post by Trocisp on 2006-06-27
How do you install?  I have it downloaded and don't know how to install.

---

### Post by pjot on 2006-06-28
ohhh userundefine :) that's just GREAT! thx alot!

now I just need azureus and I'm good to go ;)

**EDIT:** spellcheck

---

### Post by Laterix on 2006-06-28
[QUOTE=Trocisp]How do you install?  I have it downloaded and don't know how to install.[/QUOTE]
You have to extract the package and then enter the directory and type **make**. This will compile it. If you get errors make sure you have **build-essential** package installed on your system. After compiling you can run it by typing **./cairo-dock**

---

### Post by spockrock on 2006-06-28
[QUOTE=chanders]Try using ALT+Left mouse button...[/QUOTE]

yeah that worked.....

---

### Post by Trocisp on 2006-06-28
[QUOTE=Laterix]You have to extract the package and then enter the directory and type **make**. This will compile it. If you get errors make sure you have **build-essential** package installed on your system. After compiling you can run it by typing **./cairo-dock**[/QUOTE]
```
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:53:25: error: cairo-glitz.h: No such file or directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:181: warning: assignment makes pointer from integer without a cast
make: *** [cairo-dock] Error 1
```
Hmmph, what's to be done? :(

---

### Post by pjot on 2006-06-29
**Trocisp**: You have build-essential? Cause that's the only dependency. 


It looks as though you're missing that d*mn cairo-glitz.h: 
> error: cairo-glitz.h: No such file or directory
and that's really strange that it produces an error for you cause I don't have it either and the compilation works perfectly for me. Computers can be really strange from time to time...

---

### Post by truenemesis on 2006-06-29
Is XGL/Compiz required to have this dock?

---

### Post by Trocisp on 2006-06-29
[QUOTE=pjot]**Trocisp**: You have build-essential? Cause that's the only dependency. 


It looks as though you're missing that d*mn cairo-glitz.h: 

and that's really strange that it produces an error for you cause I don't have it either and the compilation works perfectly for me. Computers can be really strange from time to time...[/QUOTE]
Not sure, how can I check that?

---

### Post by Laterix on 2006-06-29
[QUOTE=Trocisp]Not sure, how can I check that?[/QUOTE]
Type:
```

sudo apt-get install build-essential

```

---

### Post by Trocisp on 2006-06-29
[QUOTE=Laterix]Type:
```

sudo apt-get install build-essential

```[/QUOTE]
apparently I already have it installed...
```
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

---

### Post by truenemesis on 2006-06-30
is XGL/Compiz required to have the dock?

---

### Post by daigorobr on 2006-06-30
You need the developer packages from the unnoficial xgl repos.
Look in the forums for the repos.

---

### Post by amoore on 2006-07-02
How do you uninstall this? its cool, but it just doesn't work for me.

---

### Post by calvinthomas on 2006-08-09
I know this hasn't been posted in for a while but I wondered if anyone could help me, I have downloaded tar.gz from the original and extracted it, gone in a terminal to where I extracted it to and then typed make and it gave me this message:

make: Nothing to be done for `all'.

Can anyone tell me what I need to do? Any help really appreciated

Calv

---

### Post by KillerBOB on 2006-08-09
Hi!

Calvinthomas, just do ```
make clean
``` and then ```
make
``` to compile. Then ```
./cairo-dock
```. For me it works and looks very nice with Xgl/Compiz. Don't know how it will look without.

/Bob

---

### Post by Tonio on 2006-08-10
There's a new version available since yesterday : 
[http://www.gnome-dock.org](http://www.gnome-dock.org)

---

### Post by Kobalt on 2006-08-10
What a wonderfull little dock. It's really good looking, smooth and efficient. I love it !! I'm now tweaking it to fit my liking. 
I'll be following it's developpment from close range ;)

Cheers ! :rolleyes:

---

### Post by Tiftof on 2006-08-10
Is there a way to keep this dock on top? I can't seem to find an option to disable autohide

---

### Post by Kobalt on 2006-08-10
Tell me, I'm searching for a way to make this baby start at each session. I've tried adding start-cairo-dock.sh via System > Settings > Sessions but it won't work. I've tried editing the /etc/rc.local file by adding the command : ```
cd /home/klattimer/workspace/cairo-dock
./cairo-dock --no-glitz &
```
But again no luck it's not working... :( Has anyone an idea on how to work it out ? 

Thanks & Cheers ! :rolleyes:

---

### Post by jd_ on 2006-08-21
Hi, I checked out the latest svn version and noticed some changes in the way dock's position is defined in the source code (no more window_move() but offsets rules). I wonder how one could have the dock to be at the bottom of the screen, hiding when inactive and coming back on the foreground when the mouse hits the bottom edge.

Thank you :)

---

### Post by Kobalt on 2006-08-22
Hi,
I've installed the latest version of the dock and it does exactly what you want. By default it positioned itself on the bottom of my screen and it hides automaticaly when I get my cursor out of the bottom of the screen...

---

### Post by jd_ on 2006-08-22
*chuckles* Well, I'll try to edit offsets and see if my dock hangs on :)

---

### Post by calvinthomas on 2006-08-22
Wow, I got this installed and it looks absolutely amazing! I don't understand how to add applications though, it says in the original post to edit the source file but I don't understand that, can anyone help?

Calv

---

### Post by ykpaiha on 2006-08-22
he program 'cairo-dock' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 452 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

sadly dead .... see it next time

---

### Post by moebis on 2006-08-25
Has anyone figured this one out yet?
```

cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:53:25: error: cairo-glitz.h: No such file or directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:181: warning: assignment makes pointer from integer without a cast
make: *** [cairo-dock] Error 1

```
I can't find libcairo2-1.2 ....ubuntu comes with 1.0.4 or something, without glitz compiled in. If you go to the developer page his only helpful hint for everyone is:
```

08/08/06 21:56:36: Modified by klattimer

    * status changed from new to closed.
    * resolution set to invalid.

build librsvg with cairo, and cairo with glitz

install devel packages, comeon people these are the basics!

```
....amazing, and all least the beerorkid repos USED to have libcairo2-1.2.2 but not the libcairo2-1.2.2-dev that is needed to compile this beast. Would be great is someone out there can either point us to a solution or build a deb for us to play with this. Thanks.

---

### Post by zorg on 2006-09-01
> **moebis said:**
> Has anyone figured this one out yet?
```

cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:53:25: error: cairo-glitz.h: No such file or directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:181: warning: assignment makes pointer from integer without a cast
make: *** [cairo-dock] Error 1

```
I can't find libcairo2-1.2 ....ubuntu comes with 1.0.4 or something, without glitz compiled in. If you go to the developer page his only helpful hint for everyone is:
```

08/08/06 21:56:36: Modified by klattimer

    * status changed from new to closed.
    * resolution set to invalid.

build librsvg with cairo, and cairo with glitz

install devel packages, comeon people these are the basics!

```
....amazing, and all least the beerorkid repos USED to have libcairo2-1.2.2 but not the libcairo2-1.2.2-dev that is needed to compile this beast. Would be great is someone out there can either point us to a solution or build a deb for us to play with this. Thanks.

First of all sorry for my English;

I had the same error,but founded a solution.I downloaded cairo 1.2.0 source and compiled it with --enabled-glitz option.After I were able to compile the dock.I also made a .deb package(I installed cairo with checkinstall -D)
and if somebody wants to try it I will send.(however I'm not guru and I don't know if it goes)
If you donloaded the mod version don't forget to put it in /opt or modify cairo.c

Now I can run well the dock just under Xgl;under X it goes very slow and I have a bad black background

---

### Post by michaeljb2005 on 2006-09-05
> **calvinthomas said:**
> Wow, I got this installed and it looks absolutely amazing! I don't understand how to add applications though, it says in the original post to edit the source file but I don't understand that, can anyone help?

Calv

If you open the source file, I forget the name of which file that is at this point (not at my computer).  There is a place where the icons and their counterpart commands are listed.  Manipulate this list to reflect which icons and binaries you want the dock to use.  Make sure to use svg icons.  Then recompile the source code and it should contain the icons linked to the programs that you specified.

---

### Post by zyml on 2006-09-05
> **zorg said:**
> First of all sorry for my English;

I had the same error,but founded a solution.I downloaded cairo 1.2.0 source and compiled it with --enabled-glitz option.After I were able to compile the dock.I also made a .deb package(I installed cairo with checkinstall -D)
and if somebody wants to try it I will send.(however I'm not guru and I don't know if it goes)
If you donloaded the mod version don't forget to put it in /opt or modify cairo.c

Now I can run well the dock just under Xgl;under X it goes very slow and I have a bad black background

Where do you add the --enabled-glitz option? Sorry but I'm a linux noob :mrgreen:

---

### Post by GPH on 2006-09-05
> ./cairo-dock: symbol lookup error: ./cairo-dock: undefined symbol: cairo_push_group


Weird...

---

### Post by Hobbes on 2006-09-10
Hey, those people out there who haven't gotten this to work because of the glitz error it is in fact a problem with the cairo pkg.

However, I can't find any alternative cairo pkg that has glitz enabled, and if anyone either knows where to locate such a package, or can create one and post it here, that would be amazing.

I have been trying to get this dock thing working for a bit now, and would really appreciate a little bit of help so I can leap the final hurdle :)

---

### Post by GPH on 2006-09-10
> **Hobbes said:**
> Hey, those people out there who haven't gotten this to work because of the glitz error it is in fact a problem with the cairo pkg.

However, I can't find any alternative cairo pkg that has glitz enabled, and if anyone either knows where to locate such a package, or can create one and post it here, that would be amazing.

I have been trying to get this dock thing working for a bit now, and would really appreciate a little bit of help so I can leap the final hurdle :)

[http://www.gnome-dock.org/trac/wiki/BuildingCairo](http://www.gnome-dock.org/trac/wiki/BuildingCairo)

---

### Post by Hobbes on 2006-09-10
Thanks, now I know what options to enable besides just --enable-glitz.

Unfortunately I still get error messages when trying to make gnome-dock.

```
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgdk-x11-2.0.so: undefined reference to `cairo_xlib_surface_create_for_bitmap'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgdk-x11-2.0.so: undefined reference to `cairo_xlib_surface_create'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgdk-x11-2.0.so: undefined reference to `cairo_xlib_surface_set_size'
collect2: ld returned 1 exit status
make: *** [cairo-dock] Error 1

```

Things that I can think of: I'm using a 1.2.2 source of cairo, do you need 1.2.4 or 1.2.0? also I have it in my home directory, do you need to compile cairo somewhere specific (I'm kind of a noob when it comes to compiling stuff, thanks to Ubuntu)

As always, all help is greatly appreciated, thank you all forum and Ubuntu gurus :)

---

### Post by Hobbes on 2006-09-10
Well, apparently the answer was getting cairo 1.2.4.

So, to anyone who wants this sexy launch bar, simply download [cairo 1.2.4]("http://cairographics.org/releases/cairo-1.2.4.tar.gz")

extract the archives and simply type:
```

./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc

```
then
```
make
```
then
```
sudo make install
```

then you should be able to make the cairo-dock and run it, enjoy :)

---

### Post by niko7865 on 2006-09-11
I was getting the same errors as you Hobbes and istalling cairo 1.2.4 fixed that and I was able to compile just fine. However when I try to run it I get this error

```
./cairo-dock: symbol lookup error: ./cairo-dock: undefined symbol: cairo_push_group

```

Anyonehave any thoughts?

---

### Post by mobilehavoc on 2006-09-11
Crap...got to the same point and I get the same "cairo_push_group" error.

Any ideas at all on how to fix this? So close and yet so far...

---

### Post by gabr1el on 2006-09-12
the cairo_push_group error is actually a version mismatch with cairo.  try hardcoding LD_LIBRARY_PATH before calling the cairo-dock binary a la:

LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH /opt/cairo-dock/cairo-dock

---

### Post by mobilehavoc on 2006-09-12
Well having the full path for cairo-dock seemed to make it hard for it to find the SVG files but the following worked when in the local directory

LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH ./cairo-dock --no-glitz &

Now to figure out how to configure the icons and shortcuts!

---

### Post by gabr1el on 2006-09-12
that's probably due to the fact that it can't find the svg icons.  do this:

open up the cairo-dock.c file before it's compiled.  up towards the top you'll see an array that contains the path to the .svg icon, title, and program path.  you need to modify that array to make sure that the paths and icons are correct.

now "make clean ; make"... give it another whirl.  there's a reason this thing isn't ready for prime-time :wink:

---

### Post by viraldhimar on 2006-09-12
Hey guys, 

I've gotten this to work..although I had to use the --no-glitz & option. It works in aiglx or metacity but its very slow. Is this what glitz takes care of? Also has anyone tried to move it? I noticed that when I moved to the edge of it(while holding down right mouse buttion) i got a resize cursor, but resizing it left a black border

---

### Post by mobilehavoc on 2006-09-13
The biggest problem I came across during my customization is the thing currently only works with SVG icons that are 48x48. I tried to use some 64x64 icons from gnome-look and they kept getting cut-off. Pain in the ***.

Oh well, hopefully they will fix it soon. Otherwise this thing is wicked fast, looks amazing and very functional.

---

### Post by joTi on 2006-09-13
> **gabr1el said:**
> the cairo_push_group error is actually a version mismatch with cairo.  try hardcoding LD_LIBRARY_PATH before calling the cairo-dock binary a la:

LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH /opt/cairo-dock/cairo-dock


Thanks for your info, but where do you type this:

"LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH /opt/cairo-dock/cairo-dock"


If i type it in the terminal, the dock comes up and i can choose to execute one program, but as soon as the cursor leaves the dock it's gone and i have to start it again with that long line.

Is it a file i should modify to make the changes permanent?

Thanks guys,
Long time reader, first time writer :)

---

### Post by mobilehavoc on 2006-09-13
Are you sure the thing isn't just auto-hiding...move your mouse cursor along the bottom of the screen and it should pop back up.

To check if it's running...type this into a console..

ps -e | grep cairo-dock

If that doesn't return anything then it's not running, otherwise it should return all running cairo-dock processes.

---

### Post by joTi on 2006-09-14
> **mobilehavoc said:**
> Are you sure the thing isn't just auto-hiding...move your mouse cursor along the bottom of the screen and it should pop back up.

To check if it's running...type this into a console..

ps -e | grep cairo-dock

If that doesn't return anything then it's not running, otherwise it should return all running cairo-dock processes.


I noticed a new behavior of the cairo-dock.
I execute the previous mentioned string, it starts up all nice and good, but as soon as i come about a inch or closer it just folds down, and i can't even execute a program.
I've been scanning all edges of the screen and does not pop-up again.
 
And when i run "ps -e | grep cairo-dock" it returns:
"5250 pts/0    00:00:00 cairo-dock"

Any guesses? 

I'm using this build:
"cairo-dock-0.0.1b"

Ps. I'm sorry if my grammar or spelling is completly off the tracks, i'm from Sweden.

---

### Post by MetalMusicAddict on 2006-09-14
Just a side question. Apple tends to go after projects like these. How will Gnome-docks devs handle this?

---

### Post by JPMaximilian on 2006-09-14
> **zorg said:**
> First of all sorry for my English;

I had the same error,but founded a solution.I downloaded cairo 1.2.0 source and compiled it with --enabled-glitz option.After I were able to compile the dock.I also made a .deb package(I installed cairo with checkinstall -D)
and if somebody wants to try it I will send.(however I'm not guru and I don't know if it goes)
If you donloaded the mod version don't forget to put it in /opt or modify cairo.c

Now I can run well the dock just under Xgl;under X it goes very slow and I have a bad black background

It works for me too but it is very, very slow, and there is a black background.  Any ideas on how to fix this?  Thanks.

---

### Post by joTi on 2006-09-14
**mobilehavoc**, do you have any solutions or ideas? 

anyone? 


would love to get this app up and running. :roll:

---

### Post by JPMaximilian on 2006-09-14
> **MetalMusicAddict said:**
> Just a side question. Apple tends to go after projects like these. How will Gnome-docks devs handle this?

I think the best bet is to deny everything and say that development took place simultaneously, yet independently, of Apple.  :D

---

### Post by raul_ on 2006-09-14
i downloaded the one on the page (that says pre-release) but the compiler complains about pretty much every line...am i the only one?

---

### Post by hizaguchi on 2006-09-15
Ah ha!  I disabled autohide.  Just go through the cairo-dock.c file and find all the "move = *some equation*" lines and replace the equation with 0, then run make again.

Now, somebody help me with the --no-glitz option.  Is it supposed to be necessary?  Mine doesn't display icons when I run it with that option, but it seems fine without it.

Edit: Woops, I tried make again after adding the icons to the directory and it works fine now.

Is this thing crazy processor hungry for you guys?

Edit one more time: Looks like the crazy processor usage was because of my pathetic attempt to stop the autohide.  I reverted to the normal code and it's cool now.  Anybody know a good way to stop it from hiding?

---

### Post by hizaguchi on 2006-09-15
Sweet!  No more autohide.  You just have to cut out all the stuff in the move-up and move-down sections, but leave the sections themselves so the variables exist but don't do anything.

---

### Post by hizaguchi on 2006-09-15
Ok, ok, one more thing.  Does clicking just above the dock cause applications to launch for you?  For me, if I click in the area where the icons would scale to (but not while they're scaled), it launches them anyway.  Did I break this, or was it pre-broken?

---

### Post by mobilehavoc on 2006-09-15
pre-broken...this is why I had to re-enable Auto-hide otherwise if it's not hidden you can accidentally launch apps by clicking slightly above the icon.

---

### Post by hizaguchi on 2006-09-15
That sucks.  Oh well, I'll just move my working applications up slightly until there's a fix. :)

---

### Post by JPMaximilian on 2006-09-15
> **hizaguchi said:**
> Ok, ok, one more thing.  Does clicking just above the dock cause applications to launch for you?  For me, if I click in the area where the icons would scale to (but not while they're scaled), it launches them anyway.  Did I break this, or was it pre-broken?

Could you be more specific in your fix for disabling auto-hide?  Thanks!

---

### Post by mobilehavoc on 2006-09-15
From compiz.net forums...

Simply comment out 2 lines of code.

near line 715:
```

// g_uiHideHandlerId = g_timeout_add (15, move_down, (gpointer) pWidget);
```

and near line 820

```
// g_uiHideHandlerId = g_timeout_add (15, move_down, (gpointer) pWidget);
```

Worked perfectly for me.:biggrin:

---

### Post by hizaguchi on 2006-09-15
Heh, that would have been easier.  Google fails me again!  I broke the thing like 20 times tinkering around before I finally just cut out the whole move-up and move-down section.  Like this:
```
static gboolean
move_up (gpointer pWidget)
{
}

static gboolean
move_down (gpointer pWidget)
{
}
```
The other method is probably better. :)

---

### Post by one_stinky_bum on 2006-09-16
I'm tempted to say Kiba dock is more advanced, with a config GUI and less CPU utilization on my Centrino 1.7Ghz, 2GB ram, i915 gateway tablet pc. The thing that cairo-dock has got down is the sensible defaults. There's no crazy bouncing around like kiba dock... I've spent well over half an hour and I can't get it to act half decent. If only kiba came with sensible defaults...

Anyways, if you can't get it to work, and you are on dapper, check out the previous post on downloading cairo-1.2.4. I also run it with the command supplied by a previous poster (run in the directory where you typed "make":```
LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH ./cairo-dock --no-glitz &
```
works for me, and I'm using aiglx+compiz. Just a bit slower/power hungry than kiba.

---

### Post by JPMaximilian on 2006-09-16
I installed kiba.  It is an absurd program.  How does my icons going crazy whenever I move my mouse over them make me more productive?  I don't know, maybe I just don't see the point.

---

### Post by one_stinky_bum on 2006-09-16
Hehe - you should play around with the config options. Right click in a clear area in the dock and select "Kiba Utils"->"gset kiba"

I know it's quite a waste of time - the kiba devs should set nice defaults like gnome-dock. But hey, it's free. I'm not complaining (that much).

Does anyone have sensible values for the physics config (elasticity, gravity, spring constant etc) that makes it act more like OS X? Care to share?

---

### Post by JPMaximilian on 2006-09-16
I tried for a bit, but it just made it so all the icons collected in the upper right-hand corner of my desktop.  I agree, a simple no frills dock option would be great.  As it is, it just seems like some crazy physics simulation.  I mean honestly, how could you actually use this dock?  You'd spend hours just chasing your icons around.  Maybe its actually a game?

---

### Post by aceracer24 on 2006-09-16
> **JPMaximilian said:**
> I installed kiba.  It is an absurd program.  How does my icons going crazy whenever I move my mouse over them make me more productive?  I don't know, maybe I just don't see the point.

Obviously, you and those that tried out kiba-dock here didn't really look into the options available or bother to come to compiz.net and read some of the forums. Kiba-dock has gone through alot of changes recently and is by far more stable and usuable then it used to be. Sure it's got some flaws but then so does everything else in active development. As for your icons going bad, you can change the model type. It's probably deaulted to dock instead of rope. Rope will hold the icons together where dock will let them each freely move about. Set to rope model and check the pulse and E17 pulse in gset-kiba and your icons will no longer fly about. If you want a zoom that is SIMILAR to cairo-dock, then disable the pulse and E17 pulse and enable the zoom. ALthough the developer for gset-kiba hasn't been around to update gset-kiba so you might have to go into gconf-editor to manually set some of the option like zoom. Zoom will act similar to cairo-dock but it's a little quirky as sometimes if your not on the icon correctly and you click it to start an app, they might fly off to the side. 

YOu should give kiba-dock a more fair chance then what it sounds like some of you are doing. It's very usable in it's current state and always getting updated. Gravedigga over at compiz.net is always making changes and adding requests.

Here is a vid I just did showing the rope model with zoom active
[http://www.aceracerftw.com/pics/kiba.mpeg]("http://www.aceracerftw.com/pics/kiba.mpeg")

Here is a link to where you can get the latest version AND find out what all you need to compile.

[http://www.compiz.net/topic-3841-info-post](http://www.compiz.net/topic-3841-info-post)

If you run 64bit I have a .deb on my repo 
deb [http://www.aceracerftw.com/amd64/ubuntu](http://www.aceracerftw.com/amd64/ubuntu) dapper main

for the key you can go directly to that link and read the readme there.

---

### Post by hizaguchi on 2006-09-16
But, does Kiba do anything that Gnome-Dock doesn't?  I mean, anything useful.  Icons flying around the screen doesn't count. :)  Gnome-Dock is a very nice looking, high performance (for me at least), and sensibly configured launcher bar.  If Kiba can do more than that, like hold useful applets, dock minimized windows, or make Koolaid, then it sounds good.  But judging from the video I think I'll stick with Gnome-Dock.  I've already got it like I want it.

---

### Post by one_stinky_bum on 2006-09-16
well, all we were asking for are sensible defaults... just one pane that says:
Dock Behavior:
x Like Mac OS X
x Minimal Effects
x Moderate Effects
x Extreme Effects

And then put all the gravity, spring constant, elasticity sliders under some "advanced" tab. 
Minimal effects just gives you a dock with a solid background and no fancy gimmicks - no bouncing, wiggling, piling on top of one another. As basic as it gets... user clicks on icon, app launches.
Moderate effects could include the mouseover pulse/zoom thing (which is cool), bounce on execution, transparent dock background etc. Just a prettied up "Minimal effects" setting with a little more drama. 
Extreme could include a good mix of the crazy-cool features, sort of how Kiba is configured by default now.

I think I'll come back when (if ever?) Kiba can manage open windows. Right now it's just a launcher, and I use a drawer on the panel for that. It would be nice to get rid of all panels and just have Kiba in autohide... now that would be nice!

Thanks for your tips though.

---

### Post by one_stinky_bum on 2006-09-16
does gnome-dock manage windows?

BTW, the icons pile up in the upper left corner when you set inertia to zero. To get them back, change the icon size (kiba-gset->launchers->model).

---

### Post by JPMaximilian on 2006-09-16
> **aceracer24 said:**
> Obviously, you and those that tried out kiba-dock here didn't really look into the options available or bother to come to compiz.net and read some of the forums. Kiba-dock has gone through alot of changes recently and is by far more stable and usuable then it used to be. Sure it's got some flaws but then so does everything else in active development.

I just don't see the point of icons flying around like that.  It must have been very difficult to write kiba-dock (I'm not a programmer, its all magic to me), and I respect everyone working on it.  But as far as practical value, I think there is something lacking.  Gnome-dock has some frills (for example magnification), which is cool looking and it adds to the functionality of the dock.  I don't see the effects of kiba-dock doing this.  But I'll tell you what, I'll install kiba-dock and see if I can't make it semi-functional, *for my needs*.  Maybe I just didn't give it an honest go before.  I'll post how it goes.

---

### Post by mobilehavoc on 2006-09-16
> **JPMaximilian said:**
> I just don't see the point of icons flying around like that.  It must have been very difficult to write kiba-dock (I'm not a programmer, its all magic to me), and I respect everyone working on it.  But as far as practical value, I think there is something lacking.  Gnome-dock has some frills (for example magnification), which is cool looking and it adds to the functionality of the dock.  I don't see the effects of kiba-dock doing this.  But I'll tell you what, I'll install kiba-dock and see if I can't make it semi-functional, *for my needs*.  Maybe I just didn't give it an honest go before.  I'll post how it goes.
I totally agree with you...I tired Kiba dock and it just didn't add anything except being able to play with the icons around the screen which in reality doesn't help at all.

Gnome-dock is still early stages but it does what I need...autohide and zoom/magnication. Icons bounce a few times to launch. It can only get better from here on. Definitely a big fan of gnome-dock now...

---

### Post by JPMaximilian on 2006-09-16
Ok, here is my honest go of kiba-dock.  I followed the instructions found here:

[http://fredcpp.wordpress.com/2006/09/03/install-kiba-dock-in-xgl-compiz/]("http://fredcpp.wordpress.com/2006/09/03/install-kiba-dock-in-xgl-compiz/")

Which worked fine for me, here are my settings that with a little messing around I got to somewhat close to the OSX dock.  
Physics tab:
elasticity:0
Fricion: 130ish
Inertia: .8ish
K: 18ish
Throw Gravity: 5ish
Gravity Multiplier: 85ish

Luanchers Tab:
Model Type:
Dock
Gravity: 5000
Wobbly Spring: 0
Spring While Dragging: Unchecked

The advantages of gnome-dock:
Icons freak out less.

Advantages of Kiba-dock:
Ability to add launchers without modifying the source/recompiling.  Ability to move the dock around.  More customization (some of which will drive you mad).  You can move the position of icons within the dock (once you have it tweaked right).

Let me know what you all think.

---

### Post by hizaguchi on 2006-09-16
Alrighty, I'll see if that repo linked above works with Edgy and give it a fair comparison.  In the mean time though, has anybody played with Engage lately?  It handles applets and reasonable effects and minimized windows and even a clock, but last time I checked you had to set up an icon for every program you were ever planning to run or else you got a big ugly "?" in the dock.  Is that still the case?  Is there a 64-bit engage repository floating around somewhere?

---

### Post by aceracer24 on 2006-09-17
In all honesty, kiba wasn't isn't currently designed with all the features you want. It was first and formost something cool to try for someone that was reletively new to programming int he language that kiba uses. Kiba is in actuality, based off of some of the code in cairo dock from my understanding. Although very loosly. If you come to compiz.net and check out the forum kiba-dock, you will see that gravedigga would like to eventually add more functionality. His skills in certain aspects are not up to par and has sinced ask for some help ..I beleive with glitz although I can't be certain. 

Yes, kiba is mostly an application launcher. Thats it. Plans to do more are in order but it's mostly just a couple people working on it. It's made great leaps from when i first installed it a couple months ago. If you tried it and it doesn't meet your needs, so be it. I just hate hearing people that gave it a 5 min trial and gave up without bothering to read about it first and then talk smack about it. It's not fair to the people that have put alot of time and effort into it. Think how you would feel in the same position.

---

### Post by one_stinky_bum on 2006-09-17
I've done college tech support for 4 years and counting... users always complain and hardly ever think of the devs. There's that ever rare "everything worked great, thank you" one gets occasionally, but that's just the way things work - don't expect people hitting forum after forum digging up information.

---

### Post by aceracer24 on 2006-09-17
Ya, I suppose your right. Still though, had to be said.

---

### Post by mobilehavoc on 2006-09-17
Warning...the latest Compiz updates break Gnome Dock (cairo-dock)...so if you need to have it working, don't update your Compiz packages.

---

### Post by jimmygoon on 2006-09-17
> **JPMaximilian said:**
> It works for me too but it is very, very slow, and there is a black background.  Any ideas on how to fix this?  Thanks.

make sure AIGLX/XGL is running with Compiz as the window manager and then run "./cairo-dock --no-glitz"

---

### Post by Jolly Roger on 2006-09-18
So does this fancy dock work with the newest Compiz updates at all? Is there any workaround to get it working? I installed everything seemingly okay but I type ./cairo-dock into the terminal and it tells me the file doesn't exist.

---

### Post by schambee on 2006-09-18
anyone that knows how to change cairo-dock.c to get rid of the 3*icons_height of the window? i want to change it to icon_height, but if i do so, the dock (icons) are no more available.

thx

---

### Post by mrgnash on 2006-09-18
It just sits in the middle of the screen flickering on mouseover. Impressive ;)

---

### Post by joTi on 2006-09-18
> **mrgnash said:**
> It just sits in the middle of the screen flickering on mouseover. Impressive ;)

Same here :)

Is this due to the Compiz updates?

I'm forced , as of now, to run Kiba-dock instead because of this.
Would really like to get the cairo-dock to run smoothly again :P


Edit:
Is there an workaround yet on this matter?

---

### Post by nimes on 2006-09-20
this problem solved

Solution:

1. open csm (compiz setting manager)
2. General options ---> Numeric Values ---> Vertical virtula size
3. this value change from 1 to 4

thats it.

---

### Post by Hobbes on 2006-09-20
wow, thanks for the fix. Not sure how you figured it out, very impressive.

---

### Post by nimes on 2006-09-21
[http://www.compiz.net/topic-4524-gnome-dock-last-update-issues](http://www.compiz.net/topic-4524-gnome-dock-last-update-issues)

:)

---

### Post by joTi on 2006-09-22
Awesome, i knew it was going to be simple to fix, but not as simple as this ;D


May i add a request for some icons, i have noticed that .svg icons is not that common, and hard to get.

Here's some apps i need icons for:
**WengoPhone, *Thunderbird**, xChat, Azureus, XMMS & DC++**
**ddidn't get the thunderbird icon mentioned before in this thread to work.*

If someone has (or know where to get) some or all of this icon's i would be super-happy, because i've searched my *** off for them :)

---

### Post by JPMaximilian on 2006-09-22
> **joTi said:**
> 
May i add a request for some icons, i have noticed that .svg icons is not that common, and hard to get.

Can you just save .pngs or other image formats as .svg in gimp?  Is it more difficult than that?

---

### Post by joTi on 2006-09-22
Actually I have tried that, but for some reason Gimp doesn't recognize the SVG format.

I think this is because it's vector based, and there is some form of programming required to make an icon.

But i have been wrong before, so anybody feel free to correct me :)

---

### Post by reda_ea on 2006-09-25
GIMP doesn't recognize SVG, it's normal.
Try with Inkscape.

and SVG are very common, almost all the new icon themes use it.

but yeah png support would be nice, I'm sure it could easily be implemented in the program.

---

### Post by joTi on 2006-09-25
Okay, will give Inkscape a shot.

So .svg is common, i probably just suck at searching icons ;)

Thanks btw


EDIT:

Have played some with Inkscape now.
First icon (thunderbird) was a pleasure to convert to .svg.

Then it started to really behaving weird.
When i save it doesn't write the picture to the file.

I first solved it (i thought) by saving to a different folder, and voila the image was saved.
But only as a thumbnail it appears.
Because as soon as i open them in a imageviewer the image is not there, but they are there as thumbnails, it's just empty "inside" the file, hence cairo-dock just shows transparancy where the icon should be.
Except for the thunderbird icon that works perfectly.

I didn't edit any settings between the thunderbird icon and the others.
Very weird, i'm clueless.


Sorry for off-topic.

---

### Post by DarkAngel88 on 2006-09-27
Hi,

I tried running cairo but I get an error saying : Floating point exception.

I really want this app. to work on my ubuntu but don't know what to do next.

Anyone can help me on this one please ?

---

### Post by Hobbes on 2006-09-28
Can you post the full error msg (usually it is not really the fpe but what else is listed that is important)

Did you follow the above guide?

1.) Download Cairo 1.2.4, ./Configure with options above, make, sudo make install

2.) Download cairo-dock, make, ./cairo-dock --no-glitz &

(for newish compiz)
3.) Go to compiz settings -> general options -> numeric values -> vertical virtual size  change to 4

Good Luck all, I have it running on two computers now, pretty sweet.

---

### Post by DarkAngel88 on 2006-09-28
Thank you for your reply Hobbes

Here is the output when I'm trying to compile cairo 1.2.4 
with this command "./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc"

```
checking for vasnprintf... no
checking for cos in -lm... yes
checking for compress in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for X... no
checking for cairo's Xlib backend...
checking for xlib... checking whether cairo's Xlib backend could be enabled... no (requires X development libraries)
checking for cairo's Xlib Xrender backend...
checking whether cairo's Xlib Xrender backend could be enabled... no (requires --enable-xlib)
checking for cairo's Microsoft Windows font backend...
checking whether cairo's Microsoft Windows font backend could be enabled... no (disabled, use --enable-win32 to enable)
checking for cairo's PNG backend...
configure: WARNING: Could not find libpng in the pkg-config search path
checking whether cairo's PNG backend could be enabled... no
configure: error: requested PNG backend could not be enabled

```

Running under quinn aiglx.

Thanks for looking !

---

### Post by Hobbes on 2006-09-30
I have it working in AIGLX with quinn's compiz, so there is some hope...

I think I may have gotten this once: try

```
sudo apt-get install libpng12-0 libpng12-dev libpng3 libpng3-dev 
```

---

### Post by DarkAngel88 on 2006-10-01
Hi Hobbes !

You were right about the missing packages.

But now, I'm getting this : 

```
checking for png... yes
checking whether cairo's PNG backend could be enabled... yes
configure: creating src/cairo-png.pc
checking for cairo's glitz backend...
checking for glitz... checking whether cairo's glitz backend could be enabled... no (requires glitz http://freedesktop.org/Software/glitz)
configure: error: requested glitz backend could not be enabled

```

Thank you for your time and your help !

---

### Post by Hobbes on 2006-10-03
do u have libglitz-glx1-dev and libglitz1-dev installed?

also did you get your cairo from here?
[http://cairographics.org/releases/cairo-1.2.4.tar.gz](http://cairographics.org/releases/cairo-1.2.4.tar.gz)

in other news: I now use kiba dock([http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package](http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package)) more often anyway, not only is there a .deb available that works perfectly... but also much more easily added to and configured.

---

### Post by GPH on 2006-11-17
Here's how I did it on my Edgy:
[B]
1. Install these packages[/B]

```
sudo apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev
```
[B]
2. Make sure you have all the necessary packages to compile.[/B]

**3. Download Cairo 1.2.6**

[http://cairographics.org/releases/cairo-1.2.6.tar.gz](http://cairographics.org/releases/cairo-1.2.6.tar.gz)

**4. Install Cairo 1.2.6**

```
./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc

```

```
make
```

```
sudo make install
```

**5. Download cairo-dock**

[http://www.gnome-dock.org/prerelease/cairo-dock-0.0.1b.tar.gz](http://www.gnome-dock.org/prerelease/cairo-dock-0.0.1b.tar.gz)
[B]
6. Extract the tarball in /opt[/B]

**7. Install cairo-dock**

```
make clean
```
```
make
```

Also, change your virtual vertical size in Beryl from 1 to 2, otherwise it will probably bug. That's a weird fix found by someone in this thread, but it works.
[B]

To open the dock, use ```
./cairo-dock --no-glitz
```[/B]
[B]
To add launchers, play with cairo-dock.c and redo ```
make
``` once you've saved the file.[/B]

This dock is much better than kiba-dock, but it's still in early development and you have to configure things manually, so be prepared to spend a little more time than just dragging icons into your dock. Also, it only accepts icons in .svg for the moment, but it's fairly easy to convert .png to .svg using InkScape. Good luck!

[IMG]http://img297.imageshack.us/img297/285/screenshot1om7.png[/IMG]

---

### Post by Kryten107 on 2006-11-17
GPH, you should make that Howto a seperate thread so people can find it easier. It worked for me until I extracted the tarball to /opt. When I tried to make it, I got this:
```
devin@Nayru:/opt/cairo-dock$ make
make: Nothing to be done for `all'.
```

Trying to run the dock gives this:
```
devin@Nayru:/opt/cairo-dock$ ./cairo-dock
Floating point exception
```

Ideas, anyone?

---

### Post by Rob2687 on 2006-11-17
cairo dock hasn't been touched in months.

---

### Post by GPH on 2006-11-18
> **Kryten107 said:**
> GPH, you should make that Howto a seperate thread so people can find it easier. It worked for me until I extracted the tarball to /opt. When I tried to make it, I got this:
```
devin@Nayru:/opt/cairo-dock$ make
make: Nothing to be done for `all'.
```

Trying to run the dock gives this:
```
devin@Nayru:/opt/cairo-dock$ ./cairo-dock
Floating point exception
```

Ideas, anyone?

Did you try ```
make clean
``` before make ? If you get past this point, try to run cairo-dock with ```
./cairo-dock --no-glitz
``` in its directory.

> cairo dock hasn't been touched in months.

True, but it's still the best OS X dock imitation in Ubuntu as far as I'm concerned.

---

### Post by Kryten107 on 2006-11-18
Ah, thanks, got it working now. :)
I still think it should be reposted as a nice howto.

---

### Post by 4KvRMU7Nnv on 2006-11-24
YES! I finally managed to get it installed and booted on startup.  Looks amazing.  Now I need help.  The command set for the "Home" folder icon is looking for the Home folder of (I assume) the person who made the package I downloaded to Install it.  Naturally, it can't find that folder because it isn't on my computer, I just can't figure out how to change the path! :confused:

---

### Post by 23meg on 2006-11-24
Sorry to go off-topic, but does anyone know of a more recent Edgy package of kiba-dock than the ones linked to [here]("http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package")?

---

### Post by loell on 2006-11-24
i think there is no recent pacakge for kiba-dock , as gravedigga(developer) is still busy in his studies, and doesn't have an internet connection yet on his new location.

---

### Post by 4KvRMU7Nnv on 2006-11-25
Ok i figured out my old problem (I hadn't been using "make" i was stupid and assumed that it would update itself if i changed the source but you have to make the folder as well.  ANyway, whenever I run the terminal application from my dock, It always opens a terminal as if it was in the folder that my cairo dock is located (/opt/cairo-dock).  I am looking for a command to force the terminal to open in the home folder.  Thanks!

---

### Post by mayjava on 2006-11-25
please i am a nem person with linux and i must say i enjoy using ubuntu,i have treid installing this dock but whenever i want to run it i get this error 


./cairo-dock: symbol lookup error: ./cairo-dock: undefined symbol: cairo_push_group


please what do i need to do to overcome this error

---

### Post by GPH on 2006-11-25
> **d3br074 said:**
> Ok i figured out my old problem (I hadn't been using "make" i was stupid and assumed that it would update itself if i changed the source but you have to make the folder as well.  ANyway, whenever I run the terminal application from my dock, It always opens a terminal as if it was in the folder that my cairo dock is located (/opt/cairo-dock).  I am looking for a command to force the terminal to open in the home folder.  Thanks!

```
"gnome-terminal --working-directory=/home/**directory**"
```

---

### Post by macewan on 2006-11-26
gravedig* is in fact back, check the kiba forum

---

### Post by macewan on 2006-11-26
did you:

make clean

before you typed: make


> **Kryten107 said:**
> GPH, you should make that Howto a seperate thread so people can find it easier. It worked for me until I extracted the tarball to /opt. When I tried to make it, I got this:
```
devin@Nayru:/opt/cairo-dock$ make
make: Nothing to be done for `all'.
```Trying to run the dock gives this:
```
devin@Nayru:/opt/cairo-dock$ ./cairo-dock
Floating point exception
```Ideas, anyone?

---

### Post by drbreen on 2006-11-26
i am wondering why enlightenment can showcase this zooming effect w/o acceleration (does it ? really ?) and if there is anything else that can do this. anyone knows ?

---

### Post by _SMD on 2006-12-04
> **Kobalt said:**
> Tell me, I'm searching for a way to make this baby start at each session. I've tried adding start-cairo-dock.sh via System > Settings > Sessions but it won't work. I've tried editing the /etc/rc.local file by adding the command : ```
cd /home/klattimer/workspace/cairo-dock
./cairo-dock --no-glitz &
```
But again no luck it's not working... :( Has anyone an idea on how to work it out ? 

Thanks & Cheers ! :rolleyes:

same here. anyone can solve this?

---

### Post by Hobbes on 2006-12-07
This was working for me:  /opt/cairo-dock/start-cairo-dock.sh

is in my sessions (startup programs).

make sure that in start-cairo-dock.sh you replace the line starting with "cd" to your own home directory.

PM if you want more help as i don't usually check this thread.

---

### Post by mautvleal on 2007-01-05
After setting off auto hiding, gnome-dock picks the mouse and we cant click in windows behind in a long range of the screen... Does anyone know how to modify it in the cairo-dock.c ?? 

Thank's

---

### Post by komensky on 2007-01-06
to original poster:

what beryl/metacity theme you using?

Thanks yuo much :)

---

### Post by olavjunior on 2007-05-08
I get this error when I try to configure cairo :

configure: error: Cairo requires at least one font backend.
                  Please install freetype and fontconfig, then try again:
                  [http://freetype.org/](http://freetype.org/)  [http://fontconfig.org/](http://fontconfig.org/)

 I'm using feisty, and didn't have any problems configureing it under edgy. I installed the freetype trough synaptics, didn't help. Isn't it posible to get cairo trough synaptics??

(I used synaptics, didn't help. Compiled succsessfully from source, but still the same error)

EDIT:  I got to install cairo-1.2.6 by installing the developement-files for libcairo2 in Synaptic. But still, when I try to make cairo-dock I get ALOT of errors! :( Anyone got an idea why?

---

