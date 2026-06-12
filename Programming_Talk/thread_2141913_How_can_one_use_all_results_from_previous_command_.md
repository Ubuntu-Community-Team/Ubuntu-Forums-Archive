---
title: "How can one use all results from previous command in a new command?"
date: 2013-05-04
forum: Programming Talk
---

### Post by shantiq on 2013-05-04
[FONT=microsoft sans serif][SIZE=2]i have found in recent times that


```
find|grep -i  NAMEOFFILEIAMLOOKINGFOR
```   is really excellent for finding scattered music files by one artist all over my harddrive

now once i have the results i want to play all the found music files with ```
nvlc --nocolor
``` 

how could i write just one line with both commands which would read the results from command one and use info for command two?

files extensions here would be flac wv ape mp3 zip

so something like 

find|grep -i  NAMEOFFILEIAMLOOKINGFOR && nvlc --nocolor * FILESFOUNDINPREVIOUSCOMMAND     if you see what i mean


i cannot as yet think of a way to do this ...  can any of you?
the simplest [least amount of code] is the route i seek here




thanx in advance    shan[/SIZE][/FONT]

---

### Post by sisco311 on 2013-05-04
You don't have to use pipes and grep:
```
find ./ -iname '*whatever*' -exec nvlc --nocolor {} +
```

Check out: [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by shantiq on 2013-05-04
thank you so much sisco

works well    also how can i filter the results so it only keeps files with extension cue;zip and does not mind if some of them are not present in search

---

### Post by sisco311 on 2013-05-04
Please check out the link I posted. Especially the 2nd section. ;)

---

### Post by shantiq on 2013-05-04
you mean in essence this section

> [COLOR=#000000][FONT=courier]find . \( -name '*.mp3' -o -name '*.jpg' \) -name 'foo*' -print[/FONT][/COLOR]
./bar/foo.jpg [COLOR=#000000][FONT=courier]./foo.mp3[/FONT][/COLOR]






ok  artist i was lookin for here was zappa so this pretty much does what i wanted  [again thanx]

```
find ./ \( -iname '*zappa*.cue' -o -iname '*zappa*.zip' \) -exec nvlc --nocolor {} +
```

---

