---
title: "Intelligent script to divide up documents by chapters, like The Odyssey?"
date: 2010-06-14
forum: Programming Talk
---

### Post by tarahmarie on 2010-06-14
Hi, all:

I've been increasing my bash-fu, and I've got several scripts operational that do things like email me parts of a book each day (I'm working on the Iliad right now) that I wouldn't sit down to read, but will read if I get 100 lines in an email every day.  PS: it's working very well.

Here's an interesting question. 

[http://www.gutenberg.org/files/28621/28621.txt](http://www.gutenberg.org/files/28621/28621.txt)

There is a link to Ovid's 'Metamorphoses'.  So, as I'm reading 100 lines of Homer each day, sometimes it cuts off in the middle of a sentence or quotation (quite irritating when Achilles is being all badass and I want to know what happens next).

I need to figure out a smarter way to divide up these works.  

cat iliad.txt | split iliad.txt --lines=100 

That's the bash command I used to split up the text of the Iliad that I got from Gutenberg.org.  You can see that if I use the same command once I download Metamorphoses, that the same sort of thing will happen.  I want to do something like this: 

Start with the text file
   For the first paragraph
     is it longer than 100 lines?
        if not, add another paragraph
        if so, stop, make the new text file.
     Start a new text file, add a paragraph....

You get the idea.  This way, I'll get at least 100 lines, and full paragraphs in each text file.

I have no idea where to start.  Any suggestions? I'll start building a script based on your suggestions, and I'll keep posting it up until it works properly.

---

### Post by Some Penguin on 2010-06-14
Wouldn't be too ugly in, say, Perl.

```

use Symbol;

my $fh_in = gensym();
open($fh_in, "input_file.txt") || die "Failed to open 'input_file.txt' because:  $!";

my @buffer = ();
my $line     = undef;

while (defined($line = <$fh_in>)) {
  if ($line =~ /\S/) {
       # has at least one non-space character
       push @buffer, $line;
  } elsif (scalar(@buffer) >= 100) {
     # write buffer to somewhere, then empty it
     ...
     @buffer = ();
  }
}

# don't forget to write buffer somewhere if non-empty

close($fh_in) || die "In practice, closing a read-only handle doesn't fail, but apparently pigs fly... $!";

```

---

### Post by tarahmarie on 2010-06-14
I'm hearing you about the perl, but I'm trying to learn bash right now. I know perl is badass, but I need to add new languages to my head one at a time ;-)

I'm thinking that I could use bash to cycle through the lines with sed, and determine whether there were any characters on the line.  Is that a possibility?

---

### Post by tarahmarie on 2010-06-14
#!/bin/bash
for all the lines in book.txt
     while there aren't 100 lines
	  add lines.
     if the next line is empty, create book1.txt and go to the next book2.txt file.
     if the next line is NOT empty
     keep adding lines until there's an empty line. Then, break the file and go to the next one.

That's sorta what I envision this script looking like.

---

### Post by soltanis on 2010-06-15
I don't think bash is an ideal language to do this in, really. Perl, Python, awk would be great.

If you want to be real lightweight than go with awk. It's quite a small language and its designed to be used on the command line and plus I think its facilities are very well suited to this task. It's really just a matter of something like this:

```

#!/bin/sh

cat book.txt | awk 'BEGIN{lines=0;postfix=0} {lines++; if (lines > 100 && length($0) == 0) { close("book" postfix ".txt"); postfix++; lines=0 } else { print >> "book" postfix ".txt" }}'

```

Such a beautiful language, really. Note that I haven't really tested that code, but what it should do is print out lines from the text file until it is over 100 lines long. Once it reaches that length, it tests until the line is blank (some kind of boundary) and then it will close the current file and start appending to a new one (note the way that awk pipes output to files -- it's a lot like how sh does it, but in my opinion a lot more straightforward and elegant. When you're done with a file, you simply call close on it, and you move on. No filehandles or complicated trickery).

---

### Post by tarahmarie on 2010-08-10
> **soltanis said:**
> I don't think bash is an ideal language to do this in, really. Perl, Python, awk would be great.

If you want to be real lightweight than go with awk. It's quite a small language and its designed to be used on the command line and plus I think its facilities are very well suited to this task. It's really just a matter of something like this:

```

#!/bin/sh

cat book.txt | awk 'BEGIN{lines=0;postfix=0} {lines++; if (lines > 100 && length($0) == 0) { close("book" postfix ".txt"); postfix++; lines=0 } else { print >> "book" postfix ".txt" }}'

```

Such a beautiful language, really. Note that I haven't really tested that code, but what it should do is print out lines from the text file until it is over 100 lines long. Once it reaches that length, it tests until the line is blank (some kind of boundary) and then it will close the current file and start appending to a new one (note the way that awk pipes output to files -- it's a lot like how sh does it, but in my opinion a lot more straightforward and elegant. When you're done with a file, you simply call close on it, and you move on. No filehandles or complicated trickery).

It looks good, but when I test it, I end up with book0.txt--a file that is identical to the first.

I would really, REALLY like to figure out a way to do this in bash.  What tests for a blank line of a text file in bash? I can't figure that one out.

---

### Post by DaithiF on 2010-08-10
Hi, well this won't win any prizes for efficiency, but:
```
#!/bin/bash
bookcounter=0
linecounter=0
while read line
do
    ((linecounter+=1))
    if [[ $linecounter -gt 100 && -z "$line" || -z "$output_file" ]]; then
        linecounter=0
        ((bookcounter+=1))
        formatted_bookcounter=$(printf "%03d" $bookcounter)
        output_file=iliad${formatted_bookcounter}.txt
        echo "...starting segment $output_file"
        echo "Iliad - segment $formatted_bookcounter" > $output_file
        echo "===================" >> $output_file
        echo "" >> $output_file
    fi
    echo "$line" >> $output_file
done < iliad

```

( -z "$line" will test for a blank line or one with only whitespace )

---

### Post by tarahmarie on 2010-08-10
> **DaithiF said:**
> Hi, well this won't win any prizes for efficiency, but:
```
#!/bin/bash
bookcounter=0
linecounter=0
while read line
do
    ((linecounter+=1))
    if [[ $linecounter -gt 100 && -z "$line" || -z "$output_file" ]]; then
        linecounter=0
        ((bookcounter+=1))
        formatted_bookcounter=$(printf "%03d" $bookcounter)
        output_file=iliad${formatted_bookcounter}.txt
        echo "...starting segment $output_file"
        echo "Iliad - segment $formatted_bookcounter" > $output_file
        echo "===================" >> $output_file
        echo "" >> $output_file
    fi
    echo "$line" >> $output_file
done < iliad

```

( -z "$line" will test for a blank line or one with only whitespace )

Ok, here's what I tried:

```

#!/bin/bash
bookcounter=0
linecounter=0
while read line
do
    ((linecounter+=1))
    if [[ $linecounter -gt 100 && -z "$line" || -z "$output_file" ]]; then
        linecounter=0
        ((bookcounter+=1))
        formatted_bookcounter=$(printf "%03d" $bookcounter)
        output_file=metamorphoses${formatted_bookcounter}.txt
        echo "...starting segment $output_file"
        echo "Metamorphoses - segment $formatted_bookcounter" > $output_file
        echo "===================" >> $output_file
        echo "" >> $output_file
    fi
    echo "$line" >> $output_file
done < metamorphoses.txt

```

And here's my output:

```

~/Documents/Projects/book divisions : Yes, Supreme Empress? $ ls
metamorphoses.txt
~/Documents/Projects/book divisions : Yes, Supreme Empress? $ smartBookDivider.sh
/home/tarahmarie/Documents/Scripts/smartBookDivider.sh: line 18: metamorphoses: No such file or directory
~/Documents/Projects/book divisions : Yes, Supreme Empress? $ smartBookDivider.sh
...starting segment metamorphoses001.txt


```

You can see I first tried your script with no extension on 'metamorphoses' at line 18, but got that error message. Then I added the extension, and got the '...starting segment' output, but nothing actually happened in the directory and I never hit the second verbose debug line.  

[http://www.gutenberg.org/files/21765/21765-8.txt](http://www.gutenberg.org/files/21765/21765-8.txt)

There's the text file I'm using. What am I doing wrong?

---

### Post by DaithiF on 2010-08-10
Hi,
that file has windows line endings, ie. pairs of carriage return / new-line characters.  unix/linux just uses new-line characters, and so as far as the script is concerned the carriage-returns means that no lines are truly empty  and so you just get one large output file.

convert the file to unix line-endings and all will be well:
```
sed -i 's/\r$//' metamorphoses.txt

```

---

### Post by tarahmarie on 2010-08-10
Ok, folks; here it is:

```

#!/bin/bash
bookcounter=0
linecounter=0
sed -i 's/\r$//' metamorphoses.txt
while read line
do
    ((linecounter+=1))
    if [[ $linecounter -gt 300 && -z "$line" || -z "$output_file" ]]; then
        linecounter=0
        ((bookcounter+=1))
        formatted_bookcounter=$(printf "%03d" $bookcounter)
        output_file=metamorphoses${formatted_bookcounter}.txt
        echo "...starting segment $output_file"
        echo "Metamorphoses - segment $formatted_bookcounter" > $output_file
        echo "===================" >> $output_file
        echo "" >> $output_file
    fi
    echo "$line" >> $output_file
done < metamorphoses.txt

```

If anyone wants to see how I'm using it, you can go look at my blog in about 6 hours.

[http://thecowgirlcoder.com/](http://thecowgirlcoder.com/)

---

### Post by soltanis on 2010-08-10
> **tarahmarie said:**
> It looks good, but when I test it, I end up with book0.txt--a file that is identical to the first.

Probably is the Windows line endings causing that. You can run the file through dos2unix first, or you could just set the record separator to "\r\n":

```

awk 'BEGIN{**RS="\r\n";**lines=0;postfix=0} {lines++; if (lines > 100 && length($0) == 0) { close("book" postfix ".txt"); postfix++; lines=0 } else { print >> "book" postfix ".txt" }}'

```

Or you can stick to your existing solution too.

---

