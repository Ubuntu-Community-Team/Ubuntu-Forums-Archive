---
title: "C question: Unix vs Linux"
date: 2009-11-01
forum: Programming Talk
---

### Post by H.A.L on 2009-11-01
I am currently enrolled in a prereq for a masters in comp sci and I am having some problems running a C program on Ubuntu that runs fine on a SUN Unix computer.  My professor says that it should work on Linux with one change and that it has worked fine on other student's Linux computers in the past.  I have asked him the question and he is unsure of what might be causing the problem and suggested posting to a forum.  I am using Code::Blocks IDE and get the following errors:

/home/ryan/CSC389/csc389/loader/semshm.c:86: error: conflicting types for &#8216;sys_errlist&#8217;
/usr/include/bits/sys_errlist.h:28: error: previous declaration of &#8216;sys_errlist&#8217; was here

I figured that the problem was in one of the #include statements and that I could get around the previous declaration problem by renaming my variable to sys_errlist1[] rather than sys_errlist[].  Unfortunately, when I did this, a lot more errors popped up so I am not sure if I am on the right track or not.  I can post those errors if it will be helpful.  Below is the source code for the main program loader.c and the other file semshm.c which handles shared memory and semaphores for loader.  Any help would be greatly appreciated.

/* -------------------------- loader.c ----------------------- */
/* This is the shell for developing the loader cpu and printer */
/* for csc 389 project                                         */
#include <stdio.h>
#include <errno.h>
#include <fcntl.h> 
#include<sys/types.h>
#include<sys/ipc.h>
#include<sys/sem.h>
#include<sys/shm.h>
#define SLEEP_INC 1
#define BADADDR (char *)(-1)  /* used in getting shared memeory */ 
#define NUM_OF_SEMS 8         /* the number of sems to create */
#define OK_TO_LOAD0 0
#define OK_TO_LOAD1 1
#define OK_TO_EXEC0 2
#define OK_TO_EXEC1 3
#define OK_TO_SET_OUTPUT0 4
#define OK_TO_SET_OUTPUT1 5
#define OK_TO_PRINT0 6
#define OK_TO_PRINT1 7
#define HOWMANY_PROCESSES 3
#define HOWMANY_JOBS 2
#define MALLOC(x)           ((x *) malloc(sizeof(x)))
#define CLR system("clear")

#define TRUE 1
#define FALSE 0
int my_semid, my_shrmemid;    /* semaphore id and shared memory ids */
int my_key;                   /* key used to get shared memory */
int my_semval;
char *my_shrmemaddr;          /* address of shared memory */
typedef struct _pcb
  { int start_loc, num_instructions, output_loc;}
  pcb_type;
typedef struct _mem
  { char operation; int operand1, operand2, result;}
    memory_type;
int * load_job, *print_job;
pcb_type *pcbs;
memory_type *memory;
int size_of_memory;
int s, i;
/* functions to be invoked later */
void V();              /*release semaphore */
static void semcall(); /* call semop */
void P();              /* acquire semaphore */
void init_sem();       /* initialize semaphores */
void syserr();         /* print error messages */
void remove_shrmem();  /* remove shared memory */
void remove_sem();     /* remove semaphores */
void driver();         /* driver for forking processes */
void loader();
void cpu();
void printer();
int fill_memory();	
void execute_memory();
void print_memory();
main () 
{ /* main program */
/* this program uses semaphores and shared memory. Semaphores are
   used to protect the shared memory which serves as a message area
   for and sender and receiver process                             */
  int i ;
  setbuf(stdout, NULL);  
  /* get semaphore id and a given number of semaphores */
  if ((my_semid = semtran(NUM_OF_SEMS)) != -1) 
{
  /* initialize the semaphores */
init_sem(my_semid, OK_TO_LOAD0, 1);
init_sem(my_semid,OK_TO_LOAD1, 1);
init_sem(my_semid,OK_TO_EXEC0, 0);
init_sem(my_semid,OK_TO_EXEC1, 0);
init_sem(my_semid,OK_TO_SET_OUTPUT0, 1);
init_sem(my_semid,OK_TO_SET_OUTPUT1, 1);
init_sem(my_semid,OK_TO_PRINT0, 0);
init_sem(my_semid,OK_TO_PRINT1, 0);
}
  /* get shared memory segement id and attach it to my_shrmemaddr */
    size_of_memory = 2*sizeof(*load_job) + 2*sizeof(*print_job) + 
                   4*sizeof(*pcbs) + 40 * sizeof(*memory);

  if ((get_attach_shrmem(size_of_memory,&my_shrmemaddr,
        &my_shrmemid)) != -1)

  /* connect to shared memory at my_shrmemaddr */
  load_job = (int *) my_shrmemaddr;
  print_job = load_job + 2;
  pcbs = (pcb_type *) (print_job + 2);
  memory = (memory_type *) (pcbs + 4);
  /* call driver to do the work of forking senders and receivers */
     driver();
  /* wait until all processes have completed their work */
  for (i = 1; i <= HOWMANY_PROCESSES; i++) wait(&s);
  printf("ending \n");
  /* remove the semaphores */
  remove_sem(my_semid);
  /* remove the shared memory */
  remove_shrmem(my_shrmemid, my_shrmemaddr);
  exit(0);
} /* end of main */

