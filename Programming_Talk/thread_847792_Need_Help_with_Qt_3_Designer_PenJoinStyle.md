---
title: "Need Help with Qt 3 Designer PenJoinStyle"
date: 2008-07-02
forum: Programming Talk
---

### Post by xclarax on 2008-07-02
Hi,

i m currently working on drawing the floor plan and i need to use MiterJoin Type in my drawing.

there is this Qt::PenJoinStyle(MiterJoin) but i didnt work in my program..
i need to join two rectangle in 45 degree MiterJoin...

i ll b really appreciated if anyone of u can help me solve the problem...

thx so much in advance :)

---

### Post by fifth on 2008-07-03
> **xclarax said:**
> Hi,

i m currently working on drawing the floor plan and i need to use MiterJoin Type in my drawing.

there is this Qt::PenJoinStyle(MiterJoin) but i didnt work in my program..
i need to join two rectangle in 45 degree MiterJoin...

i ll b really appreciated if anyone of u can help me solve the problem...

thx so much in advance :)

What did you mean by didnt work? Is the code not doing what you expect or or you getting errors? Would be easier to help if you could post a small compilable example of the problem.

---

### Post by xclarax on 2008-07-03
> **fifth said:**
> What did you mean by didnt work? Is the code not doing what you expect or or you getting errors? Would be easier to help if you could post a small compilable example of the problem.


HI here is the example i trying to work out...it's simple i jux wan to join the two rectangle using MiterJoin in 45 degrees.  Hope you can help me because i m totall new to Qt and I m not so sure whether it's the right way to use MiterJoin. Thx


//**************************************************************

#include <qwidget.h>
#include <qpainter.h>

#include <qapplication.h>
#include <math.h>


void draw( QPainter *p )
{
    	p->setBrush(Qt::HorPattern);
    	p->setPen(QPen(Qt::MiterJoin));        
	p->drawRect(100,100,25,100);
        p->drawRect(60,60, 25,100);   
       
        
        
}


typedef void (*draw_func)(QPainter*);

struct DrawThing {
    draw_func	 f;
    const char	*name;
};



DrawThing ourDrawFunctions[] = {
// name of the function, title presented to the user 

   { draw,	"Drawing the Joint" },
    { 0,		0 } };



class DrawView : public QWidget
{
    Q_OBJECT
public:
    DrawView();
    ~DrawView();
public slots:
    void   updateIt( int );
    void   printIt();
protected:
    void   drawIt( QPainter * );
    void   paintEvent( QPaintEvent * );
    void   resizeEvent( QResizeEvent * );
private:
    int		  drawindex;
    int		  maxindex;
};


//
// Construct the DrawView with buttons.
//

DrawView::DrawView()
{
    setCaption( "Joint Drawing" );
    setBackgroundMode(PaletteBase);
    drawindex = 0;				// draw first thing
}

//
// Clean up.
//
DrawView::~DrawView()
{

}

//
// Called when a radio button is clicked.
//

void DrawView::updateIt( int index )
{
    if ( index < maxindex ) {
        drawindex = index;
        update();
    }
}

//
// Calls the drawing function as specified by the radio buttons.
//

void DrawView::drawIt( QPainter *p )
{
    (*ourDrawFunctions[drawindex].f)(p);
}

//
// Called when the print button is clicked.
//

void DrawView::printIt()
{
   
}

//
// Called when the widget needs to be updated.
//

void DrawView::paintEvent( QPaintEvent * )
{
    QPainter paint( this );
    drawIt( &paint );
}

//
// Called when the widget has been resized.
// Moves the button group to the upper right corner
// of the widget.

void DrawView::resizeEvent( QResizeEvent * )
{
//    bgroup->move( width()-bgroup->width(), 0 );
}


//
// Create and display our widget.
//

#include "drawdemo.moc"

int main( int argc, char **argv )
{
    QApplication app( argc, argv );
    DrawView   draw;
    app.setMainWidget( &draw );
    draw.setCaption("Joint Drawing");
    draw.show();
    return app.exec();
}

---

