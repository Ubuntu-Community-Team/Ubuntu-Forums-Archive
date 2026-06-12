---
title: "No Default Input Device Available"
date: 2023-01-23
forum: New to Ubuntu
---

### Post by xileflirba on 2023-01-23
Hello! I'm a beginner in this area, and am a musician trying to run this code: [https://github.com/jdasam/online_amt](https://github.com/jdasam/online_amt)

 So, after installing everything on my Ubuntu terminal (WSL, 22.04, Python 3.7) (Windows 10, AMD Graphics Card, Intel CPU), and running any of the 2 versions of the code (run_on_web/plt.py), I come across this error
```
(onlineenv) felix@DESKTOP-UM451RI:/mnt/g/online_amt-master$ python run_on_web.pyhttp://127.0.0.1:5000/
 * Serving Flask app 'run_on_web' (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off
ALSA lib confmisc.c:855:(parse_card) cannot find card '0'
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_card_inum returned error: No such file or directory
ALSA lib confmisc.c:422:(snd_func_concat) error evaluating strings
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1334:(snd_func_refer) error evaluating name
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:5701:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM sysdefault
ALSA lib confmisc.c:855:(parse_card) cannot find card '0'
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_card_inum returned error: No such file or directory
ALSA lib confmisc.c:422:(snd_func_concat) error evaluating strings
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1334:(snd_func_refer) error evaluating name
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:5701:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM sysdefault
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.front
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround21
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround21
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround40
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround41
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround50
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.iec958
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.iec958
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.iec958
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib confmisc.c:855:(parse_card) cannot find card '0'
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_card_inum returned error: No such file or directory
ALSA lib confmisc.c:422:(snd_func_concat) error evaluating strings
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1334:(snd_func_refer) error evaluating name
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:5701:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:855:(parse_card) cannot find card '0'
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_card_inum returned error: No such file or directory
ALSA lib confmisc.c:422:(snd_func_concat) error evaluating strings
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1334:(snd_func_refer) error evaluating name
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:5701:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:855:(parse_card) cannot find card '0'
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_card_id returned error: No such file or directory
ALSA lib confmisc.c:422:(snd_func_concat) error evaluating strings
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1334:(snd_func_refer) error evaluating name
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:5701:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM dmix
Exception in thread <function get_buffer_and_transcribe at 0x7f9492235560>:
Traceback (most recent call last):
  File "/home/felix/miniconda3/envs/onlineenv/lib/python3.7/threading.py", line 926, in _bootstrap_inner
    self.run()
  File "/home/felix/miniconda3/envs/onlineenv/lib/python3.7/threading.py", line 870, in run
    self._target(*self._args, **self._kwargs)
  File "run_on_web.py", line 44, in get_buffer_and_transcribe
    CHANNELS = pyaudio.PyAudio().get_default_input_device_info()['maxInputChannels']
  File "/home/felix/miniconda3/envs/onlineenv/lib/python3.7/site-packages/pyaudio.py", line 949, in get_default_input_device_info
    device_index = pa.get_default_input_device()
OSError: No Default Input Device Available
```
And when listing the soundcards in ALSA, this happens:
```
(onlineenv) felix@DESKTOP-UM451RI:/mnt/g/online_amt-master$ aplay -l
aplay: device_list:274: no soundcards found...
```
The system requires a mic input, I'd appreciate knowing if that's possible with my setup, or any other alternative. Thanks! (please mind if this is not the correct forum to post)

---

### Post by MAFoElffen on 2023-01-24
WSL on Windows 10 is a terminal in a Virtual Machine. It is shielded from your hardware. That's not going to work. Even if you did turn on Hyper-V and install a full featured VM, you would have to figure out how to pass-through the sound card to the virtual machine... 

Have you thoght about maybe doing a dual boot to install Ubuntu as a dual boot alongside Windows?

---

### Post by MAFoElffen on 2023-01-24
Looking at the code... It just might run on a full fledged Virtual Machine... Hmmm. 

It's throwing that error here:
```

def get_buffer_and_transcribe(model, q):
    CHUNK = 512
    FORMAT = pyaudio.paInt16
    [COLOR=#ff0000]CHANNELS = pyaudio.PyAudio().get_default_input_device_info()['maxInputChannels'][/COLOR]
    RATE = 16000

    midiout = rtmidi.MidiOut()
    available_ports = midiout.get_ports()
    if available_ports:
        midiout.open_port(0)
    else:
        midiout.open_virtual_port("My virtual output")


```
Yes, it just might run on a full Virtual Machine version of Ubuntu without having to pass through anything except a microphone. Hmmm.

---

### Post by xileflirba on 2023-01-24
Yeah, that sounds reasonable. So is that the most practical way to get this going? I assume it's not possible to run it on Windows right?

---

### Post by MAFoElffen on 2023-01-26
You might be able to run it from a Virtual Machine from Windows: Hyper-V, VirtualBox, VMware Virtual Player... Wouldn't cost anything but time to try right? If it didn't run, then you would know that wouldn't work, then do an Install alongside Windows.

---

