---
title: "HOWTO: Drawing Sprites Using SDL"
date: 2006-11-23
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-11-23
This is the fourth HOWTO in a series of HOWTOs about game development using Simple DirectMedia Layer.

This HOWTO covers the following subjects:

1) Rendering a games scene
2) Seeing in the dark or how color keying works
3) How to tell SDL which color to make transparent
4) Rendering the scene

1) Rendering a games scene

Rendering or 'Drawing' a scene in a game believe it or not works a lot like most image manipulation packages like GIMP or Photoshop. The reason this is true is that they both use a system of layers to create a composite image that is then displayed at the end of the process.

Usually in GIMP or Photoshop you start by creating a background layer which is usually white. Then if you want to change or add anything, you add an new layer on top and place new image data on it.

Thats exactly how 2d games generate their scenes! er... only lots of times every second. :-D

So whats the standard procedure for this I hear you cry!

- Draw your background
- Draw any scenery that goes behind your sprites
- Finally draw your sprites over the top 

2) Seeing in the dark or how color keying works

If you look closely at any 2d game you will find that most backgrounds are not ever in front of anything. That means that all other layers infront have to be drawn as if they were a transparent film over the top.

This technique is known as color keying. By that we mean that a specially selected color will be deliberately NOT drawn when we apply the different layers to our scene. If you download our example code and take a look at the image file 'sprite.bmp' you can see that our sprite is draw on a black background. If we draw this as is, you will get a nasty black rectangle over the top of our lovely hills and sky!. Granted, you would still see the little guy but it takes quite a bit of convincing that this is a rendered scene and not something you knocked up in windows paint!

3) How to tell SDL which color to make transparent

So how can we specify what color SDL can treat as transparent? Well, when we load an image we can add a little code to take care of this:
```

if( compatible_image != NULL ) {
	// specify a colour that will be used to signify 'transparent' pixels
	Uint32 colorkey = SDL_MapRGB( compatible_image->format, 0, 0, 0); // choose black
	// now tell SDL to remeber our choice
	SDL_SetColorKey( compatible_image, SDL_RLEACCEL | SDL_SRCCOLORKEY, colorkey);
	// SDL_RLEACCEL is run lenght encoded acceleration to speed up the colorkeying
	// SDL_SRCCOLORKEY tells SDL that this color key applies to the source image
}

```

In the SDL_MapRGB function we can tell SDL three numbers that form a color with Red, Green and Blue parts. Hence black, which is no color at all really, is red=0,green=0 and blue=0.

The other two SDL_RLEACCEL and SDL_SRCCOLORKEY specify how the images will be drawn. Its a bit outside the scope of this HOWTO to go into details of RLE but a good five minutes on Google typing in run length encoding will get you a good explanation if you really want one. Its basically that the image surface gets optimized so that the whole color keying process gets done faster. 

4) Rendering the scene

So now we've told SDL our special color, we can now begin layering/rendering our scene. 

You will notice at this point that I've added a separate SDL_Rect for each surface as the places they will be drawn. I could have used only one but that would mean I would need to change the x,y every time we redraw the scene. This will become a problem when we start doing animation in a later HOWTO so we might as well start making life easier for ourselves now.
```

// display rectangles for sprite
SDL_Rect background_position;
SDL_Rect Sprite_position;
SDL_Rect Sprite_source;

```

I've also taken the liberty of re-arranging the code into another function to Initialize everything and another which shut everything down again. This is a good way of setting up you code to be more readable and manageable too.

So finally we do the following:

- Draw the background
- Draw the sprite over the top using our color key technique
- Update the screen 

Other thoughts

In the end most games usually turn into the following:
```

int main( int argc, char* argv[] )
{
	Init();
	while(!done)	{
		ProcessInputs();
		ReactToInputs();
		ReactToGameRules();
		DrawTheScene();
	}	
	Shutdown();
}

```

