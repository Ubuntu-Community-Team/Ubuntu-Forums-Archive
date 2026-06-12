---
title: "yet another c++ question"
date: 2006-03-21
forum: Programming Talk
---

### Post by mwanafunzi on 2006-03-21
Hi all,
    As a result of asking a couple of question on this forum, I have noticed (and people have said) that it is better to use *std::* rather than *using namespace std*. My question is, why is the former better lingo?

cheers

---

### Post by pato101 on 2006-03-21
because one might have for instance her own's vector class, so std::vector<float> would not conflict with her vector<float>. Of course if you are sure that vector<float> does not exist apart from the stdlib, you may use using namespace std without hassle. But as same happens with string, list, ...., ... the possibility of unwanted conflict grows up quickly.

Furthermore, saying std::vector is stating in the code where the vector class comes from.

---

### Post by thumper on 2006-03-21
It is bad form because it pollutes the namespace that contains the using directive.

It is not normally classes like vector or string that are problems, but more the auxillary classes and other templates.

---

### Post by toojays on 2006-03-21
On the other hand, you could also argue that it's bad practice to make your own classes have the same names as the standard classes.

mwanafunzi, in future it would be good if you could think of a more specific subject line when you make a forum post, e.g. "a question about c++ namespaces".

---

### Post by engla on 2006-03-21
[QUOTE=toojays]On the other hand, you could also argue that it's bad practice to make your own classes have the same names as the standard classes.

mwanafunzi, in future it would be good if you could think of a more specific subject line when you make a forum post, e.g. "a question about c++ namespaces".[/QUOTE]
Why? Polymorphism is great. If you think std::vector sucks, you can create your own that has just the same name and methods, just better inner workings... then it's up to you/other users if they want to use std::vector or toojays::vector.

---

### Post by mwanafunzi on 2006-03-21
thanks for the replies guys. As I am new to c++ i was (obviously) just wondering what the deal was.


cheers

---

### Post by rplantz on 2006-03-21
I find it easier to read because it's explicitly stated at the point where it's being used. I don't need to search back up the page looking for a using namespace statement.

---

### Post by toojays on 2006-03-21
[QUOTE=engla]Why? Polymorphism is great. If you think std::vector sucks, you can create your own that has just the same name and methods, just better inner workings... then it's up to you/other users if they want to use std::vector or toojays::vector.[/QUOTE]
Yeah, it's fine if you use the same interface as the standard. I was thinking of someone using the same class names, but making up their own interface, which would make it quite difficult for anyone else to step in and maintain.

---

### Post by thumper on 2006-03-21
[QUOTE=engla]Why? Polymorphism is great. If you think std::vector sucks, you can create your own that has just the same name and methods, just better inner workings... then it's up to you/other users if they want to use std::vector or toojays::vector.[/QUOTE]
Surely that is what **typedef** is for?

---

### Post by LordHunter317 on 2006-03-21
The other reason is that 'using std::vector' has specifc meaning in name resolution that 'using namespace' does not.

---

