---
title: "No sound output from my simple OpenAL application..."
date: 2010-06-06
forum: Programming Talk
---

### Post by memento-mori on 2010-06-06
Hello all,

I was attempting to write a mini OpenAL app on my 10.04 system performing basic playback and I've become a little stuck and was hoping one of you nice folks would be able to help out.

Short problem description:
--------------------------------
My application appears to run and terminate without problem but there appears to be no audio coming from my speakers.
--------------------------------

Longer version
--------------------------------
The data from the wave file I'm trying to play appears to read in OK (and has been shown to work previously when originally coded on a windows box a few years ago, so I've ruled this out as the problem).

The OpenAL device and context respectively open and create OK, the buffers and sources generate without error (and populate without error in the case of the buffer).

The device I'm opening is the default device which appears to be "OSS Software".
This is the only result from the following function call, which as I understand is meant to list all the devices present (separated by 0x00, and terminated by 0x00, 0x00):
**alcGetString( NULL, ALC_DEVICE_SPECIFIER )**

--------------------------------

I have a horrible feeling this will be a device related problem, and probably something to do with pulseaudio.

I've tried playing with /etc/libao.conf 
setting the content to: 
**default_driver=pulse**
instead of:
**default_driver=alsa**

and I've tried playing with /etc/openal/alsoft.conf
enabling the line:
**drivers = pulse,alsa,oss,solaris,dsound,winmm,port,wave**
and changing it to:
**drivers = pulse,alsa**

...with no luck unfortunately.

