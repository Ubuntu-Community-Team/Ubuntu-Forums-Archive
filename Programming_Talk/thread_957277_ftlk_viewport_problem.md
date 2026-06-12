---
title: "ftlk viewport problem"
date: 2008-10-24
forum: Programming Talk
---

### Post by grandemahatma on 2008-10-24
hallo,
please can you help me with this?

I've got the following files:


GRAPHIC.CPP:

extern int dimensioneFinestraX;
extern int dimensioneFinestraY;
class Layoutublic Fl_Tile {
private:
Viewport *toplft;
public:
Layout(int x, int y, int w, int h) : Fl_Tile(x,y,w,h) {
box(FL_BORDER_BOX);
color(FL_GRAY);
int leftX=1;
int lunghezza = dimensioneFinestraX*4/5.0;
int topY=1;
int altezza = dimensioneFinestraY*4/5.0;
toplft = new Viewport(1,leftX,topY, lunghezza, altezza);
end();
}
};


VIEWPORT.CPP:

void Viewport::draw() {
cout<<"\nHHHHHH\n";
if ( !valid() ) {
valid(1);
glClearColor(0.5, 0.5, 1.0, 0.0);
glViewport(0, 0, w(), h());
}
{
glClearColor(0.5, 0.5, 1.0, 0.0);
glViewport(0, 0, w(), h());
}
}

with the following VIEWPORT.H:

class Viewport : public Fl_Gl_Window {
private:
protected:
void draw();
public:
Viewport(int view, int x, int y, int w, int h, char* l=0) : Fl_Gl_Window(x,y,w,h,l) {
}
};




when I compile, I got the following error:
main.cpp.text+0x477): undefined reference to `vtable for Viewport'
collect2: ld returned 1 exit status
make: *** [graphX] Error 1


if I delete the line "void draw();" in VIEWPORT.H, then it compiles but the viewport in my window doesn't work (it shows random lines and colors)

what should I do?
thanks a lot

---

### Post by grandemahatma on 2008-10-24
sorry, problem solved..  I had a messed-up makefile...

---

