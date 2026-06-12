---
title: "Functionality of pointer in TCL ?"
date: 2009-05-05
forum: Programming Talk
---

### Post by tusharv on 2009-05-05
Hi ALL,

Is there functionality of pointer in TCL ?

If not, is there any logic that give me functionality like Pointer ?

I think one way is using array.

```
set a 10
set b a
set array ary {a 10}
puts ary($b)
```

Is there any other methods ?

Thanks,
Tusharv

---

### Post by squaregoldfish on 2009-05-05
You could have a look at the upvar command. It's not intended for use as a pointer, but it might provide enough flexibility for what you need. (Note that you can set the level to zero to reference variables in the current procedure.)

Steve.

---

### Post by stevescripts on 2009-05-05
Along with upvar, as pointed out by squaregoldfish, you have uplevel.

We have a saying in the TCL world, EIAS (Everything Is A String).
(In truth, it is actually, everything is a string, *OR* has a string representation...)

IMHO, one of the nice features of TCL (and other scripting languages), is that you never have to *work* with pointers.

Steve
(who really wonders which Steve in the UK is squaregoldfish?)

---

### Post by stevescripts on 2009-05-05
Maybe a little example of passing around array contents will help some folks - save the following little script, as arrayex2.tcl

```

array set test {a apple b bannana c carrot}

proc pass_array {array_name} {
	upvar $array_name this_array
	array get this_array
}


proc show_array {array_name} {
        upvar $array_name myArray

        foreach element [array names myArray] {
           puts stdout "${array_name}($element) =  $myArray($element)"
        }
    }

```

source it into an interactive tclsh:
```

(Desktop) 1 % source arrayex2.tcl
(Desktop) 2 % show_array test
test(a) =  apple
test(b) =  bannana
test(c) =  carrot
(Desktop) 3 % pass_array test
a apple b bannana c carrot
(Desktop) 4 % array set new_array [pass_array test]
(Desktop) 5 % array get new_array
a apple b bannana c carrot

```

Hope someone may find this useful/interesting.

Steve

---

### Post by squaregoldfish on 2009-05-06
> **stevescripts said:**
> 
Steve
(who really wonders which Steve in the UK is squaregoldfish?)

Well, there's not many of us :P

---

### Post by claird on 2009-05-06
> **tusharv said:**
> Hi ALL,

Is there functionality of pointer in TCL ?

If not, is there any logic that give me functionality like Pointer ?

I think one way is using array.

```
set a 10
set b a
set array ary {a 10}
puts ary($b)
```

Is there any other methods ?

Thanks,
Tusharv

Tusharv, I *deeply* don't understand the question.  To be blunt, from a Tcl perspective, pointers are fragile implementations of certain requirements, all of which Tcl solves more robustly.  Your example only adds to my confusion, in part because it's not syntactic Tcl (there is no "set array ..." as you seem to be using it, and I suspect the final command was intended to be more like "puts $ary(...").

I'm plenty familiar with the pointers of C and C++, for example.  I have trouble relating them to your description.  If your question is about *references*, Tcl abounds in those; for example, it's entirely idiomatic to write

    set fp [open $some_file]

and everyone recognizes that $fp is a *handle*, or reference, or even pointer, to the FILE details, rather than being itself a value which serializes all of FILE.

---

