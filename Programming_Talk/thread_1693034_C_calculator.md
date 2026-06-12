---
title: "C calculator"
date: 2011-02-22
forum: Programming Talk
---

### Post by med linux on 2011-02-22
[B][FONT=Arial][SIZE=5][COLOR=Red]hi guys 
I created and calculator with c language 
this is my code 
[/COLOR][/SIZE][/FONT][/B]```

[B][FONT=Arial][SIZE=5][COLOR=Red] #include <stdio.h>
main()
{
    int x;
    char a;
    int y;
    printf ("********************************************************************************************\n");
    printf ("*                               Welcome                                                    *\n");
    printf ("*                          Walcultor with C                                                *\n");
    printf ("********************************************************************************************\n");
    printf (" choose operator  : \n 1 : (+) \n 2 : (-) \n 3 : (*) \n 4 : (/) \n ");
    scanf ( "%c", &a );
    printf ( "input a number : \n");
    scanf ( "%d",&x);
    printf ("input a second number : \n");
    scanf ("%d" , &y);
    printf ("\n");
    if ( a=='1' )
    {
    printf ("%d + %d = %d ",x,y,x+y);
    }
    else if (a=='2')
    {
    printf ("%d - %d = %d ",x,y,x-y);
    }
    else if (a=='3')
    {
    printf ("%d * %d = %d ",x,y,x*y);
    }
    else if (a=='4')
    {
    printf ("%d / %d = %d ",x,y,x/y);
    }
    else  printf (" !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  ");
    printf ("\n");
}
[/COLOR][/SIZE][/FONT][/B]
```
[B][FONT=Arial][SIZE=5][COLOR=Red] but the problem is when I
i change the place of
[/COLOR][/SIZE][/FONT][/B]```

[B][FONT=Arial][SIZE=5][COLOR=Red]     printf (" choose operator  : \n 1 : (+) \n 2 : (-) \n 3 : (*) \n 4 : (/) \n ");
    scanf ( "%c", &a );

[/COLOR][/SIZE][/FONT][/B]
```
[B][FONT=Arial][SIZE=5][COLOR=Red] like that 

[/COLOR][/SIZE][/FONT][/B]```

[B][FONT=Arial][SIZE=5][COLOR=Red] #include <stdio.h>
main()
{
    int x;
    char a;
    int y;
    printf ("********************************************************************************************\n");
    printf ("*                               Welcome                                                    *\n");
    printf ("*                          Walcultor with C                                                *\n");
    printf ("********************************************************************************************\n");
    printf ( "input a number : \n");
    scanf ( "%d",&x);
    printf (" choose operator  : \n 1 : (+) \n 2 : (-) \n 3 : (*) \n 4 : (/) \n ");
     scanf ( "%c", &a );
    printf ("input a second number : \n");
    scanf ("%d" , &y);
    printf ("\n");
    if ( a=='1' )
    {
    printf ("%d + %d = %d ",x,y,x+y);
    }
    else if (a=='2')
    {
    printf ("%d - %d = %d ",x,y,x-y);
    }
    else if (a=='3')
    {
    printf ("%d * %d = %d ",x,y,x*y);
    }
    else if (a=='4')
    {
    printf ("%d / %d = %d ",x,y,x/y);
    }
    else  printf (" !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  ");
    printf ("\n");
}
[/COLOR][/SIZE][/FONT][/B]
```
[B][FONT=Arial][SIZE=5][COLOR=Red] the laste code source is not able to read %a
why ?[/COLOR][/SIZE][/FONT][/B]

---

### Post by Arndt on 2011-02-22
Try again. Don't make the code red, don't make it so large, and the tags are not <code> but in [ ] brackets.

---

### Post by med linux on 2011-02-22
Ok ...........

---

### Post by Tony Flury on 2011-02-22
[QUOTE=med linux;10483178][the laste code source is not able to read %a
why ?/QUOTE]

If you promise never to post code bolded and red again - i will tell you : 

when you do 

```

   printf ( "input a number : \n");
    scanf ( "%d",&x);
    printf (" choose operator  : \n 1 : (+) \n 2 : (-) \n 3 : (*) \n 4 : (/) \n ");
     scanf ( "%c", &a );

```
 and the user types a number and presses return - the first scanf gets the number - and leaves the return in the buffer.

The 2nd scanf then reads that return.

The solution is to strip off any characters you don't want out of the input buffer between your scanf's

```

c = getchar() ; 
while( c != '\n')
     c = getchar() ;

```

this will strip everything out of the buffer up to and including the return character - so the next thing in the buffer should be your operator character.

---

### Post by slooksterpsv on 2011-02-22
%s works, but %c doesn't.

---

### Post by med linux on 2011-02-22
thenk you verry much ! 

&

