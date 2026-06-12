---
title: "Efficient vs. Readable Code"
date: 2007-09-30
forum: Programming Talk
---

### Post by Keiji on 2007-09-30
So this stubborn guy I know refused to see how code doesn't need to be readable when it won't ever get changed. Here's the function he wrote:

```
// return greatest common denominator of m and n
int gcd(int m, int n) {return n == 0 ? m : gcd(n, m%n);}
```

This, as you can see, uses recursion, which is bad, especially in a situation like this where the function can easily be re-written as an iteration:

```
// return greatest common denominator of m and n
int gcd(int m, int n) {int r; while (n != 0) {r = m % n; m = n; n = r;} return m;}
```

He said this is less readable than the first. I agreed, but also said that it's pointless using the first because even though the first is more readable, the second is a LOT more efficient (when the parameters are large, recursive functions are much slower and can potentially cause out of memory errors), and nobody is ever going to need to read the code because it won't need changing.

So what are your thoughts? He suggested posting this here, to see what the overall view is.

---

### Post by Wybiral on 2007-09-30
My thoughts are that... They would both be readable if they were properly formatted.

But more importantly... I would go with the most logical/readable form UNTIL you've profiled and tested to determine whether it justifies the less readable form. Sometimes you need to take the "hacky" approach and make something as efficient as possible. But DO NOT make that decision until you know you have to (via profiling and testing). Also, you never know when you'll need to change a part of code... I wouldn't make that assumption at any time.

---

### Post by Tuna-Fish on 2007-09-30
"Premature optimization is the root of all evil." Swapping a recursive but easily readable function into an iterative but unreadable one before you **know** by **testing** that it is going to cause problems is premature optimization.

That, and: "Programs should be written for humans to read and only incidentally for machines to execute." are the two pillars on which the foundation of writing maintainable and long-lasting code stands.

That being said, I'd probably write the iterative function myself, only, indent it so that it is immediately apparent what it does.

---

### Post by Lord Illidan on 2007-09-30
Exactly, why didn't you indent them both?

---

### Post by Blue Sky on 2007-09-30
Neither of those are readable.

---

### Post by Fbot1 on 2007-09-30
Neither of those are really tricky and everyone will know what it does. Recursive algorithms aren't always slower but they will be in this case. I think the second one is better.

---

### Post by Lord Illidan on 2007-09-30
Also, in both cases, commenting the code will increase readability and will not detract from its efficiency.

---

### Post by Fbot1 on 2007-09-30
> **Lord Illidan said:**
> Exactly, why didn't you indent them both?

That would be unnecessary, it's a lot more straight forward like that.

> **Lord Illidan said:**
> Also, in both cases, commenting the code will increase readability and will not detract from its efficiency.

Are you being serious?

---

### Post by Wybiral on 2007-09-30
> **Lord Illidan said:**
> Exactly, why didn't you indent them both?

Indeed.

If you do determine this one to end up being faster (and it may not... You need to profile it some), it can be readable if you just format it nicely, something like...

```

int gcd(int m, int n) 
{
    int r;
    while (n != 0)
    {
        r = m % n;
        m = n;
        n = r;
    }
    return m;
}

```

C is a terrible language for "one-liners". It's always best to stretch it out and make it as readable as possible.

---

### Post by angustia on 2007-09-30
> **Keiji said:**
> So this stubborn guy I know refused to see how code doesn't need to be readable when it won't ever get changed. Here's the function he wrote:

```
// return greatest common denominator of m and n
int gcd(int m, int n) {return n == 0 ? m : gcd(n, m%n);}
```

This, as you can see, uses recursion, which is bad, especially in a situation like this where the function can easily be re-written as an iteration:

```
// return greatest common denominator of m and n
int gcd(int m, int n) {int r; while (n != 0) {r = m % n; m = n; n = r;} return m;}
```



i tried that code compiling to asm output, with and without -foptimize-sibling-calls

without -O2 -foptimize-sibling-calls, the gcd function got compiled to something like this:

```

gcd:
	pushl	%ebp
	movl	%esp, %ebp
	subl	$12, %esp
	cmpl	$0, 12(%ebp)
	je	.L2
	movl	8(%ebp), %edx
	movl	%edx, %eax
	sarl	$31, %edx
	idivl	12(%ebp)
	movl	%edx, %eax
	movl	%eax, 4(%esp)
	movl	12(%ebp), %eax
	movl	%eax, (%esp)
	call	gcd                             ;  < calling gcd from inside gcd
	movl	%eax, -4(%ebp)
	jmp	.L4
.L2:
	movl	8(%ebp), %eax
	movl	%eax, -4(%ebp)
.L4:
	movl	-4(%ebp), %eax
	leave
	ret

```

if you don't know asm, the gcd function is called from its own code

know, with -O2 -foptimize-sibling-calls:
```

gcd:
	pushl	%ebp
	movl	%esp, %ebp
	pushl	%ebx
	movl	12(%ebp), %ebx
	movl	8(%ebp), %eax
	testl	%ebx, %ebx
	jne	.L8
	jmp	.L3
	.p2align 4,,7
.L10:
	movl	%edx, %ebx
.L8:
	movl	%eax, %edx
	sarl	$31, %edx
	idivl	%ebx
	movl	%ebx, %eax
	testl	%edx, %edx
	jne	.L10
	movl	%ebx, %eax
.L3:
	popl	%ebx
	popl	%ebp
	ret

```

you can see there is no 'call' instruction between the 'gcd' label and the 'ret' (return) instruction at the end.

---

### Post by Lord Illidan on 2007-09-30
> **Fbot1 said:**
> That would be unnecessary, it's a lot more straight forward like that.

Are you being serious?

For you, it might be straightforward, however my knowledge of c++ is limited, and I'd rather not have them on one line. As a matter of fact, most books regarding c++ recommend good commenting and indentation.

---

### Post by Wybiral on 2007-09-30
> **Fbot1 said:**
> That would be unnecessary, it's a lot more straight forward like that.

Are you being serious?

You can't possibly be arguing in defense of bad coding practices... Even if it is a simple function, it makes no sense at all to bunch it up like that.

That type of code will not fly well in a serious project with multiple people.

---

### Post by Note360 on 2007-09-30
um recursion is jsut as viable as looping and jsut as readible. The formattign though sucks.

---

