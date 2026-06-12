---
title: "Getting Cairo to render freetype fonts as Ubuntu does it"
date: 2013-02-25
forum: Programming Talk
---

### Post by runesvend on 2013-02-25
Hello all

I'm using Cairo to draw text in a program using Freetype. The problem is that the font doesn't look like it does in Ubuntu. The same font type drawn using the gnome-font-viewer program, for example, is a bit "fatter", this font drawn using my program is "thinner" and doesn't look as good.

As far as I can figure out it has to do with the font style information located in /etc/fonts/conf.d/.

I've looked extensively at the code for gnome-font-viewer, but I just can't figure out what it does differently than my code.

I'm attaching a screenshot showing the difference between gnome-font-viewer and the output of my program.

Below follows the code for my program. It simply loads a font from a file (the Ubuntu Regular font), draws some text on a white background and outputs it to a png file.

The code can be built with the following command:

```
cc cairoft.c -g $(freetype-config --cflags --libs) $(pkg-config --cflags --libs cairo) -o cairoft
```

I hope someone can help me here cause I'm pretty lost.

Thanks everyone!

```
#include <cairo.h>
#include <ft2build.h>
#include FT_FREETYPE_H
#include FT_TYPE1_TABLES_H
#include FT_SFNT_NAMES_H
#include FT_TRUETYPE_IDS_H
//#include <cairo/cairo-ft.h>

#define TEXT_SIZE 13

int
main (int argc, char *argv[])
{
    FT_Library ft_library;
    FT_Face ft_face;
    cairo_surface_t *cr_surface;
    cairo_t *cr;
    cairo_font_face_t *cr_face;
    
    char text[] = "The quick brown fox jumps over the lazy frog.";
    char font_path[] = "/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf";
    char output_filename[] = "image.png";

    if (FT_Init_FreeType (&ft_library)) {
        printf("FT_Init_FreeType failed\n");
        return;
    }

    if (FT_New_Face (ft_library, font_path, 0, &ft_face)) {
        printf("FT_New_Face failed\n");
        return;
    }

    cr_surface = cairo_image_surface_create (CAIRO_FORMAT_ARGB32, 1000, 300);
    cr = cairo_create (cr_surface);

    cr_face = cairo_ft_font_face_create_for_ft_face (ft_face, 0);
    cairo_set_font_face (cr, cr_face);
    cairo_set_font_size (cr, TEXT_SIZE);

    cairo_set_source_rgb(cr, 1.0, 1.0, 1.0);
    cairo_rectangle(cr, 0, 0, 1000, 300);
    cairo_fill(cr);
    
    cairo_set_source_rgb(cr, 0.0, 0.0, 0.0);
    cairo_move_to(cr, 2, 150);
    cairo_show_text(cr, text);

    cairo_font_face_destroy (cr_face);
    FT_Done_Face (ft_face);

    cairo_surface_write_to_png (cr_surface, output_filename);
    return 0;
}
```

---

### Post by r-senior on 2013-02-26
I have no idea why your code doesn't produce a nice rendering but I thought it would be worth trying the example from the Cairo Rendering section of the Pango reference manual. I adapted it to display a single line of text in the same font that you were trying and it looks good to me. There is some anti-aliasing in the PNG but I don't think that's an issue with the rendering.

(I adjusted your code and the code below to create a 400x100 image with the text at (20, 20) for comparison).

```
#include <pango/pangocairo.h>

/* Compile with
 * gcc <filename>.c $(pkg-config --cflags --libs pangocairo) -o <filename>
 */

#define FONT "Ubuntu Regular 13"
#define TEXT "The quick brown fox jumps over the lazy dog"

static void draw_text(cairo_t * cr)
{
    PangoLayout *layout;
    PangoFontDescription *desc;

    layout = pango_cairo_create_layout(cr);
    pango_layout_set_text(layout, TEXT, -1);
    desc = pango_font_description_from_string(FONT);
    pango_layout_set_font_description(layout, desc);
    pango_font_description_free(desc);

    cairo_save(cr);
    cairo_set_source_rgb(cr, 0, 0, 0);
    pango_cairo_update_layout(cr, layout);
    cairo_move_to(cr, 20, 20);
    pango_cairo_show_layout(cr, layout);
    cairo_restore(cr);
    g_object_unref(layout);
}

int main(int argc, char **argv)
{
    cairo_t *cr;
    gchar *filename = "image2.png";
    cairo_status_t status;
    cairo_surface_t *surface;

    surface = cairo_image_surface_create(CAIRO_FORMAT_ARGB32, 400, 100);
    cr = cairo_create(surface);
    cairo_set_source_rgb(cr, 1.0, 1.0, 1.0);
    cairo_paint(cr);
    draw_text(cr);
    cairo_destroy(cr);

    status = cairo_surface_write_to_png(surface, filename);
    cairo_surface_destroy(surface);
    if (status != CAIRO_STATUS_SUCCESS) {
        g_printerr("Could not save png to '%s'\n", filename);
        return 1;
    }
    return 0;
}

```

