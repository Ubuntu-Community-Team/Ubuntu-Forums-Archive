---
title: "Simple lexer - where to put the &quot;loops&quot;"
date: 2018-01-09
forum: Programming Talk
---

### Post by trilobite2 on 2018-01-09
Hi all -  

 I've written most of a simple lexer in C but the part I have problems with is where to put the loops that iterate through a string (or through a file) and also the code that gets tokens.  

I've noticed that most (if not all) lexers that I've seen don't seem to have parameters for the main lexing and the sub-lexing functions so I'm keen to use that approach if possible.  

Here's what I have so far - 

```
 

/* toysql.c  */ 
/* A lexer for a very small subset of SQL.  */

/* This code is released to the public domain. */ 
/* "Share and enjoy......"  :)     */ 


#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>

#define NUMBER_OF_KEYWORDS 9


/* Array of our keywords in string form. */ 
char *kw_strings[] = { 
   "select", "from", "where", "and", "or", "not", "in", "is", "null" 
    } ; 
   
    
/*  Search function to search the array of keywords. */ 
int search(char *arr[], int dim, char *str) { 
    
    int i;      
    int found_match;
    
    for (i=0; i<dim; i++) { 
        if ( !strcmp(arr[i] , str ) )  {   
            found_match = 1;        
            break; 
    }   else found_match = 0;    
 }  /* For */     

    return found_match; 
}  /* search */ 


/* Token types. */ 
typedef enum { KEYWORD, IDENTIFIER,  OPERATOR, STRING, NUMBER, _EOF_ } 
 token_type ;     


/* Tokens.  */ 
typedef struct {
    token_type type;
    union {
        char *string_value;      
        int int_value;
    } value;
} token;


token *lex_kwident() {    
  token *t;     
  
  /* Get some characters here from string or file and */
  /* iterate through until a non-aphanum character is found */ 
  
    
  if (search(kw_strings, NUMBER_OF_KEYWORDS, t.value.string_value) == 1 )
      t.type = KEYWORD;
  else
      t.type = IDENTIFIER;
  
  return t;     
} 


token *lex_space() {  
   
  token *t;     
  
  return t;         
}     


/*  "Main" lexer.  Usually does not take parameters from what I've seen. */ 
token *lex() {     
   
  /*  ???  Do I put function to get characters from string/file 
   * here or should it go elsewhere?  */       
    
  token *t;     
  
  
  /*  Give token to "parser"  */ 
 parse(token) ;     
  

} 


/* Not a parser (yet) - just prints the token type. */ 
/* I think this might have to take a parameter - the token returned by lexer.  */ 
void parse() { 
  

            
  printf("Tokentype: %d\n", t.type); 
}        

          
int main() { 

/* Try the lexer on a string first. */ 
char *mystr1 = "select mycol from mytable" ; 


/* Loop here? */ 

parse(); 

return 0; 

} 


```  

So.... any help in "beefing out" this code is very welcome!  
Many thanks in advance -   

- trilobite2

---

### Post by r-senior on 2018-02-03
You seem to have a lot of the building blocks in place, but your comment here ...

```
  /*  Give token to "parser"  */ 
 parse(token) ;  
```

... suggests that you are thinking of the lexer driving the parser. It's usually the other way around; the parser calls a function in the lexer that returns the next token from the input stream.

If you look at how lex/yacc or flex/bison work, the lexer provides a function called yylex. This returns an int value that indicates the type of token and stores the semantic value of the token into a global variable called yylval. The parser has a loop that calls yylex() to request tokens and it tries to match these against its grammar rules. If the parser gets a token that it can't match, that's a syntax error. As it works through the rules, it stores the semantic values associated with the grammar rules that it matched. If parsing succeeds, these values form the validated output of the parser and feed the next stage of whatever you are doing.

You are taking a slightly different approach from lex/flex in that you are working with a token struct that combines the token type and semantic values. That should be fine. You don't need to mimic the int return value and yylval global approach.

If you make your parse function something like this, you should be getting back on the right track:

```
void parse() {
    token *t = lex();
    while (t->type != _EOF_) {
        printf("Tokentype: %d\n", t->type);
        t = lex();
    }
}
```

Your main function should just call parse() initially (no loop inside main). Obviously your test string needs to move out of main and become a global variable if the lex function is to see it.

---

### Post by trilobite2 on 2018-02-12
Hi r-senior!  

Thanks very much for your reply!  ( Oh, and sorry for the time taken for me to reply ).  

That sounds good!  I think you're spot-on there and I was looking at things the wrong way around.  
Thanks again - your suggestion is very helpful!  

Bye for now - 
- trilobite

---

### Post by steeldriver on 2018-02-12
Many years ago I found the (original?) [Dragon Book](https://en.wikipedia.org/wiki/Compilers:_Principles,_Techniques,_and_Tools) a great resource for this stuff - not sure if it's still regarded as such but you might want to check it out

---

### Post by trilobite2 on 2018-02-15
Hi steeldriver!   

 Thanks for that!   I'll have to check that out.  I've heard a lot of good things about it so now's the time.....  :)   

Thanks again - bye for now - 
- trilobite

---

