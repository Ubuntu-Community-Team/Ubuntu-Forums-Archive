---
title: "wxWidgets and Segmentation fault"
date: 2009-03-17
forum: Programming Talk
---

### Post by dphuerta on 2009-03-17
Hello!

I'm trying to run a program which uses wxWidgets. I've installed OpenGL packages (libgl1-mesa-dev, libglu1-mesa-dev, ...) and also the wxWidgets related (libgtk2.0-dev, libwxbase2.8-dev, libwxgtk2.8-dev).

Code compiles without problem, but when I try to run it I get "Segmentation fault" :-(  I've run other OpenGL and wxWidgets samples and they go fine, and I've got this program from my teacher, and it works fine for him, so it shouldn't be wrong. He tried to debug it on my laptop (I didn't remember how) and noticed the problem happened when launching the window, but couldn't give me a solution. He says it might be related with mesa libraries, but I'm not sure, because I've tried other wxWidgets samples and they worked.

I've tried to run it with strace but I don't understand anything :( Could you give some advice, please?

Thank you :)

---

### Post by dphuerta on 2009-03-17
By the way, when I run it with gdb it stops here:
0xb79ca3ab in wxWindow::DoSetSize () from /usr/lib/libwx_gtk2u_core-2.8.so.0

---

### Post by cabalas on 2009-03-17
Without any code to look at there isn't much chance of anyone being able to help you.  There just isn't enough information for someone to tell you how to fix it.

---

### Post by dphuerta on 2009-03-18
Sorry! I've attached the source files, could someone try to compile and run it? Here is the backtrace with gdb and installing dbg packages:

[Debug] 11:54:39: ../src/gtk/glcanvas.cpp(351): assert "m_vi" failed in Create(): required visual couldn't be found
[Debug] 11:54:42: ../src/gtk/window.cpp(2894): assert "(m_widget != __null)" failed in DoGetSize(): invalid window
[Debug] 11:54:44: ../src/gtk/window.cpp(2691): assert "(m_widget != NULL)" failed in DoSetSize(): invalid window
[Debug] 11:54:45: ../src/gtk/window.cpp(2692): assert "(m_parent != NULL)" failed in DoSetSize(): wxWindowGTK::SetSize requires parent.

[Debug] 11:54:46: ../src/gtk/window.cpp(2958): assert "(m_widget != __null)" failed in DoGetPosition(): invalid window
Fallo de segmentación


BACKTRACE:
[1] wxGLCanvas::wxGLCanvas(wxWindow*, int, wxPoint const&, wxSize const&, long, wxString const&, int*, wxPalette const&)
[2] AreaOpenGL() /home/david/Escritorio/Enlace hacia Apuntes/VR/p1/VR_VentanaPrac.C:83
[3] VR::VentanaPrac::CreateWidgets() /home/david/Escritorio/Enlace hacia Apuntes/VR/p1/VR_VentanaPrac.C:800
[4] VR::VentanaPrac::Mostrar() /home/david/Escritorio/Enlace hacia Apuntes/VR/p1/VR_VentanaPrac.C:418
[5] Prac1() /home/david/Escritorio/Enlace hacia Apuntes/VR/p1/VR_Prac1.C:38
[6] VR::MyApp::OnInit() /home/david/Escritorio/Enlace hacia Apuntes/VR/p1/VR_Main.C:23

Thank you!

---

