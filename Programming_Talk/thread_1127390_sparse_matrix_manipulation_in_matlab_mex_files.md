---
title: "sparse matrix manipulation in matlab mex files"
date: 2009-04-16
forum: Programming Talk
---

### Post by nitro_n2o on 2009-04-16
Hi all,

i'm try to build a sparse matrix in matlab mex file from a data file. I can get the the row, column and value, but the values in the matrix are never written!

can any one help on how to a sparse matrix using a mex files?

Thanks in advance

---

### Post by kjohansen on 2009-04-16
post the code you have so far.

mex allows you to write C functions for use with matlab, so your sparse matrix manip is written in C not mex, mex is not a language.  There are some special functions in "mex.h" for access to the inputs and outputs...

---

### Post by nitro_n2o on 2009-04-16
yeah sure i understand 

so here is what i do 

plhs[0] = mxCreateSparse(100,100,20,mxREAL); 
int *ir = mxGetIr(plhs[0]);
int *jc = mxGetJc(plhs[0]);
double *pr = mxGetPr(plhs[0]); 

int r, c; 
double v;
int k=0;
/* line looks like this: 1 3 32.8 */
while(fgets(line,sizeof line, fp)){ 
  sscanf(line,"%d %d %f",&r,&c,&v); 
  ir[k] = r; 
  jc[k] = c;
  pr[k] = v;
  k++;
}


After that the matrix returned is just All zeros 100x100 sparse

---

### Post by ubuMike on 2009-09-23
Same Problem Here!

```
//read matrix
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "mex.h"
#include "matrix.h"


struct sparseMtx{
		float len;
		unsigned int pixel; //0 to 4,294,967,295
		unsigned int voxel; //0 to 4,294,967,295
};

void mexFunction(
    int nlhs, mxArray *plhs[],
    int nrhs, const mxArray *prhs[])
{
    char *filename = mxArrayToString(prhs[0]);

    int* MNmax = (int*)mxGetData(prhs[1]);

    //M pixels N voxels
    plhs[0] = mxCreateSparse(MNmax[0],MNmax[1],MNmax[2],mxREAL);
    double *sr = mxGetPr(plhs[0]);
    int* irs = mxGetIr(plhs[0]);
    int* jcs = mxGetJc(plhs[0]);
    
    //get 
    int lenDim[] = {1,MNmax[2]};
    plhs[1] = mxCreateNumericArray(2,lenDim,mxSINGLE_CLASS,mxREAL);
    plhs[2] = mxCreateNumericArray(2,lenDim,mxINT32_CLASS,mxREAL);
    plhs[3] = mxCreateNumericArray(2,lenDim,mxINT32_CLASS,mxREAL);
    float* s = (float*)mxGetData(plhs[1]);
    int* ir = (int*)mxGetData(plhs[2]);
    int* jc = (int*)mxGetData(plhs[3]);
    
    //open file
    FILE *mtxData;
    mtxData = fopen(filename,"r");
    sparseMtx *matrix;
    matrix = new(sparseMtx);
    
    for(int i=0; i<MNmax[2];i++){
        fread ( matrix, 1, sizeof(sparseMtx), mtxData );
        
        sr[i] = (double)matrix->len;
        irs[i] = (int)matrix->pixel;
        jcs[i] = (int)matrix->voxel;
        
        s[i] = matrix->len;
        ir[i] = matrix->pixel;
        jc[i] = matrix->voxel;
        
        printf("%i\n",irs[i]);
    }
    
    fclose(mtxData);
}
```

The output from s ir and jc show up fine, but the sparse matrix is empty!!!

---

### Post by ubuMike on 2009-09-23
Google compressed-column form

ir and jc must be non-zero and increasing.

---

