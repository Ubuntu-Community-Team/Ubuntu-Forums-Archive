---
title: "SDL tutorial in C"
date: 2009-03-21
forum: Programming Talk
---

### Post by swappo1 on 2009-03-21
Hello,

I am working through the lazy foo sdl tutorial number 2.  I know C but I am not familiar with C++ which is what the tutorials are written in.  I am having trouble converting the following function to C.  I am assuming that std::string filename takes a string(the file name) into the function and puts the string in SDL_LoadBMP(filename.c_str() ).  Is there a simple way to re-write this function in C?  I will have multiple files so I would like to use a function.  I can do it with out a function but it would have redundant code.  
```
SDL_Surface *load_image( std::string filename )

{

    //Temporary storage for the image that's loaded

    SDL_Surface* loadedImage = NULL;



    //The optimized image that will be used

    SDL_Surface* optimizedImage = NULL;



    //Load the image

    loadedImage = SDL_LoadBMP( filename.c_str() );



    //If nothing went wrong in loading the image

    if( loadedImage != NULL )

    {

        //Create an optimized image

        optimizedImage = SDL_DisplayFormat( loadedImage );



        //Free the old image

        SDL_FreeSurface( loadedImage );

    }



    //Return the optimized image

    return optimizedImage;
```

---

### Post by kjohansen on 2009-03-22
since the function SDL_LoadBMP accepts a C string you can just write a function that accepts a character pointer and pass that to the SDL_LoadBMP function.

```

SDL_Surface* function(char* filename)
{
 //The optimized image that will be used

    SDL_Surface* optimizedImage = NULL;
    SDL_Surface* loadedImage = NULL;
    //Load the image
    loadedImage = SDL_LoadBMP( filename);
    return loadedImage; 
}

```

---

### Post by swappo1 on 2009-03-22
Once I declared loadedImage in the function it worked.  Thanks

---

