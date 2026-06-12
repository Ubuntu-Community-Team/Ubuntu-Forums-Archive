---
title: "Windows to Ubuntu, IDE &quot;replacement&quot; question"
date: 2006-12-11
forum: Programming Talk
---

### Post by Lycaon on 2006-12-11
Hello developers,

I alwasy have "ubunutu-periods", i always _have_ to fall back into a windows environment. Why you ask? Because all my colleages use windows, the company where i work uses windows. Most of the programs i use in windows arent replaced in linux. So i never got real time to transform to ubuntu!
But this weekend i got ill, somekinda flew, and decided to boot up my ubuntu partition again! :-D  

After some browsing testing updating etc. I thought why didn't i post a thread in this forum a few months ago, look what other users experienced.
And now i do:)
My main goal is finding some replacements for windows applications concerning  development.

On windows:
- C++ / C IDE is use Borland C++ 6, it's clean fast and has an nice simple IDE with code completion. Still you have full controll of your code etc. Another thing i like about that ide or any other: making gui's is childsplay. I'm looking for such an ide, with syntax highlighting, debugging, gui designing, etc. Plus one with some help :)  
- I used to program some php(this is a question for a friend too), for this we use EditPlus. Syntax highlighting replace all files etc. Simple fast and usable on any other file. Like css html php sql etc.

What can you guys/girls reccoment me ? I dont want to lose any functionallity that i like at windows IDE's. 

I use Ubuntu --> Gnome.

I develop for my living, but as hobby i like to build programs to make my life easier. (on windows) I would like to do the same in ubuntu:)

Thnx in advance!

ps: sorry for my bad english, bare with me:)

---

### Post by Wybiral on 2006-12-11
I use Gedit and the command line for all of my C++, but I have seen people swear by anjuta as a replacement for those Dev-C++, Code::Blocks style IDE's.

---

### Post by Ben Sprinkle on 2006-12-11
KDevelop for KDE users -- C++ GUI, syntax highlight etc.
Glade for GNOME users -- C++ GUI, syntax highlight etc.

---

### Post by pmasiar on 2006-12-11
You can try eclipse - it works same on both Windows and Linux, so skills (and keyboad shorcuts finger memory) are transferable. For web applications, try python. Also works same on both platforms. Of course depending on libraries ... and you did not mentioned database. I cannot believe people can get away without using databases! ;-)

---

### Post by lnostdal on 2006-12-11
> **Lycaon said:**
> 
- C++ / C IDE is use Borland C++ 6, it's clean fast and has an nice simple IDE with code completion. Still you have full controll of your code etc. Another thing i like about that ide or any other: making gui's is childsplay. I'm looking for such an ide, with syntax highlighting, debugging, gui designing, etc. Plus one with some help :)  
- I used to program some php(this is a question for a friend too), for this we use EditPlus. Syntax highlighting replace all files etc. Simple fast and usable on any other file. Like css html php sql etc.


..this might already be mentioned by others here, but:

* Emacs for code
* Glade for GUI-design (save as XML-files and use libglade to load @ runtime!)
* Scons for project/build-tasks
* DDD/GDB for debugging

..works great.. :)

---

### Post by Lycaon on 2006-12-12
First of all thanks for the quick replies of you all!
I decided to go for Anjuta! For c++ and c.
And gedit for PHP etc.

---

### Post by cstudent on 2006-12-12
Try taking a look at the [Code::Blocks]("http://www.codeblocks.org/") IDE.

You can download the .deb for it from here:
[http://developer.berlios.de/project/showfiles.php?group_id=5358&release_id=9217](http://developer.berlios.de/project/showfiles.php?group_id=5358&release_id=9217)

If you're using Edgy you can get a .deb for it from here:
[http://www.savefile.com/projects/1037211](http://www.savefile.com/projects/1037211)

---

### Post by maddog39 on 2006-12-13
I pretty much swear by jEdit for all my programming stuff. It's the best most flexible IDE out there. But of course it uses java so you need the Java 5 JRE+JDK from Synaptic, since its not availible in Add/Remove under Applications.

---

### Post by theDentist on 2006-12-13
Anjuta with Glade works for me   :-D

---

### Post by DC@DR on 2006-12-13
I'm using Code::Blocks IDE for a while and really happy with it, especially when I'm learning wxWidgets stuff :-)

---

### Post by Choad on 2006-12-13
your english is better than mine, and im english :S

the whole fully integrated gui designer/codeing solution doesnt really exist as much in linux. KDevelop is very similar to visual basic, and its pretty good, but thats QT not GTK

sorry i cant be much help, i just use gedit and a terminal :P

---

### Post by rekahsoft on 2006-12-13
i use NetBeans with the C/C++ pack. It is getting better and better all the time :)

---

### Post by coder_ on 2006-12-14
Since you said you use Borland's C++ environment, Isn't there a Borland C++ Builder for Linux if I'm not mistaken?

---

### Post by sapienti sat on 2006-12-14
I'm a Borland user myself, and it it would be perfect to have something like that in Linux. Boland used to have Kylix, but not anymore. The latest Kylix you can get is '02. Out of what I've read in forums, the closest are Eclipse or Anjuta. 
I'm trying to find conversion tools to bring my apps from Windows, so if any of you folks know them, please help.

---

### Post by VDM on 2006-12-16
It is like asking someone what is their favorite car... it is all a matter of taste, preferances and what they have grown up with. Just try out a few things and see what favors you is all i can say.

---

### Post by araz on 2006-12-16
I use NetBeans. You should give it a try

---

