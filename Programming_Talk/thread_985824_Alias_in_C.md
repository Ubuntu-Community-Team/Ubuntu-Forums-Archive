---
title: "Alias in C"
date: 2008-11-18
forum: Programming Talk
---

### Post by 420shaggy on 2008-11-18
How would one go about creating alias's in C?  The only idea I had was to use exec to call the alias command in linux but it fails for some reason.  When I am in bash and use alias it works fine, but when I create a C program that executes commands from PATH, it tells me that it cannot find the alias command.

```

	execvp ("alias", cmd);   //execvp auto looks in PATH

```

Where cmd is the alias I am creating.

---

### Post by mdurham on 2008-11-18
> **420shaggy said:**
> How would one go about creating alias's in C?  The only idea I had was to use exec to call the alias command in linux but it fails for some reason.  When I am in bash and use alias it works fine, but when I create a C program that executes commands from PATH, it tells me that it cannot find the alias command.

```

	execvp ("alias", cmd);   //execvp auto looks in PATH

```

Where cmd is the alias I am creating.
I think it's trying to execute "alias", no wonder it fails. You probably need to execute Bash and give Bash the arguments.
Just my thoughts.

---

### Post by wmcbrine on 2008-11-18
"alias" is a shell built-in, so it's not in the PATH. Even if you successfully ran it (through a shell), the alias would be lost again immediately as you exited the shell on completion of the exec() call.

So, the answer is, you wouldn't. But, what are you *really* trying to accomplish here? Whatever it is, there's a way to do it. This just isn't it.

---

### Post by cyfur01 on 2008-11-18
I used this to confirm what **wmcbrine** said regarding the scope of the shell:```

#include <stdlib.h>
#include <stdio.h>

int main(){
        int return_value;
        // Create an alias to "ls -o"
        return_value = system("alias lso='ls -o'");
        // If it failed, print an error
        if(return_value != 0){
                fprintf(stderr,"Unable to create alias!\n");
                exit(EXIT_FAILURE);
        }

        // Try to execute the aliased command
        return_value = system("lso");
        // If it failed, print an error message
        if(return_value != 0){
                fprintf(stderr,"Unable to call aliased function!\n");
                exit(EXIT_FAILURE);
        }

        // If it worked, just exit
        exit(EXIT_SUCCESS);
}

```

When I run this, I get:```

sh: lso: not found
Unable to call aliased function!

```

Thus, it was able to execute the alias command, but at the end of that system() call, the /bin/sh instance is ended, erasing the alias. Then the second system() call is unable to find the aliased command and thus fails. (Also note that the system() function, if used with an arbitrary string, is a considerable security risk.)

---

### Post by Cracauer on 2008-11-18
What you want is probably something like this:

```

system(". /etc/doodamooda/system-exec-init.sh ; [your command]");

```

And put aliases and other setup into that file.

---

### Post by 420shaggy on 2008-11-18
The reason I wanted to create an alias in C was a part of a project I am struggling on which is creating a small custom shell with simple functionalities to it.  But it seems that if I am going to have to call Bash to use an alias, it becomes arbitrary since then I would require a shell just to use my own shell.
  In essence then, am I to program my own method of allowing alias'?  Or is there any easier way?

---

### Post by Cracauer on 2008-11-18
I'm not getting what you say.

system("");

invokes a shell anyway. Aliases are supported in bourne shell, so there's no problem with using an initialization file.

---

### Post by wmcbrine on 2008-11-19
> **420shaggy said:**
> In essence then, am I to program my own method of allowing alias'?Yes.

---

