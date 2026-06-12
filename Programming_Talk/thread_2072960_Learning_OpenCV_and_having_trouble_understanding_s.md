---
title: "Learning OpenCV and having trouble understanding some code"
date: 2012-10-18
forum: Programming Talk
---

### Post by faraz_k86 on 2012-10-18
Hi,

Im learning openCV and am following the official documentation. I am at the histogram calculation and was having no trouble understanding the code until the time came to plot the calculated histogram.

The tutorial I am talking about is here: [http://docs.opencv.org/doc/tutorials/imgproc/histograms/histogram_calculation/histogram_calculation.html](http://docs.opencv.org/doc/tutorials/imgproc/histograms/histogram_calculation/histogram_calculation.html)

and the section that confuses me is this one:

```
/// Draw for each channel
for( int i = 1; i < histSize; i++ )
{
    line( histImage, Point( bin_w*(i-1), hist_h - cvRound(b_hist.at<float>(i-1)) ) ,
                     Point( bin_w*(i), hist_h - cvRound(b_hist.at<float>(i)) ),
                     Scalar( 255, 0, 0), 2, 8, 0  );
    line( histImage, Point( bin_w*(i-1), hist_h - cvRound(g_hist.at<float>(i-1)) ) ,
                     Point( bin_w*(i), hist_h - cvRound(g_hist.at<float>(i)) ),
                     Scalar( 0, 255, 0), 2, 8, 0  );
    line( histImage, Point( bin_w*(i-1), hist_h - cvRound(r_hist.at<float>(i-1)) ) ,
                     Point( bin_w*(i), hist_h - cvRound(r_hist.at<float>(i)) ),
                     Scalar( 0, 0, 255), 2, 8, 0  );
}
```

i know the line function and the arguments taken by it, the thing I dont get is the values given to its point 1 and point 2.

Can some one please explain to me what is happening in the line function at point 1 and point 2.

Thank you

---

