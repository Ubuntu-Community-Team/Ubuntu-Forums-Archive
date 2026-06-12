---
title: "Python regular expressions; en dashes between number ranges"
date: 2013-05-08
forum: Programming Talk
---

### Post by kumoshk on 2013-05-08
I'm writing a script that takes a text file (like a novel) as input and outputs it with HTML entity names instead of special characters (or other substitutes for them). This is to make a zipped HTML file to submit to Kindle Direct Publishing. (Yes, I don't want to use a Word document, contrary to what is popular.)

Anyway, I don't really know how to use regular expressions. It looks like a lot of reading through to pick stuff out and memorizing to me, until you get it down. So, I was wondering if someone who already knows could help me on my way by telling me how to do certain specific tasks, specifically in Python.

What I want to do is this:

Find all hyphens surrounded by numbers and substitute those hyphens (not the numbers, too) with en dashes (more specifically, with the HTML entity name: ```
&ndash;
```).

So, instead of having something like this: 1-10 (or more properly, 1–10), I'd have this: ```
1&ndash;10
```

Anyway, that's my question.


However, it would be extra-nice if I could distinguish ranges of numbers with things like phone numbers and other codes. I don't want en dashes in phone numbers. I think I'll have to settle on hyphens instead of figure dashes for the phone numbers, however, since I don't think KDP supports figure dashes, yet (it uses Latin-1). The way I was thinking to distinguish them was to rule out cases where there is more than one hyphen number combination in the same 'word'. By word, I mean a group of characters that doesn't involve punctuation (sans hyphens) and such.

Another (and far more important) extra nice thing you could tell me, if you like, is this: How to replace an arbitrary number of things in a string each with its specific thing.

I mean, instead of calling myString.replace("thing1","thing2") a whole bunch of times, I was wondering if there's a way to do it without taking so much processer power, and thus speed it up a lot. I mean, if I'm inputting a huge book, this is going to take a while with all those replacements. If there's a function that only cycles through the book once (or less than a lot of times) for all the replacing, that would be awesome.

As an alternative (if what I wanted isn't practical), I could program in Java, Lua or Vala/Genie to make it faster, perhaps. I haven't tested it to see if it actually would be, but from what I know about those languages, it should be.

---

### Post by alan9800 on 2013-05-08
have you already tried to use [re.sub](http://docs.python.org/release/2.7.3/library/re.html#re.sub)?

---

### Post by schragge on 2013-05-08
Python regular expressions support lookahead and lookbehind assertions, so something like ```
re.sub(r"(?<=\d)-(?=\d)", "&ndash;", text)
``` should be possible.

---

### Post by trent.josephsen on 2013-05-08
/([^-\d]\d+)-(\d+[^-\d])/ would match strings like 1-10 but not 1-101-1020. I think this would work:
```
re.sub(r'([^-\d]\d+)-(\d+[^-\d])', r'\1&ndash;\2', mystring)
```
It won't touch an occurrence of 1-10 at the very beginning or end of a string, but I have to go to work and I don't have time to fiddle with it right now. Maybe you can get it to work.

One typically does transformations like this one line or paragraph at a time to avoid the inefficiency you describe. If line-by-line is ok, something like this might work:
```
with open(filename) as myfile:
    for line in myfile:
        s = re.sub(r'([^-\d]\d+)-(\d+[^-\d])', r'\1&ndash;\2', line)
        # insert any other substitutions here
        print(s, file=your_output_file)
