---
title: "Gcc can make faster code than M$'s Vc 6 ?"
date: 2012-04-19
forum: Programming Talk
---

### Post by DaviesX on 2012-04-19
I have seen many people in other forum said that code compiled by gcc is slower than MS's compiler. But as I made a test just now, I found that Gcc's can generate 17.7% faster code than MS Visual C++ 6.0 did using the same program without any I/O in my aTom CPU

```

#include <stdio.h>
#include <time.h>

int main ( void )
{
    int i, a, n = 1, flag = 0;
	getchar ();
	double start = clock () / (double)CLOCKS_PER_SEC;

    for ( i = 3; i <= 10000000; i += 2 )
    {
	int end = 0, count;

	for ( count = i; count > 1; count >>= 1, end++ );

        for ( a = 2; a <= end; a++ )
        {
            if ( i % a == 0 )
            {
                flag = 0;
                break;
            }
        }

        if( flag == 1 )
			n++;
		flag = 1;
    }

    double end = clock () / (double)CLOCKS_PER_SEC;
    printf ( "n: %d\nt: %.2f", n, end - start );

	return 0;

}

```

Gcc4.6.3 2.082 s
Vc6.0    2.514 s (on average)
Gcc is 17.7% faster on average

I thought Gcc is an open-source project so that it may be inferior than the commercial one, but it's exactly faster, though Vc 6.0 is made more than 10 years (I think it was 1998) ago.

And I made another with I/O is more distinct. Probably it is because they are tested in different platform (Ubuntu 12.04 and Windows Xp Pro)
```

#include <stdio.h>
#include <time.h>

int main ( void )
{
    int i, a, flag = 0;
    getchar ();
    double start = clock () / (double)CLOCKS_PER_SEC;

    FILE *file = fopen ( "test.txt", "w+" );

    for ( i = 1; i <= 10000000; i += 2 )
    {
        int end = 0, count;

        for ( count = i; count > 1; count >>= 1, end++ );

        for ( a = 2; a <= end; a++ )
        {
            if ( i % a == 0 )
            {
                flag = 0;
                break;
            }
        }

        if( flag == 1 )
            fprintf ( file, "%d ", i );
        flag = 1;
    }

    fclose ( file );
    double end = clock () / (double)CLOCKS_PER_SEC;
    printf ( "t: %.2f", end - start );

    return 0;

}

```
Gcc4.6.3  3.246s
Vc6.0     5.50s
Gcc is almost 50% faster!

I think it is optimistic. And I'm not proficient in programming, maybe there have been some inaccurate statements, please point it out if you can find.

Vc6.0 is farely an old compiler anyway, but I don't have a Visual Studio for testing. please send your result if you have one !

---

### Post by Barrucadu on 2012-04-19
> **DaviesX said:**
> I thought Gcc is an open-source project so that it may be inferior than the commercial one, but it's exactly faster, though Vc 6.0 is made more than 10 years (I think it was 1998) ago.

That doesn't mean there are no paid developers. The Linux kernel, for example, has a huge amount of commercial sponsership (even from Microsoft). I would be amazed if GCC were not in a similar situation.

---

### Post by Bachstelze on 2012-04-19
Relative performance of compilers depend heavily on the program being compiled. It is perfectly possible that gcc produces faster code with your program, and VC++ produces faster code with some other program.

---

### Post by schauerlich on 2012-04-20
> **Bachstelze said:**
> Relative performance of compilers depend heavily on the program being compiled. It is perfectly possible that gcc produces faster code with your program, and VC++ produces faster code with some other program.

Additionally, the targeted platform can play a role. Although that's somewhat mitigated by the fact that most important optimization take place at the AST and intermediate representation level, so by the time it gets to specific architectures it's just micro-optimizations. But for tight loops, it can make a difference.

---

### Post by mehaga on 2012-04-20
Last time I did a similar test (couple of yrs ago), Intel's compiler was by far the fastest.

---

### Post by r-senior on 2012-04-20
> **Barrucadu said:**
> The Linux kernel, for example, has a huge amount of commercial sponsership (even from Microsoft).
There were some figures released a few weeks ago that presented Microsoft as a significant contributor to the Linux kernel, but it doesn't imply a long-term sponsorship. They got caught out with the GNU GPL and were forced to open-source 20000 lines of code that they'd tried to keep proprietary. They will maintain and enhance it but it's their first and only contribution.

Sorry to drift off-topic.

---

### Post by DaviesX on 2012-04-20
Can I ask how different IO does linux and windows(or gcc and vc6, I don't know) has ? Because it was a great difference on the second test.

---

