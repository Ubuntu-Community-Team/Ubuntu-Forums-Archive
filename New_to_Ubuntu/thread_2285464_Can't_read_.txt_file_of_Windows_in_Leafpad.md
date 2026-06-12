---
title: "Can't read .txt file of Windows in Leafpad"
date: 2015-07-06
forum: New to Ubuntu
---

### Post by caesium2 on 2015-07-06
My friend sent me a .txt file created with Notepad of Windows 8.1 but I can't view it using Leafpad(It appears like those alien's wording). However, I can still read it using AbiWord. I googled the problem and I found out that there's a difference in their formats of text files, although I can't really understand fully. Since I'm a complete beginner of Linux environment, I am hoping someone to explain it in simpler words and offer solution on how to solve this problem, which mean I can view .txt file in Leafpad next time. Thanks in advance.

---

### Post by monkeybrain20122 on 2015-07-06
maybe dos2unix would solve your problem. [http://askubuntu.com/questions/376404/how-to-make-text-file-created-in-ubuntu-compatible-with-windows-notepad](http://askubuntu.com/questions/376404/how-to-make-text-file-created-in-ubuntu-compatible-with-windows-notepad)

---

### Post by HermanAB on 2015-07-06
Well, Leafpad isn't exactly the world's greatest editor, so it is probably getting confused.

---

### Post by SeijiSensei on 2015-07-06
There are two possibilities, though I can't tell from your description if one or both apply.

First, there is the issue with how Notepad (and some other Windows programs) indicate the end of a line.  Notepad uses two characters for this task, the "line feed" and the "carriage return." Unix systems use just the latter.  There are simple [command-line utilities]("http://www.betamaster.us/blog/?p=390") to strip the excess characters off.  However if you're not comfortable working at the terminal prompt, I suggest you ask your friend to create files in Wordpad rather than Notepad as Wordpad files work correctly in Unix.

The other possibility might have to do with "character sets."  Do you see strange collections of symbols scattered about the document where things like quotation marks should be appearing?  The command-line program [iconv]("http://manpages.ubuntu.com/manpages/dapper/en/man1/iconv.1.html") can convert files from one character-set to another.  On Ubuntu the target should be something called "UTF-8".

---

