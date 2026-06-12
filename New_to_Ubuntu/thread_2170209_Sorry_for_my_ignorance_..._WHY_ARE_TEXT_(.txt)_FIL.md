---
title: "Sorry for my ignorance ... WHY ARE TEXT (.txt) FILES DIFFICULT to import/open etc?"
date: 2013-08-25
forum: New to Ubuntu
---

### Post by skyesharica on 2013-08-25
*I've checked but can't search the too simple query.  *
[COLOR=#800080]I'm changing over to Ubuntu 12.04 from Windows and Apple.  I've found a lot of text files don't open because of "certain wrong characters".  I know absolutely no coding, but I'm aware that coders use text editors like "gedit" for programming language.  Is this why you can't always open and edit an old text file?  I've simply saved everything possible into Libre Office.  Lot of trouble.  Am I correct?[/COLOR] 
:oops:

---

### Post by GwL3eNC on 2013-08-25
Hello,

textfiles in windows use another character set as unix files. If i switched to unix i must 
convert all my files into utf8 char set. I used the file command to identify the current 
character set and then i used the iconv command to change it. Another command
is recode which u can use. After the conversion to utf8 all special characters should
shown correct.

---

### Post by coldraven on 2013-08-25
> **GwL3eNC said:**
> Hello,

textfiles in windows use another character set as unix files. If i switched to unix i must 
convert all my files into utf8 char set. I used the file command to identify the current 
character set and then i used the iconv command to change it. Another command
is recode which u can use. After the conversion to utf8 all special characters should
shown correct.

In plainer language GwL3eNC means something like this :)
In a terminal use the "file" command to find out the filetype
```
file readme.txt
```
gives
```
readme.txt: ASCII text
```
then use "iconv" to change the character set to UTF-8
```
iconv -f ASCII -t UTF-8 readme.txt -o new-readme.txt
```

Although in my example Gedit had no problem opening both files.
There is probably a way to automate this with a batch file but my brain is not up to it today.

