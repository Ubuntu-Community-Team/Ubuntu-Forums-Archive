---
title: "Access denied to a file I recovered using Terminal on a bootable CD"
date: 2016-05-17
forum: New to Ubuntu
---

### Post by downdog89 on 2016-05-17
I booted from the latest version of Ubuntu via CD on my Windows 10 laptop. I was able to recover a deleted file using the [FONT=monospace]sudo ntfsundelete command. The file is located both on the desktop and home directory. When I try to open it or copy & paste it I receive a message stating that access was denied.

How can I gain access to the file and email it?

I a newbie to Ubuntu. Thank you for looking.[/FONT]

---

### Post by mastablasta on 2016-05-17
try:
```
sudo chmod 777 [I]yourfilename
[/I]
```
this will show current file permissions:```
ls -l *yourfilename*
```

---

### Post by downdog89 on 2016-05-17
Thank you, mastablasta. When using the sudo chmod command how do I type the filename when the filename is as an example,  smith and jones answer and counter-claim?

---

### Post by Geoffrey_Arndt on 2016-05-17
While on the desktop window - - right click and select "open terminal".    Then follow masta's instructions and type the full name of the file including spaces, and be sure the case matches.    That's one reason I don't prefer really long file names (one can almost always abbreviate if he/she stops to think (or use categorized folders).

oops - forgot about single-quotes due to file name spaces . . . thanks CantankRus . . .

---

### Post by CantankRus on 2016-05-17
If your terminal is open in the same directory as the file you can type
```
sudo chmod 777 smith
``` 
then hit tab and the terminal will auto complete adding the escape character for spaces
eg
```
sudo chmod 777 smith\ and\ jones\ answer\ and\ counter-claim
```

or enclose the file name in quotes...
```
sudo chmod 777 'smith and jones answer and counter-claim'
```

Even with those permissions I think you should still be able to right click/copy in the file browser and then in the terminal right click/"Paste Filenames"

---

### Post by downdog89 on 2016-05-17
Thank you both for your replies. That answered my question. I'm loving Ubuntu.

---

### Post by oldrocker99 on 2016-05-17
Since your problem has been rectified, please mark the thread as [SOLVED].

Thanks!

---

### Post by oldos2er on 2016-05-17
> **downdog89 said:**
> When using the sudo chmod command how do I type the filename when the filename is as an example,  smith and jones answer and counter-claim?

Just type *smith* then hit the Tab key (assuming there are no other files in the same folder beginning with "smith"), the shell will complete the name for you.

---

### Post by mastablasta on 2016-05-18
there is one more option - type the command then move the file from file manager into terminal window and see the magic happen :)

---

