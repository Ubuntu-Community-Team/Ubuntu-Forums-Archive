---
title: "[OpenGL] Image doesn't fill the whole window"
date: 2012-11-21
forum: Programming Talk
---

### Post by bird1500 on 2012-11-21
Hi,
My little app loads an image into an 1.0f x 1.0f (from -0.5f to 0.5f) texture and puts it at Z = -1.0f in perspective view whose near projection plane width and height are also 1.0f x 1.0f (from -0.5f to 0.5f) and the near projection plane is at -1.0f.

Hence I thought the image should fill the whole window, but it only fills in like half of it.
Any idea what could be the reason?

Screenshot attached.

To build from source install:
libgtkmm-3.0-dev, libglfw-dev & cmake.
The app expects image "img.jpg" in the home dir.

---

### Post by PaulM1985 on 2012-11-22
I haven't looked at your code, but based on what you are trying to achieve I think you probably want orthogonal projection rather than perspective.  Are you looking to just render simple images like that?

Paul

---

### Post by bird1500 on 2012-11-22
Same issue with orthogonal, so it must be something wrong with my source code. But at least the basic concept (the 1st paragraph in 1st post) is correct, right?

---

### Post by PaulM1985 on 2012-11-22
Could you tell me where you set up your perspective view?  I have searched the files and I can't see any calls to any of the following, which I would have expected:
glFrustrum
glOrtho
gluPerspective

How are you setting up your projection?  I would expect to see one of those calls somewhere to initialise everything.

Paul

---

### Post by bird1500 on 2012-11-22
The basic design is:

main.cpp runs main() which runs AppSetup() which creates a pBaseProg (BaseProg.cpp) which draws the texture with the BaseProg::draw(draw_t*) function .

Hence the main draw function (WinDraw from main.cpp) simply calls the draw function (from BaseProg.cpp) which does the actual drawing:

[PHP]
void
WinDraw() {
    glClear(GL_COLOR_BUFFER_BIT);
    pBaseProg->draw(&draw_params);//this draws the stuff
    glfwSwapBuffers();
}
[/PHP]Now BaseProg's draw() function uses the math code from glm.h/cpp
like this:
[PHP]
    mat4 projMat;
    projMat.perspSymm(s, s, n, f);
[/PHP]The math algorithms from glm.h/cpp are based on [this article]("http://www.songho.ca/opengl/gl_projectionmatrix.html") - I attached a PDF version of it since it's more readable. Basically I'm trying to use only OpenGL's **core profile** with my own devised math code from the above article to teach myself, but nonetheless I'm planning to make this app usable and available for the masses when it's ready.

---

