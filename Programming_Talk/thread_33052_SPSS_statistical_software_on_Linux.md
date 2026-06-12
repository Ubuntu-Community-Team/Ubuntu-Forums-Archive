---
title: "SPSS statistical software on Linux"
date: 2005-05-09
forum: Programming Talk
---

### Post by vishnukv on 2005-05-09
I am a newbie to Linux community. Can someone tell me how to run proprietary software like SPSS, which runs on windows or Mac, on a Linux system. If I can run SPSS on Linux then my migration to Linux would be complete.
Thanks in advance.

---

### Post by nocturn on 2005-05-10
[QUOTE=vishnukv]I am a newbie to Linux community. Can someone tell me how to run proprietary software like SPSS, which runs on windows or Mac, on a Linux system. If I can run SPSS on Linux then my migration to Linux would be complete.
Thanks in advance.[/QUOTE]

You can try the Windows version on WINE (free) or Crossover Office (commercial)
It would also be good if you could mail the company behind SPSS for a Linux version, if they have a Mac one, porting should be easy (OS X is Unix).

---

### Post by vishnukv on 2005-05-13
Thanks very much. I will try the company and also WINE if they give a negative reply.

---

### Post by jasplund on 2005-05-13
There´s some alternatives for linux though.

Salstat [http://salstat.sourceforge.net/](http://salstat.sourceforge.net/)
PSPP [http://www.gnu.org/software/pspp/pspp.html](http://www.gnu.org/software/pspp/pspp.html)
R [http://www.r-project.org/](http://www.r-project.org/)
Macanova [http://www.stat.umn.edu/macanova/](http://www.stat.umn.edu/macanova/)

Some of them are in the repositories. I haven´t tried any of them tough

---

### Post by MakubeX on 2005-12-22
I had tried installing SPSS on Wine but it fails to run because it does a "network version/check stuff" and then it terminates afterwards.

I'm using Wine 20050725 and Ubuntu 5.10.

I had also installed it using Cedega/CrossOver but fails to execute in the production of graphs/charts.. (it crashes at this point). I can read/open/write data (.sav files) but it is only at the graph generation part that the program hangs.

Anyone here who had successfully generated this SPSS feature in Linux?

---

### Post by towsonu2003 on 2005-12-22
there is pspp, which is an open version of spss, but under development. There is also the R (link was above, program is in repos / synaptic) which I believe is very well knwn. 

I dont have time to try out these (my adviser would kill me) but I really would like to learn your experiences if you decide to try them...

PS. I would advise you to prefer linux native software (works easier) instead of spss, if you have time to run and learn it of course.

---

### Post by Jengu on 2005-12-23
[QUOTE=MakubeX]
I'm using Wine 20050725 and Ubuntu 5.10.
[/QUOTE]

That version of wine is ancient. Type the following into the console:

sudo gedit /etc/apt/sources.list

And then copy and paste these two lines to the bottom of the file and save it:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

The next time your system checks for updates, it should notice there's a newer version of wine available. If you want to do it immediately instead of waiting for it to catch on, put this in the console:

sudo apt-get update

Then when it's done:

sudo apt-get upgrade

When prompted if you're sure you want to upgrade, press "y" for yes and hit enter.

---

### Post by towsonu2003 on 2005-12-27
what did you end up doing? Still trying to run SPSS trhu Wine, or are you trying linux native statistics packages? If the second, I am very interested in hearing your feedback... thanks.

---

### Post by devnulljp on 2006-01-10
I'd be interested in this too - looks like codeweavers isn't supporting spss, and as noted above it's preferable to use something that's linux-native anyway.

---

### Post by turezky on 2007-06-01
It seems that there exists SPSS15 for Linux, though it has no graphical interface :(
Any more suggestions about analogies???

---

### Post by pmasiar on 2007-06-01
There is another alternative: [R](http://www.r-project.org/). It has convenient Python bindings RPy, so you can process files in Python, then switch to R to heavy-duty number-crunching. Best of both worlds!

---

### Post by raja on 2007-06-01
R. Takes some time to get used to it, but more flexible than SPSS once you get it.

---

### Post by pmasiar on 2007-06-01
... and R is also fully open-source. I was very frustrated by SPSS gaps in documentation, and lack of efforts to fix it properly. 

A help page about importing Excel datasheet was missing, and it was known error, but knowledgebase at website instead of posting original (missing) help page just explained it's content in 2 rather vague and unhelpful sentences. R has incredible amount of external libraries for all kinds of analysis, is same on Win and linux, and GPL: once you learn it, you can keep using it forever.

---

### Post by fabietto0102 on 2007-07-20
Hi,
I installed Wine, the latest version for Ubuntu 7.04, and then installed SPSS (student version, I guess) and it worked fine, at least for the few options I needed (Analysis > Explore, etc..). 
This is a good news as it means Wine works indeed! 

Damn me and my curiosity, I did some experiments and ended up reformatting the HD.. 

I re-installed everything as was before and now SPSS asks me for a licence which never did before. 
Can someone please advise how I could *completely* remove Wine, SPSS, files with registration codes etc to start over again?

Would you raccomend R, btw?

Thanks
Fabietto0102
MacBook (newest)+ Ubuntu 7.04

---

### Post by pmasiar on 2007-07-20
> **fabietto0102 said:**
> Would you raccomend R, btw?

I would recommend R. It is about same league as SPSS, but because it is open source, there are many many modules for it written by academia researchers. I know bioinformatics use it a lot - couple projects for genetics and stuff.

Another good feature R has is: there are python bindings for R, RPy. So you can read your files and get data, then process them in R, get results and process them in Python. Python is *much* simpler and user-friendly scripting language than either SPPS or R have natively.

And because R is free/opensource, you can have it anywhere, you don't need to switch and relearn when changing jobs etc.

---

### Post by tommie74 on 2007-07-21
I have installed SPSS 11.5 under codeweavers cxoffice 6.1.0. (commercial version of wine). I used the same botlle (virtual windwos c: disk) that I installed office 2000 on. Everything seems to work allright except for the graph functions. I can can load data, analyze it, produce tables with output etc. Only producing graphs seems problematic. The install is going smoothly, asking for a serial etc.
So if you can miss graphs, SPSS seems to work allright. The more people us SPSS with cxoffice, the bigger the chance that they will start support on it.
Greetings,
Thomas.

---

### Post by fabietto0102 on 2007-07-22
Thank you pmasiar,

I understand and truly believe R is 10 times better than SPSS, however for a newbie like me it's too difficult to install :( ; say, it's not like installing skype... Unfortunately many things are given for granted by IT experts, and unless it's clearly explained step by step, much will be abandoned. I tried wine again and seems to work, so I'm fine for now. 

I'll wait for the time when R is downloadable out of the box from synaptic., nice and easy!

---

### Post by raja on 2007-07-22
> **fabietto0102 said:**
> Thank you pmasiar,

I understand and truly believe R is 10 times better than SPSS, however for a newbie like me it's too difficult to install :( ; say, it's not like installing skype... Unfortunately many things are given for granted by IT experts, and unless it's clearly explained step by step, much will be abandoned. I tried wine again and seems to work, so I'm fine for now. 

I'll wait for the time when R is downloadable out of the box from synaptic., nice and easy!

fabietto,
I can understand if you say that R is more difficult to use than SPSS. However, what gave the idea that is more difficult to install. It is in the Ubuntu [repos]("http://packages.ubuntu.com/feisty/math/r-base") (Universe). For the latest version, you can even get it directly from CRAN who specifically [support Ubuntu]("http://www.insecta.ufv.br/CRAN/bin/linux/ubuntu/"). 
No IT experts needed - Just do
```
sudo aptitude install r-base
```

---

### Post by pmasiar on 2007-07-22
... and then check r-cran modules available to you (at least 20 or 30) and rejoice! That's the whole point using debian: you don't need to install from sources!

---

### Post by UbuWu on 2007-07-25
Checkout [RKWard]("http://rkward.sourceforge.net/") for an easy to use, transparent frontend to R. It is very similar to SPSS.

---

### Post by raja on 2007-07-25
RKward is still early in development. So it still has very limited functionality and is buggy and prone to crash. Dont try it hoping to find an equivalent to SPSS !

---

### Post by Arwen on 2007-09-05
Hello!Can anyone tell me what to download from [here]("http://rm.mirror.garr.it/mirrors/CRAN/")?And how to install R?
Thank you

---

### Post by pmasiar on 2007-09-05
as I replied before, use synaptic to install R.

---

### Post by nanotube on 2007-09-05
> **Arwen said:**
> Hello!Can anyone tell me what to download from [here]("http://rm.mirror.garr.it/mirrors/CRAN/")?And how to install R?
Thank you

R is in the repositories. install packages "r-base" and "r-recommended", using synaptic or your favorite package manager. no need to download anything from websites. that should get you started.:)

---

### Post by nanotube on 2007-09-05
> **pmasiar said:**
> I would recommend R. It is about same league as SPSS, ....

i'd beg to differ - R is in a way higher league than SPSS. SPSS is limited to whatever stat analysis tools they chose to put into the gui menus. on R you can do whatever you want, there are many many more analysis tools available in the cran packages, and you can even write your own. Only thing is that it's missing the "friendly gui", but in terms of power, it is better. 

p.s. (did you totally dig how i trimmed the quote? :) )

---

### Post by pmasiar on 2007-09-05
> **nanotube said:**
> i'd beg to differ - R is in a way higher league than SPSS.

I agree. I should say "R is at least as good as SPSS". But was afraid to over-embellish R. :-)

>  (did you totally dig how i trimmed the quote? :) 

Yup, I like it. In couple years :-) , maybe most people will trim. I hope... :-/

---

### Post by nanotube on 2007-09-05
> **pmasiar said:**
> I agree. I should say "R is at least as good as SPSS". But was afraid to over-embellish R. :-)

hehe is that even possible? well yea, i guess it is... but it's hard to do. ;)

> 
Yup, I like it. In couple years :-) , maybe most people will trim. I hope... :-/

