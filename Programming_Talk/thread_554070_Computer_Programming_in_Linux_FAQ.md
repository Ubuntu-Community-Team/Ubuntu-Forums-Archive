---
title: "Computer Programming in Linux FAQ"
date: 2007-09-18
forum: Programming Talk
---

### Post by LaRoza on 2007-09-18
**BEFORE POSTING:**

* [Learn Computer Programming FAQ]("http://ubuntuforums.org/showthread.php?t=667422")

* **[How to post code on the forums]("http://ubuntuforums.org/showthread.php?t=641693")**

[SIZE="4"][color="blue"]Frequently Asked Questions[/color][/SIZE]

[color="blue"]**0. What Language Should I Learn?**[/color]
There are many languages that you can use: [Wiki for Programming in Linux AND Windows in many languages]("http://laroza.pbwiki.com") 

[color="blue"]**1. What Editors Can I Use?**][/color]

This is a personal preference, here are some opinions:

[PHP and ASP]("http://ubuntuforums.org/showthread.php?t=553680")
[Editor thread]("http://ubuntuforums.org/showthread.php?t=543902")
[Editor Similar to Dev-C++]("http://ubuntuforums.org/showthread.php?t=542284")

[color="blue"]**2. Compiling and running C,C++,Java,Fortran, and other programs**][/color]
See [Programming in Ubuntu Wiki]("http://ubuntuprogramming.wikidot.com")
If you want to use the Intel Fortran compiler, see [here]("http://ubuntuforums.org/showthread.php?t=585892&page=2")

[color="blue"]**3. [color="Blue"]C#[/color] on Ubuntu**][/color]
C# works in Linux, see these [Opinions]("http://ubuntuforums.org/showthread.php?t=581198") and [this for how to compile with Mono, ]("http://ubuntuforums.org/showthread.php?p=3985400#post3985400")

[color="blue"]**6. [COLOR="Blue"]Visual Basic[/color] on Ubuntu**][/color]
[Visual Basic on Ubuntu]("http://ubuntuforums.org/showthread.php?t=549177") 

[color="blue"]**7. Visual Studio**][/color]
[Visual Studio on Ubuntu]("http://ubuntuforums.org/showthread.php?t=450388")

[color="blue"]**8. IDEs**[/color]
[The IDE thread, take your pick]("http://ubuntuforums.org/showthread.php?t=6762") | [IDE Comparison]("http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments")

[color="blue"]**9. How do I start my own project?**[/color] 

[I want to start my own project, how long it will take?]("http://ubuntuforums.org/showthread.php?t=689178")

---

### Post by Majorix on 2007-09-18
Yeah this is a nice idea. I voted for it to be sticky. I also want to learn the answers so keep them coming :D

---

### Post by LaRoza on 2007-09-18
> **Majorix said:**
> I also want to learn the answers so keep them coming :D

I am just searching the forums :D.

---

### Post by Lord Illidan on 2007-09-18
Nice thread!

---

### Post by gnusci on 2007-09-19
Also another possible necessary stuffs for C/C++ developing:

```

> sudo apt-get install build-essential (compiling tools)
> sudo apt-get install freeglut3-dev   (opengl)
> sudo apt-get build-dep xorg-dev      (x11 for developing)

```

May also be necessary some 32 bit libraries that can be required for some programs:

```

> sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2

```

---

### Post by mjrclark on 2007-09-19
I did a computing course at high school that was almost all VB6. Coming from that to most of the Linux IDEs the biggest shock, and largest barrier to getting going making ones own little toy projects is there is no obvious way to make a GUI.
Gambas, essentially a VB6 clone, solves this, whilst I would recommend it to anybody wanting to stay with a basic language it is not widely used. My request is firstly that this guide has a statement equating vb6 on windows with Gambas/some other RAD tool on Ubuntu, and secondly that a link to a guide to make a simple GUI programme is included that shows at least the basics of joining GUI and logic.

---

### Post by Frak on 2007-09-19
Great thread, helps alot.

---

