---
title: "Find/[delete] all word processing files matching the criteria"
date: 2014-09-05
forum: Programming Talk
---

### Post by kumoshk on 2014-09-05
I just wrote a command-line Python program for searching all of the word processing files (doc, docx and odt) in a directory for a word or phrase. It also allows you optionally to delete the matches.

Here's a link to the code (unless pastebin.com tagged a license on it by my submitting it, please treat it as if it had the MIT license, which basically means I'm not liable, and you can do just about anything you want with it):

[http://pastebin.com/PJ4r9JBK](http://pastebin.com/PJ4r9JBK)

I don't guarantee that the software works in every case (although I hope it does). So, please test it thoroughly before doing anything too serious. The relatively simple code that gets text from docx and odt files probably needs review for more complex documents, since I'm not sure if it works properly on them, yet. Hopefully it does.

I'll likely extend this to allow for regular expression searches and for searching plain text documents, too, and all sub-directories recursively, also. If you want to do it, feel free.

---

### Post by kumoshk on 2014-09-05
Here's an updated version that doesn't allow for command-line arguments, but does allow for relative paths and moving files instead of deleting them. It will prompt you to create the destination directory if it doesn't exist. Just set word, from_dir and to_dir in the function call at the end of the file. Same license.

[http://pastebin.com/UdmXviCn](http://pastebin.com/UdmXviCn)

---

