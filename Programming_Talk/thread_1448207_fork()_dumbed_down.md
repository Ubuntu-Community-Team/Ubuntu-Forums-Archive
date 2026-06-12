---
title: "fork() dumbed down?"
date: 2010-04-06
forum: Programming Talk
---

### Post by dragos240 on 2010-04-06
I need to "thread" 2 different commands to allow them to run simultaneously. How would I go about doing this? My current source code is:
```

#include <unistd.h>
#include <stdio.h>

main()

{
system("aplay ~/stillalive.raw");
printf("This a triumph\n");
sleep(4);
printf("I'm making a note here\n");
sleep(3);
printf("HUGE SUCCESS\n");
sleep(2);
printf("It's hard to overstate my Satisfaction!\n");
sleep(7);
printf("Aperture Science!\n");
sleep(4);
printf("We do what we must, because we can.\n");
sleep(5);
printf("For the good of all of us, except the ones who are dead.....\n");
sleep(6);
printf("But there's no sense crying over every mistake.\n");
sleep(4.5);
printf("You just keep on trying 'till you run out of cake\n");
sleep(4.5);
printf("And the science gets done, and you make a neat gun, for the people who are still alive.\n");
sleep(8);
printf("\n");
sleep(5.5);
printf("I'm not even angry\n");
sleep(3.5);
printf("I'm being so sincere right now!\n");
sleep(5.5);
printf("Even though you broke my heart and killed me.....\n");
sleep(7);
return 0;
}

```

What happens is that the system call runs first, and doesn't run simultaneously with the other commands. So I need to play the file "stillalive.raw" with aplay while the messages are coming up. Fork is apparently what I want. Help?

---

### Post by MadCow108 on 2010-04-06
it may be enough to write:
system("aplay ~/stillalive.raw &");
but that is probably not very portable as it requires a shell feature

using fork:
```

  pid_t pid =fork();
  if (pid == 0) {
    //child
    system("aplay ~/stillalive.raw");
  }
  else {
    //parent
    ...
  }

```
see man fork

---

### Post by Simian Man on 2010-04-06
You are basically writing a shell script in C, which is a very silly thing to do.  If you wanted a solution to this problem it would be to use an actual shell script and run the aplay command in the background.

For learning purposes, however, you would use fork like this:

```

#include <unistd.h>
#include <stdio.h>

int main( ) {

  if(fork( ) != 0) {
    system("aplay ~/stillalive.raw");
    return 0;
  }

  /* all the rest of your stuff */
  return 0;
}

```

Fork is called once, but returns twice.  Once it returns 0 to indicate that the process is the child and the other time it returns the pid of the child to the parent.  Here the parent calls aplay and then returns while the child does all of your other stuff.

This code could be improved because the system call actually forks another process and then waits for it to return which is needless. You should look into the exec family of functions to see how to execute a program directly, but I'm not going to look that up for you.

---

### Post by dragos240 on 2010-04-06
Won't compile:
```

#include <unistd.h>
#include <stdio.h>

int main( ) {

if(fork( ) != 0) {
system("aplay ~/stillalive.raw");
return 0;
}
{
printf("This was a triumph\n");
sleep(4);
printf("I'm making a note here\n");
sleep(3);
printf("HUGE SUCCESS\n");
sleep(2);
printf("It's hard to overstate my Satisfaction!\n");
sleep(7);
printf("Aperture Science!\n");
sleep(4);
printf("We do what we must, because we can.\n");
sleep(5);
printf("For the good of all of us, except the ones who are dead.....\n");
sleep(6);
printf("But there's no sense crying over every mistake.\n");
sleep(4.5);
printf("You just keep on trying 'till you run out of cake\n");
sleep(4.5);
printf("And the science gets done, and you make a neat gun, for the people who are still alive.\n");
sleep(8);
printf("\n");
sleep(5.5);
printf("I'm not even angry\n");
sleep(3.5);
printf("I'm being so sincere right now!\n");
sleep(5.5);
printf("Even though you broke my heart and killed me.....\n");
sleep(7);
return 0;
}

```

---

### Post by schauerlich on 2010-04-06
> **dragos240 said:**
> Won't compile:

1) learn to indent. [This](http://www.python.org/dev/peps/pep-0007/) is a good start if you're unfamiliar
2) Don't just say "won't compile," tell us the error message
3) You have an extra open brace.

---

### Post by Simian Man on 2010-04-06
You have a superfluous opening brace.

---

### Post by dragos240 on 2010-04-06
It worked! Thank you!

---

### Post by -grubby on 2010-04-06
This is off-topic, but since your problem has been solved I guess I'll go ahead and ask if I can have a link to your Steam account.

---

