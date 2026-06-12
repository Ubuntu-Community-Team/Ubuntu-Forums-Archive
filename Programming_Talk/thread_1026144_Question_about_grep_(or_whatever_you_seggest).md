---
title: "Question about grep (or whatever you seggest)"
date: 2008-12-30
forum: Programming Talk
---

### Post by DBQ on 2008-12-30
Hi, I am trying to extract one thing from program output.  The program output has this format:

Minimum Memory usage:                 100 megs
Some other Memory usage:              200 megs
Maximum Memory usage:                 500 megs
Something Memory usage:               300 megs
Something else Memory usage:          300 megs

I want to extract ONLY the maximum memory usage NUMBER using grep. I tried this:  grep -o 'Usage[0-9]*'.  It gets me the number alright, BUT it gets ALL numbers.  How can I get just the memory usage number?

---

### Post by arvevans on 2008-12-30
*program_name | grep Maximum*
will get you the line with the word "Maximum" in it.

*program_name | grep Maximum | cut -d " " -f4-*
should get you the number of megs

Do a `man grep` to see how the grep program works
Do a `man cut` to see how the cut program works.

Hope this helps.

---

### Post by DBQ on 2008-12-31
I did more reading.  I think awk would be a more appropriate thing to use in this case.  My program outputs the things in this format:

run: blah1 blah2 blah3
Memory: min 100 used 150 max 200

I want to reformat the output to this:

run:  run: blah1 blah2 blah3 200

(where 200 is he max)

How do I get it all in the right order on one line?

---

### Post by arvevans on 2008-12-31
Doing that in "awk" might be awkward :P

Sorry about the pun...but I just couldn't resist the opportunity!
Dr's **A**ho, **W**einberger, & **K**ernigan would be proud of me!  :)

Purpose of the "cut" command is to extract either character position based data, or to define a delimiter and then extract data from a string based on position relative to a particular delimiter in the string.  If you set the delimiter to be a blank_space (cut -d " ") then set the field to be the nth field which would contain your data (cut -d " " -f4) would extract just the numerical data from the 4th field.

You can test this one line at a time:

    echo "Maximum Memory usage: 500 megs" | cut -d " " -f4

should just spit out the number "500" because you would be looking at the 4th blankspace defined field in the string.

---

### Post by DBQ on 2008-12-31
Cool puns there ;). What if I want to manipulate input which comes from multiple lines? For example, lets say the program outputs:

a
b
c
d

and I want to capture all of it and then print c b a d? I do not think that this is possible with a cut...unless I am mistking.

---

### Post by ghostdog74 on 2009-01-01
> **arvevans said:**
> Doing that in "awk" might be awkward :P

provide an example of how its awkward using awk as compared to whatever you are using. If you use awk, you don't even have to use cut,sed,grep,wc and such. 

@OP,
```

# more file
run: blah1 blah2 blah3
Memory: min 100 used 150 max 200

# awk '/^run/{line=$0}/^Memory/ && /max/{print line" "$NF}' file
run: blah1 blah2 blah3 200


```

---

### Post by DBQ on 2009-01-01
Thank you very much ghostdog.  Could you please kindly explain how this works?  - I would like to understand.

---

### Post by pmasiar on 2009-01-01
> **DBQ said:**
> Thank you very much ghostdog.  Could you please kindly explain how this works?  - I would like to understand.

If you want to **understand** what you do, consider doing it in Python:

[php]
for line in open('path/to/file'):
    if 'Memory' in line:
        # do whatever you need with the line
        print line,
[/php]

awk is dark magic, it was not designed for readability or easy understanding. Some people (like ghostdog) masterd it years ago, but today, it makes little sense to invest time to master it for occasional user like you.

---

### Post by ghostdog74 on 2009-01-01
> **DBQ said:**
> Thank you very much ghostdog.  Could you please kindly explain how this works?  - I would like to understand.

i will break it down for you 
```

awk '/^run/{line=$0}
     /^Memory/ && /max/{print line" "$NF}
' file

```

/^run/ : simple regular expression that says, search for line starting with word run, then save the line, also called a row, or a record,  as variable "line". 

/^Memory/ && /max/ : this simple just say find the line/record that starts with "Memory" and also contains the word "max". Once found, {print line" "$NF} means print the line saved into variable "line" together with the value of the last field, ie 200.

Don't take it seriously that awk is not designed to be "readable" or "understandable". With practice using awk and writing code in a standard proper way, its just as easy and "readable". Also, take it with a pinch of salt what others say about "not worthwhile to invest your time with it".  

If you want to learn more about awk, check my sig.

---

### Post by pmasiar on 2009-01-01
> **ghostdog74 said:**
> 
Don't take it seriously that awk is not designed to be "readable" or "understandable".


... but yes, do think for yourself, and use a pinch of salt when reading opinions. Compare

```

awk '/^run/{line=$0}
     /^Memory/ && /max/{print line" "$NF}
' file

```

[php]
for line in open('path/to/file'):
   if line.startswith('run:'):
       runline = line[4:-2] # rest of line after 'run', without newline
       continue
   if line.startswith('Memory') and 'max' in line:
       parts = line.split(' ') # split line on spaces
       maxmem = parts[-1] # last item
       print runline, maxmem
[/php]

Which code is more readable and requires less  explanation? Which solution will allow you to write similar code later? Which fits your brain better, so you can recall it half-year later without re-reading the docs?

---

### Post by ghostdog74 on 2009-01-01
> **pmasiar said:**
> 
Which code is more readable and requires less  explanation? 

Subjective.

> 
Which solution will allow you to write similar code later?

In what area does the awk solution don't allow for similar code later, give examples will you.? The Awk solution makes use of pattern matching using regexp and its is so widely used, even a programming idiot will be able to write at least simple regexp after some practice understanding its syntax.

> 
 Which fits your brain better, so you can recall it half-year later without re-reading the docs?
let me see, hmmm, Perl? Believe me, its been so many years but i still remember how to write Perl. Re-reading the docs? Who never did that while programming? I will call him a programming god. As for fitting the brain, the awk solution looks shorter than both the Python ones , and that's just enough to fit some people.
Man, seriously, are we going to start this again.?

---

### Post by pmasiar on 2009-01-01
> **ghostdog74 said:**
> Man, seriously, are we going to start this again.?

No, I am done now :-)

I'll let any ocasional reader to form her own opinion. Luckily, now she has **two** opinions, both substantiated by arguments, to choose from, not only one.

---

### Post by DBQ on 2009-01-03
Hi guys.  Thanks to both of you for all your help.  I think both of you have a good points.  I know Python, used it, and liked it.  However, I recently started learning awk and it seems like very powerful and useful tool to assist me in my everyday work.  I think it is very readable too if well written.  I am embarking on the journey of learning tools useful for parsing, and I am glad that I have such experts as the two of you to assist me ;).

---

