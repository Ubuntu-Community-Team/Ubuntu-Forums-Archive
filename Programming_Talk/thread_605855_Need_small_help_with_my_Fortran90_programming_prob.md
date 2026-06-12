---
title: "Need small help with my Fortran90 programming problems."
date: 2007-11-07
forum: Programming Talk
---

### Post by Chaoic16 on 2007-11-07
I am new to this forum, and I have been having great interest into programming using computer language.  I am currenlty learning Java and Fortran90 before moving on to C++.  However, I have been having a problem with my own project, and I am wondering if one of you would help me with this.

I had been havintg some troubles doing DO loops and using array, especially SIN() functions.  This is program I've written:

PROGRAM project_3_b

! delcaring REAL variable with dimensions
REAL::a(1:20),b(0:19),c(10:29),d(-9:10)

! the REAL, PARAMETER pi
REAL, PARAMETER::pi=3.1415926,pi_by_2=pi/20

! input the arrow 'a' values to be 1, .., 10 with implied do loop
statement (page 206-207)
arr=(/(a,a=1,10)/)

! then write loops which compute
! 1) the array 'b' to equal the array 'a times 0.5'
DO b=a,0.5

! 2) the array 'c' to equal the SIN() function of the array 'b times pi'

       DO c=SIN(b,pi)

! 3) the array 'd' to equal LOG(SIN(b*pi ) ) only if the values of
sin(pi*a ) > 0 else 'd=0'
! HINT: for this you must use a DO loop with 'IF ELSE'

               IF (SIN(pi*a)>0) THEN
                       DO d=LOG(SIN(b*pi))
               ELSE
                       DO d=0

               END DO
       END DO
END DO

PROGRAM project_3_b

See where I still am struggling with DO loops and SIN() functions, so I am wondering if one of you would be more than to point to where I am doing wrong.  Any advices from you will be truly appericated!


Chaoic out...

---

### Post by xtacocorex on 2007-11-07
You should use the [ code ] [ /code ] tags for your code (remove the spaces between the [] and the words.
 
I'm currently at work, but will try to check it out tonight sometime.
 
Also, your PI/2 is set to PI/20

---

### Post by Chaoic16 on 2007-11-07
Thank you, I truly appericate that!

:)


Chaoic out...

---

### Post by xtacocorex on 2007-11-07
You're not setting up the loops correctly.
 
First, you need to specify an integer for loop counting:
```
INTEGER :: i
```
 
For the first loop, setting the values for a:
- I haven't done implicit loop assigning of values, just printing, so this might work
```
(a(i), i = 1, 20)
```
 
For the second loop, setting the values for b:
- Assuming the code for a works, the code should be like this
```

do i = 0, 19
    b(i) = a(i+1)*0.5
end do

```
I'm using a(i+1) because of how you defined the bounds for array b.  You set a lower bounds for all of your arrays, but their ranges are all 20.
 
For the third loop, setting values for c:
```

do i = 10, 29
    c(i) = sin(b(i-10)*pi)
end do

```
Using b(i-10) because of how you defined the bounds for array c.
 
For the last loop, setting the values for d:
```

do i = -9, 10
    ! check sin of a value times pi
    if (sin(a(i+10)*pi) .gt. 0) then
        d(i) = log(sin(b(i+9)*pi))
    else
        d(i) = 0.0
end do

```
Again, you have to be aware of the bounds you set on the arrays to make sure you're pulling the right value from memory.
 
You were trying to set array segments in the loop definition, which won't work.

---

### Post by Chaoic16 on 2007-11-07
My problem is all solved, thank to all of you who gave me an advices and pointed me to specific problems in my coding.  I read Fortran90 book again, took your advice in fixing my codes and they are working smoothly now.   I truly appericate all of your advices and helps!

:)


Chaoic out...

---

