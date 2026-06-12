---
title: "New to GUI programming, tried kdevelop -&gt; faild miserably"
date: 2007-12-25
forum: Programming Talk
---

### Post by SergeiFranco on 2007-12-25
Right here is the back ground on what I am trying to achieve:
I want to create a GUI front end that will send and receive DCOP calls to/from amarok, basically controlling it through DCOP.
I have started the thread on amarok forum but I feel it is more to do with GUI development for Linux than with amarok, so I am shifting the focus here.
here is the thread:
[http://amarok.kde.org/forum/index.php/topic,14864.0.html](http://amarok.kde.org/forum/index.php/topic,14864.0.html)

So to summarize:
I am comfortable with C, but don't really know any other languages.
I have tried kdevelop but miserably failed, due to having no idea how to initialize every thing. I have tried ruby on kdevelop and also tried to run simple hello world from template but it never happened, came up with an error that was not descriptive to see what really was the problem (one would assume that if you use hello world template it should run if you press run).
I have tried to google for how to send/recieve DCOP messages on even from button press, but could not find anything...

What are my options here? Am I hopless?
Should I give up on linux for Carpc/Carputer and install windows with Roadrunner front end? or is there still hope for me?

---

### Post by DuneSoldier on 2007-12-25
I'm not familiar with QT and kdevelop. If you are familiar with C I'd go with GTK and [Glade]("http://www.jamesh.id.au/software/libglade/").

---

### Post by moma on 2007-12-25
Code::Blocks IDE itself is wxWidgets-based. C and C++.
[http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418](http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418)

---

### Post by SergeiFranco on 2007-12-25
I would rather stick to KDE (no need for extra libraries - this front end is for an system with limited space).
I believe that Glade is not what I am after.
Right lets look at this way, I am looking for a tutorial for kdevelop on how to start a GUI application from scratch and list and explanation of what all the classes/functions do in the bloody libraries.

Basically I am after some tutorial for a complete noob on how to develop in kdevelop.

---

### Post by LaRoza on 2007-12-25
[http://docs.kde.org/stable/en/kdevelop/kde_app_devel/](http://docs.kde.org/stable/en/kdevelop/kde_app_devel/)

How about their site?

[http://www.dazzle.plus.com/linux/](http://www.dazzle.plus.com/linux/)

Programming is all about debugging and reading API's.

---

### Post by deadowl on 2007-12-25
I have had a hard time with any interface that attempts to introduce graphical elements into programming (VB, Lego Mindstorms NXT, and so on). I don't blame you for having a hard time.

---

### Post by SergeiFranco on 2007-12-25
right....  where do I start, I just wasted about 10 hours trying to figure this thing out...
WHERE DO I FIND THE DCOP DOCUMENTATION???????
the only thing more or less useful I found is this mumbojumbo:
```
int main(int argc, char **argv)
{
    KApplication app(argc, argv, "firstone_client", false);

    // get our DCOP client and attach so that we may use it
    DCOPClient *client = app.dcopClient();
    client->attach();

    // do a 'send' for now
    QByteArray data;
    QDataStream ds(data, IO_WriteOnly);
    if (argc > 1)
        ds << QString(argv[1]);
    else
        ds << QString("http://www.kde.org");
    client->send("firstone", "firstoneIface", "openURL(QString)", data);

    return app.exec();
}
```

My biggest problem is I don't know where to start, and no, program that  draws little TVs are useless to me, or copy-pasting the code and compiling for some stupid organiser, or whatever other "tutorials" give me. They assume that I have programming background, which I don't, I have some basic knowledge of C++ and average C, that is about it. Almost as if it was purposely made complicated to keep it in inner circle so no one would not steal their secrets.

Can some one give a small code that will out put string contents into some application through DCOP and read some data into another string from some application through DCOP?

Also why the hell writing small C program is so complicated in Linux? How the hell I am supposed to know what to do with this make business? In windows I used GCC+JFE (as well as AVR studio) and after click of a button I got it compiled and running.
Now I tried to test some theory and could not compile small bloody hello world program. WHERE IS MY COMPILE BUTTON? (don't take last sentence very seriously ;)).

---

### Post by LaRoza on 2007-12-25
> **SergeiFranco said:**
> 
Also why the hell writing small C program is so complicated in Linux? How the hell I am supposed to know what to do with this make business? In windows I used GCC+JFE (as well as AVR studio) and after click of a button I got it compiled and running.
Now I tried to test some theory and could not compile small bloody hello world program. WHERE IS MY COMPILE BUTTON? (don't take last sentence very seriously ;)).

It is not, C is a low level language and high level functions take a little time.

You should know the languages very well before trying to make GUI programs. Making non trivial GUI's requires a good understanding of OO programming (in C++).

What I found, it is straight forward to me, so it is not Linux or the docs that are lacking.

If you want to start learning the basics of GUI programming, try an easier language, like Python (I would suggest Tcl, but that wouldn't work well for you most likely).

It can use QT, GTK and wxWidgets and ships with Tkinter. They all are good for learning how to make GUI's without having to worry about compiling, linking and pointers.

---

### Post by LaRoza on 2007-12-25
> **SergeiFranco said:**
> They assume that I have programming background, which I don't, I have some basic knowledge of C++ and average C, that is about it. Almost as if it was purposely made complicated to keep it in inner circle so no one would not steal their secrets.


That is right, they do assume, for good reason.

It is complicated (relatively) by nature, not design. There is no inner circle in Linux and everything is open to inspection and tweaking.

If you don't have the level of knowledge yet that this requires, that is not their fault.

---

### Post by SergeiFranco on 2007-12-25
Well, they could at least point in the right direction....

---

### Post by LaRoza on 2007-12-25
> **SergeiFranco said:**
> Well, they could at least point in the right direction....

Learn the language first.

---

### Post by SergeiFranco on 2007-12-25
Now I understand why the modern programs are so slow and huge - OOP makes them bloated. I think it is possible to make everything not OOP, or atleast to just stick to structs and functions. I could fit the whole interface and functions in size measured in hunderds of bytes that would run a lot quicker on a  16MHz 8bit Harward architecture, then this bloated Hello World program in cpp that runs on system that is hunderds or even thousands times faster.

Now, the real question is: I need carpc front end, nghost is not ready, amarok would be perfect if not for having static and unsuitable interface for small touch screen.
I am jealous of Windows guys with their pletora of choices for front ends.
I am seriously rethinking of not using windows on my carpc...

I have about 7 days to decide what to do, until I will have to go back to work.
Is it possible to learn C++/QT in that time and come up with working interface?
I know C++ but not very comfortable with it as I studied (and hated it) in uni about 5 years ago, never used it since....

---

### Post by LaRoza on 2007-12-25
> **SergeiFranco said:**
> Now I understand why the modern programs are so slow and huge - OOP makes them bloated. I think it is possible to make everything not OOP, or atleast to just stick to structs and functions. I could fit the whole interface and functions in size measured in hunderds of bytes that would run a lot quicker on a  16MHz 8bit Harward architecture, then this bloated Hello World program in cpp that runs on system that is hunderds or even thousands times faster.

Now, the real question is: I need carpc front end, nghost is not ready, amarok would be perfect if not for having static and unsuitable interface for small touch screen.
I am jealous of Windows guys with their pletora of choices for front ends.
I am seriously rethinking of not using windows on my carpc...

I have about 7 days to decide what to do, until I will have to go back to work.
Is it possible to learn C++/QT in that time and come up with working interface?
I know C++ but not very comfortable with it as I studied (and hated it) in uni about 5 years ago, never used it since....

OOP isn't what makes them bloated, it is usually feature creep.

What is carpc? What do you envision the interface to look like?

---

### Post by SergeiFranco on 2007-12-25
Carpc/Carputer, it is basically a PC stuck in the car that works as media player.
The interface should be very simple as it will be operated by finger (through touch screen), it should have, volume control, track control, basic play list function.
something like this: [http://guino.home.insightbb.com/roadrunner.html](http://guino.home.insightbb.com/roadrunner.html)
I would settle with that program, but it is Windows based.

---

### Post by SergeiFranco on 2007-12-25
the funny thing is that I can control amarok so easily through konsole via DCOP calls, hence I got the idea of making interface. Now I am at the level I can make my own UI with buttons and other widgets, and they can do stuff, but I have no idea how to implement DCOP, I might resort to my interface outputing to konsole and that would somehow translate DCOP calls to amarok...

---

### Post by samjh on 2007-12-26
Have you read: [http://api.kde.org/3.5-api/kdelibs-apidocs/dcop/html/index.html](http://api.kde.org/3.5-api/kdelibs-apidocs/dcop/html/index.html) ?

Or you might want to use DBus, which is DCOP's successor: [http://en.wikipedia.org/wiki/D-Bus](http://en.wikipedia.org/wiki/D-Bus) (the example provided looks like C++).  There is a C binding to it, but it's quite low-level.

---

### Post by SergeiFranco on 2008-01-02
Thanks to guys on amarok forum ( [http://amarok.kde.org/forum/index.php/topic,14864.0.html](http://amarok.kde.org/forum/index.php/topic,14864.0.html) ) that pointed me towards Kommander. This is very easy thing to use and there is no need to know/remember syntax or hierarchy of a OO language (or even private/public mumbo-jumbo), it is actually very powerful tool for a non-programmer, possibilities are endless.

---

