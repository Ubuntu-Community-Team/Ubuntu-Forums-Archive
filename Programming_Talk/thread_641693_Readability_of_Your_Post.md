---
title: "Readability of Your Post"
date: 2007-12-15
forum: Programming Talk
---

### Post by Majorix on 2007-12-15
I from time to time notice bad examples of code pasted from an editor/IDE, with a horrible rate of readability. I want to help the people in question, but am greatly held back. Consider this simple Hello World example, pasted horribly, less horribly, better and very good:

Firstly, there is this. I can't find words to describe the beauty of it, so I leave it to you to comment:
#include <iostream>
using namespace std;
int main()
{
   cout << "Hello world!";
   return 0;
}

Then there is this, the above code just > 'ed. Still terribly bad looking:
[quote]#include <iostream>
using namespace std;
int main()
{
   cout << "Hello world!";
   return 0;
}

And some people quote their code in the misleadingly-titled ```
 tags:
[code]#include <iostream>
using namespace std;
int main()
{
   cout << "Hello world!";
   return 0;
}
```
The above code looks significantly better compared to the other two, but still, there is something missing, which the following wrap demonstrates:
[PHP]#include <iostream>
using namespace std;
int main()
{
   cout << "Hello world!";
   return 0;
}[/PHP]

Just observe the magic. Indentation is just like you saw in your fav text editor. include statements have a different color, punctuation marks have a different color, return statements, strings, the rest; all is differently colored. All in all, the readability is greatly improved.

The magic described above just demands of you to simply include the wrappers [ PHP] [ /PHP] without the leading whitespaces while quoting a code.

I just felt the absence of a thread that would lead people to write readable code, so I wrote these.

Now I ask of you, which style do you prefer? Please use that in your posts from now on and make your friends and fellow Ubuntuers do it too.

EDIT: I thought I would ask of you friendly people that you include error outputs (if any) with your code, instead of just saying that the compiler/interpreter outputs errors.

When you post the error output, make sure you mark the faulty lines in your code. Usually the compiler points out these lines to you, so all you have to do is add a comment at the end of it marking it. DON'T post without the markings or it won't do any good.

It makes the job for people who want to help you MUCH easier.

---

### Post by LaRoza on 2007-12-15
This needs to get out, use [ code ] tags or [ php ] tags. I prefer php tags, they work with most languages, and make things easier for readers.

This thread has been added to the sticky I authored.

[SIZE="2"]Language Test[/SIZE]
C, Perl and Python

[php]
/*In C*/
#include <stdio.h>

int main(int args,char ** argv)
{
    printf("%s","Hello world");
    return 0;
}
[/php]

[php]
#! /usr/bin/perl
# In Perl
use strict;

main();

sub main
{
     print "Hello world";
}
[/php]

[php]
#! /usr/bin/python
# In Python
main()

def main():
    print "Hello world"
[/php]

---

### Post by Majorix on 2007-12-15
Thanks for adding it to your sticky, I will also be adding it to my sig so it would get more readers :)

---

### Post by LaRoza on 2007-12-15
> **Majorix said:**
> Thanks for adding it to your sticky, I will also be adding it to my sig so it would get more readers :)

Add the sticky, and get many issues at once.

---

### Post by Majorix on 2007-12-15
OK I have added a link to your sticky too, hope we help some people out.

---

### Post by samjh on 2007-12-16
What other syntax does vBulletin support?  Perhaps it might be worthwhile asking the administrators to add support for more programming language syntax.

[EDIT]

