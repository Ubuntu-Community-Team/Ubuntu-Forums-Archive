---
title: "[SOLVED] Converting .jar to .exe on linux"
date: 2008-06-07
forum: Programming Talk
---

### Post by psychok7 on 2008-06-07
hi there guys... i cant seem to find a good free program to convert .jar files to .exe on linux.. do you have any preferences??

---

### Post by xlinuks on 2008-06-07
Do you think Linux runs .exe files?
Anyway I would suggest clarifying what you mean.

---

### Post by psychok7 on 2008-06-07
> **xlinuks said:**
> Do you think Linux runs .exe files?
Anyway I would suggest clarifying what you mean.

dude of course i know linux doesn't run .exe(thou wine does)..i want ppl that use windows to be able to run it with a double click without any problems

---

### Post by Shin_Gouki2501 on 2008-06-07
tell them to go to the cli and type:
java -jar jarname.jar

or supply a *.bat file which does exaclty that(above call)...
assuming they have java installed...


or in windows you assing the jar fiel towards java runtime..

---

### Post by NormR2 on 2008-06-07
If by >  ppl that use windows you are refering to MS Windows, then when java is installed on a Windows machine, jar files are associated with the java -jar ... command by an entry in the Windows registry. 
The jar file must be properly constructed for the java command to find the starting point in the classes in the jar file.

You can create the same association of a command with filetype on Linux so the java -jar ... command is executed when you "open" a jar file.

---

### Post by psychok7 on 2008-06-07
yeah but guys dont forget there are a lot of people that dont know anything about computers.. i believe creating a .exe(wish i already did in windows) is the easier solution for all..just need a program that does that,runs on linux and its free..if you start talking about command line or to double click the .jar files(wish dont always work) and then it doenst work, the ppl im writting this program 2 will simply not use it. damn this are the times i miss "c"

---

### Post by psychok7 on 2008-06-07
> **psychok7 said:**
> yeah but guys dont forget there are a lot of people that dont know anything about computers.. i believe creating a .exe(wish i already did in windows) is the easier solution for all..just need a program that does that,runs on linux and its free..if you start talking about command line or to double click the .jar files(wish dont always work) and then it doenst work, the ppl im writting this program 2 will simply not use it. damn this are the times i miss "c"
[B]
PS:[/B] you guys are linux dudes used to doing it the hard way...ms windows want to simply double click and not having problmes

---

