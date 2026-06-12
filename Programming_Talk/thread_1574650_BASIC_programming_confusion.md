---
title: "BASIC programming confusion"
date: 2010-09-14
forum: Programming Talk
---

### Post by mrgreaper on 2010-09-14
ok a few months ago i started writing a program for me and my dnd friends (yes im a geek) back then both my desktop and my netbook were running windows 7. i was advised to use ubuntu remix on the netbook to improve boot times battery usuage etc and i did just that. well my project was on hold till today when i tried to restart it... on windows i used justbasic (its a the only free version i could find and seems to work great) sadly theres no linux version so i had a look online and found two options freebasic and gambas. freebasic was awkward to install and i havent figured out howto load it with out first loading terminal. gambas seems more friendly but theres a snag

in justbasic you define tables that you can link to in the programe for example...

```
[table101]

    input "to decide your race roll a d20 or hit enter for random  :"; roll

    if roll = 0 then let roll = int(rnd(1)*20) + 1 ' its impossible to roll a 0 so a 0 would mean the return key has been presed with out any data

    if roll = 1 then let race$ = "Human"

    if roll = 2 then let race$ = "Human"

    if roll = 3 then let race$ = "Human"

    if roll = 4 then let race$ = "Human"

    if roll = 5 then let race$ = "Human"

    if roll = 6 then let race$ = "Human"

    if roll = 7 then let race$ = "Human"

    if roll = 8 then let race$ = "Human"

    if roll = 9 then let race$ = "Human"

    if roll = 10 then let race$ = "Human"

    if roll = 11 then let race$ = "Human"

    if roll = 12 then let race$ = "Human"

    if roll = 13 then let race$ = "Human"

    if roll = 14 then let race$ = "Human"

    if roll = 15 then let race$ = "Elf"

    if roll = 16 then let race$ = "Elf"

    if roll = 17 then let race$ = "Dwarf"

    if roll = 18 then let race$ = "Halfling"

    if roll = 19 then let race$ = "Half-Elf"

    if roll = 20 then gosub [raceextra]


```

here a roll of 20 would send you to [raceextra] table

(my code got a little more refined as i went along but not much lol)

however gambas stps at the very first table title anouncing an unexpected "[" ...it wasnt unexpected.. i put it there.

so either gambas or justbasic isnt being fair and using code thats not really basic. im guessing this means i need to start from scratch ...a scary scary task but then i want to change some things anyway.


before i ask the questions let me exlain what the program im building is planed to do,
allow the player to randomly generate a past for their charecter wither by dice roll or pure random, 
each table is used to create it for example it may say you get a pet and it would tell you the colour and special effects of that pet (tables inside tables)

