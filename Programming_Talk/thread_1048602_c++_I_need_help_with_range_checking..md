---
title: "c++ I need help with range checking."
date: 2009-01-23
forum: Programming Talk
---

### Post by Vandorin on 2009-01-23
I'm writing a code for my computer class, it's a random number generator, and it asks you to choose a number. Based on your answer, it tells you if the number you picked is too high, too low, or close (within a 5 number range of the number picked). I am having problems with the "close" part. I emailed my teacher, and he said to use range checking, but I can't find it in our text book, and when I Google it, it comes up with something I don't understand lol. All my teacher told me is that I would set up 2 tests and use &&. Does anyone know how to do range checking?

-Thanks.

---

### Post by Tony Flury on 2009-01-23
Range checking is simply checking that a number is within a defined range - for instance : is x between 15 and 20.

You know what your range is (you defined what close meant) and you know the number you need to check against that range.

does that help ?

---

### Post by monkeyking on 2009-01-23
Normally I would use the expression "range checking" when i'm talking about picking elements in an array/vector type datastructure.

There are many ways to do this,
I would use the following way.
[PHP]
int picknumber(int lower,int upper){
   int randomnumber = yourrandomgenerator()

   if(abs(randomnumber-lower)<5 || abs(upper-randomnumber)< 5){
      printf("your randomnumber is to close:%d\n",randomnumber)
      exit(0)
   }else
      return randomnumber;
}
[/PHP]
The abs function just returns the positive value of your number,
that is just removes the negative sign if its negative.

good luck

btw I didn't check the code for typos, but it should give you and idea.
Remember to compile with -Wall,
this will catch many errors.

---

### Post by Vandorin on 2009-01-23
> **monkeyking said:**
> Normally I would use the expression "range checking" when i'm talking about picking elements in an array/vector type datastructure.

There are many ways to do this,
I would use the following way.
[PHP]
int picknumber(int lower,int upper){
   int randomnumber = yourrandomgenerator()

   if(abs(randomnumber-lower)<5 || abs(upper-randomnumber)< 5){
      printf("your randomnumber is to close:%d\n",randomnumber)
      exit(0)
   }else
      return randomnumber;
}
[/PHP]
The abs function just returns the positive value of your number,
that is just removes the negative sign if its negative.

good luck

btw I didn't check the code for typos, but it should give you and idea.
Remember to compile with -Wall,
this will catch many errors.

Here is my code so far with the abs() function included
```

#include <iostream>

#include <cstdlib>

#include <ctime>

using namespace std;

void main()
{
       float num;

       srand( (unsigned)time( NULL ) );

       int randn = (rand()%100)+1 ;

       cout << "Please pick a number from 1 to 100" << endl;

       cin >> num;

       if ( num < randn ) {
               cout << "The number is too low " << endl;
       } else if ( num > randn ) {
               cout << "The number is too high " << endl;
       } else if ( abs(randn - num) <=5 ) {
               cout << "You were very close" << endl;
	   } else if ( abs(randn - num) >=5 ) {
			   cout << "You were very close" << endl;
	   }
        else if ( num == randn ) {
               cout << "You guessed right!" << endl;
       }

       cout << randn << " " << "Was the correct number" << endl;

       system("pause");

}

``` 
I think it's right, but I'm not used to the abs() function, my teacher hasn't even taught it :(.

---

### Post by Krupski on 2009-01-23
> **Vandorin said:**
> I'm writing a code for my computer class, it's a random number generator, and it asks you to choose a number. Based on your answer, it tells you if the number you picked is too high, too low, or close (within a 5 number range of the number picked). I am having problems with the "close" part. I emailed my teacher, and he said to use range checking, but I can't find it in our text book, and when I Google it, it comes up with something I don't understand lol. All my teacher told me is that I would set up 2 tests and use &&. Does anyone know how to do range checking?

-Thanks.

Not gonna do your homework for you... but this SNIPPET should help:


```

if((guess < (random + 5)) && (guess > (random - 5))) {
    fprintf(stdout, "CLOSE... but not quite. Try again!\n");
    fflush(stdout);
} else {
    fprintf(stdout, "Nope... try again!\n");
    fflush(stdout);
}

```


This is so simple it doesn't need comments... hope this helps.

---

### Post by Vandorin on 2009-01-23
> **Krupski said:**
> Not gonna do your homework for you... but this SNIPPET should help:


```

if((guess < (random + 5)) && (guess > (random - 5))) {
    fprintf(stdout, "CLOSE... but not quite. Try again!\n");
    fflush(stdout);
} else {
    fprintf(stdout, "Nope... try again!\n");
    fflush(stdout);
}

```



