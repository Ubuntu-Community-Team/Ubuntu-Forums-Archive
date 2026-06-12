---
title: "screen, xterm and termcap confusion"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by Bateau on 2013-02-19
Hello!

I have a challenge with screen (GNU screen) and putty.
I connect to an Ubuntu 12.04 box (server install) over SSH.
I have set it up and got it working. google a bit around and found A BUNCH of screenrc examples and inspiration.
so, i went to work! :)

So, my challenge is as follows:
I want to change the width and height of my splits.
and i am a bit confused. in my screenrc i have tried with resize -v <size>, resize <size>, width <size>. i have also tried to use CTRL+a:widht <size>. I am then pressented with a notice: "Your termcap does not specify how to change the terminal's width to <size>"

what does this mean? i have googled this for hours without getting any wiser :(

and what should i use in ~/.screenrc (best practice) to adjust the width of the screensplit (and height)?

---

