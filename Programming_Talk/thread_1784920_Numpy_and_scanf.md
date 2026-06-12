---
title: "Numpy and scanf"
date: 2011-06-17
forum: Programming Talk
---

### Post by wannabegeek on 2011-06-17
[URL="http://stackoverflow.com/questions/6391195/numpy-and-scanf-equivalents-turning-binary-output-stream-into-an-array#"]
[/URL]           
                                                            Hi all,


I am using the  linux-gpib library and the python bindings, to talk to a piece of bench equipment, a VNA. I can ask the device for output from it's buffer, and it streams to std out. I use something like:
```


  >>>import gpib 
    >>>gpib.write(16,"FORM3;OUTPDATA;") #FORM3 is binary
>>>data=gpib.read(16,10000)
  
```

I'm not sure what the output format looks like, I forgot how the data is delimited. But I figure I need to do some kind of scanf function to grab the floats and put them into  an array.
  I installed numpy, and think there should be a way to ask python to do this.

  

Google hasn't helped much, numpy is really new to me. I know the MATLAB and C command is scanf.


I'll be in the lab later today or over the weekend and will
post more details.

  

thank you in advance,
 wbg

---

