---
title: "[Java] Generics weirdness"
date: 2009-01-19
forum: Programming Talk
---

### Post by CptPicard on 2009-01-19
This is odd. I have this piece of code:


```

AnalyzerBase<?,?> analyzer = null;

// Lots of stuff...

analyzer = new MVAnalyzer((Integer)opts.valueOf("n"));
if (opts.wasDetected("r"))
((MVAnalyzer)analyzer).setMultLimit((Float)opts.valueOf("r")*1000000);

// ... so on

```

Now, MVAnalyzer "extends SparseAnalyzerBase<Byte, MVAnalyzer.MVRecord>" which "extends AnalyzerBase<I, T>". So our inheritance is OK *according to Eclipse*.

Netbeans doesn't like this at all. I get a complaint of

```

/home/eneva/ActorFeeder/src/vptools/analyzer/Analyzer.java:177: inconvertible types
found   : vptools.analyzer.AnalyzerBase<capture#945 of ?,capture#446 of ?>
required: vptools.veikkaus.mv.MVAnalyzer

```

This is really annoying, as I am migrating the project over from Eclipse and I don't quite understand why an "instantiated" subclass of AnalyzerBase<?,?> is not something you could cast an AnalyzerBase<?,?> to anymore... :(

Eclipse is Ganymede and Netbeans is 6.5, both newest. System javac is 1.6.0_10; both should use it as far as I know...

---

### Post by CptPicard on 2009-01-19
Well, ok, Netbeans stops whining when you remove the generics from AnalyzerBase altogether and just use a raw type. In Eclipse it produces a warning...

[http://bugs.sun.com/bugdatabase/view_bug.do;jsessionid=f12572fdfacfaffffffff8eb858a796997eb?bug_id=4916620](http://bugs.sun.com/bugdatabase/view_bug.do;jsessionid=f12572fdfacfaffffffff8eb858a796997eb?bug_id=4916620)

Strange mismatch in behaviour anyway, and I like Eclipse's way of treating it better, as I can see situations where Netbeans' way of going about it *is* going to produce problems.

EDIT: Ok so I'm an idiot, it's a compiler setting that treats unchecked generics operations either as warnings or errors...

---

### Post by jespdj on 2009-01-20
> **CptPicard said:**
> Eclipse is Ganymede and Netbeans is 6.5, both newest. System javac is 1.6.0_10; both should use it as far as I know...
Eclipse does not use the Java compiler that's installed on your system; it has its own built-in Java compiler, based on IBM's [Jikes](http://jikes.sourceforge.net/) Java compiler.

---

