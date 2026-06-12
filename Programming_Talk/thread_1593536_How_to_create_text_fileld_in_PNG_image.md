---
title: "How to create text fileld in PNG image?"
date: 2010-10-11
forum: Programming Talk
---

### Post by Mathew Roy on 2010-10-11
Can someone tell me how to write text data like Author, Title, etc to a PNG file created by my file. This is the function in my program to write png file. When I compile this I dont get any warning, but when I run the program, I get libpng warning: "iTXt chunk not supported.". what shall I do?. Please help.

The problem is I don't have a sound knowledge in handling PNG file. Also I cant afford to study it completely due to lack of time. Pleas help me to add text filed to the PNG files created by my program.

[PHP]
int r8_png(const char *fle,struct details a)
{
    int y;
    char header[8];
     FILE *f=fopen(fle,"wb");
    fread(header, 1, 8, f);
    printf("Writing to Output file                  :-");
    fflush(stdout);
    png_ptr = png_create_write_struct(PNG_LIBPNG_VER_STRING, NULL, NULL, NULL);
    info_ptr = png_create_info_struct(png_ptr);
    png_init_io(png_ptr, f);
    if (setjmp(png_jmpbuf(png_ptr)))
    {
        printf("[write_png_file] Error during writing header");
        return -1;
    }
    png_set_IHDR(png_ptr, info_ptr, a.width, a.height,
             a.bit_depth, a.color_type, PNG_INTERLACE_NONE,
             PNG_COMPRESSION_TYPE_BASE, PNG_FILTER_TYPE_BASE);
    #if defined(PNG_TEXT_SUPPORTED)    
    {
        int txt_fields=0;
        png_text text[3];
     
        text[txt_fields].key = "Author";
        text[txt_fields].text ="Mathew Roy.T";
        txt_fields++;

        text[txt_fields].key ="Email";
        text[txt_fields].text="mathewroy@ieee.org";

        png_set_text(png_ptr, info_ptr, text,txt_fields);
    }
    
    #endif

    png_write_info(png_ptr, info_ptr);
    /* write bytes */
    if (setjmp(png_jmpbuf(png_ptr)))
        printf("[write_png_file] Error during writing bytes");
    
    png_write_image(png_ptr,row_pointers);
    png_write_end(png_ptr, NULL);
    printf("Done.\n");
    /*Free Memory*/
    for (y=0; y<a.height; y++)
        free(row_pointers[y]);
    free(row_pointers);
    /*Deleting the structures related with writng PNG image*/
    png_destroy_write_struct(&png_ptr,&info_ptr);
    
    fclose(f);
    //printf("File Closed.\n");
    return 0;
}
[/PHP]
Thank you in advance for all help extended.

---

### Post by r-senior on 2010-10-11
If you are on a schedule, have you considered using ImageMagick to annotate the image, i.e. produce your base image with your program and then add the text?

[http://www.imagemagick.org/Usage/annotating/#annotating]("http://www.imagemagick.org/Usage/annotating/#annotating")

You could combine the calling of your program and ImageMagick into a shell script?

---

### Post by Mathew Roy on 2010-10-12
[r-senior]("http://ubuntuforums.org/member.php?u=288993") I dont want to write on top of the image. What I want is to write text data to the chunk.
Thanks for your cooperation.

---

### Post by spjackson on 2010-10-12
> **Mathew Roy said:**
> Can someone tell me how to write text data like Author, Title, etc to a PNG file created by my file. This is the function in my program to write png file. When I compile this I dont get any warning, but when I run the program, I get libpng warning: "iTXt chunk not supported.". what shall I do?. Please help.

I don't know much about libpng, but from what I've read you get this if the relevant option is not compiled into libpng. If that's the case, you would need to get the source, configure what you need and build from that.

Alternatively, there may be an alternative package (I can't check at the moment) that includes extra features (like there is for the various vim packages).

---

### Post by glennrp on 2010-10-12
You need to define[FONT=monospace] (twice, once for each chunk)

[/FONT][COLOR=#000000][COLOR=#0000BB]    text[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]txt_fields[/COLOR][COLOR=#007700]].[/COLOR][COLOR=#0000BB]compression = PNG_TEXT_COMPRESSION_NONE
[/COLOR][/COLOR]

---

### Post by glennrp on 2010-10-13
> **glennrp said:**
> You need to define[FONT=monospace] (twice, once for each chunk)

[/FONT][COLOR=#000000][COLOR=#0000bb]    text[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]txt_fields[/COLOR][COLOR=#007700]].[/COLOR][COLOR=#0000bb]compression = PNG_TEXT_COMPRESSION_NONE
[/COLOR][/COLOR]

png_set_text() is expecting txt_fields to be the number of chunks, so you need to increment it once more before calling png_set_text().  Otherwise you'll only store the first text chunk.

---

### Post by Mathew Roy on 2010-10-14
> **glennrp said:**
> png_set_text() is expecting txt_fields to be the number of chunks, so you need to increment it once more before calling png_set_text().  Otherwise you'll only store the first text chunk.

Oh! I can see that, I will fix the bug.Thank you very much for finding that logical error.  But still, one text field must be written to the PNG file!.. But even that is not happening. When I execute the program I get the libpng warning..

---

### Post by glennrp on 2010-10-14
> **Mathew Roy said:**
> Oh! I can see that, I will fix the bug.Thank you very much for finding that logical error.  But still, one text field must be written to the PNG file!.. But even that is not happening. When I execute the program I get the libpng warning..

Right.  But you must also do
[COLOR=#000000][COLOR=#0000bb]text[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]txt_fields[/COLOR][COLOR=#007700]].[/COLOR][COLOR=#0000bb]compression = PNG_TEXT_COMPRESSION_NONE;

to get it to write any chunks.  The second problem, as you observed, will only prevent it from writing the final text chunk.
[/COLOR][/COLOR]

---

### Post by Mathew Roy on 2010-10-15
> **glennrp said:**
> Right.  But you must also do
[COLOR=#000000][COLOR=#0000bb]text[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]txt_fields[/COLOR][COLOR=#007700]].[/COLOR][COLOR=#0000bb]compression = PNG_TEXT_COMPRESSION_NONE;

to get it to write any chunks.  The second problem, as you observed, will only prevent it from writing the final text chunk.
[/COLOR][/COLOR]
Wow!. That fixes the bug. Thank u so much. The text chunk gets written successfully without any warning...
But, my primary aim remains unfulfilled!.:(. I cant find my name in the properties window of the image produced by my image. Now, can you kindly tell me how can I make my name appear in the property window?

---

