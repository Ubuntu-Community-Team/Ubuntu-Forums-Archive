---
title: "Global variables"
date: 2010-02-04
forum: Programming Talk
---

### Post by newport_j on 2010-02-04
I have a question about c programing in Linux or Ubuntu. I think that it is relevant to this Forum. The questions is about using global variables and files. Global variables are available to all subprograms in the computer program. I am going to post two subprograms from a program that I am maintaining and I think the question should be obvious. The first subprogram:

```


/*! \file    int_bnd2.c
  \brief     integrates Gaussian ray bundles.
  \par
  \author     Phred
  \author     Weinberg
*/


/* WEG (WAF Eigenray Generator) 

Translated to "c" and modifided by Andrew "Phred" Fredricks
form work done by Chic Weinberg.

* Function INT_BND2  integrates Gaussian ray bundles.

Variables

*   ZTRG = target depth (km)
* APRMIN = minimum ray bundle aperture (km)

*  NANGv = number of source angles
*   ANGv = source angle vector (rad)
*   PWRv = source pressure squared vector (uPa^2)

* IRAYu1 = leading  ray index
* IRAYu2 = trailing ray index
* ZVRTu1 = leading  virtual ray depth (km)
* ZVRTu2 = trailing virtual ray depth (km)

*   RRAY = ray range (km)

*   ZRAYu = unfolded ray depth (km)
*   TRAYu = unfolded ray time (s)
*   PCOSu = unfolded ray horizontal slowness (s/km)
*   PSINu = unfolded ray vertical slowness (s/km)

*   NUPRu = number of unfolded upper vertexes
*   NLWRu = number of unfolded lower vertexes
*   NCRSo = number of ray crossings

*   URAYu = unfolded ray attenuation (nepers)
*   FRAYu = unfolded ray factor (pres ratio)
*   ORAYu = unfolded ray phase (rad)

*    NSRF = number of surface reflections
*    NBTM = number of bottom reflections
*  UPRSUM = weighted upper vertex sum
*  LWRSUM = weighted lower vertex sum

*  SRCSUM = weighted source angle sum (rad)
*  PWRSUM = pressure squared sum (uPa^2)
*  TIMSUM = weighted time sum (s)
*  PHSSUM = weighted phase sum (rad)
*  PCSSUM = weighted horizontal slowness sum (s/km)
*  PSNSUM = weighted vertical slowness sum (s/km)
*  IMAFLG = eigenray flag {0,1} for {real,imag} eigenrays

* EIGTOLi = eigenray tolerance

***********************************************************************/

#include <stdlib.h>
#include <stdio.h>
#include <math.h>
#include <complex.h>

#include <pthread.h>
#include "thread.h"
#include "WAFmutex.h"

#include "WAFmathBase.h"
#include "SIMdefines.h"
#include "envstructdefs.h"
#include "WEGStrDefs.h"
#include "WEGFunDefs.h"

/*!\brief
  integrates Gaussian ray bundles.
  \param     ZTRG       target depth (km)
  \param     PTRG

  \param     SCST
  \param     APER
  \param     TRD        Test Ray Data
  \param     IRAYu1     leading  ray index
  \param     IRAYu2     trailing ray index
  \param     ZVRTu1     leading  virtual ray depth (km)
  \param     ZVRTu2     trailing virtual ray depth (km)
  \param     RRAY       ray range (km)
  \param     ZRAYu      unfolded ray depth (km)
  \param     TRAYu      unfolded ray time (s)
  \param     PCOSu      unfolded ray horizontal slowness (s/km)
  \param     PSINu      unfolded ray vertical slowness (s/km)
  \param     NSRF       nu
mber of surface reflections
  \param     NBTM       number of bottom reflections
  \param     NUPRu      number of unfolded upper vertexes
  \param     NLWRu      number of unfolded lower vertexes
  \param     NCRSo      number of ray crossings
  \param     URAYu      unfolded ray attenuation (nepers)
  \param     FRAYu      unfolded ray factor (pres ratio)
  \param     ORAYu      unfolded ray phase (rad)
  \param     UPRSUM     weighted upper vertex sum
  \param     LWRSUM     weighted lower vertex sum
  \param     SRCSUM     weighted source angle sum (rad)
  \param     RCVSUM     weighted recive angle sum (rad)
  \param     PWRSUM     pressure squared sum (uPa^2)
  \param     TIMSUM     weighted time sum (s)
  \param     PHSSUM     weighted phase sum (rad)
  \param     PCSSUM     weighted horizontal slowness sum (s/km)
  \param     PSNSUM     weighted vertical slowness sum (s/km)
  \param     IMAFLG     eigenray flag {0,1} for {real,imag} eigenrays
  \param     Env

*/
void INT_BND2( double ZTRG, double PTRG,
	       LOGICAL  SCST, double APER, TEST_RAY_DATA *TRD,
	       int IRAYu1, int IRAYu2, double ZVRTu1, 
	       double ZVRTu2, double RRAY,   double *ZRAYu,  double *TRAYu,  
	       double *PCOSu,  double *PSINu, int NSRF,   int NBTM,   
	       int *NUPRu,  int *NLWRu,  int NCRSo, double *URAYu,  
	       double *FRAYu,  double *ORAYu, double *UPRSUM, double *LWRSUM,
	       double *SRCSUM, double *RCVSUM, double *PWRSUM, double *TIMSUM, double *PHSSUM,
	       double *PCSSUM, double *PSNSUM, int *IMAFLG,
	       ENV_DEF *Env){

  int i, IRAY, NRFLo, NCSTo;
  double ZBND1=0.0, ZBND2=0.0, ZDEL, ZAPR, SDEV, ZREL, ARG; 
  double PWR[MAX_NUM_FREQ], TTRG, ARGMAX;
  double APRMIN=666.0, APRMINt, TOTPWR;

  /*
    EIGTOLi = eigenray tolerance
    APRMIN     minimum ray bundle aperture (km)
  */
  /*-----------------------------------------------------------------
    Set the maximum ray bundle argument for  ARG = 0.5*(ZREL/SDEV)**2
    so that
    exp(-ARGMAX/2)  = EIGTOLi/10
    -----------------------------------------------------------------*/

  ARGMAX = - 2.0 * log( 0.1*EIGTOLi + 1.0E-30 );

  /*-----------------------------------------
    Initialize the eigenray flag (imaginary).
    -----------------------------------------*/

  *IMAFLG = 1;

  /*---------------------------
    Set the number of caustics.
    ---------------------------*/

  NRFLo = NSRF + NBTM;
  if(NCRSo-NRFLo > 0) NCSTo = NCRSo-NRFLo;
  else NCSTo = 0;

  /*-------------------------
    Initialize weighted sums.
    -------------------------*/


  *UPRSUM = 0.0;
  *LWRSUM = 0.0;
  *SRCSUM = 0.0;
  *RCVSUM = 0.0;
  *TIMSUM = 0.0;
  *PCSSUM = 0.0;
  *PSNSUM = 0.0;

  for(i=0;i<(*Env).Nfreq;i=i+1){
    PWRSUM[i] = 0.0;
    PHSSUM[i] = 0.0;
  };

  /*-------------------------------------------------
    Integrate the ray bundles within [ZVRTu1,ZVRTu2].
    -------------------------------------------------*/

  /*printf("IRAYu1=%d IRAYu2=%d\n",IRAYu1,IRAYu2);*/
  
  for(IRAY=IRAYu1;IRAY<=IRAYu2;IRAY=IRAY+1){

    /*-----------------------------
      Set the initial bundle depth.
      -----------------------------*/


    if( IRAY > IRAYu1 ) ZBND1 = 0.5*(ZRAYu[IRAY]+ZRAYu[IRAY-1]);
    if( IRAY == IRAYu1 ) ZBND1 = 0.5*(ZRAYu[IRAY]+ZVRTu1);

    /*---------------------------
      Set the final bundle depth.
      ---------------------------*/

    if( IRAY < IRAYu2 ) ZBND2 = 0.5*(ZRAYu[IRAY]+ZRAYu[IRAY+1]);
    if( IRAY == IRAYu2 ) ZBND2 = 0.5*(ZRAYu[IRAY]+ZVRTu2);

    /*-------------------------------------
      Compute the test ray-target distance.
      -------------------------------------*/

    /*------------------------------------
      Set the minimum ray bundle aperture.
      ------------------------------------*/
    for(i=0;i<(*Env).Nfreq;i=i+1){
      if( SCST != true ){
	if(APER < 16*M_PI/(PTRG*(*Env).frequency_Hz[i])) APRMINt = APER;
	else APRMINt = 16*M_PI/(PTRG*(*Env).frequency_Hz[i]);
	/*--------------------------------------------------------
	  Set the minimum ray bundle aperture at a smooth caustic.
	  --------------------------------------------------------*/
      } else {
	if(APER < 4*M_PI/(PTRG*(*Env).frequency_Hz[i])) APRMINt = APER;
	else APRMINt = 4*M_PI/(PTRG*(*Env).frequency_Hz[i]);
      };

      if(APRMINt<APRMIN) APRMIN = APRMINt;
    };

    ZDEL = ZBND2 - ZBND1;
    ZAPR = fabs(ZDEL);
    if(ZAPR > APRMIN) SDEV = 0.5 * ZAPR;
    else SDEV = 0.5 * APRMIN;
    ZREL = ZTRG - ZRAYu[IRAY];

    /*------------------------------
      Compute the Gaussian argument.
      ------------------------------*/

    ARG = 0.5*(ZREL/SDEV)*(ZREL/SDEV);
    if( ARG < 0 ){  
      printf("INT_BND2\n");
      exit(1);
    };
    if( ARG < ARGMAX ){

      /*-----------------------------
	Compute the pressure squared.
	-----------------------------*/

      for(i=0;i<(*Env).Nfreq;i=i+1){
	PWR[i] = TRD[IRAY].PWRv 
	  * FRAYu[IRAY*MAX_NUM_FREQ+i] * FRAYu[IRAY*MAX_NUM_FREQ+i]
	  * exp(2.0*URAYu[IRAY*MAX_NUM_FREQ+i]-ARG)
	  / (sqrt(2*M_PI)*SDEV*PCOSu[IRAY]*RRAY);

	/* GRAB fix !!!!!!!!*/
	/*PWR[i] = ZAPR * (exp(-ARG) / (sqrt(2*M_PI)*SDEV))
	  * FRAYu[IRAY*MAX_NUM_FREQ+i] * FRAYu[IRAY*MAX_NUM_FREQ+i]
	  * exp(2.0*URAYu[IRAY*MAX_NUM_FREQ+i])/(RRAY * RRAY * 1000.0 * 1000.0);*/
      };

      /*printf("%f %f %f %f Pzdel=%f ZDEL=%f Normal=%f FRAYu=%f URAYu=%f RRAY=%f Loss=%f",
          ARG, exp(-ARG),
	  (TRD[IRAY].PWRv * 1000.0 * 1000.0 / PCOSu[IRAY]),RRAY,
	  (TRD[IRAY].PWRv * 1000.0 * 1000.0 / PCOSu[IRAY])*RRAY, ZDEL,
	  exp(-ARG) / (sqrt(2*M_PI)*SDEV),
	  20.0*log10(FRAYu[IRAY*MAX_NUM_FREQ+0]),
	  10.0*log10(exp(2.0*URAYu[IRAY*MAX_NUM_FREQ+0])),
	  -10.0*log10(RRAY * RRAY * 1000.0 * 1000.0),
	  10.0*log10( FRAYu[IRAY*MAX_NUM_FREQ+0] * FRAYu[IRAY*MAX_NUM_FREQ+0]
	  *exp(2.0*URAYu[IRAY*MAX_NUM_FREQ+0])/(RRAY * RRAY * 1000.0 * 1000.0)) );*/
      
      /*Note: the bundle at caustic gets processed twice.*/

      if( fabs(ZRAYu[IRAY]-ZVRTu1) <= 0  ||
	  fabs(ZRAYu[IRAY]-ZVRTu2) <= 0 )  
	for(i=0;i<(*Env).Nfreq;i=i+1) PWR[i]=0.5*PWR[i];

      TOTPWR = 0.0;
      for(i=0;i<(*Env).Nfreq;i=i+1) TOTPWR = TOTPWR + PWR[i];
      if( TOTPWR > PWRMIN*
(*Env).Nfreq ){

	/*-------------------------
	  Estimate the travel time.
	  -------------------------*/

	TTRG = TRAYu[IRAY] + PSINu[IRAY]*ZREL;

	/*-------------------------
	  Compute the weighted sum.
	  ----------------
---------*/

	*UPRSUM = *UPRSUM + TOTPWR * NUPRu[IRAY];
	*LWRSUM = *LWRSUM + TOTPWR * NLWRu[IRAY];

	*SRCSUM = *SRCSUM + TOTPWR * TRD[IRAY].ANG;
	for(i=0;i<(*Env).Nfreq;i=i+1) PWRSUM[i] = PWRSUM[i] + PWR[i];
	*TIMSUM = *TIMSUM + TOTPWR * TTRG;
	for(i=0;i<(*Env).Nfreq;i=i+1) PHSSUM[i] = PHSSUM[i] + TOTPWR * ORAYu[IRAY];
	*PCSSUM = *PCSSUM + TOTPWR * PCOSu[IRAY];
	*PSNSUM = *PSNSUM + TOTPWR * PSINu[IRAY];
	/*Test Carrying source angle*/
	/*printf("Rang=%f acos=%f\n",180.0*TRD[IRAY].RANG/M_PI,180.0*acos(PCOSu[IRAY]/PTRG)/M_PI);*/
	/**RCVSUM = *RCVSUM + TOTPWR * TRD[IRAY].RANG;*/
	*RCVSUM = *RCVSUM + TOTPWR * acos(PCOSu[IRAY]/PTRG);
	  

	/*printf("IRAY=%d PWRSUM=%e TOTPWR=%e ang=%fR %fD RCVSUM=%e ",
	    IRAY,PWRSUM[0],TOTPWR,acos(PCOSu[IRAY]/PTRG),180.0*acos(PCOSu[IRAY]/PTRG)/M_PI,*RCVSUM);*/
	
	/*-----------------------------
	  Modify the phase at caustics.
	  -----------------------------*/


	NRFLo = NSRF + NBTM;
	if(NCRSo-NRFLo > 0) NCSTo = NCRSo-NRFLo;
	else NCSTo = 0;
	for(i=0;i<(*Env).Nfreq;i=i+1)
	  PHSSUM[i] =  PHSSUM[i] - PWR[i] * ((M_PI/2.0)*NCSTo);

	
	/*---------------------------------
	  Set the first eigenray flag real.
	  ---------------------------------*/

	if( (ZBND2-ZTRG)*(ZTRG-ZBND1) >= 0 ) *IMAFLG = 0;

      };
      /*printf("    dB(PWR[0]) = %f  dB(PWRSUM[0]) = %f  loss = %f\n",
	  10.0*log10(PWR[0]),10.0*log10(PWRSUM[0]),
	  20.0*log10(TRD[IRAY].FRAY[0]) + 8.686 * TRD[IRAY].URAY[0] - 20.0*log10(1500.0 * TRD[IRAY].TRAY));*/
    };
    /*printf("\n");*/
  };
}

</code>

and the second subprogram:


<code>
/*! \file    WEG.c
  \brief     WEG (WAF Eigenray Generator) 
  \par
  computes acoustic eigenrays in a two-dimensional environment 
  using Gaussian ray bundles.
  \par
  \author     Phred
  \author     Weinberg
  \date     6-9-2004
  \test 
  WEGtest will display output of function for testing
*/

#include <math.h>
#include <complex.h>
#include <stdio.h>


#include <pthread.h>
#include "thread.h"
#include "WAFmutex.h"


#include "WAFmathBase.h"
#include "SIMdefines.h"

#include "envstructdefs.h"
#include "WEGStrDefs.h"
#include "WEGFunDefs.h"

/*!\brief
  WEG (WAF Eigenray Generator) 
  \par
  computes acoustic eigenrays in a two-dimensional environment 
  using Gaussian ray bundl
es.
  \param     Env                a structer to hold enviromental data 
  \param     eigen_ray_data     a structer to hold returned eigen rays
  \param     WPP                Paralla passed info
  \param     NumThreads         Number of Threads (including the king)
  \param     TRD                Test Ray Data
  \param     TRSD               Test RAy Segment Data
  \param     debug              debug flag
  \note
  More info is needed in this discription.
  
  <HR>
  \test

  \par <tt><b>WEGtest</b></tt>

  Test code for the <tt><b>WEG()</b></tt> function.

  \par Command Line Arguments:

  <tt><b>WEGtest</b></tt> [<em>#treads</em>]

  <em>#treads</em>) number of threads, defaults to one if not spified.

  \par Input Files:

  <tt>SorRec.in</tt>\n
  located in (<em>TOP</em>)<tt>/TestJigs/Inputs/LIB/Acoustics/</tt>,\n
  Line 2) Source range  depth\n
  Line 3) numbers of targets range  depth\n
  Line 5 +) target range\n
  Line 7 +) target depth\n
  Line 8 +) number of freq\n
  Line 9 +) frequency\n
  Line 11 +) min angle for test ray fan\n
  Line 12 +) max angle for test ray fan\n
  Line 13 +) angle step size for test ray fan\n
  Line 15 +) Max number of surface bounces\n
  Line 16 +) Max number of bottom bounces\n
  Line 17 +) Max number of upper verticys\n
  Line 18 +) Max number of lower verticys

  <tt>SeaState.in</tt>\n
  located in (<em>TOP</em>)<tt>/TestJigs/Inputs/LIB/Acoustics/</tt>,\n
  file need to be documented.
  
  <tt>SSP.in</tt>\n
  located in (<em>TOP</em>)<tt>/TestJigs/Inputs/LIB/Acoustics/</tt>,\n
  file need to be documented.
  
  <tt>Bottom.in</tt>\n
  located in (<em>TOP</em>)<tt>/TestJigs/Inputs/LIB/Acoustics/</tt>,\n
  file need to be documented.
  
  \par Code:

  Main for test code is in <tt>WEGtest.c</tt> 
  <HR>

  WEG (WAF Eigenray Generator)
*/
void WEG( ENV_DEF *Env, EIGEN_RAY *eigen_ray_data, WEG_P_PASS *WPP, int NumThreads,
   	  TEST_RAY_DATA *TRD, TEST_RAY_SEG_DATA *TRSD, LOGICAL debug ){

  int i; 

  int IRb=0; 
  int IZTRG=0;

  /*test ray fan in RADS*/
  double ANGMINi, ANGMAXi, ANGDELi;

 /*max range in km*/
  double RNGMAXi; 

  int NANGv;

  double PSRC, ATNSRC[MAX_NUM_FREQ];

  double P2SRC, GrSRC, GzSRC;

  /* Max range */
  RNGMAXi=(*Env).Target_Range[(*Env).NtargetR-1];

  /* At CloseRange set min*/
  if(0.005 > RNGMAXi) RNGMAXi = 0.005;

  /*-----------------------------------------------
    Compute the source sound slowness and gradient.
    -----------------------------------------------*/

  SND_SLW2( 1, 0.0, &((*Env).Source_Depth), &P2SRC, &GrSRC, &GzSRC,
	    &IRb, Env );
  PSRC = sqrt(P2SRC);

  /*--------------------------------
    Generate test ray source angles.
    --------------------------------*/

  /*Fan of test angles*/
  ANGMINi = (*Env).Min_Ang;
  ANGMAXi = (*Env).Max_Ang;
  ANGDELi = (*Env).Del_Ang;

  SRC_ANG2( (*Env).Source_Depth, P2SRC, &NANGv, TRD,
	    ANGMINi, ANGMAXi, ANGDELi, &IRb, Env, debug);

  /*-------------------------------------------
    Compute the source attenuation coefficient.
    -------------------------------------------*/

  for(i=0;i<(*Env).Nfreq;i=i+1){
    ATNSRC[i] = 0.0;
    VLM_ATN3( (*Env).frequency_Hz[i], &(ATNSRC[i]), 0, Env );
  };


  /*-------------------------------
    Compute.
    -------------------------------*/

  eigen_ray_data[0].Nfreq = (*Env).Nfreq;
  eigen_ray_data[0].ERAY_NDX = 0; /* No rays yet!*/
  
  PRC_BRN2( RNGMAXi, &(eigen_ray_data), WPP, NumThreads, &IRb,
	    &IZTRG, ATNSRC, GzSRC, NANGv, TRD, TRSD, PSRC, Env, debug);

}


```

