---
title: "python script request - reading from *.csv, writing to files"
date: 2012-09-04
forum: Programming Talk
---

### Post by wheel_walker on 2012-09-04
I have spreadsheets for modifying data structures in old video games, which, when edited, concatenate all the edited data together into another worksheet, which is then saved as a *.csv (comma separated value).

I need a cross-platform script that will grab the data from the *.csv, and write it to the appropriate files, provided those files are in the same directory as the python script and the *.csv.

The .csv files look like this:
```
(filename),(address, in hexadecimal),(bytes to write, in hexadecimal)
SCUS_942.30,9EE0,300001C08000140000000000FFFFFFFF6581FFFFFFFFFFFFFFFFFFFF
SCUS_942.30,9EFC,300001C08000280000000000FFFFFFFF6581FFFFFFFFFFFFFFFFFFFF
SCUS_942.30,9F18,300001C08000640000000000FFFFFFFF6581FFFFFFFFFFFFFFFFFFFF
SCUS_942.30,9F34,300001C08000140000000000FFFFFFFFF481FFFFFFFFFFFFFFFFFFFF
SCUS_942.30,9F50,300001C08000000000000000FFFFFFFF6981FFFFFFFFFFFFFFFFFFFF
SCUS_942.30,9F6C,300001C08000010000000000FFFFFFFF6881FFFFFFFFFFFFFFFFFFFF
```As there will probably be multiple *.csv files for editing different data structures in these games, I need the python script to be able to select the *.csv to use, when using the python script in terminal.
```
python csv_writer.py saga_item_data.csv
```I don't need to select the file(s) to write it to, as they are part of the *.csv; and because some of my spreadsheets work with hundreds of files, and selecting the file to which to write would only hinder me.

The *.csv files are simply plain text.
- Probably UTF-8 on Linux, (using Gnumeric or Calc) and ISO-8859-1* on Windows(using Excel).
- It's probably okay to use Windows CR+LF (which is the Windows line-break character), but don't quote me on that.

I'm not a programmer; just a data diver who knows how to search for things using a hex editor.

---

### Post by schauerlich on 2012-09-05
Generally we don't take program requests here, but help people who are trying to write their own. So, today you're going to learn some python.

