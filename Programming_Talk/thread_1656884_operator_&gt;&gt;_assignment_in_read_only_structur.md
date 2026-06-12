---
title: "operator &gt;&gt; assignment in read only structure"
date: 2010-12-31
forum: Programming Talk
---

### Post by JakeFrederix on 2010-12-31
When overloading the operator >> for a class I made, I got an error basically saying that I can not modify the object, because it's a read-only structure.

I've put the classes in a .zip file.

I don't really understand the problem. The operator should be overloaded with a signature like the one I used. And I also get the compiler's point of view. I'm telling it that the object is constant, and then I try to change it.

Can anyone tell me what's wrong with my code?

---

### Post by MadCow108 on 2010-12-31
> **JakeFrederix said:**
> I'm telling it that the object is constant, and then I try to change it.

Can anyone tell me what's wrong with my code?

you answered your own question.
remove the const or don't modify the object.

overloading >> with a const destination seldom makes sense.

---

### Post by JakeFrederix on 2010-12-31
That's a bit disappointing.
I had expected a more complex solution.

Problem with the studies of software-engineering;
- loads of theory (including pseudo-code) of how algorithms work
- little or no practical experience making anything complex in any particular programming language

I know how loads of stuff work (things such zip compression), but can't implement them properly.
Very un-satisfying.

Thanks to everyone who helps me here.

---

### Post by worksofcraft on 2010-12-31
> **JakeFrederix said:**
> That's a bit disappointing.
I had expected a more complex solution.

Problem with the studies of software-engineering;
- loads of theory (including pseudo-code) of how algorithms work
- little or no practical experience making anything complex in any particular programming language

I know how loads of stuff work (things such zip compression), but can't implement them properly.
Very un-satisfying.

Thanks to everyone who helps me here.

I didn't yet check your zip files but there are situations when you can modify const objects... check the use of attribute "mutable" for class members you want to change.

I used this once when I had to change text to foreign language in class instances that were conceptually constant. Making all the objects variable just so the compiler would let me do localization of constant text would have ruined the design IMO!

---

