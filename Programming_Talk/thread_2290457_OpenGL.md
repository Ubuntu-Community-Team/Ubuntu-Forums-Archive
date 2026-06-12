---
title: "OpenGL"
date: 2015-08-12
forum: Programming Talk
---

### Post by agszepp on 2015-08-12
I am trying to get OpenGL 3.3 working. On [https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Seventh_generation](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Seventh_generation) it says that all Haswell cards (which is what I have) support OpenGL 3.3 on Linux.

glxinfo | grep -i 'opengl' shows this:

```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.5.2
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.5.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.5.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:

```

lspci shows
```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

```

If I try running this program

```

#include <GL/glew.h> // include GLEW and new version of GL on Windows
#include <GLFW/glfw3.h> // GLFW helper library
#include <stdio.h>

int main () {
  // start GL context and O/S window using the GLFW helper library
  if (!glfwInit ()) {
    fprintf (stderr, "ERROR: could not start GLFW3\n");
    return 1;
  }

    // uncomment these lines if on Apple OS X
  /*glfwWindowHint (GLFW_CONTEXT_VERSION_MAJOR, 3);
  glfwWindowHint (GLFW_CONTEXT_VERSION_MINOR, 2);
  glfwWindowHint (GLFW_OPENGL_FORWARD_COMPAT, GL_TRUE);
  glfwWindowHint (GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);*/

  GLFWwindow* window = glfwCreateWindow (640, 480, "Hello Triangle", NULL, NULL);
  if (!window) {
    fprintf (stderr, "ERROR: could not open window with GLFW3\n");
    glfwTerminate();
    return 1;
  }
  glfwMakeContextCurrent (window);

  // start GLEW extension handler
  glewExperimental = GL_TRUE;
  glewInit ();

  // get version info
  const GLubyte* renderer = glGetString (GL_RENDERER); // get renderer string
  const GLubyte* version = glGetString (GL_VERSION); // version as a string
  printf ("Renderer: %s\n", renderer);
  printf ("OpenGL version supported %s\n", version);

  // tell GL to only draw onto a pixel if the shape is closer to the viewer
  glEnable (GL_DEPTH_TEST); // enable depth-testing
  glDepthFunc (GL_LESS); // depth-testing interprets a smaller value as "closer"

  /* OTHER STUFF GOES HERE NEXT */

  // close GL context and any other GLFW resources
  glfwTerminate();
  return 0;
}

```

I get

Renderer: Mesa DRI Intel(R) Haswell Mobile 
OpenGL version supported 3.0 Mesa 10.5.2

Is there any way I can get OpenGL 3.3 working?

---

### Post by fprietog on 2015-08-25
I'm wondering exactly the same. I'm currently using Ubuntu 15.04 (64 bits) with a Intel Core i7-4790 Processor and Intel HD Graphics 4600, but glxinfo shows OpenGL version 3.0:
```
# glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Desktop 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.5.2
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.5.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.5.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
```
I have a program that needs OpenGL 3.2. In order to run it I previously spoof the OpenGL version changing this environment variable:
```
MESA_GL_VERSION_OVERRIDE=3.2
export MESA_GL_VERSION_OVERRIDE
```
It may help you. I know that it's not what you (also me) want, but I don't know how to do it legitimately.


Regards.

---

