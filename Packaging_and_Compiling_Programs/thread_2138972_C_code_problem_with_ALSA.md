---
title: "C code problem with ALSA"
date: 2013-04-25
forum: Packaging and Compiling Programs
---

### Post by fatih6761 on 2013-04-25
I wrote a program for simply use of ALSA on Kubuntu 13.04beta2 (raring) system. The code is:
```

#include <stdio.h>
#include <alsa/asoundlib.h>


int main() {
  int val;


  printf("ALSA library version: %s\n",
          SND_LIB_VERSION_STR);


  printf("\nPCM stream types:\n");
  for (val = 0; val <= SND_PCM_STREAM_LAST; val++)
    printf("  %s\n",
      snd_pcm_stream_name((snd_pcm_stream_t)val));


  printf("\nPCM access types:\n");
  for (val = 0; val <= SND_PCM_ACCESS_LAST; val++)
    printf("  %s\n",
      snd_pcm_access_name((snd_pcm_access_t)val));


  printf("\nPCM formats:\n");
  for (val = 0; val <= SND_PCM_FORMAT_LAST; val++)
    if (snd_pcm_format_name((snd_pcm_format_t)val)
      != NULL)
      printf("  %s (%s)\n",
        snd_pcm_format_name((snd_pcm_format_t)val),
        snd_pcm_format_description(
                           (snd_pcm_format_t)val));


  printf("\nPCM subformats:\n");
  for (val = 0; val <= SND_PCM_SUBFORMAT_LAST;
       val++)
    printf("  %s (%s)\n",
      snd_pcm_subformat_name((
        snd_pcm_subformat_t)val),
      snd_pcm_subformat_description((
        snd_pcm_subformat_t)val));


  printf("\nPCM states:\n");
  for (val = 0; val <= SND_PCM_STATE_LAST; val++)
    printf("  %s\n",
           snd_pcm_state_name((snd_pcm_state_t)val));


  return 0;
}

```
Very simple.. Like examples in doc. But i can't be able to compile this program. I also added -lasound flag to gcc.
gcc output:
```

fatih@fatih-KUBUNTU:~$ gcc -lasound -o tune tune.c
/tmp/ccd2xSUq.o: In function `main':
tune.c:(.text+0x36): undefined reference to `snd_pcm_stream_name'
tune.c:(.text+0x6f): undefined reference to `snd_pcm_access_name'
tune.c:(.text+0xa8): undefined reference to `snd_pcm_format_name'
tune.c:(.text+0xb7): undefined reference to `snd_pcm_format_description'
tune.c:(.text+0xc4): undefined reference to `snd_pcm_format_name'
tune.c:(.text+0x100): undefined reference to `snd_pcm_subformat_description'
tune.c:(.text+0x10d): undefined reference to `snd_pcm_subformat_name'
tune.c:(.text+0x149): undefined reference to `snd_pcm_state_name'
collect2: hata: ld ç&#305;k&#305;&#351; durumu 1 ile döndü


```
Problem is at the linker section. What's the problem? How can i compile with ALSA?
(sorry for bad english)

---

### Post by steeldriver on 2013-04-25
the resolve order is important - try

```
gcc -o tune **tune.c -lasound**
```

---

### Post by fatih6761 on 2013-04-26
Thank you @steeldriver. Problem solved...Thread can be closed...

---