my future-radar says: doubtful. oh well. ;)

---

### Post by gnuman on 2007-09-05
> **nanotube said:**
> i'd beg to differ - R is in a way higher league than SPSS. SPSS is limited to whatever stat analysis tools they chose to put into the gui menus. on R you can do whatever you want, there are many many more analysis tools available in the cran packages, and you can even write your own. Only thing is that it's missing the "friendly gui", but in terms of power, it is better. 



I'm having to use SAS in a statistical programming class--it's required.  Anyway, I have R installed, along with the R commander, both of which are in the synaptic pkg manager.  I do my assignments in SAS, impress the instructor, and then come home to R, which I plan on using long after my "limited lease" on SAS runs out.

R commander is a very friendly GUI, IMHO:

[http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/](http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/)

---

### Post by larytet on 2007-11-03
SPSS does not work with WINE

but I ran Win2000 under Qemu and installed SPSS
as a bonus i can use evaluation version forever - Qemu allows to save "snapshots" of the OS in so called ovl (overlay) files

---

### Post by daynah on 2007-11-03
I can't figure out how to get R to run. I have r-base and r-base core installed but when I type them in terminal it says they arent a command. RKWard says I don't have r-base-core installed, though apt-get says it's to the highest.

And SPSS wouldn't even install. Suggestions?

---

### Post by ovis.bp on 2007-11-03
hi,

i have to use SPSS at university, and i can get it temp. for free from the univ, but i use ubuntu mostly, so at one side i also have windows on my computer only for this... (i have to send always syntax and output files to the teachers so i can't really change this)

but on the other hand i am a bit fed up with windows so i decided looking for something else. Also because i can only get SPSS for each half year.

i installed R-base (from the terminal) but i am too new at the whole thing (i mean dealing with linux generally) and now i don't find where did this put it...

i am also thinking about using PSPP that must be very similar to SPSS. One of the most important thing is that it should be somehow compatible with .sav files both ways (opening it and saving it like that) without loosing any data on the way of transformation:)

and it would be also good if i could use the same language that i am used to in spss syntax. (also because i am not really good in spss, and how they teach it in school is a bit like copy-pasting all the time, so they give routine but not really knowledge... it's mass education, that's what they can do...

so anyway, is there anyone who's using PSPP in ubuntu? or R? how can i find it if it's not in the applications, but i already installed it?

---

### Post by nanotube on 2007-11-03
> **daynah said:**
> I can't figure out how to get R to run. I have r-base and r-base core installed but when I type them in terminal it says they arent a command. RKWard says I don't have r-base-core installed, though apt-get says it's to the highest.

And SPSS wouldn't even install. Suggestions?

to start R, use command "R" (without quotes) :)

---

### Post by pmasiar on 2007-11-03
Even if you have SPSS free in uni, the time you spent learning is half-wasted if you switch to R. Learn R and be done with it, you can continue using it for the rest of your life, for free.

Of course it depends if your profs are open to learn something new, or they insist of you learning SPSS, because thay are too lazy/busy learning R.

---

### Post by ovis.bp on 2007-11-04
can i open an spss data file (*.sav) with R? how?

i tried it, read the manual and saw this
type  this read.table(file("file.dat", encoding="latin1"))
so i tried like this

read.spss(file("/home/ovis/egyetem/ESS_2005.sav", encoding="latin1"))
Error: could not find function "read.spss"

i looked a bit after it, and checked if i have the recommended package, and installed foreign package to see what happens but it occurred that it is already installed, so i don't know what did i do wrong... maybe i am wrong but it seems for me, that its not even that i typed something wrong, but the function doesn't work at all here...

i tried also PSPP but it couldn't open it, i don't know why. 

it said something like this
PSPP> get /FILE='/home/ovis/egyetem/ESS_2005.sav'.
warning: /home/ovis/egyetem/ESS_2005.sav: Unrecognized record type 7, subtype
        16 encountered in system file.
PSPP> 

can you help in this?

---

### Post by towsonu2003 on 2007-11-04
> **ovis.bp said:**
> can i open an spss data file (*.sav) with R? how?


I really don't know much about R, but navigate (cd) to your R environment and
```

R
library(Rcmdr)

```
And you'll see a GUI open up. you'll be able to open the file using the menus. hope this helps

---

### Post by nanotube on 2007-11-05
> **ovis.bp said:**
> can i open an spss data file (*.sav) with R? how?

i tried it, read the manual and saw this
type  this read.table(file("file.dat", encoding="latin1"))
so i tried like this

read.spss(file("/home/ovis/egyetem/ESS_2005.sav", encoding="latin1"))
Error: could not find function "read.spss"

i looked a bit after it, and checked if i have the recommended package, and installed foreign package to see what happens but it occurred that it is already installed, so i don't know what did i do wrong... maybe i am wrong but it seems for me, that its not even that i typed something wrong, but the function doesn't work at all here...

i tried also PSPP but it couldn't open it, i don't know why. 

it said something like this
PSPP> get /FILE='/home/ovis/egyetem/ESS_2005.sav'.
warning: /home/ovis/egyetem/ESS_2005.sav: Unrecognized record type 7, subtype
        16 encountered in system file.
PSPP> 

can you help in this?

you have to load the foreign library first:
```
library(foreign)
read.spss(blababla)
```

also, to get help on specifics of any command, try the "?":
```
?read.spss
```

---

### Post by Psykotik on 2008-02-04
SPSS for linux is out for a few months : [http://www.spss.com/stores/1/SPSS_reg_Base_16_0_for_Linux_r_P7919C91.cfm](http://www.spss.com/stores/1/SPSS_reg_Base_16_0_for_Linux_r_P7919C91.cfm)

But it is not compatible with compiz, you have to deactivate it to run spss.

---

### Post by retrow on 2008-03-25
Personally I don't have any need for SPSS (so far) but one of my friend in health behaviour wants use do data analysis which has been traditionally done on SPSS in most universities. She has never used Linux in her life, and I was wondering whether it would be a wise move to recommend R to her as it would save her the trouble of being bound to department computers to do her data analysis. Would it benefit her in the long run if I help her in installing Linux on her computer and then R and after showing her how to fire up the program, just cut her loose. 

We are looking at a potential convert here guys (and potential "tech help" and ensuing dates for me)  :lol:

---

### Post by pmasiar on 2008-03-25
She can use R on Windows now, and switch to Linux later when ready. Still better get used to Free R than to be shackled by non-free software.

To get extra date, you can teach her Python and RPy to simplify data processing :-)

---

### Post by nanotube on 2008-03-25
> **pmasiar said:**
> She can use R on Windows now, and switch to Linux later when ready. Still better get used to Free R than to be shackled by non-free software.

To get extra date, you can teach her Python and RPy to simplify data processing :-)

offtopic, but since you brought it up, i thought i might as well ask :) 

i'm curious - since R is a full-fledged programming language in itself, what is the benefit of using rpy anyway? i am not sure i see the point of using rpy, when one can just as (more?) easily just use R? or are there particular types of problems where using R natively would not be as efficient?

