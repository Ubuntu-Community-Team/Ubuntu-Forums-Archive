---
title: "Programming Challenge 12 : Computational Geometry"
date: 2008-05-22
forum: Programming Talk
---

### Post by Bichromat on 2008-05-22
[SIZE="5"]In a nutshell[/SIZE]
Find convex hulls of sets of points, areas and intersections.

[SIZE="5"]Complete description[/SIZE]
You are given two sets of points (in 2D). Let's call them the red and the blue points. You need to:
[LIST]
[*] find the convex hull of each set (red hull, blue hull) and the hull of all the points (let's call it the green hull).
[*] compute their areas
[*] find the points contained in both the blue and the red hull
[*] compute the area of their convex hull (the yellow hull)
[*] compute the area of the intersection of the blue and the red hull
[/LIST]

See the attachments to have a better idea of what you're asked to do.

Of course, you cannot use external tools to do the work for you.

[SIZE="5"]Input[/SIZE]
The sets (up to 5000 points) will be read from a file (input.dat). It's better if your code accepts a filename as a command line argument. The points are given as a list of (x, y) coordinates. The two sets (red then blue) are separated by a blank line. Here is an example :

```

0.3 5.5
8.7 4.3
6.0 7.4
3.6 3.9
2.8 0.7
7.3 1.3

8.5 5.6
3.2 6.1
10.6 0.6
8.4 2.5
2.3 2.3
6.1 -2.5

```

[SIZE="5"]Output[/SIZE]
Output the areas directly on the screen or in a file 'output.dat', specifying which is which (red, blue, green, yellow, intersection).

Example output (corresponds to the example input) :
```

Red: 36.39
Blue: 45.95
Green: 59.02
Yellow: 19.46
Intersection: 25.37648

```

[SIZE="5"]Judging[/SIZE]
The entries will be judged on several criteria:
[LIST]
[*] accuracy of the areas
[*] beauty and understandability of the code
[*] aptitude to react correctly to strange input
[*] efficiency of the algorithms
[/LIST]

[SIZE="5"]Bonus points[/SIZE]
Bonus points will be awarded to people who provide graphical output of the hulls (you are allowed to use an external graphical library). Other suggestions : extend the concept in 3D (graphical output definitely needed. for slightly mad coders), turn your code into a quine (for totally insane programmers :lolflag: )

[SIZE="5"]Deadline[/SIZE]
Submit your code before **May 29, 16:00 (GMT)**.
If you submit a new version of a previously posted entry, please indicate in your first post that a new version is available.

---

### Post by AaronMT on 2008-05-22
This is interesting and looks fun. I'm going to attempt this one using either C or C++ without the visual aspect. There is a standard algorithm, **The Graham Scan** Ronald Graham's 1972 paper proposed a convex hull construction algorithm that ran in O(n·lgn) time.

---

### Post by Zeotronic on 2008-05-22
I have half a mind to do this... my project is going to force me to write most of the code required anyways... including the graphical portion.

---

### Post by Lster on 2008-05-22
I'll be entering this one as I now have the time. Woohoo! :)

---

### Post by nvteighen on 2008-05-22
Hell: Geometry...!

I'm absolutely lost in this.

---

### Post by Luke has no name on 2008-05-22
Ugh.

---

### Post by Verminox on 2008-05-23
> **nvteighen said:**
> Hell: Geometry...!

I'm absolutely lost in this.

Me too. I have no clue what hulls are. :-\

---

### Post by Lster on 2008-05-23
See this:

[http://en.wikipedia.org/wiki/Convex_hull](http://en.wikipedia.org/wiki/Convex_hull)

---

### Post by Bichromat on 2008-05-23
Wikipedia should give you all you need to know to find the convex hulls. You will also need to find how to compute areas, and a few other things. Don't worry too much about efficiency, I think all algorithms are able to deal with 5000 points in a reasonable time.

If you're stuck somewhere, don't hesitate to ask for clues :)

---

### Post by Lster on 2008-05-23
I'm enjoying this one immensely - good challenge! :)

I've still got to implement multiple sets, set merging and intersection area (of hulls).

Here's a development snapshot:

---

### Post by Bichromat on 2008-05-23
Lster : nice ! :)

---

