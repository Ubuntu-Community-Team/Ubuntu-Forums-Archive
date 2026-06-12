---
title: "Tabs, indents, spaces..."
date: 2007-07-16
forum: Programming Talk
---

### Post by samjh on 2007-07-16
What kind of tabbing/spacing/indenting do you use in your source code?

---

### Post by Paul820 on 2007-07-16
I use a tab of 4, tab is replaced with spaces to be consistent with other text editors that are used to view the source. A lot of editors have different sized tabs so using spaces is much better i think.

---

### Post by yabbadabbadont on 2007-07-16
If you use true tab characters in your file, then it doesn't matter what width you use when displaying them.  The important thing is to use tabs to the indentation level, and then spaces for any special alignment you may want after that.  (in order to make the code pretty ;))

---

### Post by samjh on 2007-07-16
I use tabs rather than spaces, 4 space-width per tab/indent.  I find 8 to be too wide, and using only spaces are a pain in the rear end when indenting or de-indenting large blocks of code.

---

### Post by yabbadabbadont on 2007-07-16
> **samjh said:**
> ... and using only spaces are a pain in the rear end when indenting or de-indenting large blocks of code.

The difficulty (or not) depends upon which editor you use and its abilities. (or not) ;)

---

### Post by Wybiral on 2007-07-16
I use 4 space tabs (replaced). That way I know it will always look the same and go out the same number of characters.

> **samjh said:**
> I use tabs rather than spaces, 4 space-width per tab/indent.  I find 8 to be too wide, and using only spaces are a pain in the rear end when indenting or de-indenting large blocks of code.

That's why you need to use an edit with good features. I use Gedit which has a tab plugin so I can hit Ctrl+T and Ctrl+shift+T to indent and unindent large chunks.

---

### Post by samjh on 2007-07-16
> **Wybiral said:**
> I use 4 space tabs (replaced). That way I know it will always look the same and go out the same number of characters.



That's why you need to use an edit with good features. I use Gedit which has a tab plugin so I can hit Ctrl+T and Ctrl+shift+T to indent and unindent large chunks.

I discovered that recently.  I used to use Scite, which didn't have that feature.  Prior to Scite, I used IDEs, where the difference between spaces and tabs are not really an issue.

It depends on the project's required coding style.  Some projects mandate the use of real tabs, others will only tolerate spaces.  So I guess that is the real deciding factor.

---

### Post by pmasiar on 2007-07-16
> **samjh said:**
> I discovered that recently.  I used to use Scite, which didn't have that feature.  Prior to Scite, I used IDEs, where the difference between spaces and tabs are not really an issue.

It depends on the project's required coding style.  Some projects mandate the use of real tabs, others will only tolerate spaces.  So I guess that is the real deciding factor.

