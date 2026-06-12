---
title: "c++ Programming"
date: 2008-11-01
forum: Programming Talk
---

### Post by krusher on 2008-11-01
Hi
I am a freshmen college student. I shifted to ubuntu 3 days ago after finally dumping the Windows platform thinking its time to start doing something that matters. Hence Here i am with uBuntu.

I am starting to like it and getting comfortable with it until i wanted to study for my Programming paper. I am to study c++ programming in college where they teach using TurboC++ which was running fine on my windows platform.

I am a newbie to both programming and linux distro hence might sound dumb when i dont refer to things with their right names. So please excuse me for that.

I am looking for a complete replacement to TurboC++.( I am a newbie and hence dont even want a powerful thing. I basically use iostream and conio currently as the only header files.) So that i can easily practice the classroom programming back here on my uBuntu setup. I have tried a lot of things but aint getting what i want.

I have already tried gcc think but i dont want to be writing the program in notepad and then going to terminal and then doing that gcc sdds.cpp to compile it and then see a whole lot of errors which i dont even understand.

I have tried installin ajunta but i get a extratable file which says something about configuring from terminal which i tried but havent been able to install it yet.

I have had my hands on the kDevelop c/c++ thing and it correclt highlights the program codes when i type em but then there is no option to run it!!! I installed some additional things in the kdev thing but i only got extra things which i dont know what they do like kbabel kumbrello
and dunno what not.

I tried netbeans and it seemed fine too as i managed to open a place where i could type a program but then again, when i run it it says somthing that i dont have conio.h and i tried to paste it from my tc folder to the netbean include folder and i got something like i dont have enough permissions. I am the only account (named gaurav) on my comp and it says something about root something. When i try to login by root it says it cant be logged in from here. Now thats all even more confusing.

Ok then i have tried few more things about which i dont even remember but none worked. 
Oh yeah then i tried wine to run TuboC++ but again it aint helping. I have the turbo folder in other ntfs partition which was working fine in Windows. SO i downloaded the latest free turbo c++ version and installed that. It installed well with wine but it aint showing it in the application tab on the top in the wine thing!!! But i do see the installed folder of TC++ in that c:\ option through wine. But again i cant run that tc.exe file.


Please someone help me. I have tried all my best to help myself first but then its not working out. Hence i come here to seek help.
I have started getting comfortable to use ubuntu now and dont want to go back to windows.

Please provide me an alternative or a solution so that i can just practice my c++ programming. SO that i just type the program and then hit the run button and the output is there.

---

### Post by bapoumba on 2008-11-01
Thread moved to PT.

---

### Post by scourge on 2008-11-01
> **krusher said:**
> I have already tried gcc think but i dont want to be writing the program in notepad and then going to terminal and then doing that gcc sdds.cpp to compile it and then see a whole lot of errors which i dont even understand.

Maybe programming (at least in C++) is not for you then. I use KDevelop, so I don't have to use the command line to compile. But before I started to use a fancy IDE I learned the command line stuff. It's essential, and if you don't want to learn it you can forget about your programming career.

It seems that you're trying a lot of things, and immediately give up after the first obstacle.

---

### Post by mali2297 on 2008-11-01
> **krusher said:**
> 
I have tried installin ajunta but i get a extratable file which says something about configuring from terminal which i tried but havent been able to install it yet.

Did you install it from the repositories using Synaptic package manager? What was the message exactly?

> 
... when i run it it says somthing that i dont have conio.h

As I understand from this [Wikipedia article]("http://en.wikipedia.org/wiki/Conio.h"), conio is used to create text user interfaces in DOS. In Linux, the ncurses library is usually used for that.

---

### Post by pmasiar on 2008-11-01
OP: If C++ is not your first programming language and you already know simple scripting language like Pyton, Ruby or Perl, you can stop reading now. 

Still with me? :-) I know there would blood agains for this suggestion (it was before), but .... we have traditions, and we need to maintain them? And you knew it was coming, right? So:

