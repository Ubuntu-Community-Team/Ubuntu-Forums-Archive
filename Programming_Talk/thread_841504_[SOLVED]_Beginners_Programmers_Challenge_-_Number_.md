---
title: "[SOLVED] Beginners Programmers Challenge - Number 1"
date: 2008-06-26
forum: Programming Talk
---

### Post by Tony Flury on 2008-06-26
As suggested in another thread - this is the first challenge specifically designed to help Beginners progress in their chosen language.

**_Beginners Goals_**
The aim of this challenge is to exercise the following basic features of the competitors chosen language : 
1) Handle simple command line arguments
2) Open and close text files
3) Read and write structured output
4) Basic data handling 
5) A simple sort algorithm

It may also provide lessons in how (and maybe how not to) unambiguously describe the functionality of a program, and the benefits of having the test data set available as the program is designed and developed - this is commonly called test driven design.

**_Entry Rules_**
This challenge is intended for beginners - although more experienced developers are welcome to watch this thread, and contibute hints and tips if requested, it would be appreciated if they would refrain from posting solutions, at least until beginners have had a chance. Clearly the definition of beginner is subjective, but i would suggest that you if you think that challenge is easy, then that probably means you are not a beginner.

_Submissions - what to include_
If you want to submit an entry please make sure you include the following 
1) your source code - as an attachment
2) your compilation/build instructions
3) your execute instructions
4) the output of the specified proving run (as an attachment) - see below for details of the proving run. 

_**Program specification**_
Implement an application in whatever chosen language which implments the following functionality

1) Input data called the Table file (see below for a spec for this file). This Table represents the current standings of a Football league, (Soccer for our North American friends). The table records the team name, games played, home and away match information, overall goal difference and league points.
This input file should be able to be specified by the User as the first command line argument.

2) Input data called the results file (see below for a spec for this file). This file represents the results of a series of football matches in the league. The file records the Name of the Home and Away teams, and the Respective scores.
This input file should be able to be specified by the User as the second command line argument.

3) The data in the results file should be applied to the League table, and an updated League Table should be produced in the same format as the input data (so it can be used as input into a subsequent run of the application). The revised table should be output to the user Console (stdout in C terms). The league table should be output in league order (see below for a definition of these ordering rules).

_Table file_
This file describes the current standings of the Soccer league the format is as follows :
```

<name>[tab]<played>[tab]<home form>[tab]<away form>[tab]<Goal difference>[tab]<Points>[nl]

[tab] : A tab character 
[nl] : End of line
<name> : A team name - a sequence of Ascii characters, with no leading spcaes.
<played> : An positive integer giving the number of games played
<home form> : A formatted sequence showing the teams home record (see below)
<away form> : A formatted sequence showing the teams away record (see below)
<Goal difference> : An signed integer showing the difference between the total goals scored For and Against the team totalled across all Home and Away matches.
<Points> : the Total points gained across all games played - 3 points for a win, 1 for a draw, 0 for a loss.

<home form> & <away form>
These sections follow the same formats as follows 
<won>[space]<drawn>[space]<lost>[space]<Goals For>[space]<Goals Against>

where : 
[space] is a single space character
<won> : Number of games won - either Home or away - depending on section.
<drawn> : Number of games drawn - either Home or away - depending on section.
<lost> : Number of games lost - either Home or away - depending on section.
<Goals For> : Number of Goals scored by the team - - either Home or away - depending on section.
<Goals Against> : Number of Goals conceeded by the team - either Home or away - depending on section.

```
The application can assume that the Table File is complete, and correct. The application does not need to do any consistency checking on the table file.

_Results File_
The Results file has the following format :
```

<Home Team>[tab]<Home Score>[space]<Away Score>[tab]<Away Team>

<Home Team> : A team name as seen in the Table file - the Home team for this game
<Away Team> : A team name as seen in the Table file - the Away team for this game
<Home Score> : The number of goals scored by the Home team in this match
<Away Team> : The number of goals scored by the Away team in this match

```
There should be no restriction as to the nunber of results recorded in the Results file, or how many times an individual team should appear. It is not expected that the application will do any sort of validation to detect duplicated matches.