and now for my on-topic comment: pmasiar is right, you don't need to switch operating systems in order to use R, it's just as possible to use it from win as from lin. also note that R does have a bit of a learning curve to it (although there are R guis to help one through). that said, if you /want/ to switch to linux, and are thinking "what am i going to do for my data analysis", then R is a very good choice.

---

### Post by retrow on 2008-03-25
> **pmasiar said:**
> She can use R on Windows now, and switch to Linux later when ready. Still better get used to Free R than to be shackled by non-free software.I offered to lend her my laptop on which I loaded R withRKWard and most of the recommended libraries. It would break my heart to disclose to her about the availability of R on Windows, so I will withhold that information unless she starts getting uncomfortable around Ubuntu (which I think is quite unlikely).

> To get extra date, you can teach her Python and RPy to simplify data processing :-)Hehehe...Nice try. Geeks are cool in her book but I don't want to push my luck   :lolflag:

---

### Post by pmasiar on 2008-03-25
> **nanotube said:**
> since R is a full-fledged programming language in itself, what is the benefit of using rpy anyway? i am not sure i see the point of using rpy, when one can just as (more?) easily just use R? or are there particular types of problems where using R natively would not be as efficient?

R is good at statistic calculations. But often you need to process the file with data to be processed, filter, merge, etc, and R is bad at that part.

---

### Post by pmasiar on 2008-03-25
> **retrow said:**
> It would break my heart to disclose to her about the availability of R on Windows, so I will withhold that information

honesty is the best policy, IMHO. She will break **your** heart :-) when she finds out she could have used R on Windows with less confusion, which will inevitable happen at first attempt to google for R help.

You can explain her why free software is better, and why learning to use free software on windows (Firefox, OO.org, R, etc) is best training to be ready for a switch to Linux later. Like when she later wants to use decent but old laptop with 500MB RAM, good luck running Vista on it.

---

### Post by nanotube on 2008-03-26
> **pmasiar said:**
> R is good at statistic calculations. But often you need to process the file with data to be processed, filter, merge, etc, and R is bad at that part.

well, in my experience, R is quite eficient at filtering and merging data sets, more so than python could be. 

e.g., to filter a dataset in R by say, one of the columns having some value or set there of, you could just do
```
filtered = mydata[mydata$var == "targetvalue",]
```

while in python one would have to loop over the data rows? it seems that if there is anything python is better at than R, it surely is /not/ filtering and merging, since R has specialized code to deal with vectors and data frames, while python does not.

got any other ideas (or refutations of what i just said)? :)

---

### Post by nanotube on 2008-03-26
> **pmasiar said:**
> honesty is the best policy, IMHO. She will break **your** heart :-) when she finds out she could have used R on Windows with less confusion, which will inevitable happen at first attempt to google for R help.

heh yea, deliberately withholding information seems like not the nicest thing to do... you would be honest, however, if you said that even though R is cross-platform, rkward is only available on linux, so of course linux is the best choice. :)

---

### Post by retrow on 2008-03-26
> **nanotube said:**
> ...however, if you said that even though R is cross-platform, rkward is only available on linux, so of course linux is the best choice. :)
Well said, and thanks a ton for show me that honesty AND Linux are the only ways to go :)
[IMG]http://www.nolandgrab.org/images/Mr-Burns-Excellent.jpg[/IMG]

---

### Post by CptPicard on 2008-03-26
> **nanotube said:**
> while in python one would have to loop over the data rows? it seems that if there is anything python is better at than R, it surely is /not/ filtering and merging, since R has specialized code to deal with vectors and data frames, while python does not.

Read up on Python's filter, map and list comprehensions. One-liners to transform, select and project your vectors. Having a preference for the functional style myself, I code Python almost exlusively in terms of list transformations and generators whenever I can.

---

### Post by pmasiar on 2008-03-26
> **nanotube said:**
> while in python one would have to loop over the data rows? it seems that if there is anything python is better at than R, it surely is /not/ filtering and merging, since R has specialized code to deal with vectors and data frames, while python does not.

got any other ideas (or refutations of what i just said)? :)

Just recently I needed to create files for further processing, where in given directory I needed to find pairs of files (check naming convention if pair exists), and extract some columns to create one file for further processing. Or another example, two files with comparable data but using different IDs, merge them using ID mapping in another file.

Would you prefer to do it in R? R is good if data you have are ready to be processed, but to get them there, Python (as universal language) is much more flexible. To do statistics, R is better, because R is not focused in all those other things.

---

### Post by nanotube on 2008-03-28
> **pmasiar said:**
> Just recently I needed to create files for further processing, where in given directory I needed to find pairs of files (check naming convention if pair exists), and extract some columns to create one file for further processing. Or another example, two files with comparable data but using different IDs, merge them using ID mapping in another file.

Would you prefer to do it in R? R is good if data you have are ready to be processed, but to get them there, Python (as universal language) is much more flexible. To do statistics, R is better, because R is not focused in all those other things.

hm well, for the first case, pairs of files: extracting particular column out of the data R would be very good at, so yes, i'd use R. 
for the second case, check out R's "merge" command - i would most definitely use R to merge the datasets. (first, merge file1 with the id mapping file by id, then merge the merged file1 with file2 using id2. basically a two-line operation.)

anyway... :) there are some things i have used python for instead of R, namely when i need to use some regexps on the data, (or when the operations i'm doing are complex enough that i have to loop line by line and do my thing anyway.) I am familiar with python's regexps, but from my brief look at R's regexps, they basically make you use grep, so i just stick with python. 

but from the examples you give me, it seems that you should consider using R for more stuff. :)

---

### Post by nanotube on 2008-03-28
> **CptPicard said:**
> Read up on Python's filter, map and list comprehensions. One-liners to transform, select and project your vectors. Having a preference for the functional style myself, I code Python almost exlusively in terms of list transformations and generators whenever I can.

hm, i will look into filter and map, but i do know about list comprehensions... indeed they could serve for some data filtering needs. though not as conveniently as R, i must say. :) 

also, what would be python's reperesentation of a data frame, anyway? seems like it would have to be a dict with lists as values. or for a matrix (no col names) a list of lists... for either of those, how easy would it be to select say, rows 10-20 of a data frame or matrix? surely not as easy as R's ```
mydataframe[10:20,]
``` ?

off to look at map and filter...

---

### Post by quill3033 on 2008-03-28
Also, the Student Graduate Pack of SPSS for linux is out now. It is being sent to me and I've returned a copy of the grad pack for Windows. Hope it works well. It says in the flyer that it only has been tested on Debian and RedHat, so I'll have to see how it works with Ubuntu 6.06.

---

### Post by quill3033 on 2008-03-28
I'm finding R quite difficult to even get up and running, as in entering data etc. I'm only new to stats and just want to do basic stuff and it's a bit of a headache for me at the moment - trying to learn both stats and how to use the program. I got a textbook on R and I'll give it a go. I'm also using SPSS in Windows on a friend's computer (will get my grad pack for linux any day now).

---

### Post by nanotube on 2008-03-28
> **quill3033 said:**
> I'm finding R quite difficult to even get up and running, as in entering data etc. I'm only new to stats and just want to do basic stuff and it's a bit of a headache for me at the moment - trying to learn both stats and how to use the program. I got a textbook on R and I'll give it a go. I'm also using SPSS in Windows on a friend's computer (will get my grad pack for linux any day now).

well, R does take a bit of learning to get started on... the following tutorial may be very helpful (it was to me at the time):
[http://cran.r-project.org/doc/manuals/R-intro.pdf](http://cran.r-project.org/doc/manuals/R-intro.pdf)

---

### Post by quill3033 on 2008-04-01
yep, I've got it. Trouble is I've got R-Commander and want to learn how to use that to import SPSS data but when I go to the relevant menu it doesn't seem to work. 

And I'm torn between learning R from command line or using the other. I have bought the book by Michael Crawley but still going through to find 'how to use R'. 

I've just had the SPSS Grad Pack for Linux delivered and I'm trying to install it. I'm thrilled! Hopefully it will work without a hitch. 

Has anyone got this package and is using Ubuntu 6.06?

---

### Post by nanotube on 2008-04-02
> **quill3033 said:**
> yep, I've got it. Trouble is I've got R-Commander and want to learn how to use that to import SPSS data but when I go to the relevant menu it doesn't seem to work. 

And I'm torn between learning R from command line or using the other. I have bought the book by Michael Crawley but still going through to find 'how to use R'. 

I've just had the SPSS Grad Pack for Linux delivered and I'm trying to install it. I'm thrilled! Hopefully it will work without a hitch. 

Has anyone got this package and is using Ubuntu 6.06?

just learn R, in the long run, if you do any statistics work, it will be learning well spent. :) 