Now these subprograms come from separate computer files. Notice that each has global variables (variables that are defined outside of the program code). Also, notice that the subprogram's global declarations are different. They define global variables to a main subprogram, but they are slightly different. The include files on each subprogram are different. 


Now how can this be? I understand that each separate computer file with a subprogram, must define global variables, but at least all of the subprograms global variable definitions should be the same. But here they are different. Why is what I want to know.

Newport_j

---

### Post by lloyd_b on 2010-02-04
First off, this board uses BBCode, not HTML, so please wrap the "code" tags with brackets ("[" and "]") rather than angle brackets ("<" and ">") so that the code formats properly.  It's VERY hard to read that code without formatting (I had to copy it to my local machine, and run 'indent' on it).

Second, I recommend posting this under "Other Community Discussions/Development and Programming/Programming Talk" to get the best possible answer.

Third - there are NO global variables in that code.  A global variable is define outside of any function, and as such is available to any function.  Here's a snippet of code to illustrate this:```
#define <stdio.h>

int function1()
{
    int localvar1, localvar2;

    return 0;
}

int globalvar1;
int globalvar2;

int function2()
{
    int localvar1, localvar2;

    return 0;
}
```In this case, 'localvar1' and 'localvar2' are defined inside the braces for function1() and function2(), and as such they are local to that function, so the duplication of names means nothing.  'globalvar1' and 'globalvar2' are defined outside of the braces for any function, so they *are* global variables, so any duplication would lead to potential problems.

Note that variables defined as parameters to a function are also local to that function.

Lloyd B.

---

### Post by dwhitney67 on 2010-02-04
Agreed; no global variables are present.  Perhaps the OP is confused with the doxygen comments?

---

### Post by newport_j on 2010-02-05
Okay, I put some global variables in int_bnd2.c, so I am wondering since they were put outside the code of that subroutine, and that subroutine in a single computer file unto itself, are said variables global to the entire program which consists of over 50 separate computer files?
 
Also, it seems that the include files which are outside of the programs code differ in number on each subprogram. I have seen programs with all of the subprograms included in one computer file with only one group of include files and it is usually at the top of the program. That makes sense. What does not make sense is each subprogram having a separate group of incude files and each group is different.
 
Newport_j

---

### Post by dwhitney67 on 2010-02-05
You really should consult a beginner's guide to C programming.  The questions you ask are too basic in comparison to the level of code you posted.

I'm assuming you have not written C programs before and/or are new to Linux/Unix.

I recommend that you look into "The C Programming Guide" by Kernighan & Ritchie (K&R) , or at my favorite, "Programming in C" by Stephen Kochan.

------------------

Typically header file(s) declare functions (aka the API (Application Programming Interface)) for an application.

The function are implemented (ie. defined) in one or more C modules.  These modules may only be used to formulate a library, or it may include a module with a main() function that is used to build an application.

Try experimenting with smaller programs until you get a handle on things before dealing with the code you posted earlier.

---

### Post by lloyd_b on 2010-02-05
> **newport_j said:**
> Okay, I put some global variables in int_bnd2.c, so I am wondering since they were put outside the code of that subroutine, and that subroutine in a single computer file unto itself, are said variables global to the entire program which consists of over 50 separate computer files?
 
Also, it seems that the include files which are outside of the programs code differ in number on each subprogram. I have seen programs with all of the subprograms included in one computer file with only one group of include files and it is usually at the top of the program. That makes sense. What does not make sense is each subprogram having a separate group of incude files and each group is different.
 
Newport_j

A global variable (one that is defined outside of any function's braces) is truly global for that program - it is potentially accessible from any function (in any file).  However, in order for the compiler to be able to handle use of that variable within a given function, that variable must be declared in the file that contains the function using it.

Typically, this is done by having an "extern ..." declaration for that variable in a header file, which is included into any other files that require access to that variable.

It is quite normal for the various "#include<...>" to vary from one file to another.  It's good practice to only include those headers that are actually required.  So a file that contains functions printing to the screen will have "#include<stdio.h>", but a file containing strictly math functions will not.

One final note: You mention having added globals to one file.  This is quite possibly a mistake that you or someone else will have to deal with in the future.  It's very easy to look at a problem, and say "I'll just add a global to pass that data around".  But as the number of globals grows, and the number of files accessing them increases, it becomes more and more difficult to identify any bugs involving those variables.

Because of all the bugs that have resulted because of excessive use of globals, use of them is generally discouraged.

Global variables are the proper way to solve some problems.  But since you appear to be a novice at C programming,  I would strongly suggest you look for other solutions that don't use them.  Perhaps if you post the code involved, and explain why you think you need globals, someone here can point out another, cleaner, solution.

Lloyd B.

---

### Post by avidday on 2010-02-05
I am going to repeat my question I posted yesterday on another thread where you posted the same piece of code. This code appears to be the property of the United States Naval Undersea Warfare Center. Do they know you are posting unobfuscated pieces of their program code on open internet forums?

---

### Post by lloyd_b on 2010-02-05
> **avidday said:**
> I am going to repeat my question I posted yesterday on another thread where you posted the same piece of code. This code appears to be the property of the United States Naval Undersea Warfare Center. Do they know you are posting unobfuscated pieces of their program code on open internet forums?

Uhm - are they aware that you are going out of your way to tell everyone that the code involved is the property of the United States Naval Undersea Warfare Center?  Thanks to you, a Google search for the Center's name will now include these threads...

Lloyd B.

---

### Post by CptPicard on 2010-02-05
Posting sonar(?) code on UF PT for all the Chinese to see... priceless. :)

---

### Post by dwhitney67 on 2010-02-05
The Original Poster seems to be MIA at the present time.  If indeed his code is property of the USN, then he should take the time to read about ITAR, which I'm sure if he was in an official capacity with most any of the US gov't agencies, he would presumably already know about it.

[http://en.wikipedia.org/wiki/International_Traffic_in_Arms_Regulations](http://en.wikipedia.org/wiki/International_Traffic_in_Arms_Regulations)

---

### Post by CptPicard on 2010-02-05
I guess the black helicopters got to him.

I am not sure what worries me more ... that he was posting that here, or that he is apparently maintaining something that has things like "target" in the comments. Maybe both :)

And the code is also pretty messy for something that may have something to do with things that probably carry other things that go boom.

---

### Post by newport_j on 2010-02-05
What you say is true. Please understand that I did not choose this project; it chose me. I wrote just the algorithms that are used in this code. Someone else programmed it in c. The current lauguage de jour.  

I admit I am very shaky on c programming, but not the algorithms in that program. I designed and wrote them. The person who coded it in c is now gone from our organization and guess what they chose the algorithm designer to help improve and maintain the code. I at first asked them to get someone else, but they chose me. "Don't worry you will pick it up in no time. A programmer is a programmer and regardless of the language that he programs in. True?"

I have coded in other languages, BASIC, FORTRAN, Pascal and LISP. I know that in some of the languages just mentioned there is such a thing as a common statement for all universal declarations. By using that statement link to a common set of declarations one easily manages global variables. I am hoping that is the case here. Having different include files declarations on each subprogram violates everything that I know about good programming practice. Again, these are subprograms.

Now I am trying to time the subprogram:

int_bnd2.c

I created some some global variables that I added to int_bnd2.c at the top of the program. They are:

struct timeval t1_start, t1_end;
double time_dev_avg, time avg, time_total, time_sum; 
int repcount;

Then it occurs to me that to get the best measure of int_bnd2.c execution time that I should put the following subroutines in the subprograms that call int_bnd2, not at the top and bottom of int_bnd2.

gettimeofday(&t1_start,0)
gettimeofday(&t2_send,0)

go around the line(s) that calls int_bnd2.c Obviously, the top line goes right before the calling line and the bottom line goes right after. Like so:

gettimeofday(&t1_start,0);
int_bnd2;
gettimeofday(&t2_start,0);
time_pass[repcount] = (t1_end.tv_sec-t1_start.tv.sec)*1000000 + t1_end.tv.usec - t1_start.tv.usec;


Don't forget that this is in a subprogram that calls int_bnd2, not the int_bnd2 itself. There are three subprogram that call int_bnd2 and each one has a single line that calls int_bd2. So I must do this for each of the three calling subprograms. 

But, I cannot stop there once the call is over, then I must record the time in int_bnd2. I thus created the line and placed it as you see above. This must be done for all three calling subprograms for int_bnd2.

time_pass[repcount] = (t1_end.tv_sec-t1_start.tv.sec)*1000000 + t1_end.tv.usec - t1_start.tv.usec;

Now, time_pass is the amount of time the program was in int_bnd2 for one call from one of the three subprograms.  It is only a small slice of int_bnd2 usage time. There will be many slices; in a test run the subprogram was called over 700,000 times. Thus all slices must be summed up and that is done like so:

time_sum = time_sum + time_pass[repcount];

everytime the program execution is handed back to the calling subprograms or right after the time_pass line in each subprogram. Finally, just before the program ends I put this statement as the second to last executable in the main program like so

time_avg = time_sum/repcount;

and then I print out time_avg which will tell me how many microseconds were used in execution of int_bnd2, for the total program. 

I know that you will say that there is GNU debugger that can time all subprograms. It is not for me. I plan to introduce some CUDA code in int_bnd2.c The GNU debugger/timer cannot handle that. So I must create my own timer. It worked in testing of small programs.

I know that you will probably say that be careful in introducing to many global variables. If there is another way to do this and not introduce global variables please let me know.

Finally as you can see I am dealing with several subprograms that
each use some common variables. The way to deal with it is using global variables. I put in above is the unmodified version of the subprogram.  

That is why I want to know about c global variables.  I need to use them in calculating the total time a subprograms takes during a main programs execution. I can think of no other way. Please tell me if i am using the global variables correctly.

I have several books on c programming, some are even helpful. I see nowhere that it addresses the use of global variables in many subprograms that each are in a separate computer file.

It seems a common statement is called for here. Is there one in c that I can use?

If this program was in one computer files with all subprogram included then I would put one global declaration at the top of the program. But that is not the case here. Each subprogram is in a separate computer file. Now what do I do?

Newport_j    
 






.

---

### Post by dwhitney67 on 2010-02-05
> **newport_j said:**
> What you say is true. Please understand that I did not choose this project; it chose me.
Is the code ITAR restricted?  It does not matter who originally wrote the code, or whether it is you who maintains it now.  What matters is who _owns_ it.  Posting proprietary code could cost you your job; if you are found guilty of posting ITAR restricted material, you could be fined and/or imprisoned by the US gov't.

If you have generic questions, feel free to post them here.  Bear in mind that UF is accessed and read by foreign nationals, and posts are searchable via the internet.

---

### Post by dwhitney67 on 2010-02-05
In C, individual modules and functions are not referred to as subprograms.  Maybe that's a fortran thing?

Avoid using global variables.  Most often they are not needed.  If you must have a global, define it within a .c file, not the .h file.  Provide access functions to acquire/set this global value.

For example...

Global.h:
```

