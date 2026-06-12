---
title: "Programming Challenge #2: N-Queens Problem"
date: 2009-03-15
forum: Programming Talk
---

### Post by PythonPower on 2009-03-15
Since the [last programming challenge]("http://ubuntuforums.org/showthread.php?t=1066753") didn't get judged in the end, I thought I'd try again with a new challenge.

**Overview**

Most likely everyone here has at least heard of the [eight-queens problem]("http://en.wikipedia.org/wiki/Eight_queens_puzzle"). If not, it's the challenge of finding the number of ways eight queens can be arranged on an 8×8 chess board so that no queen can attack any other queen.

In fact, this can be extended slightly by allowing N queens to be positioned on an N×N board such that no queen can take another. And that's the N-queens problem. For example, when N=8 the number of solutions is 92 (not counting how many ways you can swap queens around; otherwise it would be 92*8! = 3709440).

**Problem**

Your problem, if you choose to accept it, is to create a program that takes an integer N and reports the number of solutions to the N-queens problem with that N.

**Winning**

One winner will be selected based on their entry. Most important is the algorithm's efficiency although clean, readable code and stability are musts too!

Any language is allowed (but please not LOLCODE - think of my sanity... ;)). The winner will be announced next Sunday (22 March 2009).

---

### Post by kknd on 2009-03-15
My solution uses backtracking. It prints the board with the queens positions.

```

#include <cstdio>

// Represents a state (stores the queens positions)
struct State
{
	int NSIDE;
	int* pos;
	
	State(int NSIDE)
	{
		this->NSIDE = NSIDE;
		this->pos = new int[NSIDE];
	}
	
	~State()
	{
		delete this->pos;
	}
	
	// Print the solution
	void print()
	{
		static int sol = 0;
		
		printf("Sol #%d:", ++sol);
		for(int i = 0; i < NSIDE; ++i) printf(" %d", pos[i]);
		printf("\n");
		
		for(int i = 0; i < NSIDE; ++i)
		{
			for(int j = 0; j < NSIDE; ++j)
				if(pos[i] == j)
					printf("R ");
				else
					printf("* ");
					
			printf("\n");
		}
		
		printf("\n");
	}
	
	// Checks if a queen pA attacks queen pB 
	bool attacks(int pA, int pB)
	{
		int tmp = pA - pB;
		if(pos[pA] == pos[pB]) return true;
		if(tmp == pos[pA] - pos[pB]) return true;
		if(tmp == pos[pB] - pos[pA]) return true;
		
		return false;
	}
	
	// Checks if any queen attacks another
	bool attacks(int n)
	{
		for(int i = 0; i < n; ++i)
			for(int j = i + 1; j < n; ++j)
				if(attacks(i, j))
					return true;
					
		return false;
			
	}
	
	// Search for a solution using backtracking
	void search(int n)
	{	
		if(n != NSIDE)
		{
			for(int i = 0; i < NSIDE; ++i)
			{
				pos[n] = i;
				if(!attacks(n + 1))
					search(n + 1);
			}
		}
		else
			print();
	}
};

int main(int argc, char* argv[])
{
	int NSIDE;
	scanf("%d", &NSIDE);
	
	State init(NSIDE);
	init.search(0);
	
	return 0;
}

```

---

### Post by jimi_hendrix on 2009-03-15
@above post

just curious...why use C++ but C IO?

---

### Post by kknd on 2009-03-15
> **jimi_hendrix said:**
> @above post

just curious...why use C++ but C IO?

C IO is usually faster... but this isn't a big issue here. I don't like C++ too, so I just use a subset of features that I like.

---

### Post by jimi_hendrix on 2009-03-15
> **kknd said:**
> C IO is usually faster... but this isn't a big issue here. I don't like C++ too, so I just use a subset of features that I like.

you might want to check out objc then

---

### Post by simeon87 on 2009-03-16
Not really a good problem for a competition as this problem has been solved before and often too...

---

### Post by PythonPower on 2009-03-16
[QUOTE=simeon87] Not really a good problem for a competition as this problem has been solved before and often too...[/QUOTE]

I did search in case the problem had been raised before but couldn't find anything that might "exhaust" the problem. Also, solutions can be improved on &#8212; the problem isn't closed yet!

---

### Post by mdawg414 on 2009-03-16
Done in LISP, specifically gcl but it should work on most common lisp interpreters.

Call like 
```
(QUEENS 8)
```
for an 8 queens problem. Replace 8 with the n of your choice

```

(defun VIOLATION (EXAMINED)
  (cond
    ((equal EXAMINED '()) NIL)
    (T (or (VIOL_HELPER (car EXAMINED) (cdr EXAMINED) 1) (VIOLATION (cdr EXAMINED))))))



(defun VIOL_HELPER (CURRENT REST OFFSET)
  (cond
    ((equal REST '()) NIL)
    ((equal CURRENT (car REST)) T)
    ((equal (abs (- (car REST) CURRENT)) OFFSET) T)
    (T (VIOL_HELPER CURRENT (cdr REST) (+ 1 OFFSET)))))



(defun QUEENS (N)
  (QUEENS_HELPER '() N '()))



(defun QUEENS_HELPER (EXAMINED N SOLNS)
  (cond
    ((VIOLATION EXAMINED) '())
    ((equal (length EXAMINED) N) (append SOLNS (list EXAMINED)))
    (T (MAKE_CHILDREN EXAMINED N N SOLNS))))


(defun MAKE_CHILDREN (EXAMINED NEXT_NUM N SOLNS)
  (cond
    ((equal NEXT_NUM 0) '())
    (T (append (QUEENS_HELPER (append EXAMINED (list NEXT_NUM)) N SOLNS) (MAKE_CHILDREN EXAMINED (- NEXT_NUM 1) N SOLNS)))))

```

This uses chronological backtracking to avoid checking too many possibilities, making an N of 100 feasible. Let me know any feedback!

I should at least mention what this returns. It returns all of the possibilities for solving the problem as lists of row numbers. For example, (QUEENS 4) gives ((3 1 4 2) (2 4 1 3)).
This means there are 2 solutions, one with queens located at (1,3) (2,1) (3,4) (4,2) and the other with queens at (1,2) (2,4) (3,1) (4,3)

---

### Post by PythonPower on 2009-03-22
Well this challenge was really close in the end. Neither program did quite as asked (IE: just print the number) but kknd's solution did show the number of solutions too. It also scaled slightly better in my tests.

mdawg414's solution was neat (as far as I can tell) and worked well too. But the winner by just a hair is **kknd**! This means he is responsible for creating the next challenge - I look for forwards to it!

---

