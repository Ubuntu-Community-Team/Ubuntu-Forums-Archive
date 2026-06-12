---
title: "Why I love/hate Perl"
date: 2007-10-16
forum: Programming Talk
---

### Post by slavik on 2007-10-16
pmasiar has one on Python, I will have one on Perl (any Ruby addicts here?)

One of the things that people complain about is Perl being unreadable. Why it can be true, it depends on the coder's habits and mindset.

Perl is as unreadable as a terminal is unusable. Think about how you learned about various simple commands (ls, cd, man, grep, awk ...), you either read it somewhere or someone told you or you transfer some knowledge you had from somewhere else (in which case #1 or #2 probably happened).

Here is an example of taking readable Perl code and making it unreadable:
```

open $file, "/etc/passwd" or die$!;
while ($line = <$file>) { #read in a line from $file and store it in $line
  @record = split /:/, $line #split every line on colons and put it into record(note the array sigil)
  print "user: ";
  print $record[0]; #print the username
  print "\t\thome directory: ";
  print $record[5]; #print the home directory
  print "\n";
}
close $file;

```

Readable, no?

Here's the "unreadable" kind :)

```

open $passwd, "/etc/passwd";
%_ = map { /^(.*?):(?:.*)+:(.*?):.*?$/gis } <$passwd>;
map { print "user: $_\t\t\thome directory: $_{$_}\n" } keys %users;
close $passwd;

```

Now to explain it:
Since Perl and Python can be used for functional programming (ie: Scheme, Haskel type), they have a map function which takes a block of code and applies it to a list (to every item in the list). Map sets the $_ variable to the item it is applying the block to.

Map takes the regular expression and applies it to every line in the file (<> fetches a line from an input/file stream), then map takes the regex and applies it to the line.

The Regex (pre syntax got their start in awk):
^ means beginning of the line
$ means the end of the line
stuff surrounded by parenthesis is to be grouped/extracted, when it is extracted, the first item gets put into $1, second into $2, and so on until $9 (perl can't hande more than 9 matches which is a limitation which I haven't met yet in practice), ?: in the beginning of parenthesis tells perl to not extract this grouping.
period/dot by itself means any printable character
* means 0 or more of the character
? means to not be greedy when matching (grab as few as possible)
+ means 1 or more of the character (a+ is same as aa*)

the matching operation is
STRING =~ m/PATTERN/FLAGS;

but when you leave out the STRING (which can be a variable), it is assumed by perl that you mean $_ (which is what map sets on every iteration). Map returns the list value of every "run" (unless you force scalar context)

When the regex matches the line, the first stuff before the colon gets put into $1 (the username) and $2 becomes the home directory.

at the end of map, it returns a list composed of of the $1 and $2 ($1,$2,$1,$2, ...), a hash in Perl is just a key,value,key,value list (array). So perl maps the list returned by map onto a hash.

next map simply prints the key and the hash value at that key for all keys in the hash :)

an example of how map can substitute a loop:

C-like Perl array iteration
```

@array = (1,2,3,4,5,6,7,8,9);
for ($i = 0; $i <= $#array; $i++) { ### $#array is the index of the last set element in @array (8 in this case)
  print $array[$i] . "\n";
}
```

Perl iteration
```

@array = (1,2,3,4,5,6,7,8,9);
for (@array) {
  print $_ . "\n";
}

```

single line version of the above
```

@array = (1,2,3,4,5,6,7,8,9);
print $_ . "\n" for(@array);
}
```

the map version
```

@array = (1,2,3,4,5,6,7,8,9);
map { print $_ . "\n" } @array;

```

NOTE: @array is explicitly declared for clarity purposes

NOTE2: when you are matching only 1 thing in a string to be used somewhere, usually you would use ```
$item = $1 if ($input =~ /PATTERN/);
``` which is clearer than doing the "proper" if block.

---

### Post by scruff on 2007-10-16
I love Perl for smaller applications. I use it almost every day at work and it does a lot of things well. It was also my first language so it tends to be the one I am most comfortable with.

I don't like it for large applications however, it just gets too messy. I do a lot of UPnP programming at work and on a few occasions I have had to write some large and complicated test automation tools. I used Perl because I have a decent UPnP module, but now I hate maintaining the whole thing.

I had to learn C# at one point and used it to write a fairly large test suite for a particular service using XMLRPC and it is very neat and easy to modify. That was my first foray into true OOP. As a result, I have moved on to C++ and Python for the bigger stuff. Perl's OO implementation is kind of a hack IMHO.

---

### Post by LaRoza on 2007-10-16
I wish I new Perl better, but I see no reason to learn it for anything other than the experience (I like to learn). I also have the same feeling on Ruby...

---

### Post by slavik on 2007-10-16
> **scruff said:**
> I love Perl for smaller applications. I use it almost every day at work and it does a lot of things well. It was also my first language so it tends to be the one I am most comfortable with.

I don't like it for large applications however, it just gets too messy. I do a lot of UPnP programming at work and on a few occasions I have had to write some large and complicated test automation tools. I used Perl because I have a decent UPnP module, but now I hate maintaining the whole thing.

I had to learn C# at one point and used it to write a fairly large test suite for a particular service using XMLRPC and it is very neat and easy to modify. That was my first foray into true OOP. As a result, I have moved on to C++ and Python for the bigger stuff. Perl's OO implementation is kind of a hack IMHO.
Perl OO IS a hack, without any IMHOs ... everyone knows that. Although Perl6 is supposed to address this and follow Python in the everything is an object mentality.

