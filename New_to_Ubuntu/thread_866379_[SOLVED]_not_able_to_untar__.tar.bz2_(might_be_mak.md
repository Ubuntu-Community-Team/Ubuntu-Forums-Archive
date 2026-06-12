---
title: "[SOLVED] not able to untar  .tar.bz2 (might be making some mistake in command)"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by imgkg on 2008-07-21
hi guys, i am kinda new to linux trying to untar "stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2" its a dictionary for stardict  well i guess i am not able to understand the "tar.bz2" command and what refers to file name in tar command is this file name ----------->"stardict-dictd_www.dict.org_gcide-2.4.2" if its filename it give me error as follows ,(file is located on the desktop)



user@user-desktop:~$ tar zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
tar: stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
user@user-desktop:~$ 




 please help me out :(

---

### Post by bprof on 2008-07-21
it looks the file name is incorrect, also to decompress use this
> 
tar -xjf filename.tar.bz2

---

### Post by Xerp on 2008-07-21
```
tar -jxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
```

---

### Post by mc4100 on 2008-07-21
> (file is located on the desktop)

Go to the desktop, right click the file and press "Extract Here".
Why do it the hard way? ;)

EDIT: I think you're error was... > tar zxvf
(You forgot the "-")
```
tar -zxvf
```

---

### Post by imgkg on 2008-07-21
so whats the file name and how to get the correct file name i just copy pasted that file name from properties window by right clicking the the file

---

### Post by ice60 on 2008-07-21
i was just looking at another thread that should help you. you can put some extra lines in your .bashrc file then from then on any time you need to decompress anything from a zip, rar, tar.bz2, tar.gz etc all you need to do is use the command '**extract** some_file.zip' or whatever extention it uses.

here's the thread and the post that has the code (it's near the end of it) -
[http://ubuntuforums.org/showpost.php?p=4254704&postcount=12](http://ubuntuforums.org/showpost.php?p=4254704&postcount=12)
[http://ubuntuforums.org/showthread.php?t=679762](http://ubuntuforums.org/showthread.php?t=679762)

just run this from your terminal -
```
gedit ~/.bashrc
```

then add this to the end -
```

#Extract things. Thanks to urukrama, Ubuntuforums.org	
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}
```
you have to re-open your terminal for it to work.

for the .rar and .7z to work you may have to search for them in the package manager and install them first.

---

### Post by imgkg on 2008-07-21
have tried as you said  getting  same error (i am sure something i am missing in file name )


user@user-desktop:~$ tar -zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
tar: stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
user@user-desktop:~$ 

(well i wanna learn how to install these tarballs didnt tried it before always messed up with it )

---

### Post by mc4100 on 2008-07-21
> **imgkg said:**
> have tried as you said  getting  same error (i am sure something i am missing in file name )


user@user-desktop:~$ tar -zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
tar: stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
user@user-desktop:~$ 

(well i wanna learn how to install these tarballs didnt tried it before always messed up with it )

```
cd /Desktop && tar -zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
```

---

### Post by Xerp on 2008-07-21
"cd" into the directory where the file is.
check it really is where you think you put it using "ls"
then ```
tar -jxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
```

Thats it - simple! :)

Pay very close attention to each of these commands.

cd is "change directory" - you need this to "be in" the place where your file is.

Next is the tar command - see how the "j" flag is used in place of the "z" flag?

---

### Post by imgkg on 2008-07-21
getting this error ( now i am sure there something wrong with filename from where to get a filename of a file ) is there something like autocomplete thing for filenames 

user@user-desktop:~$ cd /Desktop && tar -zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
bash: cd: /Desktop: No such file or directory
user@user-desktop:~$

---

### Post by ice60 on 2008-07-21
you either have to have your terminal in the same place as the file you want to work with or tell the terminal where to find it.

you can use the **ls** command to show what's in the directory you're in. if the file is on your desktop you need to "cd" (change directory) in to the desktop directory first -
```
cd Desktop
```
the terminal is case sensitive and desktop is spelt with a capital 'D'
[color=blue]**EDIT**[/color]
there's a nice tutorial for the terminal here -
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

to autocomplete the command use the 'tab' key, the one with two arrows on to the lsft of the keyboard. eg
cd Des <tab key>
and the rest of desktop should be completed for you :D

---

### Post by mc4100 on 2008-07-21
> **imgkg said:**
> getting this error ( now i am sure there something wrong with filename from where to get a filename of a file ) is there something like autocomplete thing for filenames 

user@user-desktop:~$ cd /Desktop && tar -zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
bash: cd: /Desktop: No such file or directory
user@user-desktop:~$

Oops I'm an idiot, sorry, no "/Desktop" OK, this is my last attempt:
```
cd Desktop && tar -zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
```

---

### Post by imgkg on 2008-07-21
i am so sorry to bother you again still gettting error i just copy pasted your command (anyays thanks for your help but it didnt worked)

user@user-desktop:~$ cd Desktop && tar -zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
user@user-desktop:~/Desktop$

---

### Post by mc4100 on 2008-07-21
> **ice60 said:**
> 
you can use the **ls** command to show what's in the directory you're in. 
EDIT: There was some text here, which is now deleted, because I AM AN IDIOT, so never mind. Sorry -- honestly, I need to *read* things better -- thought you said "the directory you're working in! Sorry, again, and again.
> **imgkg said:**
> i am so sorry to bother you again still gettting error i just copy pasted your command (anyays thanks for your help but it didnt worked)

user@user-desktop:~$ cd Desktop && tar -zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
user@user-desktop:~/Desktop$

Hey, don't worry about it, someone will eventually get it right, (I'm as much a beginner as you ;))

