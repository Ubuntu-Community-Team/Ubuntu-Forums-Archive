---
title: "if statement + strtok"
date: 2012-09-08
forum: Programming Talk
---

### Post by xixzeroxix on 2012-09-08
hello everyone, im new in here and im having a headache with my program,the thing is that i need to get a input from the keyboard and then separate it using strtok but have to separate the tokens using 4 diferent cases and in each case i need to print the result and save it to a string like this:

input String : Label Instruction #50,Y; Label <with>

and the output should look like this:

Label: Label
Instruction: Instruction
Character 1: #50
Character 2: Y
Comentaries: Label <with>

also it has to be able to reconize if a instruction is missed like this:

Input String: adda

Output String
Label: -----
Instruction: adda
Character 1: -----
Comentaries: -----

i already got most of the problem but i still cant make the last if statement of "after finding a ; character" i would like to print Comentaries : (any token after a ;) but when i tryed to put it on a if alll i get is a new Character[i]:(anything after the ;) i have tryed for like 2 hrs and i dont know what else can i do to fix this cna some1 please help me?

heres my code:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>
#include <ctype.h>
/*
 * ||
 */
int main() {

    char word[256];
    fgets(word,256,stdin);



char *result;


while (result != NULL)
    {

            int i=0;
            char delimit[]="\n , ;";

            result=strtok (word,delimit);

                if (word[0] != 32 && word[0] != 9)

                    {

                    printf("Label \"%s\"\n", result);
                    result = strtok (NULL, "\n , ;");

                    }

            printf("Instruction \"%s\"\n", result);
            result = strtok (NULL, "\n , ;");

                for (i = 0; i < result; i++)
                    {
                        printf("Character [%d]\"%s\"\n",i, result);
                        result = strtok (NULL, ", ;");

                    }
                if(word[0] == 59)
                {


                   printf("Comentaries \"%s\"\n",result);
                    result = strtok (NULL, ";");
                    }
result = NULL;


    }

return(0);
}



```

---

### Post by dwhitney67 on 2012-09-08
I'd be interested in helping you, but your requirements are incomplete.

You have not indicated whether input would be from a data file, or from a user.  If the latter, then it appears that your attempt at the solution lacks any guards to catch a malformed input statement.

In your code, you appear to be checking against a few types of characters (space, semi-colon, and tab-space).  These should be filtered by strtok().  As for the tab-space, you made no mention in the scant requirements that you gave that this could be part of the input string.

Anyhow, just from looking at your example input strings, initially it seems that you have two scenarios: one where there is "Label", followed by other data, and another case where there is just an instruction (i.e. no "Label").  Would it not be prudent to check these scenarios first before delving into the strtok() calls??  Try using strstr() to see if "Label" appears in the input string; if not, then it must be an instruction-only input (barring of course, any error input).

---

### Post by spjackson on 2012-09-08
I've added some comments which I hope will explain some of the reasons why this isn't working.
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>
#include <ctype.h>
/*
 * ||
 */
int main() {

    char word[256];
    fgets(word,256,stdin);



char *result;

/* result is undefined. you are lucky it is not NULL. one day it
 * might be NULL. Either initialise result or use do {} while(...);
 */
while (result != NULL)
    {

            int i=0;
            char delimit[]="\n , ;";

            result=strtok (word,delimit);

/* Here and everywhere you use word[0], I thought you meant result[0],
 * because word[0] will never change after the initial fgets - unless
 * it holds a separator in which case strtok will overwrite it with nul.
 * However result[0] doesn't help you either; you seem to want to
 * do something different depending on which separator was found. Using
 * strtok() you cannot tell what separator is encountered - strtok()
 * throws the separator away (overwriting with nul).
 */
                if (word[0] != 32 && word[0] != 9)

                    {

                    printf("Label \"%s\"\n", result);
                    result = strtok (NULL, "\n , ;");

                    }

            printf("Instruction \"%s\"\n", result);
            result = strtok (NULL, "\n , ;");

/* This i < result isn't really a meaningful test. Effectively it
 * executes until result == NULL. I'm not sure what you are trying to
 * do here.
 */
                for (i = 0; i < result; i++)
                    {
                        printf("Character [%d]\"%s\"\n",i, result);
                        result = strtok (NULL, ", ;");

                    }
                if(word[0] == 59)
                {


                   printf("Comentaries \"%s\"\n",result);
                    result = strtok (NULL, ";");
                    }
result = NULL;


    }

return(0);
}

```

