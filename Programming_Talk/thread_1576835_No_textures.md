---
title: "No textures"
date: 2010-09-17
forum: Programming Talk
---

### Post by Eragon0605 on 2010-09-17
Hello all. I am having some trouble with textures today. Over the summer, I started to create a program using all my C++/OpenGL skills. It took a bit of trial and error with the code, but I finally got textures in my program using SOIL. It's now been seven weeks since I touched the program. Now, when I got back to try and work on my program again, the textures won't display.They simply appear white, as if nothing is being loaded. My program is several thousand lines long and, therefore, I won't post it here, but I did make another, small program that uses textures and it has the same issue. It uses SFML, SOIL, OpenGL, and C++. Basically, I want to find out if there is something wrong with my code, or if there is something wrong with one of the packages on my system. I am using Ubuntu 10.04. 
[PHP]
#include <SFML/Graphics.hpp>
#include <SOIL/SOIL.h>

GLuint circle;

int main()
{
    sf::Window App(sf::VideoMode(200, 200, 32), "SFML OpenGL");

    glClearColor(1.0f, 0.f, 0.f, 0.f);

    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    glOrtho(-200, 200, 200, -200, 1.0, -1.0);

    circle = SOIL_load_OGL_texture
    (
        "burger.png",
        SOIL_LOAD_AUTO,
        SOIL_CREATE_NEW_ID,
        SOIL_FLAG_INVERT_Y
    );

    glEnable(GL_BLEND);
    glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);

    while (App.IsOpened())
    {
        sf::Event Event;
        while (App.GetEvent(Event))
        {
            if (Event.Type == sf::Event::Closed)
                App.Close();

            if ((Event.Type == sf::Event::KeyPressed) && (Event.Key.Code == sf::Key::Escape))
                App.Close();

            if (Event.Type == sf::Event::Resized)
                glViewport(0, 0, Event.Size.Width, Event.Size.Height);
        }

        App.SetActive();

        glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

        glMatrixMode(GL_MODELVIEW);
        glLoadIdentity();

        glColor3f(1.0f, 1.0f, 1.0f);

        glBindTexture(GL_TEXTURE_2D, circle);

        glBegin(GL_POLYGON);
            glTexCoord2f(0.0, 0.0); glVertex2f(-16, -16);
            glTexCoord2f(1.0, 0.0); glVertex2f(16, -16);
            glTexCoord2f(1.0, 1.0); glVertex2f(16, 16);
            glTexCoord2f(0.0, 1.0); glVertex2f(-16, 16);
        glEnd();

        App.Display();
    }

    return EXIT_SUCCESS;
}
[/PHP]I attatched an image of what my program displays.

---

### Post by slooksterpsv on 2010-09-17
I don't see glEnable(GL_TEXTURE_2D) anywhere... am I missing it? Try enabling that and see if that helps.

---

### Post by Eragon0605 on 2010-09-17
Ah, yes, I forgot to to put that in there. Anyways, adding that doesn't help at all, I'm still getting the exact same results (it was enabled in my original program).

---

### Post by slooksterpsv on 2010-09-17
I compiled your version (above) and mine after adding glEnable(GL_TEXTURE_2D); after glEnable(GL_BLEND); and it worked for me thatn. I didn't work with your initial version, try this one:
[php]
#include <SFML/Graphics.hpp>
#include <SOIL/SOIL.h>

GLuint circle;

int main()
{
    sf::Window App(sf::VideoMode(200, 200, 32), "SFML OpenGL");

    glClearColor(1.0f, 0.f, 0.f, 0.f);

    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    glOrtho(-200, 200, 200, -200, 1.0, -1.0);

    circle = SOIL_load_OGL_texture
    (
        "burger.png",
        SOIL_LOAD_AUTO,
        SOIL_CREATE_NEW_ID,
        SOIL_FLAG_INVERT_Y
    );

    glEnable(GL_BLEND);
    glEnable(GL_TEXTURE_2D);
    glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);

    while (App.IsOpened())
    {
        sf::Event Event;
        while (App.GetEvent(Event))
        {
            if (Event.Type == sf::Event::Closed)
                App.Close();

            if ((Event.Type == sf::Event::KeyPressed) && (Event.Key.Code == sf::Key::Escape))
                App.Close();

            if (Event.Type == sf::Event::Resized)
                glViewport(0, 0, Event.Size.Width, Event.Size.Height);
        }

        App.SetActive();

        glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

        glMatrixMode(GL_MODELVIEW);
        glLoadIdentity();

        glColor3f(1.0f, 1.0f, 1.0f);

        glBindTexture(GL_TEXTURE_2D, circle);

        glBegin(GL_POLYGON);
            glTexCoord2f(0.0, 0.0); glVertex2f(-16, -16);
            glTexCoord2f(1.0, 0.0); glVertex2f(16, -16);
            glTexCoord2f(1.0, 1.0); glVertex2f(16, 16);
            glTexCoord2f(0.0, 1.0); glVertex2f(-16, 16);
        glEnd();

        App.Display();
    }

    return EXIT_SUCCESS;
}  
[/php]

