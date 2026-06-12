---
title: "C++: Small Error?"
date: 2011-04-24
forum: Programming Talk
---

### Post by fallenshadow on 2011-04-24
[PHP]
void merge_sort(int low,int high)

{

	void merge(int,int,int);

	

	 int mid;

		 if(low<high)

		 {

			  mid=(low+high)/2;

			  merge_sort(low,mid);

			  merge_sort(mid+1,high);

			  merge(low,mid,high);

		 }

}

void merge(int low,int mid,int high,studentDetails (&s)[MAX_SIZE])
{
//My merge function contents
}
[/PHP]

Error:
> 

/tmp/ccr2Cncl.o: In function `merge_sort(int, int)':
Assignment2.cc: (.text+0x48b): undefined reference to `merge(int, int, int)'
collect2: ld returned 1 exit status
Compilation failed.



The error is coloured dark red, which as far as I understand means its only a small problem. However it prevents my code from compiling. I know its probably a mistake with function calling or passing but ive tried many different things and I only end up with more errors. :D

I would love a bit of advice on where ive lost my way with this.

---

### Post by ubu@ on 2011-04-24
I think you need to declare all the functions above (only signatures), because *merge_sort *is using *merge*.
if *merge* is not using *merge_sort* try only transfer the *merge* function above the *merge_sort*.

When I was programming in c++ and I had some functions in the class,  I created files* my_class.h* and *my_class.cpp*, where all the declarations were in *my_class.h* and all implementations were in *my_class.cpp.* The signatures in *my_class.cpp* then should look like that:
```
My_class::merge(...){
...
}

My_class::merge_sort(...){
...
}
```ubu@.

---

### Post by cipherboy_loc on 2011-04-24
If you look at your code, you see the following line:

```

merge(low, med, high);

```But merge is defined as:

```
[COLOR=#000000][COLOR=#007700]
[/COLOR][COLOR=Black]void merge[/COLOR][COLOR=Black]([/COLOR][COLOR=Black]int low[/COLOR][COLOR=Black],[/COLOR][COLOR=Black] int mid[/COLOR][COLOR=Black], [/COLOR][COLOR=Black]int high[/COLOR][COLOR=Red], [/COLOR][COLOR=Red]studentDetails [/COLOR][COLOR=Red](&[/COLOR][COLOR=Red]s[/COLOR][COLOR=Red])[[/COLOR][COLOR=Red]MAX_SIZE[/COLOR][COLOR=Red]])[/COLOR][/COLOR]

```You are missing the last argument. Though you didn't tell us if you had overloaded the merge function to support only 3 arguments.



Cipherboy

---

### Post by fallenshadow on 2011-04-24
[PHP]

void merge(int low,int mid,int high,studentDetails (&s)[MAX_SIZE])

{
//My merge function contents
}



void merge_sort(int low,int high)

{
	//void merge(int,int,int);
 //I dont really need or want this function declaration
	
	 int mid;

		 if(low<high)

		 {
			  mid=(low+high)/2;

			  merge_sort(low,mid);

			  merge_sort(mid+1,high);

			  merge(low,mid,high,studentDetails (&s)[MAX_SIZE]);
		 }
}
[/PHP]

Ok I swapped the functions around and removed the declaration of the merge function. However I still have a problem with this line:

> merge(low,mid,high,studentDetails (&s)[MAX_SIZE]);

I know its missing the last argument but when I try putting it in I get the following:

> error: &#8216;s&#8217; was not declared in this scope

Not sure how to solve this... as ive said I basically know the problem but haven't as yet been able to solve it.

---

### Post by layers on 2011-04-24
Whenever you have functions inside other functions, it is always great to use function definitions. For instance, for the merger(..), you will have 

```
[COLOR=#000000][COLOR=#0000BB]void merge_sort[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]int low[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000BB]int high[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
```right after #include <...>, so it is declared as a global function. With definitions, you don't need to write the functions code - just the name and its parameters. This solves problems like the egg and the chicken.

I see you have moved it correctly. Good.

