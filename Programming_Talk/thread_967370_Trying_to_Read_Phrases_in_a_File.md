---
title: "Trying to Read Phrases in a File"
date: 2008-11-02
forum: Programming Talk
---

### Post by Arukas on 2008-11-02
Normally, I do not read in strings, I've usually crunch numbers.  I'm using C/C++ to trying and read phrases in from a file.

This is what I'm using to read in the lines.  

fscanf(fp,"%s",&string);		


Problem is the phrases varry in words, so it doesn't read the entire phrase.  I thought it would read line by line but its reading word by word.  

Anyone know how to do what I'm trying to do or a better way?  

I appreicate it.

---

### Post by gnusci on 2008-11-02
I cannot really fully understand your problem, but I guess you can try with **getline**:

[http://www.cplusplus.com/reference/iostream/istream/getline.html](http://www.cplusplus.com/reference/iostream/istream/getline.html)

Here some hints:


[PHP]char chr_buff[1024];
.
.
.
std::ifstream read_file("filename");
read_file.getline(chr_buff,1024);
[/PHP]

---

### Post by Arukas on 2008-11-02
The problem I was having was fscanf skips over white space.  Something easily over looked, and drove me crazy.  I couldn't figure out how to get fscanf to read white space.  

So I used fgetc and read character by character into an string and use the '\n' to separate entries. It worked perfectly.

---

### Post by doorman on 2008-11-02
Are you using C or C++? By the line
> **Arukas said:**
> 
fscanf(fp,"%s",&string);        

my guess is you're using C. If so, you can read in a line in two ways:

1) using fscanf:
[PHP]char str[81];
fscanf( fp, "%80[^\n]%*c", str );[/PHP]
the problem when using fscanf with "%s" is that "%s" reads the input till the first white space character comes along. When using the syntax proposed, fscanf reads at lost 80 characters, or till a newline character comes along. The "%*c" means: move the file pointer one character but do not save it anywhere in the memory (this way avoiding the \n to end up in the string)

2) using fgets:
[PHP]char str[81];
fgets( str, 80, fp );[/PHP]
the fgets function is well documented here: [http://www.cplusplus.com/reference/clibrary/cstdio/fgets.html](http://www.cplusplus.com/reference/clibrary/cstdio/fgets.html)

---

### Post by Arukas on 2008-11-02
Thanks I did not know that about the fscanf and thanks for the link.  I'm been looking at different sites for refreshers and reminders.  

As for using C, I learned C/C++ together so I use both.  Only reason I use fscanf is a lot of examples I find use that it.

---

