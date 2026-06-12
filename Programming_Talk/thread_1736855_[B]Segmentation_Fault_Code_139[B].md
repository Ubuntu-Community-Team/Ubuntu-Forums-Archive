---
title: "[B]Segmentation Fault Code 139?[/B]"
date: 2011-04-22
forum: Programming Talk
---

### Post by vivichrist on 2011-04-22
I think I maybe doing recursion wrong...?

main.cc
```
#include "myarea.h"
#include <gtkmm/main.h>
#include <gtkmm/window.h>

int main(int argc, char** argv)
{
   Gtk::Main kit(argc, argv);

   Gtk::Window win;
   win.set_title("DrawingArea");

   MyArea area;
   win.add(area);
   area.show();

   Gtk::Main::run(win);

   return 0;
}
```

myarea.h
```
#ifndef GTKMM_EXAMPLE_MYAREA_H
#define GTKMM_EXAMPLE_MYAREA_H

#include <vector>
#include <gtkmm/drawingarea.h>
#include "linesegment.h"

class MyArea : public Gtk::DrawingArea
{
  double sx, sy, length;
	double branchAngle;
	double shrinkage;
	int numBranches;
	std::vector<LineSegment> lines;
public:
  MyArea();
  virtual ~MyArea();

protected:
  //Override default signal handler:
  void make_tree(double nx, double ny, double dist, double ang, int branches, double propor);
  virtual bool on_expose_event(GdkEventExpose* event);
};

#endif // GTKMM_EXAMPLE_MYAREA_H
```

myarea.cc
```
#include "myarea.h"
#include <cmath>
#include <stdlib.h>
#include <cairomm/context.h>

using namespace std;

MyArea::MyArea(){
	branchAngle = M_PI*0.3333333333*(0.1+rand()*0.000012207);
	shrinkage = 0.5 + rand()*0.0000030518;
	numBranches = 5+rand()*0.000091553;
	sx = (double)(rand()%900);
	sy = (double)(400.0 + rand()%100);
	length = (double)(50 +(rand()%150));
	LineSegment line(sx, sy, sx, sy-length);
	lines.push_back(line);
	make_tree(sx, sy, length, -M_PI*0.5, 2, 1.0);
}

MyArea::~MyArea()
{
}

bool MyArea::on_expose_event(GdkEventExpose* event)
{
  // This is where we draw on the window
  Glib::RefPtr<Gdk::Window> window = get_window();
  if(window)
  {
    Gtk::Allocation allocation = get_allocation();
    const int width = allocation.get_width();
    const int height = allocation.get_height();

    // generate a tree coordinates from random center of the window


    Cairo::RefPtr<Cairo::Context> cr = window->create_cairo_context();


    // clip to the area indicated by the expose event so that we only redraw
    // the portion of the window that needs to be redrawn
    cr->rectangle(event->area.x, event->area.y,
            event->area.width, event->area.height);
    cr->clip();

    // draw red lines out from the center of the window
    cr->set_source_rgb(0.8, 0.0, 0.0);
    for(int i=0;i<(int)lines.size();i++){
	    cr->set_line_width(sqrt((lines[i].fx-lines[i].fy)+(lines[i].tx-lines[i].ty))*0.05);
	    cr->move_to(lines[i].fx, lines[i].fy);
	    cr->line_to(lines[i].tx, lines[i].ty);
	    cr->stroke();
		}
  }

  return true;
}

void MyArea::make_tree(double nx, double ny, double dist, double ang, int branches, double propor){
		// double rnddist = dist*((1-branches*0.1)*rand()+(branches*0.1));
		double newx = nx + dist*cos(ang);
		double newy = ny + dist*sin(ang);
		
		int cap = fmin(branches, numBranches);
		if (dist>3+(5.0/length))
			for (int i=1;i<=cap;i++)
				make_tree(newx, newy, dist*shrinkage, ang-(branchAngle*propor*i*(i%2>0?-1:1)), branches+1, propor);
};
```

---

