---
title: "glDrawArrays() results in a bad image"
date: 2009-12-24
forum: Programming Talk
---

### Post by Quarg on 2009-12-24
I am taking an OpenGL tutorial, and am working with drawing things using arrays. Using the function glDrawArrays(GL_QUADS, 0, 24); results in a bad render, with a bizzare looking cube; with what looks like a black quad being drawn on it. using glArrayElement(0 - 7); results in a well-drawn quad, with no bad quads being drawn randomly. 
Any ideas as to why this is happening? 
Here's my code:
```

#include<GL/gl.h>
#include<GL/glut.h>
#include<stdio.h>
#include<stdlib.h>
//rotation variables
float xangle, yangle; 
//keyboard function
void keyboard(unsigned char key, int x, int y)
 {
	switch(key)
	 {
		case (27):
			exit(0); 
		break; 

		case ('q'):
			exit(0);
		break;
	 } 
 } 
//special key function 
void special(int key, int x, int y)
 {
	switch(key) {
		case (GLUT_KEY_UP):
			xangle += 1; 
		break;
		case (GLUT_KEY_DOWN):
			xangle -= 1; 
		break;
		case (GLUT_KEY_RIGHT):
			yangle += 1; 
		break;
		case (GLUT_KEY_LEFT):
			yangle -= 1; 	
		break; 
  	 }
	glutPostRedisplay(); 
 } 
//resize function
void resize(int width, int height)
 {
	glViewport(0, 0, (GLsizei)width, (GLsizei)height); 
	glMatrixMode(GL_PROJECTION); 
	glLoadIdentity(); 
 } 
//display function 
void display(void)
 {
	//the big array....
	static GLfloat cube[] = 
	 { 
	   //Quad one	
	   /*color*/ 1.0, 0.0, 0.0, /*vertex*/ 0.4, 0.4, 0.4,    // color: red, vertex is upper right forward corner 
	   /*color*/ 0.0, 1.0, 0.0, /*vertex*/ 0.4, -0.4, 0.4,   // color: green, vertex is lower right forward corner
	   /*color*/ 0.0, 0.0, 1.0, /*vertex*/ -0.4, -0.4, 0.4,  // color: blue, vertex is lower left forward corner
	   /*color*/ 1.0, 1.0, 0.0, /*vertex*/ -0.4, 0.4, 0.4,   // color: bizzare, vertex is in upper left forward corner
	   //Quad two
	   /*color*/ 1.0, 1.0, 0.0, /*vertex*/ -0.4, 0.4, 0.4,   // color: bizzare, vertex is in upper left forward corner
	   /*color*/ 1.0, 0.0, 1.0, /*vertex*/ -0.4, 0.4, -0.4,  // color: bizzare, vertex is in upper left back corner
	   /*color*/ 0.5, 0.0, 1.0, /*vertex*/ -0.4, -0.4, -0.4, // color: bizzare, vertex is in lower left back corner
	   /*color*/ 0.0, 0.0, 1.0, /*vertex*/ -0.4, -0.4, 0.4,  // color: blue, vertex is lower left forward corner
	   //Quad three
	   /*color*/ 1.0, 0.0, 1.0, /*vertex*/ -0.4, 0.4, -0.4,  // color: bizzare, vertex is in upper left back corner
	   /*color*/ 0.0, 1.0, 1.0, /*vertex*/ 0.4, 0.4, -0.4,   // color: bizzare, vertex is in upper right back corner
	   /*color*/ 0.5, 1.0, 0.0, /*vertex*/ 0.4, -0.4, -0.4,  // color: bizzare, vertex is in lower right back corner
	   /*color*/ 0.5, 0.0, 1.0, /*vertex*/ -0.4, -0.4, -0.4, // color: bizzare, vertex is in lower left back corner
	   //Quad four
	   /*color*/ 0.5, 1.0, 0.0, /*vertex*/ 0.4, -0.4, -0.4,  // color: bizzare, vertex is in lower right back corner
           /*color*/ 0.0, 1.0, 1.0, /*vertex*/ 0.4, 0.4, -0.4,   // color: bizzare, vertex is in upper right back corner
	   /*color*/ 1.0, 0.0, 0.0, /*vertex*/ 0.4, 0.4, 0.4,    // color: red, vertex is upper right forward corner 
           /*color*/ 0.0, 1.0, 0.0, /*vertex*/ 0.4, -0.4, 0.4,   // color: green, vertex is lower right forward corner			
	   };
	glClearColor(0, 0, 0, 0); 	//Specify the clearing color as black
	glClear(GL_COLOR_BUFFER_BIT);   //clear the buffers 

	
	
	glInterleavedArrays (GL_C3F_V3F, 0, cube); //initializes vertex and color arrays, interleaving them
	glRotatef(xangle, 1.0, 0.0, 0.0);  //rotate shape xangle
	glRotatef(yangle, 0.0, 1.0, 0.0);  //rotate shape yangle
	glDrawArrays(GL_QUADS, 0, 24);     // draw the quads (this results in a flickering image
//does more or less the same thing, with glArrayElement. Not using the glArrayElement can reduce function calls. 
/*	glBegin(GL_QUADS); 
		
		glArrayElement(0); 
		glArrayElement(1); 
		glArrayElement(2); 
		glArrayElement(3); 
//one quad
		glArrayElement(4); 
		glArrayElement(5); 
		glArrayElement(6); 
		glArrayElement(7); 
//two quads
		
		glArrayElement(0); 
		glArrayElement(5); 
		glArrayElement(6); 
		glArrayElement(1);
//three quads
		glArrayElement(3); 
		glArrayElement(4); 
		glArrayElement(7); 
		glArrayElement(2); 
	
	glEnd(); 
*/
	
	glutSwapBuffers(); //swap out buffers
 } 

int main(int argc, char *argv[])
 {
	glutInit(&argc, argv); 			      // initialize Glut using command line parameters
	glutInitDisplayMode(GLUT_RGBA | GLUT_DOUBLE); //display mode is a single buffered rgb window
	glutInitWindowSize(550, 550); 
	glutInitWindowPosition(0, 0); 	
	glutCreateWindow("Test Drawing - Arrays"); 
	glutDisplayFunc(display); 
	glutKeyboardFunc(keyboard); 
	glutSpecialFunc(special); 
	glutMainLoop(); 
 return 0; 
 } 

```
I attached a screenshot of the bad cube below.
thanks in advance for any help!

---

