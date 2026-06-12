---
title: "Python + pydev + numpy ...."
date: 2011-01-13
forum: Programming Talk
---

### Post by vincentberenz on 2011-01-13
Dear all,

My situation is a little tricky.

I have to work with both pydev and numpy.

I installed ubuntu (11.04) which comes by default with an installation of python.

I am requested to work with another version of python provided by a third party.
so I set my $PYTHONPATH to this other version of python.

Also in pydev in window/preferences/pydev/Interpreter-python I configured the interpreter and the libraries accordingly.

Everything worked just fine so far.

Now here where I get lost.

To get numpy I installed numpy and scipy as follow :
sudo apt-get install python-numpy
sudo apt-get install python-scipy

Then in pydev I added "numpy" in the forced buildins
(get the idea from here [http://old.nabble.com/-pydev---Users--ImportError:-No-module-named-numpy-td21660408.html](http://old.nabble.com/-pydev---Users--ImportError:-No-module-named-numpy-td21660408.html))

It did not work, but in a strange way:
- in pydev, if I type "import nump" and tab, it auto-complete to "numpy"
- but it would not autocomplete to anything if I try "from numpy import "
- and indeed, on run it tells me "ImportError: No module named numpy"
(I am suprised autocompletion works)

As it did not work I looked for numpy and found it in 
/usr/lib/python2.6/dist-packages/numpy/

I added the folder in pydev :
window/preferences/pydev/Interpreter-python

It still did not work.

I am half suprised as the version of python I am using is somewhere else.
Actually I checked the /python2.6/site-packages folder of this other installation and nothing related to numpy could be found there.

I have three questions :

-- how could I install numpy targeting this other version of python ?
-- should I copy /usr/lib/python2.6/dist-packages/numpy/ to [path]/python2.6/site-packages (sounds very ugly)
-- or should I do something completely differently ?

Thanks a lot !

---

### Post by Tony Flury on 2011-01-13
instead of copying the package files - why not do a symbolic link in your alternative Python install that links back to the numpy package in the standard python ? Not sure it will work - but worth a try.

As a matter of interest - what is the rationale for using a version of Python which is not the standard one provided by the system ?

---

### Post by talonmies on 2011-01-13
You probably won't be able to use numpy (or any other compiled python package for that matter) from the Ubuntu repositories with a different Python installation. Packages like numpy are compiled and against linked specific versions of cpython API and runtime libraries, and normally won't work with a different version of Python.

You will probably have to build and install your own numpy instance against the "foreign" version of python you wish to use.

---

### Post by vincentberenz on 2011-01-13
thanks for your answers !

@talonmies
sounds like you are right, even if I have to confess I was hoping to get another answer. Reading the doc for installation of numpy, I am not sure I will get to understand how to direct it to a specific instance of python. Wish me good luck :-) Any advice is also truly welcomed !

@tony
I'll try the symbolic link first ! 
The rational is that I am working with a Nao robot and Aldebaran request to use their version of python. I am not sure what the difference between the official 2.6 and their 2.6 version. But the thing is when using their version the libraries needed to control the robot are successfully imported (my guess is that also makes sure python code written on the pc will work in the robot, but in that case my scripts will all run on my pc)

I'll try in a few days !

---

### Post by enuckon on 2011-04-25
> **talonmies said:**
> You probably won't be able to use numpy (or any other compiled python package for that matter) from the Ubuntu repositories with a different Python installation...
You will probably have to build and install your own numpy instance against the "foreign" version of python you wish to use.

Thanks for the info!  I have two versions of python on Intrepid, 2.5 and 3.2.  After installation, numpy only imports from the "native" 2.5.  Would you have the links to instructions how to build against the "foreign" 3.2? Thanks again.

---

### Post by lavinog on 2011-04-25
> **vincentberenz said:**
> 
I am requested to work with another version of python provided by a third party.

What version do you need to use? 2.6?
Are you sure you can't use 2.7 (included in 11.04)

---

