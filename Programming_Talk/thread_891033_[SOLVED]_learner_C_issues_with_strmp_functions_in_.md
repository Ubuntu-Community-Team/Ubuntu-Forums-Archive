---
title: "[SOLVED] learner C issues with strmp functions in if"
date: 2008-08-15
forum: Programming Talk
---

### Post by jon zendatta on 2008-08-15
hell0.
my problem is these string comparison functions aren't being read correctly in if statements. eg the comparison of string1 constant to string variable gives correct output but the following 6 comparisons don't!
hope i am making sense with this question thanks.
```

#include <stdio.h>
#include <string.h>

int main ()
{
   int bins, kgs, dollars_ha ;
   float packout, net_kg, dollars_per_carton, total_cartons, dollars_total;
   float bb = 2.5,                            /* these seven float constants represent the land area in hectares of each cultivar */
         rg = 1.0,
         f = 1.85,
         pb = 0.5,
         pr = 0.55,
         pq = 0.25,
         gs = 0.5;
   char str1[] = "braeburn"; 
   char str2[] = "royal gala";
   char str3[] = "fuji";
   char str4[] = "pacific beauty";
   char str5[] = "pacific queen";
   char str6[] = "pacific rose";
   char str7[] = "granny smith";
   char cultivar [15];

   printf("please enter cultivar\n", cultivar); /* input any name from str1-str7 */
   scanf("%s", &cultivar);
   printf("number of bins\n", bins);
   scanf("%d", &bins);
   printf("enter packout\n", packout);          
   scanf("%f", &packout);

   kgs = (bins * 320);                          /* one bin weighs 320kg */
   net_kg = (kgs * packout / 100);
   total_cartons = (net_kg / 18);               /* one carton of apples weighs 18kg */

   printf("enter $ per carton\n", dollars_per_carton);
   scanf("%f", &dollars_per_carton);
  
   if (!strcmp(cultivar, "braeburn")) 
   dollars_ha = (int)(dollars_per_carton * total_cartons / bb);      /* gross profit per hectare */
   printf("returns $%d per ha\n", dollars_ha);
   
   if (!strcmp(cultivar, "royal gala"))
   dollars_ha = (int)(dollars_per_carton * total_cartons / rg);
   printf("returns $%d per ha\n", dollars_ha);
    
   if (!strcmp (cultivar, "fuji"))
   dollars_ha = (int)(dollars_per_carton * total_cartons / f);
   printf("returns $%d per ha\n", dollars_ha);
   
   if (!strcmp (cultivar, "pacific beauty"))
   dollars_ha = (int)(dollars_per_carton * total_cartons / pb);
   printf("returns $%d per ha\n", dollars_ha);
  
   if (!strcmp (cultivar, "pacific queen"))
   dollars_ha = (int)(dollars_per_carton * total_cartons / pq);
   printf("returns $%d per ha\n", dollars_ha);
   
   if (!strcmp (cultivar, "pacific rose"))
   dollars_ha = (int)(dollars_per_carton * total_cartons / pr);
   printf("returns $%d per ha\n", dollars_ha);
   
   if (!strcmp (cultivar, "granny smith"))
   dollars_ha = (int)(dollars_per_carton * total_cartons / gs);
   printf("returns $%d per ha\n", dollars_ha);

   return 0;
}
```

---

### Post by lisati on 2008-08-15
I don't have much experience with C, but would suggest using something like
```
if (strcmp(x,y)!=0)
```

As I understand it, strcmp returns zero when there's a match, < 0 when "x" < "y", and > 0 when "x" >  "y"

---

### Post by cmay on 2008-08-15
the first error is
```
 printf("please enter cultivar\n", cultivar); /* <--- here input any name from str1-str7 */
   scanf("%s", &cultivar);
   printf("number of bins\n", bins);
   scanf("%d", &bins);
   printf("enter packout\n", packout);          
   scanf("%f", &packout);
```

it will warn too many parameters specified since
>  printf("please enter cultivar\n");/* you only need to write this.
   scanf("%s", &cultivar);

the paramters for printf("please enter %s \n,"cultivar);
would produce the output right if you only want to ask for the user input.

hope it will help;

---

### Post by dwhitney67 on 2008-08-15
> **cmay said:**
> the first error is
```
 printf("please enter cultivar\n", cultivar); /* <--- here input any name from str1-str7 */
   scanf("%s", &cultivar);
   printf("number of bins\n", bins);
   scanf("%d", &bins);
   printf("enter packout\n", packout);          
   scanf("%f", &packout);