### Post by Alasdair on 2008-05-23
Here's my far from perfect entry, it can just about handle 5000 points but not much beyond that the yellow hull fails to draw.:( I'll have to try and fix that. It doesn't allow you to input points from a file, instead you click on the canvas to add them - although if it's an absolute requirement I'll add the ability to read from a file.

It requires the LTK library and you need tk8.4 installed. I can post a binary if you like but it's a ridiculous 25mb...:)

Edit: I fixed up the algorithm for generating the yellow hull intersection (it actually works properly now).

Edit 2 : Fixed some broken error handling code...

Edit 3 : Added ability to read points from file.

Edit 4 : Now finds areas!:)

```

(defpackage #:convex-hulls
  (:use #:cl #:ltk))

(in-package #:convex-hulls)

(defparameter *red-points* nil)
(defparameter *blue-points* nil)
(defparameter *color* "blue")

(defun main ()
  (setf *wish-pathname* "/usr/bin/wish8.5")
  (setf *wish-args* '("-name" "Ubuntu Forums Programming Challenge 12"))
  (with-ltk ()
    (let* ((canvas (make-instance 'canvas
                                  :borderwidth 3
                                  :relief :groove))
           (add-blue (make-instance 'button
                                    :text "Add blue points"
                                    :command (lambda ()
                                               (setf *color* "blue"))))
           (add-red (make-instance 'button
                                    :text "Add red points"
                                    :command (lambda ()
                                               (setf *color* "red"))))
           (calculate (make-instance 'button
                                     :text "Calculate!"
                                     :command (lambda ()
                                                (display-convex-hulls canvas))))
           (clear (make-instance 'button
                                 :text "Clear canvas"
                                 :command (lambda ()
                                            (clear canvas)
                                            (setf *red-points* nil)
                                            (setf *blue-points* nil))))
           (get-points (make-instance 'button
                                      :text "Read points from file"
                                      :command (lambda ()
                                                 (load-points-dialog canvas))))
           (coords (make-instance 'label)))
      (pack canvas :expand t :fill :both)
      (pack add-blue :side :left)
      (pack add-red :side :left)
      (pack calculate :side :left)
      (pack clear :side :left)
      (pack get-points :side :left)
      (pack coords :side :left)
      (bind *tk* "<Destroy>"
            (lambda (event)
              (declare (ignore event))
              (sb-ext:quit)))
      (bind canvas "<ButtonPress>"
            (lambda (event)
              (let* ((x (event-x event))
                     (y (event-y event))
                     (point (create-oval canvas (- x 4) (- y 4) (+ x 4) (+ y 4))))
                (itemconfigure canvas point "fill" *color*)
                (setf (text coords) (format nil "~A:~A" x y))
                (if (string= *color* "blue")
                    (push (complex x y) *blue-points*)
                    (push (complex x y) *red-points*))))))))

(defun load-points-dialog (canvas)
  (let* ((path "")
         (dialog (make-instance 'toplevel :title "Open a file"))
         (file-frame (make-instance 'frame :master dialog))
         (option-frame (make-instance 'frame :master dialog :relief :groove :borderwidth 1))
         (button-frame (make-instance 'frame :master dialog))
         (path-label (make-instance 'label :master file-frame :relief :sunken :borderwidth 3))
         (scale-label (make-instance 'label :text "Scale:" :master option-frame))
         (scale (make-instance 'entry :text 1 :master option-frame :width 5))
         (center-label (make-instance 'label :text "Center:" :master option-frame))
         (center-x (make-instance 'entry  :text 0 :master option-frame :width 5))
         (center-y (make-instance 'entry  :text 0 :master option-frame :width 5))
         (select-file (make-instance 'button
                                     :text "Choose a file:"
                                     :command (lambda ()
                                                (setf path (get-open-file :filetypes '(("Points" ".dat"))))
                                                (setf (text path-label) path))
                                     :master file-frame))
         (load (make-instance 'button
                              :text "Load"
                              :command (lambda ()
                                         (handler-bind ((error
                                                         (lambda (c)
                                                           (declare (ignore c))
                                                           (invoke-restart 'skip-load))))
                                           (restart-case
                                               (read-points-from-file path
                                                                      (complex (read-from-string (text center-x))
                                                                               (read-from-string (text center-y)))
                                                                      (read-from-string (text scale)))
                                             (skip-load () (message-box "Could not load file" "Error!" :ok :error))))
                                         (draw-points *red-points* "red" canvas)
                                         (draw-points *blue-points* "blue" canvas)
                                         (destroy dialog))
                              :master button-frame))
         (cancel (make-instance 'button
                                :text "Cancel"
                                :command (lambda ()
                                           (destroy dialog))
                                :master button-frame)))
    (pack file-frame :fill :x)
    (pack option-frame :fill :x)
    (pack button-frame :fill :x)
    (pack select-file :side :left)
    (pack path-label :side :left)
    (pack scale-label :side :left)
    (pack scale :side :left)
    (pack center-label :side :left)
    (pack center-x :side :left)
    (pack center-y :side :left)
    (pack cancel :side :right)
    (pack load :side :right)))

(defun read-points-from-file (path &optional (center #C(0 0)) (scale 1))
  "read a set of points for red and blue from a file"
  (with-open-file (in path)
    (let ((line nil) (color 'red))
      (loop while (setf line (read-line in nil nil))
            do (if (string= line "")
                   (setf color 'blue)
                   (multiple-value-bind (x ypos)
                       (read-from-string line)
                     (let ((y (read-from-string line t nil :start ypos)))
                       (setf x (+ (* x scale) (realpart center)))
                       (setf y (+ (* y scale) (imagpart center)))
                       (if (eql color 'red) 
                           (push (complex x y) *red-points*)
                           (push (complex x y) *blue-points*)))))))))

(defun draw-points (points color canvas)
  (dolist (point points)
    (let* ((x (realpart point))
           (y (imagpart point))
           (point (create-oval canvas (- x 4) (- y 4) (+ x 4) (+ y 4))))
      (itemconfigure canvas point "fill" color))))

(defun display-convex-hulls (canvas)
  (handler-bind ((error
                  (lambda (c)
                    (declare (ignore c))
                    (invoke-restart 'skip-hull))))
    (let ((red-hull nil)
          (blue-hull nil)
          (green-hull nil)
          (yellow-hull nil)
          (area-text (create-text canvas 10 10 "")))
      (restart-case (progn (setf red-hull (convex-hull *red-points*))
                           (draw-convex-hull canvas red-hull "red"))
        (skip-hull () nil))
      (restart-case (progn (setf blue-hull (convex-hull *blue-points*))
                           (draw-convex-hull canvas blue-hull "blue"))
        (skip-hull () nil))
      (restart-case (progn (setf green-hull (convex-hull (append red-hull blue-hull)))
                           (draw-convex-hull canvas green-hull "green"))
        (skip-hull () nil))
      (restart-case (progn (setf yellow-hull  (convex-hull (append (interior-points *red-points* blue-hull)
                                                           (interior-points *blue-points* red-hull))))
                           (draw-convex-hull canvas yellow-hull  "yellow"))
        (skip-hull () nil))
      (itemconfigure canvas area-text :text (format nil "Area blue: ~A Area red: ~A Area Green: ~A Area Yellow: ~A"
                                                    (restart-case (hull-area blue-hull) (skip-hull () 0))
                                                    (restart-case (hull-area red-hull) (skip-hull () 0))
                                                    (restart-case (hull-area green-hull) (skip-hull () 0))
                                                    (restart-case (hull-area yellow-hull) (skip-hull () 0)))))))

(defun draw-convex-hull (canvas hull color)
  "draws a hull to a canvas"
  (labels ((draw-hull (canvas hull color)
             (let* ((x1 (realpart (car hull)))
                    (y1 (imagpart (car hull)))
                    (x2 (realpart (cadr hull)))
                    (y2 (imagpart (cadr hull)))
                    (line (create-line canvas (list x1 y1 x2 y2))))
               (itemconfigure canvas line "width" 3)
               (itemconfigure canvas line "fill" color)
               (if (not (null (cddr hull)))
                   (draw-hull canvas (cdr hull) color)))))
    (draw-hull canvas (append hull (list (car hull))) color)))

(defun find-pivot (points)
  "find the pivot point - the coordinate with the lowest y value
   if two points have the same y value, the one with the lower x value
   should be chosen"
  (loop for point in (cdr points) with pivot = (car points)
        do (cond ((< (imagpart point) (imagpart pivot))
                  (setf pivot point))
                 ((and (= (imagpart point) (imagpart pivot))
                       (< (realpart point) (realpart pivot)))
                  (setf pivot point)))
        finally (return pivot)))

(defun polar-angle (point1 point2)
  "finds the polar angle of point1 with respect to point2"
  (atan (- (imagpart point1) (imagpart point2))
        (- (realpart point1) (realpart point2))))

(defun sort-points (points pivot)
  "sorts the points according to their polar angle with the pivot"
  ;; Copy list to avoid destructive side effects
  (sort (copy-list points) (lambda (point1 point2)
                             (> (polar-angle point1 pivot)
                                (polar-angle point2 pivot)))))

(defun convex-hull (points)
  "finds a convex hull for a list of points"
  (let* ((pivot (find-pivot points))
         (points (sort-points (remove-duplicates (remove pivot points)) pivot))
         (stack nil))
    (push pivot stack)
    (push (car points) stack)
    (push (cadr points) stack)
    (loop for point in (cddr points)
          do (loop while (< (polar-angle (car stack) (cadr stack))
                            (polar-angle point (car stack)))
                   do (pop stack))
          (push point stack))
    stack))

(defun interior-points (points hull)
  "returns a list of points that are within a hull"
  (remove-if (lambda (point)
               (not (interior-point-p point hull)))
             (remove-duplicates points)))

(defun interior-point-p (point hull)
  "return t if point is within hull. it works by testing whether a line projected along
   y = (imagpos point) will intersect the hull to both the left and the right"
  (loop for hull-point in (append (cdr hull) (list (car hull)))
        with left = nil and right = nil and prev-hull-point = (car hull)
        do (if (between (imagpart point) 
                        (imagpart hull-point)
                        (imagpart prev-hull-point))
               (let ((intersect-x  (- (realpart hull-point)
                                      (handler-case 
                                          (/ (- (imagpart hull-point) (imagpart point)) 
                                             (gradient hull-point prev-hull-point))
                                        (division-by-zero () 0)))))
                 (cond ((< (realpart point) intersect-x)
                        (setf right t))
                       ((> (realpart point) intersect-x)
                        (setf left t)))))
           (setf prev-hull-point hull-point)
        finally (return (and left right))))

(defun between (n x y)
  "returns t if n is between x and y"
  (or (and (<= x n) (>= y n))
      (and (>= x n) (<= y n))))

(defun gradient (p1 p2)
  "finds the gradient between 2 points"
  (/ (- (imagpart p1) (imagpart p2))
     (- (realpart p1) (realpart p2))))

(defun hull-area (hull)
  "calculate the area of a hull by splitting it into triangles and
   using Hero's formula"
  (let ((point (car hull)))
    (labels ((calc-area (hull current-area)
               (if (null (cdr hull))
                   current-area
                   (let* ((a (dist point (car hull)))
                          (b (dist point (cadr hull)))
                          (c (dist (car hull) (cadr hull)))
                          (s (/ (+ a b c) 2)) 
                          (area (sqrt (* s (- s a) (- s b) (- s c)))))
                     (calc-area (cdr hull) (+ current-area area))))))
      (calc-area (cdr hull) 0))))

(defun dist (p1 p2)
  (sqrt (+ (expt (- (imagpart p1) (imagpart p2)) 2)
           (expt (- (realpart p1) (realpart p2)) 2))))

```

