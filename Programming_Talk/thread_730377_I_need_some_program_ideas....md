---
title: "I need some program ideas..."
date: 2008-03-20
forum: Programming Talk
---

### Post by Yes on 2008-03-20
I'm trying to learn python, and am running into a problem -  I can't seem to learn just by reading the tutorial.  So does anyone know of a website that has example programs in Python, that won't be over my head (I only know the basics -  lists, functions, etc.).

Thanks!

---

### Post by LaRoza on 2008-03-20
see the sticky and pmasiar's sig.

---

### Post by |{urse on 2008-03-20
[http://www.daniweb.com/code/python.html]("http://www.daniweb.com/code/python.html")

that site has tons of stuff for beginners

Heres a good one that teaches simple recursion

      # Fibonacci number series
       
      def fibonacci():
      """a generator for Fibonacci numbers, goes to next number in series on each call"""
      a, b = 0, 1
      while True:
      yield a
      a, b = b, a + b
      f = fibonacci()
      for x in range(13):
      print f.next(), # 0 1 1 2 3 5 8 13 21 34 55 89 144
      print
      def fibo(n):
      """
      use recursion to get Fibonacci numbers, returns the Fibonacci value for n
      not very efficient because of the many function calls
      """
      if n < 2:
      return n
      else:
      return fibo(n - 1) + fibo(n - 2)
      for x in range(13):
      print "fibo(%d) = %d" % (x, fibo(x))
      print
      print "Calculating ..."
      print
      print "fibo(%d) = %d" % (30, fibo(30)) # this takes a moment!

---

### Post by pmasiar on 2008-03-20
another good source of samples is ActionState's recipe cookbook: [http://aspn.activestate.com/ASPN/Python/Cookbook/](http://aspn.activestate.com/ASPN/Python/Cookbook/)

But looking at examples will not teach you writing your own code: you need to write code, solve simple problems. Wiki in my sig has some.

---

