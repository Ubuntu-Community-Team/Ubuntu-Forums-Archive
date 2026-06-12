---
title: "Segmentation Fault when not using \n(new line)"
date: 2010-09-22
forum: Programming Talk
---

### Post by hemantparmar on 2010-09-22
helloo friends ...
I was writing a program for hw a turing machine works to reverse a string consisting of a and b only but the main problem was that 
the program works fine if i give a "\n" (new line) operator in each of the printf() function but if I don't give one it gives a segmentation fault just at that printf() function only .....can somebody plz explain what exactly is going on in there ......

---

### Post by Some Penguin on 2010-09-22
What's wrong is that you seem to be expecting people to be able to notice problems in code that they can't see.

---

### Post by hemantparmar on 2010-09-22
i m posting my code thanx 4 replying ....actually its not the full program its in some other notebook ...
```

#include<stdio.h>
void palendrom(void);
void copy(void);
void reverse(void);
void replace(void);
void traverse(void);
void function1(void);
void function2(void);
int ptr;
char string[200];
main()
{
    int n;
    while (1)
    {
        printf("\tpress 1 to check for palendrom\n \tpress 2 to replace \n \tpress 3  for reverse \n\tpress 4 to for copy\n");
        scanf("%d",&n);
        switch (n)
        {
        case 1:
            palendrom();
            break;
        case 4:
            copy();
            break;
        case 3:
            reverse1();
            break;
        case 2:
            replace();
            break;
        }
    }
}
palendrom()
{

    //char string[200];
    memset(string,'\0',sizeof(string));
    int i,ch;
    printf("please enter the string");
    __fpurge(stdin);
    fgets(string,200,stdin);
    printf("%s",string);

    for (i=0;i<200;i++)
    {
        ch=string[i];
        if (string[i]=='\n')
        {
            string[i]='\0';
        }
        //    printf("%d\t",ch);
        if (string[i]=='a'||string[i]=='b'||string[i]=='\0')
        {
            ch=string[i];
//        printf("%d\t",ch);
            continue;
        }
        else
        {
            ch=string[i];
            printf("\n INVALID INPUT PLEASE ENTER THE CORRECT STRING");
            break;
        }
    }
    ptr=0;
    while (1)
    {
        switch (string[ptr])
        {
        case 'a':
        {
            function1();
            printf("chutiya");
            traverse();
            ptr=ptr-1;
            if (string[ptr]=='a')
            {
                function1();
                printf("\n chutiya");
                reverse();
            }
            else
            {
                printf("NOT A PALENDROM");
                exit(1);
            }
        }
        break;
        case 'b':
            function2();
            traverse();
            ptr=ptr-1;
            if (string[ptr]=='b')
            {
                function2();
                reverse();
            }
            else
            {
                printf("NOT A palendrom");
                exit(1);
            }
            break;

        case 'x':
            printf("THE GIVEN STRING IS A PALENDROM");

        case 'y':
            printf("THE GIVEN STRING IS A PALENDROM");
        }

    }
}
copy()
{

    printf("please enter the string");
    __fpurge(stdin);
    fgets(string,200,stdin);
    printf("%s",string);
}
reverse1()
{

    printf("please enter the string");
    __fpurge(stdin);
    fgets(string,200,stdin);
    printf("%s",string);
}
replace()
{
    char b[200];
    printf("please enter the string");
    __fpurge(stdin);
    fgets(string,200,stdin);
    printf("please enter the  other string");
    __fpurge(stdin);
    fgets(b,200,stdin);
    printf("%s",string);
    printf("%s",b);
}

traverse()
{
    printf("traverse me %d",ptr);
    printf("\ni m  traverse\n");
    //int t;
    // t=ptr+1;
    printf("%d",ptr);
    if (string[ptr+1]=='x'||string[ptr+1]=='y')
    {
        printf("THE GIVEN STRING IS A PALENDROM");
        exit(1);
    }
    printf("hiiiiiiiiiii");
    while (string[ptr]!='\n'||string[ptr]!='x'||string[ptr]!='y')
    {
        ptr++;
        //printf("%d%d",ptr,t);
    }
    printf("%d",ptr);
}
reverse()
{
    printf("i am reverse");
    while (string[ptr]!='\0'||string[ptr]!='x'||string[ptr]!='y')
    {
        ptr=ptr-1;
    }
    ptr=ptr+1;
}
function2()
{
    string[ptr]='y';
}

function1()
{
    printf("\ni am function1\n");
    string[ptr]='x';
    printf("\nfunction1 me %d\n",ptr);
}


```
If i don't use \n in each of the printf() functions then it gives a segmentation fault plz help /......