but really, whatever works, if you already have spss and you know how to use it...

---

### Post by quill3033 on 2008-04-03
> **nanotube said:**
> just learn R, in the long run, if you do any statistics work, it will be learning well spent. :) 

but really, whatever works, if you already have spss and you know how to use it...

Really I only have to do stats for my psychology degree and may never use it again other than to read research. I do like SPSS for my very basic purposes. 

It seems to me that people who like R are further up the food chain in terms of stats - they use it for their work etc. and maybe even write programs etc. 

I am enjoying how SPSS (using Windows version on friend's computer) makes pretty graphs out of anything.. 

I would like to be able to operate R just for the hell of it - it's a challenge :-) 

And they seem to have great data sets. ( can see them but don't know what to do with them yet!!! :lolflag:

Still haven't installed Linux version of SPSS.  Just looking on the help page of Ubuntu for instructions for installing from cd. I hope instructions are not just for 7.10 .... I really really like 6.06

---

### Post by quill3033 on 2008-04-05
ok,i've installed it. it says it is in 

/opt/SPSSInc/SPSS16GP but I can't fine it anywhere in the Applications menu and typing SPSS in a terminal window has no effect whatsoever. When i typ the thing above

/opt/SPSSInc/SPSS16GP

it says that it is a directory... I still don't have handle as to where things are and the whole file management program management thing. 

And I can't seem to find a manual that goes through it all. 

Help if anyone has an answer to either question.

---

### Post by nanotube on 2008-04-05
> **quill3033 said:**
> ok,i've installed it. it says it is in 

/opt/SPSSInc/SPSS16GP but I can't fine it anywhere in the Applications menu and typing SPSS in a terminal window has no effect whatsoever. When i typ the thing above

/opt/SPSSInc/SPSS16GP

it says that it is a directory... I still don't have handle as to where things are and the whole file management program management thing. 

And I can't seem to find a manual that goes through it all. 

Help if anyone has an answer to either question.

so find the name of the executable, which should be in the /opt/SPSSInc/SPSS16GP directory. (browse to it through the terminal or with nautilus file browser, and see what lives in that directory).

---

### Post by quill3033 on 2008-04-05
> **nanotube said:**
> so find the name of the executable, which should be in the /opt/SPSSInc/SPSS16GP directory. (browse to it through the terminal or with nautilus file browser, and see what lives in that directory).

Hi, thank you for helping.

what does an executable file look like? I'm used to .exe in windows but I haven't worked it out for linux.

There seem to be a lot of icons  of the cute package type (that seem to indicate program files) and a lot of them are .jar but I don't really know which will actually RUN the program.

There is one that is called **activation.jar** (in the bin folder for SPSS) and I thought I'd run that but don't know whether to press Extract on the toolbar to do this and a bit worried I might do something to stuff up computer.

---

### Post by nanotube on 2008-04-06
> **quill3033 said:**
> Hi, thank you for helping.

what does an executable file look like? I'm used to .exe in windows but I haven't worked it out for linux.

There seem to be a lot of icons  of the cute package type (that seem to indicate program files) and a lot of them are .jar but I don't really know which will actually RUN the program.

There is one that is called **activation.jar** (in the bin folder for SPSS) and I thought I'd run that but don't know whether to press Extract on the toolbar to do this and a bit worried I might do something to stuff up computer.

post the complete output of
```
ls -al /opt/SPSSInc/SPSS16GP
```
and we'll go from there. ;)

---

### Post by quill3033 on 2008-04-06
> **nanotube said:**
> post the complete output of
```
ls -al /opt/SPSSInc/SPSS16GP
```
and we'll go from there. ;)

Here's what it said listing the content (?). I used the command you gave me (I knew about -a but not -al)

~$ ls -al /opt/SPSSInc/SPSS16GP
total 132
drwxr-xr-x 6 root root  4096 2008-04-05 22:24 .
drwxr-xr-x 3 root root  4096 2008-04-05 22:17 ..
drwxr-xr-x 9 root root  8192 2008-04-05 22:30 bin
drwxr-xr-x 2 root root 12288 2008-04-05 22:24 lib
-rw-r--r-- 1 root root 42409 2008-04-05 22:24 log.txt
-rw-rw-rw- 1 root root 45164 2007-11-08 15:43 readme.txt
drwxr-xr-x 2 root root  8192 2008-04-05 22:22 samples
drwxr-xr-x 2 root root  4096 2008-04-05 22:23 _uninst


Does that last line mean that it is still uninstalled? I ticked the option of the 2 week trial in the graphic interface and that; may account for it but it shouldnt . It did exactly the same as the windows version.  Thanks again, Nanotube :)

---

### Post by nanotube on 2008-04-07
> **quill3033 said:**
> Here's what it said listing the content (?). I used the command you gave me (I knew about -a but not -al)

~$ ls -al /opt/SPSSInc/SPSS16GP
total 132
drwxr-xr-x 6 root root  4096 2008-04-05 22:24 .
drwxr-xr-x 3 root root  4096 2008-04-05 22:17 ..
drwxr-xr-x 9 root root  8192 2008-04-05 22:30 bin
drwxr-xr-x 2 root root 12288 2008-04-05 22:24 lib
-rw-r--r-- 1 root root 42409 2008-04-05 22:24 log.txt
-rw-rw-rw- 1 root root 45164 2007-11-08 15:43 readme.txt
drwxr-xr-x 2 root root  8192 2008-04-05 22:22 samples
drwxr-xr-x 2 root root  4096 2008-04-05 22:23 _uninst


Does that last line mean that it is still uninstalled? I ticked the option of the 2 week trial in the graphic interface and that; may account for it but it shouldnt . It did exactly the same as the windows version.  Thanks again, Nanotube :)

aha, i think it's probably under the 'bin' subdirectory (bin usually stands for "binary" and is where binary executables are located). post output of:
```
ls -al /opt/SPSSInc/SPSS16GP/bin
``` 
i'm guessing there will be a binary called spss or something like that in there somewhere. :)

---

### Post by quill3033 on 2008-04-07
i'm guessing there will be a binary called spss or something like that in there somewhere. :)[/QUOTE]


Mmh - the output is five pages long. A few "spss' but no files with extension bin (still thinking microsoft? :confused:

