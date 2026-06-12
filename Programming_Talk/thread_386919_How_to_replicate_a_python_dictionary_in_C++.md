---
title: "How to replicate a python dictionary in C++"
date: 2007-03-17
forum: Programming Talk
---

### Post by simplyw00x on 2007-03-17
I've just started a new project -[Guitarshik]("http://moho.frihost.net/covertninja/?p=102") - which is a Frets on Fire-inspired game written in C++ (to shortcut some speed and portability issues with FoF's python and obscure libaries). I plan to support the same midi format as Frets on Fire and Guitar Hero for notes, and am using jdkmidi for midi parsing, but am having trouble defining a table of equivalents for various notes.

The python source code for FoF which does what I want is as follows:

```
noteMap = {     # difficulty, note
  0x60: (AMAZING_DIFFICULTY,  0),
  0x61: (AMAZING_DIFFICULTY,  1),
  0x62: (AMAZING_DIFFICULTY,  2),
  0x63: (AMAZING_DIFFICULTY,  3),
  0x64: (AMAZING_DIFFICULTY,  4),
  0x54: (MEDIUM_DIFFICULTY,   0),
  0x55: (MEDIUM_DIFFICULTY,   1),
  0x56: (MEDIUM_DIFFICULTY,   2),
  0x57: (MEDIUM_DIFFICULTY,   3),
  0x58: (MEDIUM_DIFFICULTY,   4),
  0x48: (EASY_DIFFICULTY,     0),
  0x49: (EASY_DIFFICULTY,     1),
  0x4a: (EASY_DIFFICULTY,     2),
  0x4b: (EASY_DIFFICULTY,     3),
  0x4c: (EASY_DIFFICULTY,     4),
  0x3c: (SUPAEASY_DIFFICULTY, 0),
  0x3d: (SUPAEASY_DIFFICULTY, 1),
  0x3e: (SUPAEASY_DIFFICULTY, 2),
  0x3f: (SUPAEASY_DIFFICULTY, 3),
  0x40: (SUPAEASY_DIFFICULTY, 4),
}
```

But clearly this won't work in C++. Is there a way I could achieve a similar effect? Basically, I have code that returns note values from the midi file (an integer), and I need to look them up in a table such as the one above in order to decide whether - and how - to display them. Hence I need a (constant) data structure of some kind that can associate in this way.

Any ideas, gods of the internets?

Carl.

---

### Post by Tomosaur on 2007-03-17
You could define a new structure/class with the relevant fields, then just create an array of this struct/class.

If you're clever, you could make a simple multi-dimensional array and avoid the struct/class definitions, but this would be less intuitive to read because you'd probably need to do a fair bit of parsing to get any real information from them, unless you can represent difficulty / note information using a common data type, but it really depends on your application. In your case, I imagine you'd have no trouble using a multi dimensional array of ints.

---

### Post by Wybiral on 2007-03-17
You need an int-to-data lookup table?
Is there a chance in repeat "int" values?

If not, would a simple array work in this case?

If that won't work, try a map: [http://www.cppreference.com/cppmap/index.html](http://www.cppreference.com/cppmap/index.html)

---

### Post by simplyw00x on 2007-03-17
I don't need to get information in the form of "EASY_DIFFICULTY,     0" - I could probaby represent this as 1,0 or maybe 10 (and SUPAEASY 3 could be 03) but my problem is, if I have an array like:

{60,61,62,63,64 .... }

How can I easily test if, say, the value '0x55' (or 55, or 85) is in this array, and what the key of that is?

---

### Post by WW on 2007-03-17
If you are trying to replicate a map, why not use a map?  C++ has a map data structure in the STL.

