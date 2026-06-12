---
title: "OpenGL Texture mix-up"
date: 2010-11-03
forum: Programming Talk
---

### Post by Eragon0605 on 2010-11-03
Greetings yet again, Ubuntu community. I come to you with another problem with one my ever-troublesome 3D OpenGL experiences. This time around, my textures decided to overwrite themselves. For example, let's say I want to load two textures. First, I would make two GLuint variables, say, tex1 and tex2. Now, I would run the following code outside the main game loop:```
tex1 = SOIL_load_OGL_texture(
"texture.png",
SOIL_LOAD_RGBA,
SOIL_CREATE_NEW_ID,
SOIL_FLAG_NTSC_SAFE_RGB);

tex2 = SOIL_load_OGL_texture(
"texture2.png",
SOIL_LOAD_RGBA,
SOIL_CREATE_NEW_ID,
SOIL_FLAG_NTSC_SAFE_RGB);
```This is what I have done in all my 2D projects and it works fine. The problem I have here is that whenever I bind tex1 to a shape, it shows the picture that I bound to tex2. I checked the value of the tex1 and tex2 variables, and they are different. And yes, before you ask, texture.png is different than texture2.png.

So basically I want to know if there is something related to 3D that is messing up my textures. The thing that really confuses me, though, is that the texture does display, it's just displaying the wrong one.

Oh yes, and let's say I made a tex3, tex4, and tex5, bound different images to all of them, and then bound them to shapes. They would all display the image I bound to tex5. If that makes sense.

I am using C++ and SFML and Ubuntu 10.10.

---

### Post by Eragon0605 on 2010-11-04
Bump. If I'm not being clear enough or you need more information, please tell me. I am not exactly an expert on these things...

---

### Post by Eragon0605 on 2010-11-09
Final bump.

---

### Post by GenBattle on 2010-11-10
I hate to be captain obvious, but it would appear that somehow all of your textures are pointing to the same memory location. But this would mean that all the values returned would be the same, which you have indicated isn't the case?

The only other reason i could think of that this might happen is that there is some sort of command buffer or something that is not being executed/flushed in between the texture loads.

Disclaimer: i don't have any experience to speak of working with OpenGL, i just thought i would try and be helpful, since you appear to be struggling to find people who can help you solve your problem. Sometimes all it takes is someone else to bounce ideas off.

---

### Post by Eragon0605 on 2010-11-10
Well, whatever the problem is, it's with the code itself. I have already tried it on two computers across three operating systems (Windows 7, Windows XP, and Ubuntu 10.10) and I get the exact same problem on all. I guess I can post the full source code here in a couple minutes (I need to boot up my other computer), it's still in the very early stages of development and is still quite short.

---

### Post by Eragon0605 on 2010-11-10
Here it is:
[PHP]
#include <SFML/Window.hpp>
#include <SOIL/SOIL.h>
#include <camera.h>

int rotspeed = 4, mvspeed = 4, roty = 0;

GLuint hap, hap2;

GLfloat fLightPos[4] = { 200.0f, 0.0f, 0.0f, 1.0f },
fNoLight[] = { 0.0f, 0.0f, 0.0f, 0.0f },
fLowLight[] = { 0.45f, 0.45f, 0.45f, 1.0f },
fBrightLight[] = { 1.0f, 1.0f, 1.0f, 1.0f };

float aspect, w, h;

void DrawCube();
void DrawGround();
void LoadTextures();

int main()
{
    // Create the main window
    sf::Window Window(sf::VideoMode(600, 600, 32), "SFML OpenGL");
    Window.UseVerticalSync(true);
    Window.ShowMouseCursor(false);

    Camera Cam(0.f, 0.f, 500.f);

    // Create a clock for measuring time elapsed
    sf::Clock Clock;

    // Set color and depth clear value
    //glClearDepth(1.f);
    glClearColor(0.f, 0.f, 0.f, 0.f);

    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    gluPerspective(45.f, 1.f, 1.f, 5000.f);

    glLightModelfv(GL_LIGHT_MODEL_AMBIENT, fNoLight);
    glLightfv(GL_LIGHT0, GL_AMBIENT, fLowLight);
    glLightfv(GL_LIGHT0, GL_DIFFUSE, fBrightLight);
    glLightfv(GL_LIGHT0, GL_SPECULAR, fBrightLight);
    glEnable(GL_LIGHTING);
    glEnable(GL_LIGHT0);

    glShadeModel(GL_SMOOTH);
    glEnable(GL_SHADE_MODEL);

    glEnable(GL_COLOR_MATERIAL);
    glColorMaterial(GL_FRONT_AND_BACK, GL_AMBIENT_AND_DIFFUSE);

    glEnable(GL_DEPTH_TEST);
    glEnable(GL_TEXTURE_2D);
    glEnable(GL_BLEND);
    glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);

    LoadTextures();

    while (Window.IsOpened())
    {
        glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

        glMatrixMode(GL_MODELVIEW);
        glLoadIdentity();

        sf::Event Event;
        while (Window.GetEvent(Event))
        {
            if (Event.Type == sf::Event::Closed)
                Window.Close();

            if ((Event.Type == sf::Event::KeyPressed) && (Event.Key.Code == sf::Key::Escape))
                Window.Close();

            if ((Event.Type == sf::Event::KeyPressed) && (Event.Key.Code == sf::Key::A))
                Cam.moveLoc(-mvspeed, 0, 0);

            if ((Event.Type == sf::Event::KeyPressed) && (Event.Key.Code == sf::Key::D))
                Cam.moveLoc(mvspeed, 0, 0);

            if ((Event.Type == sf::Event::KeyPressed) && (Event.Key.Code == sf::Key::W))
                Cam.moveLoc(0, 0, mvspeed);

            if ((Event.Type == sf::Event::KeyPressed) && (Event.Key.Code == sf::Key::S))
                Cam.moveLoc(0, 0, -mvspeed);

            if ((Event.Type == sf::Event::KeyPressed) && (Event.Key.Code == sf::Key::Right))
                Cam.rotateGlob(rotspeed, 0, 1, 0);

            if ((Event.Type == sf::Event::KeyPressed) && (Event.Key.Code == sf::Key::Left))
                Cam.rotateGlob(-rotspeed, 0, 1, 0);

            if (Event.Type == sf::Event::Resized)
            {
                glViewport(0, 0, Event.Size.Width, Event.Size.Height);

                w = Event.Size.Width, h = Event.Size.Height;

                aspect = w / h;

                glMatrixMode(GL_PROJECTION);
                glLoadIdentity();
                gluPerspective(45.f, aspect, 1.f, 5000.f);
                glMatrixMode(GL_MODELVIEW);
                glLoadIdentity();
            }
        }

        Cam.setView();

        glRotatef(roty, 1.f, 0.f, 0.f);

        DrawGround();

        DrawCube();

        glLightfv(GL_LIGHT0, GL_POSITION, fLightPos);

        Window.Display();
    }

    return EXIT_SUCCESS;
}

void DrawCube()
{
    glBegin(GL_QUADS);

        glColor3f(1.0f, 0.0f, 0.0f);

        glNormal3f(-50, -50, -50);
        glVertex3f(-50.f, -50.f, -50.f);
        glNormal3f(-50, 50, -50);
        glVertex3f(-50.f,  50.f, -50.f);
        glNormal3f(50, 50, -50);
        glVertex3f( 50.f,  50.f, -50.f);
        glNormal3f(50, -50, -50);
        glVertex3f( 50.f, -50.f, -50.f);

        glColor3f(0.0f, 1.0f, 0.0f);

        glNormal3f(-50, -50, 50);
        glVertex3f(-50.f, -50.f, 50.f);
        glNormal3f(-50, 50, 50);
        glVertex3f(-50.f,  50.f, 50.f);
        glNormal3f(50, 50, 50);
        glVertex3f( 50.f,  50.f, 50.f);
        glNormal3f(50, -50, 50);
        glVertex3f( 50.f, -50.f, 50.f);

        glColor3f(0.0f, 0.0f, 1.0f);

        glNormal3f(-50, -50, -50);
        glVertex3f(-50.f, -50.f, -50.f);
        glNormal3f(-50, 50, -50);
        glVertex3f(-50.f,  50.f, -50.f);
        glNormal3f(-50, 50, 50);
        glVertex3f(-50.f,  50.f,  50.f);
        glNormal3f(-50, -50, 50);
        glVertex3f(-50.f, -50.f,  50.f);

        glColor3f(1.0f, 1.0f, 0.0f);

        glBindTexture(GL_TEXTURE_3D, hap);

        glNormal3f(50, -50, -50);
        glTexCoord2f(1.0f, 0.0f); glVertex3f(50.f, -50.f, -50.f);
        glNormal3f(50, 50, -50);
        glTexCoord2f(1.0f, 1.0f); glVertex3f(50.f,  50.f, -50.f);
        glNormal3f(50, 50, 50);
        glTexCoord2f(0.0f, 1.0f); glVertex3f(50.f,  50.f,  50.f);
        glNormal3f(50, -50, 50);
        glTexCoord2f(0.0f, 0.0f); glVertex3f(50.f, -50.f,  50.f);

        glColor3f(0.0f, 1.0f, 1.0f);


        glNormal3f(-50, 50, 50);
        glVertex3f(-50.f, 50.f,  50.f);
        glNormal3f(-50, 50, -50);
        glVertex3f(-50.f, 50.f, -50.f);
        glNormal3f(50, 50, -50);
        glVertex3f( 50.f, 50.f, -50.f);
        glNormal3f(50, 50, 50);
        glVertex3f( 50.f, 50.f,  50.f);

        glEnd();
}

void DrawGround()
{
    glColor3f(1.0f, 1.0f, 1.0f);

    glBegin(GL_QUADS);
        glNormal3f(-50, -50, -50);
        glVertex3f(-1000.f, -51.f,  1000.f);
        glNormal3f(-50, 50, -50);
        glVertex3f(-1000.f, -51.f, -1000.f);
        glNormal3f(50, 50, -50);
        glVertex3f( 1000.f, -51.f, -1000.f);
        glNormal3f(50, -50, -50);
        glVertex3f( 1000.f, -51.f,  1000.f);
    glEnd();
}

void LoadTextures()
{
    hap = SOIL_load_OGL_texture
    (
        "happy.png",
        SOIL_LOAD_RGBA,
        SOIL_CREATE_NEW_ID,
        SOIL_FLAG_NTSC_SAFE_RGB | SOIL_FLAG_INVERT_Y
    );

    hap2 = SOIL_load_OGL_texture
    (
        "somehappy.png",
        SOIL_LOAD_RGBA,
        SOIL_CREATE_NEW_ID,
        SOIL_FLAG_NTSC_SAFE_RGB | SOIL_FLAG_INVERT_Y
    );
}[/PHP]I am using the camera library from: [http://www.flipcode.com/archives/OpenGL_Camera.shtml](http://www.flipcode.com/archives/OpenGL_Camera.shtml)

---

