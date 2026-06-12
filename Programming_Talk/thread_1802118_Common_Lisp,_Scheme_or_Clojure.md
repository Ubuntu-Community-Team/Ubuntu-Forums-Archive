---
title: "Common Lisp, Scheme or Clojure"
date: 2011-07-11
forum: Programming Talk
---

### Post by JupiterV2 on 2011-07-11
I am interested in learning one of the above languages as my next language to tackle. I primarily code in C but I've been learning (and enjoying using) Go. I have dabbled with C++ and (Visual) BASIC in the past. Python, too, is on my list but I've slated it for after learning one of these languages. I'm not going to explain myself. Just except it. =)

Here's what I've read:

CL is generally considered more practical. It has a solid standard and has a ton of good standard/contributed libraries.

Scheme is a good teacher. While it can be used "in the real world" it is most commonly used as a learning or theoretical testing language. The minimal standard is well...er...standardized but many of the extensions/implementations of Scheme make anything outside the core standard non-portable thereby limiting its usability in the "real world."

Clojure is another dialect of Lisp which is compiled to bytecode for use on the JVM. This lends itself well to pragmatic programming because of the install base of the JVM. It has some good native libraries and those via the JVM.

These inferences might be complete wrong/naive, which is why I'm looking for help! I don't think I can go "wrong" with my choice but I'm looking for the language that:

1) Would bend my mind a bit to help break out of the C way of looking at things. 

2) You can write "real world" programs. Preferably ones that would have access to GUI (GTK or multi-platform widget library akin to Swing/SWT/AWT) and database libraries (sqlite, mySQL, posgreSQL, etc).

3) Write a language interpreter (where I think CL and Scheme might excel).

---

### Post by Simian Man on 2011-07-11
Keep in mind that Common Lisp and Scheme are languages with many implementations whereas Clojure refers to a language and an implementation.  If you pick one of the first two, you'll then have to pick an implementation of which there are dozens of each.

