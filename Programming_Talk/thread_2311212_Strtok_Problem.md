---
title: "Strtok Problem"
date: 2016-01-25
forum: Programming Talk
---

### Post by Iurie_Nunu on 2016-01-25
Hi guys , I did this program in C, that takes in input a with numbers, sum and difference and gives back the integer result of it , example: input: "14+3-7" (string) output 10 (integer), but it doesn't work and i cant understand the problem, i guess it's because i can't use strtok function properly...if anybody can help me this will be very nice, because i need it for a university task. ps im new here and english it's not my first language, if i went wrong writing something im sorry...
this is the program:

```
#include <stdio.h> 
#include <string.h> 
#include <stdlib.h> 
 


    int express(char* string){ 
        char* word; 
        char* separatore= "+"; 
        int trasformato; 
        int trasformatouno;
        int i; 
        int j; 
        int k; 
        int sum; 
        int vector[100]; 
        int contatore=1; 
        //Charge all the array with zeros
        
        for(k=0;k<100;k++){ 
            vector[k]=0; 
        } 
         
        //charge the first box of the array with the first number 
        word = strtok(string, separatore); 
        trasformatouno=atoi(word);
        vector[0]=trasformatouno;
        //charge all the rest of the array 
        while (word!=NULL)  
                { 
                 word = strtok(NULL, separatore);  
                 contatore=contatore+1; 
                 trasformato= atoi(word); 
                 for (i=1; i<contatore;i++){ 
                 vector[i]=trasformato; 
             } 
                     
           }  
             
         
        for (j=0; j<contatore; j++) 
            sum +=vector[j]; 
             
         return sum; 
    } 
 
int main() { 
     
    char* input; 
    printf("Insert the operation :"); 
    scanf ("%s", input); 
    printf("the result is %d\n", express(input)); 
 
 
}
```

---

### Post by trent.josephsen on 2016-01-26
Your English is good, no need to apologize.

Here's some things I thought about your code as I read it. I didn't try to run it at first, I just walked through it in my head and predicted what would happen.

```
        word = strtok(NULL, separatore);
```
When strtok reaches the end of the string, 'word' becomes NULL here.

```
        trasformato = atoi(word);
```
And then you pass a null pointer to atoi. Oops. Who knows what this will do.

However, that's more or less irrelevant, because express() never gets called at all. Let's look at main():

```
    char *input;
    printf("Insert the operation :");
    scanf("%s", input);
```

'input' is a pointer, but it doesn't point at anything in particular. There's no buffer for scanf to fill. Here's one way to make sure the memory pointed at is valid:
```
    char input[100];
    scanf("%99s", input);
```
(Notice I changed the scanf format string so that it will never overflow the buffer.)

My compiler warned me about this last problem because I always compile with lots of warnings turned on. This is always a good idea when you're learning; the compiler can tell you about things you can't anticipate. Here's what I ran to compile your program:
```
gcc -std=c11 -Wall -Wextra -Wwrite-strings lurie.c
```

(-Wwrite-strings also tells me that 'separatore' should be typed as "const char *". This isn't technically necessary but it's almost always a good idea for variables that will point to string literals.)

Aside from enabling compiler warnings, there are many ways to debug programs. Here are two you can use immediately:
1. **Step through the code in your head** and predict what it will do. That's how I identified the atoi(NULL) error.
2. **Insert printf() calls inside your code** to display the values of variables as the program runs. *I suggest printing the value of 'i' inside the inner 'for' loop.*

Debuggers like gdb are another good way, but don't worry about those until you're a little more experienced. They're great, though, for debugging non-trivial programs.

I hope this helps. You should be able to get your program to run without crashing if you fix the two problems I've pointed out. After that, feel free to post follow up questions if you have any.

**However,** I feel obligated to warn you that you can't effectively use strtok() to solve the problem where + and - are mixed in the same expression. Ultimately, you might be following a dead-end here. But it will definitely work for expressions with only + in them.

---

### Post by Iurie_Nunu on 2016-01-27
thankyou trent for your suggestions ...at the end i decided to make it all again following another road, I used the function strsep... now eeverithing works perfectly...
```

#include <stdio.h> 
#include <string.h> 
#include <stdlib.h>

int express(char *string) { 
int somma=0; 
char* elemento; 
char* elementodue; 
int elementdue; 
int element; 
char* delim="+"; 
char* delimdue="-"; 
char* test; 
char meno = '-'; 
int contatore=0; 

while(string!=NULL) { 
elemento=strsep(&string, delim); 



test=strchr(elemento, meno); 
if (test==NULL) { 

element=atoi(elemento); 
somma=somma+element; 

} 

else { 

while(elemento!=NULL) { 
elementodue=strsep(&elemento, delimdue); 
elementdue=atoi(elementodue); 
contatore++; 
if (contatore==1) 
somma=somma+elementdue; 
else somma=somma-elementdue; 

} 



} 


} 

return somma; 

} 



int main() { 

char* input=strdup("1-2-3+54"); 

printf("the result is %d\n", express(input)); 

return 0; 
}
```

---

