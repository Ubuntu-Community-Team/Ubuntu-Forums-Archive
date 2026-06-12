---
title: "LISP - how to learn"
date: 2005-12-06
forum: Programming Talk
---

### Post by sourc3 on 2005-12-06
hi to all!
In simple words: I want to learn LISP. Can you help me to find some good documentation or suggest some good books? I would appreciate it a lot!
Another question... do I have to learn how to use emacs or are there good alternatives?

Thanks in advance!!!

---

### Post by rjwood on 2005-12-06
[Structure and Interpretation of Computer Programs]("http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-10.html")

---

### Post by sourc3 on 2005-12-06
thanks for the book! what about emacs?

---

### Post by toojays on 2005-12-06
sourc3, you don't *have* to learn Emacs, but it is highly recommended. It took me a few tries to get into Emacs, but once I got over the steep initial learning curve (and past the fairly boring tutorial) and I realised what Emacs really is, it blew my mind.

By the way, if you want to learn Emacs *and* LISP at the same time, I'd suggest the GNU manual [Programming in Emacs Lisp]("http://www.gnu.org/software/emacs/emacs-lisp-intro/emacs-lisp-intro.html"). This is one of the best introductions to programming I have ever read; it's a pity that it has such a limited audience.

Another good LISP book is [Practical Common Lisp]("http://www.gigamonkeys.com/book/").

---

### Post by sourc3 on 2005-12-07
thanks for the advice! I have no doubt of the potential of emacs, I was only looking for a possible alternative. I'm asking why, if LISP is such a famous language, there are no other editors supporting it.

---

### Post by LordHunter317 on 2005-12-07
Do you want to learn actual Common LISP or simply a language in the LISP-family?  If the latter, I'll dig up teh Scheme books I was recommended.

---

### Post by Gustav on 2005-12-07
Common Lisp is may be a more practical solution but Scheme is soooo beautiful. (I &#9029;&#9829; &#955;-functions)

---

### Post by sourc3 on 2005-12-07
Well, I already know Scheme because I'm studying it at University, but I was told that if I wanna get some serious AI related project (in which I'm very interested) I have to learn LISP.

---

### Post by sourc3 on 2005-12-08
Well, I'm going through the emacs tutorial... (so boring!!! ;) ) and I have a stupid question... how to change colors? I mean, I like to have a black background, and so I have put (set-background-color "black") in my .emacs file, but now I can't see the text I'm typing, and I would also like to change the colors of the syntax highlighting to be more visible with a black background. What can I do? Thanks!

---

