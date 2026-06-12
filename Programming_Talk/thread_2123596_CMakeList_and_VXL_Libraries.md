---
title: "CMakeList and VXL Libraries"
date: 2013-03-08
forum: Programming Talk
---

### Post by ZioBafio on 2013-03-08
[FONT=arial]Hi everyone![/FONT]

[FONT=arial]I wish to use vxl in my project, using this classes, contained in vxl libraries[/FONT]

[FONT=arial]contrib/brl/bbas/imesh/imesh_[/FONT][FONT=arial]mesh[/FONT][FONT=arial]contrib/brl/bbas/imesh/imesh_vertex[/FONT]
[FONT=arial]contrib/brl/bbas/imesh/imesh_face


[/FONT]
[FONT=arial]My project has a CMakeList.txt file in which I include also PCL libraries, here is the file's content[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]```

[/FONT]
[FONT=arial]cmake_minimum_required(VERSION 2.8 FATAL_ERROR)


project(MyProject)


find_package(PCL 1.2 REQUIRED)


include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})


add_executable (MyProject MainClass.cpp)


target_link_libraries (MyProject ${PCL_LIBRARIES})

```




I'm not so good with cmake, so my question is: 


How should I modify my CMakeList.txt file in order to include imesh_mesh, imesh_vertex, imesh_face in my project?


I have tried following vxl documentation, but I couldn't manage to have my project work properly.




Thanks for your help!
[/FONT]

---

