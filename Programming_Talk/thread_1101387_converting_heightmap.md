---
title: "converting heightmap"
date: 2009-03-20
forum: Programming Talk
---

### Post by tneva82 on 2009-03-20
Another day, another question it seems. Anyway I'm trying to get heightmaps working and to test them I need some heightmaps. So I figured converter should be easy enough to do. However either I'm screwing up with setting palette(custom palete, trying to get the 256 colours all be different. I try to create one big block there of second lowest index(1) amidst lowest level.With multiplier of 0.3(value in the heightmap*0,3 should therefore give me the height) I still get oddly high blocks. 10+ infact(and in openGL that's pretty darned high). And for added fun when I tried adding second block where I used what's supposed to be highest index gives me only about twice as long block. What the? Should be more like 200 times higher!

So somewhere I'm not getting it right. Is the error in how I set up palet in the paint program or in how I convert BMP to RAW file? Code below.

```
int main(int argc, char **argv) {
  char *input=new char[256];
  char *output=new char[256];

  strcpy(input, argv[1]);
  strcpy(output, argv[1]);

  strcat(input, ".bmp");
  strcat(output, ".raw");

  FILE *pFile=fopen(output, "wb");
   

  SDL_Surface *TextureImage; 

 
  if (( TextureImage = SDL_LoadBMP(input) )) {
    char *pixels=(char*)TextureImage->pixels;
    for(int i=0;i<TextureImage->w*TextureImage->h;i++) {
      fputc(pixels[i], pFile);
    }
	    
  } 

  // Free up any memory we may have used 
  if (TextureImage) {       
      SDL_FreeSurface(TextureImage);
  }
  fclose(pFile);
  delete[] input;
  delete[] output;

}
```

---

### Post by eye208 on 2009-03-20
You forgot to call SDL_LockSurface and evaluate the SDL_PixelFormat of the surface.

---

### Post by tneva82 on 2009-03-20
And what use pixelformat info does precicely? I know it's 256 colour picture and I'm not interested at specific colour RGB values, just the index number. I'll see if the lock surface helps but from SDL docs didn't see one thing from pixel format that actually has any relevance to issue. I know precicely the format anyway(and no need for error checking since this is just for private use. I don't use it to non-256 colour pictures).

Edit: Locksurface did squat. Still same issues.

---

### Post by Gordon Bennett on 2009-03-20
Are you using colour-indexed texturemaps?  In some OpenGL implementations, the behaviour of using such textures in certain contexts is 'undefined' :P

---

### Post by tneva82 on 2009-03-20
> **Gordon Bennett said:**
> Are you using colour-indexed texturemaps?  In some OpenGL implementations, the behaviour of using such textures in certain contexts is 'undefined' :P

I'm simply loading up BMP to SDL surface, convert pixels from there to char array and reading up value for certain X/Y co-ordinates to get(supposedly) value between 0-255 which I then multiply with height multiplier(this idea I borrowed elsewhere. They used 1.8, I have to use 0.3 just to get "just" 10.xxx height. Can't seem to get colours working properly. It's as if the colours would get random index value :-|

---