One of the reasons I like Perl is that it also has ways to cut down on the amount of code you need to write (like using a regex on a file and then sticking the whole thing into a hash).

---

### Post by scruff on 2007-10-16
Well that would be nice. I haven't looked into whats coming up in Perl 6. Off to do that now :)

---

### Post by ankursethi on 2007-10-17
I learnt Perl once. Even wrote a simple script that took several pictures from a directory and built a kind of album out of them. That was in January 2007. Now I remember nothing of it.

I'd really like to learn Perl because it's nice the way you can make your programs really short and succint. But the language itself makes it harder for me to really get into the depth of it and learn it "inside out" like you can learn a language like C.

Someday, I'll get a real book and get down to learning Perl. I've had my eyes on Perl 6, but I doubt it will ever be released.

---

### Post by slavik on 2007-10-17
get the source to perl, then you will know how Perl works ;)

as for script to make album, remember the algorithm ...

```

get a list of files
foreach $i (file) {
  generate a page for file[$i](write out HTML code or whatever)
  if ($i != $#file_list) {
    create a link to next file
  }
}

```

---

### Post by KCPokes on 2007-10-17
The beauty of Perl, without getting into which language is better (Perl verus Python versus Ruby, etc...), is that it is a standard package on default installs of all major OSes.  As much as one might love Python and Ruby, in a standard enterprise environment, without gaining an exception, you will not find Ruby and/or Python installed by default, whereas you will find Perl.  I love Linux and have tried a vast majority of the distros, but sadly Linux is still not the defacto standard operating system for major eCommerce applications for major companies.  This is not to say you will not find some that are running it as their standard, but working for a Fortune 500 company I can say that we are still more of a Sun or IBM shop then we are RHEL or any other Linux distro.  

I've written some bigger applications in Perl but without good session management builtin it becomes rather tedious.  Its great for manipulation and quick and dirty scripts, without a doubt.

---

### Post by mjwood0 on 2007-10-17
> **KCPokes said:**
> The beauty of Perl, without getting into which language is better (Perl verus Python versus Ruby, etc...), is that it is a standard package on default installs of all major OSes.  As much as one might love Python and Ruby, in a standard enterprise environment, without gaining an exception, you will not find Ruby and/or Python installed by default, whereas you will find Perl.  I love Linux and have tried a vast majority of the distros, but sadly Linux is still not the defacto standard operating system for major eCommerce applications for major companies.  This is not to say you will not find some that are running it as their standard, but working for a Fortune 500 company I can say that we are still more of a Sun or IBM shop then we are RHEL or any other Linux distro.  

I've written some bigger applications in Perl but without good session management builtin it becomes rather tedious.  Its great for manipulation and quick and dirty scripts, without a doubt.

A very good argument.  I've tried Perl.  I've tried Python.  Python is easier to write for me as a beginner, but Perl is more available.  Really want to understand them both but my time is limited.

---

### Post by loell on 2007-10-17
i love Perl because its opengl bindings is as fast as C , I hate it because after purchasing three books a couple of years ago from **begginer** ,**Reference**, **Advance** . I'm still having difficulty reading individual perls scripts. so when i found python, i just settled with it.

---

### Post by mjwood0 on 2007-10-17
> **loell said:**
> i love Perl because its opengl bindings is as fast as C , I hate it because after purchasing three books a couple of years ago from **begginer** ,**Reference**, **Advance** . I'm still having difficulty reading individual perls scripts. so when i found python, i just settled with it.

Might as well just use C for OpenGL then.

---

### Post by scruff on 2007-10-17
> **KCPokes said:**
> The beauty of Perl, without getting into which language is better (Perl verus Python versus Ruby, etc...), is that it is a standard package on default installs of all major OSes.  As much as one might love Python and Ruby, in a standard enterprise environment, without gaining an exception, you will not find Ruby and/or Python installed by default, whereas you will find Perl.  I love Linux and have tried a vast majority of the distros, but sadly Linux is still not the defacto standard operating system for major eCommerce applications for major companies.  This is not to say you will not find some that are running it as their standard, but working for a Fortune 500 company I can say that we are still more of a Sun or IBM shop then we are RHEL or any other Linux distro.  

I'm not sure I understand this statement. You will not find an OS that has Perl installed by default and not python. That is because the only OS's that include either are Linux and Unix-like OS's including OSX and all of those include both.

Windows includes neither by default...

---

### Post by loell on 2007-10-17
nah, perl opengl  (POGL) , would still have an edge if the program will have objects , i would rather have to deal with  hashes,  scalars and objects  , than a friggin pointer :p

---

### Post by scruff on 2007-10-17
> **loell said:**
> nah, perl opengl  (POGL) , would still have an edge if the program will have objects , i would rather have to deal with  hashes,  scalars and objects  , than a friggin pointer :p

You deal with references, don't you? What's the difference, other than a slightly easier syntax?

Perl's OO is weak unfortunately. I love Perl (my first  language), but it offers little in the way of encapsulation, inheritance, and other fundamental OO concepts. Objects are references to a hash in Perl, nothing more.

---

### Post by KCPokes on 2007-10-17
> **scruff said:**
> I'm not sure I understand this statement. You will not find an OS that has Perl installed by default and not python. That is because the only OS's that include either are Linux and Unix-like OS's including OSX and all of those include both.

Windows includes neither by default...

For example, Solaris does not have python installed by default yet it does have perl installed by default.  Same for AIX.  I am speaking from a production corporate UNIX eCommerce environment standpoint, not a personal install of common LInux distro.  From a support standpoint you are forced to work with what is available as installing something like Python or Ruby would require an exception and jumping through a bunch of hurdles.  

