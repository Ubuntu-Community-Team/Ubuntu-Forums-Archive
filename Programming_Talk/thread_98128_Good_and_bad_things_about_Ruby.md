---
title: "Good and bad things about Ruby"
date: 2005-12-02
forum: Programming Talk
---

### Post by commodore on 2005-12-02
I don't hear too much about ruby. I'm quite interested in the language, but I don't know anything about it. Could someone tell me what's better and worse in Ruby then in other languages?

I don't know what's wrong with me, but all the languages I like are scripting languages :S (python, perl, ruby) :D

---

### Post by Buchuki on 2005-12-02
[QUOTE=commodore]I don't know what's wrong with me, but all the languages I like are scripting languages :S (python, perl, ruby) :D[/QUOTE]

Nothing wrong with you, it just means you're concerned about being an efficient programmer. ;-)

Dusty

---

### Post by cactus on 2005-12-02
I personally believe that ruby and python have many similarities. The only *real* difference would be one of syntax, library size (getting closer), and a bit of structure. 

Ruby tends to be used in a more object oriented fashion (although that is not required), while I often see functional python (again, not required).

Python has more libraries, but I prefer the ones ruby has.

*bias warning*
I prefer the Ruby language syntax, as well as the ruby constructs (code blocks and lamdas). I dislike certain things in python..which I wont get into here.

I suggest you try them both, and see which one you prefer.

As for other languages, I think both ruby and python blow many out of the water. You can be more productive, and have more fun, using these languages. There is a place for compiled languages, but for nearly everything I do..I dont really need it.

Just bash, ruby, and python for me. :)

---

### Post by PizzAp on 2005-12-02
I really like ruby and would prefer it above python and perl.

Sorry for ranting, but python is in my opinion only a kind of constrained perl.
(I have seen beautiful python code once though, i think it was the wikipedia fs.)

The thing is, perl has lots of awkward constructs, the whole object oriented programming model is kind of a hack. 
Pythons oop is better, but the syntax still looks like c. Both python and perl have somewhat strange looking code, perl has lots of funny  $,@,%-> characters and python lacks explicit block markers and overuses ':'.

Ruby on the other hand is not as mature as perl or python, but is more aesthetic. 
The version numbers seem to correlate well with maturity and number of 3rd party modules.

Check out the ruby gnome bindings, they are very nice.

---

### Post by commodore on 2005-12-03
So, the next language I'll learn is probably ruby.

And I'm not concerned about being an officient programmer.

---

### Post by commodore on 2005-12-03
Basicly ruby is like perl?

---

