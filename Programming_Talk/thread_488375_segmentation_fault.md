---
title: "segmentation fault"
date: 2007-06-30
forum: Programming Talk
---

### Post by psrujan on 2007-06-30
Hi ,

 I have little bit of knowledge in C++.When I run the following program its gives me segmentation error. I tried to do all the possible things by reading online but not able to figure out the error. I ran it suing gdb debugger but still it stays error is somewhere near n=atoi(argv[2]);
but i am not sure. Can somebdy please help me in finding the error.

I am using ubuntu. g++ compiler.

my command line arguments are 
./output 2 3 abc.pbm 1.2 abc2.pbm 1.3


#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <algorithm>
#include <iostream>
#include <time.h>

using namespace std;
#define MAX 90
#define Lwire 2       // length of the wire 2mm -- all values are for 130nm technology
#define Nwire 128     // Number of wires 128
#define Llink 0.5     // average link load .5
#define powerleakage 2032.8 // leakage power 2032.8nw
#define V 1    BIG_DYN[y]       // voltage= 1V
#define Ibias 1      // Ibias=1nA
#define K1 0.39
#define K2 .12
#define POP_SIZE 50
#define R_CO .33
#define R_MUT .1


 int pbm[MAX][MAX][MAX],pgm[MAX][MAX],dist[MAX][MAX]={0}; 
 int a=0,b=0,nodes,arg;
 //int m,n;
 double TotalDynEnergy=0,minTotalDynEnergy=0;
 char  head[4],head1[4];
 int maxd;
// int layoutnumber=0;
// int layoutminTotalDynEnergy;

/**** Dynamic Energy for each communication pattern ****/
 
 double energy( void)
{ int i,j,d;
  double powerdyn,powershtckt,powertotal,energy=0;
   
   maxd=0;
   powerdyn= ( K1 +( K2 * Lwire))* Nwire * Llink;// Dynamic power equation
         // printf("\n power dyn %f \t",powerdyn);
        //powershtckt=V*Ibias;
        // powertotal=sumlinks*(powerdyn+powerleakage+powershtckt);
       // printf("\n %f\n ",powertotal);

          for(j=0;j<b;j++)
          { for (i=0;i<a;i++)
            { 
              d=dist[j][i];    // printf("\n value of d   %d\t",d);		
             if(d > maxd)
		 maxd=d;     // max distance in the layout
             if (d!=0)
             {// Dynamic Energy for each entry in comm pattern
              energy= energy+(0.37*d)+(powerdyn*(d-1));     //  printf("\n energy %f",energy);
             } 	    
            }
           }
      //  printf("\n Dynamic energy for this pattern  is  %f \n",energy);
      // printf("pattmaxd %d ",maxd);
	  return(energy);
}
	                                                                                        
/**** Load Communication paterns ****/

void loadpatterns(int argc,char **argv,int index)
{ FILE *pbmread;
  int i,j;  


       pbmread = fopen (argv[arg],"r"); // open communication pattern file	    
      /* if (!pbmread)
           printf("\n Cannot open the Communication Pattern file ");
       else
           printf("\nCommunication Pattern with weight %s",argv[arg+1]);*/ 

      fscanf(pbmread,"%s\n%d %d\n",head,&a,&b);  //printf("\n%s\n%d  %d\n",head,a,b);

      for (j=0;j<b;j++)
        { for(i=0;i< a;i++)
             { fscanf(pbmread,"%d",&pbm[index][j][i]);  // printf("%d  ",pbm[index][j][i]);
              }
               //printf("\n");
        } 
   fclose(pbmread);
}	


/**** Distance Matrix and Total Dynamic Energy ****/

