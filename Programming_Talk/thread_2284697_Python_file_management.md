---
title: "Python file management"
date: 2015-07-01
forum: Programming Talk
---

### Post by jaquesaulait on 2015-07-01
Hi all,
  I'm using IDLE (and python 3) to try and open a (.doc) file with this script:

[COLOR=#0000cd]my_file = open('/home/jack/Documents/Python/PFMgmt')[/COLOR]
[COLOR=#0000cd]open_file = my_file.read()[/COLOR]
[COLOR=#0000cd]print(open_file)[/COLOR]

... and it doesn't work.  I get the message (in the Python shell): 

[COLOR=#ff0000]File "/home/jack/Documents/Python/py files/File mgt practice.py", line 3, in <module>[/COLOR]
[COLOR=#ff0000]    my_file = open('/home/jack/Documents/Python/PFMgmt')[/COLOR]
[COLOR=#ff0000]IOError: [Errno 2] No such file or directory: '/home/jack/Documents/Python/PFMgmt'[/COLOR]

I know the script works as I can use it to open a text file in **/etc**, no problem.

I've checked in the absolute file path in the terminal, it looks to be correct.  I know the file is there because I put it there, I can see it there in terminal and GUI, it is bloody well there! 

[I]Can anybody please tell me why this isn't working!?
[/I]

Thanks very much for any advice.

   Jack.

---

### Post by spjackson on 2015-07-01
> **jaquesaulait said:**
> Hi all,
  I'm using IDLE (and python 3) to try and open a (.doc) file with this script:

If it is a .doc file, then isn't its name /home/jack/Documents/Python/PFMgmt.doc?

---

### Post by jaquesaulait on 2015-07-01
Hi SP,
  Thanks for the reply.  I had tried that to no avail; and the text files that have opened didn't require the (.txt) file extension.  However, I tried adding **.doc** to my script and got this error message in the shell:

[COLOR=#ff0000]File "/home/jack/Documents/Python/py files/File mgmt ex II.py", line 4, in <module>[/COLOR]
[COLOR=#ff0000]    open_file = my_file.read()[/COLOR]
[COLOR=#ff0000]  File "/usr/lib/python3.2/codecs.py", line 300, in decode[/COLOR]
[COLOR=#ff0000]    (result, consumed) = self._buffer_decode(data, self.errors, final)[/COLOR]
[COLOR=#ff0000]UnicodeDecodeError: 'utf-8' codec can't decode byte 0xd0 in position 0: invalid continuation byte

[/COLOR]At least it's not saying, 'no such file', now.  But I cannot see what is wrong with the line with the reported error, and, indeed, this script still works on an /etc file.

[COLOR=#ff0000][/COLOR]Any ideas..?

[COLOR=#ff0000][/COLOR]Thanks, Jack.[COLOR=#ff0000]

  

[/COLOR][COLOR=#ff0000][/COLOR]

---

### Post by steeldriver on 2015-07-01
What are you trying to do, exactly? If these are Word (or Word-compatible) .doc files then their raw content isn't going to be printable in the sense that python's 'print' function understands - you'd need to open them in binary mode and then do some pretty serious processing to extract any printable text, I think

If they are .docx then that might be a little easier since they are compressed archives with actual content in XML (and python has XML parser modules)

Or are you trying to send documents to an actual printer, using python?

---

### Post by jaquesaulait on 2015-07-01
I'm trying to write some text into a file using Python scripts, for which my learning materials has instructions.  My original file has the text, '*Alpha*' in it ... I'm trying to add the text, '*Beta*' ... it's not working.  Some small progress: I can now write to this file: [COLOR=#008000]/home/jack/File mgmt prac (.txt)
[/COLOR].. but the added text does not save to the original file..!  So far, *only 1* **extra** file with the added text has appeared in the folder, with the added text, *Beta*, **on its own**.  It's a mystery.  And / or I can see the added text only when the file is opened (with the same script that adds the text) in the Python shell.  (The .docx file wouldn't open in the shell, either.)  I think my learning materials are incomplete - what is the point of writing to a file if you can't save it?

---

### Post by jaquesaulait on 2015-07-12
Well, I'm no further forward, it'll just have to remain a mystery.  Thanks anyway to those who took the time to respond.  :-)

---

### Post by trent.josephsen on 2015-07-12
You had a file named (presumably) **/home/jack/File mgmt prac.txt**, containing "Alpha".

You used Python to write to (presumably) **/home/jack/File mgmt prac** the text "Beta".

Result: You now have two files, one with the .txt extension and one without, containing different data.

No mystery, just an oversight.

---