### Post by mostwanted on 2005-12-03
[http://www.ruby-lang.org/en/](http://www.ruby-lang.org/en/)
[http://poignantguide.net/ruby/](http://poignantguide.net/ruby/)
[http://tryruby.hobix.com/](http://tryruby.hobix.com/)

The two lower links are particularly cool. The Poignant Guide to Ruby should teach you what exactly makes Ruby so cool, the Try Ruby thing is just an awesome way of testing out Ruby on the Internet.

---

### Post by commodore on 2005-12-03
Mostwanted, those links are the best!

---

### Post by LordHunter317 on 2005-12-03
[QUOTE=PizzAp]Pythons oop is better, but the syntax still looks like c.[/quote]Python OOP looks nothing like C, or C++, or Java or C#, or pretty much any other Algol derivative.

---

### Post by majikstreet on 2005-12-03
also [http://www.rubycentral.com/book/](http://www.rubycentral.com/book/) is nice... I don't program ruby- I was thinking about it so I was reading that one and the Poigant one-- FOXES!

---

### Post by PizzAp on 2005-12-03
[QUOTE=LordHunter317]Python OOP looks nothing like C, or C++, or Java or C#, or pretty much any other Algol derivative.[/QUOTE]
Of course not, but imho there are similarities.

Python:
```

class _NamespaceMap:
    def __init__(self):              # self in constructors parameters
        self._nsID = 0              # self again
        self.array = [1, 2, 3]     # no constructor for array creation
        self.length = len(self.array)  # function instead of array method


```

Oop in C:
```

void
vte_terminal_feed(VteTerminal *terminal, const char *data, glong length)
{
    if (length == ((gssize)-1)) {
        length = strlen(data);
    }
    terminal->pvt->length = length;
    vte_terminal_start_processing (terminal);
}


```

I have to admit python code is really compact though.

---

### Post by lcg on 2005-12-03
[QUOTE=PizzAp]I have to admit python code is really compact though.[/QUOTE]
Not to mention it is unreadable and has semantics which are determined by the syntax (indentation). [-(
IMO, the latter is a really bad idea.

Lars

---

### Post by gord on 2005-12-03
the indentation of python is one of its greatest atrabutes, its code is clean, readable (as long as you use python as a language yourself.. not much use in just taking a peek and going blah) and the best thing, everyones code looks similar! you can quickly and easly figure out what someone else has been doing in their code and everything gets sped up as a consiquinse.

n i guess python code looks compact because it doesn't need to be all over the place; if you want to decide whats best to use, i would open up python and type 

```
 import this 
```

its a little easter egg with the 'zen' of python, if you agree with what it says then id say python is for you, else you should think of using something like ruby.

---

### Post by PizzAp on 2005-12-03
[QUOTE=gord]the indentation of python is one of its greatest atrabutes, its code is clean, readable (as long as you use python as a language yourself.. not much use in just taking a peek and going blah) and the best thing, everyones code looks similar! you can quickly and easly figure out what someone else has been doing in their code and everything gets sped up as a consiquinse.
[/QUOTE]

Everybody should program what they like most. :)

I did a few thousands lines in python and i've reached a point where i don't want to touch python anymore.
One of the reasons may be the large number of python newbies, some write very interesting stuff, but then lots of it is just badly coded or incomplete imho. 
So python code is not equal python code regarding readability.

For the indentation, as i said in my first post, i like my blocks starting and ending with a keyword. (btw, ever had to fix a python prog with broken tabs/whitespaces ?)
Ah well, i really like code that's more verbose and closer to language, makes me go faster in analyzing it.

---

### Post by cactus on 2005-12-03
[QUOTE=PizzAp]btw, ever had to fix a python prog with broken tabs/whitespaces ?[/QUOTE]
yes. Bad bad bad bad...
Even worse.. coding with another person, who ascribes to a different "spaces vs tabs" ideology..
*queue explosion sounds*

---

### Post by LordHunter317 on 2005-12-03
[QUOTE=gord]the indentation of python is one of its greatest atrabutes, its code is clean, readable (as long as you use python as a language yourself.. not much use in just taking a peek and going blah)[/quote]Both of these are subjective and I don't especially find python code clean and readable.  With the example above, it's hard to tell where one logical block begins or ends, unless you're very careful with your vertical spacing.

>  you can quickly and easly figure out what someone else has been doing in their code and everything gets sped up as a consiquinse.Formatting is rarely a huge impedance to understanding and reformatting is so trivial I don't buy this line of reasoning.

Moreover, it's too easy to break python when you're working with a multi-platform development team and not everyone's careful about making sure newlines are checked in correctly, or more often, CVS breaks and helps you by screwing them up.

---

### Post by gord on 2005-12-03
python is only going to be accepting spaces for indentation soon enough, so that clears up a lot of issues. 

and yes python can be hard to read when its presented without a good editor, but python also happens to have good editors around that are very free. colour coding goes a long way. i should also re-itterate the fact that no language will look clean and readable unless you use it yourself, for example java to me is a mess, nothing is right about it but a lot of people swear by it, they use it, i don't. 

i think this whole route the thread is going down is silly though, python is a good programing language else people wouldn't use/love it and so is ruby for the same reasons. the arguments for either side seems is more of a:

kida: "my ball is better because its red!"
kidb: "well my ball is better because its blue!" 

kind of situation. which is why i suggest reading the zen of python(i don't know of there is a zen of ruby or whatever). also trying both out is a good thing.

---

### Post by LordHunter317 on 2005-12-03
[QUOTE=gord]python is only going to be accepting spaces for indentation soon enough, so that clears up a lot of issues.[/quote]Not the ones I mentioned.

> i should also re-itterate the fact that no language will look clean and readable unless you use it yourself,That's not really true.  If you know the syntax for C, you can read most Algol derviatives.  LISP yields to scheme and a few other functional languages that are similiar.

> i think this whole route the thread is going down is silly though, python is a good programing language else people wouldn't use/love it and so is ruby for the same reasons.That's not really true.  Popularity has nothing to do with how "good" a language is outside the F/OSS community, really.   People don't write Java because they thing it's a good language or the JCL is nice.  They write it because they must.

---

### Post by gord on 2005-12-03
[QUOTE=LordHunter317]Not the ones I mentioned.[/QUOTE] i wasn't replying to you specifically

[QUOTE=LordHunter317]That's not really true.  If you know the syntax for C, you can read most Algol derviatives.  LISP yields to scheme and a few other functional languages that are similiar.[/QUOTE]
the words to focus on here are 'if you know the syntax' and 'scheme' and 'similar' 

[QUOTE=LordHunter317]That's not really true.  Popularity has nothing to do with how "good" a language is outside the F/OSS community, really.   People don't write Java because they thing it's a good language or the JCL is nice.  They write it because they must.[/QUOTE]

sure they do but that is aside from the point that i was making, there arn't many python jobs and there arn't many ruby jobs, if people are gonna use them there must be a reason behind that, ie; they chose to use them. thus you could logically conclude from that, that they are reasonably good languages.


now i don't want to go down a road where after i post someone takes apart every little thing i said looking for anything that they don't agree with, its not fun.

if you don't like python thats fine, but i think you should except the fact that others do. i personally don't like ruby but others do, and thats fine. i don't use ruby so there is prolly something that that iv not discovered that others have.

---

### Post by LordHunter317 on 2005-12-03
> **gord]i wasn't replying to you specifically[/quote]So?  You're not free to say, "The forced formatting isn't an issue," when someone raises a legitimate complaint.  That's handwaving.


> the words to focus on here are 'if you know the syntax' and 'scheme' and 'similar' :rolleyes:  This reply is a non-sequitur.  You've provided no valid reason why someone familiar with say Java, shouldn't be able to read most C# without any issues.

> sure they do but that is aside from the point that i was making,How is it aside at all?  You essentially made the claim, "Python's a good language because it's popular."  I point out that the really popular languages aren't necessarily good languages at all, no matter what measuring stick you use.  See COBAL, RPG, and Java for great examples.

> if people are gonna use them there must be a reason behind that, ie said:**
> No, that's not true.  I choose to use PERL when it's best suited to my task, but PERL is still an absolutely terrible language when compared to just about everything else.

[quote]now i don't want to go down a road where after i post someone takes apart every little thing i said looking for anything that they don't agree with, its not fun.Well, your support for Python is rather weak.  You can use whatever language you want, but you should be prepared to defend yourself when you're apologizing for a language.

[quote]if you don't like python thats fine, but i think you should except the fact that others do.I do just fine.  What I don't accept is people who support the language and make claims about it that are a) patently false, and b) have no understanding of the technical issues surronding that language.

---

### Post by gord on 2005-12-03
see, not fun ;)


this thread isn't helping anyone anymore, i posted because i wanted to support python because i like it, you don't. fine, leave it at that. its boring now.

---

### Post by furtivefelon on 2005-12-04
[QUOTE=commodore]So, the next language I'll learn is probably ruby.

And I'm not concerned about being an officient programmer.[/QUOTE]

of course you are, everyone is, if not you would be programming in assembly still :P

btw, that should be efficient instead of officient..

I enjoy lisp, it's the most flexible language anywhere, and i've tried alot of languages.. i don't like perl because it's unnesscerily condensed, python because it's white spaces (prob i haven't been reading python code for too long), I simply haven't programmed any significant programs in ruby, since that's the language i discovered after i found lisp, and found alot of the featured is just a half way hack taken from lisp..

EDIT: ops, haven't read the last post, apparently this thread has turned into a flame war of some sort.. disregard this post if anyone want to close this thread..

---

### Post by LordHunter317 on 2005-12-04
[QUOTE=gordthis thread isn't helping anyone anymore, i posted because i wanted to support python because i like it,[/quote]That's fine.

What you don't understand is that **saying Python is good *because of X,Y, and Z, that ARE NOT TRUE*** doesn't help anyone.  It hurts. Spreading misinformation is bad.

> you don't. fine, leave it at that. its boring now.The purpose here isn't to be fun.  It's to help others.  Spreading misinformation doesn't help.

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=LordHunter317]That's fine.

What you don't understand is that **saying Python is good *because of X,Y, and Z, that ARE NOT TRUE*** doesn't help anyone.  It hurts. Spreading misinformation is bad.

The purpose here isn't to be fun.  It's to help others.  Spreading misinformation doesn't help.[/QUOTE]

If helping other people was not fun, I would not be surprised to see a rapid decline in it's popularity.

It may also be that too much is being read into the points various parties are trying to make.  It seems to me as though gord is simply expressing his opinion of some features he considers useful in a language.  I think this can easily be recognized as opinion and not absolute truth-- it is just the way people like to talk in a friendly community setting.

I am of the opinion that people like whatever language/tool/software they like, and they don't really have any particular reasons why so they just kind of make them up and convince themselves.  As an example, I think green is the most superior color in the world, python and C++ are awesome computer languages, and the "Thomas Crown Affair" (remake) was the best movie ever made.  I find that I can easily convince myself of the logic behind these opinions, but others are not so easily swayed...

Since I am not in the debate club or competing for cash prizes on a game show, I feel I can express these opinions without having to be thoroughly explicit about them in casual conversation.

Since this thread deals with "good" and "bad" things about computer languages, and since good and bad are subjective terms themselves, I think we can all, as reasonable persons understand that any opinions expressed should be taken with a grain of salt.

---

### Post by LordHunter317 on 2005-12-04
[QUOTE=cwaldbieser]It may also be that too much is being read into the points various parties are trying to make.[/quote]My issue isn't so much his initial statements but more so his response to critiques:  If someone says, "I like the syntax," and I say, "but it raises these issues," and they say back, "that's just not important," and handwaves back without consideration of that opinion, that tells me the opinion isn't well formed.  Even saying, "Well I can see how that would be a problem but I haven't had to deal with it," is a more legitimate response than just waving it away, which is what I at least percived he was doing, by ignoring the newline issue (not common, but often) and with the popularity non-sequitur.  

It's one thing to have an opinion, it's another to say something that just doesn't make sense with the world we live in.  Language popularity has nothing to do with how "good" a language is, unless you define the latter solely in terms of the former.

---

### Post by commodore on 2005-12-04
LOL I asked about ruby, now everyone's flaming about python.

I allready know all I want to about ruby.

---

