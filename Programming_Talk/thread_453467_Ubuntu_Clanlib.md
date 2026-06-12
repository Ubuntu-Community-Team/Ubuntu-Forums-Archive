---
title: "Ubuntu Clanlib"
date: 2007-05-24
forum: Programming Talk
---

### Post by ART_Adventures on 2007-05-24
Hello People,

I have Feisty,  code::blocks, and am using the GCC compiler.

I would like to compile a Clanlib ([http://www.clanlib.org/](http://www.clanlib.org/)) application.

Can anybody tell me what I need to do in order to get Clanlib working. The Clanlib Dev libraries in Synaptic are for an older version. How can I build my own libraries from the Clanlib source featured on the site, or is there somewhere I can find some libraries for Clanlib on Ubuntu?

I am new to linux, but not programing.

Thanks.

---

### Post by WW on 2007-05-24
The instructions [here]("http://www.clanlib.org/docs/clanlib-0.8.0/Tutorial/Kavanek/01-Installing.html") are pretty close, although there is a mistake: the configure command should be
```

./configure

```
and not
```

../configure

```

Here is my version of the instructions. I am using Dapper, but this should still work in Feisty.

Install the libraries that ClanLib will need with the following command:
```

sudo apt-get install zlib1g-dev libjpeg62-dev libpng12-dev libmikmod2-dev libogg-dev libvorbis-dev libxxf86vm-dev

```
Most of those packages have additional dependencies, so you will actually end up installing additional packages. (Note: I don't know if those are the only libraries that you will need.  The first six are packages that provide the libraries that the web page says ClanLib needs. I also had to install the last one, libxxf86vm-dev, to get it to compile.  There may be other libraries that it needs that I already had installed.)

Download ClanLib-0.8.0.tgz, and save it to a work directory, say ~/build.

In the work directory,
```

$ tar xvzf ClanLib-0.8.0.tgz
$ cd ClanLib-0.8.0
$ ./configure

```
If the configure command finishes successfully, and it doesn't report any missing libraries, you can then run
```

$ make

```
This will take a long time.  If the make command doesn't report any errors, run
```

$ sudo make install

```
This will install the ClanLib library in /usr/local.

Add the line **/usr/local/lib** to the file **/etc/ld.so.conf**, and then run
```

$ sudo ldconfig

```
This tells your system to look for shared libraries in /usr/local/lib. (The default location is to look only in /usr/lib.)

Run the command
```

$ export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig

```
This tells the pkg-config command to look in /usr/local/lib/pkgconfig for .pc files (in addition to the default /usr/lib/pkgconfig).

Now test it out.  Here is the sample code from the file INSTALL.linux in the directory ClanLib-0.8.0:

**SampleApp.cpp**
```

#include <ClanLib/gl.h>
#include <ClanLib/core.h>
#include <ClanLib/application.h>
#include <ClanLib/display.h>

class MyApp : public CL_ClanApplication
{
public:
        virtual int main(int argc, char **argv)
        {
                // Create a console window for text-output if not available
                // Use printf or cout to display some text in your program
                CL_ConsoleWindow console("Console");
                console.redirect_stdio();

                try
                {
                        // Initialize ClanLib base components
                        CL_SetupCore setup_core;

                        // Initialize the ClanLib display component
                        CL_SetupDisplay setup_display;

                        // Initialize the ClanLib GL component
                        CL_SetupGL setup_gl;

                        // Create a display window
                        CL_DisplayWindow window("ClanLib application", 640, 480);

                        // Run until someone presses escape
                        while (!CL_Keyboard::get_keycode(CL_KEY_ESCAPE))
                        {
                                // Clear the display in a dark blue nuance
                                // The four arguments are red, green, blue and alpha (defaults to 255)
                                // All color nuances in ClanLib are measured in the interval 0->255
                                CL_Display::clear(CL_Color(0, 0, 50));

                                // Flip the display (using a double-buffer),
                                // showing on the screen what we have drawed
                                // since last call to flip()
                                CL_Display::flip();

                                // This call updates input and performs other "housekeeping"
                                // Call this each frame
                                // Also, gives the CPU a rest for 10 milliseconds to catch up
                                CL_System::keep_alive(10);
                        }
                }
                // Catch any errors from ClanLib
                catch (CL_Error err)
                {
                        // Display the error message
                        std::cout << err.message.c_str() << std::endl;
                }

                // Display console close message and wait for a key
                console.display_close_message();

                return 0;
        }
} app;

```
Save this in a new directory, say ~/clanlibtest. Here is how I compiled and ran it.
```

~/clanlibtest$ ls
SampleApp.cpp
~/clanlibtest$ g++ SampleApp.cpp -o SampleApp `pkg-config --cflags clanCore-0.8`  `pkg-config --libs clanApp-0.8 clanGL-0.8`
~/clanlibtest$ ./SampleApp
~/clanlibtest$

```
It doesn't do much--just puts up a blank window. Hit Escape to close it.

---

### Post by ART_Adventures on 2007-05-24
Thank you for these very clear, and helpful instructions. I think I am almost there. However, when I run make, it processes for quite a long time before returning with the following error. I believe a library might be missing, though I do not which. Any ideas?

```

 g++ -DPACKAGE_NAME=\"ClanLib\" -DPACKAGE_TARNAME=\"clanlib\" -DPACKAGE_VERSION=\"0.8.0\" "-DPACKAGE_STRING=\"ClanLib 0.8.0\"" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"clanlib\" -DVERSION=\"0.8.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_SYS_KD_H=1 -DHAVE_SYS_VT_H=1 -DUSE_I386_ASSEMBLER=1 -DHAVE_FSTAB_H=1 -DHAVE_LIBZ=1 -DHAVE_LIBSDL_GFX=1 -DHAVE_GLX_GETPROCADDRESSARB=1 -DUSE_GETADDR=1 -I. -I. -g -O2 -I../../Sources -MT filedialog_generic.lo -MD -MP -MF .deps/filedialog_generic.Tpo -c filedialog_generic.cpp  -fPIC -DPIC -o .libs/filedialog_generic.o
 g++ -DPACKAGE_NAME=\"ClanLib\" -DPACKAGE_TARNAME=\"clanlib\" -DPACKAGE_VERSION=\"0.8.0\" "-DPACKAGE_STRING=\"ClanLib 0.8.0\"" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"clanlib\" -DVERSION=\"0.8.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_SYS_KD_H=1 -DHAVE_SYS_VT_H=1 -DUSE_I386_ASSEMBLER=1 -DHAVE_FSTAB_H=1 -DHAVE_LIBZ=1 -DHAVE_LIBSDL_GFX=1 -DHAVE_GLX_GETPROCADDRESSARB=1 -DUSE_GETADDR=1 -I. -I. -g -O2 -I../../Sources -MT filedialog_generic.lo -MD -MP -MF .deps/filedialog_generic.Tpo -c filedialog_generic.cpp -o filedialog_generic.o >/dev/null 2>&1
make[2]: *** [filedialog_generic.lo] Error 1
make[2]: Leaving directory `/home/me/clanlib/ClanLib-0.8.0/Sources/GUI'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/me/clanlib/ClanLib-0.8.0/Sources'
make: *** [all-recursive] Error 1

```

---

### Post by WW on 2007-05-24
Sorry, I don't know what is going wrong there. Unfortunately, the g++ command that is apparently causing the problem has **>/dev/null 2>&1** at the end, which sends the error message to /dev/null.

---

### Post by ART_Adventures on 2007-05-24
Hmmm, I ran make again, and it compiled successfully. I have one further question.

When I edit /etc/ld.so.conf

It shows me:

```

include /etc/ld.so.conf.d/*.conf

```

Should I therefore edit it to read:

```

include /etc/ld.so.conf.d/*.conf
include /usr/local/lib/

```

? Thanks.

---

### Post by WW on 2007-05-24
Dapper doesn't have this feature, so I am guessing (but it is a pretty confident guess).  What you suggested (but without the word "include") would probably work, but a "better" way would be to create a file in the directory /etc/ld.so.conf.d, say **local.conf**, and put the single line **/usr/local/lib** in that file. I don't think you should put the word "include" in front of the directory name.

---

### Post by ART_Adventures on 2007-05-25
Ok. Almost there.

I compile the source file successfully, as you suggested:

```

g++ SampleApp.cpp -o SampleApp `pkg-config --cflags clanCore-0.8`  `pkg-config --libs clanApp-0.8 clanGL-0.8`

```

But when I run the executable (./SampleApp) it says

```

./SampleApp: error while loading shared libraries: libclanApp-0.8.so.1: cannot open shared object file: No such file or directory

```

I looked in /usr/local/lib and there is a file called libclanApp-0.8.so.1.

Any ideas? Thanks.

---

### Post by WW on 2007-05-25
Did you run **sudo ldconfig** after creating the file **local.conf** in /etc/ld.so.conf.d?

---

### Post by ART_Adventures on 2007-05-25
Thank you very much. That worked :-)

The problem was that I had placed local.conf in directory /etc/ instead of /etc/ld.so.conf.d/.

Thanks again, and hopefully this thread will be useful to anybody else trying to build Clanlib.

---

### Post by sneilan on 2008-09-27
This post is a year later, but, I was trying to build clanlib 8.1 on Hardy Heron 64 & I also needed to install libasound2-dev libxmu-dev libsdl-gfx1.2-dev libxi-dev

In total, I had to install all of the following to compile Clanlib 8.1 on Hardy Heron

```
sudo apt-get install libasound2-dev libxmu-dev libsdl-gfx1.2-dev libxi-dev zlib1g-dev libjpeg62-dev libpng12-dev libmikmod2-dev libogg-dev libvorbis-dev libxxf86vm-dev libsdl1.2-dev
```

---

### Post by sneilan on 2008-09-27
Also, don't bother installing the clanlib package. You don't need it & I'm not sure if it's up to date anyhow.

---

### Post by gspawn69 on 2009-08-16
I've been trying to install ClanLib 2.0.3 and I keep running into some problems. I can run the autogen.sh and configure fine without any errors, but then when I run 'make' it chugs along for quite some time and then gives me these error messages:

```

libtool: compile:  g++ -DPACKAGE_NAME=\"ClanLib\" -DPACKAGE_TARNAME=\"clanlib\" -DPACKAGE_VERSION=\"2.0.3\" "-DPACKAGE_STRING=\"ClanLib 2.0.3\"" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"clanlib\" -DVERSION=\"2.0.3\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DLT_OBJDIR=\".libs/\" -DSTDC_HEADERS=1 -DHAVE_STDBOOL_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_SYS_KD_H=1 -DHAVE_SYS_VT_H=1 -DHAVE_SYS_SYSCTL_H=1 -DUSE_I386_ASSEMBLER=1 -DHAVE_FSTAB_H=1 -DEXTERN___PROGNAME=1 -DHAVE_WCSCASECMP=1 -DHAVE_TLS=1 -DHAVE_LIBZ=1 -DHAVE_LINUX_JOYSTICK_H=1 -DHAVE_LINUX_INPUT_H=1 -DHAVE_ALSA_ASOUNDLIB_H=1 -DHAVE_X11_EXTENSIONS_XF86VMODE_H=1 -DHAVE_GLX_GETPROCADDRESSARB=1 -DHAVE_GLX_GETPROCADDRESSARB=1 -DHAVE_SYS_SOUNDCARD_H=1 -DHAVE_ALSA_ASOUNDLIB_H=1 -DUSE_GETADDR=1 -I. -g -O2 -I/usr/include/freetype2 -I../../Sources -MT sdl_graphic_context_provider.lo -MD -MP -MF .deps/sdl_graphic_context_provider.Tpo -c sdl_graphic_context_provider.cpp  -fPIC -DPIC -o .libs/sdl_graphic_context_provider.o                                                                                                                                                
In file included from sdl_graphic_context_provider.cpp:45:                                                                                                       
/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory                                                                        
make[2]: *** [sdl_graphic_context_provider.lo] Error 1                                                                                                           
make[2]: Leaving directory `/home/scott/Desktop/ClanLib-2.0.3/Sources/SDL'                                                                                       
make[1]: *** [all-recursive] Error 1                                                                                                                             
make[1]: Leaving directory `/home/scott/Desktop/ClanLib-2.0.3/Sources'                                                                                           
make: *** [all-recursive] Error 1

```

Also, I tried running 'sudo make install' afterwards just to see what would happen, and it seemed to work until right at the end as well, where I get this similar error message:

```

libtool: compile:  g++ -DPACKAGE_NAME=\"ClanLib\" -DPACKAGE_TARNAME=\"clanlib\" -DPACKAGE_VERSION=\"2.0.3\" "-DPACKAGE_STRING=\"ClanLib 2.0.3\"" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"clanlib\" -DVERSION=\"2.0.3\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DLT_OBJDIR=\".libs/\" -DSTDC_HEADERS=1 -DHAVE_STDBOOL_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_SYS_KD_H=1 -DHAVE_SYS_VT_H=1 -DHAVE_SYS_SYSCTL_H=1 -DUSE_I386_ASSEMBLER=1 -DHAVE_FSTAB_H=1 -DEXTERN___PROGNAME=1 -DHAVE_WCSCASECMP=1 -DHAVE_TLS=1 -DHAVE_LIBZ=1 -DHAVE_LINUX_JOYSTICK_H=1 -DHAVE_LINUX_INPUT_H=1 -DHAVE_ALSA_ASOUNDLIB_H=1 -DHAVE_X11_EXTENSIONS_XF86VMODE_H=1 -DHAVE_GLX_GETPROCADDRESSARB=1 -DHAVE_GLX_GETPROCADDRESSARB=1 -DHAVE_SYS_SOUNDCARD_H=1 -DHAVE_ALSA_ASOUNDLIB_H=1 -DUSE_GETADDR=1 -I. -g -O2 -I/usr/include/freetype2 -I../../Sources -MT sdl_graphic_context_provider.lo -MD -MP -MF .deps/sdl_graphic_context_provider.Tpo -c sdl_graphic_context_provider.cpp  -fPIC -DPIC -o .libs/sdl_graphic_context_provider.o                                                                                                                                                
In file included from sdl_graphic_context_provider.cpp:45:                                                                                                       
/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory                                                                        
make[2]: *** [sdl_graphic_context_provider.lo] Error 1                                                                                                           
make[2]: Leaving directory `/home/scott/Desktop/ClanLib-2.0.3/Sources/SDL'                                                                                       
make[1]: *** [install-recursive] Error 1                                                                                                                         
make[1]: Leaving directory `/home/scott/Desktop/ClanLib-2.0.3/Sources'                                                                                           
make: *** [install-recursive] Error 1 

```

Then, as a test to see if installed correctly, I tried running 'make' on the Basic2D example and got these errors:

```

scott@scott-laptop:~/Desktop/ClanLib-2.0.3/Examples/Basic2D$ make                                                                                           
g++ `pkg-config --cflags clanApp-2.0 clanDisplay-2.0 clanCore-2.0 clanGL-2.0` -pthread -c basic2d.cpp -o basic2d.o                                          
Package clanApp-2.0 was not found in the pkg-config search path.                                                                                            
Perhaps you should add the directory containing `clanApp-2.0.pc'                                                                                            
to the PKG_CONFIG_PATH environment variable                                                                                                                 
No package 'clanApp-2.0' found                                                                                                                              
Package clanDisplay-2.0 was not found in the pkg-config search path.                                                                                        
Perhaps you should add the directory containing `clanDisplay-2.0.pc'                                                                                        
to the PKG_CONFIG_PATH environment variable                                                                                                                 
No package 'clanDisplay-2.0' found                                                                                                                          
Package clanCore-2.0 was not found in the pkg-config search path.                                                                                           
Perhaps you should add the directory containing `clanCore-2.0.pc'                                                                                           
to the PKG_CONFIG_PATH environment variable                                                                                                                 
No package 'clanCore-2.0' found                                                                                                                             
Package clanGL-2.0 was not found in the pkg-config search path.                                                                                             
Perhaps you should add the directory containing `clanGL-2.0.pc'                                                                                             
to the PKG_CONFIG_PATH environment variable                                                                                                                 
No package 'clanGL-2.0' found                                                                                                                               
basic2d.cpp:1:26: error: ClanLib/core.h: No such file or directory                                                                                          
basic2d.cpp:2:33: error: ClanLib/application.h: No such file or directory                                                                                   
basic2d.cpp:3:29: error: ClanLib/display.h: No such file or directory                                                                                       
basic2d.cpp:13:24: error: ClanLib/gl.h: No such file or directory                                                                                           
basic2d.cpp:21: error: expected unqualified-id before ‘<’ token                                                                                             
basic2d.cpp:21: error: expected ‘,’ or ‘...’ before ‘<’ token                                                                                               
basic2d.cpp:24: error: expected ‘,’ or ‘...’ before ‘&’ token                                                                                               
basic2d.cpp:24: error: ISO C++ forbids declaration of ‘CL_InputEvent’ with no type                                                                          
basic2d.cpp:35: error: expected unqualified-id before ‘<’ token                                                                                             
basic2d.cpp:35: error: expected ‘,’ or ‘...’ before ‘<’ token                                                                                               
basic2d.cpp: In static member function ‘static int Program::main()’:                                                                                        
basic2d.cpp:38: error: ‘CL_SetupCore’ was not declared in this scope                                                                                        
basic2d.cpp:38: error: expected `;' before ‘setup_core’                                                                                                     
basic2d.cpp:41: error: ‘CL_SetupDisplay’ was not declared in this scope                                                                                     
basic2d.cpp:41: error: expected `;' before ‘setup_display’                                                                                                  
basic2d.cpp:52: error: ‘CL_SetupGL’ was not declared in this scope                                                                                          
basic2d.cpp:52: error: expected `;' before ‘setup_gl’                                                                                                       
basic2d.cpp:57: error: ‘args’ was not declared in this scope                                                                                                
basic2d.cpp: At global scope:                                                                                                                               
basic2d.cpp:63: error: ‘CL_ClanApplication’ does not name a type                                                                                            
basic2d.cpp:66: error: expected unqualified-id before ‘<’ token                                                                                             
basic2d.cpp:66: error: expected ‘,’ or ‘...’ before ‘<’ token                                                                                               
basic2d.cpp: In member function ‘int App::start()’:                                                                                                         
basic2d.cpp:71: error: ‘CL_ConsoleWindow’ was not declared in this scope                                                                                    
basic2d.cpp:71: error: expected `;' before ‘console’                                                                                                        
basic2d.cpp:81: error: ‘CL_DisplayWindow’ was not declared in this scope                                                                                    
basic2d.cpp:81: error: expected `;' before ‘window’                                                                                                         
basic2d.cpp:84: error: ‘CL_Slot’ was not declared in this scope                                                                                             
basic2d.cpp:84: error: expected `;' before ‘slot_quit’                                                                                                      
basic2d.cpp:87: error: expected `;' before ‘slot_input_up’                                                                                                  
basic2d.cpp:90: error: ‘CL_GraphicContext’ was not declared in this scope                                                                                   
basic2d.cpp:90: error: expected `;' before ‘gc’                                                                                                             
basic2d.cpp:93: error: ‘CL_Sprite’ was not declared in this scope                                                                                           
basic2d.cpp:93: error: expected `;' before ‘spr_logo’                                                                                                       
basic2d.cpp:104: error: ‘gc’ was not declared in this scope                                                                                                 
basic2d.cpp:104: error: ‘CL_Colorf’ was not declared in this scope                                                                                          
basic2d.cpp:112: error: ‘CL_Draw’ has not been declared                                                                                                     
basic2d.cpp:113: error: ‘CL_Draw’ has not been declared                                                                                                     
basic2d.cpp:118: error: ‘spr_logo’ was not declared in this scope                                                                                           
basic2d.cpp:122: error: ‘CL_Rect’ was not declared in this scope
basic2d.cpp:127: error: ‘CL_Draw’ has not been declared
basic2d.cpp:127: error: ‘CL_Rectf’ was not declared in this scope
basic2d.cpp:130: error: ‘CL_Draw’ has not been declared
basic2d.cpp:131: error: ‘CL_Draw’ has not been declared
basic2d.cpp:132: error: ‘CL_Draw’ has not been declared
basic2d.cpp:133: error: ‘CL_Draw’ has not been declared
basic2d.cpp:139: error: ‘CL_Draw’ has not been declared
basic2d.cpp:139: error: ‘CL_Sizef’ was not declared in this scope
basic2d.cpp:142: error: ‘CL_Draw’ has not been declared
basic2d.cpp:148: error: ‘window’ was not declared in this scope
basic2d.cpp:151: error: ‘CL_DisplayMessageQueue’ has not been declared
basic2d.cpp:154: error: expected type-specifier before ‘CL_Exception’
basic2d.cpp:154: error: expected `)' before ‘&’ token
basic2d.cpp:154: error: expected `{' before ‘&’ token
basic2d.cpp:154: error: ‘exception’ was not declared in this scope
basic2d.cpp:154: error: expected `;' before ‘)’ token
basic2d.cpp:191: error: expected `}' at end of input
make: *** [basic2d.o] Error 1

```

Now I'm guessing this is something to do with 'make' not running properly when I'm trying to install ClanLib, but I went over their documentation and made sure I had every single one of the packages it required, so I'm really confused why it's not working. If anyone could give me a hand here it would be greatly appreciated.

---

