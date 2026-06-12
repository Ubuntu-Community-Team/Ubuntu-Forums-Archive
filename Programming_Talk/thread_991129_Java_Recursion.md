---
title: "Java Recursion"
date: 2008-11-23
forum: Programming Talk
---

### Post by brian77095 on 2008-11-23
I am not looking for the answer to the problem below just understanding.



private int func1(int m, int n) {
      if (m==n || n==1)
        return 1;
      else
        return func1(m-1,n-1) + n*func1(m-1,n);
}


Based on the method above, what is the value of func1(5, 3)?

PLEASE DO NOT POST THE ANSWER!


I completely guess this question and got it right but, I have no idea how this works.

My text book really does a poor job of explaining Recursion.  I get the definition but, not the process.   

Could someone point me to a good explanation and or examples.... or even the correct way to solve above question?

Also is this something you use a lot in day to day programing?

---

### Post by jespdj on 2008-11-23
The idea of recursion is quite simple: it's a method that calls itself (directly or indirectly).

Finding out the answer is also not so difficult: write down on a piece of paper (or keep in your mind) the values of the variables (start with m = 5 and n = 3), then follow the code line by line and note down any changes to the variables. When a method is called, go into the call and remember where you went in (so you know where to return when the method ends). In other words, do what the computer would do when it executes the code.

Recursion is something that's used every now and then in real programs, it's important to understand it if you're a programmer.

---

### Post by CptPicard on 2008-11-23
Let's take a look at this in mathematical terms, I think the structure of what is going on may be clearer if we remove the programming language-specific syntactic parts. So we have a function...

```

f(m,n) = 1                          if m = 1 or n = 1
       = f(m-1,n-1) + n * f(m-1,n)  otherwise

```

So, we have

```

f(5,3) = f(4,2) + 3 * f(4,3)       first case applies
       = f(3,1) + 2 * f(3,2) +
         3 * (f(3,2) + 3 * f(3,3)) =
       ...  so on, keep working on it and note that 
            f(3,1) = 1 according to the definition

```

There really is nothing more to it, you just apply the function according to the rule until you stop at the first case.

Recursion is actually a very important concept in theory of computation, with in explicitly recursive functions and recursive structures built from data... it is particularly prevalent in functional programming where it is often used instead of looping.

---

### Post by jimi_hendrix on 2008-11-23
> **brian77095 said:**
> 
Could someone point me to a good explanation and or examples....

every type of loop in the haskell language :)

but recursion is just calling a function from within itself so it will go on forever unless you tell it when to stop (what you did with the if (m == n || n == 1))

---

### Post by drubin on 2008-11-23
> **jimi_hendrix said:**
> every type of loop in the haskell language :)

but recursion is just calling a function from within itself so it will go on forever unless you tell it when to stop (what you did with the if (m == n || n == 1))

Just on that point. The way you tell a recursive function to stop is to return a "static" hard coded value or one of the vars instead of the function call its self.

[PHP]private int func1(int m, int n) {
    if (m==n || n==1)
        return 1; //HERE is the static return type.
    else
        return func1(m-1,n-1) + n*func1(m-1,n); //Return the recursive function call.
}[/PHP]

@OP: When you post code try to use the code/php tages like so [NOPARSE][PHP]code goes in between these :)[/PHP][/NOPARSE]

---

### Post by CptPicard on 2008-11-23
> **drubin said:**
> The way you tell a recursive function to stop is to return a "static" hard coded value or one of the vars instead of the function call its self.

Actually, a way to tell a recursive function to stop is to return anything that does not contain further calls into the function down the line...

---

### Post by drubin on 2008-11-23
> **CptPicard said:**
> Actually, a way to tell a recursive function to stop is to return anything that does not contain further calls into the function down the line...

The reason I said "static" was recursion of becomes complicated when you have function a, calling function b, but b in turn calls function a.. :s.

I find recursive is a great tool but can be come complex far to quickly if you do not have a clear esacape.

