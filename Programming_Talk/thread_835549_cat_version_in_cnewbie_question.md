---
title: "cat version in c:newbie question"
date: 2008-06-20
forum: Programming Talk
---

### Post by cmay on 2008-06-20
hi.
this is my first c program.i have only programmed in a month.
its my version of the cat command. i have however this question
if its bad practice to declare int argc ,char argv in a function ?.
the program compiles and works fine. 
i dont have any class to follow or any other information than the 
tutorials i find on the net. and a single book i got on cc++.
i never found any specific information on this.

i declare this in the out function and the main as usual .
i could not make it compile otherwise.
is this a bad thing to do ?

my book mention a parameter getenv[] instead of  argv[]
its kind of old.

thanks for any input.
```


#include <stdio.h>
#include <stdlib.h>
char PROGNAME[]="dog";
FILE *infile;
FILE *outputfile;
int my_flag;
/***************: all globals:***********/
int  out();
void help();
void version();
void filecopy(FILE *inputfile,FILE *outputfile);

/********:the prototypes:****************/
int main(int argc,char *argv[]){
int c;
char *char_ptr;
while( argc > 1 && *(char_ptr=argv[1])=='-'){
argc--;
argv++;
switch(*++char_ptr){
case '?':
printf("i dont know \nwhy do you ask me \?\n");
exit(0);
case 'v':
version();
exit(0);
break;
case 'h':
help();
exit(0);
break;
case 'c':
my_flag++;
break;
default:
fprintf(stderr,"%s: unknown flag\n",PROGNAME);
exit(1);
}
}
/* 
 * if there is only argument then  usage : blahh blahh
*/
if(argc==1){
printf("USAGE: blahh blahh\n");
exit(1);
}
else
for(c=1;c<argc;c++)
if((infile=fopen(argv[c],"r"))==NULL)
fprintf(stderr,"%s: cant open %s \n",PROGNAME,argv[c]);
else
{
out(argc,argv);
fclose(infile);
}
exit(0);
}

/*********:end of main*****************/
void help(){
printf(" flag -v version \n");
printf(" flag -c works like cat command\n");
printf("so does no flag \n");
printf("\n");

}

int out(int argc, char *argv[])
{
FILE *filepointer;
void filecopy(FILE *,FILE *);
/* use this to give error message*/
char *prog =argv[0]; 

/* if there is no arguements then there is no need to argue*/     
if(argc == 1)        
filecopy(stdin,stdout);
else
while(--argc > 0)
if((filepointer=fopen(*++argv,"r"))==NULL)
{
	fprintf(stderr,"%s: cant open %s\n",prog,*argv);
	exit(1);
	} else {
	filecopy(filepointer,stdout);
	fclose(filepointer);
	}
	if(ferror(stdout))
	{
	fprintf(stderr,"%s:error in writing to stdout \n",prog);
	exit(2);
	}
	exit(0);
	}

void filecopy(FILE *inputfil,FILE *outputfil)
{
int c;
while((c=getc(inputfil))!=EOF)
putc(c,outputfil);
}

void version(){
printf("***************************************\n");
printf("* program :dog                        *\n");
printf("* version :this is my first c program *\n");
printf("* author  :cmay                       *\n");
printf("*license  :lgpl                       *\n");
printf("***************************************\n");
}
```

---

### Post by Qrikko on 2008-06-20
I hope I understand the question :)

but you are basically asking if it's "bad" or "wrong" to use the input arguments of a program?

in that case: no it's not bad :) it's what they are there for.

like the reason they are there is to help you giving initial input to a program.. can be flags, or other things. :)

and that your old book use another name then **argv is probably just some old convention or maybe related to some specific compiler or whatnot, it's just a name you could call them "variable_x" and "variable_y" if you want to :)

Hope I understood and more importantly could answer your question :)

Good luck with the C++ there are a LOT of great resources on the net so I think you will do just fine! :)

---

### Post by LaRoza on 2008-06-20
> **cmay said:**
> 
i declare this in the out function and the main as usual .
i could not make it compile otherwise.
is this a bad thing to do ?

my book mention a parameter getenv[] instead of  argv[]
its kind of old.

I didn't go over the code because it isn't formatted in a good way. 

getenv() is for getting environment variables. getopt() is a way of getting command line arguments. It works the same way, but allows for more structure. [http://www.gnu.org/software/libtool/manual/libc/Getopt.html](http://www.gnu.org/software/libtool/manual/libc/Getopt.html)

Using int argc (argument count) and char ** argv (argument vector) is standard and is the best way to name them.

> **Qrikko said:**
> 
Good luck with the C++ there are a LOT of great resources on the net so I think you will do just fine! :)

C, not C++.

---

### Post by nvteighen on 2008-06-20
```

/* ... */

while( argc > 1 && *(char_ptr=argv[1])=='-')
{
    argc--;
    argv++;
    switch(*++char_ptr)
    {
        
        /* ... */

```

Can't that be reduced to a for-loop traversing the array with a counter instead of modifying the pointer? Asking sincerely!

---

### Post by WW on 2008-06-20
> **cmay said:**
> hi.
this is my first c program.

Please help us help you by adopting an [indentation style](http://en.wikipedia.org/wiki/Indent_style); it doesn't really matter which style, as long as you use it *consistently*.
Lackofindentatio nislikewri tingwithspac esinth ewron gplaces;y ou caneven tuallyfig ureit out,bu titis moredif ficultt hannec essary.

---

### Post by cmay on 2008-06-20
hi thanks for the replies.
i have looked trough what i posted.
i should have had anhother version whit some more functions added 
and a bit more readable. 
but i must have deleted it. by accident
sorry for the inconvience .

however i was just reflecting upon having a fucntion whit the same argumenets as main. argc  and argv . that seems  a bit strange to me as i read it myselve but the program just wouldent compile otherwise. that could off course be the case of the deleted file.

i had writen a function that copied input and output to a file so
when you read the output as cat it was also saved to a file. 
its gone now  cant post it so you have to believe me when i say it was a bit more easy to read. 

thanks for your time.

---