void groute(int argc,char **argv)
{
    int x1,y1,x2,y2,k,l;
    int index;
    double DynEnergy;
    float weight;
    int distance;
    int i,j;
  
   for (arg=3,index=0;arg<argc;arg+=2,index++)
    { 
      weight=atof(argv[arg+1]);
      loadpatterns(argc,argv,index); // FUNCTION Load Communication Pattern 
  
       for (j=0;j<b;j++)
       for (i=0;i<a;i++)
         { if (pbm[index][j][i]!=0)
               {for (l=0;l<m;l++)
                for (k=0;k<n;k++)
                  { if (pgm[l][k] == i)
                    { x1=l;y1=k;}
                   if (pgm[l][k]==j)
                    { x2=l;y2=k;}
                  }
                distance=(abs(y2-y1)+abs(x2-x1));// 'x+y'or manhattan distance between nodes for pbm[i][j]!=0
                dist[j][i]=distance; // Distance matrix
               }
	    if (pbm[index][j][i]==0)
	    {dist[j][i]=0;}    
          }
            /*printf("\nweight  %f ",weight);
               printf("\n\nDistance Matrix\n");
               for ( j=0;j<b;j++)
               { for ( i=0;i<a;i++)
                 printf("%d  ",dist[j][i]);
                 printf("\n");
                }*/
  DynEnergy= energy(); // FUNCTION Dynamic energy for the pattern
   TotalDynEnergy=TotalDynEnergy+DynEnergy;//Total Dynamic Energy for all patterns
   }
   
}



int main(int argc,char *argv[])
{ 
  int N_CO,N_MUT;
  
 int dim;
//m=2; n=3;
 // int ext1,ext2;
 //printf(" %d  %s  %s %s",argc,argv[1],argv[2],argv[3],argv[4]);
 int q; 
 printf("break1\n");
  m=atoi(argv[1]);
 n=atoi(argv[2]); // mxn layout
 printf("\n %d   %d",m ,n );
 dim=m*n;
  int x[dim]; 
  int POP[POP_SIZE][dim];
  float POP_DYN[POP_SIZE];
  int i,j,k,l;
  int first,second;
//  int* ptr_co;
  int t1[i];
  float t;
  int gen;
  int MAX_Gen=10;
  int layoutnumber=0;
  
  for ( i=0;i<dim;i++)
    x[i]=i;    
q=n;
printf(" q is %d",q);

/**** Initial pop ***/   
do { printf("enter loop");
  
      for(i=0;i<dim;i++)
       POP[layoutnumber][i]=x[i];
       printf("layout break1");
       
     l=0;k=0;
      for(i=0;i<dim;i++)
      {if (l==q)
        {k=k+1;l=0;}
       pgm[k][l]=x[i];   // layout of the nodes
         l++;
      }
            printf("node break/n");
//   groute(argc,argv);
  //  Dynamic Energy array
    POP_DYN[layoutnumber]=TotalDynEnergy;
       
    layoutnumber++;
     TotalDynEnergy=0;
    pskreddy
     }while((next_permutation(x,x+dim)) /*&& ( layoutnumber < POP_SIZE)*/);
}


when i run gdb it gives


#0  0xb7d3ed6c in __strtouq_internal () from /lib/tls/i686/cmov/libc.so.6
#1  0xb7d3eaff in __strtol_internal () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7d3c166 in atoi () from /lib/tls/i686/cmov/libc.so.6
#3  0x08048b26 in main (argc=2, argv=0xbfb64324) at groute.cpp:140
(gdb) up 3
#3  0x08048b26 in main (argc=2, argv=0xbfb64324) at groute.cpp:140
140       n=atoi(argv[2]); // mxn layout

It giving error for n but not m.. i dont know y 

I appreciate any help

pskr

---

### Post by PaulFr on 2007-06-30
Your debugger stack tells me one thing : you only ran the program with one argument - see the value of argc in the following:> #0 0xb7d3ed6c in __strtouq_internal () from /lib/tls/i686/cmov/libc.so.6
#1 0xb7d3eaff in __strtol_internal () from /lib/tls/i686/cmov/libc.so.6
#2 0xb7d3c166 in atoi () from /lib/tls/i686/cmov/libc.so.6
#3 0x08048b26 in main (argc=2, argv=0xbfb64324) at groute.cpp:140

argc = 2 means there was only two valid values in argv[] array: argv[0] is the name of the program, argv[1] is the 1st argument. No wonder it is crashing on argv[2] !

I would suggest you add a ```
for (int j = 1; j < argc; j++) { printf("Argument %d : %s\n", j, argv[j]); }
``` at the start of the main function to see what arguments the program is getting. Hope this helps.

---

### Post by nitro_n2o on 2007-06-30
go to main.. and get rid of 

```
int t1[i];
```

this is wht crashing your code.. 'i' is not initialized and thus might be a negative number, or a very large number.. 

Have fun :)

---