---

### Post by lisati on 2010-09-22
I've added [noparse]```
 and 
```[/noparse] tags to the source. It can help make it easier for us to read.

---

### Post by dwhitney67 on 2010-09-22
> **hemantparmar said:**
> helloo friends ...
I was writing a program for hw a turing machine works to reverse a string consisting of a and b only but the main problem was that 
the program works fine if i give a "\n" (new line) operator in each of the printf() function but if I don't give one it gives a segmentation fault just at that printf() function only .....can somebody plz explain what exactly is going on in there ......

Try to whittle down your code so that you are only fulfilling one requirement at a time.  It seems the program does multiple things; implement one successfully, test it, and then move onto the next requirement.

As for the code itself, what you have is "spaghetti" code.  Modularize the code a little better so that you don't perform multiple "functions" within a function.

For example, see if the following makes sense:
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>


void  getInput(const char* prompt, char* buf, const int buf_size);
int   isValidInput(const char* input);
int   palindrome(const char* str);
char* replace(const char* str, const char* substring, const char* replaceStr);
void  reverse(char* str);
char* copy(const char* str);


int main()
{
   int         done = 0;
   const char* prompt = "\n\nMenu:\n\n"
                        "\ta. Check if word is a palindrome.\n"
                        "\tb. Replace substring within a string.\n"
                        "\tc. Reverse a string.\n"
                        "\td. Copy a string.\n"
                        "\tq. Quit.\n\n"
                        "Choice? ";

   while (!done)
   {
      char input1[200] = {0};
      char input2[200] = {0};
      char input3[200] = {0};

      getInput(prompt, input1, 2);

      if (!isValidInput(input1))
      {
         printf("Invalid input; please try again...\n\n");
         continue;
      }

      switch (input1[0])
      {
         case 'a':
             getInput("Enter a string: ", input1, sizeof(input1));
             printf("%s is %s a palindrome.\n", input1, (palindrome(input1) ? "" : "NOT"));
             break;

         case 'b':
             getInput("Enter a string: ", input1, sizeof(input1));
             getInput("Enter substring to replace: ", input2, sizeof(input2));
             getInput("Enter replacement substring: ", input3, sizeof(input3));
             char* newStr = replace(input1, input2, input3);
             printf("New string is %s\n", newStr);
             free(newStr);
             break;

         case 'c':
             getInput("Enter a string: ", input1, sizeof(input1));
             reverse(input1);
             printf("Reversed string is: %s\n", input1);
             break;

         case 'd':
             getInput("Enter a string: ", input1, sizeof(input1));
             char* copiedStr = copy(input1);
             printf("Copied %s.\n", copiedStr);
             free(copiedStr);
             break;

         case 'q':
             done = 1;
             break;
      }
   }

   return 0;
}

void getInput(const char* prompt, char* buf, const int buf_size)
{
   char* newline = 0;

   printf("%s", prompt);
   fgets(buf, buf_size, stdin);

   newline = strchr(buf, '\n');

   if (newline)
   {
      /* replace new line character with a null */
      *newline = '\0';
   }
   else
   {
      /* flush stdin */
      while (getchar() != '\n');
   }
}

int isValidInput(const char* input)
{
   const char c = input[0];

   return (c == 'a' || c == 'b' || c == 'c' || c == 'd' || c == 'q');
}

int palindrome(const char* str)
{
   // determine if the given string is a palindrome; return 1 if so,
   // 0 otherwise.
   return 0;
}

char* replace(const char* str, const char* substring, const char* replaceStr)
{
   // allocate a new string that is a morph of the original
   // string, where the substring has been replaced with a new
   // substring.
   return 0;
}

void reverse(char* str)
{
   // reverse the given string
}

char* copy(const char* str)
{
   // return an allocated copy of the given string.
   return 0;
}

```
I'll leave the individual functions for your to implement.  Remember, just work on one at a time, and test as you go along.

