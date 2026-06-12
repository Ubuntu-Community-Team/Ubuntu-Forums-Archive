---
title: "Human Readable programming language"
date: 2007-01-30
forum: Programming Talk
---

### Post by jpeddicord on 2007-01-30
Back around September I started a project. The one goal was to make a full programming language based on English. Essentially, the code will look somewhat like this:```
if the variable 'counter' is greater than 5 then
show a message titled 'Greater than 5' with the text 'It is greater than 5!'
if not then
end the program
end if
```The project is called Legicode, and the site is currently at [http://legicode.com](http://legicode.com). You can read up on some of the goals there, however not much info has been posted yet.


Code can be shorthanded, as to ease users into better, more compact code. The above can be shorthanded down to:```
if counter > 5 then
  show message "It is greater than 5!"
else
  end
```

First off: Progress *has* started in terms of programming. I plan on making this program cross-platform. The license is still undecided, however I do have some plans in mind.

I am looking for suggestions for parsing this chunk of code into machine/OS readable code.
Here are possible options:
[LIST]
[*]Use a lexer, directly compile the code and use a VM runtime embedded into the program (Advantages: Fast code output, quick runtimes, Disadvantages: Slow releases, embedded runtime needed)
[*]Convert to C++ (Advantages: Quick releases, no runtimes, Disadvantages: Slow parsing of code, must be passed to GCC to be compiled)
[*]Convert to Assembler (Advantages: Quick releases, no runtimes, faster even than C++, Disadvantages: Slow parsing of code, must be passed to asm compiler)
[/LIST]

Some questions:
[LIST=1]
[*]Does this project sound interesting at all to you? Would you use it? Do you think it would be able to attract even newbies?
[*]Which of the above three methods should I take for parsing the code into machine output?
[/LIST]

Let me know what everyone thinks!
Jacob

---

### Post by lloyd mcclendon on 2007-01-31
i think it's very cool.  you could teach 3rd graders this and they would be able to understand.

i don't think cpu speed is a concern, developing any kind of project with this will take a lot of time just from all the typing.  i wouldn't use it at all for any type of real world app, but as an instructional tool i think it's very innovative.  

i'd generate a lexer and parser using jlex and jcup, and then implement your semantic analysis and type checking.  for code generation it would probably be easiest at that point to go directly to asm, since you already have a fine grained view of the ast.  don't try to do the whole language at once, get the root node working from end to end, and add new constructs one by one.

instead of the endif, i'd use forced indentation like python.  the program shouldn't compile unless the structure, punctuation, and spelling is correct.  how about an editor with code completion to make it easier to learn?

---

### Post by Wybiral on 2007-01-31
Sounds like it would make for a pretty cool learning tool. People could learn to get used to using the rules of a programming languages, without having to use such a format syntax. Afterwards it might make it easier for them to learn a more formal programming language.

Best of luck!

EDIT:

Also, if you want any help, I'd be willing to pitch in. I know a lot about the linux elf executable format and assembly so I can probably help write that portion of the compiler (however I don't know much about l windows exe format to help with that side of it). So yeah, PM/Email me if you're interested.

Another thing... The "end if" stuff does sound a little too computery... Perhaps as lloyd mcclendon mentioned, a pythonic approach of using indentations might be a good idea.

---

### Post by jpeddicord on 2007-01-31
Yeah, the endif has been bugging me. I suppose that indentation shouldn't be too bad.

Wybiral: I haven't thought about having any additional developers on the project yet. Once the main codebase is started, I think I'll open it up for more development. :)

---

### Post by tzulberti on 2007-01-31
> **jacobmp92 said:**
> 

Some questions:
[LIST=1]
[*]Does this project sound interesting at all to you? Would you use it? Do you think it would be able to attract even newbies?
[*]Which of the above three methods should I take for parsing the code into machine output?
[/LIST]

Let me know what everyone thinks!
Jacob

