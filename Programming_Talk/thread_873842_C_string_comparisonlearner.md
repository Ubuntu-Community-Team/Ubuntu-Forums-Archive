---
title: "C string comparison/learner"
date: 2008-07-29
forum: Programming Talk
---

### Post by jon zendatta on 2008-07-29
hell0 
i am a C learner, writing some interactive code for my 5yr old child.some problem here with this string comparison.have omitted the rest so the world doesn't laugh at me

   char birthday [10];
   char string3[] = "january 4";
 
   if(strcmp (birthday, string3) == 0)
      printf("true\n");

thanks anyone

---

### Post by Zugzwang on 2008-07-29
It would be wise to state what your actual problem is. BTW: In your code, you don't initialise the birthday string. There should be some command to fill it with data. Maybe you forgot a "scanf" or something like that?

---

### Post by unoodles on 2008-07-29
I think strcmp returns 1 on success, I could be mistaken. Also strcmp is case sensitive, you may want to try strcasecmp().

---

### Post by dwhitney67 on 2008-07-29
> **unoodles said:**
> I think strcmp returns 1 on success, I could be mistaken. Also strcmp is case sensitive, you may want to try strcasecmp().
strcmp() returns 0 if both string are identical; less than zero if string 1 is less than string 2, or greater than zero if string 1 is greater than string 2.


[PHP]
...
const char *correctDate = "December 25, 2001";

while (1)
{
  char birthday[20] = {0};

  printf( "Enter your birthday (ex. January 10, 1970): " );
  fgets( birthday, sizeof(birthday), stdin );

  if ( strncmp( correctDate, birthday, strlen(correctDate) ) == 0 )
  {
    printf( "Good... you are correct!\n" );
    break;
  }
  else
  {
    printf( "Sorry... try again.\n" );
  }
}
...
[/PHP]

---