This is the basic skeleton, except for error checking of course. Any differences in anyone else's code usually comes down to special reasons or personal choice.

Conclusion

You can compile this example by typing the following in the terminal:
```

g++ -o colorkey colorkey.cpp -lSDL -lSDL_image

```

Well thats it for this HOWTO except to say that if you have any comments or HOWTOs of your own please feel free to contribute.

Mike

---

### Post by KIAaze on 2008-03-29
Google just led me to your howto while I was trying to solve the white background problem for iteam. ^^
Ok, so now I know what colorkeying is, but it seems we are not using it in iteam.

The SDL_SRCALPHA flag seems to be set. So how can I blit correctly from an SDL_Surface loaded from a .png to an SDL_Surface created with SDL_CreateRGBSurface?
The idea being to blit to a bigger surface that is power of 2. ;)

P.S:
Current code in iteam:
```
	//resizes to a power of 2 texture by blitting the surface to another surface with a power of 2 size
	//WARNING: It frees the image surface!!!
	//TODO: Make background transparent
	SDL_Surface* resize2 ( SDL_Surface* image, int texSize )
	{
		/* Create a 32-bit surface with the bytes of each pixel in R,G,B,A order,
		as expected by OpenGL for textures */
		SDL_Surface *ret;
		Uint32 rmask, gmask, bmask, amask;

		/* SDL interprets each pixel as a 32-bit number, so our masks must depend
		on the endianness (byte order) of the machine */
#if SDL_BYTEORDER == SDL_BIG_ENDIAN
		rmask = 0xff000000;
		gmask = 0x00ff0000;
		bmask = 0x0000ff00;
		amask = 0x000000ff;
#else
		rmask = 0x000000ff;
		gmask = 0x0000ff00;
		bmask = 0x00ff0000;
		amask = 0xff000000;
#endif

		int new_h=wanted_size ( texSize,image->h );
		int new_w=wanted_size ( texSize,image->w );

		if ( new_h!=image->h || new_w!=image->w )
		{
			printf ( "[resize2] <WARNING> Texture size is not a power of 2 or greater than the maximum allowed by the video card (%ix%i). Resizing to (%dx%d)\n",texSize,texSize,new_w,new_h );

			SDL_Surface* temp = SDL_CreateRGBSurface ( image->flags, new_w, new_h, 32, rmask, gmask, bmask, amask );

//			SDL_FillRect ( temp,NULL,SDL_MapRGBA ( temp->format, 255,255,255,255 ) );

			//Convert the surface to the appropriate display format
			ret = SDL_DisplayFormatAlpha ( temp );


//	ret = SDL_DisplayFormat(temp);
			SDL_FreeSurface ( temp );

SDL_Rect rect;
rect.x=0;
rect.y=0;
rect.w=image->w;
rect.h=image->h;
//br_blit(image,rect,ret);
//  SDL_SetAlpha  (ret, image->flags | !SDL_SRCALPHA, 255);
  printf("image->flags & SDL_SRCALPHA=%8x\n",image->flags & SDL_SRCALPHA); 
  printf("image->flags & SDL_SRCCOLORKEY=%8x\n",image->flags & SDL_SRCCOLORKEY); 
  printf("ret->flags & SDL_SRCALPHA=%8x\n",ret->flags & SDL_SRCALPHA); 
  printf("ret->flags & SDL_SRCCOLORKEY=%8x\n",ret->flags & SDL_SRCCOLORKEY); 
  printf("SDL_SRCCOLORKEY & SDL_SRCALPHA=%8x\n",SDL_SRCCOLORKEY & SDL_SRCALPHA); 
exit(47);

			SDL_BlitSurface ( image, NULL, ret, NULL );


			printf ( "[resize2] texture resized to (%dx%d)\n",ret->w,ret->h );
			if ( new_w!=ret->w || new_h!=ret->h )
			{
				printf ( "FATAL ERROR: incorrect resizing\n" );
				exit ( 245 );
			};
			SDL_FreeSurface ( image );//free the old image since we probably won't need it anymore
			SDL_SaveBMP ( ret,"ret.bmp" );
			//exit(96);
			return ( ret );
		}
		else return ( image );
	}

void br_blit(SDL_Surface* src, SDL_Rect sr, SDL_Surface* dst)
{
  // always copies to 0, 0 of the dest

  int numPixelsOnLine = sr.w;
  int bytesToMove = numPixelsOnLine * 4;
  unsigned char* srcPixels = static_cast<unsigned char*>(src->pixels);
  unsigned char* dstPixels = static_cast<unsigned char*>(dst->pixels);

  for (int y=0; y<sr.h; y++)
  {
    unsigned char* destP = &dstPixels[y*bytesToMove];
    unsigned char* srcP = &srcPixels[((sr.y+y)*src->w*4)+sr.x*4];
    memcpy(destP, srcP, bytesToMove);
  }
}
```

