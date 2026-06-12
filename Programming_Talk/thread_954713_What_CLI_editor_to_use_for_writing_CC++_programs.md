---
title: "What CLI editor to use for writing C/C++ programs?"
date: 2008-10-21
forum: Programming Talk
---

### Post by Sycron on 2008-10-21
As far as I see I can definitely write programs faster with just the console. So I'm searching for a simple console text editor with syntax highlighting . I tried jed but there sure must be another editors...

Can you help me? Thanks!

---

### Post by jespdj on 2008-10-21
Nano, Emacs, Vi

---

### Post by Sorivenul on 2008-10-21
Vim, Emacs, or FTE.
If you're looking for a "console IDE" of sorts for C/C++, there is Motor.

---

### Post by Sycron on 2008-10-21
Thanks for fast replies. I like a lot nano, but how do I set it to C/C++ Syntax Highlighting ?

---

### Post by pokerbirch on 2008-10-21
I know this is slightly off topic but have you tried Code::Blocks IDE?

---

### Post by Sycron on 2008-10-21
> **pokerbirch said:**
> I know this is slightly off topic but have you tried Code::Blocks IDE?

Yes, and I'm still using it, but like I said, I like very much the console, so with not to use it ?

---

### Post by Sycron on 2008-10-21
> **Sorivenul said:**
> Vim, Emacs, or FTE.
If you're looking for a "console IDE" of sorts for C/C++, there is Motor.

I can't find motor in synaptic, neither on Google.

Wow, I have syntax highlighting in nano and is great, is not a complicated one but it just work.

---

### Post by LaRoza on 2008-10-21
Vim, is the best.

Run:

```

sudo aptitude install vim

```

This will probably be moved to recurring discussions later...

 [img]http://www.mysmiley.net/imgs/smile/sign/sign0083.gif[/img]

---

### Post by CptPicard on 2008-10-21
> **Sycron said:**
> Thanks for fast replies. I like a lot nano, but how do I set it to C/C++ Syntax Highlighting ?

Nano is extremely simplistic... try a proper editor like Emacs instead.

An oh yes, don't listen to those vi fanboys, they are corrupted souls.

---

### Post by nvteighen on 2008-10-21
> **LaRoza said:**
> Vim, is the best.

Run:

```

sudo aptitude install vim

```

This will probably be moved to recurring discussions later...

 [img]http://www.mysmiley.net/imgs/smile/sign/sign0083.gif[/img]
Emacs, is the best.

Run:

```

sudo apt-get install emacs22

```

:D

(Seriously, try some alternatives and choose whatever fits better to you)

---

### Post by LaRoza on 2008-10-21
> **CptPicard said:**
> Nano is extremely simplistic... try a proper editor like Emacs instead.


I think the OP uses Linux, not E***s. Vim is the best editor, although E***s does have a Vim like mode, there is no need to use that operating system to run Vi.

---

### Post by LaRoza on 2008-10-21
[img]http://www.bemroses.net/images/curves.jpg[/img]

---

### Post by SeanHodges on 2008-10-21
> **LaRoza said:**
> I think the OP uses Linux, not E***s. Vim is the best editor, although E***s does have a Vim like mode, there is no need to use that operating system to run Vi.

Actually, I hear you can run Linux inside Emacs now: M-Powerbutton M-Powerbutton :)

[IMG]http://imgs.xkcd.com/comics/real_programmers.png[/IMG]

---

### Post by samjh on 2008-10-21
Vim for the win! :p

```
sudo apt-get install vim
```

To set up syntax highlighting and indenting, create a file in your home directory and name it .vimrc, then open it using vim:
```
vim .vimrc
```

To edit, press the [I] key to switch to "insert mode", and type these:
```
:set nu
:syntax on
:filetype plugin indent on
```
Then press the [Esc] key to switch to "command mode", and type this to save and quit:
```
:wq
```

Next time you open Vim, you'll have line numbers on the left-hand side, and the syntax highlighting and indenting will be adjusted according to the type of file opened.