```

it will warn too many parameters specified since


the paramters for printf("please enter %s \n,"cultivar);
would produce the output right if you only want to ask for the user input.

hope it will help;
And because "cultivar" is an array of characters, the ampersand (&) is not required in the scanf().  In addition, the use of scanf() to read in strings should be avoided.  Use fgets() instead.

So:
[PHP]fgets( cultivar, sizeof(cultivar), stdin );[/PHP]

jon zendatta -

As for strcmp(), consider using strncmp() instead.  These functions return a value less than zero if the first string is less than the second; a zero if the strings are the same; and a value greater than zero if the first string is greater than the second.

You should consider using the if-else construct in your comparisons.  If you determine that "cultivar" is "braeburn", then there is no need to compare it to the other strings.

So something like this:
[PHP]
int dollars_ha = 0;
...
if ( strcmp( cultivar, "braeburn" ) == 0 )
{
  dollars_ha = (int)(dollars_per_carton * total_cartons / bb);
}
else if ( strcmp( cultivar, "royal gala" ) == 0 )
{
  dollars_ha = (int)(dollars_per_carton * total_cartons / rg);
}
...
else
{
  printf( "Error: Input '%s' not recognized.\n", cultivar );
}
printf("returns $%d per ha\n", dollars_ha);
[/PHP]

---

### Post by cmay on 2008-08-15
i think this may work. it compiled and i got result on my machine this way.

```
#include <stdio.h>
#include <string.h>

int main ()
{
   int bins, kgs, dollars_ha ;
   float packout, net_kg, dollars_per_carton, total_cartons, dollars_total;
   float bb = 2.5,                            /* these seven float constants represent the land area in hectares of each cultivar */
         rg = 1.0,
         f = 1.85,
         pb = 0.5,
         pr = 0.55,
         pq = 0.25,
         gs = 0.5;
   char str1[] = "braeburn"; 
   char str2[] = "royal gala";
   char str3[] = "fuji";
   char str4[] = "pacific beauty";
   char str5[] = "pacific queen";
   char str6[] = "pacific rose";
   char str7[] = "granny smith";
   char cultivar [15];

   printf("please enter cultivar\n"); /* input any name from str1-str7 */
   scanf("%s", &cultivar);
   printf("number of bins\n");
   scanf("%d", &bins);
   printf("enter packout\n");          
   scanf("%f", &packout);

   kgs = (bins * 320);                          /* one bin weighs 320kg */
   net_kg = (kgs * packout / 100);
   total_cartons = (net_kg / 18);               /* one carton of apples weighs 18kg */

   printf("enter $ per carton\n");
   scanf("%f", &dollars_per_carton);
  
   if (!strcmp(cultivar, str1)==0) 
   dollars_ha = (int)(dollars_per_carton * total_cartons / bb);      /* gross profit per hectare */
   printf("returns $%d per ha\n", dollars_ha);
   
   if (!strcmp(cultivar, str2)==0)
   dollars_ha = (int)(dollars_per_carton * total_cartons / rg);
   printf("returns $%d per ha\n", dollars_ha);
    
   if (!strcmp (cultivar, str3)==0)
   dollars_ha = (int)(dollars_per_carton * total_cartons / f);
   printf("returns $%d per ha\n", dollars_ha);
   
   if (!strcmp (cultivar,str4)==0)
   dollars_ha = (int)(dollars_per_carton * total_cartons / pb);
   printf("returns $%d per ha\n", dollars_ha);
  
   if (!strcmp (cultivar,str5)==0)
   dollars_ha = (int)(dollars_per_carton * total_cartons / pq);
   printf("returns $%d per ha\n", dollars_ha);
   
   if (!strcmp (cultivar,str6)==0)
   dollars_ha = (int)(dollars_per_carton * total_cartons / pr);
   printf("returns $%d per ha\n", dollars_ha);
   
   if (!strcmp (cultivar,str7)==0)
   dollars_ha = (int)(dollars_per_carton * total_cartons / gs);
   printf("returns $%d per ha\n", dollars_ha);

   return 0;
}
```

---

### Post by cmay on 2008-08-15
now when dwhitney64 shows the exampel then take this as a real good one.
you should also consider my suggestion as its a matter of me fixing the example so it produces an output but not as the better way to go about it.
i am newbie myselve in c :)

---

### Post by jon zendatta on 2008-08-16
cool sorry for my slow reply, just home from work.thanks heaps cmay & especially dwhitney67 :KS

---

### Post by jon zendatta on 2008-08-16
yes you are so right dwhitney67. i don't really comprehend the fgets() but maybe i will have to spend more time.as i did it the simpler way & only get correct output when using string constants braeburn or fuji.
cheers
```
#include <stdio.h>
#include <string.h>

