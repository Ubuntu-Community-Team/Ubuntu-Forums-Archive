---
title: "Audio-Related errors when compiling Torque Game Engine 1.5.0 in Hardy"
date: 2008-06-05
forum: Packaging and Compiling Programs
---

### Post by flintmecha on 2008-06-05
I'm trying to compile Torque Game Engine 1.5.0 in Ubuntu 8.04. I follow the steps located here: [http://eviwo.free.fr/torque/compile.html](http://eviwo.free.fr/torque/compile.html)

When I type make, everything seems to go well until I get some errors which appear to be audio-related.
```

Creating library out.GCC4.DEBUG/lungif_DEBUG.a
--> Compiling audio/audio.cc
In file included from ./game/gameBase.h:16,
                 from ./game/shapeBase.h:10,
                 from ./game/gameConnection.h:13,
                 from audio/audio.cc:11:
./dgl/gTexManager.h:428:26: warning: no newline at end of file
In file included from ./platform/platformAL.h:25,
                 from ./platform/platformAudio.h:16,
                 from ./audio/audio.h:10,
                 from audio/audio.cc:6:
../lib/openal/LINUX/al/al_func.h:18: error: ‘<anonymous>’ has incomplete type
../lib/openal/LINUX/al/al_func.h:18: error: invalid use of ‘ALvoid’
In file included from ./platform/platformAL.h:26,
                 from ./platform/platformAudio.h:16,
                 from ./audio/audio.h:10,
                 from audio/audio.cc:6:
../lib/openal/LINUX/al/alc_func.h:11: error: ‘<anonymous>’ has incomplete type
../lib/openal/LINUX/al/alc_func.h:11: error: invalid use of ‘ALCvoid’
audio/audio.cc: In function ‘bool cullSource(U32*, F32)’:
audio/audio.cc:252: error: too few arguments to function
audio/audio.cc: In function ‘AUDIOHANDLE alxCreateSource(const Audio::Description*, const char*, const MatrixF*, AudioSampleEnvironment*)’:
audio/audio.cc:731: error: too few arguments to function
audio/audio.cc: In function ‘void alxLoopingUpdate()’:
audio/audio.cc:1732: error: too few arguments to function
audio/audio.cc: In function ‘void alxStreamingUpdate()’:
audio/audio.cc:1833: error: too few arguments to function
audio/audio.cc: In function ‘bool Audio::OpenALInit()’:
audio/audio.cc:2414: error: too few arguments to function
audio/audio.cc:2419: error: too few arguments to function
audio/audio.cc:2441: error: too few arguments to function
make[1]: *** [out.GCC4.DEBUG/audio/audio.obj] Error 1
make: *** [default] Error 2

```

Anybody know what could be the cause of this?

---

### Post by jamincollins on 2008-06-23
The source code change necessary is documented [here]("http://www.garagegames.com/mg/forums/result.thread.php?qt=74990").  I don't believe the corrections can be published here due to the licensing agreement on the code.

---

