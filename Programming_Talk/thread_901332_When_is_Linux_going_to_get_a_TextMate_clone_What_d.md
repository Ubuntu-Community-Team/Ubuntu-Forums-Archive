---
title: "When is Linux going to get a TextMate clone? What do you use?"
date: 2008-08-26
forum: Programming Talk
---

### Post by memories on 2008-08-26
I heard E-Text Editor is going to be ported to Linux. 

Looks promising, but I think vim is as powerful, if not more so, than TextMate.. but nearly all its power is hidden under a cryptic and complex layer that most people will never even scratch. 

I don't mind the learning curve, but my main gripe with vim is the fact that gvim feels like a pretty border around regular vim, instead of being a "real" GUI with GTK borders and such, instead of the (ugly) text-UI borders between windows. (see my 'vim setup' post also on this forum)

I know about Cream, but it's not much of an improvement for people not new to vim. There also doesn't seem to be any "package" that comes with some/all GUI plugins/features enabled and configured. This would be great!

What do you guys use?

---

### Post by CptPicard on 2008-08-26
I have to agree with you in vi being ugly and cryptic and unfriendly and that there really is a better alternative... **emacs** :KS

---

### Post by ilrudie on 2008-08-26
I use vi from the terminal.  emacs is what I learned first but IMHO its much more difficult to use and just as cryptic when first starting out.

---

### Post by Anzan on 2008-08-26
Gedit with embedded terminal and Python interpreter. With all of the plugins available it's an incredibly full featured application.

---

### Post by jinksys on 2008-08-26
I'm pretty simple.  Nano.  I've used vi and emacs, but I just like nano.

---

### Post by ilrudie on 2008-08-26
nano is good.  Not very many features but I used it for a while.  Its not nearly as widespread as vi is.  When I became an UNIX SA I learned vi because most every *nix out there comes with it.

---

### Post by Ruhe on 2008-08-26
I love emacs and use it everyday, even for java programming.
But not every ubuntu user can cope with emacs or vim.

Textmate is very friendly to all user with different expirience.
Gedit seems to be the Gnome textmate, big amount of plugins makes it gedit close to textmate, but not at all.
I think that problem isn't in gedit or even emacs or vim. It's the design of the hole system. MacOS is done with simplicity in mind, when linux gives us giant space for experiments.

---

### Post by pmasiar on 2008-08-26
My favorite simple **multiplatform** text editor (with just enough advanced features) is SciTE. Correct replacement depends how many and which features you want to replace and which you prefer to ignore. Very personal decision, we can give you tips but cannot decide for you.

---

### Post by LaRoza on 2008-08-26
> **CptPicard said:**
> I have to agree with you in vi being ugly and cryptic and unfriendly and that there really is a better alternative... **emacs** :KS

Looks like an abuse of power is in order...

> **pmasiar said:**
> My favorite simple **multiplatform** text editor (with just enough advanced features) is SciTE. Correct replacement depends how many and which features you want to replace and which you prefer to ignore. Very personal decision, we can give you tips but cannot decide for you.

Vim is also cross platform (but who uses Windows anyway?).

Does SciTE support Unicode?

---

### Post by Ruhe on 2008-08-26
> **LaRoza said:**
> Does SciTE support Unicode?
of course it does :)

---

### Post by rogeriopvl on 2008-08-26
In ubuntu I use Gedit and vim, although I think that something more like textmate would be great to have in Linux.

I use a macbook on most of my coding and textmate & coda are by far, my favorite editors,

In work, when I have to use windows, the first download I make after firefox is notepad++, great editor.

---

### Post by memories on 2008-08-26
I don't think it's Linux or OS X that make vim/TextMate/etc good. On Linux, we "have" all the elements, but they aren't put together in a single product. 

Anjuta is GREAT. I love it, except it doesn't have vim integration. There is work being done on this front however. I am looking forward to the project, I think it's called "Vimjuta"? It's basically an integration of gvim inside Anjuta. 

