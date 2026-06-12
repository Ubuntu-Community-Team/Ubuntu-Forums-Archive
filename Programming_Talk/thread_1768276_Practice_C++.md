---
title: "Practice C++"
date: 2011-05-26
forum: Programming Talk
---

### Post by Random_Dude on 2011-05-26
Hi everyone.

I know that there are a lot of threads about tutorials to start learning C++, but I can't find much advice on how to practice.
I've been reading the tutorial at cplusplus.com and started to solve some problems in [Project Euler]("http://projecteuler.net/") but it just doesn't seem enough. It doesn't force you to use good programming practices.

Most of the beginners' threads seem all about recommendations on good books (theory), but I would like to get some practice.

I've noticed that there are some programming challenges here at Ubuntu Forums ([http://ubuntuforums.org/showthread.php?t=1714324](http://ubuntuforums.org/showthread.php?t=1714324)) :D. I'm going to check them out too.

Any other advice on how to get practice when you're on your own with not enough skills to contribute to a open-source project?

Cheers :cool:

---

### Post by sanguinoso on 2011-05-26
Come up with a personal project; something that you're passionate about. What do you wish your computer did that it doesn't already?

---

### Post by r-senior on 2011-05-26
> **Random_Dude said:**
> Any other advice on how to get practice when you're on your own with not enough skills to contribute to a open-source project?
I'd say write an application that's small enough that you can finish it but large enough that it throws problems of design and architecture in your path. Make it as good as you can make it - don't just be content with it working. So consider things like libraries, coupling between code, comments, documentation (including documentation generators), coding standards, portability, automated testing frameworks, build systems (where applicable), version control and packaging.

In other words, write a small application but write it with a large application mindset. If it's actually useful to you, that's a bonus.

I do exactly the above (sometimes with some shortcuts) whenever I learn something new or want to understand a new version of a framework.

---

### Post by MBybee on 2011-05-26
I usually write a small game when I'm doing stuff like this. Try each time to solve a problem or task with a new method (since it's a learning exercise).

---

### Post by idi0tf0wl on 2011-05-26
Come up with little ideas of your own! Morph them into and out of one another! When you think about what *else* you could do, you'll end up do/learning a lot!

---

### Post by SledgeHammer_999 on 2011-05-26
I completely agree with **sanguinoso** and **r-senior**. I am a hobbyist C++ programmer myself. I have learned entirely on my own. I **think** I have learned good practices in the last ~5 years I have been experimenting with C++. I am at a level that I can read other open source project's code and understand it(usually). I have to boast 1 patch-commit for emesene, 2-3 for qbittorrent and 2 more to other projects that I currently forget.

I started writing small programs that would be helpful for my daily pc use but useless for other people. As time passed I increased the importance/size of the programs I wrote. Until finally one day I thought "Hmm, I have the Gtkmm API for GUI and I have the Gstreamer API for media playback, let me make an MPC clone.". For the past ~3 years I have been writing this program. There were periods where I wouldn't write a single line of code for months though. But through this multi-year effort I have learned a lot of things, I have gained insight for others and the best part was that I had to think in an abstract/object/structural kind of way in order to make such a big project functional and maintainable. 