1) I don't think that is a good idea to create such a code, because i think that i wouldn't have much support from the programming comunity. I thinl that the newvies would prefer python, which is very easy to use and have lots of docs

2) That depends. If you try to make it work in Windows, it will go for the VM

---

### Post by lnostdal on 2007-01-31
> **jacobmp92 said:**
> ```
if the variable 'counter' is greater than 5 then
show a message titled 'Greater than 5' with the text 'It is greater than 5!'
if not then
end the program
end if
```

..that does not add anything besides verbosity. Compare it with some regular programming languages:

```

(if (> counter 5)
    (showMessage :title "Greater than 5" :text "It is greater than 5!")
    (exitProgram))

```

..or..

```

if(counter > 5)
  showMessage("Greater than 5", "It is greater than 5!");
else
  exitProgram();

```

What's the real difference? The only difference I see is the increased verbosity adding nothing which will be a negative thing very, very soon - even for newbies.

---

### Post by slavik on 2007-01-31
are you writing a second version of COBOL? :P

IMO, writing languages which are very readable by people is difficult because of the way you might allow coders to arrange things.

---

### Post by Tomosaur on 2007-01-31
I like it, it could definately be used as a more 'accessible' introduction to programming languages - Python springs to mind here. It looks like it'll have a nice, clean, logical structure, and although it's more verbose than 'normal' languages, it's not too esoteric.

---

### Post by Steveire on 2007-01-31
No matter how easy you make your code, it's still code.

I don't think it's a good tool to learn programming. For one thing, it seems like it would be very boring, and use a lot of unneeded words.

```

Go to the door and open the door and walk through the door and shut the door

```
etc.

The only thing it may teach is how logic works, but there are far better ways of teaching logic to students.

---

### Post by yaaarrrgg on 2007-01-31
As a challenge, you might try to write the parser so that it can accept a range of mathematical "story problems."  Also, you might make it pre-compile to prolog...

---

### Post by jblebrun on 2007-01-31
Others here have already hinted at one of the big problems of a project like this. Re-writing existing code structures using verbose, English-like sentences will provide very little gain. 

The English language is a very flexible language, and full of opportunities for ambiguity. Even completely ignoring the problems of contextual ambiguity and learned implications, you'd still need to have a parser that can understand a variety of sentence structures for this to be possible. 

I can see a language like this actually frustrating a newbie more than helping him or her. It will present the illusion of a flexible human-language-based parser, but it's undoubtedly going to be constrained by the same rules that already constrain programming languages. The rigidity of programming language syntax is still a very important concept to become aware of, and comfortable with. A language like this detracts from that.

I can see where this might have some direction as a purely pedagogical tool (or perhaps a technical writing trainer...teehee) but it wouldn't make a good starting point for a blossoming programmer, at least not in our current environment of languages and programming paradigms.

---

### Post by jblebrun on 2007-01-31
By the way, in no way am I suggesting that you abandon this thread of thinking! I think you should continue to work on your project, but I think that questions like the one you present in the poll are somewhat misguided.

