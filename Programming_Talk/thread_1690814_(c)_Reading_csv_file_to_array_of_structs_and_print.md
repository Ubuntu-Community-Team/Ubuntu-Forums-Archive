---
title: "(c) Reading csv file to array of structs and printing it"
date: 2011-02-19
forum: Programming Talk
---

### Post by trilobite on 2011-02-19
Hi all -
I'm having problems getting this program to work. It compiles, but with a couple of format warnings, and when run, it segfaults. 

The code reads in a csv file to an array of structs, then it is supposed to print it out. In the process, it creates an "obsnum" variable to show the row number. 

Here's the code - 
```
 

#include <stdio.h>
#include <stdlib.h> 
#include <string.h>
#include <ctype.h>

char *headings[40][6] ; 

struct data { 
     int obsnum; 
     char *lastname; 
     char *firstnames;
     char *city;
     int empid ; 
     int salary ; 
} ;        

struct data mydata[4]; 


int main() { 

int i ;  

FILE *fp = fopen("data.csv", "r") ; 

 if ( fp != NULL ) 
 { 
    for(i=0; i<4; i++)  
    {           
         while(i == 0) 
           {  
             headings[40][0] = "Obs" ;         
             fscanf(fp, "%s, %s, %s, %s, %s \n", 
             headings[40][1], headings[40][2], headings[40][3], 
             headings[40][4], headings[40][5] ) ;   
             i++;      
           }   
                  
   mydata->obsnum = i ;       
   fscanf(fp, "%s, %s, %s, %d, %d \n", 
      mydata->firstnames, mydata->lastname, mydata->city, 
      mydata->empid, mydata->salary );             
   i++;       
   }  /* EOF */  
   
}  /* File exists */    
   

/*  Print the file */ 

printf("%s, %s, %s, %s, %s, %s \n", headings[40][0], 
   headings[40][1], headings[40][2], headings[40][3], 
   headings[40][4], headings[40][5] );  
  
int j; 
  
for (j=0; j<4; j++)    
  { 
    printf("%d %s %s %s %d %d", 
           mydata[j].obsnum, mydata[j].firstnames, 
           mydata[j].lastname, mydata[j].city, 
           mydata[j].empid, mydata[j].salary );   
  }  
          
return 0;   
  
}


```  

Here is the data that the code reads - 
last_name,first_names,city,emp_id,salary
Jones,Fred,Auckland,2437,45000
Watson,Alan,Dunedin,5091,58000
Smith,Brian,Christchurch,3133,55000
Dawson,John,Wellington,4685,67000

So, with the obs number being added, it should look like this when printed - 
"obs","last_name","first_names","city","emp_id","salary" 
1,Jones,Fred,Auckland,2437,45000
2,Watson,Alan,Dunedin,5091,58000
3,Smith,Brian,Christchurch,3133,55000
4,Dawson,John,Wellington,4685,67000  

These are the warnings I get - 
gcc -Wall -std=c99 -o "readfile" "readfile.c" -lm  (in directory: /home/andy/crystal)
readfile.c: In function ‘main’:
readfile.c:52: warning: format ‘%d’ expects type ‘int *’, but argument 6 has type ‘int’
readfile.c:52: warning: format ‘%d’ expects type ‘int *’, but argument 7 has type ‘int’
Compilation finished successfully.


As is probably obvious, I'm quite new to using C (and particularly to using structs). So, any help here is much appreciated!  
- trilobite

---

### Post by Some Penguin on 2011-02-19
Allocating memory for a structure that has a pointer as a member (e.g. the char* fields) allocates space to hold the pointers -- but does not allocate memory that the pointers actually point to.

Think about it:  how would the compiler know how much memory they need?  So when you fscanf() and attempt to write an arbitrary number of bytes into the space addressed by the pointer... *poof*

---

### Post by trilobite on 2011-02-19
> **Some Penguin said:**
> Allocating memory for a structure that has a pointer as a member (e.g. the char* fields) allocates space to hold the pointers -- but does not allocate memory that the pointers actually point to.

