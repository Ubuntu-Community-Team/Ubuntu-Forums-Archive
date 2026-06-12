---
title: "python plots"
date: 2010-03-24
forum: Programming Talk
---

### Post by MindSz on 2010-03-24
Hey all,


I'm completely new to python (I'm more into C) but I came across a small python program that can help me design filters, so I thought I'd give it a try.

Now the problem is that I don't know how to get the pictures to show on the screen when I run the program.

Here's the code:

```
import scipy.signal as signal
from pylab import *

def mfreqz(b,a=1):
    w,h = signal.freqz(b,a)
    h_dB = 20 * log10 (abs(h))
    subplot(211)
    plot(w/max(w),h_dB)
    ylim(-150, 5)
    ylabel('Magnitude (db)') 
    xlabel(r'Normalized Frequency (x$\pi$rad/sample)')
    title(r'Frequency response')
    subplot(212)
    h_Phase = unwrap(arctan2(imag(h),real(h)))
    plot(w/max(w),h_Phase)
    ylabel('Phase (radians)') 
    xlabel(r'Normalized Frequency (x$\pi$rad/sample)')
    title(r'Phase response')
    subplots_adjust(hspace=0.5)

def impz(b,a=1):
        impulse = repeat(0.,50); impulse[0] =1.
        x = arange(0,50)
        response = signal.lfilter(b,a,impulse)
        subplot(211)
        stem(x, response)
        ylabel('Amplitude') 
        xlabel(r'n (samples)')
        title(r'Impulse response')
        subplot(212)
        step = cumsum(response)
        stem(x, step)
        ylabel('Amplitude') 
        xlabel(r'n (samples)')
        title(r'Step response')
        subplots_adjust(hspace=0.5)
        
#Bandpass IIR
b,a = signal.iirdesign(wp = [0.05, 0.3], ws= [0.02, 0.35], gstop= 60, gpass=1, ftype='ellip')
mfreqz(b,a)
figure(2)
impz(b,a)
```

I've already installed pylab and all that. I can see the program is running, but I think I'm missing something to make the thing show the plots.

Any help is greatly appreciated.

---

### Post by goseph on 2010-03-24
[http://matplotlib.sourceforge.net/api/pyplot_api.html#matplotlib.pyplot.show](http://matplotlib.sourceforge.net/api/pyplot_api.html#matplotlib.pyplot.show)

pylab.show()

---

### Post by MindSz on 2010-03-24
Awesomeness!! Thank you!!

---

