---
title: "Weekly Programming Challenge - Friday, Dec 8, 2006"
date: 2006-12-08
forum: Programming Talk
---

### Post by po0f on 2006-12-08
**Rules**:
[list]
[*]Any language is allowed.  (No swearing though, please :))
[*]Extensive use of external libraries is frowned upon, and may be grounds for being frowned upon.
[*]Submissions must meet the requirements and must be programmed within any limitations imposed posted on the challenge page.  
[*]All submissions for the challenge **will be accepted for a period of** six (6) days after the initial posting of the contest.  (For example, challenge starts 1 Dec, submissions in by 6 Dec)  The final day will be for drinking apple juice. (s/must be submitted/bold text/, just to clarify)
[*]A user will be randomly (as randomly as possible) picked to post the following week's challenge.  If the user doesn't post a new challenge in a timely fashion, then I'll post one.  :twisted: 
[*]All code will be considered [public domain](http://creativecommons.org/licenses/publicdomain/), unless the submitter chooses to release it under a different license.
[/list]
(Rules subject to change, since I kinda made them up on the spot.)

**Objective**:
*Programmatically* (no fill in the box, please) create a 10x10 matrix multiplication table.  Example (snipped) output:
```
[FONT="Courier New"]
 1  2  3  4  5  6  7  8  9 10
 2  4  6  8 10 12 14 16 18 20
 3  6  9 12 15 18 21 24 27 30
...[/FONT]
```
Well, you get the idea.

**Limitations**:
None (at this time).

**Bonus**:
None (at this time).

Good luck and have fun!  :)

---

### Post by meng on 2006-12-08
My humble python effort.
```
def table(x, y):
    for i in range(x):
        for j in range(y):
            x = (i+1) * (j+1)
            print "%4d" % x,
        print
table(10,10)
```

---

### Post by po0f on 2006-12-08
meng,

You have been "randomly" picked to post next week's challenge, congrats!  :)


Everyone,

If you have any suggestions for limitations or bonuses for this week's challenge, please post them and they will be considered for addition to the challenge.

---

### Post by ghostdog74 on 2006-12-08
```

#!/usr/bin/python
for table in [ [ i*j for i in range(11) ] for j in range(11) ] :
    print table

```

---

### Post by po0f on 2006-12-08
ghostdog74,

Don't you just love list comprehension?  :)

---

### Post by ghostdog74 on 2006-12-08
haha..well too much of it is also not good. Makes code unreadable. But in this case, its not that bad.
anyway, i like many things in Python, not just list comprehensions...:)

---

### Post by amo-ej1 on 2006-12-08
typical implementation in C

```

#include <stdio.h>

int main(int argc, char **argv){
        int i,j;
        for(i=1;i<=10;i++){
                for(j=1;j<=10;j++){
                        printf("%4d", i*j);
                }
                printf("\n");
        }
}

```

edit: alternative would be to replace the inner loop by one printf() but i don't like typing that much ;)

---

### Post by &lt;mawe&gt; on 2006-12-08
Hi!

