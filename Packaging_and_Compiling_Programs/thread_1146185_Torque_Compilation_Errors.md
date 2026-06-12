---
title: "Torque Compilation Errors"
date: 2009-05-02
forum: Packaging and Compiling Programs
---

### Post by FlyingIsFun1217 on 2009-05-02
Hey;

I know it's not a very popular software around these areas, but I'm wondering if the errors aren't ones that might be solve-able by the larger development ubuntu community.

Error log when trying to compile:

> 
ls: cannot access libogg.so.0.5.2: No such file or directory
../lib/xiph/linux/checklinks.sh: line 17: [: argument expected
ls: cannot access libtheora.so.0.1.0: No such file or directory
../lib/xiph/linux/checklinks.sh: line 17: [: argument expected
ls: cannot access libvorbisenc.so.2.0.0: No such file or directory
../lib/xiph/linux/checklinks.sh: line 17: [: argument expected
ls: cannot access libvorbisfile.so.3.1.0: No such file or directory
../lib/xiph/linux/checklinks.sh: line 17: [: argument expected
ls: cannot access libvorbis.so.0.3.0: No such file or directory
../lib/xiph/linux/checklinks.sh: line 17: [: argument expected
../lib/xiph/linux/checklinks.sh: line 27: cd: /home/tanner/Desktop/Mech: No such file or directory
--> Linking out.GCC4.3.RELEASE/torqueDemo.bin
out.GCC4.3.RELEASE/platformX86UNIX/x86UNIXCPUInfo.obj: In function `Processor::init()':
x86UNIXCPUInfo.cc:(.text+0x1bc): undefined reference to `timeHi'
x86UNIXCPUInfo.cc:(.text+0x1c2): undefined reference to `timeLo'
x86UNIXCPUInfo.cc:(.text+0x1c7): undefined reference to `clockticks'
collect2: ld returned 1 exit status
make[1]: *** [out.GCC4.3.RELEASE/torqueDemo.bin] Error 1
make: *** [default] Error 2


Thing is, the libraries it's yelling at me about are installed... not quite the same versions, but they're there.

Thanks!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2009-05-02
Finally found the file describing the versions of the libraries that torque was looking for. Bad documentation has led to quite the nightmare compiling on a recent system.

For anyone interested: /lib/xiph/checklinks.sh

FlyingIsFun1217

---

### Post by Tricity on 2010-12-08
This error seems to be a recurring theme since gcc 4.3.x. I have analyzed the code in the attempt to fix the compilation errors, and I'd like to share my analysis. In my humble opinion, that offending assembly code to determine the CPU clock rate is pretty well described as FUBAR. Lets take a look at the code to understand why the compilation fails. First, we read the time stamp (rdtsc) and store the result - after the rdtsc command in edx:eax (hi:lo). So far, so good. Next, we wait 750 ms and perform the rdtsc again, but this time the assembly code contains a subtraction:

```

pushl  %eax                             ; save eax because it gets clobbered
pushl  %edx                             ; save edx
rdtsc                                              ; read time stamp
sub    (timeLo), %edx             ; subtract result(lo) of rdtsc FROM time
sbb    (timeHi), %eax               ; subtract result (hi) with borrow from time
mov    %eax, (clockticks)  ; ??? I suspect this was supposed to be "store eax in clockticks"
popl   %edx
popl   %eax

```Apparently, the operand order of the sub/sbb/mov were confused. In fact, we should subtract timeHi;timeLo from eax:edx, then store the high word in clockticks. I think this section has never worked.

Here is one way to get it to compile. Let us assume that the first asm statement is OK;

```

asm ("rdtsc" : "=a" (timeLo), "=d" (timeHi));

```We can declare another variable pair, say, lateLo and lateHi and use those after the 750ms wait:

```

asm ("rdtsc" : "=a" (lateLo), "=d" (lateHi));

```Last, we subtract the high words only (since the high word was the only relevant word in the original code anyway):

```

clockticks = lateHi - timeHi;

```This compiles, but does not work properly, because the high word is not sufficiently accurate to count the clock ticks, even with todays GHz CPUs. We need to have higher resolution by using both low and high words. Here is the final code (somewhat shortened), tested on Ubuntu 10.04 i386:

```

/* used in the asm */
static U32 time0[2];        
static U64 *clockticks;
static U64 tickcnt;
static char vendor[13] = {0,};
static U32 properties = 0; 
static U32 processor  = 0;
static U32 timeHi = 0;
static U32 timeLo = 0;
static U32 lateHi = 0;
static U32 lateLo = 0;


void Processor::init()
{
   Platform::SystemInfo.processor.type = CPU_X86Compatible;
   Platform::SystemInfo.processor.name = StringTable->insert("Unknown x86 Compatible");
   Platform::SystemInfo.processor.mhz  = 0;
   Platform::SystemInfo.processor.properties = CPU_PROP_C;

   clockticks = (U64*)&time0;
   properties = 0;
   processor = 0;
   time0[0] = 0; time0[1]=0;
   dStrcpy(vendor, "");

   detectX86CPUInfo(vendor, &processor, &properties);
   SetProcessorInfo(Platform::SystemInfo.processor, 
      vendor, processor, properties);

   //--------------------------------------
   // if RDTSC support calculate the aproximate Mhz of the CPU
   if (Platform::SystemInfo.processor.properties & CPU_PROP_RDTSC && 
       Platform::SystemInfo.processor.properties & CPU_PROP_FPU)
   {
      const U32 MS_INTERVAL = 20;        // Delay period in ms
      
      asm ("rdtsc" : "=a" (timeLo), "=d" (timeHi));

      U32 ms = Platform::getRealMilliseconds();
      while ( Platform::getRealMilliseconds() < ms+MS_INTERVAL )
      { /* empty */ }
      ms = Platform::getRealMilliseconds()-ms;

     asm ("rdtsc" : "=a" (lateLo), "=d" (lateHi));

      time0[1] = lateHi; time0[0] = lateLo;
      tickcnt = *clockticks;
      time0[1] = timeHi; time0[0] = timeLo;
      tickcnt -= *clockticks;

      U32 mhz = static_cast<U32>(F32(tickcnt) / F32(ms) / 1000.0f);

```In the end, it seems, the CPU clock seems irrelevant in actual game performance. Go figure.

---

### Post by Tricity on 2010-12-08
Two comments. In case somebody asks, this is the file platformX86UNIX/x86UNIXCPUInfo.cc

Second, the way I wrote the code, compatibility with other UNIX-style platforms is probably shot to hell, although I think the code should work with even more gcc compliers, including pre gcc-4.3 compilers.

Afterthought. In other forums, we get the compiler warning that the -mcpu flag is deprecated. This is easily fixed by removing the -mcpu flag in mk/conf.UNIX.mk. Note that -march is already specified.

```

# NOTE - mcpu is deprecated, changed to march=i686

CFLAGS.GENERAL    = -DUSE_FILE_REDIRECT -I/usr/X11R6/include/ -MD  \
                    `freetype-config --cflags` -march=i686 -ffast-math -pipe

```

---

### Post by Tricity on 2012-09-06
Hey Y'all users of the Torque Game Engine. I thought I'd revive this thread as is seems that GarageGames has discontinued Linux support in their newest Torque3D v1.2. Shame on them! :roll:

So apparently, TGE 1.5.2 is the last version with Linux support. I guess that warrants some effort to keep it alive. I have found some fixes and patches to let TGE 1.5.2 compile and run on Precise (12.04, i386 required, gcc-4.6). Yes, it was never supposed to run with gcc above 4.1 or so.

First, as FlyingisFun1217 found out, there are some library issues as TGE comes with its own (deprecated) sound libraries in .../lib/xiph/linux. This leads to linker errors, such as a supposedly not found vorbis_version_string. Never mind, we can create some Frankenstein symlinks:

```
 libogg.so -> /usr/lib/i386-linux-gnu/libogg.so
 libogg.so.0 -> /usr/lib/i386-linux-gnu/libogg.so.0
 libogg.so.0.5.2 -> /usr/lib/i386-linux-gnu/libogg.so.0.7.1
 libtheora.so -> libtheora.so.0.1.0
 libtheora.so.0 -> libtheora.so.0.1.0
 libtheora.so.0.1.0 -> /usr/lib/i386-linux-gnu/libtheora.so.0.3.10
 libvorbisenc.so -> /usr/lib/i386-linux-gnu/libvorbisenc.so
 libvorbisenc.so.0 -> /usr/lib/i386-linux-gnu/libvorbisenc.so.2
 libvorbisenc.so.2.0.8 -> /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
 libvorbisfile.so -> /usr/lib/i386-linux-gnu/libvorbisfile.so
 libvorbisfile.so.0 -> /usr/lib/i386-linux-gnu/libvorbisfile.so.3
 libvorbisfile.so.3.1.0 -> /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
 libvorvis.so -> /usr/lib/i386-linux-gnu/libvorbis.so
 libvorvis.so.0 -> /usr/lib/i386-linux-gnu/libvorbis.so.0
 libvorvis.so.0.3.0 -> /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5

```TGE does not seem to mind the version mismatch.

Second, the compiler needs to be set properly. The file is .../mk/conf.GCC4.mk, and we bluntly specify gcc-4.6:

```
COMPILER.c      =gcc-4.6
COMPILER.cc     =g++-4.6 -Wno-invalid-offsetof
CFLAGS += -mtune=i686

```Third: New compiler, new error messages. This time, the linker stumbles in .../engine/game/projectile.cc over the reference to a function address (line 735):

```
mSoundHandle = alxPlay(mDataBlock->sound, &getRenderTransform(), &getPosition());

```The solution is to pass an address to a variable:

```
Point3F position;
    position = getPosition();
    mSoundHandle = alxPlay(mDataBlock->sound, &getRenderTransform(), &position);

```When you fixed the CPU timing assembly code in platformX86UNIX/x86UNIXCPUInfo.cc as I described above, you should be able to finish compiling and linking.

In the debug version, I get some strange assertion errors that I have not fully examined, so for now I use BUILD=RELEASE.

This, finally, seems to work. :-D

The world editor tends to randomly crash, so there is another issue to fix, but this may be related to the assertion errors. If I find something, I'll post.

Happy  gaming with TGE 1.5.2! Sorry 'bout that, GarageGames - with Linux support, I'd have purchased your new Torque3D long ago.

---

