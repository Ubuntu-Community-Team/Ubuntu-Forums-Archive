---
title: "c++ &amp; boost porting"
date: 2007-02-07
forum: Programming Talk
---

### Post by MadMan2k on 2007-02-07
Im currently trying to build an application written for an older version of boost, where uniform_real was defined like this:
[http://www-eleves-isia.cma.fr/documentation/BoostDoc/boost_1_29_0/libs/random/random-distributions.html#uniform_real](http://www-eleves-isia.cma.fr/documentation/BoostDoc/boost_1_29_0/libs/random/random-distributions.html#uniform_real)

the new API is this:
[http://www.boost.org/libs/random/random-distributions.html#uniform_real](http://www.boost.org/libs/random/random-distributions.html#uniform_real)

the code snippet is:
```
            boost::uniform_real< rcss::random::DefaultRNG > dir( rcss::random::DefaultRNG::instance(),
                                                                 -M_PI, +M_PI );
            diff = Polar2PVector( post.r, dir() );
```

I changed it like this:

```
            boost::uniform_real<> dir( -M_PI, +M_PI );
            diff = Polar2PVector( post.r, dir(rcss::random::DefaultRNG::instance()) );
```

does it still do the same? I dont really understnand the c++ template syntax...

---

### Post by Mirrorball on 2007-02-07
This example is all you need to understand (it's from the official documentation; it took me awhile to understand it too). Copy it and change what you need:

```

**boost::mt19937** rng; // the generator[B]
boost::uniform_int<>[/B] six(1,6); // the distribution (an int from 1 to 6)
boost::variate_generator<**boost::mt19937&, boost::uniform_int<> **> die(rng, six); // create a callable object
int x = die(); // x will be an int from 1 to 6

```Here is what I think you are trying to do:

```
boost::uniform_real<> distribution( -M_PI, +M_PI );
boost::variate_generator<**boost::mt19937&**, boost::uniform_real<> > dir(rcss::random::defaultRNG::instance(), distribution);
diff = Polar2PVector( post.r, dir() );

```The part in bold depends on what generator you are using.

---