int main ()
{
   int bins, kgs, dollars_ha ;
   float packout, net_kg, dollars_per_carton, total_cartons, dollars_total;
   float bb = 2.5,                            /* these seven float constants represent the land area in hectares of each cultivar */
         rg = 1.0,
         f = 1.85,
         pb = 0.5,
         pr = 0.55,
         pq = 0.25,
         gs = 0.5;
   char str1[] = "braeburn"; 
   char str2[] = "royal gala";
   char str3[] = "fuji";
   char str4[] = "pacific beauty";
   char str5[] = "pacific queen";
   char str6[] = "pacific rose";
   char str7[] = "granny smith";
   char cultivar [15];

   printf("please enter cultivar\n"); /* input any name from str1-str7 */
   scanf("%s", &cultivar);
   printf("number of bins\n");
   scanf("%d", &bins);
   printf("enter packout\n");          
   scanf("%f", &packout);

   kgs = (bins * 320);                          /* one bin weighs 320kg */
   net_kg = (kgs * packout / 100);
   total_cartons = (net_kg / 18);               /* one carton of apples weighs 18kg */

   printf("enter $ per carton\n");
   scanf("%f", &dollars_per_carton);

   if ( strcmp( cultivar, "braeburn" ) == 0 )
   {
   dollars_ha = (int)(dollars_per_carton * total_cartons / bb);
   }
   else if ( strcmp( cultivar, "royal gala" ) == 0 )
   {
   dollars_ha = (int)(dollars_per_carton * total_cartons / rg);
   }
   else if ( strcmp( cultivar, "fuji" ) == 0 )
   {
   dollars_ha = (int)(dollars_per_carton * total_cartons / f);
   }
   else if ( strcmp ( cultivar, "pacific beauty" ) == 0 )
   {
   dollars_ha = (int)(dollars_per_carton * total_cartons / pb);
   }
   else if ( strcmp( cultivar, "pacific queen" ) == 0 )
   {
   dollars_ha = (int)( dollars_per_carton * total_cartons / pq);
   }
   else if ( strcmp( cultivar, "pacific rose" ) == 0 )
   {
   dollars_ha = (int)( dollars_per_carton * total_cartons / pr);
   }
   else if ( strcmp( cultivar, "granny smith" ) == 0 )
   {
   dollars_ha = (int)( dollars_per_carton * total_cartons / gs);
   }
   else
   {
   printf( "Error: Input '%s' not recognized.\n", cultivar );
   }
   printf("returns gross $%d per ha\n", dollars_ha);  

   return 0;
   }
  
```

---

### Post by WW on 2008-08-16
> **jon zendatta said:**
> yes you are so right dwhitney67. i don't really comprehend the fgets() but maybe i will have to spend more time.as i did it the simpler way & only get correct output when using string constants braeburn or fuji.

scanf assumes that the data to be input is delimited by whitespace.  "fuji" and "braeburn" are the only strings without spaces, so they work.  If you type in "royal gala", cultivar will be "royal".  Here's a quick test:

scanf_string_test.c
```

#include <stdio.h>

int main()
    {
    char buf[256];
    
    scanf("%s",buf);
    printf("buf = \"%s\"\n",buf);
    return 0;
    }

```
```

$ gcc -Wall scanf_string_test.c -o scanf_string_test
$ ./scanf_string_test 
royal gala
buf = "royal"
$ 

```

---

### Post by cmay on 2008-08-16
this is the solution i came up whit after reading dwhitney64 post
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char** argv)
{ 
	char input[30];
	char test[] = "hello world\n";
	printf("please type hello world\n");
	fgets(input,sizeof (input),stdin);
	if( strcmp(input,test)==0){
		printf("hurrayyy it works \n");
	}
	else printf("INVALID INPUT\n");
	
	return 0;
}

```
i dont know if its any use to you .

---

### Post by dwhitney67 on 2008-08-16
Through experimentation, I realized there is one little caveat to using fgets() when reading input from a user... the terminating carriage return (enter) given during input could potentially be stored in the buffer.

This will present a problem when performing strcmp().  Hence the reason why it is recommended to use strncmp(), along with perhaps another useful test (e.g. string length).

Another alternative (and probably easier) is to remove the carriage return character from the input buffer.  Here's an example that also employs strncmp():
[PHP]#include <stdio.h>
#include <string.h>

int main()
{
  char *magic = "Walla Walla";
  char input[32] = {0};          // initialize buffer to null

  printf( "Enter the magic phrase: " );
  fgets( input, sizeof(input), stdin );

  // Replace the terminating carriage return (if any) with a null-character
  char *pos = strchr( input, '\n' );
  if ( pos )
  {
    *pos = '\0';
  }

  if ( strncmp( input, magic, strlen(magic) ) == 0 )
  {
    printf( "Great guess!  You are right.  The magic phrase is '%s'\n", magic );
  }
  else
  {
    printf( "Sorry you guessed wrong.\n" );
  }

  return 0;
}[/PHP]

---

### Post by jon zendatta on 2008-08-16
ok that makes sense thanks Cmay i will a try now before work & reply in 12 hours.:KS

---

### Post by jon zendatta on 2008-08-16
off the topic slightly but how do i thank people for useful posts?

---

### Post by cmay on 2008-08-16
you can press that little button on the user panel.
and there is a button also to report spam or harrasment or these things.
you have to be logged in to see it however.
i use the thank you too look up on other users too see the useful posts i can learn from.
i thanked dwhitney64 for his post here since its was very good adwise from someone who knows what he is doing and its great you and i could learn from it also.

---