If you are programming beginner, in opinion of many, Python is better language to start learning basics than C++ or Java, which are overly complicated and have many details which focus on effective CPU usage, not effective use of programmer's time. Python is focused to be simple to learn and use for non-programmers too. Many leading universities in the USA are switching to Python as first language, including MIT. Some experiments show that students who spent 3 months learning Python were able to advance deeper into Java in re,aining 7 months than students learning Java only: because it's harder to grasp basic concepts if they are obfuscated by irrelevant (for beginner) details like in C++ or Java.

See sticky, see poll about best language for beginner. Reading stickies is always advisable because in thread you can get advice from a snapshot of forum members, while stickies are disputed in more details, by posters with more and more different experience. Ie no previous poster suggested to read stickies about language for beginners - it says you that they either don't read it themselves, or they are from fringe minority which disagrees with forum majority -- so such advice is fringe and suspect. Just FYI, OP.

I do not plan to respond in this thread to any discussion about "Is C++ best first language for beginner". Find relevant FAQ and let's debate there.

Have a nice day!

---

### Post by pp. on 2008-11-01
> **krusher said:**
>  ... I am to study c++ programming in college where they teach using TurboC++ which was running fine on my windows platform.

That alone is sufficient reason to keep on using TurboC++ so that you can concentrate on the matter being taught and compare notes with your peers without having to be aware all of the time that some of the differences are due to your different setup.

> **krusher said:**
> I am looking for a complete replacement to TurboC++.( I am a newbie and hence dont even want a powerful thing....) 

Your description of your struggles says otherwise. You ***do*** need that powerful thingy until such time when you have understood the several components you need for programming in C++ and how they interact with each other and with the operating system.

> **krusher said:**
> So that i can easily practice the classroom programming back here on my uBuntu setup. I have tried a lot of things but aint getting what i want.

... kDevelop c/c++ thing and it correclt highlights the program codes when i type em but then there is no option to run it!!! 
SO that i just type the program and then hit the run button and the output is there.

My advice: return to both Windows and Turbo for school work and give yourself some time to become acquainted with Linux and the tools used in Linux for programming in C++. 

If your classroom and home work leave you  enough time, you can still tinker with your new setup until you feed comfortable and confident enough to trust you school work with it.

If you are feeling adventurous, try using a virtual machine.

> **pmasiar said:**
> If you are programming beginner, in opinion of many, Python is better language to start learning basics than C++ or Java, which are overly complicated and have many details which focus on effective CPU usage, not effective use of programmer's time.

@pmasiar: so you suggest that OP look for another school where they start with your language of choice for beginners when OP complains about being unable to run "tools of trade" in Linux? This game has been overdone to bits by now, I would think.

---

### Post by jimi_hendrix on 2008-11-01
> **pp. said:**
> @pmasiar: so you suggest that OP look for another school where they start with your language of choice for beginners when OP complains about being unable to run "tools of trade" in Linux? This game has been overdone to bits by now, I would think.

ya that is a little unfair...its not his fault his school teaches C++...

---

