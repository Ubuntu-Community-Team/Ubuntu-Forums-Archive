---
title: "Updated Kubuntu 12.04 from 10.10 and know my C++ project will not link with FFTW3"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by josephc31415 on 2012-07-21
I am new user of this forum - but not of Kubuntu. I  have been working with kubuntu and FFTW library ever since 2006.

I have a GUI program using Qt that uses the FFTW3 library. The project was linking just fine with the FFTW library until I upgraded to 12.04 from version 10.10. 
below is the output when I try and make my Qt project. I have made some simple programs that use the FFTW lib. I found on a site that the position of the '-lfftw' made a difference of wither or not the program would like. I believe the problem is with the collect2 program that C/C++ uses. I also could found that it did not matter were I put the '-lfftw' in the compile command for my Qt project; it would always complain about the undefined references.

joseph@joseph-Studio-1737:~/Programs/Qt$ make                                                                                                                                                                                                                                  
g++ -Wl,-O1 -o Qt audio.o drawarea.o fft.o main.o moc_audio.o moc_drawarea.o moc_fft.o    -L/usr/lib/i386-linux-gnu -lQtGui -lQtCore -lpthread -lasound -lfftw3                                                                                                                
fft.o: In function `fft::fft(int, float*, float*)':                                                                                                                                                                                                                            
fft.cpp:(.text+0x5e): undefined reference to `fftwf_plan_r2r_1d'                                                                                                                                                                                                               
fft.o: In function `fft::fftProceed()':                                                                                                                                                                                                                                        
fft.cpp:(.text+0x9f): undefined reference to `fftwf_execute'                                                                                                                                                                                                                   
fft.o: In function `fft::~fft()':                                                                                                                                                                                                                                              
fft.cpp:(.text+0xe5): undefined reference to `fftwf_destroy_plan'                                                                                                                                                                                                              
collect2: ld returned 1 exit status                                                                                                                                                                                                                                            
make: *** [Qt] Error 1                                                                                                                                                                                                                                                         
joseph@joseph-Studio-1737:~/Programs/Qt$

---

### Post by steeldriver on 2012-07-21
it's been a few years since I used fftw but it looks like you may be trying to use the floating point versions (rather than the default double precision) - have you tried linking libfftw3f (-lfftw3f) instead of -lfftw3?

[http://www.fftw.org/doc/Precision.html](http://www.fftw.org/doc/Precision.html)

---

### Post by josephc31415 on 2012-07-21
Thanks that was the problem. The devil's in the details. Some times it just takes someone else to see the problem. Thanks again.

---

