---
title: "Load a PNG with libpng12"
date: 2012-12-01
forum: Programming Talk
---

### Post by bird1500 on 2012-12-01
Hi,
I'm using libpng12(-dev) to load PNG files but something's wrong when I display them (see screenshot).
Can anyone please spot the problem?

[PHP]
void*
Manager::loadImagePng(const char *path, float &w, float &h,
int &format, int &rowStride) {
    
    char header[8];
    
    FILE *fp = fopen(path, "rb");
    if (!fp) {
        Print("File %s could not be opened for reading");
        return NULL;
    }
    size_t numBytes = fread(header, 1, sizeof(png_bytep), fp);
    
    if(numBytes != sizeof(png_bytep)) {
        fclose(fp);
        Print("Read too few bytes");
        return NULL;
    }
    
    if (png_sig_cmp((png_bytep)header, 0, 8)) {
        Print("File is not recognized as a PNG file");
        return NULL;
    }
    
    png_structp png_ptr = png_create_read_struct(
    PNG_LIBPNG_VER_STRING, NULL, NULL, NULL);
    
    if (!png_ptr) {
        Print("png_create_read_struct failed");
        return NULL;
    }
    
    png_infop info_ptr = png_create_info_struct(png_ptr);
    if (!info_ptr) {
        Print("png_create_info_struct failed");
        return NULL;
    }
    
    if (setjmp(png_jmpbuf(png_ptr))) {
        Print("Error during init_io");
        return NULL;
    }
    
    png_init_io(png_ptr, fp);
    png_set_sig_bytes(png_ptr, 8);
    png_read_info(png_ptr, info_ptr);
    
    int width = png_get_image_width(png_ptr, info_ptr);
    w = width;
    int height = png_get_image_height(png_ptr, info_ptr);
    h = height;
    png_byte color_type = png_get_color_type(png_ptr, info_ptr);
    if(color_type == PNG_COLOR_TYPE_RGB) {
        format = GL_RGB;
    } else if(color_type == PNG_COLOR_TYPE_RGBA) {
        format = GL_RGBA;
    } else {
        Print("Unknown png format");
        return NULL;
    }
    
    png_read_update_info(png_ptr, info_ptr);
    
    /*
    png_uint_32 channels = png_get_channels(png_ptr, info_ptr);
    png_uint_32 bitdepth = png_get_bit_depth(png_ptr, info_ptr);
    rowStride = width * bitdepth * channels / 8;
    */
    rowStride = png_get_rowbytes(png_ptr,info_ptr);
    
    if (setjmp(png_jmpbuf(png_ptr))) {
        Print("[read_png_file] Error during read_image");
    }
    
    png_bytep *row_pointers = (png_bytep*) malloc(sizeof(png_bytep) * height);
    for(int y=0; y<height; y++) {
        row_pointers[y] = (png_byte*) malloc(rowStride);
    }
    
    png_read_image(png_ptr, row_pointers);
    fclose(fp);
    return row_pointers;
}
[/PHP]The function returns the raw pixels of type void* which are sent to glTexture2D() along with the params width, height, stride, format.

I use a similar function for jpeg files using libjpeg and that one works fine.

The original PNG file [is here]("http://fwallpapers.com/files/images/beautiful-nature-china.png?iact=hc&vpx=677&vpy=216&dur=427&hovh=139&hovw=239&tx=151&ty=60&sig=103454256490900199261&ei=JNO5UPAnqJrRBZqfgKgD&page=1&tbnh=137&tbnw=234&start=0&ndsp=43&ved=1t:429,r:3,s:0,i:164").

---

### Post by Lux Perpetua on 2012-12-01
Are you sure the error isn't in the code that displays the image?

---

### Post by bird1500 on 2012-12-01
I'm pretty sure this function's got an issue, though I might be wrong.

The generic function Manager::loadImage(path,...) calls either Manager::loadImageJpg(...) or Manager::loadImagePng(...) depending on the file extension of "path". Loading JPG works fine, PNG - doesn't, that's why I guess something's wrong with this particular function.

Source code of the little project attached.

