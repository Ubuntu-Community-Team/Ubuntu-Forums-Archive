---
title: "Call subroutine based on user input?"
date: 2008-08-10
forum: Programming Talk
---

### Post by geek_Man on 2008-08-10
Hello, I'm trying to write a program involving subroutines being run based on the value of some variable (a number). I've tried making an array of subroutines, but they all get run simply from being stated as being in the array (maybe that makes sense...). The thing I'm trying to do is make a bunch of menus... User types some character and another menu, based on the key that was pressed, comes up. Am I taking the right approach? Or is there some better way? If I am, how would I go about doing the above? Thanks!

P.S. Oh, FWIW, I'm using Perl.

---

### Post by pmasiar on 2008-08-10
Dictionary where keys are input, and values are reference to a function? What part is a problem? Can you show us some code?

---

### Post by geek_Man on 2008-08-10
Sure...

Let's say I have:
```
@array = (&sub1, &sub2, &sub3);
```
Just from having that code there (and provided that I've defined those subroutines), all the subroutines are run, one after the other. I would like to be able to say...
```
$i = 2;

$array[$i];
```
... and bam, &sub2 gets executed, and nothing else.

You mentioned something about references..... I remember reading about those, but can't remember the purpose they serve... Are they what I need?

Thanks for your help!

---

### Post by ConMan318 on 2008-08-10
You aren't going to be able to do this, at least not with that type of array declaration.  When you write 
```

@array = (&sub1, &sub2, &sub3);

```

@array is getting populated with the output of each of those subroutines.  Just like if you wrote
```

my $a = &routine;

sub routine {
   return 3;
}

```
$a would get 3 because the routine in the assignment statement is executed and then evaluated for assignment.

Why not just go the simple route, with something like
```

# code to get user input and check for validitiy here

$input = 2; # this is whatever the user entered above

if($input == 1){
   # do something
} elsif($input == 2){
   # do something else
} else {
   print "Error\n";
}

```

You could even use the switch module to make it easier to read.

---

