---
title: "Replacing \t\n with \n in a text file"
date: 2010-05-24
forum: Programming Talk
---

### Post by manzdagratiano on 2010-05-24
I am trying to replace all sequences '\t\n' in a huge text file with a simple '\n'. I can do this with the 'Replace' option in gedit, and while that works, gedit hangs for very large text files. Hence the command line. Now what I do is:

```
cat temp.txt | tr '\t\n' '\n' > tempprime.txt
```And this replaces ALL tabs with \n, instead of just replacing \t\n. The same results with:

```
cat temp.txt | tr "\t\n" "\n" > tempprime.txt
```where I have used double quotes implying a string.

However, when I simply try:

```
cat temp.txt | tr \t\n \n > tempprime.txt
```nothing happens whatsoever! I can check the differences between temp.txt and tempprime.txt using:

```
diff temp.txt tempprime.txt
```and there is no output.

What should the right command be pray anyone?

---

### Post by hawthornso23 on 2010-05-24
Use vi. In case you are not a vi user here are detailed instructions.

[LIST=1]
[*]Open the file with vim.
[*]Hit escape to make sure you are not in enter mode.
[*]Type ```
:1,$s/\\t\\n/\\n/g
``` then enter.
[*]Check file to see if it looks like what you want
[*]then ```
:wq
``` followed by enter to write your changes.
[/LIST]
vi rules at this sort of thing.  Best text editor ever.

---

### Post by lisati on 2010-05-24
If you want to try your hand at making a C program to do this, you might want to adapt one of my programs: see [here]("http://lisati.myftp.org/page16.html") and [here]("http://lisati.myftp.org/fixlf/")

---

### Post by manzdagratiano on 2010-05-24
Thank you for the replies!!! C++ would be quite efficient to do this - in fact I am going to be reading the output text file into a C++ program anyway, and vim would be a good idea too. The thing that bothers me is - why does 'tr' fail at doing this? Is there no fix for that?

---

### Post by soltanis on 2010-05-24
It fails at doing that because you are using the command incorrectly. For some reason the GNU people dislike manpages (and hence, theirs sucks) so I'll quote this manpage from Mac OS X:

```

 In the first synopsis form, the characters in string1 are translated into the characters in string2 where the first
     character in string1 is translated into the first character in string2 and so on.  If string1 is longer than
     string2, the last character found in string2 is duplicated until string1 is exhausted.

```

In other words, tr (or TRanslate) will perform per-character (as opposed to per-string) replacement.

You can use any number of tools to solve your problem, not just vim. For example, sed would be a common one, as would be awk:

```

awk 'BEGIN{ RS="\t\n" } { print $0 }' < input_f > output_f

```

The above code will replace all your "\t\n" with just a newline (working on the principle that awk separates records according to the record separator, RS, and by default, print writes strings with the output record separator, ORS, set to just a newline), from input_f to output_f.

Perl is the highest level language I would go; torturing yourself with C or C++ isn't really necessary unless you have very good reason.

---

### Post by manzdagratiano on 2010-05-24
> **soltanis said:**
> It fails at doing that because you are using the command incorrectly. For some reason the GNU people dislike manpages (and hence, theirs sucks) so I'll quote this manpage from Mac OS X:

```

 In the first synopsis form, the characters in string1 are translated into the characters in string2 where the first
     character in string1 is translated into the first character in string2 and so on.  If string1 is longer than
     string2, the last character found in string2 is duplicated until string1 is exhausted.

```In other words, tr (or TRanslate) will perform per-character (as opposed to per-string) replacement.

You can use any number of tools to solve your problem, not just vim. For example, sed would be a common one, as would be awk:

```

awk '{ sub(/\t\n/, "\n", $0); print $0 }' < input_f > output_f

```Perl is the highest-level language I would go to do this. Unless you have good reason, I would not torture yourself to implement this in C or C++.

Aha! That seems to explain the symptoms. Thanks!!!

---

### Post by lisati on 2010-05-24
> **soltanis said:**
>  Unless you have good reason, I would not torture yourself to implement this in C or C++.
Do I detect the possibility of a friendly challenge? :)

---

### Post by manzdagratiano on 2010-05-24
> **lisati said:**
> Do I detect the possibility of a friendly challenge? :)

Hehe... I imagine doing this is C++ is simple enough - I believe however that the torture part lies in writing down twenty lines of code instead of just one.

---

### Post by lisati on 2010-05-24
> **manzdagratiano said:**
> Hehe... I imagine doing this is C++ is simple enough - I believe however that the torture part lies in writing down twenty lines of code instead of just one.

True!

---

### Post by manzdagratiano on 2010-05-24
> **lisati said:**
> True!

On a side note, your ftp seems to be quite interesting! I guess I shall be referring to it when I host my own!

---

### Post by lisati on 2010-05-24
> **manzdagratiano said:**
> On a side note, your ftp seems to be quite interesting! I guess I shall be referring to it when I host my own!

The domain name I chose is a bit of a misnomer. I was originally thinking of using it for ftp, but ended up going in a different direction. I haven't gotten round to updating the links yet.....

---