I know you don't like external libraries, but ...
```
from Numeric import fromfunction

print fromfunction( lambda x, y: (x+1)*(y+1), (10,10) )
```
A short Ruby version:
```
(1..10).each {|i| (1..10).each {|j| printf "%4s",(i*j)}; puts}
```
And one in OCaml (I'm just learning OCaml, so this might not be a very clever one :))
```
let table x y =
  for i=1 to x do
    for j=1 to y do
      Printf.printf "%4i" (i*j);
    done;
    print_string "\n"
  done;;

table 10 10
```
UPDATE:
Bash
```
#!/bin/bash

i=1; j=1;

while [ $i -le 10 ]
do (
  while [ $j -le 10 ]
  do
    echo -n "$[ $i*$j ] "
    j=$[ $j + 1 ]
  done
  )
  echo
  i=$[ $i + 1 ]
done
```
Fortran90
```
program table
  implicit none

  integer :: x, y

  do x=1, 10
    do y=1, 10
      write(*,'(i4)',advance='no') x*y
    end do
    write(*,*)
  end do

end program table
```

Regards, mawe

---

### Post by lnostdal on 2006-12-08
For color-highlighting and correct indentation please see:
  [http://paste.lisp.org/display/31644](http://paste.lisp.org/display/31644)


edit: 
..I've stored it here also:
[http://nostdal.org/~lars/programming/lisp/ubuntu-contest/matrix-multiplication-thing.lisp](http://nostdal.org/~lars/programming/lisp/ubuntu-contest/matrix-multiplication-thing.lisp) (in case the paste goes down; it happens)



edit2:
A small improvement would be having 1 as a default argument for `:num-rows':
```
...
(defun makeMatrixMultiplicationTable (&key (num-rows 1) (num-cols num-rows) (formatted nil))
...

```

---

### Post by Arndt on 2006-12-08
> **po0f said:**
> 

**Objective**:
*Programmatically* (no fill in the box, please) create a 10x10 matrix multiplication table.  Example (snipped) output:
```
[FONT="Courier New"]
 1  2  3  4  5  6  7  8  9 10
 2  4  6  8 10 12 14 16 18 20
 3  6  9 12 15 18 21 24 27 30
...[/FONT]
```
Well, you get the idea.



Perl one-liner:

```
perl -e 'for $i (1..10) {for $j (1..10) {printf "%4d", $i*$j} print "\n"}'
```

In your table above, there are multiple spaces, so the columns should be aligned, but multiple spaces seem to be replaced with single ones when the 'code' tag is used.

---

### Post by Klipt on 2006-12-08
> **ghostdog74 said:**
> ```
...[ [ i*j for i in range(11) ] for j in range(11) ]
```

In lisp:

```
(lc (lc (* i j) i (range 11)) j (range 11))
```

...provided you first define lc (list comprehension)
```
(defmacro lc (expr var list)
   `(mapcar (lambda (,var) ,expr) ,list))
```

and range (using tail recursion, bad, but I don't know how lisp's loops work yet)
```

(defun range (n)
   (defun inner-range (list n)
      (if (<= n 0) list
                  (inner-range (cons (- n 1) list) (- n 1))))
   (inner-range () n))
```

Unfortunately the interactive reader cuts the answer short

```
(lc (lc (* i j) i (range 11)) j (range 11))
((0 0 0 0 0 0 0 0 0 0 ...) (0 1 2 3 4 5 6 7 8 9 ...)
 (0 2 4 6 8 10 12 14 16 18 ...) (0 3 6 9 12 15 18 21 24 27 ...)
 (0 4 8 12 16 20 24 28 32 36 ...) (0 5 10 15 20 25 30 35 40 45 ...)
 (0 6 12 18 24 30 36 42 48 54 ...) (0 7 14 21 28 35 42 49 56 63 ...)
 (0 8 16 24 32 40 48 56 64 72 ...) (0 9 18 27 36 45 54 63 72 81 ...) ...)
```

---

### Post by lnostdal on 2006-12-08
> **Klipt said:**
> 
...
..and range (using tail recursion, bad, but I don't know how lisp's loops work yet)
```

(defun range (n)
   (defun inner-range (list n)
      (if (<= n 0) list
                  (inner-range (cons (- n 1) list) (- n 1))))
   (inner-range () n))
```
...


(edit: one normally use something like `flet' or `labels' to define inner-functions btw.)

Here is a version using loop:

```

cl-user> (loop :for i :from 0 :to 9 :collecting i)
(0 1 2 3 4 5 6 7 8 9)

```

..some Lispers are not confortable with `loop', they might do something like this - without recursion:

```

cl-user> (let (res)
           (dotimes (i 10)
             (push i res))
           (nreverse res))
(0 1 2 3 4 5 6 7 8 9)

```


(someone should really fix the indention-issues in the forum btw. .. is there someone we could contact?)

---

### Post by shining on 2006-12-08
A basic recursive version in caml:

```

let mult n = 
  let rec aux = function
    | (i,j) when i<n -> print_int (i*j); print_string(" "); aux (i+1,j)
    | (i,j) when i=n && j<n -> print_int (i*j); print_newline(); aux(1, j+1)
    | (i,j) -> print_int(i*j); print_newline()
  in aux (1,1);;

mult 10;;

```

---

### Post by bradleyd on 2006-12-08
Arndt beet me to perl example, but this is all I have come up with for now.

#!/usr/bin/perl -w

for $x (1..10) {

for $j (1..10) {
	printf "%4d",$x*$j;
}	
	print ("\n");
}
print "Enter first number To multiply:\n";
my $first_number=<STDIN>;
chomp($first_number);
print "Enter second number To multiply:\n";
my $second_number=<STDIN>;
chomp($second_number);
my $result=($first_number*$second_number);
print ("$first_number X $second_number = $result\n");

---

### Post by daz4126 on 2006-12-08
In Ruby:

```
1.upto(10) do |x| 
        1.upto(10) do |y| 
        print x * y,"\t" 
        end
        puts 
end
```


DAZ

---

### Post by hod139 on 2006-12-08
Here's a bash solution (doesn't do a pretty print, didn't want to think about that)
```

for j in 1 2 3 4 5 6 7 8 9 10
do
for i in 1 2 3 4 5 6 7 8 9 10
do
echo -n "`expr $i \* $j`   "
done
echo ""
done

```

---

### Post by Ramses de Norre on 2006-12-08
In java:
```
public class MultMatr
{		
    final public static void main(String[] args)
    {
        java.util.Scanner keys=new java.util.Scanner(System.in);
        StringBuffer res=new StringBuffer();
        System.out.print("Give dimension?:");
        int dim=keys.nextInt();                
        for(int i=0;i<dim;i++)
        {
            int k=0;
            for(int j=0;j<dim;j++)
            {
            	k+=i+1;
                res.append(k+"\t");
            }
            res.append("\n");
        }
        System.out.println(res.toString());
    }
}


```
(and not a single multiplication)

---

### Post by Verminox on 2006-12-08
Once again I shall attempt the one liner in C++.

To set this apart from the rest, i've used only one loop instead of two nested ones.

```
#include <iostream>
int main(){
    for(int i=1,j=1;i<=100;printf("%4d",i),i++,printf(((j++%10==0)?"\n":" ")));
}

```


;)

---

### Post by SZorg on 2006-12-08
This is, actually, rather hilarious. Just two days ago I, as an ultra-newbie to programming, specifically python, struggled to make exactly that -- a 10x10 matrix.

I could've used this a couple of days ago. :p

---

### Post by meng on 2006-12-08
One presumes you've moved on to more difficult tasks, in which case congratulations. In any case, this exercise (the "contest") is good for getting exposure to new ideas, but it's not until you implement them yourself that you'll actually learn it. For instance, my understanding of list comprehensions in python continues to grow when I see examples like those posted here, but I'll know that I really grasp it when I'm able to use it myself.

---

### Post by scc4fun on 2006-12-08
> **amo-ej1 said:**
> typical implementation in C

```
int main(int argc, char **argv){
```

Any reason you use arguments when no input is needed?

---

### Post by Wybiral on 2006-12-08
This is in c++, you enter the dimensions of the multiplication table as arguments. It also formats it to even spacing (provided your dimensions dont have a product of 1000 or more). Not the most efficient, but I figured it would be a nice example of using arguments and converting cstrings to integers (as well as maintaining a digit length in an integer).

```

#include <iostream>

using namespace std;

void createTable(int width, int height){
 for(int y=1; y<=height; y++){
  for(int x=1; x<=width; x++){
   if(x*y<10)
    {cout<<"00"<<x*y<<" ";}
   else if(x*y<100)
    {cout<<"0"<<x*y<<" ";}
   else
    {cout<<x*y<<" ";}
   }
   cout<<endl;
  }
}

int main(int argc, char* argv[]){
 if(argc==3){createTable(atoi(argv[1]), atoi(argv[2]));}
 else{cout<<"Incorrent argument count!\nMust specify width and height!"<<endl;}
 return 0;
}

```

> 
davy@davy:~/Desktop$ ./a.out 10 10
001 002 003 004 005 006 007 008 009 010 
002 004 006 008 010 012 014 016 018 020 
003 006 009 012 015 018 021 024 027 030 
004 008 012 016 020 024 028 032 036 040 
005 010 015 020 025 030 035 040 045 050 
006 012 018 024 030 036 042 048 054 060 
007 014 021 028 035 042 049 056 063 070 
008 016 024 032 040 048 056 064 072 080 
009 018 027 036 045 054 063 072 081 090 
010 020 030 040 050 060 070 080 090 100 


---

### Post by duff on 2006-12-08
blah..the STL was more trouble than it's worth this time.
```

#include <vector>
#include <iostream>
#include <iterator>
#include <functional>
#include <ext/functional>
#include <ext/numeric>

using __gnu_cxx::compose1;
using __gnu_cxx::compose2;
using __gnu_cxx::iota;

int main(int argc, char *argv[])
{
   int n = atoi(argv[1]);
   std::vector<int> numbers(n*n);
   iota(numbers.begin(), numbers.end(), 0);
   std::transform(numbers.begin(), numbers.end(), 
                   std::ostream_iterator<int>(std::cout, " "),
                   compose2(
                      std::multiplies<int>(),
                      compose1(
                        std::bind2nd(std::plus<int>(), 1),
                        std::bind2nd(std::modulus<int>(), n)),
                      compose1(
                        std::bind2nd(std::plus<int>(), 1),
                        std::bind2nd(std::divides<int>(), n))));
}
```

Boost's lambda functions would've made this easier to do.

---

### Post by diggity on 2006-12-08
Here's a quick 'n dirty php/html example

```

<?php
echo '<table cellpadding="2" cellspacing="0" border="1">';
for($i=1; $i<=10; $i++)
{
    echo '<tr>';
    for($j=1; $j<=10; $j++)
    {
        echo '<td align="right">'.$i*$j.'</td>';
    }
    echo '</tr>';
}
echo '</table>';
?>

```

---

### Post by thk on 2006-12-08
> tkeitt@sparverius:~$ R

R : Copyright 2006, The R Foundation for Statistical Computing
Version 2.3.1 (2006-06-01)
ISBN 3-900051-07-0

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

> outer(1:10, 1:10)
      [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]
 [1,]    1    2    3    4    5    6    7    8    9    10
 [2,]    2    4    6    8   10   12   14   16   18    20
 [3,]    3    6    9   12   15   18   21   24   27    30
 [4,]    4    8   12   16   20   24   28   32   36    40
 [5,]    5   10   15   20   25   30   35   40   45    50
 [6,]    6   12   18   24   30   36   42   48   54    60
 [7,]    7   14   21   28   35   42   49   56   63    70
 [8,]    8   16   24   32   40   48   56   64   72    80
 [9,]    9   18   27   36   45   54   63   72   81    90
[10,]   10   20   30   40   50   60   70   80   90   100
>  1:10 %*% t(1:10)
      [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]
 [1,]    1    2    3    4    5    6    7    8    9    10
 [2,]    2    4    6    8   10   12   14   16   18    20
 [3,]    3    6    9   12   15   18   21   24   27    30
 [4,]    4    8   12   16   20   24   28   32   36    40
 [5,]    5   10   15   20   25   30   35   40   45    50
 [6,]    6   12   18   24   30   36   42   48   54    60
 [7,]    7   14   21   28   35   42   49   56   63    70
 [8,]    8   16   24   32   40   48   56   64   72    80
 [9,]    9   18   27   36   45   54   63   72   81    90
[10,]   10   20   30   40   50   60   70   80   90   100
> 

R always feels like you're cheating... ;)

---

### Post by meng on 2006-12-08
> **thk said:**
> R always feels like you're cheating... ;)
Good one! A good example of choosing the right tool (language) first then formulating the solution.

---

### Post by ghostdog74 on 2006-12-09
There's Numpy for Python. Eg.

```

#!/usr/bin/python
import numpy
a = range(11)
b = range(11)
for i in numpy.outerproduct(a,b):
    print i

```

output:
```

[0 0 0 0 0 0 0 0 0 0 0]
[ 0  1  2  3  4  5  6  7  8  9 10]
[ 0  2  4  6  8 10 12 14 16 18 20]
[ 0  3  6  9 12 15 18 21 24 27 30]
[ 0  4  8 12 16 20 24 28 32 36 40]
[ 0  5 10 15 20 25 30 35 40 45 50]
[ 0  6 12 18 24 30 36 42 48 54 60]
[ 0  7 14 21 28 35 42 49 56 63 70]
[ 0  8 16 24 32 40 48 56 64 72 80]
[ 0  9 18 27 36 45 54 63 72 81 90]
[  0  10  20  30  40  50  60  70  80  90 100]

```

---

### Post by &lt;mawe&gt; on 2006-12-09
[quote="Verminox"]Once again I shall attempt the one liner in C++.

To set this apart from the rest, i've used only one loop instead of two nested ones.

```

#include <iostream> 
int main(){   
  for(int i=1,j=1;i<=100;printf("%4d",i),i++,printf(((j++%10==0)?"\n":" ")));
}
```[/quote]
This doesn't really produce the desired output :)

---

### Post by Ramses de Norre on 2006-12-09
> **hod139 said:**
> Here's a bash solution (doesn't do a pretty print, didn't want to think about that)
```

for j in 1 2 3 4 5 6 7 8 9 10
do
for i in 1 2 3 4 5 6 7 8 9 10
do
echo -n "`expr $i \* $j`   "
done
echo ""
done

```

You can replace the for loops with ```
for((i=0;i<=10;i++))
``` this gets really handy when you've got even more than 10 numbers to iterate over.

---

### Post by jayemef on 2006-12-09
> **Ramses de Norre said:**
> You can replace the for loops with ```
for((i=0;i<=10;i++))
``` this gets really handy when you've got even more than 10 numbers to iterate over.

Better yet, use the seq command:
```
for x in `seq 1 10`
# OR
for x in $(seq 1 10)

```

---

### Post by cgrebeld on 2006-12-09
My Haskell contribution:

```

main = do
    putStr $ concat.concat $ map genRow nums
    where
        genRow col = (map ((++" ").show.(*col)) nums) ++ ["\n"]
        nums = [1..10]

```

---

### Post by abarth on 2006-12-09
In octave without loops:

[x,y] = meshgrid(1:10);
x.*y

ans =

    1    2    3    4    5    6    7    8    9   10
    2    4    6    8   10   12   14   16   18   20
    3    6    9   12   15   18   21   24   27   30
    4    8   12   16   20   24   28   32   36   40
    5   10   15   20   25   30   35   40   45   50
    6   12   18   24   30   36   42   48   54   60
    7   14   21   28   35   42   49   56   63   70
    8   16   24   32   40   48   56   64   72   80
    9   18   27   36   45   54   63   72   81   90
   10   20   30   40   50   60   70   80   90  100

---

### Post by JmSchanck on 2006-12-09
In Python:
```

>>> for i in [range(n, n*10+1, n) for n in range(1,11)]:
...      print i
... 
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
[3, 6, 9, 12, 15, 18, 21, 24, 27, 30]
[4, 8, 12, 16, 20, 24, 28, 32, 36, 40]
[5, 10, 15, 20, 25, 30, 35, 40, 45, 50]
[6, 12, 18, 24, 30, 36, 42, 48, 54, 60]
[7, 14, 21, 28, 35, 42, 49, 56, 63, 70]
[8, 16, 24, 32, 40, 48, 56, 64, 72, 80]
[9, 18, 27, 36, 45, 54, 63, 72, 81, 90]
[10, 20, 30, 40, 50, 60, 70, 80, 90, 100]

```

edit: more compact version:
```

print "\n".join([str(range(n, n*10+1, n)) for n in range(1,11)])

```

---

### Post by Peepsalot on 2006-12-09
Here is a solution in javascript

for ease of use, paste this URL into your browser
```
javascript:document.write('<table style="width:100%">');for(i=1;i<=10;++i){document.write('<tr>');for(j=1;j<=10;++j)document.write('<td>'+i*j+'</td>');document.write('</tr>');}
```

legible version:
```

<script type="text/javascript">
document.write('<table style="width:100%">')
for(i=1;i<=10;++i){
	document.write('<tr>')
	for(j=1;j<=10;++j){
		document.write('<td>'+i*j+'</td>');
	}
	document.write('</tr>');
}
</script>

```

---

### Post by &lt;mawe&gt; on 2006-12-10
2 more Perl versions:
-) a one-liner:
```
for$-(1..10){printf"%4d",$_*$-for1..10;print$/}
```
-) what would Perl be without CPAN :)
```
use Math::MultiplicationTable;

print Math::MultiplicationTable::generate(10);
```

---

### Post by pmasiar on 2006-12-10
I vote for meng's solution as most readable and easier to maintain. Python wins - again :-)

Slight improvement to readability: range() has optional <start from> parameter. Also, 1-character variable names are hard to refactor, I use ii instead of i. Meng, if you used better parameter names, you would notice that you reused x.

Also, range() produces whole list which might be huge. xrange() iterates one item at a time.

so:
```
def table(rowNum, colNum):
    """multiplication table: improving over meng's solution"""
    for ii in xrange(1, rowNum):
        for jj in xrange(1, colNum):
            print "%4d" % (ii * jj)
        print
table(10,10)
```

---

### Post by allix on 2006-12-10
Here's my C++ solution. This is the first time I've programmed in C++ for at least 2 years so don't flame me i i f-ed up hehe.  ;)

```
#include <iostream>

using namespace std;

int main()
{
	cout << "Multiplication table" << endl;
	cout << "====================================\n";
	
	for( int i = 1; i <= 10; i++){
	
		for (int j = 1; j <= 10; j++){
			cout << i*j << "\t";
		}
		
		cout << endl;
	}
	return 0;
}

```

Outputs:

```
Multiplication table
====================================
1       2       3       4       5       6       7       8       9       10
2       4       6       8       10      12      14      16      18      20
3       6       9       12      15      18      21      24      27      30
4       8       12      16      20      24      28      32      36      40
5       10      15      20      25      30      35      40      45      50
6       12      18      24      30      36      42      48      54      60
7       14      21      28      35      42      49      56      63      70
8       16      24      32      40      48      56      64      72      80
9       18      27      36      45      54      63      72      81      90
10      20      30      40      50      60      70      80      90      100

```

---

### Post by meng on 2006-12-10
> **pmasiar said:**
> I vote for meng's solution as most readable and easier to maintain. Python wins - again :-)

Slight improvement to readability: range() has optional <start from> parameter. Also, 1-character variable names are hard to refactor, I use ii instead of i. Meng, if you used better parameter names, you would notice that you reused x.

Also, range() produces whole list which might be huge. xrange() iterates one item at a time.
Thanks this will help me to code better in future. I assume my reuse of x only has local scope.

---

### Post by studiesrule on 2006-12-10
I've been waiting to try this out for a long time:
BRAINFUCK!!! (expletive not intended)

Uncommented code:
> 
++++++++++.>++++++++++++++++++++++++++++++++>+++++
[>++++++++++>>++++++++++<<<-]>-->>--<<<++++++++++
[>>++++++++++[<.>>.+<<<<.>>>-][<.>>.+<<<<.>>>-]
>----------<<+<<<.>>-]<<.

It's supposed to be one line, but it really screws up the page.

Commented code:
> 
Memory allocation /n /sp i1 n1 i2 n2

++++++++++.  ##newline (/n)
>++++++++++++++++++++++++++++++++	##space (sp)
>+++++				#initialises nos to 50
[>++++++++++>>++++++++++<<<-]	#
>-->>--<<<	#brings them to 0
++++++++++	#intialise i1
[
>>++++++++++	#initilise i2
[
<.>>.+<<<<.>>>-	#print n1 print n2 space decr i2
]
>----------	#reinitialise n2
<<+		#incr n1
<<<.		#print /n
>>-		#decr i1
]
<<.		#print /n


Output:
> 
00 01 02 03 04 05 06 07 08 09
10 11 12 13 14 15 16 17 18 19
20 21 22 23 24 25 26 27 28 29
30 31 32 33 34 35 36 37 38 39
40 41 42 43 44 45 46 47 48 49
50 51 52 53 54 55 56 57 58 59
60 61 62 63 64 65 66 67 68 69
70 71 72 73 74 75 76 77 78 79
80 81 82 83 84 85 86 87 88 89
90 91 92 93 94 95 96 97 98 99


I know it's not precisely what was asked, but I think its close enough (I'd have to add very little, but I like this output more)

This is the first time I've programmed using it, I'm telling you its the easiest language I've ever learnt (the stupidest too, but then again I was thinking about Tolkien elvish...)

Read about it:
[http://en.wikipedia.org/wiki/Brainfuck](http://en.wikipedia.org/wiki/Brainfuck)
Compiled using BrainFoo:
[http://brainfoo.sourceforge.net/](http://brainfoo.sourceforge.net/)

---

### Post by Jessehk on 2006-12-10
```

def table(size):
    """
    Draw a multiplication table
    with sides of length "size".
    """
    format_size = len(str(size ** 2))

    for i in range(1, size + 1):
        for j in range(1, size + 1):
            print "%*d" % (format_size, i * j),

        print ""

if __name__ == "__main__":
    table(10)

```

My function will print out a table of any length with correct formatting.

EDIT: Forgot to show the output:
```

  1   2   3   4   5   6   7   8   9  10 
  2   4   6   8  10  12  14  16  18  20 
  3   6   9  12  15  18  21  24  27  30 
  4   8  12  16  20  24  28  32  36  40 
  5  10  15  20  25  30  35  40  45  50 
  6  12  18  24  30  36  42  48  54  60 
  7  14  21  28  35  42  49  56  63  70 
  8  16  24  32  40  48  56  64  72  80 
  9  18  27  36  45  54  63  72  81  90 
 10  20  30  40  50  60  70  80  90 100 

```

EDIT2: It's properly formatted in the terminal, but the forum can't seem to align things correctly.

---

### Post by dwblas on 2006-12-10
> I assume my reuse of x only has local scope.I would agree that the two are different even though they have the same name.  It is confusing though.  See here [http://en.wikipedia.org/wiki/Name_mangling](http://en.wikipedia.org/wiki/Name_mangling) for Wikipedia's name-mangling.> Also, range() produces whole list which might be huge. xrange() iterates one item at a time.Also true, but the general rule of thumb IFAIK is that there is no appreciable difference until you get into a range of 10,000.  If some else knows more, please post it.

---

### Post by [knap] on 2006-12-10
My contribution in C

```
#include <stdio.h>

int m[10][10], d, n; 

  main() {

  for(n=1;n<11;n++) {
    d = 1;
      while(d<11) {
      m[n][d] = n * d;
      if(d==10) printf("%d\n",m[n][d]);
      else printf("%d ",m[n][d]); 
      d++; }
}
  }
```

Started learning C about 2 months ago at college.

---

### Post by 916 on 2006-12-10
**c++**:
```

#include <iostream.h>
void main()
{
	for(int i=1;i<=10;i++)
	{
		for(int j=0;j<10*i;j+=i)
			cout<<i+j<<"  ";
		cout<<endl;
	}
}
```
**Pascal**:
```
Program Dec_08_try;
var i,j:integer;
begin
 j:=0;
 for i:=1 to 10 do begin
   while j<i*10 do begin
     writeln(i+j,' ');
     inc(j,i);
     end;
   writeln;
   end;
 end.
```:)

---

### Post by otaviocc on 2006-12-10
Wolfram's Mathematica

```
Table[i*j, {i, 1, 10}, {j, 1, 10}] // MatrixForm
```

---

### Post by tkjacobsen on 2006-12-10
I know octave is not a real programming language, but I couldn't resist the temptation:

```

 [1:10]'*[1:10]

```

Here is a similar in python using numpy:
```

from numpy import *
a=matrix(linspace(1,10,10)).T* matrix(linspace(1,10,10))
print a

```

---

### Post by dwblas on 2006-12-10
I wanted to try a Python string.join solution but JmSchanck beat me to it so here is a deque append(left) soloution with a little flavor added to make it difficult.  It is printed as a spiral, beginning with column 6 and row 6 because 10 doesn't divide by 4 evenly, also with underscores to preserve spacing.  Output = > _10__20__30__40__50__60__70__80__90_100
_90__42__48__54__60___7__14__21__28__35
_81__36___4___8__12__16__20__24__28__42
_72__30__30___6___8__10__12__14__32__49
_63__24__27___4___3___4___5__16__36__56
_54__18__24___2___2___1___6__18__40__63
_45__12__21__10___9___8___7__20___5__70
_36___6__18__15__12___9___6___3__10___8
_27__50__45__40__35__30__25__20__15__16
_18___9__80__72__64__56__48__40__32__24Code:```
import string
from collections import deque

##========================================================================
def PrintSpiral( total_cols, total_rows ) :
   d_list = []  ## hold pointers for 'total_rows' separate deque objects
   for j in range( 0, total_rows ) :
      d_list.append( deque( ) )

   ##  find center square
   this_y = total_rows / 2
   d_list[this_y].append( 1 )

   num_ctr = 1        ## the number to print
   incr = 1           ## 1 for first 10, 2 for second 10, etc
   num_cols = 1       ## number of columns to print for this row for this pass
   x_dir = True       ## True  = + direction (right for x, down for y)
   y_dir = True       ## False = - direction (left for x, up for y)

   for j in range( 0, total_rows ) :
      x_dir = not x_dir
      for k in range( 0, num_cols ) :
         num_ctr += incr
         if num_ctr > incr * 10 :
           incr += 1
           num_ctr = incr
         if incr < 11 :
            if x_dir == True :
               d_list[this_y].append( num_ctr )
            else :
               d_list[this_y].appendleft( num_ctr )

      y_dir = not y_dir
      for k in range( 0, num_cols ) :
         num_ctr += incr
         if num_ctr > incr * 10 :
           incr += 1
           num_ctr = incr
         if incr < 11 :
            if y_dir == True :
               this_y += 1
               d_list[this_y].append( num_ctr )
            else :
               this_y -= 1
               d_list[this_y].appendleft( num_ctr )
      num_cols += 1
        
   for p in range( 0, total_rows ) :
      for each_num in d_list[p] :
         print "%3d" % (each_num),
      print
##========================================================================
if __name__ == "__main__" :
   try :
      PrintSpiral( 10, 10 )
   except :
      print "Error in PrintSpiral"
```What no assembly this time.  I was hoping to pick up a little assembly.

---

### Post by otaviocc on 2006-12-11
> **otaviocc said:**
> Wolfram's Mathematica

```
Table[i*j, {i, 1, 10}, {j, 1, 10}] // MatrixForm
```

And just to turn it uglier:

```
(Table[i, {i, 1, 10}, {j, 1, 10}] // (# Transpose[#]) & ) // MatrixForm
```

---

### Post by red_Marvin on 2006-12-11
```
'------------------------------------------------
' Language: FreeBASIC cvs
'------------------------------------------------
for row as integer = 1 to 10
    for col as integer = 1 to 10
        print space(3-len(str(row*col)));
        print row*col;
    next
    print
next
'------------------------------------------------
```
The "print space(3-len(str(row*col)));" is only there to provide nice space alignment and could be removed.
I was going to post "[1:10]'*[1:10]" for matlab too but got beaten by ocatave (oh well, it proves it works in both :))

---

### Post by llbra on 2006-12-11
A simple example in Java (optimized by StringBuffer):

public class MultiplicationTable{
    public static void main(String args[]){
        String res = new StringBuffer();
        for (int i=1; i<=10; i++){
            for (int j=1; j<=10; j++){
                res.append(i*j+"\t");
            }
            res.append("\n");
        }
        System.out.println(res.toString());
    }
}

---

### Post by samjh on 2006-12-11
Flying the Java flag:

```
public class MultiTable {

    public static void main(String[] args) {
        
        int n = 0;
        
        for (int x=1; x<11; x++) {
            for (int y=1; y<11; y++) {
                n = x * y;
                System.out.format("%03d ", n);
            }
            System.out.println();
        }
        
    }
    
}
```

Which results in the following output:
```
001 002 003 004 005 006 007 008 009 010 
002 004 006 008 010 012 014 016 018 020 
003 006 009 012 015 018 021 024 027 030 
004 008 012 016 020 024 028 032 036 040 
005 010 015 020 025 030 035 040 045 050 
006 012 018 024 030 036 042 048 054 060 
007 014 021 028 035 042 049 056 063 070 
008 016 024 032 040 048 056 064 072 080 
009 018 027 036 045 054 063 072 081 090 
010 020 030 040 050 060 070 080 090 100 
```

---

### Post by rvr777 on 2006-12-12
My perl contribution, using only one loop:

```
for(1..100){printf'%4d',$_;print"\n"if!($_%10)}
```

that is the same as

```
for (1..100) {
  printf '%4d', $_;
  if (!($_ % 10)) {
    print "\n";
  }
}
```

---

### Post by Peepsalot on 2006-12-12
> **rvr777 said:**
> My perl contribution, using only one loop:

```
for(1..100){printf'%4d',$_;print"\n"if!($_%10)}
```

that is the same as

```
for (1..100) {
  printf '%4d', $_;
  if (!($_ % 10)) {
    print "\n";
  }
}
```
i'm not a perl expert but I'm pretty sure that doesn't give the results that the contest called for.

---

### Post by samjh on 2006-12-13
> **rvr777 said:**
> My perl contribution, using only one loop:

```
for(1..100){printf'%4d',$_;print"\n"if!($_%10)}
```I tried this and the longer version of your code, but ended up with this output:

```
   1   2   3   4   5   6   7   8   9  10
  11  12  13  14  15  16  17  18  19  20
  21  22  23  24  25  26  27  28  29  30
  31  32  33  34  35  36  37  38  39  40
  41  42  43  44  45  46  47  48  49  50
  51  52  53  54  55  56  57  58  59  60
  61  62  63  64  65  66  67  68  69  70
  71  72  73  74  75  76  77  78  79  80
  81  82  83  84  85  86  87  88  89  90
  91  92  93  94  95  96  97  98  99 100
```...which is not the desired solution. ;)

---

### Post by &lt;mawe&gt; on 2006-12-13
Here is a Perl oneliner with only one loop, but it works just up to 9x9. I'm too silly to produce a 10x10 with this.
```
map{print(($_%10)?(int($_/10))*($_%10).' ':$/)}(10..100);
```

Regards, mawe

---

### Post by maddog39 on 2006-12-15
My contribution in PHP.

[PHP]
<?php
$rows = 12;
$columns = 12;

echo "<table border='0'>";
for ($i = 0; $i < $rows; $i++) {
    if ($i % $columns == 0) {
        echo "<tr>";
    }
    echo "<td>{$i}</td>";
    if (($i % $columns == $columns - 1) || ($i + 1 == $rows)) {
        echo "</tr>";
    }
}
echo "</table>";
?>
[/PHP]

---

### Post by ibuclaw on 2008-03-26
Hi, I know this topic is old, but I've been given my old grandad's computing books through his will the other week, and I thought that a great way to learn his primary language was to try it out in these challenges.

Now I've had a quick look through and haven't yet seen a **COBOL IMPLEMENTATION**!!!
:lolflag:

So here is one.
The printed output is
> 
001 002 003 004 005 006 007 008 009 010
002 004 006 008 010 012 014 016 018 020
003 006 009 012 015 018 021 024 027 030
004 008 012 016 020 024 028 032 036 040
005 010 015 020 025 030 035 040 045 050
006 012 018 024 030 036 042 048 054 060
007 014 021 028 035 042 049 056 063 070
008 016 024 032 040 048 056 064 072 080
009 018 027 036 045 054 063 072 081 090
010 020 030 040 050 060 070 080 090 100


And the code is
```

       IDENTIFICATION DIVISION.
       PROGRAM-ID. MATRIX.
       
       ENVIRONMENT DIVISION.
       
       DATA DIVISION.
       WORKING-STORAGE SECTION.
       01 X PICTURE IS 99.
       01 Y PICTURE IS 99.
       01 ANS-A PICTURE IS 999.
       01 ANS-B PICTURE IS 999.
       01 ANS-C PICTURE IS 999.
       01 ANS-D PICTURE IS 999.
       01 ANS-E PICTURE IS 999.
       01 ANS-F PICTURE IS 999.
       01 ANS-G PICTURE IS 999.
       01 ANS-H PICTURE IS 999.
       01 ANS-I PICTURE IS 999.
       01 ANS-J PICTURE IS 999.
       
       PROCEDURE DIVISION.
       PROGRAM-BEGIN.
        COMPUTE X = 1.
        COMPUTE Y = 1.
        
        PERFORM PRINT-MATRIX.

        PRINT-MATRIX.
         COMPUTE ANS-A = X * Y.
         ADD 1 TO Y.
         COMPUTE ANS-B = X * Y.
         ADD 1 TO Y.
         COMPUTE ANS-C = X * Y.
         ADD 1 TO Y.
         COMPUTE ANS-D = X * Y.
         ADD 1 TO Y.
         COMPUTE ANS-E = X * Y.
         ADD 1 TO Y.
         COMPUTE ANS-F = X * Y.
         ADD 1 TO Y.
         COMPUTE ANS-G = X * Y.
         ADD 1 TO Y.
         COMPUTE ANS-H = X * Y.
         ADD 1 TO Y.
         COMPUTE ANS-I = X * Y.
         ADD 1 TO Y.
         COMPUTE ANS-J = X * Y.
         
         DISPLAY
          ANS-A " " ANS-B " "
          ANS-C " " ANS-D " "
          ANS-E " " ANS-F " "
          ANS-G " " ANS-H " "
          ANS-I " " ANS-J.
          
         COMPUTE Y = 1.
         ADD 1 TO X.
         IF X < 10
          GO TO PRINT-MATRIX.
        
        PROGRAM-DONE.
         STOP-RUN.


```

I hope you enjoy this small contribution. And don't mock it! :)

Regards
Iain

---

### Post by LaRoza on 2008-03-26
There are new weekly challenges.

[img]http://img181.imageshack.us/img181/8060/necromancingsv7.jpg[/img]

---

