---
title: "Error: &quot;expected primary-expression &quot;"
date: 2009-09-01
forum: Programming Talk
---

### Post by abotaha on 2009-09-01
Could someone tell me what the error message "error: expected primary-expression before '{' token" means, or at least what I'm doing wrong?
Here's the code:

#include<iostream>
#include<conio.h>
#include<cmath>
#include <stdlib.h>
#include <iomanip>
using namespace std;
#define MAX 4
# define epsilon 0.38
//+++++++++++++++++++++++++++++++++++++++++++++++

void mulmatrix(int m, int n,int o,int p, long double **a, long double **b, long double **c)
{
  int i,j,k;

  for(i=0;i< m;i++)
          {
                     for(j=0;j< p;j++)
                     {
                                c[i][j] = 0;
                                for(k=0;k< o;k++)
                                {
                                           c[i][j] = c[i][j] + a[i][k] * b[k][j];
                                }
                     }
          }
}


// matrix inversion  
// the result is put in Y  

// calculate the cofactor of element (row,col)  
long double GetMinor(long double **src, long double **dest, int row, int col, int order)  
{  
    // indicate which col and row is being copied to dest  
    int colCount=0,rowCount=0;  
  
    for(int i = 0; i < order; i++ )  
    {  
        if( i != row )  
        {  
            colCount = 0;  
            for(int j = 0; j < order; j++ )  
            {  
                // when j is not the element  
                if( j != col )  
                {  
                    dest[rowCount][colCount] = src[i][j];  
                    colCount++;  
                }  
            }  
            rowCount++;  
        }  
    }  
  
    return 1;  
}  
// Calculate the determinant recursively.  
long double CalcDeterminant( long double **mat, int order)  
{  
    // order must be >= 0  
    // stop the recursion when matrix is a single element  
    if( order == 1 )  
        return mat[0][0];  
  
    // the determinant value  
    long double det = 0;  
  
    // allocate the cofactor matrix  
    long double **minor;  
    minor = new long double*[order-1];  
    for(int i=0;i<order-1;i++)  
        minor[i] = new long double[order-1];  
  
    for(int i = 0; i < order; i++ )  
    {  
        // get minor of element (0,i)  
        GetMinor( mat, minor, 0, i , order);  
        // the recusion is here!  
        det += pow( -1.0, i ) * mat[0][i] * CalcDeterminant( minor,order-1 );  
    }  
  
    // release memory  
    for(int i=0;i<order-1;i++)  
        delete [] minor[i];  
    delete [] minor;  
  
    return det;  
} 

void MatrixInversion(long double **A, int order, long double **Y)  
{  
    // get the determinant of a  
    long double det = 1.0/CalcDeterminant(A,order);  
  
    // memory allocation  
    long double *temp = new long double[(order-1)*(order-1)];  
    long double **minor = new long double*[order-1];  
    for(int i=0;i<order-1;i++)  
        minor[i] = temp+(i*(order-1));  
  
    for(int j=0;j<order;j++)  
    {  
        for(int i=0;i<order;i++)  
        {  
            // get the co-factor (matrix) of A(j,i)  
            GetMinor(A,minor,j,i,order);  
            Y[i][j] = det*CalcDeterminant(minor,order-1);  
            if( (i+j)%2 == 1)  
                Y[i][j] = -Y[i][j];  
        }  
    }  
  
    // release memory  
    delete [] minor[0];  
    delete [] minor;  
}  

//+++++++++++++++++++++++++++  MEAN VALUE ++++++++++++++++++++++++++++++++++++++
long double mean(long double arr[], int no)
{
    int i;
    long double sum = 0.0, avg;

    for (i = 0; i < no; i++)
	sum += arr[i];
    avg = sum / (long double) no;
    return avg;
}


//++++++++++++++++++++++++  VARIANCE VALUE  ++++++++++++++++++++++++++++++++++++

long double variance(long double arr[], int no)
{
    int i;
    long double sum = 0.0, tavg, avg, var;

    //for (i = 0; i < no; i++)
	//sum += arr[i];
    //tavg = sum / (long double) no;
    tavg = mean(arr, no);
    for (i = 0; i < no; i++)
	sum += (tavg - arr[i]) * (tavg - arr[i]);
	
    var = sum / (long double) (no - 1);
    return var;
}


//++++++++++++++++++++++++ MAIN PROGRAM ++++++++++++++++++++++++++++++++++++++++

