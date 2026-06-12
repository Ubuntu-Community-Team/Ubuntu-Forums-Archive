---
title: "highlight multiple searches editor - suggestions"
date: 2013-07-04
forum: Programming Talk
---

### Post by mrmaxpires on 2013-07-04
Hello guys,

I'm openning this thread to ask you if you know an text editor that allow do highlight multiple words with differents colors.
In windows i use Notepad++, and it has a option call "style token" with 5 different colors that I can use to highlight any part of the txt file... although i can run notepad++ in linux using wine, but i'm trying to find another solution to do this...

I need this kind of feature to help me in log analisys... if you guys have any other editor that does that, please help me! :) 

thank you
BR

Max

---

### Post by mrmaxpires on 2013-07-04
I found an script for VI that enable something like that:

[http://vim.wikia.com/wiki/Highlight_multiple_words](http://vim.wikia.com/wiki/Highlight_multiple_words)

but the problem now is with the numeric keypad mapping... the script of link above, assumes you have a numeric keypad already mapped on vi... 
i'd tried some ways to do it, but didn't work... 


any ideia?

---

### Post by shawnhcorey on 2013-07-04
If you're using ViM, add this line to your `~/.vimrc` file. It will highlight all the search matches.
```
set hlsearch
```

---

### Post by ofnuts on 2013-07-05
Are you talking about random search results or about syntax highlighting?

---

### Post by mrmaxpires on 2013-07-05
[COLOR=#000000]Ago[/COLOR]
[COLOR=#000000]ofnuts,

i'm talking about highlight multiple searches results... 
example:

1) search <word1> - result will highlight all occurrences of word1

2) search <pattern1> - result will [/COLOR][COLOR=#000000]highlight all [/COLOR][COLOR=#000000]occurrences of pattern1. 

in notepad++ i do that by selecting the word or pattern with mouse then right click on selected text and chose an style (color).[/COLOR]

---

### Post by mrmaxpires on 2013-07-09
any tips?

---

### Post by alan9800 on 2013-07-09
you might give a look to [jEdit](http://www.jedit.org/index.php?page=features).

---

