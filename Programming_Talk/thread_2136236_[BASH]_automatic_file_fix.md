---
title: "[BASH] automatic file fix"
date: 2013-04-16
forum: Programming Talk
---

### Post by wolfgentleman on 2013-04-16
I have an auto-generated Change Log but the dates are wrong. I am trying to make a two-liner fix for it. I have a file with the correct dates corresponding with with the log. Here is what I have:
```

$ clog=$(for\(\(i=1\;i<=\$\(wc -l <dates\)\;i+=1\)\)\; do sed 's/\( --  <>  \)Tue, 16 Apr 2013 18:[0-3][0-9]:[0-5][0-9] -0500/\\1\$\(sed -n '\$\{\$i\}p' dates\)/' <changelog\; done)
$ echo $clog > changelog

```

However the first line produces an error:
bash: =$(wc: No such file or directory


What am I doing wrong?
[RIGHT]Thanks in Advance,
Wolfgentleman
[/RIGHT]

---

### Post by prodigy_ on 2013-04-16
Pardon me for being blunt but this is the ugliest piece of bash I've ever seen. Just use heredoc: ```
cat <<-EOF > /path/to/outfile
    # code here
    ...
EOF
```

---

### Post by steeldriver on 2013-04-17
Perhaps if you explained more clearly exactly what you are trying to do someone could suggest a neater way - if you're trying to replace stuff in one file with stuff read in parallel from another file I'd suggest something like a while-read loop (which would avoid the nasty $(wc -l <file) construct)

However fwiw I think your \ escapes are incorrect i.e. in the 'for' loop you can just do

```
result=$(for ((i=0;i<=$(wc -l <file1);i++)); do *something*; done)
```

e.g.

```
$ cat file1
a b c d e
f g h i j
k l m n o
p q r s t
$ 
$ for ((i=0;i<=$(wc -l <file1);i++)); do echo $i; done
0
1
2
3
4
$ 
$ result=$(for ((i=0;i<=$(wc -l <file1);i++)); do echo $i; done)
$ echo "$result"
0
1
2
3
4
$ 
```

---

### Post by wolfgentleman on 2013-04-17
basically I have a file that has dates:
```
Thu, 04 Apr 2013
Mon, 16 Jul 2012
Wed, 15 Feb 2012
Wed, 16 Nov 2011
Fri, 12 Aug 2011
...
```


Then I have a file with dates to be replaced by the dates in the other file:
```
...
 * Fixed possible crash when deleting profiles.
  * Fixed encoding when invitation contains channel password with spaces.

 --  <>  Tue, 16 Apr 2013 18:34:22 -0500

ts3-client (3.0.10) ; urgency=low

  * Added Opus voice and music codecs. Requires server 3.0.7 or later.
...
```

I want to replace "Tue, 16 Apr 2013 18:34:22 -0500" with "Thu, 04 Apr 2013":
first date in dates file replaces the first date of the first change.

What I was trying to do was for every line in the dates file it was to a regex search for "(--  <> )Tue, 16 Apr 2013 18:[0-3][0-9]:[0-5][0-9] -0500" and replace it with <text contained in parentheses><date from date file>

---

### Post by Vaphell on 2013-04-17
you don't even have to capture for-loop output (or any loop for that matter), you can redirect everything that gets produced inside it to file
*for ....; do .....; done > output.file*
i see you want to modify input, you need intermediary, eg tmpfile renamed later, because reading and writing at the same time produces garbage


about the substitution part: do you want to substitute first date in place of first match, 2nd in place of 2nd, 3rd for 3rd, etc? Or all occurences of the pattern with the first date, then copy of the same but with another date, ...? Because if i read the code correctly option #2 is what happens.

try something like this
```
$ cat sedtest.txt
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
[B]$ pattern='( --  <>  )Tue, 16 Apr 2013 18:[0-3][0-9]:[0-9][0-9] -0500'
$ while read d; do sed -r -i "0,/$pattern/ s/$pattern/\1$d/" sedtest.txt; done < dates.txt [/B]
$ cat sedtest.txt
 --  <>  Thu, 04 Apr 2013
 --  <>  Mon, 16 Jul 2012
 --  <>  Wed, 15 Feb 2012
 --  <>  Wed, 16 Nov 2011
 --  <>  Fri, 12 Aug 2011
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
```

---

### Post by steeldriver on 2013-04-17
If you want to replace the next match with the next line from the 'dates' file then I kind of think there should be an elegant way using the GNU sed 'R *file*' command (read and queue the next line from *file*, and insert it at the end of the next 'cycle') - unfortunately so far I can only make it *append* the new date on the following line i.e.

```
$ sed '/--  <>/ {
R dates
s/\(--  <>\).*/\1/
}' changelog
...
 * Fixed possible crash when deleting profiles.
  * Fixed encoding when invitation contains channel password with spaces.

