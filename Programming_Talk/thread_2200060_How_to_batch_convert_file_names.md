---
title: "How to batch convert file names?"
date: 2014-01-17
forum: Programming Talk
---

### Post by mick7 on 2014-01-17
Hi, I'm running Edubuntu 12.04. I have a collection of educational video files whose filenames correspond to their youtube IDs (meaningless strings of characters). It is very difficult for my students to find the right video for the topic they need. I also have a .JSON file that lists the video title with the video's youtube ID, like this:

{
"C-2Ln0pK3kY": "algebra-ii--imaginary-and-complex-numbers", 
  "01c12NaUQDw": "inverse-of-a-2x2-matrix", 
  "ZD8THEz18gc": "milankovitch-cycles---precession-and-obliquity", 
  "5lmHzAHbtzg": "market-capitalization",
...
}

My question is whether there is a way to convert the file names of all the videos from the youtube ID to the title of the videos. For example

C-2Ln0pK3kY.mp4 would become Algebra-ii--imaginary-and-complex-numbers.mp4

There are hundreds of videos and it would be impossible to do by hand. Any help would be appreciated. Thanks in advance for any help you can give!

---

### Post by Vaphell on 2014-01-17
is the file in exactly that format, that is key/value pair in its own line?

```
while read -r code name; do [ -f "$code.mp4" ] && mv -v -- "$code.mp4" "${name^}.mp4"; done < <( awk 'BEGIN { FS="\""; } /:/{ print $2, $4; }' in.json )
```

```
$ cat in.json
{
"C-2Ln0pK3kY": "algebra-ii--imaginary-and-complex-numbers",
"01c12NaUQDw": "inverse-of-a-2x2-matrix",
"ZD8THEz18gc": "milankovitch-cycles---precession-and-obliquity",
"5lmHzAHbtzg": "market-capitalization"
}
$ touch {C-2Ln0pK3kY,01c12NaUQDw,ZD8THEz18gc,5lmHzAHbtzg}.mp4
$ ls
01c12NaUQDw.mp4  5lmHzAHbtzg.mp4  C-2Ln0pK3kY.mp4  in.json  inverse-of-a-2x2-matrix.mp4  ZD8THEz18gc.mp4
$ **while read -r code name; do [ -f "$code.mp4" ] && mv -v -- "$code.mp4" "${name^}.mp4"; done < <( awk 'BEGIN { FS="\""; } /:/{ print $2, $4; }' in.json )**
`C-2Ln0pK3kY.mp4' -> `Algebra-ii--imaginary-and-complex-numbers.mp4'
`01c12NaUQDw.mp4' -> `Inverse-of-a-2x2-matrix.mp4'
`ZD8THEz18gc.mp4' -> `Milankovitch-cycles---precession-and-obliquity.mp4'
`5lmHzAHbtzg.mp4' -> `Market-capitalization.mp4'
$ ls
Algebra-ii--imaginary-and-complex-numbers.mp4  Inverse-of-a-2x2-matrix.mp4  Milankovitch-cycles---precession-and-obliquity.mp4
in.json                                        Market-capitalization.mp4

```

---

### Post by mick7 on 2014-01-20
Awesome. This is exactly what I needed. Thanks.

---

### Post by mörgæs on 2014-01-20
Good, please mark the thread 'solved'.

---

