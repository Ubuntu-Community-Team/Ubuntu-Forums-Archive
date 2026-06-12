---
title: "Most beautiful piece of code you've ever seen."
date: 2010-10-09
forum: Programming Talk
---

### Post by fredscripts on 2010-10-09
Hi there!

I was wondering which was that little piece of code (4-5 lines maximum) that really made you feel like "that's really a beautiful, creative and elegant piece of code".

Mine was this way of checking if a number is prime using a regex written in perl by Abigail at comp.lang.perl.misc.

```
perl -le 'print "PRIME" if (1 x shift) !~ /^1?$|^(11+?)\1+$/' 1234
```

Note that I'm not meaning any obfuscated code or simple tasks in a really confusing way just to confuse the reader, instead I mean a different way of looking at a problem that caused your attention and admiration.

Thanks for participating! I found this an interesting thread!

---

### Post by dv3500ea on 2010-10-09
I find that functional code (as opposed to procedural) seems elegant to me. I like methods that can be evaluated as a single expression. Here is a mode method (in ruby) that I wrote a while ago while learning the language. It isn't as efficient as a procedural implementation but seems more elegant to me.

```

class Array
	def mode
		(
			(
				(
					sorted = (
						(
							self.map do |n|
								[self.count(n), n]
							end
						).sort! do |a, b|
							b[0] <=> a[0]
						end
					)
				).select do |el|
					el[0] == sorted[0][0]
				end
			).map! {|el| el[1] }
		).uniq!
	end
end

```

---

### Post by worseisworser on 2010-10-09
Friends don't let friends use tab-characters in their code. :)

---

### Post by r-senior on 2010-10-09
Not sure about the *most* beautiful, but the more Data Access Objects (DAO)s you've written in commercial Java applications, the more beautiful DAOs created with Spring/Hibernate start to look:

```

...

public class LedgerDAOImpl extends HibernateDaoSupport implements LedgerDAO {

    public Ledger createLedger(Ledger ledger) {
        return findLedgerById((Long)getHibernateTemplate().save(ledger));
    }

    public Ledger findLedgerById(long id) {
        return (Ledger)getHibernateTemplate().get(Ledger.class, id);
    }

    public List<Ledger> findAllLedgers() {
        return getHibernateTemplate().findByNamedQuery("findAllLedgers");
    }

    public void updateLedger(Ledger ledger) {
        getHibernateTemplate().update(ledger);
    }

    public void deleteLedger(Ledger ledger) {
        getHibernateTemplate().delete(ledger);
    }

}

```

---

### Post by nlsthzn on 2010-10-09
```
print "Hello, World!" 
```

Beautiful because I understand it :p

---

### Post by Simian Man on 2010-10-09
Uggh, Perl code can never really be beautiful :).  To me beautiful code is that which expresses the underlying algorithm in a very clear manner.  "Clever" code is never a good thing.

In that vein, I really like this Haskell version of quicksort from the Haskell wiki.  Though inefficient, it expresses the algorithm extremely clearly.
```

qsort [] = []
qsort (first:rest) = qsort (filter (< first) rest) ++ [first] ++ qsort (filter (>= first) rest)
```

And don't even get me started on the "Beauty" of Java :P.

---

### Post by luvshines on 2010-10-09
This is the most insane piece of code I ever saw.

```
#include <stdio.h>
main(t,_,a)
char *a;
{
return!0<t?t<3?main(-79,-13,a+main(-87,1-_,main(-86,0,a+1)+a)):
1,t<_?main(t+1,_,a):3,main(-94,-27+t,a)&&t==2?_<13?
main(2,_+1,"%s %d %d\n"):9:16:t<0?t<-72?main(_,t,
"@n'+,#'/*{}w+/w#cdnr/+,{}r/*de}+,/*{*+,/w{%+,/w#q#n+,/#{l+,/n{n+,/+#n+,/#\
;#q#n+,/+k#;*+,/'r :'d*'3,}{w+K w'K:'+}e#';dq#'l \
q#'+d'K#!/+k#;q#'r}eKK#}w'r}eKK{nl]'/#;#q#n'){)#}w'){){nl]'/+#n';d}rw' i;# \
){nl]!/n{n#'; r{#w'r nc{nl]'/#{l,+'K {rw' iK{;[{nl]'/w#q#n'wk nw' \
iwk{KK{nl]!/w{%'l##w#' i; :{nl]'/*{q#'ld;r'}{nlwb!/*de}'c \
;;{nl'-{}rw]'/+,}##'*}#nc,',#nw]'/+kd'+e}+;#'rdq#w! nr'/ ') }+}{rl#'{n' ')#\
}'+}##(!!/")
  :t<-50?_==*a?putchar(31[a]):main(-65,_,a+1):main((*a=='/')+t,_,a+1)
    :0<t?main(2,2,"%s"):*a=='/'||main(0,main(-61,*a,
"!ek;dc i@bK'(q)-[w]*%n+r3#l,{}:\nuwloca-O;m .vpbks,fxntdCeghiry"),a+1);
}
```

