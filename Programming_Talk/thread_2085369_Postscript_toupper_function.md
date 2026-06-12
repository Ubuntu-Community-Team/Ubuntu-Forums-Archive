---
title: "Postscript toupper function"
date: 2012-11-17
forum: Programming Talk
---

### Post by PryGuy on 2012-11-17
Good day everyone!

I put my hands on gfxboot that uses Postscript for it's scripts. I'm absolutely new to Postscript, but I got the point and almost did everything I wanted, but I stumbled upon one thing, I need to convert string to upper case. The script contains /tolower function, but I do not get how it works. Here it is:
```
/tolower {
  dup length 0 eq { return } if
  dup length 1 sub 0 1 rot {
    over over get 32 or 2 index 3 1 roll put
  } for
} def
```
Would you, Postscript gurus, please give me a helping hand with /toupper?

Thanks in advance!

---

### Post by Lux Perpetua on 2012-11-18
I'm guessing that you have the following auxiliary functions (which are not in the PostScript standard, as far as I am aware):
```
/over {
  1 index
} def

/rot {
  3 -1 roll
} def

```Your tolower works by setting bit #5 of each character.  Too bad, it doesn't actually work:
```
GS> ([abCdE]) tolower =         
{abcde}  
GS> % Non-alphabetic characters corrupted!

```I would first restructure the function this way: ```
/tolower {
  dup length 0 eq { return } if
  dup length 1 sub 0 1 rot {
    over over get [color=blue]char_tolower[/color] 2 index 3 1 roll put
  } for
} def

/char_tolower {
  32 or   % Incorrect for non-alphabetic characters
} def
```Now it's clear what toupper should be: ```
/toupper {
  dup length 0 eq { return } if
  dup length 1 sub 0 1 rot {
    over over get [color=blue]char_toupper[/color] 2 index 3 1 roll put
  } for
} def

/char_toupper {
  32 not and   % Incorrect for non-alphabetic characters
} def
```
If you care about the issue with non-alphabetic characters, all you have to do is reimplement char_tolower and char_toupper without touching tolower and toupper.

You might notice that tolower and toupper share almost all of their code (all but one token, actually).  In PostScript, you essentially don't ever have to repeat code: the shared code can always be refactored into its own function. Here's one way to do it:```

/tolower {
    /char_tolower map
} def

/toupper {
    /char_toupper map
} def

% (c1c2...) proc map (c1'c2'...)
% where c1 proc c1'
%       c2 proc c2'
%       ...
% (In words: apply /proc to each character of the string.
% The string is modified in place.)
/map {
  1 dict begin
    [color=blue]/proc exch def[/color]
    dup length 0 eq { return } if
    dup length 1 sub 0 1 rot {
      over over get [color=blue]proc cvx exec[/color] 2 index 3 1 roll put
    } for
  end
} def
```I used a local variable in map to make it more readable; it would have been even more incomprehensible without it.  But you get the idea: the procedure to apply to each character (like char_tolower) is given as the top argument to map.

---