My Vim command reference for beginners: [http://ubuntuforums.org/showthread.php?t=564554](http://ubuntuforums.org/showthread.php?t=564554)

---

### Post by snova on 2008-10-21
> **LaRoza said:**
> [img]http://www.bemroses.net/images/curves.jpg[/img]

The most important thing to notice here is that the peak of Emacs is slightly higher than that of Vim. It can therefore do more. Also note that the power of Emacs is sufficient to warp an unsuspecting hacker's mind, whereas an encounter with Vim is not dissimilar to that of an unhelpful brick wall.

All jokes aside, I personally have no interest in learning the myriad of key combinations Emacs uses, although I wish the escape key was a little easier to reach in Vim. When I use either one of them, that is.

I wonder- if somebody were to take a poll, would there be a correlation between those that favor Lisp as a language and those that use Emacs as an editor?

---

### Post by klange on 2008-10-21
Nano/pico "just plain works". While you vim and emacs people kill each other over which editor is better, we've already written our code, compiled it, and pushed it to git. Plus, most modern text editors (even those with the whole vi thing with having ~'s on new lines) are basically just derivatives of pico.

---

### Post by Sorivenul on 2008-10-21
> **WindowsSucks said:**
> Nano/pico "just plain works". While you vim and emacs people kill each other over which editor is better, we've already written our code, compiled it, and pushed it to git. Plus, most modern text editors (even those with the whole vi thing with having ~'s on new lines) are basically just derivatives of pico.

I think any of the editors "just plain work", but the purposes they serve are different.  I can easily use pico/nano for simple config file editing, but when I need a workhorse, vim or emacs would be my pick.  

Trying to compare the features of pico/nano to those of either vim or emacs is like comparing a bicycle to an sportscar.

---

### Post by LaRoza on 2008-10-21
> **snova said:**
> The most important thing to notice here is that the peak of Emacs is slightly higher than that of Vim.
Yes, but what more it can do has nothing to do with text editing.

> 
 It can therefore do more. Also note that the power of Emacs is sufficient to warp an unsuspecting hacker's mind, whereas an encounter with Vim is not dissimilar to that of an unhelpful brick wall.

Emacs can do a lot, true. However, Vim can edit files and edit well. I don't need to run a Lisp machine to do that.

> 
All jokes aside, I personally have no interest in learning the myriad of key combinations Emacs uses, although I wish the escape key was a little easier to reach in Vim. When I use either one of them, that is.

Vi was designed back when the Esc key was where the Caps Lock key is. Most people, that know about it, remap their Caps lock to be Esc. Caps Lock has to be one of the most useless keys and in the wrong area.

> 
I wonder- if somebody were to take a poll, would there be a correlation between those that favor Lisp as a language and those that use Emacs as an editor?
Yes, sort of. You'll find that Lisp/Scheme hackers use Emacs a lot, even if they don't use it for anything else.

---

### Post by slavik on 2008-10-22
corrupted fanboys don't have the power to ban people ... ;)

VIM or bust! :P

---

### Post by cardinals_fan on 2008-10-22
Vim.  Emacs is a very worthy operating system, but it's rather weak as an editor.

/flame-war

---

### Post by Sycron on 2008-10-22
I like you when you fighting for giving advices, I like that idea that almost everyone come here and post what's the best for him/her.

So, I read all that posts, and thank you very much. I'm going to use vim, since it requires 22MB to install. Syntax highlighting is exactly WHAT I WANT and is kewl.

Emacs is big, 66MB and on my eeepc and I can't afford that.

Now I have to read some tutorials to start, I like a lot the interface of vim. How can I compile my programs from vim ? Do I have a Sheel Window or something like that ?

---

### Post by LaRoza on 2008-10-22
> **Sycron said:**
> I like you when you fighting for giving advices, I like that idea that almost everyone come here and post what's the best for him/her.

What did you expect? It isn't advice so much as doctrine.

