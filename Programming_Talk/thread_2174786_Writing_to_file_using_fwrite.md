---
title: "Writing to file using fwrite?"
date: 2013-09-16
forum: Programming Talk
---

### Post by fallenshadow on 2013-09-16
Hey all,

I can write simple variables out to a file but the problem is I have more complex things to write out. (such as structs and 2D arrays)

For writing out a struct I tried this:


```
FILE * WRITE = fopen(fileName, "w+b");

fwrite(&charData, sizeof(struct charData),1, WRITE);
 
fclose(WRITE);

```

However, I get a weird error about "missing lvalues". What does it mean?

---

### Post by r-senior on 2013-09-16
Is charData the name of a struct or the name of a variable?

---

### Post by spjackson on 2013-09-16
> **fallenshadow said:**
> Hey all,

I can write simple variables out to a file but the problem is I have more complex things to write out. (such as structs and 2D arrays)

For writing out a struct I tried this:


```
FILE * WRITE = fopen(fileName, "w+b");

fwrite(&charData, sizeof(struct charData),1, WRITE);
 
fclose(WRITE);

```

However, I get a weird error about "missing lvalues". What does it mean?
With a minimal wrapping to turn your code fragment into a complete program, your code compiles and executes correctly. e.g.
```

#include <stdio.h>

struct charData { char buffer[8] ; } charData;

int main()
{
  const char * fileName = "fubar.dat";
  FILE * WRITE = fopen(fileName, "w+b");

  fwrite(&charData, sizeof(struct charData),1, WRITE);
 
  fclose(WRITE);

  return 0;
}

```
This suggests that your problem lies elsewhere. Your code fragment could be invalid if WRITE is a macro, or if charData isn't declared appropriately. Of course, in real code, you'd want to test the return values of fopen, fread, fwrite.

In simple terms, an lvalue is an expression that can appear on the left-hand side of the assignment operator '=', but there are other contexts where an lvalue is required.

There are arguments advising against writing a struct as a whole rather than its members. However, there are contexts where writing a whole struct can "work".

---

### Post by fallenshadow on 2013-09-16
> Is charData the name of a struct or the name of a variable?

CharData is a struct. Here is my full code for this:

```
#include <stdio.h>

int saves[3];
int party[3];
int equipment[27];

struct charData {
    int class, attack, defense, crit, clan, level, xp, maxXp, hp, maxHp, aura, maxAura, mysticAtk,
    mysticDef, hpBonus, atkBonus, defBonus, vit, aur, range, str, luck, rangeBonus, mAtkBonus,
    mdefBonus, upgradePoints, a1, a2, a3, a4, a5, a6, a7, a8, a9, a10, s1, s2, s3, s4, s5, s6, s7,
    s8,s9,s10, weight, maxWeight;

    char*name;
    char*portrait;
    char*portraitLG;
    char*type;
    char*cond;
    char*loc;
};

struct charData CharDataArray[10];


void setCharData()
{
 CharDataArray[1].name="Jarrett";
 CharDataArray[1].class=1;
 CharDataArray[1].type="Knight";
 CharDataArray[1].portrait="jarrett";
 CharDataArray[1].portraitLG="jarrettLG";
 CharDataArray[1].level=1;
 CharDataArray[1].xp=0;
 CharDataArray[1].maxXp=60;
 CharDataArray[1].hp=30;
 CharDataArray[1].maxHp=30;
 CharDataArray[1].aura=10;
 CharDataArray[1].maxAura=10;
 CharDataArray[1].cond="Healthy";
 CharDataArray[1].attack=4;
 CharDataArray[1].defense=3;
 CharDataArray[1].crit=1;
 CharDataArray[1].mysticAtk=1;
 CharDataArray[1].mysticDef=1;
 CharDataArray[1].vit=1;
 CharDataArray[1].aur=1;
 CharDataArray[1].range=1;
 CharDataArray[1].str=1;
 CharDataArray[1].luck=1;
 CharDataArray[1].clan=0;
 CharDataArray[1].hpBonus=0;
 CharDataArray[1].atkBonus=0;
 CharDataArray[1].upgradePoints=8;
 CharDataArray[1].a1=1;
 CharDataArray[1].a2=2;
 CharDataArray[1].a3=3;
 CharDataArray[1].a4=4;
 CharDataArray[1].a5=5;
 CharDataArray[1].a6=6;
 CharDataArray[1].a7=7;
 CharDataArray[1].a8=8;
 CharDataArray[1].a9=9;
 CharDataArray[1].a10=10;
 CharDataArray[1].s1=1;
 CharDataArray[1].s2=4;
 //CharDataArray[1].s3=3;
 //CharDataArray[1].s4=4;
 //CharDataArray[1].s5=5;
 CharDataArray[1].weight=22;
 CharDataArray[1].maxWeight=100;
 CharDataArray[1].loc="Konia village";

 CharDataArray[2].name="Lorne";
 CharDataArray[2].class=2;
 CharDataArray[2].type="Rogue";
 CharDataArray[2].portrait="lorne";
 CharDataArray[2].portraitLG="lorneLG";
 CharDataArray[2].level=1;
 CharDataArray[2].xp=0;
 CharDataArray[2].maxXp=40;
 CharDataArray[2].hp=20;
 CharDataArray[2].maxHp=20;
 CharDataArray[2].aura=20;
 CharDataArray[2].maxAura=20;
 CharDataArray[2].cond="Healthy";
 CharDataArray[2].attack=2;
 CharDataArray[2].defense=1;
 CharDataArray[2].crit=2;
 CharDataArray[2].mysticAtk=3;
 CharDataArray[2].mysticDef=2;
 CharDataArray[2].vit=1;
 CharDataArray[2].aur=1;
 CharDataArray[2].range=1;
 CharDataArray[2].str=1;
 CharDataArray[2].luck=1;
 CharDataArray[2].clan=0;
 CharDataArray[2].hpBonus=0;
 CharDataArray[2].atkBonus=0;
 CharDataArray[2].upgradePoints=5;
 CharDataArray[2].a1=11;
 CharDataArray[2].a2=12;
 CharDataArray[2].a3=13;
 CharDataArray[2].a4=14;
 CharDataArray[2].a5=15;
 CharDataArray[2].a6=16;
 CharDataArray[2].a7=17;
 CharDataArray[2].a8=18;
 CharDataArray[2].a9=19;
 CharDataArray[2].a10=20;
 
 CharDataArray[3].name="Aissa";
 CharDataArray[3].class=3;
 CharDataArray[3].type="Mage";
 CharDataArray[3].portrait="aissa";
 CharDataArray[3].portraitLG="aissaLG";
 CharDataArray[3].level=1;
 CharDataArray[3].xp=0;
 CharDataArray[3].maxXp=80;
 CharDataArray[3].hp=40;
 CharDataArray[3].maxHp=40;
 CharDataArray[3].aura=30;
 CharDataArray[3].maxAura=30;
 CharDataArray[3].cond="Healthy";
 CharDataArray[3].attack=1;
 CharDataArray[3].defense=1;
 CharDataArray[3].crit=1;
 CharDataArray[3].mysticAtk=5;
 CharDataArray[3].mysticDef=2;
 CharDataArray[3].vit=1;
 CharDataArray[3].aur=1;
 CharDataArray[3].range=1;
 CharDataArray[3].str=1;
 CharDataArray[3].luck=1;
 CharDataArray[3].clan=0;
 CharDataArray[3].hpBonus=0;
 CharDataArray[3].atkBonus=0;
 CharDataArray[3].upgradePoints=3;
 CharDataArray[3].a1=21;
 CharDataArray[3].a2=22;
 CharDataArray[3].a3=23;
 CharDataArray[3].a4=24;
 CharDataArray[3].a5=25;
 CharDataArray[3].a6=26;
 CharDataArray[3].a7=27;
 CharDataArray[3].a8=28;
 CharDataArray[3].a9=29;
 CharDataArray[3].a10=30;
}

int main()
{
  setCharData();
	
  const char * fileName = "fubar.dat";
  FILE * WRITE = fopen(fileName, "w+b");

  fwrite(&charData, sizeof(struct charData),1, WRITE);
 
  fclose(WRITE);

  return 0;
}

```

@spjackson: You are right the code does compile for an empty struct so the problem must be my data setup.

---

