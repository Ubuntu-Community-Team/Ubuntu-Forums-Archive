---
title: "Weekly Programming Challenge, 2 March 2007"
date: 2007-03-02
forum: Programming Talk
---

### Post by po0f on 2007-03-02
**Rules**:
[list]
[*]Any language is allowed.  (No swearing though, please :))
[*]Extensive use of external libraries is frowned upon, and may be grounds for being frowned upon.
[*]Submissions must meet the requirements and must be programmed within any limitations imposed posted on the challenge page.  
[*]All submissions for the challenge must be submitted six (6) days after the initial posting of the challenge.  (For example, this challenge starts 2 Mar, submissions in by 8 Mar)  The final day will be for community review.
[*]A winner will be posted after community review; the winner gets to post the challenge for the next week.  If the winner decides to not post a new challenge, the previous winner may.  If the previous winner doesn't post a new challenge in a timely fashion, then I'll post one.  :twisted: 
[*]All code will be considered [public domain](http://creativecommons.org/licenses/publicdomain/), unless the submitter chooses to release it under a different license.
[/list]

**Objective**:
Write a program that creates a "maze".  A maze can contain "walls" (areas you may not traverse) and "hallways" (areas you may traverse).  Hallways should not be more than 2 units wide.  And no totally random maze; a "player" inside the maze should be able to traverse all of it, ie no walled off rooms.

**Limitations**:
I'm actually thinking that the use of external libraries in this challenge *is allowed*.  I want to see some pretty mazes, people!  (OpenGL, PyGame, SDL, whatever.  :))

**Bonus 1a**:
Create a "player" for the maze, allowing them to walk around in it.

**Bonus 1b**:
Create start/finish positions inside the maze, and have the player "win" when they get to the finish.

**Bonus 2**:
Create an AI to walk through the maze, possibly calculating the shortest distance needed to travel to finish.

**Note**:
Credit to yaaarrrgg for coming up with this week's challenge.  I guess no one was motivated enough to post it, so I did.  :p

---

### Post by Wybiral on 2007-03-03
Cool, I'll try to write something when I get some more free time. I've never had to write a maze generating algorithm so this should be interesting (most likely sloppy).

All of the algorithms I've found for it aren't for cell based maps, they're for wall based (where each cell has four walls) which should make things even more interesting.

---

### Post by po0f on 2007-03-03
Wybiral,

Yeah, I instantly thought "rogue-like" when I read yaaarrrgg's idea for a WPC.  ;)

I'm working on a solution to this one as well, it kinda piqued my interest; I've been wanting to code a game for a while, and a rogue-like seems simple enough.  Maybe this will get me started.

---

### Post by Wybiral on 2007-03-03
I've made a number of wolf3d style demos and engines so if I figure out a good algorithm and have even more time to extent it with an oldskool 3d demo, I will definitely do that (with SDL+OpenGL).

Right now I'm having trouble with the algorithm itself... Nothing I've tried has turned out the way I wanted it.

The hard part is that a grid maze must maintain the cells between hallways, whereas most maze algorithms use a wall between each cell (like your typical newspaper/magazine puzzle maze)

But, it certainly is a challenge...

---

### Post by Alasdair on 2007-03-04
Here's my entry (in Common Lisp), I wrote quite a lot of it very late at night so I apologise for any poorly written code. ;-) 

Code:
[HTML]
(defconstant north 0)
(defconstant east 1)
(defconstant south 2)
(defconstant west 3)

;;; Macros for removing walls
(defmacro remove-north-wall (maze x y)
  `(setf (aref ,maze ,x ,y) `(1 ,@(rest (aref ,maze ,x ,y)))))

(defmacro remove-east-wall (maze x y)
  `(setf (aref ,maze ,x ,y) `(,(first (aref ,maze ,x ,y))
			      1
			      ,@(rest (rest (aref ,maze ,x ,y))))))

(defmacro remove-south-wall (maze x y)
  `(setf (aref ,maze ,x ,y) `(,(first (aref ,maze ,x ,y))
			      ,(second (aref ,maze ,x ,y))
			      1
			      ,@(last (aref ,maze ,x ,y)))))

(defmacro remove-west-wall (maze x y)
  `(setf (aref ,maze ,x ,y) `(,(first (aref ,maze ,x ,y))
			      ,(second (aref ,maze ,x ,y))
			      ,(third (aref ,maze ,x ,y))
			      1)))

(defun door (maze direction x y)
  "makes a door between two cells (destructive)"
  (cond ((= direction north)
	 (remove-north-wall maze x y)
	 (remove-south-wall maze x (1- y)))
	((= direction east)
	 (remove-east-wall maze x y)
	 (remove-west-wall maze (1+ x) y))
	((= direction south)
	 (remove-south-wall maze x y)
	 (remove-north-wall maze x (1+ y)))
	((= direction west)
	 (remove-west-wall maze x y)
	 (remove-east-wall maze (1- x) y))))

