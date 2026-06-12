---
title: "Capturing Output"
date: 2009-02-26
forum: Programming Talk
---

### Post by mastermindg on 2009-02-26
I've create a shell script that runs a python script to analyze images. What I would like to be able to do is capture the output of the python script and depending upon what is says do something else.

```
$ python ./SnapMatcher.py --finddups caps 75
0.0% complete
2 images
1 max possible pairs
1 comparisons made using hash table
0 pairs found above threshold
0.0 efficiency
```

What I'm looking for here is **1 pairs found above threshold**.

How can I do this?

---

### Post by soltanis on 2009-02-26
> **mastermindg said:**
> What I'm looking for here is **1 pairs found above threshold**.

How can I do this?

Dunno about shell scripts; but Perl:

```

#!/usr/bin/perl

$output = `python ./SnapMatcher.py --finddups caps 75`
if($output =~ /^1\bpairs\bfound/) {
 #...do stuff
}

```

---

### Post by mastermindg on 2009-02-26
Thanks, I figured out that this script actually creates a results file is matches are found, so it makes this a lot easier.

---

### Post by mastermindg on 2009-02-26
I need a command that will search a single file for text and depending on what text it finds will execute a command, i.e.:

open results.caps
          if buy.jpg - touch /share/forex/caps/buy.txt
          if sell.jpg - touch /share/forex/caps/sell.txt

So, look in results.cap and if the string "buy.jpg" is found, it will execute touch /.....buy.txt and so forth.

---

### Post by mastermindg on 2009-02-26
Would this work:

```
$buy = grep buy results.caps
if $buy>0 touch /share/forex/caps/buy.txt
$sell = grep sell results.caps 
if $sell>0 touch /share/forex/caps/sell.txt
```

---

### Post by geirha on 2009-02-26
This should print Found, if a line starting (^) with '1 pairs found above threshold' is found in the python script's output, and print Not found otherwise.
```

if python ./SnapMatcher.py --finddups caps 75 | grep -q '^1 pairs found above threshold'; then
   echo "Found"
else
   echo "Not found"
fi

```

---

### Post by ghostdog74 on 2009-02-26
> **mastermindg said:**
> I've create a shell script that runs a python script to analyze images. What I would like to be able to do is capture the output of the python script and depending upon what is says do something else.

```
$ python ./SnapMatcher.py --finddups caps 75
0.0% complete
2 images
1 max possible pairs
1 comparisons made using hash table
0 pairs found above threshold
0.0 efficiency
```

What I'm looking for here is **1 pairs found above threshold**.

How can I do this?

if you are doing in Python, why should you need to use the shell to get you want? Unless the Python script is not done by you and you don't know Python enough. Otherwise, use Python to capture your output.
your python script SnapMatcher already displayed the results, most probably using the print statement to print to standard output. Therefore, go look in the source code and find where it prints the output, then from there, insert something like
```

....
if "1 pairs found above threshold" in output :
  # do something

```

---

