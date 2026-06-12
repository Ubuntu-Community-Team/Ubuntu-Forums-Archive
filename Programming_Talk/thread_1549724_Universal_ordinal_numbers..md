---
title: "Universal ordinal numbers."
date: 2010-08-10
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-10
Ordinal means 1st, 2nd, 3rd...

Programmers hard code such suffixes in their software. However why do it over and over, in every application, and did you consider exceptions like 11th instead of 11st?

Then when you come to internationalize your software, notice what a nightmare! All that logic you put in... she only applies to English!

Now I think I have formula to make it universal and available to ALL applications and I want YOUR opinions, like whould it be useful and what have I missed?

So my proposal is to use the standard gettext internationalization and localization practices to solve this for English as well as every other languages on our planet :shock:

Start with my demo application. Intention is that EVERY app that needs ordinals in ANY language can use this same standard dngettext as follows:

```

// g++ youcame.c
#include <stdio.h>
#include <libintl.h>
#include <locale.h>

int main(int argc, char **argv) {
	setlocale( LC_ALL, "" );
	for (int i = 1; i < 25; ++i) printf(
		gettext("In the human race you came %d%s today!\n"),
		i, dngettext("_ordinal", "°","°", i)
	);
	return 0;
}

```

Summary of proposed conventions
-------------------------------

1. In source code (C domain) ordinals implemented with the text string "°" and translated with dngettext().

2. Each language (yes even English) to have it's own _ordinal.po file. Let me know if you have problems installing this localization:

# English "translations" for _ordinal package.
# Copyright (C) 2010 public domain
#
msgid ""
msgstr ""
"Project-Id-Version: 1\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2010-08-09 14:00+1200\n"
"PO-Revision-Date: 2010-08-09 14:15+1200\n"
"Last-Translator: chris scaife <scaife.chris@gmail.com>\n"
"Language-Team: English\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"
"Plural-Forms: nplurals=4; plural=(n+9)%10<3 && (n+90)%100>10 ? (n+9)%10 : 3;\n"


#: English ordinal numbers
msgid "°"
msgid_plural "°"
msgstr[0] "st"
msgstr[1] "nd"
msgstr[2] "rd"
msgstr[3] "th"

Observations
-----------

- Using the ordinal character ° as standard in C domain aims to
discourage programmed localization for English.

- I prepend underscore on _ordinal domain because it is general
purpose and not want it conflicting with othere packages

---

### Post by schauerlich on 2010-08-10
```
CL-USER> (format t "~:r" 1234)
one thousand two hundred thirty-fourth
```

:)

Might I suggest using a character that appears on most standard keyboards? I'd hate to have to have a keyboard palette out all the time while coding...

---

### Post by worksofcraft on 2010-08-10
Thanks for reply Schaurelich :)

I don't recognise that format command, but find myself wondering none the less how it would perform for say a French person who has sellect the French language on their computer.

Now I did think exactly same as you about using a key more commonly found on standard keyboard and following considerations came to mind:

[LIST]
[*] "Standard" keyboard is different in each country.
[*] The meaning still has to be intelligible in default POSIX/C locale.
[*] ordinal ° is Alt+Shift+; when I select USA-international layout for my keyboard.
[*] It is unlikely to be used so frequently that getting it from Character Map would be a major inconvenience.
[*] Discourage hard coded localization for English.
[*] Encourage use of internationalization package.
[*] Avoid conflict translating characters not intended to represent ordinals. 
[/LIST]

So you see I did think it through and thus I really appreciate the  feedback :)

Now translating ordinals to some languages like Italian introduce the complication of gender: 1st woman is 1ª and first man is 1º. I'm still thinking about how to make it truly internationalizable... I just wish I knew more about ordinals in non-western locales and hoping someone who does reads these Ubuntu forums ;)

---

### Post by schauerlich on 2010-08-10
> **worksofcraft said:**
> Thanks for reply Schaurelich :)

I don't recognise that format command, but find myself wondering none the less how it would perform for say a French person who has sellect the French language on their computer.