### Post by toojays on 2005-12-08
Select "Customize" from the "Options" menu. Then go to the "Faces" group, then the "Font Lock" group, then the "Font Lock Highlighting Faces" group. From there you can click the "Show" button next to the font you want to change, and type a new colour value in for "Foreground" or "Background" boxes. There is a list of valid colours at [Wikipedia's list of X11 colours]("http://en.wikipedia.org/wiki/X11_color_names").

---

### Post by sourc3 on 2005-12-08
Thanks toojays! You're the man! I'm diving into the books you suggested me, thanks! Maybe if you're planning to to have a vacation in Italy, I can give you some good points... ;) thanks!

---

### Post by capi on 2005-12-08
> I'm asking why, if LISP is such a famous language, there are no other editors supporting it. Most editors do have support for lisp. However by support I mean making it pretty with colors. I'm personally a big SLIME fan. I'll give you a quick setup. First download SLIME. [http://common-lisp.net/project/slime/](http://common-lisp.net/project/slime/) Then I save it into ~/.SLIME and open/create ~/.emacs and put this in it... ```
(add-to-list 'load-path "~/.SLIME") (require 'slime) (slime-setup) (add-hook 'lisp-mode-hook (lambda () (slime-mode t))) (add-hook 'inferior-lisp-mode-hook (lambda () (inferior-slime-mode t))) 
``` then when in emacs hold down ``alt'' and press ``m'' than ``x'' just type ``slime'' and press enter. You should see things load and come to a lisp command prompt. Practical Lisp explains it in a little more depth. SLIME also has a debian package(from debian not ubuntu) but I've never tried it on ubuntu, and it's in the non-free section. One invaluable resource is [http://www.cliki.net/index](http://www.cliki.net/index) Another one of my favorite lisp tuts is [http://psg.com/~dlamkins/sl/contents.html](http://psg.com/~dlamkins/sl/contents.html) Here's a lisp of some scheme tuts. However I don't know scheme well enough to vouch for them [http://gpwiki.org/index.php/Scheme](http://gpwiki.org/index.php/Scheme) Sorry I'm in a rush so this may sound like a bad ramble. :D I really wish I could take a knife to times through right now.

EDIT: By chance, sourc3 you don't speak italiano?

---

### Post by sourc3 on 2005-12-09
I'll give it a try, thanks for the hint! And... yes, I speak italian... of course! ;)

---

### Post by toojays on 2005-12-09
A Debian developer who packages common lisp stuff makes available a whole bunch of packages (including slime) built for breezy. You can get it by adding the following line to your sources.list:```
deb http://people.debian.org/~pvaneynd/cl-breezy-packages ./
```

sourc3: Unfortunately I'm too late to take you up on your offer. I had a big holiday in Europe in the middle of this year. :) It may be some time before I get back up there.

---

### Post by sourc3 on 2005-12-09
Just added to my sources! Thanks!

---

### Post by rolfotto on 2005-12-27
[QUOTE=sourc3]hi to all!
In simple words: I want to learn LISP. Can you help me to find some good documentation or suggest some good books? I would appreciate it a lot!
Another question... do I have to learn how to use emacs or are there good alternatives?

Thanks in advance!!![/QUOTE]

Well, if you are looking for books, this one helped me when starting out.  It starts very basic, so you may feel like skipping some sections (shrugs):

[http://www.cs.cmu.edu/~dst/LispBook/index.html](http://www.cs.cmu.edu/~dst/LispBook/index.html)

And this page may be useful to you too:

[http://www.franz.com/newtolisp/](http://www.franz.com/newtolisp/)

---

### Post by mirna on 2006-01-30
Hi,

I need help on setting up the matlab mode in emacs. I got the matlab.el and compiled it into .elc file. I put these into
\usr\share\emacs\site-lisp
directory. I know this is not directly related to learning lisp, and since I don't have the time now to learn it I'm hoping one doesn't have to learn lisp to set up matlab mode in emacs?!
Please, help!!!

Mirna

---

### Post by toojays on 2006-01-30
You would've been better off starting a new thread for your question. I don't have the exact answer, but I do have an alternative solution.

When I used to study communications theory, I used [GNU Octave](http://www.octave.org/) to work on my assignments at home. Since my lecturers only used Matlab, I needed to make my Octave code 100% compatible with Matlab.

I used the octave-mode for Emacs, which Ubuntu has in the octave2.1-emacsen package. The following bits of my .emacs file might be useful to you:```
; setup octave mode for .m files
(setq auto-mode-alist
      (cons '("\\.m$" . octave-mode) auto-mode-alist))
(add-hook 'octave-mode-hook
          (lambda()
            (abbrev-mode 1)
            (auto-fill-mode 1)
            ; next bit tells emacs to use % instead of # for Octave comments
            (setq octave-comment-char ?%)
            (modify-syntax-entry ?\% "<"  octave-mode-syntax-table)))

; this lets up and down scroll through command history when running Octave
; from within emacs
(add-hook 'inferior-octave-mode-hook
          (lambda()
            (define-key inferior-octave-mode-map [up] 'comint-previous-input)
            (define-key inferior-octave-mode-map [down] 'comint-next-input)))
```

---

### Post by lnostdal on 2006-01-30
You want this: [http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/)

Lisp will change everything you know about programming (in a good way)! Good Luck :D

---

### Post by mirna on 2006-01-31
I'll try it and let you know, but in the mean time: How does one start a new thread? I've been trying to start it but I couldn't find a way how. Call me stupid, but I really can't find a way!

Mirna

---

### Post by toojays on 2006-01-31
It is an example of really poor user interface design. There is a tiny picture of a folder just above where it says "Threads in Forum : Programming Talk". Click that picture to start a new thread.

---

### Post by mirna on 2006-02-03
Hi,

Thanks for the code, I also found an excellent web page that explains how to set up matlab mode in emacs:
[http://www2.imm.dtu.dk/~kas/software/emacs/](http://www2.imm.dtu.dk/~kas/software/emacs/)
And thanks for the help on "How to start a new thread" problem I had.

Mirna

---

### Post by asimon on 2006-02-04
A link to the excellent *Structure and Interpretation of Computer Programs* was already given. Here are the [videos of the orignial lectures](http://feeds.feedburner.com/SICP) from Ableson and Sussman. They have that 1980 feeling, but still a lot can be learned from watching them.

---

### Post by stormcoder on 2006-03-08
I've recently went through this process. So here is what I did.

[LIST]
[*]Go through synaptic and query for emacs and then lisp. Install everything you think will be useful.
[*]Lookup lisp and slime on google.
[*]Install slime
[*]go to  [Common Lisp Directory]("http://www.cl-user.net/asp/TefH1/sdataQvxVcoxQ-rnRDM==/sdataQo5Y-1Mh9urk") and look at all the resources that are available. In particular, look at the books page because there are a number of free books available, especially Practical Common Lisp. 
[*]Subscribe to [Planet Lisp RSS fees]("http://planet.lisp.org/rss20.xml")
[*]Subscribe to [Delicious Lisp RSS feed]("http://del.icio.us/rss/tag/lisp")
[*]Order Artificial Intelligence: A modern approach.
[*]Checkout [Lisp Books]("http://www.lispmachine.net/")
[*]Checkout [Common Lisp Wiki]("http://www.cliki.net/index")
[*]Get to know [Common Lisp Hyperspec]("http://www.lispworks.com/documentation/HyperSpec/Front/")
[/LIST]

Have fun. \\:D/

---

### Post by evaristegalois on 2006-03-08
you can change colors with the commands 

set-foreground-color

set-background-color

set-cursor-color

That should do it. Do M-x list-colors-display to see which colors you have available on your terminal. I put this in my .emacs file

(set-foreground-color "yellow1")
(set-background-color "black")
(set-cursor-color "yellow1")

---

### Post by tehDeuce on 2006-03-19
[QUOTE=capi]Most editors do have support for lisp. However by support I mean making it pretty with colors. I'm personally a big SLIME fan. I'll give you a quick setup. First download SLIME. [http://common-lisp.net/project/slime/](http://common-lisp.net/project/slime/) Then I save it into ~/.SLIME and open/create ~/.emacs and put this in it... ```
(add-to-list 'load-path "~/.SLIME") (require 'slime) (slime-setup) (add-hook 'lisp-mode-hook (lambda () (slime-mode t))) (add-hook 'inferior-lisp-mode-hook (lambda () (inferior-slime-mode t))) 
``` then when in emacs hold down ``alt'' and press ``m'' than ``x'' just type ``slime'' and press enter. You should see things load and come to a lisp command prompt. Practical Lisp explains it in a little more depth. SLIME also has a debian package(from debian not ubuntu) but I've never tried it on ubuntu, and it's in the non-free section. One invaluable resource is [http://www.cliki.net/index](http://www.cliki.net/index) Another one of my favorite lisp tuts is [http://psg.com/~dlamkins/sl/contents.html](http://psg.com/~dlamkins/sl/contents.html) Here's a lisp of some scheme tuts. However I don't know scheme well enough to vouch for them [http://gpwiki.org/index.php/Scheme](http://gpwiki.org/index.php/Scheme) Sorry I'm in a rush so this may sound like a bad ramble. :D I really wish I could take a knife to times through right now.

EDIT: By chance, sourc3 you don't speak italiano?[/QUOTE]

Sorry for the bump, but I can't manage to get this to work.  I've downloaded slime and extracted it to ~/.SLIME, but when I start emacs with emacs -e 'slime', it says
"Symbols function definition is void: slime", and when I try alt-m-x slime, it says [No match].  Am I doing something wrong?

---

### Post by toojays on 2006-03-20
Load emacs normally, and use 'C-h v load-path RET' to check that the directory where you extracted slime to really is in your load path. Also check in the directory to make sure the files are where they should be, and not a sub-directory below that.

---

### Post by tehDeuce on 2006-03-21
[QUOTE=toojays]Load emacs normally, and use 'C-h v load-path RET' to check that the directory where you extracted slime to really is in your load path. Also check in the directory to make sure the files are where they should be, and not a sub-directory below that.[/QUOTE]

'C-h v load-path' displays a bunch of paths, but none of them are .SLIME.  It won't let me type a space after load-path, so when do I type RET?

---

### Post by toojays on 2006-03-21
RET just means press enter/return, which it sounds like you already did. It sounds like you haven't added slime to your load path.

---

### Post by tehDeuce on 2006-03-21
It turns out I shouldn't try to do this stuff at night.  I had named my .emacs '.emacs'.  It starts up now, but the first time it started, it gave me a bunch of errors as it was starting up.  I said to ignore them, but is this something I should be worried about?

Oh, and I'm using sbcl if that matters.

---

### Post by kosac on 2006-03-22
Practical Common Lisp

You can see the online version at [http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/)


good luck :)

---