(defun freep (maze x y)
  "predicate that returns t or nil depending on whether a cell is free or not"
  (if (or (< x 0)
	  (>= x (first (array-dimensions maze)))
	  (< y 0)
	  (>= y (second (array-dimensions maze)))
	  (> (apply #'+ (aref maze x y)) 0))
      nil
      t))

(defun cell-coord (direction x y)
  "given a direction and coordinates, returns the coordinates of the ajacent cell in that direction"
  (cond ((= direction north)
	 `(,x ,(1- y)))
	((= direction east)
	 `(,(1+ x) ,y))
	((= direction south)
	 `(,x ,(1+ y)))
	((= direction west)
	 `(,(1- x) ,y))))

 (defun choose-cell-acc (acc maze x y)
    (let* ((direction (random 4))
	   (xnew (first (cell-coord direction x y)))
	   (ynew (second (cell-coord direction x y))))
      (if (freep maze xnew ynew)
	  `(,xnew ,ynew)
	  (if (> acc 100)
	      nil
	      (choose-cell-acc (1+ acc) maze x y)))))

(defun choose-cell (maze x y)
  "chooses a random ajacent cell, returns nil if it can't find a free cell"
  (choose-cell-acc 0 maze x y))


(defun get-direction (x1 y1 x2 y2)
  "Takes 2 ajacent coordinates, and returns the direction between them"
  (cond ((> y1 y2)
	 north)
	((< x1 x2)
	 east)
	((< y1 y2)
	 south)
	((> x1 x2)
	 west)))	

(defun get-start (xsize ysize)
  "picks a random starting location for maze generation to begin"
  (if (= (random 2) 0)
      `(,(random xsize) 0)
      `(0 ,(random ysize))))

(defun make-maze (xsize ysize)
  "Generates a maze using a recursive backtracking algorithm:"
  ;; It works as follows:
  ;; 1- Select a random cell (at the edge)
  ;; 2- Push this cell to the stack
  ;; 3- Select a new ajacent free cell
  ;; 4- If there are no ajacent free cells, pop the stack and try finding a free cell from the last location
  ;; 4- make a door between these 2 free cells
  ;; 5- push the new free cell to the stack, return to step 3
  ;; 6- when the stack is empty, the maze is complete
  ;; The maze is stored as a 2d array of 4 element lists with each element representing whether there is a wall in
  ;; a specific direction, eg (1 1 0 0) would represent doors north and east (1) and walls to the south and west.(0)
  (let* ((maze (make-array `(,xsize ,ysize) :initial-element '(0 0 0 0)))
	 (position (get-start xsize ysize))
	 (new-position nil)
	 (stack (list position)))
    (do ((i 0 (1+ i))) ;loop forever until return
	(nil)
      (if (eql stack nil)
	  (return))
      (setf position (first stack))
      (setf new-position (choose-cell maze (first position) (second position)))
      (cond ((eql new-position nil)
	     (pop stack))
	    (t	    
	     (let ((direction (get-direction (first position)
					     (second position)
					     (first new-position)
					     (second new-position)))
		   (x (first position))
		   (y (second position)))
	       (door maze direction x y))
	     (push new-position stack))))
    maze))

(defun print-maze (maze)
  "prints the maze"
  (let ((xsize (first (array-dimensions maze)))
	(ysize (second (array-dimensions maze))))
    (format t "~%")
    (do ((row 0 (1+ row)))
	((> row (1- ysize)))
      (do ((i 0 (1+ i)))
	((> i 1))
	(do ((col 0 (1+ col)))
	    ((> col (1- xsize)))
	  (cond ((= i 0)
		 (if (= (nth i (aref maze col row)) 0)
		     (format t "00")
		     (format t "0 ")))
		((= i 1)
		 (cond ((or (and (= (nth 1 (aref maze col row)) 0)
				 (= (nth 3 (aref maze col row)) 0))
			    (and (= (nth 1 (aref maze col row)) 1)
				 (= (nth 3 (aref maze col row)) 0)))
			(format t "0 "))
		       (t
			(format t "  "))))))
	(format t "0~%")))
    (do ((row 0 (1+ row)))
	((> row (1- xsize)))
      (format t "00"))
    (format t "0")))
[/HTML]

Sample output:
[HTML]
CL-USER> (print-maze (make-maze 30 30))

0000000000000000000000000000000000000000000000000000000000000
0 0   0     0           0     0   0             0     0     0
0 0 000 00000 00000 00000 000 0 0 0 0 000000000 0 000 0 0 0 0
0 0 0       0 0   0     0 0 0 0 0   0     0 0   0   0   0 0 0
0 0 0 00000 0 0 0000000 0 0 0 0 000000000 0 0 000 00000 0 0 0
0   0 0   0 0 0 0     0     0 0 0         0 0   0 0   0 0 0 0
0 000 0 0 0 0 0 0 0 0 0000000 0 0 000000000 000 000 0 000 0 0
0 0     0 0   0 0 0 0     0   0 0 0           0 0   0 0   0 0
0 000000000 000 0 0 00000 0 0 0 0 000 00000 0 0 0 000 0 000 0
0 0       0 0     0     0 0 0 0 0   0 0   0 0   0   0   0   0
0 0 00000 0 00000 00000 000 000 000 0 0 0 0 0000000 00000 000
0 0     0 0     0 0   0   0     0   0 0 0 0         0   0 0 0
0 00000 0 00000 0 000 000 0000000 0 000 0 00000000000 000 0 0
0       0 0 0   0   0   0     0   0 0   0   0 0   0   0     0
000000000 0 0 00000 000 00000 0 00000 00000 0 0 0 0 0 0 00000
0     0   0   0   0         0 0 0     0     0   0   0   0   0
0 0 000 000 000 0 000000000 0 0 0 00000 00000 00000000000 0 0
0 0   0 0       0 0   0     0 0   0   0   0         0   0 0 0
0 000 0 000000000 0 0 0000000 00000 0 000 000000000 0 000 0 0
0   0   0   0   0   0   0         0 0 0   0       0   0   0 0
000 00000 0 0 0 0000000 0 0000000 0 000 0 0 00000 00000 000 0
0   0     0 0 0 0   0     0 0   0 0 0   0 0 0   0       0 0 0
0 000 000 0 0 000 0 0 00000 0 0 0 0 0 000 0 0 00000000000 0 0
0 0 0   0 0 0   0 0 0 0   0   0 0 0 0 0   0 0             0 0
0 0 0 000 0 000 0 0 0 0 0 00000 0 0 0 0 000 0 0 0 000000000 0
0 0   0   0   0   0   0 0     0   0 0 0   0 0 0 0 0         0
0 0 000 00000 0 0000000 00000 0 000 0 000 0 000 0 0 0000000 0
0 0 0   0     0 0       0   0 0     0   0 0     0 0 0   0   0
0 000 000 0000000 0000000 000 00000 000 000000000 0 000 0 000
0     0 0 0       0 0     0   0     0 0           0 0   0 0 0
0000000 0 0 0000000 0 0 000 000 00000 0000000000000 0 000 0 0
0       0   0       0 0     0 0     0   0   0     0 0 0   0 0
0 0 000000000 0 000 0 0000000 00000 0 0 0 0 0 000 0 0 0 000 0
0 0         0 0 0   0 0       0       0 0 0 0   0   0 0 0   0
0 00000 0 0 0 0 00000 0 0 00000 0000000 0 00000 00000 0 0 0 0
0 0   0 0 0 0 0       0 0     0 0     0 0     0 0     0 0 0 0
000 0 000 000 00000000000 000 0 0 000 0 000 0 0 0 0 000 0 0 0
0   0   0   0 0         0   0   0 0   0     0 0 0 0     0 0 0
0 00000 0 0 0 0 000 000 000 00000 0 00000 00000 00000 000 0 0
0 0 0   0 0 0 0 0   0 0   0   0   0   0   0   0 0   0     0 0
0 0 0 000 0 0 0 0 000 000 000 0 00000 00000 0 0 0 0 0000000 0
0 0   0   0 0 0 0 0       0   0 0   0     0 0 0   0     0   0
0 0 00000 0 0 000 0 0000000 000 000 00000 0 0 00000 000 00000
0 0     0 0 0     0   0       0 0       0 0 0     0   0     0
0 00000 000 000000000 0 0000000 0 00000 0 0 00000 000 00000 0
0 0   0   0         0 0 0       0 0   0 0 0   0     0   0   0
0 0 00000 0 0 00000 0 000 0000000 0 0 000 000 00000 000 0 000
0 0       0 0 0 0   0     0       0 0   0   0   0 0   0 0   0
0 000 0000000 0 0 000000000 000 000 000 000 000 0 000 00000 0
0   0 0   0   0 0 0       0   0     0     0 0   0   0   0   0
0 0 0 0 0 0 000 0 00000 0 000 0000000 000 0 0 000 00000 0 000
0 0 0 0 0 0 0 0   0     0 0 0   0   0 0   0   0   0   0 0   0
0 0 0 0 0 0 0 0 000 00000 0 000 0 0 0 0 0000000 0 0 0 0 000 0
0 0 0   0   0 0     0 0   0   0 0 0 0 0 0   0 0 0   0 0     0
0 0 000000000 0 00000 0 000 0 0 0 000 0 0 0 0 0 00000 00000 0
0 0 0     0     0   0       0 0   0   0   0   0 0   0   0   0
0 0 000 0 0 00000 0 0000000000000 0 00000000000 0 0 000 0 000
0 0   0 0   0   0 0 0           0 0 0         0 0 0 0 0   0 0
0 000 0000000 0 0 0 0 000000000 0 0 0 0000000 0 0 0 0 00000 0
0   0         0   0           0   0         0     0         0
0000000000000000000000000000000000000000000000000000000000000
NIL
[/HTML]

---

### Post by WW on 2007-03-04
> **Wybiral said:**
> 
The hard part is that a grid maze must maintain the cells between hallways, 

I don't see where the original challege says this, or where it says the challenge must be a "grid maze".  One can interpret "walls" and "hallways" in many ways.

The challenge doesn't even say the maze must be a rectangular grid.  That is certainly one option, and it looks like that's how Alasdair has implemented it, but there are other ways to interpret the challenge.

P.S. Alasdair, that's pretty cool!

---

### Post by Alasdair on 2007-03-04
> **Wybiral]All of the algorithms I've found for it aren't for cell based maps, they're for wall based (where each cell has four walls) which should make things even more interesting.[/QUOTE]

Thats pretty much how I implemented it, it's a grid of cells, each with 4 walls, and the algorithm randomly roams round the maze knocking walls down as it goes, and backtracking when it can't go any furthur. The challenged just mentioned hallways and walls, which can be interpreted pretty freely.

[QUOTE=WW said:**
> P.S. Alasdair, that's pretty cool!

Thanks, I just wrote a small program which displays the maze using SDL. It looks a little bit fancier now. 

Code:
[HTML]
(require :sdl)
(load "maze.lisp")

(defun init-sdl ()
  (sdl:init sdl:+init-video+)
  (let ((surface (sdl:set-video-mode 1024 1024 16
				     (logior sdl:+resizable+
					     sdl:+swsurface+))))
    (when (sgum:null-pointer-p surface)
      (error "Unable to set video mode"))
    (sdl:wm-set-caption "Maze" nil)
    surface))

(defun run-sdl-event-loop ()
  (sdl:event-loop
   (:quit ()
	  (return))))

(defun draw-maze (maze surface)
  (let ((xsize (first (array-dimensions maze)))
	(ysize (second (array-dimensions maze))))
   (do ((row 0 (1+ row)))
	((> row (1- ysize)))
     (do ((col 0 (1+ col)))
	 ((> col (1- xsize)))
       (let ((cell (aref maze col row))
	     (x (+ (* col 10) 20))
	     (y (+ (* row 10) 20)))
	 (print cell)
	 (if (= (nth 0 cell) 0)
	     (sdl:draw-line surface
			    x y
			    (+ x 10) y
			    255 255 255))
	 (if (= (nth 1 cell) 0)
	     (sdl:draw-line surface
			    (+ x 10) y
			    (+ x 10) (+ y 10)
			    255 255 255))
	 (if (= (nth 2 cell) 0)
	     (sdl:draw-line surface
			    x (+ y 10)
			    (+ x 10) (+ y 10)
			    255 255 255))
	 (if (= (nth 3 cell) 0)
	     (sdl:draw-line surface
			    x y
			    x (+ y 10)
			    255 255 255)))))))

(defun start ()
  (let ((surface (init-sdl))
	(maze (make-maze 80 80)))
    (draw-maze maze surface)
    (sdl:flip surface)
    (run-sdl-event-loop))
  (sdl:quit))

(start)
[/HTML]

---

### Post by hod139 on 2007-03-04
> **Wybiral said:**
> 
Right now I'm having trouble with the algorithm itself... Nothing I've tried has turned out the way I wanted it.

The hard part is that a grid maze must maintain the cells between hallways, whereas most maze algorithms use a wall between each cell (like your typical newspaper/magazine puzzle maze)

But, it certainly is a challenge...
Maze generation algorithms are an interesting topic.  I remember learning Kruskal's and Prim's algorithms in my algorithms course.  There are definitely some neat ways to generate mazes.

---

### Post by po0f on 2007-03-04
Ok, there's only been one entry, and I think everybody's going to have a hard time topping that one.  Good job, Alasdair!  :)

---

### Post by theorem_hunter on 2007-03-04
Alasdair, this is really cool :) (i came looking for java help & then got distracted by this thread...)

i saw your screen shot, nice :) (not sure if u know this but press L-ALT PrtScr to get a screen shot of just a window, if your in gnome, but it looked to me that you were in kde)

---

### Post by Wybiral on 2007-03-04
OK, so far this is what I have:

```

err_string:
   .string   "Fatal error: %s\n"

err_alloc_maze:
   .string   "Unable to allocate maze!"

err_alloc_cells:
   .string   "Unable to allocate cells!"

err_maze_dim:
   .string   "Mazes cannot be of even dimension!"

fatal_error:
   pushl  %ebp
   movl   %esp, %ebp
   subl   $8, %esp
   movl   8(%ebp), %eax
   movl   %eax, 4(%esp)
   movl   $err_string, (%esp)
   call   printf
   mov    $1, %eax
   int    $0x80

allocate_maze:
   pushl  %ebp
   movl   %esp, %ebp
   subl   $24, %esp
   movl   $12, (%esp)
   call   malloc
   movl   %eax, -4(%ebp)
   cmpl   $0, -4(%ebp)
   je     fatal_alloc_maze_error
   movl   -4(%ebp), %eax
   movl   %eax, -20(%ebp)
   jmp    skip_alloc_maze_error
fatal_alloc_maze_error:
   movl   $err_alloc_maze, (%esp)
   call   fatal_error
skip_alloc_maze_error:
   movl   -20(%ebp), %eax
exit_alloc_maze:
   leave
   ret

allocate_cells:
   pushl  %ebp
   movl   %esp, %ebp
   pushl  %ebx
   subl   $36, %esp
   movl   8(%ebp), %eax
   movl   12(%ebp), %edx
   movb   %al, -24(%ebp)
   movb   %dl, -28(%ebp)
   movb   $0, -5(%ebp)
   movzbl -28(%ebp), %eax
   sall   $2, %eax
   movl   %eax, (%esp)
   call   malloc
   movl   %eax, -16(%ebp)
   cmpl   $0, -16(%ebp)
   je     cell_alloc_error2
   movl   $0, -12(%ebp)
   jmp    cell_alloc_error1
for_loop:
   movl   -12(%ebp), %eax
   sall   $2, %eax
   movl   %eax, %ebx
   addl   -16(%ebp), %ebx
   movzbl -24(%ebp), %eax
   movl   %eax, (%esp)
   call   malloc
   movl   %eax, (%ebx)
   movl   -12(%ebp), %eax
   sall   $2, %eax
   addl   -16(%ebp), %eax
   movl   (%eax), %eax
   testl  %eax, %eax
   jne    skip_cell_alloc_error1
   movl   $err_alloc_cells, (%esp)
   call   fatal_error
skip_cell_alloc_error1:
   addl   $1, -12(%ebp)
cell_alloc_error1:
   movzbl -28(%ebp), %eax
   cmpl   -12(%ebp), %eax
   ja     for_loop
   movl   -16(%ebp), %eax
   movl   %eax, -32(%ebp)
   jmp    skip_cell_alloc_error2
cell_alloc_error2:
   movl   $err_alloc_cells, (%esp)
   call   fatal_error
skip_cell_alloc_error2:
   movl   -32(%ebp), %eax
   addl   $36, %esp
   popl   %ebx
   popl   %ebp
   ret

init_maze:
   pushl  %ebp
   movl   %esp, %ebp
   subl   $40, %esp
   movl   8(%ebp), %eax
   movl   12(%ebp), %edx
   movb   %al, -20(%ebp)
   movb   %dl, -24(%ebp)
   movzbl -20(%ebp), %eax
   andl   $1, %eax
   xorl   $1, %eax
   testb  %al, %al
   jne    maze_dim_error
   movzbl -24(%ebp), %eax
   andl   $1, %eax
   xorl   $1, %eax
   testb  %al, %al
   jne    maze_dim_error
   call   allocate_maze
   movl   %eax, -4(%ebp)
   movzbl -24(%ebp), %eax
   movzbl -20(%ebp), %edx
   movl   %eax, 4(%esp)
   movl   %edx, (%esp)
   call   allocate_cells
   movl   %eax, %edx
   movl   -4(%ebp), %eax
   movl   %edx, (%eax)
   movzbl -20(%ebp), %edx
   movl   -4(%ebp), %eax
   movl   %edx, 4(%eax)
   movzbl -24(%ebp), %edx
   movl   -4(%ebp), %eax
   movl   %edx, 8(%eax)
   jmp    exit_maze_init
maze_dim_error:
   movl   $err_maze_dim, (%esp)
   call   fatal_error
exit_maze_init:
   movl   -4(%ebp), %eax
   leave
   ret

fill_maze:
   pushl  %ebp
   movl   %esp, %ebp
   subl   $20, %esp
   movl   12(%ebp), %eax
   movb   %al, -20(%ebp)
   movb   $0, -1(%ebp)
   jmp    begin_maze_fill_loops
maze_fill_y_loop:
   movb   $0, -2(%ebp)
   jmp    loop_jump_1
maze_fill_x_loop:
   movl   8(%ebp), %eax
   movl   (%eax), %edx
   movzbl -1(%ebp), %eax
   sall   $2, %eax
   leal   (%edx,%eax), %eax
   movl   (%eax), %edx
   movzbl -2(%ebp), %eax
   addl   %eax, %edx
   movzbl -20(%ebp), %eax
   movb   %al, (%edx)
   addb   $1, -2(%ebp)
loop_jump_1:
   movzbl -2(%ebp), %eax
   movl   8(%ebp), %edx
   movl   4(%edx), %edx
   cmpl   %edx, %eax
   jb     maze_fill_x_loop
   addb   $1, -1(%ebp)
begin_maze_fill_loops:
   movzbl -1(%ebp), %eax
   movl   8(%ebp), %edx
   movl   8(%edx), %edx
   cmpl   %edx, %eax
   jb     maze_fill_y_loop
   leave
   ret

in_bounds:
   pushl  %ebp
   movl   %esp, %ebp
   subl   $12, %esp
   movl   12(%ebp), %eax
   movl   16(%ebp), %edx
   movb   %al, -4(%ebp)
   movb   %dl, -8(%ebp)
   cmpb   $0, -4(%ebp)
   je     false_in_bounds
   movzbl -4(%ebp), %edx
   movl   8(%ebp), %eax
   movl   4(%eax), %eax
   dec    %eax
   cmpl   %eax, %edx
   jae    false_in_bounds
   cmpb   $0, -8(%ebp)
   je     false_in_bounds
   movzbl -8(%ebp), %edx
   movl   8(%ebp), %eax
   movl   8(%eax), %eax
   dec    %eax
   cmpl   %eax, %edx
   jae    false_in_bounds
   movl   $1, -12(%ebp)
   jmp    exit_in_bounds
false_in_bounds:
   movl   $0, -12(%ebp)
exit_in_bounds:
   movl   -12(%ebp), %eax
   leave
   ret

neighbor_count:
   pushl  %ebp
   movl   %esp, %ebp
   subl   $36, %esp
   movl   12(%ebp), %eax
   movl   16(%ebp), %edx
   movb   %al, -20(%ebp)
   movb   %dl, -24(%ebp)
   movb   $0, -1(%ebp)
   movzbl -24(%ebp), %eax
   movzbl -20(%ebp), %edx
   movl   %eax, 8(%esp)
   movl   %edx, 4(%esp)
   movl   8(%ebp), %eax
   movl   %eax, (%esp)
   call   in_bounds
   testb  %al, %al
   je     not_in_bounds
   movl   8(%ebp), %eax
   movl   (%eax), %edx
   movzbl -24(%ebp), %eax
   sall   $2, %eax
   leal   (%edx,%eax), %eax
   addl   $4, %eax
   movl   (%eax), %edx
   movzbl -20(%ebp), %eax
   leal   (%edx,%eax), %eax
   movzbl (%eax), %eax
   cmpb   $32, %al
   jne    y_plus_1
   addb   $1, -1(%ebp)
y_plus_1:
   movl   8(%ebp), %eax
   movl   (%eax), %edx
   movzbl -24(%ebp), %eax
   sall   $2, %eax
   leal   (%edx,%eax), %eax
   subl   $4, %eax
   movl   (%eax), %edx
   movzbl -20(%ebp), %eax
   leal   (%edx,%eax), %eax
   movzbl (%eax), %eax
   cmpb   $32, %al
   jne    y_minus_1
   addb   $1, -1(%ebp)
y_minus_1:
   movl   8(%ebp), %eax
   movl   (%eax), %edx
   movzbl -24(%ebp), %eax
   sall   $2, %eax
   leal   (%edx,%eax), %eax
   movl   (%eax), %edx
   movzbl -20(%ebp), %eax
   leal   (%edx,%eax), %eax
   inc    %eax
   movzbl (%eax), %eax
   cmpb   $32, %al
   jne    x_plus_1
   addb   $1, -1(%ebp)
x_plus_1:
   movl   8(%ebp), %eax
   movl   (%eax), %edx
   movzbl -24(%ebp), %eax
   sall   $2, %eax
   leal   (%edx,%eax), %eax
   movl   (%eax), %edx
   movzbl -20(%ebp), %eax
   leal   (%edx,%eax), %eax
   dec    %eax
   movzbl (%eax), %eax
   cmpb   $32, %al
   jne    not_in_bounds
   addb   $1, -1(%ebp)
not_in_bounds:
   movzbl -1(%ebp), %eax
   leave
   ret

generate_maze:
   pushl  %ebp
   movl   %esp, %ebp
   subl   $40, %esp
   movl   12(%ebp), %eax
   movl   16(%ebp), %edx
   movb   %al, -20(%ebp)
   movb   %dl, -24(%ebp)
   movzbl -24(%ebp), %eax
   movzbl -20(%ebp), %edx
   movl   %eax, 8(%esp)
   movl   %edx, 4(%esp)
   movl   8(%ebp), %eax
   movl   %eax, (%esp)
   call   in_bounds
   testb  %al, %al
   je     gen_not_in_bounds
   movl   8(%ebp), %eax
   movl   (%eax), %edx
   movzbl -24(%ebp), %eax
   sall   $2, %eax
   leal   (%edx,%eax), %eax
   movl   (%eax), %edx
   movzbl -20(%ebp), %eax
   leal   (%edx,%eax), %eax
   movzbl (%eax), %eax
   cmpb   $32, %al
   je     gen_not_in_bounds
   movzbl -24(%ebp), %eax
   movzbl -20(%ebp), %edx
   movl   %eax, 8(%esp)
   movl   %edx, 4(%esp)
   movl   8(%ebp), %eax
   movl   %eax, (%esp)
   call   neighbor_count
   cmpb   $1, %al
   ja     gen_not_in_bounds
   movl   8(%ebp), %eax
   movl   (%eax), %edx
   movzbl -24(%ebp), %eax
   sall   $2, %eax
   leal   (%edx,%eax), %eax
   movl   (%eax), %edx
   movzbl -20(%ebp), %eax
   leal   (%edx,%eax), %eax
   movb   $32, (%eax)
   movb   $0, -1(%ebp)
   jmp    start_gen_loop
loop_i:
   call   rand
   andl   $1, %eax
   testb  %al, %al
   je     x_rand
   movzbl -24(%ebp), %edx
   movzbl -20(%ebp), %eax
   subl   $1, %eax
   movzbl %al, %eax
   movl   %edx, 8(%esp)
   movl   %eax, 4(%esp)
   movl   8(%ebp), %eax
   movl   %eax, (%esp)
   call   generate_maze
   jmp    y_rand
x_rand:
   movzbl -24(%ebp), %edx
   movzbl -20(%ebp), %eax
   addl   $1, %eax
   movzbl %al, %eax
   movl   %edx, 8(%esp)
   movl   %eax, 4(%esp)
   movl   8(%ebp), %eax
   movl   %eax, (%esp)
   call   generate_maze
y_rand:
   call   rand
   andl   $1, %eax
   testb  %al, %al
   je     rand_jump
   movzbl -24(%ebp), %eax
   subl   $1, %eax
   movzbl %al, %eax
   movzbl -20(%ebp), %edx
   movl   %eax, 8(%esp)
   movl   %edx, 4(%esp)
   movl   8(%ebp), %eax
   movl   %eax, (%esp)
   call   generate_maze
   jmp    gen_bail
rand_jump:
   movzbl -24(%ebp), %eax
   addl   $1, %eax
   movzbl %al, %eax
   movzbl -20(%ebp), %edx
   movl   %eax, 8(%esp)
   movl   %edx, 4(%esp)
   movl   8(%ebp), %eax
   movl   %eax, (%esp)
   call   generate_maze
gen_bail:
   addb   $1, -1(%ebp)
start_gen_loop:
   cmpb   $2, -1(%ebp)
   jbe    loop_i
gen_not_in_bounds:
   leave
   ret

print_maze:
   pushl  %ebp
   movl   %esp, %ebp
   subl   $24, %esp
   movb   $0, -1(%ebp)
   jmp    print_loop_jump
init_loops:
   movb   $0, -2(%ebp)
   jmp    start_loop
print_y_loop:
   movl   8(%ebp), %eax
   movl   (%eax), %edx
   movzbl -1(%ebp), %eax
   sall   $2, %eax
   leal   (%edx,%eax), %eax
   movl   (%eax), %edx
   movzbl -2(%ebp), %eax
   leal   (%edx,%eax), %eax
   movzbl (%eax), %eax
   movsbl %al,%eax
   movl   %eax, (%esp)
   movb   $4, %al
   mov    $1, %ebx
   mov    %esp, %ecx
   mov    $1, %edx
   int    $0x80
   addb   $1, -2(%ebp)
start_loop:
   movzbl -2(%ebp), %eax
   movl   8(%ebp), %edx
   movl   4(%edx), %edx
   cmpl   %edx, %eax
   jb     print_y_loop
   movl   $10, (%esp)
   call   putchar
   addb   $1, -1(%ebp)
print_loop_jump:
   movzbl -1(%ebp), %eax
   movl   8(%ebp), %edx
   movl   8(%edx), %edx
   cmpl   %edx, %eax
   jb     init_loops
   leave
   ret

free_maze:
   pushl  %ebp
   movl   %esp, %ebp
   subl   $24, %esp
   movb   $0, -1(%ebp)
   jmp   free_maze_loop_jump
free_maze_y_loop:
   movl   8(%ebp), %eax
   movl   (%eax), %edx
   movzbl -1(%ebp), %eax
   sall   $2, %eax
   leal   (%edx,%eax), %eax
   movl   (%eax), %eax
   movl   %eax, (%esp)
   call   free
   addb   $1, -1(%ebp)
free_maze_loop_jump:
   movzbl -1(%ebp), %eax
   movl   8(%ebp), %edx
   movl   8(%edx), %edx
   cmpl   %edx, %eax
   jb     free_maze_y_loop
   movl   8(%ebp), %eax
   movl   (%eax), %eax
   movl   %eax, (%esp)
   call   free
   movl   8(%ebp), %eax
   movl   %eax, (%esp)
   call   free
   leave
   ret

.global main
main:
   leal   4(%esp), %ecx
   andl   $-16, %esp
   pushl  -4(%ecx)
   pushl  %ebp
   movl   %esp, %ebp
   pushl  %ebx
   pushl  %ecx
   subl   $32, %esp
   movl   %ecx, %ebx
   movl   4(%ebx), %eax
   addl   $4, %eax
   movl   (%eax), %eax
   movl   %eax, (%esp)
   call   atoi
   movb   %al, -10(%ebp)
   movl   4(%ebx), %eax
   addl   $8, %eax
   movl   (%eax), %eax
   movl   %eax, (%esp)
   call   atoi
   movb   %al, -9(%ebp)
   movl   $0, (%esp)
   call   time
   movl   %eax, (%esp)
   call   srand
   movzbl -9(%ebp), %eax
   movzbl -10(%ebp), %edx
   movl   %eax, 4(%esp)
   movl   %edx, (%esp)
   call   init_maze
   movl   %eax, -16(%ebp)
   movl   $35, 4(%esp)
   movl   -16(%ebp), %eax
   movl   %eax, (%esp)
   call   fill_maze
   movzbl -9(%ebp), %eax
   shrb   %al
   movzbl %al, %edx
   movzbl -10(%ebp), %eax
   shrb   %al
   movzbl %al, %eax
   movl   %edx, 8(%esp)
   movl   %eax, 4(%esp)
   movl   -16(%ebp), %eax
   movl   %eax, (%esp)
   call   generate_maze
   movl   -16(%ebp), %eax
   movl   %eax, (%esp)
   call   print_maze
   movl   -16(%ebp), %eax
   movl   %eax, (%esp)
   call   free_maze
   addl   $32, %esp
   popl   %ecx
   popl   %ebx
   popl   %ebp
   leal   -4(%ecx), %esp
   ret

```