### Post by ddrichardson on 2007-09-21
> **mjrclark said:**
> I did a computing course at high school that was almost all VB6. Coming from that to most of the Linux IDEs the biggest shock, and largest barrier to getting going making ones own little toy projects is there is no obvious way to make a GUI.
Gambas, essentially a VB6 clone, solves this, whilst I would recommend it to anybody wanting to stay with a basic language it is not widely used. My request is firstly that this guide has a statement equating vb6 on windows with Gambas/some other RAD tool on Ubuntu, and secondly that a link to a guide to make a simple GUI programme is included that shows at least the basics of joining GUI and logic.

Personally I don't think the transition to Glade/Python is  bad.

---

### Post by Blue Sky on 2007-09-22
I would recommend completely avoiding Microsoft technologies unless you plan on developing native Windows applications.
I would certainly avoid using Mono given, what at least I perceive it to have an uncertain future. I would also avoid Gambas for the same reasons as well as its slow development cycle, its lack of popularity is reflective of its future ambitions.

Perl, Python, Java, C++ - all very well supported in Linux and are excellent languages.

---

### Post by LaRoza on 2007-09-23
> **Blue Sky said:**
> I would recommend completely avoiding Microsoft technologies unless you plan on developing native Windows applications.
I would certainly avoid using Mono given, what at least I perceive it to have an uncertain future.

Perl, Python, Java, C++ - all very well supported in Linux and are excellent languages.

