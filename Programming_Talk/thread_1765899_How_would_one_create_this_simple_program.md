---
title: "How would one create this simple program?"
date: 2011-05-23
forum: Programming Talk
---

### Post by KodR on 2011-05-23
Hello,

I am a telemarketer and work in a call centre with **** house computer systems.

I want to create a simple program that shall assist my sales team with their work.

At the moment, when we try to find someones rates, we have to refer to a chart to see who their power distributer is for their suburb, then we have to goto another chart and find out the rates for that distributor... very very very annoying and time consuming!!!

I am wanting to create a simple text base program that will allow me to enter a post code and find out the relative rates.

something along the lines of 'if input = 3065 then print 'citipower'... where citipower would be the trigger element to display the tariffs, followed by press any key to exit.

I haven't much programming experience, but I do have allot of HTML/CSS experience, so I grasp the concept of coding.

I have recently taken an interest in Python, but for now I happy to program it in any language. The program needs to run stand alone on Windows XP.

Thanks!

Nik

---

### Post by roccivic on 2011-05-23
That's what you pay programmers to do. Besides these are linux forums, so it's inappropriate to be asking for a windows only solution here.

---

### Post by NovaAesa on 2011-05-23
In order to create such a program, you will have to learn a programming language. Python is a good language to start with. I would suggest online tutorials to learn the language. Once you learn the language, writing the program will be an easy task.

---

### Post by juancarlospaco on 2011-05-23
I didnt know how to make Python Apps for Windows XP, only Ubuntu.

---

### Post by roccivic on 2011-05-23
> **juancarlospaco said:**
> I didnt know how to make Python Apps for Windows XP, only Ubuntu.

Python is actually cross-platform and is available for Win, all sorts of Unices (including probably all linux distros) and Mac.

---

### Post by juancarlospaco on 2011-05-23
> **roccivic said:**
> Python is actually cross-platform and is available for Win, all sorts of Unices (including probably all linux distros) and Mac.

Correct.
But i dont have any Windows.

---

### Post by Telengard C64 on 2011-05-23
> **KodR said:**
> I am a telemarketer

Ugh.

---

### Post by JupiterV2 on 2011-05-23
> **telengard c64 said:**
> ugh.

+1

---

### Post by r-senior on 2011-05-23
> **Programming Talk**
This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any programming language is allowed.

---

> At the moment, when we try to find someones rates, we have to refer to a chart to see who their power distributer is for their suburb, then we have to goto another chart and find out the rates for that distributor... very very very annoying and time consuming!!!
Welcome to the forum. :)

The first task I think is to make sure you are clear on the data relationship and how these elements (customer, location, distributor, price) relate to each other. I'm sure you are in your head but it's worth sketching it out and testing that out with sample data. Obviously you'll need to store all the data somewhere. Are the volumes large?

When you say standalone, do you mean that only you will run it on your PC? 

Have I understood correctly - that you intend to bring up a command window and run it from the prompt? You have no need for a graphical interface?

Python would probably do the job, as would Java. I'm pretty new with Python but in Java I'd envisage objects representing your main entities in hash maps (aka dictionaries) where you read them in from data files, hold them in memory and look them up by their key value.

---

### Post by tgm4883 on 2011-05-23
Sounds like a pretty simple program, but you haven't given us a whole lot of info to go on. Could probably have something basic working in a day.

It would help if we could get some sample "charts" to see how they are formatted and exactly what you want to see when entering a zip code.

---

### Post by Vox754 on 2011-05-24
> **r-senior said:**
> ---


Welcome to the forum. :)

The first task I think is to make sure you are clear on the data relationship and how these elements (customer, location, distributor, price) relate to each other. I'm sure you are in your head but it's worth sketching it out and testing that out with sample data. Obviously you'll need to store all the data somewhere. Are the volumes large?

When you say **standalone**, do you mean that only you will run it on your PC? 

Have I understood correctly - that you intend to bring up a command window and run it from the prompt? You have no need for a graphical interface?

Python would probably do the job, as would Java. I'm pretty new with Python but in Java I'd envisage objects representing your main entities in hash maps (aka dictionaries) where you read them in from data files, hold them in memory and look them up by their key value.

