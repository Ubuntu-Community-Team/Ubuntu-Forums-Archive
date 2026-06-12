---
title: "Presentation Program"
date: 2008-02-02
forum: Programming Talk
---

### Post by bradlis7 on 2008-02-02
I've begun my own project using Python/GTK, and I'd like some feedback on it. The program will be for general presentations, with an emphasis on church events (singing, sermons).

[[IMG]http://blog.bradlis7.com/wp-content/uploads/2008/02/screenshot-1.thumbnail.png[/IMG]]("http://blog.bradlis7.com/wp-content/uploads/2008/02/screenshot-1.png")

I'll be blogging about it at [http://blog.bradlis7.com/]("http://blog.bradlis7.com/tag/presenter/"), so you can read updates there.

I'd like some ideas on the name for the program. I'd prefer for it not to sound too much like it's church software, but I'll use the best name I find. It needs to give the idea that it's for presentations, and is catchy.

Also, if anyone wants to contribute in any way (whether you're good with code or graphics, or have experience with other presentation software), please get in touch with me.

I appreciate all the help.

---

### Post by CptPicard on 2008-02-02
What's wrong with OpenOffice's "powerpoint"? I would think you could create templates to fit your needs.

---

### Post by aks44 on 2008-02-02
> **CptPicard said:**
> What's wrong with OpenOffice's "powerpoint"?
Don't forget the force that drives the whole IT industry: the NIH syndrome... ;)

---

### Post by mssever on 2008-02-02
After reading your blog, it appears that OpenOffice would suit what you're trying to do. However, making a free worship program that runs on Linux is an idea that I've had for quite some time, though I haven't actually implemented it yet.

In my mind, what sets worship software apart from regular presentation software is how it handles songs. In my idea (feel free to use as much or as little as you want), songs would live in a database somewhere (probably either SQLite or some sort of text file structure). The software would compose the slides on the fly. That would allow you to do things like take requests or make last-minute changes easily.

I also envision a client-server setup, where the server would actually drive the projector, and the client(s) (which could be on the same machine or on another machine connected via the network controls it. This would allow for maximum flexibility.

For sheet music, it might be best to simply handle that as graphics. Lilypond is the only free music typesetting program I know of, and it isn't GUI by any means. It can, however, output postscript, which can be massaged to any graphic format you want. That said, being able to store the music with the lyrics and show or hide it at will would be totally awesome--but a major undertaking.

---

### Post by bradlis7 on 2008-02-02
> **CptPicard said:**
> What's wrong with OpenOffice's "powerpoint"? I would think you could create templates to fit your needs.

Well, this isn't aimed at being a powerpoint clone. I'm taking more of the ideas from EasyWorship, which is commercial and not natively supported on linux, and OpenSong, which has a lot of usability issues, and combining it into one program. The focus will be to put up lyrics, but I'll be coding it for general text slides. There won't be near as much flexibility and customization as powerpoint has for each individual slide, but being able to pull up items in the database will be much easier than having to make one presentation for each song and having to pull up each presentation you'll have to use. If you've never messed with operating powerpoint at a church service, it's harder to understand the reasoning, but it makes sense to me why I'm doing it.

> **mssever said:**
> In my mind, what sets worship software apart from regular presentation software is how it handles songs. In my idea (feel free to use as much or as little as you want), songs would live in a database somewhere (probably either SQLite or some sort of text file structure). The software would compose the slides on the fly. That would allow you to do things like take requests or make last-minute changes easily.

You make a good point. I want to tie in the program to a database on a website (optional to the users), and also have a local database. Files are probably easiest to the users. I'm still trying to figure out if I want to use one xml file as the database, a flat-file individual files, or xml individual files. With the option of being generic slides,  lyrics, or something else, I'll probably signify that with the file extension.

Right now, the slides are rendered as the slide is selected.

> **mssever said:**
> I also envision a client-server setup, where the server would actually drive the projector, and the client(s) (which could be on the same machine or on another machine connected via the network controls it. This would allow for maximum flexibility.

I've got it set up as dual monitor, which is what all the churches I've seen have it set to. I might work in the gtk-screen functionality, but I haven't looked at it a lot. I like this idea, because they could be on a laptop wirelessly running the projector, but I've never seen it done like this before.

The sheet music was just an idea, and I realize it's really complicated. It's the last thing on my agenda, if it's even feasible.

---

### Post by pmasiar on 2008-02-02
This software is to support worship/singigng somehow? There is Christbuntu or something, ubuntu-based distro with all kinds of religious related projects. I would talk to them, most likely there is existing project you can join. Whan you will know what to do better than them, you can for or start new, but not before. You might be just reinventing the wheel, and without much experience it might be just a hexagon.

You did not mentioned what kind of skills you have, in what open source projects you participated and what you learned from it. Sorry for being blunt, but my guess is your chance for success is pretty slim. It is a lot of work to create something even marginally usefull, year or more, unless you are expert hacker. And untill you dont have anything other can use, you are alone. Can be pretty lonely... :-)

---

### Post by bradlis7 on 2008-02-02
> **pmasiar said:**
> This software is to support worship/singigng somehow? There is Christbuntu or something, ubuntu-based distro with all kinds of religious related projects. I would talk to them, most likely there is existing project you can join. Whan you will know what to do better than them, you can for or start new, but not before. You might be just reinventing the wheel, and without much experience it might be just a hexagon.

You did not mentioned what kind of skills you have, in what open source projects you participated and what you learned from it. Sorry for being blunt, but my guess is your chance for success is pretty slim. It is a lot of work to create something even marginally usefull, year or more, unless you are expert hacker. And untill you dont have anything other can use, you are alone. Can be pretty lonely... :-)

Well, I've done the research, and there are no alternatives for linux besides using Wine. If I didn't know how to do it, I wouldn't have a program that does so much with only 3 days of programming. I don't know for sure that this is going to be more than a learning experience, but I don't need you to chastise me for trying to do something good.

I'd be glad to accept the help if someone offered, but please don't assume I'm an idiot. I'm a CIS major in my senior year of college, and I know C++, Python, Java, PHP, and other languages. I've taken Computer Science courses that trained me how to write good programs. I don't know everything, but at least I'm trying.

---

### Post by RIchard James13 on 2008-02-03
One program that I have used stored songs in a database you could select from the database the songs for the service and then select appropriate backgrounds for the words. You could achieve the same thing in Impress or PowerPoint but it would be more cumbersome. You don't want to be cutting and pasting lots of text just to prepare a service.

Another aspect you could look at is being able to skip songs completely. Also in a worship service things like fancy transitions can get in the way. People really just want to be able to read the words.

---

### Post by pmasiar on 2008-02-03
> **bradlis7 said:**
> If I didn't know how to do it, I wouldn't have a program that does so much with only 3 days of programming.... I don't need you to chastise me for trying to do something good.

... please don't assume I'm an idiot. I'm a CIS major in my senior year of college, and I know C++, Python, Java, PHP, and other languages. I've taken Computer Science courses that trained me how to write good programs. I don't know everything, but at least I'm trying.

... and if you bothered to mention your background and skill level  when asking this question, you could spare me of writing previous comment and this one. You cannot assume that people can read your mind based on your nick only - because most people cannot :-)

So you wasted your time, and got yourself upset, for little gain. What is even worse, you wasted **my time**, which I could use more productively answering questions of other people. I am not sure if you appreciate I am wasting even more of my own free time on a person who seems not very appreciative.

Please read "how to ask questions" in my sig. You will need to learn how to build and manage online communities (that's why I suggested to participate in other projects before starting your own).

---

### Post by popch on 2008-02-03
Since Open Office comes with a database (of sorts), I could imagine that a combination of Impress and database would archieve much of what you state.

---

### Post by bradlis7 on 2008-02-03
> **RIchard James13 said:**
> One program that I have used stored songs in a database you could select from the database the songs for the service and then select appropriate backgrounds for the words. You could achieve the same thing in Impress or PowerPoint but it would be more cumbersome. You don't want to be cutting and pasting lots of text just to prepare a service.

Another aspect you could look at is being able to skip songs completely. Also in a worship service things like fancy transitions can get in the way. People really just want to be able to read the words.

That's a lot of what I was thinking. I'd like to do some basic transitions, but it's not going to make it to the first release. I'm using cairo for the graphics screen, and I think I'll have to move to SDL if I ever want to do transitions, but it won't be anything that's distracting from the content, which is the whole purpose of having it in the first place. I appreciate the additional thoughts.

---

### Post by bradlis7 on 2008-02-03
> **pmasiar said:**
> ... and if you bothered to mention your background and skill level  when asking this question, you could spare me of writing previous comment and this one. You cannot assume that people can read your mind based on your nick only - because most people cannot :-)

So you wasted your time, and got yourself upset, for little gain. What is even worse, you wasted **my time**, which I could use more productively answering questions of other people. I am not sure if you appreciate I am wasting even more of my own free time on a person who seems not very appreciative.

Please read "how to ask questions" in my sig. You will need to learn how to build and manage online communities...

I never required you to answer me and waste your time on me. I did get angry at your previous post because I felt that you were accusing me of not knowing anything. I simply wanted to let the community know what I was doing, I was asking for someone to evaluate my skillset and see that I was ready to do the project (I already know I can do most of it).

Anyways, it doesn't matter. I know what Impress and Powerpoint do. They are presentation programs, but no matter, they don't fulfill the same purpose that I'm trying to do from my point of view.

---

### Post by mssever on 2008-02-03
> **pmasiar said:**
> This software is to support worship/singigng somehow? There is Christbuntu or something, ubuntu-based distro with all kinds of religious related projects. I would talk to them, most likely there is existing project you can join.It's called Ubuntu Christian Edition, and I wouldn't put much stock in their work. They include Automatix as part of the standard install, and their own work is of similar quality.

My brother ran their script to convert standard Ubuntu to Ubuntu CE. Later, he called me wondering where his Forefox bookmarks had gone. The brilliant folks at CE had replaced the entire ~/.mozilla/firefox directory, just so they could install a couple of extensions. When I complained, they defended their decision--and pointed out that they had backed up the previous profile to a dotfile in a nonstandard location where no one would look. Data loss? "We only support running the conversion script on a clean install." :roll: But if it's a clean install, why bother with a conversion script in the first place?
> Whan you will know what to do better than them, you can for or start new, but not before. You might be just reinventing the wheel, and without much experience it might be just a hexagon.It usually isn't a good idea to accuse someone of reinventing the wheel when you don't know enough about the type of software to be able to support such an accusation. I'm not expecting you to know about worship software, but I do know that last time I looked, there was only one such project available for Linux, and I couldn't get it to work. Plus, it's written in Perl. :)

---

### Post by pmasiar on 2008-02-03
> **mssever said:**
> They include Automatix as part of the standard install, and their own work is of similar quality.... The brilliant folks at CE had replaced the entire ~/.mozilla/firefox directory, just so they could install a couple of extensions. 

thanks, I had only cursory idea about it's existence, and I swear to $DEITY :-) that I will not recommend ubuntu CE anytime soon! :-)

Apparently, sometimes is better idea to reinvent the wheel than trying to use someone else crap.

For me, even hint that they use Automatix would clue me not to use it.

"it is infested by Automatix! Don't touch it, just step couple steps back, and when it is safe, turn away, run for your life and never look back!" :-)

---

