---
title: "Discrepancies when porting JavaCV Gabor filter code to MatLab/Octave"
date: 2012-02-21
forum: Programming Talk
---

### Post by skytreader on 2012-02-21
[Cross-posted from Stack Overflow: [http://stackoverflow.com/questions/9375839/discrepancies-when-porting-javacv-gabor-filter-code-to-matlab]](http://stackoverflow.com/questions/9375839/discrepancies-when-porting-javacv-gabor-filter-code-to-matlab])

I'm trying to port an OpenCV/JavaCV code to MatLab (ran through Octave). However, I'm getting different results for the matrices I manipulate. I'm running a Gabor Filter through an image and I'm looking at the Gabor-filtered matrix. The base code came from [http://www.eml.ele.cst.nihon-u.ac.jp/~momma/wiki/wiki.cgi/OpenCV/Gabor%20Filter.html](http://www.eml.ele.cst.nihon-u.ac.jp/~momma/wiki/wiki.cgi/OpenCV/Gabor%20Filter.html), which I ported to JavaCV resulting to the code below:

```

    public double computeKernel(int x, int y) {
        double expTerm = Math.exp(-((x * x) + (y * y)) / (2 * VARIANCE));
        double phaseCos = PULSATION * x * Math.cos(PHASE);
        double phaseSin = PULSATION * y * Math.sin(PHASE);
        double cosTerm = Math.cos(phaseCos + phaseSin + PSI);
        return expTerm * cosTerm;
    }
    
    public IplImage evaluateKernel(BufferedImage bi) {
        int colLimit = bi.getWidth();
        int rowLimit = bi.getHeight();

        /*
         * For some reason, bi is sometimes not TYPE_INT_RGB. Following lines of
         * code creates another BufferedImage that is essentially the same as bi
         * but is of TYPE_INT_RGB.
         */
        BufferedImage kernelised = new BufferedImage(colLimit, rowLimit,
              BufferedImage.TYPE_INT_RGB);
        kernelised.getGraphics().drawImage(bi, 0, 0, null);

        IplImage sourceImage = IplImage.createFrom(kernelised);
        IplImage s8u = opencv_core.cvCreateImage(opencv_core.cvSize(colLimit,
                rowLimit), opencv_core.IPL_DEPTH_8U, 1);
        IplImage filtered = opencv_core.cvCreateImage(opencv_core.cvSize(
                colLimit, rowLimit), opencv_core.IPL_DEPTH_32F, 1);

        opencv_imgproc.cvCvtColor(sourceImage, s8u, opencv_imgproc.CV_BGR2GRAY);
        opencv_core.cvCvtScale(s8u, filtered, 1.0 / 255, 0);
        IplImage destination = opencv_core.cvCloneImage(filtered);

        CvMat kernel = CvMat.create(GaborKernel.KERNEL_SIZE,
                GaborKernel.KERNEL_SIZE, opencv_core.CV_32FC1);
        opencv_core.cvZero(kernel);

        // Create the matrix...
        for (int row = -GaborKernel.KERNEL_SIZE / 2; row <= GaborKernel.KERNEL_SIZE / 2; row++) {
            for (int col = -GaborKernel.KERNEL_SIZE / 2; col <= GaborKernel.KERNEL_SIZE / 2; col++) {
                double scalarVal = computeKernel(col, row);
                opencv_core.cvSet2D(kernel, row + GaborKernel.KERNEL_SIZE / 2,
                        col + GaborKernel.KERNEL_SIZE / 2, opencv_core
                                .cvScalar(scalarVal, 0.0, 0.0, 0.0));
            }
        }

        // And apply it for the Gabor Filter effect
        opencv_imgproc.cvFilter2D(filtered, destination, kernel, opencv_core
                .cvPoint(-1, -1));

        // Take the resulting BufferedImage
        opencv_core.cvCvtScale(destination, filtered, 255.0,
                opencv_core.IPL_DEPTH_32F);

        return filtered;
    }

```

which I then ported to MatLab (ran through Octave3.2) which resulted to the following code:

```

    function dest2 = gabor2(I, variance, pulsation, phase, psi)
    if(ndims(I)==3)
    I=rgb2gray(I);
    endif
    src = 0;
    src_f = 0;
    dest = 0;
    dest_mag = 0;
    kernelimg=0;
    big_kernelimg=0;
    kernel_size=21;
    kernel=zeros(kernel_size,kernel_size);
    
     var = variance/10.0;
     w = pulsation/10.0;
     phase = phase*pi/180.0;
     psi = pi*psi/180.0;
     
    for x = (-kernel_size/2+1) : (kernel_size/2+1)
          for y = (-kernel_size/2+1) : (kernel_size/2+1)
                  kernel_val = exp(-((x * x) + (y * y)) / (2 * var)) * cos(w * x * cos(phase) + w * y * sin(phase) + psi);
                  kernel(y + kernel_size / 2, x + kernel_size / 2) = kernel_val;
                  kernelimg(y + kernel_size / 2, x + kernel_size / 2) = (kernel_val / 2 + 0.5);
          endfor
    endfor
    colormap('gray')
    dest2=imfilter(double(I),kernel,"conv");
    imshow(dest2)

```

(The operations on the parameters---`var = variance / 10;`---has been accounted for already in the Java code. Just not shown.)

Now, the contents of dest2 and the returned IplImage vary by a considerable lot. The first few cvScalars in the IplImage contains the following values: `(34.401257, 0.0, 0.0, 0.0)(33.23243, 0.0, 0.0, 0.0)(31.17214, 0.0, 0.0, 0.0)(29.598156, 0.0, 0.0, 0.0)(28.400667, 0.0, 0.0, 0.0)`. Compare that to the first few values in dest2: `2.3535e+02   1.3314e+02   4.2834e+01  -3.1780e+00  -1.0823e+01   5.4880e+00   3.9302e+01`.

The output images aren't similar. To get a similar image, change the second to the last line of the MatLab code to `dest2=imfilter(I,kernel,"conv");` I only wrapped it in double so I'll get floating point values. Not doing so returns integer values in dest2.

Lastly, I've tried all forms of `imfilter` I know. The one with only the first two arguments and the one having "corr" for a third argument but still to no avail.

Is there anything I missed when I translated my code?

---

