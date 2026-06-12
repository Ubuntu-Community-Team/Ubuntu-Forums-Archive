---
title: "[SOLVED] Creeping gpc polygon"
date: 2008-03-29
forum: Programming Talk
---

### Post by Zeotronic on 2008-03-29
The other day I wrote code to render my gpc_polygon (and gpc_tristrip) with SDL... however, when I tried relocating it, to the position on the screen I wanted it, it would just 'walk' right off the screen... which to my understanding of my own code is not possible. Needless to say that somewhere I made a mistake, and I am posting all code that I imagine could possibly be related, in the hopes that someone can point it out to me... *Oh, I'll get arround to trying to figure it out myself,* but much to my dismay, I am going to be occupied all day today.
```
gpc_tristrip Tristrip_Rotate(gpc_tristrip tristrip,float rotate){
	//Moves the Tristrip
	long scanx=0,scany=0;
	while (scanx<tristrip.num_strips){
		while (scany<tristrip.strip[scanx].num_vertices){
			tristrip.strip[scanx].vertex[scany].x*=x;
			tristrip.strip[scanx].vertex[scany].y+=y;
			scany++;
		}
		scanx++; scany=0;
	}
	return tristrip;
}
gpc_tristrip Tristrip_Move(gpc_tristrip tristrip,float x,float y){
	//Moves the Tristrip
	long scanx=0,scany=0;
	while (scanx<tristrip.num_strips){
		while (scany<tristrip.strip[scanx].num_vertices){
			tristrip.strip[scanx].vertex[scany].x+=x;
			tristrip.strip[scanx].vertex[scany].y+=y;
			scany++;
		}
		scanx++; scany=0;
	}
	return tristrip;
}
void Tristrip_XAYA(gpc_tristrip tristrip,unsigned long strip,short* x,short* y){
	//Converts the X,Y in gpc_tristrip to two seperate arrays.
	long scan=0;
	while (scan<tristrip.strip[strip].num_vertices){
		x[scan]=(int)tristrip.strip[strip].vertex[scan].x;
		y[scan]=(int)tristrip.strip[strip].vertex[scan].y;
		scan++;
	}
}
gpc_polygon Polygon_Rotate(gpc_polygon polygon,float rotate){
	
	return polygon;
}
gpc_polygon Polygon_Move(gpc_polygon polygon,float x,float y){
	//Moves the Polygon
	long scanx=0,scany=0;
	while (scanx<polygon.num_contours){
		while (scany<polygon.contour[scanx].num_vertices){
			polygon.contour[scanx].vertex[scany].x+=x;
			polygon.contour[scanx].vertex[scany].y+=y;
			scany++;
		}
		scanx++; scany=0;
	}
	return polygon;
}
void Polygon_XAYA(gpc_polygon polygon,unsigned long contour,short* x,short* y){
	//Converts the X,Y in gpc_polygon to two seperate arrays.
	long scan=0;
	while (scan<polygon.contour[contour].num_vertices){
		x[scan]=(int)polygon.contour[contour].vertex[scan].x;
		y[scan]=(int)polygon.contour[contour].vertex[scan].y;
		scan++;
	}
}
void filledTrigonStripRGBA(SDL_Surface* dst,Sint16* vx,Sint16* vy,int n,Uint8 r,Uint8 g,Uint8 b,Uint8 a){
	//Draws a filled trigon strip.
	long scan=0;
	while (scan+2<n){
		filledTrigonRGBA(dst,vx[scan],vy[scan],vx[scan+1],vy[scan+1],vx[scan+2],vy[scan+2],r,g,b,a);
		scan++;
	}
}
SDL_Surface* Draw_Polygon(gpc_polygon polygon,gpc_tristrip tristrip,float x,float y,float rotate,SDL_Surface* destination=screen){
	//Draws the polygon and tristrip, for map objects.
	//Vertex Arrays
	long scan=0;
	
	//Tristrip
	while (scan<tristrip.num_strips){
		short xa[tristrip.strip[scan].num_vertices],ya[tristrip.strip[scan].num_vertices];
		tristrip=Tristrip_Move(Tristrip_Rotate(tristrip,rotate),x,y);
		Tristrip_XAYA(tristrip,scan,xa,ya);//Convert strip to vertex arrays
		filledTrigonStripRGBA(destination,xa,ya,tristrip.strip[scan].num_vertices,128,128,128,255);
		scan++;//Next strip
	}/**/
	scan=0;
	
	//Polygon
	while (scan<polygon.num_contours){
		short xa[polygon.contour[scan].num_vertices],ya[polygon.contour[scan].num_vertices];
		polygon=Polygon_Move(Polygon_Rotate(polygon,rotate),x,y);
		Polygon_XAYA(polygon,scan,xa,ya);//Convert contour to vertex arrays
		polygonRGBA(destination,xa,ya,polygon.contour[scan].num_vertices,255,255,255,255);
		scan++;//Next contour
	}/**/
	
	return destination;
}

//MAIN//

int main(int argc,char* args[])
{
	SDL_Init(SDL_INIT_EVERYTHING);
	SDL_initFramerate(&frames);
	
	
	gpc_polygon poly1, poly2, result;
    // poly1 is a square with vertices (0,0),(1,0),(1,1),(0,1)
    poly1.num_contours = 1;
    poly1.hole = (int *) malloc(sizeof(int));
    poly1.hole[0] = 0;
    poly1.contour = (gpc_vertex_list *) malloc(sizeof(gpc_vertex_list));
    poly1.contour->num_vertices = 4;
    poly1.contour[0].vertex = (gpc_vertex *) malloc(4*sizeof(gpc_vertex));
    poly1.contour[0].vertex[0].x = 0.0;
    poly1.contour[0].vertex[0].y = 0.0;
    poly1.contour[0].vertex[1].x = 10.0;
    poly1.contour[0].vertex[1].y = 0.0;
    poly1.contour[0].vertex[2].x = 10.0;
    poly1.contour[0].vertex[2].y = 10.0;
    poly1.contour[0].vertex[3].x = 0.0;
    poly1.contour[0].vertex[3].y = 10.0;
    // poly2 is a triangle with vertices (0.25,0.25),(1.25,0.25),(0.25,1.25)
    poly2.num_contours = 1;
    poly2.hole = (int *) malloc(sizeof(int));
    poly2.hole[0] = 0;
    poly2.contour = (gpc_vertex_list *) malloc(sizeof(gpc_vertex_list));
    poly2.contour->num_vertices = 3;
    poly2.contour[0].vertex = (gpc_vertex *) malloc(3*sizeof(gpc_vertex));
    poly2.contour[0].vertex[0].x = 2.5;
    poly2.contour[0].vertex[0].y = 2.5;
    poly2.contour[0].vertex[1].x = 12.5;
    poly2.contour[0].vertex[1].y = 2.5;
    poly2.contour[0].vertex[2].x = 2.5;
    poly2.contour[0].vertex[2].y = 12.5;
    gpc_polygon_clip(GPC_UNION, &poly1, &poly2, &result);
	gpc_tristrip tristrip;
	gpc_polygon_to_tristrip(&result,&tristrip);
	
	while (!quit){//Program Loop
		//Window Handling
		if (GL){//OpenGL Rendering
			if (full)
			{screen=SDL_SetVideoMode(fullscreen.x,fullscreen.y,bittage,SDL_FULLSCREEN | SDL_OPENGL);}
			else
			{screen=SDL_SetVideoMode(windowed.x,windowed.y,bittage,SDL_OPENGL);}
		}
		else{//SDL Rendering
			if (full)
			{screen=SDL_SetVideoMode(fullscreen.x,fullscreen.y,bittage,SDL_HWSURFACE | SDL_FULLSCREEN);}
			else
			{screen=SDL_SetVideoMode(windowed.x,windowed.y,bittage,SDL_HWSURFACE);}
		}
		SDL_WM_SetCaption("Distruction Syndrome",NULL);
		SDL_setFramerate(&frames,fps);
		change_display=0;
		
		while (!quit && !change_display){//Game Loop
			Input_Master();
			//DRAWING
			boxRGBA(screen,0,0,320,240,0,0,0,255);
			
			Draw_Polygon(result,tristrip,1,1,0,screen);
			
			SDL_framerateDelay(&frames);
			SDL_Flip(screen);
		}
		SDL_FreeSurface(screen);
	}
	SDL_Quit();
	return 0;
}

```
Take note that the tristrip creeps off the screen twice as fast as the polygon.

I'm sure you'll notice that I haven't written the rotation code yet. (just pointing it out to you)

---

### Post by Zeotronic on 2008-03-29
Wait... I understand whats wrong now!

---

