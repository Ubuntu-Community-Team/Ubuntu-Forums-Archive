---
title: "GCC errors, pleas help a linux C++ n00b out"
date: 2006-10-08
forum: Programming Talk
---

### Post by daniel of sarnia on 2006-10-08
Hello all, I've been using Kubuntu for about a year now, and I've just loved it.
    However before I made the switch I was learning C++ and python in widows. Python has not giving me any trouble, but I'm getting errors with gcc that I never had using VS 6 or borland compilers. I just started with simple code that was the first program in my c++ book too. 

  this is the simple hello_world.cc file that's giving me problems
> 
#include <iostream>

int main();
{
	std::cout <<"Hello World\n";
	return 0;

}


And this is what I get back from gcc.

> 
daniel@lintop:~/programs$ gcc hello_world.cc
hello_world.cc:8:2: warning: no newline at end of file
hello_world.cc:4: error: expected unqualified-id before &#8216;{&#8217; token


I know this is a really n00bish question but help would really be appreciated, thanks.

---

### Post by duff on 2006-10-08
gcc is the C compiler, g++ is the C++ compiler.

That and loose the semicolon after "int main()"

---

### Post by daniel of sarnia on 2006-10-08
it gives me the same error

> daniel@lintop:~/programs$ g++ hello_world.cc
hello_world.cc:8:2: warning: no newline at end of file
hello_world.cc:4: error: expected unqualified-id before &#8216;{&#8217; token


---

### Post by duff on 2006-10-08
> **daniel of sarnia said:**
> it gives me the same error

you still need to get rid of that semicolon.

---

### Post by daniel of sarnia on 2006-10-08
I did 

> #include <iostream>

int main()
{
	std::cout <<"Hello World\n";
	return 0;

} 

---

### Post by daniel of sarnia on 2006-10-08
sorry forgot to save. 

but I still get this error  

> daniel@lintop:~/programs$ g++ hello_world.cc
hello_world.cc:8:3: warning: no newline at end of file


---

### Post by duff on 2006-10-08
works for me.

Did you remember to save the file after deleting the semicolon?

---

### Post by duff on 2006-10-08
> **daniel of sarnia said:**
> sorry forgot to save. 

but I still get this error

your editor is supposed to add that for you.  you can just add a blank line at the end of the file to get rid of that warning.

---

### Post by daniel of sarnia on 2006-10-08
sorry about that, I did not notice it was just a warning. It works now. 
But why do I get that warning.(edit: just read above)

Also why is the executable it made called "a.out"

Anyhow thankyou vary much for your time/help with my n00b problem.

---

### Post by Lster on 2006-10-08
...

---

### Post by daniel of sarnia on 2006-10-08
cool, thanks guys. I was using Kate to edit my code and after putting in a blank line at the end the warning went away.

Now that I know a bit on how to use g++ I can get onto some real programing.  

Again thanks on getting me started progaming in linux. :)

---

