---
title: "Beginner Programming Challenge 14"
date: 2010-06-25
forum: Programming Talk
---

### Post by dv3500ea on 2010-06-25
[SIZE=6]Beginner Programming Challenge # 14[/SIZE]

As the winner of [Beginner Programming Challenge 13]("http://ubuntuforums.org/showthread.php?t=1500005"),
it is my turn to propose a challenge.

It will be quite mathematical but very useful for those wanting
to get into graphics/game programming but also requires some simple
text parsing.

Consider a graph on conventional **[Cartesian]("http://en.wikipedia.org/wiki/Cartesian_coordinate_system")** axes.
You will be given a set of [transformations]("http://en.wikipedia.org/wiki/Transformation_%28geometry%29") to perform from a file
of 'commands'. These will be fed into **[SIZE=2]stdin[/SIZE]**. When your program reaches a
line begginning 'end', it should read ***one*** line of coordinates and transform
each pair of coordinates, printing the transformed coordinates.

I will demonstrate the commands. The parts of the commands that should be taken as
variables will be enclosed in 2 [COLOR=blue]$[/COLOR] signs like [COLOR=blue]$[/COLOR]this[COLOR=blue]$[/COLOR]. Note that in the real commands
these [COLOR=blue]$[/COLOR] signs will no appear - they are used for clarity.

[LIST]
[*]```
transform [COLOR=blue]$[/COLOR]a[COLOR=blue]$[/COLOR] [COLOR=blue]$[/COLOR]b[COLOR=blue]$[/COLOR] [COLOR=blue]$[/COLOR]c[COLOR=blue]$[/COLOR] [COLOR=blue]$[/COLOR]d[COLOR=blue]$[/COLOR]
```    -> transform coordinates by [**matrix**]("http://en.wikipedia.org/wiki/Matrix_%28mathematics%29")
    |a b|
    |c d| which is a linear transformation.
[*]```
translate [COLOR=blue]$[/COLOR]x[COLOR=blue]$[/COLOR] [COLOR=blue]$[/COLOR]y[COLOR=blue]$[/COLOR]
```    -> [**translate**]("http://en.wikipedia.org/wiki/Translation_%28geometry%29") coordinates by [**vector**]("http://en.wikipedia.org/wiki/Euclidean_vector")
    |x|
    |y|
[*]```
enlarge [COLOR=blue]$[/COLOR]scale_factor[COLOR=blue]$[/COLOR]
```    -> [**enlarge**]("http://en.wikipedia.org/wiki/Scaling_%28geometry%29") by scale factor scale_factor about the origin
[*]```
rotate [COLOR=blue]$[/COLOR]angle_in_rads[COLOR=blue]$[/COLOR] clockwise
```    -> [**rotate**]("http://en.wikipedia.org/wiki/Rotation_%28geometry%29") angle_in_rads [**radians**]("http://en.wikipedia.org/wiki/Radian") clockwise about the origin
[*]```
rotate [COLOR=blue]$[/COLOR]angle_in_rads[COLOR=blue]$[/COLOR] anticlockwise
```    ->[**rotate**]("http://en.wikipedia.org/wiki/Rotation_%28geometry%29") angle_in_rads [**radians**]("http://en.wikipedia.org/wiki/Radian") anticlockwise about the origin
[*]```
rotate deg [COLOR=blue]$[/COLOR]angle_in_degs[COLOR=blue]$[/COLOR] clockwise
```    -> [**rotate**]("http://en.wikipedia.org/wiki/Rotation_%28geometry%29") angle_in_degs **[degrees]("http://en.wikipedia.org/wiki/Degree_%28angle%29")** clockwise about the origin
[*]```
rotate deg [COLOR=blue]$[/COLOR]angle_in_degs[COLOR=blue]$[/COLOR] anticlockwise
```    -> **[rotate]("http://en.wikipedia.org/wiki/Rotation_%28geometry%29")** angle_in_degs **[degrees]("http://en.wikipedia.org/wiki/Degree_%28angle%29")** anticlockwise about the origin
[*]```
reflect y = [COLOR=blue]$[/COLOR]m[COLOR=blue]$[/COLOR]x
```    -> **[reflect]("http://en.wikipedia.org/wiki/Reflection_%28mathematics%29")** through straight line y=mx
[*]```
end
```    -> read coordinates from next line
[/LIST]
The coordinates line, and the printed output should be in the following format
```
[COLOR=blue]$[/COLOR]x1[COLOR=blue]$[/COLOR],[COLOR=blue]$[/COLOR]y1[COLOR=blue]$[/COLOR] [COLOR=blue]$[/COLOR]x2[COLOR=blue]$[/COLOR],[COLOR=blue]$[/COLOR]y2[COLOR=blue]$[/COLOR], ... [COLOR=blue]$[/COLOR]xn[COLOR=blue]$[/COLOR],[COLOR=blue]$[/COLOR]yn[COLOR=blue]$[/COLOR]
```EXAMPLE:
input:
```

transform 1 0 0 1
translate 1 2
translate -1 -2
enlarge 2
enlarge 0.5
enlarge -1
enlarge -1
rotate 3.141592653589 clockwise
rotate 3.141592653589 anticlockwise
rotate deg 180 clockwise
rotate deg 180 anticlockwise
reflect y = 0x
reflect y = 0x
end
0,0 1,1 2,2 -1,-1, 0.5,0.5

```output:
```

0,0 1,1 2,2 -1,-1, 0.5,0.5

```I know this may seem a bit daunting but the input is easy enough to parse.
It would be a very good idea to research '[**[SIZE=3]matrix transformations[/SIZE]**]("http://www.google.co.uk/search?hl=en&source=hp&q=matrix+transformations&aq=f&aqi=g8g-m2&aql=&oq=&gs_rfai=")', '**[SIZE=3][matrix multiplication]("http://www.google.co.uk/search?hl=en&q=matrix+multiplication&aq=f&aqi=g10&aql=&oq=&gs_rfai=")[/SIZE]**'
and '[SIZE=3]**[inverse of a 2x2 matrix]("http://www.google.co.uk/search?hl=en&q=inverse+of+a+2x2+matrix&aq=f&aqi=g-c6&aql=&oq=&gs_rfai=")**[/SIZE]'. It is likely you have not come across this area of
maths before but there are plenty of places online to look it up and the actual
algorithms are relatively simple.

Rules:
[LIST]
[*][COLOR=Lime]You may use any language [COLOR=Orange]**AS LONG AS IT IS AVAILABLE IN THE UBUNTU REPOSITORIES**[/COLOR]
[/COLOR]
[*][COLOR=lime]You may use any standard libraries available with your language[/COLOR]
    [COLOR=Red]unless they have specific matrix or vector functionality[/COLOR]
[*][COLOR=red]You may not use any non-standard libraries[/COLOR]
[*][COLOR=YellowGreen]You should provide details of how to compile/run your program[/COLOR]
[*][COLOR=Lime]You may ask for helps or hints if you get stuck[/COLOR]
[*][COLOR=Red]Any obfusgated code or precompiled programs will not be marked[/COLOR]
[/LIST]

You will be marked out of 100. There will be 10 marks each available for
correctly implementing translate, enlarge, rotate, reflect and 20 marks
for correctly implementing transform. There will be 10 marks for correctly
parsing/formatting the input/output. More subjectively, there will
be up to 10 marks for each of:
[LIST]
[*]layout and commenting (use whitespace and descriptive comments)
[*]elegance of design (use object oriented or functional techniques)
[*]speed of execution (to be tested with the time command)
[/LIST]
There may be chance for extra credit later on.

Good luck, and have fun coding! :D

EXTENSION TASKS:
These are worth 5 marks each, but you can't get over 100 marks.
[LIST=1]
[*]allow a '-c' flag to be passed that causes your calculated coordinates to be converted to the 'computer' coordinate system (by which I mean origin at the top-left hand corner and positive direction down and right). The argument after the -c flag should be the x and y coordinates of the Cartesian origin on this coordinate system, separated by a ','. eg.
```
./program -c '100,200'
``` puts the origin 100px right and 200px down from 0,0.
[*]Accept an '-i' flag that prints the translation vector and transformation matrix that reverse completely all of the transformations performed from the input.
[/LIST]

---

### Post by DanielWaterworth on 2010-06-25
This seems a little easy even for a beginner. What's the extra credit options? How about n-dimensional space?

---

### Post by dv3500ea on 2010-06-25
> **DanielWaterworth said:**
> This seems a little easy even for a beginner.

Do you think?

In the UK, you need to be doing AS level further maths to even cover what a matrix is.

> **DanielWaterworth said:**
> What's the extra credit options? I will come up with these in due course. I'm considering:
[LIST]
[*]The representation of the cartesian coordinates on a computer screen.
[*]Asking for 1 matrix and 1 vector that reverse all of the transformations
[*]Some sort of function plotting ability (as in getting a list of coordinates and transforming them from a mathematical function)
[/LIST]

> **DanielWaterworth said:**
> How about n-dimensional space?
3D space, perhaps, although I'd have to teach myself 3D geometry first. I'm not even considering hyperspace geometry:confused:!!!

---

### Post by DanielWaterworth on 2010-06-25
> **dv3500ea said:**
> In the UK, you need to be doing AS level further maths to even cover what a matrix is.

I know, in fact I'll have finished A2 on Tuesday, which is my last exam. It used to be part of the GSCE syllabus. I suppose the main reason it's simple is because there's no variable sized... anything [=, (except the input).

---

### Post by lostinxlation on 2010-06-25
I think you should drop the speed requirement from the judging criteria. Having speed in mind, the scripting languages are all out.

---

### Post by dv3500ea on 2010-06-25
> **lostinxlation said:**
> I think you should drop the speed requirement from the judging criteria. Having speed in mind, the scripting languages are all out.

Don't be put off using scripting languages. In my mind speed is the least important criterion. If your program uses a scripting language this will cause it to be a bit slower, so you will lose some of the speed marks but it is more than likely that you will gain marks for elegance and find it easier to implement.

 My main intention for the speed category is to make people think about how they implement the program. For example, it is possible to represent any number of the listed transformations in 6 numbers. You could alternatively store each transformation and apply them all separately. One of these is clearly going to be better performing.

---

### Post by DaGarver on 2010-06-28
Are we allowed to assume that the last line of the text file used for input is reserved for coordinates only? As in, the second to last line is always "end" and the following line is the set of points to perform operations on?

---

### Post by burton247 on 2010-06-29
I finished my current project:

a matrix calculator for nxn matrices. 

Does all the ERO, addition, multiplication and calculates det, inverse etc. 

The inverse bit was good cause of reusing code, use of recursion and stuff

---

### Post by dv3500ea on 2010-06-29
> **DaGarver said:**
> Are we allowed to assume that the last line of the text file used for input is reserved for coordinates only? As in, the second to last line is always "end" and the following line is the set of points to perform operations on?

The line after the 'end' line will only have coordinates on it but don't assume this is at the last line in the file. You can ignore lines after the coordinate line though.

> **burton247 said:**
> I finished my current project:

a matrix calculator for nxn matrices. 

Does all the ERO, addition, multiplication and calculates det, inverse etc. 

The inverse bit was good cause of reusing code, use of recursion and stuff

That would be very useful for this challenge. Feel free to use this if you are doing the challenge. Note that this challenge only requires operations on 2x2 and 2x1 matrices. I'd be interested to know how det/inverse is found from nxn matrices (I've only covered these operations on 2x2 matrices in my maths class).

---

### Post by DaGarver on 2010-07-02
> **dv3500ea said:**
>  I'd be interested to know how det/inverse is found from nxn matrices (I've only covered these operations on 2x2 matrices in my maths class).

