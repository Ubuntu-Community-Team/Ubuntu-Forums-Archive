---
title: "opening files using terminal (Unity)"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by Gareth Edwards on 2013-03-10
Hello again all!

Ok so I'm using Ubuntu 12.10 and Unity.

I'm going through some basic lessons of using the terminal.

But how do I open a "examplefile.odf" using the terminal?

I had a search, but all involved Gnome or KDE.

Thanks for reading / helping.

Cheers,

Gareth

---

### Post by RoosterHam on 2013-03-10
ODF files are opendocument files. so if you have libre office installed (most likely will) call that application to open all .odf files.

:~$ libreoffice /path/to/file.odf

---

### Post by iMac71 on 2013-03-10
simply type in a Terminal window:```
cd /path/to/yourfile
libreoffice yourfile
```e.g.:```
cd Documents
libreoffice examplefile.odf
```

---

### Post by Gareth Edwards on 2013-03-10
Thanks Rooster,

That's cool - but is there a quicker way akin to the "gnome open" or "kde open" file.odf ?

Thanks for your input - it's early days for me using the terminal so learning the "normal" way is also good.

---

### Post by Cheesemill on 2013-03-10
You can use the command xdg-open, for example...
```
xdg-open file.odf
```
Will open file.odf with LibreOffice Writer (or whatever application you have associated with odf files).

The xdg-open command is desktop agnostic, it will work with any DE that follows the xdg specification (all of them AFAIK).

---

### Post by RoosterHam on 2013-03-10
> **Cheesemill said:**
> You can use the command xdg-open, for example...
```
xdg-open file.odf
```
Will open file.odf with LibreOffice Writer (or whatever application you have associated with odf files).

The xdg-open command is desktop agnostic, it will work with any DE that follows the xdg specification (all of them AFAIK).

I never knew about this one. You never stop learning.

Don't forget Gareth, if you are currently working in the directory that the file is in (as in if you just type "ls" it is listed) try this:

:~$ libre<TAB KEY> exam<TAB KEY>

