---
title: "OpenAL"
date: 2012-12-04
forum: Programming Talk
---

### Post by 3246251196 on 2012-12-04
Hey.
 
So, to be applied to some openGL experimentation is some openAL. I have tested out some sample programs to ensure that stand-alone-pure-openAL applications are working before adding such a module into my openGL application.
 
So far I have not been able to detect output in any of my attempts at running openAL.
 
I am aware that I am using a deprecated function (as in the source code):
```
alutLoadWAVFile((ALbyte*)"sound1.wav",&alFormatBuffer, &alBuffer,&alBufferLen, &alFreqBuffer, &alLoop);
```From researching I have heard that this should not hinder the program. Would anyone agree with that?
 
Also, I have tested the return value of:
```
alcGetString( NULL, ALC_DEVICE_SPECIFIER )
```Which returns:
```
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
PulseAudio Default
```The code for the entire application:
```
#include<iostream>
#include<AL/al.h>
#include<AL/alc.h>
#include<AL/alut.h>
 
int main()
{
    std::cout << alcGetString( NULL, ALC_DEVICE_SPECIFIER ) << std::endl;
    ALCcontext *context;
    ALCdevice *device;
 
    device = alcOpenDevice(NULL/*, ALC_DEFAULT_DEVICE_SPECIFIER*/);
    if (device == NULL)
    {
        // Handle Exception
       std::cout << "exception opening device " << std::endl;
    }
 
    //Create a context
    context=alcCreateContext(device,NULL);
 
    //Set active context
    alcMakeContextCurrent(context);
 
    // Clear Error Code
    alGetError();
 
    //char*           alBuffer;       //data for the buffer
    ALvoid*         alBuffer;
    ALenum          alFormatBuffer; //buffer format
    ALsizei         alFreqBuffer;   //frequency
    ALsizei         alBufferLen;    //bit depth
    ALboolean       alLoop;         //loop
    unsigned int    alSource;       //source
    unsigned int    alSampleSet;
 
    //load the wave file
    alutLoadWAVFile((ALbyte*)"sound1.wav",&alFormatBuffer, &alBuffer,&alBufferLen, &alFreqBuffer, &alLoop);
 
    //create a source
    alGenSources(1, &alSource);
 
    //create  buffer
    alGenBuffers(1, &alSampleSet);
 
    //put the data into our sampleset buffer
    alBufferData(alSampleSet, alFormatBuffer, alBuffer, alBufferLen, alFreqBuffer);
 
    //assign the buffer to this source
    alSourcei(alSource, AL_BUFFER, alSampleSet);
 
    //release the data
    alutUnloadWAV(alFormatBuffer, alBuffer, alBufferLen, alFreqBuffer); 
 
    //
    alSourcei(alSource,AL_LOOPING,AL_TRUE);
 
    //play
    alSourcePlay(alSource);
 
    //to stop
    alSourceStop(alSource);
 
    //
    alDeleteSources(1,&alSource);
 
    //delete our buffer
    alDeleteBuffers(1,&alSampleSet);
 
    context=alcGetCurrentContext();
 
    //Get device for active context
    device=alcGetContextsDevice(context);
 
    //Disable context
    alcMakeContextCurrent(NULL);
 
    //Release context(s)
    alcDestroyContext(context);
 
    //Close device
    alcCloseDevice(device);
 
    std::cout << "NO ERRORS" << std::endl;
    return 0;
}
```I have the sound1.wav file in the pwd, and it does work with Totem.
 
One thing I will mention is that, sometime ago, my sound card was problematic, and a on the rare side. Though, as Ubuntu's version has continued, the problem does not now exist.
 
I would guess, though, that a lot of things I am using on this Ubuntu OS are using openAL, and so far I have never had any sound issues.
 
Is anyone able to tell me what the possible issue is? I have tried searching for information on this issue myself.
 
Thank you,
324.
 
EDIT FURTHER: While I wait for peoples' responses, I will firstly insert a sleep between start and stop and then I might try [http://ubuntuforums.org/showthread.php?t=1503402](http://ubuntuforums.org/showthread.php?t=1503402) (which does not include using ALUT, I have noticed)
 
