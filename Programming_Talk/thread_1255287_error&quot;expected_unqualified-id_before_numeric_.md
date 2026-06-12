---
title: "error:&quot;expected unqualified-id before numeric constant&quot;"
date: 2009-09-01
forum: Programming Talk
---

### Post by abotaha on 2009-09-01
:confused::confused::confused:I am facing a strange problem, the following code was running successfully, but when I tried to extend  the code as my work needed and compile the final code after i updated, error message appears: **"expected unqualified-id before numeric constant"**.   Could any one help me please. The code is:
```
#include<iostream>
#include<conio.h>
#include<cmath>
#include <stdlib.h>
#include <iomanip>
using namespace std;
#define MAX 4
# define epsilon 0.5
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
      long double a[MAX][MAX],Id[MAX],b[MAX][MAX],c[MAX][MAX],e[MAX][MAX],f[MAX][MAX],MO[MAX],PG[MAX],co[MAX],aMO,vMO, aPG,vPG,al,vl,exp,var, sum=0.0;
      int iter,No,i,j,k,m,n=3,o,p;
      cout<<"Enyer the No. of iteration\n";
      cin>>No;
      long double lai[No][MAX], MOD[No][MAX], PG3[No][MAX], eps[MAX],cond, epsilon;    
      for(iter=1;iter<No;iter++)
      {
      cout<<"Enter size vector of LAI values\n";
      cin>>m;
      
      MOD[0][0] = 3.17; 
      MOD[0][1] = 4.43; 
      MOD[0][2] = 3.15; 
      MOD[0][3] = 3.16;
      
      cout<<"Enter the iteration "<<iter<<"   of LAI values of MODIS data\n";
      for(i=0;i<m;i++) {cin>>MO[i]; MOD[iter][i]=MO[i];/*cout<<"MOD[ "<<iter<<" ]= "<<MOD[iter]<<endl;*/ }
      cout<<"Enter the iteration "<<iter<<"   of LAI values output of 3-PG model\n";
      for(i=0;i<m;i++) {cin>>PG[i]; PG3[iter][i]=PG[i];}
      aMO=mean(MO, m);   vMO=variance(MO, m);  
      cout<<"the mean value of the "<<iter<<" iteration of MODIS data is:"<<"  "<<aMO<<"   "<<"the variance value of the "<<iter<<" iteration of MODIS data is:"<<"  "<<vMO<<"      "<<endl;
      aPG=mean(PG, m);   vPG=variance(PG, m); 
      cout<<"the mean value of the "<<iter<<" iteration of 3-PG output is:"<<"  "<<aPG<<"   "<<"the variance value of the "<<iter<<" iteration of 3-PG output is:"<<"  "<<vPG<<"      "<<endl;                                                    
      
      for(i=0;i<m;i++) Id[i]=1;
          
      for(i=0;i<m;i++)
      {
                      {
                               a[i][0]=MO[i]; a[i][1]=PG[i];a[i][2]=Id[i];
                      }
      }

cout<<"\n========== The Matrix a is ================\n";
for(i=0;i<m;i++)
{
                for(j=0;j<n;j++)
                {
                                cout<<a[i][j]<<" ";
                }
                cout<<"\n";
}
                       cout<<"\n====== The Transpose of a matrix a is b ======\n";  
                       o=n, p=m;
                       for(i=0;i< o;i++)
                       {
                                  for(j=0;j< p;j++)
                                  {
                                             b[i][j]=a[j][i];
                                             cout<<b[i][j]<<" ";
                                  }
                                  cout<<"\n";
                       }

                       long double **aa = new long double *[m];
                       for(int i=0;i<m;i++)aa[i]=new long double [n];
                       for (int i=0; i<m; i++)
                       for (int j=0; j<n; j++) aa[i][j]=a[i][j];
                       long double **bb = new long double *[o];
                       for(int i=0;i<o;i++)bb[i]=new long double [p];
                       for (int i=0; i<o; i++)
                       for (int j=0; j<p; j++) bb[i][j]=b[i][j];
                       long double **ccc = new long double *[o];
                       for(int i=0;i<o;i++)ccc[i]=new long double [o];
                       for (int i=0; i<o; i++)
                       for (int j=0; j<o; j++) ccc[i][j]=c[i][j];
                       for (int i=0; i<o; i++)
                       mulmatrix(o,p, m, n, bb , aa , ccc);
                       

                                  long double **cc = new long double *[o];
                                  for(int i=0;i<o;i++)cc[i]=new long double [o];
                                  for (int i=0; i<o; i++)
                                  for (int j=0; j<o; j++) cc[i][j]=ccc[i][j];
                                  
                                  long double **d =new long double *[m];
                                  for(int i=0;i<o;i++)d[i]=new long double [o];
                                  MatrixInversion(cc,o,d);
                                 
//++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
                                  long double **ee = new long double *[o];
                                  for(int i=0;i<o;i++)ee[i]=new long double [p];
                                  for (int i=0; i<o; i++)
                                  for (int j=0; j<p; j++) ee[i][j]=e[i][j];
                                  long double **dd = new long double *[o];
                                  for(int i=0;i<o;i++)dd[i]=new long double [o];
                                  for (int i=0; i<o; i++)
                                  for (int j=0; j<o; j++) dd[i][j]=d[i][j];
                                  /*long double **ccc = new long double *[o];
                                  for(int i=0;i<o;i++)ccc[i]=new long double [o];
                                  for (int i=0; i<o; i++)
                                  for (int j=0; j<o; j++) ccc[i][j]=c[i][j];*/
                                  for (int i=0; i<o; i++)
                                  mulmatrix(o,o, o, p, dd , bb , ee);

                                 
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
                                   long double **ff = new long double *[o];
                                   for(int i=0;i<o;i++)ff[i]=new long double [1];
                                   for (int i=0; i<o; i++)
                                   for (int j=0; j<1; j++) ff[i][j]=f[i][j];
                                   for (int i=0; i<o; i++)
                                   mulmatrix(3,4, 4, 1, ee , ll, ff);
                                   
                                   for (int i=0; i<4; i++)
                                   {lai[iter][i]=ll[i][0];
                                   
                                   cout.width(10);cout<<lai[iter][i]<<endl;}
                                   
                                   //+++++++++++++++++++++++++++++++++++++++++++
                                   cout<<"eps=  \n";
                                   for(i=0;i<MAX;i++)
                                   {eps[i]=fabs(MOD[iter-1][i]-MOD[iter][i]); 
                                   cout<<eps[i]<<endl;
                                   }
                                   for(i=0;i<MAX;i++)
                                   sum+=eps[i];
                                   epsilon=sum/MAX;
                                   cout<<"epsilon= "<<epsilon<<endl;

                                  //+++++++++++++++++++++++++++++++++++++++++++ 
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
                                                      cout<<lai[iter][i]<<"  \n";
                                                      
                                   
                                   }cout<<cond;
                                                      
                                   
                                   
                                   
                                   
                                   
                                  
                                   

                                 for(i=0;i< o;i++)
                                 {
                                            
                                            {
                                                       co[i]=ff[i][0];

                                            }
                                 }
                                 


                                   
                                   
                                   exp=co[2]+co[0]*aMO+co[1]*aPG;
                                   cout<<"the Expectation value of the "<<iter<<" iteration BN is:"<<"  "<<exp<<"\n";
                                   var=vPG+pow(co[0],2)*vMO+pow(co[1],2)*vPG;
                                   cout<<"the Variance value of the "<<iter<<" iteration BN is:"<<"  "<<var<<"\n";
      }
      system("pause");
      return 0; 
}


```
thanks in advance.