This does not apply for someone's personal use, of course, at which point I say go with whatever you are comfortable with.  Typically, though, if you can code in one, say Perl, you can easily move to something like Python and at least accomplish basic tasks without struggling much.

---

### Post by scruff on 2007-10-17
> **KCPokes said:**
> For example, Solaris does not have python installed by default yet it does have perl installed by default.  Same for AIX.  I am speaking from a production corporate UNIX eCommerce environment standpoint, not a personal install of common LInux distro.  From a support standpoint you are forced to work with what is available as installing something like Python or Ruby would require an exception and jumping through a bunch of hurdles.  

This does not apply for someone's personal use, of course, at which point I say go with whatever you are comfortable with.  Typically, though, if you can code in one, say Perl, you can easily move to something like Python and at least accomplish basic tasks without struggling much.

Is that right? I haven't used Solaris in at least 4 years (and never AIX) but I can't find any docs that indicate that Python is not a default on Solaris. I haven't searched on AIX yet...

 I also come from a production environment and we wouldn't use anything such as Solaris or AIX. **Many **people don't. Red Hat (while I am not at all a fan) is still used in most server environments. People don't want to pay for commercial UNIX anymore. Why should you? When Linux (even when expensive such as RHLE) offer more up-to-date software, excellent support, and a wider range of packages? For development, we use RHLE 9 exclusively. For other tasks, Fedora is the workhorse. 

While this is not a 100% educated opinion, I would still lay money on most servers out there running a Linux OS than something like Solaris. One fact that I do have is I can find tons of jobs related to Linux knowledge, but rarely (if ever) see ads for Solaris experience...

---

### Post by KCPokes on 2007-10-17
> **scruff said:**
> Is that right? I haven't used Solaris in at least 4 years (and never AIX) but I can't find any docs that indicate that Python is not a default on Solaris. I haven't searched on AIX yet...

 I also come from a production environment and we wouldn't use anything such as Solaris or AIX. **Many **people don't. Red Hat (while I am not at all a fan) is still used in most server environments. People don't want to pay for commercial UNIX anymore. Why should you? When Linux (even when expensive such as RHLE) offer more up-to-date software, excellent support, and a wider range of packages? For development, we use RHLE 9 exclusively. For other tasks, Fedora is the workhorse. 

While this is not a 100% educated opinion, I would still lay money on most servers out there running a Linux OS than something like Solaris. One fact that I do have is I can find tons of jobs related to Linux knowledge, but rarely (if ever) see ads for Solaris experience...

I have a Solaris server running downstairs right now and can tell you that python does not come by default.  How that changes over time, no idea.  I'm sure, eventually, it'll be included as well. 

As far as paying for commerical UNIX, who does?  I don't pay for Solaris.  In fact Solaris is going the way of Open Source itself.  You pay for SUN support, Sun hardware, but not necessarily the software.  

You can always argue why one company chooses to go one route while the next doesn't.  Why pay for Sun/iPlanet licenses when Apache is available and the support community is better?  Why pay for WebLogic licenses when you could potentially use JBoss?  Others make the decisions, which I may or may not agree with.  When it comes down to which is in more demand, UNIX versus Linux, it is all going to depend on where you are located.  Any more you see positions open looking for both experience as, when it comes down to it, if you have experience in one you can pick up the other pretty quickly.  We are still more of a Sun shop, with IBM as a partner, and a growing number of RHEL blade servers.  

While on the subject of the different flavors, one thing I do know is that Perl runs so much more efficient on Linux then it does Solaris.  Funny part is that it is not a slight difference either; it runs noticably faster on a desktop running Fedora then it did on a dual-core Sun server.

[EDIT] I don't disagree that Linux is becoming more and more, if not the defacto standard, prevalent in data centers.  It really comes down to the task at hand; some of these high end applications still require the architecture behind UNIX.

---

### Post by scruff on 2007-10-17
> **KCPokes said:**
> 
You can always argue why one company chooses to go one route while the next doesn't.  Why pay for Sun/iPlanet licenses when Apache is available and the support community is better?  Why pay for WebLogic licenses when you could potentially use JBoss?  Others make the decisions, which I may or may not agree with.  When it comes down to which is in more demand, UNIX versus Linux, it is all going to depend on where you are located.  Any more you see positions open looking for both experience as, when it comes down to it, if you have experience in one you can pick up the other pretty quickly.  We are still more of a Sun shop, with IBM as a partner, and a growing number of RHEL blade servers.  


I see your point. I'm not sure about other locations, but Boston, NYC, and NJ see a lot more Linux action than UNIX.

> 
While on the subject of the different flavors, one thing I do know is that Perl runs so much more efficient on Linux then it does Solaris.  Funny part is that it is not a slight difference either; it runs noticably faster on a desktop running Fedora then it did on a dual-core Sun server.

Interesting. I spent very little time on Solaris, but it is curious that it would run less efficient on a powerful Sun machine than on a weaker Linux box...

---

### Post by slavik on 2007-10-17
Sun = Sparc = hardware not as easily available.

As for people paying for commercial UNIX? People buy Macs, don't they? ;)

When you buy IBM, you buy the whole computing system/grid/whatever, just like a Mac, just how you bought computers in 1980s. You buy a system where the hardware and the software (OS) are sold together as a package.

Honestly, I wish that I could have a PowerPC or that new Sun chip under my desk. Except I don't make that kind of money (especially with grad school ahead of me).