That's odd, SciTE does not recommended Python's "best practices" style: convert tabs to 4 spaces! Needs be reported as a bug. :-(

I usually use SPE for Python and SciTE for templates, that's why did not noticed it.

---

### Post by runningwithscissors on 2007-07-17
I use an 8 character wide hard tab for indents.

I also use the K&R style for the placement of braces, and prefer underscores instead of intercaps for variable and function names and avoid uppercase in most of my code (except for when I'm writing Java or C#, because almost all of their libraries use intercaps and I don't want my code to look odd in those languages).

---

### Post by Wybiral on 2007-07-17
> **runningwithscissors said:**
> I use an 8 character wide hard tab for indents.

I also use the K&R style for the placement of braces, and prefer underscores instead of intercaps for variable and function names and avoid uppercase in most of my code (except for when I'm writing Java or C#, because almost all of their libraries use intercaps and I don't want my code to look odd in those languages).

I've recently been using underscores instead of capitals too... I think it's a result of looking at too much C code, lol.

I usually use aligned brackets on their own line though... Its easier for me to see the code chunks that way (looks spacier). Unless there's only one command in a condition or loop, then I don't use brackets (in C).

---

### Post by Golyadkin on 2007-07-17
Oh I hate tabs so much... nothing ruins good code formatting like dynamic length tabs... If a tab was always the same size, it would be great, but since it isn't and even more importantly often cannot be changed in an editor, it creates a nightmare in projects where different people work with the same sourcefiles, with different editors. That is why I am in favor of using a code style guide for all projects, with 3 spaces for indentation. (It doesn't have to be an even number, 3 is enough and leaves more space for your statements if you want to stay within the 78 character print margin. (This is often a requirement for peer reviewers being able to print your source.)

---

### Post by Modred on 2007-07-17
I use 4 spaces for most files and 2 spaces for Ruby.  I'm currently torn between 4 spaces and 4 space tab characters for file types aside from Python and Ruby, but I do like the 4 space width, regardless of how it's implemented.

---

### Post by jvc26 on 2007-07-17
I use four space wide tabs (convert from tabs to spaces) and so maintain the 4 spacing rule, but also maintain ease of use for indenting lines.
Il

---

### Post by ButteBlues on 2007-07-17
I use "Other".

That being, whatever is proper for the language I'm working in. If it requires tabs, I use tabs. If it's Python, 4 spaces; if it's Ruby 2 spaces. etc.

---

### Post by the_unforgiven on 2007-07-17
I haven't come across a specific need to use a different indentation mechanism - so, I stick to the default vim configuration - hard tab with 8 columns (no conversion to spaces) for all my C/C++/Perl/Java/whatever needs.

Just as a side note, here is an interesting entry on what all indentation styles are followed:
[http://en.wikipedia.org/wiki/Indent_style](http://en.wikipedia.org/wiki/Indent_style)

---

### Post by aks44 on 2007-07-17
Spaces, 2 (more space for the statements), brackets on their own line (clearer code IMHO, and much easier to match them).

CapitalizedTypes, almostCapitalized methods, functions, params & local variables, m_privateVariable. ;)

---

### Post by bcat on 2007-07-17
One indent is two space characters, as far as I'm concerned.

---

### Post by max.diems on 2007-07-17
What better way to say this than with a code sample?

```

#include <cstdio>
#include <cstdlib>
#include <iostream>

using namespace std;

int main(int argc, char *argv[]);

int main(int argc, char *argv[]){
    cout << "Hello, world!";
}

```

In HTML, though, I use the well-known style "Hmm.... This looks good."

---

### Post by jespdj on 2007-07-17
Spaces, no tabs! 4 spaces for indentation. I program mostly in Java, and I do the same for XML, HTML, JavaScript, Ruby etc.

---

### Post by rjfioravanti on 2007-07-17
what programs do people view code in that need to have spaces instead of tabs?

The great thing about tabs is I can set my tabs to display at whatever width I like, and my teammates can set their tabs to display however they like. So if I like 2 spaces and my teammates like 4, everyone is happy

I'm pretty sure you can't achieve this with spaces

---

### Post by Ramses de Norre on 2007-07-17
Hard tab, 4 spaces, I like being able to easily indent/unindent the code and that everyone can choose his own preferred tab width.

---

### Post by LaRoza on 2007-07-17
4 spaces/tabs as spaces

I do this because I use the same files in many text editors, on different operating systems. I used to only use three spaces, but I changed to four after realizing most others used four.

---

### Post by Occasionally Correct on 2007-07-17
I didn't always have auto-indentation, and I still don't at times, so coding anything with space-indents is just out of the question! :p My preference is tab-indentation with a 4-space width.

As for the rest of my style, aks44 summed it up pretty well! :)

---

### Post by max.diems on 2007-07-18
Spaces allow for easier copying to another program. But if some people want to ignore that problem, then I'll still read their code.

---

### Post by crashie on 2007-07-18
2 spaces unless I'm coding in some language like Java where there's a standard on how you should indent.

When I have very long statements I usually indent parts of the statement too:
```
if ((code code code...) ||
    ((code code code...) && (code code code...) &&
     (code code code...)) ||
    (code code code...)) {
  do(very long line....,
     second line);
  something();
}
```

---

### Post by Ramses de Norre on 2007-07-19
> **crashie said:**
> 2 spaces unless I'm coding in some language like Java where there's a standard on how you should indent.

When I have very long statements I usually indent parts of the statement too:
```
if ((code code code...) ||
    ((code code code...) && (code code code...) &&
     (code code code...)) ||
    (code code code...)) {
  do(very long line....,
     second line);
  something();
}
```

