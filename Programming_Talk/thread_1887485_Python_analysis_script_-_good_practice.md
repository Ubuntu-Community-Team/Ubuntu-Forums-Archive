---
title: "Python analysis script - good practice"
date: 2011-11-27
forum: Programming Talk
---

### Post by abraxas334 on 2011-11-27
I seem to be encountering this problem alot and never know which is the best solution to it.
I have a simulation or data set I want to look at with different parameters. For the sake of the example: I have 4 different data sets I want to analyse with a python script.  In my analysis script i need to subsample the data (i.e. throw out every x points) and use some kind of histogram binning and therefore have a certain number of bins. 
Now I want to do the analysis with some different subsampling (every 10th 20th 50th..etc datapoint) and number of bins for all different data sets.
Is it best to run the python analysis script many times each time changing one of the arguments, assuming that my three arguments are the choice of dataset the number of subsmples and the number of bins, or should I just put the name of the dataset into the command line and declare arrays within the script of the different number of bins and subsamples I am interested in and thus only run the script 4 times for each dataset as I am looping over my arrays internally
I have this kind of issue alot and I never know which is the best approach to take? Is there a good way of knowing/deciding?
Or is there a different approach all together?

---

### Post by MadCow108 on 2011-11-27
I don't quite get the question. your asking whether too loop the script calling a function of calling the function in a loop in the script?
its both the same, just a matter of interface to your function.
the latter case is often more flexible as you can reuse the result in the same script instead of having to write it to a file and opening that file again in the next step.

keep your function modular and you can add any interface you like on top of it later.

here both ways (parallized for good measure ;) )
```
import numpy
import multiprocessing

def run_analysis(args):
  data, l, h, stride = args
  return numpy.random.normal(size=((l-h),))[::stride]*data[l:h:stride]

if __name__ == "__main__":
  p = multiprocessing.Pool(4)
  params = [(numpy.random.uniform(size=(500,)), 0, 250, 1),
            (numpy.random.uniform(size=(500,)), 0, 250, 2),
            (numpy.random.uniform(size=(500,)), 0, 250, 4),
            (numpy.random.uniform(size=(500,)), 0, 250, 10)
          ]
  # run all options in loop
  res = p.map(run_analysis, params)
  print [x.shape for x in res]
  
  # run once dependend on arguments
  import sys
  args = [numpy.random.uniform(size=(500,)),] + map(int, sys.argv[1:])
  res = run_analysis(args)
  print res.shape

```

---

### Post by ofnuts on 2011-11-27
> **abraxas334 said:**
> I seem to be encountering this problem alot and never know which is the best solution to it.
I have a simulation or data set I want to look at with different parameters. For the sake of the example: I have 4 different data sets I want to analyse with a python script.  In my analysis script i need to subsample the data (i.e. throw out every x points) and use some kind of histogram binning and therefore have a certain number of bins. 
Now I want to do the analysis with some different subsampling (every 10th 20th 50th..etc datapoint) and number of bins for all different data sets.
Is it best to run the python analysis script many times each time changing one of the arguments, assuming that my three arguments are the choice of dataset the number of subsmples and the number of bins, or should I just put the name of the dataset into the command line and declare arrays within the script of the different number of bins and subsamples I am interested in and thus only run the script 4 times for each dataset as I am looping over my arrays internally
I have this kind of issue alot and I never know which is the best approach to take? Is there a good way of knowing/deciding?
Or is there a different approach all together?
I would go the "keep the code simple" route and rerun the program with different parms each time, unless there is  a very compelling reason not to do so: very heavy disk I/O that are reduced if runs are combined, or heavy computation that could be shared.

---

### Post by abraxas334 on 2011-11-27
Thanks everyone! These comments have been very useful :)

---