Thing about reading other's Perl code is just like reading the startx script. Even though it's shell scripting, it is still difficult to read

as far as OO, yes OO sucks, there isn't even any OO in C but that didn't stop X and GTK.

In OO Python code, I see member functions with self as the first arguement. Make that firstgument mandatory (not optional) and you can do OO in ANY language.

As for encapsulation, structs do that fine.

Then there is data hiding and restricting data access (which is important for OO). In C, the "marketing idea" turned out (C was written before OO and when Smalltalk was around, it was slow) to be "Here's a box, here's the people that will put the right thing into your box if you ask them." It doesn't stop you from looking into the box and changing it before asking someone to put something else in. But once you break that seal, you better be careful or things will blow up in your face. Think of the package manager or program installer. In Ubuntu, you compile everything from source if you want, but if you want to upgrade a single package, expect to recompile for two days. In Windows, many said to hell with proper installations and we see the results of that (registry getting screwed up, installers managing dll files by themselves, etc.)

Many guides I see in the howto forum for installing new programs are pretty much "./configure && make && make install" which bypasses the package manager ... that's nice and cute, except when things break. That is why you learn to create packages.

you can "cat /proc/cpuinfo" or you can run a program that will make lots of neat sense out of what's in there. :)

OO is nice, but not having it is not the end of the world. But how many people can code in more than 1 paradigm? (answer: fewer and fewer)

---

### Post by LaRoza on 2007-10-18
> **slavik said:**
> 

OO is nice, but not having it is not the end of the world. But how many people can code in more than 1 paradigm? (answer: fewer and fewer)

I try to learn, I learned C, for Procedural, FORTRAN 77 for structured (it makes you use Fortran's rules in a wise manner, lots of goto's), Python, Java, PHP5 and C++ for OO, and LISP for functional.

I usually code in a prodedural manner, but use OO if it makes it easier.

---

### Post by pmasiar on 2007-10-18
I loved Perl in 2001. It was my first dynamically typed language. 

Then I used in real-life big project, and it went down in flames. Standard worst-case scenario: mixed bunch of people (biologists+programmers), no strong coding standards, everybody is learning on-the-fly. Code is huge mess. We will never do any other project in Perl: even Java (crap it is) would be better then that. For throw-away script under 100 lines, maybe. But now, I use Python ever for that.

For me, Perl is write-only language. I don't want to read code I wrote myself. :-)

mjwood0, KCPokes:

You claim that Python is not available by default on SunOS and AIX, which are proprietary Unixes. I don't have stats, but my guess will be that those boxes have 10% or or less of total Linux server market, and Python might be missing on some of them (but not all). And I never head of PC-based Linux server without Python. Did you?

So my calculations are, Python is still available on 90% of the Linux/Unix servers. I understand that some companies prefer to pay for expensive boxes, but majority does not.

---

### Post by slavik on 2007-10-18
No coding standards? That's your problem right there.

Using another language does not suddenly organise your code magically.

---

### Post by pmasiar on 2007-10-18
I know but in Perl it just blows your project to pieces, more so that other languages.

---

### Post by KCPokes on 2007-10-18
> **pmasiar said:**
> I don't have stats, but my guess will be that those boxes have 10% or or less of total Linux server market, and Python might be missing on some of them (but not all). And I never head of PC-based Linux server without Python. Did you?

I don't want to get into the "this is better then that" debate, but seriously 10%?  It wouldn't be the total linux market, it would be the total *Nix server market.  It is just recently that major corporations (past 5 years) have started to embrace Linux as a viable alternative.  I'm speaking for a corporate standpoint and not a hosting business or personal use standpoint.  When it comes down to it, does it matter?  Unless someone can produce some sound numbers, which I haven't found much, its all speculation.  My standpoint is purely from what I work with everyday, as well as aquaintances that work in other corporations.  I don't prefer Solaris, it is just what is entrenched already.  We've attempted to move from applications from Unix to Linux and it is not a trivial task; sometimes you are successful, sometimes you arent.  I do beleive if you start out with the intention of it being Linux, depending on application architecture, you can make it work.  Some of the vendors, though, are a bit slow in getting stable Linux replacements out there. 

That said, I will agree with you on the Linux point; if the server is linux, there is a 99.9% chance that it will have both Perl and Python.  I say go with whatever you are comfortable with.  Quick and dirty with perl is easy and you can typically be sure that it is going to run, regardless of the OS.  I'm sure the same could be said for Python, long as its there.

---

