---
title: "c compile error"
date: 2010-02-03
forum: Programming Talk
---

### Post by newport_j on 2010-02-03
I got an error when I compiled a c program that said essentially:
 
 
error: subscripted value is neither array nor pointer
 
 
it was referring to a specific line of code in the program. What does this mean and how can I correct it?
 
Newport_j

---

### Post by QuimNuss on 2010-02-03
Could you provide more information? What compiler are you using? could you show at least the entire function so we can see what you've declared so far?

---

### Post by cariboo on 2010-02-03
You might get better help here.

---

### Post by lloyd_b on 2010-02-03
> **newport_j said:**
> I got an error when I compiled a c program that said essentially:
 
 
error: subscripted value is neither array nor pointer
 
 
it was referring to a specific line of code in the program. What does this mean and how can I correct it?
 
Newport_j

It *would* be nice if you've showed the line of code involved.  That said, what you've probably done is something like the following:```
#include <stdio.h>

int main(int argc, char ** argv)
{
        int fred;

        printf("This is fred sub 2:%d\n", fred[2]);

        return 0;
}
```In this case, what I did was declare "fred" to be of type "int", but I'm trying to access it like it was an array ('fred[2]').  

Pointers are a special case - tricks like that *are* perfectly acceptable (though maybe a bit confusing in some cases) when working with pointers.  Other than pointers, if you're accessing it like any array, then it needs to be declared as an array.

Lloyd B.

---

### Post by newport_j on 2010-02-04
Okay, the posted code is now shown.
 
<code>
 
/*! \file int_bnd2.c
\brief integrates Gaussian ray bundles.
\par
\author Phred
\author Weinberg
*/
 
/* WEG (WAF Eigenray Generator) 
Translated to "c" and modifided by Andrew "Phred" Fredricks
form work done by Chic Weinberg.
* Function INT_BND2 integrates Gaussian ray bundles.
Variables
* ZTRG = target depth (km)
* APRMIN = minimum ray bundle aperture (km)
* NANGv = number of source angles
* ANGv = source angle vector (rad)
* PWRv = source pressure squared vector (uPa^2)
* IRAYu1 = leading ray index
* IRAYu2 = trailing ray index
* ZVRTu1 = leading virtual ray depth (km)
* ZVRTu2 = trailing virtual ray depth (km)
* RRAY = ray range (km)
* ZRAYu = unfolded ray depth (km)
* TRAYu = unfolded ray time (s)
* PCOSu = unfolded ray horizontal slowness (s/km)
* PSINu = unfolded ray vertical slowness (s/km)
* NUPRu = number of unfolded upper vertexes
* NLWRu = number of unfolded lower vertexes
* NCRSo = number of ray crossings
* URAYu = unfolded ray attenuation (nepers)
* FRAYu = unfolded ray factor (pres ratio)
* ORAYu = unfolded ray phase (rad)
* NSRF = number of surface reflections
* NBTM = number of bottom reflections
* UPRSUM = weighted upper vertex sum
* LWRSUM = weighted lower vertex sum
* SRCSUM = weighted source angle sum (rad)
* PWRSUM = pressure squared sum (uPa^2)
* TIMSUM = weighted time sum (s)
* PHSSUM = weighted phase sum (rad)
* PCSSUM = weighted horizontal slowness sum (s/km)
* PSNSUM = weighted vertical slowness sum (s/km)
* IMAFLG = eigenray flag {0,1} for {real,imag} eigenrays
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
#include "sys/time.h"
int repcounter, repcount;
struct timeval t1_start,t1_end;
double time_dev_avg, time_avg, time_total, time_sum, time_pass;
int repcount;
/*!\brief
integrates Gaussian ray bundles.
\param ZTRG target depth (km)
\param PTRG
\param SCST
\param APER
\param TRD Test Ray Data
\param IRAYu1 leading ray index
\param IRAYu2 trailing ray index
\param ZVRTu1 leading virtual ray depth (km)
\param ZVRTu2 trailing virtual ray depth (km)
\param RRAY ray range (km)
\param ZRAYu unfolded ray depth (km)
\param TRAYu unfolded ray time (s)
\param PCOSu unfolded ray horizontal slowness (s/km)
\param PSINu unfolded ray vertical slowness (s/km)
\param NSRF number of surface reflections
\param NBTM number of bottom reflections
\param NUPRu number of unfolded upper vertexes
\param NLWRu number of unfolded lower vertexesstruct timeval t1_start,t1_end,t2_start,t2_end;
double time_dev_avg, time_avg, time_total, time_sum;
\param NCRSo number of ray crossings
\param URAYu unfolded ray attenuation (nepers)
\param FRAYu unfolded ray factor (pres ratio)
\param ORAYu unfolded ray phase (rad)
\param UPRSUM weighted upper vertex sum
\param LWRSUM weighted lower vertex sum
\param SRCSUM weighted source angle sum (rad)
\param RCVSUM weighted recive angle sum (rad)
\param PWRSUM pressure squared sum (uPa^2)
\param TIMSUM weighted time sum (s)
\param PHSSUM weighted phase sum (rad)
\param PCSSUM weighted horizontal slowness sum (s/km)int_bnd2_mod.c
\param PSNSUM weighted vertical slowness sum (s/km)
\param IMAFLG eigenray flag {0,1} for {real,imag} eigenrays
\param Env
*/
void INT_BND2( double ZTRG, double PTRG,
LOGICAL SCST, double APER, TEST_RAY_DATA *TRD,
int IRAYu1, int IRAYu2, double ZVRTu1, 
double ZVRTu2, double RRAY, double *ZRAYu, double *TRAYu, 
double *PCOSu, double *PSINu, int NSRF, int NBTM, 
int *NUPRu, int *NLWRu, int NCRSo, double *URAYu, 
double *FRAYu, double *ORAYu, double *UPRSUM, double *LWRSUM,
double *SRCSUM, double *RCVSUM, double *PWRSUM, double *TIMSUM, double *PHSSUM,
double *PCSSUM, double *PSNSUM, int *IMAFLG,
ENV_DEF *Env){
int i, IRAY, NRFLo, NCSTo;
double ZBND1=0.0, ZBND2=0.0, ZDEL, ZAPR, SDEV, ZREL, ARG; 
double PWR[MAX_NUM_FREQ], TTRG, ARGMAX;
double APRMIN=666.0, APRMINt, TOTPWR;
gettimeofday(&t1_start,0);
/*
EIGTOLi = eigenray tolerance
APRMIN minimum ray bundle aperture (km)
*/
/*-----------------------------------------------------------------
Set the maximum ray bundle argument for ARG = 0.5*(ZREL/SDEV)**2
so that
exp(-ARGMAX/2) = EIGTOLi/10gettimeofday(&t1_start,0);
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
if( fabs(ZRAYu[IRAY]-ZVRTu1) <= 0 ||
fabs(ZRAYu[IRAY]-ZVRTu2) <= 0 ) 
for(i=0;i<(*Env).Nfreq;i=i+1) PWR[i]=0.5*PWR[i];
TOTPWR = 0.0;
for(i=0;i<(*Env).Nfreq;i=i+1) TOTPWR = TOTPWR + PWR[i];
if( TOTPWR > PWRMIN*(*Env).Nfreq ){
/*-------------------------
Estimate the travel time.
-------------------------*/
TTRG = TRAYu[IRAY] + PSINu[IRAY]*ZREL;
/*-------------------------
Compute the weighted sum.int_bnd2_mod.c
-------------------------*/
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
 
/*-----------------------------int_bnd2_mod.c
Modify the phase at caustics.
-----------------------------*/
NRFLo = NSRF + NBTM;
if(NCRSo-NRFLo > 0) NCSTo = NCRSo-NRFLo;
else NCSTo = 0;
for(i=0;i<(*Env).Nfreq;i=i+1)
PHSSUM[i] = PHSSUM[i] - PWR[i] * ((M_PI/2.0)*NCSTo);
 
/*---------------------------------
Set the first eigenray flag real.
---------------------------------*/
if( (ZBND2-ZTRG)*(ZTRG-ZBND1) >= 0 ) *IMAFLG = 0;
};
/*printf(" dB(PWR[0]) = %f dB(PWRSUM[0]) = %f loss = %f\n",
10.0*log10(PWR[0]),10.0*log10(PWRSUM[0]),
20.0*log10(TRD[IRAY].FRAY[0]) + 8.686 * TRD[IRAY].URAY[0] - 20.0*log10(1500.0 * TRD[IRAY].TRAY));*/
};
/*printf("\n");*/
};
gettimeofday(&t1_start,0);
time_pass[repcounter] = (t1_end.tv_sec-t1_start.tv_sec)*1000000 + t1_end.tv_usec - t1_start.tv_usec;
}
 
 
</code>
 