It was drafted in pure C and then dumped to assembly. Then I optimized it for size (speed isn't a big issue, I cut out a number of C function calls and replaced them with real assembly) and labeled it.

I'm going to extend it for use in a navigable maze when I get some more spare time.

BTW, if you've never compiled assembly with gcc, just save that as "maze.s" and compile it with "gcc maze.s"

You execute it with "./a.out width height"

The dimensions must be odd numbers between 1 and 255 (not that you'd want it any bigger than that in the command line).

example:

```

./a.out 55 25

```

Oh yeah, this is GAS syntax intel assembly.

The algorithm I used was completely made up...

It's not as pretty as most (such as Alasdair's, nice work btw), but it certainly meets the competition requirements.

It works by recursively traversing the maze clearing a path...
It determines if a cell is suitable to clear by counting that cells neighbors, if it has more than two neighbor cells empty, it doesn't clear it (this prevents large empty patches or rooms).

It will generate a different maze every time.

EDIT:

BTW... You can only move left,right,down,up through the maze... NOT diagonal. It actually makes some challenging mazes.

---

### Post by Mr. C. on 2007-03-04
Nice work Alasdair.  Any start / finish points in that beast! :-)

---

### Post by theorem_hunter on 2007-03-04
Wybiral, thats really cool, i compiled & ran... wish i was at that level :)

---

### Post by Wybiral on 2007-03-04
OK, here's the same algorithm, except this time I'm using SDL+OpenGL to render the maze in the classic wolf3d raycaster style.