It's a nifty function from Common Lisp. It's basically its own embedded language... think printf on steroids. I'm guessing there's implementation-dependent localization options available, but I have no idea.

> Now I did think exactly same as you about using a key more commonly found on standard keyboard and following considerations came to mind:

Still, don't you think it's more convenient to use a symbol that you know will be on a keyboard of someone programming in C? perhaps * for its visual resemblance to º? Since it's quoted it shouldn't matter.

---

### Post by worksofcraft on 2010-08-10
Yeah I know, as an English speaking programmer myself it is very hard to understand problems faced by ordinary users in far away exotic places.

Now you see if I have NO locale defined all my software runs with the default POSIX locale and output of my sample program looks like this:

```

$> unset LANG
$> ./a.out
In the human race you come 1° today
In the human race you come 2° today
In the human race you come 3° today
...

```
Not exactly perfect for us English speakers.
Thus I reinstate my normal Kiwi English locale. The output now becomes exactly what I want and I would like ALL my applications to be able to behave just as nicely for EVERYONE on our planet ;)

```

$ export LANG=en_NZ.UTF-8
$ ./a.out
In the human race you come 1st today
In the human race you come 2nd today
In the human race you come 3rd today
...

```

I don't know... perhaps I just lost that human race but I do hope I haven't lost "the game" yet :D

---

### Post by worksofcraft on 2010-08-10
Now if I change my demo to say

Today she came 3rd in the human race

and select the Italian locale I want it to say

Oggi è venuta 3ª nella razza umana

Well actually race has two translations: razza and corsa because the English pun doesn't work in Italiano... but that's not really the issue.

So my solution is to add the following to my _ordinal.po portable object for English locale. This way the programmer is at liberty to choose whether it is the order of feminine entities and then it translates just fine for English languages that have no gender distinction on ordinals as well as for the ones that do. However perhaps I'm jumping the gun a bit here!!

```

#: feminine ordinal numbers
msgid "ª"
msgid_plural "ª"
msgstr[0] "st"
msgstr[1] "nd"
msgstr[2] "rd"
msgstr[3] "th"

```

p.s. It may not be very legible there but that's the feminine ordinal symbol, a little superscripted "a". Note, now you can see I wouldn't want to translate our regular "a" into "st", "nd", "rd" or "th" because "a" has legitimate meaning already on it's own.

---

### Post by howlingmadhowie on 2010-08-11
in a number of languages you have the problem that ordinal numbers decline. this would make the task even more convoluted.

---

### Post by worksofcraft on 2010-08-11
Hum... yes I googled that. Russian seems to be a test case example, so I suppose my real question is what would Russians expect from their computers?

According to [www.freetranslation.com](www.freetranslation.com) 

"She came 2nd in the human race today"
would become: "&#1086;&#1085;&#1072; &#1087;&#1088;&#1080;&#1077;&#1093;&#1072;&#1083;&#1072; 2-&#1072;&#1103; &#1074; &#1095;&#1077;&#1083;&#1086;&#1074;&#1077;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; &#1088;&#1086;&#1076; &#1089;&#1077;&#1075;&#1086;&#1076;&#1085;&#1103;!"
While "he came 2nd in the human race today!"
reads as "&#1086;&#1085; &#1087;&#1088;&#1080;&#1077;&#1093;&#1072;&#1083; 2-&#1086;&#1081; &#1074; &#1095;&#1077;&#1083;&#1086;&#1074;&#1077;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; &#1088;&#1086;&#1076; &#1089;&#1077;&#1075;&#1086;&#1076;&#1085;&#1103;!"

So would they be happy enough if in general 2º translates to "2-&#1086;&#1081;"  and 2ª to "2-&#1072;&#1103;"? While with three it becomes "3-&#1080;&#1081;" and "3-&#1100;&#1103;" and so on? Just how on Earth do their computer programmers cope at the moment for this kinda stuff I wonder :O

---

### Post by worksofcraft on 2010-08-11
Anyway so I'm making a virtual appliance, specifically for developing internationalization of software. It includes my internationalization tutorial materials I'm working on.

Also has logins each with different locale. To keep it all compact I'm assuming every virtual user can work with English development tools.

