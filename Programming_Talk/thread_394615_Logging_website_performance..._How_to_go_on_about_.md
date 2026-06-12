---
title: "Logging website performance... How to go on about it?"
date: 2007-03-27
forum: Programming Talk
---

### Post by cunawarit on 2007-03-27
I’ve bee assigned to figure out how fast our website is running. A programmer here has the wild idea that every page request should be logged into the DB, this is theoretically possible, I think... It would involve overriding the first and last method on the page lifecycle and entering data there. However, I think this is a truly crappy thing to do as we will be slowing the site down by all the unnecessary DB access, and we won’t be able to tell why a page is slow (what in that page is slowing it down, is it a particular image, is it the DB, is it a stupidly long table, etc…)

Anyway, what is the usual way of testing the overall speed of a website?

---

### Post by lnostdal on 2007-03-27
Hm .. you've got things like ApacheBench ..

But I think you might want to do some profiling in this case. This means measuring how much time of a request-response cycle is spent in each function of your code.

You can do this when the site has only a little traffic (because there is some overhead doing this), or you can do it with a copy of the site (something you probably already have for development etc.).

Here is how I do something like this using SBCL ([profiling from the manual]("http://www.sbcl.org/manual/Profiling.html")) and a somewhat simplified example:

```

;; Which of these three are worst?
;; It is easy to tell here that `func3' is slowest doing only one call,
;; but is it really where most time is spent when these are used from
;; application code?

(defun func1 ()
  (dotimes (i 10000)
    ))

(defun func2 ()
  (dotimes (i 20000)
    ))

(defun func3 ()
  (dotimes (i 30000)
    ))


(defun test (num-tests)
  ;; We tell the profiler what to monitor here.
  (sb-profile:profile func1 func2 func3)
  
  (dotimes (i num-tests)
    ;; Call func1 three times for each iteration.
    (dotimes (j 3)
      (func1))
    ;; Call func2 two times for each iteration.
    (dotimes (j 2)
      (func2))
    ;; Call func3 once for each iteration.
    (func3))
  
  ;; We tell the profiler to print a report here.
  (sb-profile:report) 
  (sb-profile:unprofile))



#|
A run looks like this:

cl-user> (test 5000)
  seconds  | consed |  calls |  sec/call  |  name  
-----------------------------------------------------
     1.440 |  6,576 | 10,000 |   0.000144 | func2
     1.165 |      0 | 15,000 |   0.000078 | func1
     1.148 |      0 |  5,000 |   0.000230 | func3
-----------------------------------------------------
     3.753 |  6,576 | 30,000 |            | Total

estimated total profiling overhead: 0.07 seconds
overhead estimation parameters:
  4.e-8s/call, 2.168e-6s total profiling, 7.6e-7s internal profiling
nil


..so even though `func3' is the slowest one of them per call (2.3e-4), it is
`func2' you will gain most by optimizing and it is in `func2' the
performance problem of the application represented by `test' is.

It sorts the results in the leftmost column in ascending order.
|#

```

It's easy and downright fun to figure out where most time is spent using this stuff. I bet your favourite language or environment has something similar.  

(edit: if not, your company can hire me and i'll help you migrate to SBCL (native optimizing compilation - blazingly fast!) and PostgreSQL .. :P)

---

### Post by Frosty Cold Drink on 2007-03-27
> **cunawarit said:**
> I&#8217;ve bee assigned to figure out how fast our website is running. A programmer here has the wild idea that every page request should be logged into the DB, this is theoretically possible, I think... It would involve overriding the first and last method on the page lifecycle and entering data there. However, I think this is a truly crappy thing to do as we will be slowing the site down by all the unnecessary DB access, and we won&#8217;t be able to tell why a page is slow (what in that page is slowing it down, is it a particular image, is it the DB, is it a stupidly long table, etc&#8230;)

Anyway, what is the usual way of testing the overall speed of a website?

This is horribly unnecessary! Its easy enough to corelate groups of requests in the apache logs. All you need to do is add the request time to the logs, and, along with bytes in and out, you can do some decent log analysis for performance. The substitution is %D, and you'll need ot use the LogFormat or CustomLog directive.

See more here: [http://httpd.apache.org/docs/2.0/mod/mod_log_config.html#formats](http://httpd.apache.org/docs/2.0/mod/mod_log_config.html#formats)

Edit: For the database side, run your queries with EXPLAIN, assuming you are using MySQL. Also, again if using MySQL, enable the slow query log: [http://dev.mysql.com/doc/refman/5.1/en/slow-query-log.html](http://dev.mysql.com/doc/refman/5.1/en/slow-query-log.html)

---

### Post by cunawarit on 2007-03-27
> **Frosty Cold Drink said:**
> This is horribly unnecessary!

Believe me, I know!!!

I seem to have convinced the guy I am working with that we should be looking at the logs, without telling him that his idea is... Mmmm, not that good… Anyway, the performance hang-ups seem to be in the DB.

---