Although admittedly, I have no idea what these files configure directly, I read elsewhere that this solved a similar problem so I gave it a bash (and thought I'd mention it for some reason or other).


I've included the example's code block below for completeness - but this should mostly be OK.
```

int main( void )
{
	unsigned char * pBuffer = 0;
	unsigned char * pData = 0;
	unsigned int uiSize = 0;
	Wave::WaveFMT formatChunk;

	// pBuffer = data buffer for entire wav file
	// pData = pointer to the start of the audio data
	bool success = Wave::LoadWav( "test.wav", &pBuffer, uiSize, &pData, formatChunk );

	if( success )
	{
		const ALCchar *default_device;
		default_device = alcGetString(NULL,	ALC_DEFAULT_DEVICE_SPECIFIER);

		// start openal
		ALCdevice* pDevice = alcOpenDevice( default_device ); // first sound device
		if( pDevice == 0 )
			return 1;

		ALCcontext* pContext = alcCreateContext( pDevice, NULL );
		alcMakeContextCurrent( pContext );
		assert( ALC_NO_ERROR == alcGetError( pDevice ) );

		//
		// open the audio
		//

		// sound effect vars
		unsigned int	uiSource;

		// get the openAL format
		ALenum openAlFormat = AL_UNDETERMINED;

		if( formatChunk.channels == 1 )
		{
			if( formatChunk.bits_per_sample == 8 )
				openAlFormat = AL_FORMAT_MONO8;
			else if( formatChunk.bits_per_sample == 16 )
				openAlFormat = AL_FORMAT_MONO16;
		}
		else if( formatChunk.channels == 2 )
		{
			if( formatChunk.bits_per_sample == 8 )
				openAlFormat = AL_FORMAT_STEREO8;
			else if( formatChunk.bits_per_sample == 16 )
				openAlFormat = AL_FORMAT_STEREO16;
		}

		// a supported format was not acquired
		if( openAlFormat == AL_UNDETERMINED )
		{
			// only [mono,stereo] [8,16] bit sound effects are supported.
			Wave::FreeWavBuffer( &pBuffer );
			return 1;
		}


		// Create an OpenAL data buffer
		ALuint openal_buffer_id = 0;
		alGenBuffers( 1, &openal_buffer_id );

		assert( ALC_NO_ERROR == alcGetError( pDevice ) );

		// Add the data to the buffer
		alBufferData( openal_buffer_id, openAlFormat, (ALvoid*)(pData), (ALsizei)uiSize, (ALsizei)formatChunk.sample_rate );


		assert( ALC_NO_ERROR == alcGetError( pDevice ) );

		// we've copied the data - unload the buffer data
		Wave::FreeWavBuffer( &pBuffer );

		//
		// Play the audio
		//
		alGenSources( 1, &uiSource );

		assert( ALC_NO_ERROR == alcGetError( pDevice ) );

		alSourcei( uiSource, AL_BUFFER, openal_buffer_id );

		alSourcef( uiSource,	AL_GAIN,	1.0f );
		alSource3f( uiSource,	AL_POSITION,	0.f, 0.f, 0.f );
		alSource3f( uiSource,	AL_VELOCITY,	0.f, 0.f, 0.f );
		alSourcei( uiSource,	AL_LOOPING,	AL_TRUE );

		assert( ALC_NO_ERROR == alcGetError( pDevice ) );

		alSourcePlay( uiSource );

		assert( ALC_NO_ERROR == alcGetError( pDevice ) );

		sleep( 6 );

		alSourceStop( uiSource );
		alDeleteSources( 1, &uiSource );
		alDeleteBuffers( 1, &openal_buffer_id );

		alcMakeContextCurrent(NULL);
		alcDestroyContext(pContext);
		alcCloseDevice(pDevice);
	}

	return 0;
}

```

Any thoughts on what's wrong here would be gratefully received.

Many thanks in advance,

---

### Post by memento-mori on 2010-06-07
It appears that my OpenAL shared library was doing something it wasn't supposed to.

I replaced the OpenAL library with that of one supplied by the OpenAL Soft project and as-if by magic I have sound.

The source code and instructions can be found here: http://kcat.strangesoft.net/openal.htm

At time of writing the current version is 1.12.854 and removes the crackling sound experienced in previous versions (for me at least!).

Here's what you need to do to get it going (should anyone else fall into this situation):
> 
1. Download the current version of the source code from here: [http://kcat.strangesoft.net/openal.htm](http://kcat.strangesoft.net/openal.htm)
$ wget http://kcat.strangesoft.net/openal-releases/openal-soft-1.12.854.tar.bz2

2. Extract the archive.
$ tar -xvjf openal-soft-1.12.854.tar.bz2

3. Move to the cmake directory.
$ cd openal-soft-1.12.854/cmake

4. Run CMake from this directory (you may need to apt-get install cmake).
$ cmake ..

5. Make the project.
$ make

6. Make Install the project.
$ sudo make install

7. Remove exiting openal libraries/links from /usr/lib. (WARNING: You may want to back these up first!)
$ sudo rm /usr/lib/libopenal.so*

8. Create a link pointing to your shared library (which should be in /usr/local/lib/).
$ sudo ln -s /usr/local/lib/libopenal.so.1.12.854 /usr/lib/libopenal.so.1

9. Run your application.

10. Have a beer to celebrate your sound application once again working.


Hope this helps someone in the future.

All the best.

---

### Post by 3246251196 on 2012-12-04
> **memento-mori said:**
> It appears that my OpenAL shared library was doing something it wasn't supposed to.

I replaced the OpenAL library with that of one supplied by the OpenAL Soft project and as-if by magic I have sound.

The source code and instructions can be found here: [http://kcat.strangesoft.net/openal.htm](http://kcat.strangesoft.net/openal.htm)

At time of writing the current version is 1.12.854 and removes the crackling sound experienced in previous versions (for me at least!).

Here's what you need to do to get it going (should anyone else fall into this situation):


Hope this helps someone in the future.

All the best.

Hi, I have applied the latest version of the tar file. However, no such namespace: WAVE exists. Is this your own wrapper that is essentially calling the native LoadWav* function from installed OpenAL libraries?

I have tried to search for this namespace but I have not found anything. I think, for now, I will assume it is some sort of your own wrapper and use the standard library functions.

Further research suggests that this Wave belongs to something, if you could let me know, that would be excellent. I was using al and alut before, but I am having the same problem you were when you wrote this. I just am unsure where this Wave comes from.

Thanks.

---

