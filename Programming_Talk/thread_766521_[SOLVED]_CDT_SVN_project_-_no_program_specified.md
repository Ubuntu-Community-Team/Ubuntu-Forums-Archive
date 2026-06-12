---
title: "[SOLVED] CDT SVN project - no program specified"
date: 2008-04-25
forum: Programming Talk
---

### Post by _sluimers_ on 2008-04-25
I can build the project but not run it, due to missing executable file for the C/C++ application.

This is what the console gives:
```

**** Build of configuration Debug for project ObjectViewer ****

make all 
Building file: ../Camera.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Camera.d" -MT"Camera.d" -o"Camera.o" "../Camera.cpp"
Finished building: ../Camera.cpp
 
Building file: ../Cube.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Cube.d" -MT"Cube.d" -o"Cube.o" "../Cube.cpp"
Finished building: ../Cube.cpp
 
Building file: ../ImportedModel.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"ImportedModel.d" -MT"ImportedModel.d" -o"ImportedModel.o" "../ImportedModel.cpp"
../ImportedModel.cpp: In member function &#8216;void ImportedModel::load(char*)&#8217;:
../ImportedModel.cpp:133: warning: comparison between signed and unsigned integer expressions
../ImportedModel.cpp:136: warning: comparison between signed and unsigned integer expressions
Finished building: ../ImportedModel.cpp
 
Building file: ../KeyBoardHandler.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"KeyBoardHandler.d" -MT"KeyBoardHandler.d" -o"KeyBoardHandler.o" "../KeyBoardHandler.cpp"
Finished building: ../KeyBoardHandler.cpp
 
Building file: ../Light.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Light.d" -MT"Light.d" -o"Light.o" "../Light.cpp"
Finished building: ../Light.cpp
 
Building file: ../Model.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Model.d" -MT"Model.d" -o"Model.o" "../Model.cpp"
../Model.cpp:41:2: warning: no newline at end of file
Finished building: ../Model.cpp
 
Building file: ../ModelViewer.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"ModelViewer.d" -MT"ModelViewer.d" -o"ModelViewer.o" "../ModelViewer.cpp"
Finished building: ../ModelViewer.cpp
 
Building file: ../MouseHandler.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"MouseHandler.d" -MT"MouseHandler.d" -o"MouseHandler.o" "../MouseHandler.cpp"
../MouseHandler.cpp:66:2: warning: no newline at end of file
Finished building: ../MouseHandler.cpp
 
Building file: ../OpenGlWindow.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"OpenGlWindow.d" -MT"OpenGlWindow.d" -o"OpenGlWindow.o" "../OpenGlWindow.cpp"
Finished building: ../OpenGlWindow.cpp
 
Building file: ../Pixmap.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Pixmap.d" -MT"Pixmap.d" -o"Pixmap.o" "../Pixmap.cpp"
../Pixmap.cpp:84:2: warning: no newline at end of file
../Pixmap.cpp: In member function &#8216;void pixmap::read(const char*)&#8217;:
../Pixmap.cpp:66: warning: comparison between signed and unsigned integer expressions
Finished building: ../Pixmap.cpp
 
Building file: ../Point.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Point.d" -MT"Point.d" -o"Point.o" "../Point.cpp"
Finished building: ../Point.cpp
 
Building file: ../Prisma.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Prisma.d" -MT"Prisma.d" -o"Prisma.o" "../Prisma.cpp"
Finished building: ../Prisma.cpp
 
Building file: ../Pyramid.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Pyramid.d" -MT"Pyramid.d" -o"Pyramid.o" "../Pyramid.cpp"
Finished building: ../Pyramid.cpp
 
Building file: ../TextureManager.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"TextureManager.d" -MT"TextureManager.d" -o"TextureManager.o" "../TextureManager.cpp"
../TextureManager.cpp:50:2: warning: no newline at end of file
Finished building: ../TextureManager.cpp
 
Building file: ../UserInputController.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"UserInputController.d" -MT"UserInputController.d" -o"UserInputController.o" "../UserInputController.cpp"
Finished building: ../UserInputController.cpp
 
Building file: ../main.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"main.d" -MT"main.d" -o"main.o" "../main.cpp"
Finished building: ../main.cpp
 
Building target: ObjectViewer
Invoking: GCC C++ Linker
g++  -o"ObjectViewer"  ./Camera.o ./Cube.o ./ImportedModel.o ./KeyBoardHandler.o ./Light.o ./Model.o ./ModelViewer.o ./MouseHandler.o ./OpenGlWindow.o ./Pixmap.o ./Point.o ./Prisma.o ./Pyramid.o ./TextureManager.o ./UserInputController.o ./main.o   -lfltk_gl -lfltk -lGL -lGLU
Finished building target: ObjectViewer


```

Makefiles are present in the debug folder, just no executable.

:confused: why?

[edit]Oh errr... that's supposed to be 'program not specified' in the title.[/edit]

---

