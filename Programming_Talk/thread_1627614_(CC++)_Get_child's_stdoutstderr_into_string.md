---
title: "(C/C++) Get child's stdout/stderr into string"
date: 2010-11-21
forum: Programming Talk
---

### Post by japcrword on 2010-11-21
I call a program (with exec) that outputs some data on the screen. I need to get all its output in caller process (without creation of any files on disk). I presume that I don't have source code of the callee. 

I've found this link [http://stackoverflow.com/questions/1734932/linux-pipes-as-input-and-output]("http://stackoverflow.com/questions/1734932/linux-pipes-as-input-and-output") with some guidelines. This is not exactly what I need but very similar. 

Here's my implementation (that to my disappointment isn't still working): 
[PHP]#include <stdlib.h>
#include <stdio.h>
#include <iostream>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>

int main(){
  const char* PROGRAM_NAME = "child";
  char * args[] = {"arg1", "arg2", NULL, }; // what type should I define for args to get rid of warnings?
  int pipeForStdOut[2], pipeForStdErr[2];
  std::string cntStdOut, cntStdErr;
  char buf[32] = {0};
  ssize_t bytesRead;
  pid_t childPid;

  pipe(pipeForStdOut);
  pipe(pipeForStdErr);

  if(dup2(1,pipeForStdOut[1]) == -1){
    perror("dup2.1");
    exit(-1);
  }

  if(dup2(2,pipeForStdErr[1]) == -1){
    perror("dup2.2");
    exit(-1);
  }

  childPid = fork();
  if(childPid == -1){
    perror("fork");
    exit(-1);
  }else if(childPid == 0){
    std::cout << "executing child..." << std::endl;
    if(execv(PROGRAM_NAME, args) == -1){
      std::cout << "failed to execute child process, exiting..." << std::endl;
      perror("execv");
      exit(-1);
    }
    exit(0);
  }
  wait(NULL);

  std::cout << "tidying up..." << std::endl;
  close(pipeForStdOut[1]);
  close(pipeForStdErr[1]);

  while((bytesRead = read(pipeForStdOut[0], buf, sizeof(buf)-1)) > 0){
    buf[bytesRead] = 0;
    cntStdOut += buf;
  }

  while((bytesRead = read(pipeForStdErr[0], buf, sizeof(buf)-1)) > 0){
    buf[bytesRead] = 0;
    cntStdOut += buf;
  }

  std::cout << "<stdout>\n" << cntStdOut << "\n</stdout>" << std::endl;
  std::cout << "<stderr>\n" << cntStdErr << "\n</stderr>" << std::endl;
  
  close(pipeForStdOut[0]);
  close(pipeForStdErr[0]);

  return 0;
}
[/PHP]

I used this code of the child process for debugging:
[PHP]#include <iostream>

int main(int argc, char *argv[]){
  std::cout << "child: ";
  for(int i = 0; i < argc; ++i) 
    std::cout << " \"" << argv[i] << "\" ";
  std::cout << std::endl;
  std::cerr << "Success" << std::endl;
  return 0;
}
[/PHP]

I don't understand some basic concepts of pipes, obviously. My idea was: create a pipe with pipe(2), connect its writing end to the stdout (file descriptor == 1) with dup2(2), call the child process and finally read the data from pipe's reading end. I thought the pipe should transmit all data from stdout to pipe's reading end. But this doesn't work. The result of reading from pipe is always empty. **The question is Why?** 
Oh, and of course, if anyone can help me to get rid of the annoying warnings (caused by converting constant string literals to char *[] when initializing args) that will be appreciated. 
Thanks in advance.

---

### Post by worksofcraft on 2010-11-21
> **japcrword said:**
> I call a program (with exec) that outputs some data on the screen. I need to get all its output in caller process (without creation of any files on disk). I presume that I don't have source code of the callee... 
... see above


I'll have a look when I get time a later. Meanwhile you might want to check this thread where I tested the useful [master/slave I/O]("http://ubuntuforums.org/showthread.php?t=1594884") calls that you need once before.

---

### Post by worksofcraft on 2010-11-22
I did a few tweaks to your code so it will do what you want (see below) but it might not be a good solution because your pipes have to buffer ALL the child process output before you can go read it. It would be better to read it as it is generated... whatever...
[php]
#include <stdlib.h> 
#include <stdio.h> 
#include <iostream> 
#include <sys/types.h> 
#include <sys/wait.h> 
#include <unistd.h> 
#include <fcntl.h>

