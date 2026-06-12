---
title: "pipes"
date: 2006-04-28
forum: Programming Talk
---

### Post by smart girl on 2006-04-28
hi all 

I am trying to be much familier with pipes 

I tried to write a c program that generates the following output 


[B]from child: 
I 
want 
to 
print 
this 
line 
twice 

from parent: 
I 
want 
to 
print 
this 
line 
twice [/B]

what I get is 


[B]from child: 
I 
want 
to 
print 
this 
line 
twice 

from parent: 
I 
I 
I 
I 
I 
I 
I [/B]


my code is 

Code: 

```
  
#include<stdio.h> 
#include<string.h> 

int main(void){ 
int childpid,fd[2],nb,i,j; 
char line[BUFSIZ]="I want to print this line twice"; 
char word[BUFSIZ]; 


pipe(fd); 

childpid=fork(); 

if(childpid==0) 
{ 
printf("from child:\n"); 

close(fd[0]); 

char *token=strtok(line," "); 

while(token!=NULL) 
{ 
printf(" %s\n",token); 

write(fd[1],token,(strlen(token)+1)); 

token=strtok(NULL," "); 

} 

} 

else 
{ 

wait(NULL); 
printf("from parent:\n"); 



close(fd[1]); 

for( i=0;i<7;i++){ 
nb=read(fd[0],word,sizeof(word)); 
printf("%s\n",word); 

} 

} 

return 0; 

} 
```
 


can any one tell me what's wronge with this code and how to correct it?

---

### Post by nagilum on 2006-04-29
The problem is that the client writes null-terminated strings to the pipe, including the null-character at the end. The parent process waits for the child to finish and then reads all the data which was written to the pipe at once (if you print the nb-variable in the for loop you'll see that it is 0 for the last 6 times of the loop, it only reads data in the first iteration). So the word-variable contains the whole string in every iteration, plus null-characters after each word. The printf function only prints strings up to the null-character not beyond it, and that's why you only get the 'I' all the time.

---

### Post by smart girl on 2006-04-30
thanx for your reply the problem solved by reading from pipe using while loop :)

---