main()
{
      long double a[MAX][MAX],Id[MAX],b[MAX][MAX],c[MAX][MAX],e[MAX][MAX],f[MAX][MAX],MO[MAX],PG[MAX],co[MAX],aMO,vMO, aPG,vPG,al,vl,exp,var;
      int iter,No,i,j,k,m,n=3,o,p;
      cout<<"Enyer the No. of iteration\n";
      cin>>No;
      long double lai[No][MAX], MOD[No][MAX], PG3[No][MAX], eps[MAX],cond;    
      for(iter=1;iter<No;iter++)
      {
      cout<<"Enter size vector of LAI values\n";
      cin>>m;
      
      MOD[4][0]={{3.17}, {4.43}, {3.15},{3.16}};
      
      cout<<"Enter the iteration "<<iter<<"   of LAI values of MODIS data\n";
      for(i=0;i<m;i++) {cin>>MO[i]; MOD[iter][i]=MO[i];/*cout<<"MOD[ "<<iter<<" ]= "<<MOD[iter]<<endl;*/ }
      cout<<"Enter the iteration "<<iter<<"   of LAI values output of 3-PG model\n";
      for(i=0;i<m;i++) {cin>>PG[i]; PG3[iter][i]=PG[i];}
      aMO=mean(MO, m);   vMO=variance(MO, m);  
      cout<<"the mean value of the "<<iter<<" iteration of MODIS data is:"<<"  "<<aMO<<"   "<<"the variance value of the "<<iter<<" iteration of MODIS data is:"<<"  "<<vMO<<"      "<<endl;
      aPG=mean(PG, m);   vPG=variance(PG, m); 
      cout<<"the mean value of the "<<iter<<" iteration of 3-PG output is:"<<"  "<<aPG<<"   "<<"the variance value of the "<<iter<<" iteration of 3-PG output is:"<<"  "<<vPG<<"      "<<endl;                                                    
      
      
                                   long double l[4][1]={{3.17}, {4.43}, {3.15},{3.16}};
                                   long double **ll = new long double *[4];
                                   for(int i=0;i<4;i++)ll[i]=new long double [1];
                                   for (int i=0; i<4; i++)
                                   for (int j=0; j<1; j++) ll[i][j]=l[i][j];
                                   for(i=0;i< 4;i++)
                                   {
                                              for(j=0;j< 1;j++)
                                              {
                                                         cout<<ll[i][j]<<" ";
                                              }
                                              cout<<"\n";
                                   }
                                                                     
                                  
                                   for (int i=0; i<4; i++)
                                   {lai[iter][i]=ll[i][0];
                                   
                                   cout.width(10);cout<<lai[iter][i]<<endl;}
                                   
                                   //+++++++++++++++++++++++++++++++++++++++++++
                                   cout<<"eps=  \n";
                                   for(i=0;i<MAX;i++)
                                   {eps[i]=fabs(MOD[iter-1][i]-MOD[iter][i]); 
                                   cout<<eps[i];
                                   }
                                   

                                  //+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ 
                                  cout<<"new lai after test \n";
                                   for(i=0;i<MAX;i++)
                                   {
                                                     cond=fabs((lai[iter-1][i]-MOD[iter][i])/lai[iter-1][i]);
                                                     if(cond<=epsilon)
                                                     {
                                                                      lai[iter][i]=MOD[iter][i];
                                                     }
                                                     else
                                                     {
                                                         lai[iter][i]=PG3[iter][i];
                                                     }
                                                      cout<<lai[iter][i]<<endl;
                                   
                                   }
                                   }                            
      system("pause");
      return 0;
      }

---

### Post by abotaha on 2009-09-01
Sorry i have to mentioned that the error appears when i add the line 
MOD[4][0]={{3.17}, {4.43}, {3.15},{3.16}};

which is the important line for my problem. 
I am new with c++ may be i did some think wrong. 

thanks in advance.

---

### Post by dwhitney67 on 2009-09-01
The error is because you are attempting to initialize an array in an illegal manner.  If you are indeed attempting to assign 4 values to the array, consider the following:
```

MOD[0][0] = 3.17;
MOD[0][1] = 4.43;
MOD[0][2] = 3.15;
MOD[0][3] = 3.16;

```

Upon examining your code, I also came across some code that is not permitted by ISO C++ standards, but I suppose with a "loose" compiler it works.
```

...
cout<<"Enyer the No. of iteration\n";
cin>>No;
long double lai[No][MAX], MOD[No][MAX], PG3[No][MAX], eps[MAX],cond; 
...

```
Here, the compiler is unaware of the value of "No" until run time.

Anyhow, revisit your code to determine exactly how you want to initialize your array.

P.S.  In the future, when posting code, please encapsulate it within [CODE ] [ /CODE] blocks, as I have demonstrated above.

---

### Post by abotaha on 2009-09-01
[SIZE="3"][SIZE="4"]oh thank you so much **dwhitney67**. it was wonderful.[/SIZE][/SIZE]:guitar:

---

