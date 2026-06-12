---
title: "Help compiling a Fortran program"
date: 2011-05-22
forum: Programming Talk
---

### Post by sisyphus1978 on 2011-05-22
I have never done any real programming, but I have a [book]("http://www.amazon.com/Treasures-Inside-Bell-Hidden-Chance/dp/9812381414") which contains a footnote to a fortran program, which I would very much like to run and have a look at. This is not homework or any such thing. Any pointers to get it running would be brilliant. I have tried g77, f77 and gfortran. 

Here is the source:

```
c**************************************************************************
c
       program branch-sw-pi
c
c  Computes dots located on the attractor of pseudo-wire defined
c  by NF affine functions in three dimensions following a single
c  branch of an NF-ary tree given by the binary digits of pi
c  The mappings have end points:
c    (xi(n),yi(n),zi(n)),
c    (xr(n),yr(n),zr(n))
c     The final parameters of the mappings are:
c     (wa(n) 0 0)
c      (we(n))
c      (wc(n) wd(n) wh(n)) + (wf(n))
c       (wk(n) wl(n) wm(n))
c        (wg(n))
c      Where the lower right matrix is:
c       (rl(n)*cos(thl(n))
c       (rl(n)*sin(thl(n))
c     -r2(n)*sin(th2(n)))
c      r2(n)*cos(th2(n)))
c+++++++++++++++++++++++++++++++++++++++
c  NOTES: currently the maximum number of functions is 8
c    angles are in degrees
c    niter is the total number of iterations
c    points stored are those between bstore and estore
c********************************************************
      implicit double precision (a-h, o-z)
      parameter (Pi = 3.14159265358979324d0, NF = 8)
c
      dimension xl(NF), yl(NF), zl(NF), xr(NF), yr(NF), zr(NF)
      dimension wa(NF), we(NF), wc(NF), wd(NF), wh(NF), wf(NF), wk(NF)
      dimension wl(NF), wm(NF), wg(NF), r1(NF), r2(NF), th1(NF), th2(NF)
      integer bstore, estore
c
      character*70,file1
c
c******************************************
c Open output files:
c*****************************************
      print *, '? summary file'
      read *, file1
      open(10, file = file1, status = 'unknown')
c
      print *, '? dots file'
      read *, file1
      open(11, file = file1, status = 'unknown')
c
c************************************************
c   Open file containing the binary digits if pi
c************************************************
      open(12, file = 'filebipi', status = 'old')
c
C+++++++++++++++++++++++++++++++++++++++++++
c
c NOTE: This file may be replaced by pseudo-random numbers if desired
c+++++++++++++++++++++++++++++++++++++++++++
c
c********************************************
c Enter storage information
c********************************************
      print *, '? Number of iterations'
      read *, niter
      write(1O,*) '! Number of iterations ', niter
c
      print *, '? Begining of storage'
      read *, bstore
      write(1O,*) '! Begining of storage ', bstore
c
      print *, '? End of storage'
      read *, estore
      write(1O,*) '! End of storage ', estore
c
c*******************************************
c Enter initial geometric configuration
c*******************************************
      print *, '? geometry file'
      read *, file1
      open(14, file = file1, status = 'old')
c+++++++++++++++++
c Read end-points
c+++++++++++++++++
c
      read (14,*) nfun
      do n = 1, nfun
      read (14,*) xl(n), xr(n)
      read (14,*) yl(n), yr(n)
      read (14,*) zl(n), zr(n)
      end do
c
      write(10,*) ' '
      write(10,*) ' ! Initial Configuration: nfun, X,Y,Z'
      write(10,*) nfun
      do n = 1, nfun
      write(10,*) xl(n), xr(n)
      write(10,*) yl(n), yr(n)
      write(10,*) zl(n), zr(n)
      end do
c************************************************
c  Enter scalings and rotations
c***********************************************
      print *, '? scalings and rotations'
      print *, '? r1 '
      read *, (rl(n), n = 1, nfun)
      print *, '? th1'
      read *, (th1(n), n = 1, nfun)
      print *, '? r2'
      read *, (r2(n), n &#8212; 1, nfun)
      print *, '? th2'
      read *, (th2(n), n = 1, nfun)
c
      write(10,*) ' '
      write(10,*) ' ! Scalings and rotations by mapping: (rl, th1 , r2, th2)'
      do n = 1, nfun
      write(10,*) rl(n), th1(n), r2(n), th2(n)
      end do
c
c++++++++++++++++++++++++
c
c   Transform angles into radians
c++++++++++++++++++++++++
c
      do n = 1, nfun
      th1(n) = Pi*th1(n)/180.0D0
      th2(n) = Pi*th2(n)/180.0D0
      end do
c
c**************************************
cDefine free affine mapping parameters
c**************************************
      do n = 1, nfun
      wd(n) = rl(n)*dcos(th1(n))
      wh(n) = -r2(n)*dsin(th2(n))
      wl(n) = rl(n)*dsin(th1(n))
      wm(n) = r2(n)*dcos(th2(n))
      end do
c
c
c************************************
cFind other affine mapping parameters
c+++++++++++++++++++++++++++++++++++
c
c*******************************************
cfirst determine end points for contractions
c********************************************
      xend1 = xl(1)
      yend1 = yl(1)
      zend1 = zl(1)
      xend2 = xr(1)
      yend2 = yr(1)
      zend2 = zr(1)
c
      do n = 2, nfun
      if(xl(n).lt.xendl) then
      xend1 = xl(n)
      yend1 = yl(n)
      zend1 = zl(n)
      end if
      if(xr(n).gt.xend2) then
      xend2 = xr(n)
      yend2 &#8212; yr(n)
      zend2 = zr(n)
      end if
      end do
c
c++++++++++++++++++++++++
c
c now find parameters
c++++++++++++++++++++++++
c
      xrange = xend2 &#8212; xend1
      yrange = yend2 &#8212; yend1
      zrange = zend2 &#8212; zend1
c
      do n = 1, nfun
      wa(n) = (xr(n) &#8212; xl(n))/xrange
      wc(n) = (yr(n) &#8212; yl(n) &#8212; wd(n)*yrange &#8212; wh(n)*zrange)/xrange
      wk(n) = (zr(n) &#8212; zl(n) &#8212; wl(n)*yrange &#8212; wm(n)*zrange)/xrange
      we(n) = xl(n) &#8212; xend1*wa(n)
      wf(n) = yl(n) &#8212; wd(n)*yend1 &#8212; wc(n)*xend1 &#8212; wh(n)*zend1
      wg(n) = zl(n) &#8212; wl(n)*yend1 &#8212; wk(n)*xend1 &#8212; wm(n)*zend1
      end do
c
c****************************************
c Do iterations and store when requested
c****************************************
c++++++++++++++++++++++++++++++++++++++++++
c points may be found sequentally or based on the same starting point
c++++++++++++++++++++++++++++++++++++++++++
c
      print *, '? Enter 1 if sequential patterns, 0 otherwise'
      read *, iseq
      write(10,*) '! Sequential patterns indicator ', iseq
c
      print *, '? Enter number of points per frame'
      read *, nseq
      write(10,*) '! Points per frame ', nseq
c
c++++++++++++++++++++++++++++++
c
c  Define the starting point
C++++++++++++++++++++++++++++++
C
      xx = xr(1)
      yy = yr(1)
      zz = zr(1)
c
      nstore = estore &#8212; bstore + 1
      write (11,*) nstore
c
      do i = 1, niter
c
      if(iseq.eq.0) then
      if(mod(i,nseq).eq.0) then
      xx = xr(1)      
      yy = yr(1)
      zz = zr(1)
      end if
      end if
c
      read(12,*) ii
      n1 = ii + 1
c
      xnew = wa(n1)*xx + we(n1)
      ynew = wc(n1)*xx + wd(n1)*yy + wh(n1)*zz + wf(n1)
      znew = wk(n1)*xx + wl(n1)*yy + wm(n1)*zz + wg(n1)
c
      xx = xnew
      yy = ynew
      zz &#8212; znew
c
c+++++++++++++++++++++++++++++++++
c points stored in unit 11 may be plotted
c+++++++++++++++++++++++++++++++++
c
      if((i. ge. bstore).and.(i. le. estore)) then
      write(11,*) n1, real(yy), real(zz)
      end if
c
      end do
c
      stop
      endstop
      end
```This should be pretty much copy and paste from the source footnote, but some of the formatting etc might be off. Any fortran guru's want to advise? :D

