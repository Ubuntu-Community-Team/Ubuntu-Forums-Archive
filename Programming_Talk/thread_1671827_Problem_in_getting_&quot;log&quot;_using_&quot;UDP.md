---
title: "Problem in getting &quot;log&quot; using &quot;UDPSocket&quot; in a c++ program?!"
date: 2011-01-20
forum: Programming Talk
---

### Post by jeremy28 on 2011-01-20
Hi all;

I have a logger program (a .cpp file) that is intended to log all parts of my code (for debugging).

I've not written this code and want to ask you help me with a part of it, here is the necessary parts of logger code:

 	Code:
 	#include "PracticalSocket.h"
#include <time.h>

#define LOG_FILE	0
#define LOG_UDP		1

#ifndef NO_SOCKET
UDPSocket *loggerSocket = NULL;
#endif

FILE *fd = NULL;

void initLogger(int mode)
{
	if(mode == LOG_FILE)
	{
		fd = fopen("log.txt", "w");

		char buf[500];

		sprintf(buf, "%s\t\t\t\t%s\t%s\t%s\t%s\t%s\n", "Time", "PID", "TID", "FuncName", "LogType", "Parameters");

		fprintf(fd, buf);
	}

#ifndef NO_SOCKET
	else
	{
		loggerSocket = new UDPSocket(0);
	}
#endif

}


void logger(char* funcName, int logType, char* param)
{
	char buf[1500];

	time_t rawtime;
	struct tm * timeinfo;
	time(&rawtime);

	timeinfo = localtime ( &rawtime );

	char* temp = asctime(timeinfo);

	temp[strlen(temp) - 1] = 0;

	sprintf(buf, "%s\t%x\t%x\t%s\t%d\t%s\n", temp, getpid(), (unsigned int) pthread_self(), funcName, logType, param);

#ifndef NO_SOCKET

	if(loggerSocket != NULL)
	{
		loggerSocket->sendTo(buf, strlen(buf), "127.0.0.1", 10000);
	}
#endif

	if(fd != NULL)
	{
		fprintf(fd, buf);
		fflush(fd);
	}
} 
As you see, I have 2 functions:

initLogger: To initialize logging task in a process.

logger: To report various pieces of program running (including "function name" and "return value") in log file - that is initialized in "initlogger".

My project consists of two parts: a service daemon program and a shared object (so) library to do some functions using the service that is running in the background!

I call the "initlogger" two times: 

First time, in the service program with "LOG_FILE" mode (initlogger(LOG_FILE)), so that the "log.txt" file is created and
then the "logger" function is called multiple times to write the logs into the "log.txt".

Second time, in one of the library functions with "LOG_UDP" mode (initlogger(LOG_UDP)) and then the "logger" function is called several times again.

Currently, I've run the service and the "log.txt" is created and it logs everything correctly;

I have a test program to call the library's functions (that use the service) and want to see the related logs,

Now, My question is that how should I see the library logs?!

I mean, this line:
 	Code:
 	loggerSocket->sendTo(buf, strlen(buf), "127.0.0.1", 10000); 
I think I should install a "log server" software on my computer (linux), but I don't know what software? and how should I set the port (10000) in it? 

Unfortunately, I'm not familiar with "socket programming"!

The source of "PracticalSocket" is here:
 	Code:
 	[http://cs.baylor.edu/~donahoo/practical/CSockets/practical/PracticalSocket.cpp](http://cs.baylor.edu/~donahoo/practical/CSockets/practical/PracticalSocket.cpp) 
**Could you help me with establishing a "log server" on my computer OR give me other solution to see the library logs please?**

I want to use the "practical socket"(UDP) to log!

Best Regards.

---

### Post by jeremy28 on 2011-01-20
Hi all;
 
 I have a logger program (a .cpp file) that is intended to log all parts of my code (for debugging).
 
 I've not written this code and want to ask you help me with a part of it, here is the necessary parts of logger code:
```
#include "PracticalSocket.h"
#include <time.h>

#define LOG_FILE	0
#define LOG_UDP		1

#ifndef NO_SOCKET
UDPSocket *loggerSocket = NULL;
#endif

FILE *fd = NULL;

void initLogger(int mode)
{
	if(mode == LOG_FILE)
	{
		fd = fopen("log.txt", "w");

		char buf[500];

		sprintf(buf, "%s\t\t\t\t%s\t%s\t%s\t%s\t%s\n", "Time", "PID", "TID", "FuncName", "LogType", "Parameters");

		fprintf(fd, buf);
	}

#ifndef NO_SOCKET
	else
	{
		loggerSocket = new UDPSocket(0);
	}
#endif

}


void logger(char* funcName, int logType, char* param)
{
	char buf[1500];

	time_t rawtime;
	struct tm * timeinfo;
	time(&rawtime);

	timeinfo = localtime ( &rawtime );

	char* temp = asctime(timeinfo);

	temp[strlen(temp) - 1] = 0;

	sprintf(buf, "%s\t%x\t%x\t%s\t%d\t%s\n", temp, getpid(), (unsigned int) pthread_self(), funcName, logType, param);

#ifndef NO_SOCKET

	if(loggerSocket != NULL)
	{
		loggerSocket->sendTo(buf, strlen(buf), "127.0.0.1", 10000);
	}
#endif

	if(fd != NULL)
	{
		fprintf(fd, buf);
		fflush(fd);
	}
}
```

As you see, I have 2 functions:

initLogger: To initialize logging task in a process.

logger: To report various pieces of program running (including "function name" and "return value") in log file - that is initialized in "initlogger".

My project consists of two parts: a service daemon program and a shared object (so) library to do some functions using the service that is running in the background!

I call the "initlogger" two times: 

First time, in the service program with "LOG_FILE" mode (initlogger(LOG_FILE)), so that the "log.txt" file is created and
then the "logger" function is called multiple times to write the logs into the "log.txt".

Second time, in one of the library functions with "LOG_UDP" mode (initlogger(LOG_UDP)) and then the "logger" function is called several times again.

Currently, I've run the service and the "log.txt" is created and it logs everything correctly;

I have a test program to call the library's functions (that use the service) and want to see the related logs,

Now, My question is that how should I see the library logs?!

I mean, this line:
```
loggerSocket->sendTo(buf, strlen(buf), "127.0.0.1", 10000);
```

I think I should install a "log server" software on my computer (linux), but I don't know what software? and how should I set the port (10000) in it? 

Unfortunately, I'm not familiar with "socket programming"!

The source of "PracticalSocket" is here:
```
http://cs.baylor.edu/~donahoo/practical/CSockets/practical/PracticalSocket.cpp
```

Could you help me with establishing a "log server" on my computer OR give me other solution to see the library logs please?

I want to use the "practical socket"(UDP) to log!

Best Regards.

---