void driver() /* driver to fork processes for readers and writers*/
{
/* fork processes to handle the work */
int pid;
      	if (( pid = fork() ) == -1) syserr("fork");
	if ( pid == 0 )
	  {
            loader();
            /* called printer just to test if loader
               was loading the shared memory         */
	    exit(0);
	  }
      	if (( pid = fork() ) == -1) syserr("fork");
	if ( pid == 0 )
	  {
            cpu();
	    exit(0);
	  }
      	if (( pid = fork() ) == -1) syserr("fork");
	if ( pid == 0 )
	  {
            printer();
	    exit(0);
	  }

} /* end of driver */


void loader()
{
FILE *fid;
int memory_to_load, current_job;
int more_jobs;
int job_read;
    if ((fid = fopen ("cpu.dat", "r")) == 0)
        {
        puts ("Unable to open file for reading.");
        return;
        }
    more_jobs = 2;    
    current_job = 0; 
    while (more_jobs)
        {
          if (current_job == 0)
            {
              P(my_semid, OK_TO_LOAD0);
              memory_to_load = 0;
              pcbs[current_job].start_loc = 0;
              pcbs[current_job].output_loc = 20;
              pcbs[current_job].num_instructions = 0;
              job_read = fill_memory(fid, memory_to_load);
              if (job_read != 4)
                {
                  more_jobs = more_jobs - 1;
                  load_job[current_job] = -1;
                }
              else
                load_job[current_job] = 1;
              V(my_semid, OK_TO_EXEC0);
            }                            
          else  
            {
              P(my_semid, OK_TO_LOAD1);
              memory_to_load = 10;
              pcbs[current_job].start_loc = 10;
              pcbs[current_job].output_loc = 30;
              pcbs[current_job].num_instructions = 0;
              job_read = fill_memory(fid, memory_to_load);
              if (job_read != 4)
                {
                  more_jobs = more_jobs - 1;
                  load_job[current_job] = -1;
                }
              else
                load_job[current_job] = 1;
              V(my_semid, OK_TO_EXEC1);
            }                            
          current_job = (current_job + 1) % 2;
        } /* end while more_jobs */
        /*  failed to read the four items */
        fclose(fid);
        return;
} /* end of load */        
int fill_memory (fid, memory_to_fill)
  FILE *fid;
  int memory_to_fill;
{

  int opcode_ok, end_of_job, bad_instruction;
  char opcode, cr;
  int operand1, operand2;
  int elements_read,
      current_pcb ;
  if (memory_to_fill == 0)
    current_pcb = 0;
  else 
    current_pcb = 1;
  elements_read = TRUE;
  while (elements_read )
    { 
       elements_read = fscanf (fid, "%c %d %d%c", &opcode, &operand1,
             &operand2,&cr);
       if (elements_read != 4)
         { 
           return(elements_read);
         }
       else
         {
           switch (opcode)
             {
             case '+':
                opcode_ok = TRUE;
                break;
              case '-':
                opcode_ok = TRUE;
                break;
              case '*':
                opcode_ok = TRUE;
                break;
              case '/':
                opcode_ok = TRUE;
                break;
              case '%':
                opcode_ok = TRUE;
                break;
              default :
                if (opcode == '?') 
                  {
                     bad_instruction = FALSE;
                     end_of_job = TRUE;
                  }
                else
                  {
                    end_of_job = FALSE; 
                    opcode_ok = FALSE;
		    bad_instruction = TRUE;
		  };
  
             } /* end of switch */
         } /* end of else elements read was 4 */
         if (end_of_job == TRUE)
               return( elements_read);
         pcbs[current_pcb].num_instructions = 
              pcbs[current_pcb].num_instructions + 1;
         memory[memory_to_fill].operation = opcode;
         memory[memory_to_fill].operand1 = operand1;
         memory[memory_to_fill].operand2 = operand2;
         memory_to_fill = memory_to_fill + 1;
         } /* end of while  for fill memory */
} /* end of fill memory */         