---

### Post by sisyphus1978 on 2011-05-23
Okay. So my guess is that it's fortran77 (the c gives that away), and thus the formatting seems to be one of the main stumbling blocks. I stripped out the comments and tried putting the commands in column 7 (or eight) , but to no great avail.

It has stumped my efforts though.

---

### Post by gmargo on 2011-05-23
I got this program to compile with **gfortran**.  The original source posted includes a bunch of non-ascii characters (mostly long-dash instead of minus or equals), one too-long line, one missing declaration, one bad statement, and a bad program name.

The following compiles, but of course is untested:
```

c**************************************************************************
c
       program branch_sw_pi
c
c  Computes dots located on the attractor of pseudo-wire defined
c  by NF affine functions in three dimensions following a single
c  branch of an NF-ary tree given by the binary digits of pi
c  The mappings have end points:
c    (xi(n),yi(n),zi(n)),
c    (xr(n),yr(n),zr(n))
c     The final parameters of the mappings are:
c     (wa(n) 0 0)
c      (we(n))
c      (wc(n) wd(n) wh(n)) + (wf(n))
c       (wk(n) wl(n) wm(n))
c        (wg(n))
c      Where the lower right matrix is:
c       (rl(n)*cos(thl(n))
c       (rl(n)*sin(thl(n))
c     -r2(n)*sin(th2(n)))
c      r2(n)*cos(th2(n)))
c+++++++++++++++++++++++++++++++++++++++
c  NOTES: currently the maximum number of functions is 8
c    angles are in degrees
c    niter is the total number of iterations
c    points stored are those between bstore and estore
c********************************************************
      implicit double precision (a-h, o-z)
      parameter (Pi = 3.14159265358979324d0, NF = 8)
c
      dimension xl(NF), yl(NF), zl(NF), xr(NF), yr(NF), zr(NF)
      dimension wa(NF), we(NF), wc(NF), wd(NF), wh(NF), wf(NF), wk(NF)
      dimension wl(NF), wm(NF), wg(NF), r1(NF), r2(NF), th1(NF), th2(NF)
      dimension rl(NF)
      integer bstore, estore
c
      character*70,file1
c
c******************************************
c Open output files:
c*****************************************
      print *, '? summary file'
      read *, file1
      open(10, file = file1, status = 'unknown')
c
      print *, '? dots file'
      read *, file1
      open(11, file = file1, status = 'unknown')
c
c************************************************
c   Open file containing the binary digits if pi
c************************************************
      open(12, file = 'filebipi', status = 'old')
c
C+++++++++++++++++++++++++++++++++++++++++++
c
c NOTE: This file may be replaced by pseudo-random numbers if desired
c+++++++++++++++++++++++++++++++++++++++++++
c
c********************************************
c Enter storage information
c********************************************
      print *, '? Number of iterations'
      read *, niter
      write(10,*) '! Number of iterations ', niter
c
      print *, '? Begining of storage'
      read *, bstore
      write(10,*) '! Begining of storage ', bstore
c
      print *, '? End of storage'
      read *, estore
      write(10,*) '! End of storage ', estore
c
c*******************************************
c Enter initial geometric configuration
c*******************************************
      print *, '? geometry file'
      read *, file1
      open(14, file = file1, status = 'old')
c+++++++++++++++++
c Read end-points
c+++++++++++++++++
c
      read (14,*) nfun
      do n = 1, nfun
      read (14,*) xl(n), xr(n)
      read (14,*) yl(n), yr(n)
      read (14,*) zl(n), zr(n)
      end do
c
      write(10,*) ' '
      write(10,*) ' ! Initial Configuration: nfun, X,Y,Z'
      write(10,*) nfun
      do n = 1, nfun
      write(10,*) xl(n), xr(n)
      write(10,*) yl(n), yr(n)
      write(10,*) zl(n), zr(n)
      end do
c************************************************
c  Enter scalings and rotations
c***********************************************
      print *, '? scalings and rotations'
      print *, '? r1 '
      read *, (rl(n), n = 1, nfun)
      print *, '? th1'
      read *, (th1(n), n = 1, nfun)
      print *, '? r2'
      read *, (r2(n), n = 1, nfun)
      print *, '? th2'
      read *, (th2(n), n = 1, nfun)
c
      write(10,*) ' '
      write(10,*) ' ! Scalings and rotations by mapping: (rl, th1 , r2,
     + th2)'
      do n = 1, nfun
      write(10,*) rl(n), th1(n), r2(n), th2(n)
      end do
c
c++++++++++++++++++++++++
c
c   Transform angles into radians
c++++++++++++++++++++++++
c
      do n = 1, nfun
      th1(n) = Pi*th1(n)/180.0D0
      th2(n) = Pi*th2(n)/180.0D0
      end do
c
c**************************************
cDefine free affine mapping parameters
c**************************************
      do n = 1, nfun
      wd(n) = rl(n)*dcos(th1(n))
      wh(n) = -r2(n)*dsin(th2(n))
      wl(n) = rl(n)*dsin(th1(n))
      wm(n) = r2(n)*dcos(th2(n))
      end do
c
c
c************************************
cFind other affine mapping parameters
c+++++++++++++++++++++++++++++++++++
c
c*******************************************
cfirst determine end points for contractions
c********************************************
      xend1 = xl(1)
      yend1 = yl(1)
      zend1 = zl(1)
      xend2 = xr(1)
      yend2 = yr(1)
      zend2 = zr(1)
c
      do n = 2, nfun
      if(xl(n).lt.xendl) then
      xend1 = xl(n)
      yend1 = yl(n)
      zend1 = zl(n)
      end if
      if(xr(n).gt.xend2) then
      xend2 = xr(n)
      yend2 = yr(n)
      zend2 = zr(n)
      end if
      end do
c
c++++++++++++++++++++++++
c
c now find parameters
c++++++++++++++++++++++++
c
      xrange = xend2 - xend1
      yrange = yend2 - yend1
      zrange = zend2 - zend1
c
      do n = 1, nfun
      wa(n) = (xr(n) - xl(n))/xrange
      wc(n) = (yr(n) - yl(n) - wd(n)*yrange - wh(n)*zrange)/xrange
      wk(n) = (zr(n) - zl(n) - wl(n)*yrange - wm(n)*zrange)/xrange
      we(n) = xl(n) - xend1*wa(n)
      wf(n) = yl(n) - wd(n)*yend1 - wc(n)*xend1 - wh(n)*zend1
      wg(n) = zl(n) - wl(n)*yend1 - wk(n)*xend1 - wm(n)*zend1
      end do
c
c****************************************
c Do iterations and store when requested
c****************************************
c++++++++++++++++++++++++++++++++++++++++++
c points may be found sequentally or based on the same starting point
c++++++++++++++++++++++++++++++++++++++++++
c
      print *, '? Enter 1 if sequential patterns, 0 otherwise'
      read *, iseq
      write(10,*) '! Sequential patterns indicator ', iseq
c
      print *, '? Enter number of points per frame'
      read *, nseq
      write(10,*) '! Points per frame ', nseq
c
c++++++++++++++++++++++++++++++
c
c  Define the starting point
C++++++++++++++++++++++++++++++
C
      xx = xr(1)
      yy = yr(1)
      zz = zr(1)
c
      nstore = estore - bstore + 1
      write (11,*) nstore
c
      do i = 1, niter
c
      if(iseq.eq.0) then
      if(mod(i,nseq).eq.0) then
      xx = xr(1)      
      yy = yr(1)
      zz = zr(1)
      end if
      end if
c
      read(12,*) ii
      n1 = ii + 1
c
      xnew = wa(n1)*xx + we(n1)
      ynew = wc(n1)*xx + wd(n1)*yy + wh(n1)*zz + wf(n1)
      znew = wk(n1)*xx + wl(n1)*yy + wm(n1)*zz + wg(n1)
c
      xx = xnew
      yy = ynew
      zz = znew
c
c+++++++++++++++++++++++++++++++++
c points stored in unit 11 may be plotted
c+++++++++++++++++++++++++++++++++
c
      if((i. ge. bstore).and.(i. le. estore)) then
      write(11,*) n1, real(yy), real(zz)
      end if
c
      end do
c
      stop
c      endstop
      end

```

---

### Post by sisyphus1978 on 2011-05-23
Gee thanks @gmargo. I will take a look at that. I should've guessed it was something like that.

Okay compiled it, but it seems it needs more than just that to get it running. It seems I need to supply it with some files? Is it obvious from the code what to do?

---