### Post by samjh on 2007-09-30
The first example is hardly readable (I don't like ternary conditionals):
```
// return greatest common denominator of m and n
int gcd(int m, int n) {return n == 0 ? m : gcd(n, m%n);}
```Better to stretch that out, IMHO:
```
int gcd(int m, int n)
{
    if (n == 0) {
        return m;
    } else {
        return gcd(n, m % n);
    }
}
```Adjust/omit { } braces as you desire.

---

### Post by Fbot1 on 2007-09-30
> **Wybiral said:**
> You can't possibly be arguing in defense of bad coding practices... Even if it is a simple function, it makes no sense at all to bunch it up like that.


Sure it does, it takes like 0.12 less seconds to read. Seriously though, if you make the code too "fluffy" it will hurt readability.

---

### Post by Wybiral on 2007-09-30
> **Fbot1 said:**
> Sure it does, it takes like 0.12 less seconds to read. Seriously though, if you make the code too "fluffy" it will hurt readability.

Are you saying proper indentation hurts readability?

When you look at properly formated code, you can see the blocks instantly, when you look at "one-liners" it's much more difficult to follow the branching.

After looking at this:

```

int xxx(){for(int i=0; i<100; i++){if(i<50) {yyy();} else {zzz();}} return 10;}

```

Notice how quickly you can tell the branches apart in this:

```

int xxx()
{
    for(int i=0; i<100; i++)
    {
        if(i<50) 
        {
            yyy();
        }
        else
        {
            zzz();
        }
    }
    return 10;
}

```

Also, all the code in your project should have a similar format/convention. If you allow yourself to bunch some functions up like this and stretch the rest out, you're completely ignoring any type of convention, so your project has no standard (which makes it harder for others to follow).

Like I said before, you're going to have a hard time convincing your team to allow that kind of code in a large project. Conventions are good... Your project should allows adhere to some universal format laws (otherwise it quickly turns into chaos).

---

### Post by Fbot1 on 2007-09-30
> **Wybiral said:**
> Are you saying proper indentation hurts readability?

When you look at properly formated code, you can see the blocks instantly, when you look at "one-liners" it's much more difficult to follow the branching.

After looking at this:

```

int xxx(){for(int i=0; i<100; i++){if(i<50) {yyy();} else {zzz();}} return 10;}

```

Notice how quickly you can tell the branches apart in this:

```

int xxx()
{
    for(int i=0; i<100; i++)
    {
        if(i<50) 
        {
            yyy();
        }
        else
        {
            zzz();
        }
    }
    return 10;
}

```


Spacing is fine and stuff but it really doesn't often make it much easier. Anything more than this is just makes it harder to read:
```

int xxx()
{
for (int i=0; i<100; i++)
{
if (i<50) {yyy();}
else {zzz();}
}
return 10;
}

```

> 
If you allow yourself to bunch some functions up like this and stretch the rest out, you're completely ignoring any type of convention, so your project has no standard (which makes it harder for others to follow).

No, not necessarily.

---

### Post by mssever on 2007-09-30
> **Fbot1 said:**
> ```

int xxx()
{
for (int i=0; i<100; i++)
{
if (i<50) {yyy();}
else {zzz();}
}
return 10;
}

```
Now, THAT'S hard to read! You would benefit greatly from learning Python. :)

---

### Post by j_g on 2007-09-30
I'm not surprised, but very dismayed, that no one pointed out that all code is "readable" if it is properly commented. I'm a big proponent of very, very profuse commenting. I would hate to see either version of the above code in a program, not because of indentation (although that's a big factor in improving readability), but because of the lack of any comment saying what the code does and how it does it.

[removed]

---

### Post by Fbot1 on 2007-09-30
> **mssever said:**
> Now, THAT'S hard to read! You would benefit greatly from learning Python. :)

Is it really hard?

---

### Post by Nekiruhs on 2007-09-30
> **Fbot1 said:**
> Is it really hard?
Not really, but its good coding practice to use atleast tabs. It allows one to easily identify scopes, functions, and blocks

---

### Post by Fbot1 on 2007-09-30
> **Nekiruhs said:**
> Not really, but its good coding practice to at least use tabs. It allows one to easily identify scopes, functions, and blocks

I disagree. Spaces and lines are useful because they reduce the chance that your mind incorrectly blends characters but, tabs just don't help. All they do is strain my eyes.

---

### Post by Nekiruhs on 2007-09-30
> **Fbot1 said:**
> I disagree. Spaces and lines are useful because they reduce the chance that your mind incorrectly blends characters but, tabs just don't help. All they do is strain my eyes.
And tabs allow one to quickly skim your code and recognize functional blocks. Curly braces just don't cut it.

---

### Post by Wybiral on 2007-09-30
> **Fbot1 said:**
> Is it really hard?

Yes, it is. Maybe not for that small block, but when you have more embedded conditions and loops, it's very hard to determine where a piece of code fits in the scope (without counting brackets).

> **j_g said:**
> I'm not surprised, but very dismayed, that no one pointed out that all code is "readable" if it is properly commented. I'm a big proponent of very, very profuse commenting. I would hate to see either version of the above code in a program, not because of indentation (although that's a big factor in improving readability), but because of the lack of any comment saying what the code does and how it does it.

It was mentioned, in the 7th reply:

> **Lord Illidan said:**
> Also, in both cases, commenting the code will increase readability and will not detract from its efficiency.

---

### Post by mssever on 2007-10-01
> **j_g said:**
> I'm not surprised, but very dismayed, that no one pointed out that all code is "readable" if it is properly commented. I'm a big proponent of very, very profuse commenting. I would hate to see either version of the above code in a program, not because of indentation (although that's a big factor in improving readability), but because of the lack of any comment saying what the code does and how it does it.
Comments are only useful if used properly. Comments that document functions and larger blocks of code are a good thing. Commenting every line just adds noise, making the source harder to read. In the example given above, it's immediately obvious at a glance what the block of code does. Adding comments  to the block would just add noise.
> **Fbot1 said:**
> I disagree. Spaces and lines are useful because they reduce the chance that your mind incorrectly blends characters but, tabs just don't help. All they do is strain my eyes.
Counting braces to determine which block of code you're in takes a lot of time and is error-prone. Indenting your code avoids that problem. This example is trivial, so it doesn't make a lot of difference. But what if the kernel were written without indentation? That's a whole lot of code to get lost in. By the way, Linus doesn't want more than three levels of indentation in the kernel for simplicity's sake. But that isn't accomplished by simply not indenting. It's accomplished by how you structure your code.

---

### Post by slavik on 2007-10-01
if it's an algorithm like gcd, I personally wouldn't care which way it is done. if it's something that is truly patent worthy, then it better be readable as if it was fortran. :)

---

### Post by Lord Illidan on 2007-10-01
I didn't say you had to comment every line, did I? But a comment before the start of a function/method explaining what it is doing does improve readability a lot. I used commenting a lot in my A level project, especially when I used algorithms which didn't make much sense at first sight.

---

### Post by pmasiar on 2007-10-01
> **Keiji said:**
> So this stubborn guy I know refused to see how code doesn't need to be readable when it won't ever get changed.

There is no such code what does not need changing. 
If code is bad, it needs to be rewritten
If code is good, new features will be needed or will be used outside of initial intentions.

If code is hacked for speed, I like it documented (so next guy will not "optimize it" back to readability).

Writing unreadable code smells like attempt to get job security - nobody else can maintain that code. It's better avoid companies which allow that - it is just unnecessary pain.

---

### Post by pmasiar on 2007-10-01
> **Lord Illidan said:**
> Also, in both cases, commenting the code will increase readability and will not detract from its efficiency.

> **Fbot1 said:**
> That would be unnecessary, it's a lot more straight forward like that.

Are you being serious?

I am just curious, Fbot1, about your real life programming experience. You do not sound like someone who participated in real project, just like some kid who is hacking alone without sharing.

> **Fbot1 said:**
> Sure it does, it takes like 0.12 less seconds to read. Seriously though, if you make the code too "fluffy" it will hurt readability.

Too "fluffy" is far from what was proposed. 

I just cannot understand how you can seriously propose that comments and proper indents decrease efficiency. This looks dangerously close to a troll. Are you not aware that comments and whitespace is stripped out from compiled code?

> **Fbot1 said:**
> I disagree. Spaces and lines are useful because they reduce the chance that your mind incorrectly blends characters but, tabs just don't help. All they do is strain my eyes.

You are the only person I know who claims that about tabs. Instead of rejecting common practice, you may want to get your eyesight checked. :-)

---

### Post by Fbot1 on 2007-10-02
> **pmasiar said:**
> I am just curious, Fbot1, about your real life programming experience. You do not sound like someone who participated in real project, just like some kid who is hacking alone without sharing.

just some kid

> Too "fluffy" is far from what was proposed. 

I just cannot understand how you can seriously propose that comments and proper indents decrease efficiency. This looks dangerously close to a troll. Are you not aware that comments and whitespace is stripped out from compiled code?

Yes, I do.

> 
You are the only person I know who claims that about tabs. Instead of rejecting common practice, you may want to get your eyesight checked. :-)
Maybe, I realize that I'm going to need to get used to it but it still bothers me.

---

### Post by aks44 on 2007-10-02
> **Fbot1 said:**
> jI realize that I'm going to need to get used to it but it still bothers me.

If you're bothered about "common practices", just remember that they're here for a good reason... and if you're ever going to work in a team, indentation and the like are just a small fraction of the constraints you'll have to abide to. The "lonely garage programmer" days are over, especially when it comes to anything a bit serious.


Now if you're bothered about your eyesight... better get used to check it regularly, indeed! :p

---

### Post by CptPicard on 2007-10-02
> **aks44 said:**
> The "lonely garage programmer" days are over, especially when it comes to anything a bit serious.

You insensitive clod... ok, I don't live in a garage but still ;)

---

### Post by aks44 on 2007-10-02
> **CptPicard said:**
> You insensitive clod... ok, I don't live in a garage but still ;)

As long as you're not one of those "long-haired, bearded, lonely garage programmers..." :p

Oh wait... I'm concerned by 3 out of those 5. Please disregard that post... ;)

</OT>

---

