---
title: "ALSA programming"
date: 2011-12-24
forum: Programming Talk
---

### Post by perojok on 2011-12-24
hello, trying to write a program to record a sound stream from my audiocard(integrated realtek), briefly, without error processing it looks like:
```

#include <stdio.h>
#include <stdlib.h>
#include <alsa/asoundlib.h>
int main(int argc, char **argv) //argv[1] = "hw:0,0"
int i;  
int err;
long buf[128];
int exact_rate = 44100;
int time_s = 3;
static unsigned int channels = 2;		
snd_pcm_t *playback_handle;
snd_pcm_hw_params_t *hw_params;	
char *pcm_name = strdup("plughw:0,0");		
snd_pcm_t *capture_handle;	
	
snd_pcm_open (&capture_handle, argv[1], SND_PCM_STREAM_CAPTURE, 0);
snd_pcm_hw_params_malloc (&hw_params);
snd_pcm_hw_params_any (capture_handle, hw_params);
snd_pcm_hw_params_set_access(capture_handle,hw_params,SND_PCM_ACCESS_RW_INTERLEAVED));
nd_pcm_hw_params_set_format (capture_handle, hw_params, SND_PCM_FORMAT_S16_LE);
snd_pcm_hw_params_set_rate_near(capture_handle, hw_params, &exact_rate, 0);
snd_pcm_hw_params_set_channels (capture_handle, hw_params, channels);
snd_pcm_hw_params (capture_handle, hw_params);
	
snd_pcm_hw_params_free (hw_params);
snd_pcm_prepare (capture_handle);
	
	
int fd = open("file_rec", O_WRONLY), b;
if(!fd)
 printf("file didn't open\n");
		
		
for (i = 0; i < time_s*44100/128; i++)
	{			
		b = snd_pcm_readi(capture_handle, buf, 128);              
                write(fd,buf,128);
	}		
close(fd);	
snd_pcm_close (capture_handle);
snd_pcm_open(&playback_handle,pcm_name,SND_PCM_STREAM_PLAYBACK, 0);
snd_pcm_hw_params_malloc (&hw_params);
snd_pcm_hw_params_any (playback_handle, hw_params);
snd_pcm_hw_params_set_access (playback_handle, hw_params, SND_PCM_ACCESS_RW_INTERLEAVED);
snd_pcm_hw_params_set_format (playback_handle, hw_params, SND_PCM_FORMAT_S16_LE);		
snd_pcm_hw_params_set_rate_near(playback_handle, hw_params, &exact_rate,0);
snd_pcm_hw_params_set_channels (playback_handle, hw_params, 2);
snd_pcm_hw_params (playback_handle, hw_params);
	
snd_pcm_hw_params_free (hw_params);
snd_pcm_prepare (playback_handle);

fd = open("file_rec", O_RDONLY);
while((b=read(fd, buf, 128)) > 0)		
  snd_pcm_writei (playback_handle, buf, b);			
		
snd_pcm_close (playback_handle);
close(fd);
exit (0);
}
```
i'm recording a stream in standard audiorecording programm(from mic) and ones in my programm, and get in my programm sound much dirty with a lot of noises. can you help, what can i do??

---

### Post by perojok on 2011-12-26
?

---

### Post by Petrolea on 2011-12-26
Maybe your program plays raw input, but on computer it is a bit edited and that's why there's a difference? I'm just guessing, I don't know much about audio.

---

### Post by perojok on 2011-12-26
now i increased the buffer size and got enough good sound, but it consists from cycled segment from the beggining of the recording.. i think it's more clearer, maybe you notice some mistakes in write/read block?

---

### Post by Petrolea on 2011-12-26
> **perojok said:**
> now i increased the buffer size and got enough good sound, but it consists from cycled segment from the beggining of the recording.. i think it's more clearer, maybe you notice some mistakes in write/read block?

Can't tell anything about code being good or not because I have no idea what it does. But I can see you got some sound settings there, maybe try adjusting them?

---

