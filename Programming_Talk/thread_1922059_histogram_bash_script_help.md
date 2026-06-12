---
title: "histogram bash script help?"
date: 2012-02-08
forum: Programming Talk
---

### Post by conradin on 2012-02-08
Hi all I want to make a histogram bash script that tells me the number of occurrences of a word each individual words in a file but its not going well at this point. I thought I could use the commands sort, uniq, and wc to break the file up but it isnt happening. 
Is this a standard function? Does anyone have any ideas?

I want to read a file, ignore no words, and have a nice output that tells me the number of occurrences of each word in the file.

---

### Post by Bachstelze on 2012-02-08
```
cat test.txt | tr ' ' "\n" | sort | uniq -c | sort
```

seems to work. Of course that's assuming you don't have words split over two lines...

---

### Post by Khayyam on 2012-02-10
.. or similarly using awk

```
awk '{for (i=1;i<=NF;i++)print $i}' input.txt | sort | uniq -c | sort
```The problem is what the OP means by a "word" .. 

```
% cat input.txt
I want to read a file, ignore no words, and have a nice output that tells me the number of occurrences of each word in the file.
% awk '{for (i=1;i<=NF;i++)print $i}' input.txt | sort | uniq -c | grep file
   1 file,
   1 file.
```So, unless we are filtering out certain word endings/beginings, or chars, then this will not behave as expected.

best ..

---

### Post by Habitual on 2012-02-10
```

#!/bin/bash
# wf.sh: Crude word frequency analysis on a text file.
# This is a more efficient version of the "wf2.sh" script.


# Check for input file on command line.
ARGS=1
E_BADARGS=65
E_NOFILE=66

if [ $# -ne "$ARGS" ]  # Correct number of arguments passed to script?
then
      echo "Usage: `basename $0` filename"
        exit $E_BADARGS
    fi

    if [ ! -f "$1" ]       # Check if file exists.
    then
          echo "File \"$1\" does not exist."
            exit $E_NOFILE
    fi



    ########################################################
    # main ()
    sed -e 's/\.//g'  -e 's/\,//g' -e 's/ /\
        /g' "$1" | tr 'A-Z' 'a-z' | sort | uniq -c | sort -nr
    #                           =========================
    #                            Frequency of occurrence

    #  Filter out periods and commas, and
    #+ change space between words to linefeed,
    #+ then shift characters to lowercase, and
    #+ finally prefix occurrence count and sort numerically.

    #  Arun Giridhar suggests modifying the above to:
    #  . . . | sort | uniq -c | sort +1 [-f] | sort +0 -nr
    #  This adds a secondary sort key, so instances of
    #+ equal occurrence are sorted alphabetically.
    #  As he explains it:
    #  "This is effectively a radix sort, first on the
    #+ least significant column
    #+ (word or string, optionally case-insensitive)
    #+ and last on the most significant column (frequency)."
    #
    #  As Frank Wang explains, the above is equivalent to
    #+       . . . | sort | uniq -c | sort +0 -nr
    #+ and the following also works:
    #+       . . . | sort | uniq -c | sort -k1nr -k
    ########################################################

    exit 0

```

save as say ~./wf.sh and make +x with terminal >
```
chmod 700 ~/wf.sh
```

Usage:
~/.wf.sh /path/to/file

Example:
```
cat x
```
One
two
Two
three
Three
THREE

```
wf.sh x
```
3 three
2 two
1 one

---

### Post by Khayyam on 2012-02-11
Habitual ...

I would say "very crude", I was left with odd results like the following:

```
./wf.sh input.txt | grep the
  80         the
   8 the
```There is also empty entries, and odd tabulation which I imagine are are caused by not removing blank lines and what have you.

Words ending with "!", "?" are treated uniquely, as are numbers, quotes (double and single), and other stuff you'd typically find in a document.

Anyhow .. far from purrrfect .. but it should handle most documents relatively sanely ..
 
```
#!/bin/bash
# Word Frequency Generator

if [[ -z "$1" ]] ; then
    echo "You must provide a file as input!"
    echo "Usage: $(basename $0) filename"
    exit
fi

awk '{for (i=1;i<=NF;i++) print $i}' $1 | \
    tr 'A-Z' 'a-z' | \
    sed -E 's|\"||g; s|\.||g; s|\,||g; s|[\?$]*||g; s|[\!$]*||g; s|\:\|\;||g; s|[0-9]*||g; s|^'\''\|'\''$||g; s|\(\|\)||g; /^$/d; s|'\''([a-zA-Z]*)'\''|\1|g' | \
    sort | \
    uniq -c | \
    sort -n

exit
```An example (using the same input.txt from my post above) ..

```
% cat input.txt
I want to read a file, ignore no words, and have a nice output that tells me the number of occurrences of each word in the file.
% ./wordfreq.sh input.txt
   1 and
   1 each
   1 have
   1 i
   1 ignore
   1 in
   1 me
   1 nice
   1 no
   1 number
   1 occurrences
   1 output
   1 read
   1 tells
   1 that
   1 to
   1 want
   1 word
   1 words
   2 a
   2 file
   2 of
   2 the
```Comments/suggestions welcome.

best .. khay

ps: conradin, you seem to have a habit of asking a question and then leaving the  thead hanging. This is the case in at least two treads where I have responded to you ([here]("http://ubuntuforums.org/showthread.php?t=1918827") and [here]("http://ubuntuforums.org/showthread.php?t=1919786")). You have had three people respond to you in this thread and again, nothing. If this continues then I don't feel there will be any reason for me to make an effort. Honestly, thats poor form.

edit: made some changes, does anyone know how to update/delete an attatchment? (It's ok I figured it out, but now I broke the link, gahhh)

---

### Post by Khayyam on 2012-02-11
I'd ment to mention that the sed regex could be abbreviated to the following but I'd seperated out the substitutions so that they are easier to comprehend.

```
sed -E 's|\"\|\.\|\,\|\:\|\;\|^'\''\|'\''$\|\(\|\)\|[\?$]*\|[\!$]*\|[0-9]*||g; /^$/d; s|'\''([a-zA-Z]*)'\''|\1|g'
```I'm sure vaphell would make a better job of it .. I'm not much of a regexer.

best ..

---

### Post by Khayyam on 2012-02-11
Sorry .. I screwed up the attatchment .. copy paste from the codeblock

---

### Post by emiller12345 on 2012-02-11
similar ....
```
~$ cat x | tr '[:upper:]' '[:lower:]' | tr ' ' '\n' | tr -d '[:punct:]' | grep -v "^$" | sort | uniq -c | sort -r -n
```

---

### Post by Khayyam on 2012-02-12
emiller1234 ...

I'd though of using '[:punct:]' but with this some word will get transformed, "I'll" will become "ill", "I'm" will become "im" ,"t-shirt" will come "tshirt", "Bob's" will become "bobs", etc. I tryed to keep 'words' as close to standard usage as possible.

best ...

---

### Post by emiller12345 on 2012-02-13
> **Khayyam said:**
> emiller1234 ...

I'd though of using '[:punct:]' but with this some word will get transformed, "I'll" will become "ill", "I'm" will become "im" ,"t-shirt" will come "tshirt", "Bob's" will become "bobs", etc. I tryed to keep 'words' as close to standard usage as possible.

best ...
+1 good call. I didn't think of that.

---