For discussions on Mono, see [http://ubuntuforums.org/showthread.php?t=293623&highlight=boycott+mono](http://ubuntuforums.org/showthread.php?t=293623&highlight=boycott+mono)

Future posters, do not debate Mono here.

(I agree with the above, but many people use Mono and are happy with it)

---

### Post by weedeatr on 2007-09-24
Nice nice i like this thread i think it will help alot of people!

-weedeatr-

---

### Post by LaRoza on 2007-09-25
> **weedeatr said:**
> Nice nice i like this thread i think it will help alot of people!

-weedeatr-

According to my logs, it has. My wiki has gotten many hits from this thread, and the questions that are answered with a link to this thread show it is useful, now if people read it first, before posting.

If you have other issues, please let me know. If they are significant to others, I will add them.

---

### Post by ryno519 on 2007-09-26
**Getting Essential GNOME and KDE Development Libraries and Tools**

If you are developing an application in GNOME or KDE there is a good chance you are going to need at least one or two development libraries and several other tools. These packages include several development libraries which you will need as well as an IDE, debugger, UML modeller, library documentation, interface designer, and programs to help you translate your applications to other languages. After you install these packages you will be ready to start developing.

For GNOME:
```
sudo apt-get install gnome-devel
```

This will install Anjuta, Bluefish, Glade, interface and API documentation and guidelines, necessary runtimes, development libraries and translation tools, as well as several other tools and libraries which these packages will pull with them.

It did not seem to come with a debugger, so if you want a debugger which will work with gcc/g++ you will need to install gdb.

```
sudo apt-get install gdb
```

For KDE:
```
sudo apt-get install kde-devel kde-devel-extras
```

This package is similar to gnome-devel, but it will give you KDE/Qt equivalents. You will receive necessary runtimes, Qt and KDE libraries and documentation as well as translation tools. It will also install Qt3 Designer and Umbrello, a UML modelling application (one of the better I've seen).

For whatever reason, neither kde-devel or kde-devel-extras come with an IDE. If you want an C/C++ IDE for KDE I recommend KDevelop. KDevelop is heads and shoulders above any other C/C++ IDE on the *nix platform IMHO.

```
sudo apt-get install kdevelop
```

---

### Post by FlyingIsFun1217 on 2007-09-27
> **gnusci said:**
> Also another possible necessary stuffs for C/C++ developing:

```

> sudo apt-get install freeglut3-dev   (open gl)
> sudo apt-get build-dep xorg-dev      (x11 for developing)

```


You only need the mentioned if you are doing graphical programming (Games, stuff like that) that uses OpenGL.

I'm guessing you don't need these though ;)

Just wanted to clarify!
FlyingIsFun1217

---

### Post by Vadi on 2007-09-27
Even though I'm not programming for windows, this thread helped me a ton. :)

---

### Post by LaRoza on 2007-09-28
> **Vadi said:**
> Even though I'm not programming for windows, this thread helped me a ton. :)

Do you think we should change the title to: "New Programmers In Linux -- Read This!"? I was thinking that this thread is useful to new programmer in Linux, regardless of prior experience.

---

### Post by Vadi on 2007-09-28
Sure. Keep the windows part too though.

---

### Post by Coyote21 on 2007-10-01
> **Blue Sky said:**
> I would recommend completely avoiding Microsoft technologies unless you plan on developing native Windows applications.
I would certainly avoid using Mono given, what at least I perceive it to have an uncertain future. I would also avoid Gambas for the same reasons as well as its slow development cycle, its lack of popularity is reflective of its future ambitions.

Perl, Python, Java, C++ - all very well supported in Linux and are excellent languages.

I'm 100% with you on that... Also, you won't go further with VB or even .NET, since their are essentially M$ (Acronym for Microsoft, in the freee software world) technologies. 

And also because, you will have hundreds of libraries and tools for developing, not only on Perl, Python, Java and C++, but also on Pascal (good for delphi developers (use free pascal, and it's libraries, that include GUI support and database access support), and users that are learning to program), Lisp, Ruby (widely used in games (particularly Japanese people, since ruby is made in Japan, and other things too \\:D/), and more recently in web pages thought  ruby on rails ([http://ruby.istheshit.net/](http://ruby.istheshit.net/)), Lua (made in Brazil, and that also speaks Portuguese like me), and many others, just look in the packages repositories.

Also, you might want to install an GUI wrapper around gdb, or other tools like valgrind.

---

### Post by Milliways on 2007-10-20
> **gnusci said:**
> Also another possible necessary stuffs for C/C++ developing:

```

> sudo apt-get install build-essential (compiling tools)
> sudo apt-get install freeglut3-dev   (opengl)
> sudo apt-get build-dep xorg-dev      (x11 for developing)

```

May also be necessary some 32 bit libraries that can be required for some programs:

```

> sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2

```

Thanks for these hints, but how do new linux users find out what libraries are available, and what they contain.

For all its cryptic documentation the Microsoft SDK includes what you need, or indicates what needs to be added.

---

### Post by LaRoza on 2007-10-20
> **Milliways said:**
> Thanks for these hints, but how do new linux users find out what libraries are available, and what they contain.

For all its cryptic documentation the Microsoft SDK includes what you need, or indicates what needs to be added.

What do you want to do, and in what language? I highly doubt the MS SDK tells you what library Python needs for using MySQL, I also doubt it tells you what you need to use nCurses in C.

If you know what you want to use, you will be aware of what you need. Noone starts out programming GTK apps, without knowing what GTK is.

The post you quoted was not really in line with this thread, it was advanced, except for the "build-essential" part. The questions concerning VB and build-essential are the main reasons this thread was started.

Nice to see a *Hitchhiker's* fan!

---

### Post by Milliways on 2007-10-21
I normally code in C++, using MSVC 6.0, but have decided Vista is impossible, so I am going either Linux or Mac.

One of the things that has been keeping me with Windows is ZTreeWin.
After loading up Ubuntu a couple of days ago, I decided to enhance UnixTree, but have had problems even getting it to build, before I start changing it.

Probably not a typical Linux startup, but I have always found the best way to learn anything is to start on a decent project.

Milliways, the Computer at the End of the Universe, (and my last Windows machine)  is in a long line of HHG2G themed machines. Trillian, is my Linux box.

---

### Post by Thumper! on 2007-10-22
i know it's kinda late but thanks alot dude!

---

### Post by technomaniac on 2007-10-31
Well I believe you must first read this book "Beginning Linux Programming" by Neil Mathew and Richard Stones, Wiley Publication. Even I am learning C programming on GNU/Linux-things like POSIX threads, processes, Kernel Programming..Its interesting.

---

### Post by tjagoda on 2007-11-27
Thanks for the great thread!

---

### Post by LinuxGuy1234 on 2007-12-02
A language I also found was Perl. Perl comes with all of the *buntus.

Sample script:
```

#!/usr/bin/perl
print "Hello Perl!"
```

---

### Post by Majorix on 2007-12-02
Its too easy to write unreadable codes with Perl. I try to stay away from it but it's a matter of choice, as usual.

And your avatar got me laughing :D

---

### Post by LaRoza on 2007-12-02
> **Majorix said:**
> Its too easy to write unreadable codes with Perl. I try to stay away from it but it's a matter of choice, as usual.

And your avatar got me laughing :D

Although Perl has a syntax that allows for unreadable and cryptic code, [http://99-bottles-of-beer.net/language-perl-737.html](http://99-bottles-of-beer.net/language-perl-737.html), it can be well written and is a very good language.

---

### Post by Frak on 2007-12-02
> **LaRoza said:**
> Although Perl has a syntax that allows for unreadable and cryptic code, [http://99-bottles-of-beer.net/language-perl-737.html](http://99-bottles-of-beer.net/language-perl-737.html), it can be well written and is a very good language.
Pretty Cool, for those that don't want to follow the link, the source is
```
    ''=~(        '(?{'        .('`'        |'%')        .('['        ^'-')
    .('`'        |'!')        .('`'        |',')        .'"'.        '\\$'
    .'=='        .('['        ^'+')        .('`'        |'/')        .('['
    ^'+')        .'||'        .(';'        &'=')        .(';'        &'=')
    .';-'        .'-'.        '\\$'        .'=;'        .('['        ^'(')
    .('['        ^'.')        .('`'        |'"')        .('!'        ^'+')
   .'_\\{'      .'(\\$'      .';=('.      '\\$=|'      ."\|".(      '`'^'.'
  ).(('`')|    '/').').'    .'\\"'.+(    '{'^'[').    ('`'|'"')    .('`'|'/'
 ).('['^'/')  .('['^'/').  ('`'|',').(  '`'|('%')).  '\\".\\"'.(  '['^('(')).
 '\\"'.('['^  '#').'!!--'  .'\\$=.\\"'  .('{'^'[').  ('`'|'/').(  '`'|"\&").(
 '{'^"\[").(  '`'|"\"").(  '`'|"\%").(  '`'|"\%").(  '['^(')')).  '\\").\\"'.
 ('{'^'[').(  '`'|"\/").(  '`'|"\.").(  '{'^"\[").(  '['^"\/").(  '`'|"\(").(
 '`'|"\%").(  '{'^"\[").(  '['^"\,").(  '`'|"\!").(  '`'|"\,").(  '`'|(',')).
 '\\"\\}'.+(  '['^"\+").(  '['^"\)").(  '`'|"\)").(  '`'|"\.").(  '['^('/')).
 '+_,\\",'.(  '{'^('[')).  ('\\$;!').(  '!'^"\+").(  '{'^"\/").(  '`'|"\!").(
 '`'|"\+").(  '`'|"\%").(  '{'^"\[").(  '`'|"\/").(  '`'|"\.").(  '`'|"\%").(
 '{'^"\[").(  '`'|"\$").(  '`'|"\/").(  '['^"\,").(  '`'|('.')).  ','.(('{')^
 '[').("\["^  '+').("\`"|  '!').("\["^  '(').("\["^  '(').("\{"^  '[').("\`"|
 ')').("\["^  '/').("\{"^  '[').("\`"|  '!').("\["^  ')').("\`"|  '/').("\["^
 '.').("\`"|  '.').("\`"|  '$')."\,".(  '!'^('+')).  '\\",_,\\"'  .'!'.("\!"^
 '+').("\!"^  '+').'\\"'.  ('['^',').(  '`'|"\(").(  '`'|"\)").(  '`'|"\,").(
 '`'|('%')).  '++\\$="})'  );$:=('.')^  '~';$~='@'|  '(';$^=')'^  '[';$/='`';
```
And it outputs
```
99 bottles of beer on the wall, 99 bottles of beer!
Take one down, pass it around,
98 bottles of beer on the wall!

98 bottles of beer on the wall, 98 bottles of beer!
Take one down, pass it around,
97 bottles of beer on the wall!

97 bottles of beer on the wall, 97 bottles of beer!
Take one down, pass it around,
96 bottles of beer on the wall!

96 bottles of beer on the wall, 96 bottles of beer!
Take one down, pass it around,
95 bottles of beer on the wall!

95 bottles of beer on the wall, 95 bottles of beer!
Take one down, pass it around,
94 bottles of beer on the wall!

94 bottles of beer on the wall, 94 bottles of beer!
Take one down, pass it around,
93 bottles of beer on the wall!

93 bottles of beer on the wall, 93 bottles of beer!
Take one down, pass it around,
92 bottles of beer on the wall!

92 bottles of beer on the wall, 92 bottles of beer!
Take one down, pass it around,
91 bottles of beer on the wall!

91 bottles of beer on the wall, 91 bottles of beer!
Take one down, pass it around,
90 bottles of beer on the wall!

90 bottles of beer on the wall, 90 bottles of beer!
Take one down, pass it around,
89 bottles of beer on the wall!

89 bottles of beer on the wall, 89 bottles of beer!
Take one down, pass it around,
88 bottles of beer on the wall!

88 bottles of beer on the wall, 88 bottles of beer!
Take one down, pass it around,
87 bottles of beer on the wall!

87 bottles of beer on the wall, 87 bottles of beer!
Take one down, pass it around,
86 bottles of beer on the wall!

86 bottles of beer on the wall, 86 bottles of beer!
Take one down, pass it around,
85 bottles of beer on the wall!

85 bottles of beer on the wall, 85 bottles of beer!
Take one down, pass it around,
84 bottles of beer on the wall!

84 bottles of beer on the wall, 84 bottles of beer!
Take one down, pass it around,
83 bottles of beer on the wall!

83 bottles of beer on the wall, 83 bottles of beer!
Take one down, pass it around,
82 bottles of beer on the wall!

82 bottles of beer on the wall, 82 bottles of beer!
Take one down, pass it around,
81 bottles of beer on the wall!

81 bottles of beer on the wall, 81 bottles of beer!
Take one down, pass it around,
80 bottles of beer on the wall!

80 bottles of beer on the wall, 80 bottles of beer!
Take one down, pass it around,
79 bottles of beer on the wall!

79 bottles of beer on the wall, 79 bottles of beer!
Take one down, pass it around,
78 bottles of beer on the wall!

78 bottles of beer on the wall, 78 bottles of beer!
Take one down, pass it around,
77 bottles of beer on the wall!

77 bottles of beer on the wall, 77 bottles of beer!
Take one down, pass it around,
76 bottles of beer on the wall!

76 bottles of beer on the wall, 76 bottles of beer!
Take one down, pass it around,
75 bottles of beer on the wall!

75 bottles of beer on the wall, 75 bottles of beer!
Take one down, pass it around,
74 bottles of beer on the wall!

74 bottles of beer on the wall, 74 bottles of beer!
Take one down, pass it around,
73 bottles of beer on the wall!

73 bottles of beer on the wall, 73 bottles of beer!
Take one down, pass it around,
72 bottles of beer on the wall!

72 bottles of beer on the wall, 72 bottles of beer!
Take one down, pass it around,
71 bottles of beer on the wall!

71 bottles of beer on the wall, 71 bottles of beer!
Take one down, pass it around,
70 bottles of beer on the wall!

70 bottles of beer on the wall, 70 bottles of beer!
Take one down, pass it around,
69 bottles of beer on the wall!

69 bottles of beer on the wall, 69 bottles of beer!
Take one down, pass it around,
68 bottles of beer on the wall!

68 bottles of beer on the wall, 68 bottles of beer!
Take one down, pass it around,
67 bottles of beer on the wall!

67 bottles of beer on the wall, 67 bottles of beer!
Take one down, pass it around,
66 bottles of beer on the wall!

66 bottles of beer on the wall, 66 bottles of beer!
Take one down, pass it around,
65 bottles of beer on the wall!

65 bottles of beer on the wall, 65 bottles of beer!
Take one down, pass it around,
64 bottles of beer on the wall!

64 bottles of beer on the wall, 64 bottles of beer!
Take one down, pass it around,
63 bottles of beer on the wall!

63 bottles of beer on the wall, 63 bottles of beer!
Take one down, pass it around,
62 bottles of beer on the wall!

62 bottles of beer on the wall, 62 bottles of beer!
Take one down, pass it around,
61 bottles of beer on the wall!

61 bottles of beer on the wall, 61 bottles of beer!
Take one down, pass it around,
60 bottles of beer on the wall!

60 bottles of beer on the wall, 60 bottles of beer!
Take one down, pass it around,
59 bottles of beer on the wall!

59 bottles of beer on the wall, 59 bottles of beer!
Take one down, pass it around,
58 bottles of beer on the wall!

58 bottles of beer on the wall, 58 bottles of beer!
Take one down, pass it around,
57 bottles of beer on the wall!

57 bottles of beer on the wall, 57 bottles of beer!
Take one down, pass it around,
56 bottles of beer on the wall!

56 bottles of beer on the wall, 56 bottles of beer!
Take one down, pass it around,
55 bottles of beer on the wall!

55 bottles of beer on the wall, 55 bottles of beer!
Take one down, pass it around,
54 bottles of beer on the wall!

54 bottles of beer on the wall, 54 bottles of beer!
Take one down, pass it around,
53 bottles of beer on the wall!

53 bottles of beer on the wall, 53 bottles of beer!
Take one down, pass it around,
52 bottles of beer on the wall!

52 bottles of beer on the wall, 52 bottles of beer!
Take one down, pass it around,
51 bottles of beer on the wall!

51 bottles of beer on the wall, 51 bottles of beer!
Take one down, pass it around,
50 bottles of beer on the wall!

50 bottles of beer on the wall, 50 bottles of beer!
Take one down, pass it around,
49 bottles of beer on the wall!

49 bottles of beer on the wall, 49 bottles of beer!
Take one down, pass it around,
48 bottles of beer on the wall!

48 bottles of beer on the wall, 48 bottles of beer!
Take one down, pass it around,
47 bottles of beer on the wall!

47 bottles of beer on the wall, 47 bottles of beer!
Take one down, pass it around,
46 bottles of beer on the wall!

46 bottles of beer on the wall, 46 bottles of beer!
Take one down, pass it around,
45 bottles of beer on the wall!

45 bottles of beer on the wall, 45 bottles of beer!
Take one down, pass it around,
44 bottles of beer on the wall!

44 bottles of beer on the wall, 44 bottles of beer!
Take one down, pass it around,
43 bottles of beer on the wall!

43 bottles of beer on the wall, 43 bottles of beer!
Take one down, pass it around,
42 bottles of beer on the wall!

42 bottles of beer on the wall, 42 bottles of beer!
Take one down, pass it around,
41 bottles of beer on the wall!

41 bottles of beer on the wall, 41 bottles of beer!
Take one down, pass it around,
40 bottles of beer on the wall!

40 bottles of beer on the wall, 40 bottles of beer!
Take one down, pass it around,
39 bottles of beer on the wall!

39 bottles of beer on the wall, 39 bottles of beer!
Take one down, pass it around,
38 bottles of beer on the wall!

38 bottles of beer on the wall, 38 bottles of beer!
Take one down, pass it around,
37 bottles of beer on the wall!

37 bottles of beer on the wall, 37 bottles of beer!
Take one down, pass it around,
36 bottles of beer on the wall!

36 bottles of beer on the wall, 36 bottles of beer!
Take one down, pass it around,
35 bottles of beer on the wall!

35 bottles of beer on the wall, 35 bottles of beer!
Take one down, pass it around,
34 bottles of beer on the wall!

34 bottles of beer on the wall, 34 bottles of beer!
Take one down, pass it around,
33 bottles of beer on the wall!

33 bottles of beer on the wall, 33 bottles of beer!
Take one down, pass it around,
32 bottles of beer on the wall!

32 bottles of beer on the wall, 32 bottles of beer!
Take one down, pass it around,
31 bottles of beer on the wall!

31 bottles of beer on the wall, 31 bottles of beer!
Take one down, pass it around,
30 bottles of beer on the wall!

30 bottles of beer on the wall, 30 bottles of beer!
Take one down, pass it around,
29 bottles of beer on the wall!

29 bottles of beer on the wall, 29 bottles of beer!
Take one down, pass it around,
28 bottles of beer on the wall!

28 bottles of beer on the wall, 28 bottles of beer!
Take one down, pass it around,
27 bottles of beer on the wall!

27 bottles of beer on the wall, 27 bottles of beer!
Take one down, pass it around,
26 bottles of beer on the wall!

26 bottles of beer on the wall, 26 bottles of beer!
Take one down, pass it around,
25 bottles of beer on the wall!

25 bottles of beer on the wall, 25 bottles of beer!
Take one down, pass it around,
24 bottles of beer on the wall!

24 bottles of beer on the wall, 24 bottles of beer!
Take one down, pass it around,
23 bottles of beer on the wall!

23 bottles of beer on the wall, 23 bottles of beer!
Take one down, pass it around,
22 bottles of beer on the wall!

22 bottles of beer on the wall, 22 bottles of beer!
Take one down, pass it around,
21 bottles of beer on the wall!

21 bottles of beer on the wall, 21 bottles of beer!
Take one down, pass it around,
20 bottles of beer on the wall!

20 bottles of beer on the wall, 20 bottles of beer!
Take one down, pass it around,
19 bottles of beer on the wall!

19 bottles of beer on the wall, 19 bottles of beer!
Take one down, pass it around,
18 bottles of beer on the wall!

18 bottles of beer on the wall, 18 bottles of beer!
Take one down, pass it around,
17 bottles of beer on the wall!

17 bottles of beer on the wall, 17 bottles of beer!
Take one down, pass it around,
16 bottles of beer on the wall!

16 bottles of beer on the wall, 16 bottles of beer!
Take one down, pass it around,
15 bottles of beer on the wall!

15 bottles of beer on the wall, 15 bottles of beer!
Take one down, pass it around,
14 bottles of beer on the wall!

14 bottles of beer on the wall, 14 bottles of beer!
Take one down, pass it around,
13 bottles of beer on the wall!

13 bottles of beer on the wall, 13 bottles of beer!
Take one down, pass it around,
12 bottles of beer on the wall!

12 bottles of beer on the wall, 12 bottles of beer!
Take one down, pass it around,
11 bottles of beer on the wall!

11 bottles of beer on the wall, 11 bottles of beer!
Take one down, pass it around,
10 bottles of beer on the wall!

10 bottles of beer on the wall, 10 bottles of beer!
Take one down, pass it around,
9 bottles of beer on the wall!

9 bottles of beer on the wall, 9 bottles of beer!
Take one down, pass it around,
8 bottles of beer on the wall!

8 bottles of beer on the wall, 8 bottles of beer!
Take one down, pass it around,
7 bottles of beer on the wall!

7 bottles of beer on the wall, 7 bottles of beer!
Take one down, pass it around,
6 bottles of beer on the wall!

6 bottles of beer on the wall, 6 bottles of beer!
Take one down, pass it around,
5 bottles of beer on the wall!

5 bottles of beer on the wall, 5 bottles of beer!
Take one down, pass it around,
4 bottles of beer on the wall!

4 bottles of beer on the wall, 4 bottles of beer!
Take one down, pass it around,
3 bottles of beer on the wall!

3 bottles of beer on the wall, 3 bottles of beer!
Take one down, pass it around,
2 bottles of beer on the wall!

2 bottles of beer on the wall, 2 bottles of beer!
Take one down, pass it around,
1 bottle of beer on the wall!

1 bottle of beer on the wall, 1 bottle of beer!
Take one down, pass it around,
No bottles of beer on the wall!

```

---

### Post by bousozoku on 2007-12-05
> **LaRoza said:**
> Although Perl has a syntax that allows for unreadable and cryptic code, [http://99-bottles-of-beer.net/language-perl-737.html](http://99-bottles-of-beer.net/language-perl-737.html), it can be well written and is a very good language.

Sure, but Perl is better for someone who already has good habits and Python is better for someone new to programming, as it forces structure.

I've a lot to learn about Linux in the ways it differs from UNIX and other systems, so, thanks for this thread and the related resources.

---

### Post by LaRoza on 2007-12-06
> **bousozoku said:**
> Sure, but Perl is better for someone who already has good habits and Python is better for someone new to programming, as it forces structure.


I am all for learning Python first, but don't want any misrepresentations here.

---

### Post by Vadi on 2007-12-16
I think the package to get KDE4 development files is **kdebase-dev-kde4**.

---

### Post by tr333 on 2007-12-16
For those starting C programming, I suggest you install the 'manpages-dev' package.
```
sudo apt-get install manpages-dev
```

This will give you access to the C man pages. Eg:
```
man 3 printf
man scanf
```

If you can't find the page by doing 'man <function>' then try looking specifically in section 3 of the manual with 'man 3 <function>'.  More details on this with 'man man'.

---

### Post by RIchard James13 on 2007-12-26
Regarding Python and the GUI

When I first got Glade I got version 2 which has a similar interface to the Gimp many windows over the screen. If you go into synaptic you can see that version 3 is available. It is in a single window much better if you are used to other GUI designers.

I first learnt PyGTK with the tutorials here [http://www.pygtk.org/tutorial.html]("http://www.pygtk.org/tutorial.html")

Then I started to use glade as outlined here
[http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/]("http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/")

Finally for an IDE I used Eclipse with the PyDEV plugin. This allows code-autocompletion.
[http://pydev.sourceforge.net/]("http://pydev.sourceforge.net/")

I also have a hardcopy python book but it talks about python 2 begin the new version so it is a bit out of date. You can download a python book from 
[http://www.mindview.net/Books/TIPython]("http://www.mindview.net/Books/TIPython")

However I already know how to program in multiple languages so I found that book a bit easy, the author recommends an easier book in
[http://www.swaroopch.com/byteofpython/]("http://www.swaroopch.com/byteofpython/")

---

### Post by RIchard James13 on 2007-12-26
Regarding KDevelop and Automake

Automake is the set of tools you find in most source code tarballs. The things that let you run ./configure && make && make install.

When using Kdevelop for C/C++ I found that I was always getting problems when I renamed source files or removed them from a project.
```
g++ -O0 -g3 -o clock clock.o clock12hourview.o clockcontroller.o clockmodel.o temp.o -lncurses
make[2]: *** No rule to make target `controller.h', needed by `all-am'.
make[2]: Target `all' not remade because of errors.
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***
```

On the right of Kdevelop is a tab called "Automake Manager"
By using this you can remove the old references from your automake files. In this instance I had to remove controller.h it no longer existed as a file and was referenced by automake still in my project.

```
*** Success ***
```

You can also use Kdevelop to automatically create the automake stuff for your  non-Kdevelop project. Just run Kdevelop, start a new temporary project, add your files to it, change things like what you want installed where(this is a bit limited), then build your project in Kdevelop. This will add all the right m4 automake files to your project so you can run ./configure && make && make install.

If you want a tutorial on how to do this by hand look here
[http://vindaci.members.sonic.net/cbreak/projects/autotools/]("http://vindaci.members.sonic.net/cbreak/projects/autotools/")

---

### Post by Gediminas on 2007-12-29
I recommend to use Notepad++ [Homepage]("http://notepad-plus.sourceforge.net/uk/site.htm") as IDE. It's really great, have a lot of useful functions, like plug-ins, over 40 programming languages syntax highlighting and so on ;)
it's for Windows, but you can run it using Wine, runs without problems ;)

---

### Post by Kadrus on 2007-12-29
> **Gediminas said:**
> I recommend to use Notepad++ [Homepage]("http://notepad-plus.sourceforge.net/uk/site.htm") as IDE. It's really great, have a lot of useful functions, like plug-ins, over 40 programming languages syntax highlighting and so on ;)
it's for Windows, but you can run it using Wine, runs without problems ;)
Gedit has 43 languages syntax highlighting ;)..

---

### Post by TrueDego on 2008-01-02
I used SciTE in windows for programming because it allowed me to run code from within the editor when i was using ruby and I found it to be an excellent program.  Its what I prefer to use.  if you get it, press F8 and it will show code output.  It shows and highlights code syntax and shows you errors.

---

