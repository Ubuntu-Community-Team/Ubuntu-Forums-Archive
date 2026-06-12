---
title: "Make emacs recognize 'end' keyword in Octave-mode"
date: 2010-09-02
forum: Programming Talk
---

### Post by manzdagratiano on 2010-09-02
I have a dilemma - I use octave-mode for emacs, and while the indentation etc works beautifully for keywords like 'endif' and 'endfor', for some reason the 'end' keyword itself is not recognized. This makes for an ugly indentation in the code. And while I would refuse to install Matlab on my computer even though I get a free license from the University and rather run Octave, the cluster on which I need to run my code has Matlab alone, and the sysadmin is very resistant to installing Octave (even though the cluster is CentOS, and I believe all that is needed is a mere 'yum install octave3.2'). Ergo, since Matlab does not recognize the 'endif' and 'endfor' keywords, I am compelled to use 'end' in my code for compatibility. How do I make octave mode treat 'end' the same way as 'endif' and 'endfor' as regards automatic indentation?

My .emacs file has the following inserted in it as I saw in the GNU guide:
```

(autoload 'octave-mode "octave-mod" nil t)
(setq auto-mode-alist
      (cons '("\\.m$" . octave-mode) auto-mode-alist))

(add-hook 'octave-mode-hook
          (lambda ()
            (abbrev-mode 1)
            (auto-fill-mode 1)
            (if (eq window-system 'x)
                (font-lock-mode 1))))

(defun RET-behaves-as-LFD ()
  (let ((x (key-binding "\C-j")))
    (local-set-key "\C-m" x)))
(add-hook 'octave-mode-hook 'RET-behaves-as-LFD)

(setq octave-auto-indent t)
```

---

### Post by manzdagratiano on 2010-09-03
Surely somebody has ideas?

---

### Post by manzdagratiano on 2010-09-08
Need some help here people... time is of the essence!

---

### Post by manzdagratiano on 2010-09-09
OMG! I have finally gained the power of invisibility!!! ;)

---

### Post by manzdagratiano on 2010-09-12
Maybe this seems to me to be the wrong sub-forum to have posted in. May I request the moderators to move this thread into the "Programming Talk" section of the "Development & Programming" sub-forum? I feel it is highly likely my question shall be answered there.

---

### Post by Elfy on 2010-09-12
moved

---

### Post by pbrane on 2010-09-12
What emacs version are you running? Mine is 23.1. This is in my **~/.emacs**
```

(autoload 'octave-mode "octave-mod" nil t)
(setq auto-mode-alist
      (cons '("\\.m$" . octave-mode) auto-mode-alist))

(add-hook 'octave-mode-hook
          (lambda ()
            (abbrev-mode 1)
            (auto-fill-mode 1)
            (if (eq window-system 'x)
                (font-lock-mode 1))))

```
I also have **octave3.2-emacsen** installed from the repos. It seems the octave-mod is compiled in /usr/share/emacs23/site-lisp. So I guess getting the source and modifying that.