edit: solved by using br_blit with the correct rectangle size (ret.h and ret.w). ;)
Committed revision 226.

---

### Post by Mickeysofine1972 on 2008-04-01
> **KIAaze said:**
> Google just led me to your howto while I was trying to solve the white background problem for iteam. ^^
Ok, so now I know what colorkeying is, but it seems we are not using it in iteam.

The SDL_SRCALPHA flag seems to be set. So how can I blit correctly from an SDL_Surface loaded from a .png to an SDL_Surface created with SDL_CreateRGBSurface?
The idea being to blit to a bigger surface that is power of 2. ;)

P.S:
Current code in iteam:
```
	//resizes to a power of 2 texture by blitting the surface to another surface with a power of 2 size
	//WARNING: It frees the image surface!!!
	//TODO: Make background transparent
	SDL_Surface* resize2 ( SDL_Surface* image, int texSize )
	{
		/* Create a 32-bit surface with the bytes of each pixel in R,G,B,A order,
		as expected by OpenGL for textures */
		SDL_Surface *ret;
		Uint32 rmask, gmask, bmask, amask;

		/* SDL interprets each pixel as a 32-bit number, so our masks must depend
		on the endianness (byte order) of the machine */
#if SDL_BYTEORDER == SDL_BIG_ENDIAN
		rmask = 0xff000000;
		gmask = 0x00ff0000;
		bmask = 0x0000ff00;
		amask = 0x000000ff;
#else
		rmask = 0x000000ff;
		gmask = 0x0000ff00;
		bmask = 0x00ff0000;
		amask = 0xff000000;
#endif

		int new_h=wanted_size ( texSize,image->h );
		int new_w=wanted_size ( texSize,image->w );

		if ( new_h!=image->h || new_w!=image->w )
		{
			printf ( "[resize2] <WARNING> Texture size is not a power of 2 or greater than the maximum allowed by the video card (%ix%i). Resizing to (%dx%d)\n",texSize,texSize,new_w,new_h );

			SDL_Surface* temp = SDL_CreateRGBSurface ( image->flags, new_w, new_h, 32, rmask, gmask, bmask, amask );

//			SDL_FillRect ( temp,NULL,SDL_MapRGBA ( temp->format, 255,255,255,255 ) );

			//Convert the surface to the appropriate display format
			ret = SDL_DisplayFormatAlpha ( temp );


//	ret = SDL_DisplayFormat(temp);
			SDL_FreeSurface ( temp );

SDL_Rect rect;
rect.x=0;
rect.y=0;
rect.w=image->w;
rect.h=image->h;
//br_blit(image,rect,ret);
//  SDL_SetAlpha  (ret, image->flags | !SDL_SRCALPHA, 255);
  printf("image->flags & SDL_SRCALPHA=%8x\n",image->flags & SDL_SRCALPHA); 
  printf("image->flags & SDL_SRCCOLORKEY=%8x\n",image->flags & SDL_SRCCOLORKEY); 
  printf("ret->flags & SDL_SRCALPHA=%8x\n",ret->flags & SDL_SRCALPHA); 
  printf("ret->flags & SDL_SRCCOLORKEY=%8x\n",ret->flags & SDL_SRCCOLORKEY); 
  printf("SDL_SRCCOLORKEY & SDL_SRCALPHA=%8x\n",SDL_SRCCOLORKEY & SDL_SRCALPHA); 
exit(47);

			SDL_BlitSurface ( image, NULL, ret, NULL );


			printf ( "[resize2] texture resized to (%dx%d)\n",ret->w,ret->h );
			if ( new_w!=ret->w || new_h!=ret->h )
			{
				printf ( "FATAL ERROR: incorrect resizing\n" );
				exit ( 245 );
			};
			SDL_FreeSurface ( image );//free the old image since we probably won't need it anymore
			SDL_SaveBMP ( ret,"ret.bmp" );
			//exit(96);
			return ( ret );
		}
		else return ( image );
	}

void br_blit(SDL_Surface* src, SDL_Rect sr, SDL_Surface* dst)
{
  // always copies to 0, 0 of the dest

  int numPixelsOnLine = sr.w;
  int bytesToMove = numPixelsOnLine * 4;
  unsigned char* srcPixels = static_cast<unsigned char*>(src->pixels);
  unsigned char* dstPixels = static_cast<unsigned char*>(dst->pixels);

  for (int y=0; y<sr.h; y++)
  {
    unsigned char* destP = &dstPixels[y*bytesToMove];
    unsigned char* srcP = &srcPixels[((sr.y+y)*src->w*4)+sr.x*4];
    memcpy(destP, srcP, bytesToMove);
  }
}
```

