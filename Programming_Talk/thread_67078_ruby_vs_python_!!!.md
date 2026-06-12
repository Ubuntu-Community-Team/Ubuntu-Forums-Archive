---
title: "ruby vs python !!!"
date: 2005-09-19
forum: Programming Talk
---

### Post by seiflotfy on 2005-09-19
hi guys!!! since i dont have an idea of both i would liek to have ur opinion on these programing languages!! which one is similar to C/c++ sicne thqats what i can program with!!!

---

### Post by mostwanted on 2005-09-19
Neither of them are similar to C++ in syntax, they're both similar to each other though.

I would go with Ruby because that's personally the one I want to learn of the two (I know neither). Also, the coolest programming guide is for Ruby:

[http://www.poignantguide.net/ruby/](http://www.poignantguide.net/ruby/)

---

### Post by SilentCacophony on 2005-09-19
Personally, I decided to learn Python after looking at the alternatives. One of the reasons I chose it is that Ubuntu seems to have a focus on it, as outlined [on this page](http://www.ubuntu.com/community/bounties/view?searchterm=python).

If you haven't seen it, there is a guide that is often recommended as a first read called [Dive Into Python](http://diveintopython.org/), which can be downloaded from there, or can also be found in Ubuntu.

I have not studied Ruby in-depth, but it seems a bit more complex and object-oriented than Python, while Python is a mix of procedural and object-oriented, generally allowing either approach to most tasks.

---

### Post by skoal on 2005-09-19
Oh man, I wish my good buddy from another distro were here to weigh in on this.  He preaches Ruby sermons daily from his blog altar.  He recently has been dabbling in Python (like myself), but still prefers Ruby overall, especially in web development.

I trust his profound intelligence and wisdom and simply reiterate his overall generalization here (as I understand it): Ruby is easier to learn than Python, and is a much more "pure" OO environment along the lines of Smalltalk...

\\//_

---

### Post by DancingSun on 2005-09-19
I chose Ruby myself, mainly because it is very simple to use.

It should be noted that Ruby can also be used in a more procedural way.  Actually, much of the Classes in Ruby have a whole lot of Class methods (versus Instance methods), and this allows you to use Ruby in a more procedural style if you wish.

For, an hypothetical, example:
The following uses the Class method "print" in a Class called "String" which takes a string and prints it.  This is the procedural way.
```
String::print(aString)
```
While this example uses the string object's instance variable and calls a print method on that object. This is the object oriented way.
```
aString.print
```

However, if you follow the object oriented approach, you'll find Ruby to be much more consistence to use, and that just simplifies a lot of the stuff that will need "special handling" when done in the procedural way.

On a side note, if Squeak Smalltalk were to interact better and more easily with the rest of the environment (OS) I would probably choose it over Ruby, as the design of Smalltalk is just really clean and much more elegant in comparison to Ruby (and, in my opinion, Ruby is much more elegant than Python).  Smalltalk probably won't earn you money directly, but it certainly helps to be enlightened on what the *original *object oriented programming language is like (Smalltalk is the first Object Oriented Language).

Correction:  Simula 67 is the first Object Oriented Programming Language, not Smalltalk.  The term "Object Oriented Programming" was coined by Alan Kay, the person that invented Smalltalk.  So the term OOP was first used in Smalltalk, but the concept did not originate from Smalltalk.  Nonetheless, Smalltalk's design is of pure OOP, the syntax is really clean and simple, and not mixed in with procedural or other paradigms, so it's a good language to get a grip with what OOP is like.

---

### Post by mostwanted on 2005-09-19
No, Simula was the first OO language.

---

### Post by DancingSun on 2005-09-19
[QUOTE=mostwanted]No, Simula was the first OO language.[/QUOTE]
My apologies.  Simula is the first that introduced the paradigm of OO programming.  But the term wasn't coined until Alan Kay and his Smalltalk.

---

### Post by wtd on 2005-09-19
[QUOTE=DancingSun]```
String::print(aString)
```
While this example uses the string object's instance variable and calls a print method on that object. This is the object oriented way.
```
aString.print
```[/QUOTE]


Considering that neither of those actually works, you may want to use the much simpler:

```
print aString
```

---

### Post by floppy on 2005-09-19
wtd,
I believe he was illustrating a point about syntax, not suggesting actual code to try.

---

### Post by LordHunter317 on 2005-09-19
With a newbie to any lggnauge, it's extremely imperative to make sure examples are valid.

---

### Post by DancingSun on 2005-09-19
[QUOTE=wtd]Considering that neither of those actually works, you may want to use the much simpler:

```
print aString
```[/QUOTE]
It's a hypothetical example.  I edited the post to point that out.  Sorry for your confusion.

---

### Post by cwaldbieser on 2005-09-20
[QUOTE=seiflotfy]hi guys!!! since i dont have an idea of both i would liek to have ur opinion on these programing languages!! which one is similar to C/c++ sicne thqats what i can program with!!![/QUOTE]
Vi!  Wait, no, emacs!  Or are we doing Gnome vs. KDE?  Just kidding.

I like Python better, probably for no better reason than I got into Python first.  The Unix fortune program says it best:

"Ultimately, we all like what we like and just make up the reasons why."

---

### Post by thumper on 2005-09-20
[QUOTE=cwaldbieser]"Ultimately, we all like what we like and just make up the reasons why."[/QUOTE]
Hear, hear!! 

Python for me.  Probably because I learnt it before Ruby.

---

### Post by cactus on 2005-09-22
ruby!
/me waves at skoal

---

### Post by jerome bettis on 2005-09-22
python gets my vote not necessarily because it's a 'better' language, but because there's more stuff for it. by stuff i mean modules, and stuff you can find on google about how to use said modules. if ruby really catches on (it should it's nicer than python in a lot of ways) i would expect more stuff to show up for it.

ruby is a clean OO model, a lot like java, which is both good and bad depeneding on what you're doing. if i just need a procedural program (shell script etc) i don't need classes and such in the mix. but if i've got objects all over the place, python doesn't even really have private methods, which to me is BS. also python doesn't have the ternary operator which i know you all hate, but i love it. especially nested. :-P  does ruby have that?

---

### Post by skoal on 2005-09-22
[QUOTE=cacti]ruby!
/me waves at skoal[/QUOTE]
Holy smokes! Good to see ya, brother.

ruby? I concur.  However, I really don't know squat even about ruby squat.  What is squat anyways? A vegetable?

Jerome, a module repo was actually one feature about CPAN (and perl) which prolonged my migration to Python (initially).  I know Python has [this](http://docs.python.org/modindex.html) now. I haven't dug around enough yet to find such a thing for Ruby... 

\\//_

---

### Post by seiflotfy on 2005-09-22
well i think i will go with python frist!!!
it sound more interessting!!! i dont really need ruby i think i can do enough with c/c++ and java as OO languages!!!

---

### Post by DancingSun on 2005-09-22
[QUOTE=skoal]Holy smokes! Good to see ya, brother.

ruby? I concur.  However, I really don't know squat even about ruby squat.  What is squat anyways? A vegetable?

Jerome, a module repo was actually one feature about CPAN (and perl) which prolonged my migration to Python (initially).  I know Python has [this](http://docs.python.org/modindex.html) now. I haven't dug around enough yet to find such a thing for Ruby... 

\\//_[/QUOTE]
Try [RubyGems](http://docs.rubygems.org/) for Ruby.

---

### Post by wtd on 2005-09-23
[QUOTE=jerome bettis]if i just need a procedural program (shell script etc) i don't need classes and such in the mix[/QUOTE]

Ruby is perfectly capable of being used in this way.

---

