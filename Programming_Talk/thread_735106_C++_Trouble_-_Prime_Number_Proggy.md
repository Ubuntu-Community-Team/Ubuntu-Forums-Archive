---
title: "C++ Trouble - Prime Number Proggy"
date: 2008-03-25
forum: Programming Talk
---

### Post by Lusst on 2008-03-25
edit: For the record, I have 1/2 semester of C++ experience, so forgive the barbaric program below...


I'm having a bit of trouble that has ultimately lead to a headache.

This line is designed to first identify an odd number, and then check to see if it's prime or not.  My error is in red:

```
int n;
double temp=0;

cout << "Enter any positive integer and my machine coding supercomplex"
"\ndata compressor will determine if it is a prime number." << endl;
cin >> n;

if (n <= 0)
{
        cout << "The number is not a positive integer."
        "\nHit any key to continue..." << endl;
        getch();
        return 1;
}
else if (n % 2 == 0)
{
        cout << "The number you have entered is an even number..." << endl;

        while (n == 2)
        {
        cout << "...which just so happens to be a prime number." << endl;
        cout << "\nPat yourself on the back and hit any key to exit." << endl;
        getch ();
        return 0;
        }
}
else if (n % 2 != 0)

{
        cout << " The number you have entered is an odd number..." << endl;
        temp = sqrt(n);         

cout << "temp = " << temp << endl; // Remove later - outputs correctly

[COLOR="Red"]        while (pow (temp,2) != n)  //Error - saying that every odd is a prime[/COLOR]
        {
                cout << "...which is also a prime number." << endl;
                getch();
                return 0;
        }
}
```

Any idears?

**spits in bucket**

---

### Post by WW on 2008-03-25
I don't understand how that loop is supposed to work, but that is probably because you are still debugging and it is not finished.

