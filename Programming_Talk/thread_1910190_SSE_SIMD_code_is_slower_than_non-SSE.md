---
title: "SSE SIMD code is slower than non-SSE"
date: 2012-01-16
forum: Programming Talk
---

### Post by Clive McCarthy on 2012-01-16
I'm trying some simple experiments using gcc and SSE intrinsics to speed up a quite conventional image filter convolution.

I compile with: -g -march=pentium4 -Wall -Wextra -O3 -mmmx -msse -msse2 -msse3 -mssse3 -mfpmath=sse -mstackrealign -D_REENTRANT -std=gnu89

I have found that my first attempt at using SSE is significantly slower than conventional coding. Here's a couple of code fragments from the very heart of the convolver:
```

/* my SSE SIMD method */
		pixel[0] = kr; pixel[1] = kg; pixel[2] = kb; pixel[3] = ALPHA_OPAQUE;
		//Load 4 floats from a 16-byte aligned address.
		pixel_m128 = _mm_load_ps(pixel);

		// Load 1 float into all 4 fields of an __m128
		weight_m128 = _mm_load1_ps(&weight);

		// Multiply corresponding floats
		prod_m128 = _mm_mul_ps(weight_m128, pixel_m128);
		
		// Add corresponding floats
		sum_m128 = _mm_add_ps(prod_m128, sum_m128);
		
/* my conventional method */
		r_sum += kr * weight; g_sum += kg * weight; b_sum += kb * weight;

```

I wasn't expecting the SSE result to be 25% slower than my conventional method. Am I missing something? Is the performance hit all from the type conversions to and from the SSE registers? This is my first attempt at using SSE intrinsics so I could be doing something trivially stupid. Help please.

---

### Post by Bachstelze on 2012-01-16
In general, you can trust the compiler to use whatever method is the fastest to perform the desired operation. If SSE is available, the compiler will use it. Have you looked at the generated assembly code?

---

### Post by Clive McCarthy on 2012-01-16
No I haven't looked at the assembler code. It is a VERY long time since I read such stuff and I never did get along with Intel 8080 assembler code -- I preferred the 6800 code (that's how long ago I'm talking about).

This may be the end of my SSE experiments, which gcc seems to beat handily.

---

