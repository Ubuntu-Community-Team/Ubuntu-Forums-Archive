---
title: "Trouble writing algorithm"
date: 2012-07-30
forum: Programming Talk
---

### Post by dwally89 on 2012-07-30
Hi,

I feel like I have been knocking my head against a brick wall trying to write a solution to the following problem, writing various potential solutions, but then scrapping them. I just don't seem to be able to do it?
Could someone help? Language isn't so important, but I'm most familiar with Java and C#.

> A non-empty zero-indexed array A containing N different integers is given. We are looking for the longest possible sequence built from elements of [FONT="Courier New"]A, A[B[0]], A[B[1]], ..., A[B[K]][/FONT], satisfying the following conditions:

•	The sequence must be decreasing; that is, [FONT="Courier New"]A[B[0]] > A[B[1]] > ... > A[B[K]][/FONT].
•	For any two consecutive elements of the sequence, [FONT="Courier New"]A[B[I]][/FONT] and [FONT="Courier New"]A[B[I+1]][/FONT], all the elements of A between them must be smaller than them; that is, for any [FONT="Courier New"]J = MIN(B[I], B[I+1]) + 1, ..., MAX(B[I], B[I+1]) &#8722; 1[/FONT], we have [FONT="Courier New"]A[J] < A[B[I+1]][/FONT].

Write a function:
[FONT="Courier New"]class Solution { public int sequence(int[] A); }[/FONT]

that, given a zero-indexed array A containing N different integers, computes the maximum length of a sequence satisfying the above conditions.
For example, for the following array A:
[FONT="Courier New"]  A[0]  =  9   A[1]  = 10   A[2]  =  2
  A[3]  = -1   A[4]  =  3   A[5]  = -5
  A[6]  =  0   A[7]  = -3   A[8]  =  1
  A[9]  = 12   A[10] =  5   A[11] =  8
  A[12] = -2   A[13] =  6   A[14] =  4
[/FONT]the function should return 6.
A sequence of length 6 satisfying the given conditions can be as follows:
[FONT="Courier New"]  A[9] = 12    A[1] = 10    A[4] =  3
  A[8] =  1    A[6] =  0    A[7] = -3
