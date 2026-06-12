---
title: "C++ Cos() lies! at 90 degrees!"
date: 2007-07-20
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2007-07-20
Hey guys 

In my adventures with programming I've come across a weird little thing when testing values from the cos() in math.h on ubuntu!

heres my output from a for loop that does this:
```

for(int i = 0; i<=360; i++	) {
		cout << "angle = " << i << " Radians = " << cos(i*M_PI/180) << "\n";
	}

```



OUTPUTS:

angle = 0 Radians = 1
angle = 1 Radians = 0.999848
angle = 2 Radians = 0.999391
angle = 3 Radians = 0.99863
angle = 4 Radians = 0.997564
angle = 5 Radians = 0.996195
angle = 6 Radians = 0.994522
angle = 7 Radians = 0.992546
angle = 8 Radians = 0.990268
angle = 9 Radians = 0.987688
angle = 10 Radians = 0.984808
angle = 11 Radians = 0.981627
angle = 12 Radians = 0.978148
angle = 13 Radians = 0.97437
angle = 14 Radians = 0.970296
angle = 15 Radians = 0.965926
angle = 16 Radians = 0.961262
angle = 17 Radians = 0.956305
angle = 18 Radians = 0.951057
angle = 19 Radians = 0.945519
angle = 20 Radians = 0.939693
angle = 21 Radians = 0.93358
angle = 22 Radians = 0.927184
angle = 23 Radians = 0.920505
angle = 24 Radians = 0.913545
angle = 25 Radians = 0.906308
angle = 26 Radians = 0.898794
angle = 27 Radians = 0.891007
angle = 28 Radians = 0.882948
angle = 29 Radians = 0.87462
angle = 30 Radians = 0.866025
angle = 31 Radians = 0.857167
angle = 32 Radians = 0.848048
angle = 33 Radians = 0.838671
angle = 34 Radians = 0.829038
angle = 35 Radians = 0.819152
angle = 36 Radians = 0.809017
angle = 37 Radians = 0.798636
angle = 38 Radians = 0.788011
angle = 39 Radians = 0.777146
angle = 40 Radians = 0.766044
angle = 41 Radians = 0.75471
angle = 42 Radians = 0.743145
angle = 43 Radians = 0.731354
angle = 44 Radians = 0.71934
angle = 45 Radians = 0.707107
angle = 46 Radians = 0.694658
angle = 47 Radians = 0.681998
angle = 48 Radians = 0.669131
angle = 49 Radians = 0.656059
angle = 50 Radians = 0.642788
angle = 51 Radians = 0.62932
angle = 52 Radians = 0.615661
angle = 53 Radians = 0.601815
angle = 54 Radians = 0.587785
angle = 55 Radians = 0.573576
angle = 56 Radians = 0.559193
angle = 57 Radians = 0.544639
angle = 58 Radians = 0.529919
angle = 59 Radians = 0.515038
angle = 60 Radians = 0.5
angle = 61 Radians = 0.48481
angle = 62 Radians = 0.469472
angle = 63 Radians = 0.45399
angle = 64 Radians = 0.438371
angle = 65 Radians = 0.422618
angle = 66 Radians = 0.406737
angle = 67 Radians = 0.390731
angle = 68 Radians = 0.374607
angle = 69 Radians = 0.358368
angle = 70 Radians = 0.34202
angle = 71 Radians = 0.325568
angle = 72 Radians = 0.309017
angle = 73 Radians = 0.292372
angle = 74 Radians = 0.275637
angle = 75 Radians = 0.258819
angle = 76 Radians = 0.241922
angle = 77 Radians = 0.224951
angle = 78 Radians = 0.207912
angle = 79 Radians = 0.190809
angle = 80 Radians = 0.173648
angle = 81 Radians = 0.156434
angle = 82 Radians = 0.139173
angle = 83 Radians = 0.121869
angle = 84 Radians = 0.104528
angle = 85 Radians = 0.0871557
angle = 86 Radians = 0.0697565
angle = 87 Radians = 0.052336
angle = 88 Radians = 0.0348995
angle = 89 Radians = 0.0174524
[COLOR="Red"]angle = 90 Radians = 6.12303e-17[/COLOR] HUH!?
angle = 91 Radians = -0.0174524
angle = 92 Radians = -0.0348995
angle = 93 Radians = -0.052336
angle = 94 Radians = -0.0697565
angle = 95 Radians = -0.0871557
angle = 96 Radians = -0.104528
angle = 97 Radians = -0.121869
angle = 98 Radians = -0.139173
angle = 99 Radians = -0.156434
angle = 100 Radians = -0.173648
angle = 101 Radians = -0.190809
angle = 102 Radians = -0.207912
angle = 103 Radians = -0.224951
angle = 104 Radians = -0.241922
angle = 105 Radians = -0.258819
angle = 106 Radians = -0.275637
angle = 107 Radians = -0.292372
angle = 108 Radians = -0.309017
angle = 109 Radians = -0.325568
angle = 110 Radians = -0.34202
angle = 111 Radians = -0.358368
angle = 112 Radians = -0.374607
angle = 113 Radians = -0.390731
angle = 114 Radians = -0.406737
angle = 115 Radians = -0.422618
angle = 116 Radians = -0.438371
angle = 117 Radians = -0.45399
angle = 118 Radians = -0.469472
angle = 119 Radians = -0.48481
angle = 120 Radians = -0.5
angle = 121 Radians = -0.515038
angle = 122 Radians = -0.529919
angle = 123 Radians = -0.544639
angle = 124 Radians = -0.559193
angle = 125 Radians = -0.573576
angle = 126 Radians = -0.587785
angle = 127 Radians = -0.601815
angle = 128 Radians = -0.615661
angle = 129 Radians = -0.62932
angle = 130 Radians = -0.642788
angle = 131 Radians = -0.656059
angle = 132 Radians = -0.669131
angle = 133 Radians = -0.681998
angle = 134 Radians = -0.694658
angle = 135 Radians = -0.707107
angle = 136 Radians = -0.71934
angle = 137 Radians = -0.731354
angle = 138 Radians = -0.743145
angle = 139 Radians = -0.75471
angle = 140 Radians = -0.766044
angle = 141 Radians = -0.777146
angle = 142 Radians = -0.788011
angle = 143 Radians = -0.798636
angle = 144 Radians = -0.809017
angle = 145 Radians = -0.819152
angle = 146 Radians = -0.829038
angle = 147 Radians = -0.838671
angle = 148 Radians = -0.848048
angle = 149 Radians = -0.857167
angle = 150 Radians = -0.866025
angle = 151 Radians = -0.87462
angle = 152 Radians = -0.882948
angle = 153 Radians = -0.891007
angle = 154 Radians = -0.898794
angle = 155 Radians = -0.906308
angle = 156 Radians = -0.913545
angle = 157 Radians = -0.920505
angle = 158 Radians = -0.927184
angle = 159 Radians = -0.93358
angle = 160 Radians = -0.939693
angle = 161 Radians = -0.945519
angle = 162 Radians = -0.951057
angle = 163 Radians = -0.956305
angle = 164 Radians = -0.961262
angle = 165 Radians = -0.965926
angle = 166 Radians = -0.970296
angle = 167 Radians = -0.97437
angle = 168 Radians = -0.978148
angle = 169 Radians = -0.981627
angle = 170 Radians = -0.984808
angle = 171 Radians = -0.987688
angle = 172 Radians = -0.990268
angle = 173 Radians = -0.992546
angle = 174 Radians = -0.994522
angle = 175 Radians = -0.996195
angle = 176 Radians = -0.997564
angle = 177 Radians = -0.99863
angle = 178 Radians = -0.999391
angle = 179 Radians = -0.999848
angle = 180 Radians = -1
angle = 181 Radians = -0.999848
angle = 182 Radians = -0.999391
angle = 183 Radians = -0.99863
angle = 184 Radians = -0.997564
angle = 185 Radians = -0.996195
angle = 186 Radians = -0.994522
angle = 187 Radians = -0.992546
angle = 188 Radians = -0.990268
angle = 189 Radians = -0.987688
angle = 190 Radians = -0.984808
angle = 191 Radians = -0.981627
angle = 192 Radians = -0.978148
angle = 193 Radians = -0.97437
angle = 194 Radians = -0.970296
angle = 195 Radians = -0.965926
angle = 196 Radians = -0.961262
angle = 197 Radians = -0.956305
angle = 198 Radians = -0.951057
angle = 199 Radians = -0.945519
angle = 200 Radians = -0.939693
angle = 201 Radians = -0.93358
angle = 202 Radians = -0.927184
angle = 203 Radians = -0.920505
angle = 204 Radians = -0.913545
angle = 205 Radians = -0.906308
angle = 206 Radians = -0.898794
angle = 207 Radians = -0.891007
angle = 208 Radians = -0.882948
angle = 209 Radians = -0.87462
angle = 210 Radians = -0.866025
angle = 211 Radians = -0.857167
angle = 212 Radians = -0.848048
angle = 213 Radians = -0.838671
angle = 214 Radians = -0.829038
angle = 215 Radians = -0.819152
angle = 216 Radians = -0.809017
angle = 217 Radians = -0.798636
angle = 218 Radians = -0.788011
angle = 219 Radians = -0.777146
angle = 220 Radians = -0.766044
angle = 221 Radians = -0.75471
angle = 222 Radians = -0.743145
angle = 223 Radians = -0.731354
angle = 224 Radians = -0.71934
angle = 225 Radians = -0.707107
angle = 226 Radians = -0.694658
angle = 227 Radians = -0.681998
angle = 228 Radians = -0.669131
angle = 229 Radians = -0.656059
angle = 230 Radians = -0.642788
angle = 231 Radians = -0.62932
angle = 232 Radians = -0.615661
angle = 233 Radians = -0.601815
angle = 234 Radians = -0.587785
angle = 235 Radians = -0.573576
angle = 236 Radians = -0.559193
angle = 237 Radians = -0.544639
angle = 238 Radians = -0.529919
angle = 239 Radians = -0.515038
angle = 240 Radians = -0.5
angle = 241 Radians = -0.48481
angle = 242 Radians = -0.469472
angle = 243 Radians = -0.45399
angle = 244 Radians = -0.438371
angle = 245 Radians = -0.422618
angle = 246 Radians = -0.406737
angle = 247 Radians = -0.390731
angle = 248 Radians = -0.374607
angle = 249 Radians = -0.358368
angle = 250 Radians = -0.34202
angle = 251 Radians = -0.325568
angle = 252 Radians = -0.309017
angle = 253 Radians = -0.292372
angle = 254 Radians = -0.275637
angle = 255 Radians = -0.258819
angle = 256 Radians = -0.241922
angle = 257 Radians = -0.224951
angle = 258 Radians = -0.207912
angle = 259 Radians = -0.190809
angle = 260 Radians = -0.173648
angle = 261 Radians = -0.156434
angle = 262 Radians = -0.139173
angle = 263 Radians = -0.121869
angle = 264 Radians = -0.104528
angle = 265 Radians = -0.0871557
angle = 266 Radians = -0.0697565
angle = 267 Radians = -0.052336
angle = 268 Radians = -0.0348995
angle = 269 Radians = -0.0174524
angle = 270 Radians = -1.83691e-16
angle = 271 Radians = 0.0174524
angle = 272 Radians = 0.0348995
angle = 273 Radians = 0.052336
angle = 274 Radians = 0.0697565
angle = 275 Radians = 0.0871557
angle = 276 Radians = 0.104528
angle = 277 Radians = 0.121869
angle = 278 Radians = 0.139173
angle = 279 Radians = 0.156434
angle = 280 Radians = 0.173648
angle = 281 Radians = 0.190809
angle = 282 Radians = 0.207912
angle = 283 Radians = 0.224951
angle = 284 Radians = 0.241922
angle = 285 Radians = 0.258819
angle = 286 Radians = 0.275637
angle = 287 Radians = 0.292372
angle = 288 Radians = 0.309017
angle = 289 Radians = 0.325568
angle = 290 Radians = 0.34202
angle = 291 Radians = 0.358368
angle = 292 Radians = 0.374607
angle = 293 Radians = 0.390731
angle = 294 Radians = 0.406737
angle = 295 Radians = 0.422618
angle = 296 Radians = 0.438371
angle = 297 Radians = 0.45399
angle = 298 Radians = 0.469472
angle = 299 Radians = 0.48481
angle = 300 Radians = 0.5
angle = 301 Radians = 0.515038
angle = 302 Radians = 0.529919
angle = 303 Radians = 0.544639
angle = 304 Radians = 0.559193
angle = 305 Radians = 0.573576
angle = 306 Radians = 0.587785
angle = 307 Radians = 0.601815
angle = 308 Radians = 0.615661
angle = 309 Radians = 0.62932
angle = 310 Radians = 0.642788
angle = 311 Radians = 0.656059
angle = 312 Radians = 0.669131
angle = 313 Radians = 0.681998
angle = 314 Radians = 0.694658
angle = 315 Radians = 0.707107
angle = 316 Radians = 0.71934
angle = 317 Radians = 0.731354
angle = 318 Radians = 0.743145
angle = 319 Radians = 0.75471
angle = 320 Radians = 0.766044
angle = 321 Radians = 0.777146
angle = 322 Radians = 0.788011
angle = 323 Radians = 0.798636
angle = 324 Radians = 0.809017
angle = 325 Radians = 0.819152
angle = 326 Radians = 0.829038
angle = 327 Radians = 0.838671
angle = 328 Radians = 0.848048
angle = 329 Radians = 0.857167
angle = 330 Radians = 0.866025
angle = 331 Radians = 0.87462
angle = 332 Radians = 0.882948
angle = 333 Radians = 0.891007
angle = 334 Radians = 0.898794
angle = 335 Radians = 0.906308
angle = 336 Radians = 0.913545
angle = 337 Radians = 0.920505
angle = 338 Radians = 0.927184
angle = 339 Radians = 0.93358
angle = 340 Radians = 0.939693
angle = 341 Radians = 0.945519
angle = 342 Radians = 0.951057
angle = 343 Radians = 0.956305
angle = 344 Radians = 0.961262
angle = 345 Radians = 0.965926
angle = 346 Radians = 0.970296
angle = 347 Radians = 0.97437
angle = 348 Radians = 0.978148
angle = 349 Radians = 0.981627
angle = 350 Radians = 0.984808
angle = 351 Radians = 0.987688
angle = 352 Radians = 0.990268
angle = 353 Radians = 0.992546
angle = 354 Radians = 0.994522
angle = 355 Radians = 0.996195
angle = 356 Radians = 0.997564
angle = 357 Radians = 0.99863
angle = 358 Radians = 0.999391
angle = 359 Radians = 0.999848
angle = 360 Radians = 1