If anyone else interested in this I could post my virtual appliance somewhere perhaps. Atm it just has en_NZ and it_IT locales but I do hope to add to it, or perhaps people who understand different cultures might want to add theirs... IDK?!

---

### Post by howlingmadhowie on 2010-08-11
> **worksofcraft said:**
> Hum... yes I googled that. Russian seems to be a test case example, so I suppose my real question is what would Russians expect from their computers?

According to [www.freetranslation.com](www.freetranslation.com) 

"She came 2nd in the human race today"
would become: "&#1086;&#1085;&#1072; &#1087;&#1088;&#1080;&#1077;&#1093;&#1072;&#1083;&#1072; 2-&#1072;&#1103; &#1074; &#1095;&#1077;&#1083;&#1086;&#1074;&#1077;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; &#1088;&#1086;&#1076; &#1089;&#1077;&#1075;&#1086;&#1076;&#1085;&#1103;!"
While "he came 2nd in the human race today!"
reads as "&#1086;&#1085; &#1087;&#1088;&#1080;&#1077;&#1093;&#1072;&#1083; 2-&#1086;&#1081; &#1074; &#1095;&#1077;&#1083;&#1086;&#1074;&#1077;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; &#1088;&#1086;&#1076; &#1089;&#1077;&#1075;&#1086;&#1076;&#1085;&#1103;!"

So would they be happy enough if in general 2º translates to "2-&#1086;&#1081;"  and 2ª to "2-&#1072;&#1103;"? While with three it becomes "3-&#1080;&#1081;" and "3-&#1100;&#1103;" and so on? Just how on Earth do their computer programmers cope at the moment for this kinda stuff I wonder :O

declining is more than that. for example in german:

the second star wars film was made in 1982
der zweite (second, male nominative strongly declined) "krieg der sterne"-film wurde 1982 gedreht

i saw the second star wars film last tuesday
letzten dienstag habe ich den zweiten (second, male accusative strongly declined) "krieg der sterne"-film gesehen.

no one ever tried it again
ein zweiter (second, male nominative weakly declined) hat es nie versucht

the second door on the left leads to the gym
die zweite (second, female nominative strongly declined) tuer links fuehrt zum kraftraum

take the second door on the left.
nehmen sie die zweite (second, female accusative strongly declined) tuer links.

second-hand clothes
kleidung aus zweiter (second, female dative weakly declined) hand.


etc. etc. 

you see, it's quite difficult.

of course, in german you don't really have this problem because ordinal numbers can always be written 2. (for second) or in general n. (for nth). but i don't think this is the case for Russian or Polish or similar.

---

### Post by nvteighen on 2010-08-11
This is far from trivial.

If you want to create a way to universally generate all ordinal numbers, you have to teach the computer several aspects of the language: syntax, for instance...

In generative grammar (which is the theory I like most), there are two hypotheses regarding morphology in general: the weak and the strong lexicalist hypotheses (WLH and SLH). The non-lexicalist hypothesis, i.e. the transformational one, shown to be false in the 1970s.

The Lexicalist Hypothesis's (both SLH or WLH) main principle is the so called "Projection Principle", which has been defined in both a formal and a more "layman" way:

[QUOTE=Chomsky, N.]
Representations at each syntactic level (...) are projected from the lexicon, in that they observe the subcategorization properties of lexical items.
[/QUOTE]
(*Lectures on Government and Binding. The Pisa lectures*, 2.1.38)

What this means is that no matter what you're analyzing, the theory you develop should ensure lexical properties of words are always respected. This means that your code should know about those properties if you want it generate some piece of linguistic data.

The SLH considers every word to be base-generated at D-structure. More informally, languages would have every possible form be generated from the Lexicon and the result of purely lexical rules would be then inserted into the syntax tree... after that, the syntax tree would be affected only by syntactic rules. So, for example, in the Lexicon, you'd have a word "table" and also a different word "tables", "work" (verb) would be different from "worked", or even "cute" and "cuttie" (a diminutive) would be different.