### Post by gomputor on 2008-11-01
For an IDE you can also have a look at Eclipse [[COLOR="Red"]http://www.eclipse.org/cdt/[/COLOR]]("http://www.eclipse.org/cdt/")

There is no 'conio.h' in Linux, it's Windows specific and I don't know if you can use it under Wine and if it'll work (I know nothing about Wine).
So if your college work uses 'conio.h', maybe you must do your work under Windows and not Ubuntu. I'm sure other people with more knowledge and experience can answer this clearly.

If you want to copy any files form any folder with root privileges you can start nautilus (the equivalent windows Explorer) from the command line with:
```
sudo nautilus 
```
or copy them straight from the command line with:
```
sudo cp my_file destination_folder
```

---

### Post by cmay on 2008-11-01
> Ok then i have tried few more things about which i dont even remember but none worked.
Oh yeah then i tried wine to run TuboC++ but again it aint helping. I have the turbo folder in other ntfs partition which was working fine in Windows. SO i downloaded the latest free turbo c++ version and installed that. It installed well with wine but it aint showing it in the application tab on the top in the wine thing!!! But i do see the installed folder of TC++ in that c:\ option through wine. But again i cant run that tc.exe file.


Please someone help me. I have tried all my best to help myself first but then its not working out. Hence i come here to seek help.
I have started getting comfortable to use ubuntu now and dont want to go back to windows.

Please provide me an alternative or a solution so that i can just practice my c++ programming. SO that i just type the program and then hit the run button and the output is there.
i think to be honest that you should consider using turbo c++ on freedos on a older computer or windows on a spare partion instead of wine and all sorts of magic solutions. the class seems to use windows and turbo c++  and that is then what you should learn. i cant say this is the optimal solution or the one i would recommend  over all others but honest if you learn c++ by microsoft/borland standard in class then do that but for the benefit of your further education you simply have to learn using the commandline to compile. i read once a experienced c++ programmer saying that if he was in charge of teachin a class he would teach hello world program and how to debug hello world using commandline as the very first lesson.

one more thing is that it is your life and your responsibilty  to make this work and find a solution.if it is really important to you then why not just ask your teacher what to do.

---

### Post by Calmatory on 2008-11-01
You can not program for Windows under Linux. conio.h is legacy anyway, used by DOS.

However, it is preferred to be willing to work with command line compiling and writing code with a text editor, instead of doing it all with IDE. Yes, IDE is preferred method, but one should be familar with command line aswell, e.g. in case where you need to fix something from remote machine. No IDE there. ;)

TurboC++... Wonder why not GW-BASIC or QuickBASIC... Back to 90's. :)

---

### Post by scourge on 2008-11-01
> **Calmatory said:**
> You can not program for Windows under Linux.

Totally untrue. You can write the code under Linux, compile it under Linux (with a cross-compiler like MinGW), and even run the executable under Linux (with Wine).

---

### Post by rnodal on 2008-11-01
+1
Install wine and run those tools that you used to use under windows, they will work.

-r

---

### Post by snova on 2008-11-01
> **krusher said:**
> Hi
I am a freshmen college student. I shifted to ubuntu 3 days ago after finally dumping the Windows platform thinking its time to start doing something that matters. Hence Here i am with uBuntu.

Welcome. But please, it's Ubuntu, not uBuntu. Be careful with the shift key. :)

> **krusher said:**
> I am a newbie to both programming and linux distro hence might sound dumb when i dont refer to things with their right names. So please excuse me for that.

Perfectly fine.

> **krusher said:**
> I am looking for a complete replacement to TurboC++.( I am a newbie and hence dont even want a powerful thing. I basically use iostream and conio currently as the only header files.) So that i can easily practice the classroom programming back here on my uBuntu setup. I have tried a lot of things but aint getting what i want.

conio.h is Windows-specific. It doesn't exist under Linux.

> **krusher said:**
> I have already tried gcc think but i dont want to be writing the program in notepad and then going to terminal and then doing that gcc sdds.cpp to compile it and then see a whole lot of errors which i dont even understand.

It's a useful skill to have, so I suggest you learn how to do it, but it's not necessary.

> **krusher said:**
> I have tried installin ajunta but i get a extratable file which says something about configuring from terminal which i tried but havent been able to install it yet.

I assume you downloaded it from their website? That's not how to install things. The best way to install software with Ubuntu is through the package manager. Search for "anjuta" in Synaptic and install it that way. It's significantly easier, and it has other advantages over the Windows model.

> **krusher said:**
> I have had my hands on the kDevelop c/c++ thing and it correclt highlights the program codes when i type em but then there is no option to run it!!! I installed some additional things in the kdev thing but i only got extra things which i dont know what they do like kbabel kumbrello
and dunno what not.

There is if you create a project first.

