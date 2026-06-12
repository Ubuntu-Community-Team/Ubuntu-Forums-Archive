---
title: "Accessing C++ STL Vector Element n: different when accessed at different times"
date: 2009-07-14
forum: Programming Talk
---

### Post by ncosens on 2009-07-14
[SIZE="3"]**Some Background:**[/SIZE]

A couple of friends and I started developing a game a few weeks ago.  I am the only programmer.  I'm using SDL with OpenGL for 3D.  I load mesh data from Wavefront .obj files for simplicity.  I call a function to render each face individually.


[PHP]
void oEntity::RenderFace(oFace& face, oMaterial& mat, GLenum mode)
{
	oVertice gvert;    // holds X, Y, Z geometric coordinates
	oUVcoord tvert;    // holds U, V texture coordinates
	oNormal nvert;     // holds X, Y, Z normal coordinates

	GLfloat Ambient[] = {
			mat.AmbientColor.R,
			mat.AmbientColor.G,
			mat.AmbientColor.B,
			1.0f
	};

	GLfloat Diffuse[] = {
			mat.DiffuseColor.R,
			mat.DiffuseColor.G,
			mat.DiffuseColor.B,
			1.0f
	};

	GLfloat Specular[] = {
			mat.SpecularColor.R,
			mat.SpecularColor.G,
			mat.SpecularColor.B,
			0.3f
	};

	glBegin(mode);

	glMaterialfv(GL_FRONT, GL_AMBIENT, Ambient);
	glMaterialfv(GL_FRONT, GL_DIFFUSE, Diffuse);
	glMaterialfv(GL_FRONT, GL_SPECULAR, Specular);
	glMaterialf(GL_FRONT, GL_SHININESS, mat.Shininess);
	glColor4f(0.5f, 0.5f, 0.5f, mat.Alpha);

	unsigned int temp = 0;   // for debugging purposes

	for (unsigned int fvIndex = 0; fvIndex < face.GeoVerts.size(); fvIndex++)
	{
		temp = face.GeoVerts[fvIndex];
		gvert = obj.TheMesh.GetVertice(face.GeoVerts[fvIndex] - 1);

		temp = face.UV_Verts[fvIndex];
		tvert = obj.TheMesh.GetUVcoord(face.UV_Verts[fvIndex] - 1);

		temp = face.NrmVerts[fvIndex];
		nvert = obj.TheMesh.GetNormal(face.NrmVerts[fvIndex] - 1);

		glNormal3f(nvert.X, nvert.Y, nvert.Z);
		glTexCoord2f(tvert.U, tvert.V);
		glVertex3f(scale * gvert.X, scale * gvert.Y, scale * gvert.Z);
	}

	glEnd();
}
[/PHP]


This works great...  provided you only have a relatively small number of faces.  So I had to optimize my rendering.  Which lead me to learn about vertex arrays.  And I came up with this vertex array builder:


[PHP]
bool oEntity::OnLoad(std::string FileName)
{
	if (!obj.OnLoad(FileName))
	{
		return false;
	}

	unsigned int flsize = obj.TheMesh.GetFaceListSize();

	obj.TheMesh.VertListPointer = new oVertice[flsize];    // oVertice*
	obj.TheMesh.UVlistPointer = new oUVcoord[flsize];      // oUVcoord*
	obj.TheMesh.NormListPointer = new oNormal[flsize];     // oNormal*

	oFace face = obj.TheMesh.GetFace(0);
	oVertice gvert;
	oUVcoord tvert;
	oNormal nvert;
	unsigned int counter = 0;    // vertex array index
	unsigned int temp = 0;       // for debugging purposes

	for (unsigned int flIndex = 0; flIndex < obj.TheMesh.GetFaceListSize(); flIndex++)
	{
		face = obj.TheMesh.GetFace(flIndex);

		for (unsigned int fvIndex = 0; fvIndex < face.GeoVerts.size(); fvIndex++)
		{
			temp = face.GeoVerts[fvIndex];
			gvert = obj.TheMesh.GetVertice(face.GeoVerts[fvIndex] - 1);

			temp = face.UV_Verts[fvIndex];                      // problem occurs here
			tvert = obj.TheMesh.GetUVcoord(face.UV_Verts[fvIndex] - 1);    // and here

			temp = face.NrmVerts[fvIndex];
			nvert = obj.TheMesh.GetNormal(face.NrmVerts[fvIndex] - 1);

			obj.TheMesh.VertListPointer[counter].X = gvert.X;
			obj.TheMesh.VertListPointer[counter].Y = gvert.Y;
			obj.TheMesh.VertListPointer[counter].Z = gvert.Z;

			obj.TheMesh.UVlistPointer[counter].U = tvert.U;
			obj.TheMesh.UVlistPointer[counter].V = tvert.V;

			obj.TheMesh.NormListPointer[counter].X = nvert.X;
			obj.TheMesh.NormListPointer[counter].Y = nvert.Y;
			obj.TheMesh.NormListPointer[counter].Z = nvert.Z;

			counter++;
		}
	}

	return true;
}
[/PHP]


