---
title: "filtering out comments from files"
date: 2011-11-04
forum: Programming Talk
---

### Post by gamblor01 on 2011-11-04
I have some scripts that will determine all of the available schemas we have on Oracle and then compare a certain object between them.  For example, I can check to see if a procedure is the same across all schemas by calling my script and feeding it some "default" procedure definition that it can compare to.

The problem is, I am basically just compressing all newlines and spaces into a single space and then calling diff -wB on two files to compare them.  This works fairly well, but it cannot ignore comments.  So I'm looking to enhance my script so that it handles this.  Right now I am doing this:

```

    elif [ "$ddlType" == "PROCEDURE" ]; then
        cat $file1 | tr '\n' ' ' | tr -s ' ' | sed -e "s/create or replace procedure//gI" > foo.txt
        cat $file2 | tr '\n' ' ' | tr -s ' ' | sed -e "s/create or replace procedure//gI" > bar.txt
    ...
    fi

    res=$(diff -wB foo.txt bar.txt)

```



I thought about piping the cat command into a call to **grep -v "--"** but this would eliminate ALL lines that had a comment.  That's fine if the comments are always on a line by themselves but that is not always the case.  I also thought about using awk with a file separator of "--" but then I wouldn't know how many tokens to grab prior to that.  Should I print $1, or $1 $2, or $1 $2 $3...it is unknown.

Does anyone know how to accomplish this?  If I can't get it then I suppose I will just push it on a higher level language.  Like I might just have Java parse the file first (loop thorugh the file with BufferedReader and on each line find line.indexOf("--").  If that returns a value greater than -1 I can print the substring from 0 to that index, else just print the line back).

The Java solution seems like a little bit of overkill.  Can anyone offer a simpler solution?

---

### Post by gsmanners on 2011-11-04
It might help if we knew what the problem was, but I personally think it might help if you converted things using a tool like highlight. Convert your source code into XML, and that will make it a lot easier to parse (especially if you go the high-level route).

---

### Post by MadCow108 on 2011-11-04
would this work?
```
sed -e "s/--.*//" schema.txt  | grep -v "^[ \t]\+*$"
```

you might need to make the regex a bit more complex if -- is allowed in some cases, like in quoted strings

---

### Post by gamblor01 on 2011-11-04
> **gsmanners said:**
> It might help if we knew what the problem was, but I personally think it might help if you converted things using a tool like highlight. Convert your source code into XML, and that will make it a lot easier to parse (especially if you go the high-level route).


Ummm I really don't follow you here.  My script is retrieving PL/SQL here from Oracle.  Just using dbms_metadata.get_ddl() to retrieve it and then I store the output for all of the schemas in files and compare the files.  The problem is that some of these files have comments in them, so my program would output that the following 2 strings are different, when in reality I want them to ignore spacing (this already works) and comments, thus considering them the same:

```

CREATE OR REPLACE PROCEDURE FOO IS
BEGIN
    SELECT 1 FROM DUAL;
END;

```



```

CREATE OR REPLACE PROCEDURE FOO IS
BEGIN
    SELECT 1 FROM DUAL;  -- this is an example proc
END;

```



The problem is that the two solutions I proposed (grep -v and awk with a file separator) are inadequate for the reasons already started in my first post.




> **MadCow108 said:**
> would this work?
```
sed -e "s/--.*//" schema.txt  | grep -v "^[ \t]\+*$"
```

you might need to make the regex a bit more complex if -- is allowed in some cases, like in quoted strings


Something like that should work.  I'll tweak it and see.  The "--" pattern is certainly legal to occur inside of a string but whether or not it actually does is a different story.  Thanks I'll give this a shot for now.  Might still need to do something more sophisticated that keeps track of whether or not the pattern exists inside/outside of a string though.  :/

---

### Post by Vaphell on 2011-11-04
regexes are not the way to solve parsing problems but sometimes you can get to the 'good enough' zone

assuming that odd number of quotes to the right of -- means it's inside the string

input:
```
$ echo $'stuff -- cmnt \n"stuff -- cmnt "a" v"\nstuff --cmnt"\nstuff -- cmnt "omg" omg'
stuff -- cmnt 
"stuff -- cmnt "a" v"
stuff --cmnt"
stuff -- cmnt "omg" omg
```
result
```
$ echo $'stuff -- cmnt \n"stuff -- cmnt "a" v"\nstuff --cmnt"\nstuff -- cmnt "omg","omg" omg' | sed -r 's/--[^"]*(["][^"]*){2}*[ \t]*$//'
stuff 
"stuff -- cmnt "a" v"
stuff --cmnt"
stuff
```

---

### Post by gamblor01 on 2011-11-07
> **Vaphell said:**
> regexes are not the way to solve parsing problems but sometimes you can get to the 'good enough' zone

assuming that odd number of quotes to the right of -- means it's inside the string

input:
```
$ echo $'stuff -- cmnt \n"stuff -- cmnt "a" v"\nstuff --cmnt"\nstuff -- cmnt "omg" omg'
stuff -- cmnt 
"stuff -- cmnt "a" v"
stuff --cmnt"
stuff -- cmnt "omg" omg
```
result
```
$ echo $'stuff -- cmnt \n"stuff -- cmnt "a" v"\nstuff --cmnt"\nstuff -- cmnt "omg","omg" omg' | sed -r 's/--[^"]*(["][^"]*){2}*[ \t]*$//'
stuff 
"stuff -- cmnt "a" v"
stuff --cmnt"
stuff
```


Thanks I will try that and see how it works.  I actually need to change to using single quotes as this is SQL, but it should work the same.  The odd number of quotes to the right is an interesting solution, and I am fairly certain it works.  It should even hold up when escaping quotes inside of strings:

```

'-- it''s not a comment but a string literal!'

```


Nifty eh?  I like your solution and I'm sure it will be sufficient for this case.  There are relatively few comments in these procedures and most of them are very simple such as:

```

-- 12/30/2009 EAP Added OPERATOR_ID column

```


Thanks!

---