Assuming you could make a natural language parser with enough flexibility to make it non-trivial (so that you're not just replicating the (strict) syntax of a programming language using different words and symbols), perhaps having the natural language translated into a pure language like Python (which is still fairly n00b-friendly) would be a good idea. This would help a beginner see the connections between natural language and programming language, and also learn how ambiguities in natural language must be resolved in programming languages.

---

### Post by Wybiral on 2007-01-31
Yes, it would probably be more educational if it translated to a variety of languages.

Python, C, C++, Assembly

Perhaps they could learn from the parallel.

---

### Post by ssam on 2007-01-31
you might want to look at some [apple script ]("http://en.wikipedia.org/wiki/Applescript") code. that is pretty close to english.

---

### Post by jpeddicord on 2007-01-31
Looks like I missed something in the description - the code can be shorthanded, as far down to the level of Basic or Python. I am intending for it to be flexible, so once someone is able to code, they can gradually ease into more compact code.

Essentially, the above code could be shortened to: ```
if counter > 5 then
  show message "It is greater than 5!"
else
  end
```

And I agree, this language will not have much usefulness in actual programming, but more simply as a way for newbie programmers to get started.

Take a look at the software Game Maker ([http://gamemaker.nl](http://gamemaker.nl)). It is windows and proprietary, but the code structure is very easy to use. Code can even be edited in a drag-and-drop style method. The target audience will be that same group of people.

As for AppleScript, yes, it could look similar to that.

This whole project is more of a personal thing for me to work on when bored, withering away my time. It's a personal goal to finish it and to release it, even if it won't be widely used. I have a  lot more fun programming it than I will releasing/marketing it. :)

---

### Post by Klipt on 2007-02-01
As slavik mentioned, they tried that with Cobol so managers could read it (code along the lines of "take 10 percent of earnings and give the manager a fat bonus" or something...)

Programming requires thinking in a certain way - anyone who can think this way will probably prefer to express themselves concisely. Anyone who can't (yet) will probably end up telling the computer the wrong thing, even in English.

For it to be computer readable you'd have to impose so many rules on what people can write. It's just easier to use more mathematical notation IMO. Or if you have to use a language, use lojban :-P

---

### Post by 3rdalbum on 2007-02-01
Sorry, you've been beaten to it by 20 years!

Hypercard was the world's first multimedia authoring program, released by Apple in the late 80s. It uses point-and-click to create the actual visuals, like a painting program crossed with Glade or Visual Basic. The language is Hypertalk, which bears a lot of resemblence to your language. You can even use it non-verbosely. And it was VERY popular, partly because the language was easy to write in and understand.

Macromedia had a very similar system with Director (the language was called Lingo), but now they encourage the use of the non-verbose version.

You can download a trial version of Runtime Revolution for Linux, Mac or Windows, which will let you experience a slightly-modified version of Hypertalk.

---

### Post by jpeddicord on 2007-02-01
> **3rdalbum said:**
> Sorry, you've been beaten to it by 20 years!

Hypercard was the world's first multimedia authoring program, released by Apple in the late 80s. It uses point-and-click to create the actual visuals, like a painting program crossed with Glade or Visual Basic. The language is Hypertalk, which bears a lot of resemblence to your language. You can even use it non-verbosely. And it was VERY popular, partly because the language was easy to write in and understand.

Macromedia had a very similar system with Director (the language was called Lingo), but now they encourage the use of the non-verbose version.

You can download a trial version of Runtime Revolution for Linux, Mac or Windows, which will let you experience a slightly-modified version of Hypertalk.
Maybe I'll get the edge of having this as a GPL program. ;)
Oh yeah.

---

### Post by Xanderfoxx on 2008-12-23
Although I recently came up with a similar idea, I would NEVER use English.  First of all, I would use a Logical Constructed Langauge with EXPLICIT PHONOLOGY (meaning  programmatical syntax is clearly verbalized), it performs as a dual conlang & multiparadigm programming language, with excellent support for logical and OOP paradigms, although functional and other paradigms are fully supported via a Mode Code in a Context Header (which has specialized syntax and is clearly detected with a small-memory-footprint combination speech-2-text + interpreter (which interprets the constructed language during (verbal) dictation (via a small-footprint voice activation engine than plugs-in as a runtime module into this interpreter to input script), interpreting into a non-executable object code (simplifying concise verbal logic constructs into standard syntactic shorthand), which would then JIT-compile to a selection of final languages, such as Python, Java, Delphi, C/C++, or Assembly.

---

### Post by dperfors on 2008-12-23
It doesn't seem to be very usefull to me, because with a language like smalltalk you can almost do the same:

```
x := 0.
[ (x < 10) ] 
whileTrue: [Transcript show: (x) printString.
            Transcript show: ' '.
            x := x + 1.].


0 1 2 3 4 5 6 7 8 9 

```Yes there is some extra's that are not in the English language, and the gramatic is not always the same, but that is something you can hardly avoid...

---