---

### Post by xixzeroxix on 2012-09-10
> **dwhitney67 said:**
> I'd be interested in helping you, but your requirements are incomplete.

You have not indicated whether input would be from a data file, or from a user.  If the latter, then it appears that your attempt at the solution lacks any guards to catch a malformed input statement.

In your code, you appear to be checking against a few types of characters (space, semi-colon, and tab-space).  These should be filtered by strtok().  As for the tab-space, you made no mention in the scant requirements that you gave that this could be part of the input string.

Anyhow, just from looking at your example input strings, initially it seems that you have two scenarios: one where there is "Label", followed by other data, and another case where there is just an instruction (i.e. no "Label").  Would it not be prudent to check these scenarios first before delving into the strtok() calls??  Try using strstr() to see if "Label" appears in the input string; if not, then it must be an instruction-only input (barring of course, any error input).

Hello dwhitney67,thanks for your reply.

Now in your questions, the input comes from the user,and my problem is exactly the lack of my solution to be able to determinate whenever is a invalid input 
In mi code I tried to make the strtok() function to tokenizing whenever he finds a (space a coma a semi-colon and a tabspace) and categorize the token in each case with a different print.

First I need to check if the input  first char is a “space/s” or “tab/s” if they aren’t it should print “Label” and the token 
In the case I get a “space/s” or a “tab/s” at the very first char I need to print “instruction” followed by the token after the “space/s” or “Tab/s”.

The ”character” print should be for the tokens that are separated by a “,” being them 1 or as many as the user inputs(for that I use a for-statement).

Then I need to print “Comnetaries”  after strtok() finds a “semi-colon” when it finds it I need to stop tokenizing and print everything after the semi-colon with the print “Comentaries”.

As you say I only have two scenarios, one with a correct input and one with a incorrent input in witch I should print :

For the correct input:

(any1)  (any2) (anyNumber1),(anyNumber2)  ;(anything)

Label:any1
Instruction:any2
Character[i]:anynumber1
Character[i]:anyNumber2
Comentaries:anything

As for the incorrect output I should print

(space)  (space) (anyNumber1)  

Label:-------------
Instruction:anyNumber
Character[i]:-----------------
Comentaries:----------------

As you can see this is where I having all the trouble since I don’t know how should I do it correctly.
As a note: Im using strtok() because I was told it was the easier way to make the tokens and then categorize them but so far im not able to,also im not very good at programming in C and that’s why my code is full of incoherences I would appreciate any help you can give me

---

### Post by dwhitney67 on 2012-09-10
I need to ask... is this assignment related to school work?

As for the user's input, you can try stripping away unwanted white-space from the given input.  That way, you are left with only the valid data.  You should also consider stripping away the newline character which may be captured by fgets().

As for the data format, you initially specified one format, and then gave another.  I'm not sure which is correct?

Format 1:
```

Label Instruction #50,Y; Label <with>

```
Format 2:
```

(any1) (any2) (anyNumber1),(anyNumber2) ;(anything)

```
When I examine Format 1, I see 5 fields that are separated by a white-space.  With Format 2, I see 4 fields.

Consider tokenizing the input string only using white-space as a delimiter.  Once you have your fields (4 or 5, depending on format), then you could further tokenize the appropriate field (3rd?) with a delimiter of a comma.

P.S.  In case it is not obvious, white-space denotes either a space or a tab.

---

### Post by steeldriver on 2012-09-10
As dwhitney67 pointed out in his comment, strtok explicitly overwrites the delimiter - so if you need to know (and do something different depending on) the delimiter, I think you are barking up the wrong tree with strtok

You could maybe think about implementing your own equivalent of strtok using strpbrk, giving it an additional char parameter in which to return the delimiter before it is overwritten (or a char* if you need to pass back multiple contiguous delimiters)

Hope this helps

---