KBabel is used in translating progams to another language, which you don't need to do. Umbrello is a UML program, also unnecessary.

> **krusher said:**
> I tried netbeans and it seemed fine too as i managed to open a place where i could type a program but then again, when i run it it says somthing that i dont have conio.h and i tried to paste it from my tc folder to the netbean include folder and i got something like i dont have enough permissions. I am the only account (named gaurav) on my comp and it says something about root something. When i try to login by root it says it cant be logged in from here. Now thats all even more confusing.

Like I said, conio.h doesn't exist under Linux. Copying and pasting didn't work because normally, you can't write to system directories. Don't try, either.

---

### Post by pp. on 2008-11-01
> **rnodal said:**
> +1
Install wine and run those tools that you used to use under windows, they will work.

-r

You did read the first post, didn't you, where OP says that he tried that without success?

---

### Post by wmcbrine on 2008-11-01
> **snova said:**
> conio.h is Windows-specific.*DOS*-specific. Pre-Windows. This is some seriously archaic instruction he's getting.

DOSBox or DOSEmu would work better than WINE for Turbo C++. Then again...

> *It doesn't exist under Linux.*There's a package somewhere that translates conio to curses, which might be enough to let him develop natively.

---

### Post by krusher on 2008-11-02
**@ bapoumba**
Thanks for moving the post to the right place.

**@ scourge**
Yes, its not really for me but i have to comply with the college.


**@ mali2297**
ok i got it right now. Thanks. i have installed it from synaptic now. but how do i run a program??? 


**@ pmasiar**
I will start learning python soon. But for the time being i must cope up with class and continue with the cpp.
Thanks for the suggestion.


**@ pp.**
I agree with you and now soon will make a partition to have windows running. Anyways, can u please help me out with virtual machine set up?? I would rather prefer using a virtual windows setup then install the whole thing.
I have seen some screenshots of people running windows inside a linux window.



**@ jimi_hendrix**
yep unfair.!!


**@ gomputor**
Thanks for teaching me how to copy and move files. Btw i a m using Ubuntu. is the nautilus thing available to me too?? Cause i thought its in that kde thing.

**@ cmay**
can i install freedos in my linux and then try to acess turbo cpp through it??

**@ Calmatory**
ok. btw whats legacy??? And can i use another hearder file instead of conio.h in linux that will work the same???




So the conclussion is that i will be installing windows on a seperate partition and then use tcpp there. Or else will try to do that virtual machine thing.

---

### Post by pp. on 2008-11-02
> **krusher said:**
> 
**@ pp.**
I agree with you and now soon will make a partition to have windows running. Anyways, can u please help me out with virtual machine set up?? I would rather prefer using a virtual windows setup then install the whole thing.
I have seen some screenshots of people running windows inside a linux window.

Running Windows from a separate partition or in a virtual machine are indeed reasonable options for you until you feel more comfortable and secure with Linux and its tools.

Installing a virtual machine is not all that difficult. There's a whole subforum here dedicated to "Virtualization". However, you ought to be aware of the fact that you have to do a Windows installation anyway, even if Windows is to be used in a virtual machine "only". You can not avoid a Windows installation that way.

Seeing that you have been using Linux for a very short time only, I'd recommend for the moment to stick with installing Windows in a separate partition and dual booting.

---

### Post by cmay on 2008-11-02
> **krusher said:**
> **@ bapoumba**
Thanks for moving the post to the right place.

**@ scourge**
Yes, its not really for me but i have to comply with the college.


**@ mali2297**
ok i got it right now. Thanks. i have installed it from synaptic now. but how do i run a program??? 


**@ pmasiar**
I will start learning python soon. But for the time being i must cope up with class and continue with the cpp.
Thanks for the suggestion.


**@ pp.**
I agree with you and now soon will make a partition to have windows running. Anyways, can u please help me out with virtual machine set up?? I would rather prefer using a virtual windows setup then install the whole thing.
I have seen some screenshots of people running windows inside a linux window.



