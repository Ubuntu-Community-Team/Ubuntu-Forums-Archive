---
title: "Intermediate Programming Challenge #2"
date: 2010-02-21
forum: Programming Talk
---

### Post by sharpdust on 2010-02-21
There are 292 ways to make a U.S. dollar using only U.S. coins (293 if you include the dollar coin).
For those who unfamiliar with U.S. currency, here is a run-down.

penny = 1 (100 pennies equal 1 dollar)
nickel = 5 (20 nickels equal 1 dollar)
dime = 10 (10 dimes equal 1 dollar
quarter = 25 (4 quarters equal 1 dollar)
half-dollar = 50 (2 half-dollars equal 1 dollar)

Using just these 5 coins, write a program that generates all the possible combinations of coins that generate a dollar. You should make your program as generic as possible meaning that it should be able to accept any denomination for coin values and be able to calculate any arbitrary amount.


All the possible combinations are listed here:
[http://wiki.answers.com/Q/How_many_ways_to_make_change_for_a_dollar](http://wiki.answers.com/Q/How_many_ways_to_make_change_for_a_dollar)

---

### Post by Simon17 on 2010-02-21
Classic problem. I think I did it for Euler a while ago.

---

### Post by falconindy on 2010-02-21
[s]This late at night its not immediately clear to me how to remove the upper limit on this program, but this works up to 5 dollars... hurray nesting.[/s]

```
#include <stdio.h>
#include <stdlib.h>

#define NICKEL 5
#define DIME 10
#define QUARTER 25
#define HALFDOL 50

void printCombination(int, int, int, int, int);

int
main(int argc, char** argv) {
    if (argc != 2) {
        fprintf(stderr, "Usage: %s <amount>\n", argv[0]);
        return -1;
    }

    int target = atoi(argv[1]);
    int remainder;

    for(int i = 0; i <= target / HALFDOL; i++) {
        if (i * HALFDOL == target) {
            printCombination(i, 0, 0, 0, 0);
            continue;
        } else if (i * HALFDOL > target) break;
        for(int j = 0; j <= target / QUARTER; j++) {
            if (i * HALFDOL + j * QUARTER == target) {
                printCombination(i, j, 0, 0, 0);
                continue;
            } else if (i * HALFDOL + j * QUARTER > target) break;
            for (int k = 0; k <= target / DIME; k++) {
                if (i * HALFDOL + j * QUARTER + k * DIME == target) {
                    printCombination(i, j, k, 0, 0);
                    continue;
                } else if (i * HALFDOL + j * QUARTER + k * DIME > target) break;
                for (int l = 0; l <= target / NICKEL; l++) {
                    if (i * HALFDOL + j * QUARTER + k * DIME + l * NICKEL  == target) {
                        printCombination(i, j, k, l, 0);
                        continue;
                    } else if (i * HALFDOL + j * QUARTER + k * DIME + l * NICKEL > target) {
                        break;
                    } else {
                        remainder = target - i * HALFDOL + j * QUARTER + k * DIME + l * NICKEL;
                        printCombination(i, j, k, l, remainder);
                    }
                }
            }
        }
    }

    return 0;
}

void
printCombination(int hd, int q, int d, int n, int p) {
    printf("%d HD, %d Q, %d D, %d N, %d P\n", hd, q, d, n, p);
}
```

edit: Updated to calculate an arbitrary dollar value. There's 801451 ways to make $10. =D
edit2: Add short circuit checks to abort early if we've reached our target. Significantly speeds up values over $5.
edit3: More short circuits. Cheat if our target is divisible by 5.
edit4: dont bother with penny loop.

---

### Post by StephenF on 2010-02-21
```
#!/usr/bin/env python

"""A program to generate all combinations of coins to an arbitrary value.

   The term coins is used but notes could be substituted easily."""

class Coin(object):
    def __init__(self, value, singular, plural):
        self.value = value
        self.singular = singular
        self.plural = plural
        
    def __int__(self):
        return self.value

def calculate(coins, target, items=[]):
    if not coins or target == 0:
        if items and target == 0:
            print ", ".join(items)
        return
        
    coin = coins[0]    
        
    for qty in range(target / coin.value, -1, -1):
        if qty:
            if qty > 1:
                item = "%d %s" % (qty, coin.plural)
            else:
                item = "%d %s" % (qty, coin.singular)

            calculate(coins[1:], target - qty * coin.value, items + [item])
        else:
            calculate(coins[1:], target, items)

if __name__ == "__main__":
    coins = [Coin(x, y, z) for x, y, z in ((50, "half dollar", "half dollars"),
                                           (25, "quarter", "quarters"),
                                           (10, "dime", "dimes"),
                                           (5,  "nickel", "nickels"),
                                           (1,  "penny", "pennies"))]
    target = 100
    calculate(coins, target)
```

---

### Post by howlingmadhowie on 2010-02-21
Here's a solution in scheme.  I cheated and used the built-in sort function rather than writing my own.

```

(use-modules (ice-9 format))

(define coinfinder
  (lambda (coins total)
    (define make-tree
      (lambda (coins-left remainder)
        (cond ((= 0 remainder)
               '())
              ((null? coins-left)
               #f)
              ((<= (car coins-left) remainder)
               (cons (cons (car coins-left) (make-tree coins-left (- remainder (car coins-left))))
                     (make-tree (cdr coins-left) remainder)))
              (else
               (make-tree (cdr coins-left) remainder)))))

    (define get-solutions
      (lambda (tree)
        (let ((solutions '()))
          (define get-solutions-helper
            (lambda (start end)
              (cond ((equal? (cdr end) #f)
                     (if (pair? (car end))
                         (get-solutions-helper start (car end))))
                    ((not (pair? (car end)))
                     (if (null? (cdr end))
                         (begin
                           (set! solutions (cons (cons (car end) start) solutions)))
                         (get-solutions-helper (cons (car end) start) (cdr end))))
                    (else
                     (list (get-solutions-helper start (car end))
                           (get-solutions-helper start (cdr end)))))))

          (get-solutions-helper '() tree)
          solutions)))

    (get-solutions (make-tree (sort coins >) total))))

(define bunch
  (lambda (l)
    (define bunch-helper
      (lambda (found l)
        (cond ((null? l)
               found)
              ((null? found)
               (bunch-helper
                (list (cons (car l) 1))
                (cdr l)))
              ((equal? (caar found) (car l))
               (set-cdr! (car found) (+ 1 (cdar found)))
               (bunch-helper found (cdr l)))
              (else
               (bunch-helper (cons (cons (car l) 1) found) (cdr l))))))
    (bunch-helper '() l)))

(define display-line
  (lambda (line)
    (cond ((null? line)
           '())
          ((null? (cdr line))
           (format #t "~d ~d cent pieces.\n" (cdar line) (caar line))
           (display-line (cdr line)))
          (else
           (format #t "~d ~d cent pieces, " (cdar line) (caar line))
           (display-line (cdr line))))))

(define display-results
  (lambda (l)
    (if (null? l)
        '()
        (begin
          (display-line (bunch (car l)))
          (display-results (cdr l))))))


(display-results (coinfinder (list 1 5 10 25 50 100) 100))

```

It complains about a stack overflow when the total is increased to 3 dollars.

--edit--

Here's a much shorter version.  I've added a merge sort to the top, just to make sure the coins are in the right order :)

```

(use-modules (ice-9 format))

(define reverse-sort
  (lambda (l)
    (define list-of-lists
      (lambda (l)
        (if (null? l)
            '()
            (cons (list (car l)) (list-of-lists (cdr l))))))
    (define merge
      (lambda (l1 l2)
         (cond ((null? l1)
                l2)
               ((null? l2)
                l1)
               ((> (car l1) (car l2))
                (cons (car l1) (merge (cdr l1) l2)))
               (else
                (cons (car l2) (merge l1 (cdr l2)))))))

    (define pairwise-dispatch
      (lambda (l)
        (cond ((null? l) '())
              ((null? (cdr l))
               l)
              ((list? (cddr l))
               (cons (merge (car l) (cadr l)) (pairwise-dispatch (cddr l)))))))

    (define sort-helper
      (lambda (l)
        (cond ((null? (cdr l))
               (car l))
              (else
               (sort-helper (pairwise-dispatch l))))))

    (sort-helper (list-of-lists l))))

(define coinfinder
  (lambda (coins total)
    (define print-solution
      (lambda (solution)
        (if (null? solution)
            (newline)
            (begin
              (format #t "~d times ~d cents. " (cdar solution) (caar solution))
              (print-solution (cdr solution))))))

    (define update-found
      (lambda (found elem)
        (cond ((null? found)
               (list (cons elem 1)))
              ((equal? elem (caar found))
               (cons (cons elem (+ (cdar found) 1)) (cdr found)))
              (else
               (cons (cons elem 1) found)))))

    (define get-solutions
      (lambda (found coins-left remainder)
        (cond ((= 0 remainder)
               (print-solution found))
              ((null? coins-left)
               'done)
              ((<= (car coins-left) remainder)
               (get-solutions (update-found found (car coins-left)) coins-left (- remainder \
(car coins-left)))
               (get-solutions found (cdr coins-left) remainder))
              (else
               (get-solutions found (cdr coins-left) remainder)))))

    (get-solutions '() (reverse-sort coins) total)))

(display (coinfinder (list 1 5 10 25 50) 100))


```

This one also doesn't choke on large inputs.  The time it takes seems to be somewhat less than exponential in the total amount to be changed.  i'll see if i can work out why.

---

### Post by Some Penguin on 2010-02-21
falconindy:

Do you really need the innermost loop?  If you have determined quantities for all but one type of coin, there is at most one possible quantity for the remaining type.

---

### Post by falconindy on 2010-02-21
> **Some Penguin said:**
> falconindy:

Do you really need the innermost loop?  If you have determined quantities for all but one type of coin, there is at most one possible quantity for the remaining type.

excellent point. i definitely don't.

---

### Post by ssmithy on 2010-02-25
Here's my C++ submission that uses recursion.

Edit:  Since the program uses recursion you can increase/decrease the # of coins and it will still work.  I think it took about 10 minutes or so to run using 1,000 cents ($10).  Now I know that there are 801,451 different ways to make change!

```
#include <iostream>
using namespace std;

void ways(int, int [], int [], char [], int, int, int&);
void display(int [], int [], char [], int, int);
int sum(int [], int [], char [], int, int);

void ways(int pos, int value[], int count[], char name[], int coinNumber, int total, int &waysNum)
{		
	while (sum(value, count, name, coinNumber, total) < total)
	{
		count[pos]++;
		if (sum(value, count, name, coinNumber, total) == total)
		{
			display(value, count, name, coinNumber, total);
			waysNum++;
		}
		if (pos < coinNumber-1)  // pass the next value, unless it's the last value
			ways(pos+1, value, count, name, coinNumber, total, waysNum);
	}
	count[pos] = 0; // clear before moving to next pos
	if (pos < coinNumber-1)  // pass the next value, unless it's the last value
		ways(pos+1, value, count, name, coinNumber, total, waysNum);
	
} // end ways

void display(int value[], int count[], char name[], int coinNumber, int total)
{
	for (int i = 0; i < coinNumber; i++)
		cout << count[i] << name[i] << " ";
	cout << "= " << sum(value, count, name, coinNumber, total) << endl;
}

int sum(int value[], int count[], char name[], int coinNumber, int total)
{
	int sumN = 0;
	for (int i = 0; i < coinNumber; i++)
		sumN += count[i] * value[i];
	return sumN;
}

int main()
{
	const int total = 100;
	const int coinNumber = 5;
	int waysNum = 0;
	int value[coinNumber] = {50,25,10,5,1};
	int count[coinNumber] = {0,0,0,0,0};
	char name[coinNumber] = {'h','q','d','n','p'};
	ways(0, value, count, name, coinNumber, total, waysNum);
	cout << "There are " << waysNum << " different ways to make change." << endl;
	return 0;
}
```

---

### Post by StephenF on 2010-02-26
> **ssmithy said:**
> I think it took about 10 minutes or so to run using 1,000 cents ($10).
Code profiling would probably reveal that most of your computing time is being lost running the sum function or it could just be sluggishness due to the speed of your console on account of all that text.

In Python, Running on an Intel Core2 Quad QX6850 at 3GHz.
```

stephen@tmb ~/scripts $ time python coincombo.py | tail
8 nickels, 960 pennies
7 nickels, 965 pennies
6 nickels, 970 pennies
5 nickels, 975 pennies
4 nickels, 980 pennies
3 nickels, 985 pennies
2 nickels, 990 pennies
1 nickel, 995 pennies
1000 pennies
There are 801451 coin combinations in $10.00.

real	6m54.192s
user	6m54.013s
sys	0m0.107s

```
Updated source from #4, now prints a summary.
```

#!/usr/bin/env python

"""A program to generate all combinations of coins to an arbitrary value.

   The term coins is used but notes could be substituted easily."""

combo = 0

class Coin(object):
    def __init__(self, value, singular, plural):
        self.value = value
        self.singular = singular
        self.plural = plural
        
    def __int__(self):
        return self.value

def calculate(coins, target, items=[]):
    global combo

    if not coins or target == 0:
        if items and target == 0:
            print ", ".join(items)
	    combo += 1
        return
        
    coin = coins[0]    
        
    for qty in range(target / coin.value, -1, -1):
        if qty:
            if qty > 1:
                item = "%d %s" % (qty, coin.plural)
            else:
                item = "%d %s" % (qty, coin.singular)

            calculate(coins[1:], target - qty * coin.value, items + [item])
        else:
            calculate(coins[1:], target, items)

if __name__ == "__main__":
    coins = [Coin(x, y, z) for x, y, z in ((50, "half dollar", "half dollars"),
                                           (25, "quarter", "quarters"),
                                           (10, "dime", "dimes"),
                                           (5,  "nickel", "nickels"),
                                           (1,  "penny", "pennies"))]
    target = 1000 # Value in cents.
    calculate(coins, target)
    print "There are", combo, ("coin combinations in $%d.%02d."
                                                  % divmod(target, 100))


```
Rewritten in C it is much faster but that enormous speed advantage is only apparent when the tail command is used. Basically my console can't keep up.
```

stephen@tmb ~/test $ time ./a.out | tail
8 nickels, 960 pennies
7 nickels, 965 pennies
6 nickels, 970 pennies
5 nickels, 975 pennies
4 nickels, 980 pennies
3 nickels, 985 pennies
2 nickels, 990 pennies
1 nickel, 995 pennies
1000 pennies
There are 801451 coin combinations in $10.00.

real	0m1.421s
user	0m1.377s
sys	0m0.082s


```
The C source code.
```

#include <stdio.h>
#include <stdlib.h>

/* combination counter */
int combo = 0;

struct coin
    {
    int value;
    char *singular;
    char *plural;
    };
    
struct item
    {
    int qty;
    char *denom;
    struct item *next;
    };

/* copy the existing linked list and append a new item or create a new one */
struct item *new_item(struct item *items, int qty, char *denom)
    {
    struct item *base_item, *new_item, *r, *w, *prev = NULL;
    
    new_item = malloc(sizeof(struct item));
    if (!new_item)
        {
        printf("malloc failure\n");
        exit(5);
        }
    new_item->qty = qty;
    new_item->denom = denom;
    new_item->next = NULL;

    if (items)
        {
        for (r = items; r; r = r->next)
            {
            w = malloc(sizeof(struct item));
            if (!w)
                {
                printf("malloc failure\n");
                exit(5);
                }
            if (prev)
                prev->next = w;
            else
                base_item = w;
            w->qty = r->qty;
            w->denom = r->denom;
            w->next = NULL;
            prev = w;
            }
        
        w->next = new_item;

        return base_item;
        }
    else
        return new_item;
    } 

void print_items(struct item *item)
    {
    if (item->qty)
        printf("%d %s", item->qty, item->denom); 
    if (item->next)
        {
        if (item->qty)
            printf(", ");
        print_items(item->next);
        }
    else
        printf("\n");
    }

void free_items(struct item *item)
    {
    if (item->next)
        free_items(item->next);
    free(item);
    }

void calculate(struct coin coins[], int target, struct item *items)
    {
    struct coin *coin = coins;
    int qty;
    struct item *new_items;
    
    if (coin->value == 0 || target == 0)
        {
        if (items && target == 0)
            {
            print_items(items);
            combo++;
            }
        return;
        }
        
    for (qty = target / coin->value; qty >= 0; qty--)
        {
        if (qty == 1)
            new_items = new_item(items, qty, coin->singular);
        else
            new_items = new_item(items, qty, coin->plural);
           
        calculate(&coins[1], target - qty * coin->value, new_items);
        free_items(new_items);
        
        if (coins[1].value == 0)
            break;
        }
    }

int main(void)
    {
    static struct coin coins[] =
        {
        {50, "half dollar", "half dollars"},
        {25, "quarter", "quarters"},
        {10, "dime", "dimes"},
        {5, "nickel", "nickels"},
        {1, "penny", "pennies"},
        {0, NULL, NULL}
        };
        
    int target = 1000;
    
    calculate(coins, target, NULL);
    
    printf("There are %d coin combinations in $%d.%02d.\n", combo,
                                            target / 100, target % 100);
    return 0;
    }

```

---

### Post by Lux Perpetua on 2010-03-03
Yes, recursion is a natural approach to this, as most of the replies so far have demonstrated. However, there's an extremely simple iterative nonrecursive algorithm that generates all the combinations. Here's a C program implementing it. I made no attempt at optimization, so it isn't particularly fast. (For example, it doesn't use Some Penguin's observation that the amount of the last denomination is determined uniquely if you know all the others.) ```
#include <stdio.h>
#include <stdlib.h>

unsigned int *change;
unsigned int *den;
int p;

int N;

void print(void) {
    int q;
    for (q = 0; change[q] == 0; ++q);

    printf("%d(%d)", change[q], den[q]);
    
    for (++q; q < p; ++q) 
        if (change[q] > 0)
            printf(" + %d(%d)", change[q], den[q]);

    printf("\n");
}

int main(int argc, char **argv) {
    int q;
    
    if (argc < 3) {    
        fprintf(stderr, "Usage: %s N d1 [d2, ...]\n"
                "N = desired change; d1, d2, ... are the allowed "
                "denominations.\n", argv[0]);
        exit(EXIT_FAILURE);
    }

    N = atoi(argv[1]);
    p = argc - 2;

    den = malloc(p*sizeof(*den));
    change = malloc(p*sizeof(*change));

    if (!den || !change) {
        fprintf(stderr, "memory allocation error; aborting\n");
        exit(EXIT_FAILURE);
    }


    for (q = 0; q < p; ++q) {
        den[q] = atoi(argv[q + 2]);
        change[q] = 0;
    }

    q = p - 1;
    do {
        ++change[q];
        N -= den[q];

        if (N == 0) print();
        if (N <= 0) {
            N += change[q]*den[q];
            change[q] = 0;
            --q;
        } else {
            q = p - 1;
        }
    } while (q >= 0);

    free(den);
    free(change);

    return 0;
}
```

---