_League Ordering_
As mentioned the output of the updated League Table should be in league order - this is defined as follows (for the purposes of this challenge).

1) Teams are ordered by Points gained - in descending order.
2) if two or more teams have the same number of Points, then those teams are ordered by Goal Difference - in descending order.
3) if two or more teams have the same number of Points and the same Goal difference - then those teams are ordered by name in alphabetic order - earliest first.

_Example input files_
In order to allow entrants to test their application against a known good input file set the following files are provided : 

table1.txt is the initial state of the league with no matches played.
results1.txt, results2,txt, results3,txt are results files giving the results of 3 matches for each team in total.
Your submission should include the League table (after all 3 matches per team) - obtained by applying each of these result files to the initial table and (of course) updating the league table after each result file is processed :
if your executable is called apply - and example run sequence might be : 
```

./apply table1.txt results1.txt > table2.txt
./apply table2.txt results2.txt > table3.txt
./apply table3.txt results3.txt > table4.txt

```
you need to remember to attach table4.txt (in the above example) to your submission.

**_That's it - go for it_**
That is all i can think to say about the challenge - good luck. I would expect that a beginner programmer may take up to a week or two to nail this one - but who knows who may suprise us.

---

### Post by Tony Flury on 2008-06-27
Is this one far too tough ? I am surpised (a bit) by the lack of questions, comments etc - or should i not be ?:confused:

---

### Post by bobbocanfly on 2008-06-27
Seems pretty complex, especially for a beginner....

---

### Post by Wybiral on 2008-06-27
> **bobbocanfly said:**
> Seems pretty complex, especially for a beginner....

Yes, not hard... But a lot of little arbitrary rules piled up.

---

### Post by WitchCraft on 2008-06-27
No, it shouldn't be too difficult. The command line arguments you get with argc and argv and you find plenty of examples on the web, and you can just copy paste the quicksort or bubblesort algorithm, or of course more sophisticated versions... Filehandling isn't difficult, there are lots of examples out, too.

---

### Post by Tony Flury on 2008-06-27
I did not intend to make it that complicated. It is a pretty similar to the first project i was given at uni in the first year after only a few weeks of lectures - and that was lots of dry lecture, and no chance to do any "Hello worlds" etc or anything like that.

Apologies though if people think it is too complicated.

My advice to anyone considering entering is try to do it in steps for instance :
[LIST=1]
[*]Handle command line arguments
[*]Open and close the files
[*]Read the League table file and store it
[*]Output the league table
[*]read the Results file
[*]Process the contents of the results onto the stored league
[*]sort the league
[/LIST]

That would be the order i would do it in ... the only potentially complex thing in there is the sort - and as someone pointed out there are plenty of published simple sort algorithms (bubble sort is fine).

---

### Post by nick_h on 2008-06-27
> Is this one far too tough ?
No, I think it is about right for beginners.

Anyone attempting the challenge could always skip bits to start with.  They could hardcode the filenames to start with, for example, and then work out the command line later.

I would also suggest using a library sort function rather than writing one.  (Is this within the rules?)

---

### Post by nvteighen on 2008-06-27
Ouch! I'm going for a trip for a week... and I'm pretty obsessed with a little personal exercise on data structures (if you're curious: trying to implement multi-branched trees in C...). I would do this, if I could, only because of the sorting algorithm, actually.

What I suggest is to create challenges be more focused on one specific goal. This one in its current fashion has two: 1) parsing a text given a "standard" and conform to it. 2) sorting algorithm.

Of course, if you tell people to sort nine numbers from some input; competitors would be able to choose whether grab data from user input or file or implementing a random generator, whatever they know/want to do.

I don't know if I've been clear enough.

---

### Post by thornmastr on 2008-06-27
I'm looking at this from a different perspective. I'm retired. Moving into the relative freedom of Linux from Windows is a taste both of freedom and of challenge. I am now, finally, able to concentrate on puzzles, contests, and learning. So yes, I am definitely going to do this challenge. It is, in fact, number two on my list. Hopefully I will finish with my current puzzle/challenge over the weekend and I can begin this Monday afternoon. 