**@ jimi_hendrix**
yep unfair.!!


**@ gomputor**
Thanks for teaching me how to copy and move files. Btw i a m using Ubuntu. is the nautilus thing available to me too?? Cause i thought its in that kde thing.

**@ cmay**
can i install freedos in my linux and then try to acess turbo cpp through it??

**@ Calmatory**
ok. btw whats legacy??? And can i use another hearder file instead of conio.h in linux that will work the same???




So the conclussion is that i will be installing windows on a seperate partition and then use tcpp there. Or else will try to do that virtual machine thing.

good luck to you. sorry if my post sounded a bit harsh,  as far as this goes it seems you done the right thing. im sure there will be someone here that can help you if you get stuck .

---

### Post by krusher on 2008-11-03
> **wmcbrine said:**
> *DOS*-specific. Pre-Windows. This is some seriously archaic instruction he's getting.

DOSBox or DOSEmu would work better than WINE for Turbo C++. Then again...

There's a package somewhere that translates conio to curses, which might be enough to let him develop natively.

Hi
So are you telling me there is hope to do my programming stuff in Ubuntu itself???

---

### Post by hessiess on 2008-11-03
GVim is good if you take the time to learn it.

---

### Post by krusher on 2008-11-06
GVim
Ok thanks. I will give it a try. 
For the time being i have installed virtual box and running winxp in there. Its all so quick in VBox. nice. But the only prb i got now is that i want to acess my REAL partitions and their files in the Xp running in virtual box. Any way to do that??

---

### Post by pp. on 2008-11-06
You can configure shared folders in VBox: the real machine offers some folder much as a samba server does, and the virtual machine can find them in the Window's network places.

If you can't find enough information in the fine manual, there's a whole subforum dedicated to virtualization.

---

### Post by meson2439 on 2008-12-09
From what I see, the only problem you have is due to conio.h and not the compiler itself. I bet you are using getch() inside the file too. My solution:

1)Remove conio.h 
2)Remove getch()
3)use g++ to compile 

I can guarantee no problem from conio anymore. Show your header files if any other complication surface. getch() is useless in modern OS. You must understand what getch is doing that is: Reads a character directly from the console without buffer, and without echo.

The output is no different with or without getch() in modern OS. There is no problem even if you don't include getch() in your exam answers or projects. The codes without conio and getch will run just as fine in your Turbo 3.0 C++ as long as you and your lecturer are using Windows 3.0 above. So don't worry.

---

### Post by Mickeysofine1972 on 2008-12-09
> **pmasiar said:**
> OP: If C++ is not your first programming language and you already know simple scripting language like Pyton, Ruby or Perl, you can stop reading now. 

Still with me? :-) I know there would blood agains for this suggestion (it was before), but .... we have traditions, and we need to maintain them? And you knew it was coming, right? So:

If you are programming beginner, in opinion of many, Python is better language to start learning basics than C++ or Java, which are overly complicated and have many details which focus on effective CPU usage, not effective use of programmer's time. Python is focused to be simple to learn and use for non-programmers too. Many leading universities in the USA are switching to Python as first language, including MIT. Some experiments show that students who spent 3 months learning Python were able to advance deeper into Java in re,aining 7 months than students learning Java only: because it's harder to grasp basic concepts if they are obfuscated by irrelevant (for beginner) details like in C++ or Java.

See sticky, see poll about best language for beginner. Reading stickies is always advisable because in thread you can get advice from a snapshot of forum members, while stickies are disputed in more details, by posters with more and more different experience. Ie no previous poster suggested to read stickies about language for beginners - it says you that they either don't read it themselves, or they are from fringe minority which disagrees with forum majority -- so such advice is fringe and suspect. Just FYI, OP.

I do not plan to respond in this thread to any discussion about "Is C++ best first language for beginner". Find relevant FAQ and let's debate there.

Have a nice day!

Stop Hijacking threads ! :D

Mike

---

