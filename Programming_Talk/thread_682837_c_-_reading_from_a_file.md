---
title: "c - reading from a file"
date: 2008-01-30
forum: Programming Talk
---

### Post by S15_88 on 2008-01-30
hi there i've used fscanf and fgets before but i'm having a bit of a mental block...

how would i read text from stdin a word at a time until EOF without reading the entire file into memory?  therefore working with single words only.  a word being any sequence of characters delimited by white space or the end of a sentence, ie: , ; . ? !

any help would be greatly appreciated...

Thanks, Alain

i'm thinking:
```

FILE *infile;

infile = fopen("somefile.txt", "r");

	if (infile == NULL) {
		Error("Unable to open file."); 
	}
        else{
           for(i...){
                fscanf(infile, "%s", string[i]);
           }
        }

```
or perhaps
```

 while(infile != EOF){
        fscanf(infile, "%s", string[i]);
}

```
but i don't see how to do it "word by word"

---

### Post by Martin Witte on 2008-01-30
a function to read a file word by word is not availae in c afaik see [http://www.mrx.net/c/readfunctions.html](http://www.mrx.net/c/readfunctions.html). you have to write it yourself, eg. with fgetc()

---

### Post by stroyan on 2008-01-30
You can use the scanf '%[]' *conversion specifier* to match a sequence of characters from a specific set.
The following example will break input files into words with the delimiters you listed.
This example uses a '%a[]' format that dynamically allocates storage for each word.
It uses a '%*[]' format that reads the delimiters between words without assigning that to a parameter.
[PHP]#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
    FILE *f;
    int i;
    char *word;

    for (i=1; i<argc; i++) {
        f = fopen(argv[i], "r");
        if (f == NULL) return 1;
        while (fscanf(f, "%a[^,;.?! \t\n]%*[,;.?! \t\n]", &word) == 1) {
            printf("word is '%s'\n", word);
            free(word);
        }
        fclose(f);
    }
    return 0;
}[/PHP]

---

