---
title: "able to work with array in spite of not malloc'ing enough memory"
date: 2014-10-23
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-23
Hello,
 I have defined an array using pointers. Say, I want to have 200 elements in the array; I have just malloc'ed one integer's size, and yet, I'm able to populate and access array elements without any problems. Please see the code below.

```

#include <stdio.h>
#include <malloc.h>


int i = 0;


int main(void)
{
 int* a;

 //Shouldn't it be **a = malloc(200 * sizeof(int)); ?**
 a = malloc(sizeof(int));


 for(i=0;i<200;i++)
 {
  *(a+i) = i+1;
 }


 print(a);


 return 0;
}


int print(int* a)
{
 for(i=0;i<200;i++)
  printf("%d ",*(a+i));
}

_Output_
IAMTubby@IAMTubby-Inspiron-3542:~$ ./a.out 
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99 100 101 102 103 104 105 106 107 108 109 110 111 112 113 114 115 116 117 118 119 120 121 122 123 124 125 126 127 128 129 130 131 132 133 134 135 136 137 138 139 140 141 142 143 144 145 146 147 148 149 150 151 152 153 154 155 156 157 158 159 160 161 162 163 164 165 166 167 168 169 170 171 172 173 174 175 176 177 178 179 180 181 182 183 184 185 186 187 188 189 190 191 192 193 194 195 196 197 198 199 200 


```

---

### Post by Rocket2DMn on 2014-10-23
That's just you getting lucky.  The system may allocate more space to your program than it is actually using, so as long as the address you're accessing is within that space, you won't get a segmentation fault.  Try increasing the 200 to something like 20000000.  It will probably fail.

Alternatively, try declaring and using another variable and see how the output of "a" gets screwed up:
```

#include <stdio.h>
#include <malloc.h>


int i = 0;


int main(void)
{
 int* a;

 //Shouldn't it be a = malloc(200 * sizeof(int)); ?
 a = malloc(sizeof(int));


 for(i=0;i<200;i++)
 {
  *(a+i) = i+1;
 }

 int* b;
 b = malloc(sizeof(int));
 for(i=0;i<200;i++)
 {
  *(b+i) = i+1;
 }


 print(a);
 printf("\n");
 print(b);

 return 0;
}


int print(int* a)
{
 for(i=0;i<200;i++)
  printf("%d ",*(a+i));
}

```

---

