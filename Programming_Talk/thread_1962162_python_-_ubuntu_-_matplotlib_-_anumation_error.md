---
title: "python - ubuntu - matplotlib - anumation error"
date: 2012-04-20
forum: Programming Talk
---

### Post by diedro on 2012-04-20
dear all,

I would like to create some animation with python and matplotlib

I try this one from matplotlib ]example

```

import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation

def update_line(num, data, line):
    line.set_data(data[...,:num])
    return line,

fig1 = plt.figure()

data = np.random.rand(2, 25)
l, = plt.plot([], [], 'r-')
plt.xlim(0, 1)
plt.ylim(0, 1)
plt.xlabel('x')
plt.title('test')
line_ani = animation.FuncAnimation(fig1, update_line, 25, fargs=(data, l),
    interval=50, blit=True)
#line_ani.save('lines.mp4')

fig2 = plt.figure()

x = np.arange(-9, 10)
y = np.arange(-9, 10).reshape(-1, 1)
base = np.hypot(x, y)
ims = []
for add in np.arange(15):
    ims.append((plt.pcolor(x, y, base + add, norm=plt.Normalize(0, 30)),))

im_ani = animation.ArtistAnimation(fig2, ims, interval=50, repeat_delay=3000,
    blit=True)
im_ani.save('im.mp4')

plt.show()

```

however, I get the following error:

```

Traceback (most recent call last):
  File "/home/diedro/Desktop/temp/prova_ani.py", line 29, in <module>
    ani.save('dynamic_images.mp4')
  File "/usr/local/lib/python2.7/dist-packages/matplotlib/animation.py", line 127, in save
    self._make_movie(filename, fps, codec, frame_prefix)
  File "/usr/local/lib/python2.7/dist-packages/matplotlib/animation.py", line 164, in _make_movie
    stdout=PIPE, stderr=PIPE)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```

What's wrong? I do not understand why,
please help me

---

### Post by MadCow108 on 2012-04-20
you need to install ffmpeg for animation to work

---

### Post by diedro on 2012-04-21
thanks a lot

it works now

really,really thanks

---

