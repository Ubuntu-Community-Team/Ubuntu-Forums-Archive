---
title: "program to manipulate Raw RGB file in linux"
date: 2006-02-26
forum: Programming Talk
---

### Post by dannyngweekiat_85 on 2006-02-26
Having involved in a project that capture image from digicam to process in pc. Anyone here know wat can i use for it?. Have to start a project in c... also how do we rebuild pixel image from data using C?

---

### Post by stoffe on 2006-02-26
There's probably several available libs for something like that, but if you don't find any specialized ones, Imagemagick is sure to be able to do anything you want. It has command line tools as well as bindings for numerous languages. Check it out.

---

### Post by dannyngweekiat_85 on 2006-02-27
thx for it trying to read through the file at imagemagick...thx

---

### Post by hod139 on 2006-02-27
I would suggest to also look at SDL and [Coriander]("http://damien.douxchamps.net/ieee1394/coriander/index.php") .  Here is some code I actually had laying around that uses SDL to display raw RGB data.

```

#include <SDL/SDL.h>

#define checkImageWidth 256
#define checkImageHeight 256
char checkImage[checkImageHeight][checkImageWidth][3];

/**
* Classic checkerboard texture from openGL red book
*/
void makeCheckImage(void)
{
    int i, j, c;
   
    for (i = 0; i < checkImageHeight; i++) {
        for (j = 0; j < checkImageWidth; j++) {    //start from lower-left corner
            c = ((((i&0x10)==0)^((j&0x10))==0))*255; //0 or 255 --> black or white
            checkImage[i][j][0] = (char) c;    //red component
            checkImage[i][j][1] = (char) c;    //green component
            checkImage[i][j][2] = (char) c;    //blue  component
        }
    }
}

/**
 * Simple SDL program that displays a raw handcrafted RGB image
 */
int main(int argc, char *argv[])
{    
    SDL_Surface *screen;    //This pointer will reference the drawing screen
    SDL_Surface *image;    //This pointer will reference our bitmap sprite
    SDL_Surface *temp;    //This pointer will temporarily reference the data (checker board)
    SDL_Rect dest;            //The destination region of our blit
    
    //We must first initialize the SDL video component, and check for success
    if (SDL_Init(SDL_INIT_VIDEO) != 0) {
        printf("Unable to initialize SDL: %s\n", SDL_GetError());
        return 1;
    }
    
    //When this program exits, SDL_Quit must be called
    atexit(SDL_Quit);
    
    //Set the video mode to 640x480 with 16bit colour
    screen = SDL_SetVideoMode(640, 480, 24, SDL_ANYFORMAT);
    if (screen == NULL) {
        printf("Unable to set video mode: %s\n", SDL_GetError());
        return 1;
    }    
    
    // Color information for the palette
    SDL_Color colors[256];
    unsigned int i;
        // Fill colors with color information 
        for(i=0;i<256;i++){
          colors[i].r=i;
          colors[i].g=i;
          colors[i].b=i;
        }
    // Set the color info for the screen
    SDL_SetColors(screen, colors, 0, 256 );

    // Construct the checkerboard
    makeCheckImage();
    
    // Create the temp surface from the raw RGB data
    temp = SDL_CreateRGBSurfaceFrom(checkImage, checkImageWidth, checkImageHeight, 24, 
            checkImageWidth*3, 0x000000ff, 0x0000ff00, 0x00ff0000, 0xff000000);
    if (temp == NULL) {
        printf("Unable to load checkImage: %s\n", SDL_GetError());
        return 1;
    }
    
    // The raw image data contains no palette info so
    // we need to set the palette manually using the color information 
    // constructed earlier    
    SDL_SetPalette(temp, SDL_LOGPAL|SDL_PHYSPAL, colors, 0, 256);
        
    //Convert the surface to the appropriate display format
    image = SDL_DisplayFormat(temp);
    
    //Release the temporary surface
    SDL_FreeSurface(temp);
    
    //Construct the destination rectangle for our blit
    dest.x = 100;        //Display the image at the (X,Y) coordinates (100,100)
    dest.y = 100;
    dest.w = image->w;
    dest.h = image->h;    

    //Blit the image to the screen
    SDL_BlitSurface(image, NULL, screen, &dest);
    
    // Update the part of the screen that changed
    SDL_UpdateRects(screen, 1, &dest);
        
    //Wait for 2500ms (2.5 seconds) so we can see the image
    SDL_Delay(2500);
    
    //Release the surface
    SDL_FreeSurface(image);
    
    //Return success!
    return 0;
}


```

---