---

### Post by Lster on 2008-05-23
Wow; that's really nice!

What algorithm are you using, Alasdair?

---

### Post by Bichromat on 2008-05-23
Alasdair : could you tell me exactly how to run your code ?

---

### Post by Alasdair on 2008-05-23
> **Lster said:**
> Wow; that's really nice!

What algorithm are you using, Alasdair?

I'm using a Graham scan for the convex hulls and for the point in polygon algorithm used for computing the points for the yellow hull, I came up with my own simple algorithm (though probably not original) that's somewhat similar to the [even-odd raycasting algorithm]("http://en.wikipedia.org/wiki/Point_in_polygon#Ray_casting_algorithm"). Since it's a convex polygon, you don't need to check how many times the ray intersects with the hull, just that it intersects at least once both to the right and to the left of the point.

> **Bichromat said:**
> Alasdair : could you tell me exactly how to run your code ?
Firstly you need to install sbcl and tk8.4, which you should be able to do just by running:```
sudo apt-get install sbcl tk
```
Then visit [the ltk website]("http://www.peter-herth.de/ltk/"), download the latest version and extract it somewhere.

Now to get sbcl to see ltk, you need to add it to sbcl's asdf central registry. To do this open the file '/home/your-user-name/.sbclrc' (it probably won't exist, so create it) and add the following line with the correct directory:```
(push "/path/to/directory/where/you/put/ltk/" asdf:*central-registry*)
```
Now open up a terminal and type sbcl, once you see the * prompt, type the following:
```
(asdf:oos 'asdf:load-op :ltk)
```
then:
```
(load "/path/to/challenge/entry.lisp")
```
and finally:
```
(save-lisp-and-die challenge12 :toplevel #'convex-hulls::main :executable t)
```
You should now have a working executable copy of my program called challenge12 in your home directory, assuming I didn't miss out any steps.