If computer arithmetic with floating point numbers was exact (which it isn't), the condition at the beginning of the while loop would be true for any n, since all you have done is taken the square root of n and then squared the result and compared it to n.

However, typically pow(sqrt(x),2) != x, so the test at the beginning of the loop can (and often will) be false.

It might help if you explained how your test for primality is supposed to work.


P.S. Is this [homework](http://ubuntuforums.org/showthread.php?t=717011)?

---

### Post by pedro_orange on 2008-03-25
Why don't you take smaller steps?

Logging is your friend! (Unless you're parallel programming! Then logging can be your mortal enemy!!)

---

### Post by Martin Witte on 2008-03-25
By accident a double post, see next

There is another thing you should consider: a loop has to end, in your program you  can run into a snip like this
```

#include <iostream>

using namespace std;

int main()
{
    int n(2);
    while(n==2)
    {
        cout << "n equals 2" <<endl;
    }
    return 0;
}
```It will never end, the control variable n remains 2 inside the while loop

---

### Post by LaRoza on 2008-03-25
> **Martin Witte said:**
> 
It will never end, the control variable n remains 2 inside the while loop

There is a "return" in the loop. It looks like it isn't supposed to loop.

I do believe this is homework though....

---

### Post by Lord Illidan on 2008-03-25
Why don't you use the [Sieve of Eratosthenes]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes") for your prime number checking?

---

### Post by Martin Witte on 2008-03-25
> **LaRoza said:**
> There is a "return" in the loop. It looks like it isn't supposed to loop. Ai, I overlooked that one. My answer should be  rephrased as: 

```
while(n==2)
{
     cout << "n equals 2" <<endl;
     return 0;
}

```

is actually not a loop but an inefficient if - construction

---

### Post by LaRoza on 2008-03-25
> **Martin Witte said:**
> Ai, I overlooked that one. My answer should be  rephrased as: 

```
while(n==2)
{
     cout << "n equals 2" <<endl;
     return 0;
}

```

is actually not a loop but an inefficient if - construction

Yes. 

@OP This is a rather elementary problem, so I think you should hit the books and online resources and rethink this. If this is homework, you will have to figure it out anyway. See the sticky.

[http://www.parashift.com/c++-faq-lite/how-to-post.html#faq-5.2](http://www.parashift.com/c++-faq-lite/how-to-post.html#faq-5.2)
> 
"If I did your homework for you, then you might pass your class without learning how to write a program like this. Then you might graduate and get your degree without learning how to write a program like this. You might become a professional programmer without knowing how to write a program like this. Someday you might work on a project with me without knowing how to write a program like this. Then I would have to do you serious bodily harm." [Thanks to Jack Klein]


---

### Post by Lusst on 2008-03-25
> **WW said:**
> P.S. Is this [homework](http://ubuntuforums.org/showthread.php?t=717011)?

No.

I get my jollies trying to figure out my prime numbers.  It's a hobby I picked up back at the emu farm.

[quote=LaRoza]This is a rather elementary problem[/quote]
*nod*

Like I said, I have a half semester of programming experience under my belt.

I'm not here to find a quick answer; hell, I could Google my problem and copy+paste a program in a matter of seconds.  I could also roll my *** 5 feet to the left and look over my fellow student's shoulder.

I'm registered on these boards so that I may **learn** from people far more experienced than I.  You guys know as well as I do, a C++ programmer is hard to find out in the real world.

Anyhoo,

My thinking was that I would first split the number into an odd or even.  If it's odd - get the square root of that number, and make sure that the number can only be divisible by itself and 1.

Now that I wrote it out, it makes more sense to me...I'll be damned.

Anyway, a little history on my instructor:

He's been programming around 40 years.  He goes through the material super fast, and doesn't like to answer any questions because it interferes with his Spider Solitaire game.  He's a good enough guy, but I'll definitely be lighting his *** up when evaluation time rolls around.

Thanks for the help guys - I'll hopefully be able to finger out what I did wrong.

- Seacrest out.

---

### Post by Lord Illidan on 2008-03-25
You could also read a book, or one of the many reference sites on the Internet, too.

---

### Post by Lusst on 2008-03-25
> **Lord Illidan said:**
> You could also read a book, or one of the many reference sites on the Internet, too.

Well, I can tell you this - the book C++ Programming by D.S. Malik is <=0 when it comes to helping a newbie out.

I'm starting to realize I fail at life.

Seems that I am taking a square root of a number, then squaring it back.  Which, of course...will always be true.

**slams head on keyboard**

;oahd[ch

---

### Post by WW on 2008-03-25
> **Lusst said:**
> 
My thinking was that I would first split the number into an odd or even.  If it's odd - get the square root of that number, and make sure that the number can only be divisible by itself and 1.

The square root of an integer is not necessarily an integer, so in that case, what does it mean to say that it "can only be divisible by itself and 1"?

If n *does* have an integer square root, then n is not prime, but if n does not have an integer square root, you still don't know if n is prime or not.  E.g. neither 13 nor 15 has an integer square root; 13 is prime, but 15 is not.

---

### Post by scragar on 2008-03-25
```
int n;
int i;
int k;
double temp=0;

cout << "Enter any positive integer and my machine coding supercomplex"
"\ndata compressor will determine if it is a prime number." << endl;
cin >> n;

if (n <= 0)
{
        cout << "The number is not a positive integer."
        "\nHit any key to continue..." << endl;
        getch();
        return 1;
}
else if (n % 2 == 0)
{
        cout << "The number you have entered is an even number..." << endl;

        if (n == 2)
        {
             cout << "...which just so happens to be a prime number." << endl;
             cout << "\nPat yourself on the back and hit any key to exit." << endl;
             getch ();
             return 0;
        }
}
else { **// entire if that was here is wasted, since the else captures the exact same condition a sec before**
        cout << " The number you have entered is an odd number..." << endl;
        temp = sqrt(n);


cout << "temp = " << temp << endl; // Remove later - outputs correctly

[b]
// my example:

        k = 0;
        for(i= 0; i < temp; i++)// for all numbers before the result
        {
                if(n % i == 0){
                           cout << "....divides cleanly by " << i << endl;
                           k++;
                }
                if(i == temp && temp*temp == n)
                            cout << "...And is a square number." << endl;
        }
        if(k == 0)
                cout << "...And is a prime number." << endl;
        getch();
        return 0;[/b]
}
```my example is untested, but it looks to be what your doing.

---

### Post by stratavarious on 2008-03-25
.

---

### Post by baumgc on 2008-03-25
> **Lusst said:**
> Well, I can tell you this - the book C++ Programming by D.S. Malik is <=0 when it comes to helping a newbie out.

I'm starting to realize I fail at life.

Seems that I am taking a square root of a number, then squaring it back.  Which, of course...will always be true.

**slams head on keyboard**

;oahd[ch


Yay! 
I use this book too!

Or at least. I bought it and it sits in my drawer. Can't figure out how to use it towards my class yet.

---

### Post by pedro_orange on 2008-03-26
I've not personally read the book you're discussing.

But there is actually a sticky with recommended books in. I wish I read "Accelerated C++" when I was learning to program c++ - would've saved me alot of time/money/sanity.

---

### Post by Lusst on 2008-03-26
> **pedro_orange said:**
> I've not personally read the book you're discussing.

But there is actually a sticky with recommended books in. I wish I read "Accelerated C++" when I was learning to program c++ - would've saved me alot of time/money/sanity.

Cool - I'll have to pick that up at Half Price Books.

---