### Post by pmasiar on 2007-10-18
I have no numbers of course, google "unix server market share" suggested [State of the server market](http://www.cmswire.com/cms/industry-news/the-state-of-the-server-market-000599.php). Linux grows faster that Unix, of course this is misleading because in price, PC-based server is much cheaper that high-end Unix server. And many people do what we do in our department: many PC-servers are bought from Dell with Windows and reformatted right away or year-two later.

Yes I know there are couple old Solaris boxes around (heck, we still run VAX somewhere down in the basement), but cheap PC-based Linux boxes is the hot growth area (and cheap PC-based Windows servers). According to article, Linux doubles every 2 years, Unix (at that speed) in about 20 years.

Of course article talks in terms of sales amount, not units sold, and mixes PC-based and Linux boxes with traditional Unix from same manufacturer, but the trend is unmistakable even beyond all the confusion.

---

### Post by KCPokes on 2007-10-18
> **pmasiar said:**
> And many people do what we do in our department: many PC-servers are bought from Dell with Windows and reformatted right away or year-two later.


I feel that we've taken this thread WAY off topic, but I do enjoy a good in-depth conversation.  :)

Anyway, to your point, this is, in my world, not what we'd consider a Linux server.  This is still purely a desktop running Linux.  Even if you were to install the server version, run an application on it, it does not contain the redundancy that would meet the classification of a server.  We've been doing it for years with workstations around here.  In fact we have some very visible internal applications that they are unaware of the fact that they sit in a room, on a workstation, and not a data center on a redundant server.  The system administrators want no part of it due to the fact that there is no nightly backups, no redundant hardware, and its running our install of the OS and not their standard install.  

Linux is growing in leaps and bounds, no doubt, mainly due to its ease of availability and relative ease to quickly set up on existing hardware.  It'll continue to grow.  But regardless of where it goes, the companies like Sun and IBM will continue to exist and do well solely for the fact that someone has to produce the hardware to run these enterprise applications.  As fun as a cluster of small servers sounds, its hard enough to maintain the number of large servers required to meet the traffic demands.  

But if it makes you feel any better, I am looking to replace my dual processor Sun server, at home, with a more modern machine, running Linux!  Is it Solaris that is slow or the fact that the machine is ancient (2X300Mhz), but at this point I need more speed and my other linux servers haven't failed me yet!

---

### Post by loell on 2007-10-18
speak of the devil, here's another reason to love perl. :KS

[http://kovaya.com/miscellany/2007/10/insert-coin.html]("http://kovaya.com/miscellany/2007/10/insert-coin.html")

---

### Post by pmasiar on 2007-10-19
> **KCPokes said:**
> The system administrators want no part of it due to the fact that there is no nightly backups, no redundant hardware, 

our Dell servers have no redundant hardware beyond RAID disks, but they are backed up nightly.

> companies like Sun and IBM will continue to exist and do well solely for the fact that someone has to produce the hardware to run these enterprise applications.  As fun as a cluster of small servers sounds, its hard enough to maintain the number of large servers required to meet the traffic demands.  

Obviously. They will be around for a long time - IBM mainframes are still around. 

Your point was, that Perl is more often available on those high-end servers, which I do not dispute. My point is, that those high-end servers with Perl and no Python are rare now, and will become even rarer in the future, as plain PC-based servers (what you call "workstations") will became even more widespread.

Edit: proper word for these non-high-end servers is "commodity hardware servers".

BTW are you aware that Google search servers are plain PC-based, except of one single app, ERP accounting or something, which runs on some Sun or something? It is cheaper to admit that hardware can fail, and handle it, that to pay for nearly fault-tolerant hardware. It is harder to program that way tho :-)

---

### Post by LaRoza on 2007-12-02
I just started looking into Perl again (it is two in the morning) for no particular reason. I never really "got" Perl, and couldn't use it. 

Maybe it is the Mountain Dew, or the late hour, but Perl is suddenly attractive to me. 

Hopefully I will retain what I learn.

---

### Post by slavik on 2007-12-02
I find that sometimes I need a second pass at something to "get it" :) (mathematical induction is one example).

---

### Post by LaRoza on 2007-12-02
> **slavik said:**
> I find that sometimes I need a second pass at something to "get it" :) (mathematical induction is one example).

I had trouble with functions the first time, I didn't understand how they were implemented.

Now, $_ seems like a very good idea.

I am using, [http://www.greenteapress.com/perl/](http://www.greenteapress.com/perl/)

---

### Post by pmasiar on 2007-12-02
Perl is beautiful language when you write your code during nightly hackathon. It is almost RMMADWIM - 'read my mind and do what I mean".

When it gets ugly is morning after - when you need to read and understand again your last night's transgressions. :-)

---

### Post by slavik on 2008-02-18
> **scruff said:**
> You deal with references, don't you? What's the difference, other than a slightly easier syntax?

Perl's OO is weak unfortunately. I love Perl (my first  language), but it offers little in the way of encapsulation, inheritance, and other fundamental OO concepts. Objects are references to a hash in Perl, nothing more.
umm, it IS more ... it is a reference to a **BLESSED** hash! :-P

---

### Post by pmasiar on 2008-02-18
lnodstal submitted [good rant against Perl](http://groups.google.no/group/comp.lang.lisp/msg/fc76ebab1cb2f863). Money para: "it's not that perl programmers are idiots, it's that the **language rewards   idiotic behavior** in a way that no other language or tool has ever done, and on top of it,** it punishes conscientiousness and quality craftsmanship**  -- put simply: you can commit any dirty hack in a few minutes in perl,  but you can't write an elegant, maintainabale program that becomes an  asset to both you and your employer; you can make something work, but you  can't really figure out its complete set of failure modes and conditions  of failure. "

To enliven the discussion here :twisted: , I'll add my own link: [The Problems of Perl: The Future of Bugzilla](http://avatraxiom.livejournal.com/58084.html). Author claims "**Perl would not be my first choice** for writing or maintaining a large project, such as Bugzilla." And then substantiates that claim with facts based on experience with Bugzilla - one of the most popular bug tracking package. It is not the only, even if it was one of the first open-source bug trackers, bacause of being build in Perl. many developers build competing packages, to avoid Perl.

This, I hope (likely in vain :-) ), will keep discussion about Perl out of other threads. We'll see.

**Edit:** OK maybe I misspoke. I do not want to restrict discussion about Perl per se, I want to limit  discussion about pro and con of Perl in other threads, and put it here, in context, so we don't have to repeat same arguments again and again.

---

### Post by Jessehk on 2008-02-18
> **pmasiar said:**
> 

This, I hope (likely in vain :-) ), will keep discussion about Perl out of other threads. We'll see.

