---
title: "emacs23 not using default keyboard layout"
date: 2010-04-11
forum: Programming Talk
---

### Post by mfearby on 2010-04-11
I have two keyboard layouts configured in Ubuntu 9.10 64-bit. The standard USA and one of my own where I've turned "[" into a dead key so that the following vowel gets a macron, like so "&#257;", and the backtick accents the following vowel: "á". The third-level AltGr standard method is far to slow and annoying when typing a lot of text using these characters, which is why I went with the custom setup.

The standard, unmodified, USA keyboard is configured as the default. After a reboot, it's the default, and my dead keys don't work unless I switch keyboard layouts. Problem is, emacs23 has somehow decided that "[" (with USA layout) should be a dead key but the "`" key isn't recognised as a dead key. I've tried switching layouts to my custom keyboard, and the "[" doesn't add a macron to the next letter, neither can I actually type a left-square-bracket, and the "`" key just won't work at all (neither typing its character or accenting the next one).

I'm quite new to emacs but I'm keen to learn, but if I can't type square brackets, then I'm gonna have to stick with Netbeans, where I just can't get enclojure to work, alas.

Any ideas how to set the keyboard layout for emacs23? I've tried C-x RET C-\ to select input method but there is no standard US one to choose from. Only ones I'm not interested in.

Thanks.

---

### Post by Cracauer on 2010-04-11
Are you using emacs in a terminal or native X11?

---

### Post by jpkotta on 2010-04-11
I've never dealt with keyboard layouts, but I can tell you a bit about Emacs input methods.  They're ways to "easily" insert non-ascii characters, usually tied to a specific alphabet (thus they don't really have much to do with the keyboard layout).  I use the TeX input method, which makes TeX-like key sequences insert special characters.  For example, \`a inserts à, \=a inserts &#257;, \pi inserts &#960;, and so on.

You can see what Emacs is trying to do with keystrokes by doing C-h k *key*.  Maybe you'll see a difference between [ and `.

---

### Post by mfearby on 2010-04-11
> **Cracauer said:**
> Are you using emacs in a terminal or native X11?

Using X11, GNOME with Ubuntu 9.10 64-bit, with the standard (unmodified) "USA" keyboard as my system-wide default, and my custom layout as an option that I activate when needed by clicking on the keyboard chooser up the top-right of my screen.

---

### Post by mfearby on 2010-04-11
> **jpkotta said:**
> I've never dealt with keyboard layouts, but I can tell you a bit about Emacs input methods.  They're ways to "easily" insert non-ascii characters, usually tied to a specific alphabet (thus they don't really have much to do with the keyboard layout).  I use the TeX input method, which makes TeX-like key sequences insert special characters.  For example, \`a inserts à, \=a inserts &#257;, \pi inserts &#960;, and so on.

They sound a little involved for me :-) The reason I like my custom layout for entering Latin vowels with macrons and accents is that it's just one conveniently-located key to press before the vowel I want to modify. I appreciate that if you have to enter a wider variety of characters this isn't viable, but my requirements are small, thankfully, and doing gymnastics with my fingers on a regular basis isn't going to work. Oh, and I'll only be using emacs to learn clojure, and really only call upon my custom layout with OpenOffice and Firefox when needed (when I never need to type "`" or "[" so losing the ability to enter those characters when I'm typing Latin isn't an issue).

> **jpkotta said:**
> You can see what Emacs is trying to do with keystrokes by doing C-h k *key*.  Maybe you'll see a difference between [ and `.

Thanks. I'll check that when I go home.

---

### Post by mfearby on 2010-04-12
I found the problem. When I tried pressing "[" after invoking C-h k, it wouldn't recognise anything. It was as if the key didn't work. Then I realised I was trialing a method of setting up a dead key, which I abandoned (or thought I did), but left a ~/.XCompose file still there which contained:

<bracketleft> <a>                	: "&#257;"   U0101 # LATIN SMALL LETTER A WITH MACRON

I've removed this file, restarted emacs, all's well :-) My fault, but thanks for the troubleshooting tips.

---

