---
title: "Monodevelop does not create a binary when using SDL Image"
date: 2009-06-06
forum: Programming Talk
---

### Post by Minguo on 2009-06-06
Hi, I'm trying to learn using Mono, but taking first steeps doing these tutorials.  [http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

So, trying from the beginning I tried loading an image, but curiously Monodevelop does not create an executable binary if I am using code from the SDL Image library.

The code compiles, but the binary is not created.
If I leave out the code from SDL Image, but just use basic SDL code, it compiles and creates a binary which I can run.

Example:  
```
//Base SDL function
SDL_LoadBMP("picture.bmp");
```

Works fine, compiles, and I can run the binary that's created. (Which I can also run from the console.) However,

```

//SDL Image function
IMG_Load("picture.bmp" );
```

Compiles, but if I try to 'run' the code in monodevelop I get an error message.

"Cannot execute SDL Test"
> System.ComponentModel.Win32Exception: ApplicationName='/home/brandon/Projects/SDL Test/SDL Test/bin/Debug/SDL Test', CommandLine='', CurrentDirectory='/home/brandon/Projects/SDL Test/SDL Test/bin/Debug'
  at System.Diagnostics.Process.Start_noshell (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] 
  at System.Diagnostics.Process.Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] 
  at System.Diagnostics.Process.Start () [0x00000] 
  at MonoDevelop.Core.Execution.ProcessWrapper.Start () [0x00000] 
  at (wrapper remoting-invoke-with-check) MonoDevelop.Core.Execution.ProcessWrapper:Start ()
  at MonoDevelop.Core.Execution.ProcessService.StartProcess (System.Diagnostics.ProcessStartInfo startInfo, MonoDevelop.Core.Execution.ProcessEventHandler outputStreamChanged, MonoDevelop.Core.Execution.ProcessEventHandler errorStreamChanged, System.EventHandler exited) [0x00000] 
  at MonoDevelop.Core.Execution.ProcessService.StartProcess (System.Diagnostics.ProcessStartInfo startInfo, System.IO.TextWriter outWriter, System.IO.TextWriter errorWriter, System.EventHandler exited) [0x00000] 
  at MonoDevelop.Core.Execution.ProcessService.StartConsoleProcess (System.String command, System.String arguments, System.String workingDirectory, IDictionary`2 environmentVariables, IConsole console, System.EventHandler exited) [0x00000] 
  at MonoDevelop.Core.Execution.NativePlatformExecutionHandler.Execute (System.String command, System.String arguments, System.String workingDirectory, IDictionary`2 environmentVariables, IConsole console) [0x00000] 
  at MonoDevelop.Core.Execution.DefaultExecutionHandlerFactory.Execute (System.String command, System.String arguments, System.String workingDirectory, IDictionary`2 environmentVariables, IConsole console) [0x00000] 
  at CBinding.CProject.DoExecute (IProgressMonitor monitor, MonoDevelop.Projects.ExecutionContext context, System.String configuration) [0x00000] 


And there is no binary crated in the debug folder.

Any Idea what most likley painfully obvious thing I've done/not done/overlooked that could be doing this?

SDL and all of its related libraries are all installed from Synaptic, Mono and Monodevelop as well.

---

### Post by leblancmeneses on 2009-06-06
sounds like a bug that needs to be reported to monodevelop.

if it compiles then you should get a binary.

The only assumption i can see is monodevelop confirms c# syntax which is compiled but the linking process is not reported in monodevelop which probably fails since no binary is outputted.

I'm using monodevelop for gdb debugging .. project is sweet.

---

### Post by directhex on 2009-06-06
Which lesson from the above link are you working on, and which type of project did you create?

---

### Post by Minguo on 2009-06-06
Hi, thanks for the responses!

I was working on tutorial 3, (which introduces SDL_Image)
[http://lazyfoo.net/SDL_tutorials/lesson03/index.php](http://lazyfoo.net/SDL_tutorials/lesson03/index.php)

I created an empty C++ project, and then a C++ source file.

> 
The only assumption i can see is monodevelop confirms c# syntax which is compiled but the linking process is not reported in monodevelop which probably fails since no binary is outputted.

So after I read this, I looked closer at the build output. It was saying that building was successful, so I didn't look too closely, but it seems something is wrong.

> Building: SDL Test (Debug)

Building Solution SDL Test

Building: SDL Test (Debug)
Performing main compilation...

Precompiling headers

Compiling source to object files
g++  -MMD "/home/brandon/Projects/SDL Test/SDL Test/main.cpp" -g -O0 -DDEBUG -DMONODEVELOP -I"/home/brandon/Projects/SDL Test/SDL Test/.prec/Debug"  -c -o "/home/brandon/Projects/SDL Test/SDL Test/bin/Debug/main.o"

Generating binary "SDL Test" from object files
g++ -o "/home/brandon/Projects/SDL Test/SDL Test/bin/Debug/SDL Test" "/home/brandon/Projects/SDL Test/SDL Test/bin/Debug/main.o" -l"SDL" "/usr/lib/libSDL_image.a"  
/usr/lib/libSDL_image.a(IMG_jpg.o): In function `IMG_InitJPG':
(.text+0x12): undefined reference to `jpeg_calc_output_dimensions'
/usr/lib/libSDL_image.a(IMG_jpg.o): In function `IMG_InitJPG':
(.text+0x1c): undefined reference to `jpeg_CreateDecompress'
/usr/lib/libSDL_image.a(IMG_jpg.o): In function `IMG_InitJPG':
(.text+0x26): undefined reference to `jpeg_destroy_decompress'
/usr/lib/libSDL_image.a(IMG_jpg.o): In function `IMG_InitJPG':
(.text+0x30): undefined reference to `jpeg_finish_decompress'
/usr/lib/libSDL_image.a(IMG_jpg.o): In function `IMG_InitJPG':
(.text+0x3a): undefined reference to `jpeg_read_header'
/usr/lib/libSDL_image.a(IMG_jpg.o): In function `IMG_InitJPG':
(.text+0x44): undefined reference to `jpeg_read_scanlines'
/usr/lib/libSDL_image.a(IMG_jpg.o): In function `IMG_InitJPG':
(.text+0x4e): undefined reference to `jpeg_resync_to_restart'
/usr/lib/libSDL_image.a(IMG_jpg.o): In function `IMG_InitJPG':
(.text+0x58): undefined reference to `jpeg_start_decompress'
/usr/lib/libSDL_image.a(IMG_jpg.o): In function `IMG_InitJPG':
(.text+0x62): undefined reference to `jpeg_std_error'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x16): undefined reference to `png_create_info_struct'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x20): undefined reference to `png_create_read_struct'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x2a): undefined reference to `png_destroy_read_struct'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x34): undefined reference to `png_get_IHDR'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x3e): undefined reference to `png_get_io_ptr'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x48): undefined reference to `png_get_tRNS'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x52): undefined reference to `png_get_valid'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x5c): undefined reference to `png_read_image'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x66): undefined reference to `png_read_info'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x70): undefined reference to `png_read_update_info'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x7a): undefined reference to `png_set_expand'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x84): undefined reference to `png_set_gray_to_rgb'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x8e): undefined reference to `png_set_packing'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0x98): undefined reference to `png_set_read_fn'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0xa2): undefined reference to `png_set_strip_16'
/usr/lib/libSDL_image.a(IMG_png.o): In function `IMG_InitPNG':
(.text+0xac): undefined reference to `png_sig_cmp'
/usr/lib/libSDL_image.a(IMG_tif.o): In function `IMG_InitTIF':
(.text+0x12): undefined reference to `TIFFClientOpen'
/usr/lib/libSDL_image.a(IMG_tif.o): In function `IMG_InitTIF':
(.text+0x1c): undefined reference to `TIFFClose'
/usr/lib/libSDL_image.a(IMG_tif.o): In function `IMG_InitTIF':
(.text+0x26): undefined reference to `TIFFGetField'
/usr/lib/libSDL_image.a(IMG_tif.o): In function `IMG_InitTIF':
(.text+0x30): undefined reference to `TIFFReadRGBAImage'
/usr/lib/libSDL_image.a(IMG_tif.o): In function `IMG_InitTIF':
(.text+0x3a): undefined reference to `TIFFSetErrorHandler'
collect2: ld returned 1 exit status
Build complete -- 0 errors, 0 warnings

---------------------- Done ----------------------

Build successful.

As  you can see, something is weird, even though it reports 0 errors and a successful build.  I googled the text in the "Generating binary "SDL Test" from object files" section, and found this thread:
[http://swiss.ubuntuforums.org/showthread.php?p=6333419](http://swiss.ubuntuforums.org/showthread.php?p=6333419)

He seems to have the same problem, but his compiler errors instead of simply misbehaving. (I'm guessing he's just using the console g++) 

So I tried compiling in the console using the same options the poster in that thread used. 

```
g++ main.cpp -o sdltest -lSDL -lSDL_image
``` 

and it works!  Creates the binary and everything. . . from the code written in monodevelop, but monodevelop still won't make the binary.


So, I went back to my library options, and deleted the entry I originally put for SDL_image. (I did Project->Properties->Code Generation ->Libraries tab, and then browsed to //usr/lib/libSDL_image.a
)  and instead just typed in SDL_image and added that entry. . . and then everything worked . . . making me feel a little stupid.

But why did the code originally compile? (Making me think it was set up right!)  Shouldn't it have thrown an error if I didn't have SDL_image properly pointed at? (It DID throw errors if I didn't have the #include SDL/SDL_image.h line.)

---

### Post by directhex on 2009-06-07
> **Minguo said:**
> But why did the code originally compile? (Making me think it was set up right!)  Shouldn't it have thrown an error if I didn't have SDL_image properly pointed at? (It DID throw errors if I didn't have the #include SDL/SDL_image.h line.)

I think the problem is you were using a static library (.a file). Static libraries compile one library INTO your program, rather than being referenced by your program. As a result, it wasn't that you were doing anything wrong per se - it's that you didn't have a bunch of other static libraries corresponding to the bits needed by static SDL_image.

When you switched to using -lSDL_image, you instead started dynamically linking to the .so version of the library, and dynamic libraries can have dependencies dealt with automatically:
```
directhex@desire:~$ ldd /usr/lib/libSDL_image-1.2.so.0.1.5 
	linux-vdso.so.1 =>  (0x00007fff7e1fe000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f0875c3b000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007f0875a14000)
	libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0x00007f08757f0000)
	libtiff.so.4 => /usr/lib/libtiff.so.4 (0x00007f0875595000)
	libz.so.1 => /lib/libz.so.1 (0x00007f087537d000)
	libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0x00007f08750e4000)
	libc.so.6 => /lib/libc.so.6 (0x00007f0874d72000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f0876094000)
	libm.so.6 => /lib/libm.so.6 (0x00007f0874aed000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0x00007f087480c000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f0874608000)
	libdirectfb-1.0.so.0 => /usr/lib/libdirectfb-1.0.so.0 (0x00007f0874394000)
	libfusion-1.0.so.0 => /usr/lib/libfusion-1.0.so.0 (0x00007f087418a000)
	libdirect-1.0.so.0 => /usr/lib/libdirect-1.0.so.0 (0x00007f0873f74000)
	librt.so.1 => /lib/librt.so.1 (0x00007f0873d6c000)
```

---

