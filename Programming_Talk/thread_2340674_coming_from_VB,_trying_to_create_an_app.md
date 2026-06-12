---
title: "coming from VB, trying to create an app"
date: 2016-10-20
forum: Programming Talk
---

### Post by pablogener on 2016-10-20
I swear by everything good in this world I did search before posting.

I switched to ubuntu linux sometime ago, because I was given a netbook with ubuntu preinstalled, and at work every computer we have at the office was migrated to ubuntu too.
I started programming at 8 with BASIC. I started learning VB ~15 years ago and have made hundreds of little apps with it. Now I'm living in the linux world and everything seems just too awesome to go back to M$. The thing is: I need to make programs for things I do, and I would really need to share my work with my colleages. I *reeeeaaaally* need to be able to hand out programs to other people in my work team so they use them too.
**I tried** gambas and found out (the hard way) that you can't give your programs to others and have them run your software, unless they install gambas beforehand.
I want to give others a somewhat of an equivalent of a .exe file and have them run that. It seems that that just doesn't quite exist at all, in linux.
What to do?
Sorry for the big story and all.
Long story short: I made a bash script that accepts arguments at command line and want to build a GUI for it.
Installed Qt, after a half-hour tinkering around didn't find how to $#"@$"# code what happens when a user clicks on a button.
Installed Python (with 'Glade') and hade to: first, run a console command to start designing the UI, then quit that, and run another console command to start editing the code.. damn, is it really possible to accomplish anything while working like that?
Free software is the best of the world.
It is more secure, more stable, evolves faster, is more reliable, everything about it is marvelous.
There may be a small inconvenience but it also brings a great freedom.
So, bare a small inconvenience and you get in trade a great freedom.
But, if everything in free soft is so great, how come we don't have a programming language with a decent IDE that can handle UI-to-codesheet work flow, like redmond has??
Is there anything REAL that wouldn't demand a year or more to get a simple GUI interface to be designed and rigged to run a bash script?
thanks for you time and concern, in advance.

Pablo.

---

### Post by TheFu on 2016-10-21
You are still thinking the Windows way. That will lead to great frustration as you've seen.  Embrace the *nix way of thinking and you'll be much happier.  The OS is the IDE on *nix systems. The ENTIRE OS.  Lots of videos show how to do this and how to think in this way.  If you had learned the *nix way of creating software and GUIs, then you'd think the Windows way was foolish. Trust me.

[https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/](https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/) is an intro for using the OS as the IDE. Hope it helps.  Plus the techniques are useful regardless of the languages used - python, perl, ruby, C, C++, Fortran, erlang, doesn't matter ... 

BTW, bash isn't really designed to work with a GUI. It is an admin scripting tool. For GUI programs, look to python, ruby, perl, C, C++, or a webapp.  More and more, I've been asked to make webapps so the client doesn't matter.  Phone, tablet, desktop and the OS don't matter.  Just design a nice REST API and hook up whatever client you like. This is how C/S Android apps work. Extremely flexible and the webapp is just another client.

There are also ubuntu-only ways to make GUI programs. I avoid those, since I want my programs to work on Fedora, SuSE, Gentoo, Arch, and the 50 other Linux distros, not just Ubuntu-Unity.  You can learn more here: [https://developer.ubuntu.com/en/](https://developer.ubuntu.com/en/)

BTW, welcome to the forums.

---

### Post by pablogener on 2016-10-21
thanks for your answer TheFu.
I guess it'll be really hard for me to stop thinking "The windows way". It's been just too many years using and making software for that platform.
Anyway I try to keep an open mind and learn new things all the time.
I do get the "OS as an IDE" concept but still, when trying out python or C++, it was really hard to find 'where' to put code that would make a pushbutton I placed on the GUI do something.
I think it's not a "linux culture" thing, it's more of a development model difference. VB seems to be 'user input' driven, whereas other langages seem to be 'problem-solving' driven.
All I ask is, is it possible to:
a) place a button on the form, on the GUI design view
b) go to code page
c) have a reasonable way of adding code to be performed when the user clicks on that button
?

This I proved impossible in either Qt or Python (with Glade).

Why I'm asking this? Because from a practical point of view, it would be much helpful to not-hardcore programmers, who code for a living, but for hobbyists (like myself), to be able to work "the windows way"/"the ultra-practical way" while still in *nix, in a free software environment.

I understand programming like this:

problem -> [   ???   ] -> solution

inside the [ ??? ] box goes whatever you can come up with to reach the solution.
It doesn't even have to be a good way to reach the solution, it just has to be something you can come up with, that you can make, that you can 'develop'.
Now, if the tools you're given to reach that solution demand that you walk the earth all around, and then, after being 'enlightened' with all the great knowledge of the grand-design of the *nix universe, then I believe that's not practical.
Tools should empower users so that they reach what they aim for with the least effort and in the most effective way possible.
What I'm trying to say is, if I aim to make a GUI that has a button on a form, and you click on that button, and that runs a .sh script, how can that be so difficult to make with programming languages so high-level and modern and advanced?? How much would I feel encouraged to learn python (sth I'm really looking forward to), if accomplishing such a minimal task is so hard to come by?

Is there a logical sensible reason to avoid from 'double-click on the GUI design and jump to codesheet edit at '_onClick()' section of clicked object'?

I don't know, I feel like a maniac clinging to the 'Windows way' rock when everyone's already shuttled off a dying planet.

Moreover, I'm not asking for directions on how to get done what I'm trying to do. I'm asking about programming development decisions that were made in the *nix world that I see affect most programming languages I interacted with in the past few days.
This would rank more in a 'rant' type of post, I guess.

---

### Post by TheFu on 2016-10-21
There are lots of different GUI/TUI libraries for Linux. Most GUI libs use a callback() method for any events. The callbacks are registered so that whenever GUI things happen, the event causes the callback to be processed.  This is just like how Windows works.  The closest I've come to VB was using Delphi. Basically, I'd work from the GUI and each event would link to a callback function where I'd have to add code.  It works the other way around with Unix GUIs.  This is the X/Windows model ... many decisions were made in the mid-1980s.

