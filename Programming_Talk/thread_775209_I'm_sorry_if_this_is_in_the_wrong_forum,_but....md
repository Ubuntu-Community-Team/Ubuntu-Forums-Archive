---
title: "I'm sorry if this is in the wrong forum, but..."
date: 2008-04-29
forum: Programming Talk
---

### Post by delsydebothom on 2008-04-29
...I couldn't figure out a better place to put it. I really have just a few questions:

Is there a program or plugin that will analyze a given document, identify the words in it, and then list them all of them according to how often they are used in the document? I am wanting to write a Latin grammar based around the Etymologiae of St. Isidore of Seville, and I want to arrange the vocabulary according to the most oft-used words in it.  

If there is no such program, what would I need to get and learn in order to write such a plugin for the OpenOffice.org Writer? Thanx!

---

### Post by tamoneya on 2008-04-29
i dont know of such a plugin but i think it would be REALLY easy to write a python script that works on txt files.  That would probably be quicker than a OO plugin.

---

### Post by delsydebothom on 2008-04-29
> **tamoneya said:**
> i dont know of such a plugin but i think it would be REALLY easy to write a python script that works on txt files.  That would probably be quicker than a OO plugin.

I've never programmed at all before. Where would you recommend I go to pick up the skills I would need to write such a script? Thanks again!

---

### Post by unutbu on 2008-04-29
```
#!/usr/bin/perl
use strict;
use warnings;

my $file=shift @ARGV;
open(FILE,"<",$file) || die;
my %dat;
while (my $line=<FILE>) {
    my @words=split(/\s+/,$line);
    foreach my $word (@words) {
	$dat{$word}++;
    }
}
close(FILE);

foreach my $word (sort {$dat{$b} <=> $dat{$a}} keys %dat) {
    print "$dat{$word}    $word\n";
}

```

---

### Post by cabalas on 2008-04-29
This should also work:

```
cat <file> | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn
```

This is run from the command line, as far as I know will only work with plain text files.  All you need to do is replace <file> with the name of the file you want the statistics for.

Oh for those that think this looks familiar, it's just a modified version of the command that was used for that recent History meme

- Mike

---

### Post by ghostdog74 on 2008-04-29
```

awk '{ 
    for (i=1;i<=NF;i++){
        words[$i]++}
    }
END {
    for(j in words) {
        print j" appears "words[j]" times"
    }
}' file

```

---

### Post by pmasiar on 2008-04-30
OP, I'll show you why normal people hate geeks, and why geeks consider programming in Python as not geeky enough - because even total beginner like you can understand that.

[php]
# version in Python

counts = {} # empty dictionary

for line in open('path/to/file'):
    for word in line.split(): # splits line at spaces
        # maybe delete characters like . , ; ! etc
        if word in counts:
            counts[word] += 1
        else:
            counts[word] = 1
        # whole if-else can be replaced by one line:     
        # counts.setdefault(word, 1) + 1 

# counts is ready to use
[/php]

OP: Now you see why you want to learn Python? :-)

---

### Post by WW on 2008-04-30
Just a few comments on the previous posts...

cabalas: Your example did not work for me.  By the way, you have a superfluous cat.  You could do this:
```

awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' <file> | sort -rn

```

ghostdog74: Yours doesn't sort the output, but the output format could easily be changed and piped to the **sort** command like cabalas did, e.g.
```

awk '{ 
    for (i=1;i<=NF;i++){
        words[$i]++}
    }
END {
    for(j in words) {
        print words[j] " " j
    }
}' <file> | sort -rn

```

pmasiar: As you know, that is not a complete program.  By the way, I'm not sure how you intended to use setdefault in your comment about replacing the  if-else; what worked for me was **counts[word] = counts.setdefault(word, 0) + 1**

None of the proposed solutions will deal with punctuation, capitalization, or plurals.  How the program *should* deal with these depends on what delsydebothom needs.

