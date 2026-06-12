---
title: "Live recognition problem on HTK"
date: 2009-12-10
forum: Programming Talk
---

### Post by zla on 2009-12-10
Hi everybody , i've started to leaning about HTK , now i try to use live recognition by using following script --->

in liverecog.sh ---> HVite -H am/tiehmm2m_3/newMacros \[INDENT][INDENT][INDENT]      -C liverecog.config \
      -w lm/dgs.wdnet \
      -p 0.0 -s 5.0 \
      config/dgs.dict \
      config/tie.list
[/INDENT][/INDENT][/INDENT]in liverecog.config ----> # HTK Configuration Parameters for live recogniton
[INDENT][INDENT][INDENT][INDENT]TARGETKIND = MFCC_D_A_E
TARGETRATE=100000.0 # frame interval is 10 [msec]
SAVECOMPRESSED=F    # set T, if you like to save disk storage
SAVEWITHCRC=F       
WINDOWSIZE=250000.0 # window length is 25 [msec]
USEHAMMING=T        # use HAMMING window
PREEMCOEF=0.97      # apply highpass filtering
NUMCHANS=24         # # of filterbank for MFCC is 24
NUMCEPS=12          # # of parameters for MFCC presentation
ZMEANSOURCE=T

# Rather local Parameters
ESCALE=1.0
TRACE=0
RAWENERGY=F

#WAV capture configuration
SOURCERATE=625
SOURCEKIND=HAUDIO
SOURCEFORMAT=HTK
ENORMALISE=F
USESILDET=T
MEASURESIL=F
OUTSILWARN=T
[/INDENT][/INDENT][/INDENT][/INDENT]-------------------------------------------------------------------
then i got this warning message 
--->  WARNING [-6006]  ReadAudio: Failed to read all 0 samples from OSS audio in HVite
------------------------------------------------------------------
How can i solve this problem

---

### Post by thirumal on 2011-06-03
> **zla said:**
> Hi everybody , i've started to leaning about HTK , now i try to use live recognition by using following script --->
 
in liverecog.sh ---> HVite -H am/tiehmm2m_3/newMacros \
[INDENT][INDENT][INDENT]-C liverecog.config \
-w lm/dgs.wdnet \
-p 0.0 -s 5.0 \
config/dgs.dict \
config/tie.list
[/INDENT][/INDENT][/INDENT]in liverecog.config ----> # HTK Configuration Parameters for live recogniton
[INDENT][INDENT][INDENT][INDENT]TARGETKIND = MFCC_D_A_E
TARGETRATE=100000.0 # frame interval is 10 [msec]
SAVECOMPRESSED=F # set T, if you like to save disk storage
SAVEWITHCRC=F 
WINDOWSIZE=250000.0 # window length is 25 [msec]
USEHAMMING=T # use HAMMING window
PREEMCOEF=0.97 # apply highpass filtering
NUMCHANS=24 # # of filterbank for MFCC is 24
NUMCEPS=12 # # of parameters for MFCC presentation
ZMEANSOURCE=T
 
# Rather local Parameters
ESCALE=1.0
TRACE=0
RAWENERGY=F
 
#WAV capture configuration
SOURCERATE=625
SOURCEKIND=HAUDIO
SOURCEFORMAT=HTK
ENORMALISE=F
USESILDET=T
MEASURESIL=F
OUTSILWARN=T
[/INDENT][/INDENT][/INDENT][/INDENT]-------------------------------------------------------------------
then i got this warning message 
---> WARNING [-6006] ReadAudio: Failed to read all 0 samples from OSS audio in HVite
------------------------------------------------------------------
How can i solve this problem
 hi 
Me too started to learn the htk using the online resources now i also stuck up in the same step, did you find the solution for this..

---

### Post by thirumal on 2011-06-03
> **zla said:**
> Hi everybody , i've started to leaning about HTK , now i try to use live recognition by using following script --->

in liverecog.sh ---> HVite -H am/tiehmm2m_3/newMacros \[INDENT][INDENT][INDENT]      -C liverecog.config \
      -w lm/dgs.wdnet \
      -p 0.0 -s 5.0 \
      config/dgs.dict \
      config/tie.list
[/INDENT][/INDENT][/INDENT]in liverecog.config ----> # HTK Configuration Parameters for live recogniton
[INDENT][INDENT][INDENT][INDENT]TARGETKIND = MFCC_D_A_E
TARGETRATE=100000.0 # frame interval is 10 [msec]
SAVECOMPRESSED=F    # set T, if you like to save disk storage
SAVEWITHCRC=F       
WINDOWSIZE=250000.0 # window length is 25 [msec]
USEHAMMING=T        # use HAMMING window
PREEMCOEF=0.97      # apply highpass filtering
NUMCHANS=24         # # of filterbank for MFCC is 24
NUMCEPS=12          # # of parameters for MFCC presentation
ZMEANSOURCE=T

# Rather local Parameters
ESCALE=1.0
TRACE=0
RAWENERGY=F

#WAV capture configuration
SOURCERATE=625
SOURCEKIND=HAUDIO
SOURCEFORMAT=HTK
ENORMALISE=F
USESILDET=T
MEASURESIL=F
OUTSILWARN=T
[/INDENT][/INDENT][/INDENT][/INDENT]-------------------------------------------------------------------
then i got this warning message 
--->  WARNING [-6006]  ReadAudio: Failed to read all 0 samples from OSS audio in HVite
------------------------------------------------------------------
How can i solve this problem
hI
Me too started to learn the htk using the online resources now i also stuck up in the same step, did you find the solution for this..

---

### Post by Zugzwang on 2011-06-03
Here's a guess: The OSS sound system is not available for you. If running a recent version of ubuntu, try to start your program using the "padsp" tool, i.e., instead of running "./yourexecutable", run "padsp ./yourexecutable" and see if it works. You might need to install "padsp" from the package pulseaudio-utils first, though.

---

### Post by dabraude on 2011-10-14
Please see this thread:

[http://ubuntuforums.org/showthread.php?p=11341143#post11341143]("http://ubuntuforums.org/showthread.php?p=11341143#post11341143")

You should be able to figure out how to modify your code for it

---