### Post by Tomosaur on 2008-06-07
This page might help you: [http://www.excelsior-usa.com/articles/java-to-exe.html](http://www.excelsior-usa.com/articles/java-to-exe.html)

---

### Post by xlinuks on 2008-06-07
> **psychok7 said:**
> dude of course i know linux doesn't run .exe(thou wine does)..i want ppl that use windows to be able to run it with a double click without any problems

Do you know how to create executable .jar file? If not - google how to create them.

If you think executable .jar files are not what you wish - then stop programming Java and do C++.
The "create .exe files from .jar" is the question almost every Java beginner asks, in the end he (like me and almost all the others in the past) come to understand that it's just _not_ worth the trouble doing .exe from .jars for many many reasons that you'll find in your (hopefully) long life ahead.

That's the reason why after 4 years of Java programming I know that I have to learn C++ for Java just doesn't cut it for a lot of cases.

---

### Post by psychok7 on 2008-06-07
> **xlinuks said:**
> Do you know how to create executable .jar file? If not - google how to create them.

If you think executable .jar files are not what you wish - then stop programming Java and do C++.
The "create .exe files from .jar" is the question almost every Java beginner asks, in the end he (like me and almost all the others in the past) come to understand that it's just _not_ worth the trouble doing .exe from .jars for many many reasons that you'll find in your (hopefully) long life ahead.

That's the reason why after 4 years of Java programming I know that I have to learn C++ for Java just doesn't cut it for a lot of cases.

but is there any loss of "quality" during that conversion? i mean using one of those paid conversion programs..

---

### Post by xlinuks on 2008-06-07
Yes, there's a loss. In best case what they do is pack all the java virtual machine into your exe file together with your actual program - which becomes big, fat and, arguably less flexible. In other words - it's solution, but a lame one. Under the hood it's still Java. There are different techniches doing what you need (converting to .exe) but they all suck in a way or another. For true and qualitative .exe applications.
For the sake of your future learn C++ (or C) - it's not only gonna save you money and let you create "true" .exe files, but what's much more important - will save you a lot of future frustrations, save your time, and make you a better programmer with a brighter future.
Life is short, have fun.

---

### Post by xlinuks on 2008-06-07
Why don't you want to create "natural .jar executables" - they run at double click if Java is installed. I don't mean creating .exe files. Is that not an option for you?

---

### Post by nvteighen on 2008-06-07
@OP:

Java is meant to be an interpreted cross-platform language. It was designed that way to make it run under any system where JVM is available. Creating a "true" executable implies to bind your application to a certain specific platform... for example, a C++ program compiled with g++ in 32-bit Ubuntu won't work in Windows, but won't either run on 64-bit Ubuntu.

You're asking Java to do something it wasn't meant for. xlinuks is right: for what you want C or C++ are what you need.

---

### Post by psychok7 on 2008-06-07
i study computer science and most of the stuff they teach me is in java so i need to practice.. we also have c.. but no c++ i think..
well u guys convinced me... im going to start using .jar and .bat files.. just a thing.. i tried following a tutorial on .bat, but when i run it it gives me all sort of erros..any ideia why?

---

### Post by NormR2 on 2008-06-07
If the jar files are to be executed on Windows, then the java jre must be installed. The installation of java sets it up so that a double click on a properly configured jar file will start the execution of the java program contained in the jar file. There shouldn't be any user intervention besides installing the java jre and copying the jar file to the computer. Then a double click will start the program. 

Do you have a Windows computer you can try this on? If you look at a jar file in Windows Explorer it should say "Executable Jar File" in the Type column. If it says "Jar File" then you don't have a properly installed java jre.

---

### Post by NormR2 on 2008-06-07
Copy and post the bat file errors for better help.

I keep forgetting to go to page 2, so my previous response is a repeat of xlinuks.

---

### Post by psychok7 on 2008-06-07
> **NormR2 said:**
> If the jar files are to be executed on Windows, then the java jre must be installed. The installation of java sets it up so that a double click on a properly configured jar file will start the execution of the java program contained in the jar file. There shouldn't be any user intervention besides installing the java jre and copying the jar file to the computer. Then a double click will start the program. 

Do you have a Windows computer you can try this on? If you look at a jar file in Windows Explorer it should say "Executable Jar File" in the Type column. If it says "Jar File" then you don't have a properly installed java jre.

yeah i tried on a windows pc and it works, thanks. is there there a way to double click the .jar file on linux also and make it work?

---

### Post by psychok7 on 2008-06-07
> **psychok7 said:**
> yeah i tried on a windows pc and it works, thanks. is there there a way to double click the .jar file on linux also and make it work?

yeah it also works for linux(never saw the options when u right click on it) thanks for everything guys

---

### Post by Shin_Gouki2501 on 2008-06-08
> **xlinuks said:**
> .. For true and qualitative .exe applications.
For the sake of your future learn C++ (or C) - ...

Well i dont want to start a flame war but funny enough for me i got java programms with executable jar files much easier ( they "just" work) to work then messing arround with make files and dependency hell libs..( in java we have osgi for that :P)
Its possible to create good and bad applications in java as well as C/C++. And believe it or not there are taks in the programming world were C/C++ becomes ineffective and java just fits. Its all about requierments.


For a simple gui app that works well on OSX, Linux and windows Java is just fine and simple :)

---

### Post by nvteighen on 2008-06-08
> **Shin_Gouki2501 said:**
> 
Its possible to create good and bad applications in java as well as C/C++. And believe it or not there are taks in the programming world were C/C++ becomes ineffective and java just fits. Its all about requierments.


For a simple gui app that works well on OSX, Linux and windows Java is just fine and simple :)

Common sense :)

---

### Post by CptPicard on 2008-06-08
Something you need to look at is 

