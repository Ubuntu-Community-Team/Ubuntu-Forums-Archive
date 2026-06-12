---
title: "C Program using arrays"
date: 2008-04-18
forum: Programming Talk
---

### Post by VChief on 2008-04-18
I need a favor, if anyone would be willing to help me out. I'm taking Advanced C. Beginning C was pretty easy and I flew through it with very little difficulty, but Advanced C is giving me a problem. My biggest problem, so far, seems to be understanding arrays. The first assignment included functions used to load a variable into an array, search the array and print the array. I totally bombed that assignment. So, as I'm still trying to figure it out, I was wondering if anyone would be willing to help me out. Pretty much, I'd like to give out what the assignment was and then, when the code is done, use the code to learn. I think that it would be a great help because then I can actually see how the arrays work, etc. I'm not sure if I should post the assignment or if PM would be better, so, if you're willing to help me out, please let me know the preferred method of communication for this issue.

As I said, the assignment deadline is past (last Friday), so I'm not asking anyone to do my homework (I don't play ball that way). I just want to be able to learn the material and am 99% sure this will help. I've read several things on arrays and I'm still not grasping any of it so I'm hoping to be able to learn from the code. Thank you.

EDIT: Ok, I'm bad at reading stickies...but I just saw the one for homework. As I said, the assignment deadline is already passed and I can't turn this in anymore, so I'm hoping it doesn't still violate the letter or spirit of the law. If it does, I sincerely apologize and if my request isn't acceptable, I ask if anyone can give a different explanation to my problem of understanding arrays. I'm already upset that I can't figure it out on my own, especially after doing so well in my first C class. As stated above, I'm just hoping being able to see the code will help me out, which I am positive will. But, I'll take what I can get to understand this material. Thank you.

---

### Post by smartbei on 2008-04-18
Hmmm... What exactly don't you understand?

Have you tried reading tutorials/explanations such as [this one]("http://www.codersource.net/c++_arrays_tutorial.html") (which says C++ but is really C)?

---

### Post by CptPicard on 2008-04-18
Sure, but ... could you please be a bit more specific what exactly it is you are not getting regarding arrays? :) It would be easier to answer specific questions...

---

### Post by VChief on 2008-04-18
I'm having trouble with how to use arrays and how to write them into my program. I understand the concept of arrays, I just seem to have a problem with practical application. Pretty much, past the theory, I'm done. I don't think I'm too dumb, so this is just aggravating.

I'll look at that site and see if it helps. I was just hoping for a new way to look at it (either via ANY source code or by a different explanation).

---

### Post by CptPicard on 2008-04-18
```

int arr[10];  // arr is array of 10 ints

arr[2] = 4;  // third one in array is 4 (counting from 0, remember)

arr[2]   // anywhere in your code will evaluate to 4

```

So..? :)

---

### Post by itix on 2008-04-18
I can try to help... but handing you the code seams the wrong way to go. You can stare yourdelf blind on the code and not get a {insert random curse here}.

an array is like a long line of boxes tied together with a string and they all have numbers (also called indexes). to create an array in C, simply do
```

int/double/char arrayname[100];

```

*int* or *double* or *char* are the comon prefixes that determine the boxes type, i.e. what can be stored in them. *arrayname* is whatever you want the line of boxes to be called. The *[100]* thing afterwards is how many things can be stored in the box. The first index (the nuber of the first box) is 0.

if you do

```

int boxes[100];
boxes[0] = 5;

```

You're setting the first index of arrayname to 5, i.e. you store 5 in the first box. To get whats in the first box, simply do:
```

int whatsinthefirstbox = boxes[0];

```

The best way to learn is to play around and use google basically :p

---

### Post by smartbei on 2008-04-18
Well, there is plenty of source out there. Here is a small example for a function that creates an array, and writes into it 0,1,2,3... and then prints it out.

[php]
#include <stdio.h>
#include <stdio.h>
void create_print_array(void)
{
	int numbers[20]; /* declare the array */
	int i = 0;
	
	/* set its values */
	for (i = 0; i < 20; i++) {
		numbers[i] = i;
	}
	
	/* print the values out. */
	for (i = 0; i < 20; i++) {
		printf("%d\n",numbers[i]);
	}
}

int main(void)
{
	create_print_array();
	return 0;
}
[/php]

---

### Post by VChief on 2008-04-18
> **CptPicard said:**
> ```

int arr[10];  // arr is array of 10 ints

arr[2] = 4;  // third one in array is 4 (counting from 0, remember)

arr[2]   // anywhere in your code will evaluate to 4

```

So..? :)

That part I got. I know, I'm not making it easy to get help. I attribute it to the extreme frustration. Here we go. This is what I'll do. I'm going to post what the assignment was. And I'm going to leave it at...I had no idea what I was doing. I just started writing, trying different things out. I read the chapters leading up to the assignment over and over and just never got how to put it into practice. Maybe I can get some hints about what I should of focused on first, etc...or just get a couple hints. Actually, I'd probably like that better then someone just writing it. I like that sense of accomplishment when I get something done. I really want to learn this and would like to be able to write it myself even though it's too late, just so I can learn.