Here is one possible link for the source:
[http://www.opensource.apple.com/source/emacs/emacs-41/emacs/lisp/progmodes/octave-mod.el]("http://www.opensource.apple.com/source/emacs/emacs-41/emacs/lisp/progmodes/octave-mod.el")

It seems as if 'end' is defined the same as 'endif' in this source.

This may be a newer copy
[http://www.koders.com/lisp/fidA0F5EEE9E192182435D7F1992FC6CCD2D76FE358.aspx?s=TV+Raman]("http://www.koders.com/lisp/fidA0F5EEE9E192182435D7F1992FC6CCD2D76FE358.aspx?s=TV+Raman")

---

### Post by manzdagratiano on 2010-09-12
I too have octave3.2 along with emacs 23.1.1, alongwith the package octave3.2-emacsen; I tried removing the extra options I had in my .emacs file, but all it did was remove the auto-indentation functionality. The keyword "end" is again not properly indented if I press tab on that line. So bummer!

---

### Post by pbrane on 2010-09-12
Yeah, same here. But it appears to be present in octave-mod.el. If I find out anything I'll post back.

---

### Post by jpkotta on 2010-09-12
Since you're writing Matlab-compatible code, why not use matlab-mode?

```
(add-to-list 'auto-mode-alist
             '("\\.m\\'" . matlab-mode))
```

---

### Post by manzdagratiano on 2010-09-13
> **jpkotta said:**
> Since you're writing Matlab-compatible code, why not use matlab-mode?

```
(add-to-list 'auto-mode-alist
             '("\\.m\\'" . matlab-mode))
```

Ahem! Thank you! I had no idea there existed a matlab mode. That is good news for the time being... however, is there no way I can modify octave-mode itself to make the 'end' keyword be recognized as a block delimiter? Much as matlab-mode might prove to work (I shall try now), I would rather work under octave-mode than matlab-mode, for the usual "free software, free society" reasons. I used to be big on Matlab three years ago, and then big on Mathematica until a year ago, and even though I can get them for free from my University, I do not wish to, for I would rather have true freedom.

---

### Post by manzdagratiano on 2010-09-13
> **pbrane said:**
> Yeah, same here. But it appears to be present in octave-mod.el. If I find out anything I'll post back.

Indeed... very surprising; when I look at the source you pointed me to, "end" is present as clear as day. I am stumped! More head-bashing...

---

### Post by manzdagratiano on 2010-09-13
Meine Herren! I think I found the heart of the matter! I did a 'sudo updatedb' followed by a 'locate octave-mod.el', which returns '/usr/share/emacs/site-lisp/octave3.2-emacsen/octave-mod.el' and in that file, in the 'defvar octave-end-keywords', the keyword 'end' is **not** present! Since I have this version installed from the repos, I think the problem shall be the same with everyone else.

However, merely adding the "end" keyword there does not work. I am exploring that file further - maybe looking at the differences between this file and the one from apple would help.

---

### Post by manzdagratiano on 2010-09-13
Aaarrrggghhh!!! Using the "diff" command to analyze differences proved to be a disaster, since many things have changed - including author/maintainer emails (although of course, the version in the repos is the current one!)

---

### Post by manzdagratiano on 2010-09-13
From octave-mod.el:

> 
;; FIXME: only use specific "end" tokens here to avoid confusion when "end"
;; is used in indexing (the real fix is much more complex).
(defvar octave-end-keywords
  '("endfor" "endfunction" "endif" "endswitch" "end_try_catch"
    "end_unwind_protect" "endwhile" "until"))As of now I have no idea what the "real" fix is.

---

### Post by manzdagratiano on 2010-09-13
I would assume that appending "end" in the 'octave-end-keywords' field and inserting "end" in the 'octave-block-match-alist' field to correspond to "for", "if" and "while" would do the trick, but it did not work so far for me. In the entire file the keyword "endif" occurs exactly thrice, one of which is for a shortcut, and the other two for the instances I just mentioned - one in the 'octave-end-keywords' variable and another in the 'octave-block-match-alist' variable. If putting "end" alongside "endif" in these fields does not work, I am perplexed as to what will!

---

### Post by jpkotta on 2010-09-15
As the comment says, it is tricky.  Basically, the problem is that "end" can be used as an index to a vector or to close a code block.  Thus it becomes necessary to distinguish them in the indentation code.  I think this will work (it assumes that "end"s that finish a block only have spaces and comments after them, which usually won't occur for index "end"s):

```

(eval-after-load "octave-mod"
  (progn
    (add-to-list 'octave-end-keywords "end[[:space:]]*\\([%#].*\\|$\\)")
    (setq octave-block-end-regexp
          (concat "\\<\\("
                  (mapconcat 'identity octave-end-keywords "\\|")
                  "\\)\\>"))
    ))

```

Or you could directly modify octave-mod.el and just add the end regexp to octave-end-keywords.

I tested this in a random .m file with both index "end"s and block "end"s and it seemed to indent OK.  But it's a hack as far as I'm concerned and I make no guarantees.

BTW, octave-block-end-regexp is the relevant variable -- that's what gets used in the indentation code.

---

### Post by manzdagratiano on 2010-09-17
> **jpkotta said:**
> As the comment says, it is tricky.  Basically, the problem is that "end" can be used as an index to a vector or to close a code block.  Thus it becomes necessary to distinguish them in the indentation code.  I think this will work (it assumes that "end"s that finish a block only have spaces and comments after them, which usually won't occur for index "end"s):

```

(eval-after-load "octave-mod"
  (progn
    (add-to-list 'octave-end-keywords "end[[:space:]]*\\([%#].*\\|$\\)")
    (setq octave-block-end-regexp
          (concat "\\<\\("
                  (mapconcat 'identity octave-end-keywords "\\|")
                  "\\)\\>"))
    ))

```Or you could directly modify octave-mod.el and just add the end regexp to octave-end-keywords.

I tested this in a random .m file with both index "end"s and block "end"s and it seemed to indent OK.  But it's a hack as far as I'm concerned and I make no guarantees.

BTW, octave-block-end-regexp is the relevant variable -- that's what gets used in the indentation code.


Thanks so much for the input! I am going to try it out now. However, doesn't the 'octave-block-end-regexp' just read the 'octave-end-keywords' list and match anything in there to the begin keywords? It was mysterious how that did not work. In any case, I think I will file a bug report on octave's bugzilla, as this 'end' functionality should work.

---

### Post by manzdagratiano on 2010-09-17
Hmmmm... I realized the code was doing the same thing - appending "end" to the octave-end-keywords list, and then tell octave-block-end-regexp to read the updated list. When I fired up emacs with this in my .emacs file, I got the error that the value as variable of "octave-end-keywords" was void, so bummer. However, I am still very perplexed as to why appending end manually to the two environments manually in octave-mod.el does nothing!

---

### Post by jpkotta on 2010-09-18
> **manzdagratiano said:**
> Hmmmm... I realized the code was doing the same thing - appending "end" to the octave-end-keywords list, and then tell octave-block-end-regexp to read the updated list. When I fired up emacs with this in my .emacs file, I got the error that the value as variable of "octave-end-keywords" was void, so bummer. However, I am still very perplexed as to why appending end manually to the two environments manually in octave-mod.el does nothing!

Do you have everything in the eval-after-load?  eval-after-load will only eval things after the specified .el file is loaded, thus there should be no undefined variables.  

If you are editing octave-mod.el, make sure there is no corresponding .elc file, as that will be preferred.  You can either recompile octave-mod.el or put octave-mod.el in a directory nearer to the beginning of load-path.

---

### Post by manzdagratiano on 2010-09-18
> **jpkotta said:**
> Do you have everything in the eval-after-load?  eval-after-load will only eval things after the specified .el file is loaded, thus there should be no undefined variables.  

If you are editing octave-mod.el, make sure there is no corresponding .elc file, as that will be preferred.  You can either recompile octave-mod.el or put octave-mod.el in a directory nearer to the beginning of load-path.

This is precisely what I was made to understand in the last few hours - I filed a bug report with emacs (octave-mod.el is no longer part of octave and has been moved to emacs I was told) and I was informed that the latest version of emacs has the octave-mod.el file completely rewritten, using a module smie.el that is not there in the current 23.2 version. So I pulled the latest version of emacs from the trunk in bazaar, and checkinstalled it. During the "make bootstrap" stage I came to realize that all the ".el" files were being compiled into ".elc" files, which is why merely changing the octave-mod.el file did not work at all. In this new version of emacs, the "end" keyword works just fine. There is another issue however - that there appears to be no "block-match-alist" in this version and emacs does not warn if a wrong end keyword is put in, say, "endif" with "for". I have stated this in the follow-up of the bug report. I guess I will mark the thread as "solved" for the time being - thanks a lot for your hekp all the way though - I would not have been pointed to octave-mod.el otherwise! :guitar:

---

### Post by lovelotus on 2011-08-24
> **manzdagratiano said:**
> This is precisely what I was made to understand in the last few hours - I filed a bug report with emacs (octave-mod.el is no longer part of octave and has been moved to emacs I was told) and I was informed that the latest version of emacs has the octave-mod.el file completely rewritten, using a module smie.el that is not there in the current 23.2 version. So I pulled the latest version of emacs from the trunk in bazaar, and checkinstalled it. During the "make bootstrap" stage I came to realize that all the ".el" files were being compiled into ".elc" files, which is why merely changing the octave-mod.el file did not work at all. In this new version of emacs, the "end" keyword works just fine. There is another issue however - that there appears to be no "block-match-alist" in this version and emacs does not warn if a wrong end keyword is put in, say, "endif" with "for". I have stated this in the follow-up of the bug report. I guess I will mark the thread as "solved" for the time being - thanks a lot for your hekp all the way though - I would not have been pointed to octave-mod.el otherwise! :guitar:

This thread solves my problem neatly! Good work!
By the way, I don't know how you solve the variable undefined problem.
Here is my way.I add that piece of code in the add-hook function for the octave-mode. And it works fine. Hope this will help.
```
(add-hook 'octave-mode-hook
          [COLOR="Red"](lambda ()
            (eval-after-load "octave-mod"
              (progn
                (add-to-list 'octave-end-keywords "end[[:space:]]*\\([%#].*\\|$\\)")
		(setq octave-block-end-regexp
                      (concat "\\<\\("
                              (mapconcat 'identity octave-end-keywords "\\|")
                              "\\)\\>"))
		))[/COLOR]
            (abbrev-mode 1)
            (auto-fill-mode 1))

```

---

