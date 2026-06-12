---
title: "Beginners Programming Challenge 15"
date: 2010-08-15
forum: Programming Talk
---

### Post by howlingmadhowie on 2010-08-15
Welcome to the Beginner Programming Challenge 15! woot! (i wonder if you spell it like that).

Well, i was trying to find something useful that you could actually use in a building block for a larger project and then i thought about comparing user input with allowed input.

as an example, let's say you're programming a navigation software and the user enters 

"navigaet to london"

instead of

"navigate to london"

and you want the program to guess what the user actually meant.  one way would be to code a list of strings that the application should accept. another way would be to find a way of defining the distance between two strings.

One such method is called the levenshtein distance. you can read more about it here: [http://en.wikipedia.org/wiki/Levenshtein_distance](http://en.wikipedia.org/wiki/Levenshtein_distance)

Basically it compares two strings and calculates the smallest number of steps you'd need to change one string into the other. allowed steps are---deletion, insertion and substitution.

The wikipedia article also has some pseudo-code to get you started :)

It would be great if your program could be run from the command line like this:
```

./mylevenshtein 'navigaet' 'navigate'
2

```
or alternatively:
```

./mylevenshtein file1.txt file2.txt
#somenumber

```

One main criteria for judging will be how easy it is to use your code in a larger project.

You can use any language you like, but i've only had experience with a few, so it may take me time to understand your code :) Because i'm only human, i'll probably end up marking you down for this :D

Here's some sample input:
```

dog
dig
distance: 1

navigaet
navigate
distance: 2

floccinaucinihilipilification
naucifloccipilinihilification
distance: 12

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nistrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis eute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
Lorem ipsum dolor sit emet, consectetur edipisicing elit, sed do eiusmod tempor incididunt ut lebore et dolore megne elique. Ut enim ed minim veniem, quis nostrud exercitetion ullemco leboris nisi ut eliquip ex ee commodo consequet. Duis eute irure dolor in reprehenderit in voluptete velit esse cillum dolore eu fugiet nulle perietur. Excepteur sint occeecet cupidetet non proident, sunt in culpe qui officie deserunt mollit enim id est leborum.
distance: 29

```

