---
title: "help regarding for loop syntax in ubuntu 7.10"
date: 2008-02-21
forum: Programming Talk
---

### Post by phanther on 2008-02-21
hi,
i am a novice regarding linux.actually i am working on shell scripting in ubuntu 7.1.i am facing a lot of trouble with the "for loop" statement.
In which ever the format i am giving i am getting the same error as "bad for loop variable".

please help me with the syntax of for loop, if possible please provide me with a valid example which is working in the 7.1 version of ubuntu so that i can try it out.

thanx in advance:)

---

### Post by LaRoza on 2008-02-21
> **phanther said:**
> hi,
i am a novice regarding linux.actually i am working on shell scripting in ubuntu 7.1.i am facing a lot of trouble with the "for loop" statement.
In which ever the format i am giving i am getting the same error as "bad for loop variable".

please help me with the syntax of for loop, if possible please provide me with a valid example which is working in the 7.1 version of ubuntu so that i can try it out.

thanx in advance:)

[http://www.faqs.org/docs/abs/HTML/loops.html](http://www.faqs.org/docs/abs/HTML/loops.html)

---

### Post by phanther on 2008-02-21
hey thanx for the reply,  i found the syntax i was looking for in the html link u have provided, but i have already used that syntax and i am still facing the same problem.let me clearly describe what is it that i am trying to do.the syntax goes like this:

#!/bin/bash

k=10

for ((i=1; i <= k; i++))
do
    echo -n "$i "
done

the error that i am getting is "Bad for loop variable".

thnx again and i'll be looking forward for a reply

---

### Post by darsu on 2008-02-21
Odd. I tried that; it works with bash but not with sh.


See here: [http://ubuntuforums.org/archive/index.php/t-442794.html](http://ubuntuforums.org/archive/index.php/t-442794.html)

---

### Post by phanther on 2008-02-21
@darsu

can u tell me how did u run it, n did u give the same amt of spaces as i hav in the above thread.

if so can u pls tell me wat could be the problem. i've checked the shell i'm workin in, its bash n not sh.so i still cant figure out the mistake.infact i am unable to run any script related to "for" loop

---

### Post by darsu on 2008-02-21
I cut and pasted your code into something.sh and executed it with "bash ./something.sh" and "sh ./something.sh".

---

### Post by LaRoza on 2008-02-21
Note that the default shell in Ubuntu is dash, not bash.

[http://en.wikipedia.org/wiki/Debian_Almquist_shell](http://en.wikipedia.org/wiki/Debian_Almquist_shell)

---

### Post by phanther on 2008-02-21
@darsu & LaRoza

thank you very much, i got the answer from u both.

i made the right choice of asking u darsu about the execution thing.i've been executing it using the second way i.e using "sh".i had a wrong notion while executing it.i got the answers n its clear to me now.

Thanks LaRoza for providing the information regarding the shells and loops.

Now i have another doubt regarding the the above program, it is:

what will this piece of code do:   **"#!/bin/bash"**

---

### Post by ghostdog74 on 2008-02-21
please read[ here]("http://tldp.org/LDP/abs/html/sha-bang.html"), and also the whole document.

---

### Post by Zwack on 2008-02-22
> **phanther said:**
> 
Now i have another doubt regarding the the above program, it is:

what will this piece of code do:   **"#!/bin/bash"**

That depends on where it is in the file...

If the file is executable and that is the very first line (i.e. the first two characters are #!) then it will cause the script when run to use /bin/bash as the interpreter.

Otherwise it will be an interesting comment...

Z.

---

### Post by stormzen on 2008-02-28
Please be aware that "#!/bin/bash" resulted in dash being executed.  I guess the meaning of it is the "default shell" is that dash will be run when "#!/bin/bash" is specified.  On the other hand, "# !/bin/bash" makes the script execute as expected.  ( Note the space between # and ! )

That said, there is a claim that dash is more streamlined (strict POSIX requirement) than bash, so if a script doesn't work with dash, perhaps it makes a lot of sense to fix it?  If one were to go that route, is there a good link for syntax?

Thanks!

--J.

---