Who are you to attempt such a thing?

---

### Post by pmasiar on 2008-02-18
> **Jessehk said:**
> Who are you to attempt such a thing?

maybe just someone who is annoyed when discussion of pro and con of Perl is all over other threads? 

I started "Why I love/Hate Python" when we had such talks about Python all over the place. Is your position that restricting Python advocacy and critique to dedicated thread is good, but Perl advocacy and critique should not be subject of such restrictions?

---

### Post by slavik on 2008-02-18
> **pmasiar said:**
> maybe just someone who is annoyed when discussion of pro and con of Perl is all over other threads? 

I started "Why I love/Hate Python" when we had such talks about Python all over the place. Is your position that restricting Python advocacy and critique to dedicated thread is good, but Perl advocacy and critique should not be subject of such restrictions?
yet you do advacate Python as being an easier language to anyone asking questions of how to do things in another language. maybe I should just copy/paste your comments and do a s/Python/Perl/gi on it???

---

### Post by scruff on 2008-02-18
> **slavik said:**
> yet you do advacate Python as being an easier language to anyone asking questions of how to do things in another language...

Speaking of... I see that **all over the place** around here. Not pointing any fingers at anyone directly (I don't memorize this stuff anyway) but it is extremely annoying even to just read, nevermind if **I** was the OP asking about C++ or something like. 

Every language has its place. Use the right tool for the job, all that. Who wants to hear "you should really just use language foo because it is better" each time they ask a language specific question?

---

### Post by pmasiar on 2008-02-18
> **slavik said:**
> yet you do advacate Python as being an easier language to anyone asking questions of how to do things in another language. 

Only if I see the poster is beginner and I truly believe learning that basics of programming in Python will make his/her next step (Learning C++ or whatever) simpler.

> maybe I should just copy/paste your comments and do a s/Python/Perl/gi on it???

You can try but it would not fly: It would not be true :-) 

Why you instead of attacking me try to respond to criticism of Perl I linked above (post #34)? Maybe because it is hard/impossible?

---

### Post by pmasiar on 2008-02-18
> **scruff said:**
> "you should really just use language foo because it is better" each time they ask a language specific question?

I never said that. I say: if you beginner programmer, you might be better off to learn basics of programming in Python, and after learning to crawl, learn that other programming language. In experience of many (including our unscientific poll), that is more effective way to learn programming that ie. start with C++ - but how is beginner going to know that is someone experiences will not challenge her assumption that C++ is the best language for beginner to learn basics?

BTW why we discuss Python here? :-)

---

### Post by scruff on 2008-02-18
> **pmasiar said:**
> I never said that. I say: if you beginner programmer, you might be better off to learn basics of programming in Python, and after learning to crawl, learn that other programming language. In experience of many (including our unscientific poll), that is more effective way to learn programming that ie. start with C++ - but how is beginner going to know that is someone experiences will not challenge her assumption that C++ is the best language for beginner to learn basics?

BTW why we discuss Python here? :-)

Apologies. Like I said, I wasn't pointing any fingers. I see an absolute ton of ppl in this forum trying to sway people away from whatever language they are learning and originally posting about. 

I can see where there are valid reasons to do so, but I also read plenty of "my language is best" type responses. Please don't take any personal offense to my response - none was intended :)

---

### Post by ruy_lopez on 2008-02-18
> **scruff said:**
> I see an absolute ton of ppl in this forum trying to sway people away from whatever language they are learning and originally posting about

I agree. I don't see how hijacking people's threads, helps beginners learn anything.

---

### Post by scruff on 2008-02-18
> **slavik said:**
> umm, it IS more ... it is a reference to a **BLESSED** hash! :-P

Hahaha! Good point slavik :)

---

### Post by pmasiar on 2008-02-18
> **ruy_lopez said:**
> I agree. I don't see how hijacking people's threads, helps beginners learn anything.

You exactly missed my point.

If goal of poster is to learn programming, but by lack of information thinks that say APL is the best language to start, in your opinion should I suggest best APL book, or challenge false information about APL and suggest better language ofr a beginner to learn programming? 

Even Perl would be better than APL! :-)

Looking beyond narrow-minded question of the poster and trying to solve whole problem, not just that single bug, is what helps beginner more. IMHO of course, YMMV. 

I plan to do it again, and if you want to challenge it every time, you may as well start  new thread about it, which I link to each of my suggestions :-) so we don't have to argue same issue every time.

---

### Post by ruy_lopez on 2008-02-18
> **pmasiar said:**
> You exactly missed my point

The last time I checked, I was responding to scruff, not you. Are you okay? Seriously. You are assuming everything everyone says is about you?

It takes more than one person to hijack a thread.

---

### Post by slavik on 2008-02-18
> **pmasiar said:**
> I never said that. I say: if you beginner programmer, you might be better off to learn basics of programming in Python, and after learning to crawl, learn that other programming language. In experience of many (including our unscientific poll), that is more effective way to learn programming that ie. start with C++ - but how is beginner going to know that is someone experiences will not challenge her assumption that C++ is the best language for beginner to learn basics?

BTW why we discuss Python here? :-)
You push Python, I push Perl (and C). You say that using a highlevel level like Perl/Python is best for beginners, I say that a lower level language is better.

You either start at the top and then drop the bottom because there is no GC and you don't know how pointers work, or you start at the bottom and then like the top because there is GC and you don't have to deal with the pointers.

BASIC = Beginner's All Purpose Symbolic Instruction Code. it has beginner in the name, yet even the creators said that it was a crappy language for beginners ...

