---
title: "how to remove last character of a string"
date: 2008-03-05
forum: Programming Talk
---

### Post by finer recliner on 2008-03-05
I have a file of many words that looks something like this:
```

word1
word2
word3
etc

```

each word is a different length, and they all seem to have a trailing space (or some sort of non-printable character). Whats the easiest way to strip the last character (the space) from each line?

---

### Post by stylishpants on 2008-03-05
```
perl -ple 'chomp' /tmp/file
```

"chomp" only removes a single whitespace char if the string ends with one, so it's safer than 'chop', which always removes one char regardless of what it is.

---

### Post by mike_g on 2008-03-05
Depend what sort of language you are using. But if you want to modify the file itself you will need to write it out again (for simplicity sake).

In C you could do something like: Read in each character of the file, keeping track of the character before it. Basically you only write a character before once you have read the character infront of it first. If the front character is a newline and the back character is some form of whitespace then don't write it to the file, otherwise write it. 

It would be easier in a higher level languages like Java. Then you could just read lines in as strings, trim them, then write back to a file.

---

### Post by Can+~ on 2008-03-05
> **mike_g said:**
> In C you could do something like: Read in each character of the file, keeping track of the character before it. Basically you only write a character before once you have read the character infront of it first. If the front character is a newline and the back character is some form of whitespace then don't write it to the file, otherwise write it. 

In C you could, instead of looping for each character, using strlen (string.h) for each line and going backwards until you find the first non-space character and remove it.

I guess it would be even easier in python, as python comes with the OS and has all those fancy string functions.

---

### Post by imdano on 2008-03-05
Python's .strip() method or Java's .trim() method would probably be much easier to use than C.

---

### Post by Can+~ on 2008-03-05
> **imdano said:**
> Python's .strip() method or Java's .trim() method would probably be much easier to use than C.

Uhm, python .strip() removes whitespaces (or any character specified on the parameters), he wants to remove a certain character at the end.

---

### Post by imdano on 2008-03-05
It only removes leading or trailing whitespace (or leading/trailing characters of the person's choice).  You can use rstrip() to only remove trailing (or lstrip() for leading).  It seems like that would fit his needs here.

---

### Post by Can+~ on 2008-03-05
> **imdano said:**
> It only removes leading or trailing whitespace (or leading/trailing characters of the person's choice).  You can use rstrip() to only remove trailing (or lstrip() for leading).  It seems like that would fit his needs here.

Oh wait, I just re-read the initial post and yeah, I misunderstood. I thought he wanted to remove the "1, 2, 3" from the words. Duh.

Then it's a for line in file: line.rstrip() kind of thing.

---

### Post by slavik on 2008-03-05
> **stylishpants said:**
> ```
perl -ple 'chomp' /tmp/file
```

"chomp" only removes a single whitespace char if the string ends with one, so it's safer than 'chop', which always removes one char regardless of what it is.
the answer has been given. :)

---

### Post by finer recliner on 2008-03-05
> **stylishpants said:**
> ```
perl -ple 'chomp' /tmp/file
```

"chomp" only removes a single whitespace char if the string ends with one, so it's safer than 'chop', which always removes one char regardless of what it is.

i dont think the trailing character was a space (idk what it was), but using chop with your perl call did the trick.

thank you all for your suggestions!:guitar:

---

### Post by ghostdog74 on 2008-03-05
> **finer recliner said:**
> I have a file of many words that looks something like this:
```

word1
word2
word3
etc

```

each word is a different length, and they all seem to have a trailing space (or some sort of non-printable character). Whats the easiest way to strip the last character (the space) from each line?


```

awk '{sub(/ +$/,"",$0)}1' file > newfile

```

---

### Post by onbongos on 2008-04-03
you can strip any last character with just string[:-1]

---

### Post by TeckniX on 2008-04-16
could you provide an example of how you'd use
```

string[:-1]

```

I'm trying to remove the * from an executable filename when doing an ls -l

---

### Post by ghostdog74 on 2008-04-16
> **TeckniX said:**
> could you provide an example of how you'd use
```

string[:-1]

```

I'm trying to remove the * from an executable filename when doing an ls -l

how does your file name look like ?

---

### Post by stylishpants on 2008-04-16
> **TeckniX said:**
> could you provide an example of how you'd use
```

string[:-1]

```

I'm trying to remove the * from an executable filename when doing an ls -l

Maybe you don't need to remove the last char at all.
It's possible that you're getting the trailing *  on some files because your "ls" command has the "-F" option, which appends a filetype classifier character to the filename.

This may be the case even if you are not explicitly providing the "-F" yourself, often ls gets aliased to something that has some useful default options.

Try using "\ls -l" (ls with a leading backslash) to get an unaliased ls, and see if that solves your issue.

---

### Post by mssever on 2008-04-16
> **TeckniX said:**
> could you provide an example of how you'd use
```

string[:-1]

```I'm trying to remove the * from an executable filename when doing an ls -l

You shouldn't be parsing the output of ls in the first place. ls is designed for human readers; it's impossible to reliably parse its output regardless of which options you pass to it because you can't always tell where filename boundries are. Remember, a filename can contain ANY whitespace character, including \n. Instead, use your language's facility for handling filenames. E.g., ```
#Bash
for i in *; do
  # do stuff
done

#Ruby
Dir.open(some_dir) do |dir|
  dir.each do |file|
    next if file =~ /^[.]+$/
    # do stuff
  end
end
```

---

### Post by Wybiral on 2008-04-17
What language was this supposed to be in anyway?

---

### Post by Mickeysofine1972 on 2008-04-17
Indeed, tell us what language and we will be glad to help

MIke

---

### Post by ghostdog74 on 2008-04-17
he is doing a ls -l. I am certain that's not a shell command.

---

### Post by toxygen on 2008-05-14
sed -ie 's/.$//' filename

---

