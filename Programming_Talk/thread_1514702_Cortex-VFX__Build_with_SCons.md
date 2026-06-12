---
title: "Cortex-VFX : Build with SCons"
date: 2010-06-21
forum: Programming Talk
---

### Post by ashmaston on 2010-06-21
Hello all,

I am trying to build the Cortex-VFX library. SCons was used to handle the build part. I seem to miss something though.

Here is where i have a problem :

[I]if not c.CheckLibWithHeader( env.subst( "boost_iostreams" + env["BOOST_LIB_SUFFIX"] ), "boost/filesystem/path.hpp", "CXX" ) :
sys.stderr.write( "ERROR : unable to find the boost libraries - check BOOST_LIB_PATH.\n" )
Exit( 1 )[/I]

I've installed all the boost headers and libraries and i still get this message :

[I]Checking for C++ library boost_iostreams-1_38_... no
ERROR : unable to find the boost libraries - check BOOST_LIB_PATH.
[/I]
I've set the right path to boost libs : */usr/local/lib*. For example : *libboost_iostreams-gcc43-mt-1_38.so*

I am stuck, i've read the SCons but i can't see anything wrong in my configuration. Is there anyone with a good grasp on SCons who could help me ?

Thanks a lot.

Cheers,

Ash

---

