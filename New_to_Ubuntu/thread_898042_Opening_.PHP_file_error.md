---
title: "Opening .PHP file error"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by pankirk on 2008-08-22
I wrote a very php+MySql ecommerce site and transfered all of the files from my windows machine over to my usb flash stick, then formatted windows and installed ubuntu. Now when I try to open some of the .php files for editing it says:

"gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

What does this mean? How can I fix it? And I hope my files didnt go corrupt while transfering over to my USB stick... This would be horrible.

---

### Post by Rolcol on 2008-08-22
Hm... This is just a guess but maybe windows saves it in a unix-unfriendly format.  It should still be able to open.  Have you tried opening up the files using a command line text editor?

---

### Post by pankirk on 2008-08-22
I did. I used "sudo nano path/tofile/index.php" and the result was:

> 
@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@


---

### Post by Cypher on 2008-08-22
```

sudo apt-get install tofrodos

```
Install the tofrodos package with the command above, then in the top level directory of your application run
```

find . -name "*.php" | xargs dos2unix

```
This command will find all .PHP files and convert them to Unix encoding. This should appease Gedit and other Linux editors.

---

### Post by pankirk on 2008-08-23
Hmm, even after doing "find . -name "*.php" | xargs dos2unix" I still seem to be getting the error?

---

### Post by pankirk on 2008-08-23
Should I also include that when I open up the php files for editing, some of them actually let me open them up for editing, but others wont open they just give the:
> gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
error.

---

### Post by Cypher on 2008-08-25
Run the command "file <name>.php" to get information about the file. A normal PHP file should yield
```

$ file index.php
index.php: PHP script text

```

---

### Post by pankirk on 2008-08-25
Heres the result i get
> file '/home/patrick/Desktop/index.php'
/home/patrick/Desktop/index.php: data


---

### Post by graben3 on 2008-08-25
Have you tried opening your PHP files in Geany ?

Go into the Application menu and click Add/Remove 
Search for Geany

Install it and try opening your files with it. Its made for PHP files. I'm pretty sure it won't help much...but just try it to see...

---

### Post by graben3 on 2008-08-25
> **pankirk said:**
> I did. I used "sudo nano path/tofile/index.php" and the result was:

Is the result actually what I see : @^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^

Or this has been filtered by the forum script and we only see @^@^@^@^@^@^ because of that ?

Can you please post the real index.php file in an archive in an attachment so I can try to play with it to tell your more about what to do to help you ?

---

### Post by pankirk on 2008-08-26
The result in nano is really "@^@^@^@" repeated a bunch of times, its not filtered. Heres the index.php file of the site. it's in .zip format. I'm pretty sure its corrupt by now because i hae tried almost everything

---

### Post by Rolcol on 2008-08-26
From my experience ^@ is supposed to be a null character.  There's nothing in those files...

---

### Post by Dojan5 on 2008-08-26
Have you tried open it on a server? Does it print out correctly?

---

### Post by pankirk on 2008-08-26
Yea, I installed php , apache, and mysql. But it seems when I open te index.php file nothing shows up at all, just a blank screen.

---

### Post by gjoellee on 2008-08-26
I am a website admin and open .php files all the time! Just open them with "gedit" aka "text editor". Should not be harder then that :)

but I cannot open your file...there is some kind of code gedit doesn't recognize

---

### Post by pankirk on 2008-08-26
> **gjoellee said:**
> I am a website admin and open .php files all the time! Just open them with "gedit" aka "text editor". Should not be harder then that :)

but I cannot open your file...there is some kind of code gedit doesn't recognize

I'm the same. The problem is that I can't open it with anything.

---

### Post by Cypher on 2008-08-27
The file is all 0'ed out. If you have the file on your flash drive, try loading it again..

---

### Post by pankirk on 2008-08-28
I just think that some of the files are corrupt and wont open. I transfered them all to my drive but instantly pulled it out once it was done instead of safe removed the drive, which i think has caused some files to go bad. Thanks for all your help guys.

---