---

### Post by Bichromat on 2008-05-24
OK, quotes are missing around "challenge12" in your last command, but I managed to get it to work. It looks nice ! I will test the results with a set of files so yes, your code should read the coordinates from a file.

---

### Post by Lau_of_DK on 2008-05-24
> **Alasdair said:**
> Here's my far from perfect entry,

Thank you so much for that post (+ #15). Very easy to follow code, in a language than can otherwise be difficult to pick up! Well done!

/Lau

---

### Post by Alasdair on 2008-05-24
> **Bichromat said:**
> OK, quotes are missing around "challenge12" in your last command, but I managed to get it to work. It looks nice ! I will test the results with a set of files so yes, your code should read the coordinates from a file.
Ok, I'll add that in later today if I have time.

> **Lau_of_DK said:**
> Thank you so much for that post (+ #15). Very easy to follow code, in a language than can otherwise be difficult to pick up! Well done!
Thank you very much.:)

---

### Post by Alasdair on 2008-05-26
No more entries yet? :(

Anyway I added the ability to read the points from a file, see my first post for the code and a screenshot of it in action.

---

### Post by Lster on 2008-05-26
I hope mine will be done in time. I haven't had time to further develop my solution as I've been too busy! I'll submit something but I don't know how advanced it will be! :)

---

### Post by Bichromat on 2008-05-27
Two days (and a half) left !

---

### Post by Lster on 2008-05-27
Two and a half hours is all I need. ;)

