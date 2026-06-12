---
title: "Computers are slower than I thought."
date: 2010-11-13
forum: Programming Talk
---

### Post by bradley002 on 2010-11-13
I am searching 200 megabytes of plain text for 2,000 individual words. Whenever the program finds one it is supposed to list it and its context (using grep). It took about an hour for it to print the first one. I would guess there are a few hundred instances of the sought strings in the 200 megabytes.

So, using the program I have now, I guess the only option is to leave it running all day, every day for several weeks (with breaks). 

Here is the program:

while read word ; do
   match=$(grep " $word " -h -r -C 12 ./massive_text_directory)
   if [ "$match" ] ; then
      echo "SEARCH TERM: ${word}" >> instances.txt
      echo -e "$match\n" >> instances.txt
   fi
done < big_word_list.txt

Is there a faster way to do it?

---

### Post by Some Penguin on 2010-11-13
Wu-Manber
---------
[http://www.oneunified.net/blog/2008/03/23/](http://www.oneunified.net/blog/2008/03/23/)
[http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.108.7791&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.108.7791&rep=rep1&type=pdf)


Tries
-----
[http://en.wikipedia.org/wiki/Trie](http://en.wikipedia.org/wiki/Trie)

---

### Post by endotherm on 2010-11-13
no idea how you'd do it in bash, but I would multi-thread the file io, so that you can search several files at once. it is possible that grep is running several threads, but Ive never looked into it. file IO is about the slowest thing a PC can do so it will take some time to complete.

---

### Post by Some Penguin on 2010-11-13
Also:

[http://lucene.apache.org/java/docs/index.html](http://lucene.apache.org/java/docs/index.html)

---

### Post by Acer3810T on 2010-11-13
Read all files and generate an index (tree or hash based) of all words and their occurrences.

For each word, look it up in the index.

---

### Post by Zugzwang on 2010-11-13
Actually, if you only want to do this searching operation once, building an index might be overkill. Instead, try to build one big regular expression that matches against any line that contains one of the words in your list and use this expression in "grep" to search in one go for all of the words at the same time. This should give you roughly a factor 2000 improvement in I/O at the expense of some CPU time, which shouldn't be too much in this example.

Perhaps someone else can provide you with a hint on how to build this expression - I am not familiar enough with the posix syntax for them.

---

### Post by johnl on 2010-11-13
> **Zugzwang said:**
> Actually, if you only want to do this searching operation once, building an index might be overkill. Instead, try to build one big regular expression that matches against any line that contains one of the words in your list and use this expression in "grep" to search in one go for all of the words at the same time. This should give you roughly a factor 2000 improvement in I/O at the expense of some CPU time, which shouldn't be too much in this example.

Perhaps someone else can provide you with a hint on how to build this expression - I am not familiar enough with the posix syntax for them.

You can do this like so:

```

grep -E "(rose|cow|wolf)"  /usr/share/dict/words

```

will display all words containing rose, cow, or wolf.

---

### Post by StephenF on 2010-11-13
This sounds like a job for a database of which I am not overly familiar, but...

In little more than the time it takes to scan for one word in all the files you could have built an entire database that would allow near instantaneous lookup of the positions of every word within those files.

In a database program like sqlite consider creating three tables like this[LIST=1]
[*]Word: Unique_ID, Text (e.g. "blue"), Length (e.g. 4)
[*]File: Unique_ID, Pathname
[*]Position: Unique_ID, Word_ID, File_ID, Line_Number, Line_Offset, Word_Number, Word_Offset 
[/LIST]

Once you have verified you can do database lookups with a small manually created sample set you only need then create a small program to snip out the contextual metadata of each word as it is found within the file to automate the process of database creation.

If grep takes its time it's because it has to compare the byte sequence of the word you are matching for 200 million multiplied by the word length times in order to find a match whereas your data mining program can define a word as starting with a letter and containing only letters and the following characters [-'] and finishing at any other character or the end of the file and with words trailing ' characters to be stripped so schools' (possessive plural) becomes just schools. A newline character bumps the line counter (slight oversight of what to do with hyphenated words that span a line). Because this tool is specialised it can run faster than grep provided it is written in a fast language like C.

Having grep do the job results in the discarding tons of data on each pass. The approach above saves that data, handing it over to the right tool to deal with it.

The database query might look like this.
```

sqlite> SELECT * FROM Position WHERE Text = "blue";

```

If it's still a bit slow (it most certainly will be) there are database commands for creating an index within a database. Index on Text and Word_ID is my guess. This only has to be done once and the database will automatically use the index. The words in the database will be stored in found order which is not a good thing to be searching on, otherwise.

If anyone who knows more about databases than me can chime in I would appreciate it.

---

### Post by bouncingwilf on 2010-11-13
Drop an email to GCHQ in Cheltenham or Fort Meade in Maryland : they seem to be able to (allegedly) scan virtually all the world's email traffic in real time for specific words!


Bouncinwilf

---

### Post by Arndt on 2010-11-13
> **bradley002 said:**
> I am searching 200 megabytes of plain text for 2,000 individual words. Whenever the program finds one it is supposed to list it and its context (using grep). It took about an hour for it to print the first one. I would guess there are a few hundred instances of the sought strings in the 200 megabytes.

So, using the program I have now, I guess the only option is to leave it running all day, every day for several weeks (with breaks). 

Here is the program:

while read word ; do
   match=$(grep " $word " -h -r -C 12 ./massive_text_directory)
   if [ "$match" ] ; then
      echo "SEARCH TERM: ${word}" >> instances.txt
      echo -e "$match\n" >> instances.txt
   fi
done < big_word_list.txt

Is there a faster way to do it?

Maybe [http://webglimpse.net/](http://webglimpse.net/) can help you.

---

### Post by Some Penguin on 2010-11-13
The aforementioned example of Lucene falls within the inverted-index category.  Identify stopwords (to avoid bloating your index unnecessarily), choose your analyzer (note:  the Lucene standard analyzer, last I checked, is very picky -- e.g. 'café' does NOT match 'cafe'; it's not hard to add, but is something to be aware of), index your documents, and run queries against it.  It's fast and not too hard, and the Lucene index structures and components are neatly documented if you're curious about how it works.

Wu-Manber is possibly going to be faster than a regular expression matcher, because it's specialized for fast exact string matching while a regular expression engine needs to handle wildcards and the like -- and you're at the mercy of the RE's compilation engine's author.  In both cases, word boundaries, accent folding, and other fun issues may be problematic:  e.g. how to handle punctuation, for instance.  "don't" shouldn't be flagged as containing the word "don", "In-N-Out" arguably does not contain "out" (not as a separate word, anyway), and so forth.

---

### Post by StephenF on 2010-11-13
I'm interested enough to write some code so here is the prototype which may be converted to C later on if I get back to this.

This will build or extend an existing sqlite database using words grabbed from a file but currently does not support hyphenated or apostrophe containing words, nor has the database insertion code been written yet.

```

#! /usr/bin/env python

# worddb.py: mine words from a file and use them to build a database
# usage: worddb.py /path/to/database /path/to/filetoscan

import os
import sys


try:
    from pysqlite2 import dbapi2 as sqlite
except ImportError:
    print "Module PySqlite2 is required"


def prepare_database(dbname, pathname):

    db = sqlite.connect(dbname)
    c = db.cursor()

    try:
        c.execute("CREATE TABLE file (pathname varchar(32));")
        c.execute("CREATE TABLE word (text varchar(12), length integer);")
        c.execute("""CREATE TABLE position (
                word_id integer,
                file_id integer, 
                line_number integer,
                line_offset integer,
                word_number integer,
                word_offset integer);""")

        c.execute("CREATE INDEX file_index ON file (pathname);")
        c.execute("CREATE INDEX word_index ON word (text);")

    except sqlite.OperationalError:
        pass

    c.execute("SELECT file.OID FROM file WHERE pathname = ?;", (pathname,))
    try:
        file_id = c.next()[0]
    except StopIteration:
        c.execute("INSERT INTO file (pathname) VALUES (?);", (pathname,))
        db.commit()
        c.execute("SELECT file.OID FROM file WHERE pathname = ?;", (pathname,))
        file_id = c.next()[0]
    else:
        c.execute("DELETE FROM position WHERE file_id = ?;", (file_id,))
        db.commit()
        
    return db, c, file_id


def mine_that_file(file, db, c, file_id):

    collect = False
    word_number = 0
    letter_offset = 0
    line_offset = 0
       
    for n, line in enumerate(file):
        if n % 1000 == 0:
            print "\rline", n + 1, "of", file.name
        
        for letter in line:
            if letter.isalpha():
                if collect == False:
                    collect = True
                    word_bucket = [letter]
                else:
                    word_bucket.append(letter)
            elif collect == True:
                collect = False
                word_number += 1
                print "we got a word :%s:" % "".join(word_bucket)
                print n, letter_offset
            letter_offset += 1
        line_offset += len(line)   
        letter_offset = 0 
        word_number = 0


def main():
    try:
        if len(sys.argv) != 3:
            print "Usage: worddb.py /path/to/database /path/to/textfile\n"
            sys.exit(1)

        dbname, pathname = sys.argv[1:]
            
        db, c, file_id = prepare_database(dbname, pathname)

        rp = os.path.realpath(pathname)
        with open(rp, "rU") as file:
            mine_that_file(file, db, c, file_id)

    except KeyboardInterrupt:
        print "^C"

    finally:
        c.close()
        db.close()

if __name__ == "__main__":
    main()

```

---

### Post by worksofcraft on 2010-11-13
I think 2000 words to search for is pushing the limits of what you can expect from grep. Something like [awk]("http://en.wikipedia.org/wiki/AWK") or one of the more advanced derivatives might do better... Perl could be a really good choice, although my personal preference would be C++ using std::set.

---

### Post by bradley002 on 2010-11-13
Thanks everyone, a lot of tips to work with here. StephenF -- I really appreciate you writing all that code, but I don't think I will figure out how to use it. I am pretty much a programming noob. However, I had some C++ experience in college, so maybe I can do this with std::set.

---

### Post by SeijiSensei on 2010-11-13
One thing you could do to speed things up without any additional futzing is copy the source to /dev/shm, or create a separate ramdisk using [the method described here](http://www.linuxscrew.com/2010/03/24/fastest-way-to-create-ramdisk-in-ubuntulinux/).  Then whatever approach you use will be searching through the memory rather than the hard drive.

Because Linux caches the drives so aggressively I'm not sure this will make a big difference, but it's certainly worth a try.

If by "context" you mean the line surrounding the word, you could write the lines into an SQL database (I prefer PostgreSQL myself), then use [Sphinx]("http://sphinxsearch.com/") to index the text.  It's blazingly fast when searching for text strings.  I used it to develop a catalog search engine with > 40,000 items in the database, and it would generate results in a second or two.

---

