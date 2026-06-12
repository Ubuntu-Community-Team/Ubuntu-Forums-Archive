---
title: "Confused about DMA buffers [C]"
date: 2009-03-13
forum: Programming Talk
---

### Post by roccivic on 2009-03-13
Hi all,
First off thanks for taking the time to help me out ;)

I'm writing a program that should read from /dev/dsp in C.

Some of the code:

```

/* open /dev/dsp */

#define CHANNELS 2  /* 2 = stereo */
#define SIZE 8      /* sample size: 8 bits */

int sc_open() {
	int		ffd = 0;
	int		rate = 44100;
	int		arg;
	int		status;


	ffd = open("/dev/dsp", O_RDONLY);
	if (ffd < 0) {
		perror("open of /dev/dsp failed");
		exit(1);
	}

	/* set sampling parameters */
	arg = SIZE;	   /* sample size */
	status = ioctl(ffd, SOUND_PCM_WRITE_BITS, &arg);
	if (status == -1)
		perror("SOUND_PCM_WRITE_BITS ioctl failed");
	if (arg != SIZE)
		perror("unable to set sample size");

	arg = CHANNELS;  /* mono or stereo */
	status = ioctl(ffd, SOUND_PCM_WRITE_CHANNELS, &arg);
	if (status == -1)
		perror("SOUND_PCM_WRITE_CHANNELS ioctl failed");
	if (arg != CHANNELS)
		perror("unable to set number of channels");

	arg = rate;	   /* sampling rate */
	status = ioctl(ffd, SOUND_PCM_WRITE_RATE, &rate);
	if (status == -1)
		perror("SOUND_PCM_WRITE_WRITE ioctl failed");

	return ffd;
}
```

```
/* create stream */
FILE*	sc_open_stream ( int ffd ){
	FILE		*fd;
	fd = fdopen(ffd, "r");
	if (fd < 0) {
		perror("Failed to connect stream to /dev/dsp");
		exit(1);
	}
	return	fd;
}
```

And that's where I get confused. I start reading from **fd** using **fgetc** and get a byte at a time. But between one reading and another I need to do some operations (like applying a simple software low pass filter) until I got 1000 samples. I know I could just read all samples and then do the post processing, but I would like all to be as close to real time as possible.

I guess I could do some multithreading, one thread could read /dev/dsp and store the samples in a buffer while the another thread could do the processing. But it doesn't sound like a good solution, because if the CPU will get busy the first thread might miss some samples and mess up my data.

I thought DMA buffers are there exactly for the purpose of buffering data, so that an application can read the data at it's own speed without worrying about missing sample, but I have no clue how to set this up and use it.

Many thanks to everyone.

Rouslan

---

### Post by the_unforgiven on 2009-03-13
Do you really need to manually handle /dev/dsp?
Why not use alsa-lib?

If it's for some educational purpose or something that alsa-lib doesn't provide, then I have nothing more to say. But, I doubt there is anything that alsa-lib doesn't provide. You can use it as a fairly low level API and it's the standard Linux audio subsystem.

For more details:
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

API:
[http://www.alsa-project.org/main/index.php/ALSA_Library_API](http://www.alsa-project.org/main/index.php/ALSA_Library_API)

Couple of tutorial links:
[http://equalarea.com/paul/alsa-audio.html](http://equalarea.com/paul/alsa-audio.html)
[http://www.suse.de/~mana/alsa090_howto.html](http://www.suse.de/~mana/alsa090_howto.html)

Feel free to disagree :)

---

### Post by roccivic on 2009-03-13
Thanks, I'll look into it. It might just be what I'm looking for.

One more question:
Can an application that uses libalsa be ported to windows with cygwin?

Many thanks,
Rouslan

---

### Post by the_unforgiven on 2009-03-13
> **roccivic said:**
> 
One more question:
Can an application that uses libalsa be ported to windows with cygwin?

Unfortunately, no.
ALSA stands for Advanced Linux Sound Architecture - it's specific to Linux.

However, if you want to write portable code, you might want to take a look at SDL:
[http://www.libsdl.org](http://www.libsdl.org)

It's a cross-platform multimedia programming library - includes various subsystems like video, audio, OpenGL etc.

On linux, it will use whatever is available to talk to the audio h/w - it's completely customizable.
On windows, it will use the native Win32 API (or DirectX - I'm not sure) for audio - so, you don't need an emulation like cygwin for it.

Here are some links for getting SDL working on Windows:
[http://www.gamedev.net/reference/programming/features/sdl1/](http://www.gamedev.net/reference/programming/features/sdl1/)
[http://www.gamedev.net/reference/programming/features/sdl2/](http://www.gamedev.net/reference/programming/features/sdl2/)

There is also JACK:
[http://jackaudio.org/](http://jackaudio.org/)

which is cross-platform. But, I believe, it requires POSIX API (cygwin) :(.

HTH ;)

---

