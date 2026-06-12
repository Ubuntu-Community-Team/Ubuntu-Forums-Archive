---
title: "File program Problem"
date: 2014-04-11
forum: Programming Talk
---

### Post by zinat on 2014-04-11
```

digraph _OP_control_flow {
	graph [center=true,
		epsilon=".000001",
		pack=true,
		rankdir=LR,
		ratio=compress,
		sep=".5",
		size="5.83,8.27",
		splines=true
	];
	node [fillcolor="#fff9f9",
		shape=doublecircle,
		style=filled
	];
	B02	 [fillcolor="#fff3f3",
		shape=circle];
	B01 -> B02;
	B03	 [shape=circle];
	B02 -> B03;
	B04	 [shape=circle];
	B03 -> B04;
	B05	 [fillcolor="#ffecec",
		shape=circle];
	B04 -> B05;
	B06	 [shape=circle];
	B05 -> B06;
	B07	 [fillcolor="#ffe6e6",
		shape=circle];
	B06 -> B07;
	B08	 [shape=circle];
	B07 -> B08;
	B09	 [fillcolor="#ffecec",
		shape=circle];
	B08 -> B09;
	B10	 [shape=circle];
	B09 -> B10;
	B11	 [fillcolor="#ffa0a0",
		shape=circle];
	B10 -> B11;
	B12	 [fillcolor="#ffe0e0",
		shape=circle];
	B11 -> B12	 [label="{5}"];
	B14	 [fillcolor="#ffa0a0",
		shape=circle];
	B11 -> B14	 [label="{4}"];
	B13	 [fillcolor="#ffc0c0",
		shape=circle];
	B12 -> B13	 [label="{5}"];
	B13 -> B14	 [label="{5}"];
	B15	 [fillcolor="#ffe6e6",
		shape=circle];
	B14 -> B15;
	B16	 [fillcolor="#ffcccc",
		shape=circle];
	B15 -> B16;
	B17	 [fillcolor="#ff4d4d",
		shape=circle];
	B16 -> B17	 [label="{4}"];
	B21	 [fillcolor="#ffcccc",
		shape=circle];
	B16 -> B21	 [label="{3}"];
	B18	 [fillcolor="#ff0000",
		shape=circle];
	B17 -> B18	 [label="{10}"];
	B19	 [fillcolor="#ffc0c0",
		shape=circle];
	B17 -> B19	 [label="{10}"];
	B17 -> B21	 [label="{4}"];
	B18 -> B19	 [label="{4}"];
	B20	 [fillcolor="#ffb3b3",
		shape=circle];
	B18 -> B20	 [label="{6}"];
	B20 -> B19	 [label="{6}"];
	B22	 [shape=circle];
	B21 -> B22;
	B23	 [shape=circle];
	B22 -> B23;
	B24	 [fillcolor="#ffecec",
		shape=circle];
	B23 -> B24;
	B25	 [fillcolor="#fff3f3",
		shape=circle];
	B24 -> B25;
	B26	 [fillcolor="#ff8080",
		shape=circle];
	B25 -> B26;
	B27	 [fillcolor="#ffc0c0",
		shape=circle];
	B26 -> B27	 [label="{5}"];
	B29	 [fillcolor="#ffc0c0",
		shape=circle];
	B26 -> B29	 [label="{4}"];
	B28	 [fillcolor="#ffe0e0",
		shape=circle];
	B27 -> B28	 [label="{5}"];
	B28 -> B29	 [label="{5}"];
	B30	 [shape=circle];
	B29 -> B30;
	B31	 [fillcolor="#fff3f3",
		shape=circle];
	B30 -> B31;
	B32	 [shape=circle];
	B31 -> B32;
	B32 -> B33;
}
```




This is .txt file, i want a cprogram to take the two string one before and one after this -> string from the whole file,concatenate them and store it in an array.


Can any one help with this..

---

### Post by Warren Hill on 2014-04-11
Lets be clear here about what we are trying to do.

What language are you using and would I be correct in thinking that you are trying to create a single string array the first few entries would contain this given the example text file you 

```
Array = {"B01",  "B02", "B02", "B03", "B03",  "B04", "B04", "B05", "B05", "B06", "B07", "B06", "B07", "B07", "B08", "B08", "B09", "B09",  "B10", ...} 
```

---

### Post by zinat on 2014-04-12
Yes Sir i wanna write a c program that will read whole file and where in that file this symbol i.e -> appears, concantenate the string before and after that symbol  and save it in an array

for eg save it as B01->B02 ...

---

### Post by dwhitney67 on 2014-04-12
> **zinat said:**
> 

This is .txt file, i want a cprogram to take the two string one before and one after this -> string from the whole file,concatenate them and store it in an array.


Can any one help with this..

Open the file, and read each line (using fgets).  Then for each line, check to see if it contains the string "->" (using strstr).  If it does, then split the line into two strings so that you can get the substrings on each side of the "->".

As for the array, you could allocate one using malloc, and then resize the array if necessary using realloc.

Lots of folks on this forum could write this program for you, but I think it would be best that you try doing it yourself.

---

### Post by zinat on 2014-04-14
B17 -> B19	 [label="{10}"];
	B17 -> B21	 [label="{4}"];
	B18 -> B19	 [label="{4}"];

Can any one help with the pointer solution to check for this -> symbol and one it finds the symbol it should move behind 4 characters and store the string
B17 in an array and then move 4 characters ahead and similarly save B21 likewise for each line do as above..

---

### Post by steeldriver on 2014-04-14
Did you try using strstr like dwhitney67 suggested?

Is there any particular reason this has to be done in C btw? What are you going to do with the values after you get them into the array?

---

### Post by zinat on 2014-04-15
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>


int wc(char* file_path, char* word){
    FILE *fp;
    int count = 0;
    int ch, len;


    if(NULL==(fp=fopen(file_path, "r")))
        return -1;
    len = strlen(word);
    for(;;){
        int i;
        if(EOF==(ch=fgetc(fp))) break;
        if((char)ch != *word) continue;
        for(i=1;i<len;++i){
            if(EOF==(ch = fgetc(fp))) goto end;
            if((char)ch != word[i]){
                fseek(fp, 1-i, SEEK_CUR);
                goto next;
            }
        }
        ++count;
        next: ;
    }
end:
    fclose(fp);
    return count;
}


int main(){//testestest : count 2
    char key[] = "->"; // the string I am searching for
    int wordcount = 0;


    wordcount = wc("test.txt", key);
    printf("%d \n",wordcount);
    return 0;
}




```

but i am not getting how to proceed with taking the string before and after the symbol -> . ie storing B01B02 in an array



help appreciated...

---

### Post by steeldriver on 2014-04-15
Is this your homework? if so, forum rules only allow us to *hint* and *suggest* - which we have already done. Did you look at dwhitney67's suggestions (using fgets and strstr)? if so, how did you decide to use fgetc and character-by-character comparisons?

---

