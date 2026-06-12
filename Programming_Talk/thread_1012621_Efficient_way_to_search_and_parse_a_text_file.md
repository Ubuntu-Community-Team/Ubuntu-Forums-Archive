---
title: "Efficient way to search and parse a text file?"
date: 2008-12-16
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-12-16
I have a very large text file ~50-400 MB that I need to search through, and extract information from.  Most of it, > 99%, I don't care about.  I just want a few specific lines here and there.  Problem is that the files will not be located on the computer, but rather stored on a remote drive over a network.  So is there any way that I can extract the information that I care about out of the file without having to download all of it?  Unfortunately, the information that I care about is not at known line numbers.  I could try some scheme of guessing where the information is as I am seeking through the file and jump around looking for it, but that's too complicated.  I think the answer to this question is that there is no way to find the information without risking the possibility of missing some of it without downloading the entire file and searching line-by-line.  Just want to ensure that I am not overlooking something...maybe there's a way to not get the entire line, but only the first few characters of it, then I could tell if the line is of interest to me without fetching all the characters on that line.  But I don't think this will work as getLine probably looks for the end of line character which is at the end of the line, and since the lines are not constant length...

---

### Post by scourge on 2008-12-16
> **SNYP40A1 said:**
> I have a very large text file ~50-400 MB that I need to search through, and extract information from.  Most of it, > 99%, I don't care about.  I just want a few specific lines here and there.  Problem is that the files will not be located on the computer, but rather stored on a remote drive over a network.  So is there any way that I can extract the information that I care about out of the file without having to download all of it?  Unfortunately, the information that I care about is not at known line numbers.  I could try some scheme of guessing where the information is as I am seeking through the file and jump around looking for it, but that's too complicated.  I think the answer to this question is that there is no way to find the information without risking the possibility of missing some of it without downloading the entire file and searching line-by-line.  Just want to ensure that I am not overlooking something...maybe there's a way to not get the entire line, but only the first few characters of it, then I could tell if the line is of interest to me without fetching all the characters on that line.  But I don't think this will work as getLine probably looks for the end of line character which is at the end of the line, and since the lines are not constant length...

Yes, you probably have to read the entire file - you can't magically skip to the next line without reading the rest of the current line. But you don't need to store the whole thing in memory at once, which could take an unacceptable amount of memory. Just open the remote file and read it in chunks - one line or a fixed number of bytes at a time.

---

### Post by pmasiar on 2008-12-16
run extract script on that remote machine.

Generators are rather flexible way to analyze huge text files, like logs: [http://www.dabeaz.com/generators/](http://www.dabeaz.com/generators/)

---

### Post by monkeyking on 2008-12-16
Couldn't you grep your way out of this.
Otherwise look into awk.

But it really depends on the kind of textfiles.

---

### Post by ghostdog74 on 2008-12-16
> **SNYP40A1 said:**
> but rather stored on a remote drive over a network. 

depending on what is "remote drive", some ways
1) using SSH (if SSH is turned on at the remote. Execute a remote command using ssh, that way you do your processing at the remote 
2) using telnet. If you use tools like Perl or Python, there are equivalent telnet protocol libraries you can use. Of course there must be telnet service running at the remote for this to work
3) run the actual processing at the remote server. Then "ssh" or "telnet" into remote to get the output.
4) if its on a shared drive, you can just map the drive, and do normal processing.

---