at <TAB KEY> hit the tab key, rather than write it with the <>... (I don't mean to sound condescending, but when learing it helps to explain clearly)

If you haven't leart tab completion, tell us what you see happen.

---

### Post by Gareth Edwards on 2013-03-10
Wow, thanks guys - I am really enjoying being part of the linux community (I have a system 76 so i'm in at the deep end!) - thanks for all the help people.
Will try these later and report back.

Cheers,

Gareth.

---

### Post by Gareth Edwards on 2013-03-10
OK after first efforts:

1. xdg-open file.extension *seems *to work - (I need  to be in the right directory though, right? - i.e I cant open  "file.odt" from home, I have to go to "documents" first?) - it opened up  the file in LibreOffice and allowed me to edit it etc *however - *the  terminal came up with (sorry I can't print screen right now) "javaldx:  could not find a runtime environment" , JVM, failed to read path from  javaldx, fontconfig warning.....
So like I say, it *seems *to work, but terminal comes up with 9 or 10 lines of scary looking stuff!

2.The  tab completion thing seems useful (I was unaware of this, so thank you)  - it shows relevant programs (like an auto complete?) but I don't  understand why the second part - "exam <tab> "

OK, thanks again for reading & helping :razz:

---

### Post by coldcritter64 on 2013-03-10
> - (I need  to be in the right directory though, right? - i.e I cant open   "file.odt" from home, I have to go to "documents" first?)
If you are in the home directory you have to specify an absolute path to the file for the command xdg-open, but your home directory itself can be replaced in the command with the system variable for it, the tilde symbol or ~.
eg (from home),
```
xdg-open ~/Documents/file.odt
``` Note the terminal is case sensitive and  the documents folder must have a capitalized "d".

If you are in the Documents folder (note the capital d :)) then the code can become,
```
xdg-open file.odt
``` this in terminal is known as a relative path; compared to first code which uses an absolute path. The path, or file.odt directly in this case, is relative to the location you have changed directory to (the ~/Documents folder itself). Cheers.

---

### Post by vasa1 on 2013-03-10
> **Gareth Edwards said:**
> Hello again all!

Ok so I'm using Ubuntu 12.10 and Unity.

I'm going through some basic lessons of using the terminal.

But how do I open a "examplefile.odf" using the terminal?

I had a search, but all involved Gnome or KDE.

Thanks for reading / helping.

Cheers,

Gareth

I think I know what you mean by "example.odf" but I'm not sure that .odf is a file extension, *per se*. You'll have example.odt (Writer), example.ods (Calc), example.odg (Draw), etc.

---

### Post by Gareth Edwards on 2013-03-10
@ CC64 - Thanks, was unaware of the home / ~ replacement. Was aware of case sensitivity, but always good to reinforce the point!

---

### Post by Gareth Edwards on 2013-03-10
@ vasa - yes, odt, my mistake!

---

### Post by RoosterHam on 2013-03-11
> **Gareth Edwards said:**
> OK after first efforts:

2.The  tab completion thing seems useful (I was unaware of this, so thank you)  - it shows relevant programs (like an auto complete?) but I don't  understand why the second part - "exam <tab> "



Tab-completion will complete an application name, but it will also complete file names. So if you are working in the directory of the file "example.odf" then "exam<tab>" will complete the file name also. If you are in any other directory you can specify the absolute path, and tab-complete it.

ie.
$ls -al /home/USERNAME/Docu<tab>
$xdg-open /home/USERNAME/Doc<tab>/exa<tab>

If there are multiple options for the clue you have given ( do "ls -al /home/USERNAME/Do<tab>") nothing will be displayed. double tapping the tab key will list your options (will list Downloads/ and Documents/ in our example)

Regarding the errors, many gui applications that are started from the terminal will through errors. start firefox from a terminal and watch what happens. If the applications are behaving normally then the errors may be disregarded.

---

### Post by Gareth Edwards on 2013-03-12
So the errors that come up when opening from terminal are normal and to be expected? I don't need to worry about something randomly closing halfway through working just because I opened it using the terminal? I will indeed try opening firefox later.
Thanks for all your help and tips people.

---

### Post by coldcritter64 on 2013-03-12
Errors won't *_always_* show when starting an application from terminal, but RoosterHam's example firefox usually will, and it still operates fine. A program will occasionally segfault or encounter other problems and shut halfway through operations when opened normally and a segfault or other fault can still occur even if opened from terminal. What I mean by that is you can open a program from terminal, have it crash halfway through operations, the error that caused the crash will be displayed, but that does  not mean the error will have been caused by the application being launched from terminal. 

Launching from a terminal is actually very handy if you do have a crashing application, open it in a terminal and when it crashes you will be able to see why and take action to rectify the problem; In such a case if you need assistance, you can always paste the error message here between [noparse]```

```[/noparse] tags in your editor. A simple way to do code tags is to paste the error into the editor, highlight the entire error message, and click on the # button on the editor toolbar.

<aside> @ RoosterHam,  like your location :p </aside>

---

### Post by Gareth Edwards on 2013-03-12
Thanks CC,

At the risk of going off topic - what would ```
 error message 
``` highlight #  do in editor? - I've only just started to use editor for simple <html> stuff, so excuse my ignorance....

---

### Post by vasa1 on 2013-03-12
> **Gareth Edwards said:**
> So the errors that come up when opening from terminal are normal and to be expected? I don't need to worry about something randomly closing halfway through working just because I opened it using the terminal? I will indeed try opening firefox later.
Thanks for all your help and tips people.

What is being said is that even when a program works just fine, invoking it from the terminal will throw up errors or warnings that aren't really important. The key point is that invoking a program from the terminal is a useful diagnostic tool *when things don't work as expected*.

What do you mean by "something randomly closing halfway through working"? That's a bit fuzzy ;) Could you be clearer? Basically, if something works well, it will work well whether you open it from a terminal or by double-clicking on an icon or by using the Dash. If something doesn't work well, it won't work well no matter how you start it.

---

### Post by RoosterHam on 2013-03-12
@coldcritter64, I'm quite proud to call it home. :-D

---

### Post by Gareth Edwards on 2013-03-12
Thanks Vasa, I've not actually had any problems with anything crashing, but was a bit alarmed at the error messages as mentioned earlier.

---

### Post by coldcritter64 on 2013-03-13
> ...highlight # do in editor?...

My previous instructions said highlight the error (ie. insert the cursor at the start of the message and click and drag a selection over the whole error message), **then** *_click_* on the # button on the toolbar, not highlight it. As soon as you click on th # button with the error selected the editor will automatically wrap the selection with the code tags, easy :).

<aside>@RoosterHam, yeah it's not too shabby :) , real steamy and tropical up here atm, looking forward to the colder months approaching. cheers. </aside>  (also note with the aside I use the html style <>, but bbcode tags use the [ ] style brackets. Using  this layout with the aside comments is only to easily show readers the comment is not related to the post topic, unlike the paragraph above, not for any html purposes). Posts should be on topic, but individual comments within that are off the topic should be cleary marked, as far as I'm aware.

---