Here it is (just remember this is what you asked me to do- it's very long). Thanks again. Cheers. :)

total 137984
drwxr-xr-x  9 root root     8192 2008-04-05 22:30 .
drwxr-xr-x  6 root root     4096 2008-04-05 22:24 ..
-rwxr-xr-x  1 root root    54665 2002-08-29 04:50 activation.jar
-rwxr-xr-x  1 root root     2494 2004-04-08 03:36 AppIcon.ico
-rwxr-xr-x  1 root root  1599570 2006-05-02 07:11 axis.jar
-rwxr-xr-x  1 root root  6741589 2004-07-13 06:59 br_portuguese.dict
-rwxr-xr-x  1 root root  1717664 2007-04-11 04:30 castor-1.1.jar
-rwxr-xr-x  1 5213   31      980 2008-01-17 09:47 castor.properties
-rwxr-xr-x  1 root root  1436247 2007-11-17 07:04 ChartEditor.jar
-rwxr-xr-x  1 root root      244 2007-08-24 03:29 clientscriptingcfg.ini
-rwxr-xr-x  1 root root     3868 2007-03-03 09:30 CmdLineParamHelp.txt
-rwxr-xr-x  1 root root    46725 2007-02-27 10:51 commons-codec-1.3.jar
-rwxr-xr-x  1 root root    71442 2006-05-02 07:10 commons-discovery-0.2.jar
-rwxr-xr-x  1 root root    38015 2006-05-02 07:10 commons-logging-1.0.4.jar
-rwxr-xr-x  1 root root      606 2007-10-23 07:02 commute.dat
-rwxr-xr-x  1 root root   152257 2007-11-15 12:03 cop-client.jar
-rwxr-xr-x  1 root root     6201 2007-11-17 07:05 CoreTools.jar
-r--r--r--  1 5213   31    15845 2008-01-17 09:47 dictionary-1.0.xsd
-rwxr-xr-x  1 root root    14460 2007-11-29 02:51 dregedit.dat
-rwxr-xr-x  1 root root  4765409 2004-03-11 08:08 dutch.dict
-rwxr-xr-x  1 root root  1227935 2007-10-23 07:01 echoid
-rwxr-xr-x  1 root root        5 2007-05-16 23:54 echoid.dat
-rwxr-xr-x  1 root root   487253 2007-10-23 07:19 echouid
-rwxr-xr-x  1 root root     5339 2007-06-09 07:24 email_location.properties
-rwxr-xr-x  1 root root    19267 2007-11-17 07:05 emfProcessor.jar
-rwxr-xr-x  1 root root     5341 2007-11-17 07:05 exacc.jar
-rwxr-xr-x  1 root root  4066457 2007-11-03 17:38 excel2007.jar
-rwxr-xr-x  1 root root    89309 2007-11-17 07:05 ExportTools.jar
-r--r--r--  1 root root    10000 2007-10-27 02:20 extension-1.0.xsd
-rwxr-xr-x  1 root root  5533771 2004-03-11 08:15 french.dict
-rwxr-xr-x  1 root root  6755059 2004-03-11 08:30 german.dict
-rwxr-xr-x  1 root root   287806 2007-11-17 07:04 gpl.jar
drwxr-xr-x  7 root root     4096 2008-04-05 22:22 help
-rwxr-xr-x  1 root root     5020 2007-02-04 09:41 help.htm
-r--r--r--  1 5213   31      498 2008-01-17 09:47 htmlfram.txt
-rwxr-xr-x  1 root root   466920 2007-10-27 02:13 initspsslinux
-rwxr-xr-x  1 root root  4909723 2006-10-31 06:09 italian.dict
-rwxr-xr-x  1 root root  1802694 2007-03-20 01:30 itext-2.0.1.jar
-rwxr-xr-x  1 root root    12298 2007-11-17 07:05 jaguar_treemodel.jar
-rwxr-xr-x  1 root root   203109 2002-05-18 03:08 jai_codec.jar
-rwxr-xr-x  1 root root  1431422 2002-05-18 03:08 jai_core.jar
-rwxr-xr-x  1 root root    31191 2006-05-02 07:10 jaxrpc.jar
-rwxr-xr-x  1 root root   455489 2007-02-27 09:08 JimiProClasses.zip
-rwxr-xr-x  1 root root     3419 2007-11-17 06:46 JRegEdit.jar
drwxr-xr-x  6 root root     4096 2008-04-05 22:17 _jvm
-rwxr-xr-x  1 root root     1611 2007-11-09 04:13 jvmcfg.ini
drwxr-xr-x 13 root root     4096 2008-04-05 22:23 lang
-rwxr-xr-x  1 root root     4481 2007-03-05 14:07 lawhelp.htm
-rwxr-xr-x  1 root root   961762 2007-01-31 06:43 lawutil
-rwxr-xr-x  1 root root  1241363 2007-10-23 07:01 lcommute
-rwxr-xr-x  1 root root      214 2007-08-07 05:02 liccom.sh
-rwxr-xr-x  1 root root      235 2007-11-28 07:59 licin.sh
-rwxr-xr-x  1 root root      343 2007-11-28 07:59 lic.sh
-rwxr-xr-x  1 5213   31  1443243 2008-01-17 07:35 lmsholic
-r--r--r--  1 5213   31     1405 2008-01-17 09:47 locale-map-1.0.xsd
-r--r--r--  1 5213   31     9817 2008-01-17 09:47 loclmap.xml
drwxr-xr-x  2 root root     4096 2008-04-05 22:22 Looks
-rwxr-xr-x  1 root root   286529 2007-03-02 09:56 looks-1.3.1.jar
-rwxr-xr-x  1 root root      369 2007-11-28 08:01 lopts
-rwxr-xr-x  1 root root   669902 2007-10-23 07:01 lsclean
-rwxr-xr-x  1 root root   492575 2007-10-23 07:01 lsdecode
-rwxr-xr-x  1 root root  1269106 2007-10-23 07:01 lserv
-rw-r--r--  1 root root       87 2008-04-05 22:30 lservrc
-rwxr-xr-x  1 root root  1246154 2007-10-23 07:01 lslic
-rwxr-xr-x  1 root root  1253257 2007-10-23 07:01 lsmon
-rwxr-xr-x  1 root root   430576 2007-10-23 07:01 lspool
-rwxr-xr-x  1 root root   470254 2007-10-23 07:01 lsrevoke
-rwxr-xr-x  1 root root  1223746 2007-10-23 07:01 lsrvdown
-rwxr-xr-x  1 root root   460425 2007-10-23 07:01 lsusage
-rwxr-xr-x  1 root root      433 2007-10-23 07:01 lsver
-rwxr-xr-x  1 root root   424999 2007-10-23 07:01 lswhere
-rwxr-xr-x  1 root root   327603 2003-06-25 15:05 mail.jar
-rwxr-xr-x  1 root root      215 2007-11-17 06:46 Manifest.mf
drwxr-xr-x  2 5213   31     4096 2008-01-17 09:30 MapData
-rwxr-xr-x  1 root root      497 2007-09-05 14:58 modules.js
-rwxr-xr-x  1 root root      853 2007-09-05 14:58 modules.xsl
-rwxr-xr-x  1 root root    24576 2007-07-19 02:07 omsgui.ini
-rwxr-xr-x  1 5213   31    42019 2008-01-17 07:35 packagetest
-rwxr-xr-x  1 5213   31    13130 2008-01-17 09:47 pesworker.jar
-rwxr-xr-x  1 root root     4481 2007-03-05 14:23 phonelist.htm
-rwxr-xr-x  1 root root      525 2007-04-18 02:36 phone_location.properties
-rwxr-xr-x  1 root root   509282 2007-11-17 07:05 PivotTableEditor.jar
-r--r--r--  1 5213   31   106386 2008-01-17 09:47 pmml-3-1.xsd
-rwxr-xr-x  1 root root   909270 2007-06-28 12:41 poi-3.0.1.jar
-rwxr-xr-x  1 root root  7557989 2004-07-14 02:11 portuguese.dict
-rwxr-xr-x  1 root root     6492 2007-07-20 06:02 Predefined Validation Rules SP SS.sav
-rwxr-xr-x  1 root root      251 2007-10-04 06:49 pref.sh
-rwxr-xr-x  1 5213   31   900109 2008-01-17 08:27 prodconvert
-rwxr-xr-x  1 root root     9767 2007-07-19 04:19 production-1.0.xsd
-rwxr-xr-x  1 root root     1495 2007-06-23 01:43 productnames.ini
-rwxr-xr-x  1 root root   136701 2006-12-21 07:21 RapidSpell.jar
-rwxr-xr-x  1 root root  1228025 2007-10-23 07:01 rcommute
-rwxr-xr-x  1 root root    91628 2007-10-24 03:04 repository-client-application. jar
-rwxr-xr-x  1 root root   801512 2007-08-27 11:49 repository-client.jar
-rwxr-xr-x  1 root root   379510 2007-11-17 07:05 repository-ui.jar
-rwxr-xr-x  1 root root   568104 2007-10-23 07:01 rlftool
-rwxr-xr-x  1 5213   31     3235 2008-01-17 09:47 runapp.sh
-rwxr-xr-x  1 root root    18979 2006-05-02 07:11 saaj.jar
-rwxr-xr-x  1 5213   31     3364 2008-01-17 09:46 sadmcfgfile
-rwxr-xr-x  1 5213   31     2063 2008-01-17 09:46 sadmcfgfile.awk
-rwxr-xr-x  1 5213   31     4609 2008-01-17 09:46 sadmrestart
-rwxr-xr-x  1 5213   31     2696 2008-01-17 09:46 sadmtmpdir
-rwxr-xr-x  1 5213   31     1884 2008-01-17 09:46 sadmtmpdir.awk
-r--r--r--  1 5213   31      300 2008-01-17 09:46 Sampling.txt
-r--r--r--  1 5213   31      831 2008-01-17 09:47 savexml.dtd
-rwxr-xr-x  1 root root   331961 2007-04-20 13:43 security-client.jar
-rw-rw-rw-  1 5213   31     5104 2008-01-17 09:47 serverconfig.xml
-rw-r--r--  1 root root      108 2008-04-05 22:24 setenvperm.sh
-rw-r--r--  1 root root      349 2008-04-05 22:24 setupenv1.sh
-rw-r--r--  1 root root     3637 2008-04-05 22:24 setupenv.sh
-rwxr-xr-x  1 root root       90 2008-04-05 22:24 showlic
-rwxr-xr-x  1 5213   31  1444398 2008-01-17 07:35 SHOWLIC
-rwxr-xr-x  1 5213   31      100 2008-01-17 09:47 sort-options.conf
-rwxr-xr-x  1 root root 13524257 2004-03-11 08:35 spanish.dict
-rwxr-xr-x  1 root root      117 2008-04-05 22:24 spss
-rwxr-xr-x  1 5213   31   324121 2008-01-17 08:27 SPSS
-rwxr-xr-x  1 root root       96 2008-04-05 22:24 spssactivator
-rwxr-xr-x  1 root root   994143 2006-12-15 06:41 SPSSACTIVATOR
-rwxr-xr-x  1 root root   228389 2007-10-17 01:48 spssactivator.jar
-rwxr-xr-x  1 5213   31     3174 2008-01-17 09:46 spssadmc
-rwxr-xr-x  1 root root 20015772 2007-04-27 01:50 spssbase.pdf
-rwxr-xr-x  1 root root  1241370 2007-11-17 07:05 SpssClientCore.jar
-rwxr-xr-x  1 root root  9933244 2007-11-17 07:06 SpssClientUI.jar
-r--r--r--  1 5213   31     4989 2008-01-17 09:47 spss-complex-samples-1.0.dtd
-rw-rw-rw-  1 5213   31     5430 2008-01-17 09:46 spssd.conf
-rwxr-xr-x  1 root root     1334 2008-01-19 04:16 spssdxcfg.ini
-rwxr-xr-x  1 root root       10 2008-04-05 22:24 spssenv.sh
-rwxr-xr-x  1 root root    96156 2007-12-21 08:34 spssexcel.jar
lrwxrwxrwx  1 5213   31        5 2008-04-05 22:23 spsslave.exe -> spssd
-rwxr-xr-x  1 root root       98 2008-04-05 22:24 spsslicense
-rwxr-xr-x  1 root root    10134 2005-06-24 02:57 spssmgr.ico
-r--r--r--  1 5213   31     2454 2008-01-17 09:47 spss-oms-log-1.1.xsd
-r--r--r--  1 5213   31    12931 2008-01-17 09:47 spss-output-1.3.xsd
-rwxr-xr-x  1 root root      726 2008-04-05 22:22 spssprod.inf
-rwxr-xr-x  1 root root      933 2007-11-17 08:48 spsssln.sh
-rwxr-xr-x  1 5213   31     2568 2008-01-17 09:46 spssuser
-rwxr-xr-x  1 5213   31    45997 2008-01-17 07:31 SPSSUSER
-rwxr-xr-x  1 root root  6755059 2006-10-31 06:02 swissgerman.dict
-r--r--r--  1 5213   31     1537 2008-01-17 09:47 syncsrt.srt
-r--r--r--  1 5213   31    15723 2008-01-17 09:47 table-looks-1.0.xsd
-rwxr-xr-x  1 root root       90 2007-04-13 04:52 tar.sh
drwxr-xr-x  2 root root     4096 2008-04-05 22:22 template
-rwxr-xr-x  1 5213   31    34467 2008-01-17 09:32 testload
-rwxr-xr-x  1 5213   31    32353 2008-01-17 07:31 threadtest
-rwxr-xr-x  1 root root   152016 2007-11-17 07:05 transformations.jar
-r--r--r--  1 root root   110174 2007-06-26 03:40 transformation.xsl
-rwxr-xr-x  1 root root   189113 2007-11-17 07:05 TreeEditor.jar
-rwxr-xr-x  1 root root   141112 2007-11-17 07:05 TreeModel.jar
-r--r--r--  1 5213   31    15950 2008-01-17 09:47 treeview-1.0.xsd
-rwxr-xr-x  1 root root   359764 2007-11-17 07:05 TreeViewer.jar
-rwxr-xr-x  1 root root   392594 2007-11-17 07:05 TreeViewerPanel.jar
-rwxr-xr-x  1 root root      138 2007-11-28 08:21 trial.txt
drwxr-xr-x  4 root root     4096 2008-04-05 22:18 tutorial
-rwxr-xr-x  1 root root   372668 2007-11-17 07:06 UITools.jar
-rwxr-xr-x  1 root root  2217177 2005-08-06 01:16 uk_english.dict
-rwxr-xr-x  1 root root   340635 2007-10-23 07:01 ulsdcod
-rwxr-xr-x  1 root root       83 2008-04-05 22:24 uninstallspss
-rwxr-xr-x  1 root root  2209197 2005-08-06 01:16 us_english.dict
-r--r--r--  1 5213   31     1345 2008-01-17 09:46 UserSettings.xml
-rwxr-xr-x  1 root root  2284571 2005-08-06 01:15 usuk_english.dict
-rwxr-xr-x  1 root root     4523 2005-10-27 04:28 ViewableTree.jar
-r--r--r--  1 5213   31     4084 2008-01-17 09:47 viewer-appearance-1.0.xsd
-r--r--r--  1 5213   31     5762 2008-01-17 09:47 viewer-pagesetup-1.0.xsd
-r--r--r--  1 5213   31    57357 2008-01-17 09:47 viewer-style-1.0.xsd
-r--r--r--  1 5213   31     4695 2008-01-17 09:47 viewer-table-1.0.xsd
-r--r--r--  1 5213   31     3494 2008-01-17 09:47 viewer-text-1.0.xsd
-r--r--r--  1 5213   31     6981 2008-01-17 09:47 viewer-tree-1.0.xsd
-r--r--r--  1 5213   31     2885 2008-01-17 09:47 viewer-treemodel-1.0.xsd
-rwxr-xr-x  1 root root    39019 2007-11-17 07:06 VisSupport.jar
-rwxr-xr-x  1 root root  3382382 2007-11-17 07:06 visualization.jar
-rwxr-xr-x  1 root root    38018 2007-11-17 07:06 VisUtils.jar
-rwxr-xr-x  1 root root     3150 2007-11-17 07:06 VizConverter.jar
-rwxr-xr-x  1 root root    95450 2007-11-17 07:06 VizImager.jar
-r--r--r--  1 root root   135264 2007-11-16 08:14 vizml-1.3.xsd
-r--r--r--  1 root root   170386 2007-11-16 08:14 vizml-1.4.xsd
-r--r--r--  1 root root   272629 2007-11-16 08:14 vizml-2.0.xsd
-r--r--r--  1 root root   369863 2007-11-16 08:14 vizml-2.1.xsd
-r--r--r--  1 root root   405756 2007-11-16 08:14 vizml-2.2.xsd
-r--r--r--  1 root root   445680 2007-11-16 08:14 vizml-2.3.xsd
-r--r--r--  1 root root   493451 2007-11-16 08:14 vizml-2.4.xsd
-r--r--r--  1 5213   31     1346 2008-01-17 09:47 vizml-data-1.0.xsd
-r--r--r--  1 5213   31     1323 2008-01-17 09:47 vizml-data-2.0.xsd
-r--r--r--  1 5213   31     1859 2008-01-17 09:47 vizml-data-2.1.xsd
-rw-r--r--  1 root root      361 2008-04-05 22:23 vizml.sh
-r--r--r--  1 5213   31    68739 2008-01-17 09:47 vizml-template-1.0.xsd
-r--r--r--  1 5213   31    70786 2008-01-17 09:47 vizml-template-2.0.xsd
-r--r--r--  1 5213   31   171094 2008-01-17 09:47 vizml-template-3.0.xsd
-rwxr-xr-x  1 root root   126771 2006-05-02 07:11 wsdl4j-1.5.1.jar
-rwxr-xr-x  1 root root   116047 2007-02-27 11:23 xmlrpc-2.0.1.jar

---

### Post by nanotube on 2008-04-07
it doesn't have to have a .bin extension - extensions are a windows thing, really.
i see a few candidates in that list:

spss
SPSS
runapp.sh

so... try just try running them, e.g.:
```
/opt/SPSSInc/SPSS16GP/bin/spss
```
and see what it says. :)