Have a look at "dos2unix" it may be easier
[http://linuxcommand.org/man_pages/dos2unix1.html](http://linuxcommand.org/man_pages/dos2unix1.html)

---

### Post by Norm24 on 2013-08-25
dos2unix is in the repositories.

---

### Post by skyesharica on 2013-08-26
> **GwL3eNC said:**
> textfiles in windows use another character set as unix files. If i switched to unix i must convert all my files into utf8 char set. I used the file command to identify the current 
character set and then i used the iconv command to change it. Another command is recode which u can use. After the conversion to utf8 all special characters should shown correct.

Thankyou so much for such a fast response.  I'm having a breakdown so a bit slow.  OMG - that's programming.  And more coffee than I'll ever be able to do here.  But thanks so much.  I see from this, that my vague assumption is right ... the text file is a special file--probably a basis of programming, no?  Which requires conversion in a different OS.  I'll just keep everything in an office file.  But it's good to know that a gedit file is here to stay for Ubuntu.  And I'm praying that I am too![CENTER]
PuuuuuuuRRRRRRRRRRRRRRR ......  love Ubuntu forever, I hope!  
[/CENTER]

> **coldraven said:**
> but my brain is not up to it today.

Have a look at "dos2unix" it may be easier
[http://linuxcommand.org/man_pages/dos2unix1.html](http://linuxcommand.org/man_pages/dos2unix1.html)

Thankyou so much for trying hard when your brains are tired.  I saw that link, but I cannot understand programming.  It's all helpful in a dead simple way.  Are people like me not really appropriate for this forum -- sorta irritating the "geniuses"?  It's my first cuppa.  :confused:

hey norm24, well, i have a wonderful new community.  i hope they don't mind my inexperience ... repositories mean nothing 2 me.  but thankyou.

---

### Post by eternal243 on 2013-08-26
> **skyesharica said:**
> Thankyou so much for such a fast response.  I'm having a breakdown so a bit slow.  OMG - that's programming.  And more coffee than I'll ever be able to do here.  But thanks so much.  I see from this, that my vague assumption is right ... the text file is a special file--probably a basis of programming, no?  Which requires conversion in a different OS.  I'll just keep everything in an office file.  But it's good to know that a gedit file is here to stay for Ubuntu.  And I'm praying that I am too![CENTER][I]
[COLOR=#800080][FONT=comic sans ms]PuuuuuuuRRRRRRRRRRRRRRR ......  [/FONT][/COLOR][COLOR=#ff8c00][FONT=comic sans ms]love Ubuntu forever, I hope!  [/FONT][/COLOR][/I][COLOR=#ff8c00][FONT=comic sans ms]
[/FONT][/COLOR][/CENTER]

Well that depends on what you mean by programming, that is just a simple terminal command, everything you do in linux issues commands like that in the background. It is really not that hard and if you would try to understand the basic principles then you will find that it is the most useful tool on your computer since it can do almost anything for you, without much effort at all.

Its a bit scary in the beginning I admit, with all those letters and numbers, but once you get past that it is actually quite nice. :)

Here is something to get you started, open terminal, it's already installed on your computer, then try this command: ```
whoami
``` then press enter, and it will tell you the name of your user.

Some other commands with explanations can be found here. [http://www.dummies.com/how-to/content/common-linux-commands.html](http://www.dummies.com/how-to/content/common-linux-commands.html) :)

---

### Post by ikt on 2013-08-26
> **skyesharica said:**
>  Are people like me not really appropriate for this forum -- sorta irritating the "geniuses"?  It's my first cuppa.  :confused:

You're not irritating anyone, without you I'd be bored :P

txt files shouldn't be difficult to open, but it appears windows has coded your txt files in a special way.

If you can open the text files in LibreOffice, and open gedit, copy and paste the text from LibreOffice into gedit and then save the txt file again, and that should fix your txt files. Hopefully there isn't too many :/

---

### Post by Impavidus on 2013-08-26
You sound a bit confused.

.txt files are the simples files in existence. Every byte or small group of bytes stands for a single character and any .txt can usually be opened in any text editor, like gedit, nano, wordpad (on Windows) and office-like programs. Office-like programs don't save in .txt format by default (which wouldn't preserve formatting), but on request they can. Just select the file format .txt, also knows as plain text.

When moving plain text files from one operating system to another, two problems may occur. The first is in the convention for line endings. On Linux & family, line endings are encoded in the text file using the linefeed byte, number 10. Mac uses (or used to use, I never used Mac so I don't know the details) the carriage return byte (number 13), Windows uses a carriage return followed by a linefeed, as explained [here]("http://en.wikipedia.org/wiki/Newline"). Most text editors nowadays can open files using any convention and automatically detect the convention used, and, on Linux at least, can save files using any of the conventions. The utility **dos2unix** can convert your files too.

The other problem is in the character set (which character has which number) and the encoding of the text (how the numbers are stored as a sequence of bytes; text encoding has nothing to do with writing computer code). Linux uses by default the Unicode character set in the UTF-8 encoding, Windows often uses Unicode in the UTF-16 encoding, but there are many files in old 8-bit character sets around. Many text editors are smart enough to recognise the used character set and encoding, but sometimes you need to help them a bit. Most text editors know how to save files using a variety of character sets/encodings. ASCII is a subset of most 8-bit encodings and of Unicode in the UTF-8 encoding, so it's hardly ever needed to convert it. Converting ASCII into UTF-8 (as explained by coldraven) is a no-op.

If you can't open your text files in gedit but can in libreoffice, they may not be real plain text. Libreoffice should be able to save them as plain text. This will destroy any formatting of the text.

---

### Post by grahammechanical on 2013-08-26
A little bit more information and I hope I am not confusing things further.

ASCII = American Standard Code for Information Interchange. It allows for a maximum of 128 specified characters (letter and numbers) and that is not enough to represent characters in many languages other than English. Especially as 33 character spaces had to be used for characters that controlled the printer (control codes such as line-space)

ASCII has been superceeded by Universal Character Set which has led to Unicode fonts that have space for someting like 110,000 characters which makes it possible for one font to present many language characters and to do so by simply changing the keyboard layout.

Text files are supposed to be read by any text editor but it depends if the editor that created the text file was using Unicode or an ASCII charater set. To put it another way, how old is the text file?

Regards.

---

### Post by skyesharica on 2013-08-27
> **eternal243 said:**
> Some other commands with explanations can be found here. [http://www.dummies.com/how-to/content/common-linux-commands.html](http://www.dummies.com/how-to/content/common-linux-commands.html)

Thankyou.  I've tried a few.  It's my second attempt - in my life - at that.  I am not an "able seaman" when it comes to the coding terminal box ... and if the sea starts to get rough, well, I am not able to sail through that.  But it was fun to try one or two, thanks.  To give you an example of how difficult this is, let me tell you of this command.  I tried this one:  kill [options] pid ... to stop a process. Apparently I can use this, if the process refuses to stop, instead of shutting down and losing data.  But I can't work out what to do with this.  What will I put in the [options] box?  What will it "kill"? I tried a few times but gave up.  I'd rather just do an unsafe shut down and lose data.  But thanks for trying.  Ubuntu has been really easy for me - WITHOUT any programming. 
):P

---

### Post by Buntu Bunny on 2013-08-27
> **skyesharica said:**
>  Ubuntu has been really easy for me - WITHOUT any programming. 

Welcome to the Ubuntu Forums, skyesharica. This is a wonderful place to ask questions and get help for Ubuntu. 

At some point, consider learning how to use Terminal. There are plenty of resources to take you by the hand from the beginning, and guide you through the process of learning how to talk to your system. It's just learning another language. 

Here's one to get you started,[ Learning The Shell]("http://linuxcommand.org/lc3_learning_the_shell.php").

Many more are listed at [CommandLineResources]("https://help.ubuntu.com/community/CommandLineResources").

Like anything else, you start at the beginning and take one step at a time. :)

---

### Post by skyesharica on 2013-08-27
> **ikt said:**
> You're not irritating anyone, without you I'd be bored :P

txt files shouldn't be difficult to open, but it appears windows has coded your txt files in a special way.

If you can open the text files in LibreOffice, and open gedit, copy and paste the text from LibreOffice into gedit and then save the txt file again, and that should fix your txt files. Hopefully there isn't too many :/

LOL.  Thankyou so much.  I'll do exactly that.  I'm praying that I do not have to learn another OS, especially after the Windows sweatshop, and this beautiful Ubuntu is a keeper.  In future I'll keep some gedit text files and hope for a KEEPER!

  :guitar:

---

### Post by Impavidus on 2013-08-27
Once you learn how to use the command line it will be great, a very efficient way of controlling your computer, but it's no requirement. Not any more. I think it would be best for you to learn how to do whatever you want to do with the GUI, which allows you to do basically everything except some advanced troubleshooting. There is a task manager where you can click to kill programs that don't work correctly, instead of typing the kill command. If you need to convert character encodings, open the file in whatever program that will open it, click "save as" and change the options for file type, line ending convention or character encoding. Only try the command line when you feel ready for it.

---

### Post by skyesharica on 2013-08-27
> **Impavidus said:**
> You sound a bit confused.  .txt files etc ... 

THIS IS AWESOME.  Thankyou.  I see that it is a file import problem due to sophisticated character encoding ... and has little to do with programming.  :P

---

### Post by skyesharica on 2013-08-30
> **grahammechanical said:**
> To put it another way, how old is the text file?

Absolute WOWWWW!  What brains!  Um, well some of those text files might be some years ... even up to 10 years old.

> **Buntu Bunny said:**
> Welcome to the Ubuntu Forums, skyesharica. This is a wonderful place to ask questions and get help for Ubuntu.

Thankyou friend.  It is a wonderful journey.  :popcorn:

> **Impavidus said:**
> Once you learn how to use the command line it will be great, a very efficient way of controlling your computer, but it's no requirement. Not any more. I think it would be best for you to learn how to do whatever you want to do with the GUI, which allows you to do basically everything except some advanced troubleshooting. There is a task manager where you can click to kill programs that don't work correctly, instead of typing the kill command. If you need to convert character encodings, open the file in whatever program that will open it, click "save as" and change the options for file type, line ending convention or character encoding. Only try the command line when you feel ready for it.

Yes, I've found I need almost NO advanced skills - just medium level skills - like with any OS - with the GUI.  It saved my life.  

I found SYSTEM MONITOR instead of task manager.  I want to avoid downloading any other software than what's on it.  I found the software management tool very confusing - repositories etc.  I've ticked only minimal downloads ... I think, I hope!!!  I'VE ATTACHED COPIES OF MY SETTINGS FOR SOFTWARE SOURCES - do you mind if I ask if this is all good - I forget the default settings.  #-o
[CENTER] 
[ATTACH=CONFIG]245841[/ATTACH]

[ATTACH=CONFIG]245842[/ATTACH]

[ATTACH=CONFIG]245843[/ATTACH] 
[/CENTER]

---

### Post by Impavidus on 2013-08-30
Looks OK.

Text files 10 years old could be ASCII, which, being a subset of UTF-8, shouldn't cause any problems, UCS-2, obsolete by then but still used by Win98 I think, or one of a zillion different 8-bit encodings.

---

### Post by skyesharica on 2013-08-31
> **Impavidus said:**
> Looks OK.

Thankyou Impavidus - it's just way out of my league. :lolflag:

---