int main(){ 
  const char* PROGRAM_NAME = "./child";
	char arg1[] = "arg1";
	char arg2[] = "arg2";
  char *args[] = { arg1, arg2, NULL }; 

  int pipeForStdOut[2], pipeForStdErr[2]; 
  std::string cntStdOut, cntStdErr; 

  char buf[32] = {0}; 
  ssize_t bytesRead; 
  pid_t childPid; 

  pipe(pipeForStdOut); 
  pipe(pipeForStdErr); 

  childPid = fork(); 
  if(childPid == -1){ 
    perror("fork"); 
    exit(-1); 
  }else if(childPid == 0){
		// remember 0 is for 1nput and 1 is for 0utput
		close(pipeForStdOut[0]); // parent keeps the input
		if(dup2(pipeForStdOut[1], 1) < 0) { // child gets the output end
			perror("dup2.1"); 
			exit(-1); 
		} 

		close(pipeForStdErr[0]); // parent keeps the input
		if(dup2(pipeForStdErr[1], 2) < 0){ 
		    perror("dup2.2"); 
		    exit(-1); 
		}

	    std::cout << "executing child..." << std::endl; 
	    if(execv(PROGRAM_NAME, args) == -1){ 
      std::cout << "failed to execute child process, exiting..." << std::endl; 
      perror("execv"); 
      exit(-1); 
    } 
    exit(0); 
  } 
  wait(NULL); 

  std::cout << "tidying up..." << std::endl; 

    fcntl(pipeForStdOut[0], F_SETFL, O_NONBLOCK  | O_ASYNC); 
   while(1) {
	bytesRead = read(pipeForStdOut[0], buf, sizeof(buf)-1);
	if (bytesRead <= 0) break;
	buf[bytesRead] = 0; // append null terminator
	cntStdOut += buf; // append what wuz read to the string
  } 
  std::cout << "<stdout>\n" << cntStdOut << "\n</stdout>" << std::endl; 

    fcntl(pipeForStdErr[0], F_SETFL, O_NONBLOCK  | O_ASYNC); 
   while(1) {
	bytesRead = read(pipeForStdErr[0], buf, sizeof(buf)-1);
	if (bytesRead <= 0) break;
	buf[bytesRead] = 0; // append null terminator
	cntStdErr += buf; // append what wuz read to the string
  } 
  std::cout << "<stderr>\n" << cntStdErr << "\n</stderr>" << std::endl; 

  close(pipeForStdOut[0]); 
  close(pipeForStdErr[0]); 

  return 0; 
}  
[/php]

---

### Post by japcrword on 2010-11-22
Thank you. I'll try to get myself more familiar with pseudoterminals. Still after a brief look I can't figure out how to apply it to interception of printfs and couts.

---

### Post by japcrword on 2010-11-22
Thank you very much for your time. Now it works perfectly. So, I suppose, the crucial point was to move dup2 calls into the child part of forked code? 
And thanks for the comments and fixing some minor mistakes (as with read return code) :)

---

