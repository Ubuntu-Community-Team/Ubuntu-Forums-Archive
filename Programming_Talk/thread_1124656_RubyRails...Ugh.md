---
title: "Ruby/Rails...Ugh?"
date: 2009-04-13
forum: Programming Talk
---

### Post by jacensolo on 2009-04-13
A little background. A few years ago I started to learn C++ in DOS. I had windows but my dad (I was 12ish I think and did not yet know of Linux) didn't know windows had free C++ compilers.I worked my way through, understanding most things besides pointers, references, etc. I somehow stumbled into Basic and worked with that, but never really liked its syntax. After moving to Linux and picking up python, several years later, I realize I still like C syntax. To this day I still love C.

So when I want to go into web developing for a bit, I hear about Rails/Ruby. Ruby looks good - scripting like Python. Apparently I was wrong. The language has some good features, but what kills it is the choices. Mainly the parenthesis choice. It is really hard to tell if something is in a function or not. It's not just that, there are other aspects I remember thinking "why?", but I don't remember them specifically.

Looking at Ruby as a whole, I think it seems like a good language, but I think some of the coding conventions that rails uses (such as the lack of "()" ) repels and confuses me.

So then I look into php nd find there are nice frameworks. I started looking into code igniter and it is just so much more approachable. Why is it that a lot of peeople don't like php? Not even knowing php prior, I'm putting together some simple web apps with ease. 

I'm not trying to advertise code igniter. Is there anybody else that thinks the sameway about Rails?  What makes php so bad? I don't know because I'm not that deep into it.

---

### Post by Tibuda on 2009-04-13
I disagree, nothing else to say. It's a personal taste.

---

### Post by johnl on 2009-04-13
I don't think there is anything inherently 'bad' about PHP as a language.  It's easy to pick up, easy to code, and works well for what it does.

The problem that people seem to have with PHP is it is very easy to learn bad habits and write bad code.  For example, writing code that is vulnerable to SQL injection, or relying on 'magic quotes' to prevent it.

---

### Post by Yacoby on 2009-04-13
> **jacensolo said:**
> I'm not trying to advertise code igniter. Is there anybody else that thinks the sameway about Rails?  What makes php so bad? I don't know because I'm not that deep into it.
The reasons I don't like PHP is mainly due to its standard library. I can never remember the function args order due to the fact that it is imperative, and there doesn't seem to be a standard.
Despite that, about 30% of the code I have written is in php.

> So when I want to go into web developing for a bit, I hear about Rails/Ruby. Ruby looks good - scripting like Python. Apparently I was wrong. The language has some good features, but what kills it is the choices. Mainly the parenthesis choice. It is really hard to tell if something is in a function or not. It's not just that, there are other aspects I remember thinking "why?", but I don't remember them specifically.
I would have thought that () is just an a annoyance with the syntax sugar. Just change your highlighter to highlight def a different way. Every language has what some people view as issues, and others view as benefits. It all depends on what your favorite language is. Java does my head in due to the lack of multiple inheritance, which as I have done so much C++ stuff, I take for granted.

---

### Post by CptPicard on 2009-04-13
I get this feeling that you're basing your opinions mostly on superficialities. Syntax is not the central issue (although it helps in visualization) -- what kind of concepts you have in the language and how they fit together to create abstractions, is.

I actually agree with the fact that Ruby's optional parenthesis makes function calls harder to visually identify and parse. It's a minor annoyance though, and you can always put them there as a stylistic choice.

To suggest though that, coming from C, having C-style *syntax* is somehow a big benefit to a language is really missing the point... you really need to actively use a couple of languages that actually do something beyond having a handful of imperative constructs. You will learn to appreciate stuff beyond syntactic trivialities after that.

For example in in the Ruby vs. PHP discussion, PHP's supposed merit of being syntactically more similar to C really pales in comparison to, say, Ruby's usage of closures ("blocks") and what you can build using them.

My exposure to PHP really is limited to a cursory overview, and I never liked what I saw... a language that started life as C-ish scriptlets embedded straight in HTML will have a hard time pulling itself into shape. No namespaces, messy library, reference-types in a scripting language, really strange array type, lack of most interesting higher-level constructs... it doesn't help that a great deal of PHP code out there really is written by rather weak programmers, as PHP is often the first language so it has the greatest supply of n00bs.

---

### Post by DocForbin on 2009-04-13
re: PHP, I agree the seemingly arbitrary argument order in some of the standard functions is maddening. But I haven't written very much PHP and imagine you get used to it.

The OO features in recent versions help with design and namespaces, but that all still feels pretty ad-hoc and awkward.

That said, it is a very easy language to learn, and aside from argument order most things work just like you expect them to.  And there is a ton of example (though often poor) free code out there. It's also nice not having to bother with imports for standard libraries in a scripting language (as opposed to, say, python). All in all it's a fun language to hack away in or quickly build an app on your own without any magic frameworks. I'm using it again lately for a personal project and am having fun with it.

---

### Post by Reiger on 2009-04-13
Actually PHP has everything you need to dynamically build scripts (the eval() construct) which can be utilised to build a lambda statement:

[php]
function input($args) {
  foreach($args as $key=>$value) {
   eval ("\$$key = $value + 1;");
  }
  // do something with the newly defined variables.
}
[/php]

---

### Post by DocForbin on 2009-04-18
This article by Rasmus Lerdorf, the original author of PHP, gives some insight into the language oddities.

[http://www.oracle.com/technology/pub/articles/php_experts/rasmus_php.html](http://www.oracle.com/technology/pub/articles/php_experts/rasmus_php.html)

The Ugly Duckling of Programming Languages <grin>

---

