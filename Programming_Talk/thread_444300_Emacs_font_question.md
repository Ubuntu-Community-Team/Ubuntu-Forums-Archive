---
title: "Emacs: font question"
date: 2007-05-15
forum: Programming Talk
---

### Post by O-pos on 2007-05-15
Hello,

'm using Emacs21 for statistical calculations. When I installed emacs, both GUI window and fonts was looking very ugly. I downloaded emacs-snapshot-gtk and now the window is ok, but that ugly font remained. So now I want to change the font. I'd like very much to use the same font my emacs that is default one for GNOME-Terminal. Any ideas how can I do that?

I googled and searched some sites regarding that problem, but didn't understand anything..

Thanks in advance,

O-pos

---

### Post by ilautar on 2007-05-15
You need a XFT emacs if you want to have antialiased fonts (read this: [http://peadrop.com/blog/2007/01/06/pretty-emacs)](http://peadrop.com/blog/2007/01/06/pretty-emacs)).

However, if you just want to use a pretier monospace font, do:
M-x customize-face
put default

and change to whatver you want, save. You can also check-it-out how it looks like w/o saving.

---

### Post by O-pos on 2007-05-15
Thanks for the reply, nice link: everything's ok except black background color. Will it be default after I install it as described in the link?

I want monospace font, that is being used in the terminal.

I also would like to change color-highlighting to more beautiful colors

how can I do that in a primitive language? :

"M-x customize-face
put default"

---

### Post by ilautar on 2007-05-15
Well, this can all be done, however, it is to much to be typing every change.

I have another good link for you, [www.emacswiki.org](www.emacswiki.org), take a look at custimizing section. You should be able to find everything there.

I can also provide you with some sample .emacs which does some of these customizations (like colors).

---

### Post by O-pos on 2007-05-15
I saw emacswiki, but it's so complicated that for me it will take few days to unterstand what they want to say.. what is sample.emacs? do you have maybe any precompiled emacs for ubuntu with snapshot-gtk and nice font?

---

### Post by ilautar on 2007-05-15
> **O-pos said:**
> I saw emacswiki, but it's so complicated that for me it will take few days to unterstand what they want to say.. what is sample.emacs? do you have maybe any precompiled emacs for ubuntu with snapshot-gtk and nice font?

Ok, I can see you as an emacs 'wanabe' :)

I'll try to explain what emacs is about and how can you alter behaviour (including configuration).

emacs core is written in C, however, emacs includes a powerfull elisp language, which is used to write everything else apart from 'core'. elisp can be used to alter any part of emacs behaviour.

Now, with sample '.emacs'. .emacs is a file in your $HOME directory (like /home/opos) which contains elist code. This file is executed upon start of emacs. So, by defining/altering various elisp variables and functions, you alter the behaviour of emacs. By sample '.emacs' I meant and example of how '.emacs' looks like.

You want to do the following:
- change backgroung color to balck
- change colors used for highlightning

Now you know (the basics) what .emacs is. Every (regular) emacs user probably has its own custom .emacs file, which customized look&feel to his own preferences.

For example, I use this to alter behaviour (like tab spaces & colors) of my emacs (put it into yours .emacs):

(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(auto-hscroll-mode nil)
 '(blink-cursor-mode t)
 '(case-fold-search t)
 '(dabbrev-case-fold-search nil)
 '(debug-on-error t)
 '(global-font-lock-mode t nil (font-lock))
 '(menu-bar-mode nil)
 '(scroll-bar-mode nil)
 '(show-paren-mode t)
 '(show-paren-style (quote expression))
 '(tool-bar-mode nil nil (tool-bar))
 '(transient-mark-mode t)
 '(truncate-lines nil)
 '(truncate-partial-width-windows nil))
(custom-set-faces
  ;; custom-set-faces was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(default ((t (:stipple nil :background "#001700" :foreground "lightgrey" :inverse-video nil :box nil :strike-through nil :overline nil :underline nil :slant normal :weight normal :height 120 :width normal :family "lucida console"))))
 '(cursor ((t (:background "yellow" :foreground "black"))))
 '(mode-line ((((type x w32 mac) (class color)) (:background "grey20" :foreground "grey80" :box (:line-width -1 :style released-button)))))
 '(region ((((class color) (background dark)) (:background "#004400"))))
 '(scroll-bar ((t (:background "grey20" :foreground "grey80"))))
 '(show-paren-match ((((class color)) (:background "#003300"))))
 '(vertical-border ((nil (:foreground "gray20"))))
 '(window-number-face ((((type x w32 mac)) (:foreground "cyan"))))
 '(wn-modeline-face ((t (:foreground "cyan")))))

This is only a part of customization I use. Once you get familiar with emacs and start using advanced features (or start using it as your primary editor), you will also put your own preferences there.

NOTE: some options may not be to you taste, like disabling menu. Just delete those lines from above code.
This goes for other options too, as they are mostly specific for user having them in his own '.emacs'.

I will be glad to help you further on, but you should also read some guides on using emacs. A very good place to start is:
M-x info

This will provide you with info pages included with your emacs installation.

Hopefully, you will see the 'light' in using emacs, which can really save you time if you're serious about text editing (be it programming or something else requiring you to input text).

---

### Post by fr4nko on 2009-05-21
Hi,

talking about emacs and font configuration, it seems to me that you are getting confused with a lot of complicated customisations. In order to have emacs with nice anti aliased fonts you need to grab emacs-snapshot (which comes with Xft support) and modify some font configurations, I've already made a [post]("http://ubuntuforums.org/showpost.php?p=7266554&postcount=1") about that. In particular I gives some suggestions in order to customize exactly the font rendering in order to have exactly the same fonts you are using with gnome applications.

Otherwise, to use emacs effectively, just go through the initial tutorial which is very well done and learns you the most important things. In order to use emacs effectively you don't need to be an emacs guru. You don't need to compile emacs yourself, you don't need to write tons of list configurations in your .emacs file.

I hope this helps! Enjoy programming with emacs ;)

Francesco

---