> 
So, I read all that posts, and thank you very much. I'm going to use vim, since it requires 22MB to install. Syntax highlighting is exactly WHAT I WANT and is kewl.

Vi(m) is usually pre-installed on all *nix machines as well. Not having it is very, very rare.

> 
Emacs is big, 66MB and on my eeepc and I can't afford that.

Takes up ram too. 

> 
Now I have to read some tutorials to start, I like a lot the interface of vim. How can I compile my programs from vim ? Do I have a Sheel Window or something like that ?

You can compile from vim, but it is better, IMO to either use screen or another terminal to do the compile and running. If you are using pure CLI (no X), I suggest using the virtual terminals for this. My wiki had guides for Vim.

---

### Post by Sycron on 2008-10-22
> **LaRoza said:**
> 
Vi(m) is usually pre-installed on all *nix machines as well. Not having it is very, very rare.

Well, syntax highlighting didn't work. After I installed vim everything was fine.

---

### Post by LaRoza on 2008-10-22
> **Sycron said:**
> Well, syntax highlighting didn't work. After I installed vim everything was fine.

Yes, I know.

Debian (and therefore Ubuntu) use vim-tiny as the default Vim package, "vim" has the features that are missing (which are often found by default in other distros) and "vim-full" has even more (including, gvim, a gui vim version which I never use)

---

### Post by SeanHodges on 2008-10-22
> Now I have to read some tutorials to start, I like a lot the interface of vim. How can I compile my programs from vim ? Do I have a Sheel Window or something like that ?

With Vim, you have a number of options:

1) Keep a separate terminal window/screen session open for compiling in (as has already been suggested).

2) use the :shell command to bring up a shell session, you can drop back into Vim by typing "exit".

3) Use :! to execute a one-line command, e.g. ":!make" will run make in the working directory.

4) As an extension to (3), you can use a plug-in like [Shell.vim]("http://vim.sourceforge.net/scripts/script.php?script_id=118") to emulate a shell session in a Vim buffer.

I also tend to prefer (1) and occasionally (3), but it's nice to know the other options are available.

---

### Post by kcode on 2008-10-22
> **LaRoza said:**
> 


Vi was designed back when the Esc key was where the Caps Lock key is. Most people, that know about it, remap their Caps lock to be Esc. Caps Lock has to be one of the most useless keys and in the wrong area.


how can i do this??

---

### Post by boz on 2008-10-22
You can do :make from within vim and it will run your Makefile, as long as it's in the same directory, of course.  If you do it this way, it will bring you do the line of code where the compiler found the first error, if any.

---

### Post by LaRoza on 2008-10-22
> **kcode said:**
> how can i do this??

Create a .Xmodmap file in your $HOME.

Add these two lines:
```

remove Lock = Caps_Lock
keysym Caps_Lock = Escape

```
Run:
```

xmodmap ~/.Xmodmap

```

---

### Post by Christmas on 2008-10-22
If you like Nano, you can enable syntax highlighting by doing this:

Create a text file inside your home directory, ~/.nanorc and copy/paste this line of text into it:

include "/usr/share/nano/c.nanorc"

Save it and restart Nano and that's it.

---

### Post by nvteighen on 2008-10-22
> **snova said:**
> 
I wonder- if somebody were to take a poll, would there be a correlation between those that favor Lisp as a language and those that use Emacs as an editor?

Possibly because you can embed a Lisp interpreter very easily into Emacs... though it also supports Python.

---

### Post by LaRoza on 2008-10-22
> **nvteighen said:**
> Possibly because you can embed a Lisp interpreter very easily into Emacs... though it also supports Python.

Emacs is a Lisp machine and the REPL is used as a text editor.

---

### Post by nvteighen on 2008-10-22
> **LaRoza said:**
> Emacs is a Lisp machine and the REPL is used as a text editor.
Yeah... I can live with that. :)

---