It is not overly difficult. What it does demand, and what is a serious challenge not only to beginners but professionals as well, is the requirement of careful planning. If the expectation is to read it, start programming, and be done in two hours, I don't think it's going to work out very well. What I intend to do is write out a plan to solve the problem; sketch the solution in pseudo code, and then begin to code the solution in easily manageable blocks which hopefully will be easy to test and evolve toward a viable solution.

Thanks for an interesting but not discouraging challenge.

---

### Post by Tony Flury on 2008-06-27
> **nick_h said:**
> No, I think it is about right for beginners.

I would also suggest using a library sort function rather than writing one.  (Is this within the rules?)

Good question - Nothing in the rules that I wrote prevent the use of a library sorts, it is after all part of the functionality of the chosen language/library/platform etc - just as i expect people to use libraries of some form (especially in C for instance) to read the files etc (i doubt anyone is going to read the binary data off the disk and reconstruct the data for instance). The idea of the challenge is to get people thinking about the best way to utilize the language - and libraries are part of that.

---

### Post by myrtle1908 on 2008-06-27
I've pretty much got it done with Perl.  Will post soon.

---

### Post by myrtle1908 on 2008-06-27
Well here's my stab at it.

Perl was obviously the job for this.  I'm not really a "beginner programmer" but I haven't touched Perl for many many years so I figured it would be ok and would prove a good exercise with a view to brushing up on my Perl munging skills :)

I would welcome any comments from Perl gurus and experienced programmers alike regarding flaws, bad practices etc.

1) Source is attached as 'ladder.pl.txt' and should be renamed to 'ladder.pl'  (120 lines approx).

2) No build/compile required.

3) Execute:-

./ladder.pl table1.txt results1.txt > table2.txt
./ladder.pl table2.txt results2.txt > table3.txt
./ladder.pl table3.txt results3.txt > table4.txt

4) Sample output:-
[PHP]
Barker City     3       2 0 0 4 1       0 1 0 0 0       3       7
Candy Town      3       1 0 0 1 0       1 1 0 3 2       2       7
Dudd Port       3       1 0 0 1 0       1 0 1 2 2       1       6
Elephant Rovers 3       1 0 1 4 4       0 0 1 1 2       -1      3
Anytown Utd     3       0 2 0 1 1       0 0 1 0 1       -1      2
Foxtrot County  3       0 0 1 1 2       0 0 2 2 5       -4      0
[/PHP]

---

### Post by Tony Flury on 2008-06-28
> **myrtle1908 said:**
> Well here's my stab at it.

... 

4) Sample output:-
[PHP]
Barker City     3       2 0 0 4 1       0 1 0 0 0       3       7
Candy Town      3       1 0 0 1 0       1 1 0 3 2       2       7
Dudd Port       3       1 0 0 1 0       1 0 1 2 2       1       6
Elephant Rovers 3       1 0 1 4 4       0 0 1 1 2       -1      3
Anytown Utd     3       0 2 0 1 1       0 0 1 0 1       -1      2
Foxtrot County  3       0 0 1 1 2       0 0 2 2 5       -4      0
[/PHP]

Wow :)

I sort of expected a scripting result to win - but to be honest I was not expecting a result this quickly.

Well done myrtle - a simple diff between your output and my text output shows that you did complete the challenge. 

I will leave it to others to comment on your perl should they wish to - i am no perl expert.

To everyone else - even though Myrtle has won the challenge - don't let that stop you placing your entrance. The challenges is still there for to complete.

Well done again Myrtle :-)


right - who is going to post the next beginners challenge ?

---

### Post by Sinkingships7 on 2008-06-28
Hmm... perhaps a bit more studying is in order before I attempt something like this.

---

### Post by myrtle1908 on 2008-06-28
Thanks Tony.  I too urge others to still post their solutions.  I enjoy seeing how others attack problems especially in languages I am not familiar with eg. Python.

---

### Post by Tony Flury on 2008-07-08
Only had one solution posted so far - so i think we can safely assume this one is closed, and no-one else wants to post anything.

Fair does - now - who want to come up with the next challenge ?

---

