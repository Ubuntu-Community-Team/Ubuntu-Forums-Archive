---
title: "fork() and exec()"
date: 2007-04-09
forum: Programming Talk
---

### Post by slavik on 2007-04-09
I feel this is something that everyone should know. This is the basis of how a shell works.

1. fork() - system call which creates a new process which is identical to the current process. Differences are dependent on the implementation but consider them to be 100% same for now. returns 0 to the newly created process (child process), returns child's pid to the parent (old) process, returns -1 if there was an error and no fork made.

2. exec() - actually, multiple version of exec (execlp(), execvp(), etc.) replaces the current process with a new process (create an empty main(), compile it then run it with shell's exec, the shell will die). returns nothing (since your process no longer exists as soon as exec() is done)

3. How it comes together. The basic shell. When calling 'ls', the shell forks, the child then proceeds to do the execlp("ls","ls") call, while the parent simply waits for the child to exit and then print its prompt again. if while 'ls' is running, the parent dies, 'ls' is said to become a 'zombie' (living dead, undead, etc.). The kernel kills the child process (and you thought GTA was violent).

btw, most calls to exec are something like (program, argv[0], argv[1], ... NULL);

the reason you see ls,ls is because you must give ls it's own name as the very first argument (this is what the shell does). why is this? neat things ...

in the .bashrc you can see commented out lines for aliases to ll (ls -l) and some other ... (ls -l is more used :P). what an alias does is simply replace the amtching string for another string, so if ll alias is enabled, when you write ll, one of the first things the shell will do before parsing the command is substitute ll for ls -l. but the neat thing about argv[0] is that you could do something like "ls","ll" and have a smart ls that checks how it was called and if it was called as 'll' to do ls -l and this can actually confuse people, because there is an ll but if you do any checking, ls and ll are exactly the same (byte for byte) but output different things. vim actually does this afaik (different functionality if you call it as vi or vim), gcc/g++ does a similar thing I think (haven't really checked).

Also, if you have a modified .xinitrc or .xsession, now you know what happens to the shell from  which you run X :P

---

### Post by heimo on 2007-04-10
> **slavik said:**
>  you could do something like "ls","ll" and have a smart ls that checks how it was called and if it was called as 'll' to do ls -l

Ultimate example would be BusyBox.
[http://www.busybox.net/about.html](http://www.busybox.net/about.html)
[http://www-128.ibm.com/developerworks/linux/library/l-busybox/](http://www-128.ibm.com/developerworks/linux/library/l-busybox/)

---

### Post by Dseed on 2007-04-10
I've been playing with Fork() and Exec() lately, and it can be somewhat confusing at first.  I ran into a lot of zombie trouble when I started working on a C program launcher application.

I wanted to be able to launch multiple programs with the click of a single button, while the main program wouldn't have to wait for these programs to close to return controll.

here is the solution that I eventually came up with

```


void sExecute   (const char *program, const char *command)
{
	
	pid_t mpid,pid;     // this holds the pid of the newly forked processes
	int status;

	mpid = fork();
    if (mpid == 0)          
    {
    	
    	pid = fork();
    	if (pid == 0)
    	{
    	// this is the child
    	execlp(program,program,command,0);
    	_exit(0);
		} else {
    	// this is the parent
		_exit(0);
		}
		
    } else { 
    	// parent of first fork
    	// waitpid(mpid,&status,WNOHANG);

    	waitpid(mpid,&status,0);
    }
}


```


an example of using this inside your program:
```

sExecute   ("galeon", "http://www.ubuntuforums.org");

```

this will return controll right away basically to your application, which is good if you are writing a GUI application...

you can call this back to back to open multiple programs or whatever
example:
```


void
on_button_clicked                      (GtkButton       *button,
                                        gpointer         user_data)
{
 
	const char *program;
        const char *entry_text = "http://www.ubuntuforums.org";
	
	program = "galeon";
	sExecute(program,entry_text);
	
	program = "mozilla";
	sExecute(program,entry_text);
	
	program = "firefox";
	sExecute(program,entry_text);
	
	program = "opera";
	sExecute(program,entry_text);
	

}


```

concerning ZOMBIES, i've tested this code and ran the above example, opening all of my web browsers, and then run TOP in the terminal and there are no zombies :)

the code could be made a little better as far as error checks and stuff...but this is a bare bones example anyway


Hope this helps someone

Peace
Derek

---

### Post by slavik on 2007-04-10
also, when you fork, do not forget to check for -1 return ... because then bad things might happen.

---

### Post by public_void on 2007-04-10
A nice book I found was [Advance Linux Programming]("http://www.advancedlinuxprogramming.com/"), especially chapter 3 about processes, it goes through the exec family and fork quiet well. IMO a very good read.

---

### Post by joshbodily on 2013-04-22
I'm not entirely sure that vim and vi work that way.  On my machine (Ubuntu 11.10), vim and vi are both just symlinks to /etc/alternatives/vim
$ which vi
/usr/bin/vi
$ which vim
/usr/bin/vim
$ ls -la /usr/bin/vi
/usr/bin/vi -> /etc/alternatives/vim
$ ls -la /usr/bin/vim
/usr/bin/vim -> /etc/alternatives/vim

Both 'vi' and 'vim' appear to launch the same program w/ same functionality.

---

### Post by Elfy on 2013-04-22
closing 6 year old thread

---

