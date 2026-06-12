---
title: "Problem finding gnuradio-core"
date: 2013-10-04
forum: Packaging and Compiling Programs
---

### Post by Code9 on 2013-10-04
Hello, 

I am trying to install gr-air-modes, an program that is reliant on gnradio to function. However, during the installation of gr-air-modes, it gives me the following error. 

```

-- Build type not specified: defaulting to release.
-- checking for module 'gnuradio-core'
--   package 'gnuradio-core' not found
-- checking for module 'gnuradio-core'
--   package 'gnuradio-core' not found
-- Could NOT find GNURADIO_CORE (missing:  GNURADIO_CORE_LIBRARIES GNURADIO_CORE_INCLUDE_DIRS) 
CMake Error at CMakeLists.txt:80 (message):
  GnuRadio Core required to compile gr-air-modes

```

I am able to run gnuradio-companion, so I believe it is installed. 

[IMG]http://i.imgur.com/53UB8sy.png[/IMG]


I am running Ubuntu 12.04 LTS inside a virtual machine. Thanks for any help.

---