```

#include <GL/gl.h>
#include <GL/glu.h>
#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <SDL/SDL.h>

#define false 0
#define true  1

#define DEG2RAD 0.017453289


typedef unsigned char byte;

byte key[321];
byte color_map[255][3];

// Maze structure
typedef struct s_maze {
   byte** m_cells;
   byte m_width;
   byte m_height;
} maze;

// Report any fatal errors and abort!
void fatal_error(char* err_str)
{
   printf("Fatal error: %s\n", err_str);
   exit(1);
}

// Initialize an SDL surface as the main buffer
// Also initialize OpenGL perspective and fog
void init(SDL_Surface* surface, int width, int height)
{
   if(SDL_Init(SDL_INIT_VIDEO)< 0)
   {
      fatal_error("Unable to initialize SDL video!");
   }
   const SDL_VideoInfo* info = SDL_GetVideoInfo();
   if(!info)
   {
      fatal_error("Unable to grab SDL video info!");
   }
   int bpp = info->vfmt->BitsPerPixel;
   int video_flags = SDL_OPENGL | SDL_GL_DOUBLEBUFFER | SDL_SWSURFACE;
   surface=SDL_SetVideoMode(width, height, bpp, video_flags);
   if(surface==0)
   {
      fatal_error("Unable to create OpenGL surface!");
   }
	glViewport( 0, 0, width, height );
	glMatrixMode( GL_PROJECTION );
	glEnable( GL_DEPTH_TEST );
	gluPerspective( 45, (GLfloat)width/height, .1, 100 );
	glMatrixMode( GL_MODELVIEW );

	const GLfloat fogColor[4] = {0.0, 0.0, 0.0, 1.0};
	glClearColor(fogColor[0], fogColor[1], fogColor[2], fogColor[3]);
	glFogi(GL_FOG_MODE, GL_EXP2);
	glFogfv(GL_FOG_COLOR, fogColor);
	glFogf(GL_FOG_DENSITY, 0.2);
	glEnable(GL_FOG);
}

// Render cube at x,z using indexed color c
void render_cube(int x, int z, byte c)
{
   glPushMatrix();
   glTranslatef(x, 0, z);
   glColor3ubv(color_map[c]);
   glBegin(GL_QUADS);
   glVertex3f(-0.5,  0.5, -0.5);
   glVertex3f( 0.5,  0.5, -0.5);
   glVertex3f( 0.5, -0.5, -0.5);
   glVertex3f(-0.5, -0.5, -0.5);
   glVertex3f(-0.5,  0.5,  0.5);
   glVertex3f( 0.5,  0.5,  0.5);
   glVertex3f( 0.5, -0.5,  0.5);
   glVertex3f(-0.5, -0.5,  0.5);
   glVertex3f(-0.5, -0.5,  0.5);
   glVertex3f(-0.5,  0.5,  0.5);
   glVertex3f(-0.5,  0.5, -0.5);
   glVertex3f(-0.5, -0.5, -0.5);
   glVertex3f( 0.5, -0.5,  0.5);
   glVertex3f( 0.5,  0.5,  0.5);
   glVertex3f( 0.5,  0.5, -0.5);
   glVertex3f( 0.5, -0.5, -0.5);
   glEnd();
   glPopMatrix();
}

// Allocate space for maze
maze* allocate_maze()
{
   maze* new_maze;
   new_maze = (maze*)malloc(sizeof(maze));
   if(new_maze != NULL)
   {
      return new_maze;
   }
   else
   {
      fatal_error("Unable to allocate maze!");
   }
}

// Allocate space for maze cells of width,height
byte** allocate_cells(const byte width, const byte height)
{
   byte error = false;
   byte** new_cells;
   new_cells = (byte**)malloc(height*sizeof(byte*));
   if(new_cells != NULL)
   {
      byte y;
      for(y=0; y<height; ++y)
      {
         new_cells[y] = (byte*)malloc(width*sizeof(byte));
         if(new_cells[y] == NULL)
         {
            fatal_error("Unable to allocate cells!");
         }
      }
      return new_cells;
   }
   fatal_error("Unable to allocate cells!");
}

// Initialize maze allocation
maze* init_maze(const byte width, const byte height)
{
   maze* this_maze;
   if(width%2 == 1 && height%2 == 1)
   {
      this_maze = allocate_maze();
      this_maze->m_cells = allocate_cells(width, height);
      this_maze->m_width = width;
      this_maze->m_height = height;
   }
   else
   {
      fatal_error("Mazes cannot be of even dimension!");
   }
   return this_maze;
}

// Fill maze with random color index values
void fill_maze(maze* this_maze)
{
   byte x, y;
   for(y=0; y < this_maze->m_height; ++y)
   {
      for(x=0; x < this_maze->m_width; ++x)
      {
        this_maze->m_cells[y][x] = (rand()%255)+1;
      }
   }
}

// Check if x,y is within maze
byte in_bounds(maze* this_maze, const byte x, const byte y)
{
   if(x>0 && x<this_maze->m_width-1 && y>0 && y<this_maze->m_height-1)
   {
      return true;
   }
   else
   {
      return false;
   }
}

// Count empty neighbors of cell at x,y
byte neighbor_count(maze* this_maze, const byte x, const byte y)
{
   byte n_count=0;
   if(in_bounds(this_maze, x, y))
   {
      if(this_maze->m_cells[y+1][x] == 0) n_count+=1;
      if(this_maze->m_cells[y-1][x] == 0) n_count+=1;
      if(this_maze->m_cells[y][x+1] == 0) n_count+=1;
      if(this_maze->m_cells[y][x-1] == 0) n_count+=1;
   }
   return n_count;
}

// Generate maze paths using recursive neighbor count algorithm
void generate_maze(maze* this_maze, const byte x, const byte y)
{
   if(in_bounds(this_maze, x, y) && this_maze->m_cells[y][x] != 0)
   {
      if(neighbor_count(this_maze, x, y) < 2)
      {
         this_maze->m_cells[y][x] = 0;
         byte i;
         for(i=0; i<3; ++i)
         {
            if(rand()%2) generate_maze(this_maze, x-1, y);
            else         generate_maze(this_maze, x+1, y);
            if(rand()%2) generate_maze(this_maze, x, y-1);
            else         generate_maze(this_maze, x, y+1);
         }
      }
   }
}

// Render maze using cubes (not if cell is 0)
void render_maze(maze* this_maze)
{
   byte x, y, c;
   for(y=0; y < this_maze->m_height; ++y)
   {
      for(x=0; x < this_maze->m_width; ++x)
      {
         c = this_maze->m_cells[y][x];
         if(c != 0)
         {
            render_cube(x, y, c-1);
         }
      }
   }
}

// Deallocate memory used for maze
void free_maze(maze* this_maze)
{
   byte y;
   for(y=0; y<this_maze->m_height; ++y)
   {
      free( this_maze->m_cells[y] );
   }
   free( this_maze->m_cells );
   free( this_maze );
}

// Check SDL event stack
byte events()
{
   SDL_Event event;
   if( SDL_PollEvent(&event) )
   {
      switch( event.type )
      {
         case SDL_KEYDOWN : key[ event.key.keysym.sym ]=true ;   break;
         case SDL_KEYUP   : key[ event.key.keysym.sym ]=false;   break;
         case SDL_QUIT    : return false; break;
      }
   }
   return true;
}

int main(int argc, char** argv)
{
   if(argc != 3)
   {
      fatal_error("Incorrect number of arguments!");
   }

   byte width = atoi(argv[1]);
   byte height = atoi(argv[2]);

   srand(time(NULL));

   maze* test_maze;
   SDL_Surface* buffer;

   init(buffer, 640, 400);

   test_maze = init_maze(width, height);

   fill_maze(test_maze);

   generate_maze(test_maze, width>>1, height>>1);

   // Generate color index from random values
   byte i, i2;
   for(i=0; i<255; ++i)
   {
      for(i2=0; i2<3; ++i2)
      {
         color_map[i][i2] = (rand()%155)+100;
      }
   }

   // Main render loop
   float angle = 0, x=width>>1, z=height>>1;
   while( events() && !key[SDLK_ESCAPE] )
   {
      glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
      glLoadIdentity();
      glRotatef(-angle, 0, 1, 0);
      glTranslatef(-x, 0, -z);
      render_maze(test_maze);
      SDL_GL_SwapBuffers();
      if( key[SDLK_UP  ] )
      {
         z -= cos(angle*DEG2RAD) * 0.05;
         x -= sin(angle*DEG2RAD) * 0.05;
      }

      if( key[SDLK_DOWN] )
      {
         z += cos(angle*DEG2RAD) * 0.05;
         x += sin(angle*DEG2RAD) * 0.05;
      }

      if( key[SDLK_RIGHT] ) angle-=2;
      if( key[SDLK_LEFT ] ) angle+=2;
   }

   // Release used memory
   free_maze(test_maze);
}

```

Compile it with...

```

gcc something.c -lSDL -lGLU -lGL

```

Execute with...
```

./a.out width height

```

If it's too fast, user higher dimensions, if it's to slow, use lower dimensions.

I find "./a.out 55 55" to be a good size for my computer.

There's no collision or anything, just a simple render and walkthrough.

Directional keys steer/move

You need the SDL and OpenGL dev files to compile!

---

### Post by yaaarrrgg on 2007-03-05
Hmm... doing a simple ASCII maze was a bit tricker than I initally thought, but not that bad overall.  I've never used Python before, so this was a good excuse to try :)

Here's my algorithm with comments... 

