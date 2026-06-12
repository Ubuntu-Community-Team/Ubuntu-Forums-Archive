---
title: "CakePHP vs Django vs Ruby on Rails"
date: 2008-09-04
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-09-04
With the new release of django, I was curious to see how popular it is among developers compared to other famous frameworks.

That is, I decided to create this poll to compare django with well known frameworks in other programming languages. I know there are many good frameworks on PHP, but I guess cakePHP is the most popular among them. So I'm very sorry if I'm missing your favorite framework in this poll.

Let's see which framework will win the poll.

---

### Post by pmasiar on 2008-09-04
You missed the best web framework from them all: Pylons/Turbogears :-)

---

### Post by mssever on 2008-09-04
You also missed my favorite PHP framework: Code Igniter. (Not that I use PHP much by choice anymore.)

---

### Post by themusicwave on 2008-09-04
I am really interested in trying Django.

I didn't vote because I haven't used any of the above yet.  I am just getting into we development more.

I've been doing a project in PHP lately for a non profit, and I really don't like the whole no namespaces thing.  I am spoiled by doing things like: someString.length()

I don't like how in PHP I have to know that the global function strlen() returns the length of the string you pass it.  I also hate that the whole standard library is global to begin with. Part of that stems from having the mantra "Globals are bad" drilled into my head by countless professors. All in all when I use PHP I just feel it is all very disorganized.

So due to that I lean more toward the others.  I don't know Ruby, so I would choose Django if I could, but their hosting only supports PHP.

---

### Post by cb951303 on 2008-09-05
None of them - Code Igniter!

---

### Post by Reiger on 2008-09-05
> **themusicwave said:**
> I am really interested in trying Django.

I didn't vote because I haven't used any of the above yet.  I am just getting into we development more.

I've been doing a project in PHP lately for a non profit, and I really don't like the whole no namespaces thing.  I am spoiled by doing things like: someString.length()

Yes you happen to have picked something:
a) 'Trivial', which is to say it dates back to the beginnings of PHP presumably (and is direct invocation of underlying C language)
b) No done by objects (hey, it's implemented in C!)

But *there are* these constructs you talk of:

[php]
$some_xml_string='<root><!-- this is an raw xml string --></root>';
$doc = new DOMDocument;
$doc->loadXML($some_xml_string);
[/php]

Note the arrow; since in PHP the dot (.) is reserved for the string concatenation operator, they had to pick another symbol and choosed the arow (->); still, it fulfills the same semantics as the dot does in someString.length(); with Java.

> 
I don't like how in PHP I have to know that the global function strlen() returns the length of the string you pass it.  I also hate that the whole standard library is global to begin with. Part of that stems from having the mantra "Globals are bad" drilled into my head by countless professors. All in all when I use PHP I just feel it is all very disorganized.

Well, in part you *are* right. It certainly isn't Java with it's very rigid adherance to OOP solves everything; and what it doesn't solve doesn't exist. But it takes some getting used to and then it's not so bad, I feel. As far as writing code goes, PHP does make a lot of stuff very easy and very quickly done.

---

### Post by mohtasham1983 on 2008-09-05
> **pmasiar said:**
> You missed the best web framework from them all: Pylons/Turbogears :-)

Sorry, I don't think that pylongs/Turbogears be as popular as django among python frameworks. I just wanted to compare django with frameworks in other programming languages.

---