> 

Create a menu driven program that loads the array, searches the array for a string, and prints the contents of the array. The array will contain strings that are 8 characters or less and there will be a total of five strings in the array. See the below. Use functions to display the menu, load the array, search the array and print the array. Be sure and pass the array to the load, search and print functions. Use the following array, data and menu.

Array: char animals [9][5];

Data: antelope, elephant, zebra, unicorn, buffalo

    MENU
1. Load array.
2. Search array.
3. Print array.
4. Quit.

Required functions:

int menu()
The menu function displays the menu, prompts the user to enter a number 1 thru 4 for their menu choice, checks to make sure the user entered a valid number between 1 and 4, if not prompts the user again to enter a number; when a valid number is entered returns the valid number or menu choice to main().

void loadarray(char panimals[][])
The load function loads the array with animal names entered by the user at the keyboard. The load function should check to make sure the user entered a string that is 8 characters or less before putting the animal name in the array.

void searcharray(char panimals[][])
The search function prompts the user to enter an animal name of eight characters, checks that the name entered is eight characters or less, then searches the animal array for the name.
If the animal name is found in the array it prints the name and location in the array. If not found in the array it prints The animal name and not found in array.

void printarray(char panimals[][])
The print functions prints a title, column headings, and the contents of the array. Format the output as follows:

    Animal Array
Location    Animal
      1         antelope
      2         elephant

---

### Post by VChief on 2008-04-18
> **smartbei said:**
> Well, there is plenty of source out there. Here is a small example for a function that creates an array, and writes into it 0,1,2,3... and then prints it out.

[php]
#include <stdio.h>
#include <stdio.h>
void create_print_array(void)
{
	int numbers[20]; /* declare the array */
	int i = 0;
	
	/* set its values */
	for (i = 0; i < 20; i++) {
		numbers[i] = i;
	}
	
	/* print the values out. */
	for (i = 0; i < 20; i++) {
		printf("%d\n",numbers[i]);
	}
}

int main(void)
{
	create_print_array();
	return 0;
}
[/php]

So, with

>  numbers[i] = i

The first "i" equals a slot in the array, correct, as if it were [0],[1], etc.? Then the second "i" would be the value going into that slot? I know, I probably sound stupid. I feel like I'm having problems with something that's supposed to be as simple as 1+1=2.

---

### Post by CptPicard on 2008-04-18
Correct... they're like numbered boxes really. Think of it like this -- if you wanted something like 10 integers, or maybe even an arbitrary number -- n integers -- you would have a really hard time creating yourself separate variables for them all... like int i_1, int i_2, int i_3... I am sure you can see that this won't do, and you won't even be able to do the "arbitrary number" part.

Besides, even if you DID create yourself ten separate integer variables from i_1... to i_10, iteration using a loop would be impossible. If you wanted to set every one of the variables, you'd have to do it separately by hand.. again, a complete pain. Having sequentially numbered "slots" is much more convenient...

---

### Post by smartbei on 2008-04-18
That is correct - In the statement inside the second loop there is only one i, which refers to the index of the number in the array. If the array was this (in pseudocode):
```

array = [10,20,30,40,50,60,70,80,90,100]

```
then array[0] would be 10, array[2] is 30 and array[9] is 100.

---

### Post by VChief on 2008-04-18
Ok. This was one of my first hangups, because I didn't understand it and gcc was throwing out errors about it, but then just stopped so something I else I did caused gcc to say it was OK. As i understand [i] = the amount of characters in the array, so [9] could hold up to 9 characters. What would the [5] do in this example? I looked through my book but never saw a declaration like this so wasn't sure what it does. The assignment also stated that the string could not have more than 8 letters. I wasn't sure if it had something to do with the array declaration. I was to extend my thanks to those who have already started helping me!

> char animals [9][5]

---

### Post by itix on 2008-04-18
Whoa, man!
You're doing dual indexed arrays.
If you've read mathematics, see it as vectors and matrixes. The "animals" array here is a 9 x 5 matix.... the 9 is the lenght, that's where you'll be storing the names of the animals. The 5 is the number of animals. If you do
```

char letter = animals [0] [0];

```

It will take the x position of this matrix
[X O O O O O O O O]
[O O O O O O O O O]
[O O O O O O O O O]
[O O O O O O O O O]
[O O O O O O O O O]

```

char letter2 = animals [2] [5];
```

will take the letter at position X in this matrix:

[O O O O O O O O O]
[O O O O O O O O O]
[O O O O O X O O O]
[O O O O O O O O O]
[O O O O O O O O O]

You have to think carefully about the fact that 0 is the first index.

---