---

### Post by Arndt on 2009-09-01
> **abotaha said:**
> :confused::confused::confused:I am facing a strange problem, the following code was running successfully, but when I tried to extend  the code as my work needed and compile the final code after i updated, error message appears: **"expected unqualified-id before numeric constant"**.   Could any one help me please. The code is:
```
#include<iostream>
#include<conio.h>
#include<cmath>
#include <stdlib.h>
#include <iomanip>
using namespace std;
#define MAX 4
# define epsilon 0.5
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
      long double a[MAX][MAX],Id[MAX],b[MAX][MAX],c[MAX][MAX],e[MAX][MAX],f[MAX][MAX],MO[MAX],PG[MAX],co[MAX],aMO,vMO, aPG,vPG,al,vl,exp,var, sum=0.0;
      int iter,No,i,j,k,m,n=3,o,p;
      cout<<"Enyer the No. of iteration\n";
      cin>>No;
      long double lai[No][MAX], MOD[No][MAX], PG3[No][MAX], eps[MAX],cond, epsilon;    
      for(iter=1;iter<No;iter++)
      {
      cout<<"Enter size vector of LAI values\n";
      cin>>m;
      
      MOD[0][0] = 3.17; 
      MOD[0][1] = 4.43; 
      MOD[0][2] = 3.15; 
      MOD[0][3] = 3.16;
      
      cout<<"Enter the iteration "<<iter<<"   of LAI values of MODIS data\n";
      for(i=0;i<m;i++) {cin>>MO[i]; MOD[iter][i]=MO[i];/*cout<<"MOD[ "<<iter<<" ]= "<<MOD[iter]<<endl;*/ }
      cout<<"Enter the iteration "<<iter<<"   of LAI values output of 3-PG model\n";
      for(i=0;i<m;i++) {cin>>PG[i]; PG3[iter][i]=PG[i];}
      aMO=mean(MO, m);   vMO=variance(MO, m);  
      cout<<"the mean value of the "<<iter<<" iteration of MODIS data is:"<<"  "<<aMO<<"   "<<"the variance value of the "<<iter<<" iteration of MODIS data is:"<<"  "<<vMO<<"      "<<endl;
      aPG=mean(PG, m);   vPG=variance(PG, m); 
      cout<<"the mean value of the "<<iter<<" iteration of 3-PG output is:"<<"  "<<aPG<<"   "<<"the variance value of the "<<iter<<" iteration of 3-PG output is:"<<"  "<<vPG<<"      "<<endl;                                                    
      
      for(i=0;i<m;i++) Id[i]=1;
          
      for(i=0;i<m;i++)
      {
                      {
                               a[i][0]=MO[i]; a[i][1]=PG[i];a[i][2]=Id[i];
                      }
      }

cout<<"\n========== The Matrix a is ================\n";
for(i=0;i<m;i++)
{
                for(j=0;j<n;j++)
                {
                                cout<<a[i][j]<<" ";
                }
                cout<<"\n";
}
                       cout<<"\n====== The Transpose of a matrix a is b ======\n";  
                       o=n, p=m;
                       for(i=0;i< o;i++)
                       {
                                  for(j=0;j< p;j++)
                                  {
                                             b[i][j]=a[j][i];
                                             cout<<b[i][j]<<" ";
                                  }
                                  cout<<"\n";
                       }

                       long double **aa = new long double *[m];
                       for(int i=0;i<m;i++)aa[i]=new long double [n];
                       for (int i=0; i<m; i++)
                       for (int j=0; j<n; j++) aa[i][j]=a[i][j];
                       long double **bb = new long double *[o];
                       for(int i=0;i<o;i++)bb[i]=new long double [p];
                       for (int i=0; i<o; i++)
                       for (int j=0; j<p; j++) bb[i][j]=b[i][j];
                       long double **ccc = new long double *[o];
                       for(int i=0;i<o;i++)ccc[i]=new long double [o];
                       for (int i=0; i<o; i++)
                       for (int j=0; j<o; j++) ccc[i][j]=c[i][j];
                       for (int i=0; i<o; i++)
                       mulmatrix(o,p, m, n, bb , aa , ccc);
                       

                                  long double **cc = new long double *[o];
                                  for(int i=0;i<o;i++)cc[i]=new long double [o];
                                  for (int i=0; i<o; i++)
                                  for (int j=0; j<o; j++) cc[i][j]=ccc[i][j];
                                  
                                  long double **d =new long double *[m];
                                  for(int i=0;i<o;i++)d[i]=new long double [o];
                                  MatrixInversion(cc,o,d);
                                 
//++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
                                  long double **ee = new long double *[o];
                                  for(int i=0;i<o;i++)ee[i]=new long double [p];
                                  for (int i=0; i<o; i++)
                                  for (int j=0; j<p; j++) ee[i][j]=e[i][j];
                                  long double **dd = new long double *[o];
                                  for(int i=0;i<o;i++)dd[i]=new long double [o];
                                  for (int i=0; i<o; i++)
                                  for (int j=0; j<o; j++) dd[i][j]=d[i][j];
                                  /*long double **ccc = new long double *[o];
                                  for(int i=0;i<o;i++)ccc[i]=new long double [o];
                                  for (int i=0; i<o; i++)
                                  for (int j=0; j<o; j++) ccc[i][j]=c[i][j];*/
                                  for (int i=0; i<o; i++)
                                  mulmatrix(o,o, o, p, dd , bb , ee);

                                 
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
                                   long double **ff = new long double *[o];
                                   for(int i=0;i<o;i++)ff[i]=new long double [1];
                                   for (int i=0; i<o; i++)
                                   for (int j=0; j<1; j++) ff[i][j]=f[i][j];
                                   for (int i=0; i<o; i++)
                                   mulmatrix(3,4, 4, 1, ee , ll, ff);
                                   
                                   for (int i=0; i<4; i++)
                                   {lai[iter][i]=ll[i][0];
                                   
                                   cout.width(10);cout<<lai[iter][i]<<endl;}
                                   
                                   //+++++++++++++++++++++++++++++++++++++++++++
                                   cout<<"eps=  \n";
                                   for(i=0;i<MAX;i++)
                                   {eps[i]=fabs(MOD[iter-1][i]-MOD[iter][i]); 
                                   cout<<eps[i]<<endl;
                                   }
                                   for(i=0;i<MAX;i++)
                                   sum+=eps[i];
                                   epsilon=sum/MAX;
                                   cout<<"epsilon= "<<epsilon<<endl;

                                  //+++++++++++++++++++++++++++++++++++++++++++ 
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
                                                      cout<<lai[iter][i]<<"  \n";
                                                      
                                   
                                   }cout<<cond;
                                                      
                                   
                                   
                                   
                                   
                                   
                                  
                                   

                                 for(i=0;i< o;i++)
                                 {
                                            
                                            {
                                                       co[i]=ff[i][0];

                                            }
                                 }
                                 


                                   
                                   
                                   exp=co[2]+co[0]*aMO+co[1]*aPG;
                                   cout<<"the Expectation value of the "<<iter<<" iteration BN is:"<<"  "<<exp<<"\n";
                                   var=vPG+pow(co[0],2)*vMO+pow(co[1],2)*vPG;
                                   cout<<"the Variance value of the "<<iter<<" iteration BN is:"<<"  "<<var<<"\n";
      }
      system("pause");
      return 0; 
}


```
thanks in advance.

