---
title: "[Python] Where do i go, how do i go about it"
date: 2008-11-09
forum: Programming Talk
---

### Post by Bodsda on 2008-11-09
I've been learning python for the last 8 months or so and ive gotten reasonably confident with the basics, eg. someone was asking how to write a rock paper scissors game the other day and i just sat down and wrote in in ten minutes -- compared to my 4 hours for a guess the number game when i first started learning -- but now im a bit stuck, im not using python to enhance my computing experience cause im not that good, and im not writing games or stuff so i dunno what i want to do really. 

One thought I had was to write a program to download youtube videos, and have the option to convert them from flv to mp3 and things like that, but... I have NO idea how to even start thinking about how to do this, any suggestions please?

---

### Post by Jacks0n on 2008-11-09
In terms of downloading you tube videos, think about how you'll interact with the program, and what it'll do first. Don't immediately think about the code. Will it be used on the command line, or will it have a gui? If so, what toolkit? GTK? Tkinter? QT? Will it support username/passwords for the videos that require it? Will it provide any feedback on the download rate/percentage, and if so, how? Will it provide any encoding options?

If I were you, I'd make it a command line program. And when it's finished, *then* learn about GUI's. To download the youtube page, look into the module urllib2. And in terms of converting (encoding) the video, I'd look into using an external tool to convert it (eg. ffmpeg, mplayer, and mencoder). Then you'd simply have to execute it. To execute a shell command in python look into the subprocess module (subprocess.Popen). Also if you're *really* stuck, have a look at other projects which have accomplished the same thing. A good example's [_youtube-dl_]("http://www.arrakis.es/~rggi3/youtube-dl/").

Good luck!
Jackson

---

### Post by Bodsda on 2008-11-09
Thanks for your reply.

It would be a cli app to begin with. It should except either a direct link or a keyword. The direct link would just download it then ask the user about converting. The keyword would perform a search, and download the first result.

---

### Post by RuleMaker on 2008-11-09
There is already such application "youtube-dl" (it's free and i think opensource too, but im not sure).
But anyway, you could make it just for training. Good Luck!

---

### Post by Bodsda on 2008-11-09
> **RuleMaker said:**
> There is already such application "youtube-dl" (it's free and i think opensource too, but im not sure).
But anyway, you could make it just for training. Good Luck!

I've looked at the 'youtube-dl' and yes its opensource, I could easily recreate it with my own spin, but I make it a personal rule not to copy/write code that I do not understand -- which has its perks, it means I learn things but it also has its drawbacks, as in I don't really understand that much so I've kind of limited myself to basic programs. Would someone be kind enough to either explain the following topics or link me to somewhere that explains it in idiot terms please.

1) Classes - I dont understand their purpose, their structure, or the need for them

2) Which part of the 'youtube-dl' code actually does the business (downloading)

3) How do you know what modules would help for specific tasks, eg if i said i want to upload a specific file to several torrent sites what module would i use and why?

Thanks guys

---

### Post by LaRoza on 2008-11-09
> **Bodsda said:**
> I've looked at the 'youtube-dl' and yes its opensource, I could easily recreate it with my own spin, but I make it a personal rule not to copy/write code that I do not understand -- which has its perks, it means I learn things but it also has its drawbacks, as in I don't really understand that much so I've kind of limited myself to basic programs. Would someone be kind enough to either explain the following topics or link me to somewhere that explains it in idiot terms please.


Ah, don't shy away from what you don't understand. Don't copy it, learn from it. Yes, reading other people's code takes time, no matter how cleanly it is written, but that is a valuable skill.

> 
1) Classes - I dont understand their purpose, their structure, or the need for them

[http://en.wikipedia.org/wiki/Object-oriented_programming](http://en.wikipedia.org/wiki/Object-oriented_programming)

> 
2) Which part of the 'youtube-dl' code actually does the business (downloading)

If there are no comments, look for web modules (look at the includes). Downloading from the internet is easy (it is even in the beginner programming challenge). Getting the flash would take a little extra effort. 

> 
3) How do you know what modules would help for specific tasks, eg if i said i want to upload a specific file to several torrent sites what module would i use and why?


You look at the documentation for those modules ;) You can view everything online, or download it all: [http://www.python.org/doc/](http://www.python.org/doc/)

---

### Post by Kilon on 2008-11-09
> **Bodsda said:**
> I've looked at the 'youtube-dl' and yes its opensource, I could easily recreate it with my own spin, but I make it a personal rule not to copy/write code that I do not understand -- which has its perks, it means I learn things but it also has its drawbacks, as in I don't really understand that much so I've kind of limited myself to basic programs. Would someone be kind enough to either explain the following topics or link me to somewhere that explains it in idiot terms please.

1) Classes - I dont understand their purpose, their structure, or the need for them

2) Which part of the 'youtube-dl' code actually does the business (downloading)

3) How do you know what modules would help for specific tasks, eg if i said i want to upload a specific file to several torrent sites what module would i use and why?

Thanks guys


I will not advertise myself as an experienced programmer but I think I can give you some advice. 

1) Classes is Part of what we call OO ( Object Orientated ) programming. What they basically are , organization. You can divide your code to objects like classes . Classes can contain 2 things usually attributes , which are the means for storing data , yes you guessed it I mean variables  and fuctions which process the data in some way. 

For example you can have a class for a specific object like a leg. So your leg class will have attributes , which will define the specs for the leg, like strenght, muscle mass, weigh, flexibility ,  range of movement. However each action of the leg will be a function inside the leg class.  So for example , a move leg fuctiont will use the attributes of movement range , weight and felxibility. 

Now you can have subclasses for each muscle of the leg. Again each  leg-muscle class will have its own functions and  attributes like the leg class. On the other hand they may share common attributes and functions with a class, that is called inheritance.  Thus your leg-muscle class will share common functions and attributes with the leg class, those can be for example a common movement function, or maybe a pain function etc. 

So in short , it is means to organise your code into groups and make relationships between these groups so it is easier for you to understand and read your code. OO programming is very important when your programm is getting very big. 

2) I cannot answer you this cause I have not looked at the source code. But remember each source code is  accompanied by comments inside as well, so it should not be very difficult to identify which part is for the downloading. 

3) Well there is not certain answer to this question, but a good programmer is registered to websites which share information about the libraries and the packages. if you go to [http://www.python.org/](http://www.python.org/) and look at the bottom right you will see "using Python for ..." , there are the collections of the most known python libraries for any task you may want. Depending on your demand you might need to do some googling. 

Have fun with your saga.....

---