ie WTF code... :confused:
Bad example code.
[PHP]
function a(int n) {
  if(n == 0)
      return b(n+1);//This would be your "escape" value.. or is it
  else
      return a(n-1);
}

function b(int n){
   if (n == 5 )
       return a(n);
   else
       return b(n+1);
}
[/PHP]

---

### Post by CptPicard on 2008-11-23
Interestingly, in languages that optimize all tailcalls such as Scheme, what you're doing is that you're invoking a and b as "continuations" for the computation... it's a kind of very free-form functional control structure (a kind of "GOTO" actually)... as your calls are tailcalls, you would not have to worry about stack, and the value would be produced when it is produced...

---

### Post by Lux Perpetua on 2008-11-23
> **brian77095 said:**
> Also is this something you use a lot in day to day programing?Recursion is an extremely useful way to think about problems, whether or not you end up implementing a recursive solution. Whenever you have a problem that you can reduce to simpler instances of the same problem, you have recursion. A famous example is sorting: to sort a list, you can divide it into two smaller lists, sort those, and then combine the small sorted lists into a big sorted list (combining sorted lists being easy compared to sorting an unsorted list). That reduces sorting to two smaller sorting problems. If it isn't obvious how to sort the smaller lists, you apply the same reduction to those, and on and on until you're down to subproblems that are trivial to solve.

---

### Post by namegame on 2008-11-23
A classic example of an elegant recursive function is a program that determines the least number of moves required to solve "The Towers of Hanoi" puzzle.

in the following example:

[php]void solveHanoi(int n , char from , char temp, char to)
{
    if (n==1)
        cout << from << " > " << to << endl;
    else
    {
        solveHanoi ((n-1), from, to, temp);
        cout << from << " > " << to << endl;
        solveHanoi ((n-1), temp, from, to);
    }
    return;
}
[/php]

Note: This isn't my code, it's from one of my professor's lectures.

I've actually never tried using recursion to solve the towers puzzle. I did write a program to solve a maze using recursion.

---

### Post by brian77095 on 2008-11-24
Yeah here is my books java example...

public static void moveDisks(int count, int needle1,
                               int needle3, int needle2
{
    if (count > 0)
    {
        moveDisks(count-1, needle1, needle2, needle3);
        System.out.println("Move disk " + count + " from needle "
                         + needle1 + "to needle " + needle3 + ".");
        moveDisks(count-1, needle2, needle3, needle1);
    }
}


So it seems that this can be very useful.  On that note it seems a lot of programmers never take any programing or for that matter computer courses just math.  If you are wanting to become a programmer would it be better to just take more and more math and I guess learn languages later or, is it better to do more of a blending?

---

### Post by namegame on 2008-11-24
> **brian77095 said:**
> 

So it seems that this can be very useful.  On that note it seems a lot of programmers never take any programing or for that matter computer courses just math.  If you are wanting to become a programmer would it be better to just take more and more math and I guess learn languages later or, is it better to do more of a blending?

My major is Computer Science and we focus on the programming side of the field. 

However, we are required to take Calculus 1 & 2, (Integration, Series, etc.), Discrete Mathematics, Linear Algebra, and Statistics.

My University primarily teaches C++ and C, although we are also required to learn Java and some Assembly. There is a Visual Basic class which is taught as "Computer Programming for non-majors."

---

### Post by CptPicard on 2008-11-24
> **brian77095 said:**
> 
So it seems that this can be very useful.

You couldn't even have Turing-complete programming languages at all without having some means of handling recursion :)

> If you are wanting to become a programmer would it be better to just take more and more math and I guess learn languages later or, is it better to do more of a blending?

My view tends to be that programming languages themselves are not complex enough to warrant going to school for them. My MSc degree didn't contain any mandatory "programming" per se outside of the formality of the undergrad first-semester "Intro to Java" class.

CS is mostly about algorithms, problem analysis, theory of computation, and the associated math. You want to know the relevant mathematics, but most math you come across in CS is not awfully advanced (in particular, integrals are rarely used outside of the scope of statistical learning algorithms and other specialized domains, for example)...

The programming languages are learnable on the side.

---