The error message probably contains a line number.

---

### Post by DaithiF on 2009-09-01
the space in here?
```
# define epsilon 0.5
```

---

### Post by abotaha on 2009-09-01
\\:D/\\:D/\\:D/i got the reason ....
the reason was i defined a fixed value  of epsilon in the beginning while i used in the code as a variable, so i just removed the line:

[COLOR="SeaGreen"]**# define epsilon 0.5**[/COLOR]

from the code, and it is working now. 

thanks.

---

### Post by matsuzine on 2009-09-01
In line 159 you declare a variable 'epsilon' which conflicts with the preprocessor constant defined in line 8.  

Renaming the long double variable in 159 from 'epsilon' to '_epsilon' everywhere in main() allows the program to compile for me.

```

long double lai[No][MAX], MOD[No][MAX], PG3[No][MAX], eps[MAX],cond, _epsilon;    


```

---

### Post by colau on 2009-09-01
> **abotaha said:**
> \\:D/\\:D/\\:D/i got the reason ....
the reason was i defined a fixed value  of epsilon in the beginning while i used in the code as a variable, so i just removed the line:

[COLOR="SeaGreen"]**# define epsilon 0.5**[/COLOR]

from the code, and it is working now. 

thanks.
Which editor did you use to write that code?

---

### Post by abotaha on 2009-09-01
i am using Dev-C++.

---

### Post by colau on 2009-09-01
> **abotaha said:**
> i am using Dev-C++.
Use Netbeans 6.7 .That IDE will help you to find the errors in your code easily.

---

### Post by abotaha on 2009-09-01
Thank you so much ...i will try....:popcorn::popcorn::-({|=

---

