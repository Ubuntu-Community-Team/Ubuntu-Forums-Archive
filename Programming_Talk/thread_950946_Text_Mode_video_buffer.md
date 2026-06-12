---
title: "Text Mode video buffer"
date: 2008-10-17
forum: Programming Talk
---

### Post by Hospadar on 2008-10-17
I've become interested in writing some stuff that runs in text mode and I need to be able to control the text-mode graphics buffer (for text mode progress bars, etc).  I know there are libraries out there (ncurses, etc) to help make text-mode interfaces, and I know of plenty of places to get a hold of simple widgets like progress bars, but I'm more interested in being able to do more creative things, demos, more in-depth animations, etc.  

If anyone knows where to go to learn more about how to do this kind of thing, or could themselves write me a quick tutorial, it would be greatly appreciated.  I'd like to involve as few outside libraries as possible, I would like to be able to control this directly myself (even if I have to map every character in the terminal myself). 

On a less in-depth note, how does one a) get info about the terminal (size) and b) set the text and background colors?

Thanks for the help,
Luke

---

### Post by geirha on 2008-10-17
a) **tput cols** shows the width and **tput lines** gives you the height. 

b) Read the man-page of tput and search for it on the net. It can set colors etc. Also read up on [ANSI escape codes](http://en.wikipedia.org/wiki/ANSI_escape_code)

```
echo -e '\e[1;31mred\e[0m'
```

On a side note, the aalib is cool. mplayer can play videos in ascii using it: ```
mplayer -vo aa video.mpg
```

---

### Post by red_Marvin on 2008-10-19
If you want to write demo stuff and using cli as a low res videoscreen you might be interested in aalib, I think it's greyscale though. There should be a demo around, named bb or something like that.

---