void cpu()
{
  int memory_to_execute, current_job;
  int where_to_output, memory_to_output;
  int more_jobs;
  current_job = 0;    
  more_jobs = 2;
  while (more_jobs)
    {                                                                  
      if (current_job == 0)                                            
        {                                                              
          P(my_semid, OK_TO_EXEC0);
          if (load_job[current_job] == -1)
            {
              more_jobs = more_jobs -1;
              P(my_semid, OK_TO_SET_OUTPUT0);
              print_job[current_job] = -1;
              V(my_semid, OK_TO_LOAD0);
              V(my_semid, OK_TO_PRINT0);
            }
          else
            {  
               execute_memory(current_job);
               P(my_semid, OK_TO_SET_OUTPUT0);
               pcbs[current_job + 2] = pcbs[current_job];
               memory_to_output = pcbs[current_job + 2].start_loc;
               where_to_output = pcbs[current_job + 2].output_loc;
               for (i = 1; i <= pcbs[current_job + 2].num_instructions; i++)
                 {
                   memory[where_to_output] = memory[memory_to_output];
                   memory_to_output = memory_to_output + 1;
                   where_to_output = where_to_output + 1;
                 }
               load_job[current_job] = 0;
               print_job[current_job] = 1;
               V(my_semid, OK_TO_LOAD0);
               V(my_semid, OK_TO_PRINT0);
            } /* end for else for load job[current_job] != -1  */
        }  
      else /* job is number 1 */
        {        
          P(my_semid, OK_TO_EXEC1);
          if (load_job[current_job] == -1)
            {
              more_jobs = more_jobs -1;
              P(my_semid, OK_TO_SET_OUTPUT1);
              print_job[current_job] = -1;
              V(my_semid, OK_TO_LOAD1);
              V(my_semid, OK_TO_PRINT1);
            }
          else
            {            
               execute_memory(current_job);
               P(my_semid, OK_TO_SET_OUTPUT1);                                       
               pcbs[current_job + 2] = pcbs[1];
               memory_to_output = pcbs[current_job + 2].start_loc;
               where_to_output = pcbs[current_job + 2].output_loc;
               for (i = 1; i <= pcbs[current_job + 2].num_instructions; i++)
                 {
                   memory[where_to_output] = memory[memory_to_output];
                   memory_to_output = memory_to_output + 1;
                   where_to_output = where_to_output + 1;
                 }
              load_job[current_job] = 0;
              print_job[current_job] = 1;
              V(my_semid, OK_TO_LOAD1);
              V(my_semid, OK_TO_PRINT1);
           } /* end for else for load job[1] != -1  */
         }
        current_job = (current_job + 1) % HOWMANY_JOBS;
    } /* end while more jobs */                                    
} /* end of cpu */
void execute_memory(current_job)
  int current_job;
{  
  int memory_to_execute;
  int i;
  if (current_job == 0)
    memory_to_execute = 0;
  else 
    memory_to_execute =10;
  for ( i = 1; i <= pcbs[current_job].num_instructions; i++)
    {
       switch (memory[memory_to_execute].operation)        
         {                                                  
         case '+':                                          
            memory[memory_to_execute].result =              
               memory[memory_to_execute].operand1 +         
               memory[memory_to_execute].operand2 ;         
            break;                                          
          case '-':                                         
            memory[memory_to_execute].result =              
               memory[memory_to_execute].operand1 -         
               memory[memory_to_execute].operand2 ;         
            break;                                          
          case '*':                                         
            memory[memory_to_execute].result =              
               memory[memory_to_execute].operand1 *         
               memory[memory_to_execute].operand2 ;         
            break;                                          
          case '/':                                         
            memory[memory_to_execute].result =              
               memory[memory_to_execute].operand1 /         
               memory[memory_to_execute].operand2 ;         
            break;                                          
          case '%':                                         
            memory[memory_to_execute].result =              
               memory[memory_to_execute].operand1 %         
               memory[memory_to_execute].operand2 ;         
            break;                                          
         } /* end of switch */                              
       memory_to_execute = memory_to_execute + 1;        
     }
}  /* end execute_memory */