(I haven't released it yet. But it is highly functional.)

---

### Post by cgroza on 2011-05-26
Start a project that will use the skills you want to acquire. And also, learn a GUI library and use it in your project. It will show you the real use of OOP and will need planning and class hierarchy design.

---

### Post by Random_Dude on 2011-05-27
Thanks everyone for the replies so far. :D
I was not original thinking in terms of developing my own projects. I'm still a newbie and I don't have that much programming experience in general. I was thinking more in terms of small excercises that a beguinner can solve in a few hours.

> **cgroza said:**
> And also, learn a GUI library and use it in your project. It will show you the real use of OOP and will need planning and class hierarchy design.

I've never learned how to write GUIs. I probably will never have to do it in my life for professional reasons, but it might be an excellent exercise.

What libraries do you guys recommend in terms of portability and available documentation?

Cheers :cool:

---

### Post by simeon87 on 2011-05-27
> **SledgeHammer_999 said:**
> I completely agree with **sanguinoso** and **r-senior**. I am a hobbyist C++ programmer myself. I have learned entirely on my own. I **think** I have learned good practices in the last ~5 years I have been experimenting with C++. I am at a level that I can read other open source project's code and understand it(usually). I have to boast 1 patch-commit for emesene, 2-3 for qbittorrent and 2 more to other projects that I currently forget.

I started writing small programs that would be helpful for my daily pc use but useless for other people. As time passed I increased the importance/size of the programs I wrote. Until finally one day I thought "Hmm, I have the Gtkmm API for GUI and I have the Gstreamer API for media playback, let me make an MPC clone.". For the past ~3 years I have been writing this program. There were periods where I wouldn't write a single line of code for months though. But through this multi-year effort I have learned a lot of things, I have gained insight for others and the best part was that I had to think in an abstract/object/structural kind of way in order to make such a big project functional and maintainable. 

(I haven't released it yet. But it is highly functional.)

As they say, release early, release often :)

---

### Post by SledgeHammer_999 on 2011-05-27
> **simeon87 said:**
> As they say, release early, release often :)

[offtopic]It currently is an Alpha state. I am in the process of adding autotools support for the building. Adding license notices. And debianizing my source so you can easily create a *.deb from it. I hope I'll release it this coming week.[/offtopic]

---

### Post by Petrolea on 2011-05-27
> **Random_Dude said:**
> Thanks everyone for the replies so far. :D
I was not original thinking in terms of developing my own projects. I'm still a newbie and I don't have that much programming experience in general. I was thinking more in terms of small excercises that a beguinner can solve in a few hours.



I've never learned how to write GUIs. I probably will never have to do it in my life for professional reasons, but it might be an excellent exercise.

What libraries do you guys recommend in terms of portability and available documentation?

Cheers :cool:

Nothing is 100% portable. GTK is popular, so is Qt (search for GTKmm for C++). I prefer GTK myself, but maybe it is just because I use Gnome.

