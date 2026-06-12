---
title: "C errors"
date: 2010-03-12
forum: Programming Talk
---

### Post by newport_j on 2010-03-12
When I compile the code below, 

```


#include <stdlib.h>
#include <stdio.h>
#include <math.h>
#include <complex.h>

#include <pthread.h>
#include "thread.h"
#include "WAFmutex.h"

#include "WAFmathBase.h"
/*#include "WAFmathComplex99.h"*/
#include "SIMdefines.h"
#include "envstructdefs.h"
#include "WEGStrDefs.h"
#include "WEGFunDefs.h"

void VRT_RAY2( int IRAYo, int MINRAY, int MAXRAY, double TIMv,
	       LOGICAL *FSRFu, double ZSRF,  double COSSRF, double SINSRF,
	       LOGICAL *FBTMu, double ZBTM,  double COSBTM, double SINBTM,
	       TEST_RAY_DATA *TRD,
	       double *ZRAYu, double *TRAYu, double *PCOSu, double *PSINu,
	       int *NSRFu, int *NBTMu, int *NUPRu, int *NLWRu,
	       double *URAYu, double *FRAYu, double *ORAYu, ENV_DEF *Env ){

  int i, IRAY;
  double ZRFL, COSRFL2, SINRFL2;

  /*----------------------------
    Does the virtual type exist?
    ----------------------------*/

  if( MINRAY <= MAXRAY ){

    if( *FSRFu == true ){

      if( *FBTMu == true ){
	printf("VRT_RAY2 a\n");
	exit(1);
      };

      /*Reflect about the surface.*/
      ZRFL    = ZSRF;
      COSRFL2 = COSSRF*COSSRF - SINSRF*SINSRF;
      SINRFL2 = 2.0*SINSRF*COSSRF;

    } else {

      if( *FBTMu == false ){
	printf("VRT_RAY2 b\n");
	exit(1);
      };

      /*Reflect about the bottom.*/
      ZRFL    = ZBTM;
      COSRFL2 = COSBTM*COSBTM - SINBTM*SINBTM;
      SINRFL2 = 2.0*SINBTM*COSBTM;

    };

    /*---------------------
      Unfold the test rays.
      ---------------------*/

void VRT_RAY2_FIRST_GPU(IRAYo, MINRAY, MAXRAY, TIMv, *TRD, ZRFL, COSRFL2, SINRFL2,
                       *ZRAYu, *TRAYu, *PCOSu, PSINu,
                       *NSRFu, *NBTMu, *NUPRu, *NLWRu, ORAYu); 
 
     for(i=0;i<(*Env).Nfreq;i=i+1){
       for(IRAY=MINRAY;IRAY<=MAXRAY;IRAY=IRAY+1){
	URAYu[IRAY*MAX_NUM_FREQ+i] = TRD[IRAY].URAY[i] 
	  - (2.0 * M_PI) * (*Env).frequency_Hz[i] * TIMv;
	FRAYu[IRAY*MAX_NUM_FREQ+i] = TRD[IRAYo].FRAY[i];
      };

  
    };  /*Unfold the test rays.*/

  };  /*Does the virtual type exist.*/

}


void VRT_RAY2_FIRST_GPU(int IRAYog, int MINRAYg, int MAXRAYg, double TIMvg, 
                       TEST_RAY_DATA *TRD,
		       double ZRFLg, double COSRFL2g, double SINRFL2g,
                       double *ZRAYug, double *TRAYug, double *PCOSug, double *PSINug,
                       int *NSRFug, int *NBTMug, int *NUPRug, int *NLWRug, double ORAYug){  

    int IRAYg;         

    for(IRAYg=MINRAYg;IRAYg<=MAXRAYg;IRAYg=IRAYg+1)

      ZRAYug[IRAYg] = 2.0*ZRFLg - TRD[IRAYg].ZRAYug;
      TRAYug[IRAYg] = TRD[IRAYg].TRAYug;
      PCOSug[IRAYg] = TRD[IRAYg].PCOS*COSRFL2g + TRD[IRAYg].PSIN*SINRFL2g;
      PSINug[IRAYg] = TRD[IRAYg].PCOS*SINRFL2g - TRD[IRAYg].PSIN*COSRFL2g;

      NSRFug[IRAYg] = TRD[IRAYog].NSRF;
      NBTMug[IRAYg] = TRD[IRAYog].NBTM;
      NUPRug[IRAYg] = TRD[IRAYg].NUPR;
      NLWRug[IRAYg] = TRD[IRAYg].NLWR;
      ORAYug[IRAYg] = TRD[IRAYog].ORAY;
    };
       



```

I get the following errors:

 In function ‘VRT_RAY2’:
test2.c:65: error: expected ‘)’ before ‘*’ token
test2.c: In function ‘VRT_RAY2_FIRST_GPU’:
test2.c:94: error: ‘TEST_RAY_DATA’ has no member named ‘ZRAYug’
test2.c:95: error: ‘TEST_RAY_DATA’ has no member named ‘TRAYug’
test2.c:103: error: subscripted value is neither array nor pointer

Now my main concern is with the error:

test2.c:65: error: expected ‘)’ before ‘*’ token

How do I correct that error?

Also, the error: 


test2.c:103: error: subscripted value is neither array nor pointer

I agree is is neither an array nor pointer, it is merely a subscripted variable. I subscripted ORAYug with a u just like the variable in the calling code and gave it also
a g to designate it is now in another program. How, do I correct it?

I will ignore the errors on line 94 and 95 for now.


Newport_j

---

### Post by PmDematagoda on 2010-03-12
You have many syntax errors in your coding(style faults as well, but they aren't the real problem), such syntax errors include not enclosing the functions in closing braces, using a semi-colon after a closing brance(this is unnecessary unless you are declaring a struct or something similar). In fact, I don't think I could call your code C, perhaps a mixture of BASH and C(which unfortunately is unsupported by GCC as of yet :)).

What book did you use to learn C? As a book to use to learn C, I would suggest Herbert Schlidt's(his latest C Reference has all the faults fixed :)). But many people would also suggest the K&R reference book, and considering that it has been written by pretty much the pioneers of the language, you would be better off with that. :)

---

### Post by Xyro on 2010-03-12
+1 for above comment. Unfortunately the code you are working with here requires a much greater level of understanding of C than you apparently have. Doing some reading and trying something much simpler would be a far better (and faster) approach to solving this problem.

---

### Post by dwhitney67 on 2010-03-12
+2 for the previous two posts.

newport, I believe that some of the errors relate to missing curly braces:
```

void VRT_RAY2(...) {

...

      /*Reflect about the bottom.*/
      ZRFL    = ZBTM;
      COSRFL2 = COSBTM*COSBTM - SINBTM*SINBTM;
      SINRFL2 = 2.0*SINBTM*COSBTM;

    };

    /*---------------------
      Unfold the test rays.
      ---------------------*/
}   <--- Missing

void VRT_RAY2_FIRST_GPU(...)
{   <--- Missing
...


```


P.S.  I hope your next question is derived from the K&R book.  Frankly, I am getting bored reading your posts with the most basic of questions that anyone, who spent at least a day reading the K&R book, would be able to sort out.

---

