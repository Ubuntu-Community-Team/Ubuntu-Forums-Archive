---
title: "Making uppercase and lowercase letters act the same..."
date: 2007-10-01
forum: Programming Talk
---

### Post by smartboyathome on 2007-10-01
I am going to try to make a distro for myself, and I was wondering if there is a way to make uppercase and lowercase letters act like each other (ie: 'APT-GET INSTALL UBUNTU-DESKTOP' and 'apt-get install ubuntu-desktop' are the same thing) with bash, or even zsh. I am wanting to do this because it would help me be lazy in the end. I tried searching google, but came up with only scripts to convert uppercase to lowercase. Thanks to anyone who helps.

---

### Post by pmasiar on 2007-10-01
thats not good idea, Unix is case sensitive - command names are case sensitive. Also command parameters are case sensitive, often -v and -V mean different things.

My guess it that if are not aware about case sensitivity, you are not ready to make your own distro :-) Why you so dislike lowercase?

---

### Post by aks44 on 2007-10-01
> **pmasiar said:**
> Why you so dislike lowercase?

Reminds me of one of my colleagues who always leaves Caps-Lock enabled whatever computer she uses.
One day I was really fed up and made my Caps-Lock key behave like plain old Shift. Unfortunately for her, most of our colleagues did the same since... 8-)


Now I can hear you... why do I dislike uppercase? :p

---

### Post by scruff on 2007-10-01
EVERYTHING in *nix is case sensitive. I imagine there's not a whole lot that **wouldn't** break if you really got into this. After 6 or 7 years of using nothing but Linux, I actually hate that Windows **isn't** case sensitive in most cases...

---