Gvim itself has everything a modern IDE has, except looks. And by looks I don't really mean aesthetics, but just that it's too complex, that most people wouldn't know what to do without needing to read books about the editor. Whereas with a "real" IDE you can go through all the menu options and settings, drag and drop **** etc until you get it right. 

I don't mind vim's TUI, and vim + screen are great for development. You never need to touch the mouse! but setting up vim to the point where you're developing comfortably at that level is tedious and I can't seem to find any guide on it.

---

### Post by pmasiar on 2008-08-26
> **LaRoza said:**
> Vim is also cross platform 

but you don't need PhD in vim keystroking to use SciTE :-) . When someone asks for TextMate replacement, I assume poster expecting 15 minute learning curve to be productive, not 15 weeks like with either vim or emacs.

---

### Post by LaRoza on 2008-08-26
> **pmasiar said:**
> but you don't need PhD in vim keystroking to use SciTE :-) . When someone asks for TextMate replacement, I assume poster expecting 15 minute learning curve to be productive, not 15 weeks like with either vim or emacs.

Don't say "e***s" in the same post as Vim!

I don't know anything about TextMate, it isn't (apparently) available for my OS.

---

### Post by memories on 2008-08-27
I just installed SnippetsEmu with the optional bundle, and created some mappings to automatically add closing brackets. It's a sweet setup, MAJOR upgrade. I just gotta learn how to get the file explorer working properly, so that when I double click a file, it opens in the content buffer instead of a new tab.

These are from a VimTips Wikia wiki. Credit to them, I just added support for more stuff (quotes, etc):