It's C code and the output freaked me out. Amazing :D , but as OP said, it is obfuscated indeed

---

### Post by worseisworser on 2010-10-09
```

SW-MVC> (let* ((x &#955;I2)
               (square &#955;I(with1 (* ~x ~x)
                           (format t "New value of SQUARE is ~A.~%" it))))
          (write-line "X is incremented to 3.")
          (incf ~x)
          (write-line "X is incremented to 4.")
          (incf ~x)
          (format t "..and at the end, SQUARE is ~A.~%" ~square))
New value of SQUARE is 4.
X is incremented to 3.
New value of SQUARE is 9.
X is incremented to 4.
New value of SQUARE is 16.
..and at the end, SQUARE is 16.
NIL
SW-MVC> 

```

Perhaps not the *most* beautiful code I've seen or know (I do not recall tbh.), but data-driven (dataflow), declarative, reactive and simple -- and very significant in as to what one can express; I like it! :)

[http://en.wikipedia.org/wiki/Dataflow_programming#Properties_of_dataflow_programming_languages](http://en.wikipedia.org/wiki/Dataflow_programming#Properties_of_dataflow_programming_languages)

---

### Post by Queue29 on 2010-10-09
```
float InvSqrt(float x)
{
	union {
		float f;
		int i;
	} tmp;
	tmp.f = x;
	tmp.i = 0x5f3759df - (tmp.i >> 1);
	float y = tmp.f;
	return y * (1.5f - 0.5f * x * y * y);
}
```

Its exact origins are still unknown.
[http://en.wikipedia.org/wiki/Fast_inverse_square_root](http://en.wikipedia.org/wiki/Fast_inverse_square_root)

---

### Post by dv3500ea on 2010-10-09
Recursive factorials are nice:

```

def factorial x
	x > 1 ? x * factorial(x - 1) : 1
end

```

---

### Post by worseisworser on 2010-10-09
> **dv3500ea said:**
> Recursive factorials are nice:

```

def factorial x
	x > 1 ? x * factorial(x - 1) : 1
end

```

```

CL-USER> (defmethod factorial (x)
           (* x (factorial (1- x))))
#<STANDARD-METHOD FACTORIAL (T) {1004D6BD51}>

CL-USER> (defmethod factorial ((x (eql 1)))
           1)
#<STANDARD-METHOD FACTORIAL ((EQL 1)) {1005263571}>

CL-USER> (factorial 1)
1
CL-USER> (factorial 2)
2
CL-USER> (factorial 3)
6
CL-USER> (factorial 4)
24
CL-USER> (factorial 5)
120

CL-USER> (trace factorial)
(FACTORIAL)
CL-USER> (factorial 3)
  0: (FACTORIAL 3)
    1: (FACTORIAL 2)
      2: (FACTORIAL 1)
      2: FACTORIAL returned 1
    1: FACTORIAL returned 2
  0: FACTORIAL returned 6
6
CL-USER> 

```

hurr durr ... :)

---

### Post by wmcbrine on 2010-10-09
> **Simian Man said:**
> To me beautiful code is that which expresses the underlying algorithm in a very clear manner.  "Clever" code is never a good thing.This. Beautiful and clever are almost opposites in code, and since beautiful code is simple, it's hard to find 4-5 line examples.

However, in the spirit in which the question was asked, here's one of my favorite things that I've written -- part of a switch statement in an "ANSI" (ECMA-48) parser:

```
default:
    if ((a[0] >= '0') && (a[0] <= '9'))

case '=': // for some weird mutant codes
case '?':
case ';': // parameter separator
    {
        strcat(escparm, a);
        escfig();
    }
```

Too clever by half, and not beautiful at all, but kinda fun anyway.

---

### Post by schauerlich on 2010-10-09
> **worseisworser said:**
> ```

CL-USER> (defmethod factorial (x)
           (* x (factorial (1- x))))
#<STANDARD-METHOD FACTORIAL (T) {1004D6BD51}>

CL-USER> (defmethod factorial ((x (eql 1)))
           1)

```

```
factorial 1 = 1
factorial n = n * factorial (n-1)
```

or

```
factorial n
  | n == 1    = 1
  | otherwise = n * factorial (n-1)
```


Isn't pattern matching great?

---

### Post by dv3500ea on 2010-10-10
```
factorial(0)
```
:shock:

calculate e:
```

def e iterations=17
	(
		(0..iterations).to_a.map do |n|
			1/factorial(n).to_f
		end
	).inject do |a, b|
		a + b
	end
end

```

---

### Post by ziekfiguur on 2010-10-10
```
$python -c 'import this'
```Not really beautiful code, but it certainly got my attention and admiration.

---

### Post by dv3500ea on 2010-10-10
```

#!/usr/bin/env ruby
puts `python -c 'import this'`.gsub "There should be one-- and preferably only one --obvious way to do it.",
"There's more than one way to do it.
The most obvious way to do it should work (Principle Of Least Surprise)."

```

---

### Post by flyingsliverfin on 2010-10-10
```

#! /usr/bin/python
for x in y:           
	print('\n')
	for z in x:
		print(str(z)+'  '),

```
 where x = [[1,2,3],[1,2,3],[1,2,3]] or something like that
that is small part of a program i wrote when i was in the middle of learning python for printing nested lists of equal sizes into a rectangular shape. I remmeber how proud i was to have done it so efficiently, while my dad took quite a few lines more code for the same thing :)
there is probably a better way to do it but i've had extremely little programming experience outside of what my book shows so what i code is what comes straight out of my head!

