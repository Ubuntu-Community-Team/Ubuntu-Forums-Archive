---
title: "Help debugging a .mex file"
date: 2010-07-29
forum: Programming Talk
---

### Post by stair314 on 2010-07-29
I'm trying to use a video library called VideoIO with matlab for a machine learning project. When I try to invoke the library in matlab, I get an error saying that it can't find libavutil.so.50, one of the ffmpeg libraries that VideoIO depends on. I've checked a few different things but can't find anything that looks wrong, other than the fact that it doesn't run. Can anyone suggest anything else to check to help me debug?

 Here is the error: 
error while loading shared libraries: libavutil.so.50: cannot open shared object file: No such file or directory 
??? Error using ==> videoReader_ffmpegPopen2 EOF found while trying to read the communication tag. The server process probably died. String so far: "" Function: int VideoIO::readMessageHeader(FILE*) File : pipecomm.h Line : 306 Error in ==> videoReader.videoReader at 152 vr.handle = feval(vr.plugin, 'open',vr.handle, ...

 Trying to figure out what went wrong, I found where vr is allocated:
 vr = struct('plugin',pvtVideoIO_mexName(mfilename, plugin), ... 'handle',int32(-1));

 I printed out mfilename, then ran ldd on the file it points to:
 $ ldd videoReader_ffmpegPopen2Server linux-vdso.so.1 => (0x00007fff41dff000) libavutil.so.50 => /u/goodfeli/ffmpeg/libavutil/libavutil.so.50 (0x00007fd5f2895000) libavdevice.so.52 => /u/goodfeli/ffmpeg/libavdevice/libavdevice.so.52 (0x00007fd5f268c000) libavformat.so.52 => /u/goodfeli/ffmpeg/libavformat/libavformat.so.52 (0x00007fd5f23bf000) libavcodec.so.52 => /u/goodfeli/ffmpeg/libavcodec/libavcodec.so.52 (0x00007fd5f1792000) libavfilter.so.1 => /u/goodfeli/ffmpeg/libavfilter/libavfilter.so.1 (0x00007fd5f1584000) libswscale.so.0 => /u/goodfeli/ffmpeg/libswscale/libswscale.so.0 (0x00007fd5f1351000) libstdc++.so.6 => /usr/lib64/libstdc++.so.6 (0x000000378ea00000) libm.so.6 => /lib64/libm.so.6 (0x0000003788a00000) libgcc_s.so.1 => /lib64/libgcc_s.so.1 (0x000000378c600000) libc.so.6 => /lib64/libc.so.6 (0x0000003788600000) libpthread.so.0 => /lib64/libpthread.so.0 (0x0000003789200000) libasound.so.2 => /lib64/libasound.so.2 (0x000000379a200000) libbz2.so.1 => /lib64/libbz2.so.1 (0x0000003b0b400000) libz.so.1 => /lib64/libz.so.1 (0x0000003789600000) /lib64/ld-linux-x86-64.so.2 (0x0000003787400000) libdl.so.2 => /lib64/libdl.so.2 (0x0000003788e00000) librt.so.1 => /lib64/librt.so.1 (0x000000378b200000) 

Now, by copy-pasting the path for libavutil, I verify that it is correct: 
$ ls /u/goodfeli/ffmpeg/libavutil
/libavutil.so.50 /u/goodfeli/ffmpeg/libavutil/libavutil.so.50

 So that file exists. Now in matlab I check matlab's LD_LIBRARY_PATH variable:
 >> getenv('LD_LIBRARY_PATH')
ans = /soft/diro/share/matlabr2009b/sys/os/glnxa64:/soft/diro/share/matlabr2009b/bin/glnxa64:/soft/diro/share/matlabr2009b/extern/lib/glnxa64:/soft/diro/share/matlabr2009b/runtime/glnxa64:/soft/diro/share/matlabr2009b/sys/java/jre/glnxa64/jre/lib/amd64/native_threads:/soft/diro/share/matlabr2009b/sys/java/jre/glnxa64/jre/lib/amd64/server:/soft/diro/share/matlabr2009b/sys/java/jre/glnxa64/jre/lib/amd64:/u/goodfeli/ffmpeg/libavfilter:/u/goodfeli/ffmpeg/libswscale:/u/goodfeli/ffmpeg/libavdevice:/u/goodfeli/ffmpeg/libavformat:/u/goodfeli/ffmpeg/libavcodec:/u/goodfeli/ffmpeg/libavutil:/opt/lisa/os/cuda/lib64:/opt/lisa/os/cuda/lib:/opt/lisa/byhost/lib:/opt/lisa/os/lib/vtk:/opt/lisa/os/lib/intelmkl/lib/32:/opt/lisa/os/lib:/opt/lisa/os/lib64:/usr/local/lib:/usr/lib64/atlas/::/opt/lisa/os/panda/lib:/opt/lisa/os/lib32:/opt/lisa/byhost/lib32

This seems to be correct, it includes /u/goodfeli/ffmpeg/libavutil/ and by copy-pasting it I can verify there is no typo:
 $ ls /u/goodfeli/ffmpeg/libavutil/ | grep "\.so"
 libavutil.so libavutil.so.50
Does anyone know what's going wrong? Thanks in advance.

---

### Post by lloyd_b on 2010-07-29
At a guess - it's executing a new shell to run the VideoIO, and that shell isn't inheriting the environment (particularly the LD_LIBRARY_PATH variable) from matlab.

From matlab, try executing a shell script like below this:```
#!/bin/bash
env | grep "LD_LIBRARY_PATH"
```and see if you're still getting the same value as the getenv() method you used.

It may be you need to set LD_LIBRARY_PATH before invoking matlab (rather than letting matlab do it), making sure that it will be inherited by putting "export" in front of the declaration:```
export LD_LIBRARY_PATH="/soft/diro/share/matlabr2009b/sys/os/glnxa64:/soft/diro/share/matlabr2009b/bin/glnxa64:/soft/diro/share/matlabr2009b/extern/lib/glnxa64:/soft/diro/share/matlabr2009b/runtime/glnxa64:/soft/diro/share/matlabr2009b/sys/java/jre/glnxa64/jre/lib/amd64/native_threads:/soft/diro/share/matlabr2009b/sys/java/jre/glnxa64/jre/lib/amd64/server:/soft/diro/share/matlabr2009b/sys/java/jre/glnxa64/jre/lib/amd64:/u/goodfeli/ffmpeg/libavfilter:/u/goodfeli/ffmpeg/libswscale:/u/goodfeli/ffmpeg/libavdevice:/u/goodfeli/ffmpeg/libavformat:/u/goodfeli/ffmpeg/libavcodec:/u/goodfeli/ffmpeg/libavutil:/opt/lisa/os/cuda/lib64:/opt/lisa/os/cuda/lib:/opt/lisa/byhost/lib:/opt/lisa/os/lib/vtk:/opt/lisa/os/lib/intelmkl/lib/32:/opt/lisa/os/lib:/opt/lisa/os/lib64:/usr/local/lib:/usr/lib64/atlas/::/opt/lisa/os/panda/lib:/opt/lisa/os/lib32:/opt/lisa/byhost/lib32"
``` and see if that helps.

Lloyd B.

---

### Post by stair314 on 2010-07-29
That's not the problem.
test.sh is a script that echoes LD_LIBRARY_PATH. Here's what happens when I run it from matlab.

>> system('bash test.sh')
/soft/diro/share/matlabr2009b/sys/os/glnxa64:/soft/diro/share/matlabr2009b/bin/glnxa64:/soft/diro/share/matlabr2009b/extern/lib/glnxa64:/soft/diro/share/matlabr2009b/runtime/glnxa64:/soft/diro/share/matlabr2009b/sys/java/jre/glnxa64/jre/lib/amd64/native_threads:/soft/diro/share/matlabr2009b/sys/java/jre/glnxa64/jre/lib/amd64/server:/soft/diro/share/matlabr2009b/sys/java/jre/glnxa64/jre/lib/amd64:/u/goodfeli/ffmpeg/libavfilter:/u/goodfeli/ffmpeg/libswscale:/u/goodfeli/ffmpeg/libavdevice:/u/goodfeli/ffmpeg/libavformat:/u/goodfeli/ffmpeg/libavcodec:/u/goodfeli/ffmpeg/libavutil:/opt/lisa/os/cuda/lib64:/opt/lisa/os/cuda/lib:/opt/lisa/byhost/lib:/opt/lisa/os/lib/vtk:/opt/lisa/os/lib/intelmkl/lib/32:/opt/lisa/os/lib:/opt/lisa/os/lib64:/usr/local/lib:/usr/lib64/atlas/::/opt/lisa/os/panda/lib:/opt/lisa/os/lib32:/opt/lisa/byhost/lib32

ans =

     0

This is not very surprising, since I am not relying on matlab to set LD_LIBRARY_PATH. The ffmpeg paths are set in my .bashrc.

---

