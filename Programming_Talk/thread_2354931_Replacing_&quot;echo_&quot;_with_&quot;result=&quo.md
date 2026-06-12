---
title: "Replacing &quot;echo &quot; with &quot;result=&quot; does not work, but I don't understand the error."
date: 2017-03-07
forum: Programming Talk
---

### Post by s3a on 2017-03-07
Hello, fellow Linux lovers. :)

_I'm trying to write the BASH equivalent of the following Java syntax.:_
```

public int factorial(int n) {
	if(n>1) {
		return n * factorial(n-1);
	} else {
		return 1;
	}
}

int result = factorial(5);

System.out.println(result);

```

_This works (and prints out 120, as intended).:_
```
#!/bin/bash

function f() {
	n=$1;

	if [[ n -gt 1 ]]; then
		echo $(($n*$(f $(($n-1)) )));
	else
		echo 1;
	fi
}

f 5;


```

_This does not work.:_
```
#!/bin/bash

result=-1;

function f() {
	n=$1;

	if [[ n -gt 1 ]]; then
		result=$(($n*$(f $(($n-1)) )));
	else
		result=1;
	fi
}

f 5;

echo $result;
```

_The error it gives is as follows.:_
> ./script
./script: line 9: 2*: syntax error: operand expected (error token is "*")
./script: line 9: 3*: syntax error: operand expected (error token is "*")
./script: line 9: 4*: syntax error: operand expected (error token is "*")
./script: line 9: 5*: syntax error: operand expected (error token is "*")
-1

Could someone please help me find the BASH-equivalent of the Java syntax above?

Any help in getting me to achieve with BASH what the Java syntax above shows would be GREATLY appreciated!

---

### Post by &amp;KyT$0P# on 2017-03-07
That code has two problems -

1) You're missing a $ in the "if" line.

2) Your [FONT=Courier New]f[/FONT] function outputs nothing, yet you are asking for its output in a mathematical operation.  Thus the syntax errors you're seeing.


If you fix those problems...
```
#!/bin/bash

function f() {
        n=$1;

        if [[ $n -gt 1 ]]; then
                n=$(($n*$(f $(($n-1)) )));
        else
                n=1;
        fi

        echo "$n";
}

echo $(f 5);
```
... does it work?

---

### Post by s3a on 2017-03-08
Oh! Thanks. :)

_I have another question, though.:_
How come the echo statement within the function in the BASH syntax that worked in my first post actually printed something [like System.out.println() in java], but yours is more like a return statement from Java [which *is* what I want] [such that, if I comment out the "echo $(f 5);" (without the quotes), the entire script doesn't print anything.]

---

### Post by &amp;KyT$0P# on 2017-03-08
> **s3a said:**
> How come the echo statement within the function in the BASH syntax that worked in my first post actually printed something [like System.out.println() in java], but yours is more like a return statement from Java [which *is* what I want] 
It's actually equivalent.

bash doesn't really have a concept of "return value".  In bash, for every command, you have two things - "exit code" and "output".  You are using the latter as a sort of "return value".

That difference between your working code and mine is mostly "cosmetic".

> **s3a said:**
> [such that, if I comment out the "echo $(f 5);" (without the quotes), the entire script doesn't print anything.]
Well, that's because you're then only defining a function f, but not calling it.  So nothing seems to happen.

---

### Post by kevdog on 2017-03-12
Here a nice article explaining the concept of return value in Bash functions.  halogen2 is correct -- there is no such thing as a pure function return value in bash scripts like other languages.[http://www.linuxjournal.com/content/return-values-bash-functions](http://www.linuxjournal.com/content/return-values-bash-functions)

---