good night

---

### Post by Tony Flury on 2011-02-23
> **slooksterpsv said:**
> %s works, but %c doesn't.

You should not use %s to read into a char - classic buffer overflow territory. I agree it is not an issue with this trivial application, but not a good habit to get into.

---

### Post by slooksterpsv on 2011-02-23
> **Tony Flury said:**
> You should not use %s to read into a char - classic buffer overflow territory. I agree it is not an issue with this trivial application, but not a good habit to get into.

Good to know, i didn't know that, but the getchar didn't work for me, still skipped past the part. Even with 2+ getch's it fails.

---

### Post by Tony Flury on 2011-02-23
> **slooksterpsv said:**
> Good to know, i didn't know that, but the getchar didn't work for me, still skipped past the part. Even with 2+ getch's it fails.

did you try the loop that i suggested - it is the normal way of emptying the buffer up the next return ?

Actually it could be : 

```

while( getch() != '\n') ;

```

---

### Post by slooksterpsv on 2011-02-24
> **Tony Flury said:**
> did you try the loop that i suggested - it is the normal way of emptying the buffer up the next return ?

Actually it could be : 

```

while( getch() != '\n') ;

```

Yeah, I tried your code, it didn't work, the while loop, it just skipped past it.

Sorry if that sounded rude, I'm just so fed up with Windows today I'm irritated.

---

### Post by Arndt on 2011-02-24
> **slooksterpsv said:**
> Yeah, I tried your code, it didn't work, the while loop, it just skipped past it.

Sorry if that sounded rude, I'm just so fed up with Windows today I'm irritated.

What and whose problem are we trying to solve now? Not the OP's? Do you have example code?

---

### Post by slooksterpsv on 2011-02-25
> **Arndt said:**
> What and whose problem are we trying to solve now? Not the OP's? Do you have example code?

Yup I'm on a different machine and I reproduced the error, here's the code
```

#include <stdio.h>
main()
{
    int x;
    char a;
    int y;
    printf ("********************************************************************************************\n");
    printf ("*                               Welcome                                                    *\n");
    printf ("*                          Walcultor with C                                                *\n");
    printf ("********************************************************************************************\n");
    printf ( "input a number : \n");
    scanf ( "%d",&x);
    printf (" choose operator  : \n 1 : (+) \n 2 : (-) \n 3 : (*) \n 4 : (/) \n ");
    a = getchar();
    while (a != '\n')
	a = getchar();
    printf ("input a second number : \n");
    scanf ("%d" , &y);
    printf ("\n");
    if ( a=='1' )
    {
    printf ("%d + %d = %d ",x,y,x+y);
    }
    else if (a=='2')
    {
    printf ("%d - %d = %d ",x,y,x-y);
    }
    else if (a=='3')
    {
    printf ("%d * %d = %d ",x,y,x*y);
    }
    else if (a=='4')
    {
    printf ("%d / %d = %d ",x,y,x/y);
    }
    else  printf (" !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  ");
    printf ("\n");
}

```

If I do scanf then getchar, it works, wait is it getch (which I thought was C++) or getchar (which is C)?

EDIT: It's getchar, cause getch is a conio.h function which isn't in the standard library.

---

### Post by Arndt on 2011-02-25
> **slooksterpsv said:**
> Yup I'm on a different machine and I reproduced the error, here's the code
```

#include <stdio.h>
main()
{
    int x;
    char a;
    int y;
    printf ("********************************************************************************************\n");
    printf ("*                               Welcome                                                    *\n");
    printf ("*                          Walcultor with C                                                *\n");
    printf ("********************************************************************************************\n");
    printf ( "input a number : \n");
    scanf ( "%d",&x);
    printf (" choose operator  : \n 1 : (+) \n 2 : (-) \n 3 : (*) \n 4 : (/) \n ");
    a = getchar();
    while (a != '\n')
	a = getchar();
    printf ("input a second number : \n");
    scanf ("%d" , &y);
    printf ("\n");
    if ( a=='1' )
    {
    printf ("%d + %d = %d ",x,y,x+y);
    }
    else if (a=='2')
    {
    printf ("%d - %d = %d ",x,y,x-y);
    }
    else if (a=='3')
    {
    printf ("%d * %d = %d ",x,y,x*y);
    }
    else if (a=='4')
    {
    printf ("%d / %d = %d ",x,y,x/y);
    }
    else  printf (" !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  ");
    printf ("\n");
}

```

If I do scanf then getchar, it works, wait is it getch (which I thought was C++) or getchar (which is C)?

EDIT: It's getchar, cause getch is a conio.h function which isn't in the standard library.

In any case, I recommend that you simply never use 'scanf', for any purpose. Read a whole line (ignoring empty lines if you want), and then read from that line.

---