but really... i'm surprised there are no help files that tell you where things are. hmm, maybe there is a link to it in /usr/bin/spss? look for that too. ;)

---

### Post by quill3033 on 2008-04-07
spss
SPSS
runapp.sh


Trying that - the first works (haven't yet tried the others, will do) but it won't open any of my spss data files - it goes to my home directory but when i click on the folders that lead to the sub folder ie. Desktop to then hopefully click on psyc202 folder to then open data spss folder etc it won't do it. it tries to open a folder **as though it were the data file**  and of course it can't. So i'm collecting the file  name in a string to insert in the little window. 


but really... i'm surprised there are no help files that tell you where things are. hmm, maybe there is a link to it in /usr/bin/spss? look for that too. ;)[/QUOTE]

Will look for help file. The Installation Single User Licence wasnt much help it only had a couple of isntructions to the effect that you should open the setup.bin file which we have done. Will keep you posted. 

At least this is progress. I'm going to contact the company also. I do think it's good they at least have a linux version. Won't it be good when programs come on a disk and you can just click Windows, or Apple or Linux or whatever other distro there is out there? :)

Thanks again. :)

---

### Post by nanotube on 2008-04-07
> **quill3033 said:**
> spss
SPSS
runapp.sh


Trying that - the first works (haven't yet tried the others, will do) but it won't open any of my spss data files - it goes to my home directory but when i click on the folders that lead to the sub folder ie. Desktop to then hopefully click on psyc202 folder to then open data spss folder etc it won't do it. it tries to open a folder **as though it were the data file**  and of course it can't. So i'm collecting the file  name in a string to insert in the little window. 


but really... i'm surprised there are no help files that tell you where things are. hmm, maybe there is a link to it in /usr/bin/spss? look for that too. ;)

Will look for help file. The Installation Single User Licence wasnt much help it only had a couple of isntructions to the effect that you should open the setup.bin file which we have done. Will keep you posted. 

At least this is progress. I'm going to contact the company also. I do think it's good they at least have a linux version. Won't it be good when programs come on a disk and you can just click Windows, or Apple or Linux or whatever other distro there is out there? :)

Thanks again. :)

