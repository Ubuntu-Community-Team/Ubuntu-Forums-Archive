---
title: "From command line detect all words in a file which start and end with the same letter"
date: 2010-02-02
forum: Programming Talk
---

### Post by DBQ on 2010-02-02
I am looking for a command (preferably bash) which can detect all words in a text file which start and end with the same letter.  Any ideas?  Seems this cannot be done with grep.

---

### Post by croto on 2010-02-02
I recently replied to a similar question on python:
[http://ubuntuforums.org/showthread.php?t=1393082]("http://ubuntuforums.org/showthread.php?t=1393082")
would it help?

---

### Post by Meghnaad on 2010-02-02
Hi I've written a Solution for this in bash
working on my ubuntu 9.10

Script:

```
#!/bin/bash
tr ' ' '\n' < caesar.txt | while read line
do
        first=$( echo "$line" | cut -c 1 )
        last=$( echo "$line" | cut -c ${#line} )
        if [ $first = $last  -a ${#line} -ne 1 ]
        then
                echo "$line"
        fi
done
```

I've Considered Following file as Input File 'caesar.txt'

```
Friends, Romans, lend me your ears;
I come to bury Ceasar, not to praise him.
The evil man do lives after them;
The good is oft intered with their bones;
So let it be with Caesar. The noble Brutus
Hath told you Caesar was ambitious;
If it were so, it was a grieveous fault,
And grievously hath Ceasar answered it.
Here, under the leave of Brutus and the rest-
For brutus is an honorable;
Beware of the Ides of March;
He was my freind, faithful and just to me;
Come I to speak in Caesar's funeral.
But Brutus says that he was ambitious;
And Brutus is an honorable man.
He hath brought many captives to Rome,
Whose ransoms did the genral coffer fills:
Did this in Ceasar seem ambitious ?
When that poor have cried, Caesar hath wept:
Ambitious should be made of sterner stuff:
Yet Brutus says he was ambitious;
ABCDEFGHIJKLMNOPQRSTUVXYZ
You all did see that on Luperval
I thrice presented a queenly crown,
Which he did thrice refused: was this ambition ?
Yet Brutus says he was ambitious;
And, sure, he is an honorable man.
I speak not to disprove what Brutus spoke,
But here I'm to speak what I do know.
You all did love him once, not without cause:
What cause withholds you then to mourn for him ?
O judgement! thou art fled to brutish beasts,
And men have lost their mourn reason. Bear with me;
My heart is in the cheap wooden box there with Caesar,
And I must pause till it come back to me.


					William Shakespeare.
```


and i get Following output:

```
vinsys@vinsys-server:~/Meghnaad$ bash test.sh
hath
says
that
hath
did
that
hath
says
did
that
did
says
did
```

I've not Considered words having only a single character here
If you want them as well just replace This:

```
if [ $first = $last  -a ${#line} -ne 1 ]
```

with this:

```
if [ $first = $last ]
```

Hope it's helpful
Let me know all the bugs you can find I'm sure I can fix them

---

### Post by geirha on 2010-02-02
Using bash only (requires at least bash 3.1. echo "$BASH_VERSION"):
```

#!/bin/bash
file=inputfile.txt
words=()    # array of resulting words

while read -r -a line; do               # for each line
    for word in "${line[@]}"; do        # for each word in line
        if (( ${#word} == 1 )); then    # if word har length 1, skip it
            continue
        fi
        if [[ "${word::1}" = "${word:(-1)}" ]]; then 
            words+=( "$word" )   # append word to array
        fi
    done
done < "$file"

echo "Words starting and ending with the same char: ${words[@]}"

```

---

### Post by Some Penguin on 2010-02-02
Incidentally, this is the sort of thing that slightly arcane Perl can be extremely efficient at.
```

#!/usr/bin/perl -w

use strict;

my $data = join("\n", <STDIN>);

while ($data =~ /\b(?<!')([a-z])(?:([a-z']*)\1)?\b(?!'[a-z])/gi) {
  print $&, "\n";
}

exit 0;

```This also catches 'Hath', 'Did', 'Luperval', 'I', 'a', et al.   It's a little fiddly regarding apostrophes -- actually building a sane "word" identifier takes more effort (distinguishing what punctuation belongs to a word and what isn't -- Samuels', Saint's, etc is somewhat nontrivial in the general case).

That single regex is /g (so it looks for every match when iterated), /i so it's case-insensitive.
\b is a word boundary.

The (?<!') oddity is a Perlism; it says "unless we just saw an apostrophe, in which case it's not a valid match".  \1 is a backreference to the first actual group (the [a-z]).  The 'perlre' manpage is helpful for crafting bizarre regexes like this.   (?!') is the same as (?<!') except forwards.



Added:  The closest I've gotten with a single egrep call is
 egrep -oi "\b([a-zA-Z])(([a-zA-Z']*)\1)?\b" 
which falls prey to "that's" and the like.

Added:  Improved the tail apostrophe checking.  Saints' is fine; we want to avoid That's.

---