void printer()
{
/* print jobs */
/* the code below was added to test if the loader was filling
   memory    
*/
int memory_to_print;
int current_print_job;
int more_print_jobs;
current_print_job = 0;
more_print_jobs = 2;
while (more_print_jobs)  
  {
     if (current_print_job == 0)
       {
          P(my_semid, OK_TO_PRINT0);
          if (print_job[current_print_job] == -1)
            {
               more_print_jobs = more_print_jobs - 1;
               V(my_semid, OK_TO_SET_OUTPUT0);
            }
          else
            {
               memory_to_print = 20;
               print_memory(current_print_job, memory_to_print); 
               print_job[current_print_job] = 0;
               V(my_semid, OK_TO_SET_OUTPUT0);
            }
       } /* end for current_print_job == 0 */
       else 
       {
          P(my_semid, OK_TO_PRINT1);
          if (print_job[current_print_job] == -1)
            {
               more_print_jobs = more_print_jobs - 1;
               V(my_semid, OK_TO_SET_OUTPUT1);
            }
          else
            {
               memory_to_print = 30;
               print_memory(current_print_job, memory_to_print);
               print_job[current_print_job] = 0;
               V(my_semid, OK_TO_SET_OUTPUT1);
            }
       } /* end of else for current_print_job == 2 */
     current_print_job = (current_print_job + 1) % 2;
  }  /* end of while */
} /* end of printer */

void print_memory( current_print_job, memory_to_print)
int current_print_job, memory_to_print;
{
  int i;
     printf("output for current job %d \n", current_print_job);
     for ( i =1; i <= pcbs[current_print_job + 2].num_instructions; i++)
       {
          printf("%c %d %d %d \n", memory[memory_to_print].operation,
                   memory[memory_to_print].operand1,
                   memory[memory_to_print].operand2,
                   memory[memory_to_print].result );
          memory_to_print = memory_to_print + 1;
        }
     printf("\n\n");   
} /* end of print_memory */
#include "semshm.c"


/* ------------------- semshm.c ---------------------------- */
/* Semaphore and shared memory routines -------------------- */
void remove_sem(sid) /* Used to remove semaphore with id sid */
int sid;
{
    (void)semctl(sid,0,IPC_RMID,0);
}

int semtran(nsems) /* Used to translate semaphore key to ID */
int nsems; /* Number of semaphores in the array of semaphores */
{
   int sid;

   if ((sid = semget(IPC_PRIVATE,nsems,0666|IPC_CREAT)) == -1)
      syserr("semget");
   return(sid); /* Returns the semaphore id in sid */
}

static void semcall(sid, sb) /* Calls semop to perform the operation */
                             /* described in the structure sb        */
int sid;
struct sembuf sb;
{
   if (semop(sid,&sb,1) == -1)
      syserr("semop");
}

void P(sid, which_sem) /* Will setup the sb structure for decrementing */
                       /* the semaphore for sid then calls semcall above */
                       /* to perform the P operation on the semaphore    */
int sid, which_sem;

{
struct sembuf sb;
   sb.sem_num = which_sem;
   sb.sem_op = -1;
   sb.sem_flg = 0;
   semcall(sid,sb);
}

void V(sid, which_sem) /* Will setup the sb structure for incrementing   */
                       /* the semaphore for sid then calls semcall above */
                       /* to perform the V operation on the semaphore    */