### Post by lloyd_b on 2011-04-22
I'm not sure "shrinkage" is in fact shrinkage - rand() returns a value between 1 and MAX_INT (which on most machines is 4,294,967,296).  With this calculation```
shrinkage = 0.5 + rand()*0.0000030518;
``` for shrinkage, you end up with maximum value for shrinkage of 13107.88.  Which would be more "growage" than "shrinkage".

If shrinkage is greater than 1, then if this test```
if (dist>3+(5.0/length))
``` is true to start with, then you've got endless recursion, as "length" doesn't change, and "dist" will increase each time you recurse.

I'm guessing you're working from example code that presumes MAX_INT to be 65536 (16 bit int's) rather than 4,294,967,296 (32 bit int's), in which case```
shrinkage = 0.5 + (rand()%65536)*0.0000030518;
``` should ensure shrinkage is never greater than 1 (it would have a max value of 0.7).

Lloyd B.

---

### Post by vivichrist on 2011-04-22
thanks so much lloyd_b that was a really insane problem that was driving me round the bend. I still have the problem of having nothing rendered... perhaps I should have made a const for 1/MAX_INT ? but yeah cheers and kudos to you! :D

---

### Post by vivichrist on 2011-04-22
so, working code goes something like this:

```
#include "myarea.h"
#include <limits>
#include <cmath>
#include <stdlib.h>
#include <cairomm/context.h>

using namespace std;

MyArea::MyArea()
{
	const double inverter = 1/std::numeric_limits<int>::max();
	branchAngle = M_PI*0.3333333333*(0.1+rand()*inverter*0.5);
	shrinkage = 0.5+rand()*inverter*0.1;
	numBranches = 5+rand()*inverter*3;
	sx = (double)(rand()%900);
	sy = (double)(400.0 + rand()%100);
	length = (double)(50 +(rand()%150));
	LineSegment line(sx, sy, sx, sy-length);
	lines.push_back(line);
	make_tree(sx, sy, length, -M_PI*0.5, 2, 1.0);
}

MyArea::~MyArea()
{
}

bool MyArea::on_expose_event(GdkEventExpose* event)
{
  // This is where we draw on the window
  Glib::RefPtr<Gdk::Window> window = get_window();
  if(window)
  {
    Gtk::Allocation allocation = get_allocation();
    const int width = allocation.get_width();
    const int height = allocation.get_height();
    cout << "drawing" << endl;

    // generate a tree coordinates from random center of the window


    Cairo::RefPtr<Cairo::Context> cr = window->create_cairo_context();


    // clip to the area indicated by the expose event so that we only redraw
    // the portion of the window that needs to be redrawn
    cr->rectangle(event->area.x, event->area.y,
            event->area.width, event->area.height);
    cr->clip();

    // draw red lines out from the center of the window
    cr->set_source_rgb(0.8, 0.0, 0.0);
    for(int i=0;i<(int)lines.size();i++){
	    cr->set_line_width(sqrt(abs(lines[i].fx-lines[i].fy)+abs(lines[i].tx-lines[i].ty))*0.1);
	    // cout << "linewidth:" << sqrt(abs(lines[i].fx-lines[i].fy)+abs(lines[i].tx-lines[i].ty))*0.5 << endl;
	    cr->move_to(lines[i].fx, lines[i].fy);
	    // cout << "move:" << lines[i].fx << ":" << lines[i].fy << endl;
	    cr->line_to(lines[i].tx, lines[i].ty);
	    // cout << "line:" << lines[i].tx << ":" << lines[i].ty << endl;
	    cr->stroke();
		}
  }

  return true;
}

void MyArea::make_tree(double nx, double ny, double dist, double ang, int branches, double propor){
		// double rnddist = dist*((1-branches*0.1)*rand()+(branches*0.1));
		double newx = nx + dist*cos(ang);
		double newy = ny + dist*sin(ang);
		LineSegment line(nx, ny, newx, newy);
		lines.push_back(line);
		int cap = fmin(branches, numBranches);
		if (dist>3) //+(5.0/length)
			for (int i=1;i<=cap;i++)
				make_tree(newx, newy, dist*shrinkage, ang-(branchAngle*propor*i*(i%2>0?-1:1)), branches+1, propor);
};
```

---

