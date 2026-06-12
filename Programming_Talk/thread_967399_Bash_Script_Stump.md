---
title: "Bash Script Stump"
date: 2008-11-02
forum: Programming Talk
---

### Post by DBQ on 2008-11-02
Hi everybody.  I am currently stumped by a bash script.  I need to write a script which runs a program.  The program being ran by the script expects a a parameter which has spaces in it.  For example:

```

./prog 'a b c'

```

When I run this from the command line, everything is fine.  When I run it from the script, there is a problem.  Here is how I run it:


```

./prog "'${pcmd[@]}'"

```

where pcmd contains a b c at indecies 0 1 2 respectively. When I echo the pcmd it shows 'a b c' like it should.  When I run the command above from the script the program gets only the first argument (the a).  Any help is great.  Have spent hours nailing at this, and have no idea.  Once again I need the program to treat all values in the array as one parameter.

---

### Post by DBQ on 2008-11-02
Never mind, I have figured it out.

---

