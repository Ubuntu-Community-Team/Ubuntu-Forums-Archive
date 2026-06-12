---
title: "scripting (bash, awk, sed)"
date: 2012-12-22
forum: Programming Talk
---

### Post by Drenriza on 2012-12-22
Hi guys.

I have a file containing the following lines
> DerekSagan won a  Rapier with ticket #7 DerekSagan won a  Maelstrom with ticket #8 Taro Dos won a  Malediction with ticket #8 MrPopper won an  Imperial Navy Slicer with ticket #6 The Mapsdog won a  Drake with ticket #8 banker 1 Khagah won a  Nightmare with ticket #8 Alenzo won a  Rorqual with ticket #1 Cpt Komoran won a  Daredevil with ticket #4 Dara Minerva won an  Ashimmu with ticket #6 Coruka won a  Raptor with ticket #3

My question is.
How can i do so the above end up as follows

DerekSagan
Rapier
#7
DerekSagan
Maelstrom
#8
Taro Dos
Malediction
#8
and so on.

So the "won a", "won an" and "with ticket" are removed, and the word / words before it in written to a new line.

I have tried a few things to solve this. But i cant really figure it out with bash or awk.

Thanks on advance.
Kind regards.

---

### Post by steeldriver on 2012-12-22
well it's a bit inelegant, but with sed:

```
sed -r -e 's/won an? /\n/g' -e 's/with ticket /\n/g' -e 's/#[0-9]+ /&\n/g'
``````
echo "DerekSagan won a Rapier with ticket #7 DerekSagan won a Maelstrom with ticket #8 Taro Dos won a Malediction with ticket #8 MrPopper won an Imperial Navy Slicer with ticket #6 The Mapsdog won a Drake with ticket #8 banker 1 Khagah won a Nightmare with ticket #8 Alenzo won a Rorqual with ticket #1 Cpt Komoran won a Daredevil with ticket #4 Dara Minerva won an Ashimmu with ticket #6 Coruka won a Raptor with ticket #3 " | sed -r -e 's/won an? /\n/g' -e 's/with ticket /\n/g' -e 's/#[0-9]+ /&\n/g'
DerekSagan
Rapier
#7
DerekSagan
Maelstrom
#8
Taro Dos
Malediction
#8
MrPopper
Imperial Navy Slicer
#6
The Mapsdog
Drake
#8
banker 1 Khagah
Nightmare
#8
Alenzo
Rorqual
#1
Cpt Komoran
Daredevil
#4
Dara Minerva
Ashimmu
#6
Coruka
Raptor
#3


```

---

### Post by Drenriza on 2012-12-22
Cool, thanks steel.

I need to get into sed more.

P.S.
If you think your solution is unelegant. Don't wish to see what i was trying to do xD

---

