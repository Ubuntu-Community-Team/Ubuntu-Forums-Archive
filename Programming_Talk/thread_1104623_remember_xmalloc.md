---
title: "remember xmalloc?"
date: 2009-03-23
forum: Programming Talk
---

### Post by slavik on 2009-03-23
For those of you who remember an old discussion that was on this forum regarding a malloc wrapper that was part of a sound library called xmalloc which was exit if malloc returned NULL.

The following might be related (this is in jaunty)

```

slavik@slavik-laptop:~$ firefox
ALSA lib pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

ALSA lib pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

ALSA lib pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

ALSA lib pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

ALSA lib pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

ALSA lib pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

ALSA lib pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
firefox: pulse.c:200: pulse_new: Assertion `p->context' failed.
Aborted (core dumped)

```

---