#ifndef GLOBAL_H
#define GLOBAL_H

int  getValue();
void setValue(int val);

#endif

```

Global.c:
```

#include "Global.h"

static int value = 0;    // declaring value as static ensures 
                         // that no other module can access this
                         // variable, albeit it is global to this
                         // module.

int getValue()
{
   return value;
}

void setValue(int val)
{
   value = val;
}

```

Main.c:
```

#include "Global.h"
#include "stdio.h"

extern int value;  // attempt to 'capture' external variable

int main()
{
   setValue(5);
   printf("value = %d\n", getValue());

   // sorry, cannot do...
   //value = 5;

   return 0;
}

```

---

### Post by newport_j on 2010-02-05
FYI. 

Of course, people who manage me know I am posting this code. It has even been published!!! Not by me, though.

I only showed a small section of it (less than 1%). There is a lot more to this that what I posted here - a lot more.

This subprogram consists of algorithms that can be found in any marine acoustics book. I have several. 

If am wrong in this then you can contact @ sanguentin.org.  But do not bother if you are not a lawyer.

newport_J

---

### Post by lloyd_b on 2010-02-05
Ah - the COMMON block.  I do remember those.  I've spent many a sleepless night trying to figure out which of the many programs accessing the common was responsible for setting a particular value (back when my paying job was working with a BASIC variant).  

That's one of the reasons I'm so leery of global variables now.  If they are used in a disciplined and intelligent manner, they're fine.  But if used carelessly they can lead to *very* large headaches. :)

I would recommend following dwhitney67's suggestions on how to handle the globals - this is what I was meant when I mentioned "disciplined and intelligent manner" above.

Lloyd B.

---

