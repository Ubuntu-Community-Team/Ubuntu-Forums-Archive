---
title: "Perl vs Python"
date: 2007-07-06
forum: Programming Talk
---

### Post by Greslore on 2007-07-06
I find myself needing to do more and more sys admin'ing these days.  For the most part, I have been using BASH scripts.  I was told by a few people that I should look into perl or python to make my life easier.

I will be doing stuff like modifying LDAP attributes, file and dir manipulation (writes, moves, replacing text inside of files, etc), and the like.  

Can Python handle these types of things?  I'd like to go with Python over Perl, but not sure if it can do everything Perl can do for sys admin tasks.  There seems to be a Perl Mod for everything (cpan.org) nowadays.  Is Python the same way?

---

### Post by pmasiar on 2007-07-06
Python has cheeseshop as module repository. I would be surprised if any important function is missing - and expected appropriate library to cover it coming quickly.

Perl was huge 5 years ago, but now it is mostly legacy code (and you *know* you don't want to maintain old Perl code written by others :-) ). Big part of Perl hackers moved to Python and Ruby, which have support from big companies (including Google, Sun, and MSFT). I am not aware of any important company backing Perl.

---

### Post by Soybean on 2007-07-06
Python should be capable of doing everything you need; it's probably a matter of personal preference. This forum is largely pro-python. ;)

Personally, I prefer Perl because you can do productive things with delightfully cryptic code. It makes things more challenging when you try to fix it 6 months later, but I always find it funny enough that I don't mind the challenge. :D Oddly, some people might consider this to be a drawback.

---

### Post by iqag1060 on 2007-07-06
Perl, Python, or Ruby should all pretty much be able to accomplish the same tasks - the way you go about it will be different, though. If you have experience with any of them, choose that. If you have to choose one to learn, I would skip Perl - although many swear by it. I would take a look at each of the other two. Since they're fairly different stylistically, you'll probably find one a more natural fit. After you get good at one, though, go back and look at the other. You may not switch but you will definitely appreciate certain things in a way you wouldn't have before.

The Ubuntu world - and to some extent the Linux world in general - seems to prefer Python to Ruby, so you might find it easier to find ready-made solutions to system administration tasks. Ruby has more 'magic' - like Perl but more powerful and easier to understand. You could glance at the book [Everyday Scripting with Ruby]("http://www.pragmaticprogrammer.com/titles/bmsft/index.html"). Not everything in there is the sort of stuff you're looking for, but it gives a good sense of what bringing a Ruby mindset to those sorts of tasks looks like. In the end you're going to be productive in what you're comfortable with.

---

### Post by Note360 on 2007-07-06
I would say ruby might be what you are looking for. You can use simular abilites as python with alot of the benefit of perl (mainly its regexp's). I would say learn some python first (just to nail the formatting into your head) then move to ruby. Ruby can be mroe elegant then python and more cryptic than perl. your aim is the elegant side of things.

---

### Post by bukwirm on 2007-07-06
> **Soybean said:**
> 
Personally, I prefer Perl because you can do productive things with delightfully cryptic code. It makes things more challenging when you try to fix it 6 months later, but I always find it funny enough that I don't mind the challenge. :D Oddly, some people might consider this to be a drawback.

Plus, with Perl you can insure yourself future employment because you will be the only person who can understand your scripts.

---

### Post by init1 on 2007-07-06
> **Greslore said:**
> I find myself needing to do more and more sys admin'ing these days.  For the most part, I have been using BASH scripts.  I was told by a few people that I should look into perl or python to make my life easier.

I will be doing stuff like modifying LDAP attributes, file and dir manipulation (writes, moves, replacing text inside of files, etc), and the like.  

Can Python handle these types of things?  I'd like to go with Python over Perl, but not sure if it can do everything Perl can do for sys admin tasks.  There seems to be a Perl Mod for everything (cpan.org) nowadays.  Is Python the same way?
I think python will be fine. I don't like perl.

---

### Post by ankursethi on 2007-07-07
All three of them are pretty much the same. Perl code is largely unreadable and unmaintainable not because Perl is a bad language, but because the people writing that code like to fool around and mess the entire thing up, or are bad programmers. A professional Perl programmer will write clean code which can be maintained by anybody.

I can write bad code in Python, but I can also write clean code in Perl.

---

### Post by runningwithscissors on 2007-07-08
Perl. As nice as python is, for sysadmin stuff, nothing beats Perl. CPAN has modules for just about anything. A Perl interpreter is present on _any_ Unix machine, and more sysadmins know Perl than python, so they can maintain your code, and you can work with theirs.

Perl is what you want.

---

### Post by ghostdog74 on 2007-07-08
> **Greslore said:**
> I find myself needing to do more and more sys admin'ing these days.  For the most part, I have been using BASH scripts.  I was told by a few people that I should look into perl or python to make my life easier.

I will be doing stuff like modifying LDAP attributes, file and dir manipulation (writes, moves, replacing text inside of files, etc), and the like.  

Can Python handle these types of things?  I'd like to go with Python over Perl, but not sure if it can do everything Perl can do for sys admin tasks.  There seems to be a Perl Mod for everything (cpan.org) nowadays.  Is Python the same way?
you do not ask this type of question here and expect to get a definite answer because everybody's preferences will be different. some like perl, some like python, but whatever it is, you should be asking yourself instead. why not try to code sysadmin scripts in both of them, and find out the truth for yourself. There's even no point continuing this thread, IMO

---

### Post by slavik on 2007-07-08
The following code actually implements "something" ... guess what it is. :)

```

sub sub1 {
	push @{ $_{$_[1]} }, $_[0];
}

sub sub2 {
	foreach(sort keys %_) { return shift @{ $_{$_} } if ($#{ $_{$_} } > -1); }
}

```

anyone who knows Perl will be able to read it ...

Those who don't, have no idea what's going on. :)

