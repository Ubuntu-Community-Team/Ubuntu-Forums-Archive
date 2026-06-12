---
title: "Stop and Stop Executable from another Executable"
date: 2007-12-31
forum: Programming Talk
---

### Post by BadMoFo on 2007-12-31
Had a bit of a delay in finding a solution where I could start and stop an executable from another executable.  On Windows I typically use ShellExecute or ShellExecuteEx for starting and TerminateProcess to shutdown the executable.  On Linux the best I could come up w/ was the fpipe to start the exe and fpipe pkill to shutdown the exe.  I looked into using fork and exec* functions but was unable to get the exe I started stopped successfully and more often then not the exec* would start 2 instances.

I've added my source code below if someone has a better idea would like to see it so that I can optimize my code in the future.

***** CODE SECTION *****

#include <stdio.h>
#include <pthread.h>

#include <iostream>
#include <fstream>
using namespace std;

typedef struct
{
  pthread_mutex_t	*pLock;
  int			nThreadNum;		/* the number of the thread */
} THREAD_DATA;

void *RunVideoEngineProc(void *arg)
{
	THREAD_DATA threadData = *(THREAD_DATA *)arg;
//	if (threadData.pLock)
//		pthread_mutex_lock(threadData.pLock);

	FILE *fpipeStart = NULL;
	char *commandStart = "/home/david/Projects/VRADS/bin/VideoEngine -o /home/david/Projects/VRADS/bin/VideoCache.mp4v rtsp://192.168.123.138/media.amp";
//	char *commandStart = "/home/david/Projects/VRADS/bin/infinite";
	
	if ( !(fpipeStart = (FILE*)popen(commandStart, "r")) )
	{
		// If fpipeStart is NULL
		perror("Problems with pipe start");
	}
	else
	{
		sleep(30);	// Let Video Cache for 30 Seconds
	
		FILE *fpipeStop = NULL;
		char *commandStop = "pkill VideoEngine*";
//		char *commandStop = "pkill infinite*";
	
		if ( !(fpipeStop = (FILE*)popen(commandStop, "r")) )
		{
			// If fpipeStop is NULL
			perror("Problems with pipe stop");
		}
	
		pclose(fpipeStop);
	}
	
	pclose(fpipeStart);

//	if (threadData.pLock)
//		pthread_mutex_unlock(threadData.pLock);

	pthread_exit(0);
	return NULL;
}

int main(int argc, char **argv)
{
	pthread_t threadVideoEngine;
	void *retval = NULL;
	THREAD_DATA threadData;
  
	threadData.nThreadNum = 1;            /* the number of the thread */
//	pthread_mutex_t sLock; 
//	pthread_mutex_init(&sLock, NULL);
//	threadData.pLock = &sLock;

	string filename = "config.dat", fileData;
	ifstream fileStream;

	// While Loop waiting for config.dat - If config.dat appears then it means either 1) Start New Session or 2) Stop Current Session
	while (bContinue)
	{
		// Check for config.dat file
		fileStream.open(filename.c_str(), ifstream::in);
		if ( !fileStream.good() )
		{
			fileStream.close();
			sleep(1);
			continue;
		}

		// Read first line to determine state; Start New Session or Stop Current Session
		while (getline(fin,s))
		{
		}

		fileStream.close();

		// Start VideoEngine Thread to Cache Video to a file
		if (pthread_create(&threadVideoEngine, NULL, RunVideoEngineProc, &threadData ))
		{
			fprintf(stderr, "cannot make VideoEngine thread\n");
			return 1;
		}
		
		// Wait Indefinetly for VideoEngine Thread to Finish
		if (pthread_join(threadVideoEngine, &retval))
		{
			fprintf(stderr, "cannot join VideoEngine thread\n");
			return 1;
		}

	return 0;
}

---

### Post by LaRoza on 2007-12-31
> **BadMoFo said:**
> On Linux the best I could come up w/ was the fpipe to start the exe and fpipe pkill to shutdown the exe.  I looked into using fork and exec* functions but was unable to get the exe I started stopped successfully and more often then not the exec* would start 2 instances.


Are your refering to Linux programs as "exe"? Or are you using Cygwin on Windows?

(Use PHP or CODE tags if you post code, noone is going to try to read that)

---

