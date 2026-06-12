---
title: "Batch Copy and file rename with Terminal"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by migs73 on 2014-04-22
Hi Folks

Problem one:
Multiple sub-directories containing e-books. These are named as follows;

ParentDirectory/A.N. Authorsname- Name of book/A. N. Authorsname - [NAMEOFBOOKSERIES] - Name of Book.mobi

I would like to use terminal and cd to ParentDirectory and from there mv all the *.mobi files from the sub-directories to an other Directory.

I have tried this after cd'ing into the ParentDirectory;
```
mv -R *.mobi /NewDirectory
```

It fell over on the -R operator which I thought meant recursivley. I tried many other commands I found on the web, but all fell over to the directories and files having special characters in them.

So to Problem two;

How to rename directories and files with special characters.

I have tried;
```
rename -n 's/\[NAMEOFBOOKSERIES]$/\_/' *.mobi
```

I know this will only show what will be done with the -n operator but does nothing.

Any help much appreciated.

Mike:)

---

### Post by papibe on 2014-04-22
Hi migs73.

For the move you could do this:
```
mv -iv  /path/to/ParentDirectory/*/*.mobi  /NewDirectory
```
or this:
```
find /path/to/ParentDirectory -iname '*.mobi' -exec mv -iv '{}'  /NewDirectory \;
```
As for the rename, add the option -v to see what may happend. Also you need to escape both brackets: 
```
rename -vn 's/**[COLOR="#FF0000"]\[/COLOR]**[/\_/' *.mobi
rename -vn 's/**[COLOR="#FF0000"]\[/COLOR]**]$/\_/' *.mobi
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by migs73 on 2014-04-22
Hi there, thanks for the response,

Tried the first line of code you suggested and it worked great!

Using the first line of rename code this cleared the open square brackets ([) from the title (yay!).

Your second line of code did not clear the closed bracket (]) (boo!) but I did find that removing the $ character did allow the closed bracket to be removed (yay!)
ie;
```
rename -vn 's/\]/\_/' *.mobi
``` not

```
rename -vn 's/\]$/\_/' *.mobi
```

Now I just need to find out how to remove some of the text and replace it with nothing as the rename command seems to insist that the replacement is a character.

Many Thanks

---

### Post by papibe on 2014-04-22
I'm glad that that pointed you in the right direction :)

We may be able to offer some with the renaming.

How the files are named right now?
How do you want to change them?

Also, a few actual renaming examples would be helpful.

Regards.

---

### Post by migs73 on 2014-04-23
Thanks Papibe

my files are now in the format;

A. N. Authorsname - [NAMEOFBOOKSERIES ##] - Name of Book(v3.0).mobi

note the spaces between A. N. at the start and the ## represents a two digit number (the number in the bookseries).

I would like it to be in this format;

A.N.Authorsname - Name of Book.mobi

ie strip out the uneccesary spaces, the '[NAMEOFBOOKSERIES ##]' one of the hyphens and the '(v3.0)' at the end.

Also to make things a little more awkward some of the files have been truncated due to excessive length, but I'll sort them out manually later.

Many Thanks

Mike (PS this is mainly just a learning excercise but I have lots of other ebooks and MP3's etc that I am sure will give me just as much bother at some point)

---

### Post by papibe on 2014-04-23
The easiest solution would be to install a GUI tool for renaming files.

I'd recommend pyRenamer since it's very powerful, and can deal with almost any case. For instance, this rules should work to get the results you want:
```
Original: {C}. {C}. {L} - [{X}] - {X}({X}).mobi

Renamed: {1}.{2}.{3} - {5}.mobi
```
Let us know if that works for you, or you are committed to do it on the command line.
Regards.

---

### Post by migs73 on 2014-04-23
Thanks Papibe

I'll give pyRenamer a try, looks like it will fit the bill.

Many Thanks

Mike :)

---

