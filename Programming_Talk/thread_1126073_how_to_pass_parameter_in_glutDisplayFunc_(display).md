---
title: "how to pass parameter in glutDisplayFunc (display);"
date: 2009-04-15
forum: Programming Talk
---

### Post by cosima on 2009-04-15
I need to draw a line using openGL.
The starting point and ending point of the line need to be accepted through command line input.
I had done the part to receive input but I can't find a way to pass these inputs to glutDisplayFunc(display) . 
display(void) is a callback function which is already defined. Adding one more parameter is impossible. 
Could anybody tell me how to do

Below is the code I had trouble with


void display(void)
{
	glClear (GL_COLOR_BUFFER_BIT); 
	glColor3f (1.0, 0.0, 0.0);

	lineBres(x0, y0, xEnd, yEnd);  //line drawing function

	glutSwapBuffers();
}

void main (int argc, char** argv)
{
	glutInit (&argc, argv); 
	glutInitDisplayMode (GLUT_DOUBLE | GLUT_RGB); 
	glutInitWindowSize (400, 400); 
	glutCreateWindow ("Line Rasterizer"); 

/*	char* x=argv[2];
	cout<<x<<endl;	*/

	init ( ); 
	glutDisplayFunc (display); 
	glutMainLoop ( ); 
}

thank you very much

---

### Post by markus123 on 2009-09-20
I found some help in [_[COLOR="Blue"]this post[/COLOR]_]("http://www.codeguru.com/forum/showthread.php?t=312700") 
Data that you want to draw must be declared as static. 
For example: 
#include[...]
static double matrix[40] = {0, 2, 4, 6};
[...]
myInit();
[...]
myDisplay() {
[...]
for(int i =0;i<40;i++){
glVertex2d((i*16), (matrix[i])*200 + 240);
glVertex2d((i*17), (matrix[i+1])*200 + 240);}
glEnd();
glFlush;
}
[...]
main();
[...]

It works well :guitar:

---

### Post by DougB1958 on 2009-09-20
More than being static, the key is that "parameter" information accessed by your display callback and initialized by something else has to be global (or more precisely, declared in a scope that allows it to be accessed by both the display callback and the initialization code -- but that pretty much means "global" in C). The code suggested by markus123 declares matrix as a global variable, and so works. But it doesn't strictly need the static keyword. (Although if I remember right, declaring a global variable static in C restricts its scope to the file in which it is declared, which isn't a bad thing to do to reduce the chances of accidental misuse of the global by other modules.)

---