```

#!/usr/bin/env python

# ASCII MAZE GENERATOR

    # # # # # # # # #   # 
    #   #               # 
    #   #   #   # # # # # 
    #   #   #       #   # 
    #   # # # # #   #   # 
    #                   # 
    # # # # # # # # #   # 
    #                   # 
    # # #   #   # # # # # 
    #       #           # 
    #   # # # # # # # # # 

# use:
#     python maze.py [width] [height]
#
# or, to control game difficulty, change the length of long straight corridors
#
#     python maze.py [width] [height] [min_wall_length] [max_wall_length]
#

# About the Algorithm: after thinking about it a bit, I realized that a maze is 
# topologically equivalent to a rectangle.. In other words, we can start with a
# rectangle and stretch (or distort) the edges into the middle of the rectangle.
# Repeating this will never bisect the plane; any two points will be connected
# through only one path.  We continue this until all possible distortions of the
# rectangle are exhausted for a given grid.  Poking two holes in the edge will 
# ensure there is only one solution, or path connecting them.
#
# This is of course not the simplest algorithm, but was selected for the
# game play.  It will produce long, winding corridors, for "easier" mazes.
#
#
# Kevin Seifert 2007 GPL

import random
import sys

random.seed()

# default grid size 
m = 10 
n = 10

# read grid size from args if available
if len( sys.argv ) > 2:
    m = int( sys.argv[ 1 ] )
    n = int( sys.argv[ 2 ] )

# game constants (note: there's actually 2m +1, but using this for zero index)
BOARD_X_MAX = 2 * m 
BOARD_Y_MAX = 2 * n 

# for aesthetics, and game difficultly, constrain edge lengths boundaries
# for edge drawn
BOARD_WANDER_MIN =  2
BOARD_WANDER_MAX =  4

# can roughly control game difficultly: smaller paths == more difficult
# as ther is more resolution for tighter curves
if len( sys.argv ) > 4:
    BOARD_WANDER_MIN = int( sys.argv[ 3 ] )
    BOARD_WANDER_MAX = int( sys.argv[ 4 ] )

SPACE         = ' '
WALL          = '#'
ILLEGAL_VALUE = '.'
ILLEGAL_POINT = ( -4 , -4 ) # four is right out

# init board with spaces
# this will hold both "edge" data and "path" data
board = [ [SPACE for i in xrange( BOARD_X_MAX + 1 )] \
            for j in xrange( BOARD_Y_MAX + 1 )]

# build a list of possible wall "seeds" 
possible_moves = []
for j in xrange( 1, n ):
    for i in xrange( 1, m ):
        tmpx = i * 2; 
        tmpy = j * 2; 
        possible_moves.append( ( tmpx , tmpy ) ); 

# -- end init game subs below --

# tests whether x, y is in grid
def point_valid(x,y):
    return x >= 0 and x <= BOARD_X_MAX \
                and y >= 0 and y <= BOARD_Y_MAX

# sets the value of grid at x,y
def set_point(x , y , value):
    if point_valid(x,y):
        board[y][x] = value

# gets the value of grid at x,y
def get_point(x , y):
    if point_valid(x,y):
        return board[y][x]
    
    else: 
        return ILLEGAL_VALUE

#draws rectangular frame around the grid 
# poke two holes top and bottom (inset)
def create_frame():
    for i in xrange(BOARD_X_MAX + 1 ):
        set_point( i , 0 , WALL )
        set_point( i , BOARD_Y_MAX , WALL )

    for j in xrange( BOARD_Y_MAX + 1 ):
        set_point( 0 , j , WALL )
        set_point( BOARD_X_MAX , j , WALL )
   
    #poke holes in top and bottom
    set_point( BOARD_X_MAX - 1 , 0, SPACE )
    set_point( 1 , BOARD_Y_MAX, SPACE )


# returns a starting point 
# remember that edges and paths are intereleaved
# so this will only test every other row
def get_open_end():
    # pick one randomly 
    count = len( possible_moves )
    if count > 0:
        pick = random.randint( 0 , count - 1 ) 
        return possible_moves[ pick ]
    else:
        return ILLEGAL_POINT 


#get a random change in x, y, from the set [ -1 , 0 , 1 ] 
# in all four directions, diagonals not allowed
def get_delta( ):
    # ranomly pick opposite dx, dy
    dx = random.randint( 0, 1 )
    dy = 1 - dx
    # flip half the time
    if random.randint( 0, 1 ):
        dx = dx * -1
        dy = dy * -1 
    return (dx, dy)

# will return a delta that is different from delta old
# path will be biased away from old direction
def get_delta_not( delta_old ):
    delta_new = get_delta()
    if delta_new != delta_old:
        return delta_new
    else:
        # flip if the same
        ( dx, dy ) = delta_new 
        dx = dx * -1
        dy = dy * -1
        return (dx, dy)

# picks a point and wanders around
# returns 0 if grid is exhausted 
# contrain path to 3 (of 4) directions so 
# it will not re-connect with itself
def wander():

    ( x, y ) = get_open_end()
    
    if not point_valid( x , y ): 
        return 0

    dx_old = -1
    dy_old = -1
        
    # get direction to walk
    delta_constraint = get_delta()
   
    while 1: 

        (dx, dy) = get_delta_not( delta_constraint )

        # don't walk back over old path
        if dx_old == ( dx * -1 ) and dy_old == ( dy * -1 ):
            dx = dx_old
            dy = dy_old

        # the max distance to be walked
        distance = 2 * ( random.randint( BOARD_WANDER_MIN , BOARD_WANDER_MAX ) ) + 1

        # walkin' down the line
        for i in xrange( distance + 1 ):

            # used point... remove from list (if exists)
            if possible_moves.count( (x, y) ) > 0  :
                possible_moves.remove( (x, y) )

            # eventually everything runs into a wall
            if get_point( x, y ) == WALL:
                return 1
           
            # otherwise draw wall 
            set_point( x, y, WALL ) 
    
            # cue up next point 
            x += dx
            y += dy

        dx_old = dx 
        dy_old = dy 


# paints board to screen
def render_board():
    for j in xrange(BOARD_Y_MAX + 1 ):
        for i in xrange(BOARD_X_MAX + 1 ):
             print board[j][i],
        print ''


# -- main game loop --
create_frame() 
repeat = 1
while repeat:
    repeat = wander()
render_board()


```


here is a sample maze ... 

```

[FONT="Courier New"]
# # # # # # # # # # # # # # # # # # #   # 
#   #   #               #           #   # 
#   #   #   #   # # # # #   # # #   #   # 
#   #   #   #   #       #   #           # 
#   #   #   #   #   # # # # # # # # #   # 
#   #       #   #   #   #           #   # 
#   # # # # #   #   #   #   # # # # #   # 
#   #   #                           #   # 
#   #   #   #   #   # # # # # # #   #   # 
#   #   #   #   #               #   #   # 
#   #   # # # # # # #   #   #   #   #   # 
#                       #   #   #       # 
# # # # # # # # # # # # # # #   #   # # # 
#                               #       # 
#   # # # # # # # # # # # # # # # # # # # 
#       #                           #   # 
#   #   #   # # # # # # # # # # # # #   # 
#   #                               #   # 
# # # # # # # # # # # # # # # # #   #   # 
#                                       # 
#   # # # # # # # # # # # # # # # # # # # 
[/FONT]
```

---

### Post by Blacktalon on 2007-03-07
Well, mine is very, very simple.  I kinda didn't have the time nor do I have the brain power to make it more complex and impressive as the others.  But none the less, I thought I would still submit it for everyone to see.
```

/**
 *  This code was writen and implemented by Blacktalon,
 *  The program is a simple, and very basic Maze implementation.
 *  All this does is prints out a randomly designed maze!  Enjoy.
 */

import java.util.*;



public class RandomMaze {
  private int x = 45;
  private int y = 25;

  public RandomMaze(){
    System.out.println("This is a very simple and basic program, all it does is randomly designs a simple maze");
    
    for(int i = 0; i<y; i++){
      
      RandomOpenings();
      if(i<(y-1)){
      System.out.println("*                                             *");
      System.out.println("*                                             *");
      }
    }
  }
  public void RandomOpenings(){
    java.util.Random rand;
    rand = new java.util.Random();
    int space = 1 + rand.nextInt(44);
   // System.out.println(space); 
    for(long j = 0; j<=x; j++){
       if(j == space)
         System.out.print("  ");
   //    else if (j == x)
     //    System.out.print("*");
       else
         System.out.print("*");
       if(j == x)
       System.out.println();
    }
  }

```

---

### Post by Wybiral on 2007-03-07
Here's my algorithm with an ncurses interface that lets you navigate the maze from the console.
Your console should be the default 80x24 size and you'll need ncurses to compile (who doesn't?)

```

#include <stdio.h>
#include <stdlib.h>
#include <ncurses.h>

typedef unsigned char byte;

typedef struct s_maze
{
   byte** m_cells;
   byte m_dim[2];
   byte m_finish[2];
} maze;

void fatal_error(char* err_str)
{
   printf("Fatal error: %s\n", err_str);
   exit(1);
}

void mov_bytes(byte* a, byte* b)
{
   a[0] = b[0];
   a[1] = b[1];
}

byte cmp_bytes(byte* a, byte* b)
{
   return a[0]==b[0] && a[1]==b[1];
}

maze* allocate_maze()
{
   maze* new_maze;
   if( new_maze = (maze*)malloc(sizeof(maze)) )
   {
      return new_maze;
   }
   else
   {
      fatal_error("Unable to allocate maze!");
   }
}

byte** allocate_cells(const byte width, const byte height)
{
   byte** new_cells;
   if( new_cells = (byte**)malloc(height*sizeof(byte*)) )
   {
      byte y;
      for(y=0; y<height; ++y)
      {
         if( !(new_cells[y] = (byte*)malloc(width*sizeof(byte))) )
         {
            fatal_error("Unable to allocate cells!");
         }
      }
      return new_cells;
   }
   fatal_error("Unable to allocate cells!");
}

maze* new_maze(const byte width, const byte height)
{
   maze* this_maze;
   this_maze = allocate_maze();
   this_maze->m_cells  = allocate_cells(width, height);
   this_maze->m_dim[0] = width;
   this_maze->m_dim[1] = height;

   byte x, y;
   for(y=0; y < this_maze->m_dim[1]; ++y)
   {
      for(x=0; x < this_maze->m_dim[0]; ++x)
      {
         this_maze->m_cells[y][x] = 1;
      }
   }
   return this_maze;
}

byte in_bounds(maze* this_maze, const byte x, const byte y)
{
   return (x>0 && x<this_maze->m_dim[0]-1 && y>0 && y<this_maze->m_dim[1]-1);
}

byte valid_cell(maze* this_maze, const byte x, const byte y)
{
   return in_bounds(this_maze, x, y) && (this_maze->m_cells[y][x]==0);
}

byte neighbor_count(maze* this_maze, const byte x, const byte y)
{
   byte n_count=0;
   if(in_bounds(this_maze, x, y))
   {
      if(!this_maze->m_cells[y+1][x]) n_count++;
      if(!this_maze->m_cells[y-1][x]) n_count++;
      if(!this_maze->m_cells[y][x+1]) n_count++;
      if(!this_maze->m_cells[y][x-1]) n_count++;
   }
   return n_count;
}

void generate_maze(maze* this_maze, const byte x, const byte y)
{
   if(in_bounds(this_maze, x, y) && this_maze->m_cells[y][x])
   {
      if(neighbor_count(this_maze, x, y) < 2)
      {
         this_maze->m_cells[y][x] = 0;
         byte i;
         for(i=0; i<3; ++i)
         {
            if(rand()%2) generate_maze(this_maze, x-1, y);
            else         generate_maze(this_maze, x+1, y);
            if(rand()%2) generate_maze(this_maze, x, y-1);
            else         generate_maze(this_maze, x, y+1);
         }
      }
   }
}

void generate_endpoints(maze* this_maze)
{
   byte x, y = this_maze->m_dim[1]-2;
   for(x=0; this_maze->m_cells[1][x] && x<this_maze->m_dim[0]-1; ++x)
   {
      this_maze->m_cells[1][x] = 0;
   }
   for(x=this_maze->m_dim[0]-1; this_maze->m_cells[y][x] && x>0; --x)
   {
      this_maze->m_cells[y][x] = 0;
   }
   this_maze->m_finish[0] = this_maze->m_dim[0]-1;
   this_maze->m_finish[1] = this_maze->m_dim[1]-2;
}

void print_color(const byte i, const byte x, const byte y, const byte* c)
{
   attron(COLOR_PAIR(i));
   mvprintw(y, x, c);
   attroff(COLOR_PAIR(i));
}

void print_maze(maze* this_maze, byte* cur_pos)
{
   byte x, y;
   for(y=0; y < this_maze->m_dim[1]; ++y)
   {
      for(x=0; x < this_maze->m_dim[0]; ++x)
      {
         if(this_maze->m_cells[y][x])
         {
            print_color(2, x, y, " ");
         }
         else
         {
            print_color(1, x, y, " ");
         }
      }
   }
   print_color(3, cur_pos[0], cur_pos[1], "#");
   refresh();
}

void free_maze(maze* this_maze)
{
   byte y;
   for(y=0; y<this_maze->m_dim[1]; ++y)
   {
      free( this_maze->m_cells[y] );
   }
   free( this_maze->m_cells );
   free( this_maze );
}

void init_ncurses()
{
   initscr();
   noecho();
   keypad(stdscr, TRUE);
   curs_set(0);
	start_color();
   init_pair(1, COLOR_BLACK, COLOR_BLACK);
   init_pair(2, COLOR_BLACK, COLOR_BLUE);
   init_pair(3, COLOR_GREEN, COLOR_BLACK);
   init_pair(4, COLOR_BLACK, COLOR_WHITE);
}

void run_maze(maze* this_maze)
{
   byte cur_pos[2]={0, 1}, new_pos[2]={0, 1}, kill = 0;
   while(!kill)
   {
      print_maze(this_maze, cur_pos);
      switch(getch())
      {
         case KEY_RIGHT: new_pos[0]++; break;
         case KEY_LEFT : new_pos[0]--; break;
         case KEY_DOWN : new_pos[1]++; break;
         case KEY_UP   : new_pos[1]--; break;
         case 27       : kill=1; break;
      }
      if(cmp_bytes(new_pos, this_maze->m_finish))
      {
         kill = 1;
      }
      else if(valid_cell(this_maze, new_pos[0], new_pos[1]))
      {
         mov_bytes(cur_pos, new_pos);
      }
      else
      {
         mov_bytes(new_pos, cur_pos);
      }
   }
}

int main(int argc, char** argv)
{
   byte width;
   byte height;

   init_ncurses();
   getmaxyx(stdscr, height, width);

   if(width>3 && height>3)
   {
      srand(time(NULL));
      maze* test_maze = new_maze(width, height);
      generate_maze(test_maze, width>>1, height>>1);
      generate_endpoints(test_maze);
      run_maze(test_maze);
      free_maze(test_maze);
   }
   endwin();

}

```