all seems fine untile i get to 90 degrees then its seems to go nuts!

anyone else get this?

Mike

---

### Post by Lord Illidan on 2007-07-20
It's not just 90, it's 270 as well.

My guess is that since one can never evaluate pi, the computer just generates an extremely small number. In calculators and the like, the computer is probably programmed to generate a zero in those circumstances.

[COLOR=Red]6.12303e-17 = 0.0000000000000000612303

[/COLOR]Which is a v. small number (give or take a 0)

---

### Post by Soybean on 2007-07-20
> **Lord Illidan said:**
> My guess is that since one can never evaluate pi, the computer just generates an extremely small number.
Actually, it's probably floating point error, rather than problems with PI.  Other than that, yes... it's trying to say zero, it's just not very good at it. ;) I just thought I should point out that this is something you should be aware of any time you're doing any floating point calculations -- not just trig functions.

More info here if you're interested: [http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems](http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems)

---

### Post by hod139 on 2007-07-20
As pointed out, 1e-17 is going to be zero for computers.  To give you an idea, most numeric packages use tolerances of 1e-6  (1e-8 if it is really robust).  If you really want to squeeze out a few extra decimals of accuracy you can use M_PIl   (that's uppercase 'eye'  lowercase 'ell').  That will get you 
```
angle = 90 Radians = -2.71051e-20
```and you are not going to get any better than that.  1e20 is about 32 bit infinity.

---

### Post by Lord Illidan on 2007-07-20
> **Soybean said:**
> Actually, it's probably floating point error, rather than problems with PI.  Other than that, yes... it's trying to say zero, it's just not very good at it. ;) I just thought I should point out that this is something you should be aware of any time you're doing any floating point calculations -- not just trig functions.

More info here if you're interested: [http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems](http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems)

Yeah, good link.

---

### Post by stchman on 2007-07-20
I have never had much luck with the M_PI variable.  I usually do the following:

```

int i = 0;
double pi_const = 3.141519265359;

```

I would then do the following:
```

for(i = 0; i <= 360;  i++)
{
	printf( "angle = %d Degrees = %lf\n", i, cos(i * pi_const / 180.0 ) );
}

```

Sorry I hate C++ syntax, I always use the C syntax.

You need to change your Radians to Degrees in your print statement.  The argument of cos() in C is radians, but your loop indicates degrees.

Try that.

---

### Post by stchman on 2007-07-20
I tried this on a gcc compiler

```

#include <stdio.h>
#include <math.h>

void main(void)
{
	int i = 0;
	double pi_const = 3.141519265358979323846;
	
	for(i = 0; i <= 360;  i++)
	{
		printf( "angle = %d Degrees = %20.12lf\n", i, cos( (double)i * pi_const / 180.0 ) );
	}
	
}

```

The 90 degree returned -0.00000000000000

---

### Post by hod139 on 2007-07-20
Running your code I get:
```

angle = 90 Degrees =       0.000036694115

```

Are you running a 64 bit machine?

Also, main should return an int, even in C.  I know it is not required by the C standard, but it is a good habit.

---