sounds like they have a bug....
hey, at least you have something.
good luck, have fun. :)

---

### Post by quill3033 on 2008-04-08
yep, the bug is that even though I clicked on the 'temporary license" option, it on the one hand knows that this temp licence runs out 22 april but on the other tells me that my license has expired. I've emailed company and waiting for reply.

In the message it tells me that my 'temp licence for WINDOWS" has expired which is cute. 

But it does open beautifully - :lolflag: go figure.

thanks again!:)

---

### Post by nanotube on 2008-04-08
hehe nice
it seems they haven't tested their linux port much before releasing it...

---

### Post by quill3033 on 2008-04-08
yep, they're having problems with daylight saving finishing. any time your computer times change the programs suspects that you are trying to illegally extend your licence and shuts down.

they're getting back to me. :(

---

### Post by nanotube on 2008-04-08
> **quill3033 said:**
> yep, they're having problems with daylight saving finishing. any time your computer times change the programs suspects that you are trying to illegally extend your licence and shuts down.

they're getting back to me. :(

heh, that's why we like free software - none of this bs to deal with. ( R! :) )

---

### Post by pmasiar on 2008-04-09
> **nanotube said:**
> hehe nice
it seems they haven't tested their linux port much before releasing it...

They don't test Windows release either.

I had my own set of problems with SPSS. i needed to import Excel spreadsheet, and help page about it was missing in the system help. Google found that it is FAQ, and not hold to your seat: instead of posting missing help page on their website, some drunken brain-dead helpbot wrote totally useless summary in two paragraphs of what was on the page, with no pictures or anything. 

No thanks, if I have to struggle to learn something, I prefer to learn free software which I can use anytime. R is not as click-friendly, but text-based help is better as text commands you can copy-paste than screenscraped images where to click, IMNSHO.

---

### Post by minhaaj on 2008-07-11
Well an SPSS for linux would be great.

---

### Post by Benic on 2008-09-11
For those looking for something more powerful than SPSS, Stata 10 is now available with a Linux license. Stata is less user-friendly than SPSS. You need to learn a lot of syntax, but that won't afraid Linux users... ;) 

