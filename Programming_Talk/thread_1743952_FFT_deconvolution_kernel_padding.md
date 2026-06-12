---
title: "FFT deconvolution: kernel padding"
date: 2011-04-29
forum: Programming Talk
---

### Post by mcweaver1 on 2011-04-29
Hi all,

I am currently writing code to deconvolve a blurred image with a Gaussian kernel to output the non-blurred original image.  I am using the FFTW++ header class on top of FFTW.

I have the FFT working in both directions *without* doing any deconvolution - i.e. I can read in the image, pad it, transform it, reverse-transform it, remove the padding, and get back the image exactly how I started.

It is when the deconvolution comes in that I'm running into problems.  I've been scratching my head for days and can't figure out what I'm doing wrong, so I was hoping someone with a bit more knowledge/sleep might spot my error!  This is my basic algorithm:

[LIST=1]
[*]New dimensions of image and kernel = square, with sides of length 2*max(x dimension of img, y dimension of img), rounded up to the nearest power of two (eg 352x512 image = 1024 square
[*]Pad image *all around* so centre of original image is at centre of padded image
[*]Pad Gaussian kernel to same size and and wrap columns and rows, so e.g.
```

                    [a b ........ c d
[a b c d             e f ........ g h
 e f g h      =>     : : ........ : :        where every pixel but the letters = 0
 i j k l]            : : ........ : :
                     i j ........ k l]

```
[*]Transform image and kernel (with the extra padding specified by FFTW++, so transforms are of size x * (y/2 + 1)
[*]Deconvolve by:
```

for (i = 0; i < x; i++) {
    for (j = 0; j < (y/2 + 1); j++) {
        real(deconvolved(i,j))      = real(image(i,j)) * real(kernel(i,j))
                                    + imaginary(image(i,j)) * imaginary(kernel(i,j))
                                    all divided by ( x* (y/2 + 1) )
        imaginary(deconvolved(i,j)) = imaginary(image(i,j)) * real(kernel(i,j))
                                    - real(image(i,j)) * imaginary(kernel(i,j))
                                    all divided by ( x* (y/2 + 1) )
    }
}

```
[*]Now inverse transform "deconvolved", and unpad so the original image is recovered from the centre.
[/LIST]

Hypothetically this should produce the deconvolution of the two images.  I have tried dividing each real/imaginary component by the real*real and imaginary*imaginary parts of the kernel but this produces something that doesn't even look like the image - some kind of odd spectrum.  What I currently have seems to *blur* the image further.... (although the position of the resulting image is correct)

I think I may have misunderstood how to pad the kernel (been looking online for ages and trying so many different things), my deconvolution step could be wrong but I've gone over it so many times...

Sorry for the length of this, congratulations if you managed to read all of it, and my undying gratitude if you can actually help! :)

NB: I have just attached an image displaying the results of the deconvolution as above (left) and the original image (right) in case it helps.

---