[COLOR=#ff0000] --  <>
Thu, 04 Apr 2013[/COLOR]

ts3-client (3.0.10) ; urgency=low

  * Added Opus voice and music codecs. Requires server 3.0.7 or later.

 * Fixed possible crash when deleting profiles.
  * Fixed encoding when invitation contains channel password with spaces.

[COLOR=#ff0000] --  <>
Mon, 16 Jul 2012[/COLOR]

ts3-client (3.0.10) ; urgency=low

  * Added Opus voice and music codecs. Requires server 3.0.7 or later.
...


```

Maybe there's a clever way with pattern-hold space swaps?

---

### Post by schragge on 2013-04-17
Since the line being read with **R** is queued to be inserted at the end of the cycle, I'm afraid the only thing you could do here is deleting previous content:
```
sed $'/--  <>/{Rdates\nd}' changelog
```
This would be enough if you're controlling format of the *dates* file. Otherwise, pipe it into another sed:
```
sed '/--  <>/Rdates' changelog | sed '/--  <>/{N;s/\(<> \).*\n/\1/}'
```
But obviously, the same could be more elegantly done  with *getline* in awk:
```
awk '/--  <>/{getline<"dates";sub(/^/," --  <> ")};1' changelog
```
If you want to preserve maintainer's name and email address in the changelog, you may do it like this:
```
awk -F\> -vOFS='> ' /^ *--/{getline $2<"dates"};1' changelog
```

---

### Post by Vaphell on 2013-04-17
I had similar awk solution but i read dates into array in BEGIN block and then in case of pattern i used gsub with array[i++]. With OP's pattern copy-pasted verbatim it got rather huge though.

```
awk 'BEGIN { i=0; while(( getline line < "dates.txt" )>0) date[size++]=line; }
     /Tue, 16 Apr 2013 18:[0-3][0-9]:[0-9][0-9] -0500/ { gsub( /Tue, 16 Apr 2013 18:[0-3][0-9]:[0-9][0-9] -0500/, date[i++] ); }
           { print }' file
```

---

### Post by wolfgentleman on 2013-04-17
> **Vaphell said:**
> you don't even have to capture for-loop output (or any loop for that matter), you can redirect everything that gets produced inside it to file
*for ....; do .....; done > output.file*
i see you want to modify input, you need intermediary, eg tmpfile renamed later, because reading and writing at the same time produces garbage


about the substitution part: do you want to substitute first date in place of first match, 2nd in place of 2nd, 3rd for 3rd, etc? Or all occurences of the pattern with the first date, then copy of the same but with another date, ...? Because if i read the code correctly option #2 is what happens.

try something like this
```
$ cat sedtest.txt
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
[B]$ pattern='( --  <>  )Tue, 16 Apr 2013 18:[0-3][0-9]:[0-9][0-9] -0500'
$ while read d; do sed -r -i "0,/$pattern/ s/$pattern/\1$d/" sedtest.txt; done < dates.txt [/B]
$ cat sedtest.txt
 --  <>  Thu, 04 Apr 2013
 --  <>  Mon, 16 Jul 2012
 --  <>  Wed, 15 Feb 2012
 --  <>  Wed, 16 Nov 2011
 --  <>  Fri, 12 Aug 2011
 --  <>  Tue, 16 Apr 2013 18:34:22 -0500
```
Replace first match with first date, second match with second date, third match with third date, and so on. And the code you provided did absolutely nothing. It didn't print anything, it didn't overwrite anything in the file, nothing.
> **Vaphell said:**
> I had similar awk solution but i read dates into array in BEGIN block and then in case of pattern i used gsub with array[i++]. With OP's pattern copy-pasted verbatim it got rather huge though.

```
awk 'BEGIN { i=0; while(( getline line < "dates.txt" )>0) date[size++]=line; }
     /Tue, 16 Apr 2013 18:[0-3][0-9]:[0-9][0-9] -0500/ { gsub( /Tue, 16 Apr 2013 18:[0-3][0-9]:[0-9][0-9] -0500/, date[i++] ); }
           { print }' file
```
All that did was remove the dates from the change log.

---

### Post by schragge on 2013-04-17
> **wolfgentleman said:**
> And the code you provided did absolutely nothing. It didn't print anything, it didn't overwrite anything in the file, nothing.The code **Vaphell** suggested is absolutely OK. It doing nothing only means that the pattern could not match any string in the file. Check the pattern. Probably it should not be so specific. Perhaps
```
pattern='^( *-- *<> *)Tue, 16 Apr 2013 18:[0-3][0-9]:[0-9]{2} -0500'
``` would do the trick?

As for the awk example it would work if you changed *dates.txt* to *dates*.

---

### Post by wolfgentleman on 2013-04-17
> **schragge said:**
> The code **Vaphell** suggested is absolutely OK. It doing nothing only means that the pattern could not match any string in the file. Check the pattern. Probably it should not be so specific. Perhaps
```
pattern='^( *-- *<> *)Tue, 16 Apr 2013 18:[0-3][0-9]:[0-9]{2} -0500'
``` would do the trick?

As for the awk example it would work if you changed *dates.txt* to *dates*.

I did change dates.txt to dates.

I solved my own problem:

```
$ pattern="Tue, 16 Apr 2013 18:[0-3][0-9]:[0-5][0-9] -0500"
$ num=$(wc -l <dates)
$ for((i=1;i<=${num};i+=1)); do date=$(sed -n "${i}p" <dates); t=$(sed "0,/${pattern}/s/${pattern}/${date}/" <changelog); echo "$t" > changelog; done
```

Thanks for the input. :P

---

