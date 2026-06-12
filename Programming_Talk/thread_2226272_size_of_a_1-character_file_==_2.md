---
title: "size of a 1-character file == 2"
date: 2014-05-26
forum: Programming Talk
---

### Post by IAMTubby on 2014-05-26
Hello,
I see that the size of a file which has only 1 character is 2 bytes. However, I would like to know what the second character is. _I thought it would be EOF or something._
```

IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ cat onecharacter.txt 1
IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ ls -l onecharacter.txt 
-rw-rw-r-- 1 IAMTubby IAMTubby **2** May 26 18:23 onecharacter.txt

```

But on printing the file in hex, I see that the one-character-file has OA once, whereas a file with a character followed by a new line has two OAs. Following is the hexdump of the files whose names are self-explanatory
```

IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ hexedit **Justonecharacter.txt **
00000000   31 0A                                                                                                                1.

IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ hexedit **onecharacterPlusEnter.txt **
00000000   31 0A 0A                                                                                                             1..

```

I was almost beginning to feel EOF == 2 consective EOFs, but the hexdump of 2ConsecutiveEnter.txt :p leaves me still confused on what the EOF really is and how it's arrived at.

---

### Post by spjackson on 2014-05-26
A file on a Linux filesystem does not have any EOF marker as such. In your first file, you have the character '1' and a linefeed (end of line marker), and the second one has '1' followed by 2 linefeeds. You can create a file without an end of line marker thus:
```

echo -n 1 > justone.txt

```
and its size will be precisely 1 byte.

---

### Post by IAMTubby on 2014-05-26
> **spjackson said:**
> In your first file, you have the character '1' and a linefeed (end of line marker), and the second one has '1' followed by 2 linefeeds.
Thanks spjackson,
But I did not enter the linefeed in my first file. Is it inserted by default?

> echo -n 1 > justone.txt
Tried and works!

> A file on a Linux filesystem does not have any EOF marker as such.
How then does the system come to know that it's the end of the file ?

---

### Post by spjackson on 2014-05-26
I'm an application programmer and not an expert on system internals but I think it is determined from the size recorded in the inode.

---

### Post by ofnuts on 2014-05-26
> **IAMTubby said:**
> But I did not enter the linefeed in my first file. Is it inserted by default?
Depends on the text editor you used. Note that "wc -l" actually counts the linefeeds, so the "1" file above has zero lines... Edit: and this makes perfect sense: if you concatenate a file with one line to it, this is still one linefeed for the whole file, which is therefore considered to have only one line. So the line count of the concatenation is the sum of the line counts of its constituents.

> **IAMTubby said:**
> How then does the system come to know that it's the end of the file ?
The file descriptor contains the length in bytes. Some older file systems won't support files bigger than 2G or 4G because they store this size on 31 or 32 bits. In some very old file systems (CP/M, IIRC) the file system kept the size in sectors. This wasn't a problem for binary files (that usually have internal structures that indicate the size), and text files used a specific character (Ctrl-Z) to indicate the end of the actual text in the last sector.

---

### Post by IAMTubby on 2014-05-28
> **ofnuts said:**
> The file descriptor contains the length in bytes.
Thans ofnuts.

But, I need some more help here. I've used the EOF inside a C program few times that I've almost started to believe it's what signals the end of the road. Consider the code below, assuming "test.txt" contains just numbers from 0-9. That's it, no newline, just numbers.
```
#include <stdio.h>

int main(void)
{
 FILE* fp;
 char c;


 fp = fopen("test.txt","r");


 while(1)
 {
  c = getc(fp);


  if(c == EOF)
  {
   printf("EOF == [%d] reached, breaking now\n",c);
   break;
  }
  printf("read : [%c]==[%d]\n",c,c);
 }


 return 0;
}

```

And this is the output
```
read : [0]==[48]
read : [1]==[49]
read : [2]==[50]
read : [3]==[51]
read : [4]==[52]
read : [5]==[53]
read : [6]==[54]
read : [7]==[55]
read : [8]==[56]
read : [9]==[57]
read : [
]==[10]
EOF == [-1] reached, breaking now

```

This basically shows me that there are two characters which I haven't entered - 1.linefeed(ascii == 10) and 2.EOF, I guess(value == -1)

Can you tell me something about each of these two characters ? I thought about it a bit and came up with these possible answers.
1.(the linefeed) - as you said, probably, the text editor inserts this. _But why ?_
2.I'm basically interested in knowing when the EOF is inserted.
   - Is it like, as you said, the _inode tells the filesize, after which an EOF character(-1) is inserted so that C programs know when to stop reading ? _OR 
- Is it like, _newline and EOF_ are two characters that are always there in any file, by default, and these _are concatenated to the file contents when you do a :wq! in vi. ?_


Thanks.

---

### Post by IAMTubby on 2014-05-28
> **spjackson said:**
> I think it is determined from the size recorded in the inode.
Thanks spjackson.

---

### Post by ofnuts on 2014-05-28
[LIST]
[*]Linefeed: is actually part of the file. Either you do something that your editor interprets as a line feed or it adds one by default at the end of the file (but I cannot tell you why, the editor I use (KDE's kate) doesn't). Two images: the first one, the file without a LF in the editor, notice the size and how the second "echo" output appears on the same line as the "cat" output, the second, with a LF in the editor, and the corresponding outputs.
[/LIST]

[ATTACH=CONFIG]253528[/ATTACH][ATTACH=CONFIG]253527[/ATTACH]


[LIST]
[*]The EOF isn't really a character, it's a special value used to tell you there are no more characters, a bit like NULL is returned by other calls to tell you that you can't have what you are asking (more memory or else).
[/LIST]

---

### Post by IAMTubby on 2014-05-28
> **ofnuts said:**
> 
[LIST]
[*]Linefeed: I cannot tell you why, the editor I use (KDE's kate) doesn't).
[/LIST]

[LIST]
[*]The EOF isn't really a character, it's a special value used to tell you there are no more characters, a bit like NULL is returned by other calls to tell you that you can't have what you are asking (more memory or else).
[/LIST]

I was wondering how EOF==-1 can be a negative ascii value.
Thank you ofnuts, clears it.

---

### Post by ofnuts on 2014-05-28
> **IAMTubby said:**
> I was wondering how EOF==-1 can be a negative ascii value.
Thank you ofnuts, clears it.

... and also how it can be a 32-bit ASCII value...  :)

---

### Post by The Cog on 2014-05-30
By my understanding, the whole reason that getc returns an int rather than a char (which at first thought you might expect it to do) is so that it is then able to indicate end of file by returning a value that cannot be a valid char value. If it only returned char there would be no way to signal EOF.

---

### Post by dwhitney67 on 2014-05-31
> **ofnuts said:**
> Linefeed: is actually part of the file. Either you do something that your editor interprets as a line feed or it adds one by default at the end of the file

You are correct; the line feed in Tubby's file was inserted by whatever means he used to create the file.  Line feeds do not magically get included in a file unless the editor or other tool inserts them.

Perhaps Tubby should create his text file using the following command:
```

echo -n "0123456789" > test.txt

```
Note the -n option instructs echo not to generate a newline.

---

