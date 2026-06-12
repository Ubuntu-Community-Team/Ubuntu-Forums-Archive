---
title: "Recursive Function"
date: 2008-11-10
forum: Programming Talk
---

### Post by ghandi69_ on 2008-11-10
Hey guys, 

I am working on a homework problem here, and I found it to be kinda interesting.  If you guys have any 'qualms' about me talking about homework on here I apologize, but I hope to let you know this not worth a lot of points, is just one problem out of many, and if you look at my post history you'll see I've never come on here asking for homework help before, but this one has just stumped me for some reason..

Anyway, the problem is to find the second largest element in an array, using 'recursion' and without sorting.

The recursion part is what is stumping me. Obviously, we could just sort the array and take the 2nd largest element.  We could also find the largest recursively, remove the largest value, and then find the largest again recursively, but its supposed to only run once.

The thing is, I just can't think of a base case that could be answer the same every recursive call that would grant you the 2nd largest item when finished.

Anyway, there is a good chance this is just really simple, as the actual length of code I'm sure is quite short (as opposed to creating a spelling checking program with a full gui, which was my last homework!--different class...)

Anyway, feel free to post your thoughts.

---

### Post by CptPicard on 2008-11-10
Does "without sorting" mean you need to keep the values in place? The k-th largest algorithm is obtained from exploiting the quicksort partition phase with small modifications, and runs in linear time...

---

### Post by dribeas on 2008-11-10
> **ghandi69_ said:**
> Anyway, the problem is to find the second largest element in an array, using 'recursion' and without sorting.

The thing is, I just can't think of a base case that could be answer the same every recursive call that would grant you the 2nd largest item when finished.

Consider that you could have two values returned from the recursive call. Depending on the language that can be implemented in different ways, but that might be your solution.

---

### Post by hod139 on 2008-11-10
The only hint I'll give is to look at the quickselect algorithm.  It is a variation of quicksort, and one of the standard algorithms for finding the k-th smallest/largest element.

---

### Post by CptPicard on 2008-11-10
Actually the kth-largest is overkill, you're better off just writing a tail-recursive version of a simple loop that keeps track of largest and second largest :)  (this example is the other way around, finds 2nd-smallest, but anologously ofc..)

```


def second_smallest(li):

    def recursion(my_list,a,b):
	if my_list == []:
	    return a, b
	elif my_list[0] < a:
	    return recursion(my_list[1:], my_list[0], a)
        else:
            return recursion(my_list[1:], a, b)
    
    a, b = recursion(li,10000,10000)
    return b


print second_smallest([2,5,7,3,9,1,8])


```

Now, if Python did tailcall optimization, this would essentially be a loop.

---

### Post by ghandi69_ on 2008-11-10
Thanks for the reply.

In the end, I think this problem was confusing me because this just seems like a weird way to use recursion, but this is what I came up with.  Max 1 and max 2 are global variables I modify thoughout.  and max2 should end up being the 2nd largest.

```
public static void findsecondlargest(int[] x, int index, int biggest, int big){
		
		if(index == x.length-1){
			if(x[index] > biggest){
				max2 = biggest;
				max = x[index];
			}else{
				if(x[index] > big){
					max2 = x[index];
				}
			}
			
			
		}else{
			if(x[index] > biggest){
				findsecondlargest(x, index+1, x[index], biggest);
			}else{
				findsecondlargest(x, index+1, biggest, big);
			}
		}
		
	}
```

EDIT:: upon further inspection, I think this is quite similar to the post above.

---

### Post by CptPicard on 2008-11-11
> **ghandi69_ said:**
> 
EDIT:: upon further inspection, I think this is quite similar to the post above.

Yes it is. The "moral of the story" really is that tail-recursion is equivalent to a loop, and I have a hunch that this is what the exercise tries to make people understand. As a matter of fact, functional languages tend to rely on this and write every loop as tail-calls like this.

Getting rid of your globals would make it prettier though as the solution would be completely self-contained :)

---

### Post by nvteighen on 2008-11-11
> **CptPicard said:**
> Yes it is. The "moral of the story" really is that tail-recursion is equivalent to a loop, and I have a hunch that this is what the exercise tries to make people understand. As a matter of fact, functional languages tend to rely on this and write every loop as tail-calls like this.

Getting rid of your globals would make it prettier though as the solution would be completely self-contained :)
Well, I only fully understood recursion when learning Scheme... Imperative languages seem not to like recursive-style too much...

---

### Post by drubin on 2008-11-11
> **nvteighen said:**
> Well, I only fully understood recursion when learning Scheme... Imperative languages seem not to like recursive-style too much...

They are normally slower and require more memory then basic loops.

---

### Post by CptPicard on 2008-11-11
> **drubin said:**
> They are normally slower and require more memory then basic loops.

This is only true if the compiler doesn't do tailcall optimization. If it does, they should be the same.

---

### Post by nvteighen on 2008-11-11
> **drubin said:**
> They are normally slower and require more memory then basic loops.
Yeah, and what? To me, the concept is more important than the speed. There is stuff that's more suitable to be done through iteration and others through recursion; there are languages that favor recursive style because of their semantics (i.e. Scheme and I guess Lisp in general) and others, like C, that favor iteration (obviously, not prohibiting recursion...) because of how, for example, you work with arrays... you just can't do 'cdr' (as in Scheme') to take the "rest of the array/list"; it's much easier in C to traverse the array with an index. And viceversa, iteration in Scheme gives more trouble than recursion... specially after the introduction of the "named let" technique, which allows local-scoped recursions (where before you only could do recursion with top-level procedures).

---

