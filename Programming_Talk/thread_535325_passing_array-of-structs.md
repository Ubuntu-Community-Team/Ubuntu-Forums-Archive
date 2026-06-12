---
title: "passing array-of-structs"
date: 2007-08-26
forum: Programming Talk
---

### Post by nss0000 on 2007-08-26
Gents:

Continuing my self-tutorial in 'C' ... following K&R.  

I've got to "array-of-STRUCTs" , and it appears that passing such to a function is (only) done by passing a pointer-to-array. Such like the code-fraqment below. But, is there another way to pass array-of-STRUCTs ??

  STRUCT student { []; []; ...};
  struct student get_grade( struct student * );

main()
{
  struct student people[25];
 .
 ..

 people = get_grade( people ];


}

---

### Post by Mr.Carramba on 2007-08-26
post complete code, because what you have written doesn't make any seance... without trying to guess...
since people is array of structs, and get_grade() returns only one struct you can't assign it as you have done
maybe 
```

people[x]=get_grade(...);

```

---

### Post by slavik on 2007-08-26
> **nss0000 said:**
> Gents:

Continuing my self-tutorial in 'C' ... following K&R.  

I've got to "array-of-STRUCTs" , and it appears that passing such to a function is (only) done by passing a pointer-to-array. Such like the code-fraqment below. But, is there another way to pass array-of-STRUCTs ??

  STRUCT student { []; []; ...};
  struct student get_grade( struct student * );

main()
{
  struct student people[25];
 .
 ..

 people = get_grade( people ];


}
in C, it is impossible to pass an array or any type of a "collection" (you can put an array into a struct and pass the struct).

---

### Post by the_unforgiven on 2007-08-26
You could do something like:
```

int get_grade(struct student[], int n_students);

```
But, this is no different than pass-by-pointer/pass-by-ref. method.
Also, I don't understand the logic behind your get_grades() function - what is the return value?
What is it supposed to return?

---

### Post by Mr.Carramba on 2007-08-26
> **the_unforgiven said:**
> You could do something [snip]
Also, I don't understand the logic behind your get_grades() function - what is the return value?
What is it supposed to return?
as I understand it returns a struct of type student

---

### Post by smartbei on 2007-08-26
I believe it was not clear to the original poster that when you pass a pointer to an array ina  function and then edit that array in the function, the array passed is also edited (it's the same array) (roundabout way to say it, i guess), so there is no need to return the processed array.

---

### Post by Wybiral on 2007-08-26
Basically arrays ARE pointers. "[]" is dereferencing the pointer at the index given.

There are some minor differences in the two at compile time, but more or less, an array is just a pointer to a chunk of memory that contains the elements in sequence. This is exactly why you can allocate an array dynamically using "malloc" even though it returns a "void*".

---

### Post by nss0000 on 2007-08-27
Gents:

My apologies for not posting entire code. There's a bit of "padding" I used to track_down code blunders. I don't know how to "encapsule" as most posters do with code.


#include <stdio.h>
#include <math.h>
#include <string.h>
#include <stdlib.h>

/* students.c : 8.24.07 : Array of STRUCTs calling function & returning STRUCT*/

struct stud { char class[10]; char fnam[2][20]; float agrad[3]; };

struct stud do_cal( struct stud * );  

main( int argc, char *argv[] )
{

 char *nc;
 int i, j, k;
 float agrad[3];
  
 char class[10], fnam[2][20];

 struct stud st[6];

 if ( argc != 2 )
   {
    printf("Please enter the class_name\n");
    exit(0);
   } 

  nc = argv[1];

  for (k=0; k<strlen(argv[1]); k++)
  class[k] = *(nc++);

  printf("%s\n", class); 

 for ( k=0; k<6; k++)
  { 
  for ( i=0; i<3; i++)
   st[k].agrad[i] = 0.0;
   }

  for ( k=0; k<6; k++)
  strcpy ( st[k].class , class );

  strcpy( st[0].fnam[0], "mike");
  strcpy( st[0].fnam[1], "mosley");
  strcpy( st[1].fnam[0], "Jim");
  strcpy( st[1].fnam[1], "Jones");
  strcpy( st[2].fnam[0], "Ann");
  strcpy( st[2].fnam[1], "Atkins");
  strcpy( st[3].fnam[0], "Babs");
  strcpy( st[3].fnam[1], "Beemer");
  strcpy( st[4].fnam[0], "Xan");
  strcpy( st[4].fnam[1], "Xerkis");
  strcpy( st[5].fnam[0], "Hans");
  strcpy( st[5].fnam[1], "Huber");

for (i=0; i<6; i++)
printf("Up here ... %s\t%s\t%s\t%f\t%f\t%f\n", st[i].class,st[i].fnam[0],st[i].fnam[1],st[i].agrad[0],st[i].agrad[1],st[i].agrad[2]);

  (*st) = do_cal( st ); 

for (i=0; i<6; i++)
printf("%s\t%s\t%s\t%f\t%f\t%f\n", st[i].class,st[i].fnam[0],st[i].fnam[1],st[i].agrad[0],st[i].agrad[1],st[i].agrad[2]);


  return 0;
}

/* functionland  */


struct stud do_cal( struct stud q[] )
{
  int i, j, k;
  FILE *fp;
  float ga[18][3], temp;
  char cnam[10];
  strcpy( cnam, q[0].class );
  strcat( cnam, ".dat" );
  printf("And the filename is ... %s\n", cnam); 

  for ( i=0; i<18; i++)
   {
     for ( j=0; j<3; j++)
     ga[i][j] = 0.0;
   }

 fp = fopen( cnam, "r");
 i=0;
 while ( fscanf (fp, "%f, %f, %f\n", &ga[i][0], &ga[i][1], &ga[i][2]) == 3 )
 i++;
 fclose (fp);

     /* for ( i=0; i<18; i++)
     printf("%f\t%f\t%f\n", ga[i][0], ga[i][1], ga[i][2]); */

 j = 0;
 k = 0;
 
   do {
       temp = ga[j][0] + ga[j+1][0] + ga[j+2][0];
       q[k].agrad[0] = temp/3.0;
       temp = ga[j][1] + ga[j+1][1] + ga[j+2][1];
       q[k].agrad[1] = temp/3.0;
       temp = ga[j][2] + ga[j+1][2] + ga[j+2][2];
       q[k].agrad[2] = temp/3.0; 
         
       printf("%d\t%f\t%f\t%f\n", k, q[k].agrad[0], q[k].agrad[1], q[k].agrad[2]);
       j = j + 3; 
       k++;
     } while (  j < 16 ); 
    
      

for (i=0; i<6; i++)
printf("Down here ... %s\t%s\t%s\t%f\t%f\t%f\n", q[i].class,q[i].fnam[0],q[i].fnam[1],q[i].agrad[0],q[i].agrad[1],q[i].agrad[2]);    


 return (*q);
}

---

### Post by LaRoza on 2007-08-27
> **nss0000 said:**
> Gents:

My apologies for not posting entire code. There's a bit of "padding" I used to track_down code blunders. I don't know how to "encapsule" as most posters do with code.


Use the code tags, like so:

```

#include <stdio.h>

int main(int args,char * argv)
{
    printf("Example\n");
    return 0;
}

```
The code tags look like:  [ code ] *code here* [ /code ] (no spaces in the in the tags, when actually using them)

You can also use the php tags, which adds syntax highlighting to php code, but works with most C style languages.

[php]
#include <stdio.h>

int main(int args,char * argv)
{
    printf("Example\n");
    return 0;
}
[/php]

---