### Post by smartbei on 2008-04-18
Actually, I believe animals[9][5] really means 9 arrays of length 5. Check this out:
```

#include <stdio.h>
int main(void)
{
	char test[9][5];
	printf("sizeof test: %d, sizeof test[]: %d", sizeof(test), sizeof(test[0]));	
	return 0;	
}

```
running it returns:
```

sizeof test: 45, sizeof test[]: 5

```
In this case it doesn't matter much, but I think what is really meant is test[5][9], meaning 5 arrays of length 9. It doesn't matter because it is allocated on the stack as one contiguous block of size 5*9, and the way you access it is irrelevant.

---

### Post by VChief on 2008-04-18
> **itix said:**
> Whoa, man!
You're doing dual indexed arrays.
If you've read mathematics, see it as vectors. The "animals" array here is a 9 x 5 vector.... the 9 is the lenght, that's where you'll be storing the names of the animals. The 5 is the number of animals. If you do
```

char letter = animals [0] [0];

```

It will take the x position of this vector
[X O O O O O O O O]
[O O O O O O O O O]
[O O O O O O O O O]
[O O O O O O O O O]
[O O O O O O O O O]

```

char letter2 = animals [2] [5];
```

will take the letter at position X in this vector:

[O O O O O O O O O]
[O O O O O O O O O]
[O O O O O X O O O]
[O O O O O O O O O]
[O O O O O O O O O]

You have to think carefully about the fact that 0 is the first index.


So, pretty much
```

 char animals[9][5] 

```
reserved 5 rows capable of holding 9 characters, each? See, I don't recall anything about dual indexing. Which is probably why I was confused by this at first.

---

### Post by itix on 2008-04-18
Probably why, yeah =p
Now all you have to do is enter your animals into the MATRIX (not vector, I'm stupid today... =/) and print them.

---

### Post by stratavarious on 2008-04-18
.

---

### Post by itix on 2008-04-18
I don't know what the limitation of ordinary C and C++ is, but C# has a limitations of 32 depths of indexing, meaning a 32 dimension matrix. It's a bit hard to visualize how to get a certain character out of a 32 dimension matrix, so I usually stick with 1, 2 and 3 dimnesional arrays =P

---

### Post by VChief on 2008-04-18
My next confusion came from 

```

void printarray(char panimals[][])

```

Why would it be panimals instead of animals? I assumed this was calling the array to the function. At first I thought it was a typo until I noticed it was in all of them. Also, what does the [][] do?

---

### Post by itix on 2008-04-18
No, no. You are supposed to write the function here (or implement as it is called).

write the funtion and then use the char array "*paminals*" (it's named that way to not be mixed up *animals*, even though it was a strange name to choose) in the funcion.

The reason why it's called "panimals" and why it has empty brackets is because it's a general formula for those who are going to use the function.
it says: when calling this function; please enter a *char* array with *dual indexes* that you may call whatever you want. You could have called it *pink_elephant [][]* too if you want to.

When wanting to use the array that someone according to your general formula inserted in your function, just use *panimals [] []*. It *"becomes"* the char array that someone entered into your function.

Presume now that your function is written and I find your utterly useful code and decides to use your function, i just call it with
```

char itix_matrix [20] [20];

//code to assign values to itix matrix

leewards_function(itix_matrix);

```

then itix_matrix *"becomes"* panimals [] [] or pink_elephant [] [] or whatever you defined when you wrote the function.

and your function hopefully prints my values correctly =p

---

### Post by VChief on 2008-04-18
> **itix said:**
> No, no. You are supposed to write the function here (or implement as it is called).

write the funtion and then use the char array "*paminals*" (it's named that way to not be mixed up *animals*, even though it was a strange name to choose) in the funcion.

The reason why it's called "panimals" and why it has empty brackets is because it's a general formula for those who are going to use the function.
it says: when calling this function; please enter a *char* array with *dual indexes* that you may call whatever you want. You could have called it *pink_elephant [][]* too if you want to.

When wanting to use the array that someone according to your general formula inserted in your function, just use *panimals [] []*. It *"becomes"* the char array that someone entered into your function.

Presume now that your function is written and I find your utterly useful code and decides to use your function, i just call it with
```

char itix_matrix [20] [20];

//code to assign values to itix matrix

leewards_function(itix_matrix);

```

then itix_matrix *"becomes"* panimals [] [] or pink_elephant [] [] or whatever you defined when you wrote the function.

and your function hopefully prints my values correctly =p

Ok. Thank you! I have a little bit more info to go back and re-look at this. That panimal stuff was a big confusion point for me. I thank ya'll for everything you've thrown my way. If you have any other ideas that will help me with understanding arrays and how to do this, please let me know.

---

### Post by VChief on 2008-04-18
> **stratavarious said:**
> Here's a helpful link about the arrays



Look at the first part of the tutorial

[http://www.tenouk.com/clabworksheet/labworksheet10.html]("http://www.tenouk.com/clabworksheet/labworksheet10.html")

Thank you! I'm going to go take a look at it right now.

---

