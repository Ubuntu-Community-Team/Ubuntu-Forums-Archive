---
title: "How to implement insertion and deletion operations on string in the following program"
date: 2016-05-20
forum: Packaging and Compiling Programs
---

### Post by compiler2 on 2016-05-20
I need help with the following program in C: 
```
#include<stdio.h> 
#include<stdlib.h> 
#include<string.h> 
  
typedef struct 
{ 
    char *str; 
}STRING; 
  
//initializes dynamic string 
void init(STRING *s) 
{ 
    char str[10]; 
    s->str=(char *)calloc(strlen(str)+1,sizeof(char)); 
    strcpy(s->str,str); 
} 
  
//appends a character at the end of STRING 
void append_c(STRING *s,char c) 
{ 
    int capacity=10,used=0; 
    s->str=(char *)malloc((capacity+1)*sizeof(char)); 
    int i; 
    for(i=0;i<1;i++) 
    { 
       if(used == capacity+1) 
       { 
           capacity=capacity*2; 
           s->str=(char *)realloc(s->str,sizeof(char) * (capacity+1)); 
       } 
       s->str[used]=c; 
       s->str[used+1]=0; 
       used++; 
    } 
} 
  
//concatenates string 'str' to STRING 
void append_s(STRING *s,char *str) 
{ 
    init(s); 
    strcat(s->str,str); 
} 
  
//inserts the string 'str' to STRING at position 'pos' 
//'pos' is valid if 0<=pos<=strlen(STRING) 
//if pos<0 then set pos=0 
//if pos>strlen(STRING) then set pos=strlen(STRING) 
void insertion(STRING *s,int pos,char *str) 
{ 
    char *temp; 
    int len=0; 
  
    init(s); 
    for(; s->str; temp++) 
        len++; 
    int len2=strlen(str); 
    temp=(char *)malloc((len+len2+2) * sizeof(char)); 
  
    if(pos < 0) 
        pos=0; 
    else if(pos > len) 
        pos=len; 
  
    strncpy(temp,s->str,pos+1); 
    temp[pos+1]=0; 
    strcat(temp,str); 
    strcat(temp,s->str+pos+1); 
  
} 
  
//removes 'n' characters from STRING starting from 'pos' 
//0<=pos<=strlen(STRING) 
//if n > remainder to the right then removes all remaining characters 
void deletion(STRING *s,int pos,int n) 
{ 
    char *temp; 
    int len=0; 
  
    init(s); 
    for(; s->str; temp++) 
        len++; 
    temp=(char *)malloc((len+1) * sizeof(char)); 
  
    if(pos < 0 || pos > len) 
        return; 
    int x=len-pos; 
  
    if(n <= x){ 
    strncpy(temp,s->str,pos); 
    temp[pos]=0; 
    strcat(temp,s->str+pos+n);} 
  
    else{ 
    strncpy(temp,s->str,pos); 
    temp[pos]=0;} 
} 
  
  
int main() 
{ 
    STRING s; 
    init(&s); 
  
    append_s(&s,"GRAMMING"); 
    printf("%s\n",s.str); 
  
    insertion(&s,0,"PRO"); 
    printf("%s\n",s.str); 
  
    insertion(&s,12,"L"); 
    printf("%s\n",s.str); 
  
    append_c(&s,'A'); 
    printf("%s\n",s.str); 
  
    append_s(&s,"NGUAGES"); 
    printf("%s\n",s.str); 
  
    deletion(&s,1,4); 
    printf("%s\n",s.str); 
  
    free(s.str); 
  
    return 0; 
}
[/COLOR]
```

Output should be: 
```
//GRAMMING 
//PROGRAMMING 
//PROGRAMMING L 
//PROGRAMMING LA 
//PROGRAMMING LANGUAGES 
//PAMMING LANGUAGES
```


Functions for insertion and deletion don't work. 
Could someone correct possible syntax and logical errors?

---

### Post by nikefalcon on 2016-06-18
For starters, the for loops in your 'insertion' and 'deletion' functions run indefinitely(aka infinite loop). Check the conditional expression carefully. Sit down with pen and paper if need be and work out the logic. Google is your friend-read and learn how a for loop works.
In 'insertion' function the resulting string is assigned to temp, which is a local variable. As soon as the insertion function returns, any reference to temp is invalid. 

Good luck!

---