Also I'm compiling with -lsfml-graphics and -lSOIL

---

### Post by Eragon0605 on 2010-09-17
Nope, no change with your version. I put the image file in the same folder as the cpp file, that is correct, yes?

---

### Post by slooksterpsv on 2010-09-18
> **Eragon0605 said:**
> Nope, no change with your version. I put the image file in the same folder as the cpp file, that is correct, yes?

Well with the outputted file, so if it outputs a.out, you put it where a.out is. Put the image in the same location as the executable.

---

### Post by Eragon0605 on 2010-09-18
> Well with the outputted file, so if it outputs a.out, you put it where  a.out is. Put the image in the same location as the executable. 	

Wow, I'm pretty amazing... Spaced out there a little, sorry. Anyways, yes, the output file is in the same directory as the image.

---

### Post by slooksterpsv on 2010-09-18
ahh if I go down one directory then try to run it, it doesn't find the graphic - so either run the program from the same directory as the image or it won't work. You may have to get the present directory for where you executed the program, then tell it to use the image in that directory

---

### Post by slooksterpsv on 2010-09-18
[php]
#include <SFML/Graphics.hpp>
#include <SOIL/SOIL.h>
#include <iostream>

GLuint circle;

int main(int argc, char *argv[])
{
    //Define directory string, file name string, and a combination string
    std::string directory = argv[0];
    std::string file = "/burger.png";
    std::string ffp;
    
    //Get the directory where the program is running from
    size_t find;
    find = directory.find_last_of("/\\");
    directory = directory.substr(0,find);

    //Combine directory and file name
    ffp = directory + file;

    //Extract and convert it to a constant char pointer
    const char *fullFile = ffp.c_str();

    sf::Window App(sf::VideoMode(200, 200, 32), "SFML OpenGL");

    glClearColor(1.0f, 0.f, 0.f, 0.f);

    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    glOrtho(-200, 200, 200, -200, 1.0, -1.0);

    circle = SOIL_load_OGL_texture
    (
        fullFile,
        SOIL_LOAD_AUTO,
        SOIL_CREATE_NEW_ID,
        SOIL_FLAG_INVERT_Y
    );

    glEnable(GL_BLEND);
    glEnable(GL_TEXTURE_2D);
    glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);

    while (App.IsOpened())
    {
        sf::Event Event;
        while (App.GetEvent(Event))
        {
            if (Event.Type == sf::Event::Closed)
                App.Close();

            if ((Event.Type == sf::Event::KeyPressed) && (Event.Key.Code == sf::Key::Escape))
                App.Close();

            if (Event.Type == sf::Event::Resized)
                glViewport(0, 0, Event.Size.Width, Event.Size.Height);
        }

        App.SetActive();

        glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

        glMatrixMode(GL_MODELVIEW);
        glLoadIdentity();

        glColor3f(1.0f, 1.0f, 1.0f);

        glBindTexture(GL_TEXTURE_2D, circle);

        glBegin(GL_POLYGON);
            glTexCoord2f(0.0, 0.0); glVertex2f(-160.0f, -160.0f);
            glTexCoord2f(1.0, 0.0); glVertex2f(160.0f, -160.0f);
            glTexCoord2f(1.0, 1.0); glVertex2f(160.0f, 160.0f);
            glTexCoord2f(0.0, 1.0); glVertex2f(-160.0f, 160.0f);
        glEnd();

        App.Display();
    }

    return EXIT_SUCCESS;
}  
[/php]

Try that, now it will find the directory where your image is located as long as it's located where the program  you're running is.

---

### Post by Eragon0605 on 2010-09-18
I got a nice big white square. The cpp, executable, and image files are all in my home folder. I even cd to my home directory in a terminal and ran it from there, but it still doesn't work. I'm thinking that maybe one of my lib or header files is corrupt or something. I've messed around with my computer quite a bit since I last successfully used textures. I'll try compiling it on my laptop tomorrow just to make sure that I'm not doing anything wrong.

---

### Post by Eragon0605 on 2010-09-18
Yeah, my texture displays on my laptop. I'll try reinstalling SOIL, OpenGL, etc.

---

### Post by Eragon0605 on 2010-09-18
Well I completely removed all the package files I could find related to programming, reinstalled them, and then the textures displayed. Thanks for your time.

---