You can switch your Stata 10 Windows license for a Linux license (it will cost you some money), which is way cheaper than buying a new license. I refer you to this thread:[http://ubuntuforums.org/showthread.php?t=870519&highlight=stata](http://ubuntuforums.org/showthread.php?t=870519&highlight=stata)

A must have for all number crunchers is Stat/Transfer. As its name suggests, it can transfer data between most statistical software: Excel, SPSS, Stata, SAS, R, etc. So you can build your database with Excel and then switch to SPSS or Stata and work with it. You can also convert files, turning a SAS file into a SPSS one, for example. There's no Linux version yet. I haven't tried it with Wine. Anyone did?

---

### Post by nanotube on 2008-09-13
> **Benic said:**
> 
A must have for all number crunchers is Stat/Transfer. As its name suggests, it can transfer data between most statistical software: Excel, SPSS, Stata, SAS, R, etc. So you can build your database with Excel and then switch to SPSS or Stata and work with it. You can also convert files, turning a SAS file into a SPSS one, for example. There's no Linux version yet. I haven't tried it with Wine. Anyone did?

R can import data files from all those formats (including SAS formats, but needs an extra SAS reader installed...), so I don't really see the need. :) 

and it's free. :)

but anyway, in the process of looking up stat/transfer, i saw on their website that they have a version for "unix", which probably includes linux.

---

### Post by quill3033 on 2008-09-16
Just a couple of questions: 
1. I have R and even bought text book for it and tried to teach myself. I was going through the Rmcdr. But found it too difficult. I imagine that if I knew quite a bit about stats to begin with I'd be ok - am I right? Are most people who use R out there pretty good with stats to begin with? 

2. what is the point of being able to import from excel if it is windows based? I've tried importing open office spreadsheets with it and not been able to (which of course doesn't mean it can't be done). I also downloaded the Excel files for an assignment and tried to import that data, again without success. 
I have some SPSS data files from the SPSS books I bought for uni (came with cd) and again, no luck importing those files to play around with in R. If I could do that then I could try to follow the assignments that way.

PS there is no rush on this as I dropped the stats subject and won't pick it up again till next year - but I'd like to play around with R now to see if it would be possible to do my assignments on it instead of SPSS.

---

### Post by nanotube on 2008-09-16
Hi,
the built-in functions just read the various forms of delimited text files (see help on read.table function (by typing "?read.table" at the R prompt (without quotes))). 

The package 'foreign' provides capability to read various other file formats. to use those functions, load library foreign (install if it's not installed yet). see docs for the library here: [http://cran.r-project.org/web/packages/foreign/index.html](http://cran.r-project.org/web/packages/foreign/index.html)

There is another package to read xls files but... the easiest way to do those is to convert them to csv, then read with read.table. So just use your openoffice to save the data files as delimited text, and you're good to go.

hope this helps. :)

---

### Post by Benic on 2008-09-26
> **nanotube said:**
> R can import data files from all those formats (including SAS formats, but needs an extra SAS reader installed...), so I don't really see the need. :) 

and it's free. :)

but anyway, in the process of looking up stat/transfer, i saw on their website that they have a version for "unix", which probably includes linux.

I agree with you, the R import tool is nice. Stat/transfer is an interesting addition if you have to work with different people using different software (it's my situation unfortunately :sad:). You can customize you import-export easily and it works with any given statistical software (as far as I know). But 180$ (60$ student version) is quite expensive for such a small tool, unless you make someone else pay for it... ;)

---

### Post by LexLuthor08 on 2008-10-18
please tell me where I an find the authorization wizard in spss for linux.

because 16.0 comes without many analyze functions, I have to enter the code for the addon...

---

### Post by sfbaaz on 2009-03-17
I have installed SPSS 17 on the Linux distribution Ubuntu 8.10. The installation and licensing of the program proceeded without any error message.

But when I am running SPSS, I get a repeatable locking of the screen. It happens mostly when I click Edit on the menu bar, but sometimes also with other menu items. The drop-down menu opens as expected, but when I move the cursor to point on File, the screen is locked.

After about half a minute a message box opens, saying "Timeout waiting for server response". When I click OK, this box appears once more. After a new click on OK, the screen is "unlocked" and I can continue working with the program.

This screen behavior is repeatable, as said above, but it doesn't occur every time I open the Edit drop-down menu. However, too often to be neglectable.

The software manufacturer, SPSS Inc, has only support for Red Hat Enterprise and Debian 4.0. Therefore I try to get an answer from this forum. I can mention that the problem described above does not occur with Debian 5.0.  

System info given by my Ubuntu installation:
PC Unix x86 (Ubuntu 8.10)
Kernel Linux 2.6.27-11-generic
GNOME 2.24.1
Memory 512 MiB
Processor Intel Celeron 1300 MHz
Available disk spade 2.8 GiB
-- 
Graphics Card Intel 82815 Graphics controller (obtained via Windows XP)
Screen resolution 1024x768 px.

---

### Post by grantbuntu on 2009-05-24
I recently launched a new open source option - SOFA Statistics (Statistics Open For All) - [http://www.sofastatistics.com]("http://www.sofastatistics.com").  Deb packages are available from the downloads page there and I have tested it on Jaunty, Karmic and Lucid (which is the main development platform).

I have used SPSS extensively since 1989 (on mainframe and then Windows) but I was looking for something different and ended up building it myself ;).  SOFA Statistics is still in development but the current version 0.9.11 connects to SQLite, MySQL, MS SQL Server, MS Access, and PostgreSQL, and the report table-making functionality (frequencies, cross tabs, simple report lists) is complete.  Direct data entry is possible; importing data from CSV and spreadsheets (EXCEL, OpenOffice Calc, Gnumeric, and Google Docs) has been added; and there is an integrated interactive guide for choosing the appropriate statistical test.  This guide also lets users test the normality of their data visually and with tests of skew and kurtosis.  The following main tests are included: independent and paired sample t-tests, one-way ANOVA, Kruskal-Wallis H, Pearson's Chi Square (now with Contingency tables), the Mann Whitney U, Wilcoxon Signed Ranks, Pearson's R, and Spearmans's R.  See [http://www.sofastatistics.com/features.php]("http://www.sofastatistics.com/features.php").  Internationalisation is now supported, with Galician being the first language translated into.

Feedback welcome.

---

### Post by lenu on 2009-08-24
i'm trying to install spss 17 on my ubuntu. the installation goes fine, but wine doesn't seem to be able to open the program. i'm using a cd-rom for windows, is that the problem? i can't find a linux version of spss 17 anywhere on the internet. i got the cd from my university.

- so i have a license. (actually i'm using a license server), but although i was able to give that piece of information when i installed, it still doesn't work.

i also have a copy of "spss 16 for linux", downloaded from thepiratebay. don't know though how i could get the license server information inserted into that version.

---

### Post by Benic on 2009-08-24
> **lenu said:**
> i'm trying to install spss 17 on my ubuntu. the installation goes fine, but wine doesn't seem to be able to open the program. i'm using a cd-rom for windows, is that the problem? i can't find a linux version of spss 17 anywhere on the internet. i got the cd from my university.

- so i have a license. (actually i'm using a license server), but although i was able to give that piece of information when i installed, it still doesn't work.

i also have a copy of "spss 16 for linux", downloaded from thepiratebay. don't know though how i could get the license server information inserted into that version.

No need to use a Windows version. SPSS, as well as Stata, now have universal java versions that work with Linux. I tried both and I can say that for Stata it's even better than the original when using some specific functions.

---

### Post by darkween on 2009-08-24
SPSS installed ubuntu 9.04, everything perfect. but when I try to open the program, I can not find any executable, so I thought it would be like having to open jdownloader under Java. I found a file called who spoke spssIn.sh JRegEdit.jar file, which try to open with Java 6 runtime but I can not start the program. any help?

sorry for my english

---

### Post by lenu on 2009-08-28
> **Benic said:**
> No need to use a Windows version. SPSS, as well as Stata, now have universal java versions that work with Linux. I tried both and I can say that for Stata it's even better than the original when using some specific functions.

but that will mean i'd have to buy *another* copy of spss right? the situation is rather annoying in the sense that my university has spss for windows + licenses that i'm allowed to use, but i don't get how i could get hold of the java version without paying for it just as i would without anything at all?

---

### Post by Jerubaal on 2009-08-28
> **lenu said:**
> but that will mean i'd have to buy *another* copy of spss right? the situation is rather annoying in the sense that my university has spss for windows + licenses that i'm allowed to use, but i don't get how i could get hold of the java version without paying for it just as i would without anything at all?

I am in exactly the same position :(

---

### Post by Benic on 2009-08-28
> **darkween said:**
> SPSS installed ubuntu 9.04, everything perfect. but when I try to open the program, I can not find any executable, so I thought it would be like having to open jdownloader under Java. I found a file called who spoke spssIn.sh JRegEdit.jar file, which try to open with Java 6 runtime but I can not start the program. any help?

sorry for my english

If you installed it as described in the installation documentation, look for
/opt/SPSSInc/SPSS16/bin/SPSS

You can add it to your start menu and it opens right away.

---

### Post by Benic on 2009-08-28
> **lenu said:**
> but that will mean i'd have to buy *another* copy of spss right? the situation is rather annoying in the sense that my university has spss for windows + licenses that i'm allowed to use, but i don't get how i could get hold of the java version without paying for it just as i would without anything at all?

If you purchased a Windows version of SPSS, that means you have to buy a new license, unless you can convince them to trade your Windows license. You can give it a try, who knows?

I don't use SPSS a lot now (I migrated to Stata and R), so I decided to take a look at their website and it seems they changed their product line. It looks like IBM bought the company and decided to make things differently. Will they keep the java platform? If you guys tried the latest version, you could give us some light on that.

---

### Post by oneiric on 2009-11-10
everyone out there looking for an SPSS replacement for Ubuntu ---> just install R statistics

sudo apt-get install rkward

---

### Post by Benic on 2009-11-10
> **oneiric said:**
> everyone out there looking for an SPSS replacement for Ubuntu ---> just install R statistics

sudo apt-get install rkward

Depending on the Ubuntu version you have, installing RKward from the repos can be problematic. From my own experience, with 8.10, 9.04, and 9.10 you should try to compile the [_SVN version_]("http://sourceforge.net/apps/mediawiki/rkward/index.php?title=Download_RKWard") instead.

---

### Post by shaunsmith_99 on 2009-11-10
> **gnuman said:**
> I'm having to use SAS in a statistical programming class--it's required.  Anyway, I have R installed, along with the R commander, both of which are in the synaptic pkg manager.  I do my assignments in SAS, impress the instructor, and then come home to R, which I plan on using long after my "limited lease" on SAS runs out.

R commander is a very friendly GUI, IMHO:

[http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/](http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/)


 Statistical computing is the #1 reasons I still have a Windows Machine as well... = ( Sure, R is good, but SAS and SPSS really have no substitutes.. I'm hoping that PSPP will get there eventually, but it's still very limited on it's abilities... :|:|

---

### Post by Benic on 2009-11-11
> **shaunsmith_99 said:**
> Statistical computing is the #1 reasons I still have a Windows Machine as well... = ( Sure, R is good, but SAS and SPSS really have no substitutes.. I'm hoping that PSPP will get there eventually, but it's still very limited on it's abilities... :|:|

I don't know much about SAS, but I can tell you that now both SPSS (16 and up) and Stata (10) have java-based version that can be installed on a Linux machine. I tried both of them and I had no problem. 

From my own experience and on a very personal basis, I think SPSS is no match for Stata and R, but this is arguable...

---

### Post by Stefus-Refus on 2009-11-13
I have tried
PSPP 
RKWard
RCmdr
and SPSS 16 for Linux

PSPP is almost useless
RKWard and RCmdr are good. I prefer RKWard (do not use the last version it is not compatible with Ubuntu 9.10 from some reason). The R project is has very powerfull and advanced statistics including many features that are not availible in SPSS 16 but it is not good in sorting and manipulating the data.
But SPSS is better . I found an SPSS 16 for Linux version on some torrent. And I am using it now as a main program because is easier to handel the data but for some things I still use RKward which can open spss SAV. files what is great. :D
I also tried JMP and I thing that is the best Stat program but sadly it can not run in Linux.

---

### Post by Benic on 2009-11-16
> **Stefus-Refus said:**
>  I prefer RKWard (do not use the last version it is not compatible with Ubuntu 9.10 from some reason)

If you install it with synaptics, it doesn't work. I compiled the SVN version and it works perfectly with 9.10: you should try. You can download the latest version [_here_]("http://sourceforge.net/projects/rkward/files/Current_Stable_Releases/rkward-0.5.2.tar.gz/download").

---

### Post by knattlhuber on 2009-11-23
> **shaunsmith_99 said:**
> Statistical computing is the #1 reasons I still have a Windows Machine as well... = ( Sure, R is good, but SAS and SPSS really have no substitutes.. I'm hoping that PSPP will get there eventually, but it's still very limited on it's abilities... :|:|

There is a Linux version of SAS. Granted, the SAS program editor of the Linux version sucks big time but you can still run your files through Vim. Not sure in what area you are using SPSS for but in my field (epidemiology/biostats), Stata (which has a Linux version) is head and shoulders above SPSS, especially for clustered data, regression and survival analysis.

---

