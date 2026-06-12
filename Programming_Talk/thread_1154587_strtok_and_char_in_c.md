---
title: "strtok and **char in c"
date: 2009-05-09
forum: Programming Talk
---

### Post by monkeyking on 2009-05-09
I'm trying to relearn C,
so I'm refreshing cstrings and strtok.

I'm basicly just trying to make a tokenizer that returns an **argv,
just like the 'int main(int argc, **argv)'.

Following code compiles fine,
but doesn't give me the output I wan't and valgrind reports some errors
[PHP]
#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char **get_lexemes(char *str,const char *delim,int *numTokens){
  //1. get number of tokens
  char *cpy = str;
  char *token = NULL;
  token = strtok(cpy,delim);
  printf("%s ",token);
  while ( token != NULL ){
    (*numTokens)++;
    token = strtok( NULL,delim );
  }
  printf("numToks:%d\n",*numTokens);
  
  
  //2. now do the actual tokenization
  //we have numTokens so lets allocate the array
  char **retVal = malloc((*numTokens)*sizeof(char*));//doesnt work
  int item=0;
  retVal[item++] = strtok(str,delim);
  while ( token != NULL ){
    token = strtok( NULL,delim );
    retVal[item++] = token;
  }
  
  return retVal;
}

int main(int argc, char **argv){

  char str[] = "yoyoyoyoyoyoy asdfasdfasddf qwerqwer  zcvxzxcv";
  char delim[] = " \t";
  int numToks = 0;
  char **retVals = get_lexemes(str,delim,&numToks);
  printf("%d\n",numToks);
  int i;
  for( i=0; i<numToks; i++)
    printf("i:%d %s\n",i,retVals[i]);

  return 0;
}
[/PHP]

and output

```

 ./a.out 
yoyoyoyoyoyoy numToks:4
4
i:0 yoyoyoyoyoyoy
i:1 (null)
i:2 (null)
i:3 (null)


```

thanks in advance

---

### Post by MeLight on 2009-05-10
I've commented the lines I changed, let me know if you need further explanation

[PHP]#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char **get_lexemes(char *str,const char *delim,int *numTokens){
  //1. get number of tokens
  char *cpy = malloc(strlen(str)*sizeof(char));     //MeLight> allocate space for the copy string
  strcpy(cpy, str);     //MeLight> copy the original string to the copy
  char *token = NULL;
  token = strtok(cpy,delim);
  printf("%s ",token);
  while ( token != NULL ){
    (*numTokens)++;
    token = strtok( NULL,delim );
  }
  printf("numToks:%d\n",*numTokens);


  //2. now do the actual tokenization
  //we have numTokens so lets allocate the array
  char **retVal = malloc((*numTokens)*sizeof(char*));//doesnt work
  int item=0;
  retVal[item++] = token = strtok(str,delim);   //MeLight> put the first token in to token var (so it's not null)
  while ( token != NULL ){
    token = strtok( NULL,delim );
    retVal[item++] = token;
  }

  return retVal;
}

int main(int argc, char **argv){

  char str[] = "yoyoyoyoyoyoy asdfasdfasddf qwerqwer  zcvxzxcv";
  char delim[] = " \t";
  int numToks = 0;
  char **retVals = get_lexemes(str,delim,&numToks);
  printf("%d\n",numToks);
  int i;
  for( i=0; i<numToks; i++)
    printf("i:%d %s\n",i,retVals[i]);

  return 0;
}[/PHP]

---

### Post by monkeyking on 2009-05-10
Thanks melight!


I had completely forgotten that I had to malloc and then do strcpy.
And I had also forgot to set the token var in the second loopthrough.

The code is working now.

Does anyone have a good idea on how to avoid the 2nd parsing of the cstring?

Thanks again

---

### Post by dwhitney67 on 2009-05-10
Your code may be working, but it is a bit inefficient, in that you need to do the strtok() stuff twice.

Also, I suspect that you did not free up all of the memory in your app, thus valgrind will be unhappy about that.

Here's a twist on your app:
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int get_tokens(const char* str, const char* delim, char*** tokens)
{
  int   num_tokens = 0;
  char* cpystr     = strdup(str);
  char* token      = strtok(cpystr, delim);

  while (token) {
    ++num_tokens;

    if (num_tokens == 1) {
      *tokens = malloc(sizeof(char**));
    }
    else {
      *tokens = realloc(*tokens, num_tokens * sizeof(char**));
    }

    (*tokens)[num_tokens - 1] = strdup(token);

    token = strtok(0, delim);
  }
  free(cpystr);

  return num_tokens;
}

int main()
{
  char   str[]   = "hello world";
  char   delim[] = " \t";
  char** argv    = 0;
  int    argc    = get_tokens(str, delim, &argv);

  for (int i = 0; i < argc; ++i) {
    printf("%s\n", argv[i]);
    free(argv[i]);
  }

  free(argv);
  return 0;
}