If you're boolean expression is already 4 lines long, I think it's reasonable to extract it to a separate method/function.

---

### Post by amo-ej1 on 2007-07-19
4 spaces like any sane person would use ;)

---

### Post by 7Priest7 on 2007-07-19
I use 3 spaces to indent (exept when I am using scite)(when I use scite I use 2)

I prefer 3 spaces because that is of religous importance

[http://en.wikipedia.org/wiki/3_(number)#Abrahamic_religions](http://en.wikipedia.org/wiki/3_(number)#Abrahamic_religions)

Alex

---

### Post by vexorian on 2007-07-31
> **Paul820 said:**
> I use a tab of 4, tab is replaced with spaces to be consistent with other text editors that are used to view the source. A lot of editors have different sized tabs so using spaces is much better i think.
yep

---

### Post by bogolisk on 2007-07-31
> **rjfioravanti said:**
> what programs do people view code in that need to have spaces instead of tabs?

The great thing about tabs is I can set my tabs to display at whatever width I like, and my teammates can set their tabs to display however they like. So if I like 2 spaces and my teammates like 4, everyone is happy

I'm pretty sure you can't achieve this with spaces

Well, that's because you use a crappy editor. With a decent editor you can do much more. My editor can switch indentation style (k&r, linux-kernel, whitesmith, ...)

I'd rather have all spaces or all tabs. Mixing is stupid.

---

### Post by Note360 on 2007-07-31
I use 4 spaces for everything now except Ruby and HTML (both have 2 spaces)

I usually use a sort of style guide for myself.
[B]
variables[/B] 
scalar: a_b
array: a_b*s* (plural form usually)
hashes: a_bs (same as array)

classes: ThisIsAClass (Upper case. I usually try to sum it up in One Word if possible)
methods: thisIsAMethod
functions: this_is_a_function (usually try to make it a natural read over to the arguments)

---

### Post by nanotube on 2007-09-02
i used to use 4 spaces, but then i switched to 4-width tabs.
the thing is, if i use actual spaces, and someone else is reading the code and likes to see 2-space indents, well, he's out of luck. if the file uses actual tabs, he just sets his editor to use 2-width for tabs, and he's all set.

so, tabs are more flexible. i just don't see the advantage of using spaces instead of tabs.

---

### Post by ssam on 2007-09-02
tabs, then it is the veiwers preference how wide to make them.

using 4 spaces seems like doing a pretend tab. (like when you see someone ina word processor using a hundreds of spcaes to manually right-align or center a paragraph).

i am a python user, and i aim to use PEP8 with tabs

---

### Post by Wybiral on 2007-09-02
> **ssam said:**
> using 4 spaces seems like doing a pretend tab.

Yes, but those pretend tabs will ALWAYS be the same size, not matter how big the  editors native tab size is (because it varies so much, spaces ensure that your code remains consistent in size).

---

### Post by Compyx on 2007-09-02
I use 4 spaces to indent code, and no more than 78 chars per line. That way my code looks consistent in whatever program I use to view it and I can also hack on it in a terminal emulator.

This also has the added benefit of keeping the proper indentation when posting on Usenet (although I then keep the line-length under 70 chars).

And to those who think using spaces makes it hard to re-indent your code: use a decent editor such as Vim.

---

### Post by CptPicard on 2007-09-02
> **Wybiral said:**
> (because it varies so much, spaces ensure that your code remains consistent in size).

Why does it need to remain consistent in size? You're communicating the code to others, not your indentation size. Layout is secondary to meaning, and marking a one indent stop with a single tab character seems to me to be economical and flexible. If you want to alter a spaced-out indentation, you need to do much more work with either the editor or manually.

I'm in the 4-width tab camp myself for these reasons... it also makes editing quicker. To take back an indent, you simply delete a tab, instead of counting spaces (or hitting some special editor key combination).

---

### Post by Nekiruhs on 2007-09-02
I use 4 space tabs, converted to spaces on the fly. Its so much easier to hit tab once than spacebar 4 times. And it does the same thing.

---

### Post by cb951303 on 2008-02-19
tab with true 4 space

---

### Post by Zwack on 2008-02-19
6 spaces at the start of the line and then two spaces for indents because you only have so much room on your 80 column punch cards, particularly as you have to stop at column 72...

OK I've never actually used punch cards but Fortran 77 demands certain formats and so...   :-)

Z.

---

### Post by LaRoza on 2008-02-19
> **Zwack said:**
> 6 spaces at the start of the line and then two spaces for indents because you only have so much room on your 80 column punch cards, particularly as you have to stop at column 72...

OK I've never actually used punch cards but Fortran 77 demands certain formats and so...   :-)

Z.

When I first learned Fortran 77, I didn't understand why such columns were used. I bought two old books on it, and neither of them even mentioned the columns.

I thought it was odd, until I got to the chapter on using the punch cards.

---

### Post by yabbadabbadont on 2008-02-19
> **LaRoza said:**
> When I first learned Fortran 77, I didn't understand why such columns were used. I bought two old books on it, and neither of them even mentioned the columns.

I thought it was odd, until I got to the chapter on using the punch cards.

Don't forget the coding sheets.  Indispensable back in those days, as very few people had hand held calculators in their homes, let alone a computer with an editor.  A computer in your home?!?  What are you smoking?  :lol:

---

### Post by LaRoza on 2008-02-19
> **yabbadabbadont said:**
> Don't forget the coding sheets.  Indispensable back in those days, as very few people had hand held calculators in their homes, let alone a computer with an editor.  A computer in your home?!?  What are you smoking?  :lol:

What is a coding sheet?

Keep in mind I have had a computer for about one year, and there was never a computer in the home when I grew up.

I did use a manual typewriter for some school assignments, because it worked and I liked it. The teachers thought I was...odd.

---

### Post by yabbadabbadont on 2008-02-19
> **LaRoza said:**
> What is a coding sheet?

Keep in mind I have had a computer for about one year, and there was never a computer in the home when I grew up.

I did use a manual typewriter for some school assignments, because it worked and I liked it. The teachers thought I was...odd.

[http://en.wikipedia.org/wiki/Image:FortranCodingForm.agr.jpg](http://en.wikipedia.org/wiki/Image:FortranCodingForm.agr.jpg)

I doubt that you can even find them any longer.  Too bad.  In the days when you had to write out your program by hand on a coding form, people tended to spend a lot more time on the design before writing any code.  The back of the sheets were also handy for drawing your flowcharts using your handy-dandy flowcharting drafting template.  (I think I've still got one around here somewhere...)

---

### Post by Zwack on 2008-02-19
I have an 80 column punch card which has been laminated for use as a bookmark somewhere around here...

I also used to have the parts to an Olivetti A1 Accounts computer complete with magnetic card reader...  They basically took an 80 column punch card and added a strip of 3/4" magnetic tape down one side.  Thus you have the 80 column magnetic card... :D

Remembering the punch cards makes a lot more sense out of Fortran 77.  When you look at things like the COMMON block it is clear why you would want the shared storage on the same card... :)

Z.

---

### Post by jyaan on 2008-12-23
I generally use 4 space tabs when I write personal code because I write my own Makefiles by hand, and make will throw an error if you try to use spaces instead. If it's with other people, I'll use whatever the guidelines are. I also prefer K&R.

---

### Post by Coder543 on 2008-12-23
Allman style all the way. ([http://en.wikipedia.org/wiki/Indent_style#Allman_style_.28bsd_in_Emacs.29](http://en.wikipedia.org/wiki/Indent_style#Allman_style_.28bsd_in_Emacs.29))

---

### Post by Kazade on 2008-12-23
I use tabs for indent, spaces for layout e.g.

```


void someFunction() {
____if (something > someOtherFunction(arg0, arg1,
____..................................arg2, arg3)) {
____// Do something
____}
}


```

Hmm.. not a great example, but you get the point. No matter what the tabsize everything stays lined up. I usually use a tabsize of 4 in my editor, but sometimes I drop back to 2.

---

### Post by pelle.k on 2008-12-29
No matter what you use, i find these two CLI tools very handy:
**expand** - Convert blanks in each FILE to tabs
**unexpand** - Convert tabs in each FILE to spaces

Using "External tools" plugin you may create scripts to replace only marked regions in gedit, for these times when cutting and pasting text from resources on the internet, or convert whole files to comply with your, or somebody elses standard regarding tabs and spaces.
You may want to be careful with corner cases as the one above, when mixing tabs and spaces to "beautify" code though.

---

### Post by catchmeifyoutry on 2008-12-29
> **7Priest7 said:**
> I use 3 spaces to indent (exept when I am using scite)(when I use scite I use 2)

I prefer 3 spaces because that is of religous importance

[http://en.wikipedia.org/wiki/3_(number)#Abrahamic_religions](http://en.wikipedia.org/wiki/3_(number)#Abrahamic_religions)

Alex

You're kidding, right?

4 spaces, of course I just use the tab key on my keyboard but vim replaces it by spaces. Backspace on indentation spaces removes all 4 of them, as if there is a tab. The problem without tab replacement for me is that I sometimes align stuff quickly with spaces and then you can easily combine tabs with spaces in the source file.

---

### Post by Greyed on 2008-12-29
Cripes, someone necroed but, darn it, I gotta answer this one...

> **CptPicard said:**
> Why does it need to remain consistent in size? You're communicating the code to others, not your indentation size. Layout is secondary to meaning

Layout and meaning are sometimes synonymous because layout can convey meaning.  If that weren't true why are we indenting at all?  The indentation denotes meaning.  And since indention doesn't always fall on our preferred boundary and almost certainly does not fall on someone else's the only consistent manner to indent is spaces.

> I'm in the 4-width tab camp myself for these reasons... it also makes editing quicker. To take back an indent, you simply delete a tab, instead of counting spaces (or hitting some special editor key combination).You mean like backspace?  Single.  vim is a wonderful editor in that regards.  :P

For the record, 4 spaces, no tabs **ever**, and if the language requires braces the opening brace is on the same line as the opening statement, closing brace lined with the statement it is closing.  Ergo:

[php]
while cooking {
    if spam != ham {
        eat_spam();
    }
}
[/php]Since the closing brace lines up with what it is closing it's easy to see where that block ends.  For people who need to know where the opening brace is they can bounce on the # key... or get a real editor and bounce on its match brace key.  If this style seems weird remove the closing braces, change the opening to colons and guess what you get?

[php]
while cooking:
    if spam != ham:
        eat_spam()
[/php]Mmmm, Python.  And people think it's indention to denote block structure is wierd.  Pft.

---

### Post by nvteighen on 2008-12-29
> **Greyed said:**
> 
...The indentation **denotes meaning**...

AHH!!! GeneralLinguisticsError Exception thrown!! :D

Meaning is the semantical value of some piece of language within the abstraction the language performs of the world. In other words: it's a language-specific feature, so you have in English "black" but in Latin "niger" ('bright black') and "ater" ('opaque black')... though with the word 'black' you're able to refer/denote the same reality that a Roman would have by using "ater" or "niger". (FYI: the convention of quotes in Linguistics is " " = word; ' ' = meaning)

Denotation/Reference is just the real object a meaning is able to refer to.

This difference is very interesting for programming languages. As logical languages, they rely mostly on denotational elements, e.g. a variable is always a reference, never a meaning. And also anything you give a name will be just a denotation device...

The problem/point of interest (;)) is that programming languages are able to build up meaning-structures from pure initial denotation. For example, an API is actually a description of a bunch of functions' meanings, no matter what implementation ("reality") is referred by the bare reference "gtk_window_new()", the important thing to know is what that function does, opposed to e.g. "gtk_widget_destroy()". This is what makes programming languages different to mathematical notations, where there's no place for meaning.

Ok, so back to programming: Indentation **in Python** is meaningful, not denotationful, as it is relevant to the language itself. Its reference may vary in the code... 4 spaces in a place will not necessarily refer to the same "reality" that elsewhere.

> Mmmm, Python.  And people think it's indention to denote block structure is wierd.  Pft.

Well, it is weird... most languages don't do this. But "weird" doesn't mean 'bad', does it? ;)

---

### Post by Greyed on 2008-12-29
> **nvteighen said:**
> AHH!!! GeneralLinguisticsError Exception thrown!! :D

Cripes, one wrong choice of words and the linguist comes with bats-a-swingin'!  :o

My intent was to refute CptPicard's notion that indention did not provide any meaning to the code.  To the computer indentation means nothing in most languages.  But he was talking about meaning to the programmer.  To the programmer indention does have meaning.  It is used to conceptually group instructions and provide structure to the text.  If anyone believes structure does not convey meaning then I ask them to read this paragraph as repeated below.

> 
my intent was to refute CptPicards notion that indention did not provide any meaning to the code to the computer indentation means nothing in most languages but he was talking about meaning to the programmer to the programmer indention does have meaning it is used to conceptually group instructions and provide structure to the text if anyone believes structure does not convey meaning then I ask them to read this paragraph as repeated below



> Ok, so back to programming: Indentation **in Python** is meaningful, not denotationful, as it is relevant to the language itself. Its reference may vary in the code... 4 spaces in a place will not necessarily refer to the same "reality" that elsewhere.

Agreed.  And so, too, does that reinforce the notion that indention is providing meaning for the programmer.  That is the answer to CptPicard's 2 year old question of why one would want to have consistent indentation rather than locally variable indentation.

> Well, it is weird... most languages don't do this. But "weird" doesn't mean 'bad', does it? ;)

To most people it does.  It is the most often cited problem with Python even though if people would spend 1/100th the time using it that they do complaining about it they would realize it is as natural, if not more so, than any language that requires braces.

---

### Post by skullmunky on 2009-01-03
I usually use 4-space tabs, and go for tabs rather than spaces to make it easier to unindent.  

I use Kate, and my one frustration is I'm mostly using python now, and if I want to bring in other people's code it's usually formatted in spaces.  Kate can convert to tabs, with pretty good success; but actually I also wouldn't mind sticking with spaces if it could smartly unindent.  A couple posts back someone mentioned that vim will do this (backspace to unindent 3, 4, or 8 spaces, whatever).  Not surprising, as we all know, vim is the only real editor ;) but anyone know if the same can be done in kate?

---

### Post by jpkotta on 2009-01-04
I use 4 spaces.  That way it always looks right.

I also use Xemacs.  I can't find a better indentation system.  It isn't hard to automatically reformat code to use tabs if necessary.

Ideally, the format would be tabs to indent for structure, spaces to indent for formatting.  tab = '----', space = '.'
```

if (is_foo
..&& is_bar) {
----foobar();
}
```

Unfortunately, editors aren't very smart, and can't tell which one you want.

---

### Post by nanotube on 2009-01-06
> **skullmunky said:**
> I usually use 4-space tabs, and go for tabs rather than spaces to make it easier to unindent.  

I use Kate, and my one frustration is I'm mostly using python now, and if I want to bring in other people's code it's usually formatted in spaces.  Kate can convert to tabs, with pretty good success; but actually I also wouldn't mind sticking with spaces if it could smartly unindent.  A couple posts back someone mentioned that vim will do this (backspace to unindent 3, 4, or 8 spaces, whatever).  Not surprising, as we all know, vim is the only real editor ;) but anyone know if the same can be done in kate?

you could try something like geany or scite, they are smart enough to kill 4 spaces with one backspace. (though i suspect kate may be configured to do that as well). geany also does calltips, and gives you the class hierarchy in the sidebar... so try geany. :)

---

### Post by doorman on 2009-01-06
I use a strict 2-spaces tab only! Make it much easier to navigate and/or (un)indent code simply by pressing a tab or a backspace :)

---

### Post by Greyed on 2009-01-06
Are you, by chance, a perl hacker?

---

### Post by SunSpyda on 2009-02-18
I use a 4-space tab for everything, no matter what the language.

I do this for C, C++, IA32 (32bit Assembly with Intel Syntax.) , BASIC, BASH, and everything else.

8-space tabs I find are too large, especially when I need to compile and/or edit them on a command line OS.

4-space tabs I find are enough to lay out the code properly, but not enough to waste space.

I use Vi as my editor, but I should really download Vim, since Vi's lack of highlighting is starting to get annoying.

---

### Post by jimi_hendrix on 2009-02-18
whatever vim does (8 spaces i think) is fine

---

### Post by Tibuda on 2009-02-18
Other: Spaces for indents, 2 spaces.

---

