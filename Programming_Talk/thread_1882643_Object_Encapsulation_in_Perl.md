---
title: "Object Encapsulation in Perl"
date: 2011-11-17
forum: Programming Talk
---

### Post by endontoddy on 2011-11-17
I got myself in to a 'heated debate' today with a work colleague over when/how it is appropriate to access private object variables. Take this example:

```

sub foo() {
 my ($self, $bar) = @_;
 
 $bar+=5;
 $self->{important_value} = $bar;
}

```

Is that:  $self->{important_value} = $bar;
breaking object encapsulation? One argument was that since it took place within the object's own method then it was fine. The other argument was that even within an object's own methods, object variables should be changed only using an accessor-method.

Anyone got any thoughts?

---

### Post by nvteighen on 2011-11-17
Don't be fooled by the syntax. Your "issue" only pops out when accessing some attribute directly is equivalent to using its accessor. For example, when getting or setting the attribute doesn't imply some further operation besides assignment or just accessing the data. In cases where an accessor is needed because the data requires some further processing, there will be no doubt that you'll need to use the accessor.

(These are the kind of things Lisp teaches you...)

---

### Post by endontoddy on 2011-11-19
Yes indeed, the debate centred around a disagreement over if accessors should always be used regardless of if they did any more than directly set a value (as above). The main point being that even if that were not the case now, it might be in the future (and who wants to go looking for every possible instance of that private variable being set!)

As a point of interest, and as someone who has not so much experience with less hackily cobbled together languages as Perl or C++. Are there languages that force the use of accessors? A quick Google search reveals that Java does not.

---

### Post by Vaphell on 2011-11-19
not that i know anything of value about C# but it has that syntactic sugar of getters and setters. You write code as if you called the variable directly ie obj.name=some_value; or tmp_var=obj.name; and in reality set() and get() methods are used. I think it doesn't force anything though.

---

