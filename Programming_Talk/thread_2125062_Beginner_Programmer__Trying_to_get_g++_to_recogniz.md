---
title: "Beginner Programmer : Trying to get g++ to recognize libraries for API"
date: 2013-03-12
forum: Programming Talk
---

### Post by epicbattle on 2013-03-12
Ubuntu 12.10
Can anyone explain how to tell g++ to recognize libraries from OpenSource API's or is it kind of a case by case basis?  

If it IS a case by case basis then here we go. (Just so you know I am brand spanking new at programming, and if you question what I am doing I can tell you that I probably don't know myself.)
I am trying to get an older API called PortAudio to work with g++. I think I've installed it properly, but I'm guessing its still operator error. I have been grabbing test code just to see if I can see if it will generate a sound. Here is one from portaudios site [http://www.portaudio.com/docs/v19-doxydocs/paex__saw_8c_source.html]("http://www.portaudio.com/docs/v19-doxydocs/paex__saw_8c_source.html")

```
#include <stdio.h>
   45 #include <math.h>
   46 #include "portaudio.h"
   47 #define NUM_SECONDS   (4)
   48 #define SAMPLE_RATE   (44100)
   49 
   50 typedef struct
   51 {
   52     float left_phase;
   53     float right_phase;
   54 }
   55 paTestData;
   56 
   57 /* This routine will be called by the PortAudio engine when audio is needed.
   58 ** It may called at interrupt level on some machines so don't do anything
   59 ** that could mess up the system like calling malloc() or free().
   60 */
   61 static int patestCallback( const void *inputBuffer, void *outputBuffer,
   62                            unsigned long framesPerBuffer,
   63                            const PaStreamCallbackTimeInfo* timeInfo,
   64                            PaStreamCallbackFlags statusFlags,
   65                            void *userData )
   66 {
   67     /* Cast data passed through stream to our structure. */
   68     paTestData *data = (paTestData*)userData;
   69     float *out = (float*)outputBuffer;
   70     unsigned int i;
   71     (void) inputBuffer; /* Prevent unused variable warning. */
   72 
   73     for( i=0; i<framesPerBuffer; i++ )
   74     {
   75         *out++ = data->left_phase;  /* left */
   76         *out++ = data->right_phase;  /* right */
   77         /* Generate simple sawtooth phaser that ranges between -1.0 and 1.0. */
   78         data->left_phase += 0.01f;
   79         /* When signal reaches top, drop back down. */
   80         if( data->left_phase >= 1.0f ) data->left_phase -= 2.0f;
   81         /* higher pitch so we can distinguish left and right. */
   82         data->right_phase += 0.03f;
   83         if( data->right_phase >= 1.0f ) data->right_phase -= 2.0f;
   84     }
   85     return 0;
   86 }
   87 
   88 /*******************************************************************/
   89 static paTestData data;
   90 int main(void);
   91 int main(void)
   92 {
   93     PaStream *stream;
   94     PaError err;
   95     
   96     printf("PortAudio Test: output sawtooth wave.\n");
   97     /* Initialize our data for use by callback. */
   98     data.left_phase = data.right_phase = 0.0;
   99     /* Initialize library before making any other calls. */
  100     err = Pa_Initialize();
  101     if( err != paNoError ) goto error;
  102     
  103     /* Open an audio I/O stream. */
  104     err = Pa_OpenDefaultStream( &stream,
  105                                 0,          /* no input channels */
  106                                 2,          /* stereo output */
  107                                 paFloat32,  /* 32 bit floating point output */
  108                                 SAMPLE_RATE,
  109                                 256,        /* frames per buffer */
  110                                 patestCallback,
  111                                 &data );
  112     if( err != paNoError ) goto error;
  113 
  114     err = Pa_StartStream( stream );
  115     if( err != paNoError ) goto error;
  116 
  117     /* Sleep for several seconds. */
  118     Pa_Sleep(NUM_SECONDS*1000);
  119 
  120     err = Pa_StopStream( stream );
  121     if( err != paNoError ) goto error;
  122     err = Pa_CloseStream( stream );
  123     if( err != paNoError ) goto error;
  124     Pa_Terminate();
  125     printf("Test finished.\n");
  126     return err;
  127 error:
  128     Pa_Terminate();
  129     fprintf( stderr, "An error occured while using the portaudio stream\n" );
  130     fprintf( stderr, "Error number: %d\n", err );
  131     fprintf( stderr, "Error message: %s\n", Pa_GetErrorText( err ) );
  132     return err;
  133 } 
```



This results in the error

```
Documents$ g++ portaudio_sound_test.cpp
portaudio_sound_test.cpp:40:4: error: stray ‘#’ in program
portaudio_sound_test.cpp:41:4: error: stray ‘#’ in program
portaudio_sound_test.cpp:42:4: error: stray ‘#’ in program
portaudio_sound_test.cpp:43:4: error: stray ‘#’ in program
portaudio_sound_test.cpp:44:4: error: stray ‘#’ in program
portaudio_sound_test.cpp:1:5: error: expected unqualified-id before numeric constant
portaudio_sound_test.cpp:51:4: error: expected unqualified-id before numeric constant
portaudio_sound_test.cpp:52:4: error: expected unqualified-id before numeric constant
```

Another test code comes from 

```
include <stdio.h>
#include <math.h>
#include "portaudio.h"

#define NUM_SECONDS   (5)
#define SAMPLE_RATE   (44100)
#define FRAMES_PER_BUFFER  (64)

#ifndef M_PI
#define M_PI  (3.14159265)
#endif

#define TABLE_SIZE   (200)
typedef struct
{
    float sine[TABLE_SIZE];
    int left_phase;
    int right_phase;
    char message[20];
}
paTestData;

/* This routine will be called by the PortAudio engine when audio is needed.
** It may called at interrupt level on some machines so don't do anything
** that could mess up the system like calling malloc() or free().
*/
static int patestCallback( const void *inputBuffer, void *outputBuffer,
                            unsigned long framesPerBuffer,
                            const PaStreamCallbackTimeInfo* timeInfo,
                            PaStreamCallbackFlags statusFlags,
                            void *userData )
{
    paTestData *data = (paTestData*)userData;
    float *out = (float*)outputBuffer;
    unsigned long i;

    (void) timeInfo; /* Prevent unused variable warnings. */
    (void) statusFlags;
    (void) inputBuffer;

    for( i=0; i<framesPerBuffer; i++ )
    {
        *out++ = data->sine[data->left_phase];  /* left */
        *out++ = data->sine[data->right_phase];  /* right */
        data->left_phase += 1;
        if( data->left_phase >= TABLE_SIZE ) data->left_phase -= TABLE_SIZE;
        data->right_phase += 3; /* higher pitch so we can distinguish left and right. */
        if( data->right_phase >= TABLE_SIZE ) data->right_phase -= TABLE_SIZE;
    }

    return paContinue;
}

/*
 * This routine is called by portaudio when playback is done.
 */
static void StreamFinished( void* userData )
{
   paTestData *data = (paTestData *) userData;
   printf( "Stream Completed: %s\n", data->message );
}

/*******************************************************************/
int main(void);
int main(void)
{
    PaStreamParameters outputParameters;
    PaStream *stream;
    PaError err;
    paTestData data;
    int i;


    printf("PortAudio Test: output sine wave. SR = %d, BufSize = %d\n", SAMPLE_RATE, FRAMES_PER_BUFFER);

    /* initialise sinusoidal wavetable */
    for( i=0; i<TABLE_SIZE; i++ )
    {
        data.sine[i] = (float) sin( ((double)i/(double)TABLE_SIZE) * M_PI * 2. );
    }
    data.left_phase = data.right_phase = 0;

    err = Pa_Initialize();
    if( err != paNoError ) goto error;

    outputParameters.device = Pa_GetDefaultOutputDevice(); /* default output device */
    if (outputParameters.device == paNoDevice) {
      fprintf(stderr,"Error: No default output device.\n");
      goto error;
    }
    outputParameters.channelCount = 2;       /* stereo output */
    outputParameters.sampleFormat = paFloat32; /* 32 bit floating point output */
    outputParameters.suggestedLatency = Pa_GetDeviceInfo( outputParameters.device )->defaultLowOutputLatency;
    outputParameters.hostApiSpecificStreamInfo = NULL;

    err = Pa_OpenStream(
              &stream,
              NULL, /* no input */
              &outputParameters,
              SAMPLE_RATE,
              FRAMES_PER_BUFFER,
              paClipOff,      /* we won't output out of range samples so don't bother clipping them */
              patestCallback,
              &data );
    if( err != paNoError ) goto error;

    sprintf( data.message, "No Message" );
    err = Pa_SetStreamFinishedCallback( stream, &StreamFinished );
    if( err != paNoError ) goto error;

    err = Pa_StartStream( stream );
    if( err != paNoError ) goto error;

    printf("Play for %d seconds.\n", NUM_SECONDS );
    Pa_Sleep( NUM_SECONDS * 1000 );

    err = Pa_StopStream( stream );
    if( err != paNoError ) goto error;

    err = Pa_CloseStream( stream );
    if( err != paNoError ) goto error;

    Pa_Terminate();
    printf("Test finished.\n");

    return err;
error:
    Pa_Terminate();
    fprintf( stderr, "An error occured while using the portaudio stream\n" );
    fprintf( stderr, "Error number: %d\n", err );
    fprintf( stderr, "Error message: %s\n", Pa_GetErrorText( err ) );
    return err;
}

```

I know, This is this the biggest test code ever.

Which gives the error 

```
$ g++ soundtest.cpp
/tmp/ccfAgaEH.o: In function `main':
soundtest.cpp:(.text+0x1f3): undefined reference to `Pa_Initialize'
soundtest.cpp:(.text+0x20b): undefined reference to `Pa_GetDefaultOutputDevice'
soundtest.cpp:(.text+0x261): undefined reference to `Pa_GetDeviceInfo'
soundtest.cpp:(.text+0x2c4): undefined reference to `Pa_OpenStream'
soundtest.cpp:(.text+0x30f): undefined reference to `Pa_SetStreamFinishedCallback'
soundtest.cpp:(.text+0x331): undefined reference to `Pa_StartStream'
soundtest.cpp:(.text+0x35e): undefined reference to `Pa_Sleep'
soundtest.cpp:(.text+0x36d): undefined reference to `Pa_StopStream'
soundtest.cpp:(.text+0x38b): undefined reference to `Pa_CloseStream'
soundtest.cpp:(.text+0x39f): undefined reference to `Pa_Terminate'
soundtest.cpp:(.text+0x3c9): undefined reference to `Pa_Terminate'
soundtest.cpp:(.text+0x413): undefined reference to `Pa_GetErrorText'
collect2: error: ld returned 1 exit status

```

Thank you for your patience and assistance in advance.

---

### Post by steeldriver on 2013-03-12
In the first case it looks like you copy-pasted from the web page without removing the line numbers? 

In the other cases, yes to get rid of the 'undefined reference' errors you will at a minimum need to specify the library and any subsidiary libraries on which it depends on your g++ command line (or on the link line if you split the compile and link phases). Depending how/where the libraries and header files were installed you may also need include path (-I) and library path (-L) directives

I don't know anything about the library you are trying to use but did you read the usage examples? That would be a good start [although caveat: the suggested library link order is probably going to need adjusting for the current g++ way of resolving dependencies]

[http://www.portaudio.com/docs/v19-doxydocs/compile_linux.html](http://www.portaudio.com/docs/v19-doxydocs/compile_linux.html)

---