### Post by ziekfiguur on 2010-11-22
If you are using C++ and not pure C you might want to look at the Process class from the bobcat library ([http://bobcat.sourceforge.net/](http://bobcat.sourceforge.net/) It's also in the repositories). 
It can do all the low level stuff for you and you can just do something like this:

[PHP]
    string line;
    Process process(Process::CIN | Process::COUT,
                    "/usr/bin/sha1sum");
    process.start();
    process << "Hello world\n";         // input to sha1sum
    process.close();
    process >> line;                    // retrieve the value
    cout << line << endl;
    process.stop();
[/PHP]

---

### Post by japcrword on 2010-11-23
> **worksofcraft said:**
> 
[php]
		// remember 0 is for 1nput and 1 is for 0utput
		close(pipeForStdOut[0]); // parent keeps the input
		if(dup2(pipeForStdOut[1], 1) < 0) { // child gets the output end
			
[/php]

It will be difficult to forget. It's a good joke :)

> **ziekfiguur said:**
> If you are using C++ and not pure C you might want to look at the Process class from the bobcat library ([http://bobcat.sourceforge.net/](http://bobcat.sourceforge.net/) It's also in the repositories). 


Thank you. C++ will do. I'll have a look at it.

---

### Post by japcrword on 2010-12-11
> **worksofcraft said:**
> 
[php]
#include <stdlib.h> 
#include <stdio.h> 
#include <iostream> 
#include <sys/types.h> 
#include <sys/wait.h> 
#include <unistd.h> 
#include <fcntl.h>

...
[/php]

I think pipeForStdOut[1] and pipeForStdErr[1] should be closed too (the corresponding lines are marked with (*)):
[PHP]#include <stdlib.h>  
#include <stdio.h>  
#include <iostream>  
#include <sys/types.h>  
#include <sys/wait.h>  
#include <unistd.h>  
#include <fcntl.h> 

int main(){  
  const char* PROGRAM_NAME = "./child"; 
    char arg1[] = "arg1"; 
    char arg2[] = "arg2"; 
  char *args[] = { arg1, arg2, NULL };  

  int pipeForStdOut[2], pipeForStdErr[2];  
  std::string cntStdOut, cntStdErr;  

  char buf[32] = {0};  
  ssize_t bytesRead;  
  pid_t childPid;  

  pipe(pipeForStdOut);  
  pipe(pipeForStdErr);  

  childPid = fork();  
  if(childPid == -1){  
    perror("fork");  
    exit(-1);  
  }else if(childPid == 0){ 
    // remember 0 is for 1nput and 1 is for 0utput 
    close(pipeForStdOut[0]); // parent keeps the input 
    if(dup2(pipeForStdOut[1], 1) < 0) { // child gets the output end 
      perror("dup2.1");  
      exit(-1);  
    }  

    close(pipeForStdErr[0]); // parent keeps the input 
    if(dup2(pipeForStdErr[1], 2) < 0){  
      perror("dup2.2");  
      exit(-1);  
    } 

    std::cout << "executing child..." << std::endl;  
    if(execv(PROGRAM_NAME, args) == -1){  
      std::cout << "failed to execute child process, exiting..." << std::endl;  
      perror("execv");  
      exit(-1);  
    }
    close(pipeForStdOut[1]); // (*) close output end as well
    close(pipeForStdErr[1]); // (*) close output end as well
    exit(0);  
  }  
  wait(NULL);  

  std::cout << "tidying up..." << std::endl;  

  fcntl(pipeForStdOut[0], F_SETFL, O_NONBLOCK  | O_ASYNC);  
  while(1) { 
    bytesRead = read(pipeForStdOut[0], buf, sizeof(buf)-1); 
    if (bytesRead <= 0) break; 
    buf[bytesRead] = 0; // append null terminator 
    cntStdOut += buf; // append what wuz read to the string 
  }  
  std::cout << "<stdout>\n" << cntStdOut << "\n</stdout>" << std::endl;  

  fcntl(pipeForStdErr[0], F_SETFL, O_NONBLOCK  | O_ASYNC);  
  while(1) { 
    bytesRead = read(pipeForStdErr[0], buf, sizeof(buf)-1); 
    if (bytesRead <= 0) break; 
    buf[bytesRead] = 0; // append null terminator 
    cntStdErr += buf; // append what wuz read to the string 
  }  
  std::cout << "<stderr>\n" << cntStdErr << "\n</stderr>" << std::endl;  

  close(pipeForStdOut[0]);  
  close(pipeForStdErr[0]);  
  close(pipeForStdOut[1]); // (*) close output end as well
  close(pipeForStdErr[1]); // (*) close output end as well

  return 0;  
} [/PHP]

Without that I got errors after calling the code inside main several times in a row.

---

### Post by worksofcraft on 2010-12-11
> **japcrword said:**
> I think pipeForStdOut[1] and pipeForStdErr[1] should be closed too (the corresponding lines are marked with (*)):
...
Without that I got errors after calling the code inside main several times in a row.

Actually yes, that is good point, but I think you need to move them down a few lines so that it is done in the parent process:

In the same way that the child closes the file handles being used by it's parent, the parent process should not keep the streams open that are being used by it's child.

When a process calls exit I think it closes all it's handles anyway, so I'm surprised it made any difference there :shock:

---

### Post by japcrword on 2010-12-12
> **worksofcraft said:**
> When a process calls exit I think it closes all it's handles anyway, so I'm surprised it made any difference there :shock:

Yes, only the two close calls at the main's bottom matter. But I decided to close child's descriptors as well just because there's no error in doing that (close call returns no error) and because I may copy/paste a part of the code somewhere else later and then forget to add close.

---

