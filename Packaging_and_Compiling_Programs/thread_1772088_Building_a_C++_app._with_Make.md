---
title: "Building a C++ app. with Make"
date: 2011-05-31
forum: Packaging and Compiling Programs
---

### Post by ElSafti on 2011-05-31
Hi

I try to build a software (first timer) and I can build libraries but not the binaries : ( 

I get the error:

```
numubuntu@numubuntu-System-Product-Name: ~/OpenSees$ make OpenSees
Building OpenSees Program ..
make[1] : Entering directory `/home/numubuntu/OpenSees/SRC/tcl'
make[1] : Nothing to be done for `tcl'.
make[1] : Leaving directory `/home/numubuntu/OpenSees/SRC/tcl'
make[1] : Entering directory `/home/numubuntu/OpenSees/SRC/modelbuilder/tcl'
Makefile: 30 : warning: overriding commands for target `tcl'
Makefile: 13 : warning: ignoring old commands for target `tcl'
Makefile: 41 : warning: overriding commands for target `tk'
Makefile: 21 : warning: ignoring old commands for target `tk'
make[2] : Entering directory `/home/numubuntu/OpenSees/SRC/tcl'
make[2] : Nothing to be done for `tk'.
make[2] : Leaving directory `/home/numubuntu/OpenSees/SRC/tcl'
/home/numubuntu/OpenSees/SRC/tcl/tkMain.o : In function `Tk_MainOpenSees(int, char**, int (*)(Tcl_Interp*), Tcl_Interp*)':
tkMain.cpp: (.text+0x468) : undefined reference to `Tk_MainLoop'
tkMain.cpp: (.text+0x4f1) : undefined reference to `TkpDisplayWarning'
tkMain.cpp: (.text+0x578) : undefined reference to `TkpDisplayWarning'
/home/numubuntu/OpenSees/SRC/tcl/tkAppInit.o : In function `Tcl_AppInit':
tkAppInit.cpp: (.text+0x12): undefined reference to `Tk_Init'
tkAppInit.cpp: (.text+0x1c): undefined reference to `Tk_SafeInit'
tkAppInit.cpp: (.text+0x21): undefined reference to `Tk_Init'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o: In function `TclFeViewer_saveImage(void*, Tcl_Interp*, int, char const**)':
TclFeViewer.cpp: (.text+0x98b): undefined reference to `Renderer: : saveImage(char const*, char const*)'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o: In function `TclFeViewer: : TclFeViewer(char const*, int, int, int, int, char const*, Domain&, Tcl_Interp*)':
TclFeViewer.cpp: (.text+0xd23): undefined reference to `OpenGLRenderer:: OpenGLRenderer(char const*, int, int, int, int, ColorMap&, char const*, char const*)'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o : In function `TclFeViewer :: TclFeViewer(char const*, int, int, int, int, char const*, Domain&, Tcl_Interp*)':
TclFeViewer.cpp: (.text+0xf73): undefined reference to `OpenGLRenderer:: OpenGLRenderer(char const*, int, int, int, int, ColorMap&, char const*, char const*)'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o : In function `TclFeViewer:: TclFeViewer(char const*, int, int, int, int, Domain&, int, Tcl_Interp*)' :
TclFeViewer.cpp:(.text+0x11ad): undefined reference to `OpenGLRenderer::OpenGLRenderer(char const*, int, int, int, int, ColorMap&)'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o: In function `TclFeViewer::TclFeViewer(char const*, int, int, int, int, Domain&, int, Tcl_Interp*)':
TclFeViewer.cpp:(.text+0x13dd): undefined reference to `OpenGLRenderer::OpenGLRenderer(char const*, int, int, int, int, ColorMap&)'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o: In function `TclFeViewer::saveImage(char const*, char const*)':
TclFeViewer.cpp:(.text+0x825): undefined reference to `Renderer::saveImage(char const*, char const*)'
/home/numubuntu/OpenSees/SRC/tcl/TclVideoPlayer.o: In function `TclVideoPlayer::TclVideoPlayer(char const*, char const*, char const*, Tcl_Interp*, char const*, double)':
TclVideoPlayer.cpp:(.text+0xe9e): undefined reference to `OpenGLRenderer::OpenGLRenderer(char const*, int, int, int, int, ColorMap&)'
/home/numubuntu/OpenSees/SRC/tcl/TclVideoPlayer.o: In function `TclVideoPlayer::TclVideoPlayer(char const*, char const*, char const*, Tcl_Interp*, char const*, double)':
TclVideoPlayer.cpp:(.text+0x14de): undefined reference to `OpenGLRenderer::OpenGLRenderer(char const*, int, int, int, int, ColorMap&)'
/home/numubuntu/lib/libOpenSees.a(AMDNumberer.o): In function `AMD::number(Graph&, int)':
AMDNumberer.cpp:(.text+0x18a): undefined reference to `amd_order'
/home/numubuntu/lib/libOpenSees.a(TclRecorderCommands.o): In function `TclCreateRecorder(void*, Tcl_Interp*, int, char const**, Domain&, Recorder**)':
TclRecorderCommands.cpp:(.text+0x27e4): undefined reference to `FilePlotter::FilePlotter(char const*, char const*, int, int, int, int, double)'
TclRecorderCommands.cpp:(.text+0x27fa): undefined reference to `FilePlotter::setCol(ID const&)'
TclRecorderCommands.cpp:(.text+0x2a4b): undefined reference to `FilePlotter::FilePlotter(char const*, char const*, char const*, int, int, int, int, double)'
TclRecorderCommands.cpp:(.text+0x2a61): undefined reference to `FilePlotter::setCol(ID const&)'
TclRecorderCommands.cpp:(.text+0x2bda): undefined reference to `AlgorithmIncrements::AlgorithmIncrements(EquiSolnAlgo*, char const*, int, int, int, int, bool, char const*)'
/home/numubuntu/lib/libOpenSees.a(InelasticYS2DGNL.o): In function `InelasticYS2DGNL::createView(char*, double, int, int, int, int, char)':
InelasticYS2DGNL.cpp:(.text+0x120b): undefined reference to `OpenGLRenderer::OpenGLRenderer(char const*, int, int, int, int, ColorMap&)'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Cartcomm::Clone() const':
MumpsSOE.cpp:(.text._ZNK3MPI8Cartcomm5CloneEv[MPI::Cartcomm::Clone() const]+0x24): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Graphcomm::Clone() const':
MumpsSOE.cpp:(.text._ZNK3MPI9Graphcomm5CloneEv[MPI::Graphcomm::Clone() const]+0x24): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Intercomm::Merge(bool)':
MumpsSOE.cpp:(.text._ZN3MPI9Intercomm5MergeEb[MPI::Intercomm::Merge(bool)]+0x26): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Op::Init(void (*)(void const*, void*, int, MPI::Datatype const&), bool)':
MumpsSOE.cpp:(.text._ZN3MPI2Op4InitEPFvPKvPviRKNS_8DatatypeEEb[MPI::Op::Init(void (*)(void const*, void*, int, MPI::Datatype const&), bool)]+0x1f): undefined reference to `ompi_mpi_cxx_op_intercept'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Intracomm::Create_graph(int, int const*, int const*, bool) const':
MumpsSOE.cpp:(.text._ZNK3MPI9Intracomm12Create_graphEiPKiS2_b[MPI::Intracomm::Create_graph(int, int const*, int const*, bool) const]+0x27): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Intracomm::Create_cart(int, int const*, bool const*, bool) const':
MumpsSOE.cpp:(.text._ZNK3MPI9Intracomm11Create_cartEiPKiPKbb[MPI::Intracomm::Create_cart(int, int const*, bool const*, bool) const]+0x87): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Cartcomm::Sub(bool const*)':
MumpsSOE.cpp:(.text._ZN3MPI8Cartcomm3SubEPKb[MPI::Cartcomm::Sub(bool const*)]+0x83): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Intracomm::Clone() const':
MumpsSOE.cpp:(.text._ZNK3MPI9Intracomm5CloneEv[MPI::Intracomm::Clone() const]+0x27): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Intracomm::Split(int, int) const':
MumpsSOE.cpp:(.text._ZNK3MPI9Intracomm5SplitEii[MPI::Intracomm::Split(int, int) const]+0x24): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o:MumpsSOE.cpp:(.text._ZNK3MPI9Intracomm6CreateERKNS_5GroupE[MPI::Intracomm::Create(MPI::Group const&) const]+0x27): more undefined references to `MPI::Comm::Comm()' follow
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o:(.rodata._ZTVN3MPI3WinE[vtable for MPI::Win]+0x48): undefined reference to `MPI::Win::Free()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o:(.rodata._ZTVN3MPI8DatatypeE[vtable for MPI::Datatype]+0x78): undefined reference to `MPI::Datatype::Free()'
collect2: ld returned 1 exit status
make[1]: *** [tk] Error 1
make[1]: Leaving directory `/home/numubuntu/OpenSees/SRC/modelbuilder/tcl'
make: *** [tcl] Error 2
numubuntu@numubuntu-System-Product-Name:~/OpenSees$ make OpenSees
Building OpenSees Program ..
make[1] : Entering directory `/home/numubuntu/OpenSees/SRC/tcl'
make[1] : Nothing to be done for `tcl'.
make[1] : Leaving directory `/home/numubuntu/OpenSees/SRC/tcl'
make[1] : Entering directory `/home/numubuntu/OpenSees/SRC/modelbuilder/tcl'
Makefile:30: warning: overriding commands for target `tcl'
Makefile:13: warning: ignoring old commands for target `tcl'
Makefile:41: warning: overriding commands for target `tk'
Makefile:21: warning: ignoring old commands for target `tk'
make[2] : Entering directory `/home/numubuntu/OpenSees/SRC/tcl'
make[2] : Nothing to be done for `tk'.
make[2] : Leaving directory `/home/numubuntu/OpenSees/SRC/tcl'
/home/numubuntu/OpenSees/SRC/tcl/tkMain.o: In function `Tk_MainOpenSees(int, char**, int (*)(Tcl_Interp*), Tcl_Interp*)' :
tkMain.cpp:(.text+0x468) : undefined reference to `Tk_MainLoop'
tkMain.cpp:(.text+0x4f1) : undefined reference to `TkpDisplayWarning'
tkMain.cpp:(.text+0x578): undefined reference to `TkpDisplayWarning'
/home/numubuntu/OpenSees/SRC/tcl/tkAppInit.o: In function `Tcl_AppInit' :
tkAppInit.cpp: (.text+0x12) : undefined reference to `Tk_Init'
tkAppInit.cpp: (.text+0x1c) : undefined reference to `Tk_SafeInit'
tkAppInit.cpp : (.text+0x21) : undefined reference to `Tk_Init'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o: In function `TclFeViewer_saveImage(void*, Tcl_Interp*, int, char const**)' :
TclFeViewer.cpp : (.text+0x98b): undefined reference to `Renderer::saveImage(char const*, char const*)'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o : In function `TclFeViewer :: TclFeViewer(char const*, int, int, int, int, char const*, Domain&, Tcl_Interp*)' :
TclFeViewer.cpp : (.text+0xd23): undefined reference to `OpenGLRenderer :: OpenGLRenderer(char const*, int, int, int, int, ColorMap&, char const*, char const*)'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o : In function `TclFeViewer :: TclFeViewer(char const*, int, int, int, int, char const*, Domain&, Tcl_Interp*)' :
TclFeViewer.cpp : (.text+0xf73) : undefined reference to `OpenGLRenderer :: OpenGLRenderer(char const*, int, int, int, int, ColorMap&, char const*, char const*)'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o : In function `TclFeViewer :: TclFeViewer(char const*, int, int, int, int, Domain&, int, Tcl_Interp*)':
TclFeViewer.cpp : (.text+0x11ad): undefined reference to `OpenGLRenderer :: OpenGLRenderer(char const*, int, int, int, int, ColorMap&)'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o : In function `TclFeViewer :: TclFeViewer(char const*, int, int, int, int, Domain&, int, Tcl_Interp*)' :
TclFeViewer.cpp: (.text+0x13dd) : undefined reference to `OpenGLRenderer:: OpenGLRenderer(char const*, int, int, int, int, ColorMap&)'
/home/numubuntu/OpenSees/SRC/tcl/TclFeViewer.o : In function `TclFeViewer::saveImage(char const*, char const*)' :
TclFeViewer.cpp : (.text+0x825) : undefined reference to `Renderer::saveImage(char const*, char const*)'
/home/numubuntu/OpenSees/SRC/tcl/TclVideoPlayer.o: In function `TclVideoPlayer::TclVideoPlayer(char const*, char const*, char const*, Tcl_Interp*, char const*, double)':
TclVideoPlayer.cpp:(.text+0xe9e): undefined reference to `OpenGLRenderer::OpenGLRenderer(char const*, int, int, int, int, ColorMap&)'
/home/numubuntu/OpenSees/SRC/tcl/TclVideoPlayer.o: In function `TclVideoPlayer::TclVideoPlayer(char const*, char const*, char const*, Tcl_Interp*, char const*, double)':
TclVideoPlayer.cpp:(.text+0x14de): undefined reference to `OpenGLRenderer::OpenGLRenderer(char const*, int, int, int, int, ColorMap&)'
/home/numubuntu/lib/libOpenSees.a(AMDNumberer.o): In function `AMD::number(Graph&, int)':
AMDNumberer.cpp:(.text+0x18a): undefined reference to `amd_order'
/home/numubuntu/lib/libOpenSees.a(TclRecorderCommands.o): In function `TclCreateRecorder(void*, Tcl_Interp*, int, char const**, Domain&, Recorder**)':
TclRecorderCommands.cpp:(.text+0x27e4): undefined reference to `FilePlotter::FilePlotter(char const*, char const*, int, int, int, int, double)'
TclRecorderCommands.cpp:(.text+0x27fa): undefined reference to `FilePlotter::setCol(ID const&)'
TclRecorderCommands.cpp:(.text+0x2a4b): undefined reference to `FilePlotter::FilePlotter(char const*, char const*, char const*, int, int, int, int, double)'
TclRecorderCommands.cpp:(.text+0x2a61): undefined reference to `FilePlotter::setCol(ID const&)'
TclRecorderCommands.cpp:(.text+0x2bda): undefined reference to `AlgorithmIncrements::AlgorithmIncrements(EquiSolnAlgo*, char const*, int, int, int, int, bool, char const*)'
/home/numubuntu/lib/libOpenSees.a(InelasticYS2DGNL.o): In function `InelasticYS2DGNL::createView(char*, double, int, int, int, int, char)':
InelasticYS2DGNL.cpp:(.text+0x120b): undefined reference to `OpenGLRenderer::OpenGLRenderer(char const*, int, int, int, int, ColorMap&)'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Cartcomm::Clone() const':
MumpsSOE.cpp:(.text._ZNK3MPI8Cartcomm5CloneEv[MPI::Cartcomm::Clone() const]+0x24): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Graphcomm::Clone() const':
MumpsSOE.cpp:(.text._ZNK3MPI9Graphcomm5CloneEv[MPI::Graphcomm::Clone() const]+0x24): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Intercomm::Merge(bool)':
MumpsSOE.cpp:(.text._ZN3MPI9Intercomm5MergeEb[MPI::Intercomm::Merge(bool)]+0x26): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Op::Init(void (*)(void const*, void*, int, MPI::Datatype const&), bool)':
MumpsSOE.cpp:(.text._ZN3MPI2Op4InitEPFvPKvPviRKNS_8DatatypeEEb[MPI::Op::Init(void (*)(void const*, void*, int, MPI::Datatype const&), bool)]+0x1f): undefined reference to `ompi_mpi_cxx_op_intercept'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Intracomm::Create_graph(int, int const*, int const*, bool) const':
MumpsSOE.cpp:(.text._ZNK3MPI9Intracomm12Create_graphEiPKiS2_b[MPI::Intracomm::Create_graph(int, int const*, int const*, bool) const]+0x27): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Intracomm::Create_cart(int, int const*, bool const*, bool) const':
MumpsSOE.cpp:(.text._ZNK3MPI9Intracomm11Create_cartEiPKiPKbb[MPI::Intracomm::Create_cart(int, int const*, bool const*, bool) const]+0x87): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Cartcomm::Sub(bool const*)':
MumpsSOE.cpp:(.text._ZN3MPI8Cartcomm3SubEPKb[MPI::Cartcomm::Sub(bool const*)]+0x83): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Intracomm::Clone() const':
MumpsSOE.cpp:(.text._ZNK3MPI9Intracomm5CloneEv[MPI::Intracomm::Clone() const]+0x27): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o: In function `MPI::Intracomm::Split(int, int) const':
MumpsSOE.cpp:(.text._ZNK3MPI9Intracomm5SplitEii[MPI::Intracomm::Split(int, int) const]+0x24): undefined reference to `MPI::Comm::Comm()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o:MumpsSOE.cpp:(.text._ZNK3MPI9Intracomm6CreateERKNS_5GroupE[MPI::Intracomm::Create(MPI::Group const&) const]+0x27): more undefined references to `MPI::Comm::Comm()' follow
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o:(.rodata._ZTVN3MPI3WinE[vtable for MPI::Win]+0x48): undefined reference to `MPI::Win::Free()'
/home/numubuntu/OpenSees/SRC/system_of_eqn/linearSOE/mumps/MumpsSOE.o:(.rodata._ZTVN3MPI8DatatypeE[vtable for MPI::Datatype]+0x78): undefined reference to `MPI::Datatype::Free()'
collect2: ld returned 1 exit status
make[1]: *** [tk] Error 1
make[1]: Leaving directory `/home/numubuntu/OpenSees/SRC/modelbuilder/tcl'
make: *** [tcl] Error 2
numubuntu@numubuntu-System-Product-Name:~/OpenSees$ 
```


So please guide me to what to do. I can provide the make files if needed.

Best regards,
Hisham ElSafti

---