Think about it:  how would the compiler know how much memory they need?  So when you fscanf() and attempt to write an arbitrary number of bytes into the space addressed by the pointer... *poof*
Hi Some Penguin, thanks for your reply - 
Ok, so I've changed the code so that the struct now uses arrays as follows - 
```
 
struct data { 
     int obsnum; 
     char lastname[50]; 
     char firstnames[60];
     char city[30];
     int empid ; 
     int salary ; 
} ;       

``` 
It makes no difference - I still get a list of format warnings.

---

### Post by Arndt on 2011-02-19
> **trilobite said:**
> Hi Some Penguin, thanks for your reply - 
Ok, so I've changed the code so that the struct now uses arrays as follows - 
```
 
struct data { 
     int obsnum; 
     char lastname[50]; 
     char firstnames[60];
     char city[30];
     int empid ; 
     int salary ; 
} ;       

``` 
It makes no difference - I still get a list of format warnings.

When you use fscanf to read integers, you have to supply a pointer to where to put the value. For example, &mydata->empid; not mydata->empid.

---

### Post by trilobite on 2011-02-19
> **Arndt said:**
> When you use fscanf to read integers, you have to supply a pointer to where to put the value. For example, &mydata->empid; not mydata->empid.

Hi Arndt - thanks for that, it was very helpful!  

I'm getting there - this is the code as it is now - it compiles with no errors or warnings -  
```
 

#include <stdio.h>
#include <stdlib.h> 
#include <string.h>
#include <ctype.h>

char *headings[40][6] ; 

struct data { 
     int obsnum; 
     char lastname[50]; 
     char firstnames[60];
     char city[30];
     int empid ; 
     int salary ; 
} ;        

struct data mydata[4]; 


int main() { 

int i ;  

headings[40][0] = "Obs" ;     


FILE *fp = fopen("data.csv", "r") ; 

if ( fp != NULL ) 
 { 
    fscanf(fp, "%15s, %15s, %8s, %10s, %10s \n", 
       headings[40][1], headings[40][2], headings[40][3], 
       headings[40][4], headings[40][5] ) ;   
                  
    for(i=0; i<5; i++)  
    {                                      
       mydata[i].obsnum = i ;       
       fscanf(fp, "%49s, %59s, %29s, %d, %d \n", 
          mydata[i].firstnames, mydata[i].lastname, mydata[i].city, 
          &mydata[i].empid, &mydata[i].salary );             
          /* i++; */        
    }  /* EOF */  
   
  fclose(fp);   
   
}  /* File exists */    
   

/*  Print the file */ 

printf("%s, %s, %s, %s, %s, %s \n", headings[40][0], 
   headings[40][1], headings[40][2], headings[40][3], 
   headings[40][4], headings[40][5] );  
  
int j; 
  
for (j=0; j<5; j++)    
  { 
    printf("%d %s %s %s %d %d \n", 
           mydata[j].obsnum, mydata[j].firstnames, 
           mydata[j].lastname, mydata[j].city, 
           mydata[j].empid, mydata[j].salary );   
   /* j++; */              
  }  
          
return 0;   
  
}


``` 

This now prints out the following - 
andy@obsidian:~/crystal$ ./readfile
(null), (null), (null), (null), (null), (null) 
0 last_name,first_names,city,emp_id,salary   0 0 
1 Jones,Fred,Auckland,2437,45000   0 0 
2 Watson,Alan,Dunedin,5091,58000   0 0 
3 Smith,Brian,Christchurch,3133,55000  0 0 
4 Dawson,John,Wellington,4685,67000  0 0 
andy@obsidian:~/crystal$ 

Oddly enough, the "Obs" column heading is not printed, but the other ones are. I'm also getting those (nulls) which is odd. The two extra zeroes at the end of each line also has me puzzled.

---

