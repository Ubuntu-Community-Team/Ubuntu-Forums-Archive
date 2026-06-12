---
title: "Notepad++ equivalent on Ubuntu"
date: 2011-02-21
forum: Programming Talk
---

### Post by Godspell on 2011-02-21
**[COLOR=DarkRed]This thread is NOT solved. I just happened to type the wrong name and can't seem to re-edit it :S[/COLOR]**

Hi,

Is there a code editor like Notepad++ on Ubuntu?

I understand that you can enable some features in Gedit to use it for code editing but it's still not good enough.

I've also tried Geany and Scintilla Scite (which was an engine for Notepad++?) but still, I find them less convenient than Notepad++.

One major difficulty that I find with all these code editors is the lack of match brace feature. E.g. I do a lot of Web stuff and in Notepad++, when I click <html> it will automatically colour it and its closing brace </html>. Really wicked.

However, above mentioned code editors claimed to have that but never works!

So, I really need some help finding the right editor on Ubuntu that has reliable match brace feature.

Please give me some suggestions.

Thank you very much.

Best wishes,
GS

---

### Post by matthew.ball on 2011-02-21
You can do this with emacs (and it offers many other features which Notepad++ doesn't have).

Although you would probably have to do some slight customisations to get it working, it wouldn't be hard, it would be something like:

[FONT="Courier New"](define-skeleton html-brace "String: " "<clause>" str | "insert text" "</clause>")[/FONT]

(And then bind the command [FONT="Courier New"]html-brace[/FONT] to a key-binding, or you could call "[FONT="Courier New"]M-x html-brace[/FONT]" each time to insert the above "skeleton").

You could do slightly more advanced macro hack and create the clauses/braces dynamically, but this is a just a simple example.

Now, I understand that people say there is a learning curve involved with emacs. In reality, I don't think so. I mean you just have to learn a few key-bindings, basically learn what a [FONT="Courier New"]C-x[/FONT] command does, that the [FONT="Courier New"]C-c[/FONT] commands are reserved for you to customise and learn how to navigate the [FONT="Courier New"]M-x[/FONT] (or use [emacs-gtk]("http://dev.pocoo.org/~gbrandl/emacs2.png") and use the menus, the menu is available in emacs-nox, but probably not worth the effort). There are many extensions to emacs which make this process easier (by presenting a visual list of available commands). The two most common are [FONT="Courier New"]ido[/FONT] and [FONT="Courier New"]smex[/FONT]. The former comes bundled with emacs (but is not turned on by default). Sometimes I think the emacs distribution for Ubuntu should provide the user with a default .emacs file, but alas, I don't think that will happen.

Emacs uses the [GNU Readline]("http://cnswww.cns.cwru.edu/php/chet/readline/rltop.html") key-bindings by default (though, perhaps it pre-dates Readline, some of Emacs' bindings are different to Readline, but you can just re-map the keys to suit your comfort).

On top of that, you have 36 un-bound keys in the [FONT="Courier New"]F#[/FONT]'s ([FONT="Courier New"]M-F#[/FONT], [FONT="Courier New"]C-F#[/FONT] and [FONT="Courier New"]F#[/FONT]). So you can make most common commands easily accessible.

There are *many* extensions available for emacs. In particular you can add an "intellisense"-like drop-down box (even with emacs-nox). You can add a source-code browser. You can add a snippet template system, and many others.

If you're interested, I really just think downloading emacs and having a go with the *interactive* tutorial is sufficient for learning emacs. This takes less than 10 minutes.

---

### Post by Milliways on 2011-02-21
> **Godspell said:**
> **[COLOR=DarkRed]This thread is NOT solved. I just happened to type the wrong name and can't seem to re-edit it :S[/COLOR]**

Hi,

Is there a code editor like Notepad++ on Ubuntu?

I understand that you can enable some features in Gedit to use it for code editing but it's still not good enough.

I've also tried Geany and Scintilla Scite (which was an engine for Notepad++?) but still, I find them less convenient than Notepad++.

One major difficulty that I find with all these code editors is the lack of match brace feature. E.g. I do a lot of Web stuff and in Notepad++, when I click <html> it will automatically colour it and its closing brace </html>. Really wicked.

However, above mentioned code editors claimed to have that but never works!


Geany does have a match brace feature. It will find matching {} <>
This is not what you want, however Geany has an alternative (better?) way of showing file structure using code folding.

In the editor window there is a small grey margin on the left side with [+] and [-] symbols which show hidden parts and hide parts of the file respectively. By clicking on these icons you can simply show and hide 

If you select <head> then fold it will hide all up to and including </head>

If you want to get to the end, just go down to the next line, then unfold and you will be after </head>

If you are looking for a program which does exactly what your favourite does, you will not find it, but if you are happy to look at different ways of doing a task this can usually be found.

---

### Post by tgalati4 on 2011-02-21
Have you tried bluefish?

---

### Post by Godspell on 2011-02-22
> **matthew.ball said:**
> You can do this with emacs (and it offers many other features which Notepad++ doesn't have).

Although you would probably have to do some slight customisations to get it working, it wouldn't be hard, it would be something like:

[FONT=Courier New](define-skeleton html-brace "String: " "<clause>" str | "insert text" "</clause>")[/FONT]

(And then bind the command [FONT=Courier New]html-brace[/FONT] to a key-binding, or you could call "[FONT=Courier New]M-x html-brace[/FONT]" each time to insert the above "skeleton").

You could do slightly more advanced macro hack and create the clauses/braces dynamically, but this is a just a simple example.

Now, I understand that people say there is a learning curve involved with emacs. In reality, I don't think so. I mean you just have to learn a few key-bindings, basically learn what a [FONT=Courier New]C-x[/FONT] command does, that the [FONT=Courier New]C-c[/FONT] commands are reserved for you to customise and learn how to navigate the [FONT=Courier New]M-x[/FONT] (or use [emacs-gtk]("http://dev.pocoo.org/%7Egbrandl/emacs2.png") and use the menus, the menu is available in emacs-nox, but probably not worth the effort). There are many extensions to emacs which make this process easier (by presenting a visual list of available commands). The two most common are [FONT=Courier New]ido[/FONT] and [FONT=Courier New]smex[/FONT]. The former comes bundled with emacs (but is not turned on by default). Sometimes I think the emacs distribution for Ubuntu should provide the user with a default .emacs file, but alas, I don't think that will happen.

Emacs uses the [GNU Readline]("http://cnswww.cns.cwru.edu/php/chet/readline/rltop.html") key-bindings by default (though, perhaps it pre-dates Readline, some of Emacs' bindings are different to Readline, but you can just re-map the keys to suit your comfort).

On top of that, you have 36 un-bound keys in the [FONT=Courier New]F#[/FONT]'s ([FONT=Courier New]M-F#[/FONT], [FONT=Courier New]C-F#[/FONT] and [FONT=Courier New]F#[/FONT]). So you can make most common commands easily accessible.

There are *many* extensions available for emacs. In particular you can add an "intellisense"-like drop-down box (even with emacs-nox). You can add a source-code browser. You can add a snippet template system, and many others.

If you're interested, I really just think downloading emacs and having a go with the *interactive* tutorial is sufficient for learning emacs. This takes less than 10 minutes.

As much as I find it cool, I think this sounds slightly more complicated than just using a code editor. I have just installed Emacs and briefly read the tutorial notes and gotta say, you can do quite a lot of things on there, can't you?
Like you said, it does look pretty old as well. I'm definitely checking it out (or learning?) once I have time.

Thanks for the reply.

Cheers and regards,
GS

---

### Post by Godspell on 2011-02-22
> **Milliways said:**
> Geany does have a match brace feature. It will find matching {} <>
This is not what you want, however Geany has an alternative (better?) way of showing file structure using code folding.

In the editor window there is a small grey margin on the left side with [+] and [-] symbols which show hidden parts and hide parts of the file respectively. By clicking on these icons you can simply show and hide 

If you select <head> then fold it will hide all up to and including </head>

If you want to get to the end, just go down to the next line, then unfold and you will be after </head>

If you are looking for a program which does exactly what your favourite does, you will not find it, but if you are happy to look at different ways of doing a task this can usually be found.

Yeah, I noticed that + - feature but I just didn't like it as good as the match brace.
I'm sure it's useful as well and I may even install it and check it out again but I still think I prefer the match brace feature :)

> Have you tried bluefish?

Erm...I can't remember but I think I have, once.

Can you tell me if it provides a match-brace?

Back then, I tried several editors but liked none of them.

Thank you for your replies.

Regards,
GS

---

### Post by trivialpackets on 2011-02-22
Does notepad++ run under wine?  A quick google shows that there have been some who have had success, maybe worth a shot if you really like notepad++.

---

### Post by lykwydchykyn on 2011-02-22
> **Godspell said:**
> As much as I find it cool, I think this sounds slightly more complicated than just using a code editor. I have just installed Emacs and briefly read the tutorial notes and gotta say, you can do quite a lot of things on there, can't you?
Like you said, it does look pretty old as well. I'm definitely checking it out (or learning?) once I have time.

Thanks for the reply.

Cheers and regards,
GS

Emacs has been around a long time, but it's still actively developed and widely used, and for good reason.  It's insanely powerful, but it takes time to learn.  Worth the trouble, IMHO.

Someone else suggested bluefish; I haven't used it in a few years, but last time I did I remember it auto-generating closing tags, and maybe doing what you describe as well.  It may be what you're looking for.

---

### Post by matthew.ball on 2011-02-22
> **Godspell said:**
> As much as I find it cool, I think this sounds slightly more complicated than just using a code editor. I have just installed Emacs and briefly read the tutorial notes and gotta say, you can do quite a lot of things on there, can't you?
Like you said, it does look pretty old as well. I'm definitely checking it out (or learning?) once I have time.

Thanks for the reply.

Cheers and regards,
GS
I'm sorry. What I actually told you is *not* what you're after here. What I said would just add a matching close brace each time you insert an open brace.

However, as far as *colouring* a matching opening (or closing) brace goes, that is also possible. There's a minor-mode called [FONT="Courier New"]show-paren-mode[/FONT] which highlights the matching parenthesis, I'm fairly certain this could be extended (assuming it wasn't already) to highlight a matching html brace.

I know there are a lot of extensions available specifically for html development in emacs, so perhaps someone has already got this idea and implemented it.

---

### Post by smashnburn on 2011-07-25
After a bit of research, i still cannot run notepad++ via Wine, even though it looks pretty simple.Does anyone willing to guide me step by step in order to make it work.??

Thanks in advance

---

### Post by krazyd on 2011-07-25
> **Godspell said:**
> I do a lot of Web stuff and in Notepad++, when I click <html> it will automatically colour it and its closing brace </html>. 


vim can match html tags using the matchit plugin. Pressing % inside a tag will jump to the matching tag, though I don't think it highlights the other tag.

For more info, inside vim or gvim just type ```
:help matchit 
```

---

### Post by lykwydchykyn on 2011-07-26
> **smashnburn said:**
> After a bit of research, i still cannot run notepad++ via Wine, even though it looks pretty simple.Does anyone willing to guide me step by step in order to make it work.??

Thanks in advance

Have you checked [The winehq appdb?](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13036).

It appears users are getting mixed results running it in wine.

I gave up running anything remotely important in WINE a long time ago; IMHO you're better up finding something native that's reasonably close.  Surely one of the 1.2 gazillion text editors in the repositories has what you need?

---

### Post by stchman on 2011-07-26
I have found Geany is the closest thing.  I agree, Notepad++ is really exceptional.

The vi lovers will tell you to use vim.

---

### Post by memilanuk on 2011-07-26
I too wish NotePad++ was available on Linux... but since that ain't happening anytime soon, I had to look for other options.  Geany & Gedit are usually the top two recommended, but another option that runs on Windows, Mac & Linux is Komodo Edit...

---

### Post by Godspell on 2011-08-20
> **memilanuk said:**
> I too wish NotePad++ was available on Linux... but since that ain't happening anytime soon, I had to look for other options.  Geany & Gedit are usually the top two recommended, but another option that runs on Windows, Mac & Linux is Komodo Edit...

This is an old thread but I'll reply anyway.
I installed Notepad++ via wine a while ago and it worked alright.
Feels a bit strange to use GNU licenced app on Ubuntu with wine but hey, as long as it works, right?
Anyway, just thought I'd mention since you also seemed to be quite fond of Notepad++ :)

Many thanks and regards,
GS

---

### Post by cgroza on 2011-08-20
> **Godspell said:**
> This is an old thread but I'll reply anyway.
I installed Notepad++ via wine a while ago and it worked alright.
Feels a bit strange to use GNU licenced app on Ubuntu with wine but hey, as long as it works, right?
Anyway, just thought I'd mention since you also seemed to be quite fond of Notepad++ :)

Many thanks and regards,
GS
Notepad++ uses a lot of Windows specific features. Otherwise, it's editor and editing functionality should be portable because it uses Scintilla. Only if someone would fork it and replace the Windows bits with the Linux ones...

---

### Post by dazman19 on 2011-08-22
gedit

---

### Post by illiac on 2011-12-22
How about Gvim? The gui form of vim.

---

### Post by Godspell on 2011-12-23
> **dazman19 said:**
> gedit

I've looked into Gedit. In  fact, found a website that says "Pimp my Gedit" and tried some things  said on there. Installed plug-ins, changed colours and so forth. It  became pretty feature-rich but still, imho, nowhere near as good as  Notepad++.

> How about Gvim? The gui form of vim. 	

I've tried this. I didn't like it at all. It may be  great in its own way and so forth but to me, not user-friendly at all. I  used it to open some PHP files and didn't display them properly...kept  missing "<" in PHP codes. Again, I'm sure it can be customised,  personalised and so on,...but comparing with Notepad++ (or even Gedit  for that matter), it doesn't really work out-of-the-box.

I just want something exactly like Notepad++ on Ubuntu. Nothing more, nothing less :)
Anyway, I'm currently running it under WINE so it doesn't matter much.

I may try other editors later on and post my comments.

Many thanks and regards.

---

### Post by Occiso on 2013-01-12
> **Godspell said:**
> I've looked into Gedit. In  fact, found a website that says "Pimp my Gedit" and tried some things  said on there. Installed plug-ins, changed colours and so forth. It  became pretty feature-rich but still, imho, nowhere near as good as  Notepad++.



I've tried this. I didn't like it at all. It may be  great in its own way and so forth but to me, not user-friendly at all. I  used it to open some PHP files and didn't display them properly...kept  missing "<" in PHP codes. Again, I'm sure it can be customised,  personalised and so on,...but comparing with Notepad++ (or even Gedit  for that matter), it doesn't really work out-of-the-box.

I just want something exactly like Notepad++ on Ubuntu. Nothing more, nothing less :)
Anyway, I'm currently running it under WINE so it doesn't matter much.

I may try other editors later on and post my comments.

Many thanks and regards.

I've tryed "Bluefish" (i'd also installed notepad++ with wine and doesn't give me any problem at all) and bluefish have many of the features that notepad++ have.

I used to try the searching tool in notepad++ many times before and bluefish have the same powerfull searching tool... and about highlight tags (same as notepad++)...

I've trying Bluefish for some time because is a "multi-plataform" editor that run over windows, mac, linux and some others O.S.

---

### Post by Bucky Ball on 2013-01-13
[I][B]Thread Closed

Reason: [/B][/I]Necromancy. Old thread put to bed. If a thread has been inactive for over a year please post a new thread rather than resurrecting it. Thanks.

---

