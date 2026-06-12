---
title: "incompatible pointer type!?!?!"
date: 2008-02-12
forum: Programming Talk
---

### Post by S15_88 on 2008-02-12
Hey i've got this wicked program written up that takes a file and redirects in as stdin the checks each word one by one and counts them up, counts how many sentences, and counts how many syllables there are in each word.

I'm having trouble with the syllable part as i'm getting an:
 incompatible pointer type
warning from gcc. 
i'm compiling with: gcc -ansi -Wall
and redirecting the file in with: ./a.out < testfile.txt

Here is my code i threw in some comments where i figure it's going wrong...any tips/suggestions would be greatly appreciated.

Thanks, Alain

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <strings.h>
#include <math.h>

int check_word(char *string)
{
    int i, length;

    length = strlen(string);

    for(i=0; i<length; i++)
    {
        if(string[i] == '.' && i>0 && i<length-1 && isalpha(string[i+1]) != 0)
        {
            return 2;
        }
    }
    return 1;   
}
void check_syllables(char *string, int *syllables)
{
    int i, length;

    length = strlen(string);
    
    for(i=0; i<length; i++)
    {
        if((string[i] == 'a' || string[i] == 'e' || string[i] == 'i' || string[i] == 'o' || string[i] == 'u' || string[i] == 'y') && 
           (string[i+1] != 'a' && string[i+1] != 'e' && string[i+1] != 'i' && string[i+1] != 'o' && string[i+1] != 'u' && string[i+1] != 'y'))
        {
            (syllables)++;
        }
    }
    for(i=0; i<length; i++)
    {
        if(string[i] == 'e' && i<length-1)
        {
            (syllables)--;/*THIS IS WHERE THE WARNING POINTS TO*/
        }
    }
}
void count(int *words, int *sentences, int *syllables)
{
    
    char *string, *period, *semi_colon, *colon, *question_mark, *exclamation_mark;

    string = malloc(sizeof(char)*200);
    *words = 0;
    *sentences = 0;
    *syllables = 0;

    while(fscanf(stdin,"%s", string) != EOF)
    {
        period = index(string, '.');
        semi_colon = index(string, ';');
        colon = index(string, ':');
        question_mark = index(string, '?');
        exclamation_mark = index(string, '!');

        *words = *words + check_word(string);

        if(period != NULL || semi_colon != NULL || colon != NULL || question_mark != NULL || exclamation_mark != NULL)
        {
            (*sentences)++;    
        }
        
        check_syllables(string, &syllables);
        
    }

    free(string);
}

void index_num(int *words, int *sentences, int *syllables, int *i_num)
{

/*    i_num = (206.835 - (84.6 * (z/x)) - (1.015 * (x/y))); */

}
int main()
{
    int words, sentences, syllables, i_num;

    count(&words, &sentences, &syllables);
    

/*  printf("Legibility Index = %d\n", i_number);*/
    printf("Syllable Count = %d\n", syllables);
    printf("Word count = %d\n", words);
    printf("Sentence count = %d\n", sentences);

    return 0;
}


```

---

### Post by ruy_lopez on 2008-02-12
Changing the call to check_syllables (removing & from syllables) makes the warning go away:

```
check_syllables(string, syllables)
```

I'm not an expert, but it looks like you've already passed the pointers from main() to count. So count() knows they are pointers.

---

### Post by PaulFr on 2008-02-12
See ```
            (*sentences)++;
```further down in your code for a hint. Also you may want to consider removing unnecessary **&** characters in the following :```
        check_syllables(string, &syllables);
```*An & of an int is an int*, an & of an int* is an int**, an & of an int** is an int***, and so on.*

---