The WLH instead considers that inflectional devices may be syntactic elements on their own that are then merged by movement at the Phonetic Form. This means, for example, that in the Lexicon you've got an entry [NOPARSE][+Past][/NOPARSE] that you insert into the syntax tree and then, depending on its position, [+Past] may be transformed into "did" (questions and negative statements) or "-ed/-en/..." (affirmative) by phonetical rules.

So, SLH would mean you've got to create a file where every single possible form is available. WLH would mean you try to create the final form programatically from a stems file and an endings file... but only inflectional endings, as WLH doesn't consider lexical derivation to be syntactical (e.g. easy -> easily).

Now, if you use the SLH, you may skip having to create a phonological rule system in your code, but you'll need to add gender, number and case features to every single word you intend to show in your output. No, not only for the ordinals, because you'll need to teach the program how to deduce the correct combinations. If you go for WLH, you could tell the code what's the form you want instead of deducing it, but you'll need to create a way to cope with the phonetical resulting forms.

I guess you now see how difficult this might be. Ok, I know you only want to generate ordinal numbers, not write a natural language generator, but this summarizes some issues you'd encounter. In my opinion, the simplest would be to just create language-specific lists, not a universal method, that's adapted to each language's needs and ways of doing this.

P.S: I fear I went a bit off-topic... Sorry, you know who I am :P

---

### Post by worksofcraft on 2010-08-11
> **howlingmadhowie said:**
> declining is more than that. for example in german:
...
you see, it's quite difficult.

of course, in german you don't really have this problem because ordinal numbers can always be written 2. (for second) or in general n. (for nth). but i don't think this is the case for Russian or Polish or similar.

Thanks for that excellent illustration howlingmadhowie :) It makes quite clear why in some languages it would not be practical to expect computer generated output to take all these declinations into account. In such cases it is simplest to rewrite it without an ordinal e.g. "You came 5th" translating to something like  "Your rank is 5".

> **nvteighen said:**
> This is far from trivial.

If you want to create a way to universally generate all ordinal numbers, you have to teach the computer several aspects of the language: syntax, for instance...


Yes, that is interesting but not my intention:
ngettext() functions are essential for use where the form of a word depends on a numeric quantity. Sadly many English speaking programmers are still hard coding addition of 's' for plurals. Thus they bypass the internationalization while implementing their own localization and all those lone 's's defeat translation to other languages

The same problem applies to ordinals: I'm not so much interested in how to express them for every possible language, but much more to have a generic internationalized form of ordinals so that the rules of English language need NOT be embedded in software.

---

### Post by WitchCraft on 2010-08-11
> **worksofcraft said:**
> Thanks for that excellent illustration howlingmadhowie :) It makes quite clear why in some languages it would not be practical to expect computer generated output to take all these declinations into account. In such cases it is simplest to rewrite it without an ordinal e.g. "You came 5th" translating to something like  "Your rank is 5".



Yes, that is interesting but not my intention:
ngettext() functions are essential for use where the form of a word depends on a numeric quantity. Sadly many English speaking programmers are still hard coding addition of 's' for plurals. Thus they bypass the internationalization while implementing their own localization and all those lone 's's defeat translation to other languages

The same problem applies to ordinals: I'm not so much interested in how to express them for every possible language, but much more to have a generic internationalized form of ordinals so that the rules of English language need NOT be embedded in software.

I don't think the solution for your problem exists...

---

### Post by worksofcraft on 2010-08-11
> **WitchCraft said:**
> I don't think the solution for your problem exists...

I'm researching how to make software that IS suitable for iternationalization.

Here is main part of my "speaking clock" example... produces output like: "At the 3rd beep it will be 1 minute past 12.

```

static const char *ord[] = {"st", "nd", "rd", "th"};

cout << "At the " << n <<
    ord[(n+9)%10<3 && (n+90)%100>10 ? (n+9)%10 : 3] <<
    " beep, it will be " << minute << " minute" <<
    ((minute!=1)?"s":"") << " past ") << hour << "." << endl;

```

Now I'm not going to argue about the merrits of type safeness and overloaded manipulators but give me a good old format string any day ;)

However at issue is the mega phail when it comes to internationalization:

[LIST]
[*] Word order and sentence struture is incorrect for other languages.
[*] Pluralization of minute won't work in other languages with this technique
[*] Sentence fragments create a nonsensical dictionary for localization
[*] The hard code English ordinals won't translate
[*] can't do both masculine and feminine ordinals
[/LIST]

In otherwords, this way of coding would be impossible to translate to practically ANY other language!

Standard gettext() package provides solutions and recommendations to several of these problems and with the technique I suggest in this thread we not only get the same quality English output even for the ordinals, but facilitate a great many translations by moving the English localization out of the code and into the domain of the gettext() package.

What I'm definitely NOT trying to solve are those problems native programmers of certain locales have themselves no solution for in their very own language.

---

### Post by worksofcraft on 2010-08-16
> **schauerlich said:**
> 
Might I suggest using a character that appears on most standard keyboards? I'd hate to have to have a keyboard palette out all the time while coding...

After quite a bit of research schauerlich's suggestion turns out to be by far the most sensible:
[LIST]
[*] C/C++ do not allow non ascii in their source files
[*] Python flatly refuses to translate any string containing non ascii
[/LIST]

Eventually I settled on "st" with plural "th" in default locale but it can look rather silly when the portable object isn't in place :( The good bit is I can use it from C/C++ and Python and probably every other programming language that supports gettext :)

---

### Post by WitchCraft on 2010-08-18
> **worksofcraft said:**
> 
[*] C/C++ do not allow non ascii in their source files


Wrong.

std::wstring wstrHelloUnicode = L"Hallöle Ünicodé\n";
wchar_t* swzHelloUnicode = L"&#1087;&#1088;&#1080;&#1074;&#1077;&#1090;&#1080;&#1082; &#1091;&#1085;&#1080;&#1082;&#1086;&#1076; \n";


std::wcout << wstrHelloUnicode;
wprintf(L"%ls\n",  swzHelloUnicode);

---

### Post by worksofcraft on 2010-08-18
> **WitchCraft said:**
> Wrong.

std::wstring wstrHelloUnicode = L"Hallöle Ünicodé\n";
wchar_t* swzHelloUnicode = L"&#1087;&#1088;&#1080;&#1074;&#1077;&#1090;&#1080;&#1082; &#1091;&#1085;&#1080;&#1082;&#1086;&#1076; \n";


std::wcout << wstrHelloUnicode;
wprintf(L"%ls\n",  swzHelloUnicode);

No not wrong. The ISO C standard specifies that C/C++ source code must use only ASCII because there is no guaranteed consistency between compile time and run time character coding sets. If I come across the appropriate web link again I'll post it.

The standard doesn't say you can't use other characters, but says the result is undefined. Evidently if you compile and run it on the same computer with the same settings it is quite likely to work, but if someone with completely different settings runs your compiled executable it may malfunction.