The only one I have spent a decent amount of time with is Guile which is a Scheme implementation with bindings to the Gnome libraries.  It is good but quite simple, lacking many features of Common Lisp and Clojure.  Clojure is next on my list of languages to learn (right now it's F#).

---

### Post by schauerlich on 2011-07-11
I have used all three. The order in which I learned them was:

[list=1][*]Scheme, via [Structure and Intepretation of Computer Programs](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-4.html)
[*]Common Lisp, via [Practical Common Lisp](http://www.gigamonkeys.com/book/)
[*]Clojure, via [this tutorial](http://java.ociweb.com/mark/clojure/article.html), the [Clojure Cheatsheet](http://clojure.org/cheatsheet), [API documentation](http://clojure.org/api), and Google.[/list]

My recommendation? Learn Scheme first. There are any number of good implementations, and if you follow along with SICP you won't really run into any incompatibilities between implementations or anything. I used Racket, but I assume Guile or Chicken would both be fine. SICP will be excellent for points 1 and 3 (Chapter 4 of SICP shows you how to make a Scheme interpreter in Scheme).

Next, I would learn Clojure. It's a young language, but it has a very enthusiastic community around it. Admittedly I'm no hardened Lisp hacker, but Clojure just feels like a clean, modern Lisp in a way that CL can't. As far as your second point, you really can't beat JVM integration in terms of access to libraries. If you can use it in Java, you can use it in Clojure. Get yourself set up with clojure, emacs/slime/clojure-mode, swank-clojure and leiningen, and you'll be set. Getting it up and running correctly is kind of a pain, but Google makes it manageable.

Now, where does that leave CL? By no means is it a useless language to know. If you're looking for a practical Lisp with significant mindshare and several solid implementations, CL is a great language. There are some weird things that you have to deal with for historical reasons, but by and large it's a very usable language. The CLOS is an interesting (and very useful) interpretation of OOP, integrated into the language via macros and generic functions. It's also easier to set up with SLIME, so if you're frustrated with Clojure it might be worth it to use CL instead. I used [SBCL](http://en.wikipedia.org/wiki/SBCL), one of the more popular implementations, but any of the popular ones is fine.

---

### Post by JDShu on 2011-07-11
The SICP lectures are awesome. Watch them.

[http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/](http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/)

---

### Post by JupiterV2 on 2011-07-12
Thanks for the input! I was originally leaning towards Clojure but perhaps I will learn Scheme first then move to Clojure. I ran across the SICP book and lectures several times when doing some google searches on the 3 Lisp languages. They seem to come highly recommended.

---

### Post by nvteighen on 2011-07-12
There's a huge issue you have to know about Scheme.

The Scheme standard is very minimalistic and defines just a couple of things; this means that every implementation extends the standard on its own. And there's almost no way to code portable Scheme code, as basic functions aren't defined by the standard.

It becomes worse when you realize that very few implementations have adopted the last standard R6RS, which tries to remedy this.

So, I agree with the idea that Scheme is a more gentle introduction to Lisp and that the SICP is great, but be sure to use MIT/GNU Scheme for SICP. Be aware that MIT/GNU uses a mix of R4RS, R5RS and extensions, some of which are used extensively in SICP, e.g. lazy lists. After learning it, you better continue with CL or Clojure.

The CL panorama is more similar to what you get in, e.g. C or C++. A huge standard that defines what you need and the occasional non-standard extension, so you don't get such incompatibility among CL implementations as you get among Scheme implementations. This may be the cause of why Scheme has been brought again to life but only as a scripting language (Guile, Scheme GIMP, etc.).

I don't know too much about Clojure.

---

### Post by schauerlich on 2011-07-12
> **nvteighen said:**
> There's a huge issue you have to know about Scheme.

The Scheme standard is very minimalistic and defines just a couple of things; this means that every implementation extends the standard on its own. And there's almost no way to code portable Scheme code, as basic functions aren't defined by the standard.

Very true. I wouldn't learn Scheme as a language in which to get things done; it's more useful as a learning tool. Because the language is so minimalistic, you get a better appreciation for what a language really needs in terms of core semantics, and how you can define other things that you might take for granted (structs, OOP, heck, even linked lists) in terms of more primitive concepts. It's a very interesting perspective on things that you aren't likely to get from a mainstream language.

That said, writing a program which is not a toy or intellectual exercise, in a portable manner, is an exercise in masochism. Learn CL or Clojure when you want to get something done.

---

### Post by nvteighen on 2011-07-12
> **schauerlich said:**
> 
That said, writing a program which is not a toy or intellectual exercise, in a portable manner, is an exercise in masochism. Learn CL or Clojure when you want to get something done.

FreeTruco, remember? :D

---

### Post by JupiterV2 on 2011-07-12
> **nvteighen said:**
> There's a huge issue you have to know about Scheme.

The Scheme standard is very minimalistic and defines just a couple of things; this means that every implementation extends the standard on its own. And there's almost no way to code portable Scheme code, as basic functions aren't defined by the standard.

It becomes worse when you realize that very few implementations have adopted the last standard R6RS, which tries to remedy this.

So, I agree with the idea that Scheme is a more gentle introduction to Lisp and that the SICP is great, but be sure to use MIT/GNU Scheme for SICP. Be aware that MIT/GNU uses a mix of R4RS, R5RS and extensions, some of which are used extensively in SICP, e.g. lazy lists. After learning it, you better continue with CL or Clojure.

The CL panorama is more similar to what you get in, e.g. C or C++. A huge standard that defines what you need and the occasional non-standard extension, so you don't get such incompatibility among CL implementations as you get among Scheme implementations. This may be the cause of why Scheme has been brought again to life but only as a scripting language (Guile, Scheme GIMP, etc.).

I don't know too much about Clojure.

Funnily enough, I had already bookmarked MIT/GNU to download/install. After looking at chicken, guile, kawa and ratchet I decided it would be the best choice for SICP. Good to know I was on the right track! The splintered nature of Scheme is one of the prime reasons I have no desire to use it other than to learn new concepts.

Clojure seems to be a fairly young project. It doesn't appear to be "just another lisp," and being compile to Java bytecode makes for a wide install base using a "write-once, run-anywhere" idiom. Access to the Java library, without having to write Java, is a huge bonus too. Amusingly, Clojure (as most lisp-ish languages are) has an incredibly concise syntax compared to the exceedingly verbose Java language.

That said, I'm not overly fond of Oracle and am not entirely comfortable using the JVM as a result. Enter Common Lisp implementations. I think, though, I'll stick to my plan unless I read any solid objections describing why C.Lisp might be > Clojure.

Is the editor based on Emacs which comes with MIT/GNU Scheme the ideal choice or is there a better editor to work with while going through SICP?

---

### Post by nvteighen on 2011-07-13
> **JupiterV2 said:**
> 
Is the editor based on Emacs which comes with MIT/GNU Scheme the ideal choice or is there a better editor to work with while going through SICP?

MIT/GNU Edwin is horrible, IMO.

Back then, when I was more into Scheme, I used Emacs + Quack, which is a decent Scheme-Emacs integration system (but certainly not in the league of SLIME for Common Lisp, though). You can install it directly from the repos, it's included in the emacs-goodies-el package. The nice thing of Quack is that it's compatible with nearly every Scheme implementation there is.

Setting it up it's a bit of a hassle, it doesn't start up automatically... and you have to tell Quack which Scheme are you using. You'll have to fiddle with its settings a bit in the Customize pages (M-x customize).

---

### Post by JupiterV2 on 2011-07-13
Thanks for the incite nvteighen. I'll definitely check out Quack.

---