---

### Post by pmasiar on 2007-07-08
> **slavik said:**
> anyone who knows Perl will be able to read it ...


This kind of trickery in language, and the elitism which it creates in people writing such code, is exactly the reason why I (after couple years struggling "to get it" and reading perlmonks and working on my skills and my karma) left perl community, disgusted. Python is more inviting place for beginners, and it is easier to learn from gurus.

I can still hack some perl code if needed, but I prefer not to.

---

### Post by bread eyes on 2007-07-08
> **iqag1060 said:**
> Perl, Python, or Ruby should all pretty much be able to accomplish the same tasks - the way you go about it will be different, though.

well duh

---

### Post by slavik on 2007-07-09
> **pmasiar said:**
> This kind of trickery in language, and the elitism which it creates in people writing such code, is exactly the reason why I (after couple years struggling "to get it" and reading perlmonks and working on my skills and my karma) left perl community, disgusted. Python is more inviting place for beginners, and it is easier to learn from gurus.

I can still hack some perl code if needed, but I prefer not to.

Sorry, if I sounded elitist. Every time I finish some perl code, my next challenge is to try and make it unreadable. It's also fun to squeeze 5 statements into 1.

For example, given a comma delimited list of persons' ages and name ("sherry 12, john 10, bob 100"), write a program in fewest lines possible to sort the list both ways (by name and by age) and to print it back. in perl it can be done in 2 lines (1 line for each). while that 1 line is unreadable, it is always fun taking something that is 5-10 lines and shortening it as such ...

Not to mention the fact that there is a Perl API for Pidgin. :P

---

### Post by pmasiar on 2007-07-09
> **slavik said:**
> Sorry, if I sounded elitist. ... it is always fun taking something that is 5-10 lines and shortening it as such ...

I know that this attitude is considered normal and not "elitist" in perl circles - it is called "golf" and considered fun. Some perl developers are very interesting personalities, have very deep computer knowledge and know how to have fun. 

I enjoy reading Larry's "State of the onion" reports, without doubt *very* smart person. I would recommend to anyone go and see Damien Conway's presentation, he can create incredible mix of entertainment, information, and amusement. He knows his Perl.

I just would not recommend to use Perl for code you need to maintain :-)

---

### Post by LaRoza on 2007-07-09
Learn Python, Perl and Ruby.

Then use what works.

---

### Post by slavik on 2007-07-10
> **pmasiar said:**
> I know that this attitude is considered normal and not "elitist" in perl circles - it is called "golf" and considered fun. Some perl developers are very interesting personalities, have very deep computer knowledge and know how to have fun. 

I enjoy reading Larry's "State of the onion" reports, without doubt *very* smart person. I would recommend to anyone go and see Damien Conway's presentation, he can create incredible mix of entertainment, information, and amusement. He knows his Perl.

I just would not recommend to use Perl for code you need to maintain :-)

If I write code that I need to maintain, it is very readable, look up my reverse deb lookup ...

---

### Post by iblis on 2007-07-10
> **ankursethi said:**
> All three of them are pretty much the same. Perl code is largely unreadable and unmaintainable not because Perl is a bad language, but because the people writing that code like to fool around and mess the entire thing up, or are bad programmers. A professional Perl programmer will write clean code which can be maintained by anybody.

I can write bad code in Python, but I can also write clean code in Perl.

I second this. You **can** write extremely obfuscated code in Perl* - I'm sure almost everyone is familiar with the camel code by now. But you don't **have** to make a mess out of it.

I prefer Python these days, but properly written Perl is just as nice to look at, and just as easy to understand, IMHO.

[size=1](* This is also possible in Python. See 'pydoc lambda')[/size]

---