---

### Post by Lster on 2008-05-29
Fun challenge just I had no time. Here is my unfinished solution:

... See my later post; I have updated my solution.

---

### Post by Bichromat on 2008-05-29
Lster : your code does not handle floating point coordinates, and fails to compute the areas when given negative coordinates.

So far, none of the entries are able to provide the expected output :(

---

### Post by Alasdair on 2008-05-29
Well I just updated my code to find the areas, so it now does pretty much everything you asked for, minus a few little features... The attached screenshot shows my program running next to Lster's with the same input.

---

### Post by Lster on 2008-05-29
[QUOTE=Bichromat]Lster : your code does not handle floating point coordinates, and fails to compute the areas when given negative coordinates.

So far, none of the entries are able to provide the expected output :([/QUOTE]

Indeed. Support for both would be trivial to implement but was not specified. I do admit that both floating point and negative coordinates were given in your example point list, though.

---

### Post by Bichromat on 2008-05-29
> **Alasdair said:**
> Well I just updated my code to find the areas, so it now does pretty much everything you asked for, minus a few little features... The attached screenshot shows my program running next to Lster's with the same input.
Nice! It gives pretty good results. There's a small loss of precision here and there, I think this is because Lisp uses single precision floats by default.

---

### Post by Lster on 2008-05-29
Probably too late, but:

EDIT: Fixed typos and tweaked the code.

EDIT 2: Fixed a bug that would cause a segmentation fault if some invalid input was given.

---

### Post by Bichromat on 2008-05-29
The winner of this challenge is **Alasdair** :)
While it does not compute the area of the intersection of the red and blue hulls and I couldn't get it to display properly vertices with negative coordinates (but graphical output was not compulsory anyway), his entry comes closer to the expected result.

Alasdair, it's your turn now !

---

### Post by Lster on 2008-05-29
Congrats Alasdair! :popcorn:

I'm looking forwards to the next challenge!

---