p.s. Here is the link:
[http://www.gnu.org/software/gettext/FAQ.html#nonascii_strings](http://www.gnu.org/software/gettext/FAQ.html#nonascii_strings)

but note that I'm all in favor of simply defining UTF-8 as the standard and deprecating all those conflicting ISO code pages... have you checked recently what is yours set for ? ;)

---

### Post by Reiger on 2010-08-18
But you've already given an answer to your own problem: don't use ordinals... If you aren't going to win the Nobel Literature Prize for the statements your program emits &#8220;You are the %ordinal person to try that this morning&#8221;, you might as well write them of the form &#8220;Number of people who have tried that this morning so far: %d.&#8221; or something.

Looks ugly, but the purpose of a computer generated message is to communicate something to the reader and not amaze them at the syntactic and semantic and linguistic feats of extraordinary gymnastics being performed on the screen. And it just works: all meaningful languages have ways to express quantities in terms of &#8220;number of qualifiers: quantifier&#8221; or whatever the right linguistic device is called.

---

### Post by worksofcraft on 2010-08-18
> **Reiger said:**
> 
Looks ugly, but the purpose of a computer generated message is to communicate something to the reader and not amaze them at the syntactic and semantic and linguistic feats of extraordinary gymnastics being performed on the screen. And it just works: all meaningful languages have ways to express quantities in terms of &#8220;number of qualifiers: quantifier&#8221; or whatever the right linguistic device is called.

Yes, you make an excellent point. I think this thread has been more in the way of exploring the limits of internationalization. A quick google however will confirm that countless developers are all hard coding this kind of logic especially with normal plurals like appending an 's' and that is definitely **not** the way to go in a world where globalization is becoming more and more important.

One thing that I find really worrying is how gettext in Python refuses to translate any strings that have non ascii characters in them. Does that mean we can't make an English translation from Python scripts written by French and German people, without editing their source code?! :shock:

---

### Post by WitchCraft on 2010-08-20
> **worksofcraft said:**
> 
but note that I'm all in favor of simply defining UTF-8 as the standard and deprecating all those conflicting ISO code pages... have you checked recently what is yours set for ? ;)

Actually I have about a week or two ago because of this:
[http://www.lumisoft.ee/Forum/default.aspx?g=posts&t=673](http://www.lumisoft.ee/Forum/default.aspx?g=posts&t=673)

It's UTF-8 on my Ubuntu and ANSI 1252 on DE-CH Windows 7.
So that problem only exists when you want to compile on Windows or CrApple.
And any idiot that changed the Ubuntu system default to something else is himself the one to blame.

But what really matters is that unicode works on the Linux console, while it doesn't work on the windows/dos prompt.

> **worksofcraft said:**
> No not wrong. The ISO C standard specifies that C/C++ source code must use only ASCII because there is no guaranteed consistency between compile time and run time character coding sets. If I come across the appropriate web link again I'll post it.

O shi.... didn't know, but the reality is both GNU and MS support it, and it works as long as you use BOM in textfiles or when you just use UTF-8 everywhere. Don't know about CrApple, but I suppose they do, too.

---

### Post by worksofcraft on 2010-08-20
> **WitchCraft said:**
> Actually I have about a week or two ago because of this:
[http://www.lumisoft.ee/Forum/default.aspx?g=posts&t=673](http://www.lumisoft.ee/Forum/default.aspx?g=posts&t=673)

It's UTF-8 on my Ubuntu and ANSI 1252 on DE-CH Windows 7.


Hum...

$> sudo locale-gen de_CH
Generating locales...
  de_CH.ISO-8859-1... done
Generation complete.

On my Ubuntu system default encoding of your locale appears to be ISO-8859-1, so if we both selected de_CH locale compiled the same  C++ program and swapped the binaries, would they still display non-ascii characters the way we intended?

---

### Post by WitchCraft on 2010-08-20
> **worksofcraft said:**
> Hum...

$> sudo locale-gen de_CH
Generating locales...
  de_CH.ISO-8859-1... done
Generation complete.

On my Ubuntu system default encoding of your locale appears to be ISO-8859-1, so if we both selected de_CH locale compiled the same  C++ program and swapped the binaries, would they still display non-ascii characters the way we intended?

Tell me, when you generate the locale for de_CH, you get 8859-1?
Sure you do, but UTF8 is not for locale, it's global.

Why should anyone use 8859-1? It's plain stupid, creates nothing but trouble.

---

### Post by worksofcraft on 2010-08-20
> **WitchCraft said:**
> Tell me, when you generate the locale for de_CH, you get 8859-1?
Sure you do, but UTF8 is not for locale, it's global.

Why should anyone use 8859-1? It's plain stupid, creates nothing but trouble.

I totally agree 101%,  and the sooner ISO encoding pages are flagged as "deprecated" the better. :lolflag:
Alas, most computer users just go with the default they get because they don't know the difference.

IMHO it shows just how stupid committees and standards organizations can be when bodies like ANSI try to dictate you shouldn't use anything but ASCII in your C and C++ :shock: Just how has the rest of the world been writing programs for their native language all these years one must wonder :confused:

Like I posted elsewhere, I changed my system defaults to be UTF-8 (but left some like de_CH so I would be able to experiment).

I really think Ubuntu should do this too for future releases. It's as simple as editing the entries in /usr/share/i18n/SUPPORTED

---

