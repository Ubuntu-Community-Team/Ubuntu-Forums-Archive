---
title: "Perl on Hardy, how?"
date: 2008-08-27
forum: Programming Talk
---

### Post by Nielsoerbaek on 2008-08-27
Hi, i have nothing to do for a while and my dad suggested that i started learning how to program PERL. I have no previous programming experience. 
How do i get started? I know that i need an interpreter, does that come bundled with Ubuntu, or do i have to get it myself?

Thanks in advance.

---

### Post by sdennie on 2008-08-27
Moved to Programming Talk as I think you'll get better support here.  Also, perl is installed by default in Hardy.  A useful way to find modules for what you want to do in Ubuntu is to go to System->Administration->Synaptic and search for "perl thing_you_want_to_do".  You will almost always find a variety of modules that will serve your needs and information on how to use them by inferring the man page.  For example, after installing libnet-irc-perl, you can find the information on how to use it with:

```

man Net::IRC

```

---

### Post by cmay on 2008-08-27
[http://www.perl.com/pub/a/2000/10/begperl1.html](http://www.perl.com/pub/a/2000/10/begperl1.html)

[http://articles.techrepublic.com.com/5100-10878_11-6077064.html](http://articles.techrepublic.com.com/5100-10878_11-6077064.html)
hi 
i posted two perl links for you . i am also just started perl not many hours ago so i can almost tell all i know just to get you started.
to try perl now then open gedit and type 
[PHP]#!/usr/bin/perl 
print "hello world";
[/PHP]
save file as hello.plx and to test it you have to make it an executable.
you should run  it from the terminal .
i use chmod 755./hello.plx then run whit ./hello 

hope it helps.

edit
added more links for you.
[http://use.perl.org/articles/03/02/07/1628206.shtml](http://use.perl.org/articles/03/02/07/1628206.shtml)
[http://www.perl.com/pub/a/2000/10/begperl1.html](http://www.perl.com/pub/a/2000/10/begperl1.html)
[http://docs.rinet.ru/P7/](http://docs.rinet.ru/P7/)
[http://www.wikihow.com/Learn-Perl](http://www.wikihow.com/Learn-Perl)
[http://articles.techrepublic.com.com/5100-10878_11-6077064.html](http://articles.techrepublic.com.com/5100-10878_11-6077064.html)

---

### Post by days_of_ruin on 2008-08-27
> **Nielsoerbaek said:**
> Hi, i have nothing to do for a while and my dad suggested that i started **learning how to program PERL**. I have no previous programming experience. 
How do i get started? I know that i need an interpreter, does that come bundled with Ubuntu, or do i have to get it myself?

Thanks in advance.

I think your dad hates you.:lolflag:

---

### Post by forger on 2008-08-27
as always, you need something **to do** with programming - find a feature or a command that would make your life easier, such as a robot bringing you some cold beer :)
start with the 'hello world' above, some if-then-else statements, some while loops to start enumerating things.. well you get the drift?

> **days_of_ruin said:**
> I think your dad hates you.:lolflag:
Nothing wrong in asking someone who has nothing to do to actually be productive
He could've asked him to paint the house under 50C and direct sun if he really hated him :lolflag:

---

### Post by LaRoza on 2008-08-27
> **Nielsoerbaek said:**
> Hi, i have nothing to do for a while and my dad suggested that i started learning how to program PERL. I have no previous programming experience. 
How do i get started? I know that i need an interpreter, does that come bundled with Ubuntu, or do i have to get it myself?

Thanks in advance.

You have Perl. (Don't write PERL ;))

See my wiki on how to get started.

---

### Post by days_of_ruin on 2008-08-27
> **forger said:**
> as always, you need something **to do** with programming - find a feature or a command that would make your life easier, such as a robot bringing you some cold beer :)
start with the 'hello world' above, some if-then-else statements, some while loops to start enumerating things.. well you get the drift?


Nothing wrong in asking someone who has nothing to do to actually be productive
He could've asked him to paint the house under 50C and direct sun if he really hated him :lolflag:

I was making fun of perl.:lolflag:

---

### Post by ghostdog74 on 2008-08-27
> **days_of_ruin said:**
> I was making fun of perl.:lolflag:
try making fun of Perl at comp.lang.perl.misc

---

### Post by pmasiar on 2008-08-27
> **Nielsoerbaek said:**
> Hi, i have nothing to do for a while and my dad suggested that i started learning how to program PERL. I have no previous programming experience.

How old are you? 

Can your dad or someone else around help you with Perl? If yes, it **might** be good choice. If not, Perl is likely not optimal choice.

One good choice for youngster is (windows-only) Game Maker, GUI to design and generate games, without much typing.

Best choice is (in opinion of many) Python, one of reasons is less quirky syntax, and Python shell where you can learn syntax one line at a time.

See sticky for (many, long and heated) discussions about learning programming, and wiki in my sig for links to learn Python.

---

### Post by LaRoza on 2008-08-27
@OP Perl is an older language than Python, and Python and Perl overlap in their use. Python and Ruby are languages like Perl that are more recent, and may be worth looking into also.

Many see Python and Ruby as improved Perl like languages, so they are often advocated.

Perl and Python are typically installed by default on Linux distros (not so sure about Ruby)

---

### Post by cmay on 2008-08-28
> Perl and Python are typically installed by default on Linux distros (not so sure about Ruby)
ruby is not installed per default and perl is the only language that is installed per default on debian gnu/linux  Free bsd  solaris  minix.
whereas python is only installed per default in ubunutu.
in any of these installations i have other than ubuntu i use i have to install python if i want python to be installed.

---

### Post by Nielsoerbaek on 2008-08-28
SUCCES! I just made my first perl script. I had some troubles actually running things from the terminal, but i figured it out, i think. It works anyways. Now the hard part is over, just have have to learn how to do other things than writing 2 words.:)

Thanks a lot!

---

### Post by cmay on 2008-08-28
> SUCCES! I just made my first perl script. I had some troubles actually running things from the terminal, but i figured it out, i think. It works anyways. Now the hard part is over, just have have to learn how to do other things than writing 2 words.

great :).

---

### Post by pmasiar on 2008-08-28
> **cmay said:**
> ruby is not installed per default and perl is the only language that is installed per default on debian gnu/linux  Free bsd  solaris  minix.
whereas python is only installed per default in ubunutu.
in any of these installations i have other than ubuntu i use i have to install python if i want python to be installed.

I am pretty sure that Python is installed by default on debian too (can some expert comment on that?) - and also on fedora and RH. I am not surprised that BSD, Minix and Solaris don't include Python - they are kinda limited/server/conservative distros. And even on those, installing Python is trivial, so what is your beef?

---

### Post by cmay on 2008-08-28
> I am pretty sure that Python is installed by default on debian too (can some expert comment on that?) - and also on fedora and RH. I am not surprised that BSD, Minix and Solaris don't include Python - they are kinda limited/server/conservative distros. And even on those, installing Python is trivial, so what is your beef?
no beef.
but someone say(ruby not sure about that) and in order to clarify i post 
an clarification.which is based on what i use.
on my debian etch net install no python is installed
and my debian lenny no python is installed.
and yes if some one wants python to be installed one can install it via synaptic just as easy as other programs.

---

### Post by LaRoza on 2008-08-28
> **pmasiar said:**
> I am pretty sure that Python is installed by default on debian too (can some expert comment on that?) - and also on fedora and RH. I am not surprised that BSD, Minix and Solaris don't include Python - they are kinda limited/server/conservative distros. And even on those, installing Python is trivial, so what is your beef?

Debian has several install methods, and the most minimal won't have it (it won't have anything other than the base system and GNU Core Utils and a package manager basically)

> **cmay said:**
> no beef.
but someone say(ruby not sure about that) and in order to clarify i post 
an clarification.which is based on what i use.
on my debian etch net install no python is installed
and my debian lenny no python is installed.
and yes if some one wants python to be installed one can install it via synaptic just as easy as other programs.

Could you write without random line breaks? The text will wrap on its own...

Python is installed on non minimal Debian installs.

---

### Post by cmay on 2008-08-28
> python is installed on non minimal Debian installs.
the last time i did a non minimal install was a linux magazine cover dvd of sarge and i dont seem to recollect  python being installed. i know some programs will depend on python to be installed but i am pretty sure that ruby is not installed per default in debian.

---

### Post by slavik on 2008-08-28
Minix installs anything? :P (no seriously, there is a Perl interpreter in the default Minix isntall?)

---

### Post by cmay on 2008-08-28
> Minix installs anything? :P (no seriously, there is a Perl interpreter in the default Minix isntall?)
yes.
there is the amsterdam compiler kit as well. that is c and pascal compilers. the gcc compiler you can install from the cd which has a lot of programs on it. my minix computer died however since i put it on a really old one whit 16 mb ram no ps2 mouse and a 855mb harddisk. i will install minix over my Freedos installation when i am done whit my turbo pascal 7.0 text book.:)

---

