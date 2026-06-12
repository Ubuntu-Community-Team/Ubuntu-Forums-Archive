---
title: "for loop help"
date: 2012-10-08
forum: Programming Talk
---

### Post by thaitang on 2012-10-08
i hope someone can see why my for loop is not working as desired. I have a folder of .html files with wierd names I want to change to something more meaningful. All of the html code in each file is on a single line (no. 1), making things (so I thought), straightforward. I thought I should be able to print the single line using sed and pipe it to perl to make use of its non-greedy wildcard (I know I read about sed's non-greedy syntax too but it seemed archaic compared to perl's so I have always just used perl's) to filter out the fields I want into vars that I will use to rename each file.

```
for file in * ; do
  litTitle=`sed -n "1 p" "$file"|perl -p -e 's/^.*?<title>(.*?)<\/title>/\1/'`
  #authName=`sed -n '1p' "$file"|perl -p -e 's/^.*?<\/title>.*?<title>(.*?)<\/title>/\1/'`
   echo "$file $authName $litTitle $file"
  #mv "$file" "$authName"_"$litTitle".html
done
```...but the $litTitle var contains the entire contents of the line printed without substituting for the text (.*?) between first set of <title></title> tags as desired.

I know I have done this before but damn if I can get it to work now. If anyone can see the problem and let me know I would appreciate it.

cheers,
tt

---

### Post by conradin on 2012-10-08
Try inserting set -xv
just below the shebang.
it might help you trace through. On the html file I used, the part that was supposed to pick up the title tag took the <!DOCTYPE> tag instead of the title. perhaps your code never gets to the title tag. Ill have a deeper look when Im bored at work tomorrow.

---

### Post by Vaphell on 2012-10-08
care to post some example of that first line? it's hard to debug something without the actual data :)
either way i think perl uses $1 $2 ... to call selection groups instead of sed's \1 \2 (edit: both ways seem to work in perl)

---

### Post by trent.josephsen on 2012-10-09
By memory, \n works within the expression and in the substitution string; $n works in any context after the expression has ended. Note that \1 \2 etc. are not recognized by Perl, but by the regex engine, so if you were to do a substitution expression with s/PATTERN/CODE/e, you would be forced to use $1 $2 etc. in the CODE portion.

---

