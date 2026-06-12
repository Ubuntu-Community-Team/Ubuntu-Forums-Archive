---
title: "glDrawPixels draws just garbage"
date: 2010-12-12
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2010-12-12
I have all printable ASCII characters in this picture, excluding empty space:
[img]http://img256.imageshack.us/img256/7899/font2.png[/img]

I converted it to raw binary:
```
convert font2.png -size 1128x16 -depth 8 RGBA:font.dat
```
Then I wrote some code to load and display that font:
```

static uint8_t **pixels = NULL;
static const uint16_t font_w = 1128;
static const uint16_t font_h = 16;
static const uint16_t char_w = 12;

static int read_pixels( void )
{
    FILE *fp;
    int c, row;
    size_t ch_size;

    fp = fopen( "data/font.dat", "r" );

    if ( !fp )
        return 0;

    pixels = malloc( sizeof(uint8_t*) * 95 );
    ch_size = font_h * char_w * 4;

    for( c=0; c<95; c++ )
    {
        for( row=0; row<font_h; row++ )
        {
            pixels[c] = malloc( row*font_w*4 + c*char_w*4 );
            fseek( fp, SEEK_SET, c*ch_size );
            fread( pixels[c]+row*char_w*4, char_w, 4, fp );
        }
    }

    fclose( fp );
    return 1;
}

int load_font( void )
{
    printf( "Loading font...\n" );

    if ( !read_pixels() )
        return 0;

    return 1;
}

void draw_text( int x, int y, char *str )
{
    char *c;
    int index;

    for( c=str; *c; c++ )
    {
        if ( *c == ' ' )
        {
            x++;
            continue;
        }

        if ( !isprint(*c) )
            index = 32;
        else
            index = (*c) - 32;

        if ( index < 0 || index > 127 )
            index = 32;

        glWindowPos2i( x++ * char_w, y );
        glDrawPixels( char_w, font_h, GL_RGBA, GL_UNSIGNED_BYTE, pixels[index] );
    }
}

```

It draws the text at wrong coordinates, and the text looks like this:
[img]http://img576.imageshack.us/img576/4817/helloworldfail.png[/img]
Above should read "Hello world!" (the space shows as green background color because it is not drawn).

Do you see the problem in my code? What do I do wrong? :confused:

---

### Post by ziekfiguur on 2010-12-12
> **crazyfuturamanoob said:**
> 
```

            fseek( fp, SEEK_SET, c*ch_size );

```

I don't know if it's the only error, but SEEK_SET should be the third argument, not the second.

---

### Post by crazyfuturamanoob on 2010-12-12
Edit: The code in my first post will segfault if I put SEEK_SET as third argument.

Here's my temporary solution. It just draws the entire font, and uses glScissor to hide all characters except one:
```

static uint8_t *pixels = NULL;
static const uint16_t font_w = 1128;
static const uint16_t font_h = 16;
static const uint16_t char_w = 12;

static int read_pixels( void )
{
    FILE *fp;
    fp = fopen( "data/font.dat", "r" );

    if ( !fp )
        return 0;

    pixels = malloc( font_w * font_h * 4 );
    fread( pixels, font_w*4, font_h, fp );

    fclose( fp );
    return 1;
}

int load_font( void )
{
    printf( "Loading font...\n" );

    if ( !read_pixels() )
        return 0;

    return 1;
}

void draw_text( int x, int y, char *str, unsigned char color[3] )
{
    char *c;
    int index;
    int y2;
    int start_x;

    y = the_screen_size[1] - y - font_h;
    y2 = y + font_h;
    start_x = x = x - char_w;

    glPushAttrib( GL_ENABLE_BIT|GL_PIXEL_MODE_BIT );

    glDisable( GL_DEPTH_TEST );
    glEnable( GL_SCISSOR_TEST );
    glEnable( GL_BLEND );
    glBlendFunc( GL_ONE, GL_ONE_MINUS_SRC_ALPHA );

    if ( color )
    {
        glPixelTransferf( GL_RED_SCALE, color[0] / 255.0f );
        glPixelTransferf( GL_GREEN_SCALE, color[1] / 255.0f );
        glPixelTransferf( GL_BLUE_SCALE, color[2] / 255.0f );
    }

    for( c=str; (*c); c++ )
    {
        if ( (*c) == '\n' )
        {
            x = start_x;
            y2 -= font_h;
            y -= font_h;
            continue;
        }

        x += char_w;

        if ( isspace(*c) || !isprint(*c) )
            continue;

        index = (*c) - 33;

        glWindowPos2i( x - index*char_w, y2 );
        glScissor( x, y, char_w, font_h );

        glPixelZoom( 1.0f, -1.0f );
        glDrawPixels( font_w, font_h, GL_RGBA, GL_UNSIGNED_BYTE, pixels );
    }

    glPopAttrib();
}

```
Performance is bad, but it will do for now.

---

### Post by Acer3810T on 2010-12-13
That is one crazy solution, but whatever works I guess...

---

### Post by VernonA on 2010-12-22
There are quite a few issues with this code, but the bug you are looking for is in:
```
    for( c=0; c<95; c++ )
    {
        for( row=0; row<font_h; row++ )
        {
            pixels[c] = malloc( row*font_w*4 + c*char_w*4 );
            fseek( fp, SEEK_SET, c*ch_size );
            fread( pixels[c]+row*char_w*4, char_w, 4, fp );
        }
    }

```Specifically, you keep mallocing memory for pixels[c] on each row, but what you should be doing is mallocing enough space for the whole char outside of the 'for( row==0..' loop. Then you need to read into this one big block at the right place for each row.

Whilst you are correcting this loop, you might want to fix the bug in the fseek line, as I don't think it is going to the correct place in the file. As I recall, the convert command will produce a file that is horizontally striped, but you have assumed it is vertically striped. Either way, the computation is still wrong since you also forgot to seek to the row you intend to read.

To help you debug this I would start with a separate program which simply tries to read the first char out of the file. Don't use pointers to pointers as they are an unnecessary confusion. You know up front what you are reading so declare a suitable array immediately. Once you get this working, I'd suggest creating a structure which would hold one char, then declare pixels to be an array of 96 of them.
Rgds
Vernon

---

