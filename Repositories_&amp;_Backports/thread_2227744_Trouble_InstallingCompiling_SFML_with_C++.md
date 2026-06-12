---
title: "Trouble Installing/Compiling SFML with C++"
date: 2014-06-03
forum: Repositories &amp; Backports
---

### Post by mckinnonryall on 2014-06-03
***_[SIZE=5]SOLVED: See third post[/SIZE]_***

I'm on my second programming language, and I decided I wanted to make a game or music player. I chose SFML, merely because it was more feature-rich. I tried using "[COLOR=#000000][FONT=Consolas]sudo apt-get install libsfml-dev"[/FONT][/COLOR], and it worked. I went to compile a program, and it gave me:
```
make test[COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR]g++     test.cpp   -o test
/tmp/cc5DhUEp.o: In function `main':
test.cpp:(.text+0xf7): undefined reference to `sf::String::String(char const*, std::locale const&)'
test.cpp:(.text+0x115): undefined reference to `sf::VideoMode::VideoMode(unsigned int, unsigned int, unsigned int)'
test.cpp:(.text+0x148): undefined reference to `sf::RenderWindow::RenderWindow(sf::VideoMode, sf::String const&, unsigned int, sf::ContextSettings const&)'
test.cpp:(.text+0x182): undefined reference to `sf::CircleShape::CircleShape(float, unsigned int)'
test.cpp:(.text+0x18e): undefined reference to `sf::Color::Green'
test.cpp:(.text+0x196): undefined reference to `sf::Shape::setFillColor(sf::Color const&)'
test.cpp:(.text+0x1b6): undefined reference to `sf::Window::close()'
test.cpp:(.text+0x1cf): undefined reference to `sf::Window::pollEvent(sf::Event&)'
test.cpp:(.text+0x1f7): undefined reference to `sf::Color::Color(unsigned char, unsigned char, unsigned char, unsigned char)'
test.cpp:(.text+0x214): undefined reference to `sf::RenderTarget::clear(sf::Color const&)'
test.cpp:(.text+0x22b): undefined reference to `sf::RenderStates::Default'
test.cpp:(.text+0x236): undefined reference to `sf::RenderTarget::draw(sf::Drawable const&, sf::RenderStates const&)'
test.cpp:(.text+0x245): undefined reference to `sf::Window::display()'
test.cpp:(.text+0x254): undefined reference to `sf::Window::isOpen() const'
test.cpp:(.text+0x27f): undefined reference to `sf::RenderWindow::~RenderWindow()'
test.cpp:(.text+0x2a9): undefined reference to `sf::RenderWindow::~RenderWindow()'
test.cpp:(.text+0x2ee): undefined reference to `sf::RenderWindow::~RenderWindow()'
/tmp/cc5DhUEp.o: In function `sf::CircleShape::~CircleShape()':
test.cpp:(.text._ZN2sf11CircleShapeD2Ev[_ZN2sf11CircleShapeD5Ev]+0x13): undefined reference to `vtable for sf::CircleShape'
test.cpp:(.text._ZN2sf11CircleShapeD2Ev[_ZN2sf11CircleShapeD5Ev]+0x1f): undefined reference to `vtable for sf::CircleShape'
test.cpp:(.text._ZN2sf11CircleShapeD2Ev[_ZN2sf11CircleShapeD5Ev]+0x2b): undefined reference to `sf::Shape::~Shape()'
collect2: error: ld returned 1 exit status

```
I don't think it was installed to a non-standard directory, because I used apt-get. If it was, where was it installed to, and how can I point the compiler there?
I tried the instructions on this site: "http://en.sfml-dev.org/forums/index.php?topic=9808.0", but I still received the same errors. What, exactly, is wrong, and how can I fix it?

---

### Post by steeldriver on 2014-06-03
Regardless of the installation directory you will likely need to specify the library/libraries to be linked on the g++ command line. I'm not familiar with SFML but it looks like it will be something like

```

g++ test.cpp -o test [B]-lsfml-graphics
[/B]
```

Non-standard install directories would require a library *path* specification like -L /path/to/libdir as well.

to link the libsfml-graphics library. There may be additional requirements e.g. other libsfml-* libraries or lower-level libraries of the underlying toolkit(s) such as GL.

---

### Post by mckinnonryall on 2014-06-03
That took away most of my errors. However, I got more cryptic errors.
```
/usr/bin/ld: /tmp/cc25Iy5w.o: undefined reference to symbol '_ZN2sf9VideoModeC1Ejjj'//usr/local/lib/libsfml-window.so.2: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status

```
I tried adding "-lsfml-window" and got a similar error. I repeated.
Eventually, I tried "g++ test.cpp -o test -lsfml-graphics -lsfml-window -lsfml-system" and it worked. Thank you!

---