> inoremap {      {}<Left>
inoremap {<CR>  {<CR>}<Esc>O<TAB>
inoremap {{     {
inoremap {}     {}
inoremap <silent> }   }<ESC>
                      \:let tmp0=&clipboard <BAR>
                      \let &clipboard=''<BAR>
                      \let tmp1=@"<BAR>
                      \let tmp2=@0<CR>
                      \y2l
                      \:if '}}'=="<C-R>=escape(@0,'"\')<CR>"<BAR>
                      \  exec 'normal "_x'<BAR>
                      \endif<BAR>
                      \let @"=tmp1<BAR>
                      \let @0=tmp2<BAR>
                      \let &clipboard=tmp0<BAR>
                      \unlet tmp0<BAR>
                      \unlet tmp1<BAR>
                      \unlet tmp2<CR>
                      \a

inoremap (      ()<LEFT>
inoremap (<CR>  (<CR>}<Esc>O<TAB>
inoremap ((     (
inoremap ()     ()
inoremap <silent> )   )<ESC>
                      \:let tmp0=&clipboard <BAR>
                      \let &clipboard=''<BAR>
                      \let tmp1=@"<BAR>
                      \let tmp2=@0<CR>
                      \y2l
                      \:if '))'=="<C-R>=escape(@0,'"\')<CR>"<BAR>
                      \  exec 'normal "_x'<BAR>
                      \endif<BAR>
                      \let @"=tmp1<BAR>
                      \let @0=tmp2<BAR>
                      \let &clipboard=tmp0<BAR>
                      \unlet tmp0<BAR>
                      \unlet tmp1<BAR>
                      \unlet tmp2<CR>
                      \a

inoremap [      []<Left>
inoremap [<CR>  [<CR>]<Esc>O<TAB>
inoremap []     [
inoremap []     []
inoremap <silent> }   }<ESC>
                      \:let tmp0=&clipboard <BAR>
                      \let &clipboard=''<BAR>
                      \let tmp1=@"<BAR>
                      \let tmp2=@0<CR>
                      \y2l
                      \:if ']]'=="<C-R>=escape(@0,'"\')<CR>"<BAR>
                      \  exec 'normal "_x'<BAR>
                      \endif<BAR>
                      \let @"=tmp1<BAR>
                      \let @0=tmp2<BAR>
                      \let &clipboard=tmp0<BAR>
                      \unlet tmp0<BAR>
                      \unlet tmp1<BAR>
                      \unlet tmp2<CR>
                      \a

inoremap '      ''<Left>
inoremap ''     '

inoremap "      ""<Left>
inoremap ""     "


USAGE: Paste the above in .vimrc and open up a programming file. For example, Ruby. 

type this:
def<tab> and it will expand to:

def <name>
end

now pressing tab again will highlight <name>, and pressing tab again will go into the body of the def, and finally, tab again goes to the line after 'end'. So a hello world function would be these keystrokes:

def<tab>say<tab>puts "hello world<tab>

The reason I put a single " above is because when you press " - it will output "" and put your cursor in the middle. So if I press "x it will come out as "x"

Try it out with ( { [ and '

---

### Post by jespdj on 2008-08-28
I usually use Gedit.

[Geany](http://geany.uvena.de/) is a very nice and powerful but simple editor / almost-IDE.

On Windows, I use UltraEdit. Its column mode is incredibly useful when you need it.

---

### Post by memories on 2008-08-29
I just came across PIDA:
[IMG]http://pida.co.uk/files/screenshots/pida_0-5-2_17.png[/IMG]

[http://pida.co.uk/main]("http://pida.co.uk/main")

Has anybody tried it for non-Python dev? I'm wondering how good it is for Ruby/Rails/PHP

---

### Post by crypto178 on 2008-09-04
Nobody mentioned Scribes?

---

### Post by lifestream on 2008-10-25
I think it's funny the thread is about textmate, yet people's recomendations are like apples to oranges (not relevant to the OP )

(sorry for my bad english)

That said, I've gotta say, scribes does seem close to what the OP is asking for:
(Click the link to see a video of Scribes in action.)
[http://scribes.sourceforge.net/demo.htm](http://scribes.sourceforge.net/demo.htm)

Atleast it's a start  in the right direction! I'm going to install it now :-D

I usually use Geany, but Scribes is looking goooooooood.

---

### Post by jmikola on 2009-03-17
This looks promising: [http://www.redcaride.com/](http://www.redcaride.com/)

Based on the dev write-up, and some comments on its [reddit submission]("http://www.reddit.com/r/programming/comments/83lr1/redcar_ide_is_a_programmers_text_editor_for_gnome/"), it should be compatible with existing TextMate bundles.

---

### Post by matmatmat on 2009-03-17
Vim, Scribes or Kate in Vi mode.

---

### Post by Shin_Gouki2501 on 2009-03-17
i heared ULTRA EDIT  will be ported to Linux , that should do...?!

---

### Post by namegame on 2009-03-17
Necromancy is a terrible thing...

---

### Post by tyfius on 2009-03-18
I use different tools for different tasks.

For quick editing I use Vim with a bunch of extra plugins (code completion, snippets, nerdtree, ...) but when I'm working on a bigger project I like to use a full blown IDE, or at least something with more specialized features than Vim.

[LIST]
[*]For C/C++ I use Code::Blocks. I switched to it because I felt that Anjuta became less stable and less organized. Code::Blocks integrates all the required features (debugger, code completion, project management, ...).
[*]For PHP projects I originally used Vim but switched to Eclipse PDT because it had more features. Recently I switched to NetBeans 6.5 (and now 6.7M2) because it uses less memory than Eclipse and I can find myself more in the environment.
[*]For C# projects I MonoDevelop. Quick and easy. I feel that it's not yet mature when it comes to C/C++ so I stick to Code::Blocks for that.
[/LIST]

I have tried Gedit with a bunch of plugins but I just like to use the right tool for the right job which, at the end, saves me time.

---

### Post by Mickeysofine1972 on 2009-03-18
For C/C++ I use code::Blocks

For PHP I use gPHPEdit

For Python and Squirrel/mirthkit I use GEDIT

For apache host files and bind I use nano

The reasons I use these is mainly the different workflows I have when developing in the different languages.

For instance, with python I can test/debug apps using the built in terminal on GEDIT, but its also easier for me to use gPHPEdit along with firefox3 and firebug when doing PHP and web development.

Think about what the programming language is and then think how the editor/ide will fit in with that and you will find a winner.

Mike

---

### Post by Vadi on 2009-03-18
Geany

---

