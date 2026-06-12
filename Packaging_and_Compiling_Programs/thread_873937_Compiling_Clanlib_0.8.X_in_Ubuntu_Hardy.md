---
title: "Compiling Clanlib 0.8.X in Ubuntu Hardy"
date: 2008-07-29
forum: Packaging and Compiling Programs
---

### Post by Neon Lemmy Koopa on 2008-07-29
Heres my story.

I want to use some game development stuff in Ubuntu, and the program I want requires ClanLib 0.8.x to be installed.  Upon checking the repositories, those clanlibs were for version 0.6.  now the only releases I could find on the Clanlib site were 0.8.1 and 0.8.0.  Did them both.  I got through the ./configure part quite fine.  But when I issue the make command, I end up with the following output for both versions.

```
display_mode.cpp:33:38: error: X11/extensions/xf86vmode.h: No such file or directory
display_mode.cpp: In static member function 'static std::vector<CL_DisplayMode, std::allocator<CL_DisplayMode> >& CL_DisplayMode::get_display_modes()':
display_mode.cpp:117: error: 'XF86VidModeQueryExtension' was not declared in this scope
display_mode.cpp:121: error: 'XF86VidModeModeInfo' was not declared in this scope
display_mode.cpp:121: error: 'vmodes' was not declared in this scope
display_mode.cpp:124: error: 'XF86VidModeGetAllModeLines' was not declared in this scope
make[2]: *** [display_mode.lo] Error 1
make[2]: Leaving directory `/home/sam/Downloads/ClanLib-0.8.0/Sources/Display'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sam/Downloads/ClanLib-0.8.0/Sources'
make: *** [all-recursive] Error 1

```

I have tried other methods I found on the forum, but to no avail.  If someone could please help me?

---

### Post by Neon Lemmy Koopa on 2008-07-29
Okay so I managed to figure out how to get past that part. Apparently there were some headers missing, so  I needed to install the libxxf86vm-dev package.  did that fixed that.  Now theres another wall.  heres the output from the make command.
```
Unix/soundoutput_alsa.h:37:29: error: alsa/asoundlib.h: No such file or directory
In file included from soundoutput.cpp:43:
Unix/soundoutput_alsa.h:49: error: ISO C++ forbids declaration of 'snd_pcm_t' with no type
Unix/soundoutput_alsa.h:49: error: expected ';' before '*' token
Unix/soundoutput_alsa.h:50: error: 'snd_pcm_uframes_t' does not name a type
Unix/soundoutput_alsa.h:51: error: 'snd_pcm_uframes_t' does not name a type
soundoutput.cpp: In constructor 'CL_SoundOutput::CL_SoundOutput(const CL_SoundOutput_Description&)':
soundoutput.cpp:73: error: 'class CL_SoundOutput_alsa' has no member named 'handle'
make[2]: *** [soundoutput.lo] Error 1
make[2]: Leaving directory `/home/sam/Downloads/ClanLib-0.8.1/Sources/Sound'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sam/Downloads/ClanLib-0.8.1/Sources'
make: *** [all-recursive] Error 1

```this looks like an error with alsa.
Someone please help me with this!

---

### Post by Neon Lemmy Koopa on 2008-07-29
lol I fixed that too.  There were some alsa headers missing.  Basically what I did is searched "alsa" in synaptic and checked off any package listed with "-dev" at the end and an ubuntu logo in front of it.

I did this myself, but I request that this be left here for others that may encounter this problem!

---

