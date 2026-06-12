---
title: "Emacs Shell-Mode (MSYS) Autocomplete"
date: 2014-08-01
forum: Programming Talk
---

### Post by 3246251196 on 2014-08-01
[INDENT] 					Hi,

Let's say I am in '/c/someDir'

and in someDir I have:

fun_me.py
rune_me_other.sh

When in the emacs Shell-Mode prompt I cannot run ./f.. or ./r.. - it will not autocomplete. I have to type the whole thing in.

Why is this?

Cheers.

PS:

If I touch a temp.exe

./te.. will autocomplete to temp.exe 				
[/INDENT] 			
  			   		
 			 			 			[INDENT] 				 					[Last edited by 3246251196]("http://ubuntuforums.org/posthistory.php?p=13088232"); 11 Minutes Ago at 05:00 PM. 				 				 			
[/INDENT]

---

### Post by ofnuts on 2014-08-01
Autocomplete does more that just selecting file on their names, it also check that their type and access rights make sense. In your case I would says that for whatever reason, it doesn't see these files as executable.

---

### Post by 3246251196 on 2014-08-04
ofnuts,

I agree with what you say. We develop using Windows at work, unfortunately, and I am used to the better environment. However, I do all my stuff through emacs and refuse to use anything else. If it sees a hasbang bin bash then it is considered an executable. But even when creating a new script and making it executable by adding the hash-bang emacs shell is still not considering the file to be executable even though the flags suggest. I will have to dig around more, unless someone else knows how to make the file executable. BTW it does work through the standard MSYS shell, jus tnot emacs shell mode .

---

### Post by 3246251196 on 2014-08-04
ofnuts,

I agree with what you say. We develop using Windows at work, unfortunately, and I am used to the better environment. However, I do all my stuff through emacs and refuse to use anything else. If it sees a hasbang bin bash then it is considered an executable. But even when creating a new script and making it executable by adding the hash-bang emacs shell is still not considering the file to be executable even though the flags suggest. I will have to dig around more, unless someone else knows how to make the file executable. BTW it does work through the standard MSYS shell, jus tnot emacs shell mode .

---

### Post by 3246251196 on 2014-08-11
(setq shell-completion-execonly nil)

There will be a finer grained way of specifying which extensions/files to actually considere probably, but this will do.

---