### Post by Sycron on 2008-10-22
Hey guys, I tried this and I don't know why it doesn't work.
```
#include <iostream>
using namespace std;

int main(int argc,char **argv) {
  if (argv[1]=="--try") cout << "hi!"; else cout << "Failure!";
cout << "\xA";
return 0;}
```

When I type: ```
./a.out --try
``` I get "Failure!" on screen.

---

### Post by CptPicard on 2008-10-22
You're comparing char pointers in your argv[1] == "...", not string contents. Use C++ string equality comparison instead...

---

### Post by Sycron on 2008-10-22
And what is that ? Write a very simple example, please. Why **char **argv** isnt equal to char **argv[][]** ? Or it is ?

---

### Post by CptPicard on 2008-10-22
I guess the simplest demo would be

```

#include <string>
#include <iostream>

using namespace std;

int main(int argc, char **argv) {
  if (string(argv[1]) == "foo")
    cout << "OK" << endl;
}

```

std::string has an overloaded comparison operator for both C-style null-terminated char-array strings and other string objects. You can't compare C-style string *contents* by simply comparing pointers to the first character, which you were trying to do.

---

### Post by Sycron on 2008-10-22
AWESOME , thanks!
> You can't compare C-style string contents by simply comparing pointers to the first character, which you were trying to do.
Can you give me an example of what I was comparing exactly? maybe I will understand better if you tell me so. Thank you again.

I don't know for what reasons but **string()** function works without **#include <string>**

---

### Post by motang on 2008-10-22
> **Sycron said:**
> As far as I see I can definitely write programs faster with just the console. So I'm searching for a simple console text editor with syntax highlighting . I tried jed but there sure must be another editors...

Can you help me? Thanks!
I got introduced to VIM when I started my bacholer's degree so that is what I use.  Some of my classmates moved on emacs or to nano but I stuck with VIM, I feel the most comfetable with it.

---

### Post by Sycron on 2008-10-22
Great to hear that, all my mates are STICK with that blue borland C++ 3.1 which is twenty years old.

---

### Post by CptPicard on 2008-10-22
> **Sycron said:**
> 
Can you give me an example of what I was comparing exactly? maybe I will understand better if you tell me so. Thank you again.

Read up on how C-style strings work. They are character arrays, which are terminated by the null character '\0'.

Exactly for the same reason for which you can't compare array contents for equality by comparing pointers to the first element, you can't compare string contents like that, either. You'd have to essentially go through the array one by one and compare each item in turn.

This is, btw, what the C function strcmp does, which you would have had to use if you were doing C. But this time we went through the string equality comparison operator, because it's more proper C++.

> 
I don't know for what reasons but **string()** function works without **#include <string>**

Ok, perhaps string is then in the stdlib these days... I don't actually use C++ actively so I don't really know.

---

### Post by snova on 2008-10-22
> **LaRoza said:**
> Create a .Xmodmap file in your $HOME.

Add these two lines:
```

remove Lock = Caps_Lock
keysym Caps_Lock = Escape

```
Run:
```

xmodmap ~/.Xmodmap

```

I was hoping somebody would ask that. It's right by my pinky now... my only complaint is that it's global rather than vim-specific, but I don't use it anyway, I guess.

As if my computer wasn't already hostile to non-technical people. :) "Oops, I forgot to mention I remapped the keyboard..."

Will I only have to run xmodmap once? Or every time I start X?

---

### Post by LaRoza on 2008-10-22
> **snova said:**
> I was hoping somebody would ask that. It's right by my pinky now... my only complaint is that it's global rather than vim-specific, but I don't use it anyway, I guess.

As if my computer wasn't already hostile to non-technical people. :) "Oops, I forgot to mention I remapped the keyboard..."

Will I only have to run xmodmap once? Or every time I start X?

It does it automatically I think (that file is run when X starts, since you made/changed it, you had to manually do it).

Caps Lock is rarely used (on purpose) and in the wrong spot I think. You can remap your Esc to be Caps Lock...

---