Compile with "gcc something.c -lncurses"
Execute with "./a.out"

Use the directional keys to move your guy (he starts in the top left corner, a green "#")
Press escape, or reach the end (at the bottom right corner) to exit program.

---

### Post by po0f on 2007-03-07
Wybiral,

I haven't done much ncurses programming, but couldn't you initialize curses first, then getmaxyx(stdscr, height, width) to get a maze that matches the terminal size?  (Don't ask me how to handle SIGWINCH/resize events, I didn't get that far into it.  ;))

---

### Post by Wybiral on 2007-03-07
You're right, that is much better. I updated the code.

I don't think I can make it resizable without remaking the maze (which would redo everything when you resized), I'd also have to free/reallocate all of the memory.

---

### Post by WW on 2007-03-08
If it isn't too late, here is another maze program. To run it, save the file as "hexamaze.py", and in the directory where the file is saved, run the program with the command:
>  $ python hexamaze.py
That will create a random maze of 32x24 hexagonal cells.  Starting and ending points are marked with green and red circles, respectively.

To change the size of the maze, you will have to run it like this:
>  $ python
>>> from hexamaze import *
>>> m = hexamaze(40,30,10,20)

That will create a maze with 40x30 hexagonal cells; the length of the side of each hexagon will be 10 pixels, and the border around the maze will be (at least) 20 pixels.

