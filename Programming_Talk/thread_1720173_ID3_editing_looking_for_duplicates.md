---
title: "ID3 editing/ looking for duplicates"
date: 2011-04-02
forum: Programming Talk
---

### Post by jmg158 on 2011-04-02
Hey guys,

Quick general questions really quick. 

I'm looking to write a program to go through some music files that I have scattered around and add them to common folder. In the process of doing this I would like the program to check to see if I am duplicating another file by referencing data found in the ID3 tags of the files already located in the target folder. 

(I'll probably look at name and length... it feels like sometimes small variations can screw me over though... like 'Big D and the Kids Table' or 'Big D & the Kids Table' or "Big D and the Kids' Table")

I know that python has some cute ID3 functionality, and I know C++  has some good ways of reading them as well. I looking for input as to what language I should use before I get halfway started. I'm not sure if anything exists in bash or not... but I suppose thats always another option.

Any thoughts?

---

### Post by Phenax on 2011-04-03
You'll either have to roll your own code to parse the ID3v1 and ID3v2 formats, or use an external library that can do it for you.

For C/C++: [http://id3lib.sourceforge.net/](http://id3lib.sourceforge.net/)
For Python: [http://pyid3lib.sourceforge.net/](http://pyid3lib.sourceforge.net/)
Command line utility: [http://id3v2.sourceforge.net/](http://id3v2.sourceforge.net/)
These are probably available in your package manager, and if not, I'm sure similar libraries or utilities exist. I don't have an Ubuntu system handy at the moment, so I can't check.

If you want results, I would recommend either using a command line utility and a small Bash script, possibly in conjunction with grep/sed/awk, or using Python or another expressive language along with a conforming ID3v1/ID3v2-handling library. If you want to learn something about the ID3 format, I would write it in any language, but don't use an external library.

ID3v1 is actually very simple to parse yourself. ID3v2 is a lot more complex. [The Wikipedia page for ID3 tags]("http://en.wikipedia.org/wiki/ID3") has a lot of information.


Here's some simple code that analyzes some fields of an mp3 containing ID3v1 formatted tags. It's quite naive, and doesn't use any external libraries, but it's a start. The ID3v1 tags are generally 128 bytes at the end of an mp3 file, but sometimes there are "extended" ID3v1 tags (see wikipedia article) that are different. ID3v2 is a much different beast, and requires a lot more complex code, which is why I recommend either using a command line utility or an external library to save a lot of your time.
```

#include <stdio.h>
#include <stdint.h>

typedef struct //struct for id3v1 information (incomplete)
{
    char header[4]; //header is 3 chars + null terminator (if not TAG+)
    char title[31]; //title is 30 chars + null terminator
    char artist[31]; //artist is 30 chars + null terminator
    char album[31]; //album is 30 chars + null terminator
    int year; //we parse year from 4 chars + null terminator
} id3v1;

void end_str(char *str, uint8_t size) //get rid of trailing spaces in fields
{
    while(size > 0 && str[size - 1] == ' ')
        size--;
    
    str[size] = '\0';
}

int main(int argc, char *argv[])
{
    id3v1 tag;
    char temp[5]; //for string->int conversion of year

    if(argc != 2) //takes 1 argument
    {
        printf("Usage: ./executable <mp3file>\n");
        return 1;
    }

    FILE *fp = fopen(argv[1], "r");
    if(fp == NULL)
    {
        printf("Could not open file.\n");
        return 1;
    }

    fseek(fp, -128, SEEK_END); //seek to 128 bytes from end of file
    //read the next 3 bytes of fp (the file) into tag.header.
    //we used 4 as argument instead of 3 because it adds a null terminator '\0' for us.
    fgets(tag.header, 4, fp);

    fseek(fp, -125, SEEK_END); //seek to 125 bytes from end of file
    fgets(tag.title, 31, fp); //read next 30 bytes, 31 cuz of null terminator
    end_str(tag.title, 30);
    
    fseek(fp, -95, SEEK_END); //and so on
    fgets(tag.artist, 31, fp);
    end_str(tag.artist, 30); //get rid of trailing spaces in field

    fseek(fp, -65, SEEK_END);
    fgets(tag.album, 31, fp);
    end_str(tag.album, 30);

    fseek(fp, -35, SEEK_END);
    fgets(temp, 5, fp);
    end_str(temp, 4);
    tag.year = atoi(temp); //convert to integer
    
    fclose(fp); //close file

    printf("Header: %s, Title: %s, Artist: %s, Album: %s, Year: %d\n", 
        tag.header, tag.title, tag.artist, tag.album, tag.year);

    return 0;
}

``````
>a.exe Memories.mp3
Header: TAG, Title: Memories, Artist: John Mayall, Album: Memories, Year: 1971

```

---

### Post by Some Penguin on 2011-04-03
For checking for fuzzy dedupe, consider reading up on phonetic hashes (Soundex, Metaphone, NYSIIS for instance) and stopword removal.  I don't know whether you'll need to convert numbers <-> text (matching "100 Years" with "One Hundred Years", but that would conceivably be useful too).

Phonetic hash + approximate matching on duration would probably be pretty decent.

---

### Post by Phenax on 2011-04-03
A very simple approach would be to compute the [Levenshtein distance]("http://en.wikipedia.org/wiki/Levenshtein_distance") of two strings, and if it is sufficiently close, ask the user if they are the same album/artist/etc.

---