### Post by schauerlich on 2011-02-20
What happens if there's an errant space in one of the lines of the file? poof - your fscanf doesn't work. '%s' only read until it finds whitespace, so "John Smith" is two separate strings as far as it's concerned. You're much better off reading in a whole line with fgets, and then parsing the line with strtok once it's been read.

You also declare 'headings' wrong. You declare it as an array of 6 arrays, each of those arrays containing 40 pointers to characters. I'm guessing what you want is something like this:

```
char headings[6][40];
```

That's an array of 6 char arrays (ie strings), each of which is 40 characters long.

---

### Post by nvteighen on 2011-02-20
Ok, I get a segfault with your latest code. If you don't, this is because you're relying on some undefined behaivor somewhere. Curiously, I don't get the segfault when running your code under the gdb debugger.

There are several problems with your code. One is that you mix implementation and interface; this is that you are placing the strings "Obs" into the heading just because you want it printed, but its completely superflous for saving the data... Just print that string when printing... Related to this is that you've included the fields description into the data file and you store it into the data structure... but the string "empid" isn't an integer! Another problem is that this would be much easier if you splitted each different task into a different function.

But this isn't an easy thing to do either. C is terrible for string manipulation. If you're bound to use C, use a regexp library (there's the POSIX interface, but I've never used it in C). Otherwise, this is quite the task for learning Perl... :P

---

### Post by trilobite on 2011-02-20
> **schauerlich said:**
> What happens if there's an errant space in one of the lines of the file? poof - your fscanf doesn't work. '%s' only read until it finds whitespace, so "John Smith" is two separate strings as far as it's concerned. You're much better off reading in a whole line with fgets, and then parsing the line with strtok once it's been read. 
 
Ahh... thanks for that!  Yes, I'd thought about using strtok - I'll try that. 

[QUOTE=schauerlich
You also declare 'headings' wrong. You declare it as an array of 6 arrays, each of those arrays containing 40 pointers to characters. I'm guessing what you want is something like this:

```
char headings[6][40];
```

That's an array of 6 char arrays (ie strings), each of which is 40 characters long.[/QUOTE]  
Yes - that's exactly what I want! Thanks for that.   
- trilobite

---

### Post by trilobite on 2011-02-20
> **nvteighen said:**
> Ok, I get a segfault with your latest code. If you don't, this is because you're relying on some undefined behaivor somewhere. Curiously, I don't get the segfault when running your code under the gdb debugger.

There are several problems with your code. One is that you mix implementation and interface; this is that you are placing the strings "Obs" into the heading just because you want it printed, but its completely superflous for saving the data... Just print that string when printing... Related to this is that you've included the fields description into the data file and you store it into the data structure... but the string "empid" isn't an integer! Another problem is that this would be much easier if you splitted each different task into a different function.

But this isn't an easy thing to do either. C is terrible for string manipulation. If you're bound to use C, use a regexp library (there's the POSIX interface, but I've never used it in C). Otherwise, this is quite the task for learning Perl... :P 
Thanks for that, nvleighen!  
Agreed - C isn't at all good for manipulating strings.  
- trilobite

---

### Post by ve4cib on 2011-02-20
You could also consider using strtok to parse your lines of text.  Instead of reading in and parsing the line in one step you could read the entire line in at once, storing it in a temporary buffer.  Then you use strtok to fetch each individual field, copying them into your struct as you go.

It breaks everything up into two steps, but it might make things easier for you?

---

### Post by trilobite on 2011-02-20
> **ve4cib said:**
> You could also consider using strtok to parse your lines of text.  Instead of reading in and parsing the line in one step you could read the entire line in at once, storing it in a temporary buffer.  Then you use strtok to fetch each individual field, copying them into your struct as you go.

It breaks everything up into two steps, but it might make things easier for you? 
Hi ve4cib - thanks for that!  
I agree. I will break the code up a bit, and will handle the headings and data separately. I'll also use strtok - I have a bit of experience using that. 
Separating the handling of headings and data (and adding a couple of functions to handle things too) will make the code much cleaner. 
Many thanks, everyone! I'll mark this as "solved" now.  
- trilobite

---