### Post by Steven_Williams on 2014-10-24
What you are running into is undefined behavior. [http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html#](http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html#) This articles explains a bit about it. As has been said you are "getting lucky". It will come back to bite you if you use that technique on a larger program or a different platform (Fedora, Windows, OS X). The proper way to malloc is just as you have it in your comments. I prefer using calloc myself as that helps enforce that usage and it initializes my memory to 0 so that my functions can detect objects that don't have data.

I noticed you are trying to learn C by experimenting with what you can and cannot get away with. The problem with this approach is there are areas of C that are implementation dependent. You could have perfectly good code that works on Ubuntu, but the moment you try to compile it on OS X or Windows it just breaks to pieces. You need to be familiar with what the standard enforces and does not enforce. This article explains this idea a bit more: [http://goo.gl/tCSoXk](http://goo.gl/tCSoXk)

---

### Post by IAMTubby on 2014-10-24
> **Rocket2DMn said:**
> That's just you getting lucky.  The system may allocate more space to your program than it is actually using, so as long as the address you're accessing is within that space, you won't get a segmentation fault.  Try increasing the 200 to something like 20000000.  It will probably fail.

Alternatively, try declaring and using another variable and see how the output of "a" gets screwed up:
```

#include <stdio.h>
#include <malloc.h>


int i = 0;


int main(void)
{
 int* a;

 //Shouldn't it be a = malloc(200 * sizeof(int)); ?
 a = malloc(sizeof(int));


 for(i=0;i<200;i++)
 {
  *(a+i) = i+1;
 }

[b]
 int* b;
 b = malloc(sizeof(int));
 for(i=0;i<200;i++)
 {
  *(b+i) = i+1;
 }
[/b]

 print(a);
 printf("\n");
** print(b);**

 return 0;
}


int print(int* a)
{
 for(i=0;i<200;i++)
  printf("%d ",*(a+i));
}

```
Thanks for the example Rocket2DMn.
Yes, I ran the program and see a's output getting disturbed? But how's that even happening ? We're not doing anything to a :):confused:

---

### Post by IAMTubby on 2014-10-25
> **Steven_Williams said:**
> you are "getting lucky". It will come back to bite you if you use that technique on a larger program or a different platform (Fedora, Windows, OS X). The proper way to malloc is just as you have it in your comments. 
Thanks Steven_Williams

> I prefer using calloc myself as that helps enforce that usage and it initializes my memory to 0 so that my functions can detect objects that don't have data.
Since, we have touched upon the topic, let me ask you this question, I've been thinking about.
Say, I want to have an array of 10 integers, so when I do
```

int* a;
a = malloc(**10 * sizeof(int)**);

```
Does this allocate me 1 block of 40 bytes? or 10 blocks of 4 bytes each?
_If the former_, then how am I able to traverse through an array like for(i=0;i<10;i++)printf("%d ",*(a+i)) ?
_If the latter, _ who takes care of making 10 chunks of 4 bytes each? I tried thinking and find it highly unlikely that it's going to be done by a syntax which is separated by '*'. I mean when I think of it, malloc would be a function which takes in one argument, and irrespective of how you pass it, 10*4 or 40, it should be the same once it is received by the function?
I don't know, just thinking loud here. Please advise.

> 
I noticed you are trying to learn C by experimenting with what you can and cannot get away with. The problem with this approach is there are areas of C that are implementation dependent. You could have perfectly good code that works on Ubuntu, but the moment you try to compile it on OS X or Windows it just breaks to pieces. You need to be familiar with what the standard enforces and does not enforce. This article explains this idea a bit more: [http://goo.gl/tCSoXk](http://goo.gl/tCSoXk)
Thanks Steven

---

### Post by ofnuts on 2014-10-25
> **IAMTubby said:**
> Say, I want to have an array of 10 integers, so when I do
```

int* a;
a = malloc(**10 * sizeof(int)**);

```
Does this allocate me 1 block of 40 bytes? or 10 blocks of 4 bytes each?
_If the former_, then how am I able to traverse through an array like for(i=0;i<10;i++)printf("%d ",*(a+i)) ?
_If the latter, _ who takes care of making 10 chunks of 4 bytes each? I tried thinking and find it highly unlikely that it's going to be done by a syntax which is separated by '*'. I mean when I think of it, malloc would be a function which takes in one argument, and irrespective of how you pass it, 10*4 or 40, it should be the same once it is received by the function?


[LIST]
[*]One block of 40 bytes.
[*]As you said or using [FONT=courier new]printf("%d ",a[i])[/FONT] that will work just as well. This is the baic principle of arrays in memory. Elements are contiguous, if you have the address of one element, then the next in the array is at address+element_size. The difference between pointers and addresses is that pointers have an implicit size associated to them, so the next element is always at pointer+1.
[*]It cannot be 10 chunks, since it returns only one address... how would you know where the 9 other chunks have been allocated?
[/LIST]

---

### Post by IAMTubby on 2014-10-25
> **ofnuts said:**
> 
[LIST]
[*]One block of 40 bytes.
[*]As you said or using [FONT=courier new]printf("%d ",a[i])[/FONT] that will work just as well. This is the baic principle of arrays in memory. Elements are contiguous, if you have the address of one element, then the next in the array is at address+element_size. The difference between pointers and addresses is that pointers have an implicit size associated to them, so the next element is always at pointer+1.
[*]It cannot be 10 chunks, since it returns only one address... how would you know where the 9 other chunks have been allocated?
[/LIST]

Thanks a lot ofnuts.
_Just to have a final word, so when I do a malloc(200) say, these things happen? Please let me know what you think of it_
 1. It allocates one block of 200 bytes which is actually 200/sizeof(void*) **contiguous sub blocks** each of sizeof(void*) bytes
 2. It's not confusing for malloc irrespective of whether it is int*  a = malloc(200) or float*  a = malloc(200) or char*  a = malloc(200) because all pointers have the same size, let's say sizeof(void*).
 3. And then it returns the starting address of all these sub blocks so the rest of the 49 sub blocks(200/4) can be traversed using pointer arithmetic.
Note : Introduction of term 'sub-blocks' just for understanding purpose, because I want to visualize it as individual contiguous array elements instead of one huge chunk. Only when I visualize it as 50 sub-blocks,do I get the feel that they can be traversed individually.
 
And can I also conclude saying that always allocate as much memory as the number of array elements you plan to have, (instead of getting lucky). So if you plan to have an array of 100 integers, always do
```

int* a;
a = malloc(100 * sizeof(int));
//This would allocate 400 bytes, ie one hundred 4-byte contiguous blocks and return the address of the first of those 100 blocks.

```

---

### Post by trent.josephsen on 2014-10-25
> **IAMTubby said:**
> Just to have a final word, so when I do a malloc(200) say, these things happen
 1. It allocates 200/sizeof(void*) **contiguous blocks** each of sizeof(void*) bytes
In the C model, memory is flat. When you call malloc(200), it does nothing more nor less than reserve two hundred bytes in **one contiguous block**. What you do with those bytes is your concern. If you want to treat them as an array-of-int, you can do that using pointer arithmetic and a pointer-to-int. If you want to treat them as an array-of-char, you can do that using the same pointer arithmetic and a pointer-to-char. If you first treat it as an array of char, and then change your mind and want to store ints in it, you can do that too. Memory is flat; there's no "sub-blocks", nothing about that 200-byte block says "this is divided into 50 blocks of 4 bytes" or "25 blocks of 8 bytes" or whatever. It's just bytes.

>  2. It's not confusing for malloc irrespective of whether it is int*  a = malloc(200) or float*  a = malloc(200) or char*  a = malloc(200) because all pointers have the same size, let's say sizeof(void*).
sizeof(void*) is the size of a pointer-to-void, and has nothing to do with it. The result of sizeof is in units of bytes (which is to say, chars, because [by definition sizeof(char) == 1]("http://c-faq.com/malloc/sizeofchar.html")). Yes, malloc() does the same thing no matter what kind of pointer you end up using.

>  3. And then it returns the starting address of all these blocks so the rest of the 49 blocks(200/4) can be traversed using pointer arithmetic.
Yep.
 
> And can also conclude saying that always allocate as much memory as the number of array elements you plan to have, (instead of getting lucky). So if you plan to have an array of 100 integers, always do
```

int* a;
a = malloc(100 * sizeof(int));
//This would allocate 400 bytes, ie one hundred 4-byte contiguous blocks and return the address of the first of those 100 blocks.

```

Yep again. But a slightly preferable version, in most cases, would be
```
a = malloc(100 * sizeof *a);
```
This way, you only say "int" in one place, so if a's type ever needs to change, the malloc() remains correct. [Also see.](http://c-faq.com/malloc/noscale.html)

---

### Post by ofnuts on 2014-10-25
> **IAMTubby said:**
> Thanks a lot ofnuts.
_Just to have a final word, so when I do a malloc(200) say, these things happen? Please let me know what you think of it_
 1. It allocates one block of 200 bytes which is actually 200/sizeof(void*) **contiguous sub blocks** each of sizeof(void*) bytes
 2. It's not confusing for malloc irrespective of whether it is int*  a = malloc(200) or float*  a = malloc(200) or char*  a = malloc(200) because all pointers have the same size, let's say sizeof(void*).
 3. And then it returns the starting address of all these sub blocks so the rest of the 49 sub blocks(200/4) can be traversed using pointer arithmetic.
Note : Introduction of term 'sub-blocks' just for understanding purpose, because I want to visualize it as individual contiguous array elements instead of one huge chunk. Only when I visualize it as 50 sub-blocks,do I get the feel that they can be traversed individually.
 
And can I also conclude saying that always allocate as much memory as the number of array elements you plan to have, (instead of getting lucky). So if you plan to have an array of 100 integers, always do
```

int* a;
a = malloc(100 * sizeof(int));
//This would allocate 400 bytes, ie one hundred 4-byte contiguous blocks and return the address of the first of those 100 blocks.

```
[LIST=1]
[*]No, just one block of 200 bytes, period. You can then use it as you wish, including considering it as sub-blocks.
[*]Yes, pointers have the same size (but there may be CPU architectures where pointer sizes differ(*), so beware, unless it's mandated in the fine print of the C specification)
[*]Yes.
[/LIST]
 
(*) especially if you consider pointer to functions, that could be in a different storage

---

### Post by IAMTubby on 2014-10-25
> **ofnuts said:**
> 
[LIST=1]
[*]No, just one block of 200 bytes, period. You can then use it as you wish, including considering it as sub-blocks.
[/LIST]
ok ofnuts, I get it.
So it's just one chunk of 200 bytes
I only had a problem because as soon as I do a malloc and run a for loop to print out addresses as follows,
```

int* ptr;
ptr = malloc(200);
for(i=0;i<10;i++)
 printf("%p ",ptr+i); 
```
it would give me correct addresses(by correct I mean, ptr+i is 4 bytes from ptr). So I thought that it was divided into sub-blocks. _But this advancing to the next 4 bytes is actually done by the pointer arithmetic of **int*** ptr It has nothing to do with the memory which is just one chunk._
This fits in well with what you tried to convey when you said,[Once the memory is malloc'ed,]"You can then use it as you wish"

_*Thinking again, and getting more clarity*_
Had there been some pointer type which takes 3 bytes of memory, ptr+1 would have been 3 bytes past ptr. But that doesn't mean that the 200 bytes of memory is now divided into 3-byte sub-blocks.

Thanks once again.

---

### Post by IAMTubby on 2014-10-26
> **trent.josephsen said:**
> In the C model, memory is flat. When you call malloc(200), it does nothing more nor less than reserve two hundred bytes in **one contiguous block**. What you do with those bytes is your concern. If you want to treat them as an array-of-int, you can do that using pointer arithmetic and a pointer-to-int. If you want to treat them as an array-of-char, you can do that using the same pointer arithmetic and a pointer-to-char. If you first treat it as an array of char, and then change your mind and want to store ints in it, you can do that too. Memory is flat; there's no "sub-blocks", nothing about that 200-byte block says "this is divided into 50 blocks of 4 bytes" or "25 blocks of 8 bytes" or whatever. It's just bytes.


sizeof(void*) is the size of a pointer-to-void, and has nothing to do with it. The result of sizeof is in units of bytes (which is to say, chars, because [by definition sizeof(char) == 1]("http://c-faq.com/malloc/sizeofchar.html")). Yes, malloc() does the same thing no matter what kind of pointer you end up using.


Yep.
 


Yep again. But a slightly preferable version, in most cases, would be
```
a = malloc(100 * sizeof *a);
```
This way, you only say "int" in one place, so if a's type ever needs to change, the malloc() remains correct. [Also see.]("http://c-faq.com/malloc/noscale.html")
trent.josephsen, I'm sorry I just saw this reply now when I came back to the thread to re-read.
Thank you so much, yes the explanation is very clear.

---

### Post by IAMTubby on 2014-11-01
> **Rocket2DMn said:**
> That's just you getting lucky.  The system may allocate more space to your program than it is actually using, so as long as the address you're accessing is within that space, you won't get a segmentation fault.  Try increasing the 200 to something like 20000000.  It will probably fail.
> **Steven_Williams said:**
> What you are running into is undefined behavior. [http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html#](http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html#) This articles explains a bit about it. As has been said you are "getting lucky". It will come back to bite you if you use that technique on a larger program or a different platform (Fedora, Windows, OS X). The proper way to malloc is just as you have it in your comments.
Rocket2DMn, Steven_Williams
I'm sorry to dig up this thread but just wanted a confirmation if this is the standard people follow for copying a string dynamically. Say I have a string, and I want to copy to another string but this time, by dynamically allocating memory
Please see the code below. **Is this correct? I do strlen(str)+1 because I feel it should have space for all of the contents of str, plus one for the '\0' at the end**

```
#include <stdio.h>#include <malloc.h>
#include <string.h>


int main(void)
{
 char str[100];
 char* str1;


 gets(str);

**//Is this correct? I do strlen(str)+1 because I feel it should have space for all of the contents of str, plus one for the '\0' at the end**
 str1 = malloc(**(strlen(str)+1)***sizeof(char));


 strcpy(str1,str);


 printf("length == [%ld]\n",strlen(str));
 printf("str1 == [%s]\n",str1);
}

```

Again, the code also works if I do, str1 = malloc(**1**); **Is this just getting lucky again?**

Thanks.

---

### Post by ofnuts on 2014-11-02
Yes, you need strlen()+1 bytes, and yes, if you do malloc(1) and it works you are lucky. In practice, the memory allocator could have a minimum allocation size (if you ask for 5 you'll likely get 16...) but trying your luck when programming is never a good idea, miracles aren't permanent.

In the case at hand you can also use the more concise:
```

str1=strdup(str);

```

because strdup() will malloc() the necessary space for you (so remember to free(str1) later). 

Using gets() is dangerous (if the user enters more that 100 characters there will be a buffer overrun). Use fgets() instead.

PS: a quick test indicates that the allocator gives you 24+n*32 bytes.

---

### Post by IAMTubby on 2014-11-02
> **ofnuts said:**
> Yes, you need strlen()+1 bytes, and yes, if you do malloc(1) and it works you are lucky. In practice, the memory allocator could have a minimum allocation size (if you ask for 5 you'll likely get 16...) but trying your luck when programming is never a good idea, miracles aren't permanent.]
Thanks ofnuts.

> 
strdup() will malloc() the necessary space for you (so remember to free(str1) later). 
Thanks ofnuts, never knew of that

> 
Using gets() is dangerous (if the user enters more that 100 characters there will be a buffer overrun). Use fgets() instead.
Thanks ofnuts, I've been told this several times, but I just keep putting it off because I always get gets to work. It's high time I start using fgets.
_But, the only reason I dislike using fgets is because_
1. The syntax is longer by a couple of arguments. That's fine.
2. And more importantly, the newline it adds at the end. Is there any way to counter this without writing your own code, like an fgets option for no newline or something? The number of google results relevant to this is actually amazing. But I did not find a solution in those pages.

> PS: a quick test indicates that the allocator gives you 24+n*32 bytes.
Wow, that's nice to have a formula like that. But what is n? the number of bytes I allocate? So, if i do malloc(2), do I get 24+32*2 == 88 bytes?

---

### Post by Steven_Williams on 2014-11-02
You could just use strstr to find where the newline occurs and just replace that with null. Also you could write your own gets type function that does not grab newline characters, but I think just finding and replacing will work better for you.

---

### Post by Rocket2DMn on 2014-11-02
strdup is a nice function to use, but be aware that it is a POSIX defined function, not part of the C standard.  You are also responsible for freeing the pointer later, just as if you used malloc yourself.

In the future, please start a new thread for different questions.

---

### Post by ofnuts on 2014-11-02
> **IAMTubby said:**
> Thanks ofnuts.


Thanks ofnuts, never knew of that


Thanks ofnuts, I've been told this several times, but I just keep putting it off because I always get gets to work. It's high time I start using fgets.
_But, the only reason I dislike using fgets is because_
1. The syntax is longer by a couple of arguments. That's fine.
2. And more importantly, the newline it adds at the end. Is there any way to counter this without writing your own code, like an fgets option for no newline or something? The number of google results relevant to this is actually amazing. But I did not find a solution in those pages.


Wow, that's nice to have a formula like that. But what is n? the number of bytes I allocate? So, if i do malloc(2), do I get 24+32*2 == 88 bytes?[B]

gets()/fgets()[/B]: nothing prevents you from writing your own function around fgets(). Such a function can for instance concatenate the contents of several buffers until it sees a LF (which is the only sure-fire way to handle indefinitely long input lines)(not speaking of handling CR characters if the files have a DOS/Windows origin). Otherwise for simpler stuff removing the LF is easy since if it is present is will be the last character (buffer|strlen(buffer)-1]) so you can test for its presence and replace it with '\0'.[B] 

24+n*32[/B]: what this means is that you will get the smallest of either 24, 56, 88, 120, 152, 184, 216... that fits your request. But of course other implementations could follow different rules so don't count on this. This however shows that if you allocate very many small strings you can end up wasting a some memory (16 bytes/allocation on average) (but you aren't yet where you should start to worry about this).

---

### Post by trent.josephsen on 2014-11-02
> **IAMTubby said:**
> _But, the only reason I dislike using fgets is because_
1. The syntax is longer by a couple of arguments. That's fine.
2. And more importantly, the newline it adds at the end. Is there any way to counter this without writing your own code, like an fgets option for no newline or something? The number of google results relevant to this is actually amazing. But I did not find a solution in those pages.
Not without writing your own code (or borrowing someone else's), no. But the amount of extra code-writing is trivial. Here's a function I use sometimes (borrowed from Perl):
```
int chomp(char *s) {
    if (s == NULL) {
        return 0;
    }
    while (*s) {
        if (*s == '\n') {
            *s = 0;
            return 1;
        }
        ++s;
    }
    return 0;
}
```

You can use it like chomp(fgets(...)), and it returns 1 if it removed a newline, 0 otherwise. Careful, it traverses the whole string, so if you're reading many long lines it might become slow. You still have to check for EOF or error because it doesn't indicate whether the pointer is NULL.

POSIX specifies getline(), so if you're willing to go outside of standard C, you can use that instead of fgets(). You'll still have to erase the delimiter yourself, though.

What are you doing with these strings? I find that if I write my input code robustly, I rarely care about trailing newlines. Normally what I do with the result of fgets() is one of the following:
1_ Use strtok() to break it into several smaller strings. This works for CSV files, for instance. Just adding "\n" to the delimiter string fixes the newline "problem".
2_ Use sscanf() to read fields from it. This method is somewhat more flexible in the formats it can accept, but only when you know the format in advance. Except for %c, all the scanf formats skip whitespace, including newlines.
3_ Pick it apart and deal with each character in a loop. In this case you generally want to break the loop when you hit a newline, or just skip it, both of which are easy to put in. And if your parsing functions are to be robust they ought to know how to handle newlines anyway.

I only use chomp() when I'm going to use the whole line verbatim *except for the newline*, which is unusual.

There is **no reason** for using gets(). It's been deprecated since forever ago and C11 actually *removes it from the library* because there is simply no way to use it safely. Don't be tempted by the convenience.

---

