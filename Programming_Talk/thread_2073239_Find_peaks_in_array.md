---
title: "Find peaks in array"
date: 2012-10-19
forum: Programming Talk
---

### Post by cjohns30 on 2012-10-19
I have an array that consists of peaks in a data set over a threshold value. I have a corresponding array with the frequency values of all those points that survived the threshold. I would like to now find frequency values of just the highest value for each peak, and delete all the other values. Any ideas?

---

### Post by XplosS on 2012-10-19
Can you paste sample data for the problem, please?

---

### Post by ofnuts on 2012-10-19
> **cjohns30 said:**
> I have an array that consists of peaks in a data set over a threshold value. I have a corresponding array with the frequency values of all those points that survived the threshold. I would like to now find frequency values of just the highest value for each peak, and delete all the other values. Any ideas?
Scan the array and keep those with an index sch that where value[index-1]<value[index] and value[index+1]<value[index] (if "peak" means "local maximum"). I don't think the thresholding changes anything here (except hiding peaks lower than the threshold)

---

### Post by MadCow108 on 2012-10-19
peak finding can be a complex problem, how does your data look like?
does it contain noise? what shape are the peaks? what is the shape of the background? what is the noise distribution?

on simple data ofnuts approach will work well.

on some data you may want to smooth or min-max filter the data first and/or use second derivatives to avoid small deviations.

If you know your data wwell you may be successuful with markov chains or deconvolution.
here are a couple algorithms for gaussian peaks on background with gaussian noise using deconvolution for the peaks and markov chains for denoising:
[http://root.cern.ch/root/html534/TSpectrum.html#TSpectrum:SearchHighRes](http://root.cern.ch/root/html534/TSpectrum.html#TSpectrum:SearchHighRes)

---

### Post by cjohns30 on 2012-10-24
A modified version of ofnuts solution using the values instead of the index worked. Thanks!

---