EDIT FURTHER: I have tried the suggestions in the thread posted above ([http://ubuntuforums.org/showthread.php?t=1503402](http://ubuntuforums.org/showthread.php?t=1503402)), but where this Wave namespace and its WaveFMT structure comes from I am not sure. The closest thing I have found is the function SDL_LoadWav(...)

---

### Post by 3246251196 on 2012-12-06
> **3246251196 said:**
> Hey.

So, to be applied to some openGL experimentation is some openAL. I have tested out some sample programs to ensure that stand-alone-pure-openAL applications are working before adding such a module into my openGL application.

So far I have not been able to detect output in any of my attempts at running openAL.

I am aware that I am using a deprecated function (as in the source code):
```
alutLoadWAVFile((ALbyte*)"sound1.wav",&alFormatBuffer, &alBuffer,&alBufferLen, &alFreqBuffer, &alLoop);
```From researching I have heard that this should not hinder the program. Would anyone agree with that?

Also, I have tested the return value of:
```
alcGetString( NULL, ALC_DEVICE_SPECIFIER )
```Which returns:
```
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
PulseAudio Default
```The code for the entire application, which was a sample code:
```
#include<iostream>
#include<AL/al.h>
#include<AL/alc.h>
#include<AL/alut.h>

int main()
{
    std::cout << alcGetString( NULL, ALC_DEVICE_SPECIFIER ) << std::endl;
    ALCcontext *context;
    ALCdevice *device;

    device = alcOpenDevice(NULL/*, ALC_DEFAULT_DEVICE_SPECIFIER*/);
    if (device == NULL)
    {
        // Handle Exception
       std::cout << "exception opening device " << std::endl;
    }

    //Create a context
    context=alcCreateContext(device,NULL);

    //Set active context
    alcMakeContextCurrent(context);

    // Clear Error Code
    alGetError();

    //char*           alBuffer;       //data for the buffer
    ALvoid*         alBuffer;
    ALenum          alFormatBuffer; //buffer format
    ALsizei         alFreqBuffer;   //frequency
    ALsizei         alBufferLen;    //bit depth
    ALboolean       alLoop;         //loop
    unsigned int    alSource;       //source
    unsigned int    alSampleSet;

    //load the wave file
    alutLoadWAVFile((ALbyte*)"sound1.wav",&alFormatBuffer, &alBuffer,&alBufferLen, &alFreqBuffer, &alLoop);

    //create a source
    alGenSources(1, &alSource);

    //create  buffer
    alGenBuffers(1, &alSampleSet);

    //put the data into our sampleset buffer
    alBufferData(alSampleSet, alFormatBuffer, alBuffer, alBufferLen, alFreqBuffer);

    //assign the buffer to this source
    alSourcei(alSource, AL_BUFFER, alSampleSet);

    //release the data
    alutUnloadWAV(alFormatBuffer, alBuffer, alBufferLen, alFreqBuffer); 

    //
    alSourcei(alSource,AL_LOOPING,AL_TRUE);

    //play
    alSourcePlay(alSource);

    //to stop
    alSourceStop(alSource);

    //
    alDeleteSources(1,&alSource);

    //delete our buffer
    alDeleteBuffers(1,&alSampleSet);

    context=alcGetCurrentContext();

    //Get device for active context
    device=alcGetContextsDevice(context);

    //Disable context
    alcMakeContextCurrent(NULL);

    //Release context(s)
    alcDestroyContext(context);

    //Close device
    alcCloseDevice(device);

    std::cout << "NO ERRORS" << std::endl;
    return 0;
}
```I have the sound1.wav file in the pwd, and it does work.

One thing I will mention is that, sometime ago, my sound card was problematic, and a on the rare side. Though, as Ubuntu's version has continued, the problem does not now exist.

I would guess, though, that a lot of things I am using on this Ubuntu OS are using openAL, and so far I have never had any sound issues.

Is anyone able to tell me what the possible issue is? I have tried searching for information on this issue myself.

Thank you,
324.

EDIT FURTHER: While I wait for peoples' responses, I will firstly insert a sleep between start and stop and then I might try [http://ubuntuforums.org/showthread.php?t=1503402](http://ubuntuforums.org/showthread.php?t=1503402) (which does not include using ALUT, I have noticed)

EDIT FURTHER: I have tried the suggestions in the thread posted above ([http://ubuntuforums.org/showthread.php?t=1503402](http://ubuntuforums.org/showthread.php?t=1503402)), but where this Wave namespace and its WaveFMT structure comes from I am not sure. The closest thing I have found is the function SDL_LoadWav(...)

So, I have updated the openal libraries - installed from openal-soft.

```
std::cout << alcGetString( NULL, ALC_DEVICE_SPECIFIER ) << std::endl;
    ALCcontext *context;
    ALCdevice *device;

    device = alcOpenDevice(alcGetString( NULL, ALC_DEVICE_SPECIFIER ));
```the output of alcGetString is now:
```
OpenAL Soft
```this time I try to pass in the return value into opendevice, alas- there is still no sound.

Please, anyone with experience of openal soft , or with an eye for a programming error can help me with this one?

I just want to play a simple wav file using al and alut.

Edit: I did include a 5 second loop between start and stop of source.

**================================================================================**
EDIT::::: Okay, the program does work when I tested it out with a free downloaded WAV file from the internet.

So, sound1.wav whose binary begins: RIFF$^@ÿ^?WAVEfmt

And daddy.wav whose binary begins: RIFF&<8c>^@^@WAVEfmt

sound1 does not work (it was recorded using Ubuntu's Sound Recorder program),
daddy does work.

Can anyone expand on why this is the case?

Thanks.

---

### Post by 3246251196 on 2012-12-06
I will mark this thread as solved. In summary, ALUT is limited to only opening certain types of WAV files.

---

