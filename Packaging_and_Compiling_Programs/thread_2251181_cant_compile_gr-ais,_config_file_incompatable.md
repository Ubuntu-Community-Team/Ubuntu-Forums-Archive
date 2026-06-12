---
title: "cant compile gr-ais, config file incompatable"
date: 2014-11-02
forum: Packaging and Compiling Programs
---

### Post by sdowney717 on 2014-11-02
```
scott@scott-P5QC:~/gr-ais/build$ cmake ../
-- Build type not specified: defaulting to release.
-- Boost version: 1.54.0
-- Found the following Boost libraries:
--   filesystem
--   system
-- Found Doxygen: /usr/bin/doxygen (found version "1.8.6") 
CMake Error at CMakeLists.txt:94 (find_package):
  Could not find a configuration file for package "Gnuradio" that is
  compatible with requested version "3.7.6".

  The following configuration files were considered but not accepted:

    /usr/lib/x86_64-linux-gnu/cmake/gnuradio/GnuradioConfig.cmake, version: 3.7.2.1



-- Configuring incomplete, errors occurred!
See also "/home/scott/gr-ais/build/CMakeFiles/CMakeOutput.log".
scott@scott-P5QC:~/gr-ais/build$ 

```

following instructions from here
[http://www.reddit.com/r/RTLSDR/comments/1mcikt/for_the_nautical_set_rtlsdr_with_grais_and_opencpn/](http://www.reddit.com/r/RTLSDR/comments/1mcikt/for_the_nautical_set_rtlsdr_with_grais_and_opencpn/)

following from here, i get gruel errors
[http://de8msh.blogspot.com/2012/09/rtl-sdr-toolbox-on-linux-based-os.html](http://de8msh.blogspot.com/2012/09/rtl-sdr-toolbox-on-linux-based-os.html)

---

### Post by oldos2er on 2014-11-02
Moved to Packaging & Compiling Programs.

---

### Post by sdowney717 on 2014-11-03
Solved, the problem is the gnuradio version is too old in the ubuntu repo.

run as super user this in terminal after removing old gnuradio 3.7.2.1

$ wget [http://www.sbrac.org/files/build-gnuradio](http://www.sbrac.org/files/build-gnuradio) && chmod a+x ./build-gnuradio && ./build-gnuradio

From a knowledgeable person answered at askubuntu who wrote a working script.
[http://askubuntu.com/questions/544852/cant-configure-gr-ais](http://askubuntu.com/questions/544852/cant-configure-gr-ais)

---

