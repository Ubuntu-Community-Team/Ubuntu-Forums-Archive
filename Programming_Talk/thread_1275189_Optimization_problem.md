---
title: "Optimization problem"
date: 2009-09-25
forum: Programming Talk
---

### Post by rekahsoft on 2009-09-25
hi all, i have been working on the following problem:

"In most computer systems, a collection of &#64257;les is organized in directories. In general, a
directory contains some &#64257;les and some more directories, which are called subdirectories.
Subdirectories may contain more subdirectories and &#64257;les and so on. This organization of
&#64257;les is sometimes called a directory tree.
In this question you will implement a restricted directory tree, where a directory can have at
most two subdirectories. The data structure, dir, is a structure with the following &#64257;elds:
• name: the name of the directory (a symbol)
• &#64258;st: the list of &#64257;les in the directory (a list of symbols (an slist))
• subdir1: a subdirectory (a directory structure or empty)
• subdir2: a subdirectory (a directory structure or empty).
For example, we can create a directory tree called my-dir which has a directory called usr
containing one &#64257;le info.txt, and two subdirectories, m1 and m2 . Subdirectory m1 has no
&#64257;les, but has two subdirectories, b1 and b2 , and m2 contains a single subdirectory, b4 . This is
created by
(de&#64257;ne my-dir (make-dir ’p (cons ’info.txt empty) (make-dir ’m1 empty (make-dir ’b1 empty
empty empty) (make-dir ’b2 empty empty empty)) (make-dir ’m2 empty empty (make-dir ’b4
empty empty empty))))
Write a Scheme function get-subdirs which consumes a directory and a number, depth and
returns a list of the names of all subdirectories at that depth. For instance, given the example
above (get-subdirs my-dir 0) would return (p), (get-subdirs my-dir 1) would return (m1 m2),
(get-subdirs my-dir 2) would return (b1 b2 b4), while (get-subdirs my-dir 4) would return
().
You should try to design both a correct and ef&#64257;cient solution."

Finding a solution that is O(n^2) or O(2^n) is reasonably simple...i have been trying to work on an algorithm that will take care of computation in O(n). Here is my code:

```
#lang scheme
(provide get-subdirs example_dir)

;; dir is a structure that represents a limited directory structure where:
;;    name (a symbol) represents the name of the directory 
;;    flst (a list of symbols) represents a list of files in the directory
;;    subdir1 (empty or struct dir) represents a subdirectory
;;    subdir2 (empty or struct dir) represents a subdirectory

(define-struct dir (name flst subdir1 subdir2))

;; example dir structure used for testing and examples
(define example_dir (make-dir 'dir0 '(file0.0 file0.1)
                        (make-dir 'dir1L '(file1L.0 file1L.1) empty (make-dir 'dir2LR '(file2LR.0) empty empty))
                        (make-dir 'dir1R '(file1R.0 file1R.1 file1R.2)
                            (make-dir 'dir2RL empty empty empty)
                            (make-dir 'dir2RR '(file2RR.0 file2RR.1)
                                (make-dir 'dir2RRL empty empty empty)
                                empty))))

;;;

;; get-direct-subdirs: dir -> (listof dir)
;; Purpose: Given a dir returns a list of the subdirectories
;; Examples/Tests: See get-subdirs-driver.ss

(define (get-direct-subdirs dir)
  (cond
    [(and (empty? (dir-subdir1 dir)) (empty? (dir-subdir2 dir))) empty]
    [(empty? (dir-subdir1 dir)) (cons (dir-subdir2 dir) empty)]
    [(empty? (dir-subdir2 dir)) (cons (dir-subdir1 dir) empty)]
    [else (list (dir-subdir1 dir) (dir-subdir2 dir))]))

;;;

;; get-subdirs: dir nat -> (listof sym)
;; Purpose: Return a list of the sub-directories of a given dir structure
;; Examples/Tests: See get-subdirs-driver.ss

(define (get-subdirs dir depth)
  (define (helper current-dir-list depth subdirs)
    (cond
      [(empty? current-dir-list) empty]
      [(equal? depth 0) ...]
      [else (helper (flatten (list (dir-subdir1 dir) (dir-subdir2 dir))) (- depth 1))]))
  (helper (list dir) depth empty))
```

Now the main issue i'm having is i need to find a way to have the get-subdirs function to run in O(n)....i will write more about my idea on tackling this problem. Thanks for the help :)
i need to know what order flatten runs in (i think O(n))

---