The distance between the attached files (once they've been unzipped) is 154

---

### Post by schauerlich on 2010-08-15
In Common Lisp. Takes two strings and one keyword argument, :case-insensitive. You can also run it from the command line like so:
```
schauerlich@inara:~$ sbcl --script schauerlich.lisp "navigaet" "navigate"
2
```

This improves on the pseudo-code on wikipedia because it only requires O(n) space, where n is the length of the second argument. It keeps track of the previous row and the current row, since that's all that's needed to perform the calculations.

[Pretty-looking paste.lisp.org version](http://paste.lisp.org/display/113554#2)

```
(defun levenshtein-distance* (str1 str2 &key (case-insensitive nil))
  (let* ((char-compare (if case-insensitive #'char-equal #'char=))
	 (y-length (length str1))
	 (x-length (length str2))
	 (current-row (make-array (list (1+ x-length)) :initial-element 0))
	 (prev-row (make-array (list (1+ x-length)))))
    (loop for i from 0 upto x-length do
	 (setf (aref prev-row i) i))
    (loop for y from 1 upto y-length do
	 (setf (aref current-row 0) y)
	 (loop for x from 1 upto x-length do
	      (let ((cost (if (funcall char-compare 
				       (char str1 (- y 1))
				       (char str2 (- x 1)))
			      0
			      1)))
		  (setf (aref current-row x)
			(min
			 (1+ (aref prev-row x))
			 (1+ (aref current-row (- x 1)))
			 (+ (aref prev-row (- x 1)) cost)))))
	 (rotatef prev-row current-row))
    (aref prev-row x-length)))

(defun main ()
  (format t "~d~%" 
	  (levenshtein-distance* (second *posix-argv*) (third *posix-argv*))))

(main)

```

---

### Post by Bachstelze on 2010-08-15
My first Ada program. I like this, it's quite big but the syntax is very clear.

```
with Ada.Command_Line;
with Ada.Text_IO;

procedure Distance is
	S :     String	:= Ada.Command_Line.Argument(1);
	T :     String	:= Ada.Command_Line.Argument(2);
	SL :	Natural	:= S'Length;
	TL :	Natural := T'Length;
	Table : array (Natural range 0 .. SL, 
	               Natural range 0 .. TL)
		      of Natural;

	package Integer_Text_IO is new Ada.Text_IO.Integer_IO(Integer);

	function Minimum (X :	Natural;
		          Y :	Natural;
			  Z :	Natural)
			 return Natural is
	begin
		if X <= Y then
			if X <= Z then
				return X;
			else
				return Z;
			end if;
		elsif Y <= Z then
			return Y;
		else
			return Z;
		end if;
	end Minimum;

begin

	for I in Integer range 0 .. SL loop
		for J in Integer range 0 .. TL loop
			if I = 0 then
				Table(0, J) := J;
			elsif J = 0 then
				Table(I, 0) := I;
			elsif S(I) = T(J) then
				Table(I, J) := Table(I-1, J-1);
			else
				Table(I, J) := Minimum(Table(I-1, J),
				                       Table(I, J-1),
						       Table(I-1, J-1)) + 1;
			end if;
		end loop;
	end loop;

	Ada.Text_IO.Put("Distance: ");
	Integer_Text_IO.Put(Table(SL, TL), 0);

end Distance;

```

Save as [font=monospace]distance.adb[/font], compile with [font=monospace]gnat make distance.adb[/font].

```
firas@itsuki ~ % gnat make distance.adb 
gcc-4.4 -c distance.adb
gnatbind -x distance.ali
gnatlink distance.ali
firas@itsuki ~ % ./distance dog dig
Distance: 1
firas@itsuki ~ % ./distance navigaet navigate
Distance: 2
firas@itsuki ~ % ./distance floccinaucinihilipilification naucifloccipilinihilification
Distance: 12
firas@itsuki ~ % ./distance "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nistrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis eute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum." "Lorem ipsum dolor sit emet, consectetur edipisicing elit, sed do eiusmod tempor incididunt ut lebore et dolore megne elique. Ut enim ed minim veniem, quis nostrud exercitetion ullemco leboris nisi ut eliquip ex ee commodo consequet. Duis eute irure dolor in reprehenderit in voluptete velit esse cillum dolore eu fugiet nulle perietur. Excepteur sint occeecet cupidetet non proident, sunt in culpe qui officie deserunt mollit enim id est leborum."     
Distance: 29

```

---

### Post by schauerlich on 2010-08-15
Terribly inefficient but pure-functional version in Scheme:

EDIT: borrowed some memoization code, it's now much much faster. Lorem ipsum still takes a while, but it's a vast improvement.

[http://paste.lisp.org/display/113555#1](http://paste.lisp.org/display/113555#1)

```
; memoization code borrowed from 
; http://lists.canonical.org/pipermail/kragen-hacks/1999-March/000166.html
(define (memoize func)
  (let ((memoresults '()))
    (lambda args
      (let ((memoized-pair (assoc args memoresults)))
	; for debugging:
	; (if memoized-pair (begin (print memoized-pair) (cdr memoized-pair))
	(if memoized-pair (cdr memoized-pair)
	  (let ((thing-to-save (apply func args)))
	    (begin
	      (set! memoresults (cons (cons args thing-to-save) memoresults))
	      thing-to-save)))))))



(define (string-cdr str)
  (substring str 1 (string-length str)))

(define (levenshtein-distance str1 str2)
  (let ((str1-length (string-length str1))
        (str2-length (string-length str2)))
    (cond ((= str1-length 0) 
           str2-length)
          ((= str2-length 0)
           str1-length)
          (else
           (min
            (+ (levenshtein-distance (string-cdr str1) (string-cdr str2))
               (if (char=? (string-ref str1 0) (string-ref str2 0))
                   0
                   1))
            (+ (levenshtein-distance (string-cdr str1) str2)
               1)
            (+ (levenshtein-distance str1 (string-cdr str2))
               1))))))

(set! levenshtein-distance (memoize levenshtein-distance))
```

---

### Post by Bachstelze on 2010-08-15
Haskell. Gives 30 on lorem ipsum, for some reason. :/

*EDIT:* Actually this approach is bad, no way around using some kind of state...

*EDIT2: * Corrected. Same problem as above: very inefficient.

```
import System.Environment

min3        :: Int -> Int -> Int -> Int
distance    :: String -> String -> Int

min3 a b c = if a <= b
                 then if a <= c
                          then a
                          else c
                 else if b <= c
                          then b
                          else c

distance l []       = length l
distance [] l       = length l

distance [a] [b]
        | a == b    = 0
        | otherwise = 1

distance (x:xs) [y]
        | y == x    = length xs
        | otherwise = length xs + 1
distance [y] (x:xs) = distance (x:xs) [y]

distance (x1:x2:xs) (y1:y2:ys)
        | x1 == y1  = distance (x2:xs) (y2:ys)
        | otherwise = min3 (distance (x2:xs) (y1:y2:ys))
                           (distance (x1:x2:xs) (y2:ys))
                           (distance (x2:xs) (y2:ys))
                           + 1

main = do
            args <- getArgs
            let s1 = args !! 0
            let s2 = args !! 1
            putStrLn (show (distance s1 s2))
```

---

### Post by Queue29 on 2010-08-15
In Go. It doesn't deal with files, I can't stand working with this language long enough to get io working. Go doesn't even support dynamically allocated multi dimensional arrays (!?). 

```

package main

import "fmt"
import "flag"

func main() {
	s := flag.Arg(0)
	t := flag.Arg(1)
	n := len(s)
	m := len(t)
	cost := 0
	if m>1000 || n>1000 {
		fmt.Printf("Sorry, Google can't make a language that's worth a ****.\n"+
					"Try smaller inputs?\n")
		return
	}
	
	d := new([1000][1000]int)
	for i:=0; i<=n; i++ {
		d[i][0] = i
	}
	for j:=0; j<=m; j++ {
		d[0][j] = j
	}
	
	for i:=1; i<=n; i++ {
		si := s[i-1]
		for j:=1; j<=m; j++ {
			tj := t[j-1]
			
			if si == tj {
				cost = 0
			} else {
				cost = 1
			}
			d[i][j] = min(d[i-1][j]+1, d[i][j-1]+1, d[i-1][j-1]+cost)
		}
	}
	
	fmt.Printf("%d\n", d[n][m])
	//fmt.Printf("Lev. Dist: %d\n", d[n][m])
}


func min( a,b,c int) int {
	m := a
	if b < m { m = b }
	if c < m { m = c }
	return m
}

```

---

### Post by Queue29 on 2010-08-15
In D2. Still no support for files (ahh laziness..)

```
// Lev.d

import std.stdio;

void main(string[] args)
{
	auto s = args[1];
	auto t = args[2];
	auto n = s.length;
	auto m = t.length;
	auto d = new int[][](n+1, m+1);
	auto c = 0;
	
	for(int i=0; i<=n; i++)
		d[i][0] = i;
	for(int j=0; j<=m; j++)
		d[0][j] = j;
	
	for(int i=1; i<=n; i++)
	{
		int si = s[i-1];
		for(int j=1; j<=m; j++)
		{
			int tj = t[j-1];
			if(si == tj)
				c = 0;
			else
				c = 1;
			d[i][j] = min( d[i-1][j]+1,
						   d[i][j-1]+1,
						   d[i-1][j-1]+c
						 );
		 }
	}
	writefln("%d", d[n][m]);
}

int min(int a, int b, int c)
{
	int m = a;
	if(b < m)
		m = b;
	if(c < m)
		m = c;
	return m;
}

```

---

### Post by schauerlich on 2010-08-16
Obligatory C entry. In before inevitable speed contest.

With 2 or more arguments supplied, it returns the distance between the first two arguments. Otherwise, it goes through all of the examples (including the "sitting" "kitten" one from wikipedia).

[php]#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define LEV_PRINT(str1, str2) printf("%s\n%s\ndistance: %d\n\n", str1, str2, lev_dist(str1, str2))

int min(int a, int b, int c) {
  int min = a;
  if (b < min)
    min = b;
  if (c < min)
    min = c;
  
  return min;
}

int lev_dist(char *str1, char *str2) {
  int y_length = strlen(str1);
  int x_length = strlen(str2);
  int *prev_row = (int *)malloc((x_length + 1) * sizeof(int));
  int *current_row = (int *)malloc((x_length + 1) * sizeof(int));
  int x, y, distance, cost;
  int *temp;

  for (x = 0; x <= x_length; ++x) {
    current_row[x] = 0;
    prev_row[x] = x;
  } // for x
  
  for (y = 1; y <= y_length; ++y) {
    current_row[0] = y;
    
    for (x = 1; x <= x_length; ++x) {
      cost = (str1[y - 1] == str2[x - 1]) ? 0 : 1;
     
      current_row[x] = min(prev_row[x] + 1,
			               current_row[x - 1] + 1,
			               prev_row[x - 1] + cost);
    } // for x
    
    temp = prev_row;
    prev_row = current_row;
    current_row = temp;
  } // for y

  distance = prev_row[x_length];

  free(prev_row);
  free(current_row);
  
  return distance;
} // lev_dist

int main(int argc, char **argv) {
  if (argc < 3) {
    puts("Testing examples...\n");
    LEV_PRINT("dog", "dig");
    LEV_PRINT("sitting", "kitten");
    LEV_PRINT("navigate", "navigaet");
    LEV_PRINT("floccinaucinihilipilification", "naucifloccipilinihilification");
    LEV_PRINT("Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nistrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis eute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.", "Lorem ipsum dolor sit emet, consectetur edipisicing elit, sed do eiusmod tempor incididunt ut lebore et dolore megne elique. Ut enim ed minim veniem, quis nostrud exercitetion ullemco leboris nisi ut eliquip ex ee commodo consequet. Duis eute irure dolor in reprehenderit in voluptete velit esse cillum dolore eu fugiet nulle perietur. Excepteur sint occeecet cupidetet non proident, sunt in culpe qui officie deserunt mollit enim id est leborum.");
  }
  else {
    printf("%d\n", lev_dist(argv[1], argv[2]));
  }

  return EXIT_SUCCESS;
}
[/php]

```
schauerlich@inara:~$ time ./15.out > /dev/null

real	0m0.007s
user	0m0.004s
sys	0m0.002s

```

---

### Post by Queue29 on 2010-08-16
> **schauerlich said:**
> Obligatory C entry. In before inevitable speed contest.



Well in that case..

Modified D2 entry:

[php]
// Lev.d

import std.stdio;

void main(string[] args)
{
	if(args.length == 3)
		printLevDist(args[1], args[2]);
	else
	{
		printLevDist("dog", "dig");
		printLevDist("sitting", "kitten");
		printLevDist("navigate", "navigaet");
		printLevDist("floccinaucinihilipilification", "naucifloccipilinihilification");
		printLevDist("Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nistrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis eute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.", "Lorem ipsum dolor sit emet, consectetur edipisicing elit, sed do eiusmod tempor incididunt ut lebore et dolore megne elique. Ut enim ed minim veniem, quis nostrud exercitetion ullemco leboris nisi ut eliquip ex ee commodo consequet. Duis eute irure dolor in reprehenderit in voluptete velit esse cillum dolore eu fugiet nulle perietur. Excepteur sint occeecet cupidetet non proident, sunt in culpe qui officie deserunt mollit enim id est leborum.");
	}
}

void printLevDist(string s, string t)
{
	auto n = s.length;
	auto m = t.length;
	auto d = new int[][](n+1, m+1);
	auto c = 0;
	
	for(int i=0; i<=n; i++)
		d[i][0] = i;
	for(int j=0; j<=m; j++)
		d[0][j] = j;
	
	for(int i=1; i<=n; i++)
	{
		int si = s[i-1];
		for(int j=1; j<=m; j++)
		{
			int tj = t[j-1];
			if(si == tj)
				c = 0;
			else
				c = 1;
			d[i][j] = min( d[i-1][j]+1,
						   d[i][j-1]+1,
						   d[i-1][j-1]+c
						 );
		 }
	}
	writeln(d[n][m]);
}

int min(int a, int b, int c)
{
	int m = a;
	if(b < m)
		m = b;
	if(c < m)
		m = c;
	return m;
}

[/php]

```

seth@SUbuntu:~/Code/Lev_D$ dmd -O Lev.d
seth@SUbuntu:~/Code/Lev_D$ time ./Lev > /dev/null

real	0m0.012s
user	0m0.008s
sys	0m0.000s

```

---

### Post by Bachstelze on 2010-08-17
New Haskell, using the State monad:

```
import Control.Monad.State
import System.Environment

min3    :: Int -> Int -> Int -> Int
min3 a b c = if a < b
                then if a < c
                        then a
                        else c
                else if b < c
                        then b
                        else c

type LevenshteinState = State [Int]

distance :: String -> String -> Int -> LevenshteinState Int
distance s1 s2 n = do t <- get
                      let ls1 = length s1
                      let i = mod n (ls1 + 1)
                      let j = div n (ls1 + 1)
                      let d = if n <= ls1
                                 then n
                              else if i == 0
                                 then j
                              else if (s1 !! (i-1)) == (s2 !! (j-1))
                                 then (t !! (ls1+1))
                              else
                                 min3 (head t) (t !! ls1) (t !! (ls1+1)) + 1
                      let nt = d : (take (ls1 + 1) t)
                      put nt
                      return d

levDistance :: String -> String -> Int -> LevenshteinState [Int]
levDistance s1 s2 n = if n >= (ls1 + 1)*(ls2 + 1)
                         then return []
                         else liftM2 (:) (distance s1 s2 n) (levDistance s1 s2 (n + 1))
                      where ls1 = length s1
                            ls2 = length s2

levDistanceReal :: String -> String -> Int
levDistanceReal s1 s2 = last (evalState (levDistance s1 s2 0) [])

printLevDistance :: String -> String -> IO ()
printLevDistance s1 s2 = do putStrLn s1
                            putStrLn s2
                            putStrLn ("Distance: " ++ show (levDistanceReal s1 s2))

main = do args <- getArgs
          if length args == 0
             then do putStrLn "Trying the example strings: "
                     putStrLn ""
                     printLevDistance "dig" "dog"
                     putStrLn ""
                     printLevDistance "navigaet" "navigate"
                     putStrLn ""
                     printLevDistance "floccinaucinihilipilification"
                                      "naucifloccipilinihilification"
                     putStrLn ""
                     printLevDistance ("Lorem ipsum dolor sit amet, consectetur adipisicing elit, " ++
                                       "sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. " ++
                                       "Ut enim ad minim veniam, quis nistrud exercitation ullamco laboris " ++
                                       "nisi ut aliquip ex ea commodo consequat. " ++
                                       "Duis eute irure dolor in reprehenderit in voluptate velit esse " ++
                                       "cillum dolore eu fugiat nulla pariatur. " ++
                                       "Excepteur sint occaecat cupidatat non proident, " ++
                                       "sunt in culpa qui officia deserunt mollit anim id est laborum.")
                                      ("Lorem ipsum dolor sit emet, consectetur edipisicing elit, " ++
                                       "sed do eiusmod tempor incididunt ut lebore et dolore megne elique. " ++
                                       "Ut enim ed minim veniem, quis nostrud exercitetion ullemco leboris " ++
                                       "nisi ut eliquip ex ee commodo consequet. " ++
                                       "Duis eute irure dolor in reprehenderit in voluptete velit esse " ++
                                       "cillum dolore eu fugiet nulle perietur. " ++
                                       "Excepteur sint occeecet cupidetet non proident, " ++
                                       "sunt in culpe qui officie deserunt mollit enim id est leborum.")
             else if length args == 2
                then printLevDistance (args !! 0) (args !! 1)
             else putStrLn "This program takes either 0 or 2 arguments."


```

Works, but exhausts my RAM on lorem ipsum. :/

---

### Post by howlingmadhowie on 2010-08-19
Cool :) lots of entries :)

but none of them from a true beginner :(  maybe the problem is too difficult :(

i'll have a look at them later on today :)

---

### Post by Bachstelze on 2010-08-19
> **howlingmadhowie said:**
> 
but none of them from a true beginner :(  maybe the problem is too difficult :(

I don't think so, the pseudocode on the Wikipedia page can be pretty much copy-and-pasted to Python.  Maybe they got scared by all our crazy languages. :p

I'm still baffled as to why my monadic Haskell version eats so much RAM...

---

### Post by schauerlich on 2010-08-19
> **howlingmadhowie said:**
> but none of them from a true beginner :(  maybe the problem is too difficult :(

It's about the same difficulty as the last few. I wouldn't worry about it.

---

### Post by howlingmadhowie on 2010-08-19
> **Bachstelze said:**
> I don't think so, the pseudocode on the Wikipedia page can be pretty much copy-and-pasted to Python.  Maybe they got scared by all our crazy languages. :p

I'm still baffled as to why my monadic Haskell version eats so much RAM...

I'm afraid i've never looked at haskell, but as a fan of stateless programming i should really do so at some stage.  People who use it often say it's the bee's knees.

---

### Post by sharpdust on 2010-08-19
Just to throw another entry in, here is a recursive solution in ruby. Beware, this is extremely, extremely slow. No optimization here :)

```
#!/usr/bin/env ruby

def lev(a, b)
  # Base cases
  return b.length if a.empty?
  return a.length if b.empty?
  # Check if the first characters of each string are equal,
  # then recursively call the lev function with:
  # - everything but the first character of both strings
  # - everything but the first character of a, add one
  # - everything but the first character of b, add one.
  # Find the min of the previous 3 things...very, very naive approach.
  return [
           (a[0] == b[0] ? 0 : 1) + lev(a[1..-1], b[1..-1]),
           1 + lev(a[1..-1], b),
           1 + lev(a, b[1..-1])
         ].min
end

puts lev(ARGV[0], ARGV[1])
```

By the way this and the last beginner programming challenge are certainly not "beginner" challenges.
Speaking on this one specifically, someone who is considered a beginner programmer more than likely has very little experience with algorithms. Even if the algorithm is given, all one is probably doing is trying to convert it into their preferred language rather than understanding it.
That being said, I do believe it's very difficult to come up with unique challenges and I appreciate the challenger's (and previous challengers') originality. However, to get more entries, it might be best to going back to "read data, parse data, output data" style.

---

### Post by Queue29 on 2010-08-19
> **sharpdust said:**
> 

By the way this and the last beginner programming challenge are certainly not "beginner" challenges.
Speaking on this one specifically, someone who is considered a beginner programmer more than likely has very little experience with algorithms. Even if the algorithm is given, all one is probably doing is trying to convert it into their preferred language rather than understanding it.
That being said, I do believe it's very difficult to come up with unique challenges and I appreciate the challenger's (and previous challengers') originality. However, to get more entries, it might be best to going back to "read data, parse data, output data" style.

I guess it depends on what we're considering beginner. In my mind, I've seen these challenges aimed at people who have the equivalent of a semester of CS under their belt (which really isn't much). Other wise, if we're talking about complete noob, never looked at code before beginners, then it doesn't really matter how difficult the challenges are, because the only thing they can do is copy and paste from tutorials. 

There was a challenge a few weeks back that involved re-implementing the 'ls' command which I agree was over the top, but these challenges which just involve reading through a description of an easy-to-learn algorithm and implementing it step by step is perfect for the target audience, I think. 

That being said, it is odd there are no python, java, c++, etc entries from real beginners :(

---

### Post by KdotJ on 2010-08-19
> **Queue29 said:**
> 
That being said, it is odd there are no python, java, c++, etc entries from real beginners :(

I must say, I'm surprised at all of the languages that have been submitted so far... I've never had a look at many of these before.

---

### Post by schauerlich on 2010-08-20
> **KdotJ said:**
> I must say, I'm surprised at all of the languages that have been submitted so far... I've never had a look at many of these before.

After hearing months of the lispers around here talk about learning it as a near religious experience, I figured I'd give it a shot. I'm most of the way through both [Practical Common Lisp](http://www.gigamonkeys.com/book/) and [Structure and Interpretation of Computer Programs](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-4.html#%_toc_start), and I wouldn't say I've had that mystical transition into programming nirvana, but CL and Scheme are certainly both very interesting languages which make you think a lot. Scheme, especially, boils things down to the bare essentials so you get a real nice basic but abstract view of what programming is. I've also always just been curious about functional programming, since state is so inherent in the languages I was familiar with (C, C++, Python (although it has some nice functional programming features))

---

### Post by KdotJ on 2010-08-20
> **schauerlich said:**
> I've also always just been curious about functional programming, since state is so inherent in the languages I was familiar with (C, C++, Python (although it has some nice functional programming features))

Same for me I must admit, I have only really used and played with OO languages such as VB, C# and now Java is my actual production language. However, I'm planning to slowly get into C on the side... Not so intensely that confuse myself with everything, but just in spare time.

---

### Post by schauerlich on 2010-08-21
> **KdotJ said:**
> Same for me I must admit, I have only really used and played with OO languages such as VB, C# and now Java is my actual production language. However, I'm planning to slowly get into C on the side... Not so intensely that confuse myself with everything, but just in spare time.

C is not functional... [http://en.wikipedia.org/wiki/Functional_programming](http://en.wikipedia.org/wiki/Functional_programming)

---

### Post by KdotJ on 2010-08-21
> **schauerlich said:**
> C is not functional... [http://en.wikipedia.org/wiki/Functional_programming](http://en.wikipedia.org/wiki/Functional_programming)

My apologies, my post was reay trying to say I wanted to try a different paradigm. But since I have been looking up a bit of Lisp, I think I'm going to have a little play with that. As you say, many people swear by it

---

### Post by schauerlich on 2010-08-21
> **KdotJ said:**
> My apologies, my post was reay trying to say I wanted to try a different paradigm. But since I have been looking up a bit of Lisp, I think I'm going to have a little play with that. As you say, many people swear by it

Ah, no worries. There's just a lot of people around here who see that C has functions and declare it a functional language. Heh. :)

---

### Post by worseisworser on 2010-08-21
> **schauerlich said:**
> After hearing months of the lispers around here talk about learning it as a near religious experience, I figured I'd give it a shot. I'm most of the way through both [Practical Common Lisp](http://www.gigamonkeys.com/book/) and [Structure and Interpretation of Computer Programs](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-4.html#%_toc_start), and I wouldn't say I've had that mystical transition into programming nirvana, but CL and Scheme are certainly both very interesting languages which make you think a lot. Scheme, especially, boils things down to the bare essentials so you get a real nice basic but abstract view of what programming is. I've also always just been curious about functional programming, since state is so inherent in the languages I was familiar with (C, C++, Python (although it has some nice functional programming features))

Try something a bit more advanced or focussed on macros like On Lisp or something with focus on meta-programming like AMOP. :))

edit: In any case Lisp, macros and meta-programming doesn't really shine in small contexts like these; there is little opportunity to abstract much or do meta-programming.

---

### Post by nhandler on 2010-08-21
Here is a Perl solution to the problem. The algorithm is nearly identical to the one on Wikipedia.

```

#!/usr/bin/perl
use strict;
use warnings;

my($string1,$string2);
if($#ARGV==1) {
	if(-e "$ARGV[0]") {
		open(FILE1, "<$ARGV[0]") or die "Can't Read $ARGV[0]: $!\n";
		$string1=<FILE1>;
		chomp $string1;
		close(FILE1);
	}
	else {
		$string1="$ARGV[0]";
	}
	if(-e "$ARGV[1]") {
		open(FILE2, "<$ARGV[1]") or die "Can't Read $ARGV[1]: $!\n";
		$string2=<FILE2>;
		chomp $string2;
		close(FILE2);
	}
	else {
		$string2="$ARGV[1]";
	}
	print "distance: " . &LevenshteinDistance($string1,$string2) . "\n\n";
}
else {
	print "distance: " . &LevenshteinDistance("navigaet","navigate") . "\n\n";
	print "distance: " . &LevenshteinDistance("dog","dig") . "\n\n";
	print "distance: " . &LevenshteinDistance("floccinaucinihilipilification","naucifloccipilinihilification") . "\n\n";
	print "distance: " . &LevenshteinDistance("Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nistrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis eute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.","Lorem ipsum dolor sit emet, consectetur edipisicing elit, sed do eiusmod tempor incididunt ut lebore et dolore megne elique. Ut enim ed minim veniem, quis nostrud exercitetion ullemco leboris nisi ut eliquip ex ee commodo consequet. Duis eute irure dolor in reprehenderit in voluptete velit esse cillum dolore eu fugiet nulle perietur. Excepteur sint occeecet cupidetet non proident, sunt in culpe qui officie deserunt mollit enim id est leborum.") . "\n\n";
}

sub LevenshteinDistance {
	my($s, $t)=@_;
	print "$s\n$t\n";
	my $m = length($s);
	my $n = length($t);
	my @d;
	for(my $i=0;$i<=$m;$i++) {
		$d[$i][0]=$i;
	}
	for(my $j=0;$j<=$n;$j++) {
		$d[0][$j]=$j;
	}
	for(my $j=1;$j<=$n;$j++) {
		for(my $i=1;$i<=$m;$i++) {
			if(substr($s,$i-1,1) eq substr($t,$j-1,1)) {
				$d[$i][$j]=$d[$i-1][$j-1];
			}
			else {
				$d[$i][$j]=(sort { $a <=> $b } ($d[$i-1][$j]+1,$d[$i][$j-1]+1,$d[$i-1][$j-1]+1))[0];
			}
		}
	}
	return $d[$m][$n];
}

```

If the script is not run with exactly 2 arguments passed to it, it shows the distance between a few example strings taken from this thread.

> 
$ ./mylevenshtein
navigaet
navigate
distance: 2

dog
dig
distance: 1

floccinaucinihilipilification
naucifloccipilinihilification
distance: 12

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nistrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis eute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
Lorem ipsum dolor sit emet, consectetur edipisicing elit, sed do eiusmod tempor incididunt ut lebore et dolore megne elique. Ut enim ed minim veniem, quis nostrud exercitetion ullemco leboris nisi ut eliquip ex ee commodo consequet. Duis eute irure dolor in reprehenderit in voluptete velit esse cillum dolore eu fugiet nulle perietur. Excepteur sint occeecet cupidetet non proident, sunt in culpe qui officie deserunt mollit enim id est leborum.
distance: 29


You can also pass the script 2 strings as arguments, and it will display the distance between them.

> 
$ ./mylevenshtein 'Sunday' 'Saturday'
Sunday
Saturday
distance: 3


Finally, the script checks if either of the two arguments (or both of the arguments) passed to it are files. If either is a file, the contents of the file will be used as a string.

> 
$ echo "sitting" > a
$ echo "kitten" > b
$ ls
a  b  mylevenshtein
$ ./mylevenshtein 'a' 'b'
sitting
kitten
distance: 3
$ ./mylevenshtein 'a' 'missing'
sitting
missing
distance: 3


As I mentioned earlier, the algorithm is nearly identical to the one on Wikipedia and not optimized. Therefore, it is much slower than most of the other solutions in this thread. It is also not very efficient. Trying to run this script on file1.txt.gz and file2.txt.gz (from this thread) led to Out of Memory errors.

Edit: As a learning experience, I decided to go ahead and create a GUI for this program using Glade and Gtk2. This GUI version uses the same code to calculate the levenshtein distance as the script above; it simply adds a GUI.

mylevenshtein.glade:
```

<?xml version="1.0"?>
<glade-interface>
  <!-- interface-requires gtk+ 2.6 -->
  <!-- interface-naming-policy toplevel-contextual -->
  <widget class="GtkWindow" id="main">
    <property name="visible">True</property>
    <property name="title" translatable="yes">My Levenshtein</property>
    <property name="window_position">center</property>
    <signal name="delete_event" handler="on_main_delete_event"/>
    <signal name="delete_event" handler="on_main_delete_event"/>
    <child>
      <widget class="GtkVBox" id="main_vbox">
        <property name="visible">True</property>
        <child>
          <widget class="GtkLabel" id="mylevenshtein_label">
            <property name="visible">True</property>
            <property name="label" translatable="yes">My Levenshtein</property>
            <property name="single_line_mode">True</property>
          </widget>
          <packing>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHSeparator" id="hseparator">
            <property name="visible">True</property>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="fill">False</property>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkTable" id="table1">
            <property name="visible">True</property>
            <property name="n_rows">3</property>
            <property name="n_columns">3</property>
            <child>
              <widget class="GtkLabel" id="string1_label">
                <property name="visible">True</property>
                <property name="label" translatable="yes">String 1</property>
                <property name="single_line_mode">True</property>
              </widget>
            </child>
            <child>
              <widget class="GtkLabel" id="string2_label">
                <property name="visible">True</property>
                <property name="label" translatable="yes">String 2</property>
                <property name="single_line_mode">True</property>
              </widget>
              <packing>
                <property name="top_attach">1</property>
                <property name="bottom_attach">2</property>
              </packing>
            </child>
            <child>
              <widget class="GtkEntry" id="string1_entry">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x2022;</property>
                <property name="activates_default">True</property>
              </widget>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
              </packing>
            </child>
            <child>
              <widget class="GtkEntry" id="string2_entry">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x2022;</property>
                <property name="activates_default">True</property>
              </widget>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">1</property>
                <property name="bottom_attach">2</property>
              </packing>
            </child>
            <child>
              <widget class="GtkLabel" id="distance_label">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Distance</property>
                <property name="single_line_mode">True</property>
              </widget>
              <packing>
                <property name="top_attach">2</property>
                <property name="bottom_attach">3</property>
              </packing>
            </child>
            <child>
              <widget class="GtkEntry" id="distance_entry">
                <property name="visible">True</property>
                <property name="editing_canceled">True</property>
                <property name="editable">False</property>
                <property name="invisible_char">&#x2022;</property>
              </widget>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">2</property>
                <property name="bottom_attach">3</property>
              </packing>
            </child>
            <child>
              <placeholder/>
            </child>
            <child>
              <widget class="GtkFileChooserButton" id="string1_filechooser">
                <property name="visible">True</property>
                <property name="create_folders">False</property>
                <signal name="file_set" handler="on_string1_filechooser_file_set"/>
              </widget>
              <packing>
                <property name="left_attach">2</property>
                <property name="right_attach">3</property>
              </packing>
            </child>
            <child>
              <widget class="GtkFileChooserButton" id="string2_filechooser">
                <property name="visible">True</property>
                <property name="create_folders">False</property>
                <signal name="file_set" handler="on_string2_filechooser_file_set"/>
              </widget>
              <packing>
                <property name="left_attach">2</property>
                <property name="right_attach">3</property>
                <property name="top_attach">1</property>
                <property name="bottom_attach">2</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHButtonBox" id="main_hbuttonbox">
            <property name="visible">True</property>
            <child>
              <widget class="GtkButton" id="quit_button">
                <property name="label">gtk-quit</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="receives_default">True</property>
                <property name="use_stock">True</property>
                <signal name="clicked" handler="on_quit_button_clicked"/>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <widget class="GtkButton" id="clear_button">
                <property name="label">gtk-clear</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="use_stock">True</property>
                <signal name="clicked" handler="on_clear_button_clicked"/>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <widget class="GtkButton" id="distance_button">
                <property name="label">Calculate Distance</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="has_default">True</property>
                <property name="receives_default">True</property>
                <signal name="clicked" handler="on_distance_button_clicked"/>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="position">2</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="position">3</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```

mylevenshtein.pl:
```

#!/usr/bin/perl
use strict;
use warnings;

use Gtk2 '-init';
use Gtk2::GladeXML;

my $window;
my $fortune;

my $glade = Gtk2::GladeXML->new('mylevenshtein.glade');

$glade->signal_autoconnect_from_package('main');

$window = $glade->get_widget('main');
my $mylevenshteinLabel = $glade->get_widget('mylevenshtein_label') or die;
$mylevenshteinLabel->modify_font( Gtk2::Pango::FontDescription->from_string("Ubuntu-Title 40") );
my $string1Entry = $glade->get_widget('string1_entry') or die;
my $string2Entry = $glade->get_widget('string2_entry') or die;
my $distanceEntry = $glade->get_widget('distance_entry') or die;
my $string1Filechooser = $glade->get_widget('string1_filechooser') or die;
my $string2Filechooser = $glade->get_widget('string2_filechooser') or die;
Gtk2->main;

exit 0;

sub on_clear_button_clicked {
	$string1Entry->set_text("");
	$string2Entry->set_text("");
	$distanceEntry->set_text("");
	$string1Filechooser->unselect_all();
	$string2Filechooser->unselect_all();
}

sub on_distance_button_clicked {
	my $string1=$string1Entry->get_text();
	my $string2=$string2Entry->get_text();
	my $distance = LevenshteinDistance("$string1","$string2");
	print "distance: $distance\n";
	$distanceEntry->set_text("$distance");
}

sub on_string1_filechooser_file_set {
	my $file=$string1Filechooser->get_filename();
	open(FILE, "<$file") or die;
	my $text = <FILE>;
	chomp $text;
	close(FILE);
	$string1Entry->set_text("$text");
	print "File: $file\n";
}

sub on_string2_filechooser_file_set {
	my $file=$string2Filechooser->get_filename();
        open(FILE, "<$file") or die;
        my $text = <FILE>;
        chomp $text;
        close(FILE);
	$string2Entry->set_text("$text");
	print "File: $file\n";
}

sub on_main_delete_event {Gtk2->main_quit;}

sub on_quit_button_clicked {on_main_delete_event;}    

sub LevenshteinDistance {
	my($s, $t)=@_;
	print "$s\n$t\n";
	my $m = length($s);
	my $n = length($t);
	my @d;
	for(my $i=0;$i<=$m;$i++) {
		$d[$i][0]=$i;
	}
	for(my $j=0;$j<=$n;$j++) {
		$d[0][$j]=$j;
	}
	for(my $j=1;$j<=$n;$j++) {
		for(my $i=1;$i<=$m;$i++) {
			if(substr($s,$i-1,1) eq substr($t,$j-1,1)) {
				$d[$i][$j]=$d[$i-1][$j-1];
			}
			else {
				$d[$i][$j]=(sort { $a <=> $b } ($d[$i-1][$j]+1,$d[$i][$j-1]+1,$d[$i-1][$j-1]+1))[0];
			}
		}
	}
	return $d[$m][$n];
}

```

To run the GUI version, make sure the .glade and .pl files are located in the same directory and have the correct filenames. Then, simply run 'perl ./mylevenshtein.pl' to execute the script. In this version, you can either enter the 2 strings in the provided text boxes, or use the filechooser buttons to select files that contain the strings. Selecting a file will cause the string it contains to appear in the text box. Clicking the 'Calculate Distance' button will update the 'Distance' text box. The script uses the Ubuntu-title font (sudo apt-get install ttf-ubuntu-title).

---

### Post by pedro3005 on 2010-08-22
Ok, I am a beginner to programming in general (I've been learning for 2 or 3 months now). I picked up C about a month ago. I tried to come up with my own way of doing this. It may not be the most elegant solution but I had fun doing and seeing it work :) It accepts the syntax:
./lev file1 file2
They MUST be files!
[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define STRBUFSIZE 30

char *readstr(FILE *src, char stop) {
    char c, *dest = malloc(STRBUFSIZE * sizeof(char));
    int i = 0, destsize = STRBUFSIZE;
    while (c = fgetc(src), c != EOF && c != stop) {
        if (i == destsize - 2) {
            dest = realloc(dest, (destsize + STRBUFSIZE) * sizeof(char));
            destsize += STRBUFSIZE;
        }
        dest[i] = c;
        i++;
    }
    dest[destsize-1] = '\0';
    return dest;
}

int levdistance(char *s, char *t) {

    char *smallstr = !((strlen(s) + 1) > (strlen(t) + 1)) ? s : t;
    char *bigstr = !strcmp(smallstr, s) ? t : s;
    int b_len = strlen(bigstr) + 1;
    
    char *deststr = calloc(b_len, sizeof(char)); // maybe a bit of a memory hog
    strcpy(deststr, smallstr);
    
    int j, distance = 0;
    for (j = 0; j < b_len; j++) {
        
        if (deststr[j] == bigstr[j])
            continue;
        else {
            deststr[j] = bigstr[j];
            distance++;
        }
    }
    return distance;
}

int main(int argc, char **argv) {
    
    if (argc != 3) {
        fprintf(stderr, "Error: bad syntax. Use: ./lev <file1> <file2>");
        exit(1);
    }
    
    FILE *f_one = fopen(argv[1], "r");
    FILE *f_two = fopen(argv[2], "r");
    
    char *li_one = readstr(f_one, EOF);
    char *li_two = readstr(f_two, EOF);

    printf("The distance is: %d\n", levdistance(li_one, li_two));
    return 0;
}
[/PHP]EDIT: I have realized this algorithm does NOT work. It seemingly does a good job with the examples but fails miserably with the two provided files (returns 69158 ). I am in the process of investigating this... I may have to cave in and accept I cannot build a better algorithm! :p

---

### Post by schauerlich on 2010-08-22
> **pedro3005 said:**
> EDIT: I have realized this algorithm does NOT work. It seemingly does a good job with the examples but fails miserably with the two provided files (returns 69158 ). I am in the process of investigating this... I may have to cave in and accept I cannot build a better algorithm! :p

Your algorithm only works on simple substitutions - not insertions or deletions. For example, it would correctly give 1 for "dog" and "dig," but it would give 5 for "kitten" and "kiitten" when it should be 1. Also, it will go off the end of the shorter string.

---

### Post by pedro3005 on 2010-08-22
Yes, I figured that much. Now, I'm seeing the Wiki algorithm seems to try all the possibilities (substitution, insertion and deletion) and then sees which one is most efficient. Is that correct?
> Also, it will go off the end of the shorter string.
I don't think it will, since I copied the short string to a new one whose length is equal to the big string. [COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]char [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000BB]deststr [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]calloc[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]b_len[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]sizeof[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]char[/COLOR][COLOR=#007700]));[/COLOR][/COLOR]

---

### Post by Odexios on 2010-08-29
Ok, it could be *really* better, I know. But I wrote a few things I wanted to try, so it's not the most elegant or efficient code you'll find.

Besides, I knew nothing of C (only a little bit of Ruby) until a few months ago.

The program accepts two string (./distance string1 string2) or two files (./distance -f file1 file2) and can return the distance without outputting anything (-q); here it is.


distance.c

[php]#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void fcopy(FILE *fp, char **buff);//copies an *fp file to a *buff string
int lev_length(char *strFirst, char *strSecond);//prepares everything to start lev_calc
int min(int a, int b, int c);//calculates the minimum of three numbers
int lev_calc(int **matr, int i, int j,
           char *strFirst, int indFirst,
           char *strSecond, int indSecond); //calculates the lev distance

int main(int argc, char **argv) {
    char *strFirst = NULL, *strSecond = NULL; //the string to confront
    FILE *fp1, *fp2; //for file arguments handling
    int quiet = 0; //quiet output (boolean)
    int file = 0; //file input (boolean)
    int distance;
    
    if (argc > 4) {
        printf("Error 01: too many command line arguments\n");
        return -1;
    }
    
    while (--argc > 0) {
        if (strcmp(argv[argc], "-q") == 0)
            quiet = 1;
        else if (strcmp(argv[argc], "-f") == 0)
            file = 1;
        else
            if (strFirst == NULL)
                strFirst = argv[argc];
            else if (strSecond == NULL)
                strSecond = argv[argc];
        
    }
    
    if (strSecond == NULL || strFirst == NULL) {
        printf("Error 02: comparison arguments missing\n");
        return -2;
    }
    
    if (file){
        
        fp1 = fopen(strFirst, "r");
        fp2 = fopen(strSecond, "r");
        
        fcopy(fp1, &strFirst);
        fcopy(fp2, &strSecond);
        
    }
        
    distance = lev_length(strFirst, strSecond);

    if (distance == -1) {
        printf("Error 03: out of memory. Try with smaller input\n");
        return -3;
    } 
   
    if (!quiet)
        printf("%d\n", distance);
    
    return distance;
    
}

void fcopy(FILE *fp, char **buff) {
    
    char r;
    int n, limit, i;
    char *b, *bres;
    
    b = malloc(sizeof(char) * limit);
    
    for (n = 0, limit = 1024; (r = getc(fp)) != EOF; n++) {
        
        if (limit - n < 2) {
            bres = malloc(sizeof(char) * (n+1+limit));
            for (i = 0; i < n; i++)
                bres[i] = b[i];
            free(b);
            b = bres;
        }
        
        b[n] = r;
    }
    b[n+1] = '\0';
    *buff = b;
    
}
        
    
int lev_length(char *strFirst, char *strSecond) {
    
    int lengthFirst, lengthSecond;
    int i, j;
    int **matr;
    
    
    while(strFirst[0] == strSecond[0] && strFirst[0] != '\0' && strSecond[0] != '\0') {
        
        /* when the first character of both strings is the same delete it*/
        strFirst++;
        strSecond++;
        
    }
    
    if (strSecond[0] == strFirst[0])
        return 0;
    
    for (lengthFirst=0; strFirst[lengthFirst] != '\0'; lengthFirst++)
        /*gets length of first string*/;
    
    for (lengthSecond=0; strSecond[lengthSecond] != '\0'; lengthSecond++)
        /*gets length of second string*/;
    
    matr = malloc( sizeof(*matr) * (lengthFirst +1) );
    if (matr == NULL)
        return -1;
    for(i=0; i<=lengthFirst; i++) {
        matr[i] = malloc( sizeof(**matr) * (lengthSecond + 1) );
        if (matr[i] == NULL)
            return -1;
    }
    /*make a matrix of (lengthSecond+1) * (lengthFirst+1)*/
    
    for(i=0; i<=lengthFirst; i++)
        matr[i][0] = i;
        /*the first column gets to 0*/
    
    for(i=0; i<=lengthSecond; i++)
        matr[0][i] = i;
        /*the first row gets to 0*/
    
    for (i = 1; i<=lengthFirst; i++) {
        for (j=1; j<=lengthSecond; j++)
            matr[i][j] = -1;
    }
    
    
    return lev_calc(matr, lengthFirst, lengthSecond, strFirst, lengthFirst-1, strSecond, lengthSecond-1);    
}

int min(int a, int b, int c) {
    
    if (a<b) {
        if (a<c)
            return a;
        else
            return c;
    }
    else
        if (b<c)
            return b;
        else
            return c;
}

int lev_calc(int **matr, int i, int j,
           char *strFirst, int indFirst,
           char *strSecond, int indSecond) {
    
    int indi, indj;

               
    if (matr[i][j] >=0)
        return matr[i][j];
    /*if you have already calculated the value of the cell, return it*/
    
    if (strFirst[indFirst] == strSecond[indSecond]) 
        return matr[i][j] = lev_calc(matr, i-1, j-1, strFirst, indFirst-1, strSecond, indSecond-1);
        /*if the characters are the same, return the value of the string with one character less*/
    else 
        return matr[i][j] = (1 + min(lev_calc(matr, i-1, j-1, strFirst, indFirst-1, strSecond, indSecond-1),
                       lev_calc(matr, i-1, j, strFirst, indFirst-1, strSecond, indSecond),
                       lev_calc(matr, i, j-1, strFirst, indFirst, strSecond, indSecond-1)));
        /*otherwise, return the most efficient solution, recursively from the last spot*/
}
    [/php]Everything works fine as long as the input isn't too large; when it gets too large, it quickly exhausts memory.

I'm all open to suggestion; don't care if I get out of the contest XD

EDIT: I saw that time thing... what is it?

```
odexios@odexios-laptop:~$ time ./distance > /dev/null

real    0m0.004s
user    0m0.000s
sys    0m0.004s

```

---

### Post by Bachstelze on 2010-08-29
> **pedro3005 said:**
> 
I don't think it will, since I copied the short string to a new one whose length is equal to the big string. char *deststr = calloc(b_len, sizeof(char));

It will. The length of a string is the number of characters before the first null byte. The size of the buffer is irrelevant:

```
firas@aoba ~ % cat test.c 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(void)
{
    char s1[] = "hello";
    char *s2 = calloc(100000, sizeof(char));

    /* Copy s1 into s2. */
    strncpy(s2, s1, strlen(s1)+1);

    /* Length of s2 is? */
    printf("%ld\n", strlen(s2));

    return 0;
}

firas@aoba ~ % cc -ansi -Wall -pedantic -o test test.c
firas@aoba ~ % ./test
5

```

Also in general using calloc() is superfluous.  The program above, just like yours, will work just as well with malloc(), and it will save the hassle of initialising all the memory.

And, for the love of all things cute and cuddly, **never** use strcpy(), that's asking for buffer overflows. Always use strncpy(). And don't say "I'm certain that it won't overflow", the evil god Murphy will punish you for your arrogance.

---

### Post by David Andersson on 2010-09-05
Programing language: **gema**

Gema is a "general purpose macro processor". This solution repeatedly submits a shunk of *text* to sets of pattern matching *rules* that modifies the text. Finally the text is a single number, the distance.

```

#!/usr/local/bin/gema -prim 

@set-syntax{L; }
ARGV:\n*\n*\n=@out{@main{@mangel{*} 0 @mangel{*}\n}}

mangel: =_

main:\A <D> \n\Z= $1 \n
main:\A<U>\n\Z=@main{@reduce{@reduce{@fwd{$0}}}}

reduce:\L\N<g> <D> <g>\n$1 <D> $3\n=$1 @cmpn{$2;$4;$2;$2;$4} $3\n

fwd:\L\N<g> ~<D> <g>\n=$1 $2 $3\n
fwd:\L\N<G1><g> <D> $1<g>\n=$2 ~$3 $4\n
fwd:\L\N<G1><g> <D> <G1><g>\n=$1$2 @add{$3;1} $5\n$2 ~@add{$3;1} $5\n$2 @add{$3;1} $4$5\n
fwd:\L\N <D> <G>\n=
fwd:\L\N<G> <D> \n=

```

Difficult to follow? The same with comments:

```

#!/usr/local/bin/gema -prim 
! david 2010-09-05
!
! Compute Levenshtein distance between two strings.
! Assuming the program is executable, you can invoke it with
!   levenshtein.gema "STRING1" "STRING2"
!
! Data structure
! --------------
! The program use an internal data set, where each line is of the form
!   REMAINDER_1 CURRENT_COST REMAINDER_2
! or
!   REMAINDER_1 ~CURRENT_COST REMAINDER_2
! where REMAINDER_x is one of the input strings (1 or 2) with 0 or more chars
! removed from the beginning. CURRENT_COST is the Levenshtein distance between
! the parts of the strings that has been removed so far. A "~" is added for
! temporary data lines that are not to be processed by the fwd rules.

! Init
! ----
! Do not handle space in patterns specially.
! (The work data set may have space at beginning of line)

@set-syntax{L; }

! Parse command line argument, start the process, and output the result.
! Initial data set is one line containing both input strings and CURRENT_COST=0.

ARGV:\n*\n*\n=@out{@main{@mangel{*} 0 @mangel{*}\n}}

! Change space to "_" in input, so the more efficient <G> pattern can
! be used in the rules to match an input string.

mangel: =_

! Main loop
! ---------
! Repeatedly @fwd and @reduce the data set, until only one line with empty
! strings remains, containing the final cost. Return that line.
! In each iteration, the number of lines in the data set may grow or shrink,
! but the (logical) length of every line is shortened by exactly 1.
! See "Invariant" below.

main:\A <D> \n\Z= $1 \n
main:\A<U>\n\Z=@main{@reduce{@reduce{@fwd{$0}}}}

! Reduce step
! -----------
! Find copies and keep the ones with the smallest CURRENT_COST.
! Find two consecutive lines with the same REMAINDER strings, and
! replace it with the line with the smallest CURRENT_COST.
! See "Copies" below.

reduce:\L\N<g> <D> <g>\n$1 <D> $3\n=$1 @cmpn{$2;$4;$2;$2;$4} $3\n

! Forward step
! ------------
! This is where chars are compared and CURRENT_COST is updated.
! The rules compares the first char of REMAINDER_1 and _2 in each line.
! All lines are replaced with similar lines, all (logically) on char shorter.
! Some lines are replaced with 3 lines, some with 1 line, and some removed.
!
! * If "~" line: remove the "~", keep it otherwise unchanged. No added cost.
!
! * If first chars are equal: remove those chars. No added cost.
!   Also add "~" so logical length is reduce by 1 and not by 2.
!
! * If first chars are different: replace the line with 3 new lines,
!   one where REMAINDER_1 is shortened, one where both strings are shortened, 
!   and one where REMAINDER_1 is shortened. Add 1 to the cost in all three.
!   Let the line where both strings where shortened have a "~" so the
!   logical length only was shortened by one.
!
! * If one of the strings is empty and the other is not: the line is
!   not part of an optimal path and is removed.

fwd:\L\N<g> ~<D> <g>\n=$1 $2 $3\n
fwd:\L\N<G1><g> <D> $1<g>\n=$2 ~$3 $4\n
fwd:\L\N<G1><g> <D> <G1><g>\n=$1$2 @add{$3;1} $5\n$2 ~@add{$3;1} $5\n$2 @add{$3;1} $4$5\n
fwd:\L\N <D> <G>\n=
fwd:\L\N<G> <D> \n=

! Invariant
! ---------
! All lines in the data set have the same (logical) length.
! Initially there is only one line, trivially it has the same length as itself.
! At each iteration the (logical) line length of every line is reduced by
! exactly one, keeping the invariant valid.
!
! "Logical" line length means the lengh ot the CURRENT_COST
! does not matter (its number of digits). But any "~" counts. Think of the
! invariant as length{REMAINDER_1}+length{OPTIONAL"~"}+length{REMAINDER_2}.
!
! Keeping the logical length the same is important for keeping "copies"
! close together in the data set, which is requred in the reduce step.
!
! Copies
! ------
! Here "copies" of lines in the data set means lines with exactly the
! same REMAINDER_1 and REMAINDER_2. The CURRENT_COST may or may not
! be the same. Lines with "~" are not considered copies.
!
! The @fwd rules can produce at most 3 copies with the same strings.
! The @reduce rules can remove at most 2 consecutive copies.
! The main loop applies @reduce twice for every application of @fwd to
! make sure all copies are removed.
! This corresponds to the d[i,j]=min(f(d[i,j-1]),f(d[i-1,j]),f(d[i-1,j-1]) step
! in a dynamic programming solution of Levenshtein: min() of 3 cost
! for the same remaining strings.
!
! The @fwd rules are designed so that copies eventually will be
! consecutive lines and not spread out.

```

Some sample runs:

```

$ time ./levenshtein.gema floccinaucinihilipilification naucifloccipilinihilification
 12 

real	0m0.016s
user	0m0.010s
sys	0m0.000s

$ time ./levenshtein.gema "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nistrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis eute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum." "Lorem ipsum dolor sit emet, consectetur edipisicing elit, sed do eiusmod tempor incididunt ut lebore et dolore megne elique. Ut enim ed minim veniem, quis nostrud exercitetion ullemco leboris nisi ut eliquip ex ee commodo consequet. Duis eute irure dolor in reprehenderit in voluptete velit esse cillum dolore eu fugiet nulle perietur. Excepteur sint occeecet cupidetet non proident, sunt in culpe qui officie deserunt mollit enim id est leborum."
 29 

real	0m42.670s
user	0m38.800s
sys	0m0.470s

```

---

### Post by Queue29 on 2010-09-05
^^ wow, looking at that is even worse than looking at perl.

---

### Post by Xando on 2010-09-14
I DID IT THIS WAY BECAUSE WHAT I LIKE TO IS THIS:
 
SHOUT IT, SHOUT IT, SHOUT IT OUT LOUD!
 
```

**[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]     PROGRAM[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2] MAIN[/SIZE]
 
**[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]     CHARACTER[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2]*3 S1, T1[/SIZE]
**[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]     CHARACTER[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2]*8 S2, T2[/SIZE]
**[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]     CHARACTER[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2]*100 S3, T3[/SIZE]
**[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]     CHARACTER[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2]*4096 S4, T4[/SIZE]
**[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]     INTEGER[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2] LEV[/SIZE]
 
 
[SIZE=2]    S1 = [/SIZE][SIZE=2][COLOR=#800000][SIZE=2][COLOR=#800000]'dog'[/COLOR][/SIZE]
[/COLOR][/SIZE][SIZE=2]    T1 = [/SIZE][SIZE=2][COLOR=#800000][SIZE=2][COLOR=#800000]'dig'[/COLOR][/SIZE][/COLOR][/SIZE]
[SIZE=2]    S2 = [COLOR=#800000][COLOR=#800000]'navigaet'[/COLOR][/COLOR][/SIZE]
[SIZE=2]    T2 = [COLOR=#800000][COLOR=#800000]'navigate'[/COLOR][/COLOR][/SIZE]
[SIZE=2]    S3 = [COLOR=#800000][COLOR=#800000]'floccinaucinihilipilification'[/COLOR][/COLOR][/SIZE]
[SIZE=2]    T3 = [COLOR=#800000][COLOR=#800000]'naucifloccipilinihilification'[/COLOR][/COLOR][/SIZE]
[SIZE=2]    S4 = [COLOR=#800000][COLOR=#800000]'Lorem ipsum dolor sit amet, consectetur adipisicing elit,'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2]  + [COLOR=#800000][COLOR=#800000]' sed do eiusmod tempor incididunt ut labore et dolore magna'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' aliqua. Ut enim ad minim veniam, quis nistrud exercitation'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' ullamco laboris nisi ut aliquip ex ea commodo consequat.'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' Duis eute irure dolor in reprehenderit in voluptate velit'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' esse cillum dolore eu fugiat nulla pariatur. Excepteur'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' sint occaecat cupidatat non proident, sunt in culpa qui'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' officia deserunt mollit anim id est laborum.'[/COLOR][/COLOR][/SIZE]
[SIZE=2]    T4 = [COLOR=#800000][COLOR=#800000]'Lorem ipsum dolor sit emet, consectetur edipisicing'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' elit, sed do eiusmod tempor incididunt ut lebore et'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' dolore megne elique. Ut enim ed minim veniem, quis'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' nostrud exercitetion ullemco leboris nisi ut eliquip'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' ex ee commodo consequet. Duis eute irure dolor in'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' reprehenderit in voluptete velit esse cillum dolore'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' eu fugiet nulle perietur. Excepteur sint occeecet'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' cupidetet non proident, sunt in culpe qui officie'[/COLOR][/COLOR]//[/SIZE]
[SIZE=2][COLOR=#ffffff][COLOR=#ffffff]+[/COLOR][/COLOR] + [COLOR=#800000][COLOR=#800000]' deserunt mollit enim id est leborum.'[/COLOR][/COLOR][/SIZE]
 
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     CALL[/SIZE][/COLOR][/COLOR]**[SIZE=2] EVALUATE( S1, T1 )[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     CALL[/SIZE][/COLOR][/COLOR]**[SIZE=2] EVALUATE( S2, T2 )[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     CALL[/SIZE][/COLOR][/COLOR]**[SIZE=2] EVALUATE( S3, T3 )[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     CALL[/SIZE][/COLOR][/COLOR]**[SIZE=2] EVALUATE( S4, T4 )[/SIZE]
 
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     END[/SIZE][/COLOR][/COLOR]**[SIZE=2] **[COLOR=#0000ff][COLOR=#0000ff]PROGRAM[/COLOR][/COLOR]**[/SIZE][SIZE=2] MAIN[/SIZE]
 
 
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     SUBROUTINE[/SIZE][/COLOR][/COLOR]**[SIZE=2] EVALUATE( A, B )[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     INTEGER[/SIZE][/COLOR][/COLOR]**[SIZE=2] LEV [/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     CHARACTER[/SIZE][/COLOR][/COLOR]**[SIZE=2]*(*) A[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     CHARACTER[/SIZE][/COLOR][/COLOR]**[SIZE=2]*(*) B[/SIZE]
 
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     WRITE[/SIZE][/COLOR][/COLOR]**[SIZE=2] (*,*) [COLOR=#800000][COLOR=#800000]'LEV: '[/COLOR][/COLOR], LEV( [COLOR=#0000ff][COLOR=#0000ff]TRIM[/COLOR][/COLOR](A), [COLOR=#0000ff][COLOR=#0000ff]TRIM[/COLOR][/COLOR](B) )[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     END SUBROUTINE[/SIZE][/COLOR][/COLOR]**[SIZE=2] EVALUATE[/SIZE]
 
 
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     INTEGER[/SIZE][/COLOR][/COLOR]**[SIZE=2] **[COLOR=#0000ff][COLOR=#0000ff]FUNCTION[/COLOR][/COLOR]**[/SIZE][SIZE=2] LEV( A, B )[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     CHARACTER[/SIZE][/COLOR][/COLOR]**[SIZE=2]*(*) A [/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     CHARACTER[/SIZE][/COLOR][/COLOR]**[SIZE=2]*(*) B[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     INTEGER[/SIZE][/COLOR][/COLOR]**[SIZE=2] J, K, M, N[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     INTEGER[/SIZE][/COLOR][/COLOR]**[SIZE=2] D([COLOR=#0000ff][COLOR=#0000ff]LEN[/COLOR][/COLOR](B)+1, [COLOR=#0000ff][COLOR=#0000ff]LEN[/COLOR][/COLOR](A)+1)[/SIZE]
 
 
[SIZE=2]    M = [COLOR=#0000ff][COLOR=#0000ff]LEN[/COLOR][/COLOR](A)[/SIZE]
[SIZE=2]    N = [COLOR=#0000ff][COLOR=#0000ff]LEN[/COLOR][/COLOR](B)[/SIZE]
 
 
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]      DO[/SIZE][/COLOR][/COLOR]**[SIZE=2] 70, K=1, M+1[/SIZE]
[SIZE=2]       D(1, K) = K-1[/SIZE]
[COLOR=#ff0000][COLOR=#ff0000][SIZE=2]70[/SIZE][/COLOR][/COLOR][SIZE=2]  **[COLOR=#0000ff][COLOR=#0000ff]CONTINUE[/COLOR][/COLOR]**[/SIZE]
 
 
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     DO[/SIZE][/COLOR][/COLOR]**[SIZE=2] 80, J=1, N+1[/SIZE]
[SIZE=2]       D(J, 1) = J-1[/SIZE]
[COLOR=#ff0000][COLOR=#ff0000][SIZE=2]80[/SIZE][/COLOR][/COLOR][SIZE=2]  **[COLOR=#0000ff][COLOR=#0000ff]CONTINUE[/COLOR][/COLOR]**[/SIZE]
 
 
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]     DO[/SIZE][/COLOR][/COLOR]**[SIZE=2] 100, J=2, N[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]        DO[/SIZE][/COLOR][/COLOR]**[SIZE=2] 90, K=2, M[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]           IF[/SIZE][/COLOR][/COLOR]**[SIZE=2] ( A(K-1:K-1) .EQ. B(J-1:J-1) ) **[COLOR=#0000ff][COLOR=#0000ff]THEN[/COLOR][/COLOR]**[/SIZE]
[SIZE=2]            D(J,K) = D(J-1,K-1)[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]           ELSE[/SIZE][/COLOR][/COLOR]**
[SIZE=2]            D(J,K) = [COLOR=#0000ff][COLOR=#0000ff]MIN[/COLOR][/COLOR]( D(J-1,K-1)+1, D(J-1,K)+1, D(J,K-1)+1 )[/SIZE]
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]           END IF[/SIZE][/COLOR][/COLOR]**
[COLOR=#ff0000][COLOR=#ff0000][SIZE=2]90[/SIZE][/COLOR][/COLOR][SIZE=2]   **[COLOR=#0000ff][COLOR=#0000ff]CONTINUE[/COLOR][/COLOR]**[/SIZE]
[COLOR=#ff0000][COLOR=#ff0000][SIZE=2]100[/SIZE][/COLOR][/COLOR][SIZE=2]  **[COLOR=#0000ff][COLOR=#0000ff]CONTINUE[/COLOR][/COLOR]**[/SIZE]
 
 
[SIZE=2]    LEV = D(N,M)[/SIZE]
 
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]      RETURN[/SIZE][/COLOR][/COLOR]**
**[COLOR=#0000ff][COLOR=#0000ff][SIZE=2]      END FUNCTION[/SIZE][/COLOR][/COLOR]**[SIZE=2] LEV[/SIZE]
 
 

```
 
TIME:
```

real     0n0.039s
user    0n0.000s
sys      0n0.038s

```
 
LET'S GET THIS PARTY STARTED. YES, GET THIS PARTY STARTED!
 
(/code can't handle FORTRAN formatting. Here, at least. All messed up)

---

### Post by soltanis on 2010-09-14
> **Xando said:**
> I DID IT THIS WAY BECAUSE WHAT I LIKE TO IS THIS:
 
SHOUT IT, SHOUT IT, SHOUT IT OUT LOUD!

I was so disappointed when this was not COBOL.

---

### Post by schauerlich on 2010-09-21
howlingmadhowie hasn't posted in 4 weeks... perhaps the beginner's team should take over judging?

---

### Post by Bodsda on 2010-09-22
> **schauerlich said:**
> howlingmadhowie hasn't posted in 4 weeks... perhaps the beginner's team should take over judging?
 
Good idea. Unfortunately I am on a training course at the moment so don't have my ubuntu pc or access to the internet from the hotel so I cant judge this until Saturday. I'll drop an email to the rest of the guys about this but if it is not judged by the time I get back, I'll do it then.
 
Thanks - Happy coding,
Bodsda

---

### Post by duanedesign on 2010-09-24
We will get this judged tonight or tomorrow. Thank you all for your patience.

thank you,
duanedesign

---

### Post by lisati on 2010-09-24
OMG FORTRAN! It's like a visit from a friend you haven't seen for a while.

> **duanedesign said:**
> We will get this judged tonight or tomorrow. Thank you all for your patience.

thank you,
duanedesign
Good luck!

---

### Post by duanedesign on 2010-09-30
First let me start by apologizing. There was a miscommunication that resulted in the challenge not being judged last weekend. We are now working to fix this and get the challenge judged. Thank you for your patience. The challenge **will be judged **in the next 48 hours.

**EDIT:** Well it is proving tougher then I had anticipated finding someone to judge this challenge. Our usual safety net has been very busy and unable to find the time to pick a winner. Please be patient we are working on this and will have a winner declared soon.

thank you,
duanedesign

---

### Post by Bodsda on 2010-10-06
Hi Guys,

Sorry for my recent lack of activity, but I am back and I have a winner! Please put your hands together for...

...
...
...

[COLOR=Red]_PEDRO3005_[/COLOR]

...
...
...

Congratulations. Despite the application not meeting every requirement for the challenge, the enthusiasm and will to learn has earned you brownie points. Having fun is a large part of these challenges and pedro3005 seems to have successfully ticked that box. 

Pedro3005, I would appreciate it if you could post the next challenge titled "Beginners Programming Challenge 16" - 

Due to points raised by other posters in the thread, could you also keep the target audience in mind when dreaming up the next challenge, it would be great to see more *beginners* posting.


Thanks to everyone for participating, the success of these challenges is down to you guys. 

Happy Coding,
Bodsda
Ubuntu Beginners Team Development Focus Group

---

### Post by Odexios on 2010-10-06
Ok, now that the contest is over, is there anyone who can help me with the memory exhaustion problem?

[http://ubuntuforums.org/showpost.php?p=9782799&postcount=28](http://ubuntuforums.org/showpost.php?p=9782799&postcount=28)

I'm open to every kind of suggestion, even if it's unrelated to the problem, of course.

---

### Post by schauerlich on 2010-10-06
> **Odexios said:**
> Ok, now that the contest is over, is there anyone who can help me with the memory exhaustion problem?

[http://ubuntuforums.org/showpost.php?p=9782799&postcount=28](http://ubuntuforums.org/showpost.php?p=9782799&postcount=28)

I'm open to every kind of suggestion, even if it's unrelated to the problem, of course.

Well, for starters:

```
void fcopy(FILE *fp, char **buff) {
    
    char r;
    int n, limit, i;
    char *b, *bres;
    
    b = malloc(sizeof(char) * limit);
```

limit is never initialized, meaning is can be anything. 

The reason you're having memory exhaustion problems, though, is because it's recurses 3 times per call, meaning the stack and other storage requirements grow very quickly. More importantly, you never free anything you malloc. So even though the stack is cleaned up as the calls unwind, you still leave tons of dead matrices all over the heap.

---

### Post by schauerlich on 2010-10-06
> **Bodsda said:**
> Congratulations. Despite the application not meeting every requirement for the challenge, the enthusiasm and will to learn has earned you brownie points. 

Shouldn't the winning entry, you know, work? I realize there weren't many true beginners to choose from, but still... brownie points for enthusiasm doesn't really mean much when the code is not correct. And I mean no offense to pedro3005, I'm glad he appears to have designed his own algorithm instead of blindly copying Wikipedia.

EDIT: And I don't mean to come off as a sore loser, I'm not a beginner and my entries shouldn't win anyhow...

---

### Post by Odexios on 2010-10-06
> **schauerlich said:**
> Well, for starters:

```
void fcopy(FILE *fp, char **buff) {
    
    char r;
    int n, limit, i;
    char *b, *bres;
    
    b = malloc(sizeof(char) * limit);
```limit is never initialized, meaning is can be anything. Thanks, I didn't really notice. I'll come back when I get my head out of the sand.

> The reason you're having memory exhaustion problems, though, is because it's recurses 3 times per call, meaning the stack and other storage requirements grow very quickly. More importantly, you never free anything you malloc. So even though the stack is cleaned up as the calls unwind, you still leave tons of dead matrices all over the heap.I don't see where it happens. I mean, didn't I malloc the matrix only once, in the lev_length function?

I guess I'll try with an iterative function, anyway.

---

### Post by schauerlich on 2010-10-06
> **Odexios said:**
> Thanks, I didn't really notice. I'll come back when I get my head out of the sand.

I don't see where it happens. I mean, didn't I malloc the matrix only once, in the lev_length function?

I guess I'll try with an iterative function, anyway.

Oh, you're right, I misread that. Sorry. You never freed it in lev_length though. :) A recursive solution will still be terribly inefficient (there were several such entries at the beginning of the thread, including one of mine).

---

### Post by Odexios on 2010-10-06
> **schauerlich said:**
> Oh, you're right, I misread that. Sorry. You never freed it in lev_length though. :) A recursive solution will still be terribly inefficient (there were several such entries at the beginning of the thread, including one of mine).Ok, I'll give it a try.

Is it "normal" for the stack to get filled that quickly? I thought the memory requirements in something like this would have been trivial...

EDIT: Not that trivial, I suppose. For a square matrix of, don't know, 100x100 it's already more than  10^25 calls. I underestimated it XD

---

### Post by schauerlich on 2010-10-06
> **Odexios said:**
> Ok, I'll give it a try.

Is it "normal" for the stack to get filled that quickly? I thought the memory requirements in something like this would have been trivial...

EDIT: Not that trivial, I suppose. For a square matrix of, don't know, 100x100 it's already more than  10^25 calls. I underestimated it XD

It won't make all of those calls at once. But it seems to be filling up swap too when I run it, which won't happen on a stack overflow... it will simply segfault. I'm not sure what's the reason, but then again, I don't like low level memory management type stuff...

---

### Post by schauerlich on 2010-11-24
Well, I got bored last night and decided to put my own twist on the classic ["methinks it like a weasel"](http://en.wikipedia.org/wiki/Weasel_program) thought experiment. It uses the levenshtein distance to decide how fit a mutation is, and the string can grow and shrink. Seems a bit more "evolutionary" to me. :)

```
import sys, random, string

def lev_dist(one, two):
    d = [[0] * (len(two) + 1) for i in range(len(one)+1)]
    
    for i in range(len(one) + 1):
        d[i][0] = i
    for j in range(len(two) + 1):
        d[0][j] = j

    for j in range(1, len(two) + 1):
        for i in range(1, len(one) + 1):
            if one[i-1] == two[j-1]:
                d[i][j] = d[i-1][j-1]
            else:
                d[i][j] = min(d[i-1][j] + 1,
                              d[i][j-1] + 1,
                              d[i-1][j-1] + 1)

    return d[len(one)][len(two)]


def evolve(dest, gen_size=40, close_enough=5):
    generations = 0
    src = ""

    while lev_dist(src, dest) >= (10 - close_enough + 1):
        generations += 1
        
        ng = ((x, lev_dist(x, dest)) for x in next_gen(src, gen_size))
        src = min(ng, key=lambda x: x[1])[0]
        
        if generations % 5 == 0:
            print "generation %3d: %s" % (generations, src)

    return src, generations


def next_gen(src, num):
    return map(random_op, [src] * num) 


def random_op(src):
    tmp = list(src)
    newchar = random.choice(string.lowercase + " ")

    if src.strip() == "":
        r = "i"
        pos = 0
    else:
        pos = random.randint(0, len(tmp)-1)
        r = random.choice((["s"] * 8) + ["i", "d"])
    
    if r == "i":
        tmp.insert(pos, newchar) # insertion
    elif r == "d":
        tmp.pop(pos) # deletion
    else:
        tmp[pos] = newchar # substitution

    return "".join(tmp)


def main():
    print evolve(sys.argv[1], int(sys.argv[2]), int(sys.argv[3]))
    
if __name__ == "__main__":
    main()

```

Here's a sample run. The 40 means it makes 40 mutations per generation, and the 8 is the "perfection coefficient" - how close it has to be to perfect before it says "close enough" and stops.

```
schauerlich@inara:~$ python methinks.py "methinks it is like a weasel" 40 8
generation   5: htea
generation  10: eh l a
generation  15: ts le ea
generation  20: otsi eaea
generation  25: ytsiti  ea
generation  30: etsit   ea
generation  35: ethit  le ea
generation  40: sethint sle ea
generation  45: oethint sle sea
generation  50: methint sli wea
generation  55: methint solime wes
generation  60: methinzt s like aees
generation  65: methinrs it s like ahes
generation  70: methinvs it ss like aes
generation  75: methinvs it is like  ee
generation  80: methinzs it is like  cee
generation  85: methinzs it is like  mese
generation  90: methinks it is like  ease
generation  95: methinks it is lika wease
generation 100: methints it is lika wease
generation 105: methinus it is lix a wease
generation 110: methinys it is lik a wease
generation 115: methinzs it is lije a wease
generation 120: methinys it is liee a wease
generation 125: methinas it is lie a weasl
generation 130: methinps it is lie a weasl
('methinks it is lie a weasl', 132)

```

As you can see, not perfect, but "close enough" from an evolutionary point of view. :) Anyways, I just thought beginners might be interested to see how this sort of thing can be used.

---