TUI stuff gets used for bash all the time.  **ncurses** is popular and there are some newer TUI interfaces too.  **dialog** is another option. [http://www.unixcl.com/2009/12/linux-dialog-utility-short-tutorial.html](http://www.unixcl.com/2009/12/linux-dialog-utility-short-tutorial.html) might be helpful.  Think that **xdialog** [http://xdialog.free.fr/doc/intro.html](http://xdialog.free.fr/doc/intro.html) is the GUI version.  I've only played with these and it was long, long, ago.  Zenity [https://askubuntu.com/questions/89505/fast-way-to-create-gui-for-bash-app](https://askubuntu.com/questions/89505/fast-way-to-create-gui-for-bash-app) is another example.
  
There might be a GUI tool for building apps like you seek, I just haven't used one.
 
As far as rants go, yours was fairly nice.  Sorry I don't have any VB background to bridge the gap.

---

### Post by virgosun on 2016-10-23
Hey. why dont you think about Java? I have migrated from c# to JavaFx successfully. It even run on macOS, write one, run everywhere. Of course if you dont really need to access pre-built, OS-Specific platform like .Net, ApplePush etc etc
Take a look at this [cross platform sync wallpaper, local net and internet ]("http://sonvirgo.github.io/live-wallpaper-sync/C-plform.html")

---

### Post by pablogener on 2016-10-24
presenting source code may bring substance to my claim.

I have tried zenity as you'll see in this code I wrote:

```

#######################################################################
#./montage-320x240-3x1.sh
# (cc) 2016 - Pablo Gener - Suteba Morón
# pablogener@hotmail.com
#######################################################################

#Informacion de bienvenida
zenity --info --text="MonWha v2.1\nMontaje de todas las imágenes de la carpeta\npara reenviar por redes sociales";

#Ingresar una nota de texto descriptiva de la imagen de resultado
NOTA1=$(zenity --entry --title="Nota al pie" --text="Escriba una breve nota para el pie de las imágenes:");

#Ingresar el nombre de archivo de resultado
ARCHIVORES=$(zenity --entry --title="Resultado" --text="Escriba el nombre de archivo final:" --entry-text="resultado.jpg");

#Tareas
convert -size 320x caption:"$NOTA1" nota.gif;
montage -geometry 320x -tile 1x -border 5 -gravity North *.jpg $ARCHIVORES;
montage -geometry 320x -tile 1x2 -border 5 -gravity South nota.gif $ARCHIVORES $ARCHIVORES;

convert $ARCHIVORES -trim $ARCHIVORES;

#Quitar datos innecesarios
rm -f "nota.gif";

#Informacion de salida
zenity --info --text="Tarea ejecutada";

```

but this appears too much as an excuse for a serious program to have running things.
It's a series of goofy pop-ups that remind of a wild 'script' behind the curtain.

I want to revamp this with a sober, hard and cool form on-screen to gather all the data needed
by the underlying script, and have a "Run..." button to pass values and fire it up.

Is this easily achieved with either Qt or Python ("coming from VB", mind you...)??
I proved it not.

I intend to determine myself to learn Python "at all costs", and "no matter what"! So I'll give
it another go and see how close I can get, little by little to coming to realize this.

Thanks all for your contributions, and sorry for the delay on bumping the topis, I had this
code only saved on my comp at work.

---

### Post by fenrice on 2016-10-24
Install QtCreator and follow some of the video tutorials on youtube, will get you started if you understand c++. If you don't you may want to look into python as it's a lot more forgiving. However no matter what you want to do you aren't going to figure it out in a half hour on Linux or Windows.  I personally like QtCreator a lot, because it is a good ide and pretty good forms editor, even for beginners, once you wrap your head around signals and slots it is a breeze to crank out small specialty aps. I feel that glade and gtk will take you a lot longer to pull an app together, but many people before you have learned it. And yes you are right Linux is much better for security and learning; however you have to understand that just handing out apps isn't as easy because the ecosystem is much more splintered than in windows, but it is very doable with some dedication and you will learn a lot in the process, but it's not for everyone.

---

### Post by fenrice on 2016-10-24
Install QtCreator and follow some of the video tutorials on youtube, will get you started if you understand c++. If you don't you may want to look into python as it's a lot more forgiving. However no matter what you want to do you aren't going to figure it out in a half hour on Linux or Windows.  I personally like QtCreator a lot, because it is a good ide and pretty good forms editor, even for beginners, once you wrap your head around signals and slots it is a breeze to crank out small specialty aps. I feel that glade and gtk will take you a lot longer to pull an app together, but many people before you have learned it. And yes you are right Linux is much better for security and learning; however you have to understand that just handing out apps isn't as easy because the ecosystem is much more splintered than in windows, but it is very doable with some dedication and you will learn a lot in the process, but it's not for everyone.

Also java is always an option and there is eclipse and idea community edition for GUI development. Java is a little more in line with your "easy" to install everywhere scenario and even more portable than VB, and it's a good language to know, but you have to get used to object oriented programming, just like with c++. Don't let people scare you with "security" issues. Those are with java applets. Java is a very well supported language and thousands of companies use it every day of the year 24/7.

---

### Post by michi20091979 on 2016-11-13
Hi Pablo,

I think I can understand your challenge well. I started programming with BASIC 2.0 on a Commodore 64 back when I was 11 years old, then continued with QBasic in DOS and VB from version 3 to 6 in Windows. Then I moved to the .net platform using Visual Studio from version 2002 until right now 2013 (upgrading to more current version pending). In contrast to my work place, where only Windows is allowed, I mainly use FLOSS at home. However, especially at home - where I have a lot of other important things to do - I do not want to read 20 hours of documentation just to end up with an "Hello World" application and proudly state that I did it the "Unix way". I want to be effective as I am at work using Visual Studio. In fact, even on Unix systems there's to need to make programming a suffer. In Ubuntu, you have the choice of some quite good IDEs:
* MonoDevelop: Mainly targets the .net platform, but you can also do development in C and C++. Of course, you can edit every text file you want. I also drag'n'drop my Python files there. It has support for some version control systems and you can work with databases there. Unfortunately, the versions shipped with Ubuntu 14.04+ are rather limited. In version 2.8, that came with Ubuntu 12.04, it was even possible to install plug-ins for development in Java, Python, and Vala. In my experience, MonoDevelop is quite fast and user friendly.
* Netbeans: Mainly targets Java, but it can be used to edit various other types of files. It has a plug in-system, so you might install support for other programming languages.
* Eclipse: Also mainly targets Java, but can also be extended to support other programming languages and project types. In the past, I have used it to write LaTeX documents, edit HTML/JavaScript/CSS/XML/XSD for web development and for programming in the D Programming Language. It has a very powerful system for software modelling, called "Eclipse Modeling Framework". However, in my opinion, Eclipse is a little bit user-unfriendly sometimes, but one can get used to it.

I hope my suggestions will help you. :-)

Best regards,

Michael

---