[Pango]("http://www.pango.org/") handles text rendering for GTK and presumably it is applying some settings, scaling, etc. that your direct use of Cairo doesn't employ?

Beyond that, I'm just as lost as you are I'm afraid.

---

### Post by runesvend on 2013-02-26
Asking in the #cairo channel on freenode, I was instructed (by user Jasper) to use pangocairo as well. The difference in rendering is due to the use of subpixel rendering by gnome-font-viewer.

To make it more complicated, there is something called Xsettings, which apparently stores information on how fonts are rendered on the system. The necessary values can be retrieved using the following commands:

```
gsettings get org.gnome.settings-daemon.plugins.xsettings rgba-order
gsettings get org.gnome.settings-daemon.plugins.xsettings hinting
gsettings get org.gnome.settings-daemon.plugins.xsettings antialiasing
```

I was actually planning on using this for Wayland, so this isn't relevant for me. But the code below manages to draw the text *almost* like gnome-font-viewer does (yes, we're not there yet), by hardcoding in the settings returned by the above commands. It might not look appropriate on your screen if you either don't use an LCD panel, or if your subpixel layout doesn't match that of my monitor ("RGB", I believe).

When comparing the text of gnome-font-viewer and the program below, I can see that my program uses subpixel rendering, because the individual pixels (in the seemingly black-and-white text) have red, yellow and blue mixed in.

But... the glyph (individual character) spacing isn't equal to that of gnome-font-viewer. I believe this is called "[kerning]("http://en.wikipedia.org/wiki/Kerning")". How to fix that I have no idea.

```

/* Build using
    gcc <filename> $(pkg-config --cflags --libs pangocairo) -o <output_filename>
*/

#include <pango/pangocairo.h>

#define WIDTH 1000
#define HEIGHT 300
#define TEXT_SIZE 13

static PangoRectangle
draw_text (cairo_t *cr, char *font_desc, char *text)
{
    PangoContext *pc;
    PangoLayout *layout;
    PangoFontDescription *desc;
    int i;
    cairo_font_options_t *fo;
    PangoRectangle pr;

    pc = pango_cairo_create_context(cr);
    fo = cairo_font_options_create();

    cairo_font_options_set_antialias(fo, CAIRO_ANTIALIAS_SUBPIXEL);
    cairo_font_options_set_subpixel_order(fo, CAIRO_SUBPIXEL_ORDER_RGB);
    cairo_font_options_set_hint_style(fo, CAIRO_HINT_STYLE_SLIGHT);

    pango_cairo_context_set_font_options(pc, fo);

    layout = pango_cairo_create_layout (cr);

    layout = pango_layout_new(pc);
    pango_layout_set_text (layout, text, -1);
    desc = pango_font_description_from_string (font_desc);
    pango_layout_set_font_description (layout, desc);
    pango_font_description_free (desc);

    pango_cairo_update_layout (cr, layout);
    pango_cairo_show_layout (cr, layout);

    pango_layout_get_extents(layout, &pr, NULL);
    pango_extents_to_pixels(&pr, NULL);
    printf("x: %i, y: %i, width: %i, height: %i\n", pr.x, pr.y, pr.width, pr.height);

    /* free the layout object */
    g_object_unref (layout);
    
    return pr;
}

int
main (int argc, char *argv[])
{
    cairo_surface_t *cr_surface;
    cairo_t *cr;
    PangoRectangle pr;
    
    char text[] = "The quick brown fox jumps over the lazy dog.";
    char output_filename[] = "image.png";

    cr_surface = cairo_image_surface_create (CAIRO_FORMAT_ARGB32, 1000, 300);
    cr = cairo_create (cr_surface);

    cairo_set_source_rgb(cr, 1.0, 1.0, 1.0);
    cairo_rectangle(cr, 0, 0, WIDTH, HEIGHT);
    cairo_fill(cr);
    
    cairo_set_source_rgb(cr, 0.0, 0.0, 0.0);    

    unsigned int i, ypos = 0;
    char font[32];
    for (i = 0; i < 30; i=i+2) {
        sprintf(font, "Ubuntu %u", i+6);
        pr = draw_text(cr, font, text);
        ypos = ypos + pr.height+2;
        if (ypos < HEIGHT)
            cairo_move_to(cr, 0, ypos);
        else
            break;
    }

    cairo_surface_write_to_png (cr_surface, output_filename);
    cairo_surface_destroy (cr_surface);
    return 0;
}
```

---

