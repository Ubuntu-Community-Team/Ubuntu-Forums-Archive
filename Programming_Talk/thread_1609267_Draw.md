---
title: "Draw"
date: 2010-10-30
forum: Programming Talk
---

### Post by matmatmat on 2010-10-30
Hi, I'm trying to render a texture that is not a power of 2 (eg 512, 1026 etc) with OpenTK, a C# OOP wrapper for OpenGL. But it only shows the top corner of the image.
```

		public void LoadTexture(string filename)
		{
		    if (String.IsNullOrEmpty(filename))
		        throw new ArgumentException(filename);
		 
		    int id = GL.GenTexture();
		    GL.BindTexture(TextureTarget.Texture2D, id);
		 
		    Bitmap bmp = new Bitmap(filename);
			width = bmp.Width;
			height = bmp.Height;
			int w2 = (int)PowerOf2(width);
			int h2 = (int)PowerOf2(height);
			Bitmap bmp2 = new Bitmap(w2, h2);
			Graphics gfx = Graphics.FromImage(bmp2);
			gfx.DrawImage(bmp, new Point(0,0));		
			width_ratio = width/w2;
			height_ratio = 1 - height/h2;
			bmp2.Save("save.bmp");
		    BitmapData bmp_data = bmp2.LockBits(new Rectangle(0, 0, bmp.Width, bmp.Height), ImageLockMode.ReadOnly, System.Drawing.Imaging.PixelFormat.Format32bppArgb);
		    GL.TexImage2D(TextureTarget.Texture2D, 0, PixelInternalFormat.Rgba, bmp_data.Width, bmp_data.Height, 0,
		        OpenTK.Graphics.OpenGL.PixelFormat.Bgra, PixelType.UnsignedByte, bmp_data.Scan0);
		 
		    bmp2.UnlockBits(bmp_data);
		 
		    // We haven't uploaded mipmaps, so disable mipmapping (otherwise the texture will not appear).
		    // On newer video cards, we can use GL.GenerateMipmaps() or GL.Ext.GenerateMipmaps() to create
		    // mipmaps automatically. In that case, use TextureMinFilter.LinearMipmapLinear to enable them.
		    GL.TexParameter(TextureTarget.Texture2D, TextureParameterName.TextureMinFilter, (int)TextureMinFilter.Linear);
		    GL.TexParameter(TextureTarget.Texture2D, TextureParameterName.TextureMagFilter, (int)TextureMagFilter.Linear);
		 
		    tex = id;
		}
 //render

			GL.BindTexture(TextureTarget.Texture2D, tex.tex);
				GL.Begin (BeginMode.Quads);
//					GL.TexCoord2(0,1); GL.Vertex3 (x, y, z);
//					GL.TexCoord2(1,1); GL.Vertex3 (x+width, y, z);
//		            GL.TexCoord2(1,0); GL.Vertex3 (x+width, y+height, z);
//					GL.TexCoord2(0,0); GL.Vertex3 (x, y+height, z);
					GL.TexCoord2(0,1); GL.Vertex2 (x, y+tex.height);		
					GL.TexCoord2(tex.width_ratio,1); GL.Vertex2 (x+tex.width, y+tex.height);
		            GL.TexCoord2(tex.width_ratio,tex.height_ratio);  GL.Vertex2 (x+tex.width, y);
					GL.TexCoord2(0,tex.height_ratio); GL.Vertex2 (x, y);	
				GL.End ();

```

This is what it looks like on my screen: 
[IMG]http://imagebin.ca/img/BWNFD9f.png[/IMG]
and what the picture should be:
[IMG]http://imagebin.ca/img/t2sIZSj.png[/IMG]

---

### Post by matmatmat on 2010-10-30
oops: thread title isn't right

---

