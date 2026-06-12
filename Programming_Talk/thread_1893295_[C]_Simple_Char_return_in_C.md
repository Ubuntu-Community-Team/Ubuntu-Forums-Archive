---
title: "[C] Simple Char return in C"
date: 2011-12-09
forum: Programming Talk
---

### Post by Talamare on 2011-12-09
Im sorry if this is an easy question, but this is project is due tomorrow, Ive been working on it for days now and my head wants to explode and cry

the project is to write several functions within a single program, and im stuck on this part

I need to scanf a double number thats the guys grade then use a function to tell him what letter grade he got

my current code is 


```
double grade(double gradeX, char finalX){
        char letter;
        if((gradeX <= 100)&&(gradeX >= 90)){
            letter = 'A';
        }else{
            if((gradeX < 90)&&(gradeX >= 80)){
                letter = 'B';
            }else{
                if((gradeX < 80)&&(gradeX >= 70)){
                    letter = 'C';
                }else{
                    if((gradeX < 70)&&(gradeX >= 60)){
                        letter = 'D';
                    }else{
                        if((gradeX < 60)&&(gradeX >= 0)){
                            letter = 'F';
                        }}}}}
    return letter;
}
``````
                        double gradeY=0;
                        char finalY;
                        do{
                        scanf("%lf", &gradeY);
                        }while((gradeY > 100)||(gradeY < 0));
                        
                        printf("%lf %c", grade(gradeY, finalY));
```whenever i put any number it always return the number 70 with a few rare exception where it returns a number between 70-65
simple fixes please, i cant be putting complex/advance code in beginners C

---

### Post by isaacj87 on 2011-12-10
Are double data types a requirement for the project?

Here are my modifications to what you have. This compiles and works correctly for me, but it's ugly and I did it kind of quick.

<snipped code!>

Essentially, your grade function works. Aside from using "else if", I made no other changes to the function. I also removed the need for a second arg and changed the returning data type to a char. I figured if we're returning a letter, it shouldn't be a double.

EDIT: I've removed my code snippet as 11jmb is correct. If I simply write it for you, you won't learn anything. However, I will assist you in any way I can.

---

### Post by 11jmb on 2011-12-10
This board isn't for homework, so you're on you're own for the most part.

I will give you some general tips though:
1.read about the primitive data types and how they are actually used. You should be able to give general descriptions on the similarities and differences between int, short, long, char, float, double, and _Bool.
2.read more into what printf actually does, specifically what the 'f' stands for, and what it means for your program.

If you spend enough time reading about the above topics, I guarantee that you will figure out the answer for yourself. And then you actually will have learned something instead of having somebody in an online forum do your homework for you.

three more tips that are not necessary to solving your problem but will make your code a bit better (and will probably get you a better grade):
1. use 'else if' in your grade function
2. prompt the user to enter a grade instead of just reading directly
3. look into whether all of the arguments for your grade function are necessary

---

### Post by Talamare on 2011-12-10
> **isaacj87 said:**
> Are double data types a requirement for the project?

Here are my modifications to what you have. This compiles and works correctly for me, but it's ugly and I did it kind of quick.
Essentially, your grade function works. Aside from using "else if", I made no other changes to the function. I also removed the need for a second arg and changed the returning data type to a char. I figured if we're returning a letter, it shouldn't be a double.
"char grade (int gradeX);" THIS
THIS DID IT!! OMG!!!

I cant believe that all I needed to do was change the word 'double' to 'char'

Thank you sooooooooo much!

---

### Post by isaacj87 on 2011-12-10
> **Talamare said:**
> "char grade (int gradeX);" THIS
THIS DID IT!! OMG!!!

I cant believe that all I needed to do was change the word 'double' to 'char'

Thank you sooooooooo much!

Lol, well it would appear I edited my post too late. ;)

In any case, yes, your function was trying to return a double value. This didn't make sense considering you were trying to get a char back.

I'd definitely look into what 11jmb suggested above. If you have a good handle on the basics of functions, data types, conversion specifiers, you'll definitely avoid some head-bashing and/or crying later on. :)

---

### Post by 11jmb on 2011-12-10
> **Talamare said:**
> "char grade (int gradeX);" THIS
THIS DID IT!! OMG!!!

I cant believe that all I needed to do was change the word 'double' to 'char'

Thank you sooooooooo much!

In spite of your success, I still recommend my little homework assignment if you have time.

a firm grasp on primitives and formatting will help you understand why isaacj87's code worked and your's did not.

---

### Post by lisati on 2011-12-10
> **isaacj87 said:**
> Lol, well it would appear I edited my post too late. ;)

In any case, yes, your function was trying to return a double value. This didn't make sense considering you were trying to get a char back.

I'd definitely look into what 11jmb suggested above. If you have a good handle on the basics of functions, data types, conversion specifiers, you'll definitely avoid some head-bashing and/or crying later on. :)

+1

My $0.02: it's sometimes one easily overlooked relatively small thing that can mess things up, so having a good grasp of the basics won't hurt.

---