[/FONT]
Assume that:
•	the elements of A are all distinct;
•	N is an integer within the range [1..100,000];
•	each element of array A is an integer within the range [&#8722;1,000,000,000..1,000,000,000].

Complexity:
•	expected worst-case time complexity is O(N);
•	expected worst-case space complexity is O(N), beyond input storage (not counting the storage required for input arguments).

Elements of input arrays can be modified.

I think recursion might be necessary, but I'm not exactly sure how to implement it.

Thanks

---

### Post by PaulM1985 on 2012-07-30
Homework by any chance?

---

### Post by dwally89 on 2012-07-30
> **PaulM1985 said:**
> Homework by any chance?
Nope, I'm not a student.
Any ideas on how to solve the problem?

---

### Post by ofnuts on 2012-07-30
> **dwally89 said:**
> Nope, I'm not a student.
Any ideas on how to solve the problem?

Why do I think about this: [http://xkcd.com/356/](http://xkcd.com/356/)  :)

I think you need to look a bit more in the implications of the rules. If I get the requirements right, I have the gut feeling (but you'll have to prove) that 
- the longuest sequence is between two local maxima
- if there is no other maxima in between (obviously smaller than the other two) then the sequence length is the number of points between the two (you zigzag you way down to the minimum)
- but things get hairy when you have inner maxima because you have to shortcut local minima as well as any points there below the inner maxima. For instance, if A[2] was 4, you would have one more point in the sequence.

All in all, I'm not sure I've been so helpful... for those who want to have a look here is a graphical representation of the problem on the sample data above:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=222014&d=1343689443[/IMG]

---

### Post by trent.josephsen on 2012-07-30
Very nice analysis. However, given only what you've said so far, I don't think I could do this in O(N) time in the worst case, which makes me think perhaps there's another logical shortcut the assignment expects.

You could definitely write a recursive solution but I think it would be on the order of n^2 in the worst case...

... wait, perhaps not. Basically the way it could work is each call to the function finds the maximum value, splits the array into two parts (the part to the left of the maximum and the part to the right of the maximum), then calls itself recursively on both the left-half and the right-half and returns one more than the greater value.

The slowest part is finding the maximum, which is O(n) by itself (high-water algorithm) and would give you O(n log n) complexity if I'm right. But I'm not convinced this isn't homework so I'll leave that up to OP.

---

### Post by dwally89 on 2012-07-31
> **trent.josephsen said:**
> Basically the way it could work is each call to the function finds the maximum value, splits the array into two parts (the part to the left of the maximum and the part to the right of the maximum), then calls itself recursively on both the left-half and the right-half and returns one more than the greater value.
I understand what you're saying here, but I'm not sure how to deal with the return values in order to provide the solution required.

> **trent.josephsen said:**
> The slowest part is finding the maximum, which is O(n) by itself (high-water algorithm) and would give you O(n log n) complexity if I'm right. But I'm not convinced this isn't homework so I'll leave that up to OP.
What is OP?
Nice to know that there's so much trust on these forums... I graduated almost a month ago (5th July). I'm simply doing this task to try and improve my existing skills, but as I said earlier, seem to have hit a brick wall.

I can post my current attempt at a solution if that helps?

---

### Post by Vaphell on 2012-07-31
OP=original post(er)

> I can post my current attempt at a solution if that helps?
sure

---

### Post by Tony Flury on 2012-07-31
> **dwally89 said:**
> I understand what you're saying here, but I'm not sure how to deal with the return values in order to provide the solution required.


What is OP?
Nice to know that there's so much trust on these forums... I graduated almost a month ago (5th July). I'm simply doing this task to try and improve my existing skills, but as I said earlier, seem to have hit a brick wall.

We do have a lot of people who try to get the forum to do their homework - and often the problems they are being asked to solve appear to just be algorithm problems (just like yours) - i.e. no real world application, so you will understand when people are sceptical.

OP : Original Poster - i.e. you :-)
> 
I can post my current attempt at a solution if that helps?

Often someone posting their own attempt helps - as that shows you have at least tried - and you aren't looking for a free lunch (as it were). Often we will try and help with obvious homework problems - if the OP has shown some attempt to solve the problem on their own and is bogged down with a problem.

Having said that - I can't get my head around a solution that has an O(n) complexity (i.e. linear), as any solution I can see would be around O(n log n) or worse as you need to compare some cells more than once.

The only solution i can see clearly would be a recursive one - starting at the highest point - and searching left and right for the next maxima - and stopping when there are no more to find - and each function returns the number of steps in the sequence it found.

---

### Post by dwally89 on 2012-07-31
Please find attached my attempt.

At the moment I'm not too concerned with the efficiency/complexity of the algorithm, I'm just trying to design one that works. Getting the complexity correct would be a bonus.

---

### Post by trent.josephsen on 2012-07-31
How about some pseudocode:

```
function sequence(list):
    let N = the number of elements in list
    if N = 0, return 0
    let index = the index of the maximum value in list
    let list-left = the elements of list from 0 to (index - 1) inclusive
    let list-right = the elements of list from (index + 1) to (N - 1) inclusive
    let value-left = sequence(list-left)
    let value-right = sequence(list-right)
    if value-left is greater than value-right:
        return 1 + value-left
    else:
        return 1 + value-right
```

Notice the base case -- if the list is empty, there is no such sequence, so the maximum length is 0. Every nonempty list will have at least one sequence of length 1 because both the constraints are (vacuously) true for any sequence of length 1.

Also notice that I didn't find the actual sequence; all I did was calculate its length. You could modify my algorithm to give the actual sequence, though.

If you're doing this in Java the most complicated part might be slicing the array. You can use Arrays.copyOfRange to do this easily but there's no equivalent of Python's list[start:end] or Perl's array slice notation. On the other hand, C or C++ can avoid that problem by passing a pointer into the array and a length calculated from that offset rather than making a new array every time.

Regarding complexity, I don't think it's possible to boil this algorithm down to O(n). Perhaps you could re-use the results of previous comparisons to find the maximum more quickly. But I think in the worst case that would still yield O(n log n) since you'd basically be sorting the whole thing first.

---

### Post by dwally89 on 2012-07-31
> **trent.josephsen said:**
> How about some pseudocode:

```
function sequence(list):
    let N = the number of elements in list
    if N = 0, return 0
    let index = the index of the maximum value in list
    let list-left = the elements of list from 0 to (index - 1) inclusive
    let list-right = the elements of list from (index + 1) to (N - 1) inclusive
    let value-left = sequence(list-left)
    let value-right = sequence(list-right)
    if value-left is greater than value-right:
        return 1 + value-left
    else:
        return 1 + value-right
```

Notice the base case -- if the list is empty, there is no such sequence, so the maximum length is 0. Every nonempty list will have at least one sequence of length 1 because both the constraints are (vacuously) true for any sequence of length 1.

Also notice that I didn't find the actual sequence; all I did was calculate its length. You could modify my algorithm to give the actual sequence, though.

If you're doing this in Java the most complicated part might be slicing the array. You can use Arrays.copyOfRange to do this easily but there's no equivalent of Python's list[start:end] or Perl's array slice notation. On the other hand, C or C++ can avoid that problem by passing a pointer into the array and a length calculated from that offset rather than making a new array every time.

Regarding complexity, I don't think it's possible to boil this algorithm down to O(n). Perhaps you could re-use the results of previous comparisons to find the maximum more quickly. But I think in the worst case that would still yield O(n log n) since you'd basically be sorting the whole thing first.

Thanks for your reply.
I've managed to code it up in Java and it returns the correct result.
Will have to read through it a few more times in order to fully understand it.

Thanks again

---