---

### Post by trent.josephsen on 2010-09-23
Agreed with dwhitney; the code is so scattered that it's next to impossible to troubleshoot.  Think about how you want to divide the main task into subtasks before creating functions right and left.

Now, that said, asking gcc for warnings will tell you that you have quite a few problems.  It is a good practice to review any warnings your compiler can give you before asking for public code review.

```
% gcc -W -Wall -std=c99 -pedantic palen.c
palen.c:11:1: warning: return type defaults to ‘int’
palen.c: In function ‘main’:
palen.c:27:13: warning: implicit declaration of function ‘reverse1’
palen.c: At top level:
palen.c:35:1: warning: return type defaults to ‘int’
palen.c:35:1: warning: conflicting types for ‘palendrom’
palen.c:2:6: note: previous declaration of ‘palendrom’ was here
palen.c: In function ‘palendrom’:
palen.c:39:5: warning: implicit declaration of function ‘memset’
palen.c:39:5: warning: incompatible implicit declaration of built-in function ‘memset’
palen.c:42:5: warning: implicit declaration of function ‘__fpurge’
palen.c:87:17: warning: implicit declaration of function ‘exit’
palen.c:87:17: warning: incompatible implicit declaration of built-in function ‘exit’
palen.c:103:17: warning: incompatible implicit declaration of built-in function ‘exit’
palen.c: At top level:
palen.c:116:1: warning: return type defaults to ‘int’
palen.c:116:1: warning: conflicting types for ‘copy’
palen.c:3:6: note: previous declaration of ‘copy’ was here
palen.c:124:1: warning: return type defaults to ‘int’
palen.c:132:1: warning: return type defaults to ‘int’
palen.c:132:1: warning: conflicting types for ‘replace’
palen.c:5:6: note: previous declaration of ‘replace’ was here
palen.c:145:1: warning: return type defaults to ‘int’
palen.c:145:1: warning: conflicting types for ‘traverse’
palen.c:6:6: note: previous declaration of ‘traverse’ was here
palen.c: In function ‘traverse’:
palen.c:155:9: warning: incompatible implicit declaration of built-in function ‘exit’
palen.c: At top level:
palen.c:165:1: warning: return type defaults to ‘int’
palen.c:165:1: warning: conflicting types for ‘reverse’
palen.c:4:6: note: previous declaration of ‘reverse’ was here
palen.c:174:1: warning: return type defaults to ‘int’
palen.c:174:1: warning: conflicting types for ‘function2’
palen.c:8:6: note: previous declaration of ‘function2’ was here
palen.c:179:1: warning: return type defaults to ‘int’
palen.c:179:1: warning: conflicting types for ‘function1’
palen.c:7:6: note: previous declaration of ‘function1’ was here
palen.c: In function ‘reverse1’:
palen.c:131:1: warning: control reaches end of non-void function
```

If I could replicate the problem you describe (which I can't), my first step would be to address each of these warnings, starting with the first.

---

### Post by SaintDanBert on 2010-09-23
> **hemantparmar said:**
> helloo friends ...
I was writing a program for hw a turing machine works to reverse a string consisting of a and b only but the main problem was that 
the program works fine if i give a "\n" (new line) operator in each of the printf() function but if I don't give one it gives a segmentation fault just at that printf() function only .....can somebody plz explain what exactly is going on in there ......

**printf** uses what is called "buffered I/O".  Your data goes into a system buffer before it moves to the outside world.  The newline '\n' tells the system to cause that movement. I suspect the SEGFAULT happens when you write so much your process runs out of authorized memory. This is not common on most multi-gig-ram linux boxes used lately. If you want mostly immediate and continuous output, there are ways to make that happen, some even use printf.

There are other functions that will make output. It might be that you could **sprintf** to format a buffer within your program and then **fwrite** that buffer.  A "buffer" is little more than an array used to hold your character data.  In this case, I might use an array that is 80+1 bytes long, fill 80 bytes, add a NUL '\0' to the last byte and then write.

WARNING -- I believe in answering posted questions regardless of where and why they happen. I've taught C/C++ in industry and college and am willing to teach anyone who wants to learn. You should be aware that there are forum rules against doing student homework. 

Good luck,
~~~ 0;-Dan

---