As you can see it's essentially the same routine for accessing the mesh data as the RenderFace() function.  Only I'm storing the data into an array instead of sending it to a gl function.


[SIZE="3"]**The Problem:**[/SIZE]

I'm loading a cube made of triangles.  So that makes 12 faces.  And each face has 3 int vectors for storing indexes to the location of the actual mesh data.  All seams to go well when reading data from my vectors until I reach element 16 (0 indexed).  Element 16 is the second vertex/texcoord/normal in the sixth face (triangle).  The problem is that when it accesses the information from the RenderFace() function it returns the correct index of 12.  But when when it access that SAME information from the OnLoad() function it returns 3045472188.  Which doesn't exist.  I posted this question to StackOverflow and someone mentioned that the issue may be from not initializing the vertex arrays to sufficient size.


[PHP]
obj.TheMesh.VertListPointer = new oVertice[flsize];
obj.TheMesh.UVlistPointer = new oUVcoord[flsize];
obj.TheMesh.NormListPointer = new oNormal[flsize];
[/PHP]


After applying this workaround:


[PHP]
obj.TheMesh.VertListPointer = new oVertice[flsize * 3];    // x, y, z
obj.TheMesh.UVlistPointer = new oUVcoord[flsize * 2];      // u, v
obj.TheMesh.NormListPointer = new oNormal[flsize * 3];     // x, y, z
[/PHP]


it works.  Though the meshes don't render correctly.  But that's just an organization issues.  Unless for some reason random faces don't get rendered.


[SIZE="3"]**The Discussion:**[/SIZE]

OK.  Obviously I've come across a way to get the data from vectors to arrays.  But the solution had nothing to do with accessing the information already in a vector.  Unless I'm mistaken.  For the sake of argument let's take for example the cube issue again.  The cube has 12 faces (triangles) defining it.  So when I call


[PHP]unsigned int flsize = obj.TheMesh.GetFaceListSize(); [/PHP]


flsize is set to the value of 12.  I then initialize (perhaps wrong term) each vertex array with a size of 12.  Logic tells me (again I may be wrong) that since each array is of a certain class type (i.e. oVertice) each element in the array will get initialized with enough storage for each member in the class (i.e. oVertice has 3 floats).  The workaround implies that this is not the case.  And so I have to make that room manually.  For this example let's say I didn't.  So I have room for 12 somethings.  Let's say that each something is a float.  Alright so I now have an array with room for 12 floats.  While iterating through my array building loop, it should SEGFAULT after the 4th iteration, but it doesn't and allows me to continue until I reach the 17th iteration.  This is where I access element 16 (actually the 17th value) in the UV_List int vector.  And it returns an index that is way out of range.

So this is what confuses me.

[LIST=1]
[*]How on earth does it jumble the value in the nth element of a vector?
[*]And if the vertex arrays are too small, how would it allow me to get so far?
[*]Why doesn't C++ automatically allocate enough memory based on the class type of the array?
[/LIST]


You are now free to walk about the cabin...   um I mean discuss at will.

---

