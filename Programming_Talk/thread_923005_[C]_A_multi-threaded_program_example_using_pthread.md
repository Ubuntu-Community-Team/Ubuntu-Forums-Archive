---
title: "[C] A multi-threaded program example using pthread library"
date: 2008-09-17
forum: Programming Talk
---

### Post by dwhitney67 on 2008-09-17
It seems many newbie programmers have an interest in writing multi-threaded applications, and on occasion they post their questions here on the forum.

I thought it would be nice if there was an example program, for which they could refer to, to understand the basics of creating threads and protecting shared-data objects.

Below is a simple example which derives its requirements from this Ubuntu Forums Programming Talk [posting]("http://ubuntuforums.org/showthread.php?t=921735").  Please let me know if you have any (easy!) questions or comments.

[PHP]#ifndef _GNU_SOURCE
#define _GNU_SOURCE
#endif

#include <pthread.h>
#include <stdlib.h>    // for malloc and free
#include <unistd.h>    // for usleep
#include <stdio.h>     // for printf


// Job
//
typedef struct
{
  // the information in this structure can be whatever one chooses
  // to implement; the field 'data' is merely for test purposes
  unsigned int data;
} Job;


// JobList
//
typedef struct
{
  pthread_mutex_t mutex;
  Job **          jobs;
  unsigned int    numJobs;
  unsigned int    nextJob;
} JobList;


// Args
//
typedef struct
{
  int (*proc)( unsigned int, JobList * );    // the processor function for the thread
  unsigned int tnum;                         // thread identifier
  JobList *    jobList;                      // the list of jobs to be processed
} Args;


// Function definition(s)
//
int jobProcessor( unsigned int, JobList * );
void * startThread( void * );
Job * getNextJob( JobList * );
void setupMutex( pthread_mutex_t * );
void parseCmdLineOptions( int, char **, unsigned int *, unsigned int * );


// main()
//
int main( int argc, char **argv )
{
  // Default values, unless other value(s) specified on command line
  unsigned int NUM_JOBS    = 1000;
  unsigned int NUM_THREADS = 5;

  parseCmdLineOptions( argc, argv, &NUM_JOBS, &NUM_THREADS );


  // Create JobList with the jobs, and setup the mutex that will ensure
  // it is thread-safe...
  JobList jobList;

  setupMutex( &jobList.mutex );

  jobList.jobs    = malloc( sizeof(Job*) * NUM_JOBS );
  jobList.numJobs = NUM_JOBS;
  jobList.nextJob = 0;

  for ( unsigned int i = 0; i < NUM_JOBS; ++i )
  {
    jobList.jobs[i] = malloc( sizeof(Job) );

    jobList.jobs[i]->data = i;
  }


  // Setup thread args...
  Args args;

  args.jobList = &jobList;
  args.proc    = jobProcessor;


  // Create/start the threads...
  pthread_t tid[ NUM_THREADS ];
  pthread_attr_t attr;

  pthread_attr_setschedpolicy( &attr, SCHED_OTHER );

  for ( unsigned int i = 0; i < NUM_THREADS; ++i )
  {
    args.tnum = i;  // set thread number

    pthread_create( &tid[i], &attr, startThread, (void*) &args );
  }


  // Wait for each thread to finish...
  for ( unsigned int i = 0; i < NUM_THREADS; ++i )
  {
    int *status = 0;

    pthread_join( tid[i], (void**) &status );

    printf( "thread %u terminated with status = %d\n", i, (int)status );
  }


  // Free remaining allocated memory...
  free( jobList.jobs );

  return 0;
}


// jobProcessor()
//
int jobProcessor( unsigned int tnum, JobList *jobList )
{
  Job *job = 0;

  while ( (job = getNextJob(jobList)) != 0 )
  {
    // got a job; now do something with it...
    // printf( "Thread[%u], data = %u\n", tnum, job->data );   // commented out... not thread-safe!

    // destroy the job...
    free( job );

    // arbitrary delay to give other threads a chance to play...
    usleep( (rand() % 10) * 10000 );
  }

  return 0;
}


// startThread()
//
void * startThread( void *args )
{
  Args *a = (Args*) args;

  const int status = a->proc( a->tnum, a->jobList );

  pthread_exit( (void*) status );

  return NULL;
}


// getNextJob()
//
Job * getNextJob( JobList *jobList )
{
  Job *job = 0;

  // Enter critical section...
  pthread_mutex_lock( &jobList->mutex );

  // Get the next available job (if any)...
  if ( jobList->nextJob < jobList->numJobs )
  {
    job = jobList->jobs[ jobList->nextJob ];

    ++jobList->nextJob;
  }

  // Leave critical section...
  pthread_mutex_unlock( &jobList->mutex );

  return job;
}


// setupMutex()
//
void setupMutex( pthread_mutex_t *mutex )
{
  pthread_mutexattr_t attr;

  pthread_mutexattr_init( &attr );
  pthread_mutexattr_setpshared( &attr, PTHREAD_PROCESS_PRIVATE );
  pthread_mutexattr_settype( &attr, PTHREAD_MUTEX_DEFAULT );

  pthread_mutex_init( mutex, &attr );
}


// parseCmdLineOptions()
//
void parseCmdLineOptions( int argc, char **argv, unsigned int *numJobs , unsigned int *numThreads )
{
  int opt;

  while ( (opt = getopt( argc, argv, "j:t:" )) != -1 )
  {
    switch (opt)
    {
      case 'j': *numJobs    = atoi( optarg ); break;
      case 't': *numThreads = atoi( optarg ); break;

      default:
          printf( "Usage:  %s [-j <num jobs>] [-t <num threads>]\n", argv[0] );
          printf( "where by default 'num jobs' is 1000 and 'num threads' is 5\n\n" );
          exit(1);
    }
  }
}[/PHP]
To compile this program, run this command:
```
gcc -std=gnu99 ThreadExample.c -o threadExample
```
P.S.  This was my very first attempt at developing a pthread application in C!  I've done many in C++, which is much easier, whether using the pthread libraries or using the Boost libraries.

---

### Post by joe_bruin on 2008-09-18
jobList.jobs    = malloc( sizeof(Job) * NUM_JOBS );

should be

  jobList.jobs    = malloc( sizeof(Job*) * NUM_JOBS );

---

### Post by dwhitney67 on 2008-09-18
> **joe_bruin said:**
> jobList.jobs    = malloc( sizeof(Job) * NUM_JOBS );

should be

  jobList.jobs    = malloc( sizeof(Job*) * NUM_JOBS );

You're absolutely right.  I guess the program I originally presented worked because the size of the Job structure and the size of a pointer were coincidentally 4-bytes.

I will fix the code posted above.

Thanks!

---

