---
title: "confused by grep / awk"
date: 2009-03-09
forum: Programming Talk
---

### Post by gnarf on 2009-03-09
I'm trying to run a script to display on conky my current F@H protein and other related info

the script is
```
NAME="$(grep Name /home/gnarf/.folding/unitinfo.txt | sed -e "s/Name: //")"
#PROJECT="$( grep Project /home/gnarf/.folding/FAHlog.txt | awk /'Project: /{print $3}')"
NUMBER="$(grep Project /home/gnarf/.folding/FAHlog.txt | awk 'END{print $3}' )"

### data from psummary.txt
CREDIT=$(grep "$NUMBER" /home/gnarf/.folding/psummary.txt | awk {'print $(NF-4)'})
CORE=$(grep "$NUMBER" /home/gnarf/.folding/psummary.txt | awk {'print $(NF-2)'})

echo -e "$CREDIT pts, $CORE"
echo -e "$NUMBER"
```
So the original script is the commented PROJECT line, I added the NUMBER line and the subsequent $NUMBER in the CREDIT and CORE lines
What I want is for the script to find the last project number in FAHlog.txt which NUMBER does, however it won't input into CREDIT or CORE, but PROJECT did this but not for only the last Project: #### . 


Thanks

---

### Post by ghostdog74 on 2009-03-09
too much use of grep/awk/sed. Only awk is needed.
show a sample of your input file. and describe what you want to get clearly.

---

