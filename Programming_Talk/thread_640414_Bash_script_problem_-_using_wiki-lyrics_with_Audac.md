---
title: "Bash script problem - using wiki-lyrics with Audacious"
date: 2007-12-14
forum: Programming Talk
---

### Post by Nameless_one on 2007-12-14
I am trying to do [this](http://lyriki.com/Help:Lyriki_On_Windows#Using_Wiki-Lyrics_with_Audacious). I am running into a strange problem having to do more with bash than with wiki-lyrics, I think. 

I have enabled the Song Change plugin, and I call a script I have written to extract the artist and title information from the song name (ie the playlist entry):

```
#!/bin/bash

artist=$1
title=$1
command='/home/nameless/programs/wiki_lyrics/cli/wikilyrics.rb'

artist=${artist%%\ -*}

title=${title##*-\ }

command=$command' -k gtk -a "'"$artist"'" -t "'$title'" --sites DarkLyrics'

echo $command

$command

```

The problem is that if either string contains spaces, wikilyrics.rb treats the string up to the space as the argument - for example, if the script passes -a "Loreena McKennit", wikilyrics.rb tells me it didn't find the lyrics by "Loreena. 

I have tried many ways of passing the arguments on line "command=$command...", but nothing works. 

The weird thing is that if I call wikilyrics.rb directly from command line, ie woith this line, ```
 ./wikilyrics.rb -k gtk -a "Loreena McKennitt" -t "Blacksmith"
```, everyhting works great, and it finds the lyrics. 

Any suggestions?

---

### Post by Trumpen on 2007-12-14
Why do you construct the command in so many steps? :)

Just one is needed:

```
command='/home/nameless/programs/wiki_lyrics/cli/wikilyrics.rb'
[..]
$command -k gtk -a "$artist" -t "$title" --sites DarkLyrics

```
In this way you make the shell to call the command using $artist as a unique parameter (the same applies to $title).

Using the command xargs is another way to resolve this issue:

```
command='/home/nameless/programs/wiki_lyrics/cli/wikilyrics.rb'
[..]
echo "-k gtk -a \"$artist\" -t \"$title\" --sites DarkLyrics" | xargs $command
```

Hope this helps! :)

---

### Post by Nameless_one on 2007-12-14
Thanks, I tried your first recommendation and it worked! I am new to bash scripting. I guess storing the command and its arguments in a variable messed it up. It works even for names with spaces now. All that remains is to figure out a way to make the lyrics appear in the same window and not a new one every time I change a song. 

Thank you very much :)

---

### Post by gunnyfield on 2008-02-17
Please, can you write the corrected script and what you put in the Song Change plugin?
Thanks!

---

### Post by Nameless_one on 2008-02-20
The corrected script is this:

```
#!/bin/bash

artist=$1
title=$1
command='/home/nameless/programs/wiki_lyrics/cli/wikilyrics.rb'

artist=${artist%%\ -*}

title=${title##*-\ }

$command -k gtk -a "$artist" -t "$title" --sites DarkLyrics,Lyriki,NotPopular,AZLyrics,LyricWiki

```

However, I still find the lyrics plugin unusable, because for each song, it generates a new GTK window. If we can find a way to reuse the window for the new lyrics, this could actually be useful :)

EDIT: Bear in mind that the lines that extract the artist and title strings might not work for you. I have cofigured Audacious to  display pkaylist entries in ths manner:

<artist> - [<album>] - <songtitle>

I think it will probably work for the following format, too:

<artist> - <title>

 but probably not others.

---

### Post by DerTod on 2009-03-28
I know it is a somewhat old thread but I found a quite ugly but at least theoretically working work-around for the window reusing problem.
As long as there is only one ruby process for the user running audacious you could use the command "pkill -f ruby" in the song change plugin (you could concatenate it with the script for the lyric-retrieving or you could put it in the line "Command to run toward the end of a song").
Couldn't test it because the script won't work for me (what did you put in the song change plugin? I tried "/home/dertod/skripte/audacious.sh "%n"" but it doesn't do the trick. If I run the script in the terminal with "interpret - songname" it works).

**edit:**
I tried some tweaks and I think I've found a less ugly way of terminating the lyricwindow (it's still not reusing but at least not killing all ruby processes):
I made some changes to the original Lyric-Retrieving-Script:
```
#!/bin/bash

artist=$1
title=$1
timemili=$2
time=$(($timemili/1000))

command='ruby /path/to/wikilyrics/wiki_lyrics/cli/wikilyrics.rb'

artist=${artist%%\ -*}

title=${title##*-\ }
title=$(echo ${title%\n})

$command -k gtk -a "$artist" -t "$title" --sites DarkLyrics,Lyriki,AZLyrics,LyricWiki &
sleep $time
```
And call it by using this command in Audacious' song-change-plugin:
```
xterm -bg black -fg red -T 'lyrics' -e /path/to/script/SCRIPTNAME "%n" "%l"
```
(should work with every terminal-emulator, but xterm is really fast)
The disadvantage is, that the window lives as long as the song WOULD last (no recognition of changing the song before) and that xterm as well as the gtk window for the lyric both get focus when incarnated (probably solvable through compiz?).

**another edit:**
Somewhat fixed the focus-problem. There is a nifty tool called devilspie (universe repository). Here is my example .ds file (put it in ~/.devilspie):
```

(begin
    (if (is (application_name) "wikilyrics.rb") (minimize) )
    (if (is (window_name) "lyrics")		(minimize) )
    (if (is (window_name) "lyrics")		(skip_tasklist) )

)

```
Works fine for me (still getting into focus for a short time, but well, a lot better than before).
[B]
and yet another edit:[/B]
Found a way to (at least i hope so) safely kill an existing lyric-window on song change (and only this *hope*). I just added the line:
```
pkill -9 -f wikilyrics.rb
``` right after the shebang (the rest of the script is still the same).

---

### Post by Nameless_one on 2009-06-24
I am just bumping to post that I have written a small Audacious plugin that uses the Amarok script and displays the results in a window (which it reuses). The plugin is in Alpha state, and I won't release it until I get rid of the most serious bugs. 

I had posted a guide to use the plugin on Audacious' forums, but then the Audacious site came down. I will probably post again the insrtructions to use the plugin, here, in a new thread. I hope I will get some feedback (although I don't think I will support the plugin right now - probably from September).

---

### Post by bombacar on 2012-04-14
I solve using this line in the audacious's Song Change plugin
```
pkill -9 -f 'wikilyrics.rb' & /archivos/wiki_lyrics/cli/wikilyrics.rb -k gtk -a $(echo "%n" | sed -ne 's/ - .*$//p' | sed -e 's/ /_/g') -t $(echo "%n" | sed -ne 's/^.* - //p' | sed -e 's/ /_/g')
```

This is a simple way, but work  [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by sisco311 on 2012-04-14
Necromancy. 

[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)

Thread Closed.

---