### Post by spjackson on 2013-09-16
The difference between my code and yours is that I have a variable called charData but you don't. Here are a few things you might mean:
```

  fwrite(&CharDataArray, sizeof(CharDataArray),1, WRITE); // write whole array
  fwrite(&CharDataArray, sizeof(struct charData),1, WRITE); //write just CharDataArray[0], which is all 0s
  fwrite(&CharDataArray, sizeof(struct charData),4, WRITE); //write array elements 0, 1, 2, 3
  fwrite(&CharDataArray, sizeof(struct charData),10, WRITE); // another way to write the whole array

```
But your use case is an excellent example of why NOT to write a struct. For all those char pointers, you will write out the addresses they point to. What use will that be?

---

### Post by fallenshadow on 2013-09-16
This one seems to work for the ints but the Char* items are all messed up.  However, I am attempting to write out the full struct array, so im on the right track at least.

```
fwrite(&CharDataArray, sizeof(struct charData),10, WRITE); // another way to write the whole array
```

> For all those char pointers, you will write out the addresses they point to. What use will that be?

Ah, so for the Char* to not be corrupted I have to do what? Im not sure I understand you.

---

### Post by r-senior on 2013-09-16
When you write out the struct, the char pointers become useless because they point to a memory location that has no meaning next time the program runs.

```

+----------+
| char *s1 | --> "abc\0"
+----------+
| char *s2 | --> "def\0"
+----------+
| char *s3 | --> "ghi\0"
+----------+

```

You are only saving the memory inside the boxes, i.e. the pointers, not the memory pointed to by the pointers, i.e. the characters of the strings.

---

### Post by fallenshadow on 2013-09-16
Ahh, now I get it. So I have to record the addresses somewhere and then... ugh this is a mess. T_T

---

### Post by ofnuts on 2013-09-16
> **fallenshadow said:**
> Ahh, now I get it. So I have to record the addresses somewhere and then... ugh this is a mess. T_T
No, you have to write your strings in full... you can't really have you file mapping the structure directly. I would strongly recommend doing something more robust like writing each structure item as a formatted string on its own line (or even better saving the whole in some ini-like format). Yes, that means some function to write/read the struct, handle errors, etc... but in the long run it will make lots of thing easier.

---

### Post by fallenshadow on 2013-09-16
I have a bit of a problem though, this code is used within GameEditor and it seems I can't use strings. :/

This is why I am using Char*.

---

### Post by Bachstelze on 2013-09-16
Basically, you will really need a more involved save/load function than just a call to fwrite(). As was said, if you just fwrite() the contents of your struct, it will write only the addresses of the strings, not their contents. Needless to say, dumping everything together in one fwrite() is also not portable.

---

### Post by ofnuts on 2013-09-16
> **fallenshadow said:**
> I have a bit of a problem though, this code is used within GameEditor and it seems I can't use strings. :/

This is why I am using Char*.

The sequence of bytes your "char *" points to is colloquially known as "string".

---

### Post by fallenshadow on 2013-09-17
So, ye mean something like printing line by line for the Char* elements?

```

File *stream;

char *s = "this is a string";
char c = '\n';

    stream = fopen("results","w");
    
    fprintf(stream,"%s%c",s,c);
//etc.

```

---

### Post by dwhitney67 on 2013-09-17
> **fallenshadow said:**
> So, ye mean something like printing line by line for the Char* elements?

```

File *stream;

char *s = "this is a string";
char c = '\n';

    stream = fopen("results","w");
    
    fprintf(stream,"%s%c",s,c);
//etc.

```

Get into the habit of specifying pointers to hard-code string literals as const char*.  As for the fprintf(), it works very similar to printf().
```

const char* s = "this is a string";

FILE* stream = fopen("whatever", "w");

if (stream)
{
    fprintf(stream, "%s\n", s);      // note that I included the newline in the formatting.
}
else
{
    fprintf(stderr, "Failed to open file.\n");
}

```

---

### Post by ofnuts on 2013-09-18
> **fallenshadow said:**
> So, ye mean something like printing line by line for the Char* elements?

```

File *stream;

char *s = "this is a string";
char c = '\n';

    stream = fopen("results","w");
    
    fprintf(stream,"%s%c",s,c);
//etc.

```

For all elements... Unless you are saving megabytes of data and/or saving/loading them very frequently, save them to a text file. To read them you just need a bunch of fscanf()'s that are the direct symmetric of the fprintf()'s.

---

### Post by fallenshadow on 2013-09-19
Thanks everyone! Whoa this thread got long fast! :D 