I think when people, usually coming from Windows, mention "standalone", they refer to the lazy act of having their program being a single executable, "prog.exe".

Thus, they expect to grab this executable, copy it over to other computers, also running Windows, and have it execute there without problems.

Thus, for this user, he doesn't expect to install Python or Java, he just wants it to work, standalone.

---

### Post by hakermania on 2011-05-24
> **jupiterv2 said:**
> +1
+2

---

### Post by simeon87 on 2011-05-24
This doesn't sound like a difficult program. But what are you exactly asking? Do you want to make it yourself or are you looking for a freelance programmer who can write this? You'll have to tell a programmer what the charts look like and what the output should be. Then it shouldn't be too difficult to lookup the desired info from the data.

---

### Post by satanselbow on 2011-05-24
Pretty simple to implement as a web app in PHP/mySQL - and as said above could be done in a day given the info you have provided ;)

Google about for some PHP/mySQL tutorials; [http://net.tutsplus.com/category/tutorials/php/](http://net.tutsplus.com/category/tutorials/php/) has some goodstuff (with sample code) that should get you up and running.

If you use a framework (codeigniter being my personal favourite - although cakePHP is also pretty cool) you can cut down a fair bit of donkey work :D

---

### Post by Zugzwang on 2011-05-24
Actually, writing an application seems to be totally overkill for this task, as this can be done using only *one* join query on a database.

So it might be a better approach to feed MS Access or the database engine of OpenOffice/LibreOffice with the two tables and compute a join over this data *once*. What comes out can then be exported to a table. Voila, done.

---

### Post by KodR on 2011-05-24
Hi guys! Thats allot for all of your responses! I really appreciate it!

I think just forget about me mentioning it working on Windows XP, I will get to that later with a Python Win32 compiler.

At this point I guess one could call what I need a script.
I use Linux, so I will build the program for Linux for now.


> **r-senior said:**
> The first task I think is to make sure you are clear on the data relationship and how these elements (customer, location, distributor, price) relate to each other. I'm sure you are in your head but it's worth sketching it out and testing that out with sample data. Obviously you'll need to store all the data somewhere. Are the volumes large?

No, infact this program that I am wanting to make is basicly a "print" program.

There are five power distributors in my state, meaning 5 different rates. Basicly, I will tie the post/zip codes to the relative distributor, so when one loads the program, they just need to enter the post code and it will print the relevant text, pause, then exit on any key.

Today at work I wrote the concept up in a made up computer language, but hopefully someone will ge the gist.

3068=citipower
3069=citipower
3070=citipower
citipower={print "Citipower electricity rate 1..."}
print "Please enter post code:"
if input={{3069} then print '"citipower"'}
pause

As can be seen in my made up language. The user enters post code 3069, which has been pre-defined to equal citipower, and because citipower triggers the printing of "Electricity rate 1...". Followed by program pause for any key to exit.

Thats all I am trying to make, this program I am sure would take minutes to write for someone who is an experienced programmer.

> **r-senior said:**
> When you say standalone, do you mean that only you will run it on your PC?

I mean't so Python doesn't have to be installed for it to run. I solved this future issue today.


> **r-senior said:**
> "Have I understood correctly - that you intend to bring up a command window and run it from the prompt? You have no need for a graphical interface?"

Not even, the user just needs to execute via mouse toggle (hence why I have included a 'pause', so the program does not dissapear.

---

### Post by StephenF on 2011-05-24
Have your program access the information from a central database, that way you can have many access methods (programs in many languages, maybe a web form in a browser too) but only one set of data in one central location so you can update the tables for all your co-workers without having to reissue any programs.

Consider this: your charts were probably printed from a database and for a price you might be able to get read access to the original or be issued with a copy by e-mail attachment.

A little detective work will pay off here and save you many hours of error prone data entry.

---

### Post by KodR on 2011-05-24
StephenF please stop posting in my threads, you can never just provide a straight answer, you always have to be difficult with something that has nothing to do with my original post and its so annoying.

Thank you.

---

### Post by simeon87 on 2011-05-24
> **KodR said:**
> StephenF please stop posting in my threads, you can never just provide a straight answer, you always have to be difficult with something that has nothing to do with my original post and its so annoying.

Thank you.

StephenF may well be right. In your current approach it sounds like you're going to hardcode the values into your Python script.

That's not a good idea, you'll most likely want to read them from a database or external file so that you only have to update that file / database when the data changes.

---

### Post by KodR on 2011-05-24
Its not the point, wtf can't people on forums just answer questions straight up instead of suggesting and trying to make themself feel they are complex and superior and all that. Some people have some seriously sad psycological issues. Did I ask for suggestions? no I did not.

I will be predefinging all values myself in a single static program. NOT DATABASES
****, I said I was a noob, why would people start talking accessing databases. I can only think to try and SHOW OFF their skills, how sad - look at me everybody.
I don't have time for learning all that!

I am simply going to link post codes to other ****

3070 = "Distributor 1 / Rate 1"
3071 = "Distributor 1 / Rate 1"
3072 = "Distributor 2 / Rate 1"

Then make a script that simple takes the user input, then print the the equals value

Read my original post:

I want to make a program that just takes a user value and print the relative equals value.
pre-define the values.

and people are start talking databases. Geez. Some poeple lack comm skills.

---

### Post by simeon87 on 2011-05-24
> **KodR said:**
> Its not the point, wtf can't people on forums just answer straight up instead of suggesting. Did I ask for suggestions? no I did not.

You are not a programmer, if you are not willing to take advice then take care.

You don't have to build a more complex system than necessary but we're just talking from experience.

---

### Post by KodR on 2011-05-24
ciao

---

### Post by thatguruguy on 2011-05-24
> **KodR said:**
> Its not the point, wtf can't people on forums just answer questions straight up instead of suggesting and trying to make themself feel they are complex and superior and all that. Some people have some seriously sad psycological issues. Did I ask for suggestions? no I did not.

I will be predefinging all values myself in a single static program. NOT DATABASES
****, I said I was a noob, why would people start talking accessing databases. I can only think to try and SHOW OFF their skills, how sad - look at me everybody.
I don't have time for learning all that!

I am simply going to link post codes to other ****

3070 = "Distributor 1 / Rate 1"
3071 = "Distributor 1 / Rate 1"
3072 = "Distributor 2 / Rate 1"

Then make a script that simple takes the user input, then print the the equals value

Read my original post:

I want to make a program that just takes a user value and print the relative equals value.
pre-define the values.

and people are start talking databases. Geez. Some poeple lack comm skills.

It seems like you've already decided what you want to do. Why ask for help?  Just so you can be insulting to those who try to help you? You have stated that the program would be "simple."  If so, just do it yourself.

What is it that you expect, really? Did you just want someone to come in and write a program for you to your exact specifications, with only your insults as payment?

Personally, I think that creating a database-driven solution is the only thing that makes sense and any other answer is, in a word, idiotic.

I also think that the database in question, as well as the necessary query structure, would be simple enough to create that a retarded 10-year-old could do it.  However, I recognize that your personal abilities might not rise to that level.

Good luck!

---

### Post by thatguruguy on 2011-05-24
> **KodR said:**
> StephenF please stop posting in my threads, you can never just provide a straight answer, you always have to be difficult with something that has nothing to do with my original post and its so annoying.

Thank you.

It appears that this is the only thread you've created.  Unless, of course, you create a new persona every time you have a programming issue that you want resolved for free.

---

### Post by satanselbow on 2011-05-24
> **thatguruguy said:**
> Unless, of course, you create a new persona every time you have a programming issue that you want resolved for free.

That was for free :confused: 

I was jus' making up the invoice :(

btw guru - he managed to get 2 threads out of it which, funny enough, had similar outcomes...

---

### Post by nvteighen on 2011-05-24
> **roccivic said:**
> Besides these are linux forums, so it's inappropriate to be asking for a windows only solution here.

roccivic, that's a common misconception about these forums. You can ask any programming question here; there are people here that work on other GNU/Linux distros (e.g., me), Windows, Mac, embedded devices, etc. Of course, when posting to these forums that are called "**Ubuntu** Forums Programming Talk", you should kinda expect the vast majority of posters to be using Ubuntu or GNU/Linux, at least.

> **KodR said:**
> Its not the point, wtf can't people on forums just answer questions straight up instead of suggesting and trying to make themself feel they are complex and superior and all that. Some people have some seriously sad psycological issues. Did I ask for suggestions? no I did not.

I will be predefinging all values myself in a single static program. NOT DATABASES
****, I said I was a noob, why would people start talking accessing databases. I can only think to try and SHOW OFF their skills, how sad - look at me everybody.
I don't have time for learning all that!

...


If you're a noob, then always read posts assuming that people here are very likely to have years of experience that makes them qualified to tell you what solution is better or even tell you that your general design is nonsense and that there are other ways to solve the problem. Ok, you can get the occasional bad advice, but if you're as unexperienced as you call yourself, then you won't be able to distinguish the bad advice from the good one; better wait if someone else replies to that comment with a different idea. If a sane and civilized discussion rises, watch it, read it; you'll be learning a lot.

But you don't want to learn. You want to hire someone to do something. If you were here to learn, you'd have started asking questions about databases (btw, it's the obvious solution). But no, you "don't have time" for learning, so I assume that this is either homework or some job assignment of any kind. 

Sorry, we don't do that stuff via the forums. There are people here that are professionals that have their jobs; others are students that are preparing themselves to be professionals; others, like myself, are just amateurs that just like to code. The people in the first and the second gropus don't have the time to do this for free. The ones in the third, or at least myself, value and enjoy learning about programming that much (not without effort) that we surely find it almost offensive to read a post like yours.

---

### Post by Telengard C64 on 2011-05-24
> **KodR said:**
> I am a **telemarketer** and work in a call centre

> I haven't much programming experience

> **KodR said:**
> Thats all I am trying to make, this program I am sure would take minutes to write for someone who is an experienced programmer.

> **KodR said:**
> StephenF please stop posting in my threads, you can never just provide a straight answer, you always have to be difficult with something that has nothing to do with my original post and its so annoying.

> **KodR said:**
> wtf can't people on forums just answer questions straight up instead of suggesting and trying to make themself feel they are complex and superior and all that. Some people have some seriously sad psycological issues. Did I ask for suggestions? no I did not.

> I said I was a noob, why would people start talking accessing databases. I can only think to try and SHOW OFF their skills, how sad - look at me everybody. I don't have time for learning all that!

> Geez. Some poeple lack comm skills.

> **KodR said:**
> ciao

Seems pretty clear to me that this was all a foregone conclusion. From KodR's own words I think we can conclude:

[list]
[*]KodR is not a programmer.
[*]KodR doesn't want to learn programming.
[*]KodR wants Ubuntuforums members to write the program, to given specifications, for free.
[*]KodR wants to pick and choose which Ubuntuforums members are allowed to reply to this help request.
[*]KodR has a very poor opinion of Ubuntuforums members.
[/list]

Yeah. That's about the kind of contemptuous attitude I expected based on the information provided.

'nuff said  :popcorn:

---

### Post by slavik on 2011-05-24
1. I wish I had a baseball bat
2. The requirement is not a windows only solution, just that it needs to run on Windows XP as a standalone program (most likely no admin rights to install anything) which makes sense.
3. Be nice!!!

Relevant to OP:
- py2exe can take Python code and package it properly with an interpreter and you get a standalone executable.
- Keep in mind that if you statically code all the relationships, you will need to update the code every time there is a data update.
- I would suggest keeping a version number to indicate the version/freshness of data.

EDIT: Consider doing this via spreadsheet program.

PS: I don't normally hand out warnings/infractions ... and I hope this thread does not make me start doing it. As it was stated, the OP wants to write the program and he even has the logic down.

---

### Post by Phil Stone on 2011-05-24
kodr,

The best ideal for you right now is to get into Javascript and design a browser style program that will use a form with your input into a 'query' field (text input box) that relates to information arrays that you set up in the javascript to be output to a 'results' field. As you already have knowledge of HTML / CSS this should be a relatively painless step that will also introduce you into the area of OO Programming too. (Thats Object Orientated - but don't worry about that for the moment)

You will generally find that in house computer systems tend to disallow 'proper' scripts being run  as well as reduced or null access to the command line so that route - (php/perl,python) is likely to be impractical anyway. 

You may also find a few tables and array search formulas in excel will also accomplish the desired self-referencing database too. 

Mainly the user interface will need to be straight forward so that anyone can use/update it - this is where excel wins in an office environment as most people basically cannot comprehend updating arrays. But they can update a table in a spreadsheet.

If you do have access to Access well thats just js in a different format aint it???? (idk i never had access to it. But you may want to look into that too as there may be predefined datatable tools within the package.)

If you do go the js route - you will want to set up an HTML <form> with text input field and textboxes, dont worry about looking at radio buttons and checkboxes, also don't wory about validation too much for the moment, these will come later. You will then want the javascript to take the input eg a name 'Phil Stone'. split() it into two parts (the start of two arrays) and output those parts to two more 'text fields'. Such as the first part of the name to the output field 1 and the second part of the name to output field 2. From there you will just need to look at array manipulation using push() pop() split() splice() etc. 

on a side note - the simplest things are often quite complex in programing. If it was that simple you wouldn't need to come on to the forums right? heh. Having said that I would actually recommend using Excel for the task you have. You can create a visual basic (vb) program (macro's for coders :) ) that uses the tables on the spreads as the static data, you/team member will no doubt need to update / maintain these idc. And you will advance your own knowledge in an application that is used very commonly htroughout business. search Vlookup / Hlookup in excel help. Also learn to open, select, save, and close, singular and multiple books / sheets using vb scripts. This also involves scripting so either way you're gonna have to bash some code out somewhere along the line.

Phil

---

### Post by Petrolea on 2011-05-24
This is not the first thread he made. He has multiple accounts I believe. Yesterday there was a thread like this where OP freaked out because of posts not DIRECTLY answering his question (I believe it's the same person).

Porting basic Python code to windows is really easy, it should work right away. Google Python for Windows. People talking about Database were right: If you want to keep 'database' within an array in your code you will have to update & recompile all the time.
Think about it.

---

### Post by tgm4883 on 2011-05-24
Done, 28 lines in python.

Takes 2 csv files (locations, rates)

Too bad the OP left, and was being an... nm. 

I won't be posting the script here.

:EDIT:

37 lines now, about 15 minutes of work and testing. Added in some error messages if the user input isn't found in the list, or if a rate cannot be found.

---

### Post by slavik on 2011-05-24
> **Petrolea said:**
> This is not the first thread he made. He has multiple accounts I believe. Yesterday there was a thread like this where OP freaked out because of posts not DIRECTLY answering his question (I believe it's the same person).

Porting basic Python code to windows is really easy, it should work right away. Google Python for Windows. People talking about Database were right: If you want to keep 'database' within an array in your code you will have to update & recompile all the time.
Think about it.
There is a report button for a reason.

---

### Post by Petrolea on 2011-05-24
> **slavik said:**
> There is a report button for a reason.

Oh, didn't know that, never had to use it. Thanks for info.

---

### Post by satanselbow on 2011-05-24
> **tgm4883 said:**
> 
37 lines now, about 15 minutes of work and testing. Added in some error messages if the user input isn't found in the list, or if a rate cannot be found.

Now I know I shouldn't... and will probably get my wrists slapped... oh well... what the #$%^

:lolflag::lolflag::lolflag::lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by Arndt on 2011-05-24
> **Vox754 said:**
> I think when people, usually coming from Windows, mention "standalone", they refer to the lazy act of having their program being a single executable, "prog.exe".

Thus, they expect to grab this executable, copy it over to other computers, also running Windows, and have it execute there without problems.

Thus, for this user, he doesn't expect to install Python or Java, he just wants it to work, standalone.

To me, "standalone" usually means something like that, too, and I certainly don't come from the Windows world.

---

### Post by Bandit on 2011-05-24
> **slavik said:**
> 

EDIT: Consider doing this via spreadsheet program.



+1  
For real a spread sheet would be so much easier here.
I hate to say it, but if its gonna be on windows, Excel and Access could do this in a snap and would not require any programming skills.

---