[http://java.sun.com/products/javawebstart/](http://java.sun.com/products/javawebstart/)

but otherwise doing .jars with a defined main method is the way to go really. Java does need an InstallShield style installer that manages dependencies though... on Linux we of course have everything covered by package managers.

I do disagree strongly with xlinuks' assertion about having to learn C++ though, it's a nasty language... if you want to program on Windows, C# is probably the better and future-proof option.

For the genuine low level requirements, C is great. But those requirements do not pop up as often as one might imagine.

> **xlinuks said:**
> will save you a lot of future frustrations, save your time, and make you a better programmer with a brighter future.
Life is short, have fun.

In my humble opinion I draw the opposite conclusions from this. Higher-level languages save you a lot of frustrations, *very* much save your time, and make you a better programmer, that is, a better thinker about problems. Life is short, learn something else :)

---

### Post by marko_cz on 2009-05-31
I've been lately looking for exact same thing as psychok7.


Here's the software i found:
  exe4j - [http://www.ej-technologies.com/products/exe4j/overview.html](http://www.ej-technologies.com/products/exe4j/overview.html)
 It looks quite good and it's capable of building exe file in two ways (as somewhat similar to link, that points to .jar file and 2nd as complete copy of the application). However the free version shows some kind of ad before created exe starts...
  Jar2EXE
 Some windows only tool so i didn't bother trying it.

**Offtopic**:
 I really can't understand, why every second reply here is filled with crap like this:

> **xlinuks said:**
> 
If you think executable .jar files are not what you wish - then stop programming Java and do C++.


 What the heck is this?! How is it related to original question?!
Xlinuks I strongly recommend you to just stay quiet when you can't help, instead of teaching everyone about unrelated things - or is this some kind of way you are trying to point on yourself?

 You should understand that the most common user of windows is almost unable to do even things like setting jars to be automatically opened - and i guess that's psychok7s point. I also think that creating batch file for loading Jar is certainly not today's most elegant way to run it - as we all know they're still included only for backwards compability in windows today.

---

### Post by psychok7 on 2009-05-31
> **marko_cz said:**
> I've been lately looking for exact same thing as psychok7.


Here's the software i found:
  exe4j - [http://www.ej-technologies.com/products/exe4j/overview.html](http://www.ej-technologies.com/products/exe4j/overview.html)
 It looks quite good and it's capable of building exe file in two ways (as somewhat similar to link, that points to .jar file and 2nd as complete copy of the application). However the free version shows some kind of ad before created exe starts...
  Jar2EXE
 Some windows only tool so i didn't bother trying it.

**Offtopic**:
 I really can't understand, why every second reply here is filled with crap like this:



 What the heck is this?! How is it related to original question?!
Xlinuks I strongly recommend you to just stay quiet when you can't help, instead of teaching everyone about unrelated things - or is this some kind of way you are trying to point on yourself?

 You should understand that the most common user of windows is almost unable to do even things like setting jars to be automatically opened - and i guess that's psychok7s point. I also think that creating batch file for loading Jar is certainly not today's most elegant way to run it - as we all know they're still included only for backwards compability in windows today.

i couldn't agree with you more my friend.. though i realized that maybe writing a README .txt explaining how to open the .jar might also help, i mean it is also a double click, the same as .exe, so maybe people could learn how to use it.. but i agree having a working .exe is the best ideia as long as the conversion does not corrupt the classes, i believe paid solution are the only thing i would personally risk.. or not :P
heres another solution(stupid but it works), make a .exe that the only purpose is to open the .jar :P

cheers

---

### Post by soltanis on 2009-05-31
> **psychok7 said:**
>  make a .exe that the only purpose is to open the .jar

Not only is this the easiest way, but its also the most common one I've seen used.

---

### Post by psychok7 on 2009-05-31
> **soltanis said:**
> Not only is this the easiest way, but its also the most common one I've seen used.

lol.. it was actually a joke, but im glad to know it works :P

---

### Post by pbrockway2 on 2009-05-31
> **marko_cz said:**
> **Offtopic**:
 I really can't understand, why every second reply here is filled with crap like this:

I don't know if it's offtopic, but it's late.  Very late.

To help you understand, realise that often questions of the form "How do I do X in language Y?" fail to fully consider that technologies are better fitted to some tasks than to others.  So a reasonable response is to focus on Y, rather than X, and ask whether it's the right tool for the job.

Fortunately the platform specific part (ie *launching* a Java app) can be accomplished using web start, or by a very brief "batch" file appropriate to the platform.  As was discussed above and long ago.

I would add that providing some such mechanism is the *programmer's* responsibility and should not involve cryptic "readme" instructions imposed on the end user.  The *programmer* should put in the effort to understand how things should be set up in the platforms they intend to deploy on. (In the case of Windows, how they should check or create the right associations so that the bahaviour and iconic representation of their app and its data files is as they want it.)

Any programmer who decides to use "wrapper" software to deploy their cross platform square shaped Java app in the round hole of some particular platform has the *additional responsibility* of ensuring that the wrapper software doesn't actually break their app.  Whether they find such a solution "easier" because it "just works" is, often times, just a measure of how casually they approach that additional responsibility.

---

### Post by marko_cz on 2009-06-01
> **pbrockway2 said:**
> 
To help you understand, realise that often questions of the form "How do I do X in language Y?" fail to fully consider that technologies are better fitted to some tasks than to others.  So a reasonable response is to focus on Y, rather than X, and ask whether it's the right tool for the job.

 I'm fully aware of that, however in my opinion that's not decision you are making when the application is already written and you're looking for way how to most easily distribute it on windows (not even talking now about any specific issues like crossplatform problems which c++ has..)

> **pbrockway2 said:**
> 
Any programmer who decides to use "wrapper" software to deploy their cross platform square shaped Java app in the round hole of some particular platform has the *additional responsibility* of ensuring that the wrapper software doesn't actually break their app.  Whether they find such a solution "easier" because it "just works" is, often times, just a measure of how casually they approach that additional responsibility.

 That certainly is truth as well, there is nothing to discuss. ;)

> **soltanis said:**
> Not only is this the easiest way, but its also the most common one I've seen used.

 I've been thinking about something like that before, but i'm not certain how to create such exe (seems googling isn't helping me much here) - any help would be greatly appreciated.

---

### Post by psychok7 on 2009-06-01
> **marko_cz said:**
> 


 I've been thinking about something like that before, but i'm not certain how to create such exe (seems googling isn't helping me much here) - any help would be greatly appreciated.

hum.. ill give it a look if i find out how to do it in windows ill post it

---

### Post by t100n on 2009-06-01
> **marko_cz said:**
> 
...
I've been thinking about something like that before, but i'm not certain how to create such exe (seems googling isn't helping me much here) - any help would be greatly appreciated.

Not quite sure if this really works, but opens common .exe , so give it a try (code in C)

#include <windows.h>
....

int main(int argc, char *argv){
    STARTUPINFO si;
    PROCESS_INFORMATION p;

    ZeroMemory(&si, sizeof(si));
    si.cb = sizeof(si);

    ZeroMemory(&p, sizeof(p));

    if( !CreateProcess( NULL,
        "java -jar file.jar", // CHANGE HERE 
        NULL,
        NULL,
        FALSE,
        0,
        NULL,
        NULL,
        &si,
        &p )
    ){
        printf( "Error: 0x%X", GetLastError() );
        return;
    }

    CloseHandle(p.hProcess);
    CloseHandle(p.hThread);
}

Good luck

---

### Post by psychok7 on 2009-06-01
let us know if it works please

---

### Post by SKLP on 2009-06-01
It's possible to compile a jar to a .NET assembly (exe) using ikvmc. But I guess you want a native EXE

---

### Post by marko_cz on 2009-06-01
> **SKLP said:**
> It's possible to compile a jar to a .NET assembly (exe) using ikvmc. But I guess you want a native EXE

That one looks quite good, thanks - but it seems it again isn't tool that can run in linux.

Right now i've finally set up mingw32 (for cross compiling) and built that c code from t100n - so as soon as i get my hands on some windows computer i'll test it out (will be probably tommorow morning)...

---

### Post by marko_cz on 2009-06-05
Sorry guys for keeping you waiting!

The c code from t100n works great - the jar starts without problem (thanks to him, and all of you for help). However the command line window opens as well - and it acts like parent process to the java app (so you can't close it before the app). - I wonder if it is possible to start an independent process - so the cmd may close...

---

