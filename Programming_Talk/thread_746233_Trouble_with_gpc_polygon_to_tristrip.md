---
title: "Trouble with gpc_polygon_to_tristrip"
date: 2008-04-05
forum: Programming Talk
---

### Post by Zeotronic on 2008-04-05
Recently I wrote code to convert my Box2D bodies' shapes into GPC polygons and tristrips. I decided rather than performing the operations to the tristrip as well, I would just convert the polygon into a tristrip... however, this has caused my game to crash on startup, with a "Segmentation Fault". Here is my code which is probably related to the crash, if you would like to help me but need more, let me know... though I personally think it unlikely there is a problem beyond this scope (as I have actually commented out all of the code related to tristrip rendering, and have the game working with out).
```
void PolygonDef_GPC(Body_Shape* bodyshape,b2PolygonDef* polydef,bool add=1){
	long scan=0;
	gpc_polygon shape;
	gpc_polygon former;
	
	//If bodyshape doesn't have a polygon
	if (bodyshape->polygon==NULL)
	{bodyshape->polygon=new gpc_polygon();}
	
	//Copy bodyshape polygon
	former=Copy_Polygon(*bodyshape->polygon);
	
	//If bodyshape doesn't have a tristrip
	if (bodyshape->tristrip==NULL)
	{bodyshape->tristrip=new gpc_tristrip();}
	
	//Prepare shape
	shape.num_contours=1;
	shape.hole=new int();
	shape.hole[0]=0;
	shape.contour=new gpc_vertex_list();
	shape.contour[0].num_vertices=polydef->vertexCount;
	shape.contour[0].vertex=(gpc_vertex*) malloc(shape.contour[0].num_vertices*sizeof(gpc_vertex));
	
	//Write vertices to shape
	while (scan<polydef->vertexCount){
		shape.contour[0].vertex[scan].x=polydef->vertices[scan].x;
		shape.contour[0].vertex[scan].y=polydef->vertices[scan].y;
		scan++;
	}
	
	if (add){
		//Add shape to shapes
		gpc_polygon_clip(GPC_UNION,&former,&shape,bodyshape->polygon);
	}
	else {
		//Remove shape from shapes
		gpc_polygon_clip(GPC_XOR,&former,&shape,bodyshape->polygon);
	}
	
	//Copy Polygon to Tristrip
	//gpc_polygon_to_tristrip(bodyshape->polygon,bodyshape->tristrip);
}
```
The last line, which is commented out, causes the crash when left in... I have used this before in different code, so I know that it can work... but I am clearly doing something wrong (unsuprising as I am new to GPC). So if you could tell me what I'm doing wrong?
I doubt you'll need knowledge of Box2D... just GPC.

---

