---
title: "File descriptor out of range evry time"
date: 2010-09-08
forum: Programming Talk
---

### Post by -A- on 2010-09-08
Whenever I call dup2, it returns -1. When I checked the file desciptor value of the file I opened against the return value of getdtablesize, it was way more. Is this why dup2 is returning -1? How do I solve this at runtime?

---

### Post by dwhitney67 on 2010-09-08
It is probably something you need to solve at compile time.  Better yet, why not start by posting some code to clearly show what you are trying to accomplish.  It also would help if you provided what the value of errno is.

---

### Post by -A- on 2010-09-08
Ok, I solved that, but I have this huge problem.

Heres my code...bit long:

```
#include<stdio.h>
#include<signal.h>
#include<unistd.h>
#include<sys/types.h>
#include<sys/wait.h>
#include<stdlib.h>
#include<fcntl.h>
#include<string.h>
#include<sys/stat.h>

#define SH_PROMPT ("GHOST")
#define ENDLINE ('\n')
#define PIPE_SPLIT ("|")
#define SPACE_SPLIT (" ")

//const char*argp[50],args[50];
int fdstdout, fdlog, fdstdin, fd;
int logFlag, fd;
const int lineLength=150;
int errFlag=0;
FILE *comlog;

//Functions//

int input_split(char a[], char *delimiter, char *argp[]);
void com_exec(char *arg[], int pargcount);
int intcom(char inp[]);
void readfile(char name[]);

int main()
{
    char entcommand[6];
    char excommand[3];
    char ex[5]="exit";
    char ent[6]="entry";
    char inp[200]={'\0'};
    char ext[3]="^D";
    char *com[20];
    char *arg[20];
    char c,rb;
    char *argp[50];
    int k=0;
    char *pipe;
    int pargcount=0;
    fdstdout=dup(1);
    fdstdin=dup(0);
    fdlog=open("output.log", O_RDWR|O_CREAT);
    fd=open("buffer.txt", O_RDWR|O_CREAT);    
    
    
    entagain:
    scanf("%s",entcommand);
    while(strcmp(ent,entcommand)!=0)
    {
        printf("Command line interpreter not started\n\n");
        fflush(stdout);
        //fflush(stdin);
        
        goto entagain;
    }
    
    entered:
    if(strcmp(ent,entcommand)==0)
    {
        //printf("Welcome to (Ghost in a) Shell!\n");        //Initial prompt display
        //printf("<%s>", SH_PROMPT);
        fflush(stdout);

        while(1)                        //Taking input string
        {    printf("Enter command.");
            rewind(stdin);
            fflush(stdout);
            
            c=getchar();
            //dup2(fdstdout,1);
            switch(c)
            {
                case ENDLINE: if(inp[0]=='\0')
                        {
                            dup2(fdstdout,1);
                            printf("<%s>", SH_PROMPT);
                            if(logFlag==1)
                            { 
                                fdlog=open("output.log", O_RDWR|O_CREAT|O_APPEND, S_IRWXG);
                                dup2(fdlog,1);
                            }
                        }        //If no input given
                        
                        else
                        {
                            inp[k]='\0';            //For exiting the shell
                            if(strcmp(inp,ex)==0)
                            {    k=0;
                                goto exit;
                            }
                            else                //Command execution
                            {
                                
                                //printf("%s\n", inp);
                                //pipe="|" ;
                                
                                if(logFlag==1)
                                {
                                    fdlog=open("output.log", O_RDWR|O_CREAT|O_APPEND);                            
                                    dup2(fdlog,1);
                                }
                                pargcount=input_split(inp,PIPE_SPLIT,argp);
                                com_exec(argp, pargcount);

                            }

                            //dup2(fdstdout,1);
                            //printf("<%s>", SH_PROMPT);
                            //if(logFlag==1)
                            //{
                            //    fdlog=open("output.log", O_RDWR|O_CREAT|O_APPEND);                        //    
                            //    dup2(fdlog,1);
                            //}
                            close(fd);
                            dup2(fdstdout,1);
                            fflush(stdout);
                            k=0;
                            printf("<%s>", SH_PROMPT);
                            if(logFlag==1)
                            {
                                comlog=fopen("command.log", "a");
                                fwrite(inp,1,strlen(inp),comlog);
                                fclose(comlog);
                            }
                            memset(inp,'\0',200);    
                            rb=getchar();                        
                            
                        }
                        break;
                
                default : inp[k++]=c;                    //writing the command string
                      break;        
                        
        }
                            
        
        
            
        }
    }
    exit:
    scanf("%s", excommand);
    while (strcmp(excommand,"entry")!=0)
    {
        printf("Shell has exited. \n");
        scanf("%s", excommand);
    }
    fflush(stdout);
    //rb=getchar();
    goto entered;
    return 0;
}

//Function for seperating the arguments, returns argument count//

int input_split(char inp[], char *delimiter, char *argp[])
{
    int i=0;
    int j=0;
    char *temp;
    
    if(strlen(inp)==0)
    {return 0;}

    else{
        
    temp=strtok (inp,delimiter);
                        //Stores the seperate commands/arguments into an array of pointers//
    while(temp!=NULL)
    {
        argp[i++]=temp;
        
        temp=strtok (NULL,delimiter);
    }
    return i;
    }
}

//Function for executing the commands//

void com_exec(char *arg[], int pargcount)
{
    if(pargcount==0)
    {
        printf("Wtf");
        //exit(0);
    }
    else
    {
    char *args[50];
    char *delim;
    int sargcount, j=0;
    long tbsz;
    pid_t pid1,pid2;

    if(pargcount==1)                //Implies either single command with arguments or internal command, i.e, no pipes
    {
        delim=" ";
        sargcount=input_split(arg[0],SPACE_SPLIT,args);
        if(!intcom(args[0]))
        {
            pid1=fork();
            
            if(!pid1)            //child process executing//
            {
                execvp(args[0],args);
                printf("EXECVP failed to execute.\n");
            }
            else if(pid1>0)
            {
                waitpid(pid1,NULL,0);        //Parent process executing//
            }
            else {printf("Child unborn.\n");}
        }
    }

    else                            //Multiple commands with pipes given//
    {
        //int fd;
        
        for(j=0;j<pargcount;j++)
        {
            if(j==0)
            {
                //fd=open("buffer.txt", O_RDWR|O_CREAT, S_IRWXG);    //First argument
                tbsz=getdtablesize();
                //close(fd);
                dup2(fd,1);
            }
            else if((j+1)==pargcount)
            {
                fd=open("buffer.txt", O_RDONLY);    //Last argument
                //close(fd);
                dup2(fd,0);
                dup2(fdstdout,1);
            }
            else
            {
                fd=open("buffer.txt",O_RDWR);        //In between arguments
                //close(fd);
                dup2(fd,1);
                dup2(fd,0);
            }
            delim=" ";
            sargcount=input_split(arg[j],delim,args);
            pid1=fork();
            if(!pid1)                    //child process executing
            {
                close(fd);
                execvp(args[0],args);
                printf("EXECVP failed to execute.\n");
            }
            else if(pid1>0)
            {
                waitpid(pid1,NULL,0);
            }
            else {printf("Child unborn.\n");}
        }
    }
    }
}



int intcom(char inp[])
{
   if (strcmp(inp,"log")==0)
   {
      printf("Now logging data \n");
      logFlag = 1;
      //close(fdlog);
      dup2(fdlog,1);
      
      
      return (1);  
   }         
   else if (strcmp(inp,"unlog")==0)
   {
      logFlag = 0;
      //close(fdstdout);
      dup2(fdstdout,1);
      printf("Logging no more. \n");
      return (1);  
   }
   else if (strcmp(inp,"viewcmd")==0)
   {
      // Implement Code for viewcmd
      printf("Command Log \n");
      readfile("command.log");
      return (1);
   }
   else if (strcmp(inp,"viewoutlog")==0)
   {
      // Implement Code for viewoutlog
      printf("Output Log \n");
      readfile("output.log");
      return (1);
   }
   else if (strcmp(inp,"changedir")==0)
   {
      // Implement Code for changedir
   }
   else
      return (0);
}        
    
void readfile(char name[])
{
   FILE *fp;
   char line[lineLength];
   fp = fopen(name,"r");
   while(fgets(line,sizeof(line),fp))
   {
      printf("%s",line);
   }
   fclose(fp);
}
```

SOme redundant things because I was error checking.
Thing is after it runs the first time, getchar() keeps taking in a character without me typing, and this keeps going on until it goes out of memory and hits a segmentation fault.

Why is getchar() taking a character without giving the prompt?

---

