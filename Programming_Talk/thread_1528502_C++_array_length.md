---
title: "C++ array length"
date: 2010-07-10
forum: Programming Talk
---

### Post by l3ecl on 2010-07-10
Well why would you limit  your array to a specified amount of characters? For instance why would  you write:
  char string[7] = "abc123";
 when you could write:
  char string[] = "abc123";
 in the second example you don't have to worry about how many  characters your text string is - it just seem simpler.  However, I would  imagine there is a reason why you would want to code like the first  example I just don't know what that reason is. Could someone please kindly explain.

---

### Post by schauerlich on 2010-07-10
In this example you're using C arrays. C arrays are nothing more than a chunk of contiguous memory, and that memory must be allocated to your program. You have  specify how much memory you want, ie how long you want your array to be. if you're used to something like python with dynamically resizing lists, that uses some dynamic allocation which is probably above your level right now. If you want to look into it more, google malloc.

If you want a container that is very similar to a C array, but which automatically resizes itself when necessary, look into std::vector.

EDIT: also, your two examples are NOT the same. The first makes a char array (as in, both the pointer and the memory it's pointing to) on the stack which is initialized to that string, whereas the second makes a char *pointer* on the stack, which points to a readonly part of memory that contains the string you specify. (2nd edit, I was confusing char *string and char string[], see edit in post #4)

---

### Post by l3ecl on 2010-07-10
I still don't get why any1 would put a value between the two brackets: [ ], because it just seems simpler NOT to. 

also are you sure string[] (as opposed to string[7]) is put into a read only part of the memory? because the variables aren't acting like constants as i was able to edit them:
```

char string[] = "hello reddit";
cout << string << endl;
char *ptr = string;
*ptr = 'H';
ptr = ptr+1;
*ptr = 'E';
ptr = ptr+1;
*ptr = 'L';
ptr = ptr+1;
*ptr = 'L';
ptr = ptr+1;
*ptr = 'O';

cout << string << endl;


```1st cout: "hello reddit"
after modifcation
2nd cout: "HELLO reddit"

---

### Post by schauerlich on 2010-07-10
It's possible I'm wrong about the readonly part, I'm not entirely sure. Anyways, the reason someone might want to specify a length is if they want the char array to be longer than the string that they start it off with, because they plan on changing it.

EDIT: my confusion with the readonly thing is that char *string and char string[] are not equivalent. The first makes a pointer to a readonly string (try it - the program will crash) and the second will work.

---

### Post by lisati on 2010-07-10
The use of the two forms is very different. 

Assuming you're not using dynamically allocated memory, where you can have some freedom resizing:

The first situation is when you anticipate changing the contents of the array as part of the normal running of the program, and you need to make sure that sufficient room for the longest/largest possible value your program is likely to encounter is available.

The second is when the contents of the array is unlikely to change. The compiler can set aside "just enough" according to the values it knows about.

---

### Post by schauerlich on 2010-07-10
> **lisati said:**
> The use of the two forms is very different. 

Assuming you're not using dynamically allocated memory, where you can have some freedom resizing:

The first situation is when you anticipate changing the contents of the array as part of the normal running of the program, and you need to make sure that sufficient room for the longest/largest possible value your program is likely to encounter is available.

The second is when the contents of the array is unlikely to change. The compiler can set aside "just enough" according to the values it knows about.

+1, sorry for any confusion I may have caused. :)

---

