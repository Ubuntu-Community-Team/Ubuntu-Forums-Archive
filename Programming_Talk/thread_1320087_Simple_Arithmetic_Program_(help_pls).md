---
title: "Simple Arithmetic Program (help pls)"
date: 2009-11-08
forum: Programming Talk
---

### Post by magicmax0 on 2009-11-08
I have a simple mathematical process i would like to automate with a program of some sort. Maybe even a basic shell script. I would like to have the user specify (or be prompted for) a few variables "A" "B" "C" and "M". Where A,B, and C are values in units of time aka HMS (hh.mmss). And M is in units of MiB.

A+B+C=TT (in HMS, whats the syntax for adding HMS units in the shell?)

A HMS-> / TT HMS-> = AX (unitless factor)

Where "HMS->" (aka HMS OUT) means to convert HMS to a decimal number (unitless).

And repeat for B and C, resulting in AX,BX, and CX.

Then simply:

AX*M=AS (in MiB)
BX*M=BS (in MiB)
CX*M=CS (in MiB)

The desired output would be the numerical values of AS,BS, and CS.

I know theres probably many ways to do this, any suggestions would be helpful. To keep it simple i would prefer a simple bash script if possible.

---

### Post by lswb on 2009-11-08
I don't follow all your requirements, but bash can do simple integer arithmetic either on variables or constants, by enclosing in double parentheses. For example,
```

$ echo $((2+2))
4
$ A=2
$ B=3
$ echo $((A+B))
5
$ 

```

For reading input from a user, there is the bash builtin "read"
type  "help read|less" (without quotes) in a terminal for usage

---

### Post by diesch on 2009-11-09
I don't really understand what you want to do but maybe this helps:

To add unit of times you can use *date*, but the format has to be *HhourMminSsec*:

```
$ date --date '1/1 05hour20min10sec 10hour00min10sec' +%H:%M:%S
15:20:20

```

The 1/1 makes *date* adding the values to *Do 1. Jan 00:00:00*

To convert a unit of time into an integer use the epoch time:

```
$ date --date '1/1 15:20:20' +%s
1230819620

```

---

