---
title: "Errors while compiling - mv cannot stat &quot;no such file or folder&quot;"
date: 2023-03-31
forum: New to Ubuntu
---

### Post by KosmicheCam on 2023-03-31
version: 22.04.2 LTS from within Windows Linux Subsystem terminal (no GUI)

Hi everyone, I am new to Ubuntu, and using the OS within a Windows terminal to run geoprocessing scripts.

Could someone please point me in the right direction to solve this error I am getting while compiling code? There appears to be an issue outputting 2 files.

If there is any other information needed to diagnose, please let me know.
Many thanks!

```
(base) camer_fro@UHAArky:/mnt/d/LSDTopoTools/Git_projects/LSDTopoTools_FloodplainTerraceExtraction/driver_functions_Floodplains-Terraces$ bash -x get_terraces.sh
+ mkdir -p build/
+ cd build/
+ cp ../CMakeLists_get_terraces.txt CMakeLists.txt
+ cmake .
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 2.8.12 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Eigen found (include: /usr/include/eigen3, version: 3.4.0)
-- FLANN found (include: /usr/include, lib: /usr/lib/x86_64-linux-gnu/libflann_cpp.so)
-- OpenNI found (version: 1.5.4.0, include: /usr/include/ni, lib: /usr/lib/libOpenNI.so;libusb::libusb)
-- OpenNI2 found (version: 2.2.0.33, include: /usr/include/openni2, lib: /usr/lib/x86_64-linux-gnu/libOpenNI2.so;libusb::libusb)
** WARNING ** io features related to pcap will be disabled
-- Eigen found (include: /usr/include/eigen3, version: 3.4.0)
-- OpenNI found (version: 1.5.4.0, include: /usr/include/ni, lib: /usr/lib/libOpenNI.so;libusb::libusb)
-- OpenNI2 found (version: 2.2.0.33, include: /usr/include/openni2, lib: /usr/lib/x86_64-linux-gnu/libOpenNI2.so;libusb::libusb)
-- Found Qhull version 8.0.2
-- OpenNI found (version: 1.5.4.0, include: /usr/include/ni, lib: /usr/lib/libOpenNI.so;libusb::libusb)
-- looking for PCL_COMMON
-- looking for PCL_KDTREE
-- looking for PCL_OCTREE
-- looking for PCL_SEARCH
-- looking for PCL_SAMPLE_CONSENSUS
-- looking for PCL_FILTERS
-- looking for PCL_2D
-- looking for PCL_GEOMETRY
-- looking for PCL_IO
-- looking for PCL_FEATURES
-- looking for PCL_ML
-- looking for PCL_SEGMENTATION
-- looking for PCL_VISUALIZATION
-- looking for PCL_SURFACE
-- looking for PCL_REGISTRATION
-- looking for PCL_KEYPOINTS
-- looking for PCL_TRACKING
-- looking for PCL_RECOGNITION
-- looking for PCL_STEREO
-- looking for PCL_APPS
-- looking for PCL_IN_HAND_SCANNER
-- looking for PCL_MODELER
-- looking for PCL_POINT_CLOUD_EDITOR
-- looking for PCL_OUTOFCORE
-- looking for PCL_PEOPLE
-- Configuring done
-- Generating done
-- Build files have been written to: /mnt/d/LSDTopoTools/Git_projects/LSDTopoTools_FloodplainTerraceExtraction/driver_functions_Floodplains-Terraces/build
+ make
Consolidate compiler generated dependencies of target get_terraces.out
[  6%] Building CXX object CMakeFiles/get_terraces.out.dir/mnt/d/LSDTopoTools/Git_projects/LSDTopoTools_FloodplainTerraceExtraction/LSDJunctionNetwork.cpp.o
/mnt/d/LSDTopoTools/Git_projects/LSDTopoTools_FloodplainTerraceExtraction/LSDJunctionNetwork.cpp: In member function ‘void LSDJunctionNetwork::write_valley_hilltop_chi_profiles_to_csv(std::vector<int>, float, float, LSDFlowInfo&, LSDRaster&, LSDRaster&, int, std::string, std::string)’:
/mnt/d/LSDTopoTools/Git_projects/LSDTopoTools_FloodplainTerraceExtraction/LSDJunctionNetwork.cpp:2839:80: error: taking address of rvalue [-fpermissive]
 2839 |                 string jn_str = static_cast<ostringstream*>( &(ostringstream() << source_junction) )->str();
      |                                                               ~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~
make[2]: *** [CMakeFiles/get_terraces.out.dir/build.make:188: CMakeFiles/get_terraces.out.dir/mnt/d/LSDTopoTools/Git_projects/LSDTopoTools_FloodplainTerraceExtraction/LSDJunctionNetwork.cpp.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:83: CMakeFiles/get_terraces.out.dir/all] Error 2
make: *** [Makefile:91: all] Error 2
+ mv get_terraces.out ../
mv: cannot stat 'get_terraces.out': No such file or directory
+ cd ..
```

