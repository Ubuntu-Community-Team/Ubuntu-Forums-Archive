---
title: "failed to open stdout"
date: 2010-10-11
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-11
As some of you may have gathered [elsewhere]("http://ubuntuforums.org/showthread.php?t=1589825&page=2") I'm just starting on a sub project to create a bidi-terminal emulator.

Alas, this Linux malrchy ain't easy... I try to connect my terminal to the stdin and stdout of the new shell and I just can't get it to reopen stdout of child process :confused:

[php]
// g++ execbash.cpp

#include <stdio.h> // printf
#include <unistd.h> // execve
#include <sys/wait.h> // wait
#include <stdlib.h> // getenv

/*
pipe (to create the pipe), fork (to create the subprocess), dup2 (to force the
subprocess to use the pipe as its standard input or output channel), and execve
(to execute the shell (=new process)): it needs to exchange both in- and output
with parent process... that becomes my terminal emulator.
*/
int main(int argc, char *argv[], char *envp[]) {
	char *Shell = getenv("SHELL");
printf("shell=%s\n", Shell); // deleteme - diagnostic only

	int InPipe[2]; // input of the shell (output from the terminal)
	if (pipe(InPipe)) {
		return fprintf(stderr, "Failed to create InPipe\n");
	}
	int OutPipe[2]; // output of the shell (input from the terminal)
	if (pipe(OutPipe)) {
		return fprintf(stderr, "Failed to create OutPipe\n");
	}

	// new process: the shell
	if (fork() == (pid_t) 0) {
		close(InPipe[1]); // Terminal emulator has that end 
		if (dup2(InPipe[0], 0)) {
			return fprintf(stderr, "failed to reopen stdin\n");
		}
		close(OutPipe[0]); // similar to above, but for output
		if (dup2(OutPipe[1], 1)) {
			return fprintf(stderr, "failed to reopen stdout\n");
		}
		execve(Shell, argv, envp); // this should not return!
		return fprintf(stderr, "exec %s failed\n", Shell);
	// original process: to become the terminal emulator
	} else wait(NULL);

	return !printf("That's it for now!\n");
}
[/php]

Anyone have any ideas what I'm doing wrong here?

---

### Post by dwhitney67 on 2010-10-11
You may want to read the man-page for dup2().  I states that the return value is the new file descriptor, or -1 on error.

Your if-conditionals where you check the return value of of dup2() are incorrect.

P.S.  You probably will not get much mileage out of your call to execve() with the parameters you have supplied.  Verify if it is indeed /bin/bash (or whatever shell you are running) that you want passed as the command.  Actually it is probably argv that is incorrect.

---

### Post by worksofcraft on 2010-10-11
> **dwhitney67 said:**
> You may want to read the man-page for dup2().  I states that the return value is the new file descriptor, or -1 on error.

Your if-conditionals where you check the return value of of dup2() are incorrect.

P.S.  You probably will not get much mileage out of your call to execve() with the parameters you have supplied.  Verify if it is indeed /bin/bash (or whatever shell you are running) that you want passed as the command.  Actually it is probably argv that is incorrect.

Lol... the pages I was reading only said that dup2 returns -1 on error and I jumped to conclusions somehow :shock:

I was getting to execve... hum so we supposed to specify the command and specify it once again as argv[0]... oh well easily fixed!
Tyvm... getting there... eventually :)

---