```

---

### Post by monkeyking on 2009-05-10
Thanks dwhitney,

you are always very helpfull, and supply me with good codeexamples.

I had not seen strdup before and the idea of passeing the returnToks as a argument is very nice.

I was thinking about doing it,
but I couldn't grasp the tripple pointer thingie. :)


But I have some questions.

1. You use zero as NULL, is that the same?
2. Do you strdup each token because strtok modifies the earlier return pointers?

3. you choose to use pre ++ instead of the post ++ is that just habit, or is there some special reason.

4. You use realloc, which in the worst case will result in many free/mallocs. Is this one of the cases where It would be wise to use a single linked list.
What do you think?


Thanks again,
your input is as always very much appreciated.

---

### Post by dwhitney67 on 2009-05-10
> **monkeyking said:**
> ...
I was thinking about doing it,
but I couldn't grasp the tripple pointer thingie. :)

Yeah, it took me a few tries to sort it out too.

> **monkeyking said:**
> 
But I have some questions.

1. You use zero as NULL, is that the same?
2. Do you strdup each token because strtok modifies the earlier return pointers?

3. you choose to use pre ++ instead of the post ++ is that just habit, or is there some special reason.

4. You use realloc, which in the worst case will result in many free/mallocs. Is this one of the cases where It would be wise to use a single linked list.
What do you think?
...
Answers:

1.  I use zero because it looks cool, and is 3 less characters to type.

2.  strtok() essentially modifies the pointer you pass it; it bumps it along with each successive call, such that when you are done, you don't have a pointer that points to the beginning of the string originally passed to strtok().  The application would have to know to free only the first token, but not the others, since freeing the first would free the entire pool of tokens.  I found it easier to use strdup(), which allocates and copies the string to the destination.

3.  I use the pre-increment because in the old days, when compilers were still in their infancy, it was more efficient than the post-increment.  I may be wrong, but I think the post-increment loaded the resulting value into a register so that it could be returned.  In my example, I did not need this return value.

4.  I do not know the inner-workings of realloc(); you could be correct.  With respect to the link list, sure that would be more efficient to build, however then this would not have met your original specifications to have an argv[] type of array.  Also, a linked list would make it more cumbersome (i.e. inefficient) to quickly access an element, whereas with an array, I merely need an index.

---

### Post by ibuclaw on 2009-05-10
I personally find it a fun exercise to build these things from near scratch: [http://codepad.org/K44jGjHo](http://codepad.org/K44jGjHo)

I'm not sure how optimal it is though compared to the gcc implementation (which most likely has strchr implemented in inline #asm).

Regards
Iain

---

### Post by monkeyking on 2009-05-10
Hi dwhitney

Thanks for your info and help yet again,
I managed to pull my program together such that it uses the single list internally when it tokenizes the string.

And then inputs these into an argv type array as a parameter given to the function.
[PHP]
#include <string.h>
#include <stdio.h>
#include <stdlib.h>

//single linked list definition
struct node_t{
  char *data;
  struct node_t *next;
};
typedef struct node_t node;

//single linked list node memory allocation
node *alloc(char *ary){
  node *retVal = malloc(sizeof(node));
  retVal->data = ary;
  retVal->next = NULL;
  return retVal;
}


int get_lex(char *str,const char *delim,char ***tokens){
  int len =0;
  char *token = 0;
  node *head,*current;


  //1. tokenize the string to a linked list
  token = strtok(str,delim);
  head = alloc(token);
  current=head;

  len++;
  while ( token != NULL ){
    token = strtok(0,delim);
    if(!token)//catch spurious NULL\s (multi delims...)
      continue;
    current->next = alloc(token);
    current = current->next;
    len++;
  }

  //2. populate the array and input the nodes from the linked list.
  *tokens  = malloc(len*sizeof(char*));
  int i=0;
  current=head;
  while(current){
    (*tokens)[i++] = current->data;
    head= current->next;
    free(current);
    current=head;
  }

  return len;
}

void print(char** tmp,int len){
  int i;
  for(i=0;i<len;i++)
    printf("%d: %s\n",i,tmp[i]);

}


int main(int argc, char **argv){

  char str[] = "yoyoyoyoyoyoy asdfasdfasddf qwerqwer  zcvxzxcv";
  char delim[] = " \t";
  char **toks;
  int len = get_lex(str,delim,&toks);
  print(toks,len);

  free(toks);
  return 0;
}
[/PHP]

But I think I found a small bug in your tripple pointer thingie.

If I wanted to create a pointer to an int(an int array).
I would do
[PHP]
int *i = malloc(sizeof(int))
[/PHP]
So if I wanted to create a pointer to a chararray that would be

[PHP]
char **i = malloc(sizeof(char*))
[/PHP]
So I figured

doing

[PHP]
char ***toks;
*toks = malloc(numberoftokens*malloc(sizeof(char*)))
[/PHP]

I'm really confused but the compiler and valgrind seems satisfied

---

### Post by dwhitney67 on 2009-05-10
A couple of comments:

1.  Your token could possibly be null here; in a situation like this, you would've allocated memory (to store a null), and indicated that you have at least one element.  Oh the horror!
```

...

  //1. tokenize the string to a linked list
  token = strtok(str,delim);
  head = alloc(token);
  current=head;

  len++;

...

```

2.  sizeof(char*) and sizeof(char**) both return 4 bytes, for alas, they are both representatives of a pointer.


P.S.  I like my code better.  Sorry!  :-)

---

### Post by monkeyking on 2009-05-10
Hi,
You are very correct about this NULL token.
The error would occur at the end of the file I guess.
so I simply fixed it with

if(!token)
  return 0;

In my code, I don't use strdup for the returnvalue of strtok.
And it seems to work.

I guess, it only works because I don't fumble with the string in other parts of my program.


But thanks again dwhitney, you are really helpfull.

---

