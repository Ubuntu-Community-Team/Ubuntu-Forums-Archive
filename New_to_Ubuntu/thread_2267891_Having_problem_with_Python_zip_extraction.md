---
title: "Having problem with Python zip extraction"
date: 2015-03-04
forum: New to Ubuntu
---

### Post by Kyle_Baker on 2015-03-04
Ubuntu 14.04
Dell Optiplex 760
Hello, I am having a problem running Python files after extraction. 
I extract the files, place them in documents under the same file name.
 When I search for them I get the message that they are not found. 
 I am just at a lose. 
Thank you 


Have a great day

---

### Post by ian-weisser on 2015-03-04
Can you give a more detailed example?
How are you extracting files?
How are you placing the extracted files?
How are you later searching for the extracted files?

---

### Post by Kyle_Baker on 2015-03-04
I doubled clicked on the zip file and clicked the extract . 
Then go to documents and extract there. I am very new to this.
These files are for a course on EDX just trying to learn something new.
So I follow what is said there.
" [COLOR=#3C3C3C][FONT=Open Sans]After downloading the code ([/FONT][/COLOR][search.zip]("https://s3-us-west-2.amazonaws.com/cs188websitecontent/projects/release/search/v1/001/search.zip")[COLOR=#3C3C3C][FONT=Open Sans]), unzipping it, and changing to the directory, you should be able to play a game of Pacman by typing the following at the command line:[/FONT][/COLOR]python pacman.py

I get " python: can't open file 'pacman.py': [errno2] no such file or directory




Thank you

---

### Post by sotiris2 on 2015-03-04
So you unzipped it to Documents? 
And you opened a terminal and gave the command ```
 python pacman.py
```

The problem is probably that when is you open a new terminal window its pointed at you home folder not your Documents (your home folder contains Documents and Music and Pictures etc folders). You will see that the terminal has written something like ```
kyle@kyles-pc:~$
```

kyle will be your username, kyles-pc your pc's name and more importantly right now everything after the dots (sans $ sign) is the folder you are in.

~ stands for your home folder.  If you do ```
ls
``` You will see what's in there which will include your Documents folder. If you do ```
cd Documents
``` You will go to the Documents folder. There your command should work because the file will actually be there. 

In fact after you type ```
python pac
``` pressing tab will probably complete the command for you (tab tries to complete filenames, if only one matches it will complete with it. if more match pressing tab twice will show all possible files.)

---

### Post by Kyle_Baker on 2015-03-05
Thank you for the help you sent me in a good direction. I have it working:
~$ ls *.zip
"_file name_"
~$ unzip "_file name_".zip
[extracted file] 
~cd "_file name_"
~/"_file name_"$ ls

[list of files]

~/"_file name_"$ entered files and it worked  

Have a great one

---

