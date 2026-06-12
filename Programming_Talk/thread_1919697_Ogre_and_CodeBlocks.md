---
title: "Ogre and Code::Blocks"
date: 2012-02-03
forum: Programming Talk
---

### Post by coth on 2012-02-03
Hya, I've been trying to get Ogre to run now for a couple of days. It's not working and I've become quite frustrated because there seem to be no documentation on the problems I'm getting. First I installed Ogre and C::B from the repos, after which I started an Ogre project in C::B. This won't compile since for some reason it cannot find the Ogre libraries(I think?!). 

After a bit of digging I found this; [http://www.isnull.com.ar/2010/07/ubuntu-1004-and-ogre3d-tutorial.html](http://www.isnull.com.ar/2010/07/ubuntu-1004-and-ogre3d-tutorial.html) where it's said that you have to build Ogre from scratch. I got as far as the build-part where it first complained on not finding "-lnosys", found little documentation on this but managed to find someone who told me this "library/file?"'s useless and I managed to track down where the code's calling it and removed it from the code. Then it runs for about up to 23% of the compilation where it complains on something else;

```
[ 18%] Building CXX object RenderSystems/GL/CMakeFiles/RenderSystem_GL.dir/src/nvparse/vs1.0_inst_list.cpp.o
[ 19%] Building CXX object RenderSystems/GL/CMakeFiles/RenderSystem_GL.dir/src/nvparse/_vs1.0_lexer.cpp.o
[ 20%] Building CXX object RenderSystems/GL/CMakeFiles/RenderSystem_GL.dir/src/nvparse/_vs1.0_parser.cpp.o
[ 21%] Building CXX object RenderSystems/GL/CMakeFiles/RenderSystem_GL.dir/src/nvparse/vsp1.0_impl.cpp.o
[ 22%] Building CXX object RenderSystems/GL/CMakeFiles/RenderSystem_GL.dir/__/__/RenderSystem_GL/compile_RenderSystem_GL_0.cpp.o
make[2]: *** No rule to make target `lib/libOgreMain.so.1.9.0', needed by `lib/RenderSystem_GL.so.1.9.0'.  Stop.
make[1]: *** [RenderSystems/GL/CMakeFiles/RenderSystem_GL.dir/all] Error 2
make: *** [all] Error 2

```

...and then I'm stuck. I can't find any documentation on this problem at all, I can only speculate that it's got something to do with that the tutorial for installing is for 10.04(where's I'm running 11.10) and maybe "-lnosys" is removed for later versions or something. Or am I going about this completely wrong? It makes no sense that it should be this complicated just to get Ogre up and running, especially since both Ogre and C::B is available from the repos.

---

### Post by korgoth28 on 2012-02-05
Sorry if this is a stupid question, but did you go to settings -> compiler and debugger -> linker settings, and add the correct libraries before you tried all this?

---

### Post by coth on 2012-02-14
> **korgoth28 said:**
> Sorry if this is a stupid question, but did you go to settings -> compiler and debugger -> linker settings, and add the correct libraries before you tried all this?

I did just now. .) When starting a new project there are two libraries in the linker settings of which none of them seems to exist, so I managed to track down where installing libogre-dev puts the libraries; /usr/include/OGRE, and /usr/include/OIS? Then I added these directories under the "search directories" tab instead, I also had to remove the posts in the linker settings.

Without luck though but thanks, and of course I have to do all this again everytime I start another project.

I still can't run the tutorial-files from the framework and I'm getting too many compiling-errors for it to be the code I think.

---