int sid, which_sem;
{
struct sembuf sb;
   sb.sem_num = which_sem;
   sb.sem_op = 1;
   sb.sem_flg = 0;
   semcall(sid,sb);
}

int getsem_val(sid, which_sem) /* Used to get the value of a semaphore  */
                               /* mainly used for testing and debugging */
int sid, which_sem;
{
  int value_of_sem;
  value_of_sem = semctl(sid,which_sem,GETVAL,0);
  return(value_of_sem); /* Will return the value of the semaphore */
}

void init_sem(sid, which_sem, init_val) /* Used to initialize the value of a */
                                        /* semaphore (which_sem)to the value */
                                        /* init_val                          */
/* **** NOTE USE DIFFERENT CODE FOR SUN AND LINUX IN SEMCTL BELOW ****  */
int sid, which_sem, init_val;
{
	union semun {
		int		val;
		struct semid_ds	*buf;
		ushort		*array;
	} semctl_arg;

  semctl_arg.val = init_val;
/* for the sun and hp use the line below */
//  (void) semctl(sid,which_sem,SETVAL, semctl_arg);
/* for linux use the line below and comment out the aboveline */
 (void) semctl(sid,which_sem,SETVAL, init_val);
}

void syserr(msg)
/* print system call error message and terminate */
char *msg;
{
    extern int errno,sys_nerr;
    extern char *sys_errlist[];

    fprintf(stderr,"ERROR: %s (%d",msg,errno);
    if (errno > 0 && errno < sys_nerr)
       fprintf(stderr,";%s)\n",sys_errlist[errno]);
    else
       fprintf(stderr,")\n");
    exit(1);
}

int get_attach_shrmem(num_bytes,addr,segid) /* get and attach shared memory */
                        /* for num_bytes in size and attach to address addr */
                        /* and store the id of the segment in segid */
int num_bytes;
char **addr;
int *segid;
{
 /*  char *shmat(); */
   if ((*segid =
        shmget(IPC_PRIVATE,num_bytes,0666|IPC_CREAT)) == -1)
       return(0);
   if ((*addr = shmat(*segid,0,0)) == BADADDR)
       return(0);
   return(1);
}

void remove_shrmem(segid, addr) /* remove the shared memory with segment */
                                /* id segid and address addr             */
int segid;
char *addr;
{
    (void)shmdt(addr);
    (void)shmctl(segid, IPC_RMID,0);
}

---

### Post by froggyswamp on 2009-11-01
I don't know but please consider next time using code formatting to significantly save space and improve readability.

---

### Post by dwhitney67 on 2009-11-01
@ the OP

Please repost your _complete_ code in CODE blocks so that it is more readable.

If you are unable/unwilling to post the complete code, then whittle it down to the bare essence of what is causing the Unix/Linux incompatibilities.

Thank you.

---

### Post by CptPicard on 2009-11-01
Just off the cuff reading the error message; you're redefining sys_errlist to be of different type than what it actually is in the header /usr/include/bits/sys_errlist.h.

Reading sys_errlist.h, we see

```

#ifndef _STDIO_H
# error "Never include <bits/sys_errlist.h> directly; use <stdio.h> instead."
#endif

/* sys_errlist and sys_nerr are deprecated.  Use strerror instead.  */

#ifdef  __USE_BSD
extern int sys_nerr;
extern __const char *__const sys_errlist[];
#endif
#ifdef  __USE_GNU
extern int _sys_nerr;
extern __const char *__const _sys_errlist[];
#endif

```


Can you rewrite your code to use the suggested strerror, considering what you're using seems to be deprecated?

---

### Post by terry_a_g on 2009-11-01
Try removing ```
extern char *sys_errlist[];
``` from function ```
void syserr(msg)
```

---

### Post by H.A.L on 2009-11-01
Thanks to all those who replied.  I apologize for not using code blocks.  I was unsure of how to make them, but will definitely use them in the future (just figured it out).  Terry, what you suggested got the program up and running and I now understand exactly why it was throwing the error--thanks for pointing it out CptPicard.  I really appreciate the help and the quick responses.

---

