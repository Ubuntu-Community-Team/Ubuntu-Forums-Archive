---
title: "Convert windows script to sh"
date: 2006-10-23
forum: Programming Talk
---

### Post by Khaotik on 2006-10-23
Hello, I've been using Ubuntu now for about 9 months. I dont know a whole lot about programming other than php and html, but I was wondering if it would be possible to convert a windowze app written in C+ (I think. I will get more info about that later.) file to a .sh script.

    The reason I want to do this is to get a game I love to play running and to give it out to the community so that they too can play the game on Linux. The game is Netstorm: Islands At War. Its an Activision abandonware game. Recently a few guy I know convinced Activision to give them the source code to continue to develope the game. Since then they have created a server and released several patches and additions to the game.

    One of these additions is a Autoupdater script that automatically checks game files with an http server to verify the integrity.

    I have tried to run this in wine but for some reason it cannot download the files. The app starts fine, and checks the http server fine. It then trys to download the list of files but it then bugs out.

    Instead of me writing alot of stuff I dont know much about, could someone here maybe go to [http://netstormhq.com](http://netstormhq.com) and download the game and see what they can do?

    I know im asking alot, I would be greatly appreciative and would definately consider a donation or some sort to Ubuntu or whoever decides to tackle this inquiry.

    Also, I beleive this is quite much to ask of anyone here. So, I was wondering if you could point me in the direction of a tutorial or something that would get me on my way to developing such a scrip/program. Like what languages would be best to learn.

Thank you for your time.

---

### Post by Bentov on 2006-10-30
Good morning,

I guess my first question is, what format are the files that it is trying to download?  Maybe that is the problem, are they windows exe's?  Could it be as easy as it is exepecting a file structure that doesn't exist on your side?
    
Also, if it is written in c++, why make it into a script? I would think it would be easier to just conver the c code?  You say you don't know that much about programming, but you do know how to program.  Do you have access to the source code, or do you just "know the guys that do"?  Sorry so many questions, but I've just gotten up and hey, it's my vacation. :) 

Bentov

---

### Post by Ben Sprinkle on 2006-10-30
If you have the source, compile it with **g++-4.0**.
It is C++ for Linux. **Will** work, made numorus programs with it.

---

### Post by Khaotik on 2006-10-31
@Bentov: The files are not exes. They are downloaded as archives. bz2 I think.

@synetics: I dont have the source. If I could convince the owner to install linux he could do this correct? If so Please point me to some sort of tutorial that I can show him.

---

### Post by Ben Sprinkle on 2006-10-31
If you don't have source and the owner won't give. Just decompile, there are a few decompilers but they f up the code so you might have to fix it a bit.

---