now instead of having lots of lists it would be nice if i could use csv files (makes it easier for tweaking the names etc and ofcourse i could have a set of csv`s for one world and another set for another world. but i would have to be able to get a value from one csv and add it to another for example, get the player to roll for an item then get the player to roll for a colour and combine the two say the player rolled a 5 for item and a 2 for colour (the resualt returned would be "A colour 2 item 5" "A Blood Red ShortSword") 

sorry im bad at explaing things and doing my best 

in the end the whole thing would be dumped as a text file to be printed off and used as a character sheet

so my questions or more importantly my reason for posting here

its clear im gonna have to start again and that one basic is not the same as another, im open to using another language (someone on a forum advised a basic user to use perl as aparently its similier another post on another forum (i have done a hell of a lot of google before posting) said to use java and yet another said python all of which are alien languages to me but python sounds the most useful as i would be able to host it as a webpage on my server pc so it wouldnt matter what we used at the group ...linux ...windows..mac ... a web page is a web page (my server pc has apache webserver on it) 

so what language would you suggest and how would i go about using csv in that language? and what program do you advise i get to program in

i know its a big wall of text and such a small question so i would like to thank you for reading and in advance for your replies....oh the program MUST be free please dont recommand me a paid for program and please as noob friendly as possible.

---

### Post by Strategist01 on 2010-09-14
Hi there.

I would highly recommend Java. I am not too sure how it would handle CSVs, but it does have quite a bit of database functionality. An IDE for Java would be the Eclipse IDE, which you can visit by going to [www.eclipse.com](www.eclipse.com) and selecting the top package for Linux, should be around 200 MBs.

Hope that helps in some way?

---

### Post by mrgreaper on 2010-09-14
> **Strategist01 said:**
> Hi there.

I would highly recommend Java. I am not too sure how it would handle CSVs, but it does have quite a bit of database functionality. An IDE for Java would be the Eclipse IDE, which you can visit by going to [www.eclipse.com](www.eclipse.com) and selecting the top package for Linux, should be around 200 MBs.

Hope that helps in some way?

i shall keep that one under advisement thank you, gonna wait for a few more suggestions before i take a plunge (i would download and try it now but 200megs is a bit big for when ure at work (im a night guard so plenty of time to programme) )

---

### Post by GenBattle on 2010-09-14
Indeed you have come to the fundamental problem with language portability. In the end everyone has their own idea of what is best for the language, so porting code is usually very horrible.

Personally i would recommend python for something like this. It would be relatively easy for a basic programmer to pick up (no semicolons at the end of lines, don't have to use OOP style programming) compared to something like java. It runs on both linux and windows, with nearly identical code for both platforms (system-specific stuff is all that changes). I also reccomend it because it has an interactive command-line interpreter so you can type code in and run it line by line, evolving the program as you go, rather than having to type everything in and hope it runs. Also, it's much smaller than Java+Eclipse, or even Java by itself.

I think overall you'll only get recommendations for other languages from people in this forum. We don't get many BASIC programmers here, and people generally shun it as a language because of its lack of proper programming structures and functionality.

python website: [http://python.org/](http://python.org/)

P.S. If you install python under ubuntu (from the repositories), make sure to also get IDLE or another python development program (otherwise you will have to run stuff from the command line).

---

### Post by dv3500ea on 2010-09-14
I recommend [ruby]("http://www.ruby-lang.org/"). There is a program called [shoes]("http://shoes.heroku.com/") that allows you to create graphical programs using ruby. Shoes is available to download for Linux, Max OSX or Windows. Shoes is bundled as a single file, making it easier to distribute.

Ruby comes with CSV support as part of its standard library.
This example shows how to convert a csv string to/from a ruby array of arrays:
```

require 'csv'

*[color=#AAA]#csv to ruby[/color]*
arr = CSV.parse("1,2,3\na,b,c")
*[color=#AAA]#arr == [[1, 2, 3], ["a", "b", "c"]][/color]*

*[color=#AAA]#ruby to csv[/color]*
str = (arr.map do |row|
    CSV.generate_line(row)
end).join "\n"
*[color=#AAA]#str == "1,2,3\na,b,c"[/color]*

```

You can also use ruby on a server if you want. This could be done in Apache via the 'libapache2-mod-ruby' package.

---

### Post by s.fox on 2010-09-14
Hello,

I would recommend Python also.  I personally have found it one of the easier languages to "pick up" .  It is multiplatform also,  so portability should not be much of an issue.  If you intend to start learning the language I would recommend [A Byte of Python]("http://www.ibiblio.org/g2swap/byteofpython/files/120/byteofpython_120.pdf").  I found it a nice starting block when I first started learning the language.

Aside:  dnd player here also, never written an application to generate character sheets,  sounds like a good idea to me :)

-Silver Fox

---

### Post by steevk on 2010-09-14
> **dv3500ea said:**
> I recommend [ruby]("http://www.ruby-lang.org/"). There is a program called [shoes]("http://shoes.heroku.com/") that allows you to create graphical programs using ruby. Shoes is available to download for Linux, Max OSX or Windows. Shoes is bundled as a single file, making it easier to distribute.

Hey, just wanted to say thanks for mentioning Shoes. I'm one of the maintainers, if anyone has any issues/problems/questions, just ask!

---

### Post by raydeen on 2010-09-15
+1 for Python. I use it on my job to generate .CSV files for creating dozens or hundreds of new users for our Google Groups. As long as I get a spreadsheet of the usernames (and in some cases pre-chosen passwords) I can copy and paste the needed info into a plain text file and then have the Python script parse it and spit out a .csv file that Google can read to create the accounts. I've got a basic to intermediate grasp of Python and I think it originally took me about 45 minutes to get the first working version of the script. I've modified and customized it over the last few months (and still have some work to do to make it a bit more 'Pythonic') but it's been dead simple to implement and maintain. No GUI, but it really doesn't need one. Eventually, I'd like to add a very simple GUI, just two fields for input file, output file, and maybe GO and QUIT buttons. As it is now, I just load the script up in the IDLE IDE (included with Python or easily installed if not) and check the results from there. Once it looks good, I upload the .csv. Plus, I can run it in Windows, OSX or Linux. That's actually been a blessing as I found that initially it ran great in Windows but in OSX and Linux, an extra carriage return was carrying over into the output file. It didn't appear in OSX when I ran it, but showed up in Linux. (\r). I couldn't figure out why it kept newline-ing when I knew I'd told it to strip out any \n. :D

---