On coding ideas: huh, I had the exact same problem like you. I learned programming; now what? 
So I made a tic-tac-toe game, hangman game that read words out of a file. It's a good place to start.
Then I added a GUI to both (must say that TTT was ugly as hell but that doesn't mater =P). Then keep adding new features or get new ideas.

If you play any games, make something useful to help you in-game (by that I don't mean an aimbot or something). Back then when I was playing ToP I made a range calculator: It took 2 coordinates as input and calculated distance between them, then took speed as input to calculate how long I will travel to there. 

It isn't hard once you get an idea of what you want to program :)

---

### Post by rokob on 2011-05-27
There are a series of good (and increasingly difficult) puzzles provided by facebook: 
[http://www.facebook.com/careers/puzzles.php](http://www.facebook.com/careers/puzzles.php)

They recruit developers out of the people who solve many of the puzzles, but in general they are not all that difficult (some are very difficult though). They are good practice though of implementing data structures and algorithms in any language. They also require you to think about the problem and design of your solution so that it is efficient. The grading robot will reject your solution if it is too slow or if the theoretical complexity is not good enough.

---

### Post by Random_Dude on 2011-05-27
> **Petrolea said:**
> Nothing is 100% portable. GTK is popular, so is Qt (search for GTKmm for C++). I prefer GTK myself, but maybe it is just because I use Gnome.

On coding ideas: huh, I had the exact same problem like you. I learned programming; now what? 
So I made a tic-tac-toe game, hangman game that read words out of a file. It's a good place to start.
Then I added a GUI to both (must say that TTT was ugly as hell but that doesn't mater =P). Then keep adding new features or get new ideas.

If you play any games, make something useful to help you in-game (by that I don't mean an aimbot or something). Back then when I was playing ToP I made a range calculator: It took 2 coordinates as input and calculated distance between them, then took speed as input to calculate how long I will travel to there. 

It isn't hard once you get an idea of what you want to program :)

The tic-tac-toe seems a great idea. I've learned how to do one in Visual Basic several years ago. Simple enough and I can start by making it only in the command line. :D

> **rokob said:**
> There are a series of good (and increasingly difficult) puzzles provided by facebook: 
[http://www.facebook.com/careers/puzzles.php](http://www.facebook.com/careers/puzzles.php)

They recruit developers out of the people who solve many of the puzzles,  but in general they are not all that difficult (some are very difficult  though). They are good practice though of implementing data structures  and algorithms in any language. They also require you to think about the  problem and design of your solution so that it is efficient. The  grading robot will reject your solution if it is too slow or if the  theoretical complexity is not good enough.

I don't use facebook. However, it's still a good challenge.
I'll add it to my favorites. Thanks. ;)

Thank you for the suggestions so far. Keep them coming. :guitar:

Cheers

---

### Post by Petrolea on 2011-05-27
> **Random_Dude said:**
> The tic-tac-toe seems a great idea. I've learned how to do one in Visual Basic several years ago. Simple enough and I can start by making it only in the command line. :D



I don't use facebook. However, it's still a good challenge.
I'll add it to my favorites. Thanks. ;)

Thank you for the suggestions so far. Keep them coming. :guitar:

Cheers

I was searching around my programming folder and I found some interesting ones: Program that keeps a record of all my grades in school, a program that creates cool passwords depending on input, a program that reads lines from file and orders them how ever the user wants and some more.

Hope you find any of those interesting also :)

---

### Post by JupiterV2 on 2011-05-27
I too am a hobbyist programmer. I took a few introductory classes in college but I never pursued programming as a profession. I've taught myself C and C++, and am now learning Java. Once I started poking around other people's code, and could understand it, I knew it was time to try something. I struggled with the same problem you have. What to write? Am I good enough? How do I even get started? There is an easy answer. Write anything.

Tutorials are all well and good but they don't teach you how to solve problems, just how the language works. You need to hack away at something yourself and learn to fix the issues that come up before you can truly learn to program. A programmer, in my opinion, is a problem solver. The languages are just the tools you use to solve the problem but they don't teach you how to come up with a solution to the problem itself. Just like a mechanic. You can have all the tools in the world, but unless you actually know how to FIX the darned thing, the tools just aren't of any use!

As others have already suggested, I started writing small little nonsense programs. I created a problem and tried to design a solution. Nine times out of ten, there turned out to be a much more elegant solution than what I designed but how else was I to know without trying and having other people with more experience look at my code? Tic Tac Toe is easy in premise but very hard, in practice, if you're trying to write an AI opponent. If you're writing it as a two player game, not so hard though. I wrote bash scripts too to solve issues. When I was building an LFS system for the 2nd time (an excellent learning experience, let me assure you!) I wrote a script to unpack, build and install source tarballs (build an LFS system, and you'll understand why). I didn't want to use the build script they supply under the ALFS because I didn't want to skip steps and do as much manually as possible.

Finally, I decided to scratch an itch. That is, after all, how most good programs get built. Scratching an itch. I wanted to brush up on my Japanese, which I had learned in college, since I hadn't used it in a few years. So, I created a flash-card/drill styled vocabulary testing program. Text based. Very cludgy. I then needed to create an editor for the tests. Also text based. Then I wanted a GUI so I had to rewrite most of the testing program. Things evolved and finally Vocab Builder was born (see my signature). Is it great? Is it a masterpiece? Will it change the world? Umm...no. But it was one heck of a learning experience. Version control, portability (the hardest part), multiple library APIs, packaging tools (Debian and Windows), etc.

So, after this long essay, I guess what I want to say is: Create your own problem and try and solve it. Tests on the internet will only take you so far. Ask for help and interact with people on the forums (was, and continues to be, a huge help). Teach others what you've learned  (another huge source of help, teaching is the best teacher). Project Euler was of limited help because its less about brute force programming methods than it is about finding good mathematical solutions. The beginners challenges on these forums can be fun and instructional too. I've done almost all of them (though I've only posted my solutions for a few, many years ago).

Hope this helps!

---

### Post by Random_Dude on 2011-05-27
> **Petrolea said:**
> I was searching around my programming folder  and I found some interesting ones: Program that keeps a record of all my  grades in school, a program that creates cool passwords depending on  input, a program that reads lines from file and orders them how ever the  user wants and some more.

Hope you find any of those interesting also :)

Thanks.
You sure got more imagination than I do. :)


> **JupiterV2 said:**
> I too am a hobbyist programmer. I took a few introductory classes in college but I never pursued programming as a profession. I've taught myself C and C++, and am now learning Java. Once I started poking around other people's code, and could understand it, I knew it was time to try something. I struggled with the same problem you have. What to write? Am I good enough? How do I even get started? There is an easy answer. Write anything.

Tutorials are all well and good but they don't teach you how to solve problems, just how the language works. You need to hack away at something yourself and learn to fix the issues that come up before you can truly learn to program. A programmer, in my opinion, is a problem solver. The languages are just the tools you use to solve the problem but they don't teach you how to come up with a solution to the problem itself. Just like a mechanic. You can have all the tools in the world, but unless you actually know how to FIX the darned thing, the tools just aren't of any use!

As others have already suggested, I started writing small little nonsense programs. I created a problem and tried to design a solution. Nine times out of ten, there turned out to be a much more elegant solution than what I designed but how else was I to know without trying and having other people with more experience look at my code? Tic Tac Toe is easy in premise but very hard, in practice, if you're trying to write an AI opponent. If you're writing it as a two player game, not so hard though. I wrote bash scripts too to solve issues. When I was building an LFS system for the 2nd time (an excellent learning experience, let me assure you!) I wrote a script to unpack, build and install source tarballs (build an LFS system, and you'll understand why). I didn't want to use the build script they supply under the ALFS because I didn't want to skip steps and do as much manually as possible.

Finally, I decided to scratch an itch. That is, after all, how most good programs get built. Scratching an itch. I wanted to brush up on my Japanese, which I had learned in college, since I hadn't used it in a few years. So, I created a flash-card/drill styled vocabulary testing program. Text based. Very cludgy. I then needed to create an editor for the tests. Also text based. Then I wanted a GUI so I had to rewrite most of the testing program. Things evolved and finally Vocab Builder was born (see my signature). Is it great? Is it a masterpiece? Will it change the world? Umm...no. But it was one heck of a learning experience. Version control, portability (the hardest part), multiple library APIs, packaging tools (Debian and Windows), etc.

So, after this long essay, I guess what I want to say is: Create your own problem and try and solve it. Tests on the internet will only take you so far. Ask for help and interact with people on the forums (was, and continues to be, a huge help). Teach others what you've learned  (another huge source of help, teaching is the best teacher). Project Euler was of limited help because its less about brute force programming methods than it is about finding good mathematical solutions. The beginners challenges on these forums can be fun and instructional too. I've done almost all of them (though I've only posted my solutions for a few, many years ago).

Hope this helps!

Thanks for the advice JupiterV2. ;)

In the case of tic-tac-toe, I was thinking of writing a command line program for two players and improve it. Then I would try to design a GUI for it, an AI seems way out of my abilities.

Thank you all for your suggestions.

Cheers :cool:

---

### Post by Random_Dude on 2011-05-28
I've been working on the tic-tac-toe game. It's going along but the code it's pretty ugly (i mean, REALLY ugly).

Is there any thread on this section like the .conkyrc thread on the Cafe ([http://ubuntuforums.org/showthread.php?t=281865&highlight=post+.conkyrc](http://ubuntuforums.org/showthread.php?t=281865&highlight=post+.conkyrc)) where you can just post small chunks of code and ask how to improve it?

Cheers :cool:

---

### Post by SledgeHammer_999 on 2011-05-28
I think it is OK to make a thread here and ask for suggestions...

---

### Post by r-senior on 2011-05-28
No problems posting code here - just post relevant (but not overly truncated) sections and use code tags so that it retains indentation.

The AI for tictactoe, by the way, is not that difficult. I wrote one in C some time ago that I can't beat on the hardest setting. Wikipedia covers it but I didn't worry about the triangle/star thing (just scanned each empty square for: win > block > fork > block fork > centre > opposite corner > corner in that precedence):

[http://en.wikipedia.org/wiki/Tic-tac-toe](http://en.wikipedia.org/wiki/Tic-tac-toe)

---

### Post by ssam on 2011-05-28
are there any bugs in software that you use that annoy you. have a look at its source and see if you can fix it. it might be easier than you think.

---

### Post by Random_Dude on 2011-05-28
> **ssam said:**
> are there any bugs in software that you use that annoy you. have a look at its source and see if you can fix it. it might be easier than you think.

So far there are no major bugs, I haven't finished yet.
The problem is that I don't how to do some stuff the smart way, for example: how do you include a class with a 2d array and declare every member of that array as equal to zero?

I've only started to look at classes yesterday, I never used them before so I'm learning them for the first time.

---

### Post by SledgeHammer_999 on 2011-05-28
> **Random_Dude said:**
> how do you include a class with a 2d array and declare every member of that array as equal to zero?


In the class's constructor write a loop that goes through the array's elements and assigns them the zero value. 

If there is an automated way to do this, I would like to hear it.

---

### Post by Petrolea on 2011-05-28
> **SledgeHammer_999 said:**
> In the class's constructor write a loop that goes through the array's elements and assigns them the zero value. 

If there is an automated way to do this, I would like to hear it.

Memset perhaps?

---

### Post by Random_Dude on 2011-05-28
> **SledgeHammer_999 said:**
> In the class's constructor write a loop that goes through the array's elements and assigns them the zero value. 

If there is an automated way to do this, I would like to hear it.

This is what I did. :(


> **Petrolea said:**
> Memset perhaps?

How do you use that?

---

### Post by Petrolea on 2011-05-28
> **Random_Dude said:**
> 
How do you use that?
C++ reference should be your primary guide for functions: [http://www.cplusplus.com/reference/clibrary/cstring/memset/](http://www.cplusplus.com/reference/clibrary/cstring/memset/)

---

### Post by SledgeHammer_999 on 2011-05-28
Hmm, interesting. I searched around and indeed memset is the recommended way.
Also if you're using C++ you could use std::fill instead. ->[http://www.cplusplus.com/reference/algorithm/fill/](http://www.cplusplus.com/reference/algorithm/fill/)

---

### Post by Random_Dude on 2011-05-28
Thanks SledgeHammer and Petrolea. I'm going to try these when I get a chance to work on the code. ;)

Cheers :cool:

---

### Post by Petrolea on 2011-05-28
> **Random_Dude said:**
> Thanks SledgeHammer and Petrolea. I'm going to try these when I get a chance to work on the code. ;)

Cheers :cool:

If you think the problem is solved now, mark it as [SOLVED] .

Hf with programming :)

---

### Post by Random_Dude on 2011-05-28
> **Petrolea said:**
> If you think the problem is solved now, mark it as [SOLVED] .

Hf with programming :)

Yeah I probably got enough to keep me busy for a while.
Thanks.

Cheers :cool:

---

### Post by SledgeHammer_999 on 2011-05-30
Hmm I found another way on how to initialize an array:

```
int arr[100][100] = {};
```

---

### Post by Random_Dude on 2011-05-30
> **SledgeHammer_999 said:**
> Hmm I found another way on how to initialize an array:

```
int arr[100][100] = {};
```

Nice, but unfortunately it didn't work for arrays inside classes. I don't know if I did something wrong or if it is supposed to be that way.

Cheers :cool:

---

### Post by Thewhistlingwind on 2011-05-30
> **Random_Dude said:**
> I've been working on the tic-tac-toe game. It's going along but the code it's pretty ugly (i mean, REALLY ugly).

Is there any thread on this section like the .conkyrc thread on the Cafe ([http://ubuntuforums.org/showthread.php?t=281865&highlight=post+.conkyrc](http://ubuntuforums.org/showthread.php?t=281865&highlight=post+.conkyrc)) where you can just post small chunks of code and ask how to improve it?

Cheers :cool:

I guarantee you my Lisp implementation is uglier.

---

