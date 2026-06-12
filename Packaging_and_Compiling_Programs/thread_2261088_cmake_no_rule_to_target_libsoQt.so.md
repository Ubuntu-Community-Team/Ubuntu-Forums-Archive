---
title: "cmake no rule to target libsoQt.so"
date: 2015-01-16
forum: Packaging and Compiling Programs
---

### Post by nikhil9 on 2015-01-16
first off..apologies I am a newb to ubuntu and this is my first time posting so here goes.
I was following the instructions from this website:

[http://www.roboticslibrary.org/tutorials/first-steps-linux](http://www.roboticslibrary.org/tutorials/first-steps-linux)

Everything worked until i got to the : ***Visualization of a robot manipulator*** step
I created a CMakeLists.txt file:
cmake_minimum_required(VERSION 2.8.11)


project(myViewDemo)


find_package(RL COMPONENTS SG REQUIRED)
find_package(Qt4 REQUIRED)


if(CMAKE_SIZEOF_VOID_P EQUAL 4)
        add_definitions(-DEIGEN_DONT_ALIGN)
endif(CMAKE_SIZEOF_VOID_P EQUAL 4)


add_executable(
        myViewDemo
        myViewDemo.cpp
)
target_compile_definitions(
        myViewDemo
        PUBLIC
        "" ${QT_DEFINITIONS}
)
target_include_directories(
        myViewDemo
        PUBLIC
        ${QT_INCLUDES}
)
target_link_libraries(
        myViewDemo
        ${QT_QTCORE_LIBRARY}
        ${QT_QTGUI_LIBRARY}
        ${QT_QTOPENGL_LIBRARY}
        ${RL_LIBRARIES}
        /usr/lib/libSoQt.so # or /usr/lib/x86_64-linux-gnu/libSoQt.so
)

I then created a file called myViewDemo.cpp:

#include <iostream>
#include <QWidget>
#include <Inventor/SoDB.h>
#include <Inventor/Qt/SoQt.h>
#include <Inventor/Qt/viewers/SoQtExaminerViewer.h>
#include <rl/sg/so/Scene.h>


int
main(int argc, char** argv)
{
        SoDB::init();


        QWidget* widget = SoQt::init(argc, argv, argv[0]);
        widget->resize(800, 600);


        rl::sg::so::Scene scene;
        scene.load("/usr/share/rl/examples/rlsg/unimation-puma560_boxes.xml");


        SoQtExaminerViewer viewer(widget, NULL, true, SoQtFullViewer::BUILD_POPUP);
        viewer.setSceneGraph(scene.root);
        viewer.setTransparencyType(SoGLRenderAction::SORTED_OBJECT_BLEND);
        viewer.show();


        SoQt::show(widget);
        SoQt::mainLoop();


        return 0;
}




Both files were created in a build folder. I ran cmake . . without problem
I then proceeded to run cmake --build .
I got the following error:

[100%] Building CXX object CMakeFiles/myViewDemo.dir/myViewDemo.cpp.o
make[2]: *** No rule to make target `/usr/lib/libSoQt.so', needed by `myViewDemo'. Stop.
make[1]: *** [CMakeFiles/myViewDemo.dir/all] Error 2
make: *** [all] Error 2

---

### Post by nikhil9 on 2015-01-18
realised the issue. at the bottom of the CMakeLists.txt file the following line: [COLOR=#000000]/usr/lib/libSoQt.so # or /usr/lib/x86_64-linux-gnu/libSoQt.so

I needed to select the one or the other target library dependant on whether i was running 64 or 32 bit.


[/COLOR]

---