I know people probably *facepalm* when they see my posts but I do appreciate all the advice. Im gonna have a go at this over the weekend and report back on the result. :)

---

### Post by fallenshadow on 2013-10-05
So I got the file writing going which was easy. The reading is a bit more involved.

Using fscanf I got the return value which is 1. Therefore its finding my value. The question is, how does one get at the actual value?

---

### Post by Bachstelze on 2013-10-05
fscanf() works exactly like scanf(). You give a pointer of the appropriate type and with sufficient space, and the read data gets put where the pointer says.

---

### Post by dwhitney67 on 2013-10-05
> **fallenshadow said:**
> So I got the file writing going which was easy. The reading is a bit more involved.

Using fscanf I got the return value which is 1. Therefore its finding my value. The question is, how does one get at the actual value?

The return value from fscanf() will indicate how many patterns in your format criteria were satisfied.  If you are getting a value of 1, then this implies that one format specifier was matched.

Can you elaborate on your question "... how does one get at the actual value?".  My crystal ball has been furloughed and hence is not functioning.

P.S.  Based on your original posts in this thread, I conjured the following simple program to demonstrate the writing of data using fprintf() and the reading of such using fscanf().  Perhaps this may help you.
```

#include <stdio.h>
#include <string.h>
#include <assert.h>


struct MyData
{
	int  value1, value2;
	char str[80];
};


void writeData(struct MyData* data, FILE* fp);
void readData(struct MyData* data, FILE* fp);


int main()
{
	struct MyData w_data;
	struct MyData r_data;

	w_data.value1 = 10;
	w_data.value2 = 20;
	strncpy(w_data.str, "This is a good day", sizeof(w_data.str));

	FILE* fp = fopen("MyData.txt", "w+");

	if (fp)
	{
		writeData(&w_data, fp);
		fclose(fp);
	}

	fp = fopen("MyData.txt", "r");

	if (fp)
	{
		readData(&r_data, fp);
		fclose(fp);
	}

	assert(w_data.value1 == r_data.value1);
	assert(w_data.value2 == r_data.value2);
	assert(strcmp(w_data.str, r_data.str) == 0);

	return 0;
}


void writeData(struct MyData* data, FILE* fp)
{
	assert(data != NULL);
	assert(fp != NULL);

	fprintf(fp, "%d\n", data->value1);
	fprintf(fp, "%d\n", data->value2);
	fprintf(fp, "%s\n", data->str);
}


void readData(struct MyData* data, FILE* fp)
{
	assert(data != NULL);
	assert(fp != NULL);

	fscanf(fp, "%d [^\n]", &data->value1);
	fscanf(fp, "%d [^\n]", &data->value2);
	fscanf(fp, "%79[^\t\n]", data->str);
}

```

---

### Post by fallenshadow on 2013-10-13
Thanks dwhitney, this code is excellent for the structs. However, I was having a problem with a simple int. I can store the value but not read it. *blushes*

```

 FILE * READ = fopen(fileName, "r");
 
 while (!feof(READ))
 {
   gold = fscanf(READ, "%d [^\n]", &gold);
 }
 fclose(READ);

```

It is returning 1 but the actual value in the text file is 4.

---

### Post by spjackson on 2013-10-13
You are using a single variable gold to try to hold two different values at the same time.
1. The integer value scanned ( &gold )
2. The number of items read by fscanf ( gold = fscanf(...); )

Use two different variables for the two different purposes.

---

### Post by fallenshadow on 2013-10-14
Right so we have a value to hold the fscanf value called readGold. Then I have gold which im gonna set to the actual value. However it seems to end up with a crazy high number now. Probably setting the gold to the address of it rather than the value.

```

int readGold = fscanf(READ, "%d [^\n]", &gold);
   if(readGold == 1)
   {
     gold = 0;
     gold = (READ, "%d", &gold);
     break;
   }


```

Am I at least on the right track here? ..or have I lost my way? :S

---

### Post by dwhitney67 on 2013-10-14
Why make things so difficult?  Keep it simple:
```

int gold;

if (fscanf(READ, "%d [^\n]", &gold) != 1)
{
    // error
}

```

---

### Post by fallenshadow on 2013-10-15
My code works in a normal .c file but not inside GameEditor, so it much be a bug with that. 

Sorry for the confusion folks! :/

---