Determinant of an NxN matrix is found by using a technique called [cofactor expansion]("http://en.wikipedia.org/wiki/Cofactor_(linear_algebra)"). The inverse of a matrix is actually equivalent to the reciprocal of the determinant times a matrix of its cofactors ([http://mathworld.wolfram.com/MatrixInverse.html](http://mathworld.wolfram.com/MatrixInverse.html)).

Linear Algebra is quite an interesting subject. You get to see how a lot of things relate to each other, a lot of the stuff you take for granted when doing basic algebra. And, in all honesty, it seems like having a background in it is a *major* help for this challenge.

---

### Post by DanielWaterworth on 2010-07-02
> **DaGarver said:**
> Determinant of an NxN matrix is found by using a technique called [cofactor expansion]("http://en.wikipedia.org/wiki/Cofactor_%28linear_algebra%29"). The inverse of a matrix is actually equivalent to the reciprocal of the determinant times a matrix of its cofactors ([http://mathworld.wolfram.com/MatrixInverse.html](http://mathworld.wolfram.com/MatrixInverse.html)).

Linear Algebra is quite an interesting subject. You get to see how a lot of things relate to each other, a lot of the stuff you take for granted when doing basic algebra. And, in all honesty, it seems like having a background in it is a *major* help for this challenge.

Cofactor expansion is just the way they teach you to find the determinant. There are faster ways that are used in practicality, see [http://en.wikipedia.org/wiki/Determinant](http://en.wikipedia.org/wiki/Determinant) . For the inverse, the gauss-jordan method is usually used, see [http://en.wikipedia.org/wiki/Gauss-Jordan_elimination](http://en.wikipedia.org/wiki/Gauss-Jordan_elimination) .

---

### Post by burton247 on 2010-07-02
Yes they're faster on larger matrices. But I already had a function for cofactors and det. So all I needed to do was create a new method that called cofactor() and det() and used the return slightly different to get a matrix of cofactors. Transverse it, multiply by the det and done. Wasn't much point creating a new method for a different method. It was only for a small project at uni, didn't want to spend too long it

---

### Post by DaGarver on 2010-07-07
One more question (and also to get this back on the front page...): reflect takes a parameter $y = mx$. Are we then safe to assume that the line goes through the origin? My intuition says yes; reflections across lines not going through the origin aren't very pretty, especially in the scope of this project.

---

### Post by texaswriter on 2010-07-10
bump:P

---

### Post by dv3500ea on 2010-07-11
> **DaGarver said:**
> One more question (and also to get this back on the front page...): reflect takes a parameter $y = mx$. Are we then safe to assume that the line goes through the origin? My intuition says yes; reflections across lines not going through the origin aren't very pretty, especially in the scope of this project.

Yes, you can assume that; that's why I chose y=mx instead of y=mx+c.

---

### Post by howlingmadhowie on 2010-07-14
okay, just to get the ball rolling, here's a solution in scheme:

```

#!/usr/bin/guile -s
!#

(use-modules (ice-9 rdelim) (ice-9 regex))

(define make-point
  list)
(define x-coordinate
  car)
(define y-coordinate
  cadr)

(define make-matrix
  (lambda l
    l))
(define a-value
  car)
(define b-value
  cadr)
(define c-value
  caddr)
(define d-value
  cadddr)

(define make-vector
  list)
(define x-translation
  car)
(define y-translation
  cadr)

(define make-matrix-from-two-points-as-list
  (lambda (l)
    (make-matrix (x-coordinate (car l))
		 (y-coordinate (car l))
		 (x-coordinate (cadr l))
		 (y-coordinate (cadr l)))))

(define inverse-matrix
  (lambda (matrix)
    (let ((determinant (- (* (a-value matrix) (d-value matrix))
			  (* (b-value matrix) (c-value matrix)))))
      (make-matrix (/ (d-value matrix) determinant)
		   (/ (* -1 (b-value matrix)) determinant)
		   (/ (* -1 (c-value matrix)) determinant)
		   (/ (a-value matrix) determinant)))))


(define point-add
  (lambda (point1 point2)
    (make-point (+ (x-coordinate point1) (x-coordinate point2))
		(+ (y-coordinate point1) (y-coordinate point2)))))

(define point-subtract
  (lambda (point1 point2)
    (make-point (- (x-coordinate point1) (x-coordinate point2))
		(- (y-coordinate point1) (y-coordinate point2)))))

(define scalar-product
  (lambda (vector1 vector2)
    (+ (* (x-translation vector1) (x-translation vector2))
       (* (y-translation vector1) (y-translation vector2)))))

(define PI 3.14159265358979)

(define RADS-PER-DEGREE
  (/ (* PI) 180))

(define transform
  (lambda (matrix point)
    (make-point (+ (* (x-coordinate point) (a-value matrix))
		   (* (y-coordinate point) (c-value matrix)))
		(+ (* (x-coordinate point) (b-value matrix))
		   (* (y-coordinate point) (d-value matrix))))))

(define translate
  (lambda (vector point)
    (make-point (+ (x-coordinate point) (x-translation vector))
		(+ (y-coordinate point) (y-translation vector)))))

(define enlarge
  (lambda (factor point)
    (make-point (* (x-coordinate point) factor)
		(* (y-coordinate point) factor))))

(define rotate
  (lambda (rads point)
    (transform (make-matrix (cos rads) (sin rads) (- (sin rads)) (cos rads))
	       point)))

(define rotate-degrees
  (lambda (degrees point)
    (rotate (* degrees RADS-PER-DEGREE)
	    point)))

(define reflect
  (lambda (m point)
    (let ((m-vector (make-vector m 1)))
      (point-subtract (enlarge (/ (* 2 (scalar-product point m-vector))
				  (scalar-product m-vector m-vector)) m-vector)
		      point))))

(define perform-on-list
  (lambda (operation arg point-list)
    (if (null? point-list)
	'()
	(cons (operation arg (car point-list))
	      (perform-on-list operation arg (cdr point-list))))))


(define print-point
  (lambda (point)
    (format #t "~S,~S " (x-coordinate point) (y-coordinate point))))

(define print-points
  (lambda (points)
    (if (null? points)
	(newline)
	(begin (print-point (car points))
	       (print-points (cdr points))))))

(define make-intent
  (lambda (func arg)
    (lambda (points)
      (perform-on-list func arg points))))

(define number-pattern "[+-]?[0-9]*\\.?[0-9]+")
(define two-numbers-pattern (string-concatenate (list number-pattern " " number-pattern)))
(define four-numbers-pattern (string-concatenate (list number-pattern
						       " "
						       number-pattern
						       " "
						       number-pattern
						       " "
						       number-pattern)))
(define point-pattern (string-concatenate (list number-pattern "," number-pattern)))
(define points-pattern (string-concatenate (list point-pattern
						       "( "
						       point-pattern
						       ")*")))
						       

(define number-regexp (make-regexp number-pattern))
(define two-numbers-regexp (make-regexp two-numbers-pattern))
(define four-numbers-regexp (make-regexp four-numbers-pattern))
(define points-regexp (make-regexp points-pattern))
(define end-regexp (make-regexp "^end$"))
(define rotate-clockwise-regexp (make-regexp "^rotate [0-9]*.?[0-9]+( clockwise|)$"))
(define rotate-anticlockwise-regexp (make-regexp "^rotate [0-9]*.?[0-9]+ anticlockwise$"))
(define transform-regexp (make-regexp "^transform( [+-]?[0-9]*\\.?[0-9]*){4}$"))
(define translate-regexp (make-regexp "^translate( [+-]?[0-9]*\\.?[0-9]*){2}$"))
(define enlarge-regexp (make-regexp "^enlarge [+-]?[0-9]*\\.?[0-9]*$"))
(define rotate-degrees-clockwise-regexp (make-regexp "^rotate deg [0-9]*.?[0-9]+( clockwise|)$"))
(define rotate-degrees-anticlockwise-regexp (make-regexp "^rotate deg [0-9]*.?[0-9]+ anticlockwise$"))
(define reflect-regexp (make-regexp "^reflect y = [+-]?[0-9]*\\.?[0-9]*x$"))

(define make-check-regexp
  (lambda (regexp)
    (lambda (str)
      (let ((match (regexp-exec regexp str)))
	(if match #t #f)))))

(define is-rotate-clockwise?
  (make-check-regexp rotate-clockwise-regexp))
(define is-rotate-anticlockwise?
  (make-check-regexp rotate-anticlockwise-regexp))
(define is-rotate-degrees-clockwise?
  (make-check-regexp rotate-degrees-clockwise-regexp))
(define is-rotate-degrees-anticlockwise?
  (make-check-regexp rotate-degrees-anticlockwise-regexp))
(define is-enlarge?
  (make-check-regexp enlarge-regexp))
(define is-reflect?
  (make-check-regexp reflect-regexp))

(define is-translate?
  (lambda (str)
    (let ((match (regexp-exec translate-regexp str)))
      (if match #t #f))))

(define is-transform?
  (lambda (str)
    (let ((match (regexp-exec transform-regexp str)))
      (if match #t #f))))

(define get-number
  (lambda (str)
    (string->number (match:substring (regexp-exec number-regexp str)))))

(define get-two-numbers
  (lambda (str)
    (map string->number (string-split (match:substring (regexp-exec two-numbers-regexp str)) #\space))))


(define is-points?
  (make-check-regexp points-regexp))

(define string-comma-split->number
  (lambda (str)
    (map string->number (string-split str #\,))))

(define get-points 
  (lambda (str)
    (map string-comma-split->number
	 (string-split (match:substring (regexp-exec points-regexp str)) #\space))))

      

(define is-transform?
  (lambda (str)
    (let ((match (regexp-exec transform-regexp str)))
      (if match #t #f))))

(define get-four-numbers
  (lambda (str)
    (map string->number (string-split (match:substring (regexp-exec four-numbers-regexp str)) #\space))))



(define is-end?
  (lambda (str)
    (regexp-exec end-regexp str)))


(define get-command-list
  (lambda ()
    (let ((command (read-line)))
      (cond ((is-end? command) '())
	    ((is-rotate-clockwise? command)
	     (cons (make-intent rotate (get-number command)) (get-command-list)))
	    ((is-rotate-anticlockwise? command)
	     (cons (make-intent rotate (* -1 (get-number command))) (get-command-list)))
	    ((is-rotate-degrees-clockwise? command)
	     (cons (make-intent rotate-degrees (get-number command)) (get-command-list)))
	    ((is-rotate-degrees-anticlockwise? command)
	     (cons (make-intent rotate-degrees (* -1 (get-number command))) (get-command-list)))
	    ((is-reflect? command)
	     (cons (make-intent reflect (get-number command)) (get-command-list)))
	    ((is-enlarge? command)
	     (cons (make-intent enlarge (get-number command)) (get-command-list)))
	    ((is-translate? command)
	     (cons (make-intent translate (get-two-numbers command)) (get-command-list)))
	    ((is-transform? command)
	     (cons (make-intent transform (get-four-numbers command)) (get-command-list)))))))
;	    (else (cons command (get-command-list)))))))



(define command-list (get-command-list))

(define perform 
  (lambda (command-list points)
    (if (null? command-list)
	points
	(perform (cdr command-list) ((car command-list) points)))))

(if (and (not (null? (cadr (command-line))))
	 (equal? "-i" (cadr (command-line))))
    (display (inverse-matrix 
	      (make-matrix-from-two-points-as-list
	       (perform command-list (get-points "1,0 0,1")))))
      
    (begin
      (define points #f)
      (let ((point-line (read-line)))
	(if point-line
	    (set! points (get-points point-line))))
      (print-points (perform command-list points))))

```

to run it, install guile1.8, save the script and make the script executable. then enter 
```

./myscriptname

```
in the shell.

it supports a '-i' command line switch.

in general it seems to work okay. i wasted a lot of space writing regular expressions for input parsing and at the moment it's very picky about whitespace, but i may correct that later.

have fun!

---

### Post by dv3500ea on 2010-07-14
I can't seem to run this successfully:
When I input "end\n", this error is given:
```

ERROR: Wrong type (expecting pair): ()

```
It works OK with the '-i' flag, except where a translation is used.
eg. when I input
```

translate 1 1
end

```
It should output a matrix:
```

[ 1 0
  0 1 ]

```
and a vector:
```

[ -1
  -1 ]

```
but instead it outputs the matrix:
```

[ 2/3 -1/3
  -1/3 2/3 ]

```
and no vector.

---

### Post by howlingmadhowie on 2010-07-14
nope, it doesn't produce a translation with the -i flag. i may build that in later. at the moment i produce the inverse by just entering a unity matrix and seeing what happens to it, then inverting the result. this can of course not cope with translations.

as it is, there is a bug in my code:
```

(if (and (not (null? (cadr (command-line))))

```
should be:
```

(if (and (not (null? (cdr (command-line))))

```

sorry, just a stupid typo.

---- edit ----

okay, i modified the code to output a translation vector and a rotation matrix. here it is:
```

#!/usr/bin/guile
!#

(use-modules (ice-9 rdelim) (ice-9 regex))

(define make-point
  list)
(define x-coordinate
  car)
(define y-coordinate
  cadr)

(define make-matrix
  (lambda l
    l))
(define a-value
  car)
(define b-value
  cadr)
(define c-value
  caddr)
(define d-value
  cadddr)

(define make-vector
  list)
(define x-translation
  car)
(define y-translation
  cadr)

(define make-matrix-from-two-points-as-list
  (lambda (l)
    (make-matrix (x-coordinate (car l))
		 (y-coordinate (car l))
		 (x-coordinate (cadr l))
		 (y-coordinate (cadr l)))))

(define inverse-matrix
  (lambda (matrix)
    (let ((determinant (- (* (a-value matrix) (d-value matrix))
			  (* (b-value matrix) (c-value matrix)))))
      (make-matrix (/ (d-value matrix) determinant)
		   (/ (* -1 (b-value matrix)) determinant)
		   (/ (* -1 (c-value matrix)) determinant)
		   (/ (a-value matrix) determinant)))))


(define point-add
  (lambda (point1 point2)
    (make-point (+ (x-coordinate point1) (x-coordinate point2))
		(+ (y-coordinate point1) (y-coordinate point2)))))

(define point-subtract
  (lambda (point1 point2)
    (make-point (- (x-coordinate point1) (x-coordinate point2))
		(- (y-coordinate point1) (y-coordinate point2)))))

(define scalar-product
  (lambda (vector1 vector2)
    (+ (* (x-translation vector1) (x-translation vector2))
       (* (y-translation vector1) (y-translation vector2)))))

(define PI 3.14159265358979)

(define RADS-PER-DEGREE
  (/ (* PI) 180))

(define transform
  (lambda (matrix point)
    (make-point (+ (* (x-coordinate point) (a-value matrix))
		   (* (y-coordinate point) (c-value matrix)))
		(+ (* (x-coordinate point) (b-value matrix))
		   (* (y-coordinate point) (d-value matrix))))))

(define translate
  (lambda (vector point)
    (make-point (+ (x-coordinate point) (x-translation vector))
		(+ (y-coordinate point) (y-translation vector)))))

(define enlarge
  (lambda (factor point)
    (make-point (* (x-coordinate point) factor)
		(* (y-coordinate point) factor))))

(define rotate
  (lambda (rads point)
    (transform (make-matrix (cos rads) (sin rads) (- (sin rads)) (cos rads))
	       point)))

(define rotate-degrees
  (lambda (degrees point)
    (rotate (* degrees RADS-PER-DEGREE)
	    point)))

(define reflect
  (lambda (m point)
    (let ((m-vector (make-vector m 1)))
      (point-subtract (enlarge (/ (* 2 (scalar-product point m-vector))
				  (scalar-product m-vector m-vector)) m-vector)
		      point))))

(define perform-on-list
  (lambda (operation arg point-list)
    (if (null? point-list)
	'()
	(cons (operation arg (car point-list))
	      (perform-on-list operation arg (cdr point-list))))))


(define print-point
  (lambda (point)
    (format #t "~S,~S " (x-coordinate point) (y-coordinate point))))

(define print-points
  (lambda (points)
    (if (null? points)
	(newline)
	(begin (print-point (car points))
	       (print-points (cdr points))))))

(define make-intent
  (lambda (func arg)
    (lambda (points)
      (perform-on-list func arg points))))

(define number-pattern "[+-]?[0-9]*\\.?[0-9]+")
(define two-numbers-pattern (string-concatenate (list number-pattern " " number-pattern)))
(define four-numbers-pattern (string-concatenate (list number-pattern
						       " "
						       number-pattern
						       " "
						       number-pattern
						       " "
						       number-pattern)))
(define point-pattern (string-concatenate (list number-pattern "," number-pattern)))
(define points-pattern (string-concatenate (list point-pattern
						       "( "
						       point-pattern
						       ")*")))
						       

(define number-regexp (make-regexp number-pattern))
(define two-numbers-regexp (make-regexp two-numbers-pattern))
(define four-numbers-regexp (make-regexp four-numbers-pattern))
(define points-regexp (make-regexp points-pattern))
(define end-regexp (make-regexp "^end$"))
(define rotate-clockwise-regexp (make-regexp "^rotate [0-9]*.?[0-9]+( clockwise|)$"))
(define rotate-anticlockwise-regexp (make-regexp "^rotate [0-9]*.?[0-9]+ anticlockwise$"))
(define transform-regexp (make-regexp "^transform( [+-]?[0-9]*\\.?[0-9]*){4}$"))
(define translate-regexp (make-regexp "^translate( [+-]?[0-9]*\\.?[0-9]*){2}$"))
(define enlarge-regexp (make-regexp "^enlarge [+-]?[0-9]*\\.?[0-9]*$"))
(define rotate-degrees-clockwise-regexp (make-regexp "^rotate deg [0-9]*.?[0-9]+( clockwise|)$"))
(define rotate-degrees-anticlockwise-regexp (make-regexp "^rotate deg [0-9]*.?[0-9]+ anticlockwise$"))
(define reflect-regexp (make-regexp "^reflect y = [+-]?[0-9]*\\.?[0-9]*x$"))

(define make-check-regexp
  (lambda (regexp)
    (lambda (str)
      (let ((match (regexp-exec regexp str)))
	(if match #t #f)))))

(define is-rotate-clockwise?
  (make-check-regexp rotate-clockwise-regexp))
(define is-rotate-anticlockwise?
  (make-check-regexp rotate-anticlockwise-regexp))
(define is-rotate-degrees-clockwise?
  (make-check-regexp rotate-degrees-clockwise-regexp))
(define is-rotate-degrees-anticlockwise?
  (make-check-regexp rotate-degrees-anticlockwise-regexp))
(define is-enlarge?
  (make-check-regexp enlarge-regexp))
(define is-reflect?
  (make-check-regexp reflect-regexp))

(define is-translate?
  (lambda (str)
    (let ((match (regexp-exec translate-regexp str)))
      (if match #t #f))))

(define is-transform?
  (lambda (str)
    (let ((match (regexp-exec transform-regexp str)))
      (if match #t #f))))

(define get-number
  (lambda (str)
    (string->number (match:substring (regexp-exec number-regexp str)))))

(define get-two-numbers
  (lambda (str)
    (map string->number (string-split (match:substring (regexp-exec two-numbers-regexp str)) #\space))))


(define is-points?
  (make-check-regexp points-regexp))

(define string-comma-split->number
  (lambda (str)
    (map string->number (string-split str #\,))))

(define get-points 
  (lambda (str)
    (map string-comma-split->number
	 (string-split (match:substring (regexp-exec points-regexp str)) #\space))))

      

(define is-transform?
  (lambda (str)
    (let ((match (regexp-exec transform-regexp str)))
      (if match #t #f))))

(define get-four-numbers
  (lambda (str)
    (map string->number (string-split (match:substring (regexp-exec four-numbers-regexp str)) #\space))))



(define is-end?
  (lambda (str)
    (regexp-exec end-regexp str)))


(define get-command-list
  (lambda ()
    (let ((command (read-line)))
      (cond ((is-end? command) '())
	    ((is-rotate-clockwise? command)
	     (cons (make-intent rotate (get-number command)) (get-command-list)))
	    ((is-rotate-anticlockwise? command)
	     (cons (make-intent rotate (* -1 (get-number command))) (get-command-list)))
	    ((is-rotate-degrees-clockwise? command)
	     (cons (make-intent rotate-degrees (get-number command)) (get-command-list)))
	    ((is-rotate-degrees-anticlockwise? command)
	     (cons (make-intent rotate-degrees (* -1 (get-number command))) (get-command-list)))
	    ((is-reflect? command)
	     (cons (make-intent reflect (get-number command)) (get-command-list)))
	    ((is-enlarge? command)
	     (cons (make-intent enlarge (get-number command)) (get-command-list)))
	    ((is-translate? command)
	     (cons (make-intent translate (get-two-numbers command)) (get-command-list)))
	    ((is-transform? command)
	     (cons (make-intent transform (get-four-numbers command)) (get-command-list)))))))

(define command-list (get-command-list))

(define perform 
  (lambda (command-list points)
    (if (null? command-list)
	points
	(perform (cdr command-list) ((car command-list) points)))))

(if (and (not (null? (cdr (command-line))))
	 (equal? "-i" (cadr (command-line))))
    (let ((end-translation (point-subtract (make-point 0 0) (car (perform command-list (get-points "0,0"))))))
      (display end-translation)
      (newline)
      (display (inverse-matrix
		(make-matrix-from-two-points-as-list
		 (perform-on-list 
		  translate
		  end-translation
		  (perform command-list (get-points "1,0 0,1")))))))
			
    (begin
      (define points #f)
      (let ((point-line (read-line)))
	(if (is-points? point-line)
	    (print-points (perform command-list (get-points point-line)))))))

```

---

### Post by dv3500ea on 2010-07-15
Well done, it now seems to work perfectly, though I haven't tested every possible case!

---

### Post by howlingmadhowie on 2010-07-15
question: do you also want it to be able to read commands from a file? that would make measuring speed easier.

at the moment it is however the fastest solution by a wide margin :D

---

### Post by dv3500ea on 2010-07-15
> **howlingmadhowie said:**
> question: do you also want it to be able to read commands from a file? that would make measuring speed easier.

at the moment it is however the fastest solution by a wide margin :D

Not especially, I prefer to create a file and then use the 'cat' command with a pipe to input the commands into the program. (Just because it's simpler). I can then use the 'time' command to compare the speeds of each program processing the same file.

---

### Post by nes1983 on 2010-07-16
**Solution in Newspeak.**

Hi guys, I'd like to show my solution in a [beautiful language called Newspeak]("http://newspeaklanguage.org/"). T[he full source code is available in my snipt-account]("http://snipt.net/nikoschwarz/ubuntu-newbie-challenge-working-part"), including[ a large number of unit tests]("http://snipt.net/nikoschwarz/ubuntu-newbie-challenge-testing-part/"). 

I will show here how to implement one of the commands, namely "transformation," in Newspeak. Let's postpone the parsing for later and begin by implementing a "transformer" that will do the work once the parsing is done. The unit test for that transformer looks as follows. Here, the syntax (2@2) constructs a cartesian point with x-coordinate 2 and y-coordinate 2.

```
testMatrixSet = (
  "Transformer should transform point (1,1) into point (2,2), 
   when set to twice the identity matrix."
  transformer setMatrix: {2 . 0 . 0 . 2}.
  self assert: (transformer transform: (1@1)) = (2@2)
)
```

The above is newspeak syntax for methods. The first line defines the function's name, the rest is the body of the function.

Test driven development and Newspeak are quite compatible. You start by coding the unit test, run it, and of course it will fall apart, because there's no transformer, and there's no method setMatrix:, and so forth. But the Newspeak IDE will ask you to provide each of which, step by step, and that's really how you program most of the time. 

Newspeak already ships with a Matrix class that comes in really handy. In fact, it does most of the computation we need, the only thing it isn't so good at is combining different transformations into one. Here's the transformer class, stripped down to the things needed to make the above unit test happy. I'll explain how it works after the snippet.

```
class Transformer = (
"Accumulates 2D transofrmations, then transforms points according to them."
|
	matrix = MatrixTransform2x3 identity.
|
)

'actions'
compose: aBlock = (
	matrix:: matrix composedWithLocal: (aBlock value: MatrixTransform2x3 identity)
)

setMatrix: anArray = (
	compose: [:mat| 
		mat 
                       a11: anArray first;
		       a12:  anArray second;
		       a21:  anArray third;
		       a22:  anArray fourth]
)

transform: aPoint <Point> = (
	^ matrix transformPoint: aPoint
))
```

How does this work? 
The transformer is completely described by a matrix and a vector, for the transformations can always be described as Ax+b, where A is a 2x2-matrix and b is a 1x2 vector. Now, if you chain several such operations, the resulting transformation can again be described as a transformation of the form Ax+b. (Can you prove that?)

So, all we do in the above snippet is store the current accumulated matrix, called "matrix," and then compose it with the one for the newest transformation. The newest transformation is created as the identity matrix with no offset (MatrixTransform2x3 identity), and then aBlock is asked to modify the matrix into what he sees fit. Blocks in Newspeak are closures, like in Haskell or scheme, or so. Blocks are denoted in square brackets, and we can see the block a few lines below in setMatrix:, which accepts the new matrix under the name of "mat", and then modifies it into representing the argument of the function, "anArray." (Why's there the word MatrixTransform2x3? Well, it's really just a  2x2-matrix and a 1x2 vector. They go and call that 2x3 matrix, which isn't mathematically sound, but rather poor naming. Its purpose, however, is exactly what we want: it computes Ax+b.)

Now, that does the transformation, but how do we parse the input? [Newspeak ships with a beautiful combinatorial parser library. Gilad Bracha wrote a beautiful article on it.]("http://bracha.org/executableGrammars.pdf")

The gist is that Newspeak's syntax lets you represent a grammar very close to BNF, while being fully normal object-oriented code. The resulting parser may not be the fastest in the world, but it's fully object-oriented, and so small that you can step through with a debugger. There's no mystery in what it does. In fact, it's so simple that regular expressions become superfluous in Newspeak: combinatorial parsers can do what they do too, just more easily so.

Making a long story short, here's the definition of the task's grammar, shortened to what is needed to parse the transformation command:

```
class TrafoGrammar= ExecutableGrammar (
"Grammar of the commands for point transformations.
 Also serves a parser parsing that grammar."
|
	digit = charBetween: $0 and: $9.
	transform = tokenFromSymbol: #transform.
	digits = digit plus.
	transformStatement = transform , number , number , number , number.
	number = tokenFor: (digits , (dot , digits) opt).
|
))
```


This may not look like much, but it's already enough to parse the transformation command. Let's unit test that:

```
testParseTransform = (
	| r |
	r:: grammar transformStatement parse: 'transform 1 0 0 1' readStream.
	assert: r size = 5.
	assert: r first token = #transform.
	assert: r last token first first= $1.
)
```

Grammars, apart from being really easy to define in Newspeak, have an important advantage over regular expressions: you get beautiful error messages, including the position of what you did wrong. If you specify only 3 numbers rather than 4, the above parser will automatically inform you that on given location, a number was expected but none provided.

Ok, now all we still need to do is to link our grammar with the transformer we've written earlier. Let's first write a unit test for transformations, parsed out of a command:

```
testTransform = (
	|transformer|
	transformer:: parser transformStatement parse: 'transform 2 0 0 2' readStream.
	assert: (transformer transform: 1@1) = (2@2).
)
```

We achieve that by subclassing the grammar, and hooking callbacks to each production rule that will get our transformer ready as we parse. Here's the parser shortened to what's needed for parsing transformations:

```
class TrafoParser = TrafoGrammar (
     "Parser for the grammar of commands of point transformations.
      Parses a list of commands and returns the Transformer that executes 
      the resulting transformation."

      |transformer|
)
('parsing'
transformStatement = (
	^ super transformStatement wrapper: 
              [:t :a :b :c :d| transformer setMatrix: {a. b. c. d}]
)

number = (
  "Terrible hack to invoke Newspeak's number parser."
	^ super number wrapper: [:n  |
		| stringlike token|
		token:: n token.
		token second ifNotNil: [ 
			stringlike:: token first , ( {token second first} , token second second)] 
			ifNil: [stringlike:: token first].
		 Number readExactlyFrom: stringlike readStream].
)

) : (
'instance creation'
forTransformer: aTransformer = (
	^ self new transformer: aTransformer.
)

))
```

Here, the way I'm dealing with numbers is, of course, terrible. It's so terrible because Newspeak does not bring a combinatorial number parser. There is, of course, a number parser, and you can find it in Number>>readExactlyFrom:. But it doesn't combine well with combinatorial parsers. (Task if you want to learn Newspeak and make yourself popular with the community. Write a combinatorial number parser that would fit into the above snippet. Change Newspeak such that Number>>readExactlyFrom: uses your parser, rather than theirs.)

And that's it. That will parse the transformation statement and fit into the unit test we've provided earlier. [Thanks for reading so far, please check out my blog.]("http://smalltalkthoughts.blogspot.com/")

---

### Post by dv3500ea on 2010-07-17
> **nes1983 said:**
> **Solution in Newspeak.**

Hi guys, I'd like to show my solution in a [beautiful language called Newspeak]("http://newspeaklanguage.org/"). T[he full source code is available in my snipt-account]("http://snipt.net/nikoschwarz/ubuntu-newbie-challenge-working-part"), including[ a large number of unit tests]("http://snipt.net/nikoschwarz/ubuntu-newbie-challenge-testing-part/"). 

It may be a beautiful language but I have no idea how to run your code. There is no package in the repositories that caters for the Newspeak programming language. The download page provides 2 downloads with a combined size of >50MB. The 'starter pack' contains nothing but pdfs, text files and unknown binary files. Also it seems to be released in a confusing array of licences that make me wary of installing it. It's name makes me worry it could be spyware :lol:

> **nes1983 said:**
> 
Newspeak already ships with a Matrix class that comes in really handy. In fact, it does most of the computation we need, the only thing it isn't so good at is combining different transformations into one. 

[LIST=1]
[*]You are not allowed to use any existing Matrix classes that come with the language (such as in ruby). You are expected to provide the matrix logic yourself. Also, you won't need full matrix functionality for this program - just enough to multiply 2x2 matrices by 2x2 matrices or 2x1 matrices.
[*]Combining different transformations into one is as simple as (pre)multiplying the matrices and adding the vectors.
[/LIST]
Basically, my main problem is the language you are using. I think it is good when people use unusual languages but I expect that they be installable via the Ubuntu repositories. Even brainf*ck would be an improvement.

---

### Post by nes1983 on 2010-07-17
> **dv3500ea said:**
> It may be a beautiful language but I have no idea how to run your code.

There's two options. You can compile the virtual machine yourself or you can download the pre-compiled one. [For technically unsavvy users, I recommend downloading the precompiled virtual machine. In fact, I recommend it to everyone. That's a 25 MB download, which is the virtual machine, the IDE, and a rich set of libraries.]("http://newspeaklanguage.org/the-newspeak-programming-language/downloads/")

[To install my code, copy the two files from snipt, make sure their file names end in .ns2.]("http://snipt.net/nikoschwarz/tag/beginner%20programming%20challenge%2014") Now, drag and drop both files into the running IDE window. They will get automatically installed. Then, open the Hopscotch browser, and see the two packages that have just been installed. Enter "TrafoTesting." Right-click on the package and choose "Run unit tests." All should be green.

> **dv3500ea said:**
> 
There is no package in the repositories that caters for the Newspeak programming language.

That's such a pity! You should provide one! :)

> **dv3500ea said:**
> The 'starter pack' contains nothing but pdfs, text files and unknown binary files.

Well, one of the binary files, nsvm, is a linux executable which houses the virtual machine. Just click that. It will ask for the image you want it to run, and there you select ns101.image. That is a memory dump of the running system, which is read into memory directly. That is a great way to start applications, because it is so fast. The complete IDE including the VM starts in under a second on my machine.

> **dv3500ea said:**
> Also it seems to be released in a confusing array of licences that make me wary of installing it. It's name makes me worry it could be spyware :lol:

The naming scheme is just great. The UI framework is called Brazil, the VM is Big Brother, the default image is called 101, and Gilad's blog is "Room 101," and the Newspeak blog is called "3+4." Everybody should have read 1984, by the way. Great literature.

About the licenses: Newspeak is a direct child of Smalltalk, which has a really long history. Some objects in the image have been around since 1980, literally, so some objects living in the ns101 image are older than you. Together with such a long complex history comes a difficult licensing situation, which I'm aware of. Fortunately, all licenses involved are free as in free speech. 

The situation doesn't need to be so complex forever, by the way. The Newspeak community are gradually removing Smalltalk code, and are moving towards the Strongtalk libraries. Once that is completed, all will be available under the MIT license, as is the case already in a similar project named Pharo.

> **dv3500ea said:**
> 
[LIST=1]
[*]You are not allowed to use any existing Matrix classes that come with the language (such as in ruby). You are expected to provide the matrix logic yourself. Also, you won't need full matrix functionality for this program - just enough to multiply 2x2 matrices by 2x2 matrices or 2x1 matrices.
[*]Combining different transformations into one is as simple as (pre)multiplying the matrices and adding the vectors.
[/LIST]


Let me answer that in reverse. My code does exactly what you say: it multiplies the matrices to combine transformations. It ships already with Newspeak, which is nice, but one could as well re-implement the class. The relevant snippet in the Newspeak library is this, which is what it really boils down to:

```

composedWithLocal: aTransformation into: result = (
	"Return the composition of the receiver and the local transformation passed in.
	Store the composed matrix into result."
	| b11 b12 b13 b21 b22 b23 matrix |
	matrix::  aTransformation asMatrixTransform2x3.
	b11:: matrix a11.
	b12:: matrix a12.
	b13:: matrix a13.
	b21:: matrix a21.
	b22:: matrix a22.
	b23:: matrix a23.
	result a11: (a11 * b11) + (a12 * b21).
	result a12: (a11 * b12) + (a12 * b22).
	result a13: a13 + (a11 * b13) + (a12 * b23).
	result a21: (a21 * b11) + (a22 * b21).
	result a22: (a21 * b12) + (a22 * b22).
	result a23: a23 + (a21 * b13) + (a22 * b23).
	^result
)

```

And well, of course one could re-write a class that is already in the system. Just realize that I'm not using a generic Matrix class, I'm using a specialized 2x3 transformation matrix class which does precisely what I'd be implementing myself. 

> 
Basically, my main problem is the language you are using. I think it is good when people use unusual languages but I expect that they be installable via the Ubuntu repositories. Even brainf*ck would be an improvement.

That's a silly thing to say. Newspeak is a research prototype and should be judged as such. It has already been subject of a number of influential publications on language design and IDE design. [It is unusual in that its reach is wider than the usual research community: Even on stackoverflow it was majority-voted to be the best new development tool of 2009]("http://stackoverflow.com/questions/615208/whats-the-best-new-development-tool-of-2009"). But even if Newspeak will never take off in itself, it will certainly have great impact on language research and IDE design.

Newspeak isn't yet ready for real-world programming, most research prototypes never get there. Newspeak is remarkable in how much traction it's already gained already outside of Academia. It might very well become a real-world language soon, and it already is fun and pleasant to work with.

I'm not involved in the project, but I'm a great admirer of Gilad Bracha's and his colleague's work. I think it's a major advance in the field.

---

### Post by dv3500ea on 2010-07-17
My problem is not with the actual language, but with the fact that I can't install it from the repository. It is mainly a security concern - I trust the security of the repositories much more than installing things from websites. Also, the Debian packaging system provides a unified way to manage software which makes it a lot easier. Custom ways of installing software can lead to a mess. There may be an alternative in the repository that you can use. If you go to the software centre or Synaptic and search for squeak you will find a smalltalk implementation.

---

### Post by nes1983 on 2010-07-17
> **dv3500ea said:**
> My problem is not with the actual language, but with the fact that I can't install it from the repository. It is mainly a security concern - I trust the security of the repositories much more than installing things from websites. Also, the Debian packaging system provides a unified way to manage software which makes it a lot easier. Custom ways of installing software can lead to a mess. There may be an alternative in the repository that you can use. If you go to the software centre or Synaptic and search for squeak you will find a smalltalk implementation.

Squeak is quite another system. You aren't seriously proposing that I'll resolve your task because nobody's volunteered to provide an Ubuntu package of Newspeak, are you?

---

### Post by dv3500ea on 2010-07-17
This is a ***Beginner Programming Challenge*** on the ***ubuntu*** forums. It is for people to improve their programming skills using the ***ubuntu platform*** by which I mean *buntu + any programming tools/languages/libraries available from the main, restricted, universe or multiverse repositories. It is up to the Newspeak developers to provide a debian package and ask for it to be added to the ubuntu repositories if they wish to support their language on the Ubuntu platform. The point is that if you develop an application for Ubuntu in a language that requires a custom piece of software to be installed it is difficult for users to use this software. If however, you use an obscure language but it is in the ubuntu repositories, you can create a debian package that depends on that language package so that on installing the package all of the required programming tools are installed without the user having to actively do anything extra.

---

### Post by howlingmadhowie on 2010-07-17
i'm quite happy to take nes's entry as a comment. as dv has pointed out, it isn't quite trivial to get it running on an ubuntu system. but it does contain lots of very interesting ideas, for example creating a grammar to parse the input, which is one of the main differences between his entry and my own.

one of the other differences which may be interesting for any one else who wants to take part is how nes stores the information about translations and reflections and stuff. what i do is store each line inside a function wrapper and create a list of things which take a point as an argument and give a point back as a return value. this means that all the various transformations are stored in my system. nes does this differently by creating a transformation and translation matrix which stores the combined information of all the commands given up to then.

this has the following advantage that after data input, points can be transformed very quickly, but it has the disadvantage that you can't extract out the original commands again (not that that was part of the challenge).

the basic conceptual problem with this challenge as far as i see it is not matrix algebra but how to store information about transformations. the challenge would be a whole lot easier for beginners if the list of points was given first and the transformations came after it. as it is, the challenge requires a bit of thinking around a problem in non-functional languages. 

what i wanted to do, and what i ended up doing, was writing functions (which take a point and a matrix and output a point) and then using schemey functional magic to store these functions with one of their arguments ready to accept a second argument. this struck me as being what i wanted to do as a human---i wanted to store the lines one after the other with all known arguments and create a function stack.

in other, non-functional languages, you'd have to find a different way of doing this. in java you could create an interface and constructors for translation-vectors and rotation-matrixes and stuff.  in fact, i'll do that and post the code.

---

### Post by dv3500ea on 2010-07-17
> **howlingmadhowie said:**
> 
the basic conceptual problem with this challenge as far as i see it is not matrix algebra but how to store information about transformations. the challenge would be a whole lot easier for beginners if the list of points was given first and the transformations came after it. as it is, the challenge requires a bit of thinking around a problem in non-functional languages. 


Well done! You've worked out the most essential design choice of this challenge. When I first thought of this challenge I wanted to do something that required basic matrix arithmetic and the application of matrices to linear transformations. I wanted people to learn: 
[LIST=1
[*]how to add, multiply (2x2, 2x1) and find the inverse (2x2) of matrices
[*]how to apply the linear transformation represented by a matrix to some coordinates
[*]how to represent multiple linear transformations in a single matrix
[*]how to represent rotation/enlargement/reflection as a matrix
[*]how to represent a translation as a vector and apply that to coordinates
[*]how to represent coordinates on a computer screen
[/LIST]
My idea before thinking up the syntax was that a number of linear transformations and translations should be applied to a number of coordinates. My 1st thought of how I would implement this would be to have a working matrix and vector (so 6 numbers in total) that could be applied to each pair of coordinates that was input.
The syntax for specifying the transformations/coordinates followed on logically from this way of thinking. It only occurred to me later that people may try to cache each transformation and apply them 1 by 1.

@nes1983 I hope you aren't too offended about what I have said. I don't think I got this across properly but I am glad you have posted your implementation - it is good as an example for others (as proven here). However, I won't be considering it as an entry to the challenge due to the lack of a reliable way to run it. I consider your program as an example to help people who may be struggling with writing their own entry.

---

### Post by Copernicus1234 on 2010-07-18
I saw the math and fell asleep. Bueller? Bueller? Bueller?

I belong to the apparently few who enjoy programming but not math.

Both math and programming is problem solving, but for me, one is fun and the other is not.

But ignore this post, fellow problem solvers.... go on with the math quest. :)

---

### Post by fallenshadow on 2010-07-18
> I saw the math and fell asleep. Bueller? Bueller? Bueller?

I belong to the apparently few who enjoy programming but not math.

Both math and programming is problem solving, but for me, one is fun and the other is not.

But ignore this post, fellow problem solvers.... go on with the math quest.

You seem to be the same as me then... I started reading this out of interest and then slowly my eyelids started to close! :D

---

### Post by km0r3 on 2010-07-19
> Code:
```
enlarge $scale_factor$
-> enlarge by scale factor scale_factor about the origin
```

I guess it would be less confusing calling the function "scale" instead of "enlarge", because *scale_factor* can be a value between 0 and 1 and above.

---

### Post by dv3500ea on 2010-07-19
> **km0r3 said:**
> I guess it would be less confusing calling the function "scale" instead of "enlarge", because *scale_factor* can be a value between 0 and 1 and above.

Yeah, you're probably right. Its just we've always called it enlargement at school (even when its decreasing in size). That always made us laugh. It's a bit late to change it now though.

Scale factor can also be negative (which acts like a reflection and another enlargement).

On a tenuously linked topic, if the -i flag is given and one of the transformations is enlarge 0 (or transform 0 0 0 0), an error should be given because its impossible to find the inverse of this transformation. Reminds me of a black hole...

---

### Post by howlingmadhowie on 2010-07-20
> **dv3500ea said:**
> 
Scale factor can also be negative (which acts like a reflection through y=-1x and another enlargement).


a small correction. consider the point [-1, 1], which lies on the line y=-x, and so would not be affected by a reflection through y=-1x. multiplied by a scale of -1 this point becomes [1, -1].

a scale of -1 is the matrix 
```

[ -1   0 ]
[  0  -1 ]

```

while a reflection in y=-x is the matrix
```

[  0  -1 ]
[ -1   0 ]

```

---

### Post by dv3500ea on 2010-07-20
Yeah, I made a mistake.
The reflection that is equivalent to a scale of -1 actually depends on where the point is on the graph.

---

### Post by dv3500ea on 2010-07-20
I received a private message asking for help put couldn't seem to send a reply so I will answer it here.

The message was something like this
> 
I have a question: Is the matrix a 2x2 matrix or a 4x4 matrix?

In Game Programming books they represent a 3D Matrix like this:

```

x axis(right)----------->|1 0 0| |0|
Y axis(up)-------------->|0 1 0| |0|
Z axis(heading)--------->|0 0 1| |0|
Translation------------->|0 0 0| |1|

```

This is a little confusing, and I have looked up a lot on Google, and still I cannot answer the question, so I contacted you directly.


I'm not really sure what this book is meaning but it is trying to represent 3D whereas we are dealing with 2D.

Transformation matrices for 2D are 2x2 matrices. Translations are 2x1 matrices and coordinates are also represented as 2x1 matrices. (2x1 means 2 rows, 1 column)

To transform some coordinates (2,-1) by a matrix 
|1 0|
|0 1|
and translate by
|0|
|0|
you need to calculate

```

|1 0| * |2 | + |0| = |2 |
|0 1|   |-1|   |0|   |-1|

```

(these transformations/translations are special because they don't affect the position of the coordinates)

I hope that helps. Please ask on this thread for any other help because I can't get my PM replies to send and this way benefits everyone else too.

---

### Post by nes1983 on 2010-07-22
> **dv3500ea said:**
> 
On a tenuously linked topic, if the -i flag is given and one of the transformations is enlarge 0 (or transform 0 0 0 0), an error should be given because its impossible to find the inverse of this transformation. Reminds me of a black hole...

I don't see why you'd ever need to compute the inverse matrix to solve this task.

---

### Post by dv3500ea on 2010-07-22
> **nes1983 said:**
> I don't see why you'd ever need to compute the inverse matrix to solve this task.

To calculate the matrix that represents the reverse transformation, you need to calculate the inverse of the matrix representing the combination of all the transformations done.

If you think about it, ```
transform 0 0 0 0
``` transforms every pair of coordinates to (0, 0) therefore it is impossible to know how to transform back to the point you got.

In fact, you can't find the inverse of any matrix where the [determinant]("http://en.wikipedia.org/wiki/Determinant") == 0 because finding the inverse depends on 1/determinant.

That means that certain patterns of matrices can't be inverted, such as:
|x, x|
|x, x|
or
|x, y|
|x, y|

Most programs will throw a div/0 error anyway and this is only a consideration when the program implements the -i flag.

---

### Post by nes1983 on 2010-07-23
> **dv3500ea said:**
> To calculate the matrix that represents the reverse transformation, you need to calculate the inverse of the matrix representing the combination of all the transformations done.

Ahh, it's for the extension track, with the -i flag.

---

### Post by schauerlich on 2010-07-25
Will this be judged sometime soon? (waiting for #15...)

---

### Post by dv3500ea on 2010-07-26
> **schauerlich said:**
> Will this be judged sometime soon? (waiting for #15...)

I'll wait until Saturday in case anyone else creates an entry. I was hoping that more people would take part but apparently the maths is 'too boring' for them :(

---

### Post by sharpdust on 2010-07-27
Here is my solution in ruby: 

```
#!/usr/bin/env ruby

transformations = STDIN.gets('end')

STDIN.gets # call gets again since STDIN still has a newline in it.

coordinates = STDIN.gets

coordinates = coordinates.split
coordinates.map! {|coord| coord.split(',').map!{|point| point.to_f}}

transformations.each do |line|
  command, vars = line.strip.split[0], line.strip.split[1..-1]
  case command

    # transform a b c d
    # x' = x*a + y*c
    # y' = x*b + y*d
    when 'transform'
      a, b, c, d = vars[0].to_i, vars[1].to_i, vars[2].to_i, vars[3].to_i
      coordinates = coordinates.each do |coord|
        temp_x = coord[0]
        coord[0] = (coord[0] * a) + (coord[1] * c)
        coord[1] = (temp_x   * b) + (coord[1] * d)
      end

    # translate X Y
    # x' = x + X
    # x' = y + Y
    when 'translate'
      big_x = vars[0].to_i
      big_y = vars[1].to_i
      coordinates = coordinates.each do |coord|
        coord[0] += big_x
        coord[1] += big_y
      end

    # enlarge scale_factor
    # x' = scale_factor * x
    # y' = scale_factor * y
    when 'enlarge'
      scale_factor = vars[0].to_f
      coordinates.map{|coord| coord.map!{|point| point *= scale_factor}}

    # rotate angle_in_rads clockwise
    # rotate angle_in_rads anticlockwise
    # rotate deg angle_in_degs clockwise
    # rotate deg angle_in_degs anticlockwise
    #
    # anticlockwise
    # x' = x*cos(angle) - y*sin(angle)
    # y' = x*sin(angle) + y*cos(angle)
    #
    # clockwise
    # x' =  x*cos(angle) + y*sin(angle)
    # y' = -x*sin(angle) + y*cos(angle)
    when 'rotate'
      if vars[0] == 'deg' then
        angle     = vars[1].to_f * Math::PI / 180 # convert to radians
        direction = vars[2]
      else
        angle     = vars[0].to_f
        direction = vars[1]
      end

      if direction == 'anticlockwise' then
        coordinates = coordinates.each do |coord|
          x = coord[0]
          y = coord[1]
          coord[0] = (x * Math.cos(angle)) - (y * Math.sin(angle))
          coord[1] = (x * Math.sin(angle)) + (y * Math.cos(angle))
        end
      elsif direction == 'clockwise' then
        coordinates = coordinates.each do |coord|
          x = coord[0]
          y = coord[1]
          coord[0] =  (x * Math.cos(angle))      + (y * Math.sin(angle))
          coord[1] =  (-1 * x * Math.sin(angle)) + (y * Math.cos(angle))
        end
      end

    # reflect y = mx
    # d = (x + y*m)/(1 + m^2)
    # x' = 2*d - x
    # y' = 2*d*m - y
    when 'reflect'
      m = vars[2][0..0].to_f
      coordinates = coordinates.each do |coord|
        d = (coord[0] + coord[1] * m) / (1 + m**2)
        coord[0] = (2 * d) - coord[0]
        coord[1] = (2 * d * m) - coord[1]
      end
  end
end

puts coordinates.inspect
```

---

### Post by dv3500ea on 2010-07-27
> **sharpdust said:**
> Here is my solution in ruby: 

```
...
```

Well done, that's certainly a good start. I especially like your use of white space and comments, it makes it very readable.

You have made a mistake with the transformation by a matrix:
You have:
```

x' = ax + cy
y' = bx + dy

```
but it should be
```

x' = ax + by
y' = cx + dy

```

Also, you could simplify your code by using functions. Enlargement, rotation and reflection can all be represented as a transformation by a matrix. Also, all rotations could be represented as a rotation anticlockwise in radians.
```

enlarge sf == transform sf 0 0 sf
rotate a anticlockwise == transform cos(a) -sin(a) sin(a) cos(a)
#a is in rads
reflect y=mx == transform cos(2atan(m)) sin(2atan(m)) sin(2atan(m)) -cos(2atan(m))

```

---

### Post by howlingmadhowie on 2010-07-27
hello again :)

here's a shortish solution in C. it's been a while since i've done any C programming, and i haven't freed every malloc, so it's a bit of a work in progress.

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>

#define RAD_PER_DEG (3.14159/180)

typedef struct _matrix {
  float x1;
  float x2;
  float y1;
  float y2;
} matrix;

typedef struct _point {
  float x;
  float y;
} point;

typedef struct _list {
  point *p;
  struct _list *next;
} list;

typedef struct _translation {
  float x;
  float y;
} translation;

typedef struct _combination {
  matrix *m;
  translation *t;
} combination;

matrix *getMatrix() {
  matrix *m;
  m=malloc(sizeof(matrix));
  m->x1=1;
  m->x2=0;
  m->y1=0;
  m->y2=1;
  return m;
}

combination *getCombination() {
  combination *c;
  c=malloc(sizeof(combination));
  c->m=getMatrix();
  c->t=malloc(sizeof(translation));
  c->t->x=0;
  c->t->y=0;
  return c;
}

combination *copyCombination(combination *c) {
  combination *newc=getCombination();
  newc->m->x1=c->m->x1;
  newc->m->x2=c->m->x2;
  newc->m->y1=c->m->y1;
  newc->m->y2=c->m->y2;
  newc->t->x=c->t->x;
  newc->t->y=c->t->y;
  return newc;
}

point *copyPoint(point *p) {
  point *newp=malloc(sizeof(point));
  newp->x=p->x;
  newp->y=p->y;
  return newp;
}

void printMatrix(matrix *m) {
  printf("[ %f, %f ]\n", m->x1, m->x2);
  printf("[ %f, %f ]\n", m->y1, m->y2);
}

void printCombination(combination *c) {
  printf("[ %f, %f ]     [ %f ]\n", c->m->x1, c->m->x2, c->t->x);
  printf("[                    ]  +  [    ]\n");
  printf("[ %f, %f ]     [ %f ]\n", c->m->y1, c->m->y2, c->t->y);
}


void translate(translation *t, combination *c) {
  c->t->x+=t->x;
  c->t->y+=t->y;
}

void multiply(matrix *m, combination *c) {
  combination *cc=copyCombination(c);
  c->m->x1 = m->x1 * cc->m->x1 + m->x2 * cc->m->y1;
  c->m->x2 = m->x1 * cc->m->x2 + m->x2 * cc->m->y2;
  c->m->y1 = m->y1 * cc->m->x1 + m->y2 * cc->m->y1;
  c->m->y2 = m->y1 * cc->m->x2 + m->y2 * cc->m->y2;

  c->t->x = m->x1 * cc->t->x + m->x2 * cc->t->y;
  c->t->y = m->y1 * cc->t->x + m->y2 * cc->t->y;
  free(cc);
}

void rotate(float rad, combination *c) {
  matrix *rotation;
  rotation=getMatrix();
  rotation->x1=cos(rad);
  rotation->x2=-sin(rad);
  rotation->y1=sin(rad);
  rotation->y2=cos(rad);
  multiply(rotation, c);
  free(rotation);
}

void reflect(float m, combination *c) {
  matrix *kronecker;
  point *vector;
  matrix *reflection;
  float sizesquared;
  kronecker=getMatrix();
  reflection=getMatrix();
  vector=malloc(sizeof(point));
  vector->x=m;
  vector->y=-1;
  sizesquared=m*m + 1;
  reflection->x1=kronecker->x1 - 2*(vector->x * vector->x)/sizesquared;
  reflection->x2=kronecker->x2 - 2*(vector->x * vector->y)/sizesquared;
  reflection->y1=kronecker->y1 - 2*(vector->y * vector->x)/sizesquared;
  reflection->y2=kronecker->y2 - 2*(vector->y * vector->y)/sizesquared;
  multiply(reflection, c);
  free(kronecker); free(reflection); free(vector);
}

void enlarge(float factor, combination *c) {
  matrix *enlargement;
  enlargement=getMatrix();
  enlargement->x1=factor;
  enlargement->y2=factor;
  multiply(enlargement, c);
  free(enlargement);
}

void rotateDegrees(float deg, combination *c) {
  rotate(deg*RAD_PER_DEG, c);
}

void transformPoint(point *p, combination *c) {
  point *cp=copyPoint(p);
  p->x=c->m->x1 * cp->x + c->m->x2 * cp->y + c->t->x;
  p->y=c->m->y1 * cp->x + c->m->y2 * cp->y + c->t->y;
  free(cp);
}

void transformPointList(list *pointlist, combination *c) {
  transformPoint(pointlist->p, c);
  if(pointlist->next!=NULL)
    transformPointList(pointlist->next, c);
}

void printPoints(list *pointlist) {
  point *p;
  p=pointlist->p;
  printf("%f,%f ", p->x, p->y);
  if(pointlist->next==NULL) {
    printf("\n");
  } else {
    printPoints(pointlist->next);
  }
}

int getPointstring(char *longstring, char *outputstring) {
  char ch;
  int i, finished=0;
  for(i=0; ; i++) {
    if(longstring[i]==' ') break;
    if(longstring[i]=='\0') {
      finished=1;
      break;
    }
    outputstring[i]=longstring[i];
    }
  outputstring[i]='\0';
  if(finished) return 0;
  return i+1;
}

void getPointList(list *pointlist, char *str) {
  list *l;
  point *p;
  int next;
  char buffer[20];
  
  p=malloc(sizeof(point));
  next=getPointstring(str, buffer);
  sscanf(buffer, "%f,%f", &(p->x), &(p->y));
  
  if(next==0) {
    pointlist->p=p;
    pointlist->next=NULL;
  } else {
    l=malloc(sizeof(list));
    pointlist->p=p;
    pointlist->next=l;
    getPointList(pointlist->next, &str[next]);
  }
}

int main(int argc, char **argv) {
  combination *c;
  translation *t;
  matrix *m;
  list *pointlist;
  char buffer[40]={0};
  float f;
  m=getMatrix();
  t=malloc(sizeof(translation));

  pointlist=malloc(sizeof(list));

  c=getCombination();

  while(1) {
    fgets(buffer, 39, stdin);
    if(strstr(buffer, "end")!=NULL)
      break;
    if(strstr(buffer, "transform")!=NULL) {
      sscanf(buffer, "transform %f %f %f %f", &(m->x1), &(m->x2), &(m->y1), &(m->y2));
      multiply(m, c);
      continue;
    }
    if(strstr(buffer, "rotate deg")!=NULL) {
      if(strstr(buffer, "anticlockwise")!=NULL) {
	sscanf(buffer, "rotate deg %f", &f);
	rotateDegrees(-f, c);
	continue;
      } else {
	sscanf(buffer, "rotate deg %f", &f);
	rotateDegrees(f, c);
	continue;
      }
    }
    if(strstr(buffer, "rotate")!=NULL) {
      if(strstr(buffer, "anticlockwise")!=NULL) {
	sscanf(buffer, "rotate %f", &f);
	rotate(-f, c);
	continue;
      } else {
	sscanf(buffer, "rotate %f", &f);
	rotate(f, c);
	continue;
      }
    }
    if(strstr(buffer, "enlarge")!=NULL) {
      sscanf(buffer, "enlarge %f", &f);
      enlarge(f, c);
      continue;
    }
    if(strstr(buffer, "reflect")!=NULL) {
      sscanf(buffer, "reflect y = %fx", &f);
      reflect(f, c);
      continue;
    }
  }

  fgets(buffer, 39, stdin);

  //  printCombination(c);
  getPointList(pointlist, buffer);
  //  printPoints(pointlist);
  transformPointList(pointlist, c);
  printPoints(pointlist);


  free(c->t);
  free(c->m);

  return 0;
}

```
it can be compiled with:
```

gcc file.c -lm -o somename

```
and then run with:
```

./somename

```

i may complete it before breakfast tomorrow :)

---

### Post by howlingmadhowie on 2010-07-28
okay, i've now checked it with valgrind and freed all the mallocs :)

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>

#define RAD_PER_DEG (M_PI/180)

typedef struct _matrix {
  float x1;
  float x2;
  float y1;
  float y2;
} matrix;

typedef struct _point {
  float x;
  float y;
} point;

typedef struct _list {
  point *p;
  struct _list *next;
} list;

typedef struct _translation {
  float x;
  float y;
} translation;

typedef struct _combination {
  matrix *m;
  translation *t;
} combination;

matrix *getMatrix() {
  matrix *m;
  m=malloc(sizeof(matrix));
  m->x1=1;
  m->x2=0;
  m->y1=0;
  m->y2=1;
  return m;
}

combination *getCombination() {
  combination *c;
  c=malloc(sizeof(combination));
  c->m=getMatrix();
  c->t=malloc(sizeof(translation));
  c->t->x=0;
  c->t->y=0;
  return c;
}

void freeCombination(combination *c) {
  free(c->m);
  free(c->t);
  free(c);
}

combination *copyCombination(combination *c) {
  combination *newc=getCombination();
  newc->m->x1=c->m->x1;
  newc->m->x2=c->m->x2;
  newc->m->y1=c->m->y1;
  newc->m->y2=c->m->y2;
  newc->t->x=c->t->x;
  newc->t->y=c->t->y;
  return newc;
}

point *copyPoint(point *p) {
  point *newp=malloc(sizeof(point));
  newp->x=p->x;
  newp->y=p->y;
  return newp;
}

void printMatrix(matrix *m) {
  printf("[ %f, %f ]\n", m->x1, m->x2);
  printf("[ %f, %f ]\n", m->y1, m->y2);
}

void printCombination(combination *c) {
  printf("[ %f, %f ]     [ %f ]\n", c->m->x1, c->m->x2, c->t->x);
  printf("[                    ]  +  [    ]\n");
  printf("[ %f, %f ]     [ %f ]\n", c->m->y1, c->m->y2, c->t->y);
}


void translate(translation *t, combination *c) {
  c->t->x+=t->x;
  c->t->y+=t->y;
}

void multiply(matrix *m, combination *c) {
  combination *cc=copyCombination(c);
  c->m->x1 = m->x1 * cc->m->x1 + m->x2 * cc->m->y1;
  c->m->x2 = m->x1 * cc->m->x2 + m->x2 * cc->m->y2;
  c->m->y1 = m->y1 * cc->m->x1 + m->y2 * cc->m->y1;
  c->m->y2 = m->y1 * cc->m->x2 + m->y2 * cc->m->y2;

  c->t->x = m->x1 * cc->t->x + m->x2 * cc->t->y;
  c->t->y = m->y1 * cc->t->x + m->y2 * cc->t->y;
  freeCombination(cc);
}

void rotate(float rad, combination *c) {
  matrix *rotation;
  rotation=getMatrix();
  rotation->x1=cos(rad);
  rotation->x2=-sin(rad);
  rotation->y1=sin(rad);
  rotation->y2=cos(rad);
  multiply(rotation, c);
  free(rotation);
}

void reflect(float m, combination *c) {
  matrix *kronecker;
  point *vector;
  matrix *reflection;
  float sizesquared;
  kronecker=getMatrix();
  reflection=getMatrix();
  vector=malloc(sizeof(point));
  vector->x=m;
  vector->y=-1;
  sizesquared=m*m + 1;
  reflection->x1=kronecker->x1 - 2*(vector->x * vector->x)/sizesquared;
  reflection->x2=kronecker->x2 - 2*(vector->x * vector->y)/sizesquared;
  reflection->y1=kronecker->y1 - 2*(vector->y * vector->x)/sizesquared;
  reflection->y2=kronecker->y2 - 2*(vector->y * vector->y)/sizesquared;
  multiply(reflection, c);
  free(kronecker); free(reflection); free(vector);
}

void enlarge(float factor, combination *c) {
  matrix *enlargement;
  enlargement=getMatrix();
  enlargement->x1=factor;
  enlargement->y2=factor;
  multiply(enlargement, c);
  free(enlargement);
}

void rotateDegrees(float deg, combination *c) {
  rotate(deg*RAD_PER_DEG, c);
}

void transformPoint(point *p, combination *c) {
  point *cp=copyPoint(p);
  p->x=c->m->x1 * cp->x + c->m->x2 * cp->y + c->t->x;
  p->y=c->m->y1 * cp->x + c->m->y2 * cp->y + c->t->y;
  free(cp);
}

void transformPointList(list *pointlist, combination *c) {
  transformPoint(pointlist->p, c);
  if(pointlist->next!=NULL)
    transformPointList(pointlist->next, c);
}

void freePoints(list *pointlist) {
  list *nextpoint;
  free(pointlist->p);
  if(pointlist->next!=NULL) {
    nextpoint=pointlist->next;
    free(pointlist);
    freePoints(nextpoint);
  } else {
    free(pointlist);
  }
}

void printPoints(list *pointlist) {
  point *p;
  p=pointlist->p;
  printf("%g,%g ", p->x, p->y);
  if(pointlist->next==NULL) {
    printf("\n");
  } else {
    printPoints(pointlist->next);
  }
}

int getPointstring(char *longstring, char *outputstring) {
  int i, finished=0;
  for(i=0; ; i++) {
    if(longstring[i]==' ') break;
    if(longstring[i]=='\0') {
      finished=1;
      break;
    }
    outputstring[i]=longstring[i];
    }
  outputstring[i]='\0';
  if(finished) return 0;
  return i+1;
}

void getPointList(list *pointlist, char *str) {
  list *l;
  point *p;
  int next;
  char buffer[20];
  
  p=malloc(sizeof(point));
  next=getPointstring(str, buffer);
  sscanf(buffer, "%f,%f", &(p->x), &(p->y));
  
  if(next==0) {
    pointlist->p=p;
    pointlist->next=NULL;
  } else {
    l=malloc(sizeof(list));
    pointlist->p=p;
    pointlist->next=l;
    getPointList(pointlist->next, &str[next]);
  }
}

int main(int argc, char **argv) {
  combination *c;
  translation *t;
  matrix *m;
  list *pointlist;
  char buffer[40]={0};
  float f;
  m=getMatrix();
  t=malloc(sizeof(translation));

  pointlist=malloc(sizeof(list));

  c=getCombination();

  while(1) {
    fgets(buffer, 39, stdin);
    if(strstr(buffer, "end")!=NULL)
      break;
    if(strstr(buffer, "transform")!=NULL) {
      sscanf(buffer, "transform %f %f %f %f", &(m->x1), &(m->x2), &(m->y1), &(m->y2));
      multiply(m, c);
      continue;
    }
    if(strstr(buffer, "rotate deg")!=NULL) {
      if(strstr(buffer, "anticlockwise")!=NULL) {
	sscanf(buffer, "rotate deg %f", &f);
	rotateDegrees(-f, c);
	continue;
      } else {
	sscanf(buffer, "rotate deg %f", &f);
	rotateDegrees(f, c);
	continue;
      }
    }
    if(strstr(buffer, "rotate")!=NULL) {
      if(strstr(buffer, "anticlockwise")!=NULL) {
	sscanf(buffer, "rotate %f", &f);
	rotate(-f, c);
	continue;
      } else {
	sscanf(buffer, "rotate %f", &f);
	rotate(f, c);
	continue;
      }
    }
    if(strstr(buffer, "enlarge")!=NULL) {
      sscanf(buffer, "enlarge %f", &f);
      enlarge(f, c);
      continue;
    }
    if(strstr(buffer, "reflect")!=NULL) {
      sscanf(buffer, "reflect y = %fx", &f);
      reflect(f, c);
      continue;
    }
  }

  fgets(buffer, 39, stdin);

  getPointList(pointlist, buffer);
  transformPointList(pointlist, c);
  printPoints(pointlist);

  free(t);
  free(m);
  freeCombination(c);
  freePoints(pointlist);

  return 0;
}

```

it can be run by doing:
```

sudo apt-get install build-essential
gcc -lm program.c -o binary_name
./binary_name

```

if you want to check it for memory leaks, you can do this by running:
```

sudo apt-get install valgrind
gcc program.c -Wall -g -lm -o binary_name
valgrind --leak-check=yes ./binary_name

```

---

### Post by sharpdust on 2010-07-28
> **dv3500ea said:**
> Well done, that's certainly a good start. I especially like your use of white space and comments, it makes it very readable.

You have made a mistake with the transformation by a matrix:
You have:
```

x' = ax + cy
y' = bx + dy

```
but it should be
```

x' = ax + by
y' = cx + dy

```

Also, you could simplify your code by using functions. Enlargement, rotation and reflection can all be represented as a transformation by a matrix. Also, all rotations could be represented as a rotation anticlockwise in radians.
```

enlarge sf == transform sf 0 0 sf
rotate a anticlockwise == transform cos(a) -sin(a) sin(a) cos(a)
#a is in rads
reflect y=mx == transform cos(2atan(m)) sin(2atan(m)) sin(2atan(m)) -cos(2atan(m))

```


Thanks. I've never taken linear algebra before so I was going just based on geometry.

Here is the improved version. The case/when statement could be replaced with [Object.send]("http://ruby-doc.org/core/classes/Object.html#M000332"), but I figured that would make it too confusing.

```
#!/usr/bin/env ruby

# transform a b c d
# x' = ax + by
# y' = cx + dy
def transform(x, y, vars)
  a, b, c, d = vars[0].to_f, vars[1].to_f, vars[2].to_f, vars[3].to_f
  x = a*x + b*y
  y = c*x + d*y
  return x, y
end

# translate X Y
# x' = x + X
# y' = y + Y
def translate(x, y, vars)
  big_x, big_y = vars[0].to_f, vars[1].to_f
  x += big_x
  y += big_y
  return x, y
end

# enlarge scale_factor
# x', y' = transform scale_factor, 0, 0, scale_factor
def enlarge(x, y, vars)
  scale_factor = vars[0].to_f
  x, y = transform(x, y, [scale_factor, 0, 0, scale_factor])
  return x, y
end

# rotate angle_in_rads clockwise
# rotate angle_in_rads anticlockwise
# rotate deg angle_in_degs clockwise
# rotate deg angle_in_degs anticlockwise
# x', y' = transform cos(angle), -sin(angle), sin(angle), cos(angle)
def rotate(x, y, vars)
  if vars[0] == 'deg' then
    angle     = vars[1].to_f * Math::PI / 180 # convert to radians
    direction = vars[2]
  else 
    angle     = vars[0].to_f
    direction = vars[1]
  end
  
  angle = -angle if direction == 'clockwise'

  x, y = transform(x, y, [Math.cos(angle), -(Math.sin(angle)),
                          Math.sin(angle),   Math.cos(angle)])
  return x, y
end

# reflect y = mx
# x', y' = transform cos(2atan(m)) sin(2atan(m)) sin(2atan(m)) -cos(2atan(m))
def reflect(x, y, vars)
  m = vars[2][0..0].to_f
  x, y = transform(x, y, [Math.cos(2 * Math.atan(m)),  Math.sin(2 * Math.atan(m)),
                          Math.sin(2 * Math.atan(m)), -Math.cos(2 * Math.atan(m))])
  return x, y
end

##################################
# Grab user input
# ################################
transformations = STDIN.gets('end')

STDIN.gets # call gets again since STDIN still has a newline in it.

coordinates = STDIN.gets

coordinates = coordinates.split
coordinates.map! {|coord| coord.split(',').map!{|point| point.to_f}}

transformations.each do |line|
  command, vars = line.strip.split[0], line.strip.split[1..-1]

  coordinates = coordinates.each do |coord|
    case command
       when 'transform' then coord[0], coord[1] = transform(coord[0], coord[1], vars)
       when 'translate' then coord[0], coord[1] = translate(coord[0], coord[1], vars)
       when 'enlarge'   then coord[0], coord[1] =   enlarge(coord[0], coord[1], vars)
       when 'rotate'    then coord[0], coord[1] =    rotate(coord[0], coord[1], vars)
       when 'reflect'   then coord[0], coord[1] =   reflect(coord[0], coord[1], vars)
    end
  end
end

puts coordinates.inspect
```

---

### Post by sharpdust on 2010-07-28
> **howlingmadhowie said:**
> okay, i've now checked it with valgrind and freed all the mallocs :)

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>

#define RAD_PER_DEG (M_PI/180)

typedef struct _matrix {
  float x1;
  float x2;
  float y1;
  float y2;
} matrix;

typedef struct _point {
  float x;
  float y;
} point;

typedef struct _list {
  point *p;
  struct _list *next;
} list;

typedef struct _translation {
  float x;
  float y;
} translation;

typedef struct _combination {
  matrix *m;
  translation *t;
} combination;

matrix *getMatrix() {
  matrix *m;
  m=malloc(sizeof(matrix));
  m->x1=1;
  m->x2=0;
  m->y1=0;
  m->y2=1;
  return m;
}

combination *getCombination() {
  combination *c;
  c=malloc(sizeof(combination));
  c->m=getMatrix();
  c->t=malloc(sizeof(translation));
  c->t->x=0;
  c->t->y=0;
  return c;
}

void freeCombination(combination *c) {
  free(c->m);
  free(c->t);
  free(c);
}

combination *copyCombination(combination *c) {
  combination *newc=getCombination();
  newc->m->x1=c->m->x1;
  newc->m->x2=c->m->x2;
  newc->m->y1=c->m->y1;
  newc->m->y2=c->m->y2;
  newc->t->x=c->t->x;
  newc->t->y=c->t->y;
  return newc;
}

point *copyPoint(point *p) {
  point *newp=malloc(sizeof(point));
  newp->x=p->x;
  newp->y=p->y;
  return newp;
}

void printMatrix(matrix *m) {
  printf("[ %f, %f ]\n", m->x1, m->x2);
  printf("[ %f, %f ]\n", m->y1, m->y2);
}

void printCombination(combination *c) {
  printf("[ %f, %f ]     [ %f ]\n", c->m->x1, c->m->x2, c->t->x);
  printf("[                    ]  +  [    ]\n");
  printf("[ %f, %f ]     [ %f ]\n", c->m->y1, c->m->y2, c->t->y);
}


void translate(translation *t, combination *c) {
  c->t->x+=t->x;
  c->t->y+=t->y;
}

void multiply(matrix *m, combination *c) {
  combination *cc=copyCombination(c);
  c->m->x1 = m->x1 * cc->m->x1 + m->x2 * cc->m->y1;
  c->m->x2 = m->x1 * cc->m->x2 + m->x2 * cc->m->y2;
  c->m->y1 = m->y1 * cc->m->x1 + m->y2 * cc->m->y1;
  c->m->y2 = m->y1 * cc->m->x2 + m->y2 * cc->m->y2;

  c->t->x = m->x1 * cc->t->x + m->x2 * cc->t->y;
  c->t->y = m->y1 * cc->t->x + m->y2 * cc->t->y;
  freeCombination(cc);
}

void rotate(float rad, combination *c) {
  matrix *rotation;
  rotation=getMatrix();
  rotation->x1=cos(rad);
  rotation->x2=-sin(rad);
  rotation->y1=sin(rad);
  rotation->y2=cos(rad);
  multiply(rotation, c);
  free(rotation);
}

void reflect(float m, combination *c) {
  matrix *kronecker;
  point *vector;
  matrix *reflection;
  float sizesquared;
  kronecker=getMatrix();
  reflection=getMatrix();
  vector=malloc(sizeof(point));
  vector->x=m;
  vector->y=-1;
  sizesquared=m*m + 1;
  reflection->x1=kronecker->x1 - 2*(vector->x * vector->x)/sizesquared;
  reflection->x2=kronecker->x2 - 2*(vector->x * vector->y)/sizesquared;
  reflection->y1=kronecker->y1 - 2*(vector->y * vector->x)/sizesquared;
  reflection->y2=kronecker->y2 - 2*(vector->y * vector->y)/sizesquared;
  multiply(reflection, c);
  free(kronecker); free(reflection); free(vector);
}

void enlarge(float factor, combination *c) {
  matrix *enlargement;
  enlargement=getMatrix();
  enlargement->x1=factor;
  enlargement->y2=factor;
  multiply(enlargement, c);
  free(enlargement);
}

void rotateDegrees(float deg, combination *c) {
  rotate(deg*RAD_PER_DEG, c);
}

void transformPoint(point *p, combination *c) {
  point *cp=copyPoint(p);
  p->x=c->m->x1 * cp->x + c->m->x2 * cp->y + c->t->x;
  p->y=c->m->y1 * cp->x + c->m->y2 * cp->y + c->t->y;
  free(cp);
}

void transformPointList(list *pointlist, combination *c) {
  transformPoint(pointlist->p, c);
  if(pointlist->next!=NULL)
    transformPointList(pointlist->next, c);
}

void freePoints(list *pointlist) {
  list *nextpoint;
  free(pointlist->p);
  if(pointlist->next!=NULL) {
    nextpoint=pointlist->next;
    free(pointlist);
    freePoints(nextpoint);
  } else {
    free(pointlist);
  }
}

void printPoints(list *pointlist) {
  point *p;
  p=pointlist->p;
  printf("%g,%g ", p->x, p->y);
  if(pointlist->next==NULL) {
    printf("\n");
  } else {
    printPoints(pointlist->next);
  }
}

int getPointstring(char *longstring, char *outputstring) {
  int i, finished=0;
  for(i=0; ; i++) {
    if(longstring[i]==' ') break;
    if(longstring[i]=='\0') {
      finished=1;
      break;
    }
    outputstring[i]=longstring[i];
    }
  outputstring[i]='\0';
  if(finished) return 0;
  return i+1;
}

void getPointList(list *pointlist, char *str) {
  list *l;
  point *p;
  int next;
  char buffer[20];
  
  p=malloc(sizeof(point));
  next=getPointstring(str, buffer);
  sscanf(buffer, "%f,%f", &(p->x), &(p->y));
  
  if(next==0) {
    pointlist->p=p;
    pointlist->next=NULL;
  } else {
    l=malloc(sizeof(list));
    pointlist->p=p;
    pointlist->next=l;
    getPointList(pointlist->next, &str[next]);
  }
}

int main(int argc, char **argv) {
  combination *c;
  translation *t;
  matrix *m;
  list *pointlist;
  char buffer[40]={0};
  float f;
  m=getMatrix();
  t=malloc(sizeof(translation));

  pointlist=malloc(sizeof(list));

  c=getCombination();

  while(1) {
    fgets(buffer, 39, stdin);
    if(strstr(buffer, "end")!=NULL)
      break;
    if(strstr(buffer, "transform")!=NULL) {
      sscanf(buffer, "transform %f %f %f %f", &(m->x1), &(m->x2), &(m->y1), &(m->y2));
      multiply(m, c);
      continue;
    }
    if(strstr(buffer, "rotate deg")!=NULL) {
      if(strstr(buffer, "anticlockwise")!=NULL) {
	sscanf(buffer, "rotate deg %f", &f);
	rotateDegrees(-f, c);
	continue;
      } else {
	sscanf(buffer, "rotate deg %f", &f);
	rotateDegrees(f, c);
	continue;
      }
    }
    if(strstr(buffer, "rotate")!=NULL) {
      if(strstr(buffer, "anticlockwise")!=NULL) {
	sscanf(buffer, "rotate %f", &f);
	rotate(-f, c);
	continue;
      } else {
	sscanf(buffer, "rotate %f", &f);
	rotate(f, c);
	continue;
      }
    }
    if(strstr(buffer, "enlarge")!=NULL) {
      sscanf(buffer, "enlarge %f", &f);
      enlarge(f, c);
      continue;
    }
    if(strstr(buffer, "reflect")!=NULL) {
      sscanf(buffer, "reflect y = %fx", &f);
      reflect(f, c);
      continue;
    }
  }

  fgets(buffer, 39, stdin);

  getPointList(pointlist, buffer);
  transformPointList(pointlist, c);
  printPoints(pointlist);

  free(t);
  free(m);
  freeCombination(c);
  freePoints(pointlist);

  return 0;
}

```

it can be run by doing:
```

sudo apt-get install build-essential
gcc -lm program.c -o binary_name
./binary_name

```

if you want to check it for memory leaks, you can do this by running:
```

sudo apt-get install valgrind
gcc program.c -Wall -g -lm -o binary_name
valgrind --leak-check=yes ./binary_name

```

Very impressive, works beautifully. I'll take it that this wins the speed test.

---

### Post by howlingmadhowie on 2010-07-29
> **sharpdust said:**
> 
```
#!/usr/bin/env ruby

# transform a b c d
# x' = ax + by
# y' = cx + dy
def transform(x, y, vars)
  a, b, c, d = vars[0].to_f, vars[1].to_f, vars[2].to_f, vars[3].to_f
  x = a*x + b*y
  y = c*x + d*y
  return x, y
end
```

i don't know ruby, but does this actually work as intended? or does x get overwritten in the line
```

  x = a*x + b*y

```
so the result of 
```

  y = c*x + d*y

```
is not what you want?

in my C program i got around this problem by writing a couple of cloning methods so i could copy existing matrices and points, and then use these copies on the right hand side.

in general this is a problem with assignment. in my scheme program, because it is stateless (it uses define but not set!), this problem doesn't crop up -- the function 'transform' returns a new instance of the point object and the old object is just discarded.

---

### Post by sharpdust on 2010-07-29
> **howlingmadhowie said:**
> i don't know ruby, but does this actually work as intended? or does x get overwritten in the line
```

  x = a*x + b*y

```
...


You are absolutely correct. I was copying and pasting from my other program and I appear to have missed the temporary variable part.

Here's a pretty clean fix without having to use a temporary variable.

```
#!/usr/bin/env ruby

# transform a b c d
# x' = ax + by
# y' = cx + dy
def transform(x, y, vars)
  a, b, c, d = vars[0].to_f, vars[1].to_f, vars[2].to_f, vars[3].to_f
  x, y = a*x + b*y, c*x +d*y
  return x, y
end

# translate X Y
# x' = x + X
# y' = y + Y
def translate(x, y, vars)
  big_x, big_y = vars[0].to_f, vars[1].to_f
  x += big_x
  y += big_y
  return x, y
end

# enlarge scale_factor
# x', y' = transform scale_factor, 0, 0, scale_factor
def enlarge(x, y, vars)
  scale_factor = vars[0].to_f
  x, y = transform(x, y, [scale_factor, 0, 0, scale_factor])
  return x, y
end

# rotate angle_in_rads clockwise
# rotate angle_in_rads anticlockwise
# rotate deg angle_in_degs clockwise
# rotate deg angle_in_degs anticlockwise
# x', y' = transform cos(angle), -sin(angle), sin(angle), cos(angle)
def rotate(x, y, vars)
  if vars[0] == 'deg' then
    angle     = vars[1].to_f * Math::PI / 180 # convert to radians
    direction = vars[2]
  else 
    angle     = vars[0].to_f
    direction = vars[1]
  end
  
  angle = -angle if direction == 'clockwise'

  x, y = transform(x, y, [Math.cos(angle), -(Math.sin(angle)),
                          Math.sin(angle),   Math.cos(angle)])
  return x, y
end

# reflect y = mx
# x', y' = transform cos(2atan(m)) sin(2atan(m)) sin(2atan(m)) -cos(2atan(m))
def reflect(x, y, vars)
  m = vars[2][0..0].to_f
  x, y = transform(x, y, [Math.cos(2 * Math.atan(m)),  Math.sin(2 * Math.atan(m)),
                          Math.sin(2 * Math.atan(m)), -Math.cos(2 * Math.atan(m))])
  return x, y
end

##################################
# Grab user input
# ################################
transformations = STDIN.gets('end')

STDIN.gets # call gets again since STDIN still has a newline in it.

coordinates = STDIN.gets

# Do some magic to make the coordinates a usable format.
coordinates = coordinates.split
coordinates.map! {|coord| coord.split(',').map!{|point| point.to_f}}

# Iterate each of the lines
# command is the method name (transform, enlarge, etc.)
# vars is the rest of the line.
transformations.each do |line|
  command, vars = line.strip.split[0], line.strip.split[1..-1]

  coordinates = coordinates.each do |coord|
    case command
       when 'transform' then coord[0], coord[1] = transform(coord[0], coord[1], vars)
       when 'translate' then coord[0], coord[1] = translate(coord[0], coord[1], vars)
       when 'enlarge'   then coord[0], coord[1] =   enlarge(coord[0], coord[1], vars)
       when 'rotate'    then coord[0], coord[1] =    rotate(coord[0], coord[1], vars)
       when 'reflect'   then coord[0], coord[1] =   reflect(coord[0], coord[1], vars)
    end
  end
end

puts coordinates.inspect
```

---

### Post by dv3500ea on 2010-07-29
I'm setting the deadline for any changes or new entries to 23:59 Sat 31st Jul ([UTC]("http://www.csgnetwork.com/utctimecalc.html")).
Please post any changes made to programs in a new post rather than editing the existing code.
I should be able to announce a winner some time on Sunday.

---

### Post by dv3500ea on 2010-08-01
Well done to all those who took part in this challenge. I hope you had fun and learned some valuable things.

The winner is: howlingmadhowie (for their program written in c), congratulations!

Your program was well written, with good use of functions and quite accurate mathematically, as well as extremely fast.

The contest was very close and I have posted a spreadsheet with the breakdown of the scores.

I look forward to seeing the next challenge.

---

### Post by cprofitt on 2010-08-01
I wanted to do this, but I last took a math course in 1985 so it was not something I could do unless a very good reference to the underlying math was available.

---

### Post by nes1983 on 2010-08-02
> **cprofitt said:**
> I wanted to do this, but I last took a math course in 1985 so it was not something I could do unless a very good reference to the underlying math was available.

Yea, well, you can do it in one of two ways. You can use matrices, or you don't. This task could have been solved using high school math and trigonometry only. You can, of course, with a sheet of paper and some memory of high school, easily work out a set of formulas to find a function that reflects points on a given line.

The question could have been posed much more openly to stress that. Of course, matrices make the task a whole lot easier, if you have some feeling for them.

---

### Post by wkhasintha on 2010-08-03
Im on it

---

### Post by dv3500ea on 2010-08-03
> **wkhasintha said:**
> Im on it

On what???

---

### Post by lordhaworth on 2010-08-03
I have to say that these are a great resource for looking at a new language - I am taking a first look at perl and finding these challenges a very useful exercise. 

I should hopefully catch up soon!

p.s. well done to all

---

### Post by schauerlich on 2010-08-12
Any word on when the next challenge will be out?

---

### Post by wkhasintha on 2010-08-13
> **dv3500ea said:**
> On what???

on a chair:D

---

### Post by texaswriter on 2010-08-13
if the winner of this contest doesn't make the next one, somebody can try to get in contact with a member of the beginner programming club... Maybe try [http://ubuntuforums.org/member.php?u=448461](http://ubuntuforums.org/member.php?u=448461)
Bodsda

---

### Post by howlingmadhowie on 2010-08-13
oh, sorry. the next programming challenge will be up soon :)

---

### Post by texaswriter on 2010-08-14
Oh cool, 
can you link to it from here when you do :popcorn::KS:D

---

### Post by duanedesign on 2010-08-14
You can find the index for all the challenges past and present [here.]("http://ubuntuforums.org/showthread.php?t=876494")

I will do my best to get Challenge 15 up as soon as it appears. :)

I also want to say thank you to everyone who has participated in, and help maintain, the Beginners Programming Challenge.

Again with a much larger link, [Beginners Team Programming Challenge Index]("http://ubuntuforums.org/showthread.php?t=876494").

---

### Post by howlingmadhowie on 2010-08-15
okay, here it is: [http://ubuntuforums.org/showthread.php?p=9723093](http://ubuntuforums.org/showthread.php?p=9723093)

let me know if i've made a mistake or it's unclear or whatever :)

---

