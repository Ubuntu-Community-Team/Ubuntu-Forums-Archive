---
title: "vim cpp syntax highlight"
date: 2009-03-04
forum: Programming Talk
---

### Post by cybo on 2009-03-04
i need to add an extra highlighting of the syntax for cpp, specifically for the vector<variable type>, stack<variable type> and queue<> types. 

i know how to do simple highlighting. i have already added vector and stack types into the cpp.vim file. here is what i have done:

```

syn keyword cType vector stack

```

but i need it to highlight vector<variable type> and stack<variable type>, i.e. including the '<' and '>' symbols. does anyone know how to do that?

thnx

---

### Post by geirha on 2009-03-04
Does this do what you want?
```

syn match cType "vector\s*<[^>]*>"

```

---

### Post by cybo on 2009-03-04
> **geirha said:**
> Does this do what you want?
```

syn match cType "vector\s*<[^>]*>"

```

very close but not exactly.

right now it highlights everything in the "< >". i don't want that. i want it to highlight only word vector and "<", ">" and whatever the variable types are that are within the "<>".

For example:
```

vector<int> my_vector;

``` 
should highlight word vector, <, int, and >, int is highlighted by default
```

vector<my_var_type> my_another_vector;

``` 
should highlight word vector, < and > but not my_var_type, since it is my own variable type, i.e. vim doesn't highlight it by default.

---

### Post by geirha on 2009-03-04
I see. Haven't messed around with custom syntax-highlighting for vim before, so I'm just guessing my way here. Your explanation reminded me on how php is highlighted; in particular the <?= somefunction() ?> elements. So based on the syntax highlighting of php, I tried with the following which seems to work:

```

syn region vector matchgroup=cppType start="\<vector\>\s*<" end=">" contains=cType

```

---

### Post by cybo on 2009-03-04
> **geirha said:**
> I see. Haven't messed around with custom syntax-highlighting for vim before, so I'm just guessing my way here. Your explanation reminded me on how php is highlighted; in particular the <?= somefunction() ?> elements. So based on the syntax highlighting of php, I tried with the following which seems to work:

```

syn region vector matchgroup=cppType start="\<vector\>\s*<" end=">" contains=cType

```

it almost achieved what i wanted it to do. here is what i want:

c++ has an stl library with the following containers (variable types)
stack<>
vector<>
queue<>
list<>
and others.
i want to have the ability to highlight these types. the problem is that these variables have can be multi-dimiensional 

example:
1)vector<int, vector<int>>
2)vector<my_var_type, vector<int>>

in example 1,  i want the following highlighted:
  a)vector
  b)<
  c)int
  d)vector
  e)<
  f)int
  g)>
  h)>
as i understand int will be highlighted automatically since it is build it into the vim

in example 2, i want the following highlighted:
2)vector<my_var_type, vector<int>>
  a) vector
  b)<
  c)vector
  d)<
  e)int
  f)>
  g)>
my_var_type should not be highlighted since it is the variable type i defined myself.

is it possible to do it in vim?

---

