---
title: "Geany compilation w/ make"
date: 2012-03-15
forum: Programming Talk
---

### Post by mikeglaz on 2012-03-15
I just started using Geany for a C++ game.  I'm trying to learn OpenGL to recreate the classic game Asteroids.  Now when I build the project with make on the command line everything works perfectly.  Here are the contents of my Makefile:

```
objects = Asteroid.o bullet.o main.o Projectile.o ship.o

asteroids: $(objects)
	g++ -o asteroids $(objects) -lX11 -lXi -lglut -lGL -lGLU -lm
	
Asteroid.o: Asteroid.cpp
	g++ -c Asteroid.cpp

bullet.o: bullet.cpp
	g++ -c bullet.cpp

main.o: main.cpp
	g++ -c main.cpp

Projectile.o: Projectile.cpp
	g++ -c Projectile.cpp

ship.o: ship.cpp
	g++ -c ship.cpp

clean:
	rm asteroids Asteroid.o bullet.o main.o Projectile.o ship.o

```

Now when I build within Geany all the .o files are built correctly.  As you can see in my Makefile, the executable that's created is called 'asteroids'.  When I try to run the program from Geany I get this error message:
```
./geany_run_script.sh: 5: ./ship: not found
```
ship is one of my .h files.  And actually the word ship is replaced by whatever file is highlighted inside Geany at the time.  I don't know how to make it execute the file created by the Makefile 'asteroids'.

thanks,
mike

---

### Post by kingtaurus on 2012-03-15
> **mikeglaz said:**
> I just started using Geany for a C++ game.  I'm trying to learn OpenGL to recreate the classic game Asteroids.  Now when I build the project with make on the command line everything works perfectly.  Here are the contents of my Makefile:

```
objects = Asteroid.o bullet.o main.o Projectile.o ship.o

asteroids: $(objects)
	g++ -o asteroids $(objects) -lX11 -lXi -lglut -lGL -lGLU -lm
	
Asteroid.o: Asteroid.cpp
	g++ -c Asteroid.cpp

bullet.o: bullet.cpp
	g++ -c bullet.cpp

main.o: main.cpp
	g++ -c main.cpp

Projectile.o: Projectile.cpp
	g++ -c Projectile.cpp

ship.o: ship.cpp
	g++ -c ship.cpp

clean:
	rm asteroids Asteroid.o bullet.o main.o Projectile.o ship.o

```

Now when I build within Geany all the .o files are built correctly.  As you can see in my Makefile, the executable that's created is called 'asteroids'.  When I try to run the program from Geany I get this error message:
```
./geany_run_script.sh: 5: ./ship: not found
```
ship is one of my .h files.  And actually the word ship is replaced by whatever file is highlighted inside Geany at the time.  I don't know how to make it execute the file created by the Makefile 'asteroids'.

thanks,
mike

Your makefile appears to be correct (but add an all target -> all : asteroid). To get make to compile the program fully, (it appears that geany_run_script.sh is looking for the executable ship, rather than asteroid; you might have to edit this file):
```

make asteroid

```
to run the program use the following at the command-line (in the directory that holds the project).
```

./asteroid

```

---

