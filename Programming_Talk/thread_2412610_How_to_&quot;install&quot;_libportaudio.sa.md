---
title: "How to &quot;install&quot; libportaudio.sa"
date: 2019-02-15
forum: Programming Talk
---

### Post by jorxster on 2019-02-15
Hi fellow Ubuntu devs,

I have a bit of a newb question --
I have a Python module called "pyaudio" which is meant to wrap "portaudio".
Now, "apt-get install portaudio" is not sufficient for me, I had to build portaudio in order to have ALSA support.

So I did configure && make. Now what?
Documentation doesn't tell me how to "install" it at the operating system level. How do I replace the installed 'portaudio19-dev' package with my newly compiled binaries?

cheers,
Jordan

A little more background. 
PyAudio is dependent on PortAudio:

[FONT=monospace][COLOR=#000000]Python 3.6.8 |Anaconda, Inc.| (default, Dec 30 2018, 01:22:34)  [/COLOR]
[GCC 7.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import pyaudio
>>> pyaudio
<module 'pyaudio' from '/home/jorxster/anaconda3/envs/tf-gpu/lib/python3.6/site-packages/pyaudio.py'>

[/FONT]
which uses a cpython so of portaudio:
[FONT=monospace][COLOR=#000000]>>> import _portaudio[/COLOR]
>>> _portaudio        
<module '_portaudio' from '/home/jorxster/anaconda3/envs/tf-gpu/lib/python3.6/site-packages/_portaudio.cpython-36m-x86_64-linux-gnu.so'>

This _portaudio cpython file has nothing to do with the portaudio I have compiled separately with ALSA support. But how do I get my compiled binaries to replace my system portaudio?[/FONT]

---

### Post by Claus7 on 2019-02-15
Hello,

if the previous commands you issued were successful and gave no errors, then 
sudo make install 
should work.

Regards!

---

### Post by jorxster on 2019-02-20
Thank you so much Claus7, can't believe it was that simple!

configure,
make,
make install

success!

---

