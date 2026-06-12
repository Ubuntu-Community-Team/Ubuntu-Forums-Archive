---
title: "really old network game for slow ubuntu PC for kids?"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Rorke on 2008-10-01
I've set up 4 PC, but 2 are slow, one so much so that it won't run BZFlag. I'm looking for a fun network game for the kids to play. Really, they're too young for Doom (and I haven't successfully been able to install it yet) so if anyone can recommend anything more suitable for the under 10s that's less processor intensive that BZFlag, that would be appreciated.
Thanks :-)

---

### Post by Paqman on 2008-10-01
Battle for Wesnoth.

It's a turn-based fantasy wargame, so shouldn't tax your machine too hard. The online community is pretty active, or you can play across your own network.

---

### Post by mindoms on 2008-10-02
frozen-bubble is pretty nice

---

### Post by WitchCraft on 2008-10-02
i think:
[http://cdd.alioth.debian.org/junior/tasks/](http://cdd.alioth.debian.org/junior/tasks/)
[http://cdd.alioth.debian.org/junior/tasks/arcade.html](http://cdd.alioth.debian.org/junior/tasks/arcade.html)
contains links to what you want.

i would however recommend simulation games:
[http://cdd.alioth.debian.org/junior/tasks/games-sim.html](http://cdd.alioth.debian.org/junior/tasks/games-sim.html)
(because they are less violent, and since they are for older children, your child will learn a few things by playing if it is not that old)


Apart from that, it's not that wise to let your children waste time by playing nonsense-games. Let them play with with something that's fun to play with, e.g. programming languages or educational math packages for little children.
[http://cdd.alioth.debian.org/junior/tasks/math.html](http://cdd.alioth.debian.org/junior/tasks/math.html)
[http://cdd.alioth.debian.org/junior/tasks/programming.html](http://cdd.alioth.debian.org/junior/tasks/programming.html)



But since you indicated you like ego-shooter games:
[www.urbanterror.net](www.urbanterror.net)
might be what you want. Also check out an aimbot for it (from me) at [www.aimbots.net](www.aimbots.net)

PS: The ego-shooter games based on quake need openGL hardware acceleration, so you need to install the appropriate driver if it is not installed.
to see if you have a graphics card with opengl:
```

glxinfo | grep "direct"

```

which should output:
```

direct rendering: Yes

```

If it outputs "direct rendering: No", then your graphics card either does not support openGL, or you did not install the appropriate graphics card driver, and thus you are unable to run these games.


And
[http://ufoai.sourceforge.net/](http://ufoai.sourceforge.net/)
which is basically a clone of x-com ufo defense.

And the following games are fun, too:
apt-get install junior-games-net
apt-get install 3dchess
apt-get install vectoroids
apt-get install hedgewars

---

### Post by Rorke on 2008-10-03
I was signing up to that games forum, and citing you as a referer, but your name WitchCraft is unknown there. Do you want to send me your login name? Do you get anything?

---

### Post by WitchCraft on 2008-10-03
> **Rorke said:**
> I was signing up to that games forum, and citing you as a referer, but your name WitchCraft is unknown there. Do you want to send me your login name? Do you get anything?

Sent you a PM.

Also check out: [www.nixcoders.org](www.nixcoders.org)

---

### Post by kylet450 on 2008-10-03
Urban Terror will probaby run.

[http://www.urbanterror.net/news.php](http://www.urbanterror.net/news.php)

Whats your output for: glxgears

---

### Post by Rorke on 2008-10-04
Great utility, it really shows where the difficulty is: (I've averaged the results)
Kids PC
1643.8	frames	in	5	seconds	=	327.41	FPS
Alice PC
132.62	frames	in	5	seconds	=	520.23	FPS
Jackie PC
9348.76	frames	in	5	seconds	=	1869.67	FPS
Simon PC
22929.2	frames	in	5	seconds	=	4585.69	FPS

Are there any useful tips on streamlining I can do, bearing in mind that they play Abe's Amazing Adventure, Tux, Pingus and BZFlag most?

---

### Post by binbash on 2008-10-04
[http://www.kaillera.com/](http://www.kaillera.com/)

---

### Post by kylet450 on 2008-10-04
> **Rorke said:**
> Great utility, it really shows where the difficulty is: (I've averaged the results)
Kids PC
1643.8	frames	in	5	seconds	=	327.41	FPS
Alice PC
132.62	frames	in	5	seconds	=	520.23	FPS
Jackie PC
9348.76	frames	in	5	seconds	=	1869.67	FPS
Simon PC
22929.2	frames	in	5	seconds	=	4585.69	FPS

Are there any useful tips on streamlining I can do, bearing in mind that they play Abe's Amazing Adventure, Tux, Pingus and BZFlag most?

All of them can play Urban Terror :)

---

### Post by WitchCraft on 2008-10-04
> **kylet450 said:**
> All of them can play Urban Terror :)

:lolflag:
> 
# glxgears
3981 frames in 5.0 seconds = 796.147 FPS
4319 frames in 5.0 seconds = 863.730 FPS
4374 frames in 5.0 seconds = 874.750 FPS
4390 frames in 5.0 seconds = 877.891 FPS
4268 frames in 5.0 seconds = 853.462 FPS
4302 frames in 5.0 seconds = 860.242 FPS
4261 frames in 5.0 seconds = 852.010 FPS
4286 frames in 5.0 seconds = 857.153 FPS
4350 frames in 5.0 seconds = 869.931 FPS
4387 frames in 5.0 seconds = 877.214 FPS
4334 frames in 5.0 seconds = 866.768 FPS
6442 frames in 5.0 seconds = 1288.397 FPS
14352 frames in 5.0 seconds = 2870.253 FPS
13900 frames in 5.0 seconds = 2779.975 FPS
11420 frames in 5.0 seconds = 2283.965 FPS
13649 frames in 5.0 seconds = 2729.797 FPS
13008 frames in 5.0 seconds = 2600.739 FPS
13927 frames in 5.0 seconds = 2785.328 FPS
14290 frames in 5.0 seconds = 2857.821 FPS
14382 frames in 5.0 seconds = 2876.378 FPS
14414 frames in 5.0 seconds = 2882.753 FPS
14410 frames in 5.0 seconds = 2881.925 FPS
14386 frames in 5.0 seconds = 2877.018 FPS
14413 frames in 5.0 seconds = 2882.566 FPS
14424 frames in 5.0 seconds = 2884.681 FPS
14384 frames in 5.0 seconds = 2876.690 FPS
14409 frames in 5.0 seconds = 2881.723 FPS
14397 frames in 5.0 seconds = 2879.291 FPS
14393 frames in 5.0 seconds = 2878.536 FPS
14420 frames in 5.0 seconds = 2883.961 FPS
14430 frames in 5.0 seconds = 2885.980 FPS
14381 frames in 5.0 seconds = 2876.129 FPS
14418 frames in 5.0 seconds = 2883.500 FPS
14397 frames in 5.0 seconds = 2879.296 FPS
14397 frames in 5.0 seconds = 2879.266 FPS
14415 frames in 5.0 seconds = 2882.877 FPS
14433 frames in 5.0 seconds = 2886.553 FPS
14389 frames in 5.0 seconds = 2877.696 FPS
14329 frames in 5.0 seconds = 2865.794 FPS
14412 frames in 5.0 seconds = 2882.316 FPS
14383 frames in 5.0 seconds = 2876.456 FPS
14428 frames in 5.0 seconds = 2885.462 FPS
14421 frames in 5.0 seconds = 2884.174 FPS
14389 frames in 5.0 seconds = 2877.726 FPS
14410 frames in 5.0 seconds = 2881.977 FPS
14411 frames in 5.0 seconds = 2882.059 FPS
14390 frames in 5.0 seconds = 2877.927 FPS
14412 frames in 5.0 seconds = 2882.238 FPS
14430 frames in 5.0 seconds = 2885.837 FPS
14387 frames in 5.0 seconds = 2877.390 FPS
14333 frames in 5.0 seconds = 2866.468 FPS
14410 frames in 5.0 seconds = 2881.853 FPS
14392 frames in 5.0 seconds = 2878.371 FPS
14417 frames in 5.0 seconds = 2883.311 FPS
14438 frames in 5.0 seconds = 2887.482 FPS
14386 frames in 5.0 seconds = 2877.089 FPS
14414 frames in 5.0 seconds = 2882.734 FPS
14410 frames in 5.0 seconds = 2881.832 FPS
14388 frames in 5.0 seconds = 2877.489 FPS
14414 frames in 5.0 seconds = 2882.800 FPS
14426 frames in 5.0 seconds = 2885.155 FPS
14389 frames in 5.0 seconds = 2877.734 FPS
14322 frames in 5.0 seconds = 2864.250 FPS
14419 frames in 5.0 seconds = 2883.615 FPS
14391 frames in 5.0 seconds = 2878.168 FPS
14426 frames in 5.0 seconds = 2885.122 FPS
14434 frames in 5.0 seconds = 2886.608 FPS
14391 frames in 5.0 seconds = 2878.126 FPS
14412 frames in 5.0 seconds = 2882.251 FPS
14407 frames in 5.0 seconds = 2881.319 FPS
14391 frames in 5.0 seconds = 2878.181 FPS
14412 frames in 5.0 seconds = 2882.399 FPS
14436 frames in 5.0 seconds = 2887.038 FPS
14381 frames in 5.0 seconds = 2876.036 FPS
14330 frames in 5.0 seconds = 2865.993 FPS
14406 frames in 5.0 seconds = 2881.080 FPS
14392 frames in 5.0 seconds = 2878.235 FPS
14413 frames in 5.0 seconds = 2882.555 FPS
14436 frames in 5.0 seconds = 2887.085 FPS
14389 frames in 5.0 seconds = 2877.719 FPS
14398 frames in 5.0 seconds = 2879.417 FPS
14426 frames in 5.0 seconds = 2885.113 FPS
14386 frames in 5.0 seconds = 2877.093 FPS
14407 frames in 5.0 seconds = 2881.301 FPS
14432 frames in 5.0 seconds = 2886.314 FPS
14384 frames in 5.0 seconds = 2876.708 FPS
14316 frames in 5.0 seconds = 2863.198 FPS
14420 frames in 5.0 seconds = 2883.931 FPS
14389 frames in 5.0 seconds = 2877.785 FPS
14417 frames in 5.0 seconds = 2883.246 FPS
14436 frames in 5.0 seconds = 2887.041 FPS
14377 frames in 5.0 seconds = 2875.396 FPS
14406 frames in 5.0 seconds = 2881.176 FPS
14414 frames in 5.0 seconds = 2882.701 FPS
14384 frames in 5.0 seconds = 2876.782 FPS
14392 frames in 5.0 seconds = 2878.300 FPS
14453 frames in 5.0 seconds = 2890.468 FPS
14373 frames in 5.0 seconds = 2874.570 FPS
14311 frames in 5.0 seconds = 2862.118 FPS
14418 frames in 5.0 seconds = 2883.545 FPS
14384 frames in 5.0 seconds = 2876.701 FPS
14415 frames in 5.0 seconds = 2882.988 FPS
14438 frames in 5.0 seconds = 2887.390 FPS
14380 frames in 5.0 seconds = 2875.922 FPS
14405 frames in 5.0 seconds = 2880.984 FPS
14431 frames in 5.0 seconds = 2886.017 FPS
14386 frames in 5.0 seconds = 2877.128 FPS
14408 frames in 5.0 seconds = 2881.494 FPS
14443 frames in 5.0 seconds = 2888.468 FPS
14382 frames in 5.0 seconds = 2876.264 FPS
14320 frames in 5.0 seconds = 2863.931 FPS
14425 frames in 5.0 seconds = 2884.943 FPS
14398 frames in 5.0 seconds = 2879.423 FPS
14433 frames in 5.0 seconds = 2886.599 FPS
14428 frames in 5.0 seconds = 2885.557 FPS
14374 frames in 5.0 seconds = 2874.610 FPS
14406 frames in 5.0 seconds = 2881.116 FPS
14421 frames in 5.0 seconds = 2884.134 FPS
14385 frames in 5.0 seconds = 2876.854 FPS
14424 frames in 5.0 seconds = 2884.722 FPS
14414 frames in 5.0 seconds = 2882.612 FPS
14373 frames in 5.0 seconds = 2874.456 FPS
14307 frames in 5.0 seconds = 2861.359 FPS
14425 frames in 5.0 seconds = 2884.947 FPS
14384 frames in 5.0 seconds = 2876.707 FPS
14442 frames in 5.0 seconds = 2888.316 FPS
14411 frames in 5.0 seconds = 2882.016 FPS
14382 frames in 5.0 seconds = 2876.329 FPS
14395 frames in 5.0 seconds = 2878.896 FPS
14430 frames in 5.0 seconds = 2885.861 FPS
14389 frames in 5.0 seconds = 2877.710 FPS
14413 frames in 5.0 seconds = 2882.416 FPS
14420 frames in 5.0 seconds = 2883.825 FPS
14372 frames in 5.0 seconds = 2874.255 FPS
14051 frames in 5.0 seconds = 2810.190 FPS
14313 frames in 5.0 seconds = 2862.589 FPS
13733 frames in 5.0 seconds = 2746.425 FPS
14427 frames in 5.0 seconds = 2885.327 FPS
14414 frames in 5.0 seconds = 2882.777 FPS
14369 frames in 5.0 seconds = 2873.731 FPS
14393 frames in 5.0 seconds = 2878.560 FPS
14428 frames in 5.0 seconds = 2885.584 FPS
14383 frames in 5.0 seconds = 2876.540 FPS
14416 frames in 5.0 seconds = 2883.077 FPS
14414 frames in 5.0 seconds = 2882.676 FPS
14389 frames in 5.0 seconds = 2877.618 FPS
14302 frames in 5.0 seconds = 2860.327 FPS
14435 frames in 5.0 seconds = 2886.882 FPS
14389 frames in 5.0 seconds = 2877.661 FPS
14436 frames in 5.0 seconds = 2887.061 FPS
14420 frames in 5.0 seconds = 2883.893 FPS
14374 frames in 5.0 seconds = 2874.772 FPS
14395 frames in 5.0 seconds = 2878.826 FPS
14424 frames in 5.0 seconds = 2884.623 FPS
14398 frames in 5.0 seconds = 2879.419 FPS
14408 frames in 5.0 seconds = 2881.493 FPS
14421 frames in 5.0 seconds = 2884.032 FPS
14381 frames in 5.0 seconds = 2876.083 FPS
14307 frames in 5.0 seconds = 2861.243 FPS
14429 frames in 5.0 seconds = 2885.728 FPS
14389 frames in 5.0 seconds = 2877.623 FPS
14432 frames in 5.0 seconds = 2886.337 FPS
14419 frames in 5.0 seconds = 2883.692 FPS
14392 frames in 5.0 seconds = 2878.346 FPS
14388 frames in 5.0 seconds = 2877.448 FPS
14433 frames in 5.0 seconds = 2886.490 FPS
14386 frames in 5.0 seconds = 2877.019 FPS
14427 frames in 5.0 seconds = 2885.379 FPS
14419 frames in 5.0 seconds = 2883.610 FPS
14391 frames in 5.0 seconds = 2878.159 FPS
14301 frames in 5.0 seconds = 2860.152 FPS
14421 frames in 5.0 seconds = 2884.009 FPS
14400 frames in 5.0 seconds = 2879.914 FPS
14421 frames in 5.0 seconds = 2884.133 FPS
14429 frames in 5.0 seconds = 2885.697 FPS
14386 frames in 5.0 seconds = 2877.070 FPS
14390 frames in 5.0 seconds = 2877.960 FPS
14421 frames in 5.0 seconds = 2884.072 FPS
14404 frames in 5.0 seconds = 2880.761 FPS
14418 frames in 5.0 seconds = 2883.346 FPS
14418 frames in 5.0 seconds = 2883.561 FPS
14393 frames in 5.0 seconds = 2878.454 FPS
14304 frames in 5.0 seconds = 2860.631 FPS
14430 frames in 5.0 seconds = 2885.961 FPS
14393 frames in 5.0 seconds = 2878.483 FPS
14435 frames in 5.0 seconds = 2886.836 FPS
14413 frames in 5.0 seconds = 2882.489 FPS
14394 frames in 5.0 seconds = 2878.776 FPS
14384 frames in 5.0 seconds = 2876.663 FPS
14427 frames in 5.0 seconds = 2885.295 FPS
14398 frames in 5.0 seconds = 2879.523 FPS
14419 frames in 5.0 seconds = 2883.613 FPS
14416 frames in 5.0 seconds = 2883.039 FPS
14387 frames in 5.0 seconds = 2877.277 FPS
14302 frames in 5.0 seconds = 2860.364 FPS
14414 frames in 5.0 seconds = 2882.705 FPS
14431 frames in 5.0 seconds = 2886.118 FPS
14396 frames in 5.0 seconds = 2879.197 FPS
14416 frames in 5.0 seconds = 2883.130 FPS
14387 frames in 5.0 seconds = 2877.280 FPS
14394 frames in 5.0 seconds = 2878.701 FPS
14419 frames in 5.0 seconds = 2883.757 FPS
14425 frames in 5.0 seconds = 2884.874 FPS
14396 frames in 5.0 seconds = 2879.016 FPS
14408 frames in 5.0 seconds = 2881.433 FPS
14404 frames in 5.0 seconds = 2880.679 FPS
14295 frames in 5.0 seconds = 2858.935 FPS
14422 frames in 5.0 seconds = 2884.217 FPS
14423 frames in 5.0 seconds = 2884.579 FPS
14404 frames in 5.0 seconds = 2880.782 FPS
14411 frames in 5.0 seconds = 2882.100 FPS
14399 frames in 5.0 seconds = 2879.625 FPS
14388 frames in 5.0 seconds = 2877.461 FPS
14419 frames in 5.0 seconds = 2883.681 FPS
14437 frames in 5.0 seconds = 2887.212 FPS
14390 frames in 5.0 seconds = 2877.806 FPS
14413 frames in 5.0 seconds = 2882.409 FPS
14388 frames in 5.0 seconds = 2877.579 FPS
14299 frames in 5.0 seconds = 2859.753 FPS
14410 frames in 5.0 seconds = 2881.943 FPS
14427 frames in 5.0 seconds = 2885.356 FPS
14398 frames in 5.0 seconds = 2879.431 FPS
14407 frames in 5.0 seconds = 2881.350 FPS
14407 frames in 5.0 seconds = 2881.319 FPS
14382 frames in 5.0 seconds = 2876.388 FPS
14422 frames in 5.0 seconds = 2884.298 FPS
14430 frames in 5.0 seconds = 2885.944 FPS
14399 frames in 5.0 seconds = 2879.717 FPS
14401 frames in 5.0 seconds = 2880.136 FPS
14405 frames in 5.0 seconds = 2880.887 FPS
14292 frames in 5.0 seconds = 2858.208 FPS
14419 frames in 5.0 seconds = 2883.678 FPS
14434 frames in 5.0 seconds = 2886.768 FPS
14393 frames in 5.0 seconds = 2878.476 FPS
14408 frames in 5.0 seconds = 2881.520 FPS
14404 frames in 5.0 seconds = 2880.782 FPS
14389 frames in 5.0 seconds = 2877.755 FPS
14411 frames in 5.0 seconds = 2882.091 FPS
14443 frames in 5.0 seconds = 2888.495 FPS
14384 frames in 5.0 seconds = 2876.744 FPS
14415 frames in 5.0 seconds = 2882.976 FPS
14402 frames in 5.0 seconds = 2880.217 FPS
14299 frames in 5.0 seconds = 2859.670 FPS
14422 frames in 5.0 seconds = 2884.256 FPS
14427 frames in 5.0 seconds = 2885.259 FPS
14407 frames in 5.0 seconds = 2881.308 FPS
14401 frames in 5.0 seconds = 2880.154 FPS
14410 frames in 5.0 seconds = 2881.749 FPS
14389 frames in 5.0 seconds = 2877.676 FPS
14419 frames in 5.0 seconds = 2883.715 FPS
14443 frames in 5.0 seconds = 2888.553 FPS
14387 frames in 5.0 seconds = 2877.342 FPS
14416 frames in 5.0 seconds = 2883.151 FPS
14415 frames in 5.0 seconds = 2882.810 FPS
14307 frames in 5.0 seconds = 2861.316 FPS
14406 frames in 5.0 seconds = 2881.144 FPS
14445 frames in 5.0 seconds = 2888.826 FPS
14398 frames in 5.0 seconds = 2879.420 FPS
14421 frames in 5.0 seconds = 2884.168 FPS
14408 frames in 5.0 seconds = 2881.459 FPS
14399 frames in 5.0 seconds = 2879.656 FPS
14407 frames in 5.0 seconds = 2881.236 FPS
14447 frames in 5.0 seconds = 2889.254 FPS
14389 frames in 5.0 seconds = 2877.799 FPS
14403 frames in 5.0 seconds = 2880.546 FPS
14410 frames in 5.0 seconds = 2881.925 FPS
14296 frames in 5.0 seconds = 2859.043 FPS
14418 frames in 5.0 seconds = 2883.493 FPS
14432 frames in 5.0 seconds = 2886.146 FPS
14397 frames in 5.0 seconds = 2879.380 FPS
14403 frames in 5.0 seconds = 2880.567 FPS
14411 frames in 5.0 seconds = 2882.083 FPS
14395 frames in 5.0 seconds = 2878.858 FPS
14409 frames in 5.0 seconds = 2881.738 FPS
14456 frames in 5.0 seconds = 2891.057 FPS
14388 frames in 5.0 seconds = 2877.545 FPS
14403 frames in 5.0 seconds = 2880.561 FPS
14404 frames in 5.0 seconds = 2880.614 FPS
14304 frames in 5.0 seconds = 2860.699 FPS
14405 frames in 5.0 seconds = 2880.814 FPS
14452 frames in 5.0 seconds = 2890.364 FPS
14272 frames in 5.0 seconds = 2854.217 FPS
14377 frames in 5.0 seconds = 2875.284 FPS
14410 frames in 5.0 seconds = 2881.850 FPS
14385 frames in 5.0 seconds = 2876.960 FPS
14414 frames in 5.0 seconds = 2882.700 FPS
14438 frames in 5.0 seconds = 2887.538 FPS
14389 frames in 5.0 seconds = 2877.791 FPS
14397 frames in 5.0 seconds = 2879.238 FPS
14409 frames in 5.0 seconds = 2881.712 FPS
14301 frames in 5.0 seconds = 2860.160 FPS
14409 frames in 5.0 seconds = 2881.750 FPS
14438 frames in 5.0 seconds = 2887.538 FPS
14404 frames in 5.0 seconds = 2880.760 FPS
14406 frames in 5.0 seconds = 2881.162 FPS
14408 frames in 5.0 seconds = 2881.553 FPS
14400 frames in 5.0 seconds = 2879.886 FPS
14424 frames in 5.0 seconds = 2884.713 FPS
14424 frames in 5.0 seconds = 2884.731 FPS
14379 frames in 5.0 seconds = 2875.607 FPS
14408 frames in 5.0 seconds = 2881.491 FPS
14409 frames in 5.0 seconds = 2881.698 FPS
14300 frames in 5.0 seconds = 2859.946 FPS
14420 frames in 5.0 seconds = 2883.927 FPS
14415 frames in 5.0 seconds = 2882.847 FPS
14404 frames in 5.0 seconds = 2880.688 FPS
14391 frames in 5.0 seconds = 2878.035 FPS
14412 frames in 5.0 seconds = 2882.291 FPS
14387 frames in 5.0 seconds = 2877.391 FPS
14428 frames in 5.0 seconds = 2885.552 FPS
14412 frames in 5.0 seconds = 2882.322 FPS
14396 frames in 5.0 seconds = 2879.173 FPS
14399 frames in 5.0 seconds = 2879.667 FPS
14404 frames in 5.0 seconds = 2880.766 FPS
14317 frames in 5.0 seconds = 2863.213 FPS
14427 frames in 5.0 seconds = 2885.243 FPS
14420 frames in 5.0 seconds = 2883.853 FPS
14402 frames in 5.0 seconds = 2880.331 FPS
14412 frames in 5.0 seconds = 2882.374 FPS
14411 frames in 5.0 seconds = 2882.181 FPS
14414 frames in 5.0 seconds = 2882.706 FPS
14422 frames in 5.0 seconds = 2884.377 FPS
14417 frames in 5.0 seconds = 2883.238 FPS
14398 frames in 5.0 seconds = 2879.515 FPS
14394 frames in 5.0 seconds = 2878.696 FPS
14409 frames in 5.0 seconds = 2881.690 FPS
14312 frames in 5.0 seconds = 2862.210 FPS
14426 frames in 5.0 seconds = 2885.161 FPS
14411 frames in 5.0 seconds = 2882.121 FPS
14409 frames in 5.0 seconds = 2881.669 FPS
14396 frames in 5.0 seconds = 2879.163 FPS
14409 frames in 5.0 seconds = 2881.689 FPS
14399 frames in 5.0 seconds = 2879.699 FPS
14424 frames in 5.0 seconds = 2884.756 FPS
14410 frames in 5.0 seconds = 2881.874 FPS
14392 frames in 5.0 seconds = 2878.226 FPS
14399 frames in 5.0 seconds = 2879.769 FPS
14399 frames in 5.0 seconds = 2879.800 FPS
14321 frames in 5.0 seconds = 2864.176 FPS
14422 frames in 5.0 seconds = 2884.279 FPS
14421 frames in 5.0 seconds = 2884.142 FPS
14373 frames in 5.0 seconds = 2874.428 FPS
13448 frames in 5.0 seconds = 2689.569 FPS
14405 frames in 5.0 seconds = 2880.944 FPS
14407 frames in 5.0 seconds = 2881.314 FPS
14423 frames in 5.0 seconds = 2884.474 FPS
14410 frames in 5.0 seconds = 2881.843 FPS
14413 frames in 5.0 seconds = 2882.542 FPS
14404 frames in 5.0 seconds = 2880.680 FPS
14398 frames in 5.0 seconds = 2879.591 FPS
14309 frames in 5.0 seconds = 2861.612 FPS
14431 frames in 5.0 seconds = 2886.177 FPS
14410 frames in 5.0 seconds = 2881.968 FPS
14419 frames in 5.0 seconds = 2883.626 FPS
14386 frames in 5.0 seconds = 2877.076 FPS
14391 frames in 5.0 seconds = 2878.181 FPS
14420 frames in 5.0 seconds = 2883.910 FPS
14419 frames in 5.0 seconds = 2883.681 FPS
14410 frames in 5.0 seconds = 2881.947 FPS
14402 frames in 5.0 seconds = 2880.378 FPS
14400 frames in 5.0 seconds = 2879.893 FPS
14396 frames in 5.0 seconds = 2879.114 FPS
14320 frames in 5.0 seconds = 2863.832 FPS
14429 frames in 5.0 seconds = 2885.795 FPS
14401 frames in 5.0 seconds = 2880.092 FPS
14415 frames in 5.0 seconds = 2882.850 FPS
14395 frames in 5.0 seconds = 2878.965 FPS
14399 frames in 5.0 seconds = 2879.660 FPS
14406 frames in 5.0 seconds = 2881.084 FPS
14428 frames in 5.0 seconds = 2885.460 FPS
14398 frames in 5.0 seconds = 2879.544 FPS
14415 frames in 5.0 seconds = 2882.901 FPS
14389 frames in 5.0 seconds = 2877.677 FPS
14402 frames in 5.0 seconds = 2880.320 FPS
14324 frames in 5.0 seconds = 2864.630 FPS
14427 frames in 5.0 seconds = 2885.289 FPS
14407 frames in 5.0 seconds = 2881.274 FPS
14413 frames in 5.0 seconds = 2882.415 FPS
14397 frames in 5.0 seconds = 2879.347 FPS
14389 frames in 5.0 seconds = 2877.774 FPS
14416 frames in 5.0 seconds = 2883.121 FPS
14419 frames in 5.0 seconds = 2883.650 FPS
14410 frames in 5.0 seconds = 2881.886 FPS
14410 frames in 5.0 seconds = 2881.968 FPS
14395 frames in 5.0 seconds = 2878.820 FPS
14395 frames in 5.0 seconds = 2878.975 FPS
14328 frames in 5.0 seconds = 2865.475 FPS
14422 frames in 5.0 seconds = 2884.268 FPS
14401 frames in 5.0 seconds = 2880.133 FPS
14421 frames in 5.0 seconds = 2884.028 FPS
14390 frames in 5.0 seconds = 2877.868 FPS
14407 frames in 5.0 seconds = 2881.332 FPS
14413 frames in 5.0 seconds = 2882.522 FPS
14426 frames in 5.0 seconds = 2885.030 FPS
14398 frames in 5.0 seconds = 2879.434 FPS
14408 frames in 5.0 seconds = 2881.440 FPS
14396 frames in 5.0 seconds = 2879.040 FPS
14386 frames in 5.0 seconds = 2877.164 FPS
14359 frames in 5.0 seconds = 2871.616 FPS
14390 frames in 5.0 seconds = 2877.864 FPS
14409 frames in 5.0 seconds = 2881.594 FPS
14415 frames in 5.0 seconds = 2882.865 FPS
14394 frames in 5.0 seconds = 2878.700 FPS
14386 frames in 5.0 seconds = 2877.052 FPS
14448 frames in 5.0 seconds = 2889.427 FPS
14395 frames in 5.0 seconds = 2878.987 FPS
14404 frames in 5.0 seconds = 2880.613 FPS
14422 frames in 5.0 seconds = 2884.328 FPS
14393 frames in 5.0 seconds = 2878.320 FPS
14395 frames in 5.0 seconds = 2878.968 FPS
14355 frames in 5.0 seconds = 2870.857 FPS
14412 frames in 5.0 seconds = 2882.347 FPS
14392 frames in 5.0 seconds = 2878.349 FPS
14433 frames in 5.0 seconds = 2886.504 FPS
14393 frames in 5.0 seconds = 2878.597 FPS
14389 frames in 5.0 seconds = 2877.799 FPS
14447 frames in 5.0 seconds = 2889.282 FPS
14403 frames in 5.0 seconds = 2880.551 FPS
14407 frames in 5.0 seconds = 2881.277 FPS
14413 frames in 5.0 seconds = 2882.433 FPS
14399 frames in 5.0 seconds = 2879.736 FPS
14385 frames in 5.0 seconds = 2876.915 FPS
14356 frames in 5.0 seconds = 2871.061 FPS
14394 frames in 5.0 seconds = 2878.786 FPS
14396 frames in 5.0 seconds = 2879.135 FPS
14421 frames in 5.0 seconds = 2884.025 FPS
14396 frames in 5.0 seconds = 2879.112 FPS
14389 frames in 5.0 seconds = 2877.624 FPS
14440 frames in 5.0 seconds = 2887.966 FPS
14410 frames in 5.0 seconds = 2881.896 FPS
14390 frames in 5.0 seconds = 2877.827 FPS
14422 frames in 5.0 seconds = 2884.262 FPS
14392 frames in 5.0 seconds = 2878.212 FPS
14391 frames in 5.0 seconds = 2878.086 FPS
14347 frames in 5.0 seconds = 2869.230 FPS
14406 frames in 5.0 seconds = 2881.112 FPS
14395 frames in 5.0 seconds = 2878.975 FPS
14422 frames in 5.0 seconds = 2884.310 FPS
14404 frames in 5.0 seconds = 2880.692 FPS
14380 frames in 5.0 seconds = 2875.942 FPS
14452 frames in 5.0 seconds = 2890.356 FPS
14404 frames in 5.0 seconds = 2880.648 FPS
14394 frames in 5.0 seconds = 2878.795 FPS
14414 frames in 5.0 seconds = 2882.612 FPS
14403 frames in 5.0 seconds = 2880.553 FPS
14382 frames in 5.0 seconds = 2876.396 FPS
14359 frames in 5.0 seconds = 2871.623 FPS
14411 frames in 5.0 seconds = 2882.177 FPS
14390 frames in 5.0 seconds = 2878.000 FPS
12767 frames in 5.0 seconds = 2553.344 FPS
14376 frames in 5.0 seconds = 2875.031 FPS
14073 frames in 5.0 seconds = 2814.480 FPS
13350 frames in 5.0 seconds = 2669.904 FPS
13884 frames in 5.0 seconds = 2776.622 FPS
10672 frames in 5.0 seconds = 2133.610 FPS
[SIZE="7"][COLOR="Red"][B]XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 157924 requests (153801 known processed) with 0 events remaining.[/B][/COLOR][/SIZE]



:lolflag:

---

