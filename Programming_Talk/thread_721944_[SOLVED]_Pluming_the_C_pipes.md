---
title: "[SOLVED] Pluming the C pipes"
date: 2008-03-11
forum: Programming Talk
---

### Post by dempl_dempl on 2008-03-11
Hi all,

I'm currently making some very cool archiving library. If you want to see the details about it , you'll find usefull info   [ here ]("http://ubuntuforums.org/showthread.php?t=703757")   , but that's irrelevant for this thread. 

I'm currenlty having problems with RAR format.
Since I could not find some decent low-level RAR library, I've decided to use **unrar** command  in background ,and to pipe it trough .  I did not simply   called fork/exec  without pipes, because I want to place progress monitors and appropriate events. 

```

/* This code is bit simplified, of course, I've omitted logging and stuff */


// This command prints given archive-file  to stdout  ( option **p**   )  
// without printing any extra info like Copyright form RARLabs  ( **-inul** ) 
// The objective is to have same effect as writing the following in console: 
//  **rar p -inul 'myarchive.rar'  'myfile.pdf' >   '/home/dule/myfolder/myfile.pdf' **

FILE *fpipe;
string command= "rar p -inul  \'"  + "myarchive.rar" + "\' \'" + "myfile.pdf" + "\'";

if ( !(fpipe = (FILE*)popen(command.c_str(),"r")) )
{  // If fpipe is NULL
	
	pclose(fpipe);
	exit(1);

}
char c;
ofstream fout( "/home/dule/myfolder/myfile.pdf" );

while( (c = fgetc(fpipe)) != EOF)
{
	fout << c;
}


pclose(fpipe);
return true;

```


For small text files it works .  When I try to do this with , for example , PDF file,   program exits cleanly, but it unpacks small portion of file. 

When I issue the same command from shell, it works just as it should be.
 **rar p -inul 'myarchive.rar'  'myfile.pdf' >   '/home/dule/myfolder/myfile.pdf' **


Thanks in advance.
If anyone needs full source, I'll drop a link

---

### Post by dempl_dempl on 2008-03-12
He he , I'm just posting in order to send this thread on the first page , again :-)  .

---

### Post by Zugzwang on 2008-03-12
I'm not sure but the problem might be here:
```

while( (c = fgetc(fpipe)) != EOF)

```
The variable "c" is of type char (which has a length of one byte, I think), so if you read a "FF" byte from the input stream, it is treated as "-1" which is EOF. Try to test if the pdf file ends before the first occurrence of a 0xFF byte in the stream (use hexdump).

If this is the problem, define "c" as an int and case accordingly:
```

int c;
ofstream fout( "/home/dule/myfolder/myfile.pdf" );

while( (c = fgetc(fpipe)) != EOF)
{
	fout << (char)c;
}

```
Note that your code is mixed C/C++, so the title of your post is misleading.

---

### Post by dempl_dempl on 2008-03-12
I've did exactly as you've said , and it worked !      Thank you!

---