---

### Post by TheFu on 2023-03-31
> **KosmicheCam said:**
>  
```

-- Generating done
-- Build files have been written to: /mnt/d/LSDTopoTools/Git_projects/LSDTopoTools_FloodplainTerraceExtraction/driver_functions_Floodplains-Terraces/build
+ make
Consolidate compiler generated dependencies of target get_terraces.out
[  6%] Building CXX object CMakeFiles/get_terraces.out.dir/mnt/d/LSDTopoTools/Git_projects/LSDTopoTools_FloodplainTerraceExtraction/LSDJunctionNetwork.cpp.o
/mnt/d/LSDTopoTools/Git_projects/LSDTopoTools_FloodplainTerraceExtraction/LSDJunctionNetwork.cpp: In member function ‘void LSDJunctionNetwork::write_valley_hilltop_chi_profiles_to_csv(std::vector<int>, float, float, LSDFlowInfo&, LSDRaster&, LSDRaster&, int, std::string, std::string)’:
/mnt/d/LSDTopoTools/Git_projects/LSDTopoTools_FloodplainTerraceExtraction/LSDJunctionNetwork.cpp:2839:80: error: taking address of rvalue [-fpermissive]
 2839 |                 string jn_str = static_cast<ostringstream*>( &(ostringstream() << source_junction) )->str();
      |                                                               ~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~
make[2]: *** [CMakeFiles/get_terraces.out.dir/build.make:188: CMakeFiles/get_terraces.out.dir/mnt/d/LSDTopoTools/Git_projects/LSDTopoTools_FloodplainTerraceExtraction/LSDJunctionNetwork.cpp.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:83: CMakeFiles/get_terraces.out.dir/all] Error 2
make: *** [Makefile:91: all] Error 2
+ mv get_terraces.out ../
**mv: cannot stat 'get_terraces.out': No such file or directory**
+ cd ..
```

The mv error just means that the get_terraces.out file wasn't created by the build process.  It isn't worth any time. This error is downstream of the real error.

I'm too old to know the C++ STD::Templates, but it looks like the code in LSDJunctionNetwork.cpp at line 2839 isn't the correct for the C++ version on your system. That could be the compiler version or it could be the version of the STD templates.  The compiling of LSDJunctionNetwork.cpp into LSDJunctionNetwork.cpp.o is failing.  When I was writing C++ code, Std::Templates were just starting. We used RogueWave C++ libraries in all our code.  I did hear that after I left the company, they switched over, so I was just at the cusp for when that massive change happened and the RogueWave company effectively died.

There are a number of things that look odd to me in how this build is going, but perhaps that's the way the kids do it today? Old people like me would compile LSDJunctionNetwork.cpp ---> LSDJunctionNetwork.o, then we'd take all the dependent .o files and link them into the specific program we wanted ... and it wouldn't have .out as an extension.  Our Makefile would handle that stuff.  These days, the kids use CMake, not Make/GnuMake. Similar tools, but different enough.  

Bottom line. If you can fix the root issue with LSDJunctionNetwork.cpp, then the make and mv will work.  You'll probably need a C++ person who knows the issue with this line:
```
string jn_str = static_cast<ostringstream*>( &(ostringstream() << source_junction) )->str();
```
That is a complex statement with templates, pointers, references, inheritance, and overloaded operators.  I'd probably check that the type of the source_junction variable can be passed into the ostringstream '<<' operator AND that can be converted to a string.  Pay attention to the 'const'ness. That can be important for things like this.  [https://cplusplus.com/reference/ostream/ostream/operator%3C%3C/](https://cplusplus.com/reference/ostream/ostream/operator%3C%3C/)

---

### Post by TheFu on 2023-03-31
BTW, this is less a Linux question and more a C++ question.

---