You are getting undefined s, because I don't see it declared anywhere. I am talking about ```
[COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]merge[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]low[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000BB]mid[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000BB]high[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000BB]studentDetails [/COLOR][COLOR=#007700](&[/COLOR][COLOR=#0000BB]s[/COLOR][COLOR=#007700])[[/COLOR][COLOR=#0000BB]MAX_SIZE[/COLOR][COLOR=#007700]]);[/COLOR][/COLOR]
``` I assume it is some kind of array? I see no s anywhere in the function.

---

### Post by ubu@ on 2011-04-24
I don't understand this syntax.
[COLOR=Black]declaring merge:[COLOR=#000000][COLOR=#0000bb]
[COLOR=Red]void merge[/COLOR][/COLOR][COLOR=Red]([/COLOR][COLOR=Red]int low[/COLOR][COLOR=Red],[/COLOR][COLOR=Red]int mid[/COLOR][COLOR=Red],[/COLOR][COLOR=Red]int high[/COLOR][COLOR=Red],[/COLOR][COLOR=Red]studentDetails [/COLOR][COLOR=Red](&[/COLOR][COLOR=Red]s[/COLOR][COLOR=Red])[[/COLOR][COLOR=Red]MAX_SIZE[/COLOR][COLOR=Red]][/COLOR][/COLOR]
calling  merge:
[/COLOR][COLOR=#000000][COLOR=SeaGreen]merge(low,mid,high,studentDetails (&s)[MAX_SIZE[/COLOR][COLOR=#007700][COLOR=Black][COLOR=SeaGreen]]);[/COLOR]

[/COLOR][COLOR=Black]argument #1: 
[COLOR=Red]declaring - declared as int.[/COLOR]
[COLOR=SeaGreen]calling - called as int.[/COLOR]
**ok!**
[COLOR=DarkRed]
[/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Black][COLOR=#000000][COLOR=#007700][COLOR=Black]argument #2: 
[COLOR=Red]declaring - declared as int.[/COLOR]
[COLOR=SeaGreen]calling - called as int.[/COLOR]
**ok!**[/COLOR]
[COLOR=YellowGreen]
[/COLOR][/COLOR][/COLOR][COLOR=Black]argument #3: 
[COLOR=Red]declaring - declared as int.[/COLOR]
[COLOR=SeaGreen]calling - called as int.[/COLOR]
**ok!**
[/COLOR][COLOR=Red]
[/COLOR][COLOR=Black]argument #4: 
[COLOR=Red]declaring - declared as [/COLOR][/COLOR][COLOR=Red]studentDetails (&s)[MAX_SIZE][/COLOR][COLOR=Black][COLOR=Red].[/COLOR]
[COLOR=SeaGreen]calling - [/COLOR][/COLOR][COLOR=SeaGreen]declared as [/COLOR][COLOR=SeaGreen]studentDetails (&s)[MAX_SIZE][/COLOR][COLOR=Black][COLOR=SeaGreen].[/COLOR]
[/COLOR] [COLOR=Black] **why? I don't know this syntax of c++...**[/COLOR][/COLOR][COLOR=#000000][COLOR=#007700]


[COLOR=black]Ans '*s*' is really not declared in *merge_sort*. Is it global?[/COLOR]
[/COLOR][/COLOR]

---

### Post by layers on 2011-04-24
Bottom line: remove studentDetails where you are calling and declare s.

---

### Post by Some Penguin on 2011-04-24
Broken design.  How do you expect to do any sorting or anything else if you don't pass in the data?

---

### Post by fallenshadow on 2011-04-25
This is basically an array of structs... this is what I have declared in main:

[PHP]studentDetails student[MAX_SIZE];[/PHP]

The struct is called studentDetails. I don't have s declared in the main but im not sure how should I declare it.

The way im calling and declaring stuff is based on what dWhitney posted on this page:

[http://ubuntuforums.org/showthread.php?t=1723734&page=2]("http://ubuntuforums.org/showthread.php?t=1723734&page=2")

Its the first example he posted.

---

### Post by dwhitney67 on 2011-04-25
@ fallenshadow

What the others have been trying to tell you is that you need to:

1. Declare the array
2. Pass it to the appropriate function.

From the code you have posted thus far, and from the information in your last post, the following *may* suffice; of course, you will need to fill in the details.
```

...
struct studentDetails
{
   ...
};

void merge(int low, int mid, int high, studentDetails (&s)[MAX_SIZE])
{
   ...
}

void merge_sort(int low, int high, **studentDetails (&s)[MAX_SIZE]**)
{
   if (low < high)
   {
      int mid = (low + high) / 2;

      merge_sort(low, mid, s);

      merge_sort(mid + 1, high, s);

      merge(low, mid, high, s);
   }
}

...

int main()
{
   const int MAX_SIZE = 100;

   studentDetails s[MAX_SIZE];

   ...

   merge_sort(0, MAX_SIZE - 1, s);

   ...
}

```

---

### Post by fallenshadow on 2011-04-25
Well I tried something similar to what you have posted dWhitney but it was probably missing some minor details as it didn't work. :D

This helped me to get unstuck as I currently was for some time. Thanks to everyone involved in this thread! ;)

---

