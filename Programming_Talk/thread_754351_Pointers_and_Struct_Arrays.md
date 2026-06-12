---
title: "Pointers and Struct Arrays"
date: 2008-04-13
forum: Programming Talk
---

### Post by atsukoarai86 on 2008-04-13
I'm able to read values from my file into the struct array from within a function using pointers to the array of struct.

[COLOR="SeaGreen"]// code for array of struct //[/COLOR]
[COLOR="Blue"]struct [/COLOR]CityData
{

	[COLOR="Blue"]char [/COLOR]name[20];	 [COLOR="SeaGreen"] // name of city[/COLOR]
	[COLOR="Blue"]int [/COLOR]pop,		[COLOR="SeaGreen"]// population as of 4/1/2005[/COLOR]
		popGrow;  [COLOR="SeaGreen"]   // populatino growth from 1990 to 2000[/COLOR]
} CityArray[25];

[COLOR="SeaGreen"]// function prototype //[/COLOR]
[COLOR="Blue"]void [/COLOR]Load(ifstream&, struct CityData*p);

[COLOR="SeaGreen"]// the function call...//[/COLOR]
[COLOR="Blue"]int [/COLOR]main()										
{
	[COLOR="Blue"]struct [/COLOR]CityData *arrayPtr = CityArray;	[COLOR="SeaGreen"]// assign pointer to array[/COLOR]
	[COLOR="SeaGreen"]//string Fname;		[/COLOR]			[COLOR="SeaGreen"]// user created file name for output[/COLOR]
	/[COLOR="SeaGreen"]/int HighPop;		[/COLOR]				[COLOR="SeaGreen"]// highest population in 4/2000		[/COLOR]				

	ifstream inData;	[COLOR="SeaGreen"]// declare object of ifstream[/COLOR]

	inData.open("rawdata.txt");	[COLOR="SeaGreen"]// open data file[/COLOR]
	Open(inData);   [COLOR="SeaGreen"]// tests for failure opening file[/COLOR]
	Load(inData, arrayPtr);	[COLOR="SeaGreen"]// pass pointer and ifstream object [/COLOR]
                                               [COLOR="SeaGreen"]// this one works great. [/COLOR]

       [COLOR="Blue"]return [/COLOR]0;
}
[COLOR="SeaGreen"]
// function definition//[/COLOR]
[COLOR="Blue"]void [/COLOR]Load(ifstream &ins, struct CityData *p)
{

	[COLOR="Blue"]while[/COLOR](ins)
	{
		[COLOR="Blue"]int [/COLOR]i=0;
	
		ins>>(p->name);
		ins>>(p->pop);
		ins>>(p->popGrow);

		p++;
	}

		[COLOR="Blue"]return[/COLOR];
}


------------------------------------------------------------------------------
Okay, all that mess works. Now, what I want to do is pass the pointer to the array of struct into a function that determines the greatest value of CityArray[i].pop. The code below works when I access the array directly within the main:

[COLOR="Blue"]for[/COLOR](i=0;i<25;i++){
     [COLOR="Blue"]if[/COLOR](i==0){
     max=CityArray[i].pop;
     }
     [COLOR="Blue"]else[/COLOR]{
          [COLOR="Blue"]if[/COLOR](CityArray[i].pop>max){
          max=CityArray[i].pop;
          }
     }
}

cout<<endl<<max;


So I can do it directly accessing the array of struct, but I want to pass the pointer to the struct and do this inside a function through the pointer. Can anyone help on this?

---

### Post by panayk on 2008-04-13
I think you can use the same syntax: ```
arrayPtr[i]
``` because [FONT="Fixedsys"] CityData[][/FONT] and [FONT="Fixedsys"]CityData*[/FONT] are essentially the same. Alternatively the following form should be equivalent: ```
*(arrayPtr+i)
```You can even try ```
(arrayPtr+i)->pop
``` Hope this helps!

---

### Post by forrestcupp on 2008-04-13
For future reference, the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) subforum is a better place to ask these kinds of questions.  This subforum is usually for help with Ubuntu related issues.

---

### Post by atsukoarai86 on 2008-04-13
> **panayk said:**
> I think you can use the same syntax: ```
arrayPtr[i]
``` because [FONT="Fixedsys"] CityData[][/FONT] and [FONT="Fixedsys"]CityData*[/FONT] are essentially the same. Alternatively the following form should be equivalent: ```
*(arrayPtr+i)
```You can even try ```
(arrayPtr+i)->pop
``` Hope this helps!

My brain is so mushed right now... I didn't see any programming forums... anyway... 

my problem is I get an error when I try to assign the value of the pointer to anything... like... if I have a for loop that I'm trying to use to walk through the struct array and add up the members of a certain element... I don't know how... it gives me all these errors... I tried something like this... this worked in another program I did...:

for(; p!='\0';p++){
cout<<*p;
}

as a simple example... 

but let's say I have... a temp variable... I want to go through the struct array, take the value of one member from every element, say CityArray.pop, and total them up. when I try to say

[COLOR="Blue"]void [/COLOR]AdditUp(struct CityData *p){
     [COLOR="Blue"]int [/COLOR]temp=0;

     [COLOR="Blue"]while[/COLOR](p){     [COLOR="Green"]// this line doesn't seem to pose a problem[/COLOR]
          temp=*p->pop;
          p++;
     }
 
     [COLOR="Blue"]return[/COLOR];
}



...I get an error that points to the line "temp=*p->pop;" and says "Illegal indirection"... I've tried indexing the pointer to the array like ... for(i=0; i<25;i++), then using p[i], but it won't let me do that... 

I don't know what to do...

---

### Post by forrestcupp on 2008-04-14
post the declaration of the struct that you are passing to the function.

---

### Post by panayk on 2008-04-14
Hi, it's been a while since I've programmed in C++, but:

a) Arrays are not null-terminated unless you make them. From the definition of Load, you don't seem to be storing NULL at the end of file.
b)[FONT="Courier New"] "temp=*p->pop;"[/FONT] seems wrong. I think [FONT="Courier New"]p->pop[/FONT] is correct which is short-hand for [FONT="Courier New"](*p).pop[/FONT]

EDIT: Are you using g++?

---

### Post by panayk on 2008-04-14
Anyway:

```
#include <iostream>

using namespace std;

struct Data
{
    int field;

    Data(int field) : field(field) {};
};

void print(Data *b)
{
    //this works
    for (int i=0; i<4; i++) cout << b[i].field << endl;
    
    //so does this
    for (int i=0; i<4; i++,b++) cout << b->field << endl;
}

int main(int argc, const char* argv[])
{
    Data a[] = {Data(1),Data(3),Data(5),Data(7)};

    Data *b = a;

    print(b);

    return 0;
}
```

---

### Post by atsukoarai86 on 2008-04-14
actually, the first suggestion worked!! I just wasn't implementing it properly. Simple syntax error. I guess when you've been programming something for 18 hour straight, things start to fall through the cracks. 

apparently there was no need to dereference the pointer to the struct and the member... 

Thank you all so much for all the assistance!! I genuinely appreciate it.

---