Consider this English text file:
> 
This is a test.  Is this file a sufficient test?
A word to the wise is sufficient.  How many words
are in this file?  A picture is worth a thousand
words.

Should the program report "test." and "test?" separately? What about "This" and "this"?  Or "word" and "words"?

---

### Post by Tuna-Fish on 2008-04-30
Just in case the op doesn't actually know how to use any of these:

The special characters #! at the beginning of a file mean that it can be made executable. For example, to use unutbu's perl version, open up a plain text editor, like gedit, mousepad or whatever. Then copy-paste the text exactly as it is to it, make sure there are no extraneous leading newlines, and save it to a file. Then make it executable, from command line it's `chmod a+x filename` , then run it with a text file by typing `./filename the_text_file_whose_results_you_want >  file_where_results_are_stored

---

### Post by ghostdog74 on 2008-04-30
@WW. yes i just reread OP's requirement. It seems sort is needed. However i would just use asort()/asorti() since gawk provides it. As for the Python solution, it can be used this way
```

counts = {} # empty dictionary
for line in open("file"):
    for word in line.split(): # splits line at spaces
        counts.setdefault(word, 1) 
        counts[word]+=1
print counts

```

---

### Post by WW on 2008-04-30
> **ghostdog74 said:**
> As for the Python solution, it can be used this way [...]
I see, thanks.  But I think you meant
```

        counts.setdefault(word, 0) 

```

---

### Post by nvteighen on 2008-04-30
> **WW said:**
> (...)
None of the proposed solutions will deal with punctuation, capitalization, or plurals.  How the program *should* deal with these depends on what delsydebothom needs.

Consider this English text file:

Should the program report "test." and "test?" separately? What about "This" and "this"?  Or "word" and "words"?

Little problem: Latin doesn't work like English. There are 6 cases (Nominative, Vocative, Acusative, Genitive, Dative, Ablative), 5 inflections, 3 genders...

So, the program should be able to know "homines" is plural for "homo", "consulum" is genitive plural for "consul" and not a neuter singular like "templum"...

And this doesn't get into verbs! A word like "amor", can be a noun ("love") or a verb ("I am (being) loved", passive for "amo").

(Sorry, I'm a Philology student and have to deal with Latin in an almost daily basis)

---

### Post by unutbu on 2008-04-30
Thank you WW and nvteighen for pointing out some interesting pitfalls.

This new version turns every character that is not a letter into a space. That should take care of punctuation. It also downcases every letter, so capitalization is also "handled". Plurals is too tricky for me to handle. (How can you teach a computer that the plural of goose is geese but the plural of moose is not meese?)

nvteighen's problem is also hard to fix for the same reason. The program would need to parse latin grammar. I don't know the state of the art in this domain. Perhaps it's worth someone's doctoral thesis.

Here is my feeble kluge: Let the user build a dictionary of all words he/she wants classified as one. (See %same, below. 
delsydebothom, hopefully it will be obvious to you how to edit the %same hash to fit your needs; if not post and we can explain.)

```
#!/usr/bin/perl
use strict;
use warnings;

my %same=(
    'words' => 'word',
    'homines' => 'homo',
    'consulum' => 'consul'
    );

my $file=shift @ARGV;
open(FILE,"<",$file) || die;
my %dat;
while (my $line=<FILE>) {
    $line=~s/^\IsL/ /g;
    $line=~tr/[A-Z]/[a-z]/;
    my @words=split(/\s+/,$line);
    foreach my $word (@words) {
	if ($word=~m/(\p{IsL}+)/) {
	    $word=$1;
	}
	$word=$same{$word} if (exists($same{$word}));
	$dat{$word}++;
    }
}
close(FILE);

foreach my $word (sort {$dat{$b} <=> $dat{$a}} keys %dat) {
    print "$dat{$word}    $word\n";
}

```

---

### Post by delsydebothom on 2008-04-30
> **pmasiar said:**
> OP, I'll show you why normal people hate geeks, and why geeks consider programming in Python as not geeky enough - because even total beginner like you can understand that.

[php]
# version in Python

counts = {} # empty dictionary

for line in open('path/to/file'):
    for word in line.split(): # splits line at spaces
        # maybe delete characters like . , ; ! etc
        if word in counts:
            counts[word] += 1
        else:
            counts[word] = 1
        # whole if-else can be replaced by one line:     
        # counts.setdefault(word, 1) + 1 

# counts is ready to use
[/php]

OP: Now you see why you want to learn Python? :-)

