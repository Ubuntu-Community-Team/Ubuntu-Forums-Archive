---
title: "Gedit External Tools Simple Script problem"
date: 2008-09-06
forum: Programming Talk
---

### Post by Guiness on 2008-09-06
The code below works but it would be great to have gedit select all text and copy to clipboard at the end of the code. Ctrl-A and Ctrl-C commands don't work in the commands box. Would be easy if gedit had a macro key recorder and player.

#!/bin/sh
sed -e '
s/â€™/'\''/g      
s/â€œ/“/g
'

---

### Post by Guiness on 2008-09-16
I searched the internet and still cant find any such examples, if this isnt the right place to post this question then where is the best place to post it? I cant find any forums for gedit related scripts :(

---

### Post by Idefix82 on 2008-09-16
What does your tool do? To copy stuff into the clipboard using command line you can use this tool:
[http://www.debian-administration.org/articles/565]("http://www.debian-administration.org/articles/565")
For example to copy the contents of the file in gedit into the clipboard you could type
```
cat $GEDIT_CURRENT_DOCUMENT_NAME | xcip
```

---

### Post by Guiness on 2008-09-18
Thanks for that tool, didnt know there was such a thing, now I'm a step closer. The problem now is that cat $GEDIT_CURRENT_DOCUMENT_NAME | xclip 
only works for a saved file, so for that to work I need to save the pasted contents into a filename, if there is a way to script/automate a file to be saved then that command  will work.

I have a forum where a database conversion corrupted and added these weird characters, there's about 1000 posts that are affected. So I used this tool to fix them, it replaces the weird symbols with commas or quotes or spaces.

Gedit Script
#!/bin/sh
sed -e '
s/â&#8364;&#8482;/'\''/g
s/â&#8364;&#339;/&#8220;/g
s/â&#8364;/&#8221;/g
s/Â&#8364;&#8221;/-/g
s/â&#8364;¦//g
s/â&#8364;¢/-/g
s/â&#8364;&#732;//g
s/â&#8364;&#8220;//g
s/â&#8364;&#8221;//g
s/Â//g
'

I edit the post, copy the text into Gedit, run the script command and copy it back into the post and then keep repeating the process over and over till I get sore fingers from clicking the mouse.

---

### Post by Idefix82 on 2008-09-18
So are you the administrator of the forum? If so, then do you have the files containing the posts lying on the web server somewhere in some form of text format? If you do then you can change the contents of the files from the command line without using GEdit, so no need to get soar fingers, because you can just do it for all file in one script.
The command
```
sed 's/old string/new string/d' file.txt
```
will replace all occurrences of "old string" in file.txt by "new string". You can write a small shell script to do all the replacements you need for all the files you need.

---

### Post by Guiness on 2008-09-19
I wish it was like that but nah the posts are in a SQL database format, I tried using a global search and replace SQL query but even that doesnt work, the posts still appear the same, so I have no other option but to do it the hard way:(

Is there a way to save the current contents in Gedit with a script?, something like a Ctrl+S

Would be heaps handy if Gedit had a feature to record and play back keystrokes as some windows macro editors have.

---

### Post by Idefix82 on 2008-09-19
I think, Gedit is just not the right tool for you. What I would do if I were you would be to write a script that takes things from the clipboard (using the tool I recommended earlier) then replaces things in it using sed and then puts the result back into the clipboard. That will involve either a big chain of | operators or saving the content of the clipboard into a file using cat, modifying the file using sed and then copying the content of the modified file back into the clipboard with something like cat file | xcip. This should be very easy to write and the only thing you would have left to do would be to copy things, run the script (no need to paste into an editor by hand) and then paste back into the forum (no need to copy the new content cause the script does that).

However, a much easier way would be to write a PHP script that does all these things directly on the SQL database. Or is that what you say you have tried? I can't see why it shouldn't work.

---

### Post by Guiness on 2008-09-20
I tried the SQL global replace command before and it didnt work, so I looked deeper and discovered those characters appeared differently in the database which is why they never got replaced before. This time it all worked, thanks :)

---

### Post by samkraju on 2010-03-15
I developed a small plugin that records a set of keys pressed in gedit window and then plays it back.
You can download the latest version of this plugin from [http://code.google.com/p/gedit-macro-plugin/](http://code.google.com/p/gedit-macro-plugin/)
Hope this helps you all.

---

### Post by meuchmeister on 2010-06-03
Is it possible to force gedit to output to a new shell window?
I have set up gedit to compile code when i press Ctrl-1, and execute the program when i press Ctrl-2. 
The output is then shown in the bottom pane. I want it to output in a new shell window.

---

### Post by breckenr on 2010-08-11
I have a similar problem (and I'd like to use gedit to solve it because I want one tool that can be used by many users).   I'm cleaning up text from PDF files and I want to run an External Tool script that will do it in one action.  Most things work nicely, but I can't get sed to find line breaks.  There is no response to:

s/\r//g OR s/\\r//g (NOR s/\n//g, s/\\n//g)

But 

s/ /\r/g works fine.   

If I use the regex find/replace it finds \r\n without difficulty, and even the normal Gedit search and replace works for \r.

I know that I can use the Macro tool to record the whole process but there doesn't seem to be a way to save it.  (This tool is for users who have no interest in learning the innards of Gedit or regex).

---

### Post by JanNeggers on 2010-10-19
I realize that this is an slightly older topic, but I had the same question, and found the solution:
[http://old.nabble.com/save-current-file-td21163794.html](http://old.nabble.com/save-current-file-td21163794.html)

In short:

The $GEDIT_CURRENT_DOCUMENT_NAME variable returns the current filename, which, if you open it, will give you the content of the (old) saved file. But if you choose "current document" in the "input" selection box in the "external tools" menu, then the UNsaved document enters as a first input in your script. For example you can save your current text in the beginning of your script using:

```
#!/bin/bash
cat > $GEDIT_CURRENT_DOCUMENT_NAME
```Now gedit will complain when you save the file normally, since it recognizes that some other program has altered the file. So a nicer option would be to save to a temporary file, instead of overwriting.

---