EDIT: **the rowStride is correct** (loading the PNG with Gdk::Pixbuf reports same rowStride), something else is wrong.

---

### Post by Lux Perpetua on 2012-12-01
```
GLuint
Manager::loadTexture(const char *path, float &w, float &h) {
	
	int format,rowStride;
	
	void *buf = loadImage(path, w, h, format, rowStride);
	if(buf == NULL) {
		return 0;
	}
	
	GLuint texId;
	glGenTextures(1, &texId);
	glBindTexture(GL_TEXTURE_2D, texId);
	glPixelStorei(GL_UNPACK_ALIGNMENT, rowStride);

	[color=red]glTexImage2D(GL_TEXTURE_2D, 0, format, w, h, 0, format,
	GL_UNSIGNED_BYTE, buf);[/color]
	free(buf);

	glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_NEAREST);
	glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_NEAREST);
	glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_CLAMP_TO_EDGE);
	glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_CLAMP_TO_EDGE);

	return texId;
}
```I'm pretty sure the highlighted call is incorrect: for the `buf' argument, you're passing a pointer to an array of pointers to the rows of the image.  What the function expects is a pointer to a the pixel data itself, not a pointer to a bunch of pointers to the data. (See: [http://www.opengl.org/sdk/docs/man/xhtml/glTexImage2D.xml](http://www.opengl.org/sdk/docs/man/xhtml/glTexImage2D.xml))  JPEGs work because the return value of Manager::loadImageJpg is a pointer to the pixel data, unlike Manager::loadImagePng.

**Edit:** Well, I guess the bigger problem is not the call to glTexImage2D, but the fact that the "true" type of the return value of Manager::loadImage depends on the type of the image (essentially char * for JPEG and char ** for PNG). Since the return value has type void *, the compiler is not able to catch this.

---

### Post by bird1500 on 2012-12-01
Thanks, I've noticed that too before, and I replaced:
[PHP]
png_bytep *buf = (png_bytep*) malloc(sizeof(png_bytep) * height);
    for(int y=0; y<height; y++) {
        buf[y] = (png_byte*) malloc(rowStride);
    }
[/PHP]with
[PHP]
unsigned char *buf = (unsigned char*) malloc(int(h) * rowStride);
[/PHP]followed by
png_read_image(png_ptr, (png_bytep *)buf);

However, that doesn't solve the issue, only makes it worse since libpng apparently can't work with that char*/void* type properly.
I'm reading a [tutorial]("http://www.piko3d.com/tutorials/libpng-tutorial-loading-png-files-from-streams") hoping to find out **how to load a PNG file and get raw void* pixels** out of it, not arrays of png_bytep* or other types.

---

### Post by Lux Perpetua on 2012-12-01
> **bird1500 said:**
> However, that doesn't solve the issue, only makes it worse since libpng apparently can't work with that char*/void* type properly.Obviously!  This is the same problem I highlighted above, just the other side of the coin.  You can't expect to give a function data in a format other than the extremely specific format it requires and have it do anything sensible.  

You can use something like this: ```
    png_byte *buf = malloc(h * rowStride);
    png_bytep *row_pointers = malloc(h * sizeof(png_bytep));

    /* I don't remember if libpng reads rows top-to-bottom or
     * bottom-to-top, so you may need to reverse the order of
     * the elements of row_pointers by modifying the loop below.
     */

    for (int k = 0; k < h; ++k) {
        row_pointers[k] = buf + rowStride*k;
    }

    png_read_image(read_ptr, row_pointers);

    free(row_pointers);
    return buf;
```

---

### Post by bird1500 on 2012-12-01
Thanks a lot, your solution works fine (with a few casts as below).
However I'll try to find a solution to avoid an extra buffer allocation.

[PHP]
    png_byte *buf = (png_byte *) malloc(h * rowStride);
    png_bytep *row_pointers = (png_bytep *)malloc(h * sizeof(png_bytep));
...
[/PHP]

EDIT: Actually, after I read that tutorial, looks like you did it right, row_pointers
is just an array to each row in the image as mandated by libpng, it's not a whole image
buffer.

---