This is so simple it doesn't need comments... hope this helps.

I'm not asking you to do my homework for me, I'm simply asking for help because I do not understand one part of it. Is that wrong? And as for the second part of your post, thank you, that does clear some things up, and I will hopefully be able to get it to work now.

---

### Post by Krupski on 2009-01-23
> **Vandorin said:**
> I'm not asking you to do my homework for me, I'm simply asking for help because I do not understand one part of it. Is that wrong? And as for the second part of your post, thank you, that does clear some things up, and I will hopefully be able to get it to work now.

Sorry... I'm on the staff at the local university here and I *ALWAYS* run into students who want me to hand them all the answers for free. My bad. Sorry.

-- Roger

---

### Post by monkeyking on 2009-01-23
Using your coding style, this would do the trick.

[PHP]
int main(){
  
  
  srand( (unsigned)time( NULL ) );
  
  int randn = (rand()%100)+1 ;
  printf(" number to guess is:%d\n",randn);
  

  cout << "Please pick a number from 1 to 100" << endl;
  while(1){ //continue looping until return statement
    int num; // this should be int not float
    cin >> num;
    if (num==randn ){
      cout << "you guessed correct: \n";
      return 0;
    } 
    int dif = abs(randn-num);
    if ( dif <=5 ) 
      cout << "You were very close \n";
    else if ( num < randn ) 
      cout << "The number is too low \n";
    else if ( num > randn ) 
      cout << "The number is too high \n";
    
  }
  //code never reaches here
}
[/PHP]
About your version, you should not use float, but int.
And the program keeps looping in the while statement.

good luck

edit:
the "\n" is a shorter way of writing <<endl

---

### Post by Vandorin on 2009-01-23
Ok this is the code I have so far, and I am going to talk with a friend tommorow who's in the same class and see how he's done his. Thanks for the help :D

```


#include <iostream>

#include <cstdlib>

#include <ctime>

using namespace std;

void main()
{
      float num;

      srand( (unsigned)time( NULL ) );

      int randn = (rand()%100)+1 ;

      cout << "Please pick a number from 1 to 100" << endl;

      cin >> num;

      if ( num < randn ) {
              cout << "The number is too low " << endl;
      } else if ( num > randn ) {
              cout << "The number is too high " << endl;
          } else if ( ( num < randn + 5 ) && ( num > randn + 5 ) ) {
                               cout << "You were close!" << endl;

          }
       else if ( num == randn ) {
              cout << "You guessed right!" << endl;
      }

      cout << randn << " " << "Was the correct number" << endl;

      system("pause");

}

```

---

### Post by Wybiral on 2009-01-23
```
( num < randn + 5 ) && ( num > randn + 5 )
```

This wont work. It can't ever be greater than AND less than some value at the same time :)

You probably meant:
```
( num < randn + 5 ) && ( num > randn - 5 )
```

---

### Post by Krupski on 2009-01-23
> **Wybiral said:**
> ```
( num < randn + 5 ) && ( num > randn + 5 )
```

This wont work. It can't ever be greater than AND less than some value at the same time :)

You probably meant:
```
( num < randn + 5 ) && ( num > randn - 5 )
```

Well since we're posting code... here's the one I did:

```

#include <stdio.h>
#include <stdlib.h>

int
main(void) {

    int random, guess, count;
    char buffer[BUFSIZ];

    while(1) {

        random = (rand() % 100);

        (count = 0); (guess = 0);

        fprintf(stdout, "\nGuess the number between 0 and 100!\n");
        fprintf(stdout, "(Enter -99 to exit the game)\n");
        fflush(stdout);

//        fprintf(stdout, "debug: number is %d\n", random); // debug
//        fflush(stdout);

        while(guess != random) {
            fprintf(stdout, "\nEnter your guess: ");
            fflush(stdout);

            (count++);

            fgets(buffer, BUFSIZ, stdin);
            guess = atoi(buffer);

            if(guess == -99) {
                fprintf(stdout, "\nBye!\n");
                fflush(stdout);
                return 0;
            }

            if((guess < (random + 5)) && (guess > (random - 5))) {

                fprintf(stdout, "CLOSE... but not quite. Try again!\n");
                fflush(stdout);
            } else {
                fprintf(stdout, "Nope... try again!\n");
                fflush(stdout);
            }
        }

        fprintf(stdout, "\nCongratulations! You guessed it!\n");
        fprintf(stdout, "It took you %d try(s) to do it\n", count);
        fflush(stdout);
    }
    return(0);
}

```


:)

---