```

I wouldn't really even consider using Java for something like this; all the features exist, but string operations in Java are just downright clunky. For what you're currently doing, sed might be sufficient, but awk or perl would work just as well. Any of the three will beat Python in speed if that is an issue, but I doubt it will be -- you'll probably be more limited by your hard drive. Test it first.

---

### Post by schragge on 2013-05-08
> **trent.josephsen said:**
> It won't touch an occurrence of 1-10 at the very beginning or end of a string, but I have to go to work and I don't have time to fiddle with it right now. Maybe you can get it to work.Try this
```
re.sub(r'(^|[^-\d])(\d+)-(\d+)([^-\d]|$)', r'\1\2&ndash;\3\4', line)
```

---

### Post by kumoshk on 2013-05-08
You guys are awesome! schragge's code works perfectly. This will save me lots of time. It helps to give me a starting point on beginning to use regular expressions, too.

I tested my program for speed on an average-sized novel, and it was almost instantaneous, notwithstanding I had 127 or so replace statements in there, granted the vast majority of them probably didn't find anything to replace. I'm thinking this will be workable in Python unless it gets exponentially slower as files get larger beyond a certain point.

Here are some other issues I'm facing, if you desire to help further, but unless you have an ingenius solution, these don't seem to be questions for programming (let me know if I'm wrong):

* An expression that would allow me to distinguish left single quotes from apostrophes that begin a word. My current thought here is to convert all the single quotes and apostrophes first to left single quotes and then manually search and examine those that are directly before a word. I'm thinking if I made a huge list of all the possible contractions that begin a word with an apostrophe, that would take care of it. Any idea where I can get such a list? I could make it, myself&#8212;so, it's not the end of the world if you don't know of one. Or, if you have a better idea, that would be great. [EDIT: Or at least make it ask for user input, bringing up the word and asking if it's an apostrophe or not. That's less work than manually searching, anyhow (no need to open a text editor). I could make a 'yes to all' option per word.]
* Detecting poetry and things that should be in blockquotes. My current thought is to detect multiple lines of short text that aren't dialog. This wouldn't be exact, though. So, I would need to manually review matches. Different books likely do such things differently.
* Determining how to handle ellipses where there is a period by them. It's not obvious whether the period is before or after the ellipsis (and I'm not sure whether to put a space between them). Maybe I should just leave elipsis characters out unless the entire book has no periods by ellipses.

---

### Post by trent.josephsen on 2013-05-09
Vim has a nice interactive search-and-replace feature that you could use for the first problem. Open the file in Vim, then type
```
:%s/\([a-z]\)\@<!'/`/igc
```
:%s/pattern/repl/ is a shortcut for "replace pattern with repl on every line of the current file"
/i is for case-insensitive matching
/g is for global -- if the pattern matches multiple times on a line, it will replace all of them and not just the first one
/c is for confirm -- it will ask you for confirmation each time it wants to replace something
\([a-z]\)\@<! is a negative lookbehind assertion: it says to only match the rest of the pattern if the thing immediately before it is NOT a character a-z. Since we used the /i switch, it will match A-Z as well.
' is what you want to match and ` is what you want to replace it with.

So that will replace every ' that is not preceded by a letter with `, but ask you to hit "y" before doing so. If you hit "n" that replacement won't be done. Of course you could do this in Python as well, but that's just extra work.

Have you considered transforming your text into a light markup language like Markdown, and then using one of the many available HTML translation tools? It could save you a lot of work, since the necessary transformations are much simpler. Not to mention that Markdown is far easier to read and edit by hand than HTML. Just a thought.

---

### Post by kumoshk on 2013-05-24
Just so you all know, you've helped me to learn about regular expressions, and I know how to use them now. Thanks!

---

### Post by kumoshk on 2013-07-30
> **kumoshk said:**
> * An expression that would allow me to distinguish left single quotes from apostrophes that begin a word. My current thought here is to convert all the single quotes and apostrophes first to left single quotes and then manually search and examine those that are directly before a word. I'm thinking if I made a huge list of all the possible contractions that begin a word with an apostrophe, that would take care of it. Any idea where I can get such a list? I could make it, myself&#8212;so, it's not the end of the world if you don't know of one. Or, if you have a better idea, that would be great. [EDIT: Or at least make it ask for user input, bringing up the word and asking if it's an apostrophe or not. That's less work than manually searching, anyhow (no need to open a text editor). I could make a 'yes to all' option per word.]
* Detecting poetry and things that should be in blockquotes. My current thought is to detect multiple lines of short text that aren't dialog. This wouldn't be exact, though. So, I would need to manually review matches. Different books likely do such things differently.
* Determining how to handle ellipses where there is a period by them. It's not obvious whether the period is before or after the ellipsis (and I'm not sure whether to put a space between them). Maybe I should just leave elipsis characters out unless the entire book has no periods by ellipses.

Miraculously, I solved the poetry problem like this (works perfectly, except that I need to distinguish between poetry and letters now so as to leave the line breaks out on letters):

```

                '''
		&#1100;=<blockquote>
		&#1099;=</blockquote>
		&#1098;=<br />
		We're using special characters for now instead of HTML tags. Switch later.
		'''
		
		self.contents=re.sub(r'(   +.+)\n', r'\1&#1098;\n', self.contents);
		
		self.contents=re.sub(r'((   +.+\n)+)', r'&#1100;\1&#1099;', self.contents);
		self.contents=re.sub(r'\n&#1099;', r'&#1099;\n', self.contents);
		self.contents=re.sub(r'&#1100;(   +)', r'\1&#1100;', self.contents);
		
		self.contents=re.sub(r'&#1098;&#1099;', r'&#1099;', self.contents);
```


I took care of the ellipses by turning all combinations (2 and 4 or more dots) into ellipses (and just leaving the periods out). There's more to it than that, but that's all you need to know.

As far as distinguishing single quotes from apostrophes (in contractions) goes, I'm still working on that one. I don't think my initial proposal is quite what I'm looking for.

Let me know if you're interested in the finished product. I could post it up or something, as soon as I decide on a license for it.

---

### Post by StephenF on 2013-07-31
.

---

