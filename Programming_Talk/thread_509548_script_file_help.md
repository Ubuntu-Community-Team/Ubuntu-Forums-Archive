---
title: "script file help"
date: 2007-07-25
forum: Programming Talk
---

### Post by metalix on 2007-07-25
I'm having some trouble getting my script files to run in KDE as executables.

I've included the following line at the start of my script file:

```
#!/bin/bash
```

I've also changed the permission to executable.

When I try to run the file in the prompt, it gives me an error.

Is there something I'm missing?

Thanks for helping.

---

### Post by Waappu on 2007-07-25
Hi

Could you please post that error message you get ?

---

### Post by nichipet on 2007-07-25
What error does it give? And are you giving the full path or ./ (period, slash) when starting it?

---

### Post by metalix on 2007-07-25
The error is:

```
bash: date.sh: command not found
```

I'm in the same directory as the file. Also, if I were to click on it using the GUI, the icon flashes and no window seems to open.

---

### Post by Waappu on 2007-07-25
Hi
Try this
```
./date.sh
```

---

### Post by metalix on 2007-07-25
That works, but I don't understand why.

On other Linux systems I've used, I've been able to run the script by simply typing it's name.

Is there anyway to achieve this in Kubuntu? Can I make it run from the GUI too?

Thanks for your help.

---

### Post by Waappu on 2007-07-25
Hi

I'm not expert, but if you place that script to ```
/usr/local/bin
```you can run it from terminila by it name and even every directory

---

### Post by Nekiruhs on 2007-07-25
No need to put it there. Just put it in ~/bin (make the folder if it doesn't exist). Then run source .profile

---

### Post by metalix on 2007-07-25
But from what I've seen in other systems, the first commented line tells the system the location of the bash shell that is used to execute it.

And it is an executable file, so I wonder why it won't just run.

---

### Post by Nekiruhs on 2007-07-25
> **metalix said:**
> But from what I've seen in other systems, the first commented line tells the system the location of the bash shell that is used to execute it.

And it is an executable file, so I wonder why it won't just run.
Its not a matter of the first line. Its a matter of where BASH looks for the files you type in. BASH only looks in a few folders for a file to run. These folders are normally named bin or something similar. To see what they are type in a terminal ```
echo $PATH
```. I willing to bet that your file was not in one of these folders. Thats why, when you type the name of it, it didn't run. ./ specifies a relative path. It tells BASH that the script is in your current folder. Following the steps I posted would fix it. 

Running it from the GUI just pops up a window because it runs and then closes. It ran, just really fast.

---

### Post by nichipet on 2007-07-25
> **metalix said:**
> But from what I've seen in other systems, the first commented line tells the system the location of the bash shell that is used to execute it.

And it is an executable file, so I wonder why it won't just run.

The #!/bin/bash tells it what shell to run under - different shells have different sets of commands available. And this is true of every *nix system out there. If the first line said #!/bin/ksh or #!/bin/zsh it would run under the Korn or z shell, respectively. Those shells especially have very unique commands available. You should normally be fine if you stick with #!/bin/bash or #!/bin/sh.

---

### Post by tqk on 2007-07-30
> **metalix said:**
> That works, but I don't understand why.

On other Linux systems I've used, I've been able to run the script by simply typing it's name.

I'd guess that on those other systems, "." was in your PATH.

> Is there anyway to achieve this in Kubuntu? Can I make it run from the GUI too?

You can, but this is generally considered a BAD THING.  There are ways it can be exploited by malicious types.

However, if you must:```
export PATH=$PATH:.
``` in your shell startup file (~/.bashrc) will do it.  If anyone ever tells you to do ```
export PATH=.:$PATH
``` instead, you have my permission to strangle them.  :-)

---

