---
title: "[SOLVED] A dumb compile/link question"
date: 2008-05-03
forum: Programming Talk
---

### Post by anewguy on 2008-05-03
I am working on my first program in C using GTK (very rusty at C, GTK is all new).  Part of what the program does uses the usb library - without gtk I just had to say -lusb on the gcc line and it worked okay.  When I started trying to use GTK, I started with some online tutorials, one of which included this compile line:

gcc -Wall -g -o cvsdownload *.c `pkg-config --cflags --libs gtk+-2.0 libglade-2.0`


I tried add < usb> (without the <>) before the last tick mark as I thought that was defining libraries.

That gave me this at the top of a long error list:

Perhaps you should add the directory containing `usb.pc'
to the PKG_CONFIG_PATH environment variable
No package 'usb' found
 
 I don't know where to start until I get the USB library, the usb.h file, etc., paths included in the compile somehow first.  I don't understand anything starting at the `pkg-config, and I really need help setting this up somehow.

Please help a dumb guy out again!  Thanks in advance!! :)

---

### Post by meindian523 on 2008-05-03
Please put an appropriate title.This title sounded like someone who needs a ./configure,make,make install type help.It wastes time,which,considering your beans,you would know.

---

### Post by anewguy on 2008-05-03
> **meindian523 said:**
> Please put an appropriate title.This title sounded like someone who needs a ./configure,make,make install type help.It wastes time,which,considering your beans,you would know.

Let's see, gcc has nothing to do with compiling and linking?  If I had a question on the standard INSTALLATION method I would have asked.  Can't answer that question - then don't answer at all.

EDIT:  If the forum was working correctly, you would not see my bean count.  I think it's a mistake that EVERYTIME I ask a question that it adds to that counter.  I ask TONS of questions - answer what I can.  To ASSUME a bean count of any given range means knowledge, well, you know what they say about the word assume - except you can leave the "me" out of it.

I asked a question in GOOD FAITH about a GENUINE problem I'm having.  It's a beginner's question as I don't know squat about this type of thing - I just use what someone tells me to or a tutorial shows.  

Instead of complaining, either answer the question or point me to a plain-English non-technical reference that will actually answer my question.

Your bean count's lower so you ASSUME I know more?  Congratulations if you have the knowledge - I don't, I'm learning.

---

### Post by LaRoza on 2008-05-03
> **anewguy said:**
> I am working on my first program in C using GTK (very rusty at C, GTK is all new).  Part of what the program does uses the usb library - without gtk I just had to say -lusb on the gcc line and it worked okay.  When I started trying to use GTK, I started with some online tutorials, one of which included this compile line:

gcc -Wall -g -o cvsdownload *.c `pkg-config --cflags --libs gtk+-2.0 libglade-2.0`


I tried add < usb> (without the <>) before the last tick mark as I thought that was defining libraries.

The tick marks (`) execute that command and put that in its place. Run "pkg-confiog --cflags --libs gtk+2.0 libglade-2.0" on the command line and you'll see. Put the -lusb outside the ticks like you normally compile.

> **anewguy said:**
> 
EDIT:  If the forum was working correctly, you would not see my bean count.  I think it's a mistake that EVERYTIME I ask a question that it adds to that counter.  I ask TONS of questions - answer what I can.  To ASSUME a bean count of any given range means knowledge, well, you know what they say about the word assume - except you can leave the "me" out of it.

Your bean count's lower so you ASSUME I know more?  Congratulations if you have the knowledge - I don't, I'm learning.

The forum works correctly, this feature just hasn't been activated/used yet, I am not sure why, but it will be up soon hopefully.

By the way, I wouldn't say you have a lot of beans ;)

Moved to Programming Talk.

---

### Post by anewguy on 2008-05-03
LaRoza, thanks so much!  I modified my small script (the 1 gcc line) to have the -lusb external as you mentioned.  I still ran into problems, so I got to thinking hummmmmmm.....I wonder if something has changed in regards to the libusb stuff.  You see, I have a C program that I already had working from the command line, and decided to put a GTK GUI around it so it looks better.  I went to the folder that I have the actual "other" program in (so I wouldn't mess up the good one!) and tried what always worked for it to compile: gcc -o somename *.c -lusb  

WEEELLLLLL.......that doesn't work now!  Worked in Gutsy, so huummmmmm, wonder if something moved in regards to some of the lib usb stuff.  So I go searching for usb.h, the header file it's not finding at all, and I see a few with a size of 0, and a few within kernel folders of some sort.

Now, I have no clue how this stuff was layed out before, and thereby why it was able to compile before.  I only know that I was told quite a while ago now that it's in Linux (worked Gutsy), and that you can use the same code in Windows if you install the correct libusb packages for Windows (I think from sourceforge, but might have been it's own site?).

Sooooooo, I'm screwed until I get a better understanding of what moved and to where or what is missing since the move to Hardy.  Do you know of anyone I can contact who might now what changed with the libusb stuff and where the headers, etc., are, and therefore (whew!) how to compile something using them since -lusb doesn't appear to be enough now?

Thanks again!  I envy you guys that know what you're doing so much! :):)

---

### Post by LaRoza on 2008-05-03
> **anewguy said:**
> LaRoza, thanks so much!  I modified my small script (the 1 gcc line) to have the -lusb external as you mentioned.  I still ran into problems, so I got to thinking hummmmmmm.....I wonder if something has changed in regards to the libusb stuff.  You see, I have a C program that I already had working from the command line, and decided to put a GTK GUI around it so it looks better.  I went to the folder that I have the actual "other" program in (so I wouldn't mess up the good one!) and tried what always worked for it to compile: gcc -o somename *.c -lusb  

WEEELLLLLL.......that doesn't work now!  Worked in Gutsy, so huummmmmm, wonder if something moved in regards to some of the lib usb stuff.  So I go searching for usb.h, the header file it's not finding at all, and I see a few with a size of 0, and a few within kernel folders of some sort.

Sooooooo, I'm screwed until I get a better understanding of what moved and to where or what is missing since the move to Hardy.  Do you know of anyone I can contact who might now what changed with the libusb stuff and where the headers, etc., are, and therefore (whew!) how to compile something using them since -lusb doesn't appear to be enough now?

Thanks again!  I envy you guys that know what you're doing so much! :):)

Install it, I see it in synaptic. 

```

sudo aptitude install libusb-dev

```

---

### Post by anewguy on 2008-05-03
Oh man do I feel stupid!!

Thanks!!:):)

---

### Post by LaRoza on 2008-05-03
> **anewguy said:**
> Oh man do I feel stupid!!

Thanks!!:):)

Its alright. On a fresh install, it is easy to forget what you had.

---

### Post by anewguy on 2008-05-03
A million thanks, LaRoza !!  Everything is working great now, even my very first attempt at wrapping a command line C program with a new GTK GUI! 

Everyone has been SO helpful, it is greatly appreciated!!:)

---

