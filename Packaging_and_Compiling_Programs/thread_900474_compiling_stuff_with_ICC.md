---
title: "compiling stuff with ICC"
date: 2008-08-25
forum: Packaging and Compiling Programs
---

### Post by piotrm on 2008-08-25
Hi, I just took a shot at ICC by trying to compile x264 with it (I heard legends of the speed improvements, so I thought that maybe it would make my old computer handle some HD movies better :) )
That's what I got:
```
x264$ make                                                                                                                                                                                  
rm -f .depend                                                                                                                                                                                                                                
( echo -n "`dirname common/mc.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/mc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/predict.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/predict.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/pixel.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/pixel.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/macroblock.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/frame.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/frame.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/dct.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/dct.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cpu.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/cpu.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cabac.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/common.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/common.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/mdate.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/mdate.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/set.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/quant.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/quant.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/vlc.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/vlc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/analyse.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/analyse.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/me.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/me.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/ratecontrol.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/ratecontrol.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/set.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/macroblock.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cabac.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cavlc.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/cavlc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/encoder.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/encoder.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/eval.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/eval.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/x86/mc-c.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/x86/mc-c.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/x86/predict-c.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/x86/predict-c.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname x264.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  x264.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname matroska.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  matroska.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname muxers.c`/" && icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  muxers.c -MM -g0 ) 1>> .depend;                                                                                                                                                                                                                                        
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/mc.o common/mc.c                                                                                                       
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/predict.o common/predict.c                                                                                             
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/pixel.o common/pixel.c                                                                                                 
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/macroblock.o common/macroblock.c                                                                                       
common/macroblock.c(961): warning #175: subscript out of range                                                                                                                                                                               
          h->mb.map_col_to_list0[-1] = -1;                                                                                                                                                                                                   
                                ^                                                                                                                                                                                                            

common/macroblock.c(962): warning #175: subscript out of range
          h->mb.map_col_to_list0[-2] = -2;                    
                                ^                             

icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/frame.o common/frame.c
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/dct.o common/dct.c    
common/dct.c(466): warning #175: subscript out of range                                                                                     
      ZIG( 0,0,0) ZIG( 1,0,1) ZIG( 2,1,0) ZIG( 3,2,0)                                                                                       
                  ^                                                                                                                         

common/dct.c(467): warning #175: subscript out of range
      ZIG( 4,1,1) ZIG( 5,0,2) ZIG( 6,0,3) ZIG( 7,1,2)  
      ^                                                

common/dct.c(467): warning #175: subscript out of range
      ZIG( 4,1,1) ZIG( 5,0,2) ZIG( 6,0,3) ZIG( 7,1,2)  
                  ^                                    

common/dct.c(467): warning #175: subscript out of range
      ZIG( 4,1,1) ZIG( 5,0,2) ZIG( 6,0,3) ZIG( 7,1,2)  
                              ^                        

common/dct.c(467): warning #175: subscript out of range
      ZIG( 4,1,1) ZIG( 5,0,2) ZIG( 6,0,3) ZIG( 7,1,2)  
                                          ^            

common/dct.c(468): warning #175: subscript out of range
      ZIG( 8,2,1) ZIG( 9,3,0) ZIG(10,4,0) ZIG(11,3,1)  
      ^                                                

common/dct.c(468): warning #175: subscript out of range
      ZIG( 8,2,1) ZIG( 9,3,0) ZIG(10,4,0) ZIG(11,3,1)  
                                          ^            

common/dct.c(469): warning #175: subscript out of range
      ZIG(12,2,2) ZIG(13,1,3) ZIG(14,0,4) ZIG(15,0,5)  
      ^                                                

common/dct.c(469): warning #175: subscript out of range
      ZIG(12,2,2) ZIG(13,1,3) ZIG(14,0,4) ZIG(15,0,5)  
                  ^                                    

common/dct.c(469): warning #175: subscript out of range
      ZIG(12,2,2) ZIG(13,1,3) ZIG(14,0,4) ZIG(15,0,5)  
                              ^                        

common/dct.c(469): warning #175: subscript out of range
      ZIG(12,2,2) ZIG(13,1,3) ZIG(14,0,4) ZIG(15,0,5)  
                                          ^            

common/dct.c(470): warning #175: subscript out of range
      ZIG(16,1,4) ZIG(17,2,3) ZIG(18,3,2) ZIG(19,4,1)  
      ^                                                

common/dct.c(470): warning #175: subscript out of range
      ZIG(16,1,4) ZIG(17,2,3) ZIG(18,3,2) ZIG(19,4,1)  
                  ^                                    

common/dct.c(470): warning #175: subscript out of range
      ZIG(16,1,4) ZIG(17,2,3) ZIG(18,3,2) ZIG(19,4,1)  
                              ^                        

common/dct.c(470): warning #175: subscript out of range
      ZIG(16,1,4) ZIG(17,2,3) ZIG(18,3,2) ZIG(19,4,1)  
                                          ^            

common/dct.c(471): warning #175: subscript out of range
      ZIG(20,5,0) ZIG(21,6,0) ZIG(22,5,1) ZIG(23,4,2)  
                              ^                        

common/dct.c(471): warning #175: subscript out of range
      ZIG(20,5,0) ZIG(21,6,0) ZIG(22,5,1) ZIG(23,4,2)  
                                          ^            

common/dct.c(472): warning #175: subscript out of range
      ZIG(24,3,3) ZIG(25,2,4) ZIG(26,1,5) ZIG(27,0,6)  
      ^                                                

common/dct.c(472): warning #175: subscript out of range
      ZIG(24,3,3) ZIG(25,2,4) ZIG(26,1,5) ZIG(27,0,6)  
                  ^                                    

common/dct.c(472): warning #175: subscript out of range
      ZIG(24,3,3) ZIG(25,2,4) ZIG(26,1,5) ZIG(27,0,6)  
                              ^                        

common/dct.c(472): warning #175: subscript out of range
      ZIG(24,3,3) ZIG(25,2,4) ZIG(26,1,5) ZIG(27,0,6)  
                                          ^            

common/dct.c(473): warning #175: subscript out of range
      ZIG(28,0,7) ZIG(29,1,6) ZIG(30,2,5) ZIG(31,3,4)  
      ^                                                

common/dct.c(473): warning #175: subscript out of range
      ZIG(28,0,7) ZIG(29,1,6) ZIG(30,2,5) ZIG(31,3,4)  
                  ^                                    

common/dct.c(473): warning #175: subscript out of range
      ZIG(28,0,7) ZIG(29,1,6) ZIG(30,2,5) ZIG(31,3,4)  
                              ^                        

common/dct.c(473): warning #175: subscript out of range
      ZIG(28,0,7) ZIG(29,1,6) ZIG(30,2,5) ZIG(31,3,4)  
                                          ^            

common/dct.c(474): warning #175: subscript out of range
      ZIG(32,4,3) ZIG(33,5,2) ZIG(34,6,1) ZIG(35,7,0)  
      ^                                                

common/dct.c(474): warning #175: subscript out of range
      ZIG(32,4,3) ZIG(33,5,2) ZIG(34,6,1) ZIG(35,7,0)  
                  ^                                    

common/dct.c(474): warning #175: subscript out of range
      ZIG(32,4,3) ZIG(33,5,2) ZIG(34,6,1) ZIG(35,7,0)  
                              ^                        

common/dct.c(475): warning #175: subscript out of range
      ZIG(36,7,1) ZIG(37,6,2) ZIG(38,5,3) ZIG(39,4,4)  
      ^                                                

common/dct.c(475): warning #175: subscript out of range
      ZIG(36,7,1) ZIG(37,6,2) ZIG(38,5,3) ZIG(39,4,4)  
                  ^                                    

common/dct.c(475): warning #175: subscript out of range
      ZIG(36,7,1) ZIG(37,6,2) ZIG(38,5,3) ZIG(39,4,4)  
                              ^                        

common/dct.c(475): warning #175: subscript out of range
      ZIG(36,7,1) ZIG(37,6,2) ZIG(38,5,3) ZIG(39,4,4)  
                                          ^            

common/dct.c(476): warning #175: subscript out of range
      ZIG(40,3,5) ZIG(41,2,6) ZIG(42,1,7) ZIG(43,2,7)  
      ^                                                

common/dct.c(476): warning #175: subscript out of range
      ZIG(40,3,5) ZIG(41,2,6) ZIG(42,1,7) ZIG(43,2,7)  
                  ^                                    

common/dct.c(476): warning #175: subscript out of range
      ZIG(40,3,5) ZIG(41,2,6) ZIG(42,1,7) ZIG(43,2,7)  
                              ^                        

common/dct.c(476): warning #175: subscript out of range
      ZIG(40,3,5) ZIG(41,2,6) ZIG(42,1,7) ZIG(43,2,7)  
                                          ^            

common/dct.c(477): warning #175: subscript out of range
      ZIG(44,3,6) ZIG(45,4,5) ZIG(46,5,4) ZIG(47,6,3)  
      ^                                                

common/dct.c(477): warning #175: subscript out of range
      ZIG(44,3,6) ZIG(45,4,5) ZIG(46,5,4) ZIG(47,6,3)  
                  ^                                    

common/dct.c(477): warning #175: subscript out of range
      ZIG(44,3,6) ZIG(45,4,5) ZIG(46,5,4) ZIG(47,6,3)  
                              ^                        

common/dct.c(477): warning #175: subscript out of range
      ZIG(44,3,6) ZIG(45,4,5) ZIG(46,5,4) ZIG(47,6,3)  
                                          ^            

common/dct.c(478): warning #175: subscript out of range
      ZIG(48,7,2) ZIG(49,7,3) ZIG(50,6,4) ZIG(51,5,5)  
      ^                                                

common/dct.c(478): warning #175: subscript out of range
      ZIG(48,7,2) ZIG(49,7,3) ZIG(50,6,4) ZIG(51,5,5)  
                  ^                                    

common/dct.c(478): warning #175: subscript out of range
      ZIG(48,7,2) ZIG(49,7,3) ZIG(50,6,4) ZIG(51,5,5)  
                              ^                        

common/dct.c(478): warning #175: subscript out of range
      ZIG(48,7,2) ZIG(49,7,3) ZIG(50,6,4) ZIG(51,5,5)  
                                          ^            

common/dct.c(479): warning #175: subscript out of range
      ZIG(52,4,6) ZIG(53,3,7) ZIG(54,4,7) ZIG(55,5,6)  
      ^                                                

common/dct.c(479): warning #175: subscript out of range
      ZIG(52,4,6) ZIG(53,3,7) ZIG(54,4,7) ZIG(55,5,6)  
                  ^                                    

common/dct.c(479): warning #175: subscript out of range
      ZIG(52,4,6) ZIG(53,3,7) ZIG(54,4,7) ZIG(55,5,6)  
                              ^                        

common/dct.c(479): warning #175: subscript out of range
      ZIG(52,4,6) ZIG(53,3,7) ZIG(54,4,7) ZIG(55,5,6)  
                                          ^            

common/dct.c(480): warning #175: subscript out of range
      ZIG(56,6,5) ZIG(57,7,4) ZIG(58,7,5) ZIG(59,6,6)  
      ^                                                

common/dct.c(480): warning #175: subscript out of range
      ZIG(56,6,5) ZIG(57,7,4) ZIG(58,7,5) ZIG(59,6,6)  
                  ^                                    

common/dct.c(480): warning #175: subscript out of range
      ZIG(56,6,5) ZIG(57,7,4) ZIG(58,7,5) ZIG(59,6,6)  
                              ^                        

common/dct.c(480): warning #175: subscript out of range
      ZIG(56,6,5) ZIG(57,7,4) ZIG(58,7,5) ZIG(59,6,6)  
                                          ^            

common/dct.c(481): warning #175: subscript out of range
      ZIG(60,5,7) ZIG(61,6,7) ZIG(62,7,6) ZIG(63,7,7)  
      ^                                                

common/dct.c(481): warning #175: subscript out of range
      ZIG(60,5,7) ZIG(61,6,7) ZIG(62,7,6) ZIG(63,7,7)  
                  ^                                    

common/dct.c(481): warning #175: subscript out of range
      ZIG(60,5,7) ZIG(61,6,7) ZIG(62,7,6) ZIG(63,7,7)  
                              ^                        

common/dct.c(481): warning #175: subscript out of range
      ZIG(60,5,7) ZIG(61,6,7) ZIG(62,7,6) ZIG(63,7,7)  
                                          ^            

common/dct.c(486): warning #175: subscript out of range
      ZIG( 0,0,0) ZIG( 1,1,0) ZIG( 2,2,0) ZIG( 3,0,1)  
                                          ^            

common/dct.c(487): warning #175: subscript out of range
      ZIG( 4,1,1) ZIG( 5,3,0) ZIG( 6,4,0) ZIG( 7,2,1)  
      ^                                                

common/dct.c(487): warning #175: subscript out of range
      ZIG( 4,1,1) ZIG( 5,3,0) ZIG( 6,4,0) ZIG( 7,2,1)  
                                          ^            

common/dct.c(488): warning #175: subscript out of range
      ZIG( 8,0,2) ZIG( 9,3,1) ZIG(10,5,0) ZIG(11,6,0)  
      ^                                                

common/dct.c(488): warning #175: subscript out of range
      ZIG( 8,0,2) ZIG( 9,3,1) ZIG(10,5,0) ZIG(11,6,0)  
                  ^                                    

common/dct.c(489): warning #175: subscript out of range
      ZIG(12,7,0) ZIG(13,4,1) ZIG(14,1,2) ZIG(15,0,3)  
                  ^                                    

common/dct.c(489): warning #175: subscript out of range
      ZIG(12,7,0) ZIG(13,4,1) ZIG(14,1,2) ZIG(15,0,3)  
                              ^                        

common/dct.c(489): warning #175: subscript out of range
      ZIG(12,7,0) ZIG(13,4,1) ZIG(14,1,2) ZIG(15,0,3)  
                                          ^            

common/dct.c(490): warning #175: subscript out of range
      ZIG(16,2,2) ZIG(17,5,1) ZIG(18,6,1) ZIG(19,7,1)  
      ^                                                

common/dct.c(490): warning #175: subscript out of range
      ZIG(16,2,2) ZIG(17,5,1) ZIG(18,6,1) ZIG(19,7,1)  
                  ^                                    

common/dct.c(490): warning #175: subscript out of range
      ZIG(16,2,2) ZIG(17,5,1) ZIG(18,6,1) ZIG(19,7,1)  
                              ^                        

common/dct.c(490): warning #175: subscript out of range
      ZIG(16,2,2) ZIG(17,5,1) ZIG(18,6,1) ZIG(19,7,1)  
                                          ^            

common/dct.c(491): warning #175: subscript out of range
      ZIG(20,3,2) ZIG(21,1,3) ZIG(22,0,4) ZIG(23,2,3)  
      ^                                                

common/dct.c(491): warning #175: subscript out of range
      ZIG(20,3,2) ZIG(21,1,3) ZIG(22,0,4) ZIG(23,2,3)  
                  ^                                    

common/dct.c(491): warning #175: subscript out of range
      ZIG(20,3,2) ZIG(21,1,3) ZIG(22,0,4) ZIG(23,2,3)  
                              ^                        

common/dct.c(491): warning #175: subscript out of range
      ZIG(20,3,2) ZIG(21,1,3) ZIG(22,0,4) ZIG(23,2,3)  
                                          ^            

common/dct.c(492): warning #175: subscript out of range
      ZIG(24,4,2) ZIG(25,5,2) ZIG(26,6,2) ZIG(27,7,2)  
      ^                                                

common/dct.c(492): warning #175: subscript out of range
      ZIG(24,4,2) ZIG(25,5,2) ZIG(26,6,2) ZIG(27,7,2)  
                  ^                                    

common/dct.c(492): warning #175: subscript out of range
      ZIG(24,4,2) ZIG(25,5,2) ZIG(26,6,2) ZIG(27,7,2)  
                              ^                        

common/dct.c(492): warning #175: subscript out of range
      ZIG(24,4,2) ZIG(25,5,2) ZIG(26,6,2) ZIG(27,7,2)  
                                          ^            

common/dct.c(493): warning #175: subscript out of range
      ZIG(28,3,3) ZIG(29,1,4) ZIG(30,0,5) ZIG(31,2,4)  
      ^                                                

common/dct.c(493): warning #175: subscript out of range
      ZIG(28,3,3) ZIG(29,1,4) ZIG(30,0,5) ZIG(31,2,4)  
                  ^                                    

common/dct.c(493): warning #175: subscript out of range
      ZIG(28,3,3) ZIG(29,1,4) ZIG(30,0,5) ZIG(31,2,4)  
                              ^                        

common/dct.c(493): warning #175: subscript out of range
      ZIG(28,3,3) ZIG(29,1,4) ZIG(30,0,5) ZIG(31,2,4)  
                                          ^            

common/dct.c(494): warning #175: subscript out of range
      ZIG(32,4,3) ZIG(33,5,3) ZIG(34,6,3) ZIG(35,7,3)  
      ^                                                

common/dct.c(494): warning #175: subscript out of range
      ZIG(32,4,3) ZIG(33,5,3) ZIG(34,6,3) ZIG(35,7,3)  
                  ^                                    

common/dct.c(494): warning #175: subscript out of range
      ZIG(32,4,3) ZIG(33,5,3) ZIG(34,6,3) ZIG(35,7,3)  
                              ^                        

common/dct.c(494): warning #175: subscript out of range
      ZIG(32,4,3) ZIG(33,5,3) ZIG(34,6,3) ZIG(35,7,3)  
                                          ^            

common/dct.c(495): warning #175: subscript out of range
      ZIG(36,3,4) ZIG(37,1,5) ZIG(38,0,6) ZIG(39,2,5)  
      ^                                                

common/dct.c(495): warning #175: subscript out of range
      ZIG(36,3,4) ZIG(37,1,5) ZIG(38,0,6) ZIG(39,2,5)  
                  ^                                    

common/dct.c(495): warning #175: subscript out of range
      ZIG(36,3,4) ZIG(37,1,5) ZIG(38,0,6) ZIG(39,2,5)  
                              ^                        

common/dct.c(495): warning #175: subscript out of range
      ZIG(36,3,4) ZIG(37,1,5) ZIG(38,0,6) ZIG(39,2,5)  
                                          ^            

common/dct.c(496): warning #175: subscript out of range
      ZIG(40,4,4) ZIG(41,5,4) ZIG(42,6,4) ZIG(43,7,4)  
      ^                                                

common/dct.c(496): warning #175: subscript out of range
      ZIG(40,4,4) ZIG(41,5,4) ZIG(42,6,4) ZIG(43,7,4)  
                  ^                                    

common/dct.c(496): warning #175: subscript out of range
      ZIG(40,4,4) ZIG(41,5,4) ZIG(42,6,4) ZIG(43,7,4)  
                              ^                        

common/dct.c(496): warning #175: subscript out of range
      ZIG(40,4,4) ZIG(41,5,4) ZIG(42,6,4) ZIG(43,7,4)  
                                          ^            

common/dct.c(497): warning #175: subscript out of range
      ZIG(44,3,5) ZIG(45,1,6) ZIG(46,2,6) ZIG(47,4,5)  
      ^                                                

common/dct.c(497): warning #175: subscript out of range
      ZIG(44,3,5) ZIG(45,1,6) ZIG(46,2,6) ZIG(47,4,5)  
                  ^                                    

common/dct.c(497): warning #175: subscript out of range
      ZIG(44,3,5) ZIG(45,1,6) ZIG(46,2,6) ZIG(47,4,5)  
                              ^                        

common/dct.c(497): warning #175: subscript out of range
      ZIG(44,3,5) ZIG(45,1,6) ZIG(46,2,6) ZIG(47,4,5)  
                                          ^            

common/dct.c(498): warning #175: subscript out of range
      ZIG(48,5,5) ZIG(49,6,5) ZIG(50,7,5) ZIG(51,3,6)  
      ^                                                

common/dct.c(498): warning #175: subscript out of range
      ZIG(48,5,5) ZIG(49,6,5) ZIG(50,7,5) ZIG(51,3,6)  
                  ^                                    

common/dct.c(498): warning #175: subscript out of range
      ZIG(48,5,5) ZIG(49,6,5) ZIG(50,7,5) ZIG(51,3,6)  
                              ^                        

common/dct.c(498): warning #175: subscript out of range
      ZIG(48,5,5) ZIG(49,6,5) ZIG(50,7,5) ZIG(51,3,6)  
                                          ^            

common/dct.c(499): warning #175: subscript out of range
      ZIG(52,0,7) ZIG(53,1,7) ZIG(54,4,6) ZIG(55,5,6)  
      ^                                                

common/dct.c(499): warning #175: subscript out of range
      ZIG(52,0,7) ZIG(53,1,7) ZIG(54,4,6) ZIG(55,5,6)  
                  ^                                    

common/dct.c(499): warning #175: subscript out of range
      ZIG(52,0,7) ZIG(53,1,7) ZIG(54,4,6) ZIG(55,5,6)  
                              ^                        

common/dct.c(499): warning #175: subscript out of range
      ZIG(52,0,7) ZIG(53,1,7) ZIG(54,4,6) ZIG(55,5,6)  
                                          ^            

common/dct.c(500): warning #175: subscript out of range
      ZIG(56,6,6) ZIG(57,7,6) ZIG(58,2,7) ZIG(59,3,7)  
      ^                                                

common/dct.c(500): warning #175: subscript out of range
      ZIG(56,6,6) ZIG(57,7,6) ZIG(58,2,7) ZIG(59,3,7)  
                  ^                                    

common/dct.c(500): warning #175: subscript out of range
      ZIG(56,6,6) ZIG(57,7,6) ZIG(58,2,7) ZIG(59,3,7)  
                              ^                        

common/dct.c(500): warning #175: subscript out of range
      ZIG(56,6,6) ZIG(57,7,6) ZIG(58,2,7) ZIG(59,3,7)  
                                          ^            

common/dct.c(501): warning #175: subscript out of range
      ZIG(60,4,7) ZIG(61,5,7) ZIG(62,6,7) ZIG(63,7,7)  
      ^                                                

common/dct.c(501): warning #175: subscript out of range
      ZIG(60,4,7) ZIG(61,5,7) ZIG(62,6,7) ZIG(63,7,7)  
                  ^                                    

common/dct.c(501): warning #175: subscript out of range
      ZIG(60,4,7) ZIG(61,5,7) ZIG(62,6,7) ZIG(63,7,7)  
                              ^                        

common/dct.c(501): warning #175: subscript out of range
      ZIG(60,4,7) ZIG(61,5,7) ZIG(62,6,7) ZIG(63,7,7)  
                                          ^            

common/dct.c(509): warning #175: subscript out of range
      ZIG( 0,0,0) ZIG( 1,0,1) ZIG( 2,1,0) ZIG( 3,2,0)  
                  ^                                    

common/dct.c(510): warning #175: subscript out of range
      ZIG( 4,1,1) ZIG( 5,0,2) ZIG( 6,0,3) ZIG( 7,1,2)  
      ^                                                

common/dct.c(510): warning #175: subscript out of range
      ZIG( 4,1,1) ZIG( 5,0,2) ZIG( 6,0,3) ZIG( 7,1,2)  
                  ^                                    

common/dct.c(510): warning #175: subscript out of range
      ZIG( 4,1,1) ZIG( 5,0,2) ZIG( 6,0,3) ZIG( 7,1,2)  
                              ^                        

common/dct.c(510): warning #175: subscript out of range
      ZIG( 4,1,1) ZIG( 5,0,2) ZIG( 6,0,3) ZIG( 7,1,2)  
                                          ^            

common/dct.c(511): warning #175: subscript out of range
      ZIG( 8,2,1) ZIG( 9,3,0) ZIG(10,3,1) ZIG(11,2,2)  
      ^                                                

common/dct.c(511): warning #175: subscript out of range
      ZIG( 8,2,1) ZIG( 9,3,0) ZIG(10,3,1) ZIG(11,2,2)  
                              ^                        

common/dct.c(511): warning #175: subscript out of range
      ZIG( 8,2,1) ZIG( 9,3,0) ZIG(10,3,1) ZIG(11,2,2)  
                                          ^            

common/dct.c(512): warning #175: subscript out of range
      ZIG(12,1,3) ZIG(13,2,3) ZIG(14,3,2) ZIG(15,3,3)  
      ^                                                

common/dct.c(512): warning #175: subscript out of range
      ZIG(12,1,3) ZIG(13,2,3) ZIG(14,3,2) ZIG(15,3,3)  
                  ^                                    

common/dct.c(512): warning #175: subscript out of range
      ZIG(12,1,3) ZIG(13,2,3) ZIG(14,3,2) ZIG(15,3,3)  
                              ^                        

common/dct.c(512): warning #175: subscript out of range
      ZIG(12,1,3) ZIG(13,2,3) ZIG(14,3,2) ZIG(15,3,3)  
                                          ^            

common/dct.c(518): warning #175: subscript out of range
      ZIG(2,0,1) ZIG(3,2,0) ZIG(4,3,0) ZIG(5,1,1)      
      ^                                                

common/dct.c(518): warning #175: subscript out of range
      ZIG(2,0,1) ZIG(3,2,0) ZIG(4,3,0) ZIG(5,1,1)      
                                       ^               

common/dct.c(519): warning #175: subscript out of range
      *(uint32_t*)(level+6) = *(uint32_t*)(*dct+6);    
                                               ^       

common/dct.c(520): warning #175: subscript out of range
      *(uint64_t*)(level+8) = *(uint64_t*)(*dct+8);    
                                               ^       

common/dct.c(521): warning #175: subscript out of range
      *(uint64_t*)(level+12) = *(uint64_t*)(*dct+12);  
                                                ^      

icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/cpu.o common/cpu.c
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/cabac.o common/cabac.c
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/common.o common/common.c
common/common.c(231): warning #187: use of "=" where "==" may have been intended                                                              
      if( (!strncmp( name, "no-", 3 ) && (i = 3)) ||                                                                                          
                                         ^                                                                                                    

common/common.c(232): warning #187: use of "=" where "==" may have been intended
          (!strncmp( name, "no", 2 ) && (i = 2)) )                              
                                        ^                                       

icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/mdate.o common/mdate.c
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/set.o common/set.c    
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/quant.o common/quant.c
common/quant.c(66): warning #175: subscript out of range                                                                                    
      QUANT_ONE( dct[0][2], mf, bias );                                                                                                     
      ^                                                                                                                                     

common/quant.c(66): warning #175: subscript out of range
      QUANT_ONE( dct[0][2], mf, bias );                 
      ^                                                 

common/quant.c(66): warning #175: subscript out of range
      QUANT_ONE( dct[0][2], mf, bias );                 
      ^                                                 

common/quant.c(66): warning #175: subscript out of range
      QUANT_ONE( dct[0][2], mf, bias );                 
      ^                                                 

common/quant.c(66): warning #175: subscript out of range
      QUANT_ONE( dct[0][2], mf, bias );                 
      ^                                                 

common/quant.c(67): warning #175: subscript out of range
      QUANT_ONE( dct[0][3], mf, bias );                 
      ^                                                 

common/quant.c(67): warning #175: subscript out of range
      QUANT_ONE( dct[0][3], mf, bias );                 
      ^                                                 

common/quant.c(67): warning #175: subscript out of range
      QUANT_ONE( dct[0][3], mf, bias );                 
      ^                                                 

common/quant.c(67): warning #175: subscript out of range
      QUANT_ONE( dct[0][3], mf, bias );                 
      ^                                                 

common/quant.c(67): warning #175: subscript out of range
      QUANT_ONE( dct[0][3], mf, bias );                 
      ^                                                 

icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/vlc.o common/vlc.c
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/analyse.o encoder/analyse.c
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/me.o encoder/me.c          
encoder/me.c(955): warning #186: pointless comparison of unsigned integer with zero                                                               
      COST_MV_RD( bmx, bmy, 0, 0, 0 );                                                                                                            
      ^                                                                                                                                           

icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/ratecontrol.o encoder/ratecontrol.c
encoder/ratecontrol.c(1189): warning #144: a value of type "void *" cannot be used to initialize an entity of type "double (*)(void *, double)"           
          (void *)qscale2bits,                                                                                                                            
          ^                                                                                                                                               

icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/set.o encoder/set.c
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/macroblock.o encoder/macroblock.c
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/cabac.o encoder/cabac.c          
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/cavlc.o encoder/cavlc.c          
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/encoder.o encoder/encoder.c      
encoder/encoder.c(1537): warning #167: argument of type "void *" is incompatible with parameter of type "void *(*)(void *)"                             
          x264_pthread_create( &h->thread_handle, NULL, (void*)x264_slices_write, h );                                                                  
                                                        ^                                                                                               

icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/eval.o encoder/eval.c
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/x86/mc-c.o common/x86/mc-c.c
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/x86/predict-c.o common/x86/predict-c.c
yasm -O2 -f elf -Icommon/x86/ -o common/x86/cabac-a.o common/x86/cabac-a.asm                                                                                
yasm -O2 -f elf -Icommon/x86/ -o common/x86/dct-a.o common/x86/dct-a.asm                                                                                    
yasm -O2 -f elf -Icommon/x86/ -o common/x86/deblock-a.o common/x86/deblock-a.asm                                                                            
yasm -O2 -f elf -Icommon/x86/ -o common/x86/mc-a.o common/x86/mc-a.asm                                                                                      
yasm -O2 -f elf -Icommon/x86/ -o common/x86/mc-a2.o common/x86/mc-a2.asm                                                                                    
yasm -O2 -f elf -Icommon/x86/ -o common/x86/pixel-a.o common/x86/pixel-a.asm                                                                                
yasm -O2 -f elf -Icommon/x86/ -o common/x86/predict-a.o common/x86/predict-a.asm                                                                            
yasm -O2 -f elf -Icommon/x86/ -o common/x86/quant-a.o common/x86/quant-a.asm                                                                                
yasm -O2 -f elf -Icommon/x86/ -o common/x86/sad-a.o common/x86/sad-a.asm                                                                                    
yasm -O2 -f elf -Icommon/x86/ -o common/x86/cpu-32.o common/x86/cpu-32.asm                                                                                  
yasm -O2 -f elf -Icommon/x86/ -o common/x86/dct-32.o common/x86/dct-32.asm                                                                                  
yasm -O2 -f elf -Icommon/x86/ -o common/x86/pixel-32.o common/x86/pixel-32.asm                                                                              
icc -shared -o libx264.so.60 common/mc.o common/predict.o common/pixel.o common/macroblock.o common/frame.o common/dct.o common/cpu.o common/cabac.o common/common.o common/mdate.o common/set.o common/quant.o common/vlc.o encoder/analyse.o encoder/me.o encoder/ratecontrol.o encoder/set.o encoder/macroblock.o encoder/cabac.o encoder/cavlc.o encoder/encoder.o encoder/eval.o common/x86/mc-c.o common/x86/predict-c.o common/x86/cabac-a.o common/x86/dct-a.o common/x86/deblock-a.o common/x86/mc-a.o common/x86/mc-a2.o common/x86/pixel-a.o common/x86/predict-a.o common/x86/quant-a.o common/x86/sad-a.o common/x86/cpu-32.o common/x86/dct-32.o common/x86/pixel-32.o -Wl,-soname,libx264.so.60 -lm -lpthread -s        
ipo: remark #11000: performing multi-file optimizations                                                                                                                                                                                      
ipo: remark #11006: generating assembly file /tmp/iccuFcCIZas_.s                                                                                                                                                                             
common/mc.c(73): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                       
common/mc.c(72): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                       
common/mc.c(209): (col. 9) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                      
common/mc.c(188): (col. 9) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                      
common/predict.c(606): (col. 5) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                 


common/predict.c(87): (col. 5) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                  
common/pixel.c(405): (col. 13) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                  
common/pixel.c(320): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(320): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(319): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(319): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(318): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(318): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(317): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(317): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(243): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(242): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(241): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(240): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(239): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(238): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(237): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(385): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                   
common/pixel.c(96): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                    
common/pixel.c(95): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                    
common/pixel.c(94): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                    
common/pixel.c(93): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                    
common/pixel.c(92): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                    
common/pixel.c(91): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                    
common/pixel.c(90): (col. 1) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                    
common/dct.c(285): (col. 5) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                     
common/quant.c(174): (col. 9) remark: BLOCK WAS VECTORIZED.                                                                                                                                                                                  
encoder/encoder.c(1879): (col. 9) remark: LOOP WAS VECTORIZED.                                                                                                                                                                               
encoder/cabac.c(488): (col. 5) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                  
encoder/analyse.c(1455): (col. 9) remark: BLOCK WAS VECTORIZED.                                                                                                                                                                              
encoder/analyse.c(1482): (col. 9) remark: BLOCK WAS VECTORIZED.                                                                                                                                                                              
encoder/analyse.c(985): (col. 9) remark: BLOCK WAS VECTORIZED.                                                                                                                                                                               
encoder/analyse.c(1076): (col. 13) remark: BLOCK WAS VECTORIZED.                                                                                                                                                                             
encoder/analyse.c(1185): (col. 13) remark: BLOCK WAS VECTORIZED.                                                                                                                                                                             
encoder/analyse.c(1234): (col. 13) remark: BLOCK WAS VECTORIZED.                                                                                                                                                                             
encoder/me.c(1001): (col. 5) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                    
encoder/rdo.c(501): (col. 5) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                    
encoder/rdo.c(512): (col. 5) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                    
encoder/macroblock.c(180): (col. 5) remark: BLOCK WAS VECTORIZED.                                                                                                                                                                            
encoder/cabac.c(488): (col. 5) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                  
common/macroblock.c(1423): (col. 9) remark: LOOP WAS VECTORIZED.                                                                                                                                                                             
encoder/ratecontrol.c(926): (col. 27) remark: LOOP WAS VECTORIZED.                                                                                                                                                                           
encoder/ratecontrol.c(939): (col. 22) remark: LOOP WAS VECTORIZED.                                                                                                                                                                           
encoder/ratecontrol.c(949): (col. 16) remark: LOOP WAS VECTORIZED.                                                                                                                                                                           
encoder/ratecontrol.c(965): (col. 22) remark: LOOP WAS VECTORIZED.                                                                                                                                                                           
encoder/ratecontrol.c(973): (col. 22) remark: LOOP WAS VECTORIZED.                                                                                                                                                                           
encoder/ratecontrol.c(982): (col. 22) remark: LOOP WAS VECTORIZED.                                                                                                                                                                           
encoder/analyse.c(295): (col. 9) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                
encoder/analyse.c(310): (col. 13) remark: PARTIAL LOOP WAS VECTORIZED.                                                                                                                                                                       
encoder/analyse.c(310): (col. 13) remark: PARTIAL LOOP WAS VECTORIZED.                                                                                                                                                                       
common/mc.c(303): (col. 9) remark: LOOP WAS VECTORIZED.                                                                                                                                                                                      
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o x264.o x264.c                                                                                                                 
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o matroska.o matroska.c                                                                                                         
icc -fast -I. -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o muxers.o muxers.c                                                                                                             
muxers.c(496): warning #167: argument of type "void *" is incompatible with parameter of type "void *(*)(void *)"                                                                                                                            
          x264_pthread_create( &h->tid, NULL, (void*)read_frame_thread_int, h->next_args );                                                                                                                                                  
                                              ^                                                                                                                                                                                              

ar rc libx264.a common/mc.o common/predict.o common/pixel.o common/macroblock.o common/frame.o common/dct.o common/cpu.o common/cabac.o common/common.o common/mdate.o common/set.o common/quant.o common/vlc.o encoder/analyse.o encoder/me.o encoder/ratecontrol.o encoder/set.o encoder/macroblock.o encoder/cabac.o encoder/cavlc.o encoder/encoder.o encoder/eval.o common/x86/mc-c.o common/x86/predict-c.o common/x86/cabac-a.o common/x86/dct-a.o common/x86/deblock-a.o common/x86/mc-a.o common/x86/mc-a2.o common/x86/pixel-a.o common/x86/predict-a.o common/x86/quant-a.o common/x86/sad-a.o common/x86/cpu-32.o common/x86/dct-32.o common/x86/pixel-32.o                                                                
ranlib libx264.a                                                                                                                                                                                                                             
icc -o x264 x264.o matroska.o muxers.o libx264.a -lm -lpthread -s                                                                                                                                                                            
ipo: warning #11043: unresolved x264_encoder_encode                                                                                                                                                                                          
        Referenced in /tmp/ipo_iccaB4GFb.o                                                                                                                                                                                                   
ipo: warning #11043: unresolved x264_malloc                                                                                                                                                                                                  
        Referenced in /tmp/ipo_iccaB4GFb.o                                                                                                                                                                                                   
ipo: warning #11043: unresolved x264_nal_encode                                                                                                                                                                                              
        Referenced in /tmp/ipo_iccaB4GFb.o                                                                                                                                                                                                   
ipo: warning #11043: unresolved x264_encoder_open
        Referenced in /tmp/ipo_iccaB4GFb.o
ipo: warning #11043: unresolved x264_mdate
        Referenced in /tmp/ipo_iccaB4GFb.o
ipo: warning #11043: unresolved x264_encoder_close
        Referenced in /tmp/ipo_iccaB4GFb.o
ipo: warning #11043: unresolved x264_free
        Referenced in /tmp/ipo_iccaB4GFb.o
ipo: warning #11043: unresolved x264_param_parse
        Referenced in /tmp/ipo_iccaB4GFb.o
ipo: warning #11043: unresolved x264_cpu_num_processors
        Referenced in /tmp/ipo_iccaB4GFb.o
ipo: warning #11043: unresolved x264_param_default
        Referenced in /tmp/ipo_iccaB4GFb.o
ipo: warning #11043: unresolved x264_picture_clean
        Referenced in /tmp/ipo_iccaB4GFb.o
ipo: warning #11043: unresolved x264_picture_alloc
        Referenced in /tmp/ipo_iccaB4GFb.o
ipo: warning #11043: unresolved x264_reduce_fraction
        Referenced in /tmp/ipo_iccaB4GFb.o
ipo: remark #11000: performing multi-file optimizations
ipo: remark #11006: generating assembly file /tmp/iccwUX49mas_.s
/tmp/ipo_iccaB4GFb.o: In function `main':
ipo_iccaB4GFb.c:(.text+0x34): undefined reference to `x264_param_default'
/tmp/ipo_iccaB4GFb.o: In function `Parse':
ipo_iccaB4GFb.c:(.text+0x25c): undefined reference to `x264_param_parse'
ipo_iccaB4GFb.c:(.text+0x7de): undefined reference to `x264_cpu_num_processors'
ipo_iccaB4GFb.c:(.text+0x801): undefined reference to `x264_picture_alloc'
/tmp/ipo_iccaB4GFb.o: In function `Encode':
ipo_iccaB4GFb.c:(.text+0x1142): undefined reference to `x264_encoder_open'
ipo_iccaB4GFb.c:(.text+0x1177): undefined reference to `x264_picture_alloc'
ipo_iccaB4GFb.c:(.text+0x117f): undefined reference to `x264_mdate'
ipo_iccaB4GFb.c:(.text+0x1385): undefined reference to `x264_encoder_encode'
ipo_iccaB4GFb.c:(.text+0x13f8): undefined reference to `x264_free'
ipo_iccaB4GFb.c:(.text+0x1403): undefined reference to `x264_malloc'
ipo_iccaB4GFb.c:(.text+0x1439): undefined reference to `x264_nal_encode'
ipo_iccaB4GFb.c:(.text+0x1535): undefined reference to `x264_mdate'
ipo_iccaB4GFb.c:(.text+0x1734): undefined reference to `x264_encoder_encode'
ipo_iccaB4GFb.c:(.text+0x17a1): undefined reference to `x264_free'
ipo_iccaB4GFb.c:(.text+0x17ac): undefined reference to `x264_malloc'
ipo_iccaB4GFb.c:(.text+0x17df): undefined reference to `x264_nal_encode'
ipo_iccaB4GFb.c:(.text+0x187f): undefined reference to `x264_mdate'
ipo_iccaB4GFb.c:(.text+0x189a): undefined reference to `x264_picture_clean'
ipo_iccaB4GFb.c:(.text+0x18a0): undefined reference to `x264_encoder_close'
ipo_iccaB4GFb.c:(.text+0x18ab): undefined reference to `x264_free'
/tmp/ipo_iccaB4GFb.o: In function `open_file_thread':
ipo_iccaB4GFb.c:(.text+0x1ae6): undefined reference to `x264_picture_alloc'
/tmp/ipo_iccaB4GFb.o: In function `close_file_thread':
ipo_iccaB4GFb.c:(.text+0x1b4a): undefined reference to `x264_picture_clean'
/tmp/ipo_iccaB4GFb.o: In function `open_file_y4m':
ipo_iccaB4GFb.c:(.text+0x22b6): undefined reference to `x264_reduce_fraction'
ipo_iccaB4GFb.c:(.text+0x230d): undefined reference to `x264_reduce_fraction'
make: *** [x264] B&#322;&#261;d 1

```

Please tell me, am I doing something wrong, or is it just some x264 problem?

---

### Post by ubuntp on 2008-09-11
The problem is the -ipo switch. About speed improvements with x264 see [here]("http://macles.blogspot.com/2008/09/intel-cc-compiler-gcc-and-intel-atom.html"), seems to be not so great.

---

### Post by VMC on 2008-09-12
Here's a guy that also thought ICC was going to get him a 30% increase in speed. After all the problems he had it wasn't much if any speed improvement over gcc.

[http://www.linuxquestions.org/questions/linux-kernel-70/compiling-2.6.26.3-with-intel-compiler-668510/](http://www.linuxquestions.org/questions/linux-kernel-70/compiling-2.6.26.3-with-intel-compiler-668510/)

---