### Post by Talamare on 2011-12-10
learning that I dont need }{ between else and if is nice too, makes the code look cleaner

it may seem like im slacking by asking for help but i really do study hard, its just the power points they give us are borderline worthless and then they just tell us to type programs, i actually learned as much as i did from googling things

the only guy in the class who is able to do these stuff properly is someone whos actually a paid programmer nearly everyone else is even still behind me (and they pay the programmer to write their stuff for them) >_<

I definitely read up the guides he pointed to after i finish this demonic task ^_^

---

### Post by 11jmb on 2011-12-10
> **Talamare said:**
> it may seem like im slacking asking for help

Asking for help is good. There are plenty of people on this board who would be happy to help.

Posting code and saying "I need help with homework" is frowned upon, so try to ask about concepts or specific errors if you can.

---

### Post by 11jmb on 2011-12-10
> **siyaji said:**
> basically char is for character and it will return any type only if it is accepting any data type at the the of function or data definition/deceleration



OK, I'm a strong C programmer, and this even confused me. a char is just a byte of data representing an unsigned number [0-255]. This byte can also represent a character on the ASCII table (which is why you were only getting 65-70 when you treated a char as a double)


Another good practice is to add the -Wall flag to your compile command. It stands for "warn all", meaning that wit will generate a lot of warnings that are not necessarily compiler errors, but will point out sources of potential logic or runtime errors. I guarantee -Wall would have warned you about the double/char problem

---

### Post by Talamare on 2011-12-10
> **11jmb said:**
> Another good practice is to add the -Wall flag to your compile command. It stands for "warn all", meaning that wit will generate a lot of warnings that are not necessarily compiler errors, but will point out sources of potential logic or runtime errors. I guarantee -Wall would have warned you about the double/char problem

Sorry but... what?

---

### Post by 11jmb on 2011-12-10
how are you compiling your code?

---

### Post by Talamare on 2011-12-10
> **11jmb said:**
> how are you compiling your code?

Visual Studios C++ 2010 Express,;
Hit F5 to make the program work;

---

### Post by 11jmb on 2011-12-10
Oh, sorry. I made the unfair assumption that you were using gcc.

For VS, you should use /Wall. the link will show you how to set the warning level

[http://msdn.microsoft.com/en-us/library/thxezb7y.aspx](http://msdn.microsoft.com/en-us/library/thxezb7y.aspx)

---

### Post by Talamare on 2011-12-10
> **11jmb said:**
> Oh, sorry. I made the unfair assumption that you were using gcc.

For VS, you should use /Wall. the link will show you how to set the warning level

[http://msdn.microsoft.com/en-us/library/thxezb7y.aspx](http://msdn.microsoft.com/en-us/library/thxezb7y.aspx)

Ah cool;

Do i just type /wall at the start of the program?;

---

### Post by 11jmb on 2011-12-10
no, scroll down to the section that says 
> To set this compiler option in the Visual Studio development environment
and follow the instructions

Also, make sure to capitalize the 'W'

---

### Post by squenson on 2011-12-10
Hint: could you get the letter 'E' with your code?

---

### Post by 11jmb on 2011-12-10
> **squenson said:**
> Hint: could you get the letter 'E' with your code?

Or the number 69 in the original code :D

---

### Post by Vaphell on 2011-12-10
i could swear i have seen this school project some time ago :-)

@OP, if you test against score ranges in a descending order you can drop the upper bound check.
If you test for 90+, then for 80+ - score=95 can't get this far, because it went into the preceding path already. Same thing with 70+ - anything 80+ was consumed by the previous tests so you can be 100% sure than only numbers below 80 get this far.
In other words you are good to go with
score>=90
score>=80
...

also you can use an array and a bit of math to translate tested score to the grade in a single stroke. Score ranges are regular so math covers them nicely.
```

int grade_count[5] = {0}
char grade[] = "FDCBA"; //0->F, 1->D, 2->C, 3->B, 4->A
int score;
...
//incrementing grade counter
grade_count[score<50?0:(score==100?4:(score/10-5))]++;
...
//final result
for( i=4; i>=0; i-- )
    printf( "grade %c: %d\n", grade[i], grade_count[i] );
```

**score<50 ? 0 : ( score==100 ? 4 : (score/10-5 ) )** sets 0 (F) for score<50, 4(A) for 100 and first_digit-5 to everything else (ie 65-> 6-5=1 (D), 88-> 8-5=3 (B))

you could also write a mechanism that tests against arbitrary thresholds stored in an array (in this case{0,60,70,80,90}) . Go through the array, if score>=threshold the index identifies the grade.

---

### Post by Bachstelze on 2011-12-10
> **11jmb said:**
> OK, I'm a strong C programmer, and this even confused me. a char is just a byte of data representing an unsigned number [0-255].

Wrong, char may be signed. It is compiler-dependent whether char is signed or unsigned (so if you want to be sure of the signedness, use signed char or unsigned char).

Also...

> **isaacj87 said:**
> EDIT: I've removed my code snippet as 11jmb is correct. If I simply write it for you, you won't learn anything. However, I will assist you in any way I can.

Personally I am a strong believer in learning by example. If someone doesn't know how to do something, show them code that does it and let them learn from it and ask specific questions about parts of the code if they don't understand something. From my experience, walking someone through simple things is just a waste of both your and their time. This is not grade school.

---

### Post by 11jmb on 2011-12-10
> **Bachstelze said:**
> Wrong, char may be signed. It is compiler-dependent whether char is signed or unsigned (so if you want to be sure of the signedness, use signed char or unsigned char).


Correct, this was a complete brain-fart on my part. (perhaps looking like a fool is my punishment for writing nothing but Java all week?) Anyway thanks for correcting, in fact, most compilers I have used have defaulted to signed.


> **Bachstelze said:**
> 
Personally I am a strong believer in learning by example. If someone doesn't know how to do something, show them code that does it and let them learn from it and ask specific questions about parts of the code if they don't understand something. From my experience, walking someone through simple things is just a waste of both your and their time. This is not grade school.

Yes, but not when somebody comes on here asking the forums to do his homework. Then, I think treating it like grade school is completely justified.

---

