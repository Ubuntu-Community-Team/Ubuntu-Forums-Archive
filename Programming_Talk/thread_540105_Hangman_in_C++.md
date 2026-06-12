---
title: "Hangman in C++"
date: 2007-09-01
forum: Programming Talk
---

### Post by peabody on 2007-09-01
I was bored, let me know what you guys think:

[http://peabody.weeman.org/hangman.cpp](http://peabody.weeman.org/hangman.cpp)

---

### Post by eph1973 on 2007-09-01
Just a minor spelling error I noticed:

Line 30 of do_turn():

<< "Congratulations!  You avoided the hangman's nose." << endl;

nose should be noose (unless you really meant they avoided the hangman's nose :-))

---

### Post by peabody on 2007-09-01
Good call, I'll have to fix that :).

---

### Post by TheLions on 2008-01-01
OK i'll return this thread to life cause i'm trying to create simple hangman, but i'm stuck.

since i'm newbie to c can anyone explain (or even better write some code) how to read random words from external text file and then put it char array.:confused:

---

### Post by geirha on 2008-01-01
I'm guessing you are meaning c++ and not c since this is a c++ thread ... here's a tutorial I found on google that seems to cover it:
[http://www.functionx.com/cpp/articles/filestreaming.htm](http://www.functionx.com/cpp/articles/filestreaming.htm)

---

### Post by Fixman on 2008-01-01
Nice done.

---

### Post by TheLions on 2008-01-01
> **geirha said:**
> I'm guessing you are meaning c++ and not c since this is a c++ thread ... here's a tutorial I found on google that seems to cover it:
[http://www.functionx.com/cpp/articles/filestreaming.htm](http://www.functionx.com/cpp/articles/filestreaming.htm)

unfortunately i need it in c not c++, i thought that it's the same, but it isn't:(

---

### Post by geirha on 2008-01-01
> **TheLions said:**
> unfortunately i need it in c not c++, i thought that it's the same, but it isn't:(

Ah, well, find yourself a c beginner guide, file IO is usually covered in those. The actual function you want to look for is [fopen](http://en.wikipedia.org/wiki/Fopen).

---

### Post by LaRoza on 2008-01-01
> **TheLions said:**
> unfortunately i need it in c not c++, i thought that it's the same, but it isn't:(

See my wiki.

---

### Post by revanthedarth on 2008-01-01
You may use stdio (FILE*) and read all the words in a file. Then you'll randomly choose which to use. You can store words in a linked list or extendible array. The rest should be easy.

---

### Post by TheLions on 2008-01-01
> **revanthedarth said:**
> You may use stdio (FILE*) and read all the words in a file. Then you'll randomly choose which to use. You can store words in a linked list or extendible array. The rest should be easy.

you mean i create matrix and put every word in one row?
then with rand choose which row?

> **LaRoza said:**
> See my wiki.

from some turtorial on your wiki.

[PHP]#include < stdio.h>

void main()
{
    FILE *fp;
    int i;

    fp = fopen("foo.dat", "w");        /* open foo.dat for writing */

    fprintf(fp, "\nSample Code\n\n");  /* write some info */
    for (i = 1; i <= 10 ; i++)
	fprintf(fp, "i = %d\n", i);

    fclose(fp);			       /* close the file  */
}[/PHP]

when i run it in Kdevelop, i get this:
```
/bin/sh: /home/marko/hhj/debug/./src/hhj: not found
Press Enter to continue!
```

where should i create file called foo.dat?

---

### Post by dwhitney67 on 2008-01-01
The 'foo.dat' file is _created_ in the current directory.  It doesn't have to exist prior to running the program.

The error you are receiving pertains to your setup of Kdevelop.  Since I am not familiar with that tool, I will instruct you how to get this program compiled and running using the command line:

```
$ gcc code.c
$ ./a.out
$ cat foo.dat
```

Btw, either you copied/pasted a syntactically incorrect file, or you have typos in your code.  Here's the proper code:

[PHP]#include <stdio.h>      /* no space between < and stdio.h */

int main()      /* main returns an int; should not be void */
{
    FILE *fp;
    int i;

    fp = fopen("foo.dat", "w");        /* open foo.dat for writing */

    fprintf(fp, "\nSample Code\n\n");  /* write some info */
    for (i = 1; i <= 10 ; i++)
    fprintf(fp, "i = %d\n", i);

    fclose(fp);                   /* close the file  */

    return 0;   /* return value for main() */
}[/PHP]

---

### Post by revanthedarth on 2008-01-03
> **TheLions said:**
> you mean i create matrix and put every word in one row?
then with rand choose which row?


This is the extendible-array way. Linked list way is simpler to code. Then choose which word randomly, and go forward on the linked list that times.

By the way, fopen(path, "w") creates a file called path, if path exists, consider it deleted and created again (as empty file).

---

### Post by TheLions on 2008-01-03
> **revanthedarth said:**
> This is the extendible-array way. Linked list way is simpler to code. Then choose which word randomly, and go forward on the linked list that times.
...

thanks for the reply, but can you write an example for static array or linked list way?

also i'm interested how to print text in different color then black. any thoughts?

---

### Post by revanthedarth on 2008-01-03
For colors, [http://www.linuxjournal.com/article/8603](http://www.linuxjournal.com/article/8603)
I tried that too :)

Linked list is easier, so this is for lined list:
```

struct node
{
	char* data;
	struct node* next;
};
struct node *root, *end, *iter;
void init()
{
	root = (struct node*)malloc(sizeof(struct node));
	end = root;
}
void addData(char* arg)
{
	end->data = arg;
	end->next = (struct node*)malloc(sizeof(struct node));
	end = end->next;
}
char* returnTheIth(int i)
{
	end->next = root;
	iter = root;
	for(int j=0; j<i; j++)
		iter = iter->next;
	return iter->data;
}

```
You can store the size of linked list, and when you want the i.th element, you'll take (i %size)th element.

And, it's not static array, It's extendible. I can't write from stratch, but i remember the pseudo-code
```

init array for N space
fill N space
if size == N
     reallocate the array, size + N bytes
fill the array
if the array is full
     reallocate the array, size + N bytes
...

```

---

