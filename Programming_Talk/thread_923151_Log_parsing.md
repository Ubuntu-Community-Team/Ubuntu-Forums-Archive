---
title: "Log parsing"
date: 2008-09-18
forum: Programming Talk
---

### Post by thelamb on 2008-09-18
I would like anyone to share his thoughts with me about log parsing. I have been reading quite a lot about it on the internet but no real satisfactioning answers. The results are stored in a file.

My main goal is performance, here is what Im trying to do:
There are rougly 4000 log files that need to be parsed every day, varying in size from a few kb to a few mb. The logs are from game servers so the size depends on the activity in the particular server. There are about 20 regular expressions that the parser is looking for, most will not be found but there will be many hits for 'new connections' on busy servers.

Before posting my code I would like to hear anyones thoughts about this, like what language is probably fastest for this(I was thinking perl) and are there any techniques you know of that might help. The filestructure for the logs are:
~/logs/game/serverIP_port/date.log
where 'game' is a number representing a game(d'oh) like Soldier of Fortune 2 etc. and 'date' is '20080916'. The parser should run once a day, parsing the logs from the day before.

I'm not asking anyone to code this for me, just share some thoughts with me on the fastest way to do this.

Thanks in advance

---

### Post by ghostdog74 on 2008-09-18
whether its fast or not, depends on how you code your parser and how the data file looks like and how big is the file. Show a sample of those logs, and describe what you expected the output to be.

---

### Post by cb951303 on 2008-09-18
I don't think that speed will be an issue here.
could you send some log samples ?

---

### Post by ghostdog74 on 2008-09-18
> **cb951303 said:**
> I don't think that speed will be an issue here.
could you send some log samples ?
yes it does, when the file size gets bigger and bigger

---

### Post by thelamb on 2008-09-18
I just opened a log file at random, it's size was 13.5 MB and it contains lines like shown below + a lot of useless lines:

```
[09.17.2008 00:15:32] {Plain_Text}|78937| New Connection (slot #5) <IP GOES HERE> [?] UnnamedPlayer (seq 7309194)
[09.17.2008 00:15:33] {Plain_Text}|78938| Player GUID Computed <GUID GOES HERE>(-) (slot #5) <IP GOES HERE> UnnamedPlayer
[09.17.2008 14:24:05] |103556| Kick/Ban Command Issued (Prior Kick/Ban) for (slot#8) <IP GOES HERE> <GUID GOES HERE> UnnamedPlayer
[09.17.2008 14:57:31] |108445| VIOLATION (PB HACK) #132056: UnnamedPlayer (slot #2) Violation (<TYPE goes here>) #132056 [<GUID GOES HERE>(-) <IP GOES HERE>]

```

The parser will parse all lines that contain 'New Connection', 'VIOLATION (' and some more(up to about 20 I think but these are the most common).

The result is the line from the log containing the matched regex, preferable the parser would paste the serverIP before the log line. So if the parser should parse the lines above the result file would contain:

```
123.123.123.123:2222 [09.17.2008 00:15:32] {Plain_Text}|78937| New Connection (slot #5) <IP GOES HERE> [?] UnnamedPlayer (seq 7309194)
123.123.123.123:2222 [09.17.2008 14:57:31] |108445| VIOLATION (PB HACK) #132056: UnnamedPlayer (slot #2) Violation (<TYPE goes here>) #132056 [<GUID GOES HERE>(-) <IP GOES HERE>]
```

But if adding the serverIP infront of every match slows down the parser too much then a different way to 'remember' the serverIP isnt a problem(like 1 result file for every server(e.g. 123-123-123-123-2222.result) isn't a problem).

The 'New connection' search will by far get the most hits, on big server there can be many players connecting daily. The other matches(like violation) are far less common(probably 50 a day from all 4000 logs).

The result file will be processed by a different script.

Thanks for your time

---

### Post by cb951303 on 2008-09-18
> **ghostdog74 said:**
> yes it does, when the file size gets bigger and bigger

nope OP said few MB. for that size it doesn't metter. try it you will see

---

### Post by ghostdog74 on 2008-09-18
> **cb951303 said:**
> nope OP said few MB. for that size it doesn't metter. try it you will see

i know. What if OP want to parse more than 500Mb log? Its better to make code as resilient as possible.

---

### Post by cb951303 on 2008-09-18
> **ghostdog74 said:**
> i know. What if OP want to parse more than 500Mb log? Its better to make code as resilient as possible.

if that's the case he should code it to handle 500 MB
but if he needs only few mb of parsing then there is no need for him to learn a C or C++ just to parse it faster (assuming he doesn't know already). I'm being practical here. The best thing about writing your own code for your own use is that you know where to stop.

---

### Post by ghostdog74 on 2008-09-18
> **thelamb said:**
> 

The parser will parse all lines that contain 'New Connection', 'VIOLATION (' and some more(up to about 20 I think but these are the most common).

The result is the line from the log containing the matched regex, preferable the parser would paste the serverIP before the log line. So if the parser should parse the lines above ...


```

awk 'BEGIN{ gotit=0}
/New Connection/ || /VIOLATION \(/{
 for(i=1;i<=NF;i++){
  if( $i ~ /[0-9]+\.[0-9]+\.[0-9]+\.[0-9]/){
    #if match IP address.
    IP=$i
    gotit=1
  }
 }
}
gotit==1 { print IP,$0; gotit=0}
}' file

```

---

### Post by thelamb on 2008-09-18
I think I was a bit unclear about the serverIP part.
The logfiles are in: ~/logs/game/serverIP_PORT/date.log
e.g. ~/logs/game/1-1-1-1-2222/20080917.log
The serverIP is nowhere in the log file(Any IP found in the logfile is the player's IP). But this is not the most important part of my problem anyway, it is getting the 'New Connection' and 'VIOLATION' lines out of the logs as fast as possible and store them in a different 'results' file.

My guess is that the largest logfile is approximately 15-20 MB. 500 MB will never happen. Though there are around 4000 of these logfiles.

At the moment there is a shell script doing this, it takes about 2 hours for 3600 logfiles(this includes adding everything in a database, I don't have a time for 'just' the parsing, but the parser is taking the most time). I can run a test without the database stuff if you wish.

Now you might ask: "If it's running already, why are you trying to re-do it." the answers are:
 - Educational purposes(I know php, c++ but as far as I know these are not the fastest languages to be doing this kind of parsing in - or am I wrong?)
 - scalability(any performance gain is welcome, personally I feel that 2 hours is too long for this, noting that there are new servers added every day.)

---

### Post by ghostdog74 on 2008-09-18
> **thelamb said:**
>  But this is not the most important part of my problem anyway, it is getting the 'New Connection' and 'VIOLATION' lines out of the logs as fast as possible and store them in a different 'results' file.

you can try egrep
```

 egrep "New Connection|VIOLATION \(" file > new_results_file

```

---

### Post by thelamb on 2008-09-18
Yes, that is possible. But my question is if anyone has an idea what the fastest way of doing this is. The current script that does this job is using egrep.

---

### Post by ghostdog74 on 2008-09-18
> **thelamb said:**
> Yes, that is possible. But my question is if anyone has an idea what the fastest way of doing this is. The current script that does this job is using egrep.
you can show a sample of your script ( the part that you think is slow ). If its slow, then its the way its coded and the choice of tools used.

---

### Post by pp. on 2008-09-18
I would suggest to review the specifications of the problem. 

You formulate the problem as if the strings to be matched could occur anywhere within a line at all. Yet the examples you give suggest that the line layout conforms to either of two patterns (date/time, possibly followed by '{plain_text}', followed by a number between two pipe characters), and that the strings to be searched for ought to occur right after the second 'pipe' character ('|').

The solutions suggested so far in this thread can be relied on to scan each line quite efficiently. Not knowing the suggested utilities, I do not know how many times each line is scanned for a list of twenty possible patterns to detect.

However, depending on the syntax of the individual lines and on the strings to look for, it might suffice to look at a smallish part of each line only instead of looking several times over at all of each line. There might be a gain in performance.

---

### Post by pmasiar on 2008-09-18
> **thelamb said:**
> My main goal is performance,... what language is probably fastest for this(I was thinking perl) and are there any techniques you know of that might help. 

Perl was used for years, but now, Python is better choice. [Generator Tricks for Systems Programmers](http://www.dabeaz.com/generators/) shows tricks how simplify parsing logs using generators (to avoid reading whole log into memory while keeping the flexibility). See wiki in my sig for links

---

### Post by Calmatory on 2008-09-18
As I understood, you do not archive the old results and parse only the new log files. Instead, you always parse the same log files over and over again, day after day.

Parse all files modified since last parse
Store the obtained data in database/file/archive
store the modification date and time of all of the files

This way you do not parse the old files again and again.

---

### Post by thelamb on 2008-09-18
No, I don't actually re-parse old files. 
The format of the logs are:
date.log (e.g. 20080918.log).

The parser will run tonight(after 00:00, so on date 20080919) and it will only parse logs that are named 20080918.log).

Today( 20080918 ), the parser was running for the 20080917.log files.

So every log file(regardless of the serverIP or game) has the same name, which is the date.

@pmasiar
I'll have a look at that link tomorrow, thanks!

---

### Post by Reiger on 2008-09-18
For efficiency I would try to start up x threads each executing exactly the same code but with slighlty different input (you got it: a commandline parameter).

Then based on x it selects the filename and outputs a file with certain name. That should on any decent modern server yield the performance gain of concurrency; the parser can run multiple threads quite independent of each other; heck -- they operate on & output entirely different files...

So whatever language you choose try to find something that can be mutltithreaded (benefit of sharing code across multiple threads, on top of concurrency, thus removing quite a bit of 'startup' time and in case of optimizing JIT compilers resulting in more heavily optimised code).

---

### Post by ghostdog74 on 2008-09-18
> **pmasiar said:**
> Perl was used for years, but now, Python is better choice. [Generator Tricks for Systems Programmers](http://www.dabeaz.com/generators/) shows tricks how simplify parsing logs using generators (to avoid reading whole log into memory while keeping the flexibility). See wiki in my sig for links

If your argument on "Python is better choice" than Perl for parsing is based on whether it has iterators/generators, then its not very concrete because AFAIK, [Iterators/generators](http://hop.perl.plover.com/#free) can be implemented in Perl. I am sure there are Perl iterator modules as well.  When parsing files, normally the method is iterate each line. If the file is small then it can be put into memory as the OP sees fit. However, normal way is still to go over line by line. In this case, any parsing tools can be used. The trick now is how the parser is coded (algorithm wise). example, if using Python, whether its using alot of regexp using re,(whether its compiled) or using Python's inbuilt string manipulaton,  or if using shell, whether its piping too much eg egrep <blah> | egrep <blah> |sed <blah>....etc.

---

### Post by pmasiar on 2008-09-19
> **ghostdog74 said:**
> When parsing files, normally the method is iterate each line. If the file is small then it can be put into memory as the OP sees fit. However, normal way is still to go over line by line. 

Article about Python generators linked above explains limits and lack of flexibility of "iterating line by line" approach, which I also assumed 'the standard'. Read it. 

Even if Perl can implement generators, they will be hacked on top of the language, like OOP is. Even if it work, it looks like ugly hack, exactly what it is.

---

### Post by ghostdog74 on 2008-09-19
> **pmasiar said:**
> Article about Python generators linked above explains limits and lack of flexibility of "iterating line by line" approach, which I also assumed 'the standard'. Read it. 

Even if Perl can implement generators, they will be hacked on top of the language, like OOP is. Even if it work, it looks like ugly hack, exactly what it is.

unless you can come up with proof that using Python generators can indeed speed up file parsing when compared to other languages/tools and methods, like actually parsing OP's very big file and taking timings, otherwise, I would still say, don't jump to conclusion.

---

### Post by pmasiar on 2008-09-19
> **ghostdog74 said:**
> unless you can come up with proof that using Python generators can indeed speed up file parsing when compared to other languages/tools and methods, like actually parsing OP's very big file and taking timings, otherwise, I would still say, don't jump to conclusion.

It's not about speeding the parsing: it is about speeding the development of the parsing code, and making it more flexible. You still did not read the link, did you? 8-)

---

### Post by ghostdog74 on 2008-09-19
> **pmasiar said:**
> It's not about speeding the parsing: it is about speeding the development of the parsing code, and making it more flexible. You still did not read the link, did you? 8-)

i want to refer you to [this](http://ubuntuforums.org/showpost.php?p=5813633&postcount=15). OP has a performance concern and he is referring to speed of parsing, not the speed of development. You quoted OP and suggest Python generators. I had assumed you are suggesting Python generators as a fast way of file parsing since then.

---

### Post by pmasiar on 2008-09-19
If OP considers Perl, he is obviously not concerned about the execution speed, right? Python's generators are comparable in execution speed with Perl (I don't have number, but I would not expect generators be order of magnitude slower - should be fast enough), so I am not sure where the execution speed requirement came from - certainly not from OP, AFAICT. 

Maybe we should wait for OP to chime in, so we have better input info to base our advice?

---

### Post by pp. on 2008-09-19
> **pmasiar said:**
> ... I am not sure where the execution speed requirement came from - certainly not from OP, AFAICT. 

Maybe we should wait for OP to chime in, so we have better input info to base our advice?

Parts of the OP:

> **thelamb said:**
> ...

My main goal is performance, here is what Im trying to do: ...  I would like to hear anyones thoughts about this, like what language is probably fastest for this(I was thinking perl) and are there any techniques you know of that might help.

---

### Post by slavik on 2008-09-19
actually, even reading line by line is not bad, because even C does buffered input from files (you can adjust the buffer size) ...

---

