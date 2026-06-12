---
title: "Libjpeg jpeg_write_coefficient"
date: 2011-10-31
forum: Programming Talk
---

### Post by takercena on 2011-10-31
Hello everyone,
I have created my own DCT calculation arrays. Therefore for 256 * 256 pixels size of image, I have prepared 1024 blocks of DCT arrays (8 * 8). 

How do I use jpeg_write_coefficients to write my arrays values into jpeg file using jpeg_write_coefficients. 
jpeg_write_coefficients needs jvirt_barray_ptr * coef_arrays. How do I create this? 

In addition, how to retrieve back the coefficients from the jpeg file?
Thanks.

---