Looking at this thread: [http://ubuntuforums.org/showthread.php?t=343317](http://ubuntuforums.org/showthread.php?t=343317) , it seems such support is complex and not affordable.

---

### Post by Compyx on 2007-12-16
I refuse to use php-tags around code that isn't php, in my opinion this only adds confusion.

It should be possible to hack the vBulletin sources to add syntax highlighting for other languages, PEAR has a nice package: [http://pear.php.net/package/Text_Highlighter](http://pear.php.net/package/Text_Highlighter)

(I just noticed something horrible: vBulletin is commercial software, why the hell does Ubuntu use this?)

If html code were allowed, it would be trivial to add syntax highlighting to just about any language on the planet: Vim.
Vim can export syntax highlighted code to html, so you can just copy/paste your code from Vim to these forums.

Unfortunately I can't find the option to turn html code on, so I guess I'll have to write a script that highlights code with bbCode tags. Perhaps I'll do this in PHP and put it on my website so other people can use it. Should be an interesting project.

---

### Post by samjh on 2007-12-16
> **Compyx said:**
> (I just noticed something horrible: vBulletin is commercial software, why the hell does Ubuntu use this?)

Already answered: [http://ubuntuforums.org/showthread.php?t=176622](http://ubuntuforums.org/showthread.php?t=176622) ;)

---

### Post by LaRoza on 2007-12-16
> **Compyx said:**
> I refuse to use php-tags around code that isn't php, in my opinion this only adds confusion.

(I just noticed something horrible: vBulletin is commercial software, why the hell does Ubuntu use this?)
.

What confusion? Is the word "Code" at the top more descriptive of the contents? People use the php tags know that that is the tag, not language.

Why is that horrible? It is the best tool for the job, and that is the whole idea. Ubuntu doesn't use it, UbuntuForums.org does.

---

### Post by TreeFinger on 2007-12-16
I never used the 'php' blocks because I thought it was just for PHP code. I would just use the 'code' blocks. I'll start using 'php' when pasting my C++ code from now on. Thanks for the tip.

---

### Post by DouglasAWh on 2007-12-16
I'm happy to tell everyone that my Perl or whatever is PHP if that's what we're to do, but I don't like it...

---

### Post by samjh on 2007-12-16
I don't like using PHP tags for non-PHP code.  It's misleading for those who do not know what PHP is, or the differences between PHP and other programming languages.  For experienced programmers, it doesn't matter.

---

### Post by Majorix on 2007-12-16
The PHP tag is just misleadingly-titled. Look at the CODE tag, does it have any syntax highlighting? What good is it for pasting hundreds of lines of object-oriented code?

---

### Post by LaRoza on 2007-12-16
> **Majorix said:**
> The PHP tag is just misleadingly-titled. Look at the CODE tag, does it have any syntax highlighting? What good is it for pasting hundreds of lines of object-oriented code?

I find it best for bash commands, but I asked for a fix:

[http://ubuntuforums.org/showthread.php?p=3964416#post3964416](http://ubuntuforums.org/showthread.php?p=3964416#post3964416)

---

### Post by dfreer on 2007-12-16
I noticed myself that when posting configuration files, that the CODE tag doesn't really allow you to "Tab" lines out, making them less readable. Thanks for letting me know about the PHP tag though!

---

### Post by Majorix on 2007-12-30
I have added a request/reminder for error outputs too, as so many people just say "the code produces errors" and then don't post what the errors are.

---

### Post by kool_kat_os on 2007-12-30
sorry...

---

### Post by wolfbone on 2007-12-30
One could always use a pastebin of course.

paste.lisp.org is especially good for CL and ELisp because it even provides links to the documentation of each symbol it recognises:
 
[http://paste.lisp.org/display/53308](http://paste.lisp.org/display/53308) 
[http://paste.lisp.org/display/53309](http://paste.lisp.org/display/53309)

...though the Emacs links seem to be broken atm.

---

### Post by Majorix on 2007-12-30
There is always the [Ubuntu Pastebin]("http://paste.ubuntu-nl.org/").

---

### Post by bkelly on 2008-01-27
Somewhere in the HOME page or at a high level within this site, put a link to a page that describes all the codes we can use in our posts. Provide example.  I found this thread and still am not certain how to use PHP and CODE codes.  

See about adding an option to Reveal the full text of a post without display interpretation.  When I see that someone has posted something that looks cool, I can select the Reveal option to see the codes that produced it.  I have found this very handy in other forums.

---

### Post by LaRoza on 2008-01-27
> **bkelly said:**
> Somewhere in the HOME page or at a high level within this site, put a link to a page that describes all the codes we can use in our posts. Provide example.  I found this thread and still am not certain how to use PHP and CODE codes.  

See about adding an option to Reveal the full text of a post without display interpretation.  When I see that someone has posted something that looks cool, I can select the Reveal option to see the codes that produced it.  I have found this very handy in other forums.

[noparse]
[php]
Put code here. All tags are opened then closed.
[/php]
[/noparse]

To see how I made that, click on the quote button, it will show my post with [noparse]>  [/noparse] tags.

---

### Post by Jessehk on 2008-01-28
I see no reason to mislabel code as being PHP for the sole benefit of pretty colours.

---

### Post by LaRoza on 2008-01-28
> **Jessehk said:**
> I see no reason to mislabel code as being PHP for the sole benefit of pretty colours.

Then don't do it.

Syntax highlighting is a very important feature of editors and the PHP tags are the only way to sanely get that effect.

We all have preferences, and a weird label for syntax highlighting is a good trade off sometimes.

---

### Post by thornmastr on 2008-01-28
I have always felt that behind the usually calm and intelligent  comments of LaRoza has been the visage of  "L'Enfant terrible" philosopher scratching at the back of his eyelids. I think the monster is beginning to peek forth. Hooray!

---

### Post by LaRoza on 2008-01-28
> **thornmastr said:**
> I have always felt that behind the usually calm and intelligent  comments of LaRoza has been the visage of  "L'Enfant terrible" philosopher scratching at the back of his eyelids. I think the monster is beginning to peek forth. Hooray!

I may be edgy at times, if you feel I am out of character, let me know. I have been knee deep in the Backyard and Religious debate issue at the moment.

---

### Post by Lord Illidan on 2008-01-29
Hey, I never noticed this..Excellent, will be using it. I also agree that the PHP tags are a bit of a misnomer. I also thought they were just for PHP code.

---

### Post by pmasiar on 2008-01-29
PHP tags could use parameter 'language', default PHP, so we could avoid misunderstanding. Colorization is fine for all C-like languages.

But forum software is closed source IIUC, so I guess slim chance having that... :-(

---

### Post by LaRoza on 2008-01-29
> **pmasiar said:**
> PHP tags could use parameter 'language', default PHP, so we could avoid misunderstanding. Colorization is fine for all C-like languages.

But forum software is closed source IIUC, so I guess slim chance having that... :-(

Actually, they can alter it, and they have many times. (The thanks feature is a hack)

---

### Post by technmom on 2010-06-11
Okay so I just broke this rule, but am not sure how to do code quotes.

---

### Post by uOpt on 2010-06-11
All these format boxes are useless, IMHO, if they don't have 80 chars text width.

---

### Post by dv3500ea on 2010-06-11
[This site]("http://www.challenge-you.com/bbcode") converts code in a very large number of languages into highlighted BBcode using the [code], [color] and [b] tags.

---

### Post by xsinsx on 2010-06-11
> **dv3500ea said:**
> [This site]("http://www.challenge-you.com/bbcode") converts code in a very large number of languages into highlighted BBcode using the ```
, [color] and [b] tags.

to demonstrate his find for this site i will post a bit and see how it turns out.

[code][color=#408080]*#!/usr/bin/python*[/color]
[color=#408080]*#Project Euler Problem 1 solution in python.*[/color]
[color=#408080]*#If we list all the natural numbers below 10. *[/color]
[color=#408080]*#that are multiples of 3 or 5, we get 3, 5, 6 and 9. *[/color]
[color=#408080]*#The sum of these multiples is 23.*[/color]
[color=#408080]*#Find the sum of all the multiples of 3 or 5 below 1000.*[/color]

x [color=#666666]=[/color] [color=#666666]0[/color]
[color=#008000]**for**[/color] i [color=#AA22FF]**in**[/color] [color=#008000]range[/color]([color=#666666]1[/color],[color=#666666]1000[/color]):
        [color=#008000]**if**[/color] i [color=#666666]%[/color] [color=#666666]3[/color] [color=#666666]==[/color] [color=#666666]0[/color] [color=#AA22FF]**or**[/color] i [color=#666666]%[/color] [color=#666666]5[/color] [color=#666666]==[/color] [color=#666666]0[/color]:
                x [color=#666666]=[/color] x [color=#666666]+[/color] i
                [color=#008000]**print**[/color] x, i

```


I think this is a new bookmark for me. This is very neat and solves a lot of the misconception and such that people were speaking of.

---

