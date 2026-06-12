---
title: "Debug in eclipse and anjuta"
date: 2007-11-13
forum: Packaging and Compiling Programs
---

### Post by yuval2111 on 2007-11-13
hi, i am new with ubuntu and anjuta and have a little experience with programming java at eclipse. i started to learn C, and i have some questions:
i have a simple C program:
****************************

#include <stdio.h>
int main(){
	int i=0;
	while(i<5){
		i++;
		printf("hello\n");
	}
	return 0;
}

*****************************
1) i want to create it in eclipse, so i go to file->new->manage make C project(is that the right choice?)->i worte "ex1" at project name->next->finish(when the "debug" and "release" are marked)
in ex1 project->new->source file->and the name ex1.c->finish
i wrote my program and save it. now i want to debug my ex1.c file so i go to Run->debug->at "project" i browse and insert ex1 and at "c/c++ application" i browsed and insert ex1. and finally press debug. a message open that say "Failed to set program arguments , environment or working directory". at details the message is: "Unable to set working directory: mi_cmd_env_cd: Usage DIRECTORY". what is my problem?

2) In anjuta i want to debug my program ex1.c i press Debug->run target -> i have two sections "Debugger target" and "command line parameters". what should i put in this sections ?

thanks and sorry for the long details.

---

### Post by yuval2111 on 2007-11-18
please!

---

### Post by SiM[e] on 2007-12-02
I m getting the same error :(

"Unable to set working directory: mi_cmd_env_cd: Usage DIRECTORY"

---

### Post by kvolden on 2008-01-24
A little late, perhaps, but here is a similar thread that fixed the problem for me: [http://ubuntuforums.org/showthread.php?t=43577](http://ubuntuforums.org/showthread.php?t=43577)

---

