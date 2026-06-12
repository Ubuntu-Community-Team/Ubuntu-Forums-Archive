---
title: "[SOLVED] Rotation around Z axis doesn't work?"
date: 2008-06-25
forum: Programming Talk
---

### Post by paukku92 on 2008-06-25
I am doing 3d rotations in my program, and rotation around X and Y seem to work fine but rotating around Z axis makes the object malformed. Can anybody say whats wrong with the code:

```

//X rotation matrix
float Xrot[3][3]={{0,0,0},{0,0,0},{0,0,0}};

Xrot[0][0]=1;
Xrot[1][1]=coslookup(Angle.X);
Xrot[2][1]=-sinlookup(Angle.X);
Xrot[1][2]=sinlookup(Angle.X);
Xrot[2][2]=coslookup(Angle.X);

//Z rotation matrix
float Yrot[3][3]={{0,0,0},{0,0,0},{0,0,0}};

Yrot[0][0]=coslookup(Angle.Y);
Yrot[2][0]=sinlookup(Angle.Y);
Yrot[1][1]=1;
Yrot[0][2]=-sinlookup(Angle.Y);
Yrot[2][2]=coslookup(Angle.Y);

//Z rotation matrix
float Zrot[3][3]={{0,0,0},{0,0,0},{0,0,0}};

Zrot[0][0]=coslookup(Angle.Z);
Zrot[1][0]=-sinlookup(Angle.Z);
Zrot[0][1]=sinlookup(Angle.Z);
Zrot[1][1]=coslookup(Angle.Z);
Zrot[2][2]=1;

float rot[3][3]={{0,0,0},{0,0,0},{0,0,0}};
	
for(int y=0;y<3;y++)
{
	for(int x=0;x<3;x++)
	{
		rot[x][y]=Xrot[0][y]*Yrot[x][0]+Xrot[1][y]*Yrot[x][1]+Xrot[2][y]*Yrot[x][2];
	}
}

for(int y=0;y<3;y++)
{
	for(int x=0;x<3;x++)
	{
		rot[x][y]=rot[0][y]*Zrot[x][0]+rot[1][y]*Zrot[x][1]+rot[2][y]*Zrot[x][2];
	}
}

for (int i=0;i<ModelData.Vertexes.size();i++)
{		
	TransformedModelData.Vertexes.at(i).X=rot[0][0]*ModelData.Vertexes.at(i).X+rot[1][0]*ModelData.Vertexes.at(i).Y+rot[2][0]*ModelData.Vertexes.at(i).Z;
	TransformedModelData.Vertexes.at(i).Y=rot[0][1]*ModelData.Vertexes.at(i).X+rot[1][1]*ModelData.Vertexes.at(i).Y+rot[2][1]*ModelData.Vertexes.at(i).Z;
	TransformedModelData.Vertexes.at(i).Z=rot[0][2]*ModelData.Vertexes.at(i).X+rot[1][2]*ModelData.Vertexes.at(i).Y+rot[2][2]*ModelData.Vertexes.at(i).Z;
}
	
CalculateAABB();

```

I have checked the matrices many times, so I'm wondering what causes the malformation.

---

### Post by WW on 2008-06-25
This loop overwrites elements of rot but then uses them to compute later elements:
```

for(int y=0;y<3;y++)
{
	for(int x=0;x<3;x++)
	{
		rot[x][y]=rot[0][y]*Zrot[x][0]+rot[1][y]*Zrot[x][1]+rot[2][y]*Zrot[x][2];
	}
}

```
Instead, use another matrix, e.g.
```

float rot2[3][3]={{0,0,0},{0,0,0},{0,0,0}};

for(int y=0;y<3;y++)
{
	for(int x=0;x<3;x++)
	{
		rot2[x][y]=rot[0][y]*Zrot[x][0]+rot[1][y]*Zrot[x][1]+rot[2][y]*Zrot[x][2];
	}
}

for (int i=0;i<ModelData.Vertexes.size();i++)
{		
	TransformedModelData.Vertexes.at(i).X=rot2[0][0]*ModelData.Vertexes.at(i).X+rot2[1][0]*ModelData.Vertexes.at(i).Y+rot2[2][0]*ModelData.Vertexes.at(i).Z;
	TransformedModelData.Vertexes.at(i).Y=rot2[0][1]*ModelData.Vertexes.at(i).X+rot2[1][1]*ModelData.Vertexes.at(i).Y+rot2[2][1]*ModelData.Vertexes.at(i).Z;
	TransformedModelData.Vertexes.at(i).Z=rot2[0][2]*ModelData.Vertexes.at(i).X+rot2[1][2]*ModelData.Vertexes.at(i).Y+rot2[2][2]*ModelData.Vertexes.at(i).Z;
}
	
CalculateAABB();

```

---

### Post by paukku92 on 2008-06-25
Thanks a lot for the help. Now it seems to work.

---