Thanks! I'm actually learning it right now, via an online tutorial. It actually isn't that much different than learning a natural language--in fact, its much easier. Pax!

---

### Post by delsydebothom on 2008-04-30
> **WW said:**
> Just a few comments on the previous posts...

cabalas: Your example did not work for me.  By the way, you have a superfluous cat.  You could do this:
```

awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' <file> | sort -rn

```

ghostdog74: Yours doesn't sort the output, but the output format could easily be changed and piped to the **sort** command like cabalas did, e.g.
```

awk '{ 
    for (i=1;i<=NF;i++){
        words[$i]++}
    }
END {
    for(j in words) {
        print words[j] " " j
    }
}' <file> | sort -rn

```

pmasiar: As you know, that is not a complete program.  By the way, I'm not sure how you intended to use setdefault in your comment about replacing the  if-else; what worked for me was **counts[word] = counts.setdefault(word, 0) + 1**

None of the proposed solutions will deal with punctuation, capitalization, or plurals.  How the program *should* deal with these depends on what delsydebothom needs.

Consider this English text file:

Should the program report "test." and "test?" separately? What about "This" and "this"?  Or "word" and "words"?

That's a problem I'll have to sort out manually, I think. Once I see the word, I'll be able to identify its case, number, gender, tense, declension, etcetera, and know what order I need arrange the grammar. It really is no good to learn just one form of a word in an inflected language like Latin, even though it would seem easier at first. 

I really just need a general idea, because I'm not going to follow the final result religiously; that would result in an incredibly inorganic grammar, and make it difficult for anyone trying to learn Latin with it. For me, the learning process is something like a snowball; once you get it rolling down a hill, it will gain speed and size all on its own. Likewise, once a person gets the initial "adrenalin rush" of reading meaningful sentences in another language, building vocabulary and grammatical knowledge will become second nature.

Of course, I've rambled a bit off topic. Everyone has been very helpful. Its taken some work for me to understand what all the code meant, but I did manage to get it to do what I wanted it to do. Thanks, all!

---

### Post by cabalas on 2008-05-01
> **WW said:**
> Just a few comments on the previous posts...

cabalas: Your example did not work for me.  By the way, you have a superfluous cat.  You could do this:
```

awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' <file> | sort -rn

```



Hmm odd it works perfectly for me, ran it over a copy of moby dick with no problems, anyone else tried it?.  Thanks for the improvement though, makes it look a hell of a lot nicer.

- Mike

---

### Post by nvteighen on 2008-05-01
Just a little thought:

At my university there are two doctor candidates that are doing some similar lexical research on Spanish. I now remember a little speech they held about their project some months ago where they told us that no matter how powerful software you have, you'll always have to check manually what the computer has done.

Natural languages seem not to like computers!

---

### Post by WW on 2008-05-01
> **cabalas said:**
> Hmm odd it works perfectly for me, ran it over a copy of moby dick with no problems, anyone else tried it?.  Thanks for the improvement though, makes it look a hell of a lot nicer.

- Mike
Here's a test file, and a sample run with your awk command:

**testfile.txt**
> 
This is a test.  Is this file a sufficient test?
A word to the wise is sufficient.  How many words
are in this file?  A picture is worth a thousand
words.

```

$ awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' testfile.txt | sort -rn
1 word
1 is
1 in
1 
$ 

```
**a[$2]++** only counts the occurrences of the second word in each line.  Check out ghostdog74's awk command, where a loop is used to count the occurrences of each word in each line.

---