The line of code that is offending the compiler is:
 
 
time_pass[repcounter] = (t1_end.tv_sec-t1_start.tv_sec)*1000000 + t1_end.tv_usec - t1_start.tv_usec;
 
 
 
This give me the following error :
 
 
error: subscripted value is neither array nor pointer. 
 
 
I have shown the line of code that causes this error.
 
 
Any help is appreciated.
 
Newport_j

---

### Post by Xyro on 2010-02-04
```
double time_dev_avg, time_avg, time_total, time_sum, **time_pass**;
```

time_pass is a double, not a double* or a double[].

replace the line:

```
double time_dev_avg, time_avg, time_total, time_sum, time_pass;
```

with

```
double time_dev_avg, time_avg, time_total, time_sum, time_pass[MAX_EXPECTED_LENGTH];
```

where MAX_EXPECTED_LENGTH is, well, the maximum expected length of that vector.

When you declare "time_pass" as a double, the compiler allocates 8 bytes of memory for a double precision number. When you reference it via "time_pass[index]", what you are accessing is the value stored at the memory location given by the address contained in "time_pass" + index*8bytes. Since "time_pass" is a double precision number (as you've defined it) and NOT an address, the compiler starts crying. If you were to declare "time_pass" as a pointer or an array, it would no longer hold a double value, but the address to a double value (what you want).

Edit: Also, you may want to note that your index "repcounter" is not initialized or modified anywhere in your code, so you will have a bug when it does compile.

---

### Post by avidday on 2010-02-04
This is incredible.

James, does anybody from the Navy know you are posting their torpedo simulation source code online in a public forum?

---

### Post by dwhitney67 on 2010-02-04
> **avidday said:**
> This is incredible.

James, does anybody from the Navy know you are posting their torpedo simulation source code online in a public forum?

Whatever the code is, it meet my criteria for being poorly written.  Anyone passing more than 5 or 6 parameters to a function needs to go back to boot camp.

---

