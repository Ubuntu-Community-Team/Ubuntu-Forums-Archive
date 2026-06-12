---
title: "help with c program"
date: 2008-01-12
forum: Programming Talk
---

### Post by onewaytrip on 2008-01-12
im trying to write a program that will reverse a string, here my code:

#include <stdio.h>

//////////////////////////////////////////
int length(char *str)
        {
        int i = 0;
        for(i=0; str[i]!=0; i++)
                {       }

        return i;
        }

//////////////////////////////////////////
void reverse(char *str)
        {
        int i;
        int k = length(str)-1;
        char *tmp;
        char temp;
        strcopy(str, tmp);
        for(i=0,k; i<=k; i++,k--)
                {
                temp = str[i];
                str[i] = tmp[k];
                tmp[k] = temp;
                }
        }

//////////////////////////////////////////
void strcopy(char *str, char *dub_str)
        {
        int i;
        for(i=0; ; i++)
                {
                dub_str[i] = str[i];
                if(dub_str[i] == '\0')
                        {
                        break;
                        }
                }
        }

//////////////////////////////////////////
int main()
        {
        char *test ="hello\0";
        printf("%s \n",test);
        reverse(test);
        printf("%s \n",test);
        return 0;
        }

everything looks fine to me but when i run it i get a "bus error". and when i run it on xcode it tells me that "str[i] = tmp[k];" is where the error is. any help will be great. 

thanks in advance.

---

### Post by fyplinux on 2008-01-12
:) 
the ending of a string is '\0', not 0

and when copying , the destination should by initialized.normally:

char *a = "eee";
char *s = malloc(size of(a));
strcpy(s,a);

---

### Post by amo-ej1 on 2008-01-12
and why are you using custom implementation of strcpy and strlen ? 

At the initialisation you don't need to place the \0 in the string, it is appended there automatically.

---

### Post by bobrocks on 2008-01-12
Hello there, I am positive you would get a faster response if you put your post into code tags to preserve indentation.

[PHP]
int length(char *str)
{
int i = 0;
for(i=0; str[i]!=0; i++)
{ }

return i;
}
[/PHP]

There is a problem here in that you are comparing for the end of char array terminator, but that character is actually the char '\0' not the number 0.

[PHP]
int length(char *str) {
    int i = 0;
    for(i=0; str[i]!= '\0'; i++)  { }

    return i;
}
[/PHP]

[PHP]
void reverse(char *str)
{
int i;
int k = length(str)-1;
char *tmp;
char temp;
strcopy(str, tmp);
for(i=0,k; i<=k; i++,k--)
{
temp = str[i];
str[i] = tmp[k];
tmp[k] = temp;
}
}
[/PHP]

There is a couple of problems here, for one you are using strcopy before you have declared it.  the function strcopy should be before this or you will have to add a definition of the strcopy function before this function.

eg - void strcopy(char*, char*);

Also you have declared tmp as a pointer for char array that you have sent to strcopy.  You first need to define the length of this char array either using malloc or simply doing - 
[PHP]
char t[k];
char *tmp = t;
[/PHP]

Lastly in this function your algorithm for reversing is wrong.  You have gone to the effort of creating a copy and then used a swapping algorithm which is what you would have done without a copy.  You are basically reversing both strings and then stopping both in the middle.  You could fix this many ways, I leave you to find them but here is a simple one

[PHP]
void reverse(char *str) {
    int i,j;
    int k = length(str)-1;
    
    char t[k];
    char *tmp = t;
    char temp;
    strcopy(str, tmp);

    for(i=0, j=length(str);i != j;i++, k--) {
        str[i] = tmp[k];
    }
}
[/PHP]

Lastly in main, you should declare the char array, \0 is implicit -

[PHP]
int main() {
    char test[] ="hello";
    printf("%s \n",test);
    reverse(test);
    printf("%s \n",test);
    return 0;
}
[/PHP]

Anyway, that should work I think.  

Have fun.

---

### Post by bobrocks on 2008-01-12
> **amo-ej1 said:**
> and why are you using custom implementation of strcpy and strlen ? 

At the initialisation you don't need to place the \0 in the string, it is appended there automatically.

This is standard practice for learning a language, you usually start out writing these types of functions.  Besides which they are usually good practice in learning about  arrays and pointers.  They are a good beginning in the language.

---

### Post by amo-ej1 on 2008-01-12
asking people to reinvent the wheel for eductational purposes is imo a lack of creativity. There are million things to do with pointers. And by reinventing the wheel, you introduce new problems that are no part of the original problem.

---

### Post by Compyx on 2008-01-12
> **bobrocks said:**
> 
There is a problem here in that you are comparing for the end of char array terminator, but that character is actually the char '\0' not the number 0.


Wrong. The escape sequence '\0' represents an octal number: the number 0. It is perfectly legal to use plain 0 as a string terminator, although using '\0' makes it more obvious you're working with strings.

It also perfectly legal to use 0 as a NULL-pointer constant, although this only obfuscates the code and I would not recommend it.

---

### Post by LaRoza on 2008-01-12
> **amo-ej1 said:**
> asking people to reinvent the wheel for eductational purposes is imo a lack of creativity. There are million things to do with pointers. And by reinventing the wheel, you introduce new problems that are no part of the original problem.

Actually, rewriting standard library functions is a very good way to learn. K&R is full of such examples, and I never heard anyone against this, unless it was not a learning experience, in which case, rewriting doesn't make sense.

---

### Post by bobrocks on 2008-01-12
> **Compyx said:**
> Wrong. The escape sequence '\0' represents an octal number: the number 0. It is perfectly legal to use plain 0 as a string terminator, although using '\0' makes it more obvious you're working with strings.

It also perfectly legal to use 0 as a NULL-pointer constant, although this only obfuscates the code and I would not recommend it.

Yes you are correct, it is the escaped 0 but I still consider it a problem to do it.  

Sorry

---

### Post by Wybiral on 2008-01-12
> **amo-ej1 said:**
> asking people to reinvent the wheel for eductational purposes is imo a lack of creativity. There are million things to do with pointers. And by reinventing the wheel, you introduce new problems that are no part of the original problem.

As silly as it sounds, writing a string library (or class in C++) is one of the first assignments most books will have you do (at least from the ones I've read). I think it's just because of how easy they are to understand and implement, plus they make you aware of the dangers behind the scenes when dealing with memory allocation / pointer manipulation / overflow.

---

### Post by onewaytrip on 2008-01-12
thanks for the help. yeah i was told the same thing, that re-writing standard library functions was a good way to learn which is why im doing it.

---

