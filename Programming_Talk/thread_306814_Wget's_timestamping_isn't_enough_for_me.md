---
title: "Wget's timestamping isn't enough for me"
date: 2006-11-25
forum: Programming Talk
---

### Post by Chomp on 2006-11-25
I don't know what I'm doing wrong. I downloaded a directory with wget, and timestamping is on by default.
```
wget -r -np http://url.com/directory
```

I left it on overnight, some files failed and eventually wget stopped connecting. So I have maybe 75% of all the files. I am dying to get that last 25%. 

When I try to do it again, it **re-downloads** files I already have even though timestamping is on. All of the files in this directory have **completely unique** names, so if a file on the server has the same name as a file on my computer, they are exact copies. 

How can I tell wget to skip any files that have the same name? Or is there an alternative? Timestamping in wget is worthless for some reason.

---

### Post by shining on 2006-11-25
> **Chomp said:**
> I don't know what I'm doing wrong. I downloaded a directory with wget, and timestamping is on by default.
.

[http://www.editcorp.com/Personal/Lars_Appel/wget/wget_5.html](http://www.editcorp.com/Personal/Lars_Appel/wget/wget_5.html) :
> 
The time-stamping in GNU Wget is turned on using `--timestamping' (`-N') option, or through timestamping = on directive in `.wgetrc'. With this option, for each file it intends to download, Wget will check whether a local file of the same name exists. If it does, and the remote file is older, Wget will not download it.


What do you mean it's on by default, you put timestamping = on in .wgetrc ?
Did you try running wget with -N or -timestamping , just to be sure?

---

### Post by Chomp on 2006-11-25
I know it's on, I've read that FAQ many times. Plus I'm using a proxy with wget, which would only work if wget was properly reading .wgetrc because that's where I put the port and #IP number. Timestamping is 100% on, it just doesn't work. [Edit:[color=red]I should clarify. It does work and I understand how it works. The problem is there is a slight error with the times so when it works, it downloads the same file again, thinking it's a new file. And if I turn it off, it will do that anyway. So I do not know what to do at this point.[/color]]

My first guess is that my system time and the time on the server aren't the same for the files, leading to this confusion. But I am no internet expert, so I could be completely wrong. 

Timestamping just isn't the solution I want at times, you know? Isn't there an option that only compares names instead of names and times?

---

### Post by shining on 2006-11-26
What about this one?

> 
`-nc' 
`--no-clobber' 
 Do not clobber existing files when saving to directory hierarchy within recursive retrieval of several files. This option is extremely useful when you wish to continue where you left off with retrieval of many files. If the files have the `.html' or (yuck) `.htm' suffix, they will be loaded from the local disk, and parsed as if they have been retrieved from the Web.


I wonder what it'll do to the file that was only partly downloaded (file being downloaded when the transfer was cancelled). There is also this option:
> 
`-c' 
`--continue' 
 Continue getting an existing file. This is useful when you want to finish up the download started by another program, or a previous instance of Wget. Thus you can write: 
wget -c [ftp://sunsite.doc.ic.ac.uk/ls-lR.Z](ftp://sunsite.doc.ic.ac.uk/ls-lR.Z)

 If there is a file name `ls-lR.Z' in the current directory, Wget will assume that it is the first portion of the remote file, and will require the server to continue the retrieval from an offset equal to the length of the local file. Note that you need not specify this option if all you want is Wget to continue retrieving where it left off when the connection is lost--Wget does this by default. You need this option only when you want to continue retrieval of a file already halfway retrieved, saved by another FTP client, or left by Wget being killed. Without `-c', the previous example would just begin to download the remote file to `ls-lR.Z.1'. The `-c' option is also applicable for HTTP servers that support the Range header.


Maybe both can used together?

---

