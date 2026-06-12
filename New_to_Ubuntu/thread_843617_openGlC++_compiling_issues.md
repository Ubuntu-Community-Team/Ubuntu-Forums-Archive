---
title: "openGl/C++ compiling issues"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Genieman on 2008-06-28
Hey guys
 I'm having serious trouble getting this openGL demo to run on ubuntu.  I have FLTK wrapped with Libgfx but I'm running into a lot of errors when trying to compile a demo program.  

mp0.cxx:10:21: error: gfx/gfx.h: No such file or directory
mp0.cxx:11:21: error: gfx/gui.h: No such file or directory
mp0.cxx:12:20: error: gfx/gl.h: No such file or directory
mp0.cxx:13:25: error: gfx/gltools.h: No such file or directory
mp0.cxx:20: error: expected class-name before ‘{’ token
mp0.cxx: In member function ‘void GUI::setup_unit_canvas()’:
mp0.cxx:68: error: ‘GL_PROJECTION’ was not declared in this scope
mp0.cxx:68: error: ‘glMatrixMode’ was not declared in this scope
mp0.cxx:69: error: ‘glLoadIdentity’ was not declared in this scope
mp0.cxx:71: error: ‘gluOrtho2D’ was not declared in this scope
mp0.cxx: In member function ‘void GUI::pixel_to_canvas(int*, double*)’:
mp0.cxx:79: error: ‘unproject_pixel’ was not declared in this scope
mp0.cxx: In member function ‘virtual void GUI::setup_for_drawing()’:
mp0.cxx:90: error: ‘glClearColor’ was not declared in this scope
mp0.cxx:91: error: ‘GL_DEPTH_TEST’ was not declared in this scope
mp0.cxx:91: error: ‘glDisable’ was not declared in this scope
mp0.cxx:92: error: ‘GL_LIGHTING’ was not declared in this scope
mp0.cxx:95: error: ‘GL_MODELVIEW’ was not declared in this scope
mp0.cxx:95: error: ‘glMatrixMode’ was not declared in this scope
mp0.cxx:96: error: ‘glLoadIdentity’ was not declared in this scope
mp0.cxx: In member function ‘virtual void GUI::draw_contents()’:
mp0.cxx:108: error: ‘GL_COLOR_BUFFER_BIT’ was not declared in this scope
mp0.cxx:108: error: ‘glClear’ was not declared in this scope
mp0.cxx:111: error: ‘glColor3f’ was not declared in this scope
mp0.cxx:116: error: ‘GL_TRIANGLES’ was not declared in this scope
mp0.cxx:116: error: ‘glBegin’ was not declared in this scope
mp0.cxx:117: error: ‘glVertex2f’ was not declared in this scope
mp0.cxx:120: error: ‘glEnd’ was not declared in this scope
mp0.cxx:125: error: ‘status’ was not declared in this scope
mp0.cxx: In member function ‘virtual bool GUI::key_press(int)’:
mp0.cxx:168: error: ‘Fl’ has not been declared
mp0.cxx:168: error: ‘FL_SHIFT’ was not declared in this scope
mp0.cxx:171: error: ‘status’ was not declared in this scope
mp0.cxx: In function ‘int main(int, char**)’:
mp0.cxx:188: error: ‘class GUI’ has no member named ‘initialize’
mp0.cxx:191: error: ‘class GUI’ has no member named ‘default_fps’
mp0.cxx:194: error: ‘class GUI’ has no member named ‘canvas’
mp0.cxx:195: error: ‘class GUI’ has no member named ‘canvas’
mp0.cxx:204: error: ‘class GUI’ has no member named ‘run’

I feel like this could all be due to some small error that I just don't understand please help.
thanks

---

### Post by nowshining on 2008-06-29
did u install build-essentials?

---