```

#!/usr/bin/python

#
# hexamaze.py
#

import pygame
import random
from math import sqrt

#
# The "set" data type is not built-in in Python 2.3
#
try:
    set
except NameError:
    from sets import Set as set

#
# A minimalist "graph" class
#
class graph:

    def __init__(self):
        self.edges = []
        self.nbrs = {}
        
    def add_edge(self,vertex1,vertex2):
        if (self.nbrs.has_key(vertex1)):
            self.nbrs[vertex1].append(vertex2)
        else:
            self.nbrs[vertex1] = [vertex2]
        if (self.nbrs.has_key(vertex2)):
            self.nbrs[vertex2].append(vertex1)
        else:
            self.nbrs[vertex2] = [vertex1]
        self.edges.append( (vertex1,vertex2) )
        
    def remove_edge(self,vertex1,vertex2):
        if (self.nbrs.has_key(vertex1)):
            if vertex2 in self.nbrs[vertex1]:
                self.nbrs[vertex1].remove(vertex2)
                if len(self.nbrs[vertex1]) == 0:
                    del self.nbrs[vertex1]
        if (self.nbrs.has_key(vertex2)):
            if vertex1 in self.nbrs[vertex2]:
                self.nbrs[vertex2].remove(vertex1)
                if len(self.nbrs[vertex2]) == 0:
                    del self.nbrs[vertex2]
        if (vertex1,vertex2) in self.edges:
            self.edges.remove((vertex1,vertex2))
        if (vertex2,vertex1) in self.edges:
            self.edges.remove((vertex2,vertex1))


    def neighbors(self,vertex):
        if (self.nbrs.has_key(vertex)):
            return self.nbrs[vertex]
        else:
            return []
    

class hexamaze:

    def __init__(self,rows,columns,gridsize=20,border=10):
        print "Constructing maze..."
        self.nrows = rows
        self.ncols = columns
        self.gridsize = gridsize
        self.border = border
        # wall_topology is a graph of all the possible walls
        self.wall_topology = graph()
        # walls is a graph of the actual walls in the maze that is constructed
        # walls is a subgraph of wall_topology
        self.walls = graph()
        #
        # The set have_vacant_nbrs (not a great name, I know) contains all
        # the vertices in the wall to which a new wall can be attached.
        #
        self.have_vacant_nbrs = set()
        #
        # Build the wall_topology graph.  Each edge in the graph corresponds to
        # a wall in the maze.  Each vertex in the graph is labeled as a triple
        # of (i,j) pairs, where each (i,j) denotes a cell.  The triple holds
        # the labels of the three cells that meet at the wall vertex.
        # This loop also initializes the set have_vacant_nbrs.
        #
        for j in range(self.nrows-1):
            for i in range(self.ncols-1):
                if j % 2 == 0:
                    # j is even
                    wallvertexSlr = ((i,j),(i+1,j),(i+1,j+1))
                    wallvertexSul = ((i,j),(i+1,j+1),(i,j+1))
                    wallvertexL = ((i-1,j),(i,j),(i,j+1))
                    wallvertexB = ((i+1,j-1),(i+1,j),(i,j))
                    self.wall_topology.add_edge(wallvertexSlr,wallvertexSul)
                    self.wall_topology.add_edge(wallvertexSul,wallvertexL)
                    self.wall_topology.add_edge(wallvertexSlr,wallvertexB)
                    if (i == 0):
                        # First column...
                        self.have_vacant_nbrs.add(wallvertexL)
                    if (i == self.ncols-2):
                        # Last column...
                        wallvertexR = ((i+1,j),(i+2,j+1),(i+1,j+1))
                        self.wall_topology.add_edge(wallvertexSlr,wallvertexR)
                        self.have_vacant_nbrs.add(wallvertexR)
                    if (j == 0):
                        # Bottom row...
                        self.have_vacant_nbrs.add(wallvertexB)
                    if (j == self.nrows-2):
                        # Top row...
                        wallvertexA = ((i,j+1),(i+1,j+1),(i,j+2))
                        self.wall_topology.add_edge(wallvertexSul,wallvertexA)
                        self.have_vacant_nbrs.add(wallvertexA)
                else:
                    # j is odd
                    wallvertexSll = ((i,j),(i+1,j),(i,j+1))
                    wallvertexSur = ((i+1,j),(i+1,j+1),(i,j+1))
                    wallvertexL = ((i,j),(i,j+1),(i-1,j+1))
                    wallvertexB = ((i,j-1),(i+1,j),(i,j))
                    self.wall_topology.add_edge(wallvertexSll,wallvertexSur)
                    self.wall_topology.add_edge(wallvertexSll,wallvertexL)
                    self.wall_topology.add_edge(wallvertexSll,wallvertexB)
                    if (i == 0):
                        # First column...
                        self.have_vacant_nbrs.add(wallvertexL)
                    if (i == self.ncols-2):
                        # Last column...
                        wallvertexR = ((i+1,j),(i+2,j),(i+1,j+1))
                        self.wall_topology.add_edge(wallvertexSur,wallvertexR)
                        self.have_vacant_nbrs.add(wallvertexR)
                    if (j == self.nrows-2):
                        # Top row...
                        wallvertexA = ((i,j+1),(i+1,j+1),(i+1,j+2))
                        self.wall_topology.add_edge(wallvertexSur,wallvertexA)
                        self.have_vacant_nbrs.add(wallvertexA)
        #
        # Build the maze graph, with all possible connections (i.e. with
        # no walls.  Later, connections will removed as walls are added.
        #
        self.maze = graph()
        for j in range(self.nrows-1):
            for i in range(self.ncols-1):
                self.maze.add_edge((i,j),(i,j+1))
                self.maze.add_edge((i,j),(i+1,j))
                if i == self.ncols-2:
                    self.maze.add_edge((i+1,j),(i+1,j+1))
                if j % 2 == 0:
                    # j is even
                    self.maze.add_edge((i,j),(i+1,j+1))
                else:
                    # j is odd
                    self.maze.add_edge((i+1,j),(i,j+1))
                if j == self.nrows-2:
                    # top row...
                    self.maze.add_edge((i,j+1),(i+1,j+1))
                    
        self.build_maze()
        print "Choosing a start point..."
        self.maze_start = self.find_deadend((0,0))
        print "Choosing a finish point..."
        self.maze_finish = self.find_farthest(self.maze_start)
        print "Plotting the maze..."
        screen_width = 2*border + int(self.gridsize*(sqrt(3)*(self.ncols+0.5)))
        screen_height = 2*border + int(self.gridsize*(1.5*self.nrows + 0.5))
        self.plotinit(screen_width,screen_height)
        self.plot()
        
    def candidates_for_connection(self,v):
        # Get the list of possible neighbors of the wall vertex v
        vnbrs = self.wall_topology.neighbors(v)
        # Find the vertices in vnbrs that have no neighbors, put the result in u
        u = []
        for n in vnbrs:
            if len(self.wall_topology.neighbors(n)) > 1 and self.walls.neighbors(n) == []:
                u.append(n)
        return u

    def build_a_wall(self,vstart):
        n = self.candidates_for_connection(vstart)
        while (n != []):
            vnext = random.choice(n)
            self.walls.add_edge(vstart,vnext)
            e = self.maze_edge_from_wall_vertices(vstart,vnext)
            self.maze.remove_edge(e[0],e[1])
            vnext_nbrs = self.wall_topology.neighbors(vnext)
            for v in vnext_nbrs:
                if (v in self.have_vacant_nbrs and self.candidates_for_connection(v)==[]):
                    # Remove v from self.have_vacant_nbrs
                    self.have_vacant_nbrs.remove(v)
            vstart = vnext
            n = self.candidates_for_connection(vnext)
            if (n != []):
                self.have_vacant_nbrs.add(vnext)
            
    def build_maze(self):
        while len(self.have_vacant_nbrs) > 0:
            vstart = random.choice(list(self.have_vacant_nbrs))
            self.have_vacant_nbrs.remove(vstart)
            self.build_a_wall(vstart)

    def maze_edge_from_wall_vertices(self,v1,v2):
        e = []
        for x in v1:
            if x in v2:
                e.append(x)
        return e

    def find_deadend(self,v):
        n = self.maze.neighbors(v)
        while len(n) > 1:
            v = random.choice(n)
            n = self.maze.neighbors(v)
        return v
    
    def next_level_set(self, levelset):
        nextlevelset = set()
        for z in levelset:
            v1 = z[0]
            v2 = z[1]
            nbrs = self.maze.neighbors(v2)
            nbrs.remove(v1)
            for n in nbrs:
                nextlevelset.add((v2,n))
        return nextlevelset
         
    def find_farthest(self,v):
        vnbrs = self.maze.neighbors(v)
        levelset = set()
        for n in vnbrs:
            levelset.add((v,n))
        nextlevelset = self.next_level_set(levelset)
        while len(nextlevelset) > 0:
            levelset = nextlevelset
            nextlevelset = self.next_level_set(levelset)
        pick = random.choice(list(levelset))
        return pick[1]
                
        
    def plotinit(self,width,height):
        pygame.init()
        self.screen = pygame.display.set_mode((width,height),1)
        pygame.display.set_caption("Hexamaze")
        
    def testplot(self):
        self.screen.fill((255,255,255))
        x0 = 10
        y0 = 10
        for e in self.maze.edges:
            p1 = e[0]
            p2 = e[1]
            x1 = x0+p1[0]*15
            y1 = y0+p1[1]*15
            x2 = x0+p2[0]*15
            y2 = y0+p2[1]*15
            pygame.draw.line(self.screen,(0,0,0),[x1,y1],[x2,y2],1)
        pygame.display.flip()

    def maze_vertex_to_screen_coords(self,v):
        i = v[0]
        j = v[1]
        p = j % 2
        x = self.border + self.gridsize*(0.5*sqrt(3)*(2-p) + i*sqrt(3))
        y = self.border + self.gridsize*(1+j*1.5)
        return (x,y)

    def draw_wall_between(self,v1,v2):
        sv1 = self.maze_vertex_to_screen_coords(v1)
        sv2 = self.maze_vertex_to_screen_coords(v2)
        mid = map( (lambda x,y: (x+y)/2.0), sv1, sv2)
        dir = (-(sv1[1]-sv2[1])/sqrt(3),(sv1[0]-sv2[0])/sqrt(3))
        swv1 = map( (lambda x,y: (x+(0.5*y)) ), mid, dir)
        swv2 = map( (lambda x,y: (x-(0.5*y)) ), mid, dir)
        pygame.draw.aaline(self.screen,(0,0,0),swv1,swv2,1)        
                
    def plot(self):
        self.screen.fill((255,255,255))
        # Draw the walls defined in the walls graph.
        for w in self.walls.edges:
            wv1 = w[0]
            wv2 = w[1]
            maze_edge = self.maze_edge_from_wall_vertices(wv1,wv2)
            mv1 = maze_edge[0]
            mv2 = maze_edge[1]
            self.draw_wall_between(mv1,mv2)
        # Draw the "permanent" walls that make up the boundary of the maze.
        p = self.nrows % 2
        for i in range(self.ncols):
            # bottom walls...
            self.draw_wall_between((i,0),(i,-1))
            self.draw_wall_between((i,0),(i+1,-1))
            # top walls...
            self.draw_wall_between((i,self.nrows-1),(i,self.nrows))
            if (p == 0):
                # even number of rows...
                self.draw_wall_between((i,self.nrows-1),(i-1,self.nrows))
            else:
                # odd number of rows...
                self.draw_wall_between((i,self.nrows-1),(i+1,self.nrows))
        # side walls...
        for j in range(self.nrows):
            self.draw_wall_between((0,j),(-1,j))
            self.draw_wall_between((self.ncols-1,j),(self.ncols,j))
            if (j % 2) == 0:
                # j is even
                self.draw_wall_between((self.ncols-1,j),(self.ncols,j+1))
                self.draw_wall_between((self.ncols-1,j),(self.ncols,j-1))
            else:
                # j is odd
                self.draw_wall_between((0,j),(-1,j+1))
                self.draw_wall_between((0,j),(-1,j-1))
        start = self.maze_vertex_to_screen_coords(self.maze_start)
        finish = self.maze_vertex_to_screen_coords(self.maze_finish)
        pygame.draw.circle(self.screen,(0,255,0),[int(start[0]),int(start[1])],int(0.5*self.gridsize),0)
        pygame.draw.circle(self.screen,(255,0,0),[int(finish[0]),int(finish[1])],int(0.5*self.gridsize),0)
        pygame.display.flip()

if __name__ == "__main__":
    m = hexamaze(32,24,12,10)
    s = raw_input("Hit Enter to exit. ")

```

---

### Post by WW on 2007-03-08
Blacktalon:

When you include computer code in a forum post, it is a good idea to put it inside [ code ] and [ /code ] tags.  That is, edit your post like this:

[ code ]
...your program here...
[ /code ]

but don't include the spaces inside the square brackets--I only put the space in so my example *wouldn't* be processed like actual code.  When you include your code this way, the forum software will not mess up the indentation. Your code wll be easier to read and to cut-and-paste if someone wants to run it.

---

### Post by Wybiral on 2007-03-08
WW, that hexagonal based maze is really cool looking!

---

### Post by Wybiral on 2007-03-10
It's Saturday... Someone should post a new challenge!

---

### Post by Mr. C. on 2007-03-10
Anyone up for a Sudoku solver?

---

### Post by Wybiral on 2007-03-10
I've never played Sudoku, but I guess this could be a good chance to learn. You should post that as this weeks challenge.

---

### Post by alberto ferreira on 2008-10-20
WW python's hexamaze gives this error:

>  File "hexamaze.py", line 76
    self.walls = graph()
    ^
IndentationError: unexpected indent


And if I use the downloaded version the following occurs:
> Traceback (most recent call last):
  File "hexamaze.py", line 7, in <module>
    import pygame
ImportError: No module named pygame

HOW do i solve it :( ?

---

### Post by WW on 2008-10-20
Alberto,

To be sure there isn't a problem with the code that I posted, I just copied it back to my computer and ran it.  It still works for me, so check that you didn't accidentally change the spacing at lines 75-80 when you copied the file.

To get pygame in Ubuntu, install the package [python-pygame](http://packages.ubuntu.com/hardy/python-pygame).

---

### Post by ratmandall on 2008-10-20
> **alberto ferreira said:**
> WW python's hexamaze gives this error:




And if I use the downloaded version the following occurs:

HOW do i solve it :( ?

Unindent that line, and you will need pygame module installed.

---

### Post by alberto ferreira on 2008-10-23
Ok now, the whole program got screwed because when I pasted it in the terminal the terminal formatted it to fit in it's screen (the code) so ....


Anyways, awesome!!!

Can't you play?? You've got to add that! :D

---

### Post by WW on 2008-10-24
> **alberto ferreira said:**
> 
Anyways, awesome!!!

Thanks!
> **alberto ferreira said:**
> 
Can't you play?? You've got to add that! :D
I did create a version that let's you move around the maze, with sound effects for moving, bumping into walls, and reaching the end.  It still needs work, but when it is ready, I'll make it available somewhere.

---

