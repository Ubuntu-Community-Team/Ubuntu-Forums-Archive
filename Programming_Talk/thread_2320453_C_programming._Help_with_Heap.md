---
title: "C programming. Help with Heap"
date: 2016-04-14
forum: Programming Talk
---

### Post by udragu on 2016-04-14
Hello all. I've tried to study C11.
I've some stuck;)

there is a code```


double *get_vect(int n)
{
    double *indi = malloc(n*sizeof(double));
    return indi;
}
int main(int argc, char* argv[]) 
{
int num=1000;
    double *res = get_vect(num);
    return 0; 
}

```

Is it necessary to call free() every time when I use malloc(), even inside main()?
And if it's necessary, may be, is there a better way to pass some extra &param for result array?
What's the principal difference between return pointer on heap and void get_vect(int n,&res){....}. What's better and When?

Thanks all. Sorry if it's look like homework).

---

### Post by Rocket2DMn on 2016-04-14
It's not strictly necessary if the program is ending, but I think it's good practice to always free your allocated memory.  Additionally, it helps to better track down true memory leaks when using tools like valgrind.  In most cases, the best mindset is - if you allocate it, you free it.

In C, the most common approach is for functions to return a status code for success/failure.  If the function's job includes allocating memory, pass a double pointer, e.g.:
```

int get_vect(int n, double** ptr)
{
    *ptr = malloc(n*sizeof(double));
    if (*ptr == NULL) {
        return -1;
    } else {
        return 0;
    }
}

```
In either case, the data will still be on the heap.  The approach you choose is a matter of preference.  In your function's case, a user could check the return of get_vect for NULL, but in more complex scenarios it's not so easy, hence the use of a return code.

---

### Post by udragu on 2016-04-19
[ 						 							]("http://ubuntuforums.org/member.php?u=310232") 	[**[COLOR=#DD4814][B]Rocket2DMn**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=310232"), Big Thx ;). **Understand**. 


[ 						 					]("http://ubuntuforums.org/member.php?u=310232")

---

