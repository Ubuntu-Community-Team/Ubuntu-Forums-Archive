---
title: "default arguments in C++"
date: 2006-07-24
forum: Programming Talk
---

### Post by nebc on 2006-07-24
I'm having problems with default arguments in C++.  The CamState files
compile just fine but I get an error when I try and compile fvcart.cpp.  Here's the error:

../../objdir/FvCartPanel.o(.text+0x3a3c): In function `FvCartPanel::UpdateImage()':
pathcode/fvcart/FvCartPanel.cpp:292: undefined reference to `CamState::still()'
collect2: ld returned 1 exit status

code in FvCartPanel
-------------------------------------------
if(but2->isChecked())
{
  if(csp->still()){
    // assuming that we've already moved here
    posp.set(hs/2, ws/2);
    //....
    
-------------------------------------------
csp is a CamState object

 void moveToAbsPanTilt(int pan, int tilt);
 bool still(double time = 0.001);
 
 void set_framerate(int framerate);
-------------------------------------------
Here is the CamState.cpp

bool CamState::still(double time) {
  /* has the camera stopped moving?  - using a hack for
     now, absolute amount of time since last movment */
  //if (motortimer.elapsed() > 500) // used to be 800

  // 500 wasn't working at all.  Kept on saying that camera had moved
  // to recently this value seems to work well -BC
  if (motortimer.elapsed() > time)
    return true;
  else
    return false;
}
-------------------------------------------

Anyone know what I'm doing wrong?

---

### Post by fluffington on 2006-07-24
Edit: never mind.

---

### Post by gborzi on 2006-07-24
The problem is that CamState::still is defined in CamState.cpp with a double argument, i.e.> bool CamState::still(double time)  but it is called without arguments, i.e.> csp->still()
Perhaps you forgot to give a default value in the CamState::still declaration ? something like
> class CamState {
public:
...
bool still( double time = 0 );
...
};

---

### Post by joft on 2006-07-24
Hi,

> **nebc said:**
> 
../../objdir/FvCartPanel.o(.text+0x3a3c): In function `FvCartPanel::UpdateImage()':
pathcode/fvcart/FvCartPanel.cpp:292: undefined reference to `CamState::still()'
collect2: ld returned 1 exit status


I'd say that you got a linking error here. The linker (ld) isn't able to find the function "CamState::still()".

So you have to add a commandline argument "-l<libname>" which tells the compiler to include the library named <libname> which implements this function.

---

### Post by nebc on 2006-07-24
Thanks for your replies!

It turns out that my code was fine but that I needed to clean my libraries and make them again.

Neb

---

