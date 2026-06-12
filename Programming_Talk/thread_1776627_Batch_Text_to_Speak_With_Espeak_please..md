---
title: "Batch Text to Speak With Espeak please."
date: 2011-06-06
forum: Programming Talk
---

### Post by sTpny on 2011-06-06
Hi Everyone, 

I use my mp3 player to listen to audio-books and I'd like to know how to make my own from ebooks using espeak. So.. 

I have chopped an ebook (Mary Crofts "How I clobbered every cash confiscatory agency known to man, the 1000 Papercuts Technique") into Parts and Chapters and saved them all individually as separate files, ex:

Papercuts - Part 1 - 1 - What Happened
Papercuts - Part 1 - 2 - How it happened

etc.. 

Now I would like to use the magic of espeak to convert the files into usable audio for my mp3 player, but I would also like to use the magic of bash scripting to convert all of them at the same time. My Bash Magic is still very limited though, so I have no clue how to do this. 

Could someone please help formulate a command line that will batch convert my ebook files into mp3's, so I can keep learning new things as a I walk my little weiner dog. This will be very much appreciated. 

Thanks.

---

### Post by epicoder on 2011-06-06
Run this command in bash (It won't work in dash) in the same directory as your text files:
```
for file in "./Papercuts - Part*.txt"; do espeak [your options here] -f "$file" --stdout | lame [your options here] - $(basename "$file" .txt)".mp3"; done
```This code is untested (as I am running windows atm) so please point out any mistakes I may have made.

---

### Post by sTpny on 2011-06-07
> **sh228 said:**
> Run this command in bash (It won't work in dash) in the same directory as your text files:
```
for file in "./Papercuts - Part*.txt"; do espeak [your options here] -f "$file" --stdout | lame [your options here] - $(basename "$file" .txt)".mp3"; done
```This code is untested (as I am running windows atm) so please point out any mistakes I may have made.


Thanks.. I should be able to make something work with that.. I'll try it out in the AM.

---

### Post by geirha on 2011-06-07
The * needs to be outside the quotes, otherwise it won't have the special wildcard meaning.

```

for f in "Papercuts - Part"*.txt; do
  espeak -f "$f" --stdout | lame - "${f%.txt}.mp3"
done

```

---

### Post by sTpny on 2011-06-08
> **geirha said:**
> The * needs to be outside the quotes, otherwise it won't have the special wildcard meaning.

```

for f in "Papercuts - Part"*.txt; do
  espeak -f "$f" --stdout | lame - "${f%.txt}.mp3"
done

```


That worked.. thanks. :)

---

### Post by epicoder on 2011-06-08
Actually, * does work in double quotes.
```
# for x in "./desk*.png"
> do echo $x
> done
./desktop.png ./desktop2.png
```
geirha was most likely thinking of single quotes ' , in which everything loses it's special meaning (except ' ).

---

### Post by geirha on 2011-06-08
> **sh228 said:**
> Actually, * does work in double quotes.
```
# for x in "./desk*.png"
> do echo $x
> done
./desktop.png ./desktop2.png
```
geirha was most likely thinking of single quotes ' , in which everything loses it's special meaning (except ' ).

Nope. The for-loop there only iterates once, on the single word "./desk*.png". The pattern is expanded on the echo command, since you failed to quote $x properly.

```

$ touch file1.txt file2.txt
$ for f in "./file*.txt"; do echo "$f"; done
./file*.txt
$ for f in ./file*.txt; do echo "$f"; done
./file1.txt
./file2.txt

```

---