---

### Post by worseisworser on 2010-10-10
> **flyingsliverfin said:**
> ```

#! /usr/bin/python
for x in y:           
	print('\n')
	for z in x:
		print(str(z)+'  '),

```
 where x = [[1,2,3],[1,2,3],[1,2,3]] or something like that

Not sure about the beautiful, but it's possible to write Perl in other languages too:

```

CL-USER> (let ((x '((1 2 3) (1 2 3) (1 2 3))))
           (format t "~{~{~A~^, ~}~%~}" x))
1, 2, 3
1, 2, 3
1, 2, 3

```

:)

edit: Oh, you used just " " ..? i used ", " here. ... :)

---

### Post by flyingsliverfin on 2010-10-10
your one confuses me a lot more than mine :)

---

### Post by mo.reina on 2010-10-10
taken from [here]("http://stackoverflow.com/questions/184618/what-is-the-best-comment-in-source-code-you-have-ever-encountered")

```
// Dear maintainer:
// 
// Once you are done trying to 'optimize' this routine,
// and have realized what a terrible mistake that was,
// please increment the following counter as a warning
// to the next guy:
// 
// total_hours_wasted_here = 34
// 
```

and this:
```
stop(); // Hammertime!
```

comments count right? :-\"

---

### Post by worseisworser on 2010-10-10
> **worseisworser said:**
> Not sure about the beautiful, but it's possible to write Perl in other languages too:

```

CL-USER> (let ((x '((1 2 3) (1 2 3) (1 2 3))))
           (format t "~{~{~A~^, ~}~%~}" x))
1, 2, 3
1, 2, 3
1, 2, 3

```

:)

edit: Oh, you used just " " ..? i used ", " here. ... :)

> **flyingsliverfin said:**
> your one confuses me a lot more than mine :)

Yeah, I might have gone for something like...

```

CL-USER> (let ((x '((1 2 3) (1 2 3) (1 2 3))))
           (map nil (lambda (elt)
                      (format t "~A, ~A, ~A~%"
                              (first elt)
                              (second elt)
                              (third elt)))
                x))
1, 2, 3
1, 2, 3
1, 2, 3

```


...instead. :)

---

### Post by linux18 on 2010-10-11
```
 
:(){ :|:& };:  
```

WARNING! it's a fork bomb.

I occasionally find myself typing into a terminal and excecuting it just because it looks like the list of emoticons I would use to describe the code itself while it is excecuting.

---