For example:
```

#include <iostream>
#include <map>


using namespace std;

enum difficulty {SUPAEASY_DIFFICULTY, EASY_DIFFICULTY, MEDIUM_DIFFICULTY, AMAZING_DIFFICULTY};

class note_data
    {
    private:

    difficulty diff;
    int note;

    public:

    note_data();
    note_data(difficulty,int);
    void print();
    };

note_data::note_data()
    {
    diff = SUPAEASY_DIFFICULTY;
    note = 0;
    }

note_data::note_data(difficulty d, int n) : diff(d), note(n)
    {
    }

void note_data::print()
    {
    if (diff == AMAZING_DIFFICULTY)
        cout << "Amazing";
    else if (diff == MEDIUM_DIFFICULTY)
        cout << "Medium";
    else if (diff == EASY_DIFFICULTY)
        cout << "Easy";
    else
        cout << "Supaeasy";
    cout << ", " << note;
    }



int main()
    {
    map<int,note_data> noteMap;

    noteMap[0x60] = note_data(AMAZING_DIFFICULTY, 0);
    noteMap[0x61] = note_data(AMAZING_DIFFICULTY, 1);
    noteMap[0x62] = note_data(AMAZING_DIFFICULTY, 2);
    noteMap[0x63] = note_data(AMAZING_DIFFICULTY, 3);
    noteMap[0x64] = note_data(AMAZING_DIFFICULTY, 4);
    noteMap[0x54] = note_data(MEDIUM_DIFFICULTY, 0);
    noteMap[0x55] = note_data(MEDIUM_DIFFICULTY, 1);
    noteMap[0x56] = note_data(MEDIUM_DIFFICULTY, 2);
    noteMap[0x57] = note_data(MEDIUM_DIFFICULTY, 3);
    noteMap[0x58] = note_data(MEDIUM_DIFFICULTY, 4);
    noteMap[0x48] = note_data(EASY_DIFFICULTY, 0);
    noteMap[0x49] = note_data(EASY_DIFFICULTY, 1);
    noteMap[0x4a] = note_data(EASY_DIFFICULTY, 2);
    noteMap[0x4b] = note_data(EASY_DIFFICULTY, 3);
    noteMap[0x4c] = note_data(EASY_DIFFICULTY, 4);
    noteMap[0x3c] = note_data(SUPAEASY_DIFFICULTY, 0);
    noteMap[0x3d] = note_data(SUPAEASY_DIFFICULTY, 1);
    noteMap[0x3e] = note_data(SUPAEASY_DIFFICULTY, 2);
    noteMap[0x3f] = note_data(SUPAEASY_DIFFICULTY, 3);
    noteMap[0x40] = note_data(SUPAEASY_DIFFICULTY, 4);

    int note = 0x57;
    cout << "note=0x57: ";
    noteMap[note].print();
    cout << endl;

    note = 0x3f;
    cout << "note=0x3f: ";
    noteMap[note].print();
    cout << endl;   
    return 0;
    }

```
Output:
> 
note=0x57: Medium, 3
note=0x3f: Supaeasy, 3


---

### Post by simplyw00x on 2007-03-17
> If you are trying to replicate a map, why not use a map? C++ has a map data structure in the STL.
Because my C++ was learnt about 8 years ago. You're a god, thanks!

---

### Post by Wybiral on 2007-03-17
But it would be just as easy, and faster, to use a simple array...

```

#include <stdio.h>

#define SUPAEASY_DIFFICULTY 0
#define EASY_DIFFICULTY     1
#define MEDIUM_DIFFICULTY   2
#define AMAZING_DIFFICULTY  3

typedef struct
{
   int difficulty;
   int note;
} t_noteMap;

t_noteMap setNoteMap(int difficulty, int note)
{
   t_noteMap temp_map;
   temp_map.difficulty = difficulty;
   temp_map.note = note;
   return temp_map;
}

int main()
{
   t_noteMap noteMap[0x100];
   noteMap[0x60] = setNoteMap(AMAZING_DIFFICULTY, 0);
}

```

And, as Tomosaur mentioned, you don't even need a structure, if each element had two elements, you could just index them like this:

```

#include <stdio.h>

#define DIFFICULTY 0
#define NOTE       1

#define SUPAEASY_DIFFICULTY 0
#define EASY_DIFFICULTY     1
#define MEDIUM_DIFFICULTY   2
#define AMAZING_DIFFICULTY  3

void setNoteMap(int map[2], int difficulty, int note)
{
   map[DIFFICULTY] = difficulty;
   map[NOTE] = note;
}

int main()
{
   int noteMap[0x100][2];
   setNoteMap(noteMap[0x60], AMAZING_DIFFICULTY, 0);

   // Print result
   printf("0x60: NOTE = %i\n", noteMap[0x60][NOTE]);
}

```

I know this is C code, but it can easily be adapted to be more C++ like.

My advice is if you don't have to use more complex data types, don't.

If you know the range of the space you need, then just statically allocate it.

It will be much faster!

---

### Post by simplyw00x on 2007-03-18
I've gone for the struct method; it seems to be working so far, though I think WW's method might come in useful later on, when I'm dealing with moe complex structures. Thanks to all.

---

### Post by Wybiral on 2007-03-18
Maps are definitely useful. But they can be pretty slow. If you can get away with using an array or something that's easy for the program to read/write to, your program will perform better.

---