Seriously though, did you try right clicking on the file stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
and then pressing "Extract Here"? It's much easier.

---

### Post by imgkg on 2008-07-21
used used that cd command it showed like this 


user@user-desktop:~$ cd Desktop
user@user-desktop:~/Desktop$ 



(then used tar command)


user@user-desktop:~$ cd Desktop
user@user-desktop:~/Desktop$ tar -zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
user@user-desktop:~/Desktop$ 

this is what i get

---

### Post by imgkg on 2008-07-21
i guess its on desktop 

user@user-desktop:~/Desktop$ pwd
/home/user/Desktop
user@user-desktop:~/Desktop$

---

### Post by ice60 on 2008-07-21
try running this  -
```
cd ~/Desktop && tar xjf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
```

---

### Post by mc4100 on 2008-07-21
```
cd Desktop && tar -jxf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
```

---

### Post by imgkg on 2008-07-21
thank you so much ice60 it worked ( beer from me ) did anyone understood what mistake was i making

 cd Desktop && tar -jxf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2 <---------this command gives error again

---

### Post by mc4100 on 2008-07-21
> **imgkg said:**
> cd Desktop && tar -jxf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2 <---------this command gives error again
::resigned face:: Of course it does!
I'm glad you finally got it to work! Yay :)
.. you should press the medal, in the bottom right, for Ice60. It's a thank-you.
(BTW, I'm as curious as you to know what kept going wrong)

---

### Post by ice60 on 2008-07-21
> **imgkg said:**
> thank you so much ice60 it worked ( beer from me ) did anyone understood what mistake was i making

 cd Desktop && tar -jxf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2 <---------this command gives error again
no problem, after a few weeks of using ubuntu things get a lot easier.

what error are you getting? i'm useless with all those decompressing commands because i use something like i showed in post#6 and that does it all for me, i just use the extract command :D

---

### Post by imgkg on 2008-07-21
thank you guys for staying with me i guess mistake i was making was i wasnt in my directory where file was

---

### Post by ice60 on 2008-07-21
there are two problems you were having -

1, running the command in the wrong place

2, issuing the wrong command

```
user@user-desktop:~$ cd Desktop && tar -zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
user@user-desktop:~/Desktop$
```
you are stringing two commands together -
```
cd Desktop
```
and 
```
tar -zxvf stardict-dictd_www.dict.org_gcide-2.4.2.tar.bz2
```
the && means if the cd Desktop runs with no errors go on to the next command.
cd Desktop will only work if the Desktop directory is in the directory you are running the command from, you should see it with the 'ls' command. 

if you run -
**cd ~/Desktop**
that will get you there even if the desktop directory isn't in the directory you are in because the ~/ bit is short for /home/USERNAME. so with that you are giving the full path to the desktop so there can't be any mistakes.

the tar -zxvf didn't work above because it's the wrong command, it's used to decompress tar.gz archives, not tar.bz2 that you had.

---

### Post by imgkg on 2008-07-21
thank you once again

---

