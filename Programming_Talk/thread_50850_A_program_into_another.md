---
title: "A program into another"
date: 2005-07-21
forum: Programming Talk
---

### Post by josuealcalde on 2005-07-21
I want to launch a compress file manager (for example, file-roller, but could be other)  into another. Both are guis to see some file:

```

GtkWidget *statusbox;
	switch(fork())
	{
		case -1:
			//Throw a warning dialog
			...
		case 0:
			printf("En <0>\n");fflush(stdout);
			char * arg[3]; 
			strcpy(arg[0], "file-roller");
			strcpy(arg[1], _package->getFile().c_str()); //The file param for file roller
			arg[2] = NULL;
			execvp (arg[0], arg);
			//Throw a warning dialog -- PROBLEM IS HERE
			...
			
	}
```


The problem is I can't know if the execvp has throw the command correctly in the main program, so I can't throw a warning dialog in this moment.

How could I make to be able to throw file-roller (or another command), to be able to interact with both applications, file-roller and the parent and close them in the order I want, and be able to know if the command fails to show a gtk dialog?

Thanks.

---

### Post by LordHunter317 on 2005-07-21
Your main process blocks and waits for the other application to exit, via waitpid.  waitpid will return the status code returned by the application.  If it's not zero, the application exited in error.

---

### Post by josuealcalde on 2005-07-21
Yes, I know, but, what I want is to be able to interact with both programs at the same time and to be able to close the programs in the order the user want.

I am able to do this with the above code. The problem... I can't advise user if file-roller fails. It won't appear and it won't show any advise.

---

### Post by LordHunter317 on 2005-07-21
[QUOTE=josuealcalde]Yes, I know, but, what I want is to be able to interact with both programs at the same time and to be able to close the programs in the order the user want.

I am able to do this with the above code. The problem... I can't advise user if file-roller fails. It won't appear and it won't show any advise.[/QUOTE]
 You do what I said.  The procedure for catching a spawned process that fails to start is pretty easy:[list][*]Spawn the process, via fork.[*]The child process calles an exec() function to spawn off the new one[*]The parent process waits via waitpid() for the process to return.[*]If the return code from waitpid() in the parent is anything but zero, **then the child process had an error**[/list]The only issue comes up is within the blocking; you may not be able to block in waitpid() and still present an interactive application.  There's a fairly simple solution for this: add a signal handler for SIGCHLD.  This handler shouldn't do anything but set a global flag variable (make sure to declare it volitile).  Your application checks this variable everytime through it's main loop.  If it's set, it calls waitpid(), which should return immediately.  You can then reap the process, and the error check is the same as above.

To be perfectly clear:  Get the child process return status via waitpid().  Anything other than 0 means error.

---

### Post by josuealcalde on 2005-07-21
Thanks, for your help. I didn't want to use signals, and prefered not to user wait and things like that...

I have found a solution:

```

if (g_spawn_command_line_async ("here the command", 
				&dialogerror)){	
	//HERE, IT GOES WELL
}
else{
	//HERE, IT GOES BAD
}

```


This works for me.

---