I'd rather as a computer scientist have a situation where there are 10 people who can write good code in C/Python/Perl/whatever else than if there were 100 people who could write any code in Python and yelling that C is crap because it is not dynamically type and doesn't have GC.

Remember, performance tradeoff for an app might be OK (depending on what it does), but I will never accept a performance system for the entire system.

Beagle is written in C#, Tracker is written in C ... now tell me which has better performance. (as a bonus, guess which one I have)

The reason why I like Perl is that many things that I want to do in C are much easier in Perl. If I can do it easily in C, I do it. If I can't, I look into Perl.

---

### Post by pmasiar on 2008-02-18
> **ruy_lopez said:**
> The last time I checked, I was responding to scruff, not you. Are you okay? Seriously. You are assuming everything everyone says is about you?

It takes more than one person to hijack a thread.

Well, you agreed with scruff. I responded to your comment. Do you disagree because I said it, or you disagree on substance?

It might be funny but [scruff's thread about simplest way to generate XML](http://ubuntuforums.org/showthread.php?t=700647) was solved exactly because I challenged OP's assumptions and suggested completely different solution.

So if I followed your logic, I would not be able to provide that more optimal solution.

BTW I don't like you attacking me personally, instead of commenting on substance. Maybe because you cannot?

Relax, I am not here to get you. I am trying to solve problems, while having reasonable fun.

---

### Post by pmasiar on 2008-02-18
> **slavik said:**
> You push Python, I push Perl (and C). You say that using a highlevel level like Perl/Python is best for beginners, I say that a lower level language is better.

You either start at the top and then drop the bottom because there is no GC and you don't know how pointers work, or you start at the bottom and then like the top because there is GC and you don't have to deal with the pointers.

This was discussed to death in other threads, I am not going to start again. Our [completely unscientific poll](http://ubuntuforums.org/showthread.php?t=528134) gave victory to high-level languages, with Python winning overall.


> I'd rather as a computer scientist have a situation where there are 10 people who can write good code in C/Python/Perl/whatever else than if there were 100 people who could write any code in Python and yelling that C is crap because it is not dynamically type and doesn't have GC....

Remember, performance tradeoff for an app might be OK (depending on what it does), but I will never accept a performance system for the entire system.


Do you have me somewhere on record that I said C is crap? Can you link it? Or you prefer to build a strawman and then  tear it to pieces, so it will feel as a victory?

In fact, **everywhere I mention Python I suggest C as second language to learn**.

I just tell: "avoid Perl if you can" :-)

All these intense emotions, and **anti-Perl rants (post #34) are still uncontested. So looks they survived the fury?** :-)

---

### Post by ruy_lopez on 2008-02-18
> **pmasiar said:**
> I don't like you attacking me personally, instead of commenting on substance. Maybe because you cannot?I don't see a lot of substance. I see a lot of ideology. On both sides. Ideological arguments never have any ending. They are a waste of time. I prefer to occupy myself with practical considerations.

---

### Post by pmasiar on 2008-02-18
> I prefer to occupy myself with practical considerations
Me too.

OK at least we agree that best way to get practical solutions is to ask beginners about what they assume, to help them get better solution than simply answering the misplaced question they asked originally.

---

### Post by slavik on 2008-02-18
Need I mention the way Python lazily creates multiple references to the same list when the programmer wanted multiple separate lists? Or that one example where 2 children inhereting from a single parent with a list end up with a reference to the same list?

Both were asked about on this forum.

As for answering misplaced questions ... I don't remember many people asking what the OP was interested in ...

EDIT: as for another reason why I love Perl, it is exactly because OO is a hack and everything can be accessed as a hash, so you can list anything the hash includes. Don't know if any other languages do this.

---

### Post by slavik on 2008-02-19
Yet another reason why I love Perl, it is reflective (I found this out because someone posted to a wikipedia link with a language table in LaRoza's language recommendation page thread).

---

### Post by slavik on 2008-05-27
and to resurrect this thread:

[php]
#!/usr/bin/perl

use threads;

$i = 0;

sub sub1 {
    while (1) {
    	$i++;
	}
}

sub sub2 {
    while (1) {
    	$i--;
	}
}

$thr1 = threads->new(\&sub1);
$thr2 = threads->new(\&sub2);

$thr1->join();
$thr2->join();
[/php]

[img]http://ccannizzaro.com/images/limon.jpg[/img]

If you have 2 or more CPUs in your system, you will not that the above code will fully load 2 CPUs. Something which cannot be said for some other language ...

---

### Post by days_of_ruin on 2008-05-27
[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=python&lang2=perl]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=python&lang2=perl")

Speed is about the same.And every programmer can read it.
python ftw!

---

### Post by |{urse on 2008-05-27
hrm, I told my boss i was going to rewrite our product serial number generator in perl, currently it's in asp. She made a hideous face and said eww perl. wth! I asked her why she didn't like perl and she said "Well it's so old." LOL I'm hearing a lot of this lately, Is ruby so new that perl is old now? and does that mean that python is ancient? Where does that leave good old "mother of all", C?

---

### Post by alguin2 on 2008-05-27
I got hooked into Perl as an all-purpose, no-nonsense scripting/small-utility language since it first came out as a programming language "flavor of the week". I've tried using other languages (esp. Python), and have always come back to Perl because of its simplicity and performance.  

I've always felt Python to be sluggish in comparison to Perl, but never had any stats to back it up.   I found two, but I'm not 100% sure if the speed advantage still exists or if it's in the scale shown by these benchmarks:

1. Python vs Perl vs Java vs C++: 
[INDENT][http://furryland.org/~mikec/bench/]("http://furryland.org/~mikec/bench/")
[/INDENT]

2. PerlOpenGL (POGL) vs PyOpenGL:
[INDENT][URL="http://graphcomp.com/pogl.cgi?v=0111s3B2&r=s3m3"]http://graphcomp.com/pogl.cgi?v=0111s3B2&r=s3m3
[/URL][/INDENT]

---

### Post by slavik on 2008-05-28
honestly, even if Perl is much faster than Python, I will still tend to put them in the same category.

The thing about Mike Connel's benchmarks is that in one of them he uses range() while in the rest, he uses xrange(). I am no Python guru, but I am sure there is a difference of generating the entire list (range()) at once versus generating one element at a time (xrange()).

Another thing to keep in mind is that I was told by someone doing lots of text processing, that Java would crash up, but both Perl and Python would chew it without problems.

In Perl, C calls are pretty much just that, it's a straight function call.

---

### Post by pmasiar on 2008-06-01
Very interesting [article about Larry Wall](http://www.softpanorama.org/People/Wall/index.shtml), and Perl in context.

- Perl was the first big original open-source project (not a reimplementation of something preexisting)
- Perl was first "big" language provided by community, without backup of a big company.
- Perl was first "scripting" language used in enterprise-level computing, proving that you do not have to compile to execute programs (and show how productivity can be increased by that).

So, I cherish and appreciate Perl (now even little more than before reading that article) - even if I prefer to use Python for my code.

---

### Post by slavik on 2008-06-01
> **pmasiar said:**
> Very interesting [article about Larry Wall](http://www.softpanorama.org/People/Wall/index.shtml), and Perl in context.

- Perl was the first big original open-source project (not a reimplementation of something preexisting)
- Perl was first "big" language provided by community, without backup of a big company.
- Perl was first "scripting" language used in enterprise-level computing, proving that you do not have to compile to execute programs (and show how productivity can be increased by that).

So, I cherish and appreciate Perl (now even little more than before reading that article) - even if I prefer to use Python for my code.
Well, depends on whether AWK can be considered a scripting language, since Perl borrows it's regex syntax from AWK which was written by Kernighan (and 2 colleagues, hence the abbreviation).

AWK could be considered the first scripting language used in enterprised (AT&T wanted a text processor in exchange for funding Unics)

IMO, Perl6 also brings some new "things" to the table, main point is that it is a community developed language specification. Perl, Ruby, and Python all have communities but all working on a single implementation of the language.

I was also told that Perl6 has been changed due to feedback from projects that are working on implementations (the biggest one AFAIK is pugs, it's an interpreter written in Haskell).

---

### Post by brunovecchi on 2008-08-09
I absolutely LOVE Perl. I am not a programmer (I'm a molecular biologist); I don't need to build any millon-line code application so the scalability/mantainability issue does not concern me. 
The fact is, I can write a script that proccesses hundreds of megabytes of text (ie, entire genomes) with ease having spent only a couple of hours of writing/running/debugging and without major frustrations.
Part of this is because of the deliberate decisions that Larry Wall (a linguist) made when he designed the language, and another very important part of this is due to the huge repository of freely available modules ([**CPAN**]("http://search.cpan.org/")). We saw earlier in this thread an example of a module making the coding of a multi-threaded process a trivial task.

Perl all the way.

I know that I could very well do whatever I said here with any other language, but the fact is, I don't need to because I already am comfortable with the only one I know.

---

### Post by fiatveritas on 2012-04-04
> **pmasiar said:**
> lnodstal submitted [good rant against Perl](http://groups.google.no/group/comp.lang.lisp/msg/fc76ebab1cb2f863). Money para: "it's not that perl programmers are idiots, it's that the **language rewards   idiotic behavior** in a way that no other language or tool has ever done, and on top of it,** it punishes conscientiousness and quality craftsmanship**  -- put simply: you can commit any dirty hack in a few minutes in perl,  but you can't write an elegant, maintainabale program that becomes an  asset to both you and your employer; you can make something work, but you  can't really figure out its complete set of failure modes and conditions  of failure. "

To enliven the discussion here :twisted: , I'll add my own link: [The Problems of Perl: The Future of Bugzilla](http://avatraxiom.livejournal.com/58084.html). Author claims "**Perl would not be my first choice** for writing or maintaining a large project, such as Bugzilla." And then substantiates that claim with facts based on experience with Bugzilla - one of the most popular bug tracking package. It is not the only, even if it was one of the first open-source bug trackers, bacause of being build in Perl. many developers build competing packages, to avoid Perl.

This, I hope (likely in vain :-) ), will keep discussion about Perl out of other threads. We'll see.

**Edit:** OK maybe I misspoke. I do not want to restrict discussion about Perl per se, I want to limit  discussion about pro and con of Perl in other threads, and put it here, in context, so we don't have to repeat same arguments again and again.

I read the article on Bugzilla and it was much more readable given that the author wasn't blasting away at Perl programmer's integrity. Inodstal's arguement is biased and, as a result, is difficult to take seriously because rather than cite examples, he or she just talks about ethical matters like hacking. I recently started programming in Perl and love Hash tables. What I don't like is a thinking pattern that emerges, e.g., negation. Rather than saying if(not A) you can write unless(A) which is problematic because I have a possitive manner of thinking rather than negative. Which brings me to my other point: people don't like that Perl is flexible and, therefore, refuse to learn how other programmer script in Perl.

---

