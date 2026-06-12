---
title: "vim: list of available colors?"
date: 2011-08-22
forum: Programming Talk
---

### Post by CryptKeeper777 on 2011-08-22
I can't really believe that Google didn't solve this issue. I'm just playing around with the colors of the line numbers in vim ("highlight LineNr ctermfg=... ctermbg=..." in the .vimrc file) but I don't know what colors are available.

Is there a list of the available colors (names/numbers)?

---

### Post by dazman19 on 2011-08-22
is there a switch for it to accept hexidecimal? or binary?

my understanding is 32bit colours are quite easy to manipulate with bit shifting or hex.

---

### Post by CryptKeeper777 on 2011-08-22
I actually just want a list with all colors that I can use. The obvious ones like red, blue, green, black, white etc. are not a problem, I just couldn't find a list with all these colors... I don't need fancy colors, just the basic ones, but I don't know, which colors belong to these basic colors. I tried out purple for example, but vim didn't recognize it.

---

### Post by cgroza on 2011-08-22
I think the colours are terminal dependent. I know xterm supports 256 colours.

---

### Post by CryptKeeper777 on 2011-08-23
I'm using Terminator, if that helps to help me...

---

### Post by ja27 on 2012-10-19
Editing VIM colorschemes: color names I have found until now:

black = 0
darkgray

darkred = brown = 1
red = lightred

darkgreen = 2
green = lightgreen

darkyellow = 3
yellow

darkblue = 4
blue = lightblue

darkmagenta = 5
magenta = lightmagenta

darkcyan = 6
cyan = lightcyan

gray = lightgray = 7
white

Hex values (e.g. #ac2d00) can only be used with the gvim (guifg/guibg) entries!

---

