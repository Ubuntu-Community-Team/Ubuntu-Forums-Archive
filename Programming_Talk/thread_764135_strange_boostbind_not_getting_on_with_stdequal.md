---
title: "strange: boost::bind not getting on with std::equal"
date: 2008-04-23
forum: Programming Talk
---

### Post by dbd on 2008-04-23
Hey,

I'm getting some strange complaints from the compiler when I use boost::bind in std::equal, for example, when I attempt to compile this: 

```
using namespace std;
using namespace boost;

bool NeuralNet::outputCorrect(const vector<float>* expectedOutput)
{
	return( equal(expectedOutput->begin(), expectedOutput->end(), m_outputLayer->begin(), bind(&NeuralNet::differenceSmallEnough, this, _1, _2)) );
}
```

I get the error:
```
/usr/include/boost/bind.hpp:1130: error: 'struct boost::_bi::equal' is not a function,
/usr/include/c++/4.2/bits/stl_algobase.h:772: error: conflict with 'template<class _InputIterator1, class _InputIterator2> bool std::equal(_InputIterator1, _InputIterator1, _InputIterator2)'
/home/mezz/programming/myproject/NeuralNet/src/neuralnet.cpp:173: error: in call to 'equal'
```

It seems that boost is trying to override stl's equal with its own, so to make it compile I have to use std::equal instead of just equal. No big deal, but it's strange.

Now, I've only just started to discover the wonders of boost, and it's only recently that I've started to start using anything other than the most basic stl algorithms, so I may have missed something obvious, but this behaviour seems very strange to me. Surely boost shouldn't get in the way of stl, I'm almost tempted to cry "bug"!

Also, what's even more strange is when I compile this same code in MS Visual Studio 2005 it works fine without the std::, and I wouldn't have thought the compiler has anything to do with that. I'm using the same version of boost (1.34.1) The only difference with the VS version is that I had to include stdafx.h (which does windows lean and mean, as if windows could ever be "lean"!), but that shouldn't make a difference either, should it?

As I said, I'm a bit new to this boost lark, so maybe this is nothing strange at all, so I'd be interested if anyone could explain what is going on?

By the way, I'm using KDevelop, with gcc-4.2.3, in Hardy Heron KDE4

Cheers

dbd

---