edit: solved by using br_blit with the correct rectangle size (ret.h and ret.w). ;)
Committed revision 226.

Hey KIAAZE

Well you can read the original article here along with source code: 

[http://ubuntu-gamedev.wikispaces.com/Drawing+Sprites+Using+SDL](http://ubuntu-gamedev.wikispaces.com/Drawing+Sprites+Using+SDL)

Also, if you checkout my branch of iteam you can look at how the terrain destroying code draws a halo thats another good way of blitting to the new ^2 texture.

Actually, its been a while since we spoke and I had forgotten to mention that I have been rewriting my gp2d code heavily, so heavily infact that it isn't even gp2d anymore lol.

I have anothe game in the offing and its been distracting me alot but I promise I will return to iteam as soon as I get my net connection back at home in a few weeks

Mike

---

### Post by KIAaze on 2008-04-01
Be careful about the too heavily. There's already a rewrite being done in gp2d-new and I've done quite a few changes to gp2d/trunk myself. This will make 3 GP2D versions to merge one day!!!

Also, maybe you should be the one merging your classes into trunk. I started doing it, but I haven't been able to really make them work yet (not even in your branch :/ ).

P.S: And I'm not sure if we need a WeaponsList class... What more than a vector/map can it do? O.o

---

### Post by Mickeysofine1972 on 2008-04-01
> **KIAaze said:**
> Be careful about the too heavily. There's already a rewrite being done in gp2d-new and I've done quite a few changes to gp2d/trunk myself. This will make 3 GP2D versions to merge one day!!!

Also, maybe you should be the one merging your classes into trunk. I started doing it, but I haven't been able to really make them work yet (not even in your branch :/ ).

P.S: And I'm not sure if we need a WeaponsList class... What more than a vector/map can it do? O.o

actually I've started using a normal pointer array for that sort of thing now as I dont really trust vector much and this seems to lead to more stable memory management

I think I'm probably going to make the new base code into a different game libarary anyway as it is more geared toward 3d stuff at the moment. I can show anyone yet though as I dont have a svn set up on sf.net yet.

Mike

---