Reading in CSVs:
[http://docs.python.org/library/csv.html](http://docs.python.org/library/csv.html)

Converting hex to int:
[http://docs.python.org/library/functions.html#int](http://docs.python.org/library/functions.html#int) (base=16)

Jumping to a position in a file:
[http://docs.python.org/library/stdtypes.html#file-objects](http://docs.python.org/library/stdtypes.html#file-objects) (you want "seek" to find byte x of the file)

Converting that hex ascii string to a byte string:
[http://code.activestate.com/recipes/510399-byte-to-hex-and-hex-to-byte-string-conversion/](http://code.activestate.com/recipes/510399-byte-to-hex-and-hex-to-byte-string-conversion/)

Then write out the byte string to the file.

---

### Post by schauerlich on 2012-09-05
Lucky for you I was sufficiently bored.

```
$ cat blah.csv
bar.bin,0F,313233
$ cat bar.bin
abcdefghijklmnopqrstuvwxyz
$ python foo.py blah.csv 
$ cat bar.bin
abcdefghijklmno123stuvwxyz
$ cat foo.py
import csv
import sys

def hex_to_bytes(s):
    return "".join(chr(int(s[i:i+2], 16)) for i in range(0, len(s), 2))

if __name__ == "__main__":
    csv_file = sys.argv[1]

    with open(csv_file, "r") as inf:
        reader = csv.reader(inf)

        for filename, addr, data in reader:
            addr = int(addr, 16)
            data = hex_to_bytes(data)

            with open(filename, "r+b") as outf:
                outf.seek(addr)
                outf.write(data)
```

extending that to multiple CSVs is left as an exercise to the reader. (hint: it's as simple as deleting one line and adding another)

---

### Post by wheel_walker on 2012-09-05
> **schauerlich said:**
> Lucky for you I was sufficiently bored.

```
$ cat blah.csv
bar.bin,0F,313233

$ cat bar.bin
abcdefghijklmnopqrstuvwxyz

$ python foo.py blah.csv 

$ cat bar.bin
abcdefghijklmno123stuvwxyz

$ cat foo.py
import csv
import sys

def hex_to_bytes(s):
    return "".join(chr(int(s[i:i+2], 16)) for i in range(0, len(s), 2))

if __name__ == "__main__":
    csv_file = sys.argv[1]

    with open(csv_file, "r") as inf:
        reader = csv.reader(inf)

        for filename, addr, data in reader:
            addr = int(addr, 16)
            data = hex_to_bytes(data)

            with open(filename, "r+b") as outf:
                outf.seek(addr)
                outf.write(data)
```Extending that to multiple CSVs is left as an exercise to the reader. (hint: it's as simple as deleting one line and adding another)
I don't need it to work on multiple CSVs (with or without wildcards), or to work on all CSVs with a directory.  Doing so may create problems, if some CSVs share the same data, or if someone forgets to remove an out-dated CSV.

Thank you.  Would you mind if I credited you?  Do you have any website you'd like me to link to, if someone wants to post a thank-you message, or anything you want advertised?

EDIT

My spreadsheets originally were going to use hex editors, but I couldn't find a hex editor that worked correctly - they would insert data instead of just overwriting data (which was what I needed, overwriting).  I mentioned this to the author of one such hex editor, and I think he's working on the issue.

EDIT
And what version of python is this for?

---

### Post by trent.josephsen on 2012-09-05
I'm a little puzzled by why you'd use spreadsheets to begin with. Is using a hex editor to edit the binary directly not an option? Just wondering.

---

### Post by wheel_walker on 2012-09-06
> **trent.josephsen said:**
> I'm a little puzzled by why you'd use spreadsheets to begin with. Is using a hex editor to edit the binary directly not an option? Just wondering.
Editing with just a hex editor is perfectly fine, but it gets tedious when you're editing a table with 256 entries, and 27 bytes per entry.  Or when you're adjusting a set of pointer tables, and correcting the entries they point to.

My goal is to make modding these games accessible to everyone, and spreadsheets do a pretty good job of that, especially when combined with the python script here.

---

### Post by trent.josephsen on 2012-09-06
Ah, I see.

In that case, not to tell you your business, but I would add a field to the spreadsheet for annotations describing each segment -- that would do wonders for accessibility.

---

### Post by wheel_walker on 2012-09-06
> **trent.josephsen said:**
> Ah, I see.

In that case, not to tell you your business,...
Feel free to tell me anything.  I like opportunities to learn new things which are easily applied.

> **trent.josephsen said:**
> ... but I would add a field to the spreadsheet for annotations describing each segment -- that would do wonders for accessibility.
Are you talking about detailed descriptions for each offset, and suchlike?  Here's a good example of what I do:
[http://biolab.warsworldnews.com/viewtopic.php?f=5&t=13](http://biolab.warsworldnews.com/viewtopic.php?f=5&t=13)

If you're talking about something else entirely, then please tell me more about it.

---

### Post by trent.josephsen on 2012-09-06
I was referring to keeping the annotations in-line with the content. I used a hex editor once a long time ago (last century) that basically read in and interpreted the file for you (using plugins for different kinds of binary files), and allowed you to change the content by setting values in a form with human-readable labels. It would be easy to do that in a spreadsheet format, not entirely different from your Items worksheet. As it is I'm not 100% sure what the rows and columns in that sheet represent -- maybe there's not a good way to improve it.

---

### Post by schauerlich on 2012-09-07
> **wheel_walker said:**
> I don't need it to work on multiple CSVs (with or without wildcards), or to work on all CSVs with a directory.  Doing so may create problems, if some CSVs share the same data, or if someone forgets to remove an out-dated CSV.

Thank you.  Would you mind if I credited you?  Do you have any website you'd like me to link to, if someone wants to post a thank-you message, or anything you want advertised?

EDIT

My spreadsheets originally were going to use hex editors, but I couldn't find a hex editor that worked correctly - they would insert data instead of just overwriting data (which was what I needed, overwriting).  I mentioned this to the author of one such hex editor, and I think he's working on the issue.

EDIT
And what version of python is this for?

Feel free to steal it shamelessly. Or link to this thread. Whatever works for you.

It should work on anything 2.6+. I believe the with statement was added then.

---

### Post by wheel_walker on 2012-09-07
> **trent.josephsen said:**
> I was referring to keeping the annotations in-line with the content.
Annotations?  In-line?

> **trent.josephsen said:**
> I used a hex editor once a long time ago (last century) that basically read in and interpreted the file for you (using plugins for different kinds of binary files), and allowed you to change the content by setting values in a form with human-readable labels. It would be easy to do that in a spreadsheet format, not entirely different from your Items worksheet. As it is I'm not 100% sure what the rows and columns in that sheet represent -- maybe there's not a good way to improve it.
But people would still have to open the file or files in a hex editor.  This python script is automated, and - in conjuction with the format I described for *.csv files - it can edit as many files as you need to, without you having to do anything except edit the spreadsheet.

Besides all that, many of the games I modify are CD/DVD based games, which require you to remove files from the disc image before you can modify them.  This python script only requires you to remove them and put them in the same directory as the *.csv file and the python script, after which you can insert them back into the disc image.

While a hex editor that allows you to create custom forms would be useful, it still isn't as powerful or flexible as a cleverly formatted spreadsheet and this python script.

I'm starting college in two weeks, for Computer Science.  In a few years, I'll have the skills to write my own hex editor.  I plan to make a hex editor with certain searching, count, replace-all, and string exporting functionality; and which is cross-platform.  This will be the hex editor I wish I had when I first started this hobby.  I can go into more detail if you are interested in the exact features I want, and why I want them.

MORE DETAIL:

* Find, Find Again Down, and Find Again Up
** Starting at Beginning of file, Starting at Cursor, Starting at Specified Address in Hex or Dec
*** Using various kinds of wildcards, like *, ?; or the ability to search for abc OR def, with the ability to keep adding OR statements

* Count
** Starting at Beginning of file, Starting at Cursor, Starting at Specified Address in Hex or Dec, or Between address A and address B
*** Using various kinds of wildcards, like *, ?; or the ability to  search for abc OR def, with the ability to keep adding OR statements
** Scripting capabilities, to Count all occurances of whatever to all files inside a directory, or specific files or directories, using wildcards for both the things to count and files/directories in which to count them.

* Replace Next Down, Replace Next Up, Replace All
** Starting at Beginning of file, Starting at Cursor, Starting at Specified Address in Hex or Dec, or **between address A and address B** (This last one is the single most useful feature I want)
 *** Using various kinds of wildcards for the string to replace, like *, ?; or the ability to  search for abc OR def, with the ability to keep adding OR statements; with the ability to set unique replacements for both of them
**** For example, I could replace 81 6E with 01 2A; OR 6E 01 with  2A 01.  This is useful if I'm not sure of the endianness of the data structure in question.
** Scripting capabilities, to Replace all occurrences of whatever to all  files inside a directory, or specific files or directories, using  wildcards for both the things to replace and files/directories in which to replace them.

* Hex String Exporting options
** Export hex string with base addresses: in hex or dec; how many places if you want extra zeros; or insert a starting base address of your own instead of the actual base address of the string.
** Export hex string with hexadecimal prefixes: or whatever prefex or postfix you want, ideally a text delimiter for import into a spreadsheet.
** Export hex string with a prefix or postfix for the base addresses.
** Export hex string and apply a decompression routine to it.  Requires plug-ins for various decompression routines, or scripting capabilities.
** Export hex string and disassemble it.  Requires plug-ins for various instruction sets.
** Export to clipboard, export to plain text, export to HTML, and plug-ins for exporting to various programming languages.

* Filetypes
** Can open a file inside a disc image
** Can open a process

END OF DETAILS!

There is also a demand for a spreadsheet application geared towards modding.  It would be a sort of game editor maker, as there are some very serious defects with spreadsheets, which you hit upon earlier in this conversation - namely, the user interface.

I'm sure that I can create some very clever arrangements of drop-down boxes that will tell you exactly what you are editing, but this creates a problem: after I get all the drop-down boxes set up, I need to go through EVERY SINGLE ONE OF THEM, and set them to reflect the original state of the game's data structures.  This will take weeks - I wont do it, it's too tedious.

So, what I need in a spreadsheet - when I'm done creating the UI - is a script that will read the original game data, and will set the UI to reflect that data.

Because it requires a script to do this, it is beyond the abilities of most people who want to modify games.  So the spreadsheet app should have this functionality built in.

Other than that, it needs to allow the user to select various UI thingies to reflect the different data structures - bit toggles, unsigned and signed bytes, endianness, unsigned and signed words, unsigned and signed d-words, and it needs plug-ins for various assemblers and disassemblers.

When I'm done with all that, I need a patch format that can work with disc image games or non-disc image games, and which reflects any possible change to the game files.
* Create file or directory
* Delete file or directory
* Overwrite data
* Insert data (makes file larger)
* Delete data (makes file smaller)

An xml-based format is my best bet, as I can easily generate xml with even the lamest spreadsheet app.

Because I have only these 5 types of commands, it can royally mess the game up, but that's the editor's problem, not mine.  I can't come up with all possible commands (like inserting a sub-file based on it's position in a pointer table in an archive, which may or may not be compressed) with only a spreadsheet editing program.  Well, I could, but it would take too long.  If you want to make a game editor that complex, then learn to program, and write your own.

Also, all of these programs need to work on crappy computers.  Even leafpad locks up when I try to Replace All random things when I'm formatting hex strings for use in a spreadsheet.

The spreadsheet editing program needs to recognize hexadecimal and binary when it sees it, and it needs hexadecimal math functions, so I don't have to use hex2dec and dec2hex.

> **schauerlich said:**
> Feel free to steal it shamelessly. Or link to this thread. Whatever works for you.

It should work on anything 2.6+. I believe the with statement was added then.
Thanks again!

---

